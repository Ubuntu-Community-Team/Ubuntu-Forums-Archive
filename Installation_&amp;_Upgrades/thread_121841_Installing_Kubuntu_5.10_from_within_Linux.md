---
title: "Installing Kubuntu 5.10 from within Linux"
date: 2006-01-26
forum: Installation &amp; Upgrades
---

### Post by Howcomes on 2006-01-26
I'm currently running Slackware 10.2 and for whatever reason the cd doesnt boot, but i can mount it properly

root@ohnoes:/dev# mount /dev/cdrom
root@ohnoes:/mnt/cdrom# ls
README.diskdefines  doc/      isolinux/   pics/  preseed/
dists/              install/  md5sum.txt  pool/  ubuntu@

Is there any way to install from within linux - furthermore how will this effect LILO ? (I'm dual booting XP and Slack atm)

And yes i want to remove Slackware and install Kubuntu

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2            1151        9951    70694001    7  HPFS/NTFS
/dev/hda3   *           1        1151     9237375   83  Linux

im hoping to format /dev/hda3 so i can put Kubunutu on there. (/dev/hda2 is my Windows XP install)

UPDATE: I've sinced reburned the iso (that blank cd was a little scratched up :P) and it boots now. however - If you look in the /docs/ you'll find an HTML Manual with instructions on booting the Install from other mediums (network, harddrive).

This involves copying vmlinuz and some other gzipped file and editing your lilo.conf , it didnt work the first time around for me, so i gave up and just booted off the newly burned CD - but feel free to look into that yourselfs :P

---

