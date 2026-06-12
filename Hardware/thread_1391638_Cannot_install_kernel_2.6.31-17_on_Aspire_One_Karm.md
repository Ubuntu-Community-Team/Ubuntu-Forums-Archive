---
title: "Cannot install kernel 2.6.31-17 on Aspire One Karmic"
date: 2010-01-27
forum: Hardware
---

### Post by stchman on 2010-01-27
Hello all, I have not used my Aspire One in a while so there were lots of updates.

Everything installed except the latest kernel 2.6.31-17.  After installation I was asked to reboot(normal).  I was using the -16 kernel and the -17 packages installed, but uname -a still returns the -16 kernel.

I un-installed and re-installed the following packages with a sudo apt-get clean to make sure to download the packages fresh.

linux-headers-2.6.31-17
linux-headers-2.6.31-17-generic
linux-image-2.6.31-17-generic

Still the same thing.

Anyone have any insight?

Thanks.

---

### Post by FlyingBuzz on 2010-01-27
see the output of 

ls /boot

command. If it contains something about 2.6.31-17
run sudo update-grub (or update-grub2 if you're using grub2)

---

### Post by stchman on 2010-01-31
Here is the output when I try to install 2.6.31-17


```

bob@bajor:~$ sudo apt-get install linux-generic linux-headers-2.6.31-17 linux-headers-2.6.31-17-generic linux-headers-generic linux-image-2.6.31-17-generic linux-libc-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-libc-dev is already the newest version.
linux-libc-dev set to manually installed.
The following extra packages will be installed:
  linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.31 linux-source-2.6.31
The following NEW packages will be installed:
  linux-generic linux-headers-2.6.31-17 linux-headers-2.6.31-17-generic linux-headers-generic linux-image-2.6.31-17-generic
  linux-image-generic
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.0MB of archives.
After this operation, 172MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic-updates/main linux-image-2.6.31-17-generic 2.6.31-17.54 [28.8MB]
Get:2 http://us.archive.ubuntu.com karmic-updates/main linux-image-generic 2.6.31.17.30 [3,322B]                                              
Get:3 http://us.archive.ubuntu.com karmic-updates/main linux-generic 2.6.31.17.30 [3,314B]                                                    
Get:4 http://us.archive.ubuntu.com karmic-updates/main linux-headers-2.6.31-17 2.6.31-17.54 [9,531kB]                                         
Get:5 http://us.archive.ubuntu.com karmic-updates/main linux-headers-2.6.31-17-generic 2.6.31-17.54 [674kB]                                   
Get:6 http://us.archive.ubuntu.com karmic-updates/main linux-headers-generic 2.6.31.17.30 [3,316B]                                            
Fetched 39.0MB in 42s (913kB/s)                                                                                                               
Selecting previously deselected package linux-image-2.6.31-17-generic.
(Reading database ... 125150 files and directories currently installed.)
Unpacking linux-image-2.6.31-17-generic (from .../linux-image-2.6.31-17-generic_2.6.31-17.54_i386.deb) ...
Done.
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.31.17.30_i386.deb) ...
Selecting previously deselected package linux-generic.
Unpacking linux-generic (from .../linux-generic_2.6.31.17.30_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.31-17.
Unpacking linux-headers-2.6.31-17 (from .../linux-headers-2.6.31-17_2.6.31-17.54_all.deb) ...
Selecting previously deselected package linux-headers-2.6.31-17-generic.
Unpacking linux-headers-2.6.31-17-generic (from .../linux-headers-2.6.31-17-generic_2.6.31-17.54_i386.deb) ...
Selecting previously deselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_2.6.31.17.30_i386.deb) ...
Setting up linux-image-2.6.31-17-generic (2.6.31-17.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 11: quiet: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.31-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-17-generic; however:
  Package linux-image-2.6.31-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.17.30); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.31-17 (2.6.31-17.54) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                     Setting up linux-headers-2.6.31-17-generic (2.6.31-17.54) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-headers-generic (2.6.31.17.30) ...
Errors were encountered while processing:
 linux-image-2.6.31-17-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
bob@bajor:~$ 


```

Looks like the packages I download are not working properly.

---

### Post by stchman on 2010-02-02
I just updated another machine and it needed to install the -17 kernel.

That went without incident.  It is a 64 bit machine, but I cannot see that being a difference.

---

### Post by stchman on 2010-02-05
Ok, now I cannot install 2.6.31-19 kernel.  I get the same messages.

I wonder if it is an Aspire One thing.  Any other Aspire One owners having this difficulty?

---

### Post by grahampa on 2010-02-18
I am having the same problem.
I have an Acer Aspire 1410 not technically an Aspire One.

---

### Post by grahampa on 2010-02-18
Update:
My computer was complaining that it could not find 'update-grub' and after looking around sure enough my 'update-grub' was gone. Not sure where it went. It had to have been there for previous kernel updates.

Either way I installed(reinstalled?) grub 2 and during its configure process it found the 2 kernels (2.6.31-17 and 2.6.31-19) and then after a reboot 'uname -r' tells me that I am using 2.6.31-19.

I realize reinstalling grub2 is kind of a shot gun solution, but it worked for me.

---

### Post by xeclipsex on 2010-02-19
To all aspire users u need to update flash bios before getting rid of windows... if u already did that then u need to install u netbootin and set up a flash drive as a boot device with free dos option ive searched all over the place for this answer and the other issues linked to it aspire series is a tough one for linux if u cant update flash bios. solutions will be posted soon in the installation forum thread "Heads up acer users" as soon as i get a chance to link some sites for all

---

### Post by stchman on 2010-02-20
I installed the latest BIOS from ACER's website 3310 and now what?  How do you install the latest kernel?

Thanks.

---

### Post by stchman on 2010-02-20
Here is what I get when I install the -19 kernel with the latest 3310 BIOS.


```
bob@bajor:~$ sudo apt-get install linux-generic linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic linux-headers-generic linux-image-2.6.31-19-generic linux-libc-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-libc-dev is already the newest version.
linux-libc-dev set to manually installed.
The following extra packages will be installed:
  linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.31 linux-source-2.6.31
The following NEW packages will be installed:
  linux-generic linux-headers-2.6.31-19 linux-headers-2.6.31-19-generic linux-headers-generic linux-image-2.6.31-19-generic
  linux-image-generic
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.1MB of archives.
After this operation, 172MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic-updates/main linux-image-2.6.31-19-generic 2.6.31-19.56 [28.8MB]
Get:2 http://us.archive.ubuntu.com karmic-updates/main linux-image-generic 2.6.31.19.32 [3,380B]                                              
Get:3 http://us.archive.ubuntu.com karmic-updates/main linux-generic 2.6.31.19.32 [3,372B]                                                    
Get:4 http://us.archive.ubuntu.com karmic-updates/main linux-headers-2.6.31-19 2.6.31-19.56 [9,531kB]                                         
Get:5 http://us.archive.ubuntu.com karmic-updates/main linux-headers-2.6.31-19-generic 2.6.31-19.56 [674kB]                                   
Get:6 http://us.archive.ubuntu.com karmic-updates/main linux-headers-generic 2.6.31.19.32 [3,368B]                                            
Fetched 39.1MB in 56s (697kB/s)                                                                                                               
Selecting previously deselected package linux-image-2.6.31-19-generic.
(Reading database ... 125179 files and directories currently installed.)
Unpacking linux-image-2.6.31-19-generic (from .../linux-image-2.6.31-19-generic_2.6.31-19.56_i386.deb) ...
Done.
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.31.19.32_i386.deb) ...
Selecting previously deselected package linux-generic.
Unpacking linux-generic (from .../linux-generic_2.6.31.19.32_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.31-19.
Unpacking linux-headers-2.6.31-19 (from .../linux-headers-2.6.31-19_2.6.31-19.56_all.deb) ...
Selecting previously deselected package linux-headers-2.6.31-19-generic.
Unpacking linux-headers-2.6.31-19-generic (from .../linux-headers-2.6.31-19-generic_2.6.31-19.56_i386.deb) ...
Selecting previously deselected package linux-headers-generic.
Unpacking linux-headers-generic (from .../linux-headers-generic_2.6.31.19.32_i386.deb) ...
Setting up linux-image-2.6.31-19-generic (2.6.31-19.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 11: quiet: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.31-19-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-19-generic; however:
  Package linux-image-2.6.31-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.19.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.31-19 (2.6.31-19.56) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                     Setting up linux-headers-2.6.31-19-generic (2.6.31-19.56) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-headers-generic (2.6.31.19.32) ...
Errors were encountered while processing:
 linux-image-2.6.31-19-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by stchman on 2010-02-20
I found the problem.

Apparently when I tried to get both the SD card readers working I used this command in the /etc/default/grub file.

Here is what I did:

```

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1 elevator-noop quiet splash"

```

The line I commented out was the original line and the pciehp was the stuff I did.  This kept from properly installing the new kernel.

Now I cannot get the RH SD reader to work.  The LH reader works fine.

Thanks.

---

