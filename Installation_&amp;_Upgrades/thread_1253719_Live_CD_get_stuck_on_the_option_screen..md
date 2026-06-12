---
title: "Live CD get stuck on the option screen."
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by gwu777 on 2009-08-30
Hi there,

I have a samsung V25 Pentium 4 2.4gh with 512Mb memory. it has an Intel 845GV IGD onboard card.

I have been able to install ubuntu 7, then 8. I am now trying to install 9.04.

I have tried everything. I have checked the CD for defect it is alright and furthermore it works on other computer. To be fair, I have the same problem with version of xubuntu 9.04...

First the live CD get stuck as I chose run the live CD or install ubuntu. It stays on the screen and the processor and cd are turning for hours, but nothing happen. I have tried on safe mode, as I had to run the 8.10 live CD on that mode before. I have even tried with all the acpie stuff off, to no avail...

I have tried to install ubuntu via wubi or whatever it is called through windows. It has installed OK, except that when it start, it get stuck as it is loading the graphical interface and all I get is a black screen.

The upsetting thing is it was working with ubuntu 7 and ubuntu 8.10, why can't I do anything now?

Any ideas or scenarios would be more than welcome...

---

### Post by Maheriano on 2009-08-30
Mine did this too. I tried a different brand of CD, burned it again and it worked fine. I know now that I have a spindle of CD that for some reason won't accept being created into a LiveCD.

---

### Post by gwu777 on 2009-08-31
> **str8outtacpt said:**
> i put ubuntu 8.10 on my computer and windows doesnt even boot any sugguestions? is it still there?

Is it still there will really depend on the option you have chosen while installing ubuntu... Do you have the option when you start your PC to start windows? If not have you installed ubuntu in its own partition?

---

### Post by gwu777 on 2009-08-31
> **Maheriano said:**
> Mine did this too. I tried a different brand of CD, burned it again and it worked fine. I know now that I have a spindle of CD that for some reason won't accept being created into a LiveCD.

Went and got new CDs, it is slightly better... Kind of. I am not stuck any more on the option screen, but I now have the same problem than when I have fully installed it. The graphical interface doesn't load. I hear the welcome sound but my screen stay black. This is in safe mode...

Any way I can define some graphic card attribute before starting it? Would it be as I think the problem?

---

### Post by gwu777 on 2009-09-01
I folowed the advide of a French ubuntu doc:[cette documentation]("http://doc.ubuntu-fr.org/ati_usplash"), and I have reconfiguered xorg using:

sudo dpkg-reconfigure -phigh xserver-xorg

However, the command didn't ask me to chose a driver as specified in the doc. It seems to have been done automatically. However, using this I am now able to start ubuntu, with the graphic interface.

I do have another problem, my keyboard and mouse - trackpad are not responsive and I have the following windows:

First:
Internet error
Fail to initialize HAL!

Then:
The panel encountered a problem while loading "OAFIID:GNOME_IndicatorApplet".
Do you want to delete the applet from your configuration?

I cannot do anything about it though because keyboard and mouse are completely irresponsive. I tried to reconfigure xorg using:

Dpkg-reconfigure xserver-xorg when in terminal mode without effects...

Another thing - I am still on the live CD - when I open the xorg.conf file using nano:
sudo nano /etc/X11/xorg.conf it appears empty?!?!

Any ideas?

---

### Post by presence1960 on 2009-09-01
> **str8outtacpt said:**
> i put ubuntu 8.10 on my computer and windows doesnt even boot any sugguestions? is it still there?

it is suggested that you start your own thread so everyone asking for help gets the best help possible. It can get really confusing & messy when multiple people with multiple problems are seeking help in the same thread. Please start your own thread. Thank you.

---

### Post by Maheriano on 2009-09-02
> **gwu777 said:**
> I folowed the advide of a French ubuntu doc:[cette documentation]("http://doc.ubuntu-fr.org/ati_usplash"), and I have reconfiguered xorg using:

sudo dpkg-reconfigure -phigh xserver-xorg

However, the command didn't ask me to chose a driver as specified in the doc. It seems to have been done automatically. However, using this I am now able to start ubuntu, with the graphic interface.

I do have another problem, my keyboard and mouse - trackpad are not responsive and I have the following windows:

First:
Internet error
Fail to initialize HAL!

Then:
The panel encountered a problem while loading "OAFIID:GNOME_IndicatorApplet".
Do you want to delete the applet from your configuration?

I cannot do anything about it though because keyboard and mouse are completely irresponsive. I tried to reconfigure xorg using:

Dpkg-reconfigure xserver-xorg when in terminal mode without effects...

Another thing - I am still on the live CD - when I open the xorg.conf file using nano:
sudo nano /etc/X11/xorg.conf it appears empty?!?!

Any ideas?
Don't try and fix that, just burn another new CD and start again. That's going to be too much of a headache to deal with. I'd suggest looking at borrowing a few blank CDR or DVDR off a friend and taking a look at your burner to see if there's something wrong with it. Maybe even do a checksum after burning or even try burning it on a friend's computer. There's something not right with yours.

---

### Post by gwu777 on 2009-09-02
> **Maheriano said:**
> Don't try and fix that, just burn another new CD and start again. That's going to be too much of a headache to deal with. I'd suggest looking at borrowing a few blank CDR or DVDR off a friend and taking a look at your burner to see if there's something wrong with it. Maybe even do a checksum after burning or even try burning it on a friend's computer. There's something not right with yours.

The a quick conclusion to get to! I have obviously done my checksum and they are all fine, my CD intergrity check is perfect for information. I have burnt the CD on different kind of CDs and they are all working an several PC but this laptop. Unfortunatly, I believe the problem come from the laptop and not the CDs.

We are going to have to go for the headache.

---

### Post by gwu777 on 2009-09-07
I now have the official 9.04 cd, thank you canonical!

I believe the problem is with my video card, I already had some problem with Ubuntu 8. I need to set the drivers in xorg to Intel. the safe mode doesn't work. Does anyone know how to do that from the live CD?

I have tried to edit xorg using:

sudo nano /etc/X11/xorg.conf

But the file is empty, shouldn't there be something written in it?

---

### Post by gwu777 on 2009-09-12
Here is an update to my problem...

After trying unsuccesfully to un the live CD, I decided to give a try to the install ubuntu option. I started the instalation but then decided to cancel it in the middle. The instalation program asked if I wanted to revert to the live CD. I said yes. THE LIVE CD STARTED PERFECTLY!

Now I like to understand things... When I select the normal option start the live CD, all I get is a blank screen in the best case scenario, despite my best effort at tinkering with the diverse options... I cancel an instalation and ubuntu starts happily? If find this strange and I would like to know with which different option the live CD started. (For information, I have retried a few time, and the only way to have the love CD starting is going through a cancelled instalation - go figure...)

Ubuntu is now instaled, and to add pain to my misery, once every three time the laptop is started or so, I get a blank screen instead of the logging screen, I usually force shutdown the pc, restart it and it works fine for a couple of restart...

Apparently all this is due to a downgrade in the handling of intel drivers in jaunty. I am now unable to set any kind of screen resolution as the options are greyed out. I am not able to change the driver for my card, as now everything is automatic and gtk display manager doesn't work on jaunty; and as it is clearly written in xorg.conf, some of the option are now automatically set, such as the driver for my card and I am now unable to configure an other driver...

Enough writing, obviously, any light would be appreciated, I am now going to post in the display and graphic forum hopping to have some answers...

Have a good day everyone.

---

### Post by presence1960 on 2009-09-12
Sorry I thought I was subscribed to this thread , but it is too late to cry over spilled milk.

I don't know if you tried F4 - safe graphics mode when the CD boots. See [here]("https://help.ubuntu.com/community/BootOptions"). if you have reason to believe your vid card is the problem that would be the first thing to try.

When the Live CD fails to work properly usually the alternate text based installer will work. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by gwu777 on 2009-09-12
No needs to apologise, thank you for your input... As I have described earlier I have tried safe mode and, I am just wondering about the peculiar behavior of the live cd.

---

### Post by presence1960 on 2009-09-12
> **gwu777 said:**
> No needs to apologise, thank you for your input... As I have described earlier I have tried safe mode and, I am just wondering about the peculiar behavior of the live cd.

My bad I didn't make the connection that safe mode is safe graphics mode. Sometimes for whatever the reason, usually related to hardware, the Live Cd does not work properly. In most of those cases the altenate text based installer is the way to go.

The alternate text based installer isn't pretty like the Live Cd, but it has support for much more options than the Live CD does. The main thing about it is that it will usually work where the Live CD does not.

Did you try making a bootable USB from the Live CD iso, provided your machine can boot from USB?

---

### Post by gwu777 on 2009-09-14
Well I have been able to install ubuntu OK now - kind off!

I just want to know why I haven't been able to start the live CD normaly or in sage mode, but it works fine if I go through a canceled instalation... What is the difference - see previous post!

---

