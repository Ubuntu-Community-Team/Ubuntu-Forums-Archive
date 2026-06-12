---
title: "SD Card slot not detected"
date: 2011-08-08
forum: Hardware
---

### Post by Erdr1ck on 2011-08-08
I just got a new Asus eeepc - a 1215 - and wiped it clean and installed a Windows/Linux dual-boot with no problems.  However when I went to transfer all of my old data from my old eee to the new via the SD card slot, it didn't auto-detect like it used to on the old system.  

So I dug around and noticed that it wasn't even registering the existence of the SD card/slot in fdisk.  Based on some other users issues with SD card readers in other laptops, I tried adding tifm_sd to /etc/modules, but that didn't help either.

Can anyone suggest other ways to get Ubuntu to recognize my built-in SD card slot?

-Erdrick

---

### Post by Erdr1ck on 2011-08-09
Based on some other users problems, I ran lspci and found nothing remotely resembling an SDcard slot or reader.  Maybe the system doesn't recognize the hardware?

Any suggestions would be welcome

/b/

---

