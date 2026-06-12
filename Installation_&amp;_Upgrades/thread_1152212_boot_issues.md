---
title: "boot issues"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by toferdelachris on 2009-05-07
I'm trying to boot ubuntu 8.40 and/or gparted so I can keep windows xp before I install ubuntu, and I've now officially given up trying to find another person with my problem...

I've retrieved the files from the ubuntu .iso and put those on a 2 gb san disk drive. I've tried to boot from here after changing boot order in BIOS, to no avail - the only return is "Disk error" and then I press a key and it boots windows.

Same with gparted, I formatted the san disk and put gparted on it, boot from the san disk, and "Disk error."

If it makes a difference, I was able to install Ubuntu via wubi, but I don't know exactly what limitations that means I'll have on Linux...

Help?

---

### Post by jerrrys on 2009-05-07
are you using the live cd?

---

### Post by zeex on 2009-05-07
> **toferdelachris said:**
> I'm trying to boot ubuntu 8.40 and/or gparted so I can keep windows xp before I install ubuntu, and I've now officially given up trying to find another person with my problem...

I've retrieved the files from the ubuntu .iso and put those on a 2 gb san disk drive. I've tried to boot from here after changing boot order in BIOS, to no avail - the only return is "Disk error" and then I press a key and it boots windows.

Same with gparted, I formatted the san disk and put gparted on it, boot from the san disk, and "Disk error."

If it makes a difference, I was able to install Ubuntu via wubi, but I don't know exactly what limitations that means I'll have on Linux...

Help?

Hi, 

Here is what you can do. 

1: Burn a ISO DVD of 8.04 
2: Empty a drive in windows (This is where you 'll install Ubuntu)
3: Remove Wubi
4: Set CD/DVD drive primary boot device in BIOS
5: Put the DVD in and Reboot 
6: After the live DVD is up and running. You 'll see install icon on the desktop
7: double click and start the installation.
8: Choose the empty partition from windows. Make a swap space from this partition itself.
9: Mount swap and / . check the format flag
10: Go ahead with the installation.

This should do it. 

Good luck :)

---

### Post by toferdelachris on 2009-05-08
Thanks so much for the suggestions... I figured out most of my issues - I have a eee 1000he, so there's no cd/dvd drive...

anyway, where I stand now is that I have shrunk my windows partition to about 50% of the total size of my HD, so I have now have ubuntu on a bootable usb drive. I can get all the way to choosing what part of the drive I want to install Ubuntu on, and I have a ton of free space to which I want to install (like 70 gb), but when I choose the "write to largest available free space" option, it tries to delete my EFI system partition, resize windows to like 8 gb, and then give the rest to ubuntu... how the do I make it so it doesn't resize any of my existing partitions and just use up the huge amounts of free space...?

---

### Post by zeex on 2009-05-08
> **toferdelachris said:**
>  I have a eee 1000he, so there's no cd/dvd drive...


Next time please specify the system in case you 've a special setup/machine. General assumption is it's a laptop/Desktop.

> 
 but when I choose the "write to largest available free space" option, it tries to delete my EFI system partition, resize windows to like 8 gb, and then give the rest to ubuntu... how the do I make it so it doesn't resize any of my existing partitions and just use up the huge amounts of free space...?

Do manual partitioning, then you can control everything. Just be careful with the drives containing data.

---

