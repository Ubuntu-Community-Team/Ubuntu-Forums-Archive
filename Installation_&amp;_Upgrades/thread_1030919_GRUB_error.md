---
title: "GRUB error"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by SoxFan on 2009-01-04
I attempted to install ubuntu studio (64 bit) on my Compaq Presario laptop and dual boot with WinXP.  The install didn't complete and not the computer will not boor (GRUB Error 17).

I made a full recovery CD set just before attempting this using the installed application that came with the machine.  When I was unable to boot I attempted to restore only to get a message "These PC Recovery discs do NOT support this PC model"  I have a post on the HP/Compaq forum to reslove.  When this failed I used a ubuntu 8.10 live CD and successfully booted from that CD.  I have been able to search the files on the hard drive but don't know where to start to repair the problem.  I did search for the menu.lst file to see what boot sequence I could find but I couldn't find that file anywhere.  I had to alter this file on a different machine and thought it might be the source of my issue.

Any help would be greatly appreciated.

---

### Post by caljohnsmith on 2009-01-04
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. If you don't have internet connectivity when using the Live CD, you can instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then do the following in a terminal:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by SoxFan on 2009-01-05
I found a Super GRUB .iso and made a CD to boot from.  Using it I was able to restore the proper boot sequence and got the machine back to running WinXP.  I will continue to work with it and the suggestions sent by caljohnsmith while I attempt to increase my knowledge of ubuntu.

Thanks.:KS

---

### Post by knguyen144 on 2009-01-05
> **SoxFan said:**
> I found a Super GRUB .iso and made a CD to boot from.  Using it I was able to restore the proper boot sequence and got the machine back to running WinXP.  I will continue to work with it and the suggestions sent by caljohnsmith while I attempt to increase my knowledge of ubuntu.

Thanks.:KS

I got into the same situation you had, I am using SuperGrub CD, it helped to boot into Window XP (with the CD). I could not figure out how to set my machine boot straight from harddisk.
Could you please help me with  step-by-step instructions ?
I am confused with the Super Grub Menu.
It seems my Ubuntu partition was wiped out, I can't use Super Grub to fix the Linux Boot any more. Perhaps, I should re-install Ubuntu again.

---

### Post by Pumalite on 2009-01-05
If you can boot a Live CD; post:
sudo fdisk -lu
(to see how many drives and the state of your partitions. Once that is Clear you can install Ubuntu on top os the ols partition.)

---

### Post by SoxFan on 2009-01-06
> **knguyen144 said:**
> I got into the same situation you had, I am using SuperGrub CD, it helped to boot into Window XP (with the CD). I could not figure out how to set my machine boot straight from harddisk.
Could you please help me with  step-by-step instructions ?
I am confused with the Super Grub Menu.
It seems my Ubuntu partition was wiped out, I can't use Super Grub to fix the Linux Boot any more. Perhaps, I should re-install Ubuntu again.

I selected 

WIN => MBR & !WIN!

It allowed the PC to boot to WinXP.  Once that is done the PC booted to WinXP from the hard drive.  The ubuntu boot was no longer functional and it requred me to re-install ubuntu studio but at lease it was recoverable.

Hope that helps.......

---

