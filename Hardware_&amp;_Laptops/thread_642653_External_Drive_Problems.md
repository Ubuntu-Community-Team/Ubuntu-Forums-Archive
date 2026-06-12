---
title: "External Drive Problems"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by myst1c on 2007-12-16
I'm somewhat new to Ubuntu, as I've just installed it a couple days ago. I've pretty much gotten the hang of it, but I'm having a problem.

So, I have an external 400 gigabyte drive. It's a Western Digital MyBook. Whenever I plug it in, I get this error:

[IMG]http://i239.photobucket.com/albums/ff314/myst1crule/MyBookError.png[/IMG]

I attached it to a Windows machine and formatted it, to no avail. Can anybody give me a hand here?

---

### Post by myst1c on 2007-12-16
anybody? please? it's kind of important, as i don't have very much hard disk space without it,,, does it help to know that it's file system is NTFS?

---

### Post by myst1c on 2007-12-17
it's been 3 hours, and i haven't gotten a single response... can SOMEBODY help me please?

---

### Post by lazyfirecloud on 2007-12-17
Do you need the data in both Windows and Linux?  If you use NTFS, you won't be able to use linux permissions on it.
1) if you do want to share data, then NTFS is probably the way to go.  Make sure you have nstf-3g, then mount it by hand.  I don't think you can use the automatic mounting through nautilus if it is in NTFS.
the command should look something like: sudo mount -t ntfs-3g /dev/hdc1 /mount
where /mount is an empty directory you created  (I made mine /data since it contains all my data)  and /dev/hdc1 is your device.  you'll have to figure out which is your device.  you can add it to your /etc/fstab if you want.
2) if you're only going to use it in linux, then I would just use gparted and format it into ext3.

---

### Post by Norst on 2007-12-17
Basically the drive did not separate from windows cleanly when you last used the drive.

A) If you have access to windows on the same machine or anothe box close, follow the instructions in the error window.

B) If you don't have access to windows do the following:

first we need to see where the drive is showing up in /dev
[B]
with the drive not plugged into the machine:[/B]
```
ls /dev/sd*
```

in my case I get:
```
/dev/sda   /dev/sdb   /dev/sdc   /dev/sdc2  /dev/sdc5  /dev/sdd1  /dev/sdf
/dev/sda1  /dev/sdb1  /dev/sdc1  /dev/sdc3  /dev/sdd   /dev/sde

```

Now we** plug it in**, give the box a sec to see it and do the same command again (in my case I'm just using a usb stick):
```
/dev/sda   /dev/sdb1  /dev/sdc2  /dev/sdd   /dev/sdf
/dev/sda1  /dev/sdc   /dev/sdc3  /dev/sdd1  /dev/sdg
/dev/sdb   /dev/sdc1  /dev/sdc5  /dev/sde   /dev/sdg1

```

By this I now know the drive I'm pluging in is /dev/sdg1 (yours will obviously be different). Depending on how the drive is partitioned, you may see ones like sdg sdg2 sdg3 ect.... It will be up to you to know what partition is having the issue. Chances are its the one ending in 1.

Now type:
```
sudo apt-get install ntfsprogs
```

then:
```
sudo ntfsfix /dev/*(YOUR /dev from above)*
```

It may warn/ask you about fixing the journal, say yes. When it's done, you can remove the re-plug the drive, and hopefully it will mount for you.

I'm no pro, but I have a similar issue when I was recovering a drive from a laptop for a friend, using a external drive case.

Hope this helps,
Norst

---

### Post by myst1c on 2007-12-17
problem solved... thanks alot norst

---

