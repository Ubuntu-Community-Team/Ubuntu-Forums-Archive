---
title: "LVM on ubuntu"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by duffman25 on 2005-06-14
Hi

I've installed Ubuntu (5.04) on a laptop & on a amd64. When I first installed ubuntu I didn't knew anything about LVM (logical volumen manager) so I did a more "traditional" partitioning. I've recently look for info and now that I know what LVM can do for me I think I would like to install it on both pc's.

My question is, is there a way to install LVM support on both machines without having to reinstall the whole os? Every howto I've found works on a unpartitioned system, so I 'm beginning to think it's not possible.

Anyway,... I think I'll give it a go even if I have to format my Hd, so my other question is, what's the best configuration for a single Hd with LVM? What partitions could be created? I've hear that LVM has some problems with root partition & boot partition (because grub can't boot it). Any experiences with ubuntu & LVM would be appreciated.

Thanxs for everything.

PS: sorry for my english mistakes.

---

### Post by duffman25 on 2005-06-16
[QUOTE=duffman25]Hi

I've installed Ubuntu (5.04) on a laptop & on a amd64. When I first installed ubuntu I didn't knew anything about LVM (logical volumen manager) so I did a more "traditional" partitioning. I've recently look for info and now that I know what LVM can do for me I think I would like to install it on both pc's.

My question is, is there a way to install LVM support on both machines without having to reinstall the whole os? Every howto I've found works on a unpartitioned system, so I 'm beginning to think it's not possible.

Anyway,... I think I'll give it a go even if I have to format my Hd, so my other question is, what's the best configuration for a single Hd with LVM? What partitions could be created? I've hear that LVM has some problems with root partition & boot partition (because grub can't boot it). Any experiences with ubuntu & LVM would be appreciated.

Thanxs for everything.

PS: sorry for my english mistakes.[/QUOTE]

Nobody has installed ubuntu with LVM support?

---

### Post by alastair on 2005-06-16
Have a go and report back. The installation on top of LVM appears pretty easy.

I'd probably leave / and /boot (and /swap) on non-LVM - but /usr, /var and /home are all candidates.

I did try an LVM over RAID 1 (2x SATA, Dell 1800) a while back - but had problems. On a single disk, who knows? I would hope it works. Let us know.

---

### Post by leohart on 2005-06-27
I had some problem using LVM when setting up (like creating a new LVG) but other than that (since SuSE created the LVG for me already I just use it the same way).

One thing, in SuSE, they put /boot in non-LVM and the rest in a LVG with different LVs of course. Since SuSE is a pretty good distro, I don't think that is bad choice.

Is there any reason NOT to put the rest in a LVG?

/boot cannot be in LVG since GRUB doesn't boot (as far as I have heard)

---

### Post by dicklund2 on 2005-06-29
I have it, and it worked fine for 1-2 weeks then it crashed (well, Ubuntu dont start at all) Dont know if I can blame LVM for that, But now I have big truble accessing data on LVM ](*,)  But it realy is a fine feature when it works!

take a look at [http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
I am a linux newbee and I got it to work wiht this info. Now I have forgot the steps, but start on 11 and go step by step. This took me many hours, but dont give up!

LVM2 is what you want

By the way, I have the LVM only for datastorage, the install is on other partitions like "standard"

Good luck

---

### Post by tonym on 2005-07-09
I have LVM on RAID1 running under Ubuntu.

I tend to put swap on straightforward partitions but I beleive they can go on LVM or RAID.

I put /boot on RAID1 only as I don't think LILO or GRUB can cope with LVM.

I then have separate partitions for /, /usr, /var & /home on LVM on RAID.

The only awkward one is /.  You have to generate an initrd file with appropriate drivers.  I believe this can be done automatically if you do an install onto LVM or RAID.  To do it at another time,  use mkinitrd to create a temporary initrd file before your first reboot onto the new partition.  After booting use dpkg-reconfigure on your kernel package to create a new standard initrd file.

There are some problems with RAID1 in Hoary that can lead to the RAID devices not being created at boot up and then LVM picking up one of the underlying partitions on its own.  This then means you only update one of the mirrors and get nicely corrupted.   A workaround seems to be to delete /etc/mdadm/mdadm.conf but not sure whether that has any bad side effects.

---

