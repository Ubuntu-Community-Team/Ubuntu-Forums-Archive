---
title: "Installing video driver"
date: 2009-08-15
forum: Hardware
---

### Post by bobke on 2009-08-15
1- I have a new Geforce 8400GS PCI-E 16x (that replaced my 7300GT) and downloaded this driver (from nvidia.com) for it, but have not installed yet. Supposed to come with a step-by-step instructions. 
[http://www.nvidia.com/object/linux_display_ia32_185.18.31.html](http://www.nvidia.com/object/linux_display_ia32_185.18.31.html)

2- Found this on the Ubuntu forums that shows step-by step instructions.
How to install nvidia185.18 graphics driver
[http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+driver+185.18](http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+driver+185.18)

I am confused as to which is the best approach. Should I use #1 or 2, or get another card that supports the older driver.  Right now it appears that the above driver is not supported (in any Ubuntu packge) up through 8.04 and maybe even 9.x. I also found something here at Ubuntu.com that suggested not to install a driver by hand, but to use the one in the package instead and let it install automatically. 
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).  

If the latter is true, will I need to get another card like my old 7300 that has the older driver? (the 7300 worked great for years, until it fell victim to the infamous"capacitor-plague".) What are the pitfalls, if any, to installing the above nvidia driver for the 8400?

---

### Post by ratcheer on 2009-08-15
Your card and driver are fine. Keep them.

Use this method, it works:

Ctrl-Alt-F1
cd to location of your driver file
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-185.18.31-pkg1.run
Choose x.org auto configuration when it asks
sudo reboot

Tim

---

### Post by bobke on 2009-08-17
> **ratcheer said:**
> Your card and driver are fine. Keep them.

Use this method, it works:

Ctrl-Alt-F1
cd to location of your driver file
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-185.18.31-pkg1.run
Choose x.org auto configuration when it asks
sudo reboot

Tim I got something like this: Compiler kernel check failed. Do you want to download the latest kernel from nvidia (y). Then got this: The cc version check failed. The compiler used to compile the kernel (gcc 4.0) dosnt match the current compiler (gcc 4.1) the linux 2.6 kernel module loader rejects this... If you know what you are doing and want to ignore the gcc version check select (n) to continue installation or (y) to abort.

I don't know what I am doing!  So I a aborted.  What now?

---

### Post by cascade9 on 2009-08-17
You may find that the command-

export CC=/usr/bin/gcc-4.0 

before you try to install the nvidia  drivers works

---

### Post by bobke on 2009-08-17
> **cascade9 said:**
> You may find that the command-

export CC=/usr/bin/gcc-4.0 

before you try to install the nvidia  drivers works

This is what I get:

root@desk:~# export CC=/usr/bin/gcc-4.0 
root@desk:~#

Did'nt mention here that the last couple of boots I also get: "File system check failed" but I can still boot and login to root. If I try to find a file that is in a folder such as the video driver, I'll get "file not found."  I' m told this has to do with partitioning, when I reinstalled mepis on another partition. This may be part of the problem. I've printed another thread from this forum that tells me how to fix this. I don't know if it will affect the driver installation, though.

---

### Post by cascade9 on 2009-08-18
No idea on your  "File system check failed" problem, but "export CC=/usr/bin/gcc-4.0" appears to have worked (no error msgs, etc) 

To be more exact, this is the command set I would try- (mostly copied from ratcheers post)


cd to location of your driver file
sudo /etc/init.d/gdm stop
export CC=/usr/bin/gcc-4.0
sudo sh ./NVIDIA-Linux-x86-185.18.31-pkg1.run
Choose x.org auto configuration when it asks
sudo reboot

---

### Post by bobke on 2009-08-26
> **cascade9 said:**
> No idea on your  "File system check failed" problem, but "export CC=/usr/bin/gcc-4.0" appears to have worked (no error msgs, etc) 

To be more exact, this is the command set I would try- (mostly copied from ratcheers post)


cd to location of your driver file
sudo /etc/init.d/gdm stop
export CC=/usr/bin/gcc-4.0
sudo sh ./NVIDIA-Linux-x86-185.18.31-pkg1.run
Choose x.org auto configuration when it asks
sudo reboot

I had to type the following commands separately because they didn't give satifactory results enough to continue through each one in succession. But you get the idea. Again, I wonder if this is a problem of the fsck failure. 

root@desk: cd /home/me
root@desk:/home/me# /etc/init.d/gdm stop
bash: /etc/ini.d/gdm: no such file or directory

root@desk:/home/me# export CC=/usr/bin/gcc-4.0
root@desk:/home/me#

root@desk:/home/kim# sh ./NVIDIA-Linux-x86-185.18.31-pkg1.run
sh: can't open NVIDIA

---

### Post by ratcheer on 2009-08-29
The problem with the gdm stop command is that you left out a letter:

/etc/init.d/gdm
not /etc/ini.d/gdm

Then, for the next command, were you in the directory with the Nvidia driver file? Did you preface tha command with sudo?

You have to follow the instructions, exactly. Go back to my first post in this thread.

Tim

---

### Post by bobke on 2009-09-07
> **ratcheer said:**
> The problem with the gdm stop command is that you left out a letter:

/etc/init.d/gdm
not /etc/ini.d/gdm

Then, for the next command, were you in the directory with the Nvidia driver file? Did you preface tha command with sudo?

You have to follow the instructions, exactly. Go back to my first post in this thread.

Tim

Having trouble finding time to continue trying, but here's more:

Got to installation but stopped at this:

"No matching precompiled kernel interface was found on nvidia ftp site; the installer will need to compile a kernel interface for your kernel.  "OK"

ERROR: you do not appear to have libc header files installed on your system. Please install your distributions libc developemt package.

----
I thought the "export =CC" line was suppose to fix this. I'm still stuck!


Remember I'm using Edgy where the repos are supposedly obsolete. If this has any bearing on the driver installation.

---

### Post by bobke on 2009-09-08
The installation failed because apparently the installer can't find a kernel source code. I need to get and install the following:

Kernel-source code
Kernel-header
Kernel-dev pkg

These appear to be in the Edgy repos for easy download and install (shown as not installed). Unfortuanatly the Edgy repos are gone EOL. So I have no easy method of installing them. These need to be installed before the installation can take place according to the instructions. Where can I go to download these, and how are they installed?

Ubuntu Edgy, Geforce 7300LE, legacy driver 71.86.11 or any that will work with Edgy and this card. Also there is supposed to be a linker file (usr/bin/ld) - this is present.

---

### Post by bobke on 2009-09-10
> **bobke said:**
> The installation failed because apparently the installer can't find a kernel source code. I need to get and install the following:

Kernel-source code
Kernel-header
Kernel-dev pkg

These appear to be in the Edgy repos for easy download and install (shown as not installed). Unfortuanatly the Edgy repos are gone EOL. So I have no easy method of installing them. These need to be installed before the installation can take place according to the instructions. Where can I go to download these, and how are they installed?

Ubuntu Edgy, Geforce 7300LE, legacy driver 71.86.11 or any that will work with Edgy and this card. Also there is supposed to be a linker file (usr/bin/ld) - this is present.Well, I didn't exactly give up on all this. But because I couldn't find the above. I tried something else. I installed Edgy on hda5, reconfigured x-org to 'nv' driver and rebooted. What! It worked!. So I went back to hda1 (where the problem started) and  reset to 'nv' , and it worked! So I'm back to normal. What I got out of all this is: a number of new commands and better understanding of the processes to repair the problem. However, I don't know for sure if any of them would have worked because I never could install a driver. Oh well! 

This problem is resolved

Thanks all for your input

bk

---

