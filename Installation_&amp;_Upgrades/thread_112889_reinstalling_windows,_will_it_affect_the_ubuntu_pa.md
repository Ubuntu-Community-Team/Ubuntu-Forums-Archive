---
title: "reinstalling windows, will it affect the ubuntu partition?"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by nandasunu on 2006-01-05
I have an xp/ubuntu dual boot and the time has come (yet again) to reinstall good old winXP. Will doing this remove the grub? Will it affect my ubuntu install at all?

thanks.

---

### Post by Alpha_toxic on 2006-01-05
Unfortunately it will remove GRUB, but it will not affect Ubuntu's partition in any other way.
You can reinstall GRUB using the Live-CD, but as I haven't tried it my self, I don't know exactly how...
Good luck anyway :)

---

### Post by benco on 2006-01-05
To restore GRUB on the MBR of your disk just :
*** CAUTION *** 
I assume your disk is /dev/hda and your ubuntu boot partition is on /dev/hda1

- boot a Live CD (I have a knoppix CD for that and 'knoppix 3' starts in text mode - faster)
- mount your ubuntu partition with something like :
> 
# mount -t ext3 -orw /dev/hda1 /mnt

- chroot to this partition
> 
# chroot /mnt

- install GRUB
> 
# grub-install /dev/hda

- and reboot.

I am not so sure the mount/chroot is mandatory but it doesn't hurt.

---

### Post by nandasunu on 2006-01-05
Thanks for your help, I will try that (fingers crossed [-o< )

---

### Post by Koobi on 2006-01-05
[QUOTE=nandasunu]Thanks for your help, I will try that (fingers crossed [-o< )[/QUOTE]

please post your results :)
i want to do the same (i.e. install windows on a seperate partition) but i'm afraid of messing it up...the thing is i don't have a few hours to spare to fix the problem in case something goes wrong and i don't have another machine to test it out on.

so i would appreciate it if you let me know how it went and what you did.
thanks.

---

### Post by nandasunu on 2006-01-07
> 
so i would appreciate it if you let me know how it went and what you did.

I haven't done it yet as I am now considering wiping the windows partition all together... :-\" 

If I do it I will for sure let you know how it works.

---

