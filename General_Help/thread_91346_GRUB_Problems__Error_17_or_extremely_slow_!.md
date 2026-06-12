---
title: "GRUB Problems : Error 17 or extremely slow !"
date: 2005-11-17
forum: General Help
---

### Post by Shinkan on 2005-11-17
Hi there !

I've just set up again an Ubuntu Breezy.
I have had this problem when GRUB started :
GRUB stage 1.5.
(long time)
GRUB loading ...
(long time)
Error 17

Partition disposition was :
HD 1 37 Gb, Windows ntfs (37 Gg) edited to 32 Gb, ext3 root mounted (5 Gb)
HD 2 120 Go, Windows/Various Data (110 Gb) + 10 Gb free space used as home (9 Gb) + swap (700 Mb).

So I have set up Breezy one more time, two more time ... I changed the partitions disposition, now GRUb works but it is extremely slow:
GRUB stage 1.5.
(long long time)
(and I have the OS list)

Partition disposition is :
HD 1 sized back to one ntfs partition of 37 Gb
HD 2 : 10 Gb used as root and swap

On each case, GRUB was set up on the MBR (of the first disk I think).

So I would like GRUB to be a little more speedy, because I have already set up breezy before (the day of its release), and GRUB was working perfectly ... thus I've not changed any hardware since the first install ...

Thanks in advance !

---

### Post by Shinkan on 2005-11-17
up :/

---

### Post by newtonfn on 2006-01-29
I had the same problem.
Take a long long long long time to load GRUB (around 5 minutes)

I can not provide more info because it was on a friend's pc, who agree to tolerate that lag (how often do you reboot your pc ;))

In that PC the BIOS spend a long time detecting the hard disk too, but after boot there is no problem, neither with Ubunto nor Windows.

Before ubunto was installed, with the WinNT loader, everything was fine and fast (only the bios was slow to detect the disks but the bootloader was as fast as it should be)

I don't know where to start looking for troubles. ¿any idea?
Thx

---

### Post by nik on 2006-01-29
Wouldn't be surprised if it has something to do with the windows partitions... I have a usb fat32 hd, and I have exactly the same problem when I try to boot with that plugged in. Don't know of a solution, but I seem to remember someone talking about this if the hd had an error? Someone know how to check for errors in linux?

---

