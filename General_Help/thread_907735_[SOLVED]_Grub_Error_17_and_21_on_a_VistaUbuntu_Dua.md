---
title: "[SOLVED] Grub Error 17 and 21 on a Vista/Ubuntu Dual-Boot"
date: 2008-09-01
forum: General Help
---

### Post by steerguy on 2008-09-01
I have Vista x64 on 2x400gb drives in a software raid 0. I couldn't get Ubuntu to work with the raid so I put in an independent 250gb drive that has only Ubuntu on it.

After installing Ubuntu 8.04 x64, I spent some time customizing it and what have you, plenty of reboots in the process and it went fine. However, I decided I wanted to go play some games on my Vista boot. Vista wasn't on the grub for Ubuntu, presumably because it's on a different drive. So I changed the order of the drives in the bios so the Vista drive would be loaded first. This gave me error 21.

I thought that maybe I could just remove the 250gb drive and I'd be back to normal but this gave some other grub error. So, I put it back in and tried to boot into Ubuntu again and was given error 17. Now I can't access either drive and I'm running off the live CD.

How do I fix it?

---

### Post by caljohnsmith on 2008-09-01
Sounds like what happened is you accidentally installed Grub to the master boot record (MBR) of your Vista HDD; when you try and boot your Vista HDD, your HDD order has changed, so Grub can't find its system files and gives an error 21. 

Anyway, the solution for that problem is to reinstall the Vista MBR to the Vista HDD. But instead of reinstalling the Vista MBR per se, I'm going to give you an easy method that should work from Ubuntu. First download and install the package "ms-sys":
```
sudo apt-get install ms-sys
```
Next, figure out which is your Vista HDD:
```
sudo fdisk -lu
```
Look for the "NTFS" under "system" for it to be a Windows partition. Also, make sure the Vista partition has an asterisk * in the boot category. If it doesn't let me know. Once you're sure you know which is your Vista HDD in the form "/dev/sdX" (where X is a, b, or c), then do the following command:
```
sudo ms-sys -m /dev/sdX
```
So sdX would be sdb if that is the HDD Vista is on. Give that a try and let me know how it goes.

---

### Post by steerguy on 2008-09-01
> ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys

I enabled the universe and multiverse depositories. Do I need to add one to get the file? Or maybe the live cd just doesn't have all the sources the full isntall does.

---

### Post by caljohnsmith on 2008-09-01
My mistake, I forgot that package is not in the standard repositories. Just download the package from [this link]("http://debian.oregonstate.edu/debian/pool/main/m/ms-sys/ms-sys_2.1.0-1_i386.deb"). If you save that package to your Desktop, you can install it with:
```
cd ~/Desktop
sudo dpkg -i ms-sys*.deb
```

---

### Post by steerguy on 2008-09-01
That's the i386 version, I need the amd64, terminal gave an error.
Edit- nevermind, chagned i386 to amd64 in the file name, testing...

---

### Post by steerguy on 2008-09-01
This is the result of fdisk:
> Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbc8f5a39

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   102402047    51200000    7  HPFS/NTFS
/dev/sda2       102402048  1358032887   627815420    7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x574a6170

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   781420543   390709248    6  FAT16

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3fd03fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63     9687194     4843566    7  HPFS/NTFS
/dev/sdc2         9687195   488392064   239352435    5  Extended
/dev/sdc5         9687258   468905219   229608981   83  Linux
/dev/sdc6       468905283   488392064     9743391   82  Linux swap / Solaris

I don't think it's picking up my fake raid 0 drives correctly. I'm also not sure what the fat16 space is from.

---

### Post by caljohnsmith on 2008-09-01
It looks like your Vista is on sda. Therefore, try the following:
```
sudo ms-sys -m /dev/sda
```

---

### Post by steerguy on 2008-09-01
> **caljohnsmith said:**
> It looks like your Vista is on sda. Therefore, try the following:
```
sudo ms-sys -m /dev/sda
```

It returned:
Windows 2000/XP/2003 master boot record successfully written to /dev/sda
Do I reboot now to see how it works? Is it ok that Vista isn't listed in the type of boot record?

---

### Post by caljohnsmith on 2008-09-01
Yes, reboot and see if it works; make sure the Vista HDD is the first in the BIOS boot order.

---

### Post by steerguy on 2008-09-01
> **caljohnsmith said:**
> Yes, reboot and see if it works; make sure the Vista HDD is the first in the BIOS boot order.

It works, I'm in vista now! You're my hero!
Now, is it possible for me to ever use my Ubuntu installation again and how do I go about doing that?

---

### Post by caljohnsmith on 2008-09-01
> **steerguy said:**
> It works, I'm in vista now! You're my hero!
Now, is it possible for me to ever use my Ubuntu installation again and how do I go about doing that?
Your Ubuntu HDD is untouched, so you should be able to just set your Ubuntu HDD back as the first to boot in BIOS and then boot Ubuntu fine. But as a better solution to your overall problem, I propose we just add Vista as an entry in your Grub's menu.lst, so then you don't have to change your BIOS settings every time you want to boot Vista vs. Ubuntu. Sound like a plan?

If that sounds good to you, then go ahead and boot Ubuntu, and then post the output of:
```
cat /boot/grub/menu.lst
```

---

### Post by steerguy on 2008-09-01
> **caljohnsmith said:**
> Your Ubuntu HDD is untouched, so you should be able to just set your Ubuntu HDD back as the first to boot in BIOS and then boot Ubuntu fine. But as a better solution to your overall problem, I propose we just add Vista as an entry in your Grub's menu.lst, so then you don't have to change your BIOS settings every time you want to boot Vista vs. Ubuntu. Sound like a plan?

If that sounds good to you, then go ahead and boot Ubuntu, and then post the output of:
```
cat /boot/grub/menu.lst
```

I still get Grub error 17 from that drive

---

### Post by caljohnsmith on 2008-09-02
> **steerguy said:**
> I still get Grub error 17 from that drive
OK, most likely that is an easy problem to fix. Boot your Live CD and do the following commands:
```
sudo grub
grub> find /boot/grub/stage2
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
If you get any errors, let me know. Otherwise, make sure your Ubuntu HDD is now first in the BIOS boot order, and reboot. You should get the Grub menu again if all goes well. Let me know how it goes.

---

### Post by steerguy on 2008-09-02
Looks good so far, about to reboot, here's what the response from the last code was:
> grub> root (hd2,4)
root (hd2,4)
grub> setup (hd2)
setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+16 p (hd2,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.


---

### Post by steerguy on 2008-09-02
I'm getting error 21 on the Ubuntu drive now. That's progress, right? What happens is the grub loader goes through it's count down, then gives me the error. It then goes to the grub menu of choices (4 ubuntu options and a memtest), picking any of the Ubuntu's results in error 21.

---

### Post by caljohnsmith on 2008-09-02
> **steerguy said:**
> I'm getting error 21 on the Ubuntu drive now. That's progress, right? What happens is the grub loader goes through it's count down, then gives me the error. It then goes to the grub menu of choices (4 ubuntu options and a memtest), picking any of the Ubuntu's results in error 21.
Yes, that's definitely progress. :) That means Grub can find all its system files OK now (including menu.lst), but we need to correct your Grub menu entries for Ubuntu. Your main Ubuntu install is on sdc5, so try this:
[LIST=1]
[*]Reboot, and when you get the grub menu, select the first Ubuntu entry with your up/down arrow keys, and hit "e".
[*]Next use the arrow keys to select the "root (hdX,Y)" line, and hit "e" again.
[*]Modify that line to read "root (hd0,4)", hit return to save, and then press "b" to boot. If all goes well you should be able to boot Ubuntu.
[/LIST] 
If that works you then need to modify your /boot/grub/menu.lst so that the change is permanent, and you can do that with:
```
gksudo gedit /boot/grub/menu.lst
```
And then we can work on booting Windows. Let me know if you run into any trouble with doing the above.

---

### Post by steerguy on 2008-09-02
Ok, I changed all the 2's to 0's in menu.lst and saved. Here's what it looks like now:
> 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ae747b0a-5775-4c86-a433-a246ea415708 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ae747b0a-5775-4c86-a433-a246ea415708 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ae747b0a-5775-4c86-a433-a246ea415708 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ae747b0a-5775-4c86-a433-a246ea415708 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
Also, I'm leaving for school right now and I won't be back until around 5:15 EST so it'll be a while for my next reply.

---

### Post by caljohnsmith on 2008-09-02
OK, glad the Ubuntu entries worked for you. Since you have two other HDDs and Grub sometimes sees the order of HDDs different then how BIOS sees them, you'll have to try two different entries in your menu.lst for Vista. Add both of the following, and one of them should work; and of course once you know which one works, you can delete the other one:
```
title Windows Vista (hd1)
root (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title Windows Vista (hd2)
root (hd2,0)
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Give that shot and let me know how it goes.

---

### Post by steerguy on 2008-09-02
Awesome, it was HD1. I really appreciate all your help in fixing this. I was afriad I'd lost both OS's I'd spent 2 days setting up.

---

### Post by caljohnsmith on 2008-09-02
> **steerguy said:**
> Awesome, it was HD1. I really appreciate all your help in fixing this. I was afriad I'd lost both OS's I'd spent 2 days setting up.
You're welcome, and I'm glad everything is working for you again. :) If it's not too much trouble, it would be good if you can go to the top of the thread where it says "thread tools", click it, and select "solved". That will help others in the future who do a search on the same type of issue.

---

