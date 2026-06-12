---
title: "Installing NVIDIA graphics card driver"
date: 2009-08-18
forum: Hardware
---

### Post by Saxcore on 2009-08-18
Hiya. I've had a look around, and can't seem to find anything specifically on this problem, however i'm very new to all of this, so forgive me if i'm getting confused. 

I'm currently trying to install a driver for my NVIDIA 8600 GT card. When i run the installer, it reaches an error when it attempts to compile the kernel module. Here is part of the nvidia-installer.log file that is output.

```
ERROR: The kernel header file
       '/lib/modules/2.6.24-24-generic/build/include/linux/kernel.h' does not
       exist.  The most likely reason for this is that the kernel source path
       '/lib/modules/2.6.24-24-generic/build' is incorrect.  Please make sure
       you have installed the kernel source files for your kernel and that they
       are properly configured; on Red Hat Linux systems, for example, be sure
       you have the 'kernel-source' or 'kernel-devel' RPM installed.  If you
       know the correct kernel source files are installed, you may specify the
       kernel source path with the '--kernel-source-path' command line option.
```

The thing that i don't get (and this is probably pretty simple) is that it is trying to use the source code from 2.6.24-24, which for some reason i don't have. However, i assumed my system was at least up to version 2.6.28-15

So, entering
```
uname -r
```
into the terminal returns
```
2.6.24-24-generic
```

...could it be that it simply thinks it is an older kernel version than it actually is?

As i said, this is probably extremely straight forward...

Thanks in advance! 

-Sam

---

### Post by sitendurocks@gmail.com on 2009-08-18
Hi!

i have the exact same card, and i have sorted out the problem, so here is what i suggest you do. 
 1st makes sure your kernel i s updated by running the update manager feature.
 2. download the software called ubuntu tweak and remove the old kernel packages..
3. then you will need to download the latest nividia driver from nvidia website named 185.18.31. and keep it in your home folder. and write down the name of the nvidia file on a piece of paper it should be something like "NVIDIA-Linux-x86_64-185.18.31-pkg1.run"
4. restart the computer.
5. after the computer starts you should start your internet connection and then press ctrl+alt+F1.
6. in the console type in your user name and password and th terminal window will come.
7. here type sudo /etc/init.d/gdm stop , this will stop the xorg.
8. now enter " sudo sh NVIDIA-Linux-x86_64-185.18.31-pkg1.run" , remember the "sudo sh" will be followed by the actual name of your nvida driver that you wrote on the paper.
9. accept everything they ask you to do and continue with the installation. 
10. soon they will ask you if you want the  installer to compile a kernel and you should confirm. 
11. the rest of the installation is a breeze.
12. after sometime they will ask whether you want to configure your  "xorg.conf" file? you should say yes.
13. after the driver is installed and theterminal opens once more you should type "sudo /etc/init.d/gdm restart"
14. after that if the normal graphical user interface doe not come back just press ctrl+alt+f7.
15. there you are done.
16. none of the above steps is made by me, i got everything from this community and its my time to give something back, hope it helps you!!

---

### Post by Saxcore on 2009-08-18
Hi, thanks for your quick reply!

I'm already at the point where i need to install the driver/ create the kernel module (i'm on another computer at the moment, as i uninstalled the previous graphics drivers last night). However, it is when running the NVIDIA*.run file that i hit problems.

I'll try the "ubuntu tweak" as you've suggested; however, i think that the module compilation may continue to have problems, as it looks for older source code that i no longer have. From what i can tell, i either need to find older source code or update my system to know which version it actually is.. (i'm assuming my system isn't 2.6.24-24).

Anyway, thanks for your help! Appreciated.

---

