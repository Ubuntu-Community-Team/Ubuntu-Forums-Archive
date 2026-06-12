---
title: "mic (and webcam) on an hp dv6700t laptop"
date: 2008-11-30
forum: Hardware
---

### Post by punkbohemian on 2008-11-30
I have a hp dv6700t laptop with an integrated mic and webcam and neither are working with ubuntu 8.04. I'm not even sure where to start to fix this, other than read that 10,000 page guide I've heard about. There must be an easier way, can someone point me in the right direction? Thanks.

---

### Post by sergiom99 on 2008-12-01
mine worked out of the box in Kubuntu 8.10. plese post the output of the lsusb command typed in a console shell. there you'll see your camera specs and then we can try to find a way to make it work.
Did you tried cheese?
```
sudo apt-get install cheese
```
Its a program to use your cam.

---

### Post by punkbohemian on 2008-12-02
It turns out my webcam was working fine (I do have Cheese), though my mic still isn't capturing sound. I did a test call in Skype as well as tried to record a test using the basic sound recorder. I went into my volume panel to make sure it wasn't accidentally muted (it isn't), and my sound settings are set to ALSA for sound capture (like everything else).

This is what i got from the lsusb command.

Bus 007 Device 003: ID 0c45:62c0 Microdia 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

What's next? Thanks.

---

