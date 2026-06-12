---
title: "Considering buying a Hauppauge WinTV PVR 350."
date: 2006-01-24
forum: Hardware &amp; Laptops
---

### Post by bb002 on 2006-01-24
I'm looking to get rid of my vcr(20 years old and decides to eat a tape on occasion) and stereo(Big hunk a junk that I only use for FM radio).

I would like to know if Ubuntu Breezy supports all of the functions of this card (TV In+FM In+S-Video/Composite In+Remote Receiver In). If linux supports the composite and s-video then I may even by able to get rid of my tv(doubt i will but it becomes an option).

Any know? I'd like to know before I buy and then have to file a RMA. I've seen a few reviews but none that say whether everything works or not. The best I've gotten is "tv tuner and remote work" which doesn't tell if that require some fuse to make it work or not. THanks.

---

### Post by MrFahrenheit on 2006-01-24
I use a PVR 350 on my Knoppmyth box.

check out [www.mysettopbox.tv](www.mysettopbox.tv) for some great resources.

---

### Post by bb002 on 2006-01-30
Does everything work or atleast tell me what you know does work.

---

### Post by bb002 on 2006-02-28
Got my PVR-350 the other day. Got everything working, too! Didn't realize that Linux would allow me to turn the tv out on the 350 into a second desktop. Linux is great! My only complaint is getting the radio to work.

The only program I can get to control the radio is the one provided with ivtv. and it is annoying to have to start a terminal and type "ivtv-radio -f 98.9 -d /dev/radio0" everytime I want to listen to the radio. Other than that, sweet card.

---

### Post by PepeLapiu on 2007-04-10
Can you tell me which software/drivers you used nd if possible any instructions would be appreciated. I am getting ready to instal Ubuntu 7.04 and I have the PVR-350 already in my machine ....I would hate to not be able to use this card in my future Ubuntu box.

---

### Post by bb002 on 2007-05-15
I currently have 350 in a linux box running Ubuntu Dapper and the May 4th 2007 svn of MythTV.


My tuner card has the samsung chipset which I believe is the one with little support but I haven't had any issues myself.

Only thing I had todo extra was custom compile the ivtv drivers. Believe the ones I am using are the 0.4.5 verision. I'm at work right now I get off in about 3 hours so hopefully I remember post again with proper info and instructions at that point.


Sweet!! just checked [http://ivtvdriver.org](http://ivtvdriver.org)
> 2007-02-18

We received the official permission from Hauppauge to repackage and redistribute the firmware files. The license pair is now part of all distributed firmware archives. We are very grateful to Hauppauge for giving us this permission and for Axel Thimm for writing these licenses. Also many thanks to Intel's legal department for allowing to derive them from their firmware licensing texts. 
THAT just made compiling/installing the driver so much easier....no more hunting for the latest firmware :)
that hunting happens to be why i still use the outdated 0.4.5 drivers. I just might be updating tonight.

I think the latest driver might be as simple as ```
./configure
make
sudo make install
```
previously that was just the first 3 steps. next you had to find the fiirmware, rename it, install it to the proper location, and make a few links....was a real pain but it worked.

I'll update soon and see if there are any quirks you should be aware of. but the non-digital Hauppauge cards are all supported through the ivtv driver at [http://ivtvdriver.org](http://ivtvdriver.org) Instructions should be located there as well.

---

### Post by fisinen on 2008-01-09
Did Anyone manage to get the IR Remote working? I need help with that.

---

