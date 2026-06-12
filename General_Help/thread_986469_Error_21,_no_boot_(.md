---
title: "Error 21, no boot :("
date: 2008-11-18
forum: General Help
---

### Post by claymater on 2008-11-18
Ok so I have looked around ALLL DAYYYY to find a good answer to my "error 21 problem" and I really cant find anything to fix this... I was suspended in windows last night, this morning I tried to log in, and it didnt work, so I did a "dirty shutdown" (held down the button till it turned off) and when I booted up it gave me "Grub error 21" message. 

After seeing this I called my dad over, he looked at it, and we tried a few things out, we took the hard drive out (each one, I have 1 80GB(master) and 1 500GB(slave)) and on the "slave" HD is where all my ubuntu stuff was saved, we pluged both the HD's into another computer (one by one) and we got noting from my 500GB HD. Oh great, so it for one, won't boot up into either OS, 2 it cant see the 500GB HD. 

I loaded up my live CD, and I could see the 80GB, and could use all the files on it, but I still cant boot into windows (or ubuntu-without live CD-)


So does anyone know how to fix this? 

Thanks guys!

---

### Post by caljohnsmith on 2008-11-18
It sounds like part of the problem is that Grub is installed to the MBR (Master Boot Record) of your master HDD, while Grub's boot files are in the Ubuntu partition on your slave drive. If you can simply change your BIOS to boot the Ubuntu drive, then you can install Grub to the MBR of the slave drive and boot both Ubuntu and Windows from the slave drive. That way your drives will be independent of each other, and if you restore a Windows MBR to your master drive, you should be able to boot Windows again. If you keep your drives independent of each other in that manner, you shouldn't have a problem booting the Windows drive if something happens to the Ubuntu drive, like what you are experiencing now.

So while you have both HDDs connected, how about booting your Live CD, opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu

```
Let me know if you can set your BIOS to boot the slave drive, and we can work from there if you want. :)

---

### Post by claymater on 2008-11-18
> **caljohnsmith said:**
> It sounds like part of the problem is that Grub is installed to the MBR (Master Boot Record) of your master HDD, while Grub's boot files are in the Ubuntu partition on your slave drive. If you can simply change your BIOS to boot the Ubuntu drive, then you can install Grub to the MBR of the slave drive and boot both Ubuntu and Windows from the slave drive. That way your drives will be independent of each other, and if you restore a Windows MBR to your master drive, you should be able to boot Windows again. If you keep your drives independent of each other in that manner, you shouldn't have a problem booting the Windows drive if something happens to the Ubuntu drive, like what you are experiencing now.

So while you have both HDDs connected, how about booting your Live CD, opening a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu

```
Let me know if you can set your BIOS to boot the slave drive, and we can work from there if you want. :)

Well see the problem with fixing the MBR is that I cant see the slave drive (500GB) I can only see my master drive (80GB) but it wont boot for some reason because it cant see the slave drive D: 

Oh btw, the output of ```
sudo fdisk -lu

``` is 

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf3677250

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      112455   156232124    78059835    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


```

---

### Post by caljohnsmith on 2008-11-18
OK, I understand now. So if you want to get Windows booting again, you could boot your Windows Install CD, go to the "recovery console" and run:
```
fixmbr
```
And then Windows should boot again. If you don't have a Windows Install CD, you can instead do the following from your Ubuntu Live CD:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
And that will install a Windows MBR to sda, or the same thing as the "fixmbr" command. Let me know how it goes or if you run into problems.

---

