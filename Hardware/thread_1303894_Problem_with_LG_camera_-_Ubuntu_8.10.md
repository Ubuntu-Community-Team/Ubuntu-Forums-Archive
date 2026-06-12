---
title: "Problem with LG camera - Ubuntu 8.10"
date: 2009-10-28
forum: Hardware
---

### Post by Jammanuser on 2009-10-28
Hello,
Ubuntu 8.10 is not detecting my USB LG enV3 (DLC100) cell phone when I plug it in. However, when i run the command "lsusb", it shows the device.

Anyone have an ideas on how to get it to work?

Thanks in advance.

-Jam Man

:guitar:

---

### Post by Jammanuser on 2009-10-28
lsusb:
```
Bus 007 Device 002: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 004 Device 003: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone**
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 413c:8156 Dell Computer Corp. 
Bus 001 Device 006: ID 413c:8158 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8157 Dell Computer Corp. 
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by lswb on 2009-10-28
Are you trying to use the cell phone as a modem or trying to access the camera? If the modem. try clicking on Network Manager applet and see if gives you a Mobile Broadband connection option.

If the camera, it's likely that the cell phone does not use standard digital camera protocols that will let it be automatically recognized or mounted. For cdma phones you may be able to use the bitpim program, I don't know what's available for GSM phones.

---

### Post by Jammanuser on 2009-10-28
> **lswb said:**
> Are you trying to use the cell phone as a modem or trying to access the camera? If the modem. try clicking on Network Manager applet and see if gives you a Mobile Broadband connection option.

If the camera, it's likely that the cell phone does not use standard digital camera protocols that will let it be automatically recognized or mounted. For cdma phones you may be able to use the bitpim program, I don't know what's available for GSM phones.

I'm trying to access my phone, so I can get some pics off of it, that I took with the built-in 3.0 mega camera.

How do I know if its a cdma or gsm phone?

Thanks for the reply.

---

### Post by lswb on 2009-10-29
In the USA Verizon and Sprint use CMDA, and AT&T and T-Mobile and most of the other large companies use GSM. Smaller companies you'd need to check to be sure.

The bitpim package or their website has a list of supported phones and what capabilities the software has for those models. I expect there are similar programs for GSM phones.

---

### Post by Jammanuser on 2009-10-29
> **lswb said:**
> In the USA Verizon and Sprint use CMDA, and AT&T and T-Mobile and most of the other large companies use GSM. Smaller companies you'd need to check to be sure.

The bitpim package or their website has a list of supported phones and what capabilities the software has for those models. I expect there are similar programs for GSM phones.

Ok, mine's a Verizon phone, so I suppose its CMDA.
What and where is the bitpim package?

---

### Post by Jammanuser on 2009-10-29
Nevermind. Found it in Add/Remove Applications.

---

### Post by Jammanuser on 2009-10-29
Ok, I installed BitPim, but its still not detecting my phone.
I even tried setting the "Phone Type" to both "LG VX4400" and then "LG VX6000", which is the model "lsusb" shows my phone as, but it still does not detect it.

Any other ideas?

---

### Post by Jammanuser on 2009-10-29
And on my USB cord for my phone, there is a sticker which gives the model of the phone as a "LG DLC100". I don't know if that helps or not.

---

### Post by Jammanuser on 2009-10-29
Ok, I just googled "LG env3", and come to find out, it is a VX9200. 
Apparently, lsusb doesn't recognize it as that though (probably because its a fairly new phone), and instead detects it as a VX4400/VX6000.

I looked in the supported phones list for bitpim, but it doesn't mention that phone, so I guess its not supported (though I do believe the earlier version of the same phone - the LG env2 IS supported). :(

So now what do I do?

Is there any way to get it to work?

---

### Post by lswb on 2009-10-29
There might be. I really can't give a better answer.

Verizon and the other cellular carriers are known to disable certain features on their phones for their own financial benefit. For instance, they have a service (payment required of course, or pay for a plan upgrade) to send the pictures to an email account. Downloading directly from the phone may not be easily possible.

Bitpim does have IIRC a "filesystem" mode that works to view (possibly only part of) the filesystem on a phone. Again it will not work on all models, but it does work with many that are not on the "supported" list. But be careful, read all the caveats. It is possible to brick the phone by accessing its internal memory or storage in unexpected ways.

The phone companies don't want us to be able to access our phones easily. It reduces their revenue sources.

---

### Post by oldgeekster on 2009-11-10
> **Jammanuser said:**
> Ok, I just googled "LG env3", and come to find out, it is a VX9200. 
Apparently, lsusb doesn't recognize it as that though (probably because its a fairly new phone), and instead detects it as a VX4400/VX6000.

I looked in the supported phones list for bitpim, but it doesn't mention that phone, so I guess its not supported (though I do believe the earlier version of the same phone - the LG env2 IS supported). :(

So now what do I do?

Is there any way to get it to work?Hi Jammanuser - finally found your thread and glad to see I'm not the only one using an enV3 and wanting to use bitpim, (misery loves company). I'm running Karmic Koala (ver. 9.10) and have found that the bitpim.org site has a "latest update" that covers the enV3 (VX9200) phone - unfortunately there is no available debian (.deb) file for that version.  They do have a version for RedHat Package Manager (.rpm) which I have tried to convert to deb repeatedly with alien, however, the resulting package will not work under Karmic regardless of my "geeky" tricks.  You might try to do something similar since you are running an older version of Ubuntu, (if you still are). Their "latest update" RPM package is about halfway down the page on bitpim.org below:
**BitPim Test Release 1.0.7.20090805 (10 Aug 2009)**

 My 8 gig micro sd card for the phone doesn't arrive until tomorrow.  When it does, I should be able to transfer picture files to/from it by simply removing the card from the phone (after I get IT working properly), placing it in an adapter and plugging that into my normal memory card reader slot. (I already know that works as I've been using the card out of my camera and simply communicating with it via Nautilus..  Good luck!

---

### Post by Jammanuser on 2009-11-12
> **oldgeekster said:**
> Hi Jammanuser - finally found your thread and glad to see I'm not the only one using an enV3 and wanting to use bitpim, (misery loves company). I'm running Karmic Koala (ver. 9.10) **and have found that the bitpim.org site has a "latest update" that covers the enV3 (VX9200) phone** - unfortunately there is no available debian (.deb) file for that version.  

Really? That's news for me. :) That's great. I had just about given up on the problem.
> 
They do have a version for RedHat Package Manager (.rpm) which I have tried to convert to deb repeatedly with alien, however, the resulting package will not work under Karmic regardless of my "geeky" tricks.  You might try to do something similar **since you are running an older version of Ubuntu, (if you still are)**. 

Yeah, I'm still using 8.10 (haven't upgraded yet, see no reason to). 
> 
Their "latest update" RPM package is about halfway down the page on bitpim.org below:
**BitPim Test Release 1.0.7.20090805 (10 Aug 2009)**

Thank you. Found it easily enough.
> 
 My 8 gig micro sd card for the phone doesn't arrive until tomorrow.  When it does, **I should be able to transfer picture files to/from it by simply removing the card from the phone** (after I get IT working properly), placing it in an adapter and plugging that into my normal memory card reader slot. (I already know that works as I've been using the card out of my camera and simply communicating with it via Nautilus..  Good luck!
Will that work? I might want to try that too, but where is the built-in card located in the phone? Can it be easily accessed (i.e. *without* breaking my phone...;))?

Thanks for helping.

-Jam Man

:guitar:

P.S. Love your sig...:D

---

### Post by Jammanuser on 2009-11-12
There is a program, KPackage, which you can install through the Add/Remove Applications, that supports the .rpm format. Just found it, and gonna try it on BitPim now...

-Jam Man

:guitar:

EDIT: Nope, didn't work. Tried to use KPackage to install that BitPim update, and got an error (see attached image).

---

### Post by oldgeekster on 2009-11-12
> **Jammanuser said:**
> snipped for brevity...

Will that work? I might want to try that too, but where is the built-in card located in the phone? Can it be easily accessed (i.e. *without* breaking my phone...;))?

Thanks for helping.Hey Jam Man, sorry it has taken a couple days to get back into this thread.  (Equally sorry to hear you also had problems converting that new bitpim rpm over to deb.)

I received my 8 gig micro SDHC card yesterday.  Turned off the phone, opened the little slot on the right side of the enV3 and (careful to make certain I didn't have it backwards) inserted the tiny little card into the slot. Turned the phone back on and apparently it took care of formatting the card and putting appropriate sub-directories for my videos/pictures/music/etc. on it.  A quick check with Settings&Tools | Memory | Card Memory proved everything was good to go. While I was in that area I made sure that save options was set up for stuff to get saved to the card rather than the camera's own memory.

Moved the pictures I already had saved on the phone to the card - then turned off the phone and removed the card.

Placed the micro SDHC card into an SDHC adapter I already had laying around and stuck it into the card slot on my Toshiba notebook.  It took about 10-15 seconds and Ubuntu 9.10 recognized it - even popped up a nautilus window showing the content.  Cool!

I was able to copy those pictures over to the computer - then just for fun wanted to test the music - so copied a mess of Alan Jackson MP3's over to the card.

When I got the micro SDHC card back into the phone and lit it off, I was elated to find that the enV3 plays MP3's without a problem.

Hope this helps with what you were originally trying to do Jam.  Sure is working swell for me.  I'd like to be able to use bitpim (primarily for the Calendar stuff) but just being able to move pics/videos/music back and forth will keep me happy until they release another version for Ubuntu that covers our VX-9200 phones.

-=dave=-

---

### Post by Jammanuser on 2009-11-13
Thanks for that.
I finally found a program for Ubuntu that will open a .rpm archive, and extract the contents. The application is Xarchiver 0.4.6. You can download/install it through the Add/Remove Applications.

Now I just got to figure out how to install that Bitpim update.

---

### Post by oldgeekster on 2009-11-13
> **Jammanuser said:**
> Thanks for that.
I finally found a program for Ubuntu that will open a .rpm archive, and extract the contents. The application is Xarchiver 0.4.6. You can download/install it through the Add/Remove Applications.

Now I just got to figure out how to install that Bitpim update.Good luck - I've been at personal computers for one very, very long time - (before there was such a thing as MSDOS) - the problem will be in trying to tweak all of the scripts and dependencies then compiling them. (I finally gave up - too much undocumented stuff that I couldn' figure out what the originator of that package was trying to do - also it was set up for an older version of RedHat). ;)

In the mean time, I am *loving* my new enV3 (9200) - the excellent little keyboard lets me keep up with 4 of the grandkids that love to text old Papa. Have only now started using the camera a bit more effectively.

Let us know if you have any luck!

---

