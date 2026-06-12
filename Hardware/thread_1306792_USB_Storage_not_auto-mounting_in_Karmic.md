---
title: "USB Storage not auto-mounting in Karmic"
date: 2009-10-30
forum: Hardware
---

### Post by plb on 2009-10-30
I've attached a USB storage device to my laptop (Acer Aspire 5735) and it does not auto-mount as it use to in 9.04.  Also noticed the sdcard reader doesn't seem to function as it use to either. Fresh install of Ubuntu 9.10.

---

### Post by ldjuda on 2009-11-01
> **plb said:**
> I've attached a USB storage device to my laptop (Acer Aspire 5735) and it does not auto-mount as it use to in 9.04.  Also noticed the sdcard reader doesn't seem to function as it use to either. Fresh install of Ubuntu 9.10.
I had an issue where my SDCARD was not mounting. In order to get the sdcard to mount type the following command in console...

```
sudo modprobe tifm_core
``````
sudo modprobe tifm_sd
``` Then go ahead and insert your sdcard. Good luck!

---

### Post by wired99 on 2010-03-31
Thanks for the info, this helped me a great deal.

I had a similar problem with my mp3 players not mounting nor even being recognized by Ubuntu Karmic (although it had no problem mounting my PSP)

I read many posts with no success.

I tried the following command:

sudo modprobe tifm_core

then I plugged my little 2G ipod shuffle and it was automatically mounted by Karmic.

I have a question (if anyone is still reading this post)
after running the "modprobe tifm_core" command I got the following warning:

"WARNING: All config files need .conf: /etc/modprobe.d/bad_list, it will be ignored in a future release."

what does this mean? Is there something specific I should be looking for as the system updates?

---

