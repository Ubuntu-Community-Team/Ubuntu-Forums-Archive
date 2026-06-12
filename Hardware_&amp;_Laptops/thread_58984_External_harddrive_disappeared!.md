---
title: "External harddrive disappeared!"
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by Rydberg on 2005-08-22
Hi,
I've been running Hoary for about a month now, and it has been a pretty smooth ride setting it up even though I'm new to Linux.

I have an external 250 GB Maxtor HD harddrive, and up until recently, it has worked very well with Ubuntu. It's connected via firewire to the mobo, and it consists of a single NTFS partition.

A few days ago, it's suddenly not recognized by the system anymore, and won't mount when I switch it on. What could cause this?

I doubt that it's a hardware issue, the drive is still accessible in Windows XP, and appears to be perfectly healthy.

The drive shows up in the Ubuntu device manager, but as an "Unknown Device", and it doesn't provide a whole lot of info.
I've seen in similar threads that one should monitor kernel messages when the device is plugged in, and I've done so, but no messages related to the drive came up. I tried plugging in a USB memory stick, and that worked just fine.

What I did to my system the day it stopped working:
Not much really. A few days earlier, I had switched to the linux-k7 kernel, to take full advantage of my available RAM and such. Everything worked great. The last day the drive was working, an update to the k7 kernel was issued. I don't know if this could affect anything, but it's the only thing I can think of that I did to my system around that time.
I have tried booting the old i386 kernel, but that didn't show the drive anymore either.


Does anybody have any idea what could have caused this and how I can resolve it? All my goodies are on that drive :(
Thank you

---

### Post by NaitoNeko on 2005-08-22
[QUOTE=Rydberg]Hi,
I've been running Hoary for about a month now, and it has been a pretty smooth ride setting it up even though I'm new to Linux.

I have an external 250 GB Maxtor HD harddrive, and up until recently, it has worked very well with Ubuntu. It's connected via firewire to the mobo, and it consists of a single NTFS partition.

A few days ago, it's suddenly not recognized by the system anymore, and won't mount when I switch it on. What could cause this?

I doubt that it's a hardware issue, the drive is still accessible in Windows XP, and appears to be perfectly healthy.

The drive shows up in the Ubuntu device manager, but as an "Unknown Device", and it doesn't provide a whole lot of info.
I've seen in similar threads that one should monitor kernel messages when the device is plugged in, and I've done so, but no messages related to the drive came up. I tried plugging in a USB memory stick, and that worked just fine.

What I did to my system the day it stopped working:
Not much really. A few days earlier, I had switched to the linux-k7 kernel, to take full advantage of my available RAM and such. Everything worked great. The last day the drive was working, an update to the k7 kernel was issued. I don't know if this could affect anything, but it's the only thing I can think of that I did to my system around that time.
I have tried booting the old i386 kernel, but that didn't show the drive anymore either.


Does anybody have any idea what could have caused this and how I can resolve it? All my goodies are on that drive :(
Thank you[/QUOTE]
 Dis you tried to mount it manually ?, do you have it in the fstab file?

---

### Post by Rydberg on 2005-08-22
No I have not mounted it manually and it's not in my fstab. The reason for not having tried this is that I don't know the device name, and since basically nothing happens when it's plugged in, I doubt that it is even assigned one. What can I do to find it out?

Shouldn't hotplug take care of this? It used to, but suddenly stopped! Ah, 'tis the linux experience in a nutshell. ;)

---

### Post by Reb on 2005-08-22
Plug it in and type dmesg in a terminal. You'll see something about a new device. Paste all of that here.

---

### Post by Rydberg on 2005-08-22
Unfortunately I get nothing. It's like it didn't exist.

When I plug in my USB memory stick, I get some output, and it creates an icon on the desktop and all. So at least some parts of the hotplug thingy is working.

I swear this drive is connected and responds perfectly in XP!


Added:
I'm growing increasingly suspicious of the 2.6.10-34.4 upgrade of k7. Was the previous version 34.3? Whatever it was, how can I downgrade and find out if this screwed things up? Is that a good idea anyway? It's strange though that it stopped working in the 386 kernel as well. I've read some in Ubuntu's bugzilla, and there are some similar cases, although older, and there's not a whole lot in there that fixes my problems...

---

### Post by Rydberg on 2005-08-24
I gave up for now, and connected the drive via the slower USB instead of Firewire, which works.
I suppose all I can do is to wait for another update that magically fixes what the last one broke.

I've been thinking about installing the 2.6.11-6-k7 kernel.. But I don't want to remove or break my current 2.6.10-5-k7... How do I install them side by side, so I can choose which one to run in GRUB?

---

