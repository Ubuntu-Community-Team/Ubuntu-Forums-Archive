---
title: "No usb in HP laptop with 64-bit 8.04 installed"
date: 2008-06-28
forum: Hardware
---

### Post by Altur on 2008-06-28
I installed the x86 64-bit version of Ubuntu last week (had been using 32-bit) on my Hp pavillion laptop (dv6604nr for some information.) and I've loved it so far, pretty painless install and setup. I have been using Ubuntu as my primary OS for about a year now, but am still not quite good enough to figure out some of this on my own. I'm having issues getting any of my usb devices to work with my Laptop. My mouse, keyboard, and printer will not work with the machine, nor any other usb devices I try to connect after the first 30 seconds after boot. I don't know where to look to find any more information (error codes, outputs or anything). I have reinstalled Ubuntu and still no luck.

I have tested my devices, and they all work in OpenSUSE 11, and with Vista.
I posed this originally on the x86-64 forums, but I may get more response over here.

---

### Post by phen on 2008-06-28
try the following: 
1. open terminal from the applications menu
2. connect a usb device
3. please type

```

dmesg

```

4. post the output here, not everything but the last couple of lines. everything with USB in it

5. leave the usb device connected and type
```

lsusb

```
which gives you a list of usb devices.

6. last step: type and paste into this thread:
```

lspci

```
(LiSt PCI devices) so that we can check for usb controllers.

---

### Post by Altur on 2008-06-29
Thanks very much for the post, but I actually fixed my problem.  After running the command you gave me in step 3 i noticed a few things loaded from the edited rc.local script [this page]("https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr)#head-f089ea2173c5de043ea747d2d8d1da1e25ca8e67") had me load to make my wireless drivers work that I ended up not needing (b43 worked fine for me) so I went in and removed those edits and everything worked much better for me.  I'm typing this from the USB keyboard I've been trying to connect.  It works fine and I've unplugged and replugged it in just to make sure.

Again, thanks for the help, I probably would never have figured it out if it weren't for you and would have just been angry with my laptop.

---

