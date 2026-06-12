---
title: "HP DV2037us"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by jeffdeloach on 2006-09-05
Has anyone had success in getting the webcam to work on a HP DV2037? If so please help!!! Maybe if not, can you tell me how to find out what drivers are needed for my laptop.

---

### Post by potterzot on 2006-09-08
You can try using the spca5xx driver.  It works with many other versions that are very similar.  Do a 'sudo lsusb -v' to get the hardware code.  I've just gotten one of these myself, but the driver doesn't seem to work for this webcam yet.  You might just have to wait for new releases.

The hardware address is 0c45 (Microdia) and 62c0 it's got a sonix processor, and looks like microdia made the sensor.  Sonix has some spec's on their website, but I'm not sure how to proceed.  I've modified the source for spca5xx to include 62c0, and added the necessary functions, but without memory addresses and stuff that I don't really understand, I can put the right values in...guess we will have to wait.

Also, my laptop refuses to come out of sleep or hibernate.  Have you managed to get it working?  How about the mic?  I think the mic may be on the same chip as the webcam...

---

### Post by jeffdeloach on 2006-09-09
Thanks for the info. My mic does not work, I have not fooled with that yet. My laptop seems to wake up just fine, I haven't done anything. I installed Dapper, and all works except the webcam and mic that I know of so far.

---

