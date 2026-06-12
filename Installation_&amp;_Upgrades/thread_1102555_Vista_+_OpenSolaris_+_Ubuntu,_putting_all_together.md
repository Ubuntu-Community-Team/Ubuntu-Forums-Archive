---
title: "Vista + OpenSolaris + Ubuntu, putting all together"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by giscardf on 2009-03-21
Hi guys,

I am trying to do something that was supposed to be simple...;)

I did install Windows Vista
After that I did Install OpenSolaris
And at the end the Ubuntu.

So, I did edit the grub menu.lst file

The vista was point to (hd0,0)
The Solaris was point to (hd0,1)
The Ubuntu was point to some specific vmz loader...

So when the computer start I can use both solaris and ubuntu, however when I try to pick up the vista I got the message

Error 13 : Invalid or unsupported executable format

Do your guys have any idea on how to fix that?

Thanks and Regards

---

### Post by tommcd on 2009-03-21
Post the output of:
```
sudo fdisk -l
```
This will list your partitions. 
Also post the Vista entry from your /boot/grub/menu.lst file. If Vista is installed to the 1st partition of the drive, as you indicated with (hd0,0), then the entry for Vista in menu.lst should look like:
```

title Microsoft Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1
```
Also, Windows should be on a primary partition; and it should be the 1st partition on the drive.
And welcome to the Ubuntu forums!

---

### Post by giscardf on 2009-03-21
Well, sorry for the delay...

I was reinstalling everything again.... At this time I did

Install Windows
Install Solaris
Install Ubuntu

after all, now is solaris whom does not start by the grub
Below is the output for sudo fdisk -l
/dev/sda1 ... HPFD/NTFD (Windows Vista)
/dev/sda2 ... Linux     (Ubuntu)
/dev/sda3 ... Extended  (Ubuntu Swap)
/dev/sda4 ... Linux Swap (Solaris)
/dev/sda5 ... Linux Swap (Soalris)

my menu.lst is
title Windows Vista
root (hd0,0)
savedefault
makeactive 
chainloader +1

title OpenSolaris
root (hd0,2)
chainloader +1

Hope this can help you to help me...

Thanks

---

### Post by tommcd on 2009-03-22
> **giscardf said:**
> 
after all, now is solaris whom does not start by the grub
Below is the output for sudo fdisk -l
/dev/sda1 ... HPFD/NTFD (Windows Vista)
/dev/sda2 ... Linux     (Ubuntu)
/dev/sda3 ... Extended  (Ubuntu Swap)
/dev/sda4 ... Linux Swap (Solaris)
/dev/sda5 ... Linux Swap (Soalris)


The extended partition /dev/sda3 is not swap. An extended partition contains the logical partitions /dev/sda4 and /dev/sda5 in your setup. Which partition is Solaris, /dev/sda4 or /dev/sda5? Please post the entire output of **sudo fdisk -l**.

I don't know anything about Solaris since I have never used it. A quick google search reveals that you can chainload Solaris similar to Windows. See these:
[http://www.linuxquestions.org/questions/solaris-opensolaris-20/how-to-use-grub-to-boot-the-triple-os-windowslinuxsolaris-298718/](http://www.linuxquestions.org/questions/solaris-opensolaris-20/how-to-use-grub-to-boot-the-triple-os-windowslinuxsolaris-298718/)
[http://www.bolthole.com/solaris/grub.html](http://www.bolthole.com/solaris/grub.html)
Edit you grub menu.lst and add the entry for Solaris like in those examples. Change the partition number (hdX,Y) to match your Solaris partition. Backup your menu.lst first for safety.

---

### Post by giscardf on 2009-03-22
Hi guys,

Well, thanks for all the responses... I did find out the problem. So here we go a explanation for whom try to do the same thing.

First of All:
Solaris does delete ubuntu grub configuration. So the best way to do all the things is install Windows, so Solaris and So Ubuntu

How to do that:
1. Using the windows create only the windows parition (let all remaining disk free) and install windows on it
2. Using the Ubuntu live CD create Solaris partition (it shall be configured as swap). Let all remaining disk free
3. Install Solaris
4. Using the Ubunty live CD create the Ubuntu partitions (main partition using ext3 and a swap partition using swap) (*please read CAUTION below).
5. Install Ubuntu
6. Edit grub file to include new Solaris
title OpenSolaris
rootnoverify (hdx,y)
savedefault
makeactive
chainloader +1

CAUTION: On step 4 you have to edit the solaris partition by setting it as "do not use this parition" Otherwise UBUNTU will format the solaris partition. That was my mistake, and that was why Solaris could not be started by grub.

Just to summarize. There is not problem with grub. The only "problem" is that Ubuntu format all swap partitions when it is installed, and hence Solaris10 is saw by Ubuntu was a swap partition it was been formated. When you set this parition to not be used and install ubuntu, it will not touch it.

Thanks all and regards

---

### Post by tommcd on 2009-03-22
Interesting. I was wondering why you had 2 partitions identified as swap in your last post. I did not know that Ubuntu would recognize a Solaris root partition as swap.

---

