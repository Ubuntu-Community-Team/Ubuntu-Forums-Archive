---
title: "Netbook Remix Dell Mini Can't Boot From Image"
date: 2009-04-23
forum: Hardware
---

### Post by jlhughes on 2009-04-23
I've followed the steps and downloaded the netbook img remix and loaded it on to a thumb drive using ImageWriter. (I did this work on my Ubuntu desktop machine.)

I stuck the thumb drive in the Mini and pressed 0 to get to the boot menu.  I selected "Removable Drives" and hit return.

The screen shows:

SYSLINUX 3.53 Debian-2009-03-09 EBIOS Copyright blah blah blah 
Loading . . . __

And nothing happens.

Is there a way to test the image?  I've tried booting from a full-size laptop and get the same result -- Loading . . . 

Ideas?

---

### Post by HankB on 2009-04-23
> **jlhughes said:**
> 
Is there a way to test the image?  I've tried booting from a full-size laptop and get the same result -- Loading . . . 

Ideas?

I've done a bunch of loads using thumb drives and various flavors in the last couple days. Two things burned me.

1. Freshly format your USB stick before you start. Some tools will silently run out of space and leave empty/missing files on the USB drive.

2. Check the downloaded image before you load. I had problems and found that one of my images (fetched via bittorrent) was about 1/2% short of being complete. It booted but installation failed. Check ths images using md5sum. (If you're burning your thumb drives on Windows, you can load the cygwin tools to get md5sum.)

I suspect the first issue is giving you grief.

HTH,
hank

---

