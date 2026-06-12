---
title: "Kingston's U3 DataTraveler 2GB on Linux ?"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by FaBMak on 2006-06-13
Hi,

I'm looking for a USB flash drive and i found this model:
[http://www.kingston.com/flash/dt_u3.asp](http://www.kingston.com/flash/dt_u3.asp)

But, before buy it i want know if work on Ubuntu Linux. Have someone experience on this USB flash drive ?

Thanks,

FaBMak

---

### Post by hogweed on 2006-06-14
FaBMaK:

I haven't used this particular drive, but do use a Lexar JumpDrive and have been generally keeping my ears open.

There should be no problem at all with the drive that you are looking at. You should just be able to plug it in and it should automatically be mounted, etc., without you needing to do anything special (well, except lay down the cash to buy the drive).

Best of luck.

 -- hogweed

---

### Post by indigoshift on 2006-08-06
I have the 1GB version of this USB drive, and I plug it into a Compaq Evo N600c.  I thought it wasn't working for the longest time, but realized I wasn't being patient enough to allow it to auto-mount.

The Kingston will present itself to the OS (even if the OS is Windows) as two devices:  a CD-ROM and a flashdrive.  I think it takes Ubuntu about 30 to 45 seconds (on this laptop, anyway) to mount both devices.

If anyone knows how to turn this functionality off, I'd love to hear it.  I'd rather have just a dumb USB stick acting as data storage--if only to reduce the waiting when I plug it in.

Other than the wait time, it seems to work great.  I swap files back and forth between this laptop and my Windows machine all the time, with no problems.

---

### Post by skirkpatrick on 2006-08-06
Ug!  Those U3 drives are very annoying because of that extra CD device that it presents.  I actually took one I had back and bought a different one.  From the information I could discover, there is no way to disable the CD device as the hardware in the USB drive ALWAYS presents both devices to the OS.

---

### Post by indigoshift on 2006-08-14
Ugh.  Well, that's bad news.

Although my basic faith in humanity tells me that, eventually, someone will figure it out.  Hopefully, they'll post the results.  ;)

---

### Post by tranxene on 2006-10-21
In order to get rid of these annoying U3 features, just download the [w32 executable]("http://www.u3.com/uninstall/") and run it on a win box. It will remove all U3 related stuff on the stick and the pc. This also affects the hidden partition on the USB device, which appears as hard drive.

---

### Post by leteci on 2006-10-27
So U3 kingston works on ubtuntu with u3 features or not?

---

### Post by drweberdk on 2006-12-13
Hey I just did as tranxene explained and uninstalled all that U3 software. All you need is an windows machine to run the uninstall from and the U3 drive only has one drive. No CD-ROM and no pesky software that only runs on windows. Nice! :D

---

### Post by indigoshift on 2007-04-08
I did the same thing not too long ago, but something odd happened:

Note that this tale involves two USB sticks and two computers.  It's a little confusing.

I gave my wife my 1GB stick to use with her System76 laptop, as I'd just bought a 2GB stick for myself.

I used the uninstall program linked above to remove all the unwanted stuff from the 1GB stick, as my wife didn't need all that stuff with Ubuntu.  So, I plugged the 1GB stick into my XP box and uninstalled everything.

Ever since then, my XP box won't recognize the 2GB stick at all.  Every other computer I own (XP and Ubuntu both) recognize it just fine.  But the XP machine I ran the uninstall utility on won't see the 2GB stick.  It'll see the 1GB stick without all the Kingston software on it, and it'll even see my old 32MB stick from 5 years ago.

Keep that in mind if you're going to run the uninstall utility.  I think it removes registry hooks from the computer running the uninstall or something.  I can't figure it out.

Sure wish I had another XP machine to run the utility again on the 2GB stick...I think that removing all the extra stuff from that stick will let my XP box see it.

I don't know, really. It's weird.

---

### Post by alexpwalsh on 2008-03-19
I've got a 4GB U3 drive.... The baseline answer to your question, is that Yes, the drive will work with Linux, any distro. It will work on any PC that has a USB port, its just that some capabilities may be disabled. The actual U3 lauch pad does not work in linux, I've been trying with WINE and such, but with no luck. And as for the above comments about the CD drive that appears, mine does not appear. To change that [this guy]("http://teknohog.godsong.org/hacks/u3/") explains how to turn it ON, so I suppose you could do the opposite to reverse it.

---

### Post by tlynch999 on 2008-06-11
> **alexpwalsh said:**
> I've got a 4GB U3 drive.... The baseline answer to your question, is that Yes, the drive will work with Linux, any distro. 

Thanks...I'm about to head out to pick up an 8 gig U3 drive, and would like to *not* wipe it out in case it's usable on the windows machines I use.  

It's up for 1/2 price, but I'd like to keep the functionality if I can...  [Here tis]("http://www.bestbuy.com/site/olspage.jsp?skuId=8472351&type=product&id=1185265539078") in case anyone's shopping.

---

