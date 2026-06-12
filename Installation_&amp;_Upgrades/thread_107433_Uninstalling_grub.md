---
title: "Uninstalling grub"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by BotBuilder on 2005-12-23
Or more particularly, making the computer boot up to winddows again without grub.

This is a rather non-ubuntu problem, but hey.

I want to install ubuntu on this computer, but when I tried before I installed 64 bit ubuntu, which apparently isnt a very good idea when you've got a new-ish graphics card.  Anyway, I'd like to wipe my whole hard drive (windows and all), so I'll need to backup stuff.  I've accumalated about 10GB of stuff I want to back up, but I dont really want to burn it to DVDs - a much more attractive solution is just putting it on a hard drive.  Turns out I've got an 80GB hard drive un-used in an old computer that holds a version of redhat that doesnt work on the hardware.  It also has GRUB.  The other 80gb hard drive has windows.  If I remove the hard drive with grub/redhat on it, the computer complains about being unable to load the operating system.

Cutting a longish story short,  I need to make windows the new default boot thingamabob (I think its called the main boot record - MBR).  Any way I can do this with a small boot-app or something?

Thanks.

---

### Post by Sutekh on 2005-12-23
You will need your Windows Installation CD.  Boot with the CD and start a recovery console.  I think you press 'R' at some stage.

Then use
```
fixmbr
```
to re-install the Windows bootloader

---

### Post by BotBuilder on 2005-12-23
Thanks, I've tried this, however it is asking for an administrator password.

We have 4 administrator profiles set up and and only one has a password. He hasn't used the computer in years and isn't sure of teh password.  You can only try 3 passwords and it sends it into a 5 minute reboot cycle so its not v ery much fun to guess.

The recovery disk refers to it as "the" administrator password.  If I got windows working again how could I find this?  Also, is there another tool that would be able to do this task reliably and not require a password?

Thanks

---

### Post by moollar on 2005-12-23
Had a similar problem recently. I found two solutions (actually it's the same solution, you can just go about it different ways).

1st, if you have a Win98 CD or bootdisk, boot from that and use this command at the Dos prompt:

fdisk /mbr

2nd, if you don't have a boot disk/CD, you could probably download it from bootdisk.com and type the above command from the Dos prompt.

Note that this only works when there is one partition on the hard drive, so you'll have to delete any partitions you don't want (fdisk should be able to help with this too).

Hope this helps...

---

### Post by moollar on 2005-12-23
[QUOTE=moollar]Note that this only works when there is one partition on the hard drive, so you'll have to delete any partitions you don't want (fdisk should be able to help with this too).
[/QUOTE]

I may be wrong about the one partition thing, but it happened to work AFTER I had got rid of the other partitions. Someone please correct me if I'm wrong - I'd like to know myself ;)

---

### Post by BotBuilder on 2005-12-24
Thanks for the help, I got a copy of [freedos]("http://www.freedos.org/") and did "fdisk /mbr" as you suggested.

This seems to have done the job quite nicely :)  On a multi-partition system as well.

Anyway, now I've just got to figure out how to get ubuntu installed on this computer... I think I'll resize my windows partition and stick it in in the freed space.  ATM its having troubles installing on a second drive.

---

