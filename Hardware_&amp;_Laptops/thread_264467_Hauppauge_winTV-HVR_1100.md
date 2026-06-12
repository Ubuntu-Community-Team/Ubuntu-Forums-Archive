---
title: "Hauppauge winTV-HVR 1100"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by neptune39 on 2006-09-24
Has anyone got this working in dapper? I'm trying to use it with mythTV but cannot get it to work. I have updated my kernel to the one that is supposed to work with this card but it doesn't. Seems mine is phillips based and everyone elses isn't.

Also if anyone uses a card they would recomend that would be great,  this one is pci and no hardware decoder so is cheap, im looking for one that will just work with no hassle, any ideas much apreiciated.

when i try lspci it comes up as unknown/generic so i know this is a driver problem yes?

---

### Post by neptune39 on 2006-09-24
I think im going to swap this for the Nova T as I have found a few decent bits on how to set that one up and it seems really easy to do.

---

### Post by info2 on 2006-09-25
You may take a look at 

 [http://www.linuxtv.org](http://www.linuxtv.org)
and
 [http://www.linuxtv.org/v4lwiki/index.php/Em2880](http://www.linuxtv.org/v4lwiki/index.php/Em2880)

Many TV-Cards/Sticks are supportet with this software and the howto's are relative easy. Maybe you need to follow up some links deep into the wikis there, but i am sure you'll find many useful informations.

---

### Post by neptune39 on 2006-09-25
Cheers for the links. I did swap it for the nova t pci and it works out of the box, i got channels within 5 mins  so avoid the hvr 1100. now been having trouble with mythtv, .18 wouldnt get the listings and .20 wouldn't work with mythweb now trying 0.19 and looks promising. Anyone trying to do this should try [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
Its very simple and the first part will at least check if your card is working.

---

### Post by neptune39 on 2006-09-25
Oh and pc world has the nova t pci cards for £40 if anyone is interested.

---

### Post by stfu on 2006-11-08
hmm, did someone get this card working? if so, how? :)

---

### Post by seiflotfy on 2006-11-13
[http://ubuntuforums.org/showthread.php?t=298094&highlight=wintv](http://ubuntuforums.org/showthread.php?t=298094&highlight=wintv)

---

### Post by stfu on 2006-12-20
I actually got it working after 5 months. After some edgy kernel updates it seemed to just pop out after modprobing cx8800-dvb.

---

### Post by dvarsam on 2006-12-20
Hello!

I read your post:

[QUOTE=neptune39]I did swap it for the **Nova T Pci** and it works out of the box, i got channels within 5 mins  so avoid the hvr 1100. now been having trouble with mythtv, .18 wouldnt get the listings and .20 wouldn't work with mythweb now trying 0.19 and looks promising. Anyone trying to do this should try [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)
Its very simple and the first part will at least check if your card is working.[/QUOTE]

May I encourage you to add the **Nova T PCI** card on the "Ubuntu Hardware Compatibility/Support" Page:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia](https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia)

And:

[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

Your input is valuable for other Ubuntu users too!
Please spare some of your time, go in there & add your product, your experience & a handy howto available to others...!!!

Thanks.

P.S.> Don't forget to add the card that didn't work also!

---

### Post by Spermy on 2007-04-08
I have actually got my Hauppauge HVR1100 working in Ubuntu 6.06

It took about 3 weeks, and i followed numerous guides and then asked for help on the forums before I got it to find any channels....

But it does work. I started out by trying to use tvtime, then tried Xawtv, followed by giving in and asking for help. I got a reply from a nice man, who pointed me in the direction of VLX Media player, however it didn't work for me... He also suggested a couple of web pages, one of which had Gxine  on it... So i figured it couldn't be anyworse, it worked wonderfully..... So I can't tell you exactly what i had to install and when, but it WILL work.

My forum post:
[http://ubuntuforums.org/showthread.php?t=394991&highlight=hauppauge+hvr+1100](http://ubuntuforums.org/showthread.php?t=394991&highlight=hauppauge+hvr+1100)

---

