---
title: "Catalyst error; ATI Mobility Radeon 9000, Tosihiba Satellite A75 12.04"
date: 2012-08-31
forum: Hardware
---

### Post by kmcderm133 on 2012-08-31
Hello. I'm running Ubuntu 12.04 on a Toshiba Satellite A75-S226. Since upgrading to 12.04, I have no 3D graphics. I don't run many games on this machine, so I don't know when this started. Trying to start the Catalyst Control Center gives me the error message that there is no graphics adapter installed. Also running aticonfig from a terminal gives the message "aticonfig: No supported adapters detected".
The steps outlined here: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx) 
to uninstall the driver and Catalyst don't work completely, and installation intructions found here: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide) don't fix anything either. Xorg is installed, but I think this is just the regular Catalyst program. (I could be wrong?) Additional Drivers in my System Settings shows only the laptops modem, not the graphics card. Please let me know how I can get this working. Here are my system specs:

Toshiba Satellite A75- S226
Intel Pentium 4 3 GHZ CPU
ATI Mobility Radeon 9000 GPU
874 MB RAM (Yeah, I know...)
60 GB hard drive 

Note:  As this is a laptop I can't think of anything else to list, hopefully I haven't left       anything out. 

Thanks in advance,
 -kmcderm133

---

### Post by mastablasta on 2012-08-31
i am not sure that card is supported by fglrx.
info on opensoruce driver: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
go down the page to "purge fglrx" (but you can also read other things): [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver")

---

### Post by ajgreeny on 2012-08-31
That card is definitely not capable of using fglrx so you will be stuck with the open source radeon driver that you are currently using.

I do not know if having installed the fglrx driver will cause any problems, but if it were me, I would uninstall it just in case, as there could be some conflict.

---

### Post by kmcderm133 on 2012-08-31
*facepalm* 

Thanks Mastablasta and ajgreeny! It turns out that, yes, if I remove all the ATI software I can run 3D applications.... Oops. Still, it would have been nice to have an app that would let me tweak graphics performance. *shrug* Oh well.

   Again, Thanks so much for your help!! :)

 -kmcderm133

---

### Post by mastablasta on 2012-09-03
xorg.conf file can tweak it a bit. i am not sure if there is a GUI available.

---

### Post by kmcderm133 on 2012-09-04
> **mastablasta said:**
> xorg.conf file can tweak it a bit. i am not sure if there is a GUI available.

Thanks for the tip Mastablasta! I think I'll look for one. I don't know enough to tweak it on my own, I think, and I still get plenty of graphics corruption, even on text. (I should be more mindful of the temperature though, this laptop gets hot pretty quickly.)

  Thanks again,
  -kmcderm133

---

### Post by kmcderm133 on 2012-09-09
I just had the time to check for the file, and I have no xorg.conf. The closest thing I have is a directory called 'xorg.conf.d', nothing in there looks like it relates to graphics or anything. What did I do wrong now?

---

