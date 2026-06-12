---
title: "[SOLVED] Can't figure out how to install Brother MFC-465CN printer via USB"
date: 2008-08-21
forum: General Help
---

### Post by ACGarib on 2008-08-21
Hi, I can't install my new printer.

I go to system, administration, printing, then click the "new printer" button.

Under the devices list, I see Brother MFC-465CN USB #1, so I click that.

It then says to select a printer from the database or use a postscript printer description. I choose select printer from database. I click on brother, but then MFC-465cn is not listed as a model number.

I am stuck there.

I saw a website: [http://uint32t.blogspot.com/2008/06/linux-printing-brother-mfc-465cn.html](http://uint32t.blogspot.com/2008/06/linux-printing-brother-mfc-465cn.html)

and I did 

```
sudo apt-get install brother-lpr-drivers-extra brother-cups-wrapper-extra
```

then the website says to go to printing and do a test page to see if everything is OK, but I could never find the model number in the database so there is no printer to select a test print for.

What am I doing wrong?

I don't need to do any fancy networking or CUPS stuff because it's just connected to USB.

Thanks,
Andrew

---

### Post by ACGarib on 2008-08-21
Well, I got it to work. I removed the stuff I installed earlier, then followed a different guide: [http://ubuntuforums.org/showthread.php?t=590793&](http://ubuntuforums.org/showthread.php?t=590793&)

Lo and behold it works!

It seems like no matter how hard I try, I can never get something to work until just after I give up and make a thread here.:lolflag:

---

