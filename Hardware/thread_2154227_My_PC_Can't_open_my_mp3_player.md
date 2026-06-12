---
title: "My PC Can't open my mp3 player"
date: 2013-06-14
forum: Hardware
---

### Post by Cmiller2 on 2013-06-14
I would like to sync my music files to my mp3 player. Device format is MTP, made by Sandisk. Its a Sansa Clip Zip. Infomation about it can be retrieved [here]("http://shopping.yahoo.com/905373854-clip-zip-4gb-black-mp3-player/specs;_ylt=ApUjTDjVnDsIWssE0vNfd0H4SHAD") (sorry if it sounds like I'm soliciting, mods can remove the link if need be. I'm not trying to advertise, just letting you all know the details of my device).

Lubuntu's PCManFM cannot open the device up. I believe its due to my mp3 player not being compatible with Linux. Is there anyway around this? I would very much like to import the music to my device. I get the following error:

**Unable to open MTP device '[usb:001,004]'**

PC details:

Dell Inspiron Notebook
RAM 4G
3.0 Gherts
AMD graphic card

Alright, I believe I've given all the info you need to know. Please let me know if I missed anything.

~Cmiller

---

### Post by scbingham on 2013-06-14
This article might point you in the right direction:

[http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access/)

There are lots of articles out there.

Looks like MTP problems will become more common place. If you have success, post your results & hopefully you'll be helping others :)

---

### Post by Cheesemill on 2013-06-14
> **Cmiller2 said:**
> Alright, I believe I've given all the info you need to know. Please let me know if I missed anything.

You've missed out the most important detail, which version of Ubuntu are you running?

Some recent versions of Ubuntu have had issues with their implementation of MTP (it doesn't work) which has now been fixed.

---

### Post by SeijiSensei on 2013-06-14
Try switching to MSC as the USB mode.  From the manual:

USB Mode
USB Mode determines how your player communicates with your computer. Auto
Detect is selected by default. You can also choose to always connect in MTP (Media
Transfer Protocol) or MSC (Mass Storage Class) modes. Windows can use MTP or MSC
mode, but Mac OS will only work with MSC mode. If you set the USB Mode to Auto
Detect, make sure you are running Windows Media Player version 10 or higher.
1. Select USB Mode.
2. Select Auto Detect, MTP, or MSC.

---

### Post by Cmiller2 on 2013-06-14
> **Cheesemill said:**
> You've missed out the most important detail, which version of Ubuntu are you running?

Some recent versions of Ubuntu have had issues with their implementation of MTP (it doesn't work) which has now been fixed.

I use a Lubuntu 13.04.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Okay, I followed what SeijiSensei suggestion. I switched to MSC mode on my SanDisc mp3 player. By going into the settings it was quite easy. I am able to open the folders now in my mp3 player. However, though I can see the "folders" I see no files whatsoever. There were existing music files on the mp3 player, though when I go into the music folder, those mp3 files are not there. They exist in the mp3 device, but apparently linux does recognize them. Are they hidden? I don't get it.

[COLOR=#000000]scbingham, I could not understand the article. It was referring to Android Ice Cream sandwhich phone which I have not idea what that is (I use Galaxy 3), and it does not imply nothing about an mp3 player.

[/COLOR]

---

### Post by scbingham on 2013-06-14
I was thinking more along the lines of the problems with MTP & ubuntu, which those android phones now use, instead of USB Mode.

---

