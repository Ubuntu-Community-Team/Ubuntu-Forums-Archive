---
title: "Shouldn't 700MHz be enough to play a DVD on my computer?"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by daller on 2005-11-12
Hi There, 

I'm trying to figure out, what's wrong with the pc, I just puit together... 

Kaffeine play DVD's a little slowly! 

Here are the specs: 
700 MHz AMD Duron 
256 MB Ram 100 MHz 
60GB Harddisk 
ATI Radeon 9200 PRO (The cover says 9250) 

I have activated DMA: 

nikoline@ubuntu:~$ sudo hdparm 

/dev/hdd /dev/hdd: 
IO_support = 1 (32-bit) 
unmaskirq = 1 (on) 
using_dma = 1 (on) 
keepsettings = 0 (off) 
readonly = 0 (off) 
readahead = 256 (on) 
HDIO_GETGEO failed: Invalid argument 

Any ideas? 

Edit: I tried the "ati"-driver instead of "fglrx" (dropping from 140 fpsm, down to 70 :) - But the DVD playback got better...) 

Any ideas on how to get 3d-acceleration, without breaking DVD playback now?

---

### Post by ssam on 2005-11-12
have you tried a few different players, xine, ogle, vlc, mplayer?

700 mhz is probably just about fast enough to play it in software with a will optimised player.

---

### Post by xequence on 2005-11-12
I have a 701 mhz processor and I played a 700 MB dvd quality movie file, I think it was Xvid. Every 20 minutes or so it would get a little out of sync, so I just pressed stop and fast forwarded to the place where I left off. It was quite watchable. I dont know if it would be any different with an accual DVD though.

---

### Post by daller on 2005-11-14
I even tried a DivX, and it was even worse!

With the "ati" driver - everything is great, just no 3d-acceleration.

Maybe the gfx isn't good for this pc? (too new?)

---

### Post by elempoimen on 2005-11-14
nevermind...didn't catch that you'd activated dma

what screendepth are you running...24bit or 16bit?

---

### Post by daller on 2005-11-14
[QUOTE=elempoimen]nevermind...didn't catch that you'd activated dma

what screendepth are you running...24bit or 16bit?[/QUOTE]

24... Is that a problem?

---

### Post by elempoimen on 2005-11-14
You might want to try 16.  It seems quite a bit faster to me.  If a slow DVD is your problem, that could fix it.

---

### Post by darrenrxm on 2005-11-15
Im not sure if this will help (this is more of a temp fix.) But you might want to try geezbox linux live cd. It's basically mplayer as a livecd. But be warned it is a **huge** 6meg download. And it will take nearly 5 seconds to burn to a cd. Also, they say you need around a 400mhz pentium 2 with 64 megs of ram. So, I would assume it could smoothly play your dvd's on your computer.

You should try out vlc if you want a low power media player. On windows it only uses 5% cpu on my system. I've been meaning to try it on ubuntu, haven't gotten around to it yet.

---

### Post by hil on 2005-11-22
I tested my DVD on both Kaffeine and xine. Kaffeine deactivated the DMA of the CDROM drive every first time I ran it after boot. xine did not have that problem. Check after you start Kaffeine. DMA might be deactivated.

---

### Post by michael_salcher on 2005-11-22
try installing mplayer and try out all video output drivers (usually "xv" is the fastest)

---

### Post by Kannisto on 2005-11-22
If you get something like 140 fps in glxgears something is wrong 
with your 3d acceleration. I get around 2000 with the same card 
My processor is 2400 sempron, but the glxgears isn't cpu limited.

---

### Post by SickTwist on 2005-11-22
Also, make sure that you are running an optimized kernel for your processor instead of the default i386 kernel. There are many threads explaining how to do this for your AMD Duron.

I have sucessfully played DVDs on a PII box (using Ogle in XFCE with X running in 16 bit color) so you should be able to pull it off with your hardware.

---

