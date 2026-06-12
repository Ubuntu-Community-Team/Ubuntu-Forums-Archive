---
title: "Insufficient Memory to Download Gparted"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by tobys on 2009-07-14
When I originally partitioned my hard drive for Ubuntu, the partition was created with the minimum amount of space to run Ubuntu. I cannot download updates or any additional software onto my Ubuntu partition. I would like to increase the partition size; however, I cannot download GParted due to insufficient space on the partition. I would rather not order a CD and instead download GParted to my 2GB USB stick. Is there an easy way to do this via Firefox / terminal?

---

### Post by Marlonsm on 2009-07-14
Well, if you have another partion, wouldn't it be easier to boot the OS you have there and resize partitions using it?
If it's Windows, you can use Easeus Partition Manager, I've already used it and it's very easy to use.
[http://download.cnet.com/Easeus-Partition-Manager-Home-Edition/3000-2248_4-10863346.html]("http://download.cnet.com/Easeus-Partition-Manager-Home-Edition/3000-2248_4-10863346.html")

---

### Post by drs305 on 2009-07-14
> **tobys said:**
> I would like to increase the partition size; however, I cannot download GParted due to insufficient space on the partition. I would rather not order a CD and instead download GParted to my 2GB USB stick. Is there an easy way to do this via Firefox / terminal?

Have you tried changing the download location of Firefox? In edit, preferences, main tab you can change the download location. You can probably select an alternate partition or external device from this section.

---

### Post by snowpine on 2009-07-14
Hi Drs305, check out Unetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You can use it to create a bootable USB stick with Parted Magic or distro that has Gparted built in (like Puppy).

No point installing Gparted on your Ubuntu partition, because you can't resize a partition from within itself.

---

### Post by drs305 on 2009-07-14
I use the SystemRescueCD, but there is also a gparted CD, which I thought the user was downloading since a download of the app to a separate USB device wouldn't do much good, as you say. 

I prefer the systemrescueCD, but either would do, as would snowpine's suggestion.

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

[Gparted CD]("http://gparted.sourceforge.net/livecd.php")

---

### Post by prshah on 2009-07-14
> **tobys said:**
> I cannot download updates or any additional software onto my Ubuntu partition.

This seems pretty unlikely to me. About 5% of the partition is reserved for "root" (sudo) operations. I think you should comfortably be able to download gparted within this reserved space. gparted uses about 2mb or so. However, if you are really that pressed for space, you can always clear your /var/cache/apt/archives/ directory to gain some free space; at least enough for gparted. This directory contains all update-manager downloaded .deb files, which can be safely deleted once installed. For example, my archive directory currently occupies 231M of space; ```
Tue Jul 14 22:15:14 ~:$ du -sh /var/cache/apt/archives/
231M    /var/cache/apt/archives/

```

---

