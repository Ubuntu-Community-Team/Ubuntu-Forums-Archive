---
title: "New user driver install problem 15.10"
date: 2015-12-21
forum: Hardware
---

### Post by bob163 on 2015-12-21
I am trying to install a graphics driver (NVIDIA-Linux-x86_64-340.96.run) using the terminal.(not x-terminal)

z@y:~$ sudo su
[sudo] password for z: 
root@y:/home/z# sudo '/home/z/Downloads/NVIDIA-Linux-x86_64-340.96.run' 
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 340.96.................................................................................................................................................................................................................................
root@y:/home/z# 




I am getting the error message
 ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

                                       OK

---

### Post by howefield on 2015-12-21
Why not use the included in a default Ubuntu installation "*Additional Drivers*" application to install the driver ?

Much easier.

---

### Post by bob163 on 2015-12-21
Doh!!

---

