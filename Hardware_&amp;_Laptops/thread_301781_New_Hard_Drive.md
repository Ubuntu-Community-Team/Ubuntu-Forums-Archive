---
title: "New Hard Drive"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by le_vainqueur on 2006-11-17
I am looking to buy a new hard drive so that I can dual boot Ubuntu.  I was wondering how I can determine whether I have an ATA or IDE, and how I can determine what speed of a hard drive my system can handle without over-heating.

---

### Post by 56phil on 2006-11-17
What kind of computer do you have?

---

### Post by le_vainqueur on 2006-11-17
It'a a Gateway.  I don't remember the model.  I bought it about 3 years ago.

---

### Post by taurus on 2006-11-17
> **le_vainqueur said:**
> It'a a Gateway.  I don't remember the model.  I bought it about 3 years ago.
Probably EIDE then...

---

### Post by le_vainqueur on 2006-11-17
What about the speed.  I've read that if you buy a drive that is too fast for your system, it may overheat easily.  

Also, I don't seem to find a description of a hard drive being IDE when shopping.  I see several with ATA, but others have neither identification.  If there is nothing labled, does this mean it is IDE since that's older?

---

### Post by taurus on 2006-11-17
[http://www.newegg.com/Product/ProductList.asp?N=2010150014+1035907789&Submit=ENE&SubCategory=14](http://www.newegg.com/Product/ProductList.asp?N=2010150014+1035907789&Submit=ENE&SubCategory=14)

---

### Post by futz on 2006-11-18
> **le_vainqueur said:**
> What about the speed.  I've read that if you buy a drive that is too fast for your system, it may overheat easily.
What utter nonsense. Where did you read that? Pay no attention to that source from now on. Total crap.


> Also, I don't seem to find a description of a hard drive being IDE when shopping.  I see several with ATA, but others have neither identification.  If there is nothing labled, does this mean it is IDE since that's older?
ATA == IDE

---

### Post by Bartender on 2006-11-18
Yeah, ATA & IDE are essentially the same thing.  The thing you want to make sure of is whether the PC is using the PATA (parallel) or SATA (serial) interface.  Easy to tell with one glance inside.  PATA uses the wide ribbon cable for data, SATA uses a small (about the size of a lightweight lamp cord) cable.  Your Gateway's almost certainly PATA.  Look inside with a flashlight, find the ribbon cable, and using your fingernail to help you, start counting the tiny ridges across the cable.  What I want you to do is determine whether you have a 40-wire cable or an 80-wire cable.  You don't have to count all the way across; once you've gotten to 20 you'll be able to tell cause you'll be halfway across the cable if it's a 40-wire.  If it's a 40-wire I would suggest you make sure to buy a retail box HDD instead of a "white box" because the retail box will include a new data cable, and that cable *should* be an 80-wire.  80-wire is superior to 40-wire for data transmission, and it's easier to set up.  With an 80-wire all you have to do is make sure the little jumper on the back of both drives is set to "Cable Select" (or "CS"), then plug the drive you expect to be used as the bootable drive into the clip at the end of the cable.  The cable should be color-coded to indicate which end goes to the motherboard, but you can always tell because the end with 2 clips a few inches apart is the HDD end.  Plug your new drive into the clip that's a few inches back from the end of the cable.  Then start the PC and go into BIOS.  Check on the main page to be sure it detected both drives and to see how it identifies them.  Move on to "Boot", then boot order or bootable devices or whatever your BIOS calls it and set it so that your old drive is the bootable device.  Windows should start up.
With everything set up as "Cable Select" you can select the second drive as the boot device by going back to BIOS and changing the boot order.  
Are you planning to put Linux on that second drive?  I'm not absolutely sure about this so please do some more research, but I think there are basically 2 ways to do it.  
You plug in the 2nd drive, make sure everything is recognized in BIOS, then when installing Linux you go into manual partitioning and make sure that / and swap are installed to the second drive (hdb) but GRUB installs to the first drive.  How to do this?  On the last page of the install procedure, just before it's ready to do the deed, you'll see a tiny box where it asks where you want GRUB.  It'll probly say "hd0", and that's where you want it to go.  If this is all done properly here's the sequence of events that you want: the PC will boot to the first drive, GRUB will pop up, you'll get a choice of which OS to boot from, if you choose Linux the PC then proceeds to the second drive looking for an operating system.  

When your PC first starts up, it's dumber than a bag of hammers.  It needs help every step of the way, and if the BIOS, MBR, GRUB, etc. aren't right it'll get confused.  It's up to the PC operator to spoon-feed the info in the correct order.
 
The other way (not the only other way I'm sure!) to do it is plug in your new drive, disconnect the data cable from the Windows HDD, and install everything (GRUB, /, swap) to the second drive.  You end up with a fully functional Linux drive. Then you control which OS starts up by going into BIOS and telling it to boot from the first HDD or the second one.  This method seems a bit clunky to me, but it's a bomb-proof way of protecting your Windows data from any mistakes during the Linux installation.
 

OK, the heat thing you heard about.  That's not *entirely* nonsensical but it's probly not something you have to worry about.  Desktop ATA drives spin at 7200 RPM and create some heat.  SCSI drives spin at 10,000 RPM and create more heat.  Since you're not going to a SCSI setup this isn't an issue.  

However, you are adding another heat-producing device inside your case.  If your case was already border-line in the thermal management area, another drive could create trouble.  But this is unlikely.  While you've got it open check for dust building up inside, especially trouble spots like the CPU fan/heatsink.  Powerful (and heat-producing) video cards are what usually cause trouble when added to an existing PC, not an extra ATA HDD.

---

### Post by le_vainqueur on 2006-11-18
Awesome, thanks for the help!!!

---

