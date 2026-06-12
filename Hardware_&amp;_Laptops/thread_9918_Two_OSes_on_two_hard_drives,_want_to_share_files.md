---
title: "Two OSes on two hard drives, want to share files"
date: 2005-01-02
forum: Hardware &amp; Laptops
---

### Post by Niomi on 2005-01-02
I looked around in the wiki and user's guide, and couldn't find anything-- am I overlooking anything obvious? *linuxnewbie!*

I go to school over the internet, and keeping Windows on my computer is a must since it's the only system the software supports. Not to mention I'm a Sims addict, which doesn't run under Linux - to my knowledge.

I picked up a new hard drive today, a 120GB drive. I made it a slave of my 80GB with XP on it, stuck Linux on 120 GB and dual booted. My problem is, I want Windows to be able to acess, read, and write to the files on the 120GB drive, and vise versa. Neither OS is detecting the other drive.

Also, would it be possible to get Mozilla to share one profile, so if I make a bookmark in one OS it'll show up in the other?

Edit:
AMD Athalon 2.7 2800+
1GB RAM

---

### Post by Adrenal on 2005-01-02
Sorry man, windows will never write to ext3(linux format) same with how linux will never write to ntfs. However, if your windows is fat32, i think you can allow linux to write to it.
Since your using Ubuntu, you can mount your ntfs there as read only. To have windows access your linux drive, go into windows, read [this](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)
Be careful though, its kinda untested, back up anything you can't live without

---

### Post by Rancoras on 2005-01-02
In addition to what Adrenal said, you could create a separate fat32 partition specifically for the sharing of files between the 2 operating systems.

For your Firefox / Mozilla question, look here and modify for your needs:

[http://www.mozilla.org/support/firefox/tips#beh_bookmarks](http://www.mozilla.org/support/firefox/tips#beh_bookmarks)

---

