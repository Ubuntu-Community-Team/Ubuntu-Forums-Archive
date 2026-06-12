---
title: "GRUB boot problem?"
date: 2008-08-19
forum: General Help
---

### Post by connor da og on 2008-08-19
Right,
I installed ubuntu around 2-3 days ago, and after that i had trouble booting my XP (I dual boot) it would just load and reboot, so today I've re-installed XP but now i dont get an option to select my OS, it automaticaly loads XP, any ideas? -  i do not wish to re-install ubuntu for loss of data, and if theres a way to re-install a GRUB boot loader, will it Fu*k up my xp?

---

### Post by coffeecat on 2008-08-19
This is a fairly simple repair job. Windows has overwritten Grub stage 1 on the master boot record and this needs to be reinstalled.

Boot up with the live CD, and go to System > Administration > Partition Editor (Gparted). Don't do anything except look. See which is your Ubuntu root partition. It will be something like sda5 or sda6 I would expect, and Windows will be on sda1 - probably. Now go to Applications > Accessories and open a terminal. Do the following command:

```
sudo grub
```The prompt will change from $ to >. For the next step I'm going to assume your Ubuntu root partition is on sda6. If it's something different, see below. Do the following at the grub prompt:

```
root (hd0,5)
setup (hd0)
quit
```If you need to change the root reference, sda2 would be (hd0,1), sda5 (hd0,4) and so on. See how grub counts from zero, uses hd instead of sd, uses a comma and puts the whole lot in brackets.

Now exit the terminal, reboot, remove the CD and you should have the grub menu again. Post back if any error messages or anything unclear.

**Edit:** and no, this won't - er - mess up Windows. Grub stage 2 and the grub menu are on your Ubuntu root partition (in /boot/grub) and shouldn't have been affected by reinstalling Windows - unless the Windows CD reformatted the whole drive. You'll soon see if it did when you open up Gparted in the live CD

**2nd Edit:** another little tip. Never forget that you have a powerful repair and maintenance tool in the live CD - assuming you used the live and not the alternate CD to install. Not only can you do repair jobs like this, but you can copy data off both Linux and Windows partitions with it because the live environment will automount USB drives. Windows has nothing like it. :cool: :wink:

---

### Post by connor da og on 2008-08-19
> **coffeecat said:**
> This is a fairly simple repair job. Windows has overwritten Grub stage 1 on the master boot record and this needs to be reinstalled.

Boot up with the live CD, and go to System > Administration > Partition Editor (Gparted). Don't do anything except look. See which is your Ubuntu root partition. It will be something like sda5 or sda6 I would expect, and Windows will be on sda1 - probably. Now go to Applications > Accessories and open a terminal. Do the following command:

```
sudo grub
```The prompt will change from $ to >. For the next step I'm going to assume your Ubuntu root partition is on sda6. If it's something different, see below. Do the following at the grub prompt:

```
root (hd0,5)
setup (hd0)
quit
```If you need to change the root reference, sda2 would be (hd0,1), sda5 (hd0,4) and so on. See how grub counts from zero, uses hd instead of sd, uses a comma and puts the whole lot in brackets.

Now exit the terminal, reboot, remove the CD and you should have the grub menu again. Post back if any error messages or anything unclear.

**Edit:** and no, this won't - er - mess up Windows. Grub stage 2 and the grub menu are on your Ubuntu root partition (in /boot/grub) and shouldn't have been affected by reinstalling Windows - unless the Windows CD reformatted the whole drive. You'll soon see if it did when you open up Gparted in the live CD

**2nd Edit:** another little tip. Never forget that you have a powerful repair and maintenance tool in the live CD - assuming you used the live and not the alternate CD to install. Not only can you do repair jobs like this, but you can copy data off both Linux and Windows partitions with it because the live environment will automount USB drives. Windows has nothing like it. :cool: :wink:

Thanks ;), I'll give this a shot, but i no for a fact i didnt reformat the whole drive, just the c partion :P

---

### Post by connor da og on 2008-08-19
Thanks very much youve saved me alota hassle :D

---

