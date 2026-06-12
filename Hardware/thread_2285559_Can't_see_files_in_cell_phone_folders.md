---
title: "Can't see files in cell phone folders"
date: 2015-07-06
forum: Hardware
---

### Post by rva1945 on 2015-07-06
Hi:

As soon as I plug the phone a window pops up, I choose the option Open Folders, I see the folders but they appear as empty while there are files, for example, pictures in DCIM folder (I see them when starting in Windows 7).

Any ide of what I'm doing wrong?

Thanks

---

### Post by dino99 on 2015-07-07
it could be related to the chmod settings set for these folders

---

### Post by rva1945 on 2015-07-11
And how to?

As soon as I plug the phone, the window opens and I see the folders. It appears as GT-S5310L, but I can't find it while listing folders in Terminal.

I understand I should chmod (parameters?) to see the files (videos, pictures, etc.).

---

### Post by Vladlenin5000 on 2015-07-11
GT-S5310L is, supposedly, a Samsung Galaxy Pocket Neo GT-S5310...
Which Android version are you currently running? Original Android 4.1, official update (which version?) or third-party (community) ROM?

---

### Post by rva1945 on 2015-07-11
Android 4.1.2

I listed dev folder, and if the cell is connected, a serial folder appears.

I tried

chmod -w -R serial
but I get
chmod: changing permissions of `serial': Operation not permitted
chmod: changing permissions of `serial/by-path': Operation not permitted
chmod: changing permissions of `serial/by-id': Operation not permitted

---

### Post by Vladlenin5000 on 2015-07-11
If I remember correctly (it was a long time ago... ;-)), Android 4.1 still used the old mass storage device profile - newer Android versions adopted MTP/PTP. So, assuming I'm correct you should explicitly allow that from the phone's dropdown menu.
If however it uses the MTP/PTP you'll need, from the same menu to toogle those modes:
PTP gives you access to the camera's folder and that folder only.
MTP gives you access to everything else.

Obs.: It works perfectly with my Meizu MX3 and it always did (MTP/PTP) but I've heard many users complaining about it with other phones.

---

### Post by rva1945 on 2015-07-11
As soon as I selected that mode in my phone, the files showed up...but my had added a sdcard to it, where the pics and vids are stored, and it is now shown as empty, not even the folders are seen.

Well, I can copy the files from the extsdcard to the sdcard (internal), but I'd like to see the files stored in the external extsdcard.

Question: what's Galiza Naçao?

---

### Post by Vladlenin5000 on 2015-07-11
Not entirely unexpected that external SD behaviour. I can't test/reproduce it because Meizus have internal only (16, 32 or 64GB). 

Off-topic: "Galiza Nação" (Galicia Nation!) is just a slogan. We're currently under Spanish 'occupation' ;-)

---

### Post by rva1945 on 2015-07-11
Well, from a strinct genetic point of view...I'm Galician. My father was born in Coruña (Concello de Ames) and my mother was born here in Argentina to Galician parents from Ourense.

I was fortunate enough to visit Ourense a few years ago. I fell in love with Galicia and want to visit all of it in the near future, money permitting.


Bye and thanks.

---

### Post by Vladlenin5000 on 2015-07-11
Great :-) 

PM (or Skype) me when you do so whe may eventually enjoy an Estrella Galicia or 1906, the vintage version.

---

