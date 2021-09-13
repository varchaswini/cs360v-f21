# Setting up a virtual machine on the lab computers

Note: you need a UT CS account in order to use this approach. 

You can use any of the following (gilligan) CS machines to complete projects for this class. As you need access to the KVM module for this project, you cannot use other CS machines. See [here](https://www.cs.utexas.edu/facilities/documentation) for information about how to access these machines remotely. 
- gilligan
- ginger
- lovey
- mary-ann
- skipper
- the-professor
- thurston-howell-iii

1. Download the compressed [VM image](https://www.cs.utexas.edu/~vijay/teaching/project1.tar.gz) (3.4 GB) on one of the gilligan machines. The uncompressed VM image (8.8 GB) is available for download [here](http://www.cs.utexas.edu/~soujanya/project1-vm.qcow2). You can use `wget` to download an image over the command line:
```
$ wget https://www.cs.utexas.edu/~vijay/teaching/project1.tar.gz
```

2. Now start up a VM that listens on a specific port using the following command. To avoid contention over ports, use `<port-id> = 5900 + <team-number>`. For example, if your group-id is 15, your port-id will be 5915.
```
$ qemu-system-x86_64 -cpu host -drive file=<path-to-qcow2-image>,format=qcow2 -m 512 -net user,hostfwd=tcp::<port-id>-:22 -net nic -nographic -enable-kvm
```

3. On another terminal, ssh into the same machine and connect to the VM using the following command. On connecting, enter the password as `abc123`.
```
$ ssh -p <port-id> cs378@localhost
```

4. Verify that you have gdb 7.7 and gcc 4.8 in the VM. Also cross check that you have python-3.4 installed or in your $HOME directory. In case you need to install any of them, follow the instructions on the [installations](https://github.com/vijay03/cs360v-f21/blob/main/installation.md) page.

5. Download the code for project 1 onto the VM. We recommend making a git repository out of your existing work and cloning it onto the VM. 

You can now ssh into your VM and run JOS and GDB in the same way as described in [Lab 0](https://github.com/vijay03/cs360v-f21/blob/main/Lab0.md).