---
title: "64gb Exfat micro sd marked as dirty cant format"
date: 2014-05-19
forum: Hardware
---

### Post by ads2996 on 2014-05-19
Hi,

I am unsure of where this belongs. But the sd card in my phone has been dirty, and i am unable to format it in windows. This is the 3rd card this has happpened to me and aftereach time i have completely wiped my phone and started from scratch. I have never been able to fix the card i just got them replaced by amazon. I am able to copy stuff off but nothing else.

Any help will be greatly appreicated

---

### Post by matt_symes on 2014-05-19
Hi

When you say dirty, what do you mean ?

Is it read only ? Can you check the filing system on it ?

I had a usb pen drive that was read only and i was able to clear the read only flag using hdparm of all things.

Kind regards

---

### Post by ads2996 on 2014-05-19
when i run fsutil dirty query k:
i get drive is dirty

its file system is exfat,i use it in my s3, windows did manage to tell the probelm is a.bmp file which is corrupted and thus the entire card is read only. and the time before it was a video file i think.

---

### Post by ads2996 on 2014-05-19
hdpram looks promising, but i have never used it before or heard of it for that matter.

---

