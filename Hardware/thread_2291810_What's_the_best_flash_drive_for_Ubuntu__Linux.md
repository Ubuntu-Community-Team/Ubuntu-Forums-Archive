---
title: "What's the best flash drive for Ubuntu / Linux"
date: 2015-08-23
forum: Hardware
---

### Post by Old_Printer on 2015-08-23
I have several flash drives, some dating back to only being 66 and 125mb. Sometimes they mount quickly, sometimes not at all. I've performed a FAT format on them and they work for a while. At some point one of them won't launch on one machine, but it'll launch on another. I'd like to have a flash drive that's dependable.

Can someone give me an opinion on what flash drive works the best with Ubuntu / Linux?

Thanks,

Old_Printer

---

### Post by TheFu on 2015-08-23
For me, it is not related to the OS, but the hardware compatibility. Some USB drives just don't like some USB ports. This matters more when looking for USB drives that are bootable. For normal storage, just about any USB3 drive will perform fine.  USB2 drives are slower - noticeably so. I haven't used any USB2 devices in about 2 yrs.

However, the single most important thing for not corrupting the file system on any storage devices is to **always, always, always use the "eject" to umount the storage before removal.**  If you don't do this, caching may not have written everything to the storage when it is pulled.

All of this is anecdotal, not researched and definitely not facts. I only have about 20 USB storage devices, which isn't enough to learn anything.

---

### Post by sudodus on 2015-08-23
> **TheFu said:**
> For me, it is not related to the OS, but the hardware compatibility. Some USB drives just don't like some USB ports. This matters more when looking for USB drives that are bootable. For normal storage, just about any USB3 drive will perform fine.  USB2 drives are slower - noticeably so. I haven't used any USB2 devices in about 2 yrs.

However, the single most important thing for not corrupting the file system on any storage devices is to **always, always, always use the "eject" to umount the storage before removal.**  If you don't do this, caching may not have written everything to the storage when it is pulled.

All of this is anecdotal, not researched and definitely not facts. I only have about 20 USB storage devices, which isn't enough to learn anything.

I think you know what you are talking about ;-)

I would like to add a couple of links with more information about pendrives, flash drives, USB sticks, thumbdrives ...

[Howto help USB boot drives](http://ubuntuforums.org/showthread.php?t=2196858)

[FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by astralnysledz on 2015-08-23
With my USB sticks I noticed the following:
1. Virtually any stick and SD card (because they're also recognized as USB storage devices) will work with Linux (not always the case with BSDs!).
2. Problems related to mounting are in most cases caused by broken partitioning. As TheFu wrote, this may be a result of improper removal of said devices.
3. dd writes some .iso installation images wrongly, though we all know this very basic command is not omnipotent ;).
4. EFI boot on usb sticks complicates a lot.
5. Sometimes USB3 fails, when USB2 has no problems. I encountered this once with a USB3 stick from Toshiba.

I would personally recommend Kingston, though don't expect wonders from cheap, high capacity flash drives. Somehow volume doesn't go well with correctness of read/write.

---

### Post by TheFu on 2015-08-23
I've had cheap flash drives work when name brand ones failed.
I've had expensive drives fail or work depending on the system it is plugged into.

IME, there isn't any way to know in advance which will work or which will not work.

I've also seen where USB2 ports work when USB3 ports on the same machine do not.  Same flash drive used in both.

I haven't found that branding helps or hurts bootability of a flash drive.  However, branding and real specs DO HELP with performance.  Haven't purchased anything less than Class10 SDHC in years. 

Anyway - time to get to a weekly LUG meeting.

---

### Post by Old_Printer on 2015-08-25
Thanks for the replies on this. I really appreciate it. I was able to find some brand name sticks, new, not refurbished, 8g each, for $8 for both online today -- free shipping. The seller has almost 100% feedback. I'm cool with it.

I had been thinking that a low volume size might be more dependable, and when astralnysledz mentioned it, it sounded like good advice. Everything is so inexpensive online today. I can't believe I paid $35 for my 1g flash drive back in 2006. Then again, today a loaf of bread at the big store only costs .84 cents. These are the days.

Old_Printer

---

