---
title: "[beagleboard XM] resolution not supported when connecting through HDMI/DVI"
date: 2012-11-26
forum: Hardware
---

### Post by aagavin on 2012-11-26
When I install ubuntu onto the SD card and connect and plug my beagleboard into my TV I get a resolution not supported message.

Any way to fix this?

Thanks

---

### Post by h3nr1ke on 2013-02-08
Hello guys... its an old post but I'm facing the exactly problem... does any body knows what happens? or what should I do?

thanks in advance

---

### Post by aagavin on 2013-02-08
No one seems to know any way to fix this. :(

---

### Post by schmidtbag on 2013-03-10
i too am getting a problem with this on my tv.  s-video works but once the gui initializes it kicks on dvi again and i cant get it to stop doing that

---

### Post by crvella on 2013-06-27
I'm using the beagleboard XM

I use the DVI out.  I am using a HDMI to HDMI to plug into my TV.

My TV (when using HDMI cable) will not accept anything less than 1920x1080.

BeagleBoardXM does not support this resolution, but if you edit the file

/boot/uboot/uEnv.txt and set the dvi mode to 1920x1080, it will work on your TV.  THere will just be some clipping.  That said, I have seen somewhere where you can set an 'offset' so the can counter the clipping.  Can't remember where I saw the offset now.

---

### Post by schmidtbag on 2013-06-27
I'm 90% sure I've tried that already, at multiple refresh rates and it still won't work.  My TV supports 1080p @60Hz, 24Hz, 30Hz, and 1080i so there's no reason this shouldn't work.  Beagleboard is the only digital-signal device I own (of 5 devices) that doesn't work on my TV.  However, it does work on older DVI-only monitors.

---

