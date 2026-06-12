---
title: "problems adding Samsung sv8004h XP HD"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by euthyfro on 2007-01-16
This has become quite the saga, so i'll give as much detail as i can.  I want to add a Samsung sv8004h hard drive that has XP on it to my machine running Edgy on a 250 gb SATA HD (nForce4 mainboard).  my only open ATA cable is the slave to my DVDr. That's where i started a few days ago.
What i've done so far:  i was worried about messing up the ubuntu install & just wanted to check if the sv8004h was still operational so i unplugged the the 250gb HD & plugged the old XP HD in to see if it would start up at least, which it didn't.  i got a "boot failure, insert system disc" message, so i did & got the same message.  This made me assume that the drive was shot, so i thought "no big loss" took it out plugged my ubuntu HD back in & got...
The same damned boot failure message.
After getting all worked up & trying to re-install grub & ubuntu & failing at everything i realized that the machine just wasn't locating any HD at all.
After unplugging the HDs doing a CMOS RAM clear at the suggestion of a friend who knows a lot more about this then i and  plugging it back in & enabling S.M.A.R.T. HDD in BIOS i at least got back to where i started (btw, what is "S.M.A.R.T. HDD" anyway?  the best my friends & i could do was that it must be better than S.T.U.P.I.D. HDD)
So then i put in both HDs powered up &...
Absolutely nothing!  black screen, can't get into BIOS no booting of any sort.
Now i've had this machine & ubuntu for all of almost 2 months, have almost no experience w/computers beyond using them.  moving that jumper to do the CMOS RAM clear scared me a bit, but there's no turning back now.
Next we moved on to looking at the sv8004h's jumper settings (& it has a lot of them, it's another point that makes no sense to me.) i've got 3 sets of diagrams with master, slave & cable select settings in each.  this is an 80gb hard drive but it's jumper settings are for the lower 32 gb, the upper 32 gb and the 32 gb clip.  i'm in trial & error territory now.  setting the jumpers to slave (upper 32 gb) gives me the mainboard's opening EVGA screen & i can get into BIOS but then i get an 
"IDE ROM BIOS 5.50
 Detecting array..."  screen that lasted like 10 minutes before i decided it wasn't really doing anything, shut down, took that HD out & now i'm here. 
does any1 know what i'm talking about or what i'm doing wrong or if what i'm trying to do is even possible?

---

### Post by budgie9 on 2007-01-16
There could be a couple of reasons why you are getting no where with your system.

Firstly the first HD in the computer has to be set to be the MASTER drive, so you will need to set the Samsung HD to be master for it to be seen by the BIOS and thus for it to run it up for you.
You will need to obtain from the web the installation manual for that drive. I found the following one for the 40 GB version of that drive and that is avaliable here
personal.inet.fi/cool/lwgt/myoldvdr/V40ProductManual.pdf

This MAY use the same jumper settings as your drive, but I would strongly suggest you try to find the manual for that drive model you have. If not try the settings in the above manual and set the drive to be the master.
Any second drive  installed should be set to be a SLAVE. on the same controller cable.
You will have two controllers on the motherboard.  
If you have both HD details then make sure you set the drives up correctly one a master the other the slave.  Then both drives should fire up and be listed as the computer starts. If not check the jumper settings again.

The other reason you may have trouble is one well known,  that is taking a XP installed HD from one computer to another. In a lot of cases XP will not fire up, unless it is in the original computer it was installed on. However, some have got it working on other computers. but don't be surprised if you do not. You would more than likely have to wipe the drive and re-install XP.

---

