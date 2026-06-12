---
title: "Removing r5u870"
date: 2009-01-02
forum: Hardware
---

### Post by joey_p1979 on 2009-01-02
I keep getting the following when I try to install any thing. I am a newbie to Linux and I am just learning the commands. Thank you for the help. 

Setting up r5u870-dkms (0.11.1-0ubuntu1~ppa2i) ...             
Removing old r5u870-0.11.1 DKMS files...                       

------------------------------
Deleting module version: 0.11.1
completely from the DKMS tree. 
------------------------------ 
Done.                          
Loading new r5u870-0.11.1 DKMS files...

Creating symlink /var/lib/dkms/r5u870/0.11.1/source ->
                 /usr/src/r5u870-0.11.1               

DKMS: add Completed.
Installing prebuilt kernel module binaries (if any)
Building module...                                 

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-9-generic -C /lib/modules/2.6.27-9-generic/build M=/var/lib/dkms/r5u870/0.11.1/build....(bad exit status: 2)                                                                

Error! Bad return status for module build on kernel: 2.6.27-9-generic (i686)
Consult the make.log in the build directory                                 
/var/lib/dkms/r5u870/0.11.1/build/ for more information.                    
0                                                                           
0                                                                           
dpkg: error processing r5u870-dkms (--configure):                           
 subprocess post-installation script returned error exit status 10          
Errors were encountered while processing:                                   
 r5u870-dkms                                                                
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

