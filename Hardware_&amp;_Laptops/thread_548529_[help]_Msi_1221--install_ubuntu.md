---
title: "[help] Msi 1221--install ubuntu?"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by leptons on 2007-09-11
Hi, I'm kind of a newb here.

I have just bought a msi 1221 laptop barebone (specs here: [http://www.msicomputer.com/product/p_spec.asp?model=MS-1221&class=nb](http://www.msicomputer.com/product/p_spec.asp?model=MS-1221&class=nb))

then I bought a 
Core 2 Duo Merom T7500,
WD Scorpio 160 GB SATA Hard Drives
Crucial 2GB x1 stick memory
Intel PRO/Wireless 3945ABG Mini-PCI Express

assembled the parts in the laptop... the laptop turns on fine, no errors. memtest ran fine.

the next task: install ubuntu on it.

so I pop the Kubuntu live disk 7.04 (x86 version) in, tried to go into the live CD, but then the
"/bin/sh can&#8217;t access tty; job control mode off" comes up
I tried the solution involving changing the boot option to "quiet top break=top" 
from this website
[http://www.linuxquestions.org/questions/showthread.php?t=474493&page=3](http://www.linuxquestions.org/questions/showthread.php?t=474493&page=3)

still the computer continues loading but eventually goes into a blank screen with an underscore character flashing and nothing happens.

then I realized that my hardware might be too new so I downloaded a daily built of the new ubuntu Gusty (AMD 64 alternate CD) and popped that in.

after loading the text based installation process, an error pops up saying "no kernel modules were found", I ignored that error and continue on, then it says no internet interfaces were found... I continue on to partitioning the disk, 10% to /, 1GB swap, and the rest /home. but the the partition fails saying "an attempt to mount a file system failed", the / partition fails to mount.

I do not know what to do now... perhaps I should've downloaded the x86 version. However, my internet connection is quite slow and I would like to know how likely is that going to work if I download it. Also, should I get the daily built or tribe 5 release? or is there any solution to get the installation to work seeing these errors?

any help is appreciated.

---

### Post by leptons on 2007-09-11
I suspect that the issue is caused by the SATA harddrive... is there any potential solution for the problem?

---

### Post by leptons on 2007-09-11
a humble bump for my thread... I just want to install linux at the least so I can at least have a operating system to mess with. I've searching for hours with no real results for this problem...

---

### Post by ryanthegeek on 2007-09-12
O.K.  I have searched the forums many times.  This is my first post.  I also have the ms-1221 (got it the same day this post started).  

You need to download the alternate desktop cd.  You will see this option at the bottom of

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

 Start Download 

 Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.

I used Gparted to format the drive first.  Use the text base installer to get Ubuntu installed, I do not recall if I used the "break=top" work around or not.  X will crash before you are done (the video driver will fail).  After X crashes "sudo apt-get install xserver-xorg-video-intel".  Then type "sudo nano /etc/X11/xorg.conf" change vesa to intel.  Reboot, X should start.  

Sorry about the sloppy post, I just wanted to let you know it is possible to install ubuntu on th ms-1221.

---

### Post by h12o on 2007-11-11
If you are still bothered with the problem, try "all-generic-ide" kernel option.

1st, let the BIOS be disable AHCI.

2nd, If you find these lines in /boot/grub/menu.lst:
```
# kopt=root=UUID=********-****-****-****-************ ro
```
(hidden letters are your own disk UUID)

change, like this:
```
# kopt=root=UUID=********-****-****-****-************ ro all-generic-ide

```

---

