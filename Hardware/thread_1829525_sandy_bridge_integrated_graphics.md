---
title: "sandy bridge integrated graphics"
date: 2011-08-20
forum: Hardware
---

### Post by s3gfault on 2011-08-20
I've recently installed kubuntu 11.04 amd64 onto my new Intel core i5-2400 based computer and seem to be having some problems with the integrated graphics.  The install went OK (except that some of the windows in the installer were not rendered correctly).  The computer will boot just fine into kubuntu and will load the desktop.  Soon after loading the desktop though, the computer will slow almost to a halt, then the monitor will blink on and off maybe three or four times, then the desktop will lock up.  The mouse cursor will still move but nothing responds.  I can use Ctrl-Alt-F1 to bring up a console, but can't switch back to the desktop (and trying to do so will lock up the console too).

hardware:
```

1 x BIOSTAR TH67+ LGA 1155 Intel H67 HDMI SATA 6Gb/s USB 3.0 Micro ATX Intel Motherboard
1 x Intel Core i5-2400 Sandy Bridge 3.1GHz (3.4GHz Turbo Boost) LGA 1155 95W Quad-Core Desktop Processor BX80623I52400
1 x G.SKILL Ripjaws Series 8GB (2 x 4GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model F3-12800CL9D-8GBRL
1 x WDC WD2500BEVS-60UST0 250GB SATA HDD

```

Any advice?
Thanks

---

### Post by sbraz on 2011-08-20
[http://ubuntuforums.org/showthread.php?t=1822629](http://ubuntuforums.org/showthread.php?t=1822629) (VERY long thread)
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374) (other fixes for sandy bridge)

---

### Post by s3gfault on 2011-08-20
> **sbraz said:**
> [http://ubuntuforums.org/showthread.php?t=1822629](http://ubuntuforums.org/showthread.php?t=1822629) (VERY long thread)
[http://ubuntuforums.org/showthread.php?t=1817374](http://ubuntuforums.org/showthread.php?t=1817374) (other fixes for sandy bridge)

Thanks sbraz, those were the same two threads I found yesterday too.  I should have mentioned it in my first post.  I tried adding acpi_osi=linux pci=noacpi to the kernel boot params as razorxpress suggested in that second link you posted, but it didn't help.  The first thread you mentioned the user is having a different problem than I am, something about power consumption.

I think I will try to install the 3.0 kernel and see if it helps.

---

### Post by s3gfault on 2011-08-20
> **s3gfault said:**
> I think I will try to install the 3.0 kernel and see if it helps.

Yes, that did work.  There is a little tearing along the edges when I drag the window, but nothing I can't live with.

---

### Post by sbraz on 2011-08-20
> **s3gfault said:**
> The first thread you mentioned **the user is having a different problem than I am**, something about power consumption.

I think I will try to install the 3.0 kernel and see if it helps.
yes and no, he had problems about graphics and switched to kernel 3.0 to solve them but ran into some power issues.

if you notice your pc running hotter with kernel 3.0, boot with **i915.i915_enable_rc6=1**.

---

