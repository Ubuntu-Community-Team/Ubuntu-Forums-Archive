---
title: "Mounting Dell DJ HDD"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by BitTorrentBuddha on 2006-02-13
Is there a way to mount the hard disk inside my mp3 player, [dell dj 30 gen 2], as a hard drive so that I can take from and write to the disk?
or is there some other way to get a driver working on it?

---

### Post by encompass on 2006-02-14
from looking here... [HTML]http://www.linuxquestions.org/hcl/showproduct.php?product=1808[/HTML]
It says the is it just a nomad  and try installing gnomad```
sudo apt-get install gnomad2
```  See if that works for you...  Please report your success..

---

### Post by BitTorrentBuddha on 2006-02-14
still no such luck, but the output from lsusb shows that it isn't even recognized by the computer... so I'm thinking maybe I did something to my mobo, [removed some USB jumpers :-| for no apparent reason], and if I try replacing them I can get it... unless there's another way to test to see if your USB ports are working properly...

---

### Post by encompass on 2006-02-14
Tot test you Motherboard try plugging in a mouse... Thats how I test it... it doesn't test for USB2 but it will test if it works.
BTW I know how you feel having a 30gb HD I have one too and I own a P4 3ghz.

---

### Post by BitTorrentBuddha on 2006-02-14
and should the issue arise of not owning a USB mouse?

---

### Post by BitTorrentBuddha on 2006-02-14
actually, I found a USB christmas tree I got a while back, and no power = \ so is this fixed by putting the jumpers I took off the USB pins while building it?

---

### Post by BitTorrentBuddha on 2006-02-15
bump :-#

---

### Post by BitTorrentBuddha on 2006-02-15
ok, got the USB jumpers back to where they were, tried hooking up the DJ and still nothing detected in gnomad or lsusb... does anybody know how to fix this? It's the only thing tying me to windows at the moment...

---

### Post by encompass on 2006-02-16
[QUOTE=BitTorrentBuddha]ok, got the USB jumpers back to where they were, tried hooking up the DJ and still nothing detected in gnomad or lsusb... does anybody know how to fix this? It's the only thing tying me to windows at the moment...[/QUOTE]
Sounds like the USB device is not working... lsusb should give you something... Have you checked the device with the HAL device manager? (System--->Administration...)  If you can't see the device it sounds liek a hardware issue.  Let's make dead sure it is not that before movie on.  IMOA

---

### Post by BitTorrentBuddha on 2006-02-16
The USB stuff shows up in device manager but when I plug things in I don't get power to them...

---

### Post by encompass on 2006-02-16
Gosh I am stumped, but google doesn't seem to be...
[http://forums.us.dell.com/supportforums/board/message?board.id=dce_djmusic&message.id=3170](http://forums.us.dell.com/supportforums/board/message?board.id=dce_djmusic&message.id=3170)
try that one...

---

### Post by BitTorrentBuddha on 2006-02-16
so, the version of libnjb in synaptic is just outdated and I need to compile from CVS?

---

### Post by encompass on 2006-03-05
and this DJ worked in windows without the USB working?  I am confused...

---

### Post by BitTorrentBuddha on 2006-03-05
well, I'm thinking it's the usb ports on this computer (the windows box is my old computer, just built this one)

---

