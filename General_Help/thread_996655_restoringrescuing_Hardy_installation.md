---
title: "restoring/rescuing Hardy installation"
date: 2008-11-29
forum: General Help
---

### Post by Barfy74 on 2008-11-29
Hi,

I've recently converted to Ubuntu with a dual boot Hardy/Vista Ultimate machine (still need Windows for work and the girlfriend). Everything was going well until I decided to try running before I was walking properly.

I wanted to play Simcity 3000, and couldn't get it to work under Hardy, so had the bright idea of setting up a new small partition with Warty installed to just play the game (I know, probably not a great idea). Anyway, this wasn't going to plan, so I jacked it in and went back to my Hardy installation...

... But I left the Warty disc in my drive, and when I booted into Hardy, it started running through some 'updates'. I didn't think anything of it until the disc drive started spinning up. I managed to get a quick look at what was going on, and caught a glimpse of Kernel [can't remember the number] being removed.

The update finished, and immediately I lost my wireless internet connction. Then I probably committed the most basic schoolboy error imaginable (a legacy of windows perhaps). I restarted the machine... Next time at the grub, I selected Ubuntu, and got an error message saying that 'file can't be found'.

Is it possible to restore without a full reinstall? Is there any help for a screw up of this magnitude?

Cheers,
Barfy

---

### Post by caljohnsmith on 2008-11-29
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
ls -l /boot
cat /mnt/boot/grub/menu.lst
```
And please post the output of all the above commands; we can work from there if you want. :)

---

