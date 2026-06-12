---
title: "USB Device Detection Problem"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by Zilphanael on 2008-01-19
I have an mp3 player which I'm trying to edit the contents of on my Gutsy laptop.  lsusb detects the device, but fdisk -f doesn't.  I tried the obvious address, /dev/sdb1 (my hard drive uses /dev/sda), but no dice. So I saved an ls of /dev without the device, plugged it in, and then saved another ls of /dev.  I diff'ed the two, and this is what I got:
```
20a21
> libmtp-usbdev3.11
668a670,673
> usbdev3.11_ep00
> usbdev3.11_ep01
> usbdev3.11_ep81
> usbdev3.11_ep82

```
Now what do I do?

---

### Post by kidders on 2008-01-20
Hi there,

Those device nodes are USB endpoints (ep00, ep01...) and a Media Transfer Protocol interface. Your media player doesn't seem to support mass storage mode (ie hard disk emulation), which is a more open, conventional way of communicating with computers.

Unless you can find a way to make your media player talk like a mass storage device, you'll need specialised software to communicate with it. Unfortunately, MTP is something I know *nothing* about, but a web search for "libmtp" seemed to turn up some promising results ... including some pages from this forum. Apparently, it's some sort of Microsoft concoction.

Depending on the amount of reverse engineering involved in getting MTP devices working in Linux, and how closely your media player adheres to the MTP specification, you should be able to get some degree of functionality out of it. I'd be very interested to know how much success you have.

---

### Post by Papa-san on 2008-01-20
It is a Microsoft concoction... It takes the 'sync' software that came with it. As yet, I am unable to get it to work without doing it on my wifes' windows box. I've even tried to replace the firmware with an older style, but it's still a no-go. I'll keep working on it and will check back here as well...

---

### Post by Zilphanael on 2008-01-21
Well, I don't know if the mp3 player TALKS like a mass storage device or not, but its name when it's plugged in includes the words "mass storage device", and on my Windoze computer I can edit the files (kinda, there are some issues) in Windoze Explorer without the software.  It's honestly not enough of a big deal for me to try to reverse-engineer my way into getting a Microsoft standard working (heh, using "Microsoft" and "working" in the same sentence hurts a little) on Linux, especially since I know virtually nothing about the system still.  Thanks for the help though.

---

### Post by kidders on 2008-01-21
> **Zilphanael said:**
> It's honestly not enough of a big deal for me to try to reverse-engineer my way into getting a Microsoft standard workingOther people will have done that part already, I assume.

---

### Post by Papa-san on 2008-01-22
> **kidders said:**
> Other people will have done that part already, I assume.

Not that I have found. I have a Creative Zen, and I haven't found anyone with it working thru Ubuntu 6.06. (Edgy, Feisty, and Gutsy don't work on my laptop, except for me to do a full install. The upgrades won't work. I'm waiting to receive my install discs...) And with that, the success I have found is minimal...

---

