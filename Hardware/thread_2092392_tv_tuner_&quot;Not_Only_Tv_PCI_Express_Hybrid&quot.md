---
title: "tv tuner &quot;Not Only Tv PCI Express Hybrid&quot;"
date: 2012-12-07
forum: Hardware
---

### Post by okurde on 2012-12-07
I really don't know what to do. Tutorials, advice or discusions I have found were about other tv tuner cards and not helpful at all, aven if the tuner card had the same chipset. 

TVtime gives me a message that there is no such directory as /dev/video0.
There are no other elements with "video" in name in /dev/. It works great on WindowsXP but I never had it working on lany Linux.

device details: 
"Not Only Tv PCI Express Hybrid" 
model: LV8H
chipset: Conexant CX23885
[SIZE=2]it's both an analog and dvb-t tuner
system[SIZE=2]:[/SIZE] Ubuntu 12.10 AMD64
[/SIZE][SIZE=1][SIZE=2]when I use [/SIZE]lspci -v[/SIZE] it seems that the device is detected by the system.

[SIZE=2]02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
    Subsystem: Conexant Systems, Inc. Device ec80
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fb000000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: <access denied>
    Kernel driver in use: cx23885
    Kernel modules: cx23885[/SIZE]

someone adviced me this might contain useful information

/var/log/dmesg
[http://pastebin.com/raw.php?i=V8s9nVTT](http://pastebin.com/raw.php?i=V8s9nVTT)
lspci -vn
[http://pastebin.com/raw.php?i=xFxK11M2](http://pastebin.com/raw.php?i=xFxK11M2)

---

### Post by gordintoronto on 2012-12-07
Try this:
[http://askubuntu.com/questions/50006/getting-a-conexant-cx23885-tv-capture-card-working](http://askubuntu.com/questions/50006/getting-a-conexant-cx23885-tv-capture-card-working)

It seems to say the card is /dev/dvb

And it suggests a very recent kernel, which you might find in Xubuntu 12.10,

---

### Post by okurde on 2012-12-08
Using: ~$ tvtime --device /dev/dvb made no difference.
No such directory as /dev/dvb

ls /dev [http://pastebin.com/raw.php?i=Kpd3RGuL](http://pastebin.com/raw.php?i=Kpd3RGuL)

also, I had Ubuntu 12.10 installed and  the same problem. Will Installing Xubuntu 12.10 make any difference?

---

### Post by gordintoronto on 2012-12-08
I'm pretty sure Ubuntu 12.10 and Xubuntu 12.10 use the same kernel. Was the kernel 3.5.5 or higher?

---

### Post by okurde on 2012-12-09
I've installed Xubuntu 12.10 (I wanted to try Xfce anyway) and "uname -r" says this:
3.5.0-19-generic

tvtime still not working.
No such directory as /dev/dvb
No such directory as /dev/video0

---

### Post by gordintoronto on 2012-12-09
You could try "the cutting edge": [http://cdimage.ubuntu.com/xubuntu/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)

That's a very early version of 13.04.

---

