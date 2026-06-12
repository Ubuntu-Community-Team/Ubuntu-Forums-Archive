---
title: "Partitioning advice"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by seven7seven on 2009-08-08
Hi,

I want to address a very particular issue, as most guides and documentation were not very helpful in actually helping me decide.

I'm getting a 500GB drive, which according to my math, will give me around 465 GiB of usable data. I want to install both Windows and Ubuntu (including swap partition(s)).

I need help deciding on how to spread the partitions, while maintaining a few guidelines:

- I want a big partition (~350G), which will be used only for data (no binaries, security reasons). This will be NTFS (or, let me know if you have any better suggestions please), and accessible by both OS.
- I have no idea how much swap I should get, but I figure 2G is enough?
- I'll be installing Windows first, then Ubuntu. Windows will have the first chunk of the hard drive. (~100G).
- That leaves Ubuntu with ~13G, more than enough.

How should I arrange these? I was thinking of doing this:

```

Windows  Linux  Swap  Files
----------------------------
100      13     2     350
```


What I want to know, is this setup right? Should I place the swap partition at the end of the HDD? Maybe split them into 1G chunks?

What would you do? :)

Thanks!

---

### Post by raymondh on 2009-08-08
> **seven7seven said:**
> Hi,

I want to address a very particular issue, as most guides and documentation were not very helpful in actually helping me decide.

I'm getting a 500GB drive, which according to my math, will give me around 465.6 GiB of usable data. I want to install both Windows and Ubuntu (including swap partition(s)).

I need help deciding on how to spread the partitions, while maintaining a few guidelines:

- I want a big partition (~350G), which will be used only for data (no binaries, security reasons). This will be NTFS (or, let me know if you have any better suggestions please), and accessible by both OS.
- I have no idea how much swap I should get, but I figure 2G is enough?
- I'll be installing Windows first, then Ubuntu. Windows will have the first chunk of the hard drive. (~100G).
- That leaves Ubuntu with ~13G, more than enough.

How should I arrange these? I was thinking of doing this:


Windows  Linux  Swap  Files
----------------------------
100      13     2     350

What I want to know, is this setup right? Should I place the swap partition at the end of the HDD? Maybe split them into 1G chunks?

What would you do? :)

Thanks!

Looks good.  I've noticed a tendency to grow linux as one gets' comfortable with it :)  So, in this set-up, you may have to take space (later on) from somewhere.  I made my linux 20GB which is more than enough for me.

As for SWAP, it really depends on your suspend habits.  Mine is 1.5GB and I rarely get to use it.

NTFS is a good format which can be read by both OS'.

Good luck.

EDIT : Am assuming your system and BIOS is of recent vintage.  Otherwise, (if older ... say 90's vintage), you may run into the cylinder limit which is either 8GB or 136GB.  See [Herman's]("http://members.iinet.net/%7Eherman546/index.html") website and it's BIOS index for more reading.

---

### Post by seven7seven on 2009-08-08
Thanks! I don't think I'll have any problems, the HDD is "attatched" to a Dell Studio XPS 16. I won't be using their OS Rescue Disks either (if they even send them) - I'll do a fresh Windows 7 install, most likely.

I'm also considering stealing some more space from the Windows partition, make it 90 / 23 or something, although most of my past distros have been squished at the end of an 80G drive, in 7-8G partitions. :)

---

### Post by drs305 on 2009-08-08
Just a personal preference: I put my swap at the very end (far right) of the extended partition so when I resize the others it doesn't get in the way. Of course, you can always just delete the swap partition and create a new one after you've moved everything around, but by sticking it out of the way you won't have to do that.

---

### Post by raymondh on 2009-08-08
> **seven7seven said:**
> Thanks! I don't think I'll have any problems, the HDD is "attatched" to a Dell Studio XPS 16. I won't be using their OS Rescue Disks either (if they even send them) - I'll do a fresh Windows 7 install, most likely.

I'm also considering stealing some more space from the Windows partition, make it 90 / 23 or something, although most of my past distros have been squished at the end of an 80G drive, in 7-8G partitions. :)

Seven,

Now that you mentioned an "attached" HDD which I assume is an external HD ..... remember that if you install GRUB and Ubuntu in the external, you will/can only boot into Ubuntu with the external attached, unless you plan to use a different bootloader and chainload Ubuntu to it.  

Good luck.  Yes, it's possible.

---

### Post by seven7seven on 2009-08-08
> **raymondhenson said:**
> Seven,

Now that you mentioned an "attached" HDD which I assume is an external HD ..... remember that if you install GRUB and Ubuntu in the external, you will/can only boot into Ubuntu with the external attached, unless you plan to use a different bootloader and chainload Ubuntu to it.  

Good luck.  Yes, it's possible.

Nope, not an external drive, it's an 2.5" SATA.

Sorry for the confusion, I just meant it's not for my desktop. It just comes inside the new laptop (very conveniently!).

---

### Post by raymondh on 2009-08-08
> **seven7seven said:**
> Nope, not an external drive, it's an 2.5" SATA.

Sorry for the confusion, I just meant it's not for my desktop. It just comes inside the new laptop (very conveniently!).

Cool.  Have fun, read up and enjoy your ubuntu experience :)

---

### Post by seven7seven on 2009-08-08
> **drs305 said:**
> Just a personal preference: I put my swap at the very end (far right) of the extended partition so when I resize the others it doesn't get in the way. Of course, you can always just delete the swap partition and create a new one after you've moved everything around, but by sticking it out of the way you won't have to do that.

I did consider that, actually. But then I read something about disk performance at the edge of the drive, shouldn't that be a problem?

If I do move it, then I'll have two primary partitions, then an extended one with 2 logical partitions, correct? 

```
[W] [L] *[F S]
```

EDIT: Actually, if the Swap follows the Linux partition, like in the original setup, would it still be in the extended partition? This is the first time I can afford the luxury of spare space for a Swap partition, so I have no idea.

---

### Post by drs305 on 2009-08-08
You can have a maximum of 4 primary partitions, but an extended partition counts as one. Since extended partitions give you flexibility, you should probably devote one of the primary partitions to an extended partition. 

I like extended partitions for the flexibility - you can split them up more than you will ever need. Since moving unallocated space between the extended and primary partitions is a bit more involved, I usually only have one primary partition (as long as I leave enough space so I won't have to grow or shrink it) and use all the rest for logical partitions within the extended one. It's all personal preference.

As far as location on the disk, technically the location may effect performance but with swap the chances are excellent that you are never going to notice, wherever you place it.

---

### Post by seven7seven on 2009-08-11
Alright, thanks for the help chaps. Everything's up and running, even a dedicated GRUB partition.

I ran into some problems with my internet connection (both wifi and ethernet work fine on Windows) - I can't get any on Ubuntu. The wifi card is identified, it just doesn't pick up anything. I could probably work it out by downloading some packages via Ethernet, but I can't get that to work...

Should I start a new thread, or can you guys help me out here?

The Ethernet controller is a Broadcom Netlink Gigabit Ethernet adaptor, on a Dell Studio XPS 16, which should have out-of-the-box support for Ubuntu.

Let me know if you need any outputs. Thanks!

LE: Some later research found that it was a power management issue - Windows was shutting the device down, and it couldn't be brought up properly by Ubuntu. All that I had to do was enable Wake-on-lan in Device Manager, for the adapter. Hope this helps someone else with similar problems.

---

