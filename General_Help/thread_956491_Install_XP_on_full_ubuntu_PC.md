---
title: "Install XP on full ubuntu PC"
date: 2008-10-23
forum: General Help
---

### Post by cespinal on 2008-10-23
Hey guys, need some help: 

I have an HP Dv9000 with ubuntu occupying my whole disk. I would like to make a small partition in order to install XP and play a couple of games I like..

how to proceed?

---

### Post by phidia on 2008-10-23
If you have adequate free space on your drive then you can use gparted (guide [here]("https://help.ubuntu.com/community/HowtoPartition?highlight=(gparted)")) to reclaim some of the drive for xp. 
You will need to reset up grub because xp will take over the bootloader/MBR. There's a wiki on that [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub").

Depending on what games you want to play you might just install [wine]("https://help.ubuntu.com/community/Wine") and get them working in that?

---

### Post by cespinal on 2008-10-23
I have tried wine on those games...it wont work :( 

thanks! I will try with super grub disk... seems quite simple

---

### Post by cespinal on 2008-10-24
done!... now I have XP but it cant for the hell of me make it surf the web... all this reminds me why im still loving ubuntu like the first day :D

---

### Post by cespinal on 2008-10-24
update... im still here downloading some drivers... its amazing how it takes a whole hour to get the video card drivers, while it only took a few minutes on ubuntu...

mmm besides all, Im loving google chrome despite I can not get it to run the flash plugin.. 

ok now to the point: I cant access to windows from de grub menu because it is not available!!!!... the only way to get into windows is navigating through the super grub cd!!... how can I place windows in grub so I dont need to boot from the super grub cd everytime I want to use windows?

---

### Post by caljohnsmith on 2008-10-24
If you can boot into Ubuntu OK still, then open a terminal (applications > accessories > terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And at the end of the file add:
```
title Windows XP
root (hd0,0)
chainloader +1
```
That assumes XP is on the first partition sda1, so if XP's instead on sda2, use (hd0,1), or sda3 use (hd0,2), etc. Let me know if that works. :)

---

### Post by cespinal on 2008-10-27
I guess it did not work :( now I have to use the super grub disk to load linux (and windows)...

---

### Post by caljohnsmith on 2008-10-27
Go ahead and use Super Grub to boot into Ubuntu, then open a terminal (Applications > Accessories > Terminal) and please post:
```
sudo fdisk -lu
sudo blkid -c /dev/null
cat /boot/grub/menu.lst
```
When you say it "does not work", what happens on start up? Do you get any Grub errors? Do you see the Grub menu? Please be specific.

---

### Post by cespinal on 2008-10-27
Sorry for not being specific

on startup, the system goes trough the bios stuff, and then, when it is suppossed grub to start, the screen just stays black with the tipical gray sub-dash blinking on the upper left corner :P

---

