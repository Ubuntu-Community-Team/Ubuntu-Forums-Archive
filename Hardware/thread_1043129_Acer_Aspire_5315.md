---
title: "Acer Aspire 5315"
date: 2009-01-18
forum: Hardware
---

### Post by majingohan99 on 2009-01-18
hi yesterday i installed ubuntu 8.10 dual boot with vista a bit more hectic than i thought but i got it done i shrunk down my d partition 50-50 so ubuntu has 16gb everything seemed ok i connected to internet then started downloading updates then poof everything went off even the AC light telling me it was plugged in i turned it on again & it acted like nothing even happened both ubuntu and vista were fine then again poof off again at totally random times
vista is working perfectly (well not any worse) so cud u plz give me a clue into wot i shud do also the fan sounded dead so it might be overheating so a hand in tht also wud be helpful thnxs

description
The Aspire 5315 combines the Intel Celeron mobile processor, Intel Graphics Media Accelerator (GMA) X3100, Intel High Definition Audio support, and Acer Arcade Deluxe1.


Quick Specs
Intel Celeron (2 GHz), 1 GB DDR II SDRAM, 6.2 lbs, 15.4 in TFT active matrix, Microsoft Windows Vista Home Basic

---

### Post by jfr1tz on 2009-01-18
When you boot ubuntu after awhile it just powers off? and you also can not hear the fan running when booting ubuntu? Is the fan running when you boot vista? and how can you tell it is running or not?

---

### Post by majingohan99 on 2009-01-18
> **jfr1tz said:**
> When you boot ubuntu after awhile it just powers off? and you also can not hear the fan running when booting ubuntu? Is the fan running when you boot vista? and how can you tell it is running or not?

it shuts off the fan makes no sound what so ever but when i boot vista fan kicks in again also its on during start up the ubuntu logo comes up then fans dead in the water i can tell the fan is different than usual coz right now i can here it but in ubuntu it is silent

---

### Post by jfr1tz on 2009-01-18
[fan issues on an aspire 5315]("http://www.google.com/search?q=acer+aspire+5315+ubuntu+fan")

It seems this is a known problem, the first hit on google sends you to a thread on the ubuntuforums[Acer aspire shuts down]("http://ubuntuforums.org/showthread.php?t=604158") which discusses the problem. A quick glance through the topic suggest a bios update might fix the problem, but i suggest reading through the thread first and make sure you have the same problem(updating a bios is not without RISK)

EDIT, i would suggest not booting ubuntu until you have fixed the problem as it appears indeed that the fan is not running, causing the laptop to overheat and shutdown to prevent further damage

---

### Post by FrankBlonk on 2009-06-07
try this page :

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

And edit the file in the terminal window by:

sudo nano /etc/modprobe.d/alsa-base

and add the following line at the bottom:

options snd-hda-intel model=acer 

Reboot youre Laptop.....

problem solved...?

mine did.):P

Good luck....

---

### Post by mysoogal on 2009-08-18
> **majingohan99 said:**
> hi yesterday i installed ubuntu 8.10 dual boot with vista a bit more hectic than i thought but i got it done i shrunk down my d partition 50-50 so ubuntu has 16gb everything seemed ok i connected to internet then started downloading updates then poof everything went off even the AC light telling me it was plugged in i turned it on again & it acted like nothing even happened both ubuntu and vista were fine then again poof off again at totally random times
vista is working perfectly (well not any worse) so cud u plz give me a clue into wot i shud do also the fan sounded dead so it might be overheating so a hand in tht also wud be helpful thnxs

description
The Aspire 5315 combines the Intel Celeron mobile processor, Intel Graphics Media Accelerator (GMA) X3100, Intel High Definition Audio support, and Acer Arcade Deluxe1.


Quick Specs
Intel Celeron (2 GHz), 1 GB DDR II SDRAM, 6.2 lbs, 15.4 in TFT active matrix, Microsoft Windows Vista Home Basic



please be careful when updating bios ! i also have same laptop i updated wrong bios and now cant use laptop its really dead due to the wrong bios flash, i really mean it, please do not touch anything that is bios related if you have to update bios please please make sure you read if its the right bios for your laptop and always double check, as for my laptop tomorrow im going to pay 100 dollars to remove old bios chip and replace with a new one but not with acer because they are such bastards

ACER in my opinionated reasons are really such horrible bastards i will never ever buy laptop from such company. please take my advice do not update to acer 5315 bios update version 1.45 it will really cost you good. ACER soldiered the bios chip in the motherboard and that's how they make money these sick bastards, its a new board you would think they would've used the new method of easy chip implant and remove with a pin. like you get on those desktop boards. wish me luck please work my laptop again i miss watching documentary :(



thanks for your time, and please take my advice


by the way, the over heating can not be fixed really, you will need to go back into ms vista basic and install the epower crap acer pre-installed then cooling will really work. even thu i hate vista i will have to use it again, after my laptop gets new chip

---

### Post by fubarmonkey on 2009-08-19
This is a common issue with overheating. It seems to specially happen after waking up from hibernation/sleep. For whatever reason, the fan bellow the case does not active on wake when it needs to cool down the board, causing the board to overheat and shutdown. Since the fan is controlled by the BIOS, chances are it's been addressed in a BIOS update. I recently downloaded the latest BIOS for the model but have yet to test to see if it continues to do this.

Still, if you have a Windows partition handy (since the BIOS patch is WinXX only) it wouldn't hurt to update the BIOS anyway. Just make sure you download the correct one.

---

### Post by mysoogal on 2009-08-19
I'm happy to say, I'm typing from my Laptop now with the New bios chip replaced. :popcorn: :guitar:

everything works, just need to re-install some usb drivers graphics drivers etc.

I would like to also give you this advice !, Clean your laptop, open it and clean the air intake and outtake you can remove the FAN easy just clean and make sure eveything is clean, i've done this now and i can tell you, everything seem to be cooler, over heating is gone for me, im still on xp pro now, not sure if i will go back to vista, still have ubuntu 8.10 on thu .

---

### Post by abrg on 2009-10-02
a week later now and no over heating using bios v1.45 fixed it up played  a couple of games it used to shut off on and no  more problem with xp or vista i have 2 hard drives vista on one, and xp on the other I updated my bios to v1.45 and so far no over heating, might be bios or the following setting but it works I have had some luck by setting the laptop to never sleep or hibernate while plugged in on Balanced power setting,and set it to do nothing when the top is closed , , I did down load acer power framework and epower as well but I have no idea if it did any good it still over heated afterwards I as well went into advanced settings in control panel for power options, and set the setting for hibernerone ation to 12,000 minutes I am not sure how high it goes I got bored waiting it is kind of slow getting to 10,000,and so far no over heating just something I am trying, I am not a fan of hibernation any how I guess it might bring the expected life expectancy around sooner but at least it is usable in the meantime, I ,ve had the same problem with overheating it started one day I reformatted, and decided to try xp on it I changed to xp then I put vista back on and it still does it when it comes out of sleep mode if I start it and use it without stopping, works fine until sleep mode I emailed Acer no response about it from them yet, but I have read people saying they called Acer , and Acer said they are not aware of it so I when I emailed them included a link to some forums with hundreds of people having these problems using their documents attachment link, on their support email maybe they will check it out I am not holding my breathe i have since switched to Lenovo no problems there my next purchases will not include Acer, for anything I have to pay if I call in I have 4 of these 5315, Acer computers all four have THE SAME PROBLEM , I have installed all these software monitors cleaned , removed the mesh all kinds of things people say worked but none have, none of the monitor programs give the same CPU temp so I have no faith in them hopefully enough people will contact ACER support and get them to do something about it , one would think they would want to to avoid a possible class action suite with all the people that have the same problem I have read in forums a bunch of different solutions none have worked any body know anything I put the copy of XP on the Lenovo comparible to the acer except it works fine on any os,

---

### Post by SemKin on 2009-10-04
**mysoogal!**
How do you solved the problem with the bios acer 5315.YA alterations to 1.45 and all died ((

---

### Post by abrg on 2009-10-09
I’m afraid. Depending on your motherboard and BIOS type, that indicates either a failure to initialise the Display Card, or a failure to complete the memory check. Have a look at your motherboard manual and follow the instructions to ‘reset CMOS’. sometimes i have removed the cmos battery, shorted between the cmos positive and negative contacts,  with something metallic with the laptop unplugged and battery removed That may correct the problem if you’re lucky, but I’m very very doubtful it will.
 
If your motherboard has the BIOS chip inserted , into a socket you should contact the motherboard manufacturer and see if a replacement chip is available.which the acer's I have do not,  If not, you are probably confronted with a ‘dead’ motherboard. I wish I could offer a happier message, but BIOS upgrades are always a risk.

If your computer is working  smoothly, don’t do it. The main two reasons for performing a BIOS upgrade are 

[LIST=1]
[*]To enable support for a new processor that wasn’t available when the motherboard was manufactured..
[*]To correct a ‘known issue’ with the BIOS for your motherboard that causes your computer to function incorrectly.
[/LIST]

---

### Post by valentinraceanu on 2009-11-24
Hi all,

I had some problems with the aspire 5315 too. Here is what worked for me:
If you have overheating problems when returning from standby you need a bios upgrage.
If after a bios update your OS doesn't start it's because it doesn't have SATA drivers and you need to reset HDD Sata Mode setting in BIOS from AHCI to IDE.

Anyone has problems with low battery life (10 minutes) ?

Valentin

---

### Post by Groszman on 2009-12-02
Here ist what worked for me:

you have to take care - using the worng bios can damage your computer to stop functioning at all. Propably according to the reports that told their computer stoped working with BIOS 1.45 the latest BIOS you get on [http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html) is 1.43 which also solves the fan/heat problem.

If you run a parallel windows system, you can download an .exe file which will flash your BIOS. If not, you need to create a FREE DOS iso image containing the BIOS driver. How to do that can be found here:
[http://www.tummy.com/journals/entrie...0080920_234755]("http://www.tummy.com/journals/entries/jafo_20080920_234755")

If you're user of an acer aspire 5315, you can use the iso file, angel garcia created. it worked properly for me. Do the following:
1. Download iso file from:
[http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz](http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz)
2. Burn it
3. Reboot laptop and hit F2 directly in the first screen to enter BIOS. Make sure that your CD Drive ist the first boot drive. Save and Exit
4. Choose: "1) Continue to boot FreeDOS from CD-ROM"
5. Choose: "1) Install to harddisk using FreeDOS SETUP"
6. Don't be afraid: Setup won't install Free Dos to harddrive. Instead you end up on prompt X: - change directory to firm (enter: "cd firm")
7. start "if50.bat" by entering it. That'll flash your BIOS. Afterwards your fans should work properly.

---

### Post by valentinraceanu on 2009-12-18
Why can't I just run the .exe file from Windows to flash my BIOS? I did that and had no problems. Just had to change the setting described above.

---

### Post by Beyo on 2010-01-22
But how can I be sure which BIOS version is correct?
On Acer page BIOS v 1.45 is listed on Vista drivers, but on 5315 I am using XP..so I wouldnt like flashing my BIOS,

Now I must use XP, because this overheating problems...:(

---

### Post by rixtr66 on 2010-03-24
This worked for me.using win7/ubuntu 9.10.
i burned the iso and followed the directions,and viola!
BUT after flashing the bios,the fans ran in ubuntu,however
when i booted into windows i got the blue screen of death!
so i had to reinstall.but overall it was worth it.
thanks
Rick

---

### Post by mitja on 2010-05-11
Flashing the BIOS worked for me as well. Thank you very much Groszman (and also Angel Garcia for making the ISO file).

---

### Post by thaikerman on 2010-05-22
> **majingohan99 said:**
> hi yesterday i installed ubuntu 8.10 dual boot with vista a bit more hectic than i thought but i got it done i shrunk down my d partition 50-50 so ubuntu has 16gb everything seemed ok i connected to internet then started downloading updates then poof everything went off even the AC light telling me it was plugged in i turned it on again & it acted like nothing even happened both ubuntu and vista were fine then again poof off again at totally random times
vista is working perfectly (well not any worse) so cud u plz give me a clue into wot i shud do also the fan sounded dead so it might be overheating so a hand in tht also wud be helpful thnxs

description
The Aspire 5315 combines the Intel Celeron mobile processor, Intel Graphics Media Accelerator (GMA) X3100, Intel High Definition Audio support, and Acer Arcade Deluxe1.


Quick Specs
Intel Celeron (2 GHz), 1 GB DDR II SDRAM, 6.2 lbs, 15.4 in TFT active matrix, Microsoft Windows Vista Home Basic


majingohan99, listen what you are running into is a common bug on Acer laptops and also on some IBM, and Toshibas, if you google through you will see this is is the case. The handling is not yet worked out, it was assigned to Andy Woodcroft to handle and he has been working on it but it is not yet resolved, the problem is cause by the kernel. apparently there is something off on the  handling of the fan and temp setting, the reason vista performs all right is that it does no have this problem with the NTOSKERNEL which is the windows kernel. I would not go playing with the BIOS unless the system manufacturer has issued a new version of the Bios to fix some issue with the system that you have. however make sure it is for your system and for your system alone, ie a bios update for an ACER 5720Z will not work with your system as it is not intended for it. and then again only if you actually are experiencing such an issue, again this bug you are experiencing is not releated to your laptop in specific or even your model of laptop so Bios update will not necesarily fix it.
-
Im sorry I can not give you the solution as its not yet worked out, I  know it sucks, I have an Aspire 5790 and I am also experiencing the same issue, which has been around for more than a year now.

---

### Post by majingohan99 on 2010-08-24
> **thaikerman said:**
> majingohan99, listen what you are running into is a common bug on Acer laptops and also on some IBM, and Toshibas, if you google through you will see this is is the case. The handling is not yet worked out, it was assigned to Andy Woodcroft to handle and he has been working on it but it is not yet resolved, the problem is cause by the kernel. apparently there is something off on the  handling of the fan and temp setting, the reason vista performs all right is that it does no have this problem with the NTOSKERNEL which is the windows kernel. I would not go playing with the BIOS unless the system manufacturer has issued a new version of the Bios to fix some issue with the system that you have. however make sure it is for your system and for your system alone, ie a bios update for an ACER 5720Z will not work with your system as it is not intended for it. and then again only if you actually are experiencing such an issue, again this bug you are experiencing is not releated to your laptop in specific or even your model of laptop so Bios update will not necesarily fix it.
-
Im sorry I can not give you the solution as its not yet worked out, I  know it sucks, I have an Aspire 5790 and I am also experiencing the same issue, which has been around for more than a year now.
heya... thanks for all your help...
Now ubuntu supports all my laptops hardware and am now runnin triple boot of tiny xp / tiny7 and ubuntu 10.04 all serving their purposes....

but a few months ago... i set a bios password on my HDD as all my OS's at the time could be easily acessed... nd it was easier to have one master password.. the password was 10 characters long... then... for reasons i can't remember decided to update the bios... the flash was a success and all my hardware was working... it booted my laptop HDD.. then asked for my password.. i started typing.. pressed enter.. it didn't accept.. thought i did it wrong so tried again... after 5 attempts.. it gave me an error message and went off 0_o
I booted up again.. and as i started to type in my password i realized tht after i reached 8 characters.. it stopped typing ¬_¬
the new bios update (1.37 to 1.(i couldn't giv a *** wot it is, acer can suck my ****) ) wouldn't allow 10 characters.. or let me downgrade the bios to unlock it... i tried everything... first thing was clearing the cmos... even my local PC shop (GHI ( its run by retards who took 3 attempts at replacing psp lcd screen :/ ) gave up nd give me ( charged me ) a new HDD....


now i have a 80 gb locked HDD which won't boot on any other pc/laptop.. but mine... nd is locked....

any ideas... its been sitting in cupboard for a while now... ??
xD

hope u enjoyed my rant... to summarise
acer and GHI are ran by retards...
tht is all
xD

---

### Post by PereUbu on 2010-10-12
Hurra! Flashing the BIOS worked for me too. 
Thanx a bunch Groszman & Angel Garcia!!!!

I have been struggling with this problem for years....

---

### Post by karlmp on 2010-10-13
,

---

### Post by karlmp on 2010-10-13
> **Groszman said:**
> Here ist what worked for me:

you have to take care - using the worng bios can damage your computer to stop functioning at all. Propably according to the reports that told their computer stoped working with BIOS 1.45 the latest BIOS you get on [http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html) is 1.43 which also solves the fan/heat problem.

If you run a parallel windows system, you can download an .exe file which will flash your BIOS. If not, you need to create a FREE DOS iso image containing the BIOS driver. How to do that can be found here:
[http://www.tummy.com/journals/entrie...0080920_234755]("http://www.tummy.com/journals/entries/jafo_20080920_234755")

If you're user of an acer aspire 5315, you can use the iso file, angel garcia created. it worked properly for me. Do the following:
1. Download iso file from:
[http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz](http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz)
2. Burn it
3. Reboot laptop and hit F2 directly in the first screen to enter BIOS. Make sure that your CD Drive ist the first boot drive. Save and Exit
4. Choose: "1) Continue to boot FreeDOS from CD-ROM"
5. Choose: "1) Install to harddisk using FreeDOS SETUP"
6. Don't be afraid: Setup won't install Free Dos to harddrive. Instead you end up on prompt X: - change directory to firm (enter: "cd firm")
7. start "if50.bat" by entering it. That'll flash your BIOS. Afterwards your fans should work properly.

thank you, you saved my life.

---

### Post by filolog on 2010-10-17
Hi,

Just to confirm that **flashing BIOS worked for me as well!**

I had the same fan issue on **[COLOR=Red]ACER Aspire 5315[/COLOR]**. Fan did not work on Ubuntu or any other linux from LiveCD or LiveUSB (it worked properly under Vista, though). After 15 minutes, laptop would just overheat and shut down...

I read thousands of posts, and became very suspicious of the .exe application for flashing BIOS v1.45 in Windows Vista (which is the latest and the only one to download from this [COLOR=Red]ACER.CO.UK[/COLOR] site):

[http://www.acer.co.uk/acer/service.do;jsessionid=AB12754677EB7CC33930582BE04AB4BA.public_a_14a?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1.att21k=1&CRC=3713735360](http://www.acer.co.uk/acer/service.do;jsessionid=AB12754677EB7CC33930582BE04AB4BA.public_a_14a?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3734&sp=page15e&ctx2.c2att1=17&miu10ekcond13.attN2B2F2EEF=3734&CountryISOCtxParam=UK&ctx1.att21k=1&CRC=3713735360)

Too many a folk reported that it broke their BIOS (even by running it as an administrator and closing all other applications like AV, wireless, etc.)

I decided not to trust it and instead I used the live CD ISO with FreeDOS and v1.43 BIOS prepared by Angel Garcia.

(by the way, v1.43 of BIOS seems to be the latest on [COLOR=Red]ACER.COM[/COLOR] site:  [http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html))

I extracted the file on my other Fujitsu-Siemens laptop with PClinuxOS and burned the iso and followed Groszman's directions! 

Thank you very much Groszman (and also Angel Garcia for making the ISO file). 
You saved me from sloooooow and crappy Vista on this Acer dual-boot laptop. I can now enjoy my Ubuntu 10.04 and fan issue is gone!!!!

---

### Post by frumblebear on 2010-12-23
Just flashed the BIOS on Acer 5315 using the instructions by Groszman. Brilliant. Fan working properly. very grateful to Groszman et al.:D

---

### Post by rocket321 on 2011-02-02
This definitely solved my problem with no fan/overheating problem on ACER Aspire 5315. I have read in other forums that it could be the bios, but I also read never mess with the bios. So I dealt with this problem since 9.10, until I found these great instructions on updating the bios and the great reviews it got. So I took a chance and it worked!!! Thank you so much!!!

---

### Post by diarmuid_mcdaid on 2011-02-15
Hi, I'm still struggling with this issue.

I first downloaded and extracted angel garcia's iso. Then burned this to cd. I then changed the boot order so i could boot from the cd. I seems the laptop will not boot from cd, and boots straight into ubuntu. 

I then downloaded UNetbootin and used the same iso, and created a bootable flash drive. I then changed the boot order, and this time the laptop booted from the flash drive. 

I then choose option 1, this brings me to another screen with the option 1. Install to harddisk using FreeDOS SETUP (default) .

I select this option then, I Get:

FreeCom version 0.84-pre2 XMS_Swap [Aug 28 2006 00:29:00]
A: is MEMDISK.
Checking for CDROM driver or c:\fdbootcd.iso...
El-Torito Bootable CD-ROM Driver for Dos v1.4, [http://www.nu2.nu/eltorito/](http://www.nu2.nu/eltorito/)
(c) 2000 by Gary Tong
(c) 2001-2002 by Bart Lagerweij
No Booted CD-ROM found.
Driver not installed 
CDROM found, checking for \freedos\setup\odin directory...
There is no CDROM, or the wrong CD-ROM! 
A:\>\

Please Help! Many Thanks!

---

### Post by Ryanlundie on 2011-03-17
Hey guys,
Its not working for me either.
I tried angel garcia's iso but it booted into ubuntu.
Really appreciate your help guys

---

### Post by GuestBob on 2011-05-08
> **Groszman said:**
> Here ist what worked for me:

you have to take care - using the worng bios can damage your computer to stop functioning at all. Propably according to the reports that told their computer stoped working with BIOS 1.45 the latest BIOS you get on [http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html) is 1.43 which also solves the fan/heat problem.

If you run a parallel windows system, you can download an .exe file which will flash your BIOS. If not, you need to create a FREE DOS iso image containing the BIOS driver. How to do that can be found here:
[http://www.tummy.com/journals/entrie...0080920_234755]("http://www.tummy.com/journals/entries/jafo_20080920_234755")

If you're user of an acer aspire 5315, you can use the iso file, angel garcia created. it worked properly for me. Do the following:
1. Download iso file from:
[http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz](http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz)
2. Burn it
3. Reboot laptop and hit F2 directly in the first screen to enter BIOS. Make sure that your CD Drive ist the first boot drive. Save and Exit
4. Choose: "1) Continue to boot FreeDOS from CD-ROM"
5. Choose: "1) Install to harddisk using FreeDOS SETUP"
6. Don't be afraid: Setup won't install Free Dos to harddrive. Instead you end up on prompt X: - change directory to firm (enter: "cd firm")
7. start "if50.bat" by entering it. That'll flash your BIOS. Afterwards your fans should work properly.

This.

Thank you very much for explaining this so clearly, I join a line of other newbies who have managed not to hose their computer whilst performing this fix.  I needed to sit my laptop on top of a bag of frozen peas to be able to get it to run for long enough to do this (rock on with veg. cooled hardware).  

Also, I tried this with a USB (UNetbootin) like a couple of other people in this thread and it didn't work.  Used a CD; first time - it's a mystery to me but there it is.

---

### Post by Groszman on 2011-10-19
Sorry guys, i've got no idea how to fix the my computer won't-boot-from-cd-rom-problem. but here is an actual link to the free dos version by angel garcia.
[http://dl.dropbox.com/u/14099789/FDOS_v1_43.iso.tar.gz](http://dl.dropbox.com/u/14099789/FDOS_v1_43.iso.tar.gz)

---

### Post by rickarino on 2011-10-26
I just followed the step by step, booted linux and observed the fan spinning away!  I'm way more psyched than I should be. :)

---

### Post by msalo on 2011-11-24
Thank you! It seems I got the help for my exact same problem here. Flashing was a success and the fan is now clearly running.

I almost bought a new laptop for my kids, but now you've save me plain cash! Thanks again!

---

### Post by alpage2 on 2012-02-05
> Originally Posted by Groszman View Post
Here ist what worked for me:

you have to take care - using the worng bios can damage your computer to stop functioning at all. Propably according to the reports that told their computer stoped working with BIOS 1.45 the latest BIOS you get on [http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html) is 1.43 which also solves the fan/heat problem.

If you run a parallel windows system, you can download an .exe file which will flash your BIOS. If not, you need to create a FREE DOS iso image containing the BIOS driver. How to do that can be found here:
[http://www.tummy.com/journals/entrie...0080920_234755](http://www.tummy.com/journals/entrie...0080920_234755)

If you're user of an acer aspire 5315, you can use the iso file, angel garcia created. it worked properly for me. Do the following:
1. Download iso file from:
[http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz](http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz)
2. Burn it
3. Reboot laptop and hit F2 directly in the first screen to enter BIOS. Make sure that your CD Drive ist the first boot drive. Save and Exit
4. Choose: "1) Continue to boot FreeDOS from CD-ROM"
5. Choose: "1) Install to harddisk using FreeDOS SETUP"
6. Don't be afraid: Setup won't install Free Dos to harddrive. Instead you end up on prompt X: - change directory to firm (enter: "cd firm")
7. start "if50.bat" by entering it. That'll flash your BIOS. Afterwards your fans should work properly.

I have downloaded the FDOS iso from angel garcia, burned it to disk, and successfully flashed the BIOS on my acer 5315. The BIOS flash appeared to go well, and reported success when it had finished, and on reboot, I can enter the BIOS setup screen and it reports version 1.43 - so far, so good!

But when I try to boot from either hard drive, dvdrom, or a USB stick with an ubuntu install system on, the result is always the same - a black screen with the message:

BOOTMGR missing

Ctrl Alt Del to reboot.

I should add that prior to this the hard drive had been wiped clean, so no OS, ready for an ubuntu install.

I had tried to install Win95, to use the windows method of flashing the BIOS, but the Win95 installer had not been able to see the Hard Drive. In light of events, I would have suspected a 
hard drive fault, were it not for the fact that I can't boot from DVD or USB either.

Can anyone advise what the problem is? Do I need to set up something in the BIOS - I couldn't see any obvious settings that needed changing. Boot order was HD followed by DVD, as one would expect.

Help!

Thanks in anticipation
Alan

I figured it out - due to overheating and laptop cutting out in mid install - I got it going again and got as far as deleting partitions to clean up after failed install - leaving the HD with no MBR - and the BIOS was hanging when it hit that problem with the hard drive, and not moving on to try the other boot devices. I simply moved the cdrom up in the boot order to first place, and ubuntu it is now installing from the install CD. Fan is reassuringly active!
Alan

---

### Post by opentheforumwetcants on 2013-02-23
Thank you.

---

### Post by eljaywasi on 2013-06-20
Sorry for reviving an old post but I am trying to correct this same issue with a friend's Acer Aspire 5315. I've got 13.04 installed for her but if the laptop doesnt get good air flow it'll overheat and shutdown. I assume that flashing the bios will fix this but Angel Garcia dropbox link ([http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz](http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz)) doesn't work anymore. Does anyone know if this can still be found anywhere? 

I guess I could install windows again or run freedos myself but the only bios I can get is the 2008 v1.45 .exe on the Acer website which it sounds like doesn't work for most people. The laptop really isnt worth fixing if the motherboard get bricked, but then again she can't afford a new one right now.

---

### Post by BlinkinCat on 2013-06-20
> **eljaywasi said:**
> Sorry for reviving an old post but I am trying to correct this same issue with a friend's Acer Aspire 5315. I've got 13.04 installed for her but if the laptop doesnt get good air flow it'll overheat and shutdown. I assume that flashing the bios will fix this but Angel Garcia dropbox link ([http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz](http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz)) doesn't work anymore. Does anyone know if this can still be found anywhere? 

I guess I could install windows again or run freedos myself but the only bios I can get is the 2008 v1.45 .exe on the Acer website which it sounds like doesn't work for most people. The laptop really isnt worth fixing if the motherboard get bricked, but then again she can't afford a new one right now.

Hi,

Rather than resurrecting a thread marked solved, you would be better off creating a new one.
You can always include a link back to this thread if you wish.

Cheers and good luck - :)

---

### Post by alpage2 on 2013-06-20
I can't put my hands on the file previously offered by Angel Garcia, but due to the cack-handed way I went about it, I did not use it. I have the DOS and windows-based files for this version of the BIOS (v. 1.43), and all you should need in addition is FDOS, which you can get from [www.fdos.org](www.fdos.org). If you would like to send me your email address by private message, I'll attach the files to my reply.

Alan

---

### Post by eljaywasi on 2013-06-23
PM sent, thanks Alan!

---

### Post by alpage2 on 2013-06-30
Hi Lee

Did the 1.43 BIOS file work OK? Did you use it with windows or FDOS?

Alan

---

### Post by eljaywasi on 2013-07-02
Hi Alan,

Thanks again for the files! I finally convinced my friend to accept the risk in trying to update the BIOS this evening but unfortunately ran into a road block: The CD-ROM drive no longer functions so I can't use a CD image and USB key is also a no-go since I can't seem to get it to boot FDOS from the USB no matter what boot order I select in the BIOS. So I guess we're stuck until perhaps we can locate a usb cdrom drive to try. Unless anyone has any suggestions?

PS: I also noticed that although Groszman's link is broken it appears Angel Garcia's dropbox link with the original ISO is still functioning:
[http://dl.dropbox.com/u/14099789/FDOS_v1_43.iso.tar.gz](http://dl.dropbox.com/u/14099789/FDOS_v1_43.iso.tar.gz)
Maybe it will be useful for someone in the future!

---

### Post by alpage2 on 2013-07-03
Hello Lee

Thanks for the update - yes, it sounds like the only way forward is to buy or borrow an external CD/DVD drive - or maybe an empty external hard drive might work in a similar way?

If you can download Angel Garcia's file - that will probably be easier to use, since it combines everything you need  ;)  - and if not, I have since discovered that I do have that file, on another machine.

Good Luck
Alan

---

### Post by sparklenet on 2013-07-08
This has been a very helpful thread, and thank you for keeping it going. If you opened a new thread (as was suggested above) this Noob might not find the way there.
 My Acer 5315 overheated and shut down just as the Ubuntu 12.04 was beginning the install. No operating system now, as I used DBAN first. After I let it cool overnight, what should my next step be? 
Thanks

---

### Post by alpage2 on 2013-07-08
Hello Sparklenet

Absolutely right - better to keep all the information in one place. New threads are for different subjects ;-)

No worries about your 5315 - this is exactly the same position I found myself in - and everything you need is in this message thread.

Some of the links to the BIOS file no longer work - but one does:

Go back to message #29 by Groszman and download FDOS_v1_43.iso.tar.gz, on a working machine.

This contains the bios update file that you need, and FDOS.

Expand the archive and create a boot FDOS CD, (read all of my original message #32, including instructions from Groszman).

Boot the 5315 with the FDOS CD and run the bios update on the 5315 - following all instructions very carefully - in particular, do not interrupt it whilst it is installing the bios, or you will most likely end up with a brick!

After the bios update, you should find that ubuntu installs normally, with the fan purring happily in the background  :-)

Good Luck!
Post back with any problems, and with the outcome  ;-)
Alan

---

### Post by sparklenet on 2013-07-08
Alan,
Thank you for pointing me in the right direction. I'm on my way, but still lost :???:
I followed your post #32, steps 1-3. Could not find option 4 or 5, so I opened the CD drive and re-inserted the FDOS v1.43 disc and hoped for the best. Apparently Ubuntu installed further than I thought, as it chose to try to boot OS from the HD, even though I just made sure to save CD drive as first. I got a frozen Ubuntu desktop, stuck cursor. I did a hard shutdown.
I am certainly learning some new things! 
What is the next step?
Sparklenet

---

### Post by alpage2 on 2013-07-08
Hi Sparklenet

It sounds like your existing bios is set to boot from the HD, first.

You just need to change the boot order to CD first, in the system bios.

Turn on and enter the bios - F2 or del - can't remember which - find and change the boot order to CD first.

Then try again to boot from FDOS boot CD.

Almost there  ;-)
Alan

---

### Post by sparklenet on 2013-07-08
Alan

I did hit F2 to access BIOS, right arrow to 'boot' tab, first listed is CD/DVD drive, second is HDD. Save and exit. FDOS disc in drive spins, Ubuntu starts to boot. It opens up Ubuntu desktop, but cursor is frozen and error message pops up.
I did this with FDOS disc in drive from the  start. Is there a step I'm missing?

---

### Post by sparklenet on 2013-07-08
Alan,

F2: Information, Main, Security, Boot, Exit; right arrow to Boot
Boot:
Boot Priority Order:
1: IDE 1: Optiarc CD-RW
2: IDE 0: Hitachi HTS541....
3: Network Boot
4: USB HDD
5: USB FDD
6: USB CDROM

F10 Save and exit
 Exit saving changes?
 choose YES, enter

CD drive spins, it boots to Ubuntu Desktop, cursor frozen
Besides hard shutdown, how else can I exit?

What next should I try?

Sparklenet

---

### Post by alpage2 on 2013-07-09
Hi Sparklenet

It looks as though it is not recognising the FDOS cd as a boot disk, and passing on to boot from the hard drive.

Can we just confirm exactly how you created the FDOS disk:

1. downloaded FDOS_v1_43.iso.tar.gz  from the link in message #29?

2. extracted the archive?  tar -zxvf FDOS_v1_43.iso.tar.gz    ?

3. burned the resulting .iso file (FDOS_v1_43.iso) to a CD?

Is the answer yes to every question, above? If not, how does it vary?

What software application did you use to burn the .iso  - and what settings did you choose?   - this may be where the problem lies.

Regards
Alan

---

### Post by sparklenet on 2013-07-10
Hello Alan,

Ah, now here is where I missed it, step #2. Being new to Ubuntu, I am not yet familiar with extracting archives (would that be unzipping files?). 
1. I downloaded FDOS_v1_43.isotar.gz.
(missed step 2, thinking it would be done magically in the next operation ;)
3. burned the downloaded file to CD.

OK. Now that I've used Archive Manager to extract an .iso file, I have another noob question for you. The CD burning application gave me two choices:
--"Do you want to create a disc from the contents of the image or with the image file inside? There is only one selected file (FDOS_v1_43.iso). It is the image of a disc and its contents can be burned."--
 So, do I want to "burn as file" or "burn contents"? I want to make sure and do it right this time.

I will wait for reply before proceeding.

Thanks,
Sparklenet

---

### Post by alpage2 on 2013-07-10
Hi Sparklenet

Mystery solved  :-)

What you need to do is to burn the image to a CD  -  this is not the same as merely copying the file to a CD  - it has to burn the image!

Unfortunately, the options offered (was this on a windows machine?) are a bit ambiguous, so you may have to try both, and see which one works as a boot disk!  ;)

A few more hints on burning .iso images:

If this is a windows PC, windows will just automatically use the highest burning speed available on your hardware, sometimes resulting in a faulty boot disc, which won't work, or worst case scenario, could result in a corrupted bios file that bricks the 5315.

I would advise the use of a third-party cd/dvd burner that gives you control over the burn speed, and use a slow speed. I see in the ubuntu download pages the recommendation is infraRecorder:  [http://infrarecorder.org/](http://infrarecorder.org/)

If burning the .iso on an ubuntu machine, I'm afraid the default disk burner has always been a bit flaky. I always install k3b - should be available in the software centre - an excellent disk burner with control over the speed. Choose to burn an image file, at a  slow speed, with an automatic write verify and you should be good to go.

Good luck
Alan

---

### Post by sparklenet on 2013-07-10
Hi Alan,

I really appreciate the specific details you just shared about disk burning software. I installed Ubuntu successfully on my old Windows XP desktop last week. I was using the default disc burner that came bundled in U 12.04. I am so new to Ubuntu I haven't had the chance to tweak it with new software yet, so I value the nod toward reliable and useful applications.

I will install k3b when I find it, and try this process again. 

Encouraged,
Sparklenet

---

