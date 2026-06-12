---
title: "RAID 1 rebuild"
date: 2008-08-19
forum: Hardware
---

### Post by brad8266 on 2008-08-19
Quick question. I am working on a machine that has hardware based RAID 1 running on it. One of the drives was accidently unplugged and the machine was booted up. Once it was noticed that the one drive was unplugged it was plugged in and when booted up it says that the array is in degraded state. How do I get it back to optimal state, all synced back up??

It is LSI Logic Megaraid hardware raid 1.

---

### Post by Loaded.len on 2008-08-20
You probably have an option in the RAID BIOS to rebuild the array.

I think on that controller you get into the RAID BIOS with CTRL-M during POST

---

### Post by brad8266 on 2008-08-20
> **Loaded.len said:**
> You probably have an option in the RAID BIOS to rebuild the array.

I think on that controller you get into the RAID BIOS with CTRL-M during POST

Yes I got in there but I am unsure of what options to use to rebuild it while keep all of the data intact. It wont wipe anything will it?

---

### Post by Potatoj316 on 2008-08-20
it shouldnt but im not too familiar with RAID.  if you can specify what drive is the one to update than it should be fine, but if it is looking for a blank drive to update to than I dont really know.  if you can back up your files first to another drive that might be a good idea.  but the best idea would be to read the manual, they usually know what to do.  if you dont have the manual you probably can ask google, it is usually rather cooperative with finding stuff like that.

---

### Post by brad8266 on 2008-08-20
Well i tried to sync them and the raid program wiped both hard drives out so i am royally screwed at this point. This was a server2003 machine with lots of stuuf that was needed. What are my options at this point for data recovery? Can the drive be repartitioned at all or anything?

---

