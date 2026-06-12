---
title: "How to get Ubuntu to recognize more than 1 external HDD"
date: 2012-03-11
forum: Hardware
---

### Post by The Bright Side on 2012-03-11
Hey guys!

I bought a second external hard drive yesterday. Now I did the following steps:

1. Connect my old external HDD via USB
2. It shows up and mounts properly as "ExHDD1" in Nautilus
3. It shows up as sdc in gparted
4. Connect my new external HDD via USB in addition
5. It doesn't show up in Nautilus or gparted

So that sucks. So I tried it the other way round:

1. Connect my new external HDD via USB
2. It shows up as "Unknown" in Nautilus (not mounted, of course. It's unformatted)
3. It shows up as sdc in gparted
4. Connect my old external HDD via USB in addition
5. It doesn't show up in Nautilus or gparted

What am I doing wrong? Any ideas? I would really like to use both my external hard drives. When I connect a USB key with anything else connected at the same time, it always shows up and mounts properly.

---

### Post by 2F4U on 2012-03-11
Are you doing this on a laptop or PC? Are the hdd's externally powered or through the usb port? It may be that the machine cannot provide enough power to get both hdd's working. Are there any error messages in the log files?

---

### Post by The Bright Side on 2012-03-11
Hey, I found the problem and it had nothing to do with Ubuntu. I was using the wrong power supply on the USB enclosure, thus frying the drives. Expensive week coming up.

---

