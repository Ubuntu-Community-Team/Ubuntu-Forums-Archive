---
title: "USB connected HP Laserjet 5mp stopped working after 12.04 update"
date: 2014-06-13
forum: Hardware
---

### Post by creative3 on 2014-06-13
About a week ago some 12.04 updates came in, and suddenly my Laserjet would no longer print all documents. Anything with straight text would still print, but anything with an image or a PDF document would not print. This happened to all three of my computers running 12.04. The printer is connected with a parrellel to USB adapter. I also tried connecting it with a HP jetdirect plus server and still had the same result.

The odd thing is, that I also have an HP minin running Puppy Precise, and it will still print everything just fine.

I've tried using both CUPS and HP Tools, and have also tried using all the available PPDS.

It must have been caused by a 12.04 update. Can anyone help?

---

### Post by creative3 on 2014-06-13
After a little more testing, I found the failure happened with any document containing bullet lists. In LibreOffice, if I remove the bullet formatting, the document will print fine. I have tried different fonts, but still no resolution.

Is there a way to upload LibreOffice fonts to the printer?

---

### Post by tgalati4 on 2014-06-13
Typically after any kernel update you can expect some CUPS breakage.  That is just the way it is.  The first thing to try is to delete the printer and reinstall it, but only after a reboot and then check for any additional updates.  Sometimes kernel updates cause regressions and then there are more updates to fix the regressions.  If you have tried these steps and you are still having problems, then file a bug against CUPS to track it and see if others are having similar issues.

There are several versions of 12.04.  What version are you running?

Open a terminal:

```
uname -a
cat /etc/issue
lsb_release -a

```

---

### Post by creative3 on 2014-06-14
After a little more testing, I found the failure happened with any document containing bullet lists. In LibreOffice, if I remove the bullet formatting, the document will print fine. I have tried different fonts, but still no resolution.

Is there a way to upload LibreOffice fonts to the printer?

---

### Post by tgalati4 on 2014-06-14
If you can't print PDF documents, then your printer queue is broken.  You don't upload fonts to the printer, you define them in a PDF document which is then converted to the laserjet format (PCL or raw bitmap) for printing.

Are there error messages in /var/log/cups?

Your printer should have an early Postscript SIMM card (memory chip).  Try cleaning with an eraser and reseating the memory stick.  I'm pretty sure early Postscript has bullet's in its fonts.  Because of the age of the printer, I would not be surprised if the chip is failing.  Try printing a test page that shows all of the built-in characters.  Otherwise try using a different printer driver that handles the Postscript correctly.

---

