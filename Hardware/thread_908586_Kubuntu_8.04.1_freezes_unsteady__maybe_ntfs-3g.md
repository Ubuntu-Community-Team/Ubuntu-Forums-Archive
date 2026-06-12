---
title: "Kubuntu 8.04.1 freezes unsteady / maybe ntfs-3g?"
date: 2008-09-02
forum: Hardware
---

### Post by neo1985 on 2008-09-02
Hello folks!

I'm new to kubuntu Linux since a few days and have a sticky problem where I can't find any help on the net yet (I think the problem is too special).

I'm not a full n00b, I'm programming on Linux for several years, directly on the console, but yet only used Windows as Desktop operating system.
What I'm missing is knowledge on administrating Linux, and even its hardware.

My system is a AMD Athlon XP 1800+, 1.5 Ghz CPU, with 768MB SDRAM. Due to a complete Windows system crash (which is the reason why I now completely switched over to Linux, and because I planned to switch to Linux in the future, I now took the chance ;)), I formatted the first, 40 GB Seagate hard disk with ext3, using the automatic disc configuration of the kubuntu installer. I left my secondary hard-disk, a 250 GB IBM, unchanged, because it holds all my files I rely on. This secondary hard-disk is formatted NTFS due the long lasting use of Windows. A friend told me that Linux provides the ntfs-3g driver in a stable version now, and I thought that there was no better way to directly switch to Linux.

But I think, this is what makes my system unstable: When I mount and browse trough my NTFS-formatted hard-drive, the system sometimes completely freezes. No mouse move or keystroke can be invoked when this occurs - only a hard-reset makes the system run again. And I think that this occurs always when the system tries to access something on the NTFS-formatted hard-disk. Just a few minutes ago, a tried to watch a movie. Yes, it worked, but then I forwarded the movie - a short hard-disk access noise occured - and the system freezed. But this does not always happen. Trying to play an mp3 file from the NTFS is no problem, and even browsing it. It occurs completely unsteady. And now - I write this text since a few minutes after the last reboot - and the system remains stable and good!

Hm I see I'm writing a roman, but I don't know how to find out what the problem for these freezes is. Is it really the ntfs-3g, or is it the proprietary Nvidia driver I use to run X11? Or had you heard of such problems by other people or can give me a hint how to find it out? What tools can I maybe run to check out if my NTFS drives has errors?

I would be very appreciated if you can help me!

Thanks a lot in advance!

neo1985

---

### Post by szaka on 2008-09-03
It's either a hardware problem with your disk or Nvidia problem. NTFS-3G is a user space program which due to the OS architecture can never cause freeze and hangs. Only hardware and kernel problem can.

This URL [http://ntfs-3g.org/support.html#ioerror](http://ntfs-3g.org/support.html#ioerror) also lists several disk brands which are well-known to have serious hardware problems (Seagate, Western Digital, LaCie).

---

