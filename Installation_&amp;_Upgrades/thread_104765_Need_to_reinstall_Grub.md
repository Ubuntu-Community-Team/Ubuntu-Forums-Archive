---
title: "Need to reinstall Grub"
date: 2005-12-16
forum: Installation &amp; Upgrades
---

### Post by VirtualMe on 2005-12-16
Hi all.  I have a dual boot with Ubuntu and Windows XP.  I reinstalled XP without thinking, which destroyed Grub.  Is there any way to reinstall Grub and be able to boot into Ubuntu again, or should I just reinstall Ubuntu?  Thanks for your help!

---

### Post by Sutekh on 2005-12-16
There is a Wiki page just for this case

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

You'll need a LiveCD to try this.

---

### Post by VirtualMe on 2005-12-16
Thanks Sutekh.  Looks just like what I need.  Good thing I downloaded the Live CD to try Ubuntu before I downloaded the install CD.  I will give the instructions a whirl.

---

### Post by Sutekh on 2005-12-16
Excellent, always a good idea to have a LiveCD around, they can be very helpful.  Make sure that you understand the instructions, if you need clarification just ask.

---

### Post by VirtualMe on 2005-12-16
Okay, after multiple reloads of the Live CD, I got somwhere.
I followed the instructions, and I think I got the right hda1, hda2, mounted to the right places.
However when I try to do "/sbin/grub-install /dev/hda" it says "Read-only file system".
What now?  Could it be because my windows partition is formatted as NTFS?

---

### Post by Cuppa-Chino on 2005-12-17
slightly different problem for me: 
after mucho-frustrations with Breezy I was going to try a different Linux and that install did not work but it did alter GRUB how can I safely 

* change grub back to the original (yes :oops: forgot to do a proper backup)

I can still boot into Breezy and XP and they are still on the list just want to not blow grub completely out of the water....

---

### Post by VirtualMe on 2005-12-18
Hi Cuppa-Chino.  I certainly don't know much about this yet, but could you just manually fix menu.lst?  I guess that would depend on how messed up it is.

Does anyone else have any ideas what I could do to fix my problem?  My poor computer has just been sitting there for a whole day doing nothing now.  Someone needs to help it!  :p :)

---

### Post by az on 2005-12-18
[QUOTE=VirtualMe]Okay, after multiple reloads of the Live CD, I got somwhere.
I followed the instructions, and I think I got the right hda1, hda2, mounted to the right places.
However when I try to do "/sbin/grub-install /dev/hda" it says "Read-only file system".
What now?  Could it be because my windows partition is formatted as NTFS?[/QUOTE]

Since breezy, the installer cd has a rescue mode.  Type rescue after you boot the installer and hit enter.

Boot into it and it will go through the steps as normal (detecting your hardware)  the last step will ask you which partition to chroot into.  Pick your ubuntu install and at the shell, run

grub-install /dev/hda

The live cd probably mounts it read-only , where in rescue mode it is readwrite.


The live cd is fun to have, but it is not indespensable.

---

### Post by az on 2005-12-18
[QUOTE=Cuppa-Chino]slightly different problem for me: 
after mucho-frustrations with Breezy I was going to try a different Linux and that install did not work but it did alter GRUB how can I safely 

* change grub back to the original (yes :oops: forgot to do a proper backup)

I can still boot into Breezy and XP and they are still on the list just want to not blow grub completely out of the water....[/QUOTE]
So, this other distribution created it's own partition and installed it's own grub?

Boot into rescue mode as just described and pick your ubuntu install.  Run install-grub, too.  That will install the grub from ubuntu with it's config (without the distribution you made last.  Since you are still able to boot into Ubuntu, you probably created the new partiton on another disk, of after the other partitions since the partition names have not changed (and you would not be able to boot ubuntu if it thinks it is on another partition)

---

### Post by Cuppa-Chino on 2005-12-18
thanks azz ...

actually just (about 45mins ago) solved the problem by "brutally" running an install from the Breezy disk and going through the motions without formatting the root drive (just changed from dev/sda3 back to root) and the forcing the installation to install GRUB

the installation programm squeeked and jeeked but it worked - loads of errors (obviously as I was not allowing it to install anything really)

oh the other distro was dapper (puts itself on a partition and then reboots to finish installation but never get past 5% !) and a failed gentoo install (later seems interesting but the install just does not seem to work)

---

### Post by VirtualMe on 2005-12-18
[QUOTE=azz]Since breezy, the installer cd has a rescue mode.  Type rescue after you boot the installer and hit enter.

Boot into it and it will go through the steps as normal (detecting your hardware)  the last step will ask you which partition to chroot into.  Pick your ubuntu install and at the shell, run

grub-install /dev/hda

The live cd probably mounts it read-only , where in rescue mode it is readwrite.


The live cd is fun to have, but it is not indespensable.[/QUOTE]

I tried what you said and I got this:
"The file /boot/grub/stage1 not read correctly."

---

### Post by papa_goose on 2005-12-19
Hey guys...

Totally new to linux but liking it so far...

I too need to reinstall grub, after an xp installation, however, ubuntu is installed on my 2nd hard drive so i can boot it by changing boot order in the bios.

Am i able to reinstall grub from within ubuntu onto my first hard drive?

---

### Post by az on 2005-12-19
[QUOTE=papa_goose]Hey guys...

Totally new to linux but liking it so far...

I too need to reinstall grub, after an xp installation, however, ubuntu is installed on my 2nd hard drive so i can boot it by changing boot order in the bios.

Am i able to reinstall grub from within ubuntu onto my first hard drive?[/QUOTE]
If ubuntu knows it is on the secod hard drive (grub and fstab both use hdb) then all you have to do is

sudo grub-install /dev/hda

The stage 1 gets put on the mbr, pointing to the hdb grub binaries for stage two.

---

### Post by Emerzen on 2005-12-19
[QUOTE=papa_goose]Hey guys...

Totally new to linux but liking it so far...

I too need to reinstall grub, after an xp installation, however, ubuntu is installed on my 2nd hard drive so i can boot it by changing boot order in the bios.

Am i able to reinstall grub from within ubuntu onto my first hard drive?[/QUOTE]


If you installed Ubuntu w/ the boot order in the BIOS changed, then you won't be able to simply reinstall GRUB.  You'll have to change your menu.lst so that GRUB looks for Ubuntu on the 2nd harddrive (because when it was installed it was on the 1st), then reinstall GRUB as above.  Should work fine then.  The important thing is that your menu.lst matches up w/ what GRUB will try to do when it boots.

---

