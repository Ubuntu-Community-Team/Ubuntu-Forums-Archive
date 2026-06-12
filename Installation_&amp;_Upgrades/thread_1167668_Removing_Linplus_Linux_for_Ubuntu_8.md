---
title: "Removing Linplus Linux for Ubuntu 8"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by udey on 2009-05-23
Hi,

I have downloaded the Ubuntu 8.04 LTS Desktop for 64 bit and it always goes into error.

I have a new Acer notebook Intel Core 2 Duo, 160 GBHDD, 2 GB RAM
No software except for Linplus OS is pre-installed

**Since Linplus Linux is already installed** - could that be the reason why Ubuntu can't start installation.

I don't get a GUI Menu after the Language and "Install" options are selected - after these 2 steps it goes into 
* Loading Kernel
* Busybox v.1.1.3
* (initramfs) [  39.799278] ata2.00: revalidation failed (error=-5)
* [  39.825696] ata2: exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0 t4
* [   39.825736] ata2: irq_stat 0x40000008



Downloaded from the website:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Really frustrating as no website on the entire net can suggest how to uninstall Linplus or any Linux OS except for buying a Windows XP CD and then using that to format the HDD.

:(

At wits end with it - any solution to this error ?

Best Wishes,
Ujjwal Dey

---

### Post by zvacet on 2009-05-23
Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") an d after burning [CD integrity check?]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")If all is O.K. you can install Ubuntu.What kind of error do you get when you try to install?And,yes you can install Ubuntu if you already have OS.You can dual boot two linux distros or you can delete preinstalled one and install Ubuntu.

---

### Post by udey on 2009-05-23
Hi yes, I did the md5 sum and the CD works on my Windows Desktop PC and prompts me to install Ubuntu within Windows.

But on the Linplus OS Notebook the CD boots and goes through the menus to get the mentioned errors in first  post - the same errors appear again and again in Busy box - See first post.

I want to completely remove Linplus linux and install Ubuntu 8.04

---

### Post by udey on 2009-05-23
The error faced by TanaT at below link

is the closest thing to my error I could find on the net.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635)


And I am not able to access "cd /boot/grub" nor the Terminal from the 
Busybox (initramfs) 

Damn!

---

### Post by udey on 2009-05-23
Hi,

Also found this thread.
[http://ubuntuforums.org/showthread.php?t=804713](http://ubuntuforums.org/showthread.php?t=804713)

I have similar problem with everything halting at "initramfs" in the Busybox .

But don't know :
1. how I can select to install only Wubi.exe
2. or how I can access Terminal at "intramfs" to change "menu.lst"

](*,):confused: :(

Didn't think it would this complicated.

---

### Post by udey on 2009-05-23
Hello Friends,

Has no one else experienced this with their Notebook/ Laptop ?


Damn Acer has loaded a useless DOS-type Linplus, not even the GUI one which I would have resigned to use happily after all this.

:(

---

### Post by udey on 2009-05-24
OK, gave up on 8.04

The Ubuntu 9.04 version for 64 bit got installed - like eating cake - so simple.

):P  :D :popcorn: \\:D/ :lol:=D>


Well, that certainly shows its a worthy upgrade and more universal than the 8.04

WOW !!!

**FINALLY I GOT UBUNTU !!!**


Now I have to get Bluettoth, Webcam to work - just pooint me to relevant thread.

Also MP3/ DVD/ VCD etc won't play in its Media player - so need to get online for that.

Thanks for all those who tried.

Best Wishes,
UD

---

### Post by zvacet on 2009-05-24
> Also MP3/ DVD/ VCD etc won't play in its Media player - so need to get online for that.

Type in terminal

```
sudo apt-get install ubuntu-restricted-extras
```

and add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to your source list.

---

