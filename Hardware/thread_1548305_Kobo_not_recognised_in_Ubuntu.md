---
title: "Kobo not recognised in Ubuntu"
date: 2010-08-08
forum: Hardware
---

### Post by mark111 on 2010-08-08
I am running a Asus 1005HA with Ubuntu 10.04 and have recently purchased a Kobo ebook reader.  The Asus recognises the Kobo as a USB device, but there is no application that automatically loads to transfer books from the laptop or otherwise manage content.  I installed calibre, which reads my books on my laptop hard drive but does not recognise the Kobo.  Calibre does not have the plug in for Kobo, and I can't find the location for that plug in.  I also tried installing Wine and then Adobe ADE, but that didn't seem to connect to the device.

Anyone know how to connect a content management app in Ubuntu to my new Kobo?

Many thanks.

---

### Post by rwigle on 2010-09-01
I am not sure this really answers your question, but maybe going through the whole thing would help others.

I just got my kobo ereader setup running and it has been a trial. I run Lucid on an Acer EEE netbook.

You should look at the following thread first about getting Adobe Digital editions running under wine if you haven't already. It also explains about actually downloading the book. (See #34 and the ones following. That is simpler than #33 and managed to work for me.)

[http://ubuntuforums.org/showthread.php?t=701191&highlight=ebook+drm&page=4](http://ubuntuforums.org/showthread.php?t=701191&highlight=ebook+drm&page=4)

OK, so then you have your URLlink.acsm and you have managed to download the book to your hard drive.

Then I used calibre to put the book on my Kobo. I am using the version from the Ubuntu Software Center, which is version 0.6.42, so it does not have the Kobo drivers. (I think if you download from the Calibre web site they do.)

Anyway, you just need to use the "Save to disk" function, writing to the Kobo, which is seen as a USB drive. I chose the "Save to a single folder" option and created a new folder with the author's name (Dickens, Charles).
Calibre will save the book, the image for the cover and some metadata in that folder.

Hope this helps someone, if not mark111.

---

