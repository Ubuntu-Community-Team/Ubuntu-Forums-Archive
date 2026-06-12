---
title: "Ubuntu 9.04 upgrade from Ubuntu 8.10 and ATI cards fglrx problem"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by cluendo on 2009-04-23
Hey! Today I was upgrading my Ubuntu 8.10 to Ubuntu 9.04 and get a attention about my ATI fglrx driver problem...I have ATI Radeon x700pro card. I can't believe.. Is this means that my card is no longer supported by this driver ?? What should I do to fix it? Is there any way to solve this problem somehow ? Uhh... I very want to test this new release..
Thanx 4 All :)

---

### Post by cluendo on 2009-04-23
No answers ?

---

### Post by autra on 2009-04-23
[http://ubuntuforums.org/showthread.php?t=1133844&page=2](http://ubuntuforums.org/showthread.php?t=1133844&page=2)

look at this

It seems that you need the new version of fglrx, because the old ones are not compatible with the new xorg server in jaunty.
But a lot of graphic card are not compatible any more with the new version of fglrx.

You have no choice but using open source drivers if they work for you, or staying in 8.10 (like me)

---

### Post by cluendo on 2009-04-23
Heh...Its not fair..I will not be able to use this version of ubuntu ? ... Open source drivers is sh*t at the moment.. ......

---

### Post by napzilla on 2009-04-23
Buy a new graphics card? I'm going with the "stay with Intrepid for a bit and see if someone develops a workaround" strategy, myself.

---

### Post by elleppahc on 2009-04-23
I have just finished this upgrade which tool 4 hours.
Now on boot up no display.
I HAVE A ATI RADEON 1600 PRO CARD and had some initial display problems with 8.10 updates, was able to resolve by safe mode options.
With 9.04 it deletes options and gives no alternative. Cant update my graphics card any more as it is a pci card.
My system is now stuffed until some one comes up with a solution that can be done on boot up by usb or cd.
Or worst way complete new install. I have used linux for a year without much trouble. I have a backup of most, but have or will loose data without the time to do it all again. What a shame I can see some people returning to Windows. The programmers need a severe kicking for this, it takes a long time to gain ground against windows only to loose it with this type of upgrade.

---

### Post by JK3mp on 2009-04-23
Ick ! could this be true!?! LoL, i too have an ATI card. And im downloading jaunty right now. I'll try it on a seperate partition for testing. If i have any luck or figure anything out i'll let ya know ;)

---

### Post by BubuXP on 2009-04-23
> **elleppahc said:**
> [...] The programmers need a severe kicking for this, it takes a long time to gain ground against windows only to loose it with this type of upgrade.

Repeating what are the issues:

- Jaunty comes with X.Org server 1.6 and fglrx 9.4

- only fglrx 9.4 and upper versions will be compatible with xorg-server 1.6, so you cannot use previous versions of fglrx on Jaunty.

- beginning with version 9.4, the fglrx driver have no more support for old GPU models (more info here [http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_94&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_94&num=1) )

- the 9.4 driver isn't so stable even with the right GPUs


This said, in effect I don't understand why programmers didn't add some "GPU check" on the restricted drivers manager, to remove the possibility to install the driver with the old GPUs (or to advice the users in case of distro upgrade). Maybe with an update this can be fixed...

---

### Post by Rywern on 2009-04-23
heh, i have both an ati machine (that i use daily with two monitors) and a nvidia one, no problems whats so ever on the nvidia one.. pressed the upgrade distro button. blop blopadop all done and working as planned (even better than before) but ive been sitting with my ati machine all day trying to work out the kinks with the new drivers and such... having two monitors arent really helping here either...

so im gonna stick to 8.10 on my ati machine for now... soon im gonna get myself a nvidia card for that one too but i guess ill live for now...

now for the actual testing part.
i tried the one you install through "Hardware Drivers", i tried without it and just installing 9.4 from atis homepage, and  tried withoutanything at all.. just to see.... so far im not sure which one is best.. but im leaning towards the one you get from ubuntu itself.. with alittle tweaking in the "display" tool...

---

### Post by Slowspeed on 2009-04-23
I just completed upgrading from 8.10 to 9.04. I used the gui Update Manager. The Upgrade process notified me that the ATI fglrx driver was not supported and gave me the option to stop the upgrade or continue with default opensource driver. I don't use compiz and I have not see the new notification alerts yet. Flash playback is acceptable and the gui screens render fine. 
I do see on bootup some freezing pixelation screen before the hour glass and it is slow to draw the initial desktop. After, it settles down initial testing seems fine. 
I am using an old ati radeon xpress card that only has 128MB of ram.
Just thought I would share my initial results.

---

### Post by jemlinus on 2009-04-23
I guess I'm going have fun with my x300 card. :(

---

### Post by BobbyS on 2009-04-23
I also run a x300.....................glad I didn't upgrade! :rolleyes:

---

### Post by s3lekta on 2009-04-23
jumped on the bandwagon ...

upgraded - rebooted - black screen

on a Vaio with a ati mobile 3400 hd :(

---

### Post by ukoda on 2009-04-23
Same story as most here but now it's looking great and features that didn't work before now work.  After doing the upgrade I was left a scrambled screen when it was to switch to hire mode.  The general step I took to fix it were:
1. Booted from a Ubuntu Gutsy USB key. Other versions and CD should be fine too.
2. Opened a terminal and used "sudo su" to become root.
3. Mounted my hard drive.  In my case "mkdir /mnt/sda5" then "mount -t ext3 /dev/sda5 /mnt/sda5".  Use "fdisk -l" to find the right place.
4. Downloaded the latest diver using wget after finding the right URL from the ATI website.  Look at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) for my HD 3200 card I needed "wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-4-x86.x86_64.run"
5. After it download rebooted and selected recovery option at boot menu.
6. Selected the "NETROOT" option.
7. Ran the downloaded "sh ./downloadedfile".
8. Went with default options.
9. Rebooted and all was good in the world!

NB: Your mileage may vary.

---

### Post by s3lekta on 2009-04-24
> **ukoda said:**
> Same story as most here but now it's looking great and features that didn't work before now work.  After doing the upgrade I was left a scrambled screen when it was to switch to hire mode.  The general step I took to fix it were:
1. Booted from a Ubuntu Gutsy USB key. Other versions and CD should be fine too.
2. Opened a terminal and used "sudo su" to become root.
3. Mounted my hard drive.  In my case "mkdir /mnt/sda5" then "mount -t ext3 /dev/sda5 /mnt/sda5".  Use "fdisk -l" to find the right place.
4. Downloaded the latest diver using wget after finding the right URL from the ATI website.  Look at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) for my HD 3200 card I needed "wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-4-x86.x86_64.run"
5. After it download rebooted and selected recovery option at boot menu.
6. Selected the "NETROOT" option.
7. Ran the downloaded "sh ./downloadedfile".
8. Went with default options.
9. Rebooted and all was good in the world!

NB: Your mileage may vary.

sorry guys,stupid question.... will step 1 work if i have installed this through wubi?

also for step #1, I can just use my ubuntu 8.10 cd to boot up right?

last question, for step #3. how would i determine what to mount? ex: which sda number? like what he used above, sda5.

i just want to make sure, so i dont end up upgrading and then get stuck at a black screen again ... then restore back to 8.10 :(

thanks

---

### Post by CorporateGoth on 2009-04-24
*sigh* looks like the new driver dropped support for my FireGL V5200 card to (lowest FireGL is V5600).  But being on a laptop, I can't upgrade the vid. card.  At least, not easily (or cheaply).

But then, ATI has been terrible with linux support for a number of years now.  I guess for now I am stuck on the OS drivers.

---

### Post by SR_ELPIRATA on 2009-04-24
I joined ubuntu with 7.10 and 8.04 was a change that I didnt like much, graphics wise and I had an nvidia video card then. Since then, I've decided that I'm not going to even try .04 versions, usually .10 works as a charm.

So I plan to wait, as now I have an HD 3300 (asus built in) and I dont want to get a black display surprise :)

Of course, if they upgraded that thing... 9.10 will reveal some problems as well, unless they polish your suggestions and put them to work.

ELP

---

### Post by eggplant37 on 2009-04-24
> **JK3mp said:**
> Ick ! could this be true!?! LoL, i too have an ATI card. And im downloading jaunty right now. I'll try it on a seperate partition for testing. If i have any luck or figure anything out i'll let ya know ;)

Here's the warning I'll make. I upgraded last night from 8.10 to 9.04. I had 3D working well enough to run World of Warcraft on wine without much problem, albeit with low frame rates with the 9.3 Catalyst drivers. Not impossible to play, but not a real joy, either.

Now, after the upgrade last night, I'm averaging 1-3 fps using the ati radeon driver installed with 9.04 on a Dell Inspiron 1501 laptop with the Radeon Xpress 200M chip in it. 

Don't waste your time until they determine where the problem is and get this crap fixed. I'll be reverting to 8.10 this weekend.

---

### Post by StuartN on 2009-04-24
> **eggplant37 said:**
> Now, after the upgrade last night, I'm averaging 1-3 fps using the ati radeon driver installed with 9.04 on a Dell Inspiron 1501 laptop with the Radeon Xpress 200M chip in it.

I just tried the live cd Jaunty 9.04 on my Dell Inspiron 1501 and was pleased to see both the Broadcom wireless (using the wl driver) and the ATI Radeon Xpress 200M video (using the radeon driver) worked out-of-the-box.

But as you say, the old radeon driver is way slower than Catalyst 9.4, so I am not installing yet.

---

### Post by fmfrisch on 2009-04-24
Upgraded from 8.10 to 9.04. After reboot the grapic worked. But not really good. Wasnt able to enable Compiz etc. Upgraded my restricted ATI driver to the latest version. Things got better but the ATI driver is really unstable and buggy. Maximizing windows takes forever. Movie playback is bad. I'm on a Radeon HD3650. Just thought I should share.

---

### Post by LT1Caprice57L on 2009-04-24
Yep.  Graphics performance was all but pathetic in 9.04 with my Mobility Radeon 9000.

'Course, being on a laptop means that if I want a new video adapter, I have to buy a new laptop. [IMG]http://i141.photobucket.com/albums/r60/mr740ti/squint.gif[/IMG]

Oh well, I was planning on it anyway...

---

### Post by DwalerXIII on 2009-04-24
I tried the live cd and even that is not working. I have a HD2600 pro.
The splashscreen appears and then there's the black screen with some lines of colors at the top of the screen. I tried in safe mode but then I can't get the resolution right. My monitor is a wide screen with resolution 1680x1050. In safe mode I have only 1024x768.

I made the switch to ubuntu with Dapper Drake. Every new release was better than the one before. This in not the case anymore. 

Also my laptom with an intel graphics card cannot run Compiz anymore. 
Ubuntu is going backwards.

---

### Post by Muchacho_Gasolino on 2009-04-24
I've got a Thinkpad T43 with an ATI x300. I upgraded yesterday and saw the scrambled screen. I downgraded to the radeon driver by booting in recovery mode and

```
sudo apt-get remove xorg-driver-fglrx
```

Jaunty is really pretty, and now I can at least see it, but my processor is constantly loaded and I have some weird scrambled graphics problems when scrolling 2D windows sometimes. 

I suppose I'm behind the times, but it seems odd for AMD/ATI to consider a card "legacy" that is five years old and still obviously in wide use...

Is there a way to only downgrade the Xorg server?

---

### Post by ukoda on 2009-04-24
> **s3lekta said:**
> sorry guys,stupid question.... will step 1 work if i have installed this through wubi?

also for step #1, I can just use my ubuntu 8.10 cd to boot up right?

last question, for step #3. how would i determine what to mount? ex: which sda number? like what he used above, sda5.

i just want to make sure, so i dont end up upgrading and then get stuck at a black screen again ... then restore back to 8.10 :(

thanks

The is three basic things you must do.  Find the right file. Get it somewhere you can access on the affected system.  Boot to the command line as root and run it.

I have no experience with wubi so can not help directly.  The first step, finding the file, can be done with any machine.  My steps were to allow that to be the affected machine.  In your case you could find it from Windows and write the target URL, carefully, on paper.  Then boot the affected system to a command line in recovery mode, use wget and hand enter the URL you wrote down.  Then run it.  That would save all the complication of mounting partitions etc and may be the best way in your case.

---

### Post by kpkethc on 2009-04-25
I can't begin to express my frustration with this. I am new to Ubuntu about 6 months ago. I amazed at how 8.10 handles graphics on my laptop with an Xpress 1100 card. Now, I can't run compiz and things just don't look right. Is there any hope for a future driver or we pretty much SOL? Hopefully someone could shed some light so I can just go back to Intrepid.

---

### Post by s3lekta on 2009-04-25
> **ukoda said:**
> The is three basic things you must do.  Find the right file. Get it somewhere you can access on the affected system.  Boot to the command line as root and run it.

I have no experience with wubi so can not help directly.  The first step, finding the file, can be done with any machine.  My steps were to allow that to be the affected machine.  In your case you could find it from Windows and write the target URL, carefully, on paper.  Then boot the affected system to a command line in recovery mode, use wget and hand enter the URL you wrote down.  Then run it.  That would save all the complication of mounting partitions etc and may be the best way in your case.

thanks, for responding ... that makes sense i'll give it a shot

---

### Post by carusoswi on 2009-04-25
I run a six-year old Shuttle XPC that includes an ATI RV350 (as Radeon 9550) onboard graphics card.  As I used the update manager to upgrade from 8.10 to 9.04, I also received the message about the ATI fglrx on my system not supported.  Being the fool-hearty type, I clicked to continue the upgrade.

To my surprize, the upgrade went smoothly, my display is working, compiz is working, and I didn't have to do anything out of the ordinary.

Is my card new enought that it is being supported?  I am not the lucky type, so pure luck cannot be the explanation for my lack of problems.

Caruso

---

### Post by ales on 2009-04-25
Hi,

I stopped upgrade after the warning, that my X800 /RV400 ot 450/ is no more supported. **But I have the question, ati writes on their www, that users using older chips should use their 9.3 driver. Does this mean, tthat this driver will work on 9.04 or not? **
Ubuntu just says, there is no support.

Does this mean, that al users with older chips should stay in 8.10 Ubuntu or buy a new card?

Considering this, and also previous problems with ATI drivers under Linux, I have a strong feeling, that I will not buy ATI anymore but nVidia maybe...

Ales

---

### Post by darojasp on 2009-04-25
> **ales said:**
> Hi,

I stopped upgrade after the warning, that my X800 /RV400 ot 450/ is no more supported. **But I have the question, ati writes on their www, that users using older chips should use their 9.3 driver. Does this mean, tthat this driver will work on 9.04 or not? **
Ubuntu just says, there is no support.

Does this mean, that al users with older chips should stay in 8.10 Ubuntu or buy a new card?

Considering this, and also previous problems with ATI drivers under Linux, I have a strong feeling, that I will not buy ATI anymore but nVidia maybe...

Ales

It won't work because the driver 9.3 is not compatible with X.org Server 1.6

---

### Post by caravel on 2009-04-25
WellI upgraded to 9.04 yesterday and everything was going fine.  I was playing Quake4, Doom3 and UT2K4 flawlessly.  Booted up this morning and black screen with a garbled red stripe near to the top (the login screen) and the whole system locked up.

I had to reboot in recovery mode, do the x server fix and then drop to the root terminal and do "sudo apt-get remove fglrx*" and hope for the best.  That got it working again, but I see that the newer driver is still not available.  I can only get the older driver (8.3?) through apt and this apparently doesn't work with the latest version of xorg??  This begs the question:  Why was it working for me last night??  I had rebooted as well about 3 times and it was still working.

I'm downloading the 9.4 drivers from ATI now.  I have an HD 3650 so fingers crossed it will work.

---

### Post by caravel on 2009-04-25
I installed the 9.4 drivers with exactly the same result and had to uninstall them from the recovery root terminal (/usr/share/ati/fglrx-uninstall.sh) and restore xorg.conf from a backup.  It's working now but without the fglrx driver - so no OpenGL.

What's the next stage a clean install?

---

### Post by eggplant37 on 2009-04-25
> **caravel said:**
> WellI upgraded to 9.04 yesterday and everything was going fine.  I was playing Quake4, Doom3 and UT2K4 flawlessly.  Booted up this morning and black screen with a garbled red stripe near to the top (the login screen) and the whole system locked up.

I had to reboot in recovery mode, do the x server fix and then drop to the root terminal and do "sudo apt-get remove fglrx*" and hope for the best.  That got it working again, but I see that the newer driver is still not available.  I can only get the older driver (8.3?) through apt and this apparently doesn't work with the latest version of xorg??  This begs the question:  Why was it working for me last night??  I had rebooted as well about 3 times and it was still working.

I'm downloading the 9.4 drivers from ATI now.  I have an HD 3650 so fingers crossed it will work.

Good luck. Please report back on whether or not you had success, as I'm stuck with an Xpress 200M that won't do diddly dee with 3D apps like World of Warcraft. I could use help with word on a fix.

---

### Post by eggplant37 on 2009-04-25
> **caravel said:**
> I installed the 9.4 drivers with exactly the same result and had to uninstall them from the recovery root terminal (/usr/share/ati/fglrx-uninstall.sh) and restore xorg.conf from a backup.  It's working now but without the fglrx driver - so no OpenGL.

What's the next stage a clean install?

Ah, I see. You sound like you've had exactly same results as I have. I don't relish having to reload this laptop, as I've a huge vmware partition on it, a bunch of data and my Warcraft directory to back up in order to reload it. Maybe this time I'll partition off my /home dir.

---

### Post by Jackelope King on 2009-04-25
According to ATI's website, my graphics card is compatible with the newest driver (ATI Catalyst 9.4 Proprietary Linux x86 Display Driver). I see a lot of people talking about v9.4 vs. v9.3. If this driver is available for me (ATI Mobility Radeon x700, which isn't on the list of now-legacy graphics cards), am I good to go on an upgrade to Jaunty (barring other potential disasters)?

---

### Post by ales on 2009-04-25
> **Jackelope King said:**
> According to ATI's website, my graphics card is compatible with the newest driver (ATI Catalyst 9.4 Proprietary Linux x86 Display Driver). I see a lot of people talking about v9.4 vs. v9.3. If this driver is available for me (ATI Mobility Radeon x700, which isn't on the list of now-legacy graphics cards), am I good to go on an upgrade to Jaunty (barring other potential disasters)?

The following products have been moved to the legacy software support structure (**including Mobile** and All-in-Wonder Variants):

ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
**ATI Radeon X700 Series**
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series


AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

Any customers using a combination of a ATI Radeon™ HD 2000 Series, ATI Radeon™ HD 3000 Series, or ATI Radeon™ HD 4000 Series product with any of the legacy products listed above in a single PC system must use the ATI Catalyst 9.3 or earlier driver.   All future ATI Catalyst™ releases made available past the ATI Catalyst™ 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.

---

### Post by Jackelope King on 2009-04-25
Well, that answers that. No time to do two installs today if Jaunty fails. Thanks for the help!

---

### Post by StuartN on 2009-04-25
> **LT1Caprice57L said:**
> Yep.  Graphics performance was all but pathetic in 9.04 with my Mobility Radeon 9000.

My Radeon Xpress 200M runs **glxgears** at 2,200 frames per second with the older proprietary Catalyst driver that works in Ubuntu 8.10.

Running the Ubuntu 9.04 Live CD with the "radeon" driver selected at bootup, I am getting just 320 frames per second (one seventh of the speed in 8.10).

---

### Post by ales on 2009-04-25
> **Jackelope King said:**
> Well, that answers that. No time to do two installs today if Jaunty fails. Thanks for the help!


I suggest to wait if they make a compatible driver. If not, I will stay for now with 8.10 and by the end of year will buy nVidia, have enough of weak ATI support...

Ask yourself, if you need to upgrade, what will it bring to you right  now?

---

### Post by Jackelope King on 2009-04-25
> **ales said:**
> I suggest to wait if they make a compatible driver. If not, I will stay for now with 8.10 and by the end of year will buy nVidia, have enough of weak ATI support...

Ask yourself, if you need to upgrade, what will it bring to you right  now?

Oh, absolutely. I need to get a new machine this summer anyway (my current, ancient Gateway laptop is starting to have overheating problems), so I'll make sure I get my next one with an nVidia card.

I'm in no hurry to upgrade right now (though I've heard very, very good things about Jaunty's boot times and loading times), as Intrepid has been doing a fantastic job for me so far.

---

### Post by ales on 2009-04-25
> **Jackelope King said:**
> Oh, absolutely. I need to get a new machine this summer anyway (my current, ancient Gateway laptop is starting to have overheating problems), so I'll make sure I get my next one with an nVidia card.

I'm in no hurry to upgrade right now (though I've heard very, very good things about Jaunty's boot times and loading times), as Intrepid has been doing a fantastic job for me so far.


Well, i don't see the boot time as a big bang. As I started to use Ubuntu 3 years ago, it was a real pain with my ATI, now with 8.10 all works perfectly. 9.04 is not a big step forward, it's just a upgrade with newer libraries. It could be interesting to make a poll, how many people are using the X series Radeons...
I think this is a mistake from the side of ATI...

---

### Post by nelio2k on 2009-04-25
I don't really feel like downgrading anymore. When I first got onboard the 8.10 train, I had to downgrade to 8.04 for a while. Now that I've upgraded to 9.04, I don't want to wipe my system and start anew with 8.10. 

Personally, I feel that there needs to be a list of what to expect when upgrading, instead of just a universal distribution upgrade, and leaving certain users in the dust. 

Documentation should be better on Ubuntu's side to warn users the incompatibility of the ATI's drivers, instead of letting people upgrade and finding out the hard way that it doesn't work.

For now, with my X1600 card, I'm running opensource ati driver.
Compiz seems to run fine, so does glxgears. But things like cooliris freezes my computer after a couple of seconds of usage.

Yeah, so if you want to use the open-source driver, that's the best bet for now until ATI comes out with a proprietary driver, which I don't think they will. As of now, moving onward from 9.04 and beyond, it seems that ATI will just start losing customers who uses Linux and/or don't want to shell out several hundred dollars for Windows every couple of years. Either that or the opensource driver gets better as more people spend time on it.

For those who don't know how to set it up to use opensource driver:
--------------
Open terminal

Reset your xorg.conf (Optional, if you really want to clear everything)
```
sudo dpkg-reconfigure xserver-xorg 
```

Use vim or gedit:
```
sudo gedit /etc/X11/xorg.conf
```

Look for the line
```
Section "Device"
```

Within that section, insert/edit the line with Driver so that it says:
```
Driver "ati"
```

--------------
Reboot, and things should work out better than using vesa, or in this case, incompatible ATI drivers.

This is my xorg.conf file for reference. Yours might look different, 
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "Module"
        Load    "dri"
        Load    "GLcore"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "ati"
EndSection



```

---

### Post by caravel on 2009-04-25
I reinstalled and it went pretty much without a hitch, except the resolution and refresh rate on my CRT monitor was messed up after I enabled the restricted driver.  I fixed this by going into System -> Preferences -> Display menu and setting up the correct refresh rate and resolution there.  Any changes I made in the Catalyst control center did not work - even after a reboot.  It now seems ok.

I have an HD 3650 though so for those with the unsupported X series cards or earlier it looks like the OSS driver will be the only option?

For those trying the upgrade, I'd say: Don't bother, backup your data and reinstall.  This has caused me a lot of headache so far.  Wireless has been a pain the **** as well...

**caravel considers going out and buying several metres of Cat5 backbone and some wall sockets**

---

### Post by s3lekta on 2009-04-25
Has anyone also had any success with the 3000 HD series other then a few of you on this thread?

Currently using ati mobile radeon 3400 HD.

---

### Post by Robertjm on 2009-04-25
I downloaded 9.04 while I took off to the post office today. Now it's burnt to disc, but with nothing to do. Luckily I read this thread BEFORE taking the plunge. I have an X1600 AGP card :( Been running the same mobo and processor for nearly seven years now.

Had been thinking about upgrading my computer recently. Guess it's time to do that and move over to NVidia graphics cards for a change (been an ATI family member for over 15 years!). 

Robert

---

### Post by eggplant37 on 2009-04-25
> **Jackelope King said:**
> Oh, absolutely. I need to get a new machine this summer anyway (my current, ancient Gateway laptop is starting to have overheating problems), so I'll make sure I get my next one with an nVidia card.

I'm in no hurry to upgrade right now (though I've heard very, very good things about Jaunty's boot times and loading times), as Intrepid has been doing a fantastic job for me so far.

Save yourself some money and get a can of compressed air, open that thing and blow the dust out of the fan. 

I wish I hadn't done the upgrade. I'll probably spend a good portion of my afternoon on Monday backing up, wiping, repartitioning and reloading 8.10.

Oh, and while I'm at it, I'll never buy ATI again. They can bloody rot for all I care.

---

### Post by s3lekta on 2009-04-26
> **ukoda said:**
> The is three basic things you must do.  Find the right file. Get it somewhere you can access on the affected system.  Boot to the command line as root and run it.

I have no experience with wubi so can not help directly.  The first step, finding the file, can be done with any machine.  My steps were to allow that to be the affected machine.  In your case you could find it from Windows and write the target URL, carefully, on paper.  Then boot the affected system to a command line in recovery mode, use wget and hand enter the URL you wrote down.  Then run it.  That would save all the complication of mounting partitions etc and may be the best way in your case.

thanks it all worked out, the thing now is, every so often video / system lags. compiz works fine, cairo dock takes awhile to animate/load my launchers

I just restored it back to 8.10.  I think i will just wait on 9.04... till there is a better solution

---

### Post by Pirschjaeger on 2009-04-26
> **s3lekta said:**
> Has anyone also had any success with the 3000 HD series other then a few of you on this thread?

Currently using ati mobile radeon 3400 HD.

Hi,

I have a Toshiba Satellite with the ATI 3400 HD. Jaunty seems to have been built with my laptop in mind. Compiz works fine. I have absolutely no graphics issues. It's been a very positive upgrade from 8.10.

However,....

I also have a Dell Vostro 1000 with an ATI 200m. This rig has been a PoS from the beginning. But I have to say it has worked best with 8.10 and worst with 9.04. Quite a contrast to the Toshiba. I'm giving up on installing Jaunty on the Dell for now and going back to 8.10.

I also have an EEEPC 701. I've installed the 9.04 netbook remix and plan to go with something else. The net book remix is extremely slow. The last time I saw an OS run this slow is when I installed Linux on my cell phone sd and ran a pc from it.

But on a positive point, I like 9.04 more than the others. I'm using the 'new wave' theme with a dark background. The new look is quite nice and definitely an improvement; a fresh cup-a-joe rather than the old coffee stains. :)

Don't be too discouraged though. We have to keep in mind that software and hardware quality is always being compromised by our demands. Within a month the Ubuntu gods will have worked out most of the problems.

We also have to consider the fact that the hardware manufacturers are not lining up to offer assistance to the Linux developers. But if we want to help out with the development of Linux then we should always buy from manufacturers that are supportive of the Linux communities and development.

Bill doesn't own all of them.

---

### Post by mactece on 2009-04-26
> **Muchacho_Gasolino said:**
> 
```
sudo apt-get remove xorg-driver-fglrx
```



I couldn't get 9.04 to boot after upgrade but then I followed 
I followed this advice (see post 23 above) and then reinstalled the proprietary driver and all seems to be ok now. However I haven't tried to do anything fancy yet. I'm running a gigabyte mobo with 780 chipsey and built in HD3400 graphics, btw.

Forgot to say I could boot in recovery mode and started a netroot session to do the above

---

### Post by necr0mancer on 2009-04-26
Hey guys, im new to Ubuntu. So I installed Ubuntu 9.04 Jaunty final the other day, and I have an ATI Radeon HD4870x2. I tried installing the ATI/AMD proprietary fglrx driver that was recommended by hardware drivers. When i restarted my pc, my whole ubuntu crashed. The whole screen froze up and I couldnt do anything. I had to re-install ubuntu. Does anyone know how to fix this problem and get it to work? i mean the 4870x2 quite a new gfx card so it should be supported. Any help will be appreciated!

---

### Post by eggplant37 on 2009-04-26
> **Pirschjaeger said:**
> Hi,

I have a Toshiba Satellite with the ATI 3400 HD. Jaunty seems to have been built with my laptop in mind. Compiz works fine. I have absolutely no graphics issues. It's been a very positive upgrade from 8.10.

However,....

I also have a Dell Vostro 1000 with an ATI 200m. This rig has been a PoS from the beginning. But I have to say it has worked best with 8.10 and worst with 9.04. Quite a contrast to the Toshiba. I'm giving up on installing Jaunty on the Dell for now and going back to 8.10.

I also have an EEEPC 701. I've installed the 9.04 netbook remix and plan to go with something else. The net book remix is extremely slow. The last time I saw an OS run this slow is when I installed Linux on my cell phone sd and ran a pc from it.

But on a positive point, I like 9.04 more than the others. I'm using the 'new wave' theme with a dark background. The new look is quite nice and definitely an improvement; a fresh cup-a-joe rather than the old coffee stains. :)

Don't be too discouraged though. We have to keep in mind that software and hardware quality is always being compromised by our demands. Within a month the Ubuntu gods will have worked out most of the problems.

We also have to consider the fact that the hardware manufacturers are not lining up to offer assistance to the Linux developers. But if we want to help out with the development of Linux then we should always buy from manufacturers that are supportive of the Linux communities and development.

Bill doesn't own all of them.

Yes, but didn't ATI at one time crow on and on about how supportive of Linux development they were, and offered up some kind of drivers for Linux development. Now that these cards are all supposedly obsolete, I wonder what's preventing them from releasing the specs so that proper drivers can be written for them?

ATI is off my list of vendors permanently.

---

### Post by s3lekta on 2009-04-26
> **Pirschjaeger said:**
> Hi,

I have a Toshiba Satellite with the ATI 3400 HD. Jaunty seems to have been built with my laptop in mind. Compiz works fine. I have absolutely no graphics issues. It's been a very positive upgrade from 8.10.



WOW, that's good to here.  After the reboot did you have to boot into recovery mode and install the 9.4 drivers from ati? no oher changes you had to do?

or you just did a straight update through update manager and got lucky? :)

---

### Post by GraFfiX420 on 2009-04-26
From Kano at phoronix:

You do not need to use U 9.04 or something similar But maybe just patch the id back into the fglrxko_pci_ids.h. This file is self explaining usually, you just add the id you see with

lspci -nn|grep 0300

...[1002:xxxx]

Also you should backup the /etc/ati/control file from 9-3 release to overwrite the new one. 

My reply:

Hey Kano I was wondering if you would be so kind as to shed some light on your method? This is the file locales I get with 9.3 installed.

graffix@satellite-II:/$ locate fglrxko_pci_ids.h
/usr/src/fglrx-8.593/fglrxko_pci_ids.h
/var/lib/dkms/fglrx/8.593/build/fglrxko_pci_ids.h
/var/lib/dkms/fglrx/8.593/build/2.6.x/fglrxko_pci_ids.h
graffix@satellite-II:/$

Which one do I need to edit in the pci ids to or all of them?

Then I assume I grab the control file from /etc/ati ver 9.3, then copy over my 9.4 install.

Could bridgman or anyone else on the devel team shed any light on how this would work with an x1200? It's not that big of a deal, but I would like to upgrade to juanty someday, and I don't want to have to wait for the open source drivers to catch up...

Kano's reply, thanks Kano ;)


The last 2 are just links to the first one, basically you could reuse the file from 9-3 too and replace it on the 9-4 install.

Haven't tried it yet as i'm using my toshiba a215-s4757 lappy with 8.10 and I need to backup some things first. But this should take care of the issues with no displays detected after install. I assume if you were to build your own packages, changing this info in the source it would work too.

---

### Post by eggplant37 on 2009-04-26
> **GraFfiX420 said:**
> From Kano at phoronix:

You do not need to use U 9.04 or something similar But maybe just patch the id back into the fglrxko_pci_ids.h. This file is self explaining usually, you just add the id you see with

lspci -nn|grep 0300

...[1002:xxxx]

Also you should backup the /etc/ati/control file from 9-3 release to overwrite the new one. 

My reply:

Hey Kano I was wondering if you would be so kind as to shed some light on your method? This is the file locales I get with 9.3 installed.

graffix@satellite-II:/$ locate fglrxko_pci_ids.h
/usr/src/fglrx-8.593/fglrxko_pci_ids.h
/var/lib/dkms/fglrx/8.593/build/fglrxko_pci_ids.h
/var/lib/dkms/fglrx/8.593/build/2.6.x/fglrxko_pci_ids.h
graffix@satellite-II:/$

Which one do I need to edit in the pci ids to or all of them?

Then I assume I grab the control file from /etc/ati ver 9.3, then copy over my 9.4 install.

Could bridgman or anyone else on the devel team shed any light on how this would work with an x1200? It's not that big of a deal, but I would like to upgrade to juanty someday, and I don't want to have to wait for the open source drivers to catch up...

Kano's reply, thanks Kano ;)


The last 2 are just links to the first one, basically you could reuse the file from 9-3 too and replace it on the 9-4 install.

Haven't tried it yet as i'm using my toshiba a215-s4757 lappy with 8.10 and I need to backup some things first. But this should take care of the issues with no displays detected after install. I assume if you were to build your own packages, changing this info in the source it would work too.

Once you work this out, could you share your method in detail, please?

---

### Post by peakshysteria on 2009-04-26
> **cluendo said:**
> Hey! Today I was upgrading my Ubuntu 8.10 to Ubuntu 9.04 and get a attention about my ATI fglrx driver problem...I have ATI Radeon x700pro card. I can't believe.. Is this means that my card is no longer supported by this driver ?? What should I do to fix it? Is there any way to solve this problem somehow ? Uhh... I very want to test this new release..
Thanx 4 All :)

Graphics worked out of the box for me after upgrading from 8.10 to 9.04. I got prompted that my card wasn't supported. Went ahead and jumped anyway. Working pretty smooth actually.

---

### Post by gocek on 2009-04-26
> **necr0mancer said:**
> Hey guys, im new to Ubuntu. So I installed Ubuntu 9.04 Jaunty final the other day, and I have an ATI Radeon HD4870x2. I tried installing the ATI/AMD proprietary fglrx driver that was recommended by hardware drivers. When i restarted my pc, my whole ubuntu crashed. The whole screen froze up and I couldnt do anything. I had to re-install ubuntu. Does anyone know how to fix this problem and get it to work? i mean the 4870x2 quite a new gfx card so it should be supported. Any help will be appreciated!

Well, I have HD4870 and had the same issues. Did the freeze happen after logging in? My symptoms were: ubuntu boots up, I get to type in my login, then password, then I hit enter, see black screen and then it freezes.

What I did about that was to power it down and go to sleep as it was late in the night and when I turned it on the next they it magically worked o.O Try that ;)
If you get a black screen that is, it would indicate that the driver will work for you evetnaully, just try to boot it from time to time.

You can also try this: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

This manual installation worked for me.

As a sidenote: you don't have to reinstall ubuntu if the driver won't work for you. Check this thread: [http://ubuntuforums.org/showthread.php?t=1135274](http://ubuntuforums.org/showthread.php?t=1135274)

---

### Post by roxas99999 on 2009-04-26
Well, I run a ATI Radeon x1200 card, and I'm not even sure if I should upgrade. This is the way I see it so far.

1) Many ATI Radeon cards are not supported anymore.

2) This is because of of this...."server-y" thingy is incompatible with the
current driver.

3) You can use this in the terminal to get the driver:
```

sudo apt-get remove xorg-driver-fglrx

```

Now, my question. Does it work? Will the upgrade, even
with the driver installed, be bad for performance?
Is the driver buggy? Will it work like 8.10?

---

### Post by cutterjohn on 2009-04-26
> **gocek said:**
> Well, I have HD4870 and had the same issues. Did the freeze happen after logging in? My symptoms were: ubuntu boots up, I get to type in my login, then password, then I hit enter, see black screen and then it freezes.

What I did about that was to power it down and go to sleep as it was late in the night and when I turned it on the next they it magically worked o.O Try that ;)
If you get a black screen that is, it would indicate that the driver will work for you evetnaully, just try to boot it from time to time.

You can also try this: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

This manual installation worked for me.

As a sidenote: you don't have to reinstall ubuntu if the driver won't work for you. Check this thread: [http://ubuntuforums.org/showthread.php?t=1135274](http://ubuntuforums.org/showthread.php?t=1135274)Try turning off compiz/beryl (none setting in the Visual Effects tab of Appearance).

I found that having ANYTHING on with 9.1 - .4 would cause my nb (GT725/4850) to freeze when resuming from suspend, along with a variety of other problems that seemed to be fixed in 9.3.  (Still froze after a suspend so I turned all the eyecandy off again.  Haven't bothered to try with 9.4 as I have nearly zero confidence in ATI's drivers.)

---

### Post by Vjetar on 2009-04-26
I have read all posts in topic, did some surfing on ATI site and now I'm just more confused. In upgrade proces from 8.10 to 9.04 i get notice my card isn't supported with fglrx driver. What a heck, I installed anyway. I have FireGL V3100 and tried to install "ATI FirePro Beta Software Suite Multilanguage" version 8.601 released 4/20/2009 on ATI site. . No luck. Display freezes when X started.
With 8.600 shipped with Jaunty i have had same problems.

But!

ATI documentation says My card is supported, then where is the problem.
And can someone pleas explain me 9.x nomeclatation in comparison what i found on ATI/AMD site.

---

### Post by s3lekta on 2009-04-26
i give up ... probobly my last choice is to do a full clean install & install those restricted drivers manually, which i'm not prepared to do as of yet, unfortunately installed through wubi

this is gonna be a pain in the a s s to re-install all my apps / progs

so much for a smooth upgrade transition :(

back to 8.10 again

ahh what a hassel to upgrade, but how can i complain... free OS

---

### Post by babaum on 2009-04-26
I'm running a fresh Jaunty install on my thinkpad t43p (same ATI x300), used it as my workstation since yesterday non-stop, working flawlessly. 

Also, according to the AMD/ATI driver site, the x300 chipset is now considered "legacy" and we are likely to face a lack of driver updates from now on. The current AMD/ATI driver supports X 7.4 (included in Jaunty).

---

### Post by weezerisrock on 2009-04-27
sigh, count me in as one of the ones going back to 8.10 *sob*

Open source drivers work, but the gameplay is terrible.  I'm running a laptop with a x1300 card in it.  Welcome to Legacy.  

Now as far as I can tell it there are two things that caused this problem.  The moving of a good number of cards to legacy and removing them from the driver, and the new xorg not being compatible with anything older than catalyst 9.4 correct?

I was really liking the load times too. :(

---

### Post by Seti on 2009-04-27
EPIC. FAIL.
sorry

---

### Post by Dearhell on 2009-04-27
I have [the same problem](http://ubuntuforums.org/showthread.php?t=1138302) with my Dell Laptop with an ATI x300 graphic card. 

I had to reinstall Ubuntu 8.10 also.

> The desktop it's blurry, change colors when you move the mouse pointer, the icons cannot be seen and also the background.

First I have tried updating from ubuntu 8.10 and I got this problem.

Later on, I installed from zero Ubuntu 9.04 and it happens exactly the same problem.

I have tried to change resolution (it starts with 1920x1200), but when I select another resolution, automatically ubuntu restarts session and uses the same resolution as before.

Also there are no propietary drivers to install.

---

### Post by Dearhell on 2009-04-27
> **babaum said:**
> I'm running a fresh Jaunty install on my thinkpad t43p (same ATI x300), used it as my workstation since yesterday non-stop, working flawlessly. 

Also, according to the AMD/ATI driver site, the x300 chipset is now considered "legacy" and we are likely to face a lack of driver updates from now on. The current AMD/ATI driver supports X 7.4 (included in Jaunty).

If you fix it please let me now, I have the same ATI card and the same problem.

---

### Post by Noiano on 2009-04-27
I usually do not use ati's proprietary drivers because they're more cpu hungry when playing hd videos. So I use open source drivers. After upgrading to 9.04 the attached screenshoot shows the me screwed up desktop.

In the xorg.0.log I only see just one error, the one that reports the system cannot load /usr/lib/xorg/modules/extensions//libglx.so.

Any ideas?:confused:

---

### Post by Pirschjaeger on 2009-04-27
> **s3lekta said:**
> WOW, that's good to here.  After the reboot did you have to boot into recovery mode and install the 9.4 drivers from ati? no oher changes you had to do?

or you just did a straight update through update manager and got lucky? :)

Since having written what I did I have had two problems. Don't bother trying to play avi movies when in full graphics mode. My Toshiba froze up solid. I reduced my graphics mode to normal and it worked perfectly.

I also install the ati driver from their site. It's done through terminal but not too difficult.

Interesting thing: the Toshiba Satellite came with Vista. After a couple hours with Vista I decided to ditch it and throw XP on the drive. XP wouldn't load and neither would Linux. As always, Google was my friend and told me how to change a BIOS setting meant to block all but Vista. Anyway, just before installing 9.04 I had reset my BIOS to default settings. I totally forgot about the ACHI (?) and 'compatibility' setting. After installing 9.04 I found I couldn't burn a CD. I thought about it a while and remembered the BIOS setting. I reset to 'compatibility' then updated in synaptic. After that, I could burn CDs. Just something to keep in mind.

So far, everything else works fine.

---

### Post by maxclimber1w on 2009-04-27
Ok, my display was broken after upgrade. It would run the bootloader, then come up with a scrambled screen.

I run an ATI HD 2400.

I booted into safe mode, into a terminal, and removed all the ati drivers with:

```
envyng -t
```

then following the instructions.
(apt-get remove fglrx* might do the trick if you have no envyng installed.)

Then I ran ```
apt-get install fglrx
```
and then ```
aticonfig --initial -f
```

worked great! Running with full effects again. Good luck.

---

### Post by Vjetar on 2009-04-27
Please be more specific what you did, becouse ```
sudo apt-get install fglrx
``` reported "E: Couldn't find package fglrx"

---

### Post by Muchacho_Gasolino on 2009-04-27
> **babaum said:**
> I'm running a fresh Jaunty install on my thinkpad t43p (same ATI x300), used it as my workstation since yesterday non-stop, working flawlessly. 

Also, according to the AMD/ATI driver site, the x300 chipset is now considered "legacy" and we are likely to face a lack of driver updates from now on. The current AMD/ATI driver supports X 7.4 (included in Jaunty).

Are you using the fglrx driver? I'm on a thinkpad t43, also with an x300, and the fglrx driver did not work for me, at least at intitial upgrade.

Vjetar, ```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by Vjetar on 2009-04-27
> **Muchacho_Gasolino said:**
> 

Vjetar, ```
sudo apt-get install xorg-driver-fglrx
```

Tnx, i founded packet myself, but still no luck. 
```
aticonfig --initial -f
```
reported "aticonfig: No supported adapters detected"

lspci|grep ATI :
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)] (rev 80)
01:00.1 Display controller: ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)] (Secondary) (rev 80)

---

### Post by bluelamp999 on 2009-04-27
Hi friends,

I'm running 8.10 on a Dell Latitude D810 with an ATI Mobility Radeon X300.

I have a multi-display 'Big Desktop' setup using the ATI proprietary driver and running the Catalyst Control Centre 9.3 (desktop area = 3840 x 1200).

I don't run Compiz (as it won't run on the above resolution) but I do have Metacity compositing turned on for Google Earth etc.

So, am I to be forever stuck with 8.10?

What about the open-source drivers? 

Would they allow the above setup with comparable performance?

Cheers...

---

### Post by hockman5 on 2009-04-27
> **ukoda said:**
> Same story as most here but now it's looking great and features that didn't work before now work.  After doing the upgrade I was left a scrambled screen when it was to switch to hire mode.  The general step I took to fix it were:
1. Booted from a Ubuntu Gutsy USB key. Other versions and CD should be fine too.
2. Opened a terminal and used "sudo su" to become root.
3. Mounted my hard drive.  In my case "mkdir /mnt/sda5" then "mount -t ext3 /dev/sda5 /mnt/sda5".  Use "fdisk -l" to find the right place.
4. Downloaded the latest diver using wget after finding the right URL from the ATI website.  Look at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) for my HD 3200 card I needed "wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-4-x86.x86_64.run"
5. After it download rebooted and selected recovery option at boot menu.
6. Selected the "NETROOT" option.
7. Ran the downloaded "sh ./downloadedfile".
8. Went with default options.
9. Rebooted and all was good in the world!

NB: Your mileage may vary.
I tried this unsuccessfully. I have a 2400HD pro card. The error file says"
KErnel Module: failed to build fglrx-8.602 with DKMS
Kernel Module: Removing fglrx-8.602 from DKMS

What does all this mean??? Will I ever be able to boot up 9.04 with my ATI Radeon card?

---

### Post by aditirex on 2009-04-27
I'm having a Elitebook 8530p with an ATI 3650HD . After upgrading to Jaunty  I got the blank screen . After some tryouts I runned in recovery mode :
```
aticonfig --acpi-services off 
```
Not sure what this option disables because it seems the battery is not eaten by the graphic card as in the case of using the open source drivers .
Hope this helps someone :)

---

### Post by kc600 on 2009-04-27
> **maxclimber1w said:**
> 
I booted into safe mode, into a terminal, and removed all the ati drivers with:

```
envyng -t
```

then following the instructions.

This worked for me (ATI Radeon HD 2350). I didn't have to do other stuff, just removing ATI stuff worked got me my login screen back.  

By the way, envyng is in the envyng-core package.

Thanks!

---

### Post by DJJo on 2009-04-27
i also did a upgrade from 8.10 to 9.04. because i had problems with my ati drives. and nou ik can do dual screen with my open GL. but visual effects wil not work. but i am stil happy about theat.

---

### Post by SpetsnazC4 on 2009-04-27
I have a T41 Thinkpad with a Radeon Mobility 7500. I did an install of 9.04 from scratch. I had done upgrades of the past several releases with no problems but I figured it was time to clear out the cobwebs. The install of 9.04 went fine. After turning off compiz the display seemed to work as well as with 8.10.

Today I booted my laptop up and had a lovely display of garbled lines. I tried the recovery mode graphics fix but no luck. I booted with the livecd and quickly found this nice thread. "sudo apt-get remove xorg-driver-fglrx" to the rescue! Thanks for posting that gem. Things seem to be ok now. I won't miss any of the nice compositing eyecandy as this machine was to weak to run them before.

I am definitely going to stick with nvidia when I replace this machine.

---

### Post by ales on 2009-04-28
> **SpetsnazC4 said:**
> I have a T41 Thinkpad with a Radeon Mobility 7500. I did an install of 9.04 from scratch. I had done upgrades of the past several releases with no problems but I figured it was time to clear out the cobwebs. The install of 9.04 went fine. After turning off compiz the display seemed to work as well as with 8.10.

Today I booted my laptop up and had a lovely display of garbled lines. I tried the recovery mode graphics fix but no luck. I booted with the livecd and quickly found this nice thread. "sudo apt-get remove xorg-driver-fglrx" to the rescue! Thanks for posting that gem. Things seem to be ok now. I won't miss any of the nice compositing eyecandy as this machine was to weak to run them before.

I am definitely going to stick with nvidia when I replace this machine.

Same here. If you loose support under windows u can still use your HW with previous driver, but here you can't, what kind of logic is this.

---

### Post by Scooby1 on 2009-04-28
Just a note in case anyone here was having the same problems as I was,

Have an x850, using radeon driver, everything wonderful in 8.04, full 3D, compiz effects smooth. Fresh install of jaunty, x-server constantly crashes, compiz effects were slow. Fast forward a day, I read that jaunty now uses EXA Acceleration by default (8.04 used XAA). Added this line under devices in xorg.config to force XAA acceleration:

Option "AccelMethod" "XAA"

and now everything seems to work seamlessly...

---

### Post by babaum on 2009-04-28
For those asking if I'm using fglrx, I'm not. It doesn't work, and it will break Jaunty if you force install. I think a couple of days ago, they (AMD/ATI) locked the driver install for Jaunty to avoid that - if you try to install now, all you get is a "distro not compatible" type of message.

I think this is a pretty serious problem, given the nature of the Ubuntu distro. I was getting used to wait for the next version and upgrading Ubuntu just to upgrade all supported software within it - take Mono Develop, for example. It's almost impossible to build it in Intrepid without creating a monster by installing all the requirements. So, I can't use my favorite IDE unless I use Jaunty. :(

I know I'll get flamed for this, but I think the decision of upgrading X and letting all of us (most ATI owners) in the dark was impressively against the original Ubuntu philosophy. C'mon, blaming ATI because they won't be updating their drivers forever to get along with every new X version? The least I could say about this is "childish". 

I'm a fan and user of Ubuntu since the beginning, but now I just want to keep using my favorite distro with the latest Gnome version and the latest apps I really like and got brand new versions recently. And I can't, because I didn't dropped a lot of cash for my T43p with a nice 3d accel video card to get a "good enough" open driver. Besides, I love to play Neverwinter Nights during lunchbreak. What a shame. :frown:

---

### Post by krisvek on 2009-04-28
It's not the Ubuntu devs fault.  If they had stuck with a Xorg server version older than 1.6, people would be complaining about their inability to keep up with the newest developments in software, they'd be behind in the current tech, and compatibility issues with OTHER software would appear.

The blame is on AMD, solely.  AMD has been doing poorly with their proprietary linux driver support, and this is just the latest example.  The two issues are, support for Xorg server 1.6, and support for 'older' cards.  AMD finally released a driver that supported Xorg server 1.6, but for some inane reason, decided that they would stop support for many, many 'older' cards on the very same release, thus leaving many people without any other option than to either stay with the older versions, or to upgrade with the open source driver.

It does not appear as if this standing will be changed any time soon, at least, not by AMD.  The only real alternatives I see are for the open source drivers to improve greatly and thus become a satisfying option (and they're definitely working on it, but it takes time, which takes patience, which of course, sucks), or for someone somewhere to figure out some hack that allows the older fglrx drivers to be compatible with Xorg server 1.6.  It would seem that this will not be easy, or else AMD would have done it themselves.

---

### Post by babaum on 2009-04-28
> **krisvek said:**
> It's not the Ubuntu devs fault.  If they had stuck with a Xorg server version older than 1.6, people would be complaining about their inability to keep up with the newest developments in software, they'd be behind in the current tech, and compatibility issues with OTHER software would appear.

Indeed. I agree with your point of view too. And it doesn't change the fact that by blaming AMD, you are asking for the hardware to work with your software, and this will never be right. Just think about Windows and it's insanely larger number of users... imagine what would happen if Microsoft releases a new "explorer.exe" (or theme engine, or whatever) with a release note: sorry folks, this won't work with nvidia forceware drivers. Nvidia should modify its driver to work with our new shell. Bad, bad driver!

Now look how ridiculous this blaming of AMD/ATI is.

---

### Post by StuartN on 2009-04-28
> **babaum said:**
> Now look how ridiculous this blaming of AMD/ATI is.

I agree, blaming anyone but the user-base is pointless - we put ourselves in this position by deciding to install a closed-source driver. It is a great argument against using any proprietary drivers, and for not buying any hardware that relies on closed source. In that respect Ubuntu has made a great job (for the vast majority of ATI hardware) of detecting cards and installing working drivers, even if they do deliver a poorer performance than the proprietary driver they replace.

Anyone who has not yet upgraded should be warned to test their system performance with a Live CD before making the switch.

And repeating this link for anyone in 9.04 who needs to remove traces of the proprietary driver so that the open source one functions correctly: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by emenblade on 2009-04-28
Hi there im new to the forums, i realize there probably anything any one can do as of yet, how ever i figure this is the place to share my problem so that when a solution is found i will be already at the right spot. =D

when I installed Ubuntu 9.04 last night i decided to immediately install my proprietary driver, because after a few months with puppy Linux i was eager to enjoy some enhanced Linux graphics. i do not have old hardware.
my graphics card: Ati radion 3650
i downloaded the drivers from the manufacturers website, and once i restarted my system i was greeted with only a black screen. my crt monitor handles resolutions of up to 1280X1024, and it cant play what every is being sent to it. Sadly i think i will use the older version of Ubuntu until ati updates their Linux drivers =D.

---

### Post by babaum on 2009-04-28
Are you saying that your video card refuses to work with the brand, shiny new X version? Oh, sorry. Shame on it. 

Sorry, I just couldn't resist to drop a line of sarcasm. 

I'm switching to openSuse now, friends. They even have a brand new Gnome 2.26 package, for the "rather old" version 11.1.

---

### Post by babaum on 2009-04-28
Are you saying that your video card refuses to work with the brand, shiny new X version? Oh, sorry. Shame on it. 

Sorry, I just couldn't resist to drop a line of sarcasm. 

I'm switching to openSuse now, friends. They even have a brand new Gnome 2.26 package, for the "rather old" version 11.1.

---

### Post by pgdave on 2009-04-28
This worked for me with a ATI HD2600 card:

Go to recovery mode,and to root prompt:

apt-get remove fglrx*
apt-get install xorg-driver-fglrx
aticonfig --initial -f

Then reboot.

---

### Post by defaria on 2009-04-28
> **ales said:**
> The following products have been moved to the legacy software support structure (**including Mobile** and All-in-Wonder Variants):

ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
**ATI Radeon X700 Series**
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series


AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

Any customers using a combination of a ATI Radeon™ HD 2000 Series, ATI Radeon™ HD 3000 Series, or ATI Radeon™ HD 4000 Series product with any of the legacy products listed above in a single PC system must use the ATI Catalyst 9.3 or earlier driver.

I'm confused. Let me state that I have an ATI Radeon HD 3200 in my desktop (not laptop). I assume that falls in the ATI Radeon HD 3000 Series. How exactly does one use a combination of an ATI Radeon HD 3000 Series like my 3200 **in combination with** one of the above listed series? Isn't either one card or the other? :confused:

So far my 3200 doesn't work with Ubuntu 9.04, even with the supposedly working 9.4 Catalyst drivers. I've had black screens, white screens, messed up screens, window manager aborts, failure to recognize a dual monitor set up, etc.

Is my ATI Radeon HD 3200 supposed to be supported or not on Unbuntu 9.04? If so how do I get the correct driver so I can run dual monitor and also do 3d stuff and Compiz?

---

### Post by defaria on 2009-04-28
> **krisvek said:**
> It does not appear as if this standing will be changed any time soon, at least, not by AMD.  The only real alternatives I see are for the open source drivers to improve greatly and thus become a satisfying option (and they're definitely working on it, but it takes time, which takes patience, which of course, sucks), or for someone somewhere to figure out some hack that allows the older fglrx drivers to be compatible with Xorg server 1.6.  It would seem that this will not be easy, or else AMD would have done it themselves.

How about the alternative of giving up on ATI and buying and nvida card? I'm seriously considering it to side step these issues. The problem is there are also nvida issues too right? Can people step up here and list what sort of nvida card you have, whether it's working with 9.04, whether it does the 3d, composting stuff and whether or not it handles multiple monitors. Thinking about all of the time I've wasted trying to resolve this issue when I could say drop $70 on a card, install it and be done with the problems....

---

### Post by emarkay on 2009-04-28
NINE pages here - no Launchpad notes - and this is my fifth post on this forum regarding this.

WHAT DO I DO TO GET MY ONCE FINE 8.10 SYSTEM RUNNING AS FINE WITH MY ATI/AMD Radeon HD2600 HT  "VEN_1002 - DEV 9580": @ 1360 x 768 with 512M of VRAM?

THANK YOU!

---

### Post by defaria on 2009-04-28
My guess? You install another fine video card! That's what you do!

---

### Post by s3lekta on 2009-04-28
> **pgdave said:**
> This worked for me with a ATI HD2600 card:

Go to recovery mode,and to root prompt:

apt-get remove fglrx*
apt-get install xorg-driver-fglrx
aticonfig --initial -f

Then reboot.

thats good to hear, how did you install fresh or upgrade? is everything else working?

---

### Post by s3lekta on 2009-04-28
> **emenblade said:**
> Sadly i think i will use the older version of Ubuntu until ati updates their Linux drivers =D.

got the face all wrong =( .... not to many happy users on this thread

---

### Post by emarkay on 2009-04-28
> **defaria said:**
> My guess? You install another fine video card! That's what you do!

Thanks for a stupid and pointless reply.

---

### Post by emarkay on 2009-04-28
> **s3lekta said:**
> thats good to hear, how did you install fresh or upgrade? is everything else working?

Did not work for me.

---

### Post by defaria on 2009-04-29
> **emarkay said:**
> Thanks for a stupid and pointless reply.

It's only stupid and pointless for those of you who lack vision. What is says to anybody paying attention is "Currently there is no way" - which is a response that imparts a message does it not? By contrast **your** response imparts nothing of meaning. Now take you negativity elsewhere...

---

### Post by PsyWolf on 2009-04-29
I just wanted to mention that i did a fresh install with a Radeon 1600 series card and actually am getting much smoother compiz effects.  I haven't tried game performance though, and the open source drivers currently break the boxee interface.

---

### Post by nengracia on 2009-04-29
Didn't upgrade Intrepid to Jaunty 'coz I saw this post (I have ATI X1650).

What I did was create a new installation of Jaunty. Guess what, everything's working fine. In fact, I think Jaunty fully supports ATI (my model, at least). Though it ain't visible to me yet, all 3d effects are working fine. When I look thru "hardware drivers", my video card isn't listed so I think it's supported.

Also, DVD video playback has further improved (no more flickers), even my TV is working perfect using TVTime. All in all, Jaunty is a far improvement of Intrepid and I'm very satisfied.

Thanks all to the Ubuntu Community! Keep up the good work!

---

### Post by Genera1Mayhem on 2009-04-29
Did an upgrade from 8.10 to 9.04 on this Thinkpad R50, and compiz was fine before the upgrayeddd but now runs like CRAP.  ATI Radeon Mobility 7500 or something similar here..

Why does Ubuntu have to be so damn slow?  I'm starting to think about trying Gentoo again..

---

### Post by Vjetar on 2009-04-29
> **Scooby1 said:**
> Just a note in case anyone here was having the same problems as I was,

Have an x850, using radeon driver, everything wonderful in 8.04, full 3D, compiz effects smooth. Fresh install of jaunty, x-server constantly crashes, compiz effects were slow. Fast forward a day, I read that jaunty now uses EXA Acceleration by default (8.04 used XAA). Added this line under devices in xorg.config to force XAA acceleration:

Option "AccelMethod" "XAA"

and now everything seems to work seamlessly...

Didn't work for me. I have FireGL V3100 with ati driver, fglrx crashes system. If I using compiz and efects, ewerything is painfuly slow.

---

### Post by StuartN on 2009-04-29
> **defaria said:**
> How exactly does one use a combination of an ATI Radeon HD 3000 Series like my 3200 **in combination with** one of the above listed series? Isn't either one card or the other? :confused:

Some people install more than one video card to drive multiple displays. The performance will then be the performance of the weakest card.

> **defaria said:**
> So far my 3200 doesn't work with Ubuntu 9.04, even with the supposedly working 9.4 Catalyst drivers. I've had black screens, white screens, messed up screens, window manager aborts, failure to recognize a dual monitor set up, etc.

An ATI Radeon HD3200 is fully supported by Catalyst 9.4 according to [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

If you upgraded rather than installed then try this [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by eggplant37 on 2009-04-29
> **defaria said:**
> My guess? You install another fine video card! That's what you do!

So, what does one do if they have a laptop, bright boy?

I'm not tossing aside a perfectly good laptop that was doing fine in 8.10 and now refuses to work because of some astoundingly stupid decisions made by both Ubuntu devs and ATI. I simply don't have the $$ to dump on a brand new laptop every 3 years when crap like this happens.

Support my gear, that's all I'm asking.

---

### Post by emarkay on 2009-04-29
> **defaria said:**
> It's only stupid and pointless for those of you who lack vision. What is says to anybody paying attention is "Currently there is no way" - which is a response that imparts a message does it not? By contrast **your** response imparts nothing of meaning. Now take you negativity elsewhere...

If they were a real assistant here they would have said what you said, not some smarmy comment - and it's negative to me because I had a perfectly good system, that by upgrading is now useless.  

Now for the issue - once and for all - and I will state that I have upgraded to the ATI/AMD driver and it still does not function.

1. What has changed
2. Is there a bug report?
3. Is there a workaround.
4. Are there any tests I can do?

And, no I am not going to replace the graphics card.

Signed
MRK

---

### Post by defaria on 2009-04-29
> **eggplant37 said:**
> So, what does one do if they have a laptop, bright boy?

My statement still stands in that it says there is nothing you can do about it with that video card at this time. I don't know what people do with laptops. I don't own one. And it occurs to me that you purchased one regardless of the fact that you knew you can't easily replace or stuff in a different video card.

> I'm not tossing aside a perfectly good laptop that was doing fine in 8.10 and now refuses to work because of some astoundingly stupid decisions made by both Ubuntu devs and ATI. I simply don't have the $$ to dump on a brand new laptop every 3 years when crap like this happens.

I really don't think the Ubuntu devs or the ATI devs got together or decided separately "Gee if we put this and this together then everybody will be screwed!". In fact, I suspect they'd be very happy if this were **not** the case. It's just that getting it done requires effort and time.

> Support my gear, that's all I'm asking.

Sorry it's not my job to support your gear! But I tell ya what... There's nothing stopping you from taking the open source torch, getting the open source drivers and modifying them to the point where it works perfectly. What you say? That's a lot of work and would take time? Ah, so perhaps now you are seeing the problem a bit better.

Look I agree, for those of us who have these unsupported cards it looks foolish that Ubuntu decided to go ahead and use the latest X server and it looks foolish that ATI didn't have the driver ready in time. Perhaps Ubuntu thought the drivers would be ready or ATI thought that not that many people have these specific cards. I feel quite confident that everybody involved not only wished the situation would be different but that it would be at least resolved by release time or shortly thereafter. Hey I'm pissed it doesn't work for me either. But you must learn to deal with reality and the reality it, at this time, you just can't get there from here. Learn to deal with it and/or look for alternate solution. I'm sorry you picked an inflexible hardware platform...

---

### Post by defaria on 2009-04-29
> **emarkay said:**
> If they were a real assistant here they would have said what you said, not some smarmy comment - and it's negative to me because I had a perfectly good system, that by upgrading is now useless.  

[What is this becoming, the "Twitter" generation?]

I don't know. I'm not part of the twitter generation myself.

---

### Post by fmfrisch on 2009-04-29
I'm following this thread carefully to find any solutions to my problems with fglrx. Seems like this thread  is moving away from its topic. Can we get back to the real problem and away from personal disputes. 

Is there a bug report? I'm having problems with a Radeon HD3650. All Desktop Effects related. Any one in the same position? Maximize/Minimize + resizing windows is slow. More than normal CPU. Again someone recognizing these problems and most important does someone know something??

---

### Post by emarkay on 2009-04-29
I have followed the instructions here:

[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/285603](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/285603)

I also see that there MIGHT be a related issue with the new EXT4 fielsystem - but I don't see a real connection.  I did change to EXT4. on all machines - so far my NVIDIA machine  (this one) is fine.

What I am getting (on the other machine) as a fault is no panels, and apparently the screen size is larger than the monitor - BUT - rearranging the icons keeps tehm to the screen size displayed.  strange.

It is a Radeon HD2600XT AGP card, on a HDTV using HDMI, at 1360 x 768 with 512Meg VRAM.

---

### Post by Scrim on 2009-04-29
I have installed 9.04 as the first Linux distro on my main pc (Im fairly new to linux) I run a HD2600XT PRO AGP

After a few reinstalls (because i hadnt mastered the recovery mode) due to blank screens and crashing (a clever windows system that alerts you that somethings not working properly for those not acustomed to windows) After fidling with things im not 100% about, I had a decent single monitor working. I then installed ATI 9.4 drivers from the [ati website]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English") this then allowed me somehow to untick the mirror screens in Display and now I have a desktop stretched across 2 screens.

However I (a[nd a few others]("http://ubuntuforums.org/showthread.php?t=1135612&page=2")) am unable to use the xinerama feature unless I disable xrandr (which should replace xinerama if Im correct?) Once disabled I can use catalyst control centre to get
2 desktops in a crazy useless resolution
a cursor on both screens that work independantly
If i change the resolution it goes caput.

It's a shame as I was so impressed with my toshiba portege M200 which does as it says on the tin "Just works"

Hopefully we'll get some solutions soon?!

---

### Post by emarkay on 2009-04-29
Any other ideas or suggestions to try - I don't want to have to go BACK to the older Ubuntu!

What about the Phoronix variants? 
[http://www.radeonhd.org/](http://www.radeonhd.org/)

It indicates here it should work, too:
[http://www.linux-magazine.com/online/news/proprietary_driver_for_ubuntu_9_04_fglrx_for_x_server_1_6](http://www.linux-magazine.com/online/news/proprietary_driver_for_ubuntu_9_04_fglrx_for_x_server_1_6)

Here's some updated "X" drivers - but I am not sure how to test to see if tese work
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by dulbirakan on 2009-04-29
I am using Radeon 4850 with proprietary drivers from ubuntu. It takes longer to boot (10, 15 seconds), has compositing issues, quirks in effects, the video playback is awful and all those stuff... But worst of  all it does not resume from suspend.

Did any one else noticed the suspend problem or is it just me?

Btw. My GF has Radeon X1600Pro and she is totally fine with the open source drivers that came along with ubuntu. Even has the desktop effects turned on. Lucky her I guess, the card falls to a sweet spot where the open source drivers provide 3D support...

---

### Post by theducks on 2009-04-29
Radeon 9550, Upgraded from 8.10 3 tries and locks up with funny colored Ubunttu's 
boots from Live CD. Did a fresh install, OK 
then I did the updates and added the control fglrx-amdcccle
Bad Move :/
tried apt-get remove fglrx-amdcccle which ran, but no joy.

First the Intel problem on my Toshiba laptop, now this.. Graphics card support is NOT ready for primetime :/

---

### Post by deboh on 2009-04-29
[B]''No valid Mirror found
    While scanning your repository no mirror entry for the update information was found. This can happen if you run a internal mirror or if the mirror information is out of date.
    Do you want to rewrite 'sources.list file' anyway? If you choose 'yes' it will update all 'intrepid' to 'jaunty' entries. If you select 'no' the update will cancel.[/B]
   
 
the above was what i got while trying to upgrade from 8.10 to 9.04 via a mirror deb upgrade as provided for me from my community linux based internet provided using the friefunk software in order for me to have a faster upgrade, and so i clicked ''YES'' and restarted my update manager, everything seem to go on fine but eventually when i expected things to work out i got a sort of system check and realized that my graphics card was being tampered with, long story short, i do not know if i have successfully upgraded because my graphics quality has been reverted to default and now i see nothing when ubuntu starts up except the orange-brown background that comes up after the splash screen, i dual booth xp and ubuntu and the graphics card seem to be fine when i boothed into Xp but it wont show me a thing wheni booth into ubuntu. i have no idea what this is or what i should do. i need help. i use an Nvidia geforce 7100gs.

---

### Post by dulbirakan on 2009-04-29
> **babaum said:**
> Indeed. I agree with your point of view too. And it doesn't change the fact that by blaming AMD, you are asking for the hardware to work with your software, and this will never be right. Just think about Windows and it's insanely larger number of users... imagine what would happen if Microsoft releases a new "explorer.exe" (or theme engine, or whatever) with a release note: sorry folks, this won't work with nvidia forceware drivers. Nvidia should modify its driver to work with our new shell. Bad, bad driver!

Now look how ridiculous this blaming of AMD/ATI is.

Well I see you have a serious misconception here. Yes, we want our hardware to work with our software. That is true. But no one expects AMD, ATI engineers knocking our doors to solder new transistors or capacitors to our existing cards. 

The drivers are like a layer between SW and HW and we just want a more compatible layer there. It is the duty of HW manufacturers to provide compatible drivers for operating systems. If AMD/ATI stated that they did not support Linux, It would be ridiculous to demand drivers. Yet they provide this crappy piece of code, we call proprietary drivers hence they are responsible to provide fixes until it works...

Also, microshaft releases new versions of explorer and theme engines with every new release of windooze and even with that HUGE user base microshaft faces driver issues. Or have you totally forgotten the first six months of vista?

---

### Post by quackeroni_pizza on 2009-04-29
I can confirm similar behavior on an HD3650.. sluggish compiz desktop effects with the proprietary Catalyst driver. I tried switching to the radeonhd drivers and got better dekstop performance..... but sadly they have terrible power management. 

My computer ran at ~55 C + fan operated at full blast + power consumption was 44W with the radeon drivers. Radeon did deliver substantially improved desktop performance.

The same system ran at ~45 C + fan was noiseless + power consumption was ~22W with the Catalyst driver. And the Catalyst driver resulted in an extremeley sluggish UI.

I love choices :)

---

### Post by babaum on 2009-04-29
> **dulbirakan said:**
> Well I see you have a serious misconception here. Yes, we want our hardware to work with our software. That is true. But no one expects AMD, ATI engineers knocking our doors to solder new transistors or capacitors to our existing cards. 

The drivers are like a layer between SW and HW and we just want a more compatible layer there. It is the duty of HW manufacturers to provide compatible drivers for operating systems. If AMD/ATI stated that they did not support Linux, It would be ridiculous to demand drivers. Yet they provide this crappy piece of code, we call proprietary drivers hence they are responsible to provide fixes until it works...

Also, microshaft releases new versions of explorer and theme engines with every new release of windooze and even with that HUGE user base microshaft faces driver issues. Or have you totally forgotten the first six months of vista?

Sorry buddy, but for an engineer's (like those guys at AMD) mind, there's no misconception, only facts. The first fact is that the driver works perfectly - it runs Neverwinter Nights in my T43p way faster than the Windows driver, for an example. So, I can't avoid to think like them (with logic and reason first): so, you modified your little software, that thing called "X", and you want me to go after that BUG in MY driver because, imagine, now it won't work with "LINUX"????

Facts, buddy: the driver works perfectly for LINUX, but X is broken. For all you guys considering nvidia, another workstation stopped today in my company because of the driver versus the new X conflict (will post details about it tomorrow).

---

### Post by emarkay on 2009-04-29
I guess I need to file a Launchpad bug...

[https://bugs.launchpad.net/ubuntu/+bug/369621](https://bugs.launchpad.net/ubuntu/+bug/369621)

---

### Post by cleopete on 2009-04-29
> **babaum said:**
> Sorry buddy, but for an engineer's (like those guys at AMD) mind, there's no misconception, only facts. The first fact is that the driver works perfectly - it runs Neverwinter Nights in my T43p way faster than the Windows driver, for an example. So, I can't avoid to think like them (with logic and reason first): so, you modified your little software, that thing called "X", and you want me to go after that BUG in MY driver because, imagine, now it won't work with "LINUX"????

I've known a few engineers, and they aren't anymore married to a fact-based existence than the rest of the general knuckle-head population.  The fact is AMD has had weak driver support for ATI since the day they bought their red-headed step child.

I'd been a Radeon fanboy since my first 7200, but last summer, I finally inhaled deep and bought an Nvidia 8800 GS, and I only wish I'd done it sooner.  Their driver support is far superior to AMD- whether it's Linux or that other OS whose name escapes me at the moment.

That doesn't help with my Xpress 1100-based laptop.  At less than two years old I expect better than "legacy" support.  If they don't want to make a decent driver, than they could at least let the kids living in their parents' basements do it, they have the time.

I've always come down solidly on the AMD side of the Intel vs. AMD argument (the geekish version of the Ford v. Chevy debate).  Now that I've ditched Radeon, it may be time to lose AMD too.

BTW: Neverwinter Nights was lame, You might just as well say it runs Spider Solitaire WAY better than Windows, so what?

---

### Post by Renan Decarlo on 2009-04-29
> **cleopete said:**
> I've known a few engineers, and they aren't anymore married to a fact-based existence than the rest of the general knuckle-head population.  The fact is AMD has had weak driver support for ATI since the day they bought their red-headed step child.

I'd been a Radeon fanboy since my first 7200, but last summer, I finally inhaled deep and bought an Nvidia 8800 GS, and I only wish I'd done it sooner.  Their driver support is far superior to AMD- whether it's Linux or that other OS whose name escapes me at the moment.

That doesn't help with my Xpress 1100-based laptop.  At less than two years old I expect better than "legacy" support.  If they don't want to make a decent driver, than they could at least let the kids living in their parents' basements do it, they have the time.

I've always come down solidly on the AMD side of the Intel vs. AMD argument (the geekish version of the Ford v. Chevy debate).  Now that I've ditched Radeon, it may be time to lose AMD too.

BTW: Neverwinter Nights was lame, You might just as well say it runs Spider Solitaire WAY better than Windows, so what?

Totally, totally agreed. I've got a ATI X300 and it's all f*cked up now -.-'. So, the ATI users can't use the newer versions of Linux, that's it? So it's time to go on Intel and Nvidia.

---

### Post by alfredska on 2009-04-30
> **Renan Decarlo said:**
> Totally, totally agreed. I've got a ATI X300 and it's all f*cked up now -.-'. So, the ATI users can't use the newer versions of Linux, that's it? So it's time to go on Intel and Nvidia.

These posts reveal some seriously spoiled individuals.  Patience!  Launchpad bugs have been created ([285603]("https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/285603") along with its 3 marked duplicates, [369621]("https://bugs.launchpad.net/ubuntu/+bug/369621"), and surely others).  Jaunty hasn't even been out for a week yet, not to mention developers now have to adhere to [Stable Release Update rules]("https://wiki.ubuntu.com/StableReleaseUpdates"), which restricts their ability to address this issue as quickly as you'd like.  Quality assurance is important to the Linux community, so again, have patience.  This problem WILL BE ADDRESSED.

---

### Post by brons2 on 2009-04-30
I have a 4850 and mine was broken after the upgrade too.  Had to boot to a terminal prompt and do the 'sudo apt-get remove xorg-driver-fglrx' thing.  After that I was able to boot.

I'm going to try the new proprietary driver right now, holding my breath...

---

### Post by Guilden_NL on 2009-04-30
> **eggplant37 said:**
> Yes, but didn't ATI at one time crow on and on about how supportive of Linux development they were, and offered up some kind of drivers for Linux development. Now that these cards are all supposedly obsolete, I wonder what's preventing them from releasing the specs so that proper drivers can be written for them?

ATI is off my list of vendors permanently.

Yes, you are very correct.  And what burns me is that AMD bought ATI, and AMD was touting themselves as a Linux supporter.  I've written off AMD as my CPU supplier from here on out unless they get some Linux religion fast.

AMD is acting like they are run by either of the two Evil Steve's: Jobs and Ballmer. [-(

---

### Post by brons2 on 2009-04-30
> **Guilden_NL said:**
> Yes, you are very correct.  And what burns me is that AMD bought ATI, and AMD was touting themselves as a Linux supporter.  I've written off AMD as my CPU supplier from here on out unless they get some Linux religion fast.

AMD is acting like they are run by either of the two Evil Steve's: Jobs and Ballmer.

agree.  The 4850 is my very first ATI card and while I love the card, the software support sucks compared to nVidia - in both Linux and Windows.  First thing I had to do when I got the card out of the box and installed it on XP was to write a custom .inf file to get the fan to go fast enough, it was running 70c at idle, out of the box.  I finally just gave up and went to an aftermarket cooling setup on the card and now it runs like it should, idle in the 30s and full load in the 50s.

Now this issue comes up, just another nail in the coffin.  Next card will be a GTXxxx something or another.

---

### Post by Guilden_NL on 2009-04-30
> **babaum said:**
> Sorry buddy, but for an engineer's (like those guys at AMD) mind, there's no misconception, only facts. The first fact is that the driver works perfectly - it runs Neverwinter Nights in my T43p way faster than the Windows driver, for an example. So, I can't avoid to think like them (with logic and reason first): so, you modified your little software, that thing called "X", and you want me to go after that BUG in MY driver because, imagine, now it won't work with "LINUX"????

Facts, buddy: the driver works perfectly for LINUX, but X is broken. For all you guys considering nvidia, another workstation stopped today in my company because of the driver versus the new X conflict (will post details about it tomorrow).

Well this engineer (and Enterprise Architect) disagrees with you.  Yes the X server has been updated and improved.  If you look at the history of it, it's a generational change and not something they sneaked in at the last moment.  Let's use the Windows analogy since you brought them up.  If AMD/ATI decided to ignore developing drivers for Windows Vista or Windows 7, it's their choice, but they do so at their own risk.  Sure Linux is only ~25% of the global OS market, but both AMD _**and**_ ATI have touted themselves as Linux supporters, trying to sell more of their product to the folks that run Linux.  Now they are abandoning a huge portion of their existing customer base with many of those now "legacy" products being less than two years old. (As is the case with the ATI express 1100 in my son's laptop.)  

I happen to work for one of the largest computer mfgrs in the world who has a very large internal Linux community.  The internal Linux community discussions are quite heated and anti-AMD and ATI as a result of their decision.  I certainly don't make our vendor/partner decisions, but some of the people that do are ardent Linux fans.  It's AMD's and ATI's decision, they made it and now they will reap the benefits either positive or negative from that decision.

Personally I think they should have reached out to the open source community and made a deal to take over support for the proprietary drivers.  But they didn't, again it's their choice and they will see if that was a good step or not.

---

### Post by mihai.ile on 2009-04-30
someone in here almost got it working using 8.10 xserver-xorg from CD (see posts below post #12):
[http://ubuntuforums.org/showthread.php?p=7179258#post7179258](http://ubuntuforums.org/showthread.php?p=7179258#post7179258)

---

### Post by alive1 on 2009-04-30
Hi, I have a Thinkpad T500 with 2gb ram and an ATI 3650 card. With the 9.4 drivers under ubuntu 9.04 I 
- Can't use OpenGL without an immediate crash of the entire system
- Can't play any video without random crashes happening about every 10 mins of video (Entire system, needs reboot after)
- Can't achieve dual-screen with two separate screens on one desktop (Xinerama doesn't work, everything is one big desktop)

Basically, my computer could just as well be a Pentium 133 thanks to these drivers.  Carrying around my laptop feels like 1% multimedia and 99% brick.

---

### Post by ales on 2009-04-30
> **defaria said:**
> I'm confused. Let me state that I have an ATI Radeon HD 3200 in my desktop (not laptop). I assume that falls in the ATI Radeon HD 3000 Series. How exactly does one use a combination of an ATI Radeon HD 3000 Series like my 3200 **in combination with** one of the above listed series? Isn't either one card or the other? :confused:

So far my 3200 doesn't work with Ubuntu 9.04, even with the supposedly working 9.4 Catalyst drivers. I've had black screens, white screens, messed up screens, window manager aborts, failure to recognize a dual monitor set up, etc.

Is my ATI Radeon HD 3200 supposed to be supported or not on Unbuntu 9.04? If so how do I get the correct driver so I can run dual monitor and also do 3d stuff and Compiz?


According to the list your card is enough new and should be supported. It is possible, that u need to modify the xorg.conf On 8.10 I added a real amount of lines to it I found on one forum. I will try to paste it here. Maybe ithelps. But later in the evening. Problems with your card are maybe because the shhift to new x and new driver is not for now goog. The will surely update the driver. But you have to wait. I stay in 8.10 and will look how this develops till 9.10 Ubuntu...

---

### Post by alpharesearch on 2009-04-30
I have a FireGL X1... so I went to the AMD web page to download the suggested 8.583 Catalyst driver (Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3 )... the driver had a option for ubuntu/9.04 to create deb files and install and this is what I did... after the install and reboot I got this error:
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (loader failed, 7)
(EE) Failed to load module "fglrx" (module requirement mismatch, 0)
(EE) No drivers available.

Does this mean my card is not longer supported?

I need Open GL to work with Blender, is it possible to downgrade just the X server?

To me it looks like X has two components with different version numbers... like x server 1.6 and xorg 7.4... but I don't understand the relation... can someone please explain this to me, thank you.

I used this command to find out what card I have:
lspci -v | less
```

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NG [FireGL X1] (rev 80)
        Subsystem: ATI Technologies Inc Device 0172
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at ec00 [size=256]
        Memory at ff8f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at ff800000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: fglrx_pci
        Kernel modules: radeonfb

01:00.1 Display controller: ATI Technologies Inc Radeon R300 [FireGL X1] (Secondary) (rev 80)
        Subsystem: ATI Technologies Inc Device 0173
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at ff8e0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>


```

---

### Post by mr_raider on 2009-04-30
I have an x1900xt which is still a fairly good card, and I'd like to keep using it. How do the open source drivers perform in native games like NWN or WINE emulation games under jaunty? I'm sticking to 8.10 for now, because everything works as is.

---

### Post by hockman5 on 2009-04-30
I have an ATI Radeon HD2400 (supported) but I couldn't get the upgrade to work so I did a fresh install of Jaunty. After some tweaking and downloading the ATI driver from ATI, I got it to work. Now Compiz won't work. It says that I am using the Vesa driver with no rendering method. How can I correct that?

---

### Post by peakshysteria on 2009-04-30
Got working graphics and Compiz out of the box with my card. Haven't bothered to checkout the Ati driver yet. But it worked very well with Intrepid.

---

### Post by ales on 2009-04-30
> **peakshysteria said:**
> Got working graphics and Compiz out of the box with my card. Haven't bothered to checkout the Ati driver yet. But it worked very well with Intrepid.

Have u now 9.04? with open drivers?

---

### Post by t-readyroc on 2009-04-30
> **StuartN said:**
> My Radeon Xpress 200M runs **glxgears** at 2,200 frames per second with the older proprietary Catalyst driver that works in Ubuntu 8.10.

Running the Ubuntu 9.04 Live CD with the "radeon" driver selected at bootup, I am getting just 320 frames per second (one seventh of the speed in 8.10).

> **eggplant37 said:**
> Here's the warning I'll make. I upgraded last night from 8.10 to 9.04. I had 3D working well enough to run World of Warcraft on wine without much problem, albeit with low frame rates with the 9.3 Catalyst drivers. Not impossible to play, but not a real joy, either.

Now, after the upgrade last night, I'm averaging 1-3 fps using the ati radeon driver installed with 9.04 on a Dell Inspiron 1501 laptop with the Radeon Xpress 200M chip in it. 

Don't waste your time until they determine where the problem is and get this crap fixed. I'll be reverting to 8.10 this weekend.

I stopped my upgrade process when I found this thread.  I've got a laptop w/the 200M as well, so I guess I'll be waiting out this issue.  Hopefully they'll get it sorted before too long.

---

### Post by emarkay on 2009-04-30
> **hockman5 said:**
> I have an ATI Radeon HD2400 (supported) but I couldn't get the upgrade to work so I did a fresh install of Jaunty. After some tweaking and downloading the ATI driver from ATI, I got it to work. Now Compiz won't work. It says that I am using the Vesa driver with no rendering method. How can I correct that?


What kind of tweaking?   :)  

Compiz can be a separate issue IMHO - just getting a legit display is priority #1 here.

Thanks!

---

### Post by emarkay on 2009-04-30
I see a variety of issues here with the ATI cards and I wanted to post an ATI series-to-model number cross ref:

    Rage series
    Rage Mobility series
    Radeon R100 (7xxx) series
    Radeon R200 (8xxx, 9xxx) series
    Radeon R300 (9xxx, X10xx) series
    Radeon R300 PCIe (X3xx, X5xx, X6xx) series
    Radeon R400 AGP (X7xx, X8xx) series
    Radeon R400 PCIe (X7xx, X8xx) series
    Radeon X12xx & 2100 IGP series
    Radeon R500 (X1xxx) series
    Radeon R600 (HD 2xxx, HD 3xxx) series
    Radeon HD 3xxx IGP series
    Radeon R700 (HD 4xxx) series
    Mobility Radeon Series
    FireGL series
    FirePro 3D series
    FireMV/FirePro Multi-View series
    Mobility FireGL series

[http://en.wikipedia.org/wiki/Comparison_of_ATI_graphics_processing_units](http://en.wikipedia.org/wiki/Comparison_of_ATI_graphics_processing_units)

Further breakdown:

  * RV505:	Radeon X1550, X1550 64bit
  * RV515:	Radeon X1300, X1550, X1600; FireGL V3300, V3350
  * RV516:	Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250
  * R520:	Radeon X1800; FireGL V5300, V7200, V7300, V7350
  * RV530:	Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200
  * RV535:	Radeon X1300, X1650
  * RV550:	Radeon X2300 HD
  * RV560:	Radeon X1650
  * RV570:	Radeon X1950, X1950 GT; FireGL V7400
  * R580:	Radeon X1900, X1950; AMD Stream Processor
  * R600:	Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650
  * RV610:	Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000
  * RV620:	Radeon HD 3450, HD 3470
  * RV630:	Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;	FireGL V3600/V5600
  * RV635:	Radeon HD 3650, HD 3670
  * RV670:	Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170
  * R680:	Radeon HD 3870 X2
  * M52:	Mobility Radeon X1300
  * M54:	Mobility Radeon X1400; M54-GL
  * M56:	Mobility Radeon X1600; Mobility FireGL V5200
  * M58:	Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200
  * M62:	Mobility Radeon X1350
  * M64:	Mobility Radeon X1450, X2300
  * M66:	Mobility Radeon X1700, X1700 XT; FireGL V5250
  * M68:	Mobility Radeon X1900
  * M71:	Mobility Radeon HD 2300
  * M72:	Mobility Radeon HD 2400; Radeon E2400
  * M74:	Mobility Radeon HD 2400 XT
  * M76:	Mobility Radeon HD 2600;  	(Gemini ATI) Mobility Radeon HD 2600 XT
  * M82:	Mobility Radeon HD 3400
  * M86:	Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700
  * M88:	Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2
  * RS600:	Radeon Xpress 1200, Xpress 1250
  * RS690:	Radeon X1200, X1250, X1270
  * RS740:	RS740, RS740M
  * RS780:	Radeon HD 3100/3200/3300 Series
  * R700:	Radeon R700
  * RV710:	Radeon HD4570, HD4350
  * RV730:	Radeon HD4670, HD4650
  * RV740:	Radeon HD4770. EXPERIMENTAL AND UNTESTED
  * RV770:	Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro
  * RV790:	Radeon HD 4890
  * M92:	Mobility Radeon HD4330, HD4530, HD4570. EXPERIMENTAL
  * M93:	Mobility Radeon M93. EXPERIMENTAL AND UNTESTED
  * M96:	Mobility Radeon HD4600
  * M97:	Mobility Radeon HD4860. EXPERIMENTAL AND UNTESTED
  * M98:	Mobility Radeon HD4850, HD4870

[url]http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README[\url]

Also: 
"The open-source Radeon driver supports earlier ATI graphics processors including the R100, R200, R300, and R400 series. There is also initial work for the R500 and R600 series support."

[http://www.radeonhd.org/](http://www.radeonhd.org/)

FWIW my issue is with the R600 series card.

---

### Post by emarkay on 2009-04-30
additional reference info: 

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
specifically:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Post-Installation_Tweaks](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Post-Installation_Tweaks)
...with this title: "Installation Guide for Ubuntu Jaunty (v 9.04) Currently Doesn't WORK!! Be Forewarned... "

[http://www.rage3d.com/board/forumdisplay.php?f=61](http://www.rage3d.com/board/forumdisplay.php?f=61)

---

### Post by emarkay on 2009-05-01
Anyone have any more information - I don't know enough about the changes to 9.04 over 8.10 to be able to even start looking into why this is happening.

(in other words, Help us, experts!)

What does this have to do in relation to all this - specifically:
[http://wiki.x.org/wiki/radeonhd#head-cc89624fd96105127892119323e209b3d80e137d](http://wiki.x.org/wiki/radeonhd#head-cc89624fd96105127892119323e209b3d80e137d)

---

### Post by apparle on 2009-05-01
> **StuartN said:**
> My Radeon Xpress 200M runs **glxgears** at 2,200 frames per second with the older proprietary Catalyst driver that works in Ubuntu 8.10.

Running the Ubuntu 9.04 Live CD with the "radeon" driver selected at bootup, I am getting just 320 frames per second (one seventh of the speed in 8.10).

How did you select the open source ati driver in Live CD bootup

---

### Post by StuartN on 2009-05-01
> **apparle said:**
> How did you select the open source ati driver in Live CD bootup

The distribution selected the "radeon" driver itself, I didn't need to do anything. It is an Xpress 200M in a Dell Inspiron laptop.

---

### Post by brons2 on 2009-05-01
> **emarkay said:**
> Anyone have any more information - I don't know enough about the changes to 9.04 over 8.10 to be able to even start looking into why this is happening.

(in other words, Help us, experts!)

The latest ATI driver that is compatible with the version of xorg that is shipped with 9.04 does not have support for any ATI cards that are older than the 2xxx series.

The older driver which supports those cards does not work with the xorg version that is in 9.04.

I don't think there is a fix at this time, other than to not use the fglrx drivers and forgo hardware acceleration.

---

### Post by emarkay on 2009-05-01
> **brons2 said:**
> The latest ATI driver that is compatible with the version of xorg that is shipped with 9.04 does not have support for any ATI cards that are older than the 2xxx series.

The older driver which supports those cards does not work with the xorg version that is in 9.04.

I don't think there is a fix at this time, other than to not use the fglrx drivers and forgo hardware acceleration.

But my card IS a 2xxx series!

And for those that DO have older cards, there needs to be a specific place for info to get them running; not everyone has hourse  of time per day and the resources to dig...

---

### Post by emarkay on 2009-05-01
Bumped.

---

### Post by hockman5 on 2009-05-01
> **emarkay said:**
> What kind of tweaking?   :)  

Compiz can be a separate issue IMHO - just getting a legit display is priority #1 here.

Thanks!

I downloaded the ATI driver from their website. I tried to compile the one for Ubuntu 9. but it didn't work so I went with the default and it worked. I installed it from terminal (since that is all I had). It worked all day yesterday, even after several reboots, but, today when I went to boot up, I get a blank black screen again with no keyboard control. ATI Radeon 2400HD.

---

### Post by emarkay on 2009-05-01
> **hockman5 said:**
> I downloaded the ATI driver from their website. I tried to compile the one for Ubuntu 9. but it didn't work so I went with the default and it worked. I installed it from terminal (since that is all I had). It worked all day yesterday, even after several reboots, but, today when I went to boot up, I get a blank black screen again with no keyboard control. ATI Radeon 2400HD.

That may be the oft reported "Freeze" issue - it's separate. One thing on that one seems to be the new EXT4 - did you reformat to that? Do a search to find more on it.

---

### Post by hockman5 on 2009-05-01
> **emarkay said:**
> That may be the oft reported "Freeze" issue - it's separate. One thing on that one seems to be the new EXT4 - did you reformat to that? Do a search to find more on it.

Originally I did the Upgrade so it was EXT3 and I had the same problem. Then I did a new install and selected EXT4, same problem.
So you are saying this freeze has nothing to do with the ATI driver? I will look into it further.

---

### Post by charlesdean2002 on 2009-05-01
I see a lot oy yelling about  grafix cards, well I  placed my hard drive in another computer and my desktop still is unusable , but yes it looks like a video issue I have ati apg card. the other computer  a pci card unknown but know it is not ati. on install it told me it was checking drivers  , was that a lie? If it was checking ho come it approved the computer for upgrade. I want to know if they some way I can use grub command to go back to 8.10. And how come our designers forgot to adapt working drivers from our previous 8.10 os for the upgrade this has left a lot of ubuntu users without their computers until the bug is fixed. 
Windows lost over 14,000 customers to linux os  just this year. how many will stay if our designers keep making windows mistakes like this one? I came and stayed with ubuntu now for five years and this has been the worse nightmare I have experienced with linux thus far . I have lost a lot of time on this upgrade and may loose all my work in my computer now. I am glad I did not do it to my wife's computer other wise I couldn't come to forums.
HELP please ubuntu save this day

---

### Post by charlesdean2002 on 2009-05-01
gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]
I type all this in and it says unrecognizable 
is it to be in steps coz it don' show that. now i only goes to grub when I ask for command it does same things here. What a nightmare!
remember mine does not go to desktop so I have to learn to do command from "esc" on start up. 
I have no desktop to make adjustments . when it goes to desktop it appears scrambled, even if I place the hard drive into another older computer . no panels not keyboard use and no mouse!

---

### Post by emarkay on 2009-05-01
"I  placed my hard drive in another computer and my desktop still is unusable"

As in windows that is dangerous as there may be mainboard video, audio, processor differences; without doing a complete reinstall that could cause "unimaginable" problems.

"but yes it looks like a video issue I have ati apg card. the other computer  a pci card unknown but know it is not ati. "

In Terminal or at the prompt type:sudo lshw
Look for "*-display" - about 40% down in list:

"on install it told me it was checking drivers  , was that a lie? If it was checking ho come it approved the computer for upgrade."

It does check to see what you have to know what to install, but there is no "Approval" process - it's a "dumb machine" and if the program finds enough to begin the install it will try all options - it may not be perfect, but it should get you to a point where you can work on it - remember MS Windows and "Plug-and-Pray" every time you added something you could get the "Blue Screen of Death"...

"I want to know if they some way I can use grub command to go back to 8.10. "

No.

"And how come our designers forgot to adapt working drivers from our previous 8.10 os for the upgrade this has left a lot of ubuntu users without their computers until the bug is fixed. "

Remember Ubuntu is composed of thousands of programs - just as is Windows - except here they are individually tailored to the users - YES this "open source" can cause problems because of this, (instead of "Bill Gates" saying "yes, no, ytes, yes, no" to everything - but then you only get Bill Gates' way to do it).  It's a choice to use Open Source.

"Windows lost over 14,000 customers to linux os  just this year. how many will stay if our designers keep making windows mistakes like this one? "

Not a mistake by definition, but there can be errors and remember even I have an issue with Ubuntu now (here)  - but I always have a backup plan...  and even Windows, your car and maybe even your life hav issues that are not perfect, but at least you are doing the right thing here by trying to get help - we are doing our best..
  
"I came and stayed with ubuntu now for five years and this has been the worse nightmare I have experienced with linux thus far. I have lost a lot of time on this upgrade and may loose all my work in my computer now. I am glad I did not do it to my wife's computer other wise I couldn't come to forums. HELP please ubuntu save this day"

Well it's been DAYS here on this issue for me, but we are all trying.

Put the disk in the machine you want, and insure the program is installed on THAT disk and PC together for starters.  Then we can begin debugging - I would suggest a new thread with specific questions, too.

---

### Post by peakshysteria on 2009-05-01
> **ales said:**
> Have u now 9.04? with open drivers?

Yep. Graphics worked out of the box as previous mentioned. I had installed the Ati driver on my 8.10 setup (worked very well. Not sure which version). Upgraded my system to Jaunty Beta. Which auto-removed the installed Ati driver during the upgrade process. All is very smooth here. It's been a while since I've had any trouble with Ati drivers for my card.

I was very surprised to see that it worked out of the box this time.

---

### Post by emarkay on 2009-05-01
I decided to wipe the install and try over.  I did have to use the "Safe Graphics Mode" on the Live CD to get any display, but after doing that I installed a new (formatted and all) Ubuntu 9.04 Jaunty.  (I get those names confused - sorry,,,)

I ignored the note about the "Restricted Driver Available" and immediately copied the ATI/AMD Catalyst 9.4 to my new "DOWNLOAD" directory and ran it.

I don't know if it's all working yet, but I did get a good display and saw GLXGEARS running at over 1000 FPS.  Could have been mung or kipple somewhere from trying to figure this out, but I did finally get my 16:9 display at 60Hz.

---

### Post by apparle on 2009-05-01
I have Radeon Xpress 200 which is 'legacy'

I was getting poor performace on a Live CD.........no desktop effects.. so I wasn't sure whether to install jaunty or not

Finally I installed jaunty from an alternate CD and now the desktop effects run smoothly out of box withoout any configuration at all........
I could even say that as per as desktop effects are considered performance has improved:)

I am getting 400FPS here against 1300 FPS on fglrx in intreprid but who cares.....as long as desktop effects and videos run smooth its fine with me. For what else do I need a graphic card any ways?

Also I am rather puzzled. There is nothing in /etc/X11/xorg.conf. Absolutely nothing. The size is also 0B

---

### Post by charlesdean2002 on 2009-05-01
> **charlesdean2002 said:**
> gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]
I type all this in and it says unrecognizable 
is it to be in steps coz it don' show that. now i only goes to grub when I ask for command it does same things here. What a nightmare!
remember mine does not go to desktop so I have to learn to do command from "esc" on start up. 
I have no desktop to make adjustments . when it goes to desktop it appears scrambled, even if I place the hard drive into another older computer . no panels not keyboard use and no mouse!
Can some one tell mt the tip to take me back to the previous 8.01. I can not find a fix on this. right now I am on here with the 8.04 live cd.. I built a nice 8.01 and want to go back it was hard work setting up my computer for 8.01 and I like it I want for 9.01 
are they any techs from ubuntu reading this or direct me to help?

---

### Post by mag00 on 2009-05-01
I have finished to upgrade from 8.10 x64 and I like what I see here. But my video card is a x600 pro (ati) and it does not seems to be working fine. 

When I restarted the PC the video flicking some minutes and then stopped flicking. It seems that the card just was seizing the new environment.

I was using compiz-fusion on 8.10, but now I will wait for some new driver after try it again. For now I just will use the "normal" settings on visual effects configuration.

[]'s

---

### Post by s3lekta on 2009-05-02
ok, i managed to install 9.04 fresh and everything seems to be okay

the problem is now,

if i maximize and minimize a window it takes a few seconds or so.. i know someone mentioned it in the thread but i tried a few recommendations and still not winning

let me know if you guys / gals have any links

thanks

video card again :( ati radeon 3400 hd

---

### Post by Jdavison on 2009-05-02
I also have an ATI HD3450 and have video issues with 9.04.  I was planning on switching to Ubuntu/Linux as my main OS, but after fighting with the graphics issues I think I'm going to stick with the Windows 7 beta (and upcoming RC) as my desktop OS.  I really wanted to like "Jaunty", especially after looking at the difference in resource utilization between it and Windows, but wrestling with things that should "just work" like dual displays and video card functionality really seems silly. With the amount of time I've burned on try to get Ubuntu running the way I need it to, it really makes just purchasing a Windows or OS X license a more cost-effective solution, depending on your hardware platform.

---

### Post by joebrueske on 2009-05-02
I just thought I'd mention that I haven't had any difficulty getting my laptop up and running perfectly with my ATI X1600 Mobility card. I did have to install compizconfig-settings-manager. I don't know why it wasn't installed, and Compiz automatically ran after I switch the Special Effects to Extra.

I did NOT get an error message when installing from the CD that the drivers weren't compatible with the video card. So I figured it would work just fine. But you never know with hardware, you know? I haven't tried installing any other open source drivers, whatever Jaunty comes with seems to work just fine for an older mobility card.

Now I'm just running into small issues with Flash. BUT... oh BUT... Full screen flash (ie. hulu) works FLAWLESSLY. OH, YES. One less thing I have to use Windows for. MWAHAHAHAHAHA. I still need it for um . . . for . . . hmmm. Of, right, my PS1 emulator. 

...click ... click ... Holy Crap! EPSXE runs FASTER in Ubuntu than under Windows! Dang! I don't think I'll be using Windows on this laptop for a loooong tiiime! LOL

---

### Post by hasplu on 2009-05-02
Hi all

I've got ati radeon 9600. after 4 days of reading and trying, I managed to get to a desktop screen :P But that was all...

I removed the fglrx drivers, which improved the system, but still evrything freezes when trying to watch youtube for example. 
I added in xorg.conf in device section "Device ati", adn nothing changed, even I thing the system become a bit slower.

Then decided to install ati 9.3 drivers, downloaded them from their site, rebooted in recovery mode, chose netroot and than I ran the downloaded "sh ./ati driver" The driver began to install "Ati Properietary Linux Driver - 8.593" and finished with strange error:

"Error: ./default_policy.sh does not support version default: v2: i686 :lib : : none: 2.6.28.11-generic. make sure that the version is being correctly set by --iscurrentdistro"

The funy thing is that the last command is unknown for the system :P

"uname -r" shows I am really using 2.6.28-11-generic, so please anyone can give me a clue what's wrong with this error? I am really starting to piss off with ati....

---

### Post by DwalerXIII on 2009-05-02
> **emarkay said:**
> I decided to wipe the install and try over.  I did have to use the "Safe Graphics Mode" on the Live CD to get any display, but after doing that I installed a new (formatted and all) Ubuntu 9.04 Jaunty.  (I get those names confused - sorry,,,)

I ignored the note about the "Restricted Driver Available" and immediately copied the ATI/AMD Catalyst 9.4 to my new "DOWNLOAD" directory and ran it.

I don't know if it's all working yet, but I did get a good display and saw GLXGEARS running at over 1000 FPS.  Could have been mung or kipple somewhere from trying to figure this out, but I did finally get my 16:9 display at 60Hz.

Can you let us know if this works? My card is an hd2600 also. I'm scared of doing the update and I'm waiting for some good news.

---

### Post by bemis23 on 2009-05-02
I've been having the same issue here as many people after installing the Catalyst 9.4 package (corrupted display, hard lock). I've reinstalled Jaunty and am working now with the open source driver which is fine for display, but the fan noise is driving me bonkers since I've got no fan speed controls with an Asus-made ATI 4870X2.  

I still use Windows for most of my gaming, so 3D acceleration is not as important for me, but the fan speed problem is severe.  Can anyone recommend any solutions since I apparently can't use the CCC?

---

### Post by shrndegruv on 2009-05-02
if you have an ati card, stay away from jaunty like its the plague.

---

### Post by mr_raider on 2009-05-02
> **shrndegruv said:**
> if you have an ati card, stay away from jaunty like its the plague.

That seems to be my best bet for now. I'll see if can pick up a cheap 9600gt to replace my my venerable x1900xt.

---

### Post by blackSP on 2009-05-02
> **shrndegruv said:**
> if you have an ati card, stay away from jaunty like its the plague.


Not necessarily.
I have a HD2400 and after a failed upgrade and 2 clean installs failing after a driver upgrade I installed again and stayed away from any graphics tweaking.

I have not even started the 'System-Administration-Hardware Drivers' cause that will install the dreaded fglrx virus.

Anyway, I just checked my xorg.conf and it's still empty. Yep, zero bytes! Maybe that's my key to succes...

Now my video output is fast, windows open and close in a jiffy, VLC works as it was supposed to. I will install and run some game in a minute to see how that goes.

Update:
Running Nexuiz is a nightmare. Definitely no Open GL support, and when switched off a frame rate of about 2fps. Totally unplayable!

---

### Post by shrndegruv on 2009-05-02
> **blackSP said:**
> Not necessarily.
I have a HD2400 and after a failed upgrade and 2 clean installs failing after a driver upgrade I installed again and stayed away from any graphics tweaking.

I have not even started the 'System-Administration-Hardware Drivers' cause that will install the dreaded fglrx virus.

Anyway, I just checked my xorg.conf and it's still empty. Yep, zero bytes! Maybe that's my key to succes...

Now my video output is fast, windows open and close in a jiffy, VLC works as it was supposed to. I will install and run some game in a minute to see how that goes.

Update:
Running Nexuiz is a nightmare. Definitely no Open GL support, and when switched off a frame rate of about 2fps. Totally unplayable!

i have a laptop -- the open source drivers run about 15 degrees C hotter than fglrx.  which is unacceptable.  

Im back to windows until there exists a driver for ATI cards that has full 3d support, support for suspend/hibernate, and doesn't burn off my crotch when the machine sits in my lap.

---

### Post by wolffkrieger on 2009-05-02
I have a Radeon HD 2600 Pro AGP card. It worked perfectly in 8.10 with the proprietry drivers installed via "Hardware Drivers". After a clean install of 9.04 using EXT4 for / and EXT3 for /home (someone mentioned this could be an issue but in my case it is not) I was able to boot up perfectly but without any 3D enabled.

I tried installing the restricted drivers via "Hardware Drivers" but was unable to complete said installation due to an alert that said something along the lines of "jockey connection problem" (something like that). I retried to activate the propietry driver and got the same error.

So I went to synaptic and found the fglrx driver. Installed it. Rebooted and my screen froze upon entering my session. I recovered my screen and instead tried with EnvyNG. EnvyNG has always worked but I felt that it was a little slow.

I recently had to reinstall 9.04 due to a HDD conflict when trying to install WinXP (as a dualboot system). I retried installing the propietry driver from "Hardware Drivers", got the same "Jockey" error, but retried. The "Hardware Drivers" menu seemed to have frozen a bit but no "Jockey" alert. So I rebooted the system and to my surprise my card is working great. The whole "Jockey" issue might have been a problem related to my dsl connection. But so far everything seems to be working just great.

I would suggest you try installing the propietry drivers with "Hardware Drivers" and if not try EnvyNG (maybe it even works for the older cards).

---

### Post by apparle on 2009-05-02
I configured my xorg.conf to run open source drivers.

Now I am seeing some peculiar behaviour........sometimes the driver starts and all effects are fine and sometimes I boot without the drivers resulting in no graphic effects. When I try to enable them in Kwin I get that compositing is not enabled on my card.........although I have explicitly enabled compositing in xorg.conf...........I think sometimes the new Xorg server starts with my xorg.conf and sometimes with default settings without considering the xorg.conf file

---

### Post by emarkay on 2009-05-02
> **DwalerXIII said:**
> Can you let us know if this works? My card is an hd2600 also. I'm scared of doing the update and I'm waiting for some good news.

So far so good - I am having some trouble installing X-Plane 9 - there's something different about Jaunty - the executables aren't executing off the DVD, but I should have an answer soon - but Internet pages and VLC MPEG 4 movie cips look fine in full screen HDTV.

The X-Plane issue is the libopenal change in Jaunty - and it's all WORKING PERFECTLY!

---

### Post by TimTim on 2009-05-03
After I upgrade my Ubuntu to 9.04 from 8.10, no sound when I viewing Youtube. :(:(:( And the VLC & Movie Player crashed when they tried to play those .flv file. Any helps? Thanks...

---

### Post by timClicks on 2009-05-03
TimTim - do you have a flash player installed? You may also need to download the codecs for the different media formats.

---

### Post by kingcharles1666 on 2009-05-03
> **shrndegruv said:**
> i have a laptop -- the open source drivers run about 15 degrees C hotter than fglrx.  which is unacceptable.  

Im back to windows until there exists a driver for ATI cards that has full 3d support, support for suspend/hibernate, and doesn't burn off my crotch when the machine sits in my lap.

Same problem on my Dell C640 with ATI 7500
My machine is almost melting. It smells terrible.

I am wondering if this may be dangerous and can destroy your graphics card?
Is this the future for Linux? Come on AMD deliver something useful please!

---

### Post by shrndegruv on 2009-05-03
if you smell something, something is wrong.  I would suspect defective hardware before suspecting the driver.  even with the open source driver, my card was 20 degrees C below the threshold for the card.

---

### Post by kingcharles1666 on 2009-05-03
The laptop is Dual Boot and in Windows XP it is not heating up like this, so it is not unlikely that the driver is the suspect here

---

### Post by chudak on 2009-05-03
I strongly suggest that anyone who is unhappy with the fact that AMD removed support for relatively new graphics cards from their new driver WRITE to AMD and voice their opinion!!!

I'm running a T60 that is less than two years old. It has an ATI Mobility Radeon X1400 chipset. This TWO YEAR OLD laptop is no longer supported by AMD.

This is inexcusable!!!

---

### Post by darojasp on 2009-05-03
> **chudak said:**
> I strongly suggest that anyone who is unhappy with the fact that AMD removed support for relatively new graphics cards from their new driver WRITE to AMD and voice their opinion!!!

I'm running a T60 that is less than two years old. It has an ATI Mobility Radeon X1400 chipset. This TWO YEAR OLD laptop is no longer supported by AMD.

This is inexcusable!!!

I completely agree. I can understand that a decade old card goes to legacy. But a two years old card? and it's not only a linux problem since those cards are also legacy on windows. So it is definitely an AMD problem.

---

### Post by romulus on 2009-05-03
I'm going back to windows until ubuntu/linux community gets it together with nvidia and amd/ati i'v been fighting graphics issues since 8.10. so good bye maybe i'll se ya in october 2009.

---

### Post by s3lekta on 2009-05-03
> **s3lekta said:**
> ok, i managed to install 9.04 fresh and everything seems to be okay

the problem is now,

if i maximize and minimize a window it takes a few seconds or so.. i know someone mentioned it in the thread but i tried a few recommendations and still not winning

let me know if you guys / gals have any links

thanks

video card again :( ati radeon 3400 hd

bump anyone?

---

### Post by pbpersson on 2009-05-03
I am using one of the following cards in this Jaunty machine:

ATI Radeon 9550 Series
ATI Radeon 9600 Series

GUI works fine, woobly windows are fine, and even the desktop cube is fine but Google Earth is a disaster.

I forget which card is in this machine and I cannot check now because I have a kitten sleeping in my lap

---

### Post by lvleph on 2009-05-03
I just posted a complaint on the AMD forums. Please, post your complaint too.
```

http://forums.amd.com/game/messageview.cfm?catid=260&threadid=112829&enterthread=y
```

---

### Post by chudak on 2009-05-04
> **lvleph said:**
> I just posted a complaint on the AMD forums. Please, post your complaint too.
```

http://forums.amd.com/game/messageview.cfm?catid=260&threadid=112829&enterthread=y
```

And it was immediately locked by a moderator. Apparently they must have Best Buy or Apple training their moderators and customer service reps. They just don't give a **** about their customers.

Vote with your wallets people.

---

### Post by hasplu on 2009-05-04
> **lvleph said:**
> I just posted a complaint on the AMD forums. Please, post your complaint too.
```

http://forums.amd.com/game/messageview.cfm?catid=260&threadid=112829&enterthread=y
```

yep, I saw the answer too...

Is there any way downgrading the driver to 9.3 or 9.2? because "stick to 9.3", according to amd is maybe the only way for me to have working OS with X support.

The Dri does not recognize properly my rv360 and as a result everything works  like a nightmare :(

---

### Post by jaxpiron on 2009-05-04
I made a great mistake 3 years ago on ordering this laptop with the ati card in it (x1400). Won't repeat it next time for sure.

Luckily I installed jaunty on a separate partition to see how it worked without the restricted drivers...

well 3d is not (yet) there, but I think users with this card will probably have much more rewards with the 9.10 os drivers...

so I stick with 8.10 with restricted drivers when I need 3d, occasionally use 9.04.

still it is a shame that this thing is driving new people away from this great os.

what is really disturbing is that it is not possible to use the "working on intrepid" restricted drivers on jaunty.

---

### Post by mrkr on 2009-05-04
Hi All,
i'm new to this forum and I got Jaunty working(on a dirty way) with Xinerama(Dualview) and fglrx.

I installed Jaunty on a diffrent parition (dualboot) and made a diff between the amdpcsdb  from working intrepid(left) and the buggy jaunty(right):

[PHP]24,26d23
< Gxo50HzTimingSupport=V1
< Gxo24HzTimingSupport=V1
< Gxo2530HzTimingSupport=V1
132,133d128
< EnableRandR12=SFALSE
< MultiviewXineramaNo3D=V1
137c132
< Width=V2560
---
> Width=V1280
139c134
< Refresh=V60
---
> Refresh=V75
141,142d135
< DAL_ACEspectReady=V0
< DALLastSelected=V1
143a137,140
> DALR6 CRT_MaxModeInfo=R000000000005000000040000000000004B000000
> DALR6 CRT2_MaxModeInfo=R000000000005000000040000000000004B000000
> DAL_ACEspectReady=V0
> DALLastSelected=V3
152,155d148
< DALR6 CRT_MaxModeInfo=R000000000005000000040000000000004B000000
< DALR6 CRT2_MaxModeInfo=R000000000005000000040000000000004B000000
< DAL_CRT2NDDACColorTemperatureSourceD10976BF=R0200000064190000
< DAL_CRTColorTemperatureSourceD1097682=R0200000064190000
158,159c151
< DALR6 CRT2=R0000000000000000000000006400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000640000006419000000000000000000000000000000000000000000000000000000000000
< DALR6 CRT2640x480x0x60=R000000000000000000000000000000000000000000000000010000000100000000000000000000000000000000000000
---
> DAL_CRTColorTemperatureSourceD1097682=R0200000064190000
161,162d152
< DALR6 CRT640x480x0x60=R000000000000000000000000000000000000000000000000010000000100000000000000000000000000000000000000
< DALR6 CRT21280x1024x0x60=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
164,165c154,156
< DALR6 CRT1280x1024x0x75=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
< DALR6 CRT21280x1024x0x75=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
---
> DAL_CRT2NDDACColorTemperatureSourceD10976BF=R0200000064190000
> DALR6 CRT2=R0000000000000000000000006400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000640000006419000000000000000000000000000000000000000000000000000000000000
> DALR6 CRT21280x1024x0x60=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
168,170d158
< DALDriverGammaData_Index0FS3DRed=R00000101020203030404050506060707080809090A0A0B0B0C0C0D0D0E0E0F0F10101111121213131414151516161717181819191A1A1B1B1C1C1D1D1E1E1F1F20202121222223232424252526262727282829292A2A2B2B2C2C2D2D2E2E2F2F30303131323233333434353536363737383839393A3A3B3B3C3C3D3D3E3E3F3F40404141424243434444454546464747484849494A4A4B4B4C4C4D4D4E4E4F4F50505151525253535454555556565757585859595A5A5B5B5C5C5D5D5E5E5F5F60606161626263636464656566666767686869696A6A6B6B6C6C6D6D6E6E6F6F70707171727273737474757576767777787879797A7A7B7B7C7C7D7D7E7E7F7F80808181828283838484858586868787888889898A8A8B8B8C8C8D8D8E8E8F8F90909191929293939494959596969797989899999A9A9B9B9C9C9D9D9E9E9F9FA0A0A1A1A2A2A3A3A4A4A5A5A6A6A7A7A8A8A9A9AAAAABABACACADADAEAEAFAFB0B0B1B1B2B2B3B3B4B4B5B5B6B6B7B7B8B8B9B9BABABBBBBCBCBDBDBEBEBFBFC0C0C1C1C2C2C3C3C4C4C5C5C6C6C7C7C8C8C9C9CACACBCBCCCCCDCDCECECFCFD0D0D1D1D2D2D3D3D4D4D5D5D6D6D7D7D8D8D9D9DADADBDBDCDCDDDDDEDEDFDFE0E0E1E1E2E2E3E3E4E4E5E5E6E6E7E7E8E8E9E9EAEAEBEBECECEDEDEEEEEFEFF0F0F1F1F2F2F3F3F4F4F5F5F6F6F7F7F8F8F9F9FAFAFBFBFCFCFDFDFEFEFFFF
< DALDriverGammaData_Index0FS3DGreen=R00000101020203030404050506060707080809090A0A0B0B0C0C0D0D0E0E0F0F10101111121213131414151516161717181819191A1A1B1B1C1C1D1D1E1E1F1F20202121222223232424252526262727282829292A2A2B2B2C2C2D2D2E2E2F2F30303131323233333434353536363737383839393A3A3B3B3C3C3D3D3E3E3F3F40404141424243434444454546464747484849494A4A4B4B4C4C4D4D4E4E4F4F50505151525253535454555556565757585859595A5A5B5B5C5C5D5D5E5E5F5F60606161626263636464656566666767686869696A6A6B6B6C6C6D6D6E6E6F6F70707171727273737474757576767777787879797A7A7B7B7C7C7D7D7E7E7F7F80808181828283838484858586868787888889898A8A8B8B8C8C8D8D8E8E8F8F90909191929293939494959596969797989899999A9A9B9B9C9C9D9D9E9E9F9FA0A0A1A1A2A2A3A3A4A4A5A5A6A6A7A7A8A8A9A9AAAAABABACACADADAEAEAFAFB0B0B1B1B2B2B3B3B4B4B5B5B6B6B7B7B8B8B9B9BABABBBBBCBCBDBDBEBEBFBFC0C0C1C1C2C2C3C3C4C4C5C5C6C6C7C7C8C8C9C9CACACBCBCCCCCDCDCECECFCFD0D0D1D1D2D2D3D3D4D4D5D5D6D6D7D7D8D8D9D9DADADBDBDCDCDDDDDEDEDFDFE0E0E1E1E2E2E3E3E4E4E5E5E6E6E7E7E8E8E9E9EAEAEBEBECECEDEDEEEEEFEFF0F0F1F1F2F2F3F3F4F4F5F5F6F6F7F7F8F8F9F9FAFAFBFBFCFCFDFDFEFEFFFF
< DALDriverGammaData_Index0FS3DBlue=R00000101020203030404050506060707080809090A0A0B0B0C0C0D0D0E0E0F0F10101111121213131414151516161717181819191A1A1B1B1C1C1D1D1E1E1F1F20202121222223232424252526262727282829292A2A2B2B2C2C2D2D2E2E2F2F30303131323233333434353536363737383839393A3A3B3B3C3C3D3D3E3E3F3F40404141424243434444454546464747484849494A4A4B4B4C4C4D4D4E4E4F4F50505151525253535454555556565757585859595A5A5B5B5C5C5D5D5E5E5F5F60606161626263636464656566666767686869696A6A6B6B6C6C6D6D6E6E6F6F70707171727273737474757576767777787879797A7A7B7B7C7C7D7D7E7E7F7F80808181828283838484858586868787888889898A8A8B8B8C8C8D8D8E8E8F8F90909191929293939494959596969797989899999A9A9B9B9C9C9D9D9E9E9F9FA0A0A1A1A2A2A3A3A4A4A5A5A6A6A7A7A8A8A9A9AAAAABABACACADADAEAEAFAFB0B0B1B1B2B2B3B3B4B4B5B5B6B6B7B7B8B8B9B9BABABBBBBCBCBDBDBEBEBFBFC0C0C1C1C2C2C3C3C4C4C5C5C6C6C7C7C8C8C9C9CACACBCBCCCCCDCDCECECFCFD0D0D1D1D2D2D3D3D4D4D5D5D6D6D7D7D8D8D9D9DADADBDBDCDCDDDDDEDEDFDFE0E0E1E1E2E2E3E3E4E4E5E5E6E6E7E7E8E8E9E9EAEAEBEBECECEDEDEEEEEFEFF0F0F1F1F2F2F3F3F4F4F5F5F6F6F7F7F8F8F9F9FAFAFBFBFCFCFDFDFEFEFFFF
178,185c166,169
< DALR6 CRT1024x768x0x75=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
< DALR6 CRT21024x768x0x75=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
< DALR6 CRT1280x960x0x60=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
< DALR6 CRT21280x960x0x60=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
< DALR6 CRT800x600x0x75=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
< DALR6 CRT2800x600x0x75=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
< DALR6 CRT1280x768x0x60=R000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000
< DALR6 CRT21280x768x0x60=R000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000
---
> DALR6 CRT1280x1024x0x75=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
> DALR6 CRT21280x1024x0x75=R000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
> DAL_CRTColorTemperatureSource00000000=R0200000064190000
> DAL_CRT2NDDACColorTemperatureSource00000000=R0200000064190000
187d170
< DesktopSetup=Shorizontal
190,192d172
< [AMDPCSROOT/SYSTEM/BUSID-4:0:0-0/LibXUtil/Display1]
< Map=V1
< Enable=V1
195c175,177
< GammaChannelSelState=V0
---
> [AMDPCSROOT/SYSTEM/BUSID-4:0:0-0/LibXUtil/Display1]
> Map=V2
> Enable=V1
197c179
< Map=V1
---
> Map=V2
200a183,184
> [AMDPCSROOT/SYSTEM/BUSID-4:0:0-1/LDC]
> LinkedAllSliders=V1
202,204d185
< DisplayPopupState=V0
< LastViewedPage=SWillkommen
< LastSelectedDevice=S1024:38280:4098:8759:6023|0
207d187
< ColorPreviewDlgState=V0
209,211c189
< [AMDPCSROOT/SYSTEM/BUSID-4:0:0-1/LDC]
< LinkedAllSliders=V1
< GammaChannelSelState=V0
---
> LastSelectedDevice=S1024:38280:4098:8759:6023|0[/PHP]

I saw that RandR was disabled on intrepid so replaced amdpcsdb(jaunty) with amdpcsdb(intrepid).
Then i rebooted to jaunty an activated Xinerama -> that worked for me.

I have an ATI HD 2600 XT and i'm not sure if this works for you (maybe you just need to deactivate RandR to get this working).

To copy/edit amdpcsdb  do it from a livecd (Jaunty must not boot before you copy/edit the file otherwise it will be overwritten)

---

### Post by Russian78 on 2009-05-04
> **hasplu said:**
> yep, I saw the answer too...

Is there any way downgrading the driver to 9.3 or 9.2? because "stick to 9.3", according to amd is maybe the only way for me to have working OS with X support.

The Dri does not recognize properly my rv360 and as a result everything works  like a nightmare :(

Sorry Hasplu, as you see, ATI/AMD will not give any reasonable answer to the mess, that they made, so the only hope is to wait for an upgrade of the radeon open source driver or to "vote with your pocket".

---

### Post by kingcharles1666 on 2009-05-04
This thread is still open on the ATI/AMD forum:

[http://forums.amd.com/game/messageview.cfm?catid=260&threadid=112796&enterthread=y](http://forums.amd.com/game/messageview.cfm?catid=260&threadid=112796&enterthread=y)

Post your expirences there, maybe it helps

---

### Post by scottkicksbutt on 2009-05-04
I searched for 3 days to get the ati/amd proprietary drivers functioning correctly but in the end determined it just would not work for my hardware.  I followed the this link to get the opens source drivers installed -  [https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD")

I have a Thinkpad T60p with the following video card: 01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5200]

compiz works just fine as well

---

### Post by 213374U on 2009-05-04
Glad I read through this post prior to upgrading. I'm still running Feisty Fawn due to the fact that it took me nearly a week to get everything up and stable with my ATI card. Compiz running and all. Seems every release since just has worse ATI support than the last.

This box will be staying on Feisty, no more upgrades for me.... at least until I get a new machine :)

---

### Post by edantes on 2009-05-04
I am still puzzled of why the "legacy" Catalyst 9.3 does not work with  Jaunty/Ubuntu 9.04.   In this page ATI says 

"Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4"

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

It builds for Jaunty without complaining:

sudo ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/jaunty

But on reboot, it says driver is incompatible.

Leave it to ATI the explaining of  why a 1 year old card is "Legacy", but the old driver IS supposed to work, isn't?

---

### Post by Russian78 on 2009-05-04
> **edantes said:**
> I am still puzzled of why the "legacy" Catalyst 9.3 does not work with  Jaunty/Ubuntu 9.04.   In this page ATI says 

"Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4"

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

It builds for Jaunty without complaining:

sudo ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/jaunty

But on reboot, it says driver is incompatible.

Leave it to ATI the explaining of  why a 1 year old card is "Legacy", but the old driver IS supposed to work, isn't?



As far as I know, the legacy driver 9.3 did not support version 1.6 of x server, which is only supported by driver version 9.4. Jaunty implements x server 1.6 and this must explane why 9.3 is not working in Jaunty - sad but true!

---

### Post by edantes on 2009-05-04
> **Russian78 said:**
> As far as I know, the legacy driver 9.3 did not support version 1.6 of x server, which is only supported by driver version 9.4. Jaunty implements x server 1.6 and this must explane why 9.3 is not working in Jaunty - sad but true!

Isn't the current version for X.Org X11R7.4?

 Catalyst 9.3 in the 03/29/2009 version lists 7.4 as supported.  What does the "1.6" version refer to?

---

### Post by Muchacho_Gasolino on 2009-05-04
My xserver-xorg package is 1:7.4~5ubuntu18
My xserver-xorg-core package is 2:1.6.0-0ubuntu14

Does Jaunty have to use the latest xorg? Is there a way to downgrade xorg and not lose other functionality?

By the way, I have my Thinkpad t43 with an ATI x300 running nicely using the open source drivers. My CPU does run a little high sometimes, but I never checked it while running 8.10 so I don't know if that is a new phenomenon. I haven't noticed a significant performance hit.

---

### Post by hockman5 on 2009-05-04
I reinstalled a fresh 9.04 for the third time (since the upgrade crashed). Desktop works but no very good, no compiz and some bad graphics. So I install the proprietery ATI Radeon driver. This is where the system crashes and will not display login, and mouse and keyboard freeze. The text screen in the background comes on three times for about a half a second each time then it is dead. The last line of the screen says "checking battery state" (I am not on a laptop). I am going to keep at this I guess and see if I can get it working.

---

### Post by edantes on 2009-05-04
> **Muchacho_Gasolino said:**
> My xserver-xorg package is 1:7.4~5ubuntu18
My xserver-xorg-core package is 2:1.6.0-0ubuntu14

Does Jaunty have to use the latest xorg? Is there a way to downgrade xorg and not lose other functionality?

By the way, I have my Thinkpad t43 with an ATI x300 running nicely using the open source drivers. My CPU does run a little high sometimes, but I never checked it while running 8.10 so I don't know if that is a new phenomenon. I haven't noticed a significant performance hit.

Does it run Googleearth?  It is usually the the first great divide.  3D OpenGL would be the next.

Without a /etc/xorg.conf, how do I know exactly what driver and parameters I am running?

---

### Post by dh003i on 2009-05-04
Hi all, I'm having similar problems, as I [documented here]("http://ubuntuforums.org/showthread.php?p=7190435#post7190435"). I upgraded without uninstalling the ATI drivers first...big mistake.

When rebooting after upgrade, all I saw was a blank screen, with a half inch square of random colors that appeared to be the cursor.

I uninstalled the properietary drivers, and adjusted my Xorg.conf accordingly. 

I still have problems: now after I login, I don't see window borders, can't open my KDE menu, and pretty much can't do anything except open a full-screen file-manager (Dolphin) window and navigate around.

What is going on here? (I was having some problems with Dolphin windows maximizing improperly before too). How can I fix this, and install the latest radeon drivers? I can't even do anything in KDE (and ATI's install method seems to rely on a GUI being present, which is awful).

Can I install the Catalyst 9.4 drivers soley from the command line? And how can I go about troubleshooting and fixing this buggy window behavior? (what log files should I look at; what could be wrong)?

---

### Post by psyced on 2009-05-05
Just got a fresh install of Jaunty.
My config from Hardy works except for Xinerama (as many others noted).

If I turn on Xinerama in xorg.conf I get a black screen upon going to the login screen. The Xinerama option in ATI Catalyst is also disabled..

ATI Radeon HD 2600XT.

> Can I install the Catalyst 9.4 drivers soley from the command line?That is what I did. Take a look at this page: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by lptr on 2009-05-05
Accidently I recently read in a magacine, that there are severe hitchups with Intel based graphics under 9.04. 

This morning my 8.04 box wants another kernel update (2.6.24-24) so I thought let me have a look into this part of forum to see if there are some known things I have to waiting for. 

Now I saw this thread read along until here and I am deeply concerned about Ubuntu. Fine, that booting time has been reduced dramatically. Fine that graphics performance will increase. But hey. What does this help, when I cannot rely on the base distro?

Having several ATIs round here. Some running the OS drivers for reliability reasons. Others don't. All having one common: They are pretty aged.

I understand that EOL support must be there. I understand that things must progress. But does it make sense to change everything under the hood, that not even Intel is able to deliver a solid working driver for their own chipsets? As far as I understood from the magacine article it is so, that nearly 70 percent of code in driver handles initialization. And as the ATI driver the Intel driver handles not only a handfull of chipsets. They - at Intel - say that as of the radical change nearly everything needs to be changed in driver itself. ESPECIALLY the initialization part. 

The OS driver things can be handled and debugged by kernel and X folks as open source part makes this possible. But for the closed source part it is nearly impossible to say what does work and what not. 

Again I am deeply concerned about the current situation. Is Mark still in the boat at Cannonical? Ok.  :arrow: Maybe it was his decision, to take this bold step - who knows.

---

### Post by hockman5 on 2009-05-05
> **scottkicksbutt said:**
> I searched for 3 days to get the ati/amd proprietary drivers functioning correctly but in the end determined it just would not work for my hardware.  I followed the this link to get the opens source drivers installed -  [https://help.ubuntu.com/community/RadeonHD]("https://help.ubuntu.com/community/RadeonHD")

I have a Thinkpad T60p with the following video card: 01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5200]

compiz works just fine as well

I tried to follow the directions there as well but they didn't work.
sudo apt-get --reinstall install libg11-mesa-glx comes up with nothing....
also it can't find libltd17-dev or libg11-mesa-dev

And when I try ./autogen.sh  I get an error saying that autoreconf not found.

So I am back to using the vanilla/default ati radeon driver that sucks....
Icons get messed up, curser gets weird too and no Compiz.

---

### Post by hockman5 on 2009-05-05
I got everything to work including compiz by following these directions...

[http://forum.compiz-fusion.org/showthread.php?t=6794&highlight=software+rasterizer](http://forum.compiz-fusion.org/showthread.php?t=6794&highlight=software+rasterizer)

---

### Post by psyced on 2009-05-05
> Icons get messed up, curser gets weird too and no Compiz.I've noticed cursor twitches as well, under the default driver.

---

### Post by loudog23 on 2009-05-06
hopefully, with all the thread and post about issues with video drivers they will see that they might have drop these drivers a little too soon.

I wish i could go on with jaunty, it's really nice and i find it a little smoother that 8.10 on my system. But since i have Xpress200, i'm stuck with Intrepid (or jaunty without 3d :( )

good day all

---

### Post by Freakeomi on 2009-05-06
I have a Dell E1505 with ATI graphics card. 
I originally tried to use Ubuntu 8.04 and 8.10 but both had lack of support for my wireless card, but detected my ATI X1300 Mobility Card.  When I upgraded to 9.04 I liked how it automatically found my wireless (which has been a long standing problem with Ubuntu), but I read that ATI no longer supports "older" cards.  

I tried using FGLRX, will screw up my graphics and give me a blank screen and I have to go into console to remove it.  

I've also tried using envyNG and manually trying to install drivers for 9.3 (which apparently is not supports with the  new version of xorg)

Compiz runs (using default drivers with 9.04), but I'm not sure how to test if it can run 3d programs properly.  Any ideas?

---

### Post by noizo on 2009-05-06
Hello everyone.

After reading all posts... i'm confused.
I have ATI Radeon Mobility Express X1100 integrated with my ASUS X51RL laptop. Is this is 200M chipset?
fglrxinfo gives me this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.8201 Release

While i was reading all info, i have assumed that i need to install 9.4 driver first, and then upgrade to Jaunty with desktop effects disabled in first place.

But when i went on AMD site for drivers, there is only 9.3 driver available for my card.
Since 9.3 do not support xorg 1.6 and there is no 9.4 driver for my card... wtf? Am i stuck on Intrepid forever?

As far as i remember my card was not compatible with opensource drivers, at least not in 100%.
Please advise me something. I'm not a gamer, i just use compiz and emerald themes.

Regards

---

### Post by inspired on 2009-05-06
I have a laptop with an ATI Mobility Radeon 9200.

When I upgraded wtih 9.04, video performance downgraded to something unusable. Watching movies in VLC was not an option... and windows took seconds to respond to minimising, etc. Running Firefox was really slow.

I tried to install the fglrx drivers following the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

I used version 9.3

That hosed my system. I then found out 8.4 (or something) was the last version to support the 9200 chip.

I uninstalled fglrx using a root command prompt in recovery mode. I also got dconf to reset the xorg file to the default.

After that my graphics performance is more or less back to how it was in Ubuntu 8.10. I get a reading of about 1700 fps when I test it. I have no idea what the fps was before... never had a reason to test it.

So something happened during my uninstalling of the proprietary drivers and/or the reset of the xorg.conf file.

Thought this info might help someone.

Jonathan


UPDATE
 I have done one test trying to watch a video file in VLC. Fine in a small window.. .but crap when I go full screen. Will do more tests and update with results here.

---

### Post by hasplu on 2009-05-07
Hi again :)
After 7 days of fighting with my Ati Radeon 9600XT (RV360), I finally managed to make it work with open source drivers (I gave up with fglrx - couldn't find a working solution for me).

Fowolling [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) I removed fglrx installed driver:

```
sudo apt-get remove --purge xorg-driver-fglrx
```


Than I manually delited everywhere fglrx presented on my system by 
```
dpkg -l '*fglrx*'
```
and
```
locate fglrx
```

And I mean everywhere. I don't know if it is wise or even necessary, but it worked for me.
After that I removed the installed ati druivers, because they ware a mess after my struggle with the PC and reinstall them, making sure there is nothing left from fglrx driver as well:

```
sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

I needed to reconfigure the xorg.conf file in order to use selected ati drivers. It is important to do this as ROOT, otherwise the Xserver does not use the manually configured xorg.conf after reboot of the system.
going as root:

```
sudo su
```
and executing 
```
dpkg-reconfigure xserver-xorg
```

Now is the funny part - to configure manually my xorg.conf file. Really helpful were this pages:

[http://dri.sourceforge.net/doc/DRIuserguide.html](http://dri.sourceforge.net/doc/DRIuserguide.html)
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

At the end it looks like this:

```
Section "Device"
	Identifier	"Radeon 9600"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"AccelMethod"	"EXA"
# XAA/EXA
	Option		"AcelDFS"	"0"
	Option		"AGPMode"	"8"
	Option		"GARTSize"	"512"
	Option		"EnablePageFlip"	"1"
	Option		"ColorTiling"	"1"
	Option		"RenderAccel"	"1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Radeon 9600"
EndSection

Section "Module"
	Load	"glx"
	Load	"dri"
EndSection

Section	"DRI"
    Group	"video"
    Mode	0666
EndSection
```

than rebooted and everything works like a charm - glxgears shows over 750 frames, which is enough for my needs and there is no problem with the video at all.

About the youtube .flv movies I discoverd, that the problem was with the installed swf player - uninstalled it, because conflicted with the already installed shockwave flash v.9, removed and the flash itself and installed the new shockwave flash 10.0.r22. And I can watch youtube or other web movies with no problem any more 
:guitar:

I want to say THANK YOU Russian 78 for the great assistance and the next beer is on me :)

---

### Post by eggplant37 on 2009-05-07
> **noizo said:**
> Hello everyone.

After reading all posts... i'm confused.
I have ATI Radeon Mobility Express X1100 integrated with my ASUS X51RL laptop. Is this is 200M chipset?
fglrxinfo gives me this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.8201 Release

While i was reading all info, i have assumed that i need to install 9.4 driver first, and then upgrade to Jaunty with desktop effects disabled in first place.

But when i went on AMD site for drivers, there is only 9.3 driver available for my card.
Since 9.3 do not support xorg 1.6 and there is no 9.4 driver for my card... wtf? Am i stuck on Intrepid forever?

As far as i remember my card was not compatible with opensource drivers, at least not in 100%.
Please advise me something. I'm not a gamer, i just use compiz and emerald themes.

Regards

Stay put until they figure out some kind of fix. I'm trying to patiently wait and would have reloaded this laptop with 8.10 if I wasn't so dependent upon it for work.

---

### Post by pedrofausto on 2009-05-07
I have ATI Technologies RS690M [Radeon X1200 Series] in my Toshiba Satellite A215
I've tried the open ati driver but wasn't good enougth for me.

Then, I removed every xserver-xorg-driver (intel, ati, radeonhd, sis, etc) and reinstalled only the radeon driver (NOT radeonhd) and it's dependencies and works fine for me :)

Less glitches and hangs.

---

### Post by ssri on 2009-05-08
at least this problem is garnering more publicity.


[http://blogs.computerworld.com/the_ubuntu_and_ati_blues](http://blogs.computerworld.com/the_ubuntu_and_ati_blues)

---

### Post by shrndegruv on 2009-05-08
> **ssri said:**
> at least this problem is garnering more publicity.


[http://blogs.computerworld.com/the_ubuntu_and_ati_blues](http://blogs.computerworld.com/the_ubuntu_and_ati_blues)

should have been entitled the Jaunty Fiasco.  

Seriously, this is bad.  If MS or Apple did something like this, the press would be all over it.  All I see is a bunch of ego-falating articles about how awesome ubuntu is....](*,)

---

### Post by blackSP on 2009-05-08
I agree. 9.04 should be called the **Gruesome Misanthrope**!

I'm now constantly holding my breath and stay away from any update coming through the update manager after 6 re-installs, countless black screens, sound going disappearing, hot-keys working randomly...

---

### Post by bangolio on 2009-05-08
I'm a bit confused here about whether my card is supported or not.
I guess I'm one of the "lucky" ones:
no general display problems or blank screens after upgrading to 9.04 but everything was running awful (menus would take 5 seconds to show etc) until I disabled compiz.
So now when I try to enable "Visual Effects" it fails.

I have ATI Mobility Radeon 3000 series and I'm not sure whether it's supposed to work or not, cant find it in the list of ATI cards.

Maybe one of the more advanced users could sum things up? which cards are supported and which arent, what's the cause of this problem etc

Thanks :)

---

### Post by apparle on 2009-05-08
> **bangolio said:**
> I'm a bit confused here about whether my card is supported or not.
I guess I'm one of the "lucky" ones:
no general display problems or blank screens after upgrading to 9.04 but everything was running awful (menus would take 5 seconds to show etc) until I disabled compiz.
So now when I try to enable "Visual Effects" it fails.

I have ATI Mobility Radeon 3000 series and I'm not sure whether it's supposed to work or not, cant find it in the list of ATI cards.

Maybe one of the more advanced users could sum things up? which cards are supported and which arent, what's the cause of this problem etc

Thanks :)
did you try the open source driver
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Once I modified the xorg.conf the desktop effecs in kubuntu (Kwin effects) were working fine for me.....just for the note I have Radeon Xpress 200 IGP

---

### Post by s3lekta on 2009-05-08
> **apparle said:**
> did you try the open source driver
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
Once I modified the xorg.conf the desktop effecs in kubuntu (Kwin effects) were working fine for me.....just for the note I have Radeon Xpress 200 IGP

3000 series work but terrible performance as per other users on this thread.  Problems such as slow minimising / maximizing, 
cpu / ram getting eaten up

bug reported here --> [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)

---

### Post by mihai.ile on 2009-05-08
So this means this year is not going to be the year of desktop linux??? oh my...

---

### Post by jgcamp99 on 2009-05-09
Here's where Linux may fail as a mainstream OS ? Before 3d eye candy, your video card really didn't matter with any of the OS's. ATi & nVidia will cut support for video cards. OS X & Windows, they don't change enough and that really means often enough for this to be as noticeable an issue.

For previous versions of ATi cards to have 3d eye candy, would Ubuntu need to support something like 8.04 (the LTS version) even longer, while letting the 6 month versions continue to develop as relatively stable versions of cutting edge ?

Linux has always been an older hardware systems saving OS. But it appears with this, the 3d video issues will make any system's video card obsolete. 

Before, one could upgrade video cards, but right now, anyone still trying to get by with AGP is obviously "shirt out of luck" for 9.04 and beyond ?

3d video effects, I raely used them, but being on 9.04 I still use basic video features, so the 3d desktop isn't as big an issue for me. But just feel that I'm shorted because emotionally I feel the video card (9600 XT) should at least be able to run the 3d desktop. I wouldn't expect gaming to be exceptional ? 

Just me or anyone else feel this way ?

---

### Post by ssri on 2009-05-09
This coming from bridgman (ATI/AMD rep on [_phoronix_]("http://www.phoronix.com/forums/showthread.php?t=15796&page=33"))

[quote="bridgman"]"All of this misses the point though. We're not saying "move to the open source drivers cause they run faster" (although they do tend to be faster for most users in everything but 3d), we're saying "these GPUs are moving to a reduced support model, and _rather than quarterly updates of the fglrx driver we believe that our users will be better served by the open source drivers in the same timeframe"_. Comparing fglrx to the open source drivers this month is missing the point -- on a reduced support schedule there wouldn't have been a driver update this month anyways. Comparing 3, 6, 9 or 12 months from now is what matters since that's when the quarterly update drivers would have happened."[/quote]

Does that mean ATI will not offer quarterly driver updates to their recent "legacy" cards?  Man, ATI is leaving more and more of its userbase up the creek without a paddle.

---

### Post by apparle on 2009-05-09
I am kind of happy ATI stopped the support. Now that they have stopped the support people will have no other option but to go for open source. So I think the deveopment of open source drivers will get a good boost...
Though it will cause problems initially but I think we will surely get stable opensource drivers after some time.
As the cards are declared legacy......will ATI release the documentation for them??
If that does happen the I am happy I am rid of fglrx

---

### Post by eggplant37 on 2009-05-09
> **apparle said:**
> I am kind of happy ATI stopped the support. Now that they have stopped the support people will have no other option but to go for open source. So I think the deveopment of open source drivers will get a good boost...
Though it will cause problems initially but I think we will surely get stable opensource drivers after some time.
As the cards are declared legacy......will ATI release the documentation for them??
If that does happen the I am happy I am rid of fglrx

Well, I'll admit when I saw ATi release development specs for OpenGL on their RadeonHD line this week, the R600 & R700 chip lines, I was pretty taken aback. Let's hope that they'll release specs on the rest of these chips, i.e., the Radeon Xpress 200M that's got me preparing to reload 8.10 so that I can get some gaming done on this laptop.

---

### Post by haneya on 2009-05-10
Hi, I dont know if its ok to post here , but having the same issue with ati x1600 and jaunty .

I know that ati dropped the support for old models cards , but I guess I had to make sure , I installed ati driver and of course it didnt work , so I removed it then the problem begins = video frezz using mplayer and X restart while using Compiz .

I followed this tutorial [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver") to remove fglrx completely but still having the same issue..

I dont know is there any thing else to do to improve the performance and fix these issue with compiz and video playing , or its not because of fglrx installation and every body suffer from it. 
> output of locate fglrx
/etc/X11/xorg.conf.fglrx-0
/usr/share/app-install/desktop/fglrx-driver.desktop
/usr/share/apport/package-hooks/source_fglrx-installer.py
/usr/share/jockey/handlers/fglrx.py
/usr/share/jockey/handlers/fglrx.pyc
/var/cache/jockey/fglrx.oldconf


> output of dpkg -l '*fglrx*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pn  fglrx-amdcccle <none>         (no description available)
un  fglrx-control  <none>         (no description available)
un  fglrx-control- <none>         (no description available)
un  fglrx-driver   <none>         (no description available)
pn  fglrx-kernel-s <none>         (no description available)
pn  fglrx-modalias <none>         (no description available)
un  xfree86-driver <none>         (no description available)
pn  xorg-driver-fg <none>         (no description available)


xorg log > 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux anas-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 11 15:53:00 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc M56P [Radeon Mobility X1600] rev 0, Mem @ 0xd0000000/268435456, 0xcfef0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeon from file name radeon.ids
(==) Matched radeon for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
	ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
	ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
	ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
	ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
	ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
	ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
	ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
	ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD Graphics, ATI Radeon Graphics,
	ATI Mobility Radeon HD Graphics, ATI Mobility Radeon Graphics,
	ATI Radeon Graphics
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): TOTO SAYS 00000000cfef0000
(II) RADEON(0): MMIO registers at 0x00000000cfef0000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Mobility Radeon X1600" (ChipID = 0x71c5)
(WW) RADEON(0): R500 support is under development. Please report any issues to [email]xorg-driver-ati@lists.x.org[/email]
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1179 SubsystemID: 0xff10
	IOBaseAddress: 0x2000
	Filename: BR21699.BIN 
	BIOS Bootup Message: 

M56P BR#21699 BIOS 400E/380M                                                


(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x1000000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x1000000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 400000
(II) RADEON(0): Default Memory Clock: 380000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1100000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.29.0
(==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1600
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 110000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 400.000000, mclk: 380.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=110000; xclk=40000
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 68940
HBlank: 128, HOverPlus: 16, HSyncWidth: 48
VBlank: 16, VOverPlus: 1, VSyncWidth: 3
(II) RADEON(0): Skipping TV-Out
encoder: 0x15
encoder: 0xf
encoder: 0x13
(II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e60
(II) RADEON(0): Port1:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVTM1
  DDC reg: 0x7e50
(II) RADEON(0): Port2:
  XRANDR name: DVI-0
  Connector: DVI-I
  DFP1: INTERNAL_KLDSCP_TMDS1
  DDC reg: 0x7e40
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 0
(II) RADEON(0): I2C device "LVDS:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3333600000000
(II) RADEON(0): 	000f0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101ee1a0080502010301030
(II) RADEON(0): 	13004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026402000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	004c544e31353458332d4c30360a0070
finished output detect: 1
(II) RADEON(0): I2C device "DVI-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3333600000000
(II) RADEON(0): 	000f0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101ee1a0080502010301030
(II) RADEON(0): 	13004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026402000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output DVI-0 disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1280x800
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit d0000000 0 0
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 262112 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00640000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00644000
(II) RADEON(0): Will use 6400 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 32 kb for PCI GART at offset 0x0fff8000
(II) RADEON(0): Will use 6400 kb for back buffer at offset 0x00648000
(II) RADEON(0): Will use 6400 kb for depth buffer at offset 0x00c88000
(II) RADEON(0): Will use 120832 kb for textures at offset 0x012c8000
(II) RADEON(0): Will use 122048 kb for X Server offscreen at offset 0x088c8000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 32768 kB allocated with handle 0xf8509000
(II) RADEON(0): [pci] ring handle = 0xf8509000
(II) RADEON(0): [pci] Ring mapped at 0xb77bd000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf860a000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb77bc000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf860b000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xa751e000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf880b000
(II) RADEON(0): [pci] GART Texture map mapped at 0xa589e000
(II) RADEON(0): [drm] register handle = 0xcfef0000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffd000 0xdfffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xdfffd000 is: 0xdfffd000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0xffffffc0
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffd000 0xdfffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 1
(II) EXA(0): Offscreen pixmap area of 124977152 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Set up textured video
Output CRT1 disable success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x800 - 1408 816 10
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffd000 0xdfffd000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
freq: 68940000
best_freq: 68940000
best_feedback_div: 383
best_ref_div: 10
best_post_div: 15
(II) RADEON(0): crtc(0) Clock: mode 68940, PLL 68940
(II) RADEON(0): crtc(0) PLL  : refdiv 10, fbdiv 0x17F(383), pdiv 15
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output digital setup success
Output LCD1 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Output CRT1 disable success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "UseFBDev" is not used
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us,ara"
(**) AT Translated Set 2 keyboard: xkb_layout: "us,ara"
(**) Option "xkb_variant" ","
(**) AT Translated Set 2 keyboard: xkb_variant: ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(**) AT Translated Set 2 keyboard: xkb_options: "grp:alt_shift_toggle,grp_led:scroll"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us,ara"
(**) Video Bus: xkb_layout: "us,ara"
(**) Option "xkb_variant" ","
(**) Video Bus: xkb_variant: ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(**) Video Bus: xkb_options: "grp:alt_shift_toggle,grp_led:scroll"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Genius Wireless Mouse
(**) Genius Wireless Mouse: always reports core events
(**) Genius Wireless Mouse: Device: "/dev/input/event6"
(II) Genius Wireless Mouse: Found 3 mouse buttons
(II) Genius Wireless Mouse: Found x and y relative axes
(II) Genius Wireless Mouse: Configuring as mouse
(**) Genius Wireless Mouse: YAxisMapping: buttons 4 and 5
(**) Genius Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius Wireless Mouse" (type: MOUSE)
(**) Genius Wireless Mouse: (accel) keeping acceleration scheme 1
(**) Genius Wireless Mouse: (accel) filter chain progression: 2.00
(**) Genius Wireless Mouse: (accel) filter stage 0: 20.00 ms
(**) Genius Wireless Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event8"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3333600000000
(II) RADEON(0): 	000f0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101ee1a0080502010301030
(II) RADEON(0): 	13004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026402000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3333600000000
(II) RADEON(0): 	000f0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101ee1a0080502010301030
(II) RADEON(0): 	13004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026402000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3333600000000
(II) RADEON(0): 	000f0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101ee1a0080502010301030
(II) RADEON(0): 	13004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026402000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3333600000000
(II) RADEON(0): 	000f0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101ee1a0080502010301030
(II) RADEON(0): 	13004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026402000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3333600000000
(II) RADEON(0): 	000f0103802115780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101ee1a0080502010301030
(II) RADEON(0): 	13004bcf100000190000000f00000000
(II) RADEON(0): 	00000000002387026402000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
invalid output device for dac detection
Unhandled monitor type 0

Thanks.

---

### Post by Noiano on 2009-05-10
As mentioned here [http://ubuntuforums.org/showthread.php?p=7158165#post7158165](http://ubuntuforums.org/showthread.php?p=7158165#post7158165) I tried an upgrade to jaunty and I got these strange squares around text (see attachment).
I also tried a clean install and I got the same thing. I tried vesa and I get a black screen.
In conclusion:
[LIST]
[*]no opensource driver (strange white squares)
[*]no vesa driver (black screen)
[*]no proprietary driver
[/LIST]

I was forced to switch to opensuse 11.1. I do want to switch back to ubuntu. What can I do?:confused:

---

### Post by ssri on 2009-05-11
hmmmm, I do not know if anyone mentioned this, but some intrepid soul (pun not intended) compiled xserver 1.5.2 for Jaunty, the version that works with the proprietary Catalyst 9.3 drivers for "legacy" cards.  Now, I have not tried it myself since I've been busy lately.  I would strongly advise someone to use a test system or partition before replacing their Jaunty default version.  Also, you will have to lock synaptic from reverting it back to 1.6.  If one is successful, I do not know how the stable the system is going to be afterwards.  Just passing the info along, that's all. 8-[

[http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)

---

### Post by Graham_ on 2009-05-11
> **apparle said:**
> I am kind of happy ATI stopped the support. Now that they have stopped the support people will have no other option but to go for open source. So I think the deveopment of open source drivers will get a good boost...
Though it will cause problems initially but I think we will surely get stable opensource drivers after some time.
As the cards are declared legacy......will ATI release the documentation for them??
If that does happen the I am happy I am rid of fglrx

Providing legacy support to real old cards is one thing, but to make cards that are only a year old legacy?  With all the different cards out there, I wonder if the statistics will show the majority of ATI customers are now branded (unsupported) legacy customers?

---

### Post by apparle on 2009-05-11
I think we should put a poll
I agree with you
> I wonder if the statistics will show the majority of ATI customers are now branded (unsupported) legacy customers?

---

### Post by Dearhell on 2009-05-12
Many people for sure has this problem, you only have to see this post to notice that.

---

### Post by Silent Warrior on 2009-05-12
Huh, no wonder upgrading was such a hassle... I guess I really should've investigated this before mindlessly upgrading, noticing that 9.3 is the last driver I can use in Windows. :oops: Oh well. Good thing I don't have a fit over losing Compiz, but I was hoping to get some VegaStriking done...

[Mourning X1900-user...]

---

### Post by completenerd on 2009-05-12
during first install of 9.04 ubuntu says that some hardware drivers are not supported,continue on and further down the line comes a question if you want to use propriety hardware drivers:mark the box to say yes ,continue on toend of install,reboot system and hey presto everything works,even my wireless.All running on a 5 year old Acer with yes an ATI card:)

why windows when there's Linux

---

### Post by onecosmos on 2009-05-13
Hi all

For those people that have ATI HD4550 cards and thinking of upgrading to 9.04, the following information might be of help.
When i first tried to install the new version i came on a scrambled screen and sometimes a back screen (even when booting from the live CD).
The easy way around this is by doing the following

When the installer comes up, before you press enter and continue with the install, press F4 and select the graphics safe option (this works either on proper install and on Live CD).
After going through with the install process, you can download the proper drivers from ATI-AMD website for the Linux OS.
There is a pdf with instructions on how to install the drivers, on the ATI - AMD site.

Catalyst centre seems operational and the drivers from ATI seem to work fine.

---

### Post by bangolio on 2009-05-14
didnt work here, mobility radeon 3400

---

### Post by onecosmos on 2009-05-14
Did you load the graphics safe option?

---

### Post by ales on 2009-05-16
I upgraded from 8.10 to 9.04 with my x800. Using opensource driver. No 3d working. but mostly i don't play so not a big deal for me. But i would welcome the possibility to use 3d, enemy territory etc.

Anyway, no problems with the upgrade. Just downloaded, installed and worked.

---

### Post by mo0osah on 2009-05-17
I bought a gateway C140XL a year ago that came with ATI Radeon 2300 HD.  Needless to say, I'm very disappointed about not being able to update to 9.04 and get 3d support ....  :mad:

---

### Post by starnich on 2009-05-17
In short, the ATI drivers are crap, had major problems since upgrading, left with a system that gives me a headache after half an hour because of the permenant 60hz refresh rate problem that nobody seems to have an answer for.

Had to work on the system for 4 hours just to get it to boot up after the upgrade.

May have to crawl back to windows :(((((

---

### Post by bangolio on 2009-05-18
After updating the system yesterday, the problem has been solved.
I'm a happy man once again. :D

---

### Post by Eruaran on 2009-05-19
I have installed a HD 3850 in my system and I have to say I am bitterly disappointed.

I have been using GNU/Linux in earnest since February 2005 and this is the first time that I have been so unhappy that, though it really IS painful, I've actually considered moving back to Windows just so that I can use the hardware that I want to use.

The drivers, proprietary or not, that are being offered to users in the Ubuntu repository are GARBAGE. They DO NOT WORK. What you get if you install them is a completely unusable system.

If anyone wants to flame or lecture me please consider this: When people cannot use their hardware - That's an absolute showstopper for just about anyone. People get very upset, it's game over. I really don't care what you want to tell me about the latest xorg and driver issues. Its 2009. This should not be happening.

If the older stuff works and the new stuff doesn't, you keep offering people what works until the problems with the new are worked out. As it is, what I was offered broke my system.

---

### Post by shrndegruv on 2009-05-19
> **Eruaran said:**
> I have installed a HD 3850 in my system and I have to say I am bitterly disappointed.

I have been using GNU/Linux in earnest since February 2005 and this is the first time that I have been so unhappy that, though it really IS painful, I've actually considered moving back to Windows just so that I can use the hardware that I want to use.

The drivers, proprietary or not, that are being offered to users in the Ubuntu repository are GARBAGE. They DO NOT WORK. What you get if you install them is a completely unusable system.

If anyone wants to flame or lecture me please consider this: When people cannot use their hardware - That's an absolute showstopper for just about anyone. People get very upset, it's game over. I really don't care what you want to tell me about the latest xorg and driver issues. Its 2009. This should not be happening.

If the older stuff works and the new stuff doesn't, you keep offering people what works until the problems with the new are worked out. As it is, what I was offered broke my system.

I feel exactly the same way.  I hope Canonical learns something and will warn users in the future in big bold letters if an upgrade will break their system.  It is not ideal to tell ati users that they might want to hold off on updating, but its better than not making that clear and breaking everything.  

That said, does the catalyst 9.5 drivers work better than the 9.4?

---

### Post by LinuxTAd on 2009-05-19
I have had hits and misses on qty. 2 ATI HD3870's running. My main issue is I do not want mirrored. Got that fixed... I am not running the big desktop but I am able to drag icons and shortcuts files etc to the secondary monitor form my main monitor. I cannot however drag open windows over to my secondary monitor.

Xinematic is a show stopper and have had 0 luck getting that going.

I am just doing trial and error at the moment being a relatively new to Ubuntu, I also am running 9.04, and manually loaded the drivers from ATI. Here is my xorg.conf as currently running:

> 

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

#Section "ServerFlags"
#    Option        "Xinerama" "on"
#    Option        "randr" "on"
#EndSection
#doesn't work

#Section "ServerFlags"
#    Option        "Xinerama" "true"
#EndSection
#doesn't work

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "OverlayOnCRTC2" "1"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

#######################################

##For G5 Gaming mouse
Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "auto"
    Option "Buttons" "7" # Tells X11 the number of buttons on the mouse
    Option "ZAxisMapping" "4 5" # Tells X11 which buttons to use for scrolling, 4 is up, 5 is down
    Option "ButtonMapping" "1 2 3 6 7 4 5"
EndSection


---

### Post by redjam on 2009-05-21
Hi,

So I have upgraded to 9.04 and now I have no display and thus my machine is broken.

I have an Dell Inspiron 530n with ATI Radeon HD 2400 PRO graphics card; is there any chance that putting in a new card would fix the problem?

If so, what should I buy? Needs to be relatively inexpensive.

If not, what are the other options? Fresh install of 8.* is one but that means loosing all the work I've put in setting it up over the past year.

Is it worth waiting to see if a solution emerges in the next few days? (I can't wait much longer than that).

Thanks.

---

### Post by alliance1975 on 2009-05-21
HP DV5000 w/ATI radeon xpress 200m. recent upgrade resulted in poor performance of video card. No apparent solutions. Very disapointing. Even more disapointing is that I see no posts with any plans for how to remedy. Will ATI make specs available to open source drivers, or do we just sit and hope?

---

### Post by bangolio on 2009-05-21
> **bangolio said:**
> After updating the system yesterday, the problem has been solved.
I'm a happy man once again. :D

am i the only one here that the problem was solved for him during that update?

I've had the jaunty-ati issue since upgrading to jaunty, then after a little while I updated some packages using the update-manager (Qt 4 or something, it had OpenGL in the description) and everything was back to normal :D

any info on this?

---

### Post by Chester87 on 2009-05-21
This is what i did;

Download the latest ATI driver from the ati website

Mine was ati-driver-installer-9-5-x86.x86_64.run downloaded it to 

Now open your terminal Applications>Accessories>Terminal

Go to your download folder

```
cd Desktop
sudo chmod +x ati-driver-installer-9-5-x86.x86_64.run
sudo ./ati-driver-installer-9-5-x86.x86_64.run
 
```

Follow the on-screen instructions

When you have multiple monitors like in my setup, go to Preferences > Display

Put in your correct display configurations and click apply.

Log-out and log back in. And your done. I've got a HD3450.

Hope this helps for people with multiple screens.

UPDATE: I turned off Compiz, because with it I couldn't even play a *.mkv full HD video file without crashing Ubuntu.
UPDATE2: If you use the ATI config tool in Applications>Ati Catalyst. Be careful that you don't break your ubuntu, if you somehow do break it using catalyst. Boot in safe-mode, and type the following line in prompt: aticonfig --initial

---

### Post by farlander762 on 2009-05-21
Dang.

I set up a friend of mine running 9.04 64 bit last week.  Today he bought two beautiful LG's to plug into it.  Knowing that graphics can be "funny" in Linux I wrote down his info when I set it up.  It is an x300 RV370 card.  I guess I'll talk him into a nVidia card.  They are easy to set up.  I have no experience with ATI stuff.

---

### Post by peakshysteria on 2009-05-22
> **farlander762 said:**
> Dang.

I set up a friend of mine running 9.04 64 bit last week.  Today he bought two beautiful LG's to plug into it.  Knowing that graphics can be "funny" in Linux I wrote down his info when I set it up.  It is an x300 RV370 card.  I guess I'll talk him into a nVidia card.  They are easy to set up.  I have no experience with ATI stuff.

Might just work out of the box. Just see under --> Screens and Graphics and Display preferences. Let us know how it works out.

---

### Post by sonofusion82 on 2009-05-23
my display was corrupted too after the upgrade, but i just ssh into my machine then typed "aticonfig --initial" to set a default configuration into xorg.conf... after that, everything was fixed... desktop effects for KDE4 works fine too..

---

### Post by Ethelbert2 on 2009-05-26
[COLOR="DarkGreen"][FONT="Verdana"]I'm bemused by much of this discussion though it seems to be the place to solve my problem. But the wrangling is putting me off Linux again.

I just started trying it again after two years. Before, I finally gave up because Linux would not find wifi cards and modems ( though I did battle my way through to getting them going, it took so much time), and more importantly there is software I can't do without in Windows eg Photoshop, word recognition, certain datebases like IBM's Approach). But I really would like it to be usable.

Immediately I have hit problems. This time the first distribution I tried was Ubuntu as so many articles recommend it for ease and user friendliness (and I used it before). It would not even start up after the loading sequence - which it seems now from this thread, is because i have a Radeon 7000 video card.

Too old a card you might say or "get a new one" as some contributors glibly say.  But **the point** of using Linux initially was to make an *old* computer run - because I wanted to try Linux but not on anything new for the time being. It is a Pentium 3 450Hx  - got lots of RAM (512MB). I am not going to spend more money on it - I want to salvage it.

I have spent two weeks now trying various flavours (There are too many to try all) and including every type of Ubuntu. Many of these give me blank or meaningless coloured jagged lines displays and not even a way to go into the command line. Some give just a blank display when log in is due.

A few work ( a bit) like Damn Small and Absolute, though neither found the network card let alone the wifi.  

They seemed to have older kernels, I worked out, so I decided to try Xubuntu 8.04 instead of the latest.

Finally I had found one that worked, and I quite like it,  although even then it did not find the wifi card (rtl8185) or the modem. (Much Googling and battling later I discovered the relatively simple GUI version of Ndiswrapper exists and solved the wifi anyway with a Windows driver.) Still working on the modem.

I upgraded then to 8.10 with trepidation but it works (the newer of the kernel versions listed in Grub too).

But I would obviously like to use 9.04 and dare not. (So I seem to be stuck with Open Office 2.4 for example and not the much better 3.1)

Now I come across this row and argument thread and realise my problem is bigger than I thought.  It is seriously making me rethink using Linux at all.

The best OS so far for this old computer to tell the truth has been Win XP SP3 which just handles everything ( or there is a disc to run that will do so).  I don't imply by that that I don't understand the problems, just what is the case.

But I was sold on, persuaded, by forums and articles that Linux is the system that will help with older computers and make them perform better.

But quite frankly this whole row here - and the continuing wifi problem etc, just argues otherwise. I constantly read about how Linux is so much less broken and more supportive with drivers etc than Windows. Just not true is it?

I am not a computer buff, I don't want to learn lots of stuff for the hell of it, I just want to use a computer. I don't mind learning what I need and there is some satisfaction in finding a solution to some things but don't enjoy endless arcane discussions as above in this thread.  I do like the idea of Linux and open source etc,

I don't belittle the huge effort so many people put in but while this 9.04 type thing happens you will not convince me to switch however. I am tempted to leave off again and have another go perhaps in another two years though not for the moment. I'll see what happens in the next few weeks.

And I would like to try a 64 bit version on my main computer.

But as a mainstream desktop system Linux is a far off dream it seems to me.

(One other point - Windows of course when it produces a new system, requires advanced hardware, and you cannot run 7 or Vista on older stuff. So it may be that it is understood later versions of Ubuntu will not do for older computers. But you can run XP on really quite old machines - and on that OS you can then run virtually all the newer software versions).

If I have to stick with 8.10 Xubuntu why can I not still use the latest Open Office etc - which it seems I cannot.)?

Excuse the long contribution - I was really just trying to work out how to get 9.04 usable.
[/FONT][/COLOR]

---

### Post by ssri on 2009-05-26
> **Ethelbert2 said:**
> [COLOR="DarkGreen"][FONT="Verdana"]
If I have to stick with 8.10 Xubuntu why can I not still use the latest Open Office etc - which it seems I cannot.)?

Excuse the long contribution - I was really just trying to work out how to get 9.04 usable.
[/FONT][/COLOR]

The last section of this post is a little OT.  If you want to install the newest version of Openoffice, then install it using dpkg from here...

[http://ubuntuforums.org/showthread.php?t=1000861](http://ubuntuforums.org/showthread.php?t=1000861)

Okay, now recommence wailing against ATI ;)

---

### Post by ssri on 2009-05-26
> **redjam said:**
> Hi,

So I have upgraded to 9.04 and now I have no display and thus my machine is broken.

I have an Dell Inspiron 530n with ATI Radeon HD 2400 PRO graphics card; is there any chance that putting in a new card would fix the problem?

If so, what should I buy? Needs to be relatively inexpensive.

If not, what are the other options? Fresh install of 8.* is one but that means loosing all the work I've put in setting it up over the past year.

Is it worth waiting to see if a solution emerges in the next few days? (I can't wait much longer than that).

Thanks.

If fglrx is installed from the repos by mistake, make sure you have an internet connection, boot into the terminal and type:

sudo apt-get remove --purge fglrx*

or use in the uninstall script from ATI, /usr/share/ATI

sudo sh ./uninstall.sh

then, to get the opensource drivers back:

sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa mesa-utils
sudo apt-get install --reinstall xorg xserver-xorg xserver-xorg-core

For Radeon (old ATI cards - R5xx):
sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-radeon

For RadeonHD (R5xx - above):
sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-radeonhd

Bring back the default xorg.conf:
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by peakshysteria on 2009-05-28
Installed Jaunty on an old laptop with P3 and ATI 9000 card for my five year old son yesterday. All seems to be good out of the box when it comes to 2d games and such. No 3d.

---

### Post by mr_raider on 2009-05-31
Replaced my x1900xt with a 9800gt. Problem solved.

---

### Post by HeavyMetaler on 2009-06-04
I have an ATI 2400HD XT and had issues getting fglrx to work properly with BigDesktop. 

Adding these lines in /etc/ati/amdpcsdb allowed me to get back big desktop mode without borking everything up. 
```

EnableRandR12=SFALSE
MultiviewXineramaNo3D=V1
DesktopSetup=Shorizontal

```
 The Xorg.conf that came from "aticonfig --inital -f" didn't work for me either and I had to revert to a different one.  This is using the fglrx package that came from ati's website.  Full compiz/everything working with big desktop as opposed to two separate X screens.
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

For fun I will post my entire amdpcsdb in case it helps someone else get things working.
```

AMDPCSDBV1
[AMDPCSROOT/SYSTEM/MCIL]
PXACAutoSwitch=V0
PXDCAutoSwitch=V0
CVRULE_CUSTOMIZEDMODESENABLED=V1
DFP_AddHDTVPixelFormats=V2
DALLinuxSupport=V1
DALNonStandardModesBCD=R140010500000006017921344000000601800144000000060185613920000006016001200000000601280076800000060144009000000006012800960000000601680105000000060
DALRULE_ADDNATIVEMODESTOMODETABLE=V1
DALRULE_ALLOWMONITORRANGELIMITMODESCRT=V0
DALRULE_DYNAMICMODESUPPORT=V1
DALRULE_GetLCDFakeEDID=V1
DALRULE_GetTVFakeEDID=V1
DALRULE_NOFORCEBOOT=V1
DALRULE_POWERPLAYDISREGARDDISPLAY=V1
DALRULE_RESTRICTDISPLAYSBASEDONPANELRES=V0
DALRULE_REGISTRYACCESS=V1
GCORULE_FlickerWA=V1
GCORULE_LCDValidatePixelClkOnly=V1
GXOM5XDisableLaneSwitch=V1
R6LCD_RETURNALLBIOSMODES=V1
TVEnableOverscan=V1
UvdEnabled=V1
Gxo50HzTimingSupport=V1
Gxo24HzTimingSupport=V1
Gxo2530HzTimingSupport=V1
DALLastSelected=V24
DALLastConnected=V24
DALLastTypes=V157
DALObjectData0=R01010001010001010001010001020001020003010203010201040001040003010403010401020001020003010203010201080001080003080103080103080203080203080103080103080403080403080103080103080203080203080103080101100001100003100103100103100203100203100103100103100403100403100103100103100203100203100103100103081003081003081003081003081003081003081003081003081003081003081003081003081003081003081003081001010001010001010000000001020000000001010002000201040000000001010002000401020000000001010002000201080000000001080002000101080002000201080002000101080002000401080002000101080002000201080002000101100000000001100002000101100002000201100002000101100002000401100002000101100002000201100002000101080002001001080002001001080002001001080002001001080002001001080002001001080002001001080002001000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALObjectData1=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALSelectObjectData0=R01010001010001010001010001020001020003010203010201040001040003010403010401020001020003010203010201080001080003080103080103080203080203080103080103080403080403080103080103080203080203080103080101100001100003100103100103100203100203100103100103100403100403100103100103100203100203100103100103081003081003081003081003081003081003081003081003081003081003081003081003081003081003081003081001010001010001010000000001020000000001010002000201040000000001010002000401020000000001010002000201080000000001080002000101080002000201080002000101080002000401080002000101080002000201080002000101100000000001100002000101100002000201100002000101100002000401100002000101100002000201100002000101080002001001080002001001080002001001080002001001080002001001080002001001080002001001080002001000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALSelectObjectData1=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALCurrentObjectData=R010800020010
DALR6 DFP_MaxModeInfo=R00000000900600001A040000000000004B000000
DALR6 DFPI 2_MaxModeInfo=R00000000900600001A040000000000004B000000
DAL_DFP2ColorTemperatureSourceAC10403C=R0200000064190000
DAL_DFPColorTemperatureSourceAC10403C=R0200000064190000
AsicOnLowPower=V0
[AMDPCSROOT/SYSTEM/2ID-1002-791E-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7941-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-796E-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9610-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9611-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9614-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7124-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7105-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-710f-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-712e-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-712f-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-710e-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7125-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7104-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-940b-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-940a-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-940f-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9447-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7152-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7172-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7173-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-7153-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71d2-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71f2-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71fa-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71da-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-728c-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-72ac-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-95cc-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-958d-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-958c-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9511-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-949c-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-949f-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-949e-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9444-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9446-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9456-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-71bb-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-719b-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-95cd-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-95ce-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-95cf-0/DDX]
MultiviewEnabled=V1
[AMDPCSROOT/SYSTEM/2ID-1002-3151-0/DDX]
MultiviewEnabled=V1
ForceMultiHead=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9452-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/2ID-1002-9519-0/DDX]
MultiviewEnabled=V1
MultiviewHeterogeneous=V1
[AMDPCSROOT/SYSTEM/DDX]
OGLFMTA2R10G10B10Enable=V0
EnableRandR12=SFALSE
MultiviewXineramaNo3D=V1
DesktopSetup=Shorizontal
[AMDPCSROOT/SYSTEM/DDX/RECENTMODE]
EnableRestore=V1
[AMDPCSROOT/SYSTEM/DDX/RECENTMODE/SCREEN00]
Width=V3360
Height=V1050
Refresh=V60
[AMDPCSROOT/SYSTEM/LibXUtil/Display1]
Map=V8
Enable=V1
[AMDPCSROOT/SYSTEM/LDC]
LastViewedPage=SDisplay Manager
DisplayPopupState=V0
HelpDisabled=V0
DP_MSG_FLAG=V0
WarningDlgDisabled=V0
LastSelectedDevice=S256:38081:4098:3330:4136|4
[AMDPCSROOT/SYSTEM/BUSID-1:0:0-0/MCIL]
DAL_ACEspectReady=V0
DALLastConnected=V8
DALLastTypes=V157
DALObjectData0=R01000000010000000000000001000000010000000000000001000000010000000000000001000000010000000000000001000000020000000000000001000000020000000000000003000000010000000200000003000000010000000200000001000000040000000000000001000000040000000000000003000000010000000400000003000000010000000400000001000000020000000000000001000000020000000000000003000000010000000200000003000000010000000200000001000000080000000000000001000000080000000000000003000000080000000100000003000000080000000100000003000000080000000200000003000000080000000200000003000000080000000100000003000000080000000100000003000000080000000400000003000000080000000400000003000000080000000100000003000000080000000100000003000000080000000200000003000000080000000200000003000000080000000100000003000000080000000100000001000000100000000000000001000000100000000000000003000000100000000100000003000000100000000100000003000000100000000200000003000000100000000200000003000000100000000100000003000000100000000100000003000000100000000400000003000000100000000400000003000000100000000100000003000000100000000100000003000000100000000200000003000000100000000200000003000000100000000100000003000000100000000100000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000001000000010000000000000001000000010000000000000001000000010000000000000000000000000000000000000001000000020000000000000000000000000000000000000001000000010000000000000002000000000000000200000001000000040000000000000000000000000000000000000001000000010000000000000002000000000000000400000001000000020000000000000000000000000000000000000001000000010000000000000002000000000000000200000001000000080000000000000000000000000000000000000001000000080000000000000002000000000000000100000001000000080000000000000002000000
DALObjectData1=R0000000002000000010000000800000000000000020000000000000001000000010000000800000000000000020000000000000004000000010000000800000000000000020000000000000001000000010000000800000000000000020000000000000002000000010000000800000000000000020000000000000001000000010000001000000000000000000000000000000000000000010000001000000000000000020000000000000001000000010000001000000000000000020000000000000002000000010000001000000000000000020000000000000001000000010000001000000000000000020000000000000004000000010000001000000000000000020000000000000001000000010000001000000000000000020000000000000002000000010000001000000000000000020000000000000001000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000
DALCurrentObjectData=R010000000800000000000000020000000000000010000000
DALR6 DFP_MaxModeInfo=R00000000900600001A040000000000004B000000
DALR6 DFPI 2_MaxModeInfo=R00000000900600001A040000000000004B000000
DAL_DFP2ColorTemperatureSourceAC10403C=R0200000064190000
DAL_DFPColorTemperatureSourceAC10403C=R0200000064190000
AsicOnLowPower=V0
DALSelectObjectData0=R01000000010000000000000001000000010000000000000001000000010000000000000001000000010000000000000001000000020000000000000001000000020000000000000003000000010000000200000003000000010000000200000001000000040000000000000001000000040000000000000003000000010000000400000003000000010000000400000001000000020000000000000001000000020000000000000003000000010000000200000003000000010000000200000001000000080000000000000001000000080000000000000003000000080000000100000003000000080000000100000003000000080000000200000003000000080000000200000003000000080000000100000003000000080000000100000003000000080000000400000003000000080000000400000003000000080000000100000003000000080000000100000003000000080000000200000003000000080000000200000003000000080000000100000003000000080000000100000001000000100000000000000001000000100000000000000003000000100000000100000003000000100000000100000003000000100000000200000003000000100000000200000003000000100000000100000003000000100000000100000003000000100000000400000003000000100000000400000003000000100000000100000003000000100000000100000003000000100000000200000003000000100000000200000003000000100000000100000003000000100000000100000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000003000000080000001000000001000000010000000000000001000000010000000000000001000000010000000000000000000000000000000000000001000000020000000000000000000000000000000000000001000000010000000000000002000000000000000200000001000000040000000000000000000000000000000000000001000000010000000000000002000000000000000400000001000000020000000000000000000000000000000000000001000000010000000000000002000000000000000200000001000000080000000000000000000000000000000000000001000000080000000000000002000000000000000100000001000000080000000000000002000000
DALSelectObjectData1=R0000000002000000010000000800000000000000020000000000000001000000010000000800000000000000020000000000000004000000010000000800000000000000020000000000000001000000010000000800000000000000020000000000000002000000010000000800000000000000020000000000000001000000010000001000000000000000000000000000000000000000010000001000000000000000020000000000000001000000010000001000000000000000020000000000000002000000010000001000000000000000020000000000000001000000010000001000000000000000020000000000000004000000010000001000000000000000020000000000000001000000010000001000000000000000020000000000000002000000010000001000000000000000020000000000000001000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000010000000800000000000000020000000000000010000000
DALInstallFlag=V1
DALR6 DFPI 2640x480x0x60=R000000000000000000000000000000000000000000000000000000000000000000000000000000000100000001000000
DALR6 DFPI 2=R0000000000000000000000006400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000640000006419000000000000000000000000000000000000000000000000000000000000
DALR6 DFP640x480x0x60=R000000000000000000000000000000000000000000000000000000000000000000000000000000000100000001000000
DALR6 DFP=R0000000000000000000000006400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000640000006419000000000000010000000000000000000000000000000000000000000000
DALR6 DFPI 21680x1050x0x60=R000000000000000000000000000000000000000000000000000000000000000000000000000000000100000001000000
DALR6 DFP1680x1050x0x60=R000000000000000000000000000000000000000000000000000000000000000000000000000000000100000001000000
DALLastSelected=V24
GDOADJR6 DFP=R000000000200000010000000000000000100000000000000000000000100000001000000000000000200000002000000000000000200000001000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
GDOADJR6 DFPI 2=R000000000200000010000000000000000100000000000000000000000100000001000000000000000200000002000000000000000200000001000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALDriverGammaData_Index0FS3DRed=R00000101020203030404050506060707080809090A0A0B0B0C0C0D0D0E0E0F0F10101111121213131414151516161717181819191A1A1B1B1C1C1D1D1E1E1F1F20202121222223232424252526262727282829292A2A2B2B2C2C2D2D2E2E2F2F30303131323233333434353536363737383839393A3A3B3B3C3C3D3D3E3E3F3F40404141424243434444454546464747484849494A4A4B4B4C4C4D4D4E4E4F4F50505151525253535454555556565757585859595A5A5B5B5C5C5D5D5E5E5F5F60606161626263636464656566666767686869696A6A6B6B6C6C6D6D6E6E6F6F70707171727273737474757576767777787879797A7A7B7B7C7C7D7D7E7E7F7F80808181828283838484858586868787888889898A8A8B8B8C8C8D8D8E8E8F8F90909191929293939494959596969797989899999A9A9B9B9C9C9D9D9E9E9F9FA0A0A1A1A2A2A3A3A4A4A5A5A6A6A7A7A8A8A9A9AAAAABABACACADADAEAEAFAFB0B0B1B1B2B2B3B3B4B4B5B5B6B6B7B7B8B8B9B9BABABBBBBCBCBDBDBEBEBFBFC0C0C1C1C2C2C3C3C4C4C5C5C6C6C7C7C8C8C9C9CACACBCBCCCCCDCDCECECFCFD0D0D1D1D2D2D3D3D4D4D5D5D6D6D7D7D8D8D9D9DADADBDBDCDCDDDDDEDEDFDFE0E0E1E1E2E2E3E3E4E4E5E5E6E6E7E7E8E8E9E9EAEAEBEBECECEDEDEEEEEFEFF0F0F1F1F2F2F3F3F4F4F5F5F6F6F7F7F8F8F9F9FAFAFBFBFCFCFDFDFEFEFFFF
DALDriverGammaData_Index0FS3DGreen=R00000101020203030404050506060707080809090A0A0B0B0C0C0D0D0E0E0F0F10101111121213131414151516161717181819191A1A1B1B1C1C1D1D1E1E1F1F20202121222223232424252526262727282829292A2A2B2B2C2C2D2D2E2E2F2F30303131323233333434353536363737383839393A3A3B3B3C3C3D3D3E3E3F3F40404141424243434444454546464747484849494A4A4B4B4C4C4D4D4E4E4F4F50505151525253535454555556565757585859595A5A5B5B5C5C5D5D5E5E5F5F60606161626263636464656566666767686869696A6A6B6B6C6C6D6D6E6E6F6F70707171727273737474757576767777787879797A7A7B7B7C7C7D7D7E7E7F7F80808181828283838484858586868787888889898A8A8B8B8C8C8D8D8E8E8F8F90909191929293939494959596969797989899999A9A9B9B9C9C9D9D9E9E9F9FA0A0A1A1A2A2A3A3A4A4A5A5A6A6A7A7A8A8A9A9AAAAABABACACADADAEAEAFAFB0B0B1B1B2B2B3B3B4B4B5B5B6B6B7B7B8B8B9B9BABABBBBBCBCBDBDBEBEBFBFC0C0C1C1C2C2C3C3C4C4C5C5C6C6C7C7C8C8C9C9CACACBCBCCCCCDCDCECECFCFD0D0D1D1D2D2D3D3D4D4D5D5D6D6D7D7D8D8D9D9DADADBDBDCDCDDDDDEDEDFDFE0E0E1E1E2E2E3E3E4E4E5E5E6E6E7E7E8E8E9E9EAEAEBEBECECEDEDEEEEEFEFF0F0F1F1F2F2F3F3F4F4F5F5F6F6F7F7F8F8F9F9FAFAFBFBFCFCFDFDFEFEFFFF
DALDriverGammaData_Index0FS3DBlue=R00000101020203030404050506060707080809090A0A0B0B0C0C0D0D0E0E0F0F10101111121213131414151516161717181819191A1A1B1B1C1C1D1D1E1E1F1F20202121222223232424252526262727282829292A2A2B2B2C2C2D2D2E2E2F2F30303131323233333434353536363737383839393A3A3B3B3C3C3D3D3E3E3F3F40404141424243434444454546464747484849494A4A4B4B4C4C4D4D4E4E4F4F50505151525253535454555556565757585859595A5A5B5B5C5C5D5D5E5E5F5F60606161626263636464656566666767686869696A6A6B6B6C6C6D6D6E6E6F6F70707171727273737474757576767777787879797A7A7B7B7C7C7D7D7E7E7F7F80808181828283838484858586868787888889898A8A8B8B8C8C8D8D8E8E8F8F90909191929293939494959596969797989899999A9A9B9B9C9C9D9D9E9E9F9FA0A0A1A1A2A2A3A3A4A4A5A5A6A6A7A7A8A8A9A9AAAAABABACACADADAEAEAFAFB0B0B1B1B2B2B3B3B4B4B5B5B6B6B7B7B8B8B9B9BABABBBBBCBCBDBDBEBEBFBFC0C0C1C1C2C2C3C3C4C4C5C5C6C6C7C7C8C8C9C9CACACBCBCCCCCDCDCECECFCFD0D0D1D1D2D2D3D3D4D4D5D5D6D6D7D7D8D8D9D9DADADBDBDCDCDDDDDEDEDFDFE0E0E1E1E2E2E3E3E4E4E5E5E6E6E7E7E8E8E9E9EAEAEBEBECECEDEDEEEEEFEFF0F0F1F1F2F2F3F3F4F4F5F5F6F6F7F7F8F8F9F9FAFAFBFBFCFCFDFDFEFEFFFF
DALOvlYUVBrightness=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVContrast=R6400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVSaturation=R6400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000640000006400000064000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVHue=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVGamma=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVInvGamma=R0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
DALOvlYUVOvlKelvin=R64190000
[AMDPCSROOT/SYSTEM/BUSID-1:0:0-0/DDX]
GammaCorrectionI=S0x06419064
GammaCorrectionII=S0x06419064
DesktopSetup=Shorizontal,reverse
[AMDPCSROOT/SYSTEM/BUSID-1:0:0-0/LDC]
LinkedAllSliders=V1
[AMDPCSROOT/SYSTEM/BUSID-1:0:0-0/LibXUtil/Display1]
Map=V8
Enable=V1
[AMDPCSROOT/SYSTEM/OpenGL]
StereoMode=Soff
[AMDPCSROOT/SYSTEM/BUSID-1:0:0-1/LDC]
LinkedAllSliders=V1

```

---

### Post by kannedheat on 2009-06-05
I had the same problem.  See my post:
> **kannedheat said:**
> I had the same problem. Try this it worked for me.

Boot up to a terminal session and type:
```
apt-get remove --purge xorg-driver-fglrx
```
Since I used the ATI console
```
/urs/share/ati/fglrx -uninstall.sh
```
```
reboot
```
I was good to go. You might want to try
```
apt-get install xserver-xorg-video-radeon
```
If you need to get online through the terminal session 
```
iwconfig
```
```
ifconfig *$device_name* up
```
```
iwlist scan
``````
iwconfig *$device* essid "*connections name*"
```
```
dhclient *$device*
```
Good luck I hope this helps.

---

### Post by &quot;SunSpire&quot; on 2009-06-07
Hey guys, I'm new to the boards :)

Here's the story ... been using Ubuntu 8.04 for quite a while, with ATI x1650 pro video card and proprietary drivers, THEN I moved home and now I got wireless internet instead of cable connection - I spent ages trying to get my Realtek Wifi PCI card to work in Ubuntu 8.04 but eventually gave up. So last night I installed 9.04 from scratch (via Wubi) and was really happy to see Wifi and Adv. Desktop Effects working out of the box, but of course it didn't take long before I found out about the ATI problem discussed here ... I'm really frustrated now :( 

My question would be, do you think I can go back to 8.10 without breaking my Wifi internet connection? (Like, when was that Wifi driver added? It's not available in 8.04) If so then I'll happily install the older ATI driver for now, and if the situation doesn't get better I might switch to Nvidia myself (I didn't think I'd ever say that in my life!)

Thanks everyone!

"SunSpire"

---

### Post by ales on 2009-06-07
> **"SunSpire" said:**
> Hey guys, I'm new to the boards :)

Here's the story ... been using Ubuntu 8.04 for quite a while, with ATI x1650 pro video card and proprietary drivers, THEN I moved home and now I got wireless internet instead of cable connection - I spent ages trying to get my Realtek Wifi PCI card to work in Ubuntu 8.04 but eventually gave up. So last night I installed 9.04 from scratch (via Wubi) and was really happy to see Wifi and Adv. Desktop Effects working out of the box, but of course it didn't take long before I found out about the ATI problem discussed here ... I'm really frustrated now :( 

My question would be, do you think I can go back to 8.10 without breaking my Wifi internet connection? (Like, when was that Wifi driver added? It's not available in 8.04) If so then I'll happily install the older ATI driver for now, and if the situation doesn't get better I might switch to Nvidia myself (I didn't think I'd ever say that in my life!)

Thanks everyone!

"SunSpire"

If you want to get back to 8.10, you will need to install it from scratch I think. Never heard of doengrade from any ubuntu distro. And to ati. if u don't want to wait if the driver issue will be solved, then buy nvidia, or HD ATI series. But as the nvidia supports its chips its better choice in linux. I checked that sapphire hd4650 radeon is 52 euros or similar nvidia.

---

### Post by &quot;SunSpire&quot; on 2009-06-07
I know I have to install from scratch if I want to downgrade, that's not a big deal. But I would only do that if I know for sure that my Realtek Wifi card will still work in 8.10, cos it does not in 8.04 ... in 9.04 it did work right out the box.

Going back to 8.10 to fix the ATI issues is pointless if I break the Wifi in the process :P

Thank you!

"SunSpire"

---

### Post by vildanovak on 2009-06-07
Please did anybody try to upgrade with the x600 mobile? I would love to update, and try out the opensource driver(once again), but 3d performance in blender is for me the topmost needed thing, since i am an 3d artist. I don't understand well what types are supported, and don't want to mess up my production machine. I hoped this gets resolved soon when I shocked realized that after the 9.04 release, but it seems ATI just wants to loose all linux customers.

---

### Post by markbuntu on 2009-06-08
Well, ati is dropping windows too. No new drivers for windows users either.

The open source driver should work just fine with your x600, accelerated2D and 3D. You can try the live cd to find out.

---

### Post by linuxpt on 2009-06-08
I have an ATI graphic card x1200 and I've tried everything on the new ubuntu distro and nothing worked. 
Im going to change back to 8.04. Till someone says that something solved this problem.

---

### Post by oldrocker99 on 2009-06-08
> **linuxpt said:**
> I have an ATI graphic card x1200 and I've tried everything on the new ubuntu distro and nothing worked. 
Im going to change back to 8.04. Till someone says that something solved this problem.

I have an X1200 as well. Tonight I removed the fglrx drivers and enabled the OSS drivers, installed Jaunty, and compiz is running pretty well at 30 FPS. I notice a fglrx driver in System/Hardware Drivers, but I haven't enabled it yet.

:guitar:

---

### Post by oldrocker99 on 2009-06-09
(Sigh)](*,)

Well, I tried this evening to install the fglrx drivers from System/Hardware Drivers. Because my xorg.config file was set up for the open source driver (the only way I could upgrade to Jaunty), I changed the "ati" in the Drivers section to "fglrx" (otherwise Hardware Drivers didn't like the xorg.config file). The drivers loaded and installed. I rebooted. Screwed-up graphics again. Booting in diagnostic mode and trying to fix teh X server did no good. And I had thought that the driver I downloaded through the Hardware Drivers, uh, wizard, could be trusted.  So...

I'm copying my homedir to a backup and reinstalling.

](*,)Again.

:guitar:

---

### Post by markbuntu on 2009-06-10
The x1200 will not work with any new ati fglrx driver from 9.4 on or any linux distribution that uses xserver1.0.16 or later. This includes jaunty9.04 so stop wasting your time.

---

### Post by reydempto on 2009-06-11
Sigh.....i wasted all my time upgrading for nothing

just to confirm with you guys i have an ATI radeon x1300, and it is a NO GO! back to intepid i go :(

---

### Post by deeperDATA on 2009-06-11
> **reydempto said:**
> Sigh.....i wasted all my time upgrading for nothing

just to confirm with you guys i have an ATI radeon x1300, and it is a NO GO! back to intepid i go :(

There is still hope - I'm using a Toshiba Satellite A215 with an ATI Radeon X1200 card. I *upgraded* from 8.10 to 9.04 and the FGLRX driver had extremely poor performance with many distorted graphics. The proprietary driver worked but the performance was very slow.
So I performed a clean install of 9.04 and the FGLRX is working on my system flawlessly. It's documented that it isn't supposed to work with my card but not only does it work, I'm able to use Blender and a few other 3D apps that NEVER worked before with any kind of driver. Very strange.

---

### Post by jonte_se on 2009-06-17
hi, 
i had the same problem on my NC8430 with ATI X1600.
I installed 2.6.30 kernel and used the radeon driver. problem solved.

[http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)
(radeon: Add support for R6xx/R7xx GPUs)

---

### Post by RGPerson on 2009-07-09
> **jonte_se said:**
> hi, 
i had the same problem on my NC8430 with ATI X1600.
I installed 2.6.30 kernel and used the radeon driver. problem solved.

[http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)
(radeon: Add support for R6xx/R7xx GPUs)


Okay, two questions: 1) Will 2.6.30 work with ATI Radeon 4550?  And 2) How the heck do I get 2.6.30?

I'm a Windows girl (really, been in tech support for 10 years).  I've dabbled with this linux (ubuntu) now and then, but I still feel like a blind person stuck in a forest when I have to get into the terminal for configurations and installations.

Update: I have a new plan: I have an extra 160GB HD.  It should be returning to me tomorrow (was recovery media for a crashed hard drive I was trying to get recovered).  Once we have it, I'm going to hook it up to the Linux computer and copy my real home directory to it.  Then I'm going to start completely over.  We'll install, in separate partitions, 8.04, 8.10 and 9.04 so we can experiment but still have a backup OS that works so we can watch our shows.

So I'd still like to know how I can get this 2.6.30. It sounds like it's better than all of those 3.  I will still be researching this.

Gabrielle

---

### Post by Kombak on 2009-07-09
Well, I guess that means I am boned with my Ati 9550.....  I knew there was a reason I always hated ATI.

---

### Post by peakshysteria on 2009-07-10
> **Kombak said:**
> Well, I guess that means I am boned with my Ati 9550.....  I knew there was a reason I always hated ATI.

As mentioned earlier in this thread; my 5 year old sons laptop with an ATI 9000 card runs very smooth out of the box.

---

### Post by RGPerson on 2009-07-12
Well, the fresh installed worked great.  I backed up everything I wanted to a separate drive, then I started over.  I installed 8.10 with manual partitioning. I have a 250 GB drive.  I partitioned it into 3 70GB partitions and a 40GB swap partition.  I installed 8.10 into the first 70 GB partition.  Works fine.  Video drivers installed fine.

Went on to install 9.04.  Installed manually choosing the partition. Put it on the 2nd 70GB partition. It installed fine. It notified me of restricted drivers so I installed them.  Everything is working great on that end.  Still have to see about my Hauppauge but I'll work on that another day.


Gabrielle

---

### Post by Fleshmelt on 2009-07-12
Being the Noob that I am, I went ahead and clicked the upgrade button without understanding the warning that was presented.  Now I have Ububtu 9.04 on my machine with a ATI Radeon X1600 that has no usable driver.  I am just learning Linux and I have spent several hours configuring stuff that I would rather not have to do again.  Is there a way to roll back to Ubuntu 8.10 without reinstalling?

Ok, after actually taking the time to read this entire forum it looks like the x1600 might work with the open source driver.  I am going to try this and I will edit this post when I know for sure.
As for rolling back I figured out that I can make a new partition and put 8.10 on it but I was trying to make a separate partition for Ubuntu when I installed it in the first place and managed to fail miserably and wiped the Windows partition (including 3 years of hard work).  Can someone direct me to a tutorial on how to do this that is written in plain English?

---

### Post by ocsmidnight on 2009-07-21
Ok, so I understand the overall issue with the exclusion of support for some video cards in the new fglrx driver and how this relates to Jaunty's use of X Server 1.6. Here is my question. When I run ```
lspci | grep Radeon
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]

``` I obviously see that I have a Radeon X1200 in my Toshiba laptop. Now, from what I've read this card is one that is now unsupported. However, as shown above it says it uses the RS690M chipset. According to [this article from Phoronix]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1") the RS690M chipset is still supported. Does this mean I can find a workaround and use the new fglrx drivers instead of the open source?

---

### Post by DonLuke on 2009-07-22
Same problem, that's a bad thing

---

### Post by Mark Phelps on 2009-07-22
> **ocsmidnight said:**
> According to [this article from Phoronix]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1") the RS690M chipset is still supported. Does this mean I can find a workaround and use the new fglrx drivers instead of the open source?
I read the same article, and it's not clear what that statement is intended to say because they follow that reference indicating that a later model card IS supported -- implying that the earlier models are NOT supported.

Personally, I would believe what AMD/ATI posted when they indicated that the X1200 is no longer supported.

---

### Post by DonLuke on 2009-07-23
For who has installed this driver and want to replace it with the old (but working) open source driver witout reinstalling all ubuntu:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


this helped me

---

### Post by Deicider on 2009-07-24
Have the same prob
I own a x700 ati card and have troubles with drivers, first cause i have already installed the nvidia drivers ( my nvidia card had other probs and i changed it with my x700)
1.How can i uninstall Nvidia drivers?
2.If i solve 1, will i manage to install correctly ati drivers on 9.04?
3.The above guy said he did something at it worked, does it really work?
4.Help
5.Please
6. (:

---

### Post by DaLightBender on 2009-08-23
Will koala fix this issue?

---

### Post by Mark Phelps on 2009-08-23
> **DaLightBender said:**
> Will koala fix this issue?

No -- AMD/ATI dropped driver support for the legacy cards.  The only recourse is the open source driver -- which is already available in Jaunty.

---

### Post by Maddmaxx on 2009-08-25
[http://ubuntuforums.org/showthread.php?t=1248220](http://ubuntuforums.org/showthread.php?t=1248220) Post # 6... It's a start, but WTF?

---

### Post by kalyp on 2009-09-16
Thanks a lot! It was all screwed up, dpkg-reconfigure didn't change anything, and that link solved everything, only by removing the fglrx driver. I was ready to reinstall to 8.10 :)

> **DonLuke said:**
> For who has installed this driver and want to replace it with the old (but working) open source driver witout reinstalling all ubuntu:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


this helped me

---

### Post by Vjetar on 2009-09-16
Just to add my 5 cents to whole discussion.

For some strange reasons I had to reinstall 9.04 from scratch. Previous installation was 8.10 upgraded to 9.04 and Compiz worked painfully slow.

Now, everything is in right order, Compiz works fine, all without any special lines in xorg.conf. Just plain installation.

Strange!

---

### Post by rsrini on 2009-09-19
I am using ATI radeon 9200 video AGP card with Asus motherboard K8NE-Deluxe. Installed the Ubuntu 9.04. It worked fine. One day i made the bios change for primary video card search from pci to AGP. After booting i was not able to get back my display. I am not able to use the Ubuntu. Windows is fine. With boot cd also it is working fine. Monitor compact CRT V45. Tried with BenQ G2020 TFT also. No solution. Even if i set the screen resolution to different from boot cd and then boot from HDD. Still problem persists. With TFT it  goes out of range. Always gives junk screen and struck. Any way i can clean the files related to video and only update with new from boot cd. 

Tried delete the xorg.conf file, no use. through rescue mode fix display. no use. Any help appreciated.

R.Srinivasan.

---

### Post by Bertran on 2009-10-02
Hey
 
I'm using ATI Mobility Radeon X2300 and my card is no longer supported with the Jaunty version of fglrx. I downgraded my xserver to an intrepid version using this guide ([http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)). Works well for me. 
[]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue")

---

### Post by oldrocker99 on 2009-10-06
> **Bertran said:**
> Hey
 
I'm using ATI Mobility Radeon X2300 and my card is no longer supported with the Jaunty version of fglrx. I downgraded my xserver to an intrepid version using this guide ([http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)). Works well for me. 
[]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue")

A MOST interesting post, and I may give it a try. Thanks for the spot!

:guitar:

---

### Post by ssri on 2009-10-07
> **oldrocker99 said:**
> A MOST interesting post, and I may give it a try. Thanks for the spot!

:guitar:

Yeah, I did this a few months ago on my Mobility Radeon x2300, and just used my modified xorg.conf from intrepid.  Everything works well so far in Jaunty.

---

### Post by martingratton on 2009-10-14
> **Bertran said:**
> Hey
 
I'm using ATI Mobility Radeon X2300 and my card is no longer supported with the Jaunty version of fglrx. I downgraded my xserver to an intrepid version using this guide ([http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)). Works well for me. 


Hi 
in the process we have to modify the file /etc/apt/sources.list. but it tells me i cant save because i dont have the permission,  how can i solve this.

thx

---

### Post by Vjetar on 2009-10-14
> **martingratton said:**
> Hi 
in the process we have to modify the file /etc/apt/sources.list. but it tells me i cant save because i dont have the permission,  how can i solve this.

Type in terminal:
```
sudo gedit /etc/apt/sources.list
```
enter your password and edit sources.list with admin rights.

HTH

---

### Post by lavikl on 2009-10-20
What about the new 9.10 ? will it support the older ATI cards ? or at least offer some kind of an automatic solution ?

---

### Post by ales on 2009-10-20
> **lavikl said:**
> What about the new 9.10 ? will it support the older ATI cards ? or at least offer some kind of an automatic solution ?


Hi,


I am runnign 9.10 fresh beta installation. It uses my X800 GTO with open drivers automaticaly after installation, no need to do anything. COmpiz also running. without problems. SOme minor glitches in games like ENemy Ter. or Urban Terror, otherwise no problmes.

---

### Post by mrdanny on 2009-10-23
Has anybody tried the ATI Radeon X1250 with Karmic Koala?

---

### Post by ssri on 2009-10-23
> **lavikl said:**
> What about the new 9.10 ? will it support the older ATI cards ? or at least offer some kind of an automatic solution ?

The older cards (R500 and below: [http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units)) will never get any support past Catalyst 9.3, as legacy support has been shifted to supporting the development of the opensource drivers.  So, Catalyst 9.3 (which supports kernels up to 2.6.28) is the end of the line when it comes to closed-source proprietary drivers for ATI legacy cards.

---

### Post by triffle on 2009-12-26
> **s3lekta said:**
> thats good to hear, how did you install fresh or upgrade? is everything else working?

I installed via upgrade, and I can confirm that the following worked for me:

> Go to recovery mode,and to root prompt:

apt-get remove fglrx*
apt-get install xorg-driver-fglrx
aticonfig --initial -f

Then reboot.


Here is my setup via lspci

travis@travis-laptop:~$ lspci

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge

00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)

00:04.0 PCI bridge: ATI Technologies Inc Device 7914

00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)

00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)

00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

**01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]**

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

08:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

travis@travis-laptop:~$ 

I hope this helps someone...

---

### Post by kaiwi on 2010-01-10
Hi

I'm having the same problem. Want to upgrade from Ubuntu 8.10 to Ubuntu 9.04. 

Update manager warns me:

> Upgrading may reduce desktop effects, and performance in games and other graphically intensive programs.

This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 9.04.

Do you want to continue?


So I don't want to continue and am sticking with Ubuntu 8.10. 

My PC is less than 3 years old. I therefore didn't expect this kind of problem. 

Is there any chance that the AMD 'fglrx' graphics driver will be supported by the next long-term support release of Ubuntu?

Cheers

---

### Post by Mark Phelps on 2010-01-11
> **kaiwi said:**
> ... Is there any chance that the AMD 'fglrx' graphics driver will be supported by the next long-term support release of Ubuntu? ...

Depends on what you mean by "support".

IF you mean provide a package that can be installed using that driver, the community already does that -- but it's limited what AMD/ATI has decided to support. 

ATI decided last May to drop support for a lot of cards/chips. The package only provides support for the newer HD 3x/4x/5x cards.  It does not, and WILL NOT, be providing support for the older "legacy" cards.

The community provides an open-source driver, which is improving all the time.

---

### Post by gordontytler on 2010-01-15
Will a new kernel break my **ATI Radeon HD 3470** driver again ?

being quite new to ubuntu I let the update manager upgrade me to 9.10. The result was both screens black and all my gnome settings messed up because I switched off at the wrong moment. After several reboots the screens were still black and there was no "last good" option on grub that worked.

So after doing the update my computer was broken with no option to go back.

I eventually fixed it by downloading the latest version of the driver and fixing the Xorg config but before I did this I noticed that a re-install of the original driver detected a new kernal version and then crashed out trying to recompile itself.

Now my Update Manager wants to install the Linux kernel image for version 2.6.31 on x86/x86_64.

There is no way I will do this without 

1) some way of rolling it back if it goes wrong
2) getting a new card with a supported driver (if so which one)
3) someone with the same card knows it will work with 2.6.31

What does ubuntu forum advise ?

thanks

---

### Post by phreeky on 2010-01-18
> **Mark Phelps said:**
> It does not, and WILL NOT, be providing support for the older "legacy" cards.

The community provides an open-source driver, which is improving all the time.

Still bothers me as it effects my computer at work (came back to work after holidays hoping I could find a solution).

These so called "older/legacy" cards are still being sold BRAND NEW in plenty of machines, Dell systems included. In fact we have a hundreds of them at work.

ATI/AMDs decision to drop support in the closed-source driver was terrible. That's something you do AFTER there is support in the open-source driver, not prior to them getting it working. Very backwards indeed.

---

