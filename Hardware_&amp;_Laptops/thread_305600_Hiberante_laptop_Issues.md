---
title: "Hiberante laptop Issues  :/"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by jonface on 2006-11-23
Well I've been running 6.10 for a few weeks now and it's pretty much setup the way I want. The only major problem at the moment is hibernate/suspend(sleep?). 

I have the following laptop:

[http://gentoo-wiki.com/HARDWARE_Clevo_D900K](http://gentoo-wiki.com/HARDWARE_Clevo_D900K)
Summary: Laptop, AMD FX60, 2GB ram, GeForce 7900GTX, 2x100gb HD

When I first installed ubuntu I didn't make a swap partition as it never seemed to use it the first time round. I've got 2gb of ram so I thought this was the reason. So anyway I forgot it would be needed for hibernate and made a partition afterwards for swap.

The swap partition is not mounted at the moment (can't remember why, its /dev/sdb3 btw) instead I have a swap file. I don't know why but every boot I have to run mkswap on /swap_file and then swapon -a otherwise it's not detected as swap. 

I've tried fiddling and reading articles on the forum and net but can't seem to get hibernate to work and only managed to break things a few time. I've attached the following logs/file:

acpid, dmesg, fstab, hibernate.log, messages

Any advice on where to start would be welcome.

Thanks.

---

### Post by yeko on 2006-11-24
Hi i'm using dapper but i've got same problem about hibernate..If  U found a solution please forward.I;ll be  apretiated..

---

### Post by caricc on 2006-11-24
I am also using Dapper. But i have found out by trial and error that when I want to put my laptop into hibernation I have to select the logout icon, like I was shutting down my laptop. Then select the hibernate button. Wait for the screen saver to come up then close my notebook. After a few minutes it will finish shutting down. Any other way and my notebook is left on and runs the battery out. 

Hope this helps.

---

### Post by jonface on 2006-11-24
Mine says it is hibernating but after turning it back on, its just like a clean boot. Not sure where to start :/

---

### Post by caricc on 2006-12-08
Select system/preferences/power management:
running on ac tab: Actions chose hibernate.
running on battery tab: actions: same choice. 
general tab: see and make your own choices. 

Enjoy.

---

### Post by zgornel on 2006-12-09
> **jonface said:**
> Well I've been running 6.10 for a few weeks now and it's pretty much setup the way I want. The only major problem at the moment is hibernate/suspend(sleep?). 

I have the following laptop:

[http://gentoo-wiki.com/HARDWARE_Clevo_D900K](http://gentoo-wiki.com/HARDWARE_Clevo_D900K)
Summary: Laptop, AMD FX60, 2GB ram, GeForce 7900GTX, 2x100gb HD

When I first installed ubuntu I didn't make a swap partition as it never seemed to use it the first time round. I've got 2gb of ram so I thought this was the reason. So anyway I forgot it would be needed for hibernate and made a partition afterwards for swap.

The swap partition is not mounted at the moment (can't remember why, its /dev/sdb3 btw) instead I have a swap file. I don't know why but every boot I have to run mkswap on /swap_file and then swapon -a otherwise it's not detected as swap. 

I've tried fiddling and reading articles on the forum and net but can't seem to get hibernate to work and only managed to break things a few time. I've attached the following logs/file:

acpid, dmesg, fstab, hibernate.log, messages

Any advice on where to start would be welcome.

Thanks.
First of all, for hibernate to work you need a swap partition (Suspend2 works with files like Windows, the normal swsupend does not). Second you need a swap partition bigger (or at least equal) than the amount of memory on your system because all the contents of the ram will be saved on the swap (dunno if there is a option to compress the data).
The simplest way to create the swap partition is to create it with GParted, right clik it and choose *swapon*. Then, go to */dev/disk/by-uuid* and see which UUID points to your swap partition (do a *ls -l*). Then, add this line to /etc/fstab:
```
UUID=<your swap uuid> none  swap  sw   0     0 
```. 
Also, edit /etc/initramfs-tools/conf.d/resume and add the line: RESUME=UUID=<your swap uuid>. 
Reboot.
Only after reboot try and see if hibernate works. Remeber, the swap UUID has to be the same in /dev/disks/by-uuid, /etc/fstab and /etc/initramfs-tools/conf.d/resume. From my experience, simply adding /dev/hdX in these files as swap partition does not work for hibernation, it has to be a UUID entry.

---

### Post by nmincone on 2006-12-21
Everyone with suspend/hibernation problems, please STF before asking your questions, chances are it has already been addressed.

[Search this thread for clues...]("http://ubuntuforums.org/showthread.php?t=284994")
This is a real problem that needs real solutions. Supporting hardware for suspend/hibernation is tricky business and could use some polishing in Linux. There's no magic bullet (at the moment).

---

