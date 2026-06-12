---
title: "Lost+Found folder - how to delete ?"
date: 2015-02-26
forum: Hardware
---

### Post by michael-piziak on 2015-02-26
There's a "Lost+Found" folder on my thumb drive.  How to delete it without formatting the entire card?  It doesn't appear to have anything in it and it is locked.

Folder says I'm not the owner.   I think it appeared after I started formatting my thumb drive as Linux ext2 or ext4.

---

### Post by Bucky Ball on 2015-02-26
You don't want to delete the lost+found directory. It is an important system folder and will be recreated on next boot anyway. There is some pretty good explanation of why it is there and what it does [here]("http://unix.stackexchange.com/questions/18154/what-is-the-purpose-of-the-lostfound-folder-in-linux-and-unix"). ;)

---

### Post by slickymaster on 2015-02-26
Lost+Found is an important directory which is useful for recovering files which are not properly closed due to many reason such as power failure. Lost+Found is created by system at the time of any Linux OS installation for each partition you create. This folder contains the files with no links and files to be recovered. Any file to be recovered is kept in this folder.

---

### Post by michael-piziak on 2015-02-26
Well, I just wanted to delete it from the thumb drive, not the computer.  I can leave it there, but I found it odd that it showed up on the thumb drive.

---

### Post by Bucky Ball on 2015-02-26
It you formatted the dongle with EXT*, then it is supposed to be there.

---

### Post by slickymaster on 2015-02-26
> **Bucky Ball said:**
> It you formatted the dongle with EXT*, then it is supposed to be there.
Exactly.

---

