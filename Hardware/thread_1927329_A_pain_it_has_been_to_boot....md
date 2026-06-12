---
title: "A pain it has been to boot..."
date: 2012-02-17
forum: Hardware
---

### Post by LiteDrive on 2012-02-17
From the USB on my Asus P8Z68-M PRO. I am without a CD or DVD drive in my tower, else I would be using this instead. As far as using a USB drive, it works fine, however when I try to boot from UEFI, all that happens is my screen goes blank and, if I'm lucky, it just reboots. Otherwise, I have to restart the computer manually.

I JUST bought this custom tower, and was able to boot a different USB fine (with Windows 7), though the USB was my friends so I don't have access to it anymore. When I boot straight from the USB (i.e., without UEFI), I wind up getting a bunch of "Asking cache for write data failed" errors, and then it just stagnates at that. The initial splash screen loads fine, but that's the best if anything. I've tested this drive on my laptop and it works perfectly fine without any issues. Is there any hope at all for this? Is my 4gb usb drive considered obsolete with my motherboard? Should I use my external HDD instead? If possible, I'd like to just boot off of the USB.

Note: the version I'm trying to install is 11.10.

---

### Post by wolfen69 on 2012-02-17
Disable the ASMedia SATA in BIOS first.

---

### Post by LiteDrive on 2012-02-17
Thank you, but how exactly do I do that? And will that disable my hard drive (which is SATA 6)?

---

### Post by wolfen69 on 2012-02-17
It won't disable your hard drive. You'll have to find it in the BIOS. That's how other people have gotten it to work.

---

### Post by LiteDrive on 2012-02-18
After doing this, I've lost access to my hdd and have received the following output:

```
Write protect is off
Mode Sense: 03 00 00 00
No caching mode page present
Assuming drive cache: write through

Attached SCSI removable disk
```

And then it just stops there and does nothing...

Is it even possible to boot a Linux system with this motherboard?

---

### Post by xiaokaige on 2012-02-18
You need to disable ASMedia SATA in your BIOS.

---

### Post by wolfen69 on 2012-02-18
According to the reviews on newegg.com, that's what it took to get it to install linux. Do you have a graphics card installed? I see that it uses switchable graphics.

---

### Post by LiteDrive on 2012-02-18
The only issue is that I'm not sure exactly what ASMedia is. I was able to get it to work with Wubi, but this was after setting my SATA mode to Raid and disabling the HDD status SMART Check.

Edit:

Yes, I do have a graphics card - Nvidia GTX 550i or something like that.

Edit 2:

Actually, Ubuntu refuses to boot. It will lead me to GRUB with Wubi, and then it simply stops at a blank purple screen...

I also believe that before all of this I had already disabled ASMedia, but even with a few Google searches, it's hard to actually understand what ASMedia actually is. Can someone explain?

---

### Post by LiteDrive on 2012-02-18
I should also note that the only way to get it installed was through teh ACPI workaround. Now, despite the fact that it's installed, it refuses to boot. Ontop of that, recovery mode does the same exact thing.

---

### Post by misterbk on 2012-02-21
I'm investigating compatibility for this board too.  (Pre-purchase, as I have learned is best...)

The ASMedia SATA is an extra 6GB/s SATA port.  Notice most boards have two, and this one has three.  <EDIT:> I believe the Intel chipset provides two 6GB/s SATA ports, and either one of...  [1] ASMedia may have an implementation that people believe is faster (has been suggested by searches) or [2] ASMedia may provide a nice cheap integrated controller chip that can provide more ports by connecting internally to PCIe lanes.

What you are trying to do (if you haven't) is disable the ASMedia SATA controller.  This should (?) work similarly to how you can disable the SATA controller or PATA controller (or audio chip or onboard LAN etc.) in the bios in any type of motherboard.

Unfortunately finding someone who also has this board and is running Ubuntu on it and is active on this forum might be hard, so you'll have to put your own skills to figuring out where this option is.

---

