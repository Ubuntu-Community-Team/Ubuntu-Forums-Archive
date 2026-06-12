---
title: "Trying to format a hard drive.. crashed."
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by MaXiMiUS on 2009-01-17
[s]The story is pretty simple. I was trying to format a hard drive of mine with GParted.. and I happened to crash in the process. I can't seem to get Ubuntu to boot properly now (running from LiveUSB), as the hard drive now contains errors due to the failed formatting/partitioning..

How can I get in to Ubuntu so I can run GParted now? I'm at a loss for what to do.

It's an IDE drive, btw, and I don't really care what happens to any data already on the drive, I just want to be able to use the drive, lol.[/s]

Uhh... nevermind! As I was typing this, Ubuntu finally booted, after 5+ minutes of trying to read from the drive.

Going to check if I can format the drive now..

Edit: No good.. it just ignored the drive. I can't detect/format it :(

I know there's nothing physically wrong with the drive.. it's just got a bit of.. messed up data on it. That's all..

---

### Post by spacegypsy on 2009-01-17
Try running Gparted from live-cd

---

### Post by MaXiMiUS on 2009-01-17
Don't have access to a CD/DVD burner.. and my only USB stick has Ubuntu on it. Suggestions/links?

---

### Post by aheckler on 2009-01-17
If you can boot to the LiveCD, run ```
dd if=/dev/null of=**HDD**
``` to zero out the drive. Replace "**HDD**" with the location of your disk of course; it should be something like "/dev/sda1".

(This assumes you can at least mount it.)

---

### Post by MaXiMiUS on 2009-01-17
I can't seem to get Ubuntu to mount the drive. Ubuntu was able to mount it perfectly fine before the crash.

---

### Post by TonyFordz on 2009-01-17
Hey man if you have a Windows XP CD boot into that CD then at your partitions list whip them all out then remove the CD & restart your PC booting the Ubuntu CD that is what I do when I have that problem. It should mount fine then...

---

