---
title: "Can't use /dev/sda2"
date: 2005-11-30
forum: Hardware &amp; Laptops
---

### Post by Tuntis on 2005-11-30
Hi, I have an problem:

I have an LaCie 250gb drive. I used Partition Magic to take 30gb out of it for Ubuntu(nonformatted space). The installation's stage 1 was fine, it even dualbooted to Windows XP Professional without ANY problem, but on Ubuntu there was an problem:

[QUOTE=Grub Config]Root   (HD3,1)
Kernel /Boot/VMLinuz-2.6.12-9-386 Root=/dev/sdd2 ro quiet splash
Initrd /Boot/Initrd.img-2.6.12-9-386
Savedefault
Boot[/QUOTE]
As you can see for first, there's no SDD. Tried replacing SDD with SDA, it should be the ext3 partition Kubuntu install made:
[Quote=Error]ALERT: /dev/sda2 not found, dropping to a shell![/Quote]
Aha.
Tried SDA1, which seems to be the NTFS partition I use in Windows, it shows me some BusyBox shell, doesn't continue installation.

I tried to resolve this with the friendly guys in IRC for about 3 hours, and help IS needed.

---

### Post by Tuntis on 2005-12-01
He...llo? I really wish to try out this fancy Linux but nobody seems to even say "Hi" in my thread for useless purposes?

---

### Post by Tuntis on 2005-12-03
Hello, does the topic scare you or what?! I need some help here! :(

---

### Post by aaronc222 on 2005-12-03
Can you boot into a shell at all?

If so, go to the terminal and run
```
ls /dev/s*
```

It should list all devices starting with 's'(since your partitions are on sda). I get hda since that's the drive I'm using.
```
hda  hda1  hda5  
```

My guess is that you may have an sda3 or sda4 instead of it being sda2 like you'd expect.

---

### Post by Tuntis on 2005-12-03
No luck. I'm going to partition an IDE drive now anyways, but how do I get grub off my C:\ drive so that Ubuntu can install Grub again?

---

### Post by aaronc222 on 2005-12-03
Grub should install over itself without any problems. I've had to redo my setup more than a couple of times.

---

