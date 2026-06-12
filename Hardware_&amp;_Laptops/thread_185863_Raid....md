---
title: "Raid..."
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by TrueTenacity on 2006-06-01
I've got a raid 0 array with an NTFS partition connected to my on-board Sil3114 SATA raid... how the hell do i mount it???

---

### Post by mavicus on 2006-06-01
I would like to know this also. I configured 2 SATA drives as a mirror during install, like I have before with breezy, however it didn't "stick" when the box finally came up.

The two drives are formerly a mirror set whose data is no longer needed.

disk manager and gparted both show the drives as /dev/sda and /dev/sdb, and gparted shows that they still contain ext3 file systems with data still on them.

I can't get them to mount. gparted shows the single partition on each one as being flagged as raid.

What tool do I use to pick up these drives as either a raid 0 or raid 1 set so I can mount them?

](*,)

---

### Post by purephase on 2006-06-03
I have the same issue. I have an nVidia stripe with one of the existing partitions  formatted with NTFS (with a lot of backup data I want to keep). I'm trying to install dapper on one of the other system partitions (currently NTFS) but GParted only sees the physical disks, not the RAID setup.

I thought this was addressed in Breezy? Why is this happening with a later release?

---

### Post by purephase on 2006-06-04
Nevermind. I figured it out. It's the lack of nvraid support for linux (no drivers, can't blame them).

---

### Post by tamashumi on 2006-08-23
I have the same problem. 2 sata raid0 segate drives on my on-board SiL3114 controller. They are my only drives I want to install linux on them without splitting the array for dual boot with windows.

I found it's almost impossible but there are some ways. 1st of all there are some drivers at Silicon Image website. But I guess I need to have hdd installed linux distribution 1st to play with them. However how can I install if my drive is unrecognised? :rolleyes:

I trie to install or run live the most recent distribution of Suse, Knoppix, Mandriva, Ubuntu and Fedora.
Only the Fedore Core 5, Bordeaux works over the issue (got it installed right now). But still I prefer (just in the 1st feeling) to install Ubuntu. Please any solution? :biggrin:

---

