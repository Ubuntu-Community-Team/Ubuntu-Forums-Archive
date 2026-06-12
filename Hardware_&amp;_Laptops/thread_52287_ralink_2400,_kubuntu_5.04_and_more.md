---
title: "ralink 2400, kubuntu 5.04 and more"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by bozotheclown on 2005-07-27
Hi all,

I have to say I'm very enthousiastic about (K)Ubuntu 5.04 and a bit dissapointed as well.
Here goes....
I have a machine based on the Asus A7N8X-E Deluxe board en use the wifi card with that (ralink 2400).

When one has no networking because the adapter is not supported 'out of the box' I't one thing to download a driver on another machine (if one has another machine) and put it on a cd/floppy to next install it on the machine with the unsupported adapter but..........

The driver has to be compiled. No kernel sources available on the Kubuntu cd/dvd? nope, I guess not. What now?

Less importent but still irritating:
1x sata160G and 1 pata 80G in that order.
When I install Kubuntu it insists in installing grub on the pata disk which is not what I boot from (WindowsXP is on the sata disk)
When I do it the manual way I can put grub on the sata disk and XP boots from the grub menu but Kubuntu doesn't. It's hd1,4 and should be 0,4. This could be  done somewhat more intelligent I suppose? The grub on the patadisk btw doesn't work correctly either.... when in my bios I set HDD0 to boot before SCSI (which is sata on this thing) Kubuntu boots from Grub but XP doesn't:)

Now I get to the next point which is that once Grub is installed and the whole shebang isn't functioning as I'd like..... how to get rid of Grub without a dos bootdisk (fdisk /mbr) which doesn't see satadisks:)


Now.... I edited the grub menu and Grub on my sata-disk works great but.....
Mounting my ntfs pata disk (/dev/hda1) works after I'va manually added it to fstab but only as root. Accessing it also only works a root.
This is nog really userfriendly I suppose or am I rambling bullshit right now?

How do I get it so it's the way I want it to work?

Mind you..... I'm not a nono.... I've been using several Linux dists and FreeBSD releases but when it's put together like (K)Ubuntu is (great!) I'd like some of the comfort my XP gives me. Why? simply because when it does I can dump XP and use a nice (K)Ubuntu with Enlightenment for the eyecandy:) and play my games using my for now rather poorly(in (K)Ubuntu) supported 6600gt. By poorly I just mean that I can only select 60 and 75hz in 1280x1024 and my tft works best at 72hz in that resolution. The screen is also shifted to the right half a centimeter in Kubuntu'.


This may seem a negative rant but I assure you it isn't. I like Kubuntu, if I didn't I'd kill the partitions and resize my XP partitition back to full.

---

