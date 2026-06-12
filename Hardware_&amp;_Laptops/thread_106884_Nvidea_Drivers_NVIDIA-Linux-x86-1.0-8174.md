---
title: "Nvidea Drivers NVIDIA-Linux-x86-1.0-8174"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by Sp@z on 2005-12-21
These drivers are more current than the ones I am currently using. I have tried installing them using the Nvidea websight instructions but I got this error.

Anyone use these drivers before? My openGl is kinna choppy in Ut2K4 and was hoping updating the drivers would help. In case you need to know I am running Nvidea 5700 Ultra 128 MB....... Also I use the 686 kernal for AMD processors.

Here is the error message...........

 ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
         kernel.  This may be because it is in use (for example, by the X
         server), but may also happen if your kernel was configured without
         support for module unloading.  Please be sure you have exited X
         before attempting to upgrade your driver.  If you have exited X, know
         that your kernel supports module unloading, and still receive this
         message, then an error may have occured that has corrupted the NVIDIA
         kernel module's usage count; the simplest remedy is to reboot your
         computer.

---

### Post by Syphin on 2005-12-21
I installed them using the Ubuntu guide from this thread: [HOWTO: Latest NVIDIA drivers]("http://ubuntuforums.org/showthread.php?t=75074")
Method 2

They seem to run fine on my nv6600.  Although i havnt been able to realy test them on a high gfx game yet myself.

To install it you need to uninstall the previous nvidia driver, and a cpl more things..  Its all listed in that thread. Worked very well for me with no errors. :)

---

### Post by codejunkie on 2005-12-21
[QUOTE=Sp@z]These drivers are more current than the ones I am currently using. I have tried installing them using the Nvidea websight instructions but I got this error.

Anyone use these drivers before? My openGl is kinna choppy in Ut2K4 and was hoping updating the drivers would help. In case you need to know I am running Nvidea 5700 Ultra 128 MB....... Also I use the 686 kernal for AMD processors.

Here is the error message...........

 ERROR: An NVIDIA kernel module 'nvidia' appears to already be loaded in your
         kernel.  This may be because it is in use (for example, by the X
         server), but may also happen if your kernel was configured without
         support for module unloading.  Please be sure you have exited X
         before attempting to upgrade your driver.  If you have exited X, know
         that your kernel supports module unloading, and still receive this
         message, then an error may have occured that has corrupted the NVIDIA
         kernel module's usage count; the simplest remedy is to reboot your
         computer.[/QUOTE]
you need to completly remove all nvidia packages in synaptic they cause problems, with the official driver, and you need to have gcc-3.4, build-essential, and the linux-headers package for your kernel installed 
then to install the driver switch to the terminal with ctrl+alt+F1 login and run 
```
sudo /etc/init.d/gdm stop
```
then
```
sudo export CC=gcc-3.4
```
the run the nvidia installer as root 
once it has finished edit your /etc/X11/xorg.conf file and change the driver to nvidia.

---

### Post by Sp@z on 2005-12-21
Thank you for the replies. I searched these forums for 20 minutes for a howto. OMG I really need to expand my vocabulary I guess! Thanx again!

---

### Post by Sp@z on 2005-12-22
I got it to load and work using the HowTo method 2 as well thanx again!~

---

