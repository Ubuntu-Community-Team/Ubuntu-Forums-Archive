---
title: "grub keeps restarting when i select windows xp"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by Battlenus on 2009-01-15
windows was working before but now it just restarts. the last thing that i did in windows was pressing the shut down button before it did a shut down update.

is there anyway that the windows xp disk can repair the startup?
or can a window vista disk can repair a windows xp startup?

thanks for the help

---

### Post by fenario on 2009-01-16
I have the same problem.
After connecting a second hdd to my computer as an additional storage disk my grub didn't work any longer.
I tried the sudo grub, root (hd0,6), setup (hd0) method; didn't work
so I installed another linux with grub.
all my 5 linux partitions work ok but when i click on windoes xp
it opens a previuos "dead" grub menu
clicking on XP there it just loops back into that 2nd grub menu again.
the windows partition is not recognized by ubuntu nor the other distros though gparted shows it.

i'm afraid of stuffing things up even more and loosing my penguins.
what can I do?

---

### Post by rMatey on 2009-01-18
Hi!  Just working thru my own similar problem.  I was working with XP pro on a different SATA disk (primary) and have 8.10 on the second disk.  Anyway, while I'm working on a repair for which I need some more input on fixing the corrupted file that loads an old 8.04 grub one.

   You can find a Super Grub Disk and use the boot Linux Directly option to get your penguin system back up and running.  I tried to use the built-in Startup Manager to correct the problem, but Grub keeps finding the incorrect one.  Why XP Pro does work is a question.... but it can't find the penquin one.

   Hey guys, does anyone know how to correct a corrupted boot list and startup1 folder.  I think thats the problem.  Maybe we need to remove Grub and then re-enable it.

---

### Post by caljohnsmith on 2009-01-18
Fenario, it sounds like your problem might be that you at some point accidentally installed Grub to the boot sector of your Windows partition. If that's the problem, to fix it boot your Windows Install CD, go to the "recovery console" and do:
```
fixboot
```
And then try booting Windows again. If that doesn't work, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by rMatey on 2009-01-18
I got mine fixed.  What happened to me was that I updated some Winder$ drivers, and got a corrupted XP.  I think it did something to the GRUB because it always reported a File Not Found.  
  I unplugged the drive with Ubuntu and rebooted XP in safe mode, used last good boot.  Then I messed around with Grub, but didn't find anything...
  I guess in my checking I swapped the boot.... its a long story. D/A!!!!!

  I fixed it by reinstalling the Windows Boot on the Windows drive, sans the Linux sata 2.   I then fixed the Ubuntu sans the Windows drive.  Then I reinstalled Grub with the Super Grub disk on the Sata 1 with the Ubuntu on it, and the Sata with XP on the second drive.


   It works like it did before all of the messing around!  :)

 (Note To Self:  watch what plug goes where.  Don't update XP drivers without being really sure that they won't trash install. Just because they say they are updates, they all don't work.. unlike Ubuntu.)

:P

---

### Post by fenario on 2009-02-01
Thanks CalJohn :D; I got mine fixed now with: **fixboot C:** at the windows repair/recovery console. Somebody suggested to add the C: as well after fixboot.

That saved me from installing the whole lot again and this after a brand new install with all my fav programs, java, .net, flash, gtk, dx10, and beyond SP3; which is the better part of a day you saved me. I spent that on Ubuntu instead.

You were right; I did install grub on hd0,0 instead of hd0 only,
I installed it later to hd0 but only my 8 linux partitions worked.
when I added a second hard drive the sequence of sda1, sda2, etc got stuffed up too. It does funny things to Windows as well; it used the new hdd to record system restore folders. In Vista you can choose where to place them. In XP? Dunno. Thanks for responding. Good on you!

fixboot

---

### Post by caljohnsmith on 2009-02-01
Glad to hear fixboot is all it took to solve your problem, fenario. Cheers and enjoy all your OSes. :)

---

