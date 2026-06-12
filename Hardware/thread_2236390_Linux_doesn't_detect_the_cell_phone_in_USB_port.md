---
title: "Linux doesn't detect the cell phone in USB port"
date: 2014-07-26
forum: Hardware
---

### Post by rva1945 on 2014-07-26
Hi:

(12.04) I had been working with my old phone, I just bought a Samsumg Pocket Neo and now when I plug it into the USB port, it starts taking charge but no news in Nautilus.

If course it passed the "MS test": MS Explorer detects it (W7 in another partition, no virtual machine here).

The closest I was: in one occasion after plugging and unplugging it many times it was detected and I could see the folders in the phone but no files (no pictures, no mp3, no nothing that was there).

Any idea?

---

### Post by slooksterpsv on 2014-07-26
Do you have USB media enabled on the phone itself? When you plug it in, if you go to the file manager do you see it listed on the left hand side?

---

### Post by rva1945 on 2014-07-27
Of course, as I said, MS Explorer detects the phone when it is plugged.

---

### Post by jeremy31 on 2014-07-27
This might help out
[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)

---

### Post by SeijiSensei on 2014-07-27
Support for the MTP protocol that Android now uses was weak at best in 12.04.  It's a little better now in 14.04.

---

### Post by slooksterpsv on 2014-07-27
Sorry there's two options on that. 1 could be vendor software that allows access a certain way and 2 is the regular android connection way. I can't say as I've ever had issues - generally if I have it's only because I've had to manually mount it (via terminal) or mount it via Thunar/Nautilus/Dolphin/PCManFM. Just double checking.

---

