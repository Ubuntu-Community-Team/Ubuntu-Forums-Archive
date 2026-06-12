---
title: "wireless not working"
date: 2009-12-01
forum: Hardware
---

### Post by nal13 on 2009-12-01
So I was running 9.04, then upgraded to 9.10 on my HP Mini 1000 and everything was working fine. Then because of something that went wrong, I really don't know what, while trying to setup a dual boot with 9.10 netbook on top of 9.10 desktop, I had to reformat. So I did so, I had another 9.10 SD card handy, I put it in and make sure the wifi worked, it did, then I install it. After I install it, the wireless driver won't load again. I googled it and came up with [this](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP Mini 1000), but that didn't work. I also can't connect to an ethernet, even if I reboot with it plugged in. Am I missing something here? TIA

---

### Post by nal13 on 2009-12-01
I should add that I did go to "Hardware Drivers" and it does say the driver I need, when I hit activate and type in my password, it says downloading and has the scrolling thing going, but it only does that for a few seconds and disappears leaving it saying "This driver is not activated."

---

### Post by n4thanl on 2009-12-01
I don't have an answer, but this happened to me as well. My wireless doesn't work anymore. I even tried downloading the .deb from my windows partition and installing it. Install failed.

---

### Post by nal13 on 2009-12-01
I might just try using 9.04 then upgrading to 9.10, it seemed to work last time. IDK

---

### Post by n4thanl on 2009-12-01
Sounds like a pain in the butt...

---

### Post by nal13 on 2009-12-01
What really confuses me is the fact that I was getting online when testing it out before I installed it. Is this a legal thing with the drivers?

---

### Post by nal13 on 2009-12-01
Where is a good place to d/l 9.04 now? I got an "alternative" version, but that doesn't seem to work.

---

### Post by tonyurso on 2009-12-01
Iam having the same problem! any help on this?

---

### Post by nal13 on 2009-12-01
I guess it's an easy fix, if you can access the internet via ethernet, but we can't. UGH!  Is there a way we could load the drivers on a sd card and install them that way?

---

### Post by beloved88 on 2009-12-01
HP Mini 1101
I had the same issue at first.
You probably have a Broadcom wireless device, use ```
lspci
``` to check.  Then go to broadcom's website and download the appropriate driver.  follow the instructions in the README very carefully, everything is done as root, so just typer ```
sudo -s
``` before you start.  there is one step that is nessisary, that is moving the wl.ko file into your kernel, but the readme is vague about whether you need to do that, because it's under a different step for something else.  there's a nother thread on here somewhere that's in much more detail about all this

---

### Post by nal13 on 2009-12-02
> **beloved88 said:**
> HP Mini 1101
I had the same issue at first.
You probably have a Broadcom wireless device, use ```
lspci
``` to check.  Then go to broadcom's website and download the appropriate driver.  follow the instructions in the README very carefully, everything is done as root, so just typer ```
sudo -s
``` before you start.  there is one step that is nessisary, that is moving the wl.ko file into your kernel, but the readme is vague about whether you need to do that, because it's under a different step for something else.  there's a nother thread on here somewhere that's in much more detail about all this

Thanks, I ended up just loading 9.04 then upgrading.

---

