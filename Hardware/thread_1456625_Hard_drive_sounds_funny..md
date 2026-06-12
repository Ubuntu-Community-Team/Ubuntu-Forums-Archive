---
title: "Hard drive sounds funny."
date: 2010-04-17
forum: Hardware
---

### Post by primusx86 on 2010-04-17
Hello. I have a hard drive and it sounds funny under Ubuntu Karmic, but in Windows 7 it has little sound. Under Ubuntu it has a clicking sound. I ask if anyone can explaine this to me:)
Model Family:     Western Digital Caviar Second Generation Serial ATA family
Device Model:     WDC WD5000AAKS-00YGA0

I actualy edited  /etc/hdparm.confby adding:
/dev/sda {
        apm = 254
}

at the end of the file,but no success.

---

### Post by nitstorm on 2010-04-17
I have a similar problem with my Seagate External HDD . Until I used it with Ubuntu it didn't click but once I used in with Ubuntu a few times it started clicking and the clicking noise continued even when I was in Windows

This won't mess up the drive will it? That's the main concern....

---

### Post by primusx86 on 2010-04-17
well it could result in a shorter HDD life. About 2 years less or something like that. I am just speculating. But the sound is not normal. So I hope someone can solve it. I cannot, I have too little knowlege :(

---

### Post by replica2010 on 2010-04-17
I've noticed this as well, with 250gb WD sata drives (4x, raid). However, the only time I've heard it is when updating grub.  Disabling the os-prober a few days ago *seems* to have fixed it for me.  I too, would like to know what (and why) Linux is doing with regards to this.

---

