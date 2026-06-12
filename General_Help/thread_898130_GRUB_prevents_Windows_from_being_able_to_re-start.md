---
title: "GRUB prevents Windows from being able to re-start"
date: 2008-08-22
forum: General Help
---

### Post by cp1969 on 2008-08-22
Sorry if this has been covered.  I did a search but did not see anything.

One of my kids powered down the computer while running XP (it was locked up...imagine that).

Now, when I try to boot up to XP, I get the Windows screen that says "Windows  shut down abnormally....blah, blah....how do you want to re-start (safe mode, normal, etc.)

No matter which choice you make, it causes a restart of the computer which leads to....the GRUB boot screen.  Right back where I started.  Endless do-loop.

So, is there an easy fix?  If not, I'm not too disappointed.  This may be the time to sever the ties completely.

Thanks.

---

### Post by mb_webguy on 2008-08-22
If you're getting to the Windows boot options screen, the problem has nothing to do with GRUB.  Windows simply isn't booting properly.  You need to get your Windows installation disk, boot from it, and repair Windows.  This may possibly remove GRUB, so have your Ubuntu installation disk handy to repair GRUB if necessary.

---

### Post by cp1969 on 2008-08-22
I know there isn't a problem with GRUB...it's doing exactly what it's supposed to do.  What I need to do is bypass it--once--to restart Windows.  I may be wrong, but it seems to me that when you are at the Windows options screen, any of those choices initiates a re-boot, which then causes GRUB to run again, and it interrupts the boot process so the user can select which operating system he wants.

---

### Post by mb_webguy on 2008-08-22
I doubt it.  Selecting one of the options on the Windows boot options screen continues the boot process from that point.  If you're being bounced back to GRUB, it most likely means that Windows is simply failing to boot.

The only way to bypass the bootloader -- in this case GRUB -- is to use the BIOS boot options screen and boot from another source, such as the Windows installation disc.  If you choose to boot from the hard drive, it will always use whatever bootloader is installed on that drive.

---

### Post by caljohnsmith on 2008-08-23
> **mb_webguy said:**
> If you're being bounced back to GRUB, it most likely means that Windows is simply failing to boot.
+1. I agree with mb_webguy, but if you really want to prove to yourself whether it's a Grub problem, cp1969, you could temporarily reinstall the Windows MBR by running "fixmbr" in the recovery console from the Windows Install CD. I think you will see the same problem, but you can try if you want. Then when you are ready to put Grub back in the MBR, just boot your Live CD and do:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][will return the Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```

---

### Post by cp1969 on 2008-08-29
Apparently this is a somewhat common problem and has something to do with Linux and Windows residing on the same HDD.

[http://www.ozzu.com/mswindows-forum/won-boot-t73477.html](http://www.ozzu.com/mswindows-forum/won-boot-t73477.html)

edit:  Guess I forgot to mention that I, too, tried to boot XP from the CD but get the black screen.

---

### Post by Mgiacchetti on 2008-08-29
try this, at the windows choice selection screen, Disable automatic restart on system failure

this may give way to a bsod if it is the case.

another thing you can use to troubleshoot is to find out where it stops booting, 
safe mode will load on screen just as if you were to press ctrl alt f1 immediately after choosing a linux kernel in ubuntu.

make note where this process stops

---

### Post by cp1969 on 2008-08-30
It stops right after checking RAM (this is when I try to boot from HDD).  There is a brief message that says 'keyboard error' or something like that, then the GRUB screen immediately comes up.

---

### Post by caljohnsmith on 2008-08-30
> **cp1969 said:**
> It stops right after checking RAM (this is when I try to boot from HDD).  There is a brief message that says 'keyboard error' or something like that, then the GRUB screen immediately comes up.
So are you still able to use Ubuntu on that HDD OK? If you can, then that would make a hardware problem unlikely, and that leaves Windows as the problem. I would take mb_webguy's advice and do a "Windows repair". Just boot your Windows Install CD, and it will give you the option to "repair" an existing Windows installation. Let us know how it goes or if you need more info/details.

---

### Post by gatenby_jp on 2008-08-30
I think he is dealing with a standard windows problem rather than a grub issue ... the only thing that concerns is the keyboard error which sounds like it is a bios message. 

If it is a windows problem he should either boot in windows safe mode ... go to my computer ... right click on local disk c:drive ... select properties then tools then check drive for errors tick both tick boxes select run ... when it says needs exclusive access must it schedule for after a reboot say yes then reboot and try load windows again ... 
alternately boot with the windows install disk and on the first screen choose r for repair and run the following command chkdsk /p ... he will probably get a end result saying chkdsk found some errors ... if so he must run the command repeatedly until it does not report errors

if he runs fixmbr ... he must reinstall grub to mbr afterwards

---

### Post by cp1969 on 2008-08-30
> **caljohnsmith said:**
> So are you still able to use Ubuntu on that HDD OK? If you can, then that would make a hardware problem unlikely, and that leaves Windows as the problem. I would take mb_webguy's advice and do a "Windows repair". Just boot your Windows Install CD, and it will give you the option to "repair" an existing Windows installation. Let us know how it goes or if you need more info/details.

Yes, Ubuntu is fine, which is a good thing or I would not be able to post here.

I can't boot from the Windows CD.  I get to the point where it says to 'press any key to boot from CD', which I do, but get nothing but a dark screen.

---

### Post by cp1969 on 2008-08-30
> **gatenby_jp said:**
> I think he is dealing with a standard windows problem rather than a grub issue ... the only thing that concerns is the keyboard error which sounds like it is a bios message. 

If it is a windows problem he should either boot in windows safe mode ... go to my computer ... right click on local disk c:drive ... select properties then tools then check drive for errors tick both tick boxes select run ... when it says needs exclusive access must it schedule for after a reboot say yes then reboot and try load windows again ... 
alternately boot with the windows install disk and on the first screen choose r for repair and run the following command chkdsk /p ... he will probably get a end result saying chkdsk found some errors ... if so he must run the command repeatedly until it does not report errors

if he runs fixmbr ... he must reinstall grub to mbr afterwards

There is no booting in safe mode.  If I try to do that from the Windows whatchamacallit screen that appears immediately after selecting 'Windows' in GRUB, all I get is a return to the GRUB options screen.

I can't boot Windows from the CD.  It goes as far as checking the RAM, then a brief 'keyboard error' message appears, then......nothing.

In the link I posted above, many people have experienced this same problem.  I can view the files in the Windows partition and everything appears to be there; however in the Windows folder I notice a BUNCH (at least a hundred) of folders labeled "$NtUninstalKB941568$".  The only thing that varies in the title of these folders is the number of digits following the "KB".  I *think* that these may be the result of installing SP2.

This isn't a very old installation of XP--it was installed on a new hard drive, along with ubuntu, last November.

---

### Post by caljohnsmith on 2008-08-30
I remember reading in another linux forum about someone who couldn't boot their Windows CD, and it turned out to be a problem with the Windows CD having issues with the other linux partitions on the HDD. The solution was actually quite simple, and you've got nothing to lose by trying it.

All you need to do is temporarily "hide" your Ubuntu partition, so first you'll need to know which Grub (hdX,Y) partition it is. If you don't all ready know, then on start up, when you get the Grub menu, highlight your Ubuntu entry and press "e" to edit it. It will show a line "root (hdX,Y)", and that is the (hdX,Y) you need. Hit "ESC" to go back to the menu, hit "C" to go into the Grub CLI, and then do:
```
grub> hide (hdX,Y)
```
Next put in your Windows CD, and from the Grub CLI:
```
grub> reboot
```
Hopefully your Windows CD will work now. When you are ready to get Ubuntu back, just go back to the Grub CLI again and use:
```
grub> unhide (hdX,Y)
```
Let me know how it goes.

---

### Post by cp1969 on 2008-08-30
It didn't.  Now I can't even boot ubuntu.  

Windows did not boot and now I get error 17 on Grub.

---

### Post by caljohnsmith on 2008-08-30
OK, sorry it didn't work for you; did you then "unhide" the Ubuntu partition as I gave in my previous post? That should be all you need to do to boot back into Ubuntu.

---

### Post by cp1969 on 2008-08-30
I can't get to a position in which to exercise the unhide command.
The grub screen doesn't come up; all I get is the grub 17 error message.  I've got it booted using the unbuntu cd right now but am posting this from another computer.

---

### Post by cp1969 on 2008-08-30
Should have mentioned that after booting with the ubuntu CD, I was able to get the line

grub>

Then I iput the command

grub> unhide (hd0,3)

and got the message:  

Error 27: Selected disk does not exist

---

### Post by caljohnsmith on 2008-08-30
From the Live CD, did you get into the Grub CLI by doing:
```
sudo grub
```
Because if you just type "grub", you can get errors like you got.

---

### Post by cp1969 on 2008-08-30
I'm at the point where ubuntu has returned the prompt

grub>

That is up on the screen; I didn't type it.  I can then hit the TAB key and see what commands are available.

---

### Post by caljohnsmith on 2008-08-30
You should be able to do it fine from the Live CD. Just open a terminal, and do:
```
sudo grub
grub> unhide (hd0,3)
grub> quit
```
If for some reason that doesn't work for you, from the Live CD run gparted:
```
gksudo gparted
```
Right-click the Ubuntu partition, select "manage flags" and uncheck the "hidden" one. Apply changes, quit.

---

### Post by cp1969 on 2008-08-30
That got me back to where I can at least boot into ubuntu.

---

### Post by caljohnsmith on 2008-08-30
One more check--if you do:
```
sudo fdisk -lu
```
Does it show only one partition as bootable, and is that partition Windows? (i.e. the asterisk next to the Windows partition)?

---

### Post by cp1969 on 2008-08-30
> **caljohnsmith said:**
> One more check--if you do:
```
sudo fdisk -lu
```
Does it show only one partition as bootable, and is that partition Windows? (i.e. the asterisk next to the Windows partition)?

I am not sure what I'm looking at.

the asterisk is by the one labeled /dev/sda1.  also under 'system' it says this is HPFS/NTFS.  there are 8 such devices, 1 thru 8.    there is no asterisk by any of the three windows devices.

Then there is a message that says Partition table entries are not in disk order.

Then, it lists another device, /dev/sdb1 and there is an asterisk by it.

---

### Post by cp1969 on 2008-08-30
OK...here's an interesting(?) wrinkle.

This machine has two hard drives.  When I installed ubuntu, I bought a new hard drive and installed ubuntu and XP on it in separate partitions.

The old drive, which held XP and ME, had crashed due to, I think, Macafee or Spybot.  At any rate, it was unbootable.

Now, I can unplug the power from **either **hard drive and boot up into...ubuntu.  I would have expected the new drive to do that, but not the old one.

How did this happen?  I never installed ubuntu on that old drive.

---

### Post by gatenby_jp on 2008-08-30
unplug the old drive from system ... then post results from sudo fdisk -lu

you could also try polishing the windows cd with a soft cloth and retry booting with it ... seems that pc is not able to read the boot from windows cd ...

---

### Post by cp1969 on 2008-08-31
cep@cep-desktop:~$ sudo fdisk -lu
[sudo] password for cep:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x12041203

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41736869    20868403+   7  HPFS/NTFS
/dev/sda2        80148285   247609844    83730780    f  W95 Ext'd (LBA)
/dev/sda3       247609845   312576704    32483430   83  Linux
/dev/sda4        41736870    80148284    19205707+  83  Linux
/dev/sda5        81915498   163830869    40957686    e  W95 FAT16 (LBA)
/dev/sda6       163830933   245746304    40957686    e  W95 FAT16 (LBA)
/dev/sda7       245746368   247609844      931738+  82  Linux swap / Solaris
/dev/sda8        80148411    81915434      883512   82  Linux swap / Solaris

Partition table entries are not in disk order
cep@cep-desktop:~$

---

### Post by cp1969 on 2008-09-07
TTT

Anyone?

---

