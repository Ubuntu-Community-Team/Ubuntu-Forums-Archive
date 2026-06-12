---
title: "Boot error"
date: 2011-06-07
forum: Hardware
---

### Post by xecure on 2011-06-07
Not sure If I'm posting in the right place, but i'll give it a shot anyways.


I had arch linux installed on my system, but decided to wipe that out and install ubuntu. Before I went ahead and did that I've installed DSL on a USB (because I've always wanted to try it) and ran DSL for a while. While I was in DSL I decided to delete the arch linux partition (there was only one partition in the hard drive) Afterwards I stick a another USB in my computer with a bootable version of ubuntu and restart my system, pulled out my DSL USB, and this is where my problems start.

When my PC restarted I hit f12 to choose where to boot from and hit the USB option, the I get the error message that says "Strike the f1 key to continue, f2 to run the setup utility"
Hitting the f1 key gives me the message "boot error" and hitting f2 brings up the setup utility (but thats kind of useless to me right now).

When I restart again and let it boot from hard drive as it usually would it gets stuck on a screen that says "boot error". Also tried popping in an old ubuntu CD, and a windows vista CD and tried booting it from those and still received the same error.


Any idea how I can install any OS on my HD right now? 
(I'm dealing with a 10 year old Dell dimension 2400)

---

### Post by jerrrys on 2011-06-07
i know that its not suppose to happen, but i would load something like [gparted live]("http://gparted.sourceforge.net/livecd.php") to see if maybe theres still a boot loader hanging around.  if gparted won't run, i don't know...

---

### Post by xecure on 2011-06-07
> **jerrrys said:**
> i know that its not suppose to happen, but i would load something like [gparted live]("http://gparted.sourceforge.net/livecd.php") to see if maybe theres still a boot loader hanging around.  if gparted won't run, i don't know...
Ok so I just tried that and I am able to get into GParted. I saw that there were no partitions in my HD so I created one and restarted with ubuntu in my USB stick. But I still get a boot error when doing this. Anyway to install ubuntu from GParted live?

---

### Post by jerrrys on 2011-06-07
gparted is not a ubuntu installer and cannot be used for that.

now if i understand correctly, your gparted live usb is working and finding nothing.  but your ubuntu live usb will not boot.

if this is so, can you try this ubuntu flash on another computer?

---

### Post by xecure on 2011-06-07
> **jerrrys said:**
> gparted is not a ubuntu installer and cannot be used for that.

now if i understand correctly, your gparted live usb is working and finding nothing.  but your ubuntu live usb will not boot.

if this is so, can you try this ubuntu flash on another computer?
Just tried the USB on another laptop and it works fine, any other ideas?

---

### Post by jerrrys on 2011-06-07
insert both DSL and ubuntu flash drives and attempt a boot

---

