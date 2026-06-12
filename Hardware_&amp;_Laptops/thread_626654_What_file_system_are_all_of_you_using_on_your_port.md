---
title: "What file system are all of you using on your portable hard drives?"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by rchar66 on 2007-11-29
I was just curious what type of file system all of you are using on your portable hard drives?

I have two portable hard drives that I use and they are still formated, they way they came from the factory, with NTFS.

One is a Simpletech Pininfarina 160Gb that I use for transfering files from home and work and also to clients.

The second one is a Simpletech Pininfarina 500Gb that I use mainly at home for storage of all of my files.

They both work great in Ubuntu 7.04 without any problems to read and write to them. There was just one small issue I had with the 160Gb drive the other day.

When I unplugged it from a windows machine, I forgot to right click in the system tray and tell windows to stop communicating with the drive before unplugging it. In Ubuntu it couldn't mount it because it wasn't closed cleanly in windows. I just plugged back into Windows and stopped it through the system tray and everything is fine again.

What other file system could I use, that would work in both Ubuntu and Windows besides NTFS? I've used FAT32 in the past without problems, but on a large capacity drive, I would need to partition it, right?

Is the a Linux format that works with Windows to?

Thanks in advance,
Richard

---

### Post by srt4play on 2007-11-29
You can use ext3 on them, get the windows ext3 filesystem driver [here]("http://www.fs-driver.org").  It doesn't work well with Vista yet though.

---

### Post by vanadium on 2007-11-29
I use ext3 for removable drives. I use fat32 for USB sticks.

---

