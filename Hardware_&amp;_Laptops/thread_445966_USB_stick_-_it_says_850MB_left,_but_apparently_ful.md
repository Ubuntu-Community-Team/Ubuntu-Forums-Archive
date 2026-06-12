---
title: "USB stick - it says 850MB left, but apparently full?"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by qix on 2007-05-16
I have a USB stick plugged into my computer atm. It's 1,5GB, and when I plug it in it says that there is ~850MB left. If I try to copy a file to it, it says that it is full, I can't even create a folder.

What to do? Can I check for errors, or defects? It's a fat16 filesystem afaik.

---

### Post by Old Pink on 2007-05-16
Where did you buy the memory stick? Many imitation/cheaper memory sticks are designed to show a capacity higher than they are capable of holding.

Have you tried backing up the memory stick, formatting and trying agian?

Does the memory stick accept files on Windows/another computer? 

How big is the file you're trying to put on the stick? What is the largest file the stick will accept?

Is the lock (present on the side of most memory sticks) in the lock position?

---

### Post by GrumpyBob on 2007-05-16
Have you looked to see if theres a trash folder?  Ask nautilus to show hidden files...

Robert

---

### Post by Old Pink on 2007-05-16
> **GrumpyBob said:**
> Have you looked to see if theres a trash folder?  Ask nautilus to show hidden files...

Robert

Ctrl+H - before you ask :)

---

### Post by GrumpyBob on 2007-05-16
I do it via the View drop-down menu!

Robert

---

### Post by qix on 2007-05-16
Hey, and thanks for the quick replies.

To answer your questions:
1) I don't see any hidden files.
2) I don't see any lock on the USB stick, so that ain't the case.
3) I tried to create a folder on the stick. It can't even do that. I tried copying small text-files aswell.
4) I don't know where it is bought. Its not my memory stick. But there is engraved "1GB" to the USB-metal-stick, so if it's a fake, it's not a cheap one. [it's 1GB, not 1.5GB as I initially said.]
5) I haven't tried backing it up and formatting it... I can' do that, if there aren't any disk-check utilities?

I just tried deleting a lot of files on it. That worked fine! However, I could still not make any directories or copy even small files to it! When I try to do it, it says that the disk is full?!

Can I have delete + read rights, and not create/write rights? I would assume I would have rights to write on it if I can delete stuff.

---

### Post by qix on 2007-05-16
I fdisk'ed the drive, and did mkfs.vfat on the partition. It seems to work fine now, with 1GB.

---

