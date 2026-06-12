---
title: "Lenovo Ideapad S10 success stories?"
date: 2008-10-09
forum: Hardware
---

### Post by uiberto on 2008-10-09
Hey gang,

I'm looking at buying one of these new-fangled netbooks. The Lenovo Ideapad S10 looks pretty good, but I can't find much evidence of people installing Ubuntu on it (for better or worse).

Any of you out there running Ubuntu on your Lenovo Ideapad S10? 

Does anyone have multiple Netbooks and have some comparisons to draw?

I'd love to hear your stories.

Uiberto

---

### Post by spike666 on 2008-10-09
I got my S10 yesterday and have put ubuntu onto it (from usb dvd drive).

Everything seems to have gone without a hitch except for the wireless stuff. Once everything was installed, I plugged into a wired network and ran the updates... After that completed, wireless networks showed up and I was able to turn on minor eyecandy and I was able to connect to the local unsecured wireless network.

Trouble came when I tried to connect to my WPA-secured network at home... It's odd; I can see the network, and I can join it. It prompts for password and seems to negotiate, but I never get signed an IP. When I look at the router's status, the s10 shows up in the DHCP clients table with an assigned IP, so something is going on with the local machine.

I've been troubleshooting this for about 2 hours and I've tried the secured network at work and my girlfriend's WPA wireless network but to no avail. It only likes open access points.

I haven't tried the SD port yet or the webcam, but I've seen some posts in the forums that seem promising for those.

Getting used to the keyboard has been tough, though. I had an old Vaio PCG-505tx before this that I was using when I wanted to be super-mobile, and that thing had a small keyboard, too, but this one has some keys in weird places (~ is above the 1 and the up-arrow is between teh right-shift and the ? keys)

so far, it's great, though.

---

### Post by wylee on 2008-12-02
Just got around to install Ubuntu 8.10 (studio). Have it set up to dual boot now.

So far so good, wireless is working, compiz etc. I havent tested webcam yet.

One problem though, and that is with the lan or ethernet. I can configure and browse the internet. But for some reason I'm unable to scp files (specifically a 3 gig file) across the lan, getting error an messages:


Corrupted MAC on input

I'm hoping this is some sort of driver issue and it's not that the ethernet has gone bad.

Anyone else running into this?

---

### Post by perminna on 2008-12-11
I got my red S10e (European "Education" version) on Tuesday. Yesterday I first installed XP Home English (the netbook was delivered with German XP) and then installed Ubuntu 8.10. The dual boot is working without any problems, yay.

After using Eee PC 701 for 3 months (Ubuntu 8.04.1, tweaks, fixes, hacks, grey hair, annoyance, etc), S10e impressed me! Ubuntu 8.10 is working perfectly without even minor problems. All the following are working out of the box. I have not yet installed any updates, Ubuntu is offering 200 MB of them.
-Cam is working (tested with Cheese)
-SD reader is working (SDHC support, tested with A-data 16GB class 6 SDHC card)
-Wifi is working with WEP (I haven't tested LAN)
-audio is working (both speakers and audio out (headphones))
-Bluetooth is working (there's a built-in Bluetooth and I succesfully connected the netbook with my Nokia 6300 phone)
-brightness adjusting with FN keys (without OSD)
-volume adjusting with FN keys (with OSD)

I have not tested the following:
-Built-in mic
-LAN

---

### Post by wkoell on 2008-12-12
I'd like to hear about power management: does it suspend, hibernate and wake up correctly? How long it runs on battery? 

Does the mic work out of the box, somewhere i read it doesn't.

---

### Post by BIGtrouble77 on 2008-12-14
My wife just let me setup ubuntu on my s10 which I can officially use on xmas.  I have the 1gb ram, 160gb version...

First off, I installed ubuntu through the pen drive install feature from the live cd.  I did NOT have to plug into the wired ethernet connection.  I just enabled the restricted drivers and everything worked perfectly.  Kinda sucks I have to use restricted drivers, but it works- signal is MUCH better than my macbook pro.  I have no clue why the other guys in this thread needed to wire up.

I tried to suspend... It worked fine with the power connected, couldn't get it to suspend from battery (power settings were correct).  I only had 2 min to play with it, but I'm sure it's easy to get going.  When it did suspend it came out fine and didn't crash, so it looks pretty stable.

Compiz effects worked from the start and everything was very responsive.  The only issue was the touchpad sensitivity REALLY sucks.  It's because the touchpad is not a perfect square, but the synaptics driver thinks it is.  Apparently it can be fixed with a synaptics driver patch.

I'm eager to see if my 1680x1050 monitor will work well.  But that'll have to wait till xmas. :(  The screen on this thing does look really nice, very deep rich colors and good contrast.  It should do well for light web development, music and all my emulators.

I'm gonna call Lenovo tomorrow to see if I can get a refund on the worthless XP license.

-bt

---

### Post by perminna on 2008-12-15
> **wkoell said:**
> I'd like to hear about power management: does it suspend, hibernate and wake up correctly? How long it runs on battery? 

Does the mic work out of the box, somewhere i read it doesn't.

I tried suspend and hibernate after I'd installed all the updates Ubuntu was offering (about 200 MB). I tested 'em with power cord plugged in. Quick results: both work. Although when hibernating an error message is displayed.. but laptop wakes up without any problems.

I haven't had the time to test the battery life because I have an European version with 6 cell battery. It looks like it *could* be 5+ hours but I cannot be sure because I haven't tested properly.

I haven't tested the built-in mic but I also have read that it's a problem with 8.10 + S10. I can test it in the near future.

---

### Post by perminna on 2008-12-16
Just to let you know, I've written Windows XP & Ubuntu 8.10 dual boot instructions *[in English in my blog]("http://www.thatsabsurd.net/2008/12/xp-and-ubuntu-dual-boot-s10e/")*.

---

### Post by //yardo on 2008-12-19
> **BIGtrouble77 said:**
> I'm gonna call Lenovo tomorrow to see if I can get a refund on the worthless XP license.

-bt

Thanks for the info. Can you update us on the XP License refund?

---

### Post by jron on 2008-12-24
If anyone would like to troubleshoot wifi issues with me, please see my detailed thread here:

[http://ubuntuforums.org/showthread.php?t=1010751](http://ubuntuforums.org/showthread.php?t=1010751)

Also, I recently installed the new Alpha 2 and attempted to pull 750MB file over the LAN with wired ethernet and experienced connection failures using Samba, and HTTP.

---

### Post by larseko on 2008-12-25
I just got my S10 with 160GB disk etc. I have installed ubuntu 8.10 in dualboot with xp, and it works perfectly. I think this is the smoothest experience I've had installing linux on a laptop. Webcam, wireless, monitor, sound, suspend, everything works like they should. Haven't tried hibernation, though. Another thing worth mentioning is the mobile broadband modem I have, which also works out of the box. Just choose the right network and go (the modem has pin code disabled, though). Funny thing is that I can't get the modem to work in XP, as the shitty application it installs won't accept lower resolutions than 800x600. So, pwnd wndzzz. :D

Only thing, as someone also mentioned, is the sound, which is a bit low? Funny, but I haven't tried with headphones yet.

---

### Post by jron on 2008-12-25
larseko, pulseaudio is (as usual) the problem. It caps ALSA at 50% If you killall pulseaudio then run alsamixer, you can bump the volume up to audible levels. I'm trying to work out my wifi issues; if you could post the output from a few commands, I would be very grateful.

lspci -nn | grep Broadcom

and

lshw -C Network

I'm wondering if Lenovo switched wifi cards.

Thank you!

---

### Post by dkitty on 2008-12-26
> **//yardo said:**
> Thanks for the info. Can you update us on the XP License refund?

I would like to know about that too. I never thought to ask for a refund.

---

### Post by larseko on 2008-12-27
> **jron said:**
> larseko, pulseaudio is (as usual) the problem. It caps ALSA at 50% If you killall pulseaudio then run alsamixer, you can bump the volume up to audible levels. I'm trying to work out my wifi issues; if you could post the output from a few commands, I would be very grateful.

lspci -nn | grep Broadcom

and

lshw -C Network

I'm wondering if Lenovo switched wifi cards.

Thank you!

Thanks, that seems to have sorted out the sound issues, but I didn't find the levels was at 50% or lower, they were almost to the max. As for the other info, I'm happy to provide it:

```
larsekol@lentop:~$ lspci -nn |grep Broadcom
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
larsekol@lentop:~$ 
larsekol@lentop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:27:0b:37
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:85:68:cd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.2.187 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:90:38:4e:16:55
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
larsekol@lentop:~$ 

```

Hope that helps :)

---

### Post by BIGtrouble77 on 2008-12-30
> **//yardo said:**
> Thanks for the info. Can you update us on the XP License refund?
Lenovo was pretty unprofessional about my request.  The guy I talked to said that these machines don't have real windows licenses so they couldn't refund anything.  After I explained what an oem license was he hung up on me.

I emailed sales support, but they gave me the run around.  They also didn't want to talk about the horrible phone service I got.  Honestly, I'd stay away from them.  There are too many other companies that will give much better support.  This was just pathetic.  I think I was pretty nice considering the lack of professionalism on their end.

With that said, the only reason they would not consider refunding winxp was because I purchased through Circuit City and would have to request a refund from them. :confused:  The only reason I did not go through Lenovo directly was because they were not offering the higher spec'd model at the time.  Anyway, if you purchased through them you may have some success.  

Ubuntu does work perfectly on this machine.  I've had no issues except the unacceptably small right shift key. 1680x1050 external monitor was too sluggish for me, 1280x1024 was ok.  720p HD movies from my Vado are too much, unfortunately- videos are a slideshow.  h.264 encoded dvd's work great.  All the emulators I setup worked beautifully.  Very cool little gaming/multimedia machine.

-bt

---

### Post by dkitty on 2009-01-05
That doesn't sound promising Trouble, but then, I did not have high expectations. Thank you for the update regardless.

I received my S10 shipped to my office today. There were a few squeeeees of joy from a normally sober chica. :D

Ubuntu 8.10 is ready for install on a USB stick at home. I can't wait.

---

### Post by dkitty on 2009-01-06
I had a little trouble installing Intrepid 8.10. I used the System > Administration > Create a USB startup disk option. However, I tried the alternate install CD-Rom as a base. The install process hung several times after formatting the s10's HDD.

I downloaded the live CD instead and used that to great effect, but please note, do not use the alternate install CD to create your USB boot disc.

Also, out of curiosity, I connected an USB Sony CD writer/ player before booting the s10. I held the Fn button and pressed F11/F12 and was pleasantly surprised to find the boot selection included the Sony USB CD drive listed by name. I could have booted from a CD. :D

---

### Post by notessensei on 2009-01-07
> **jron said:**
> I'm trying to work out my wifi issues

I had problems on 8.10 with WIFI and Leap which sounds a little similar (by symptoms). Try this: right-click on the network icon and create/edit your settings (ssid/passcode). Worked for me.
:-) stw

---

### Post by m3ph on 2009-01-07
Hi,

I got everything except my battery charge meter running. It shows me 0% charge all the time...
What could be causing this?

---

### Post by arsenic23 on 2009-01-07
Just to stop other people from trying their luck, you will most likely **NEVER** get a refund for a copy of XP that comes with a netbook.  Microsoft licenses these intalls under their [COLOR="DarkRed"]**ULCPC license**[/COLOR] and it costs the manufacturers almost nothing.  It also puts restrictions on the computers sold with the software such as: no great then 1gig of RAM, CPU no faster then X, etc...

That said, I ordered my S10 a few days ago, and I just look at the XP license as something that will increase the value of the laptop when I sell it a few years from now.  [COLOR="Silver"](  bought the cheapest one, a 500gig drive, and 2gigs of ram )[/COLOR]

---

### Post by dkitty on 2009-01-07
> **m3ph said:**
> I got everything except my battery charge meter running. It shows me 0% charge all the time...
What could be causing this?

Try the 8th post in [this thread](http://ubuntuforums.org/showthread.php?t=963832), m3ph. I'm not sure you have the exact same problem, but it is worth a look, no? Good luck.

---

### Post by drinkmocha on 2009-01-10
so was anyone able to make the mic work? please reply, i'm about to get the S10 and i'm so stoked about it :)

---

### Post by BIGtrouble77 on 2009-01-14
> **drinkmocha said:**
> so was anyone able to make the mic work? please reply, i'm about to get the S10 and i'm so stoked about it :)

The mic works perfectly fine for me.  I don't have it working with skype yet because skype defaults to the mic port, not the actual internal mic.  I'm sure I just have to do a pulse audio change to get the 'Front Mic' to be recognized from skype.  I would recommend doing the pulse audio update in the Tips and Tricks section.

I have absolutely everything working from the start.  I'm surprised some of you are having issues.  The only thing out of the ordinary was fixing pulse audio, which was very easy.  Oh, and the touchpad driver fix was needed too.

-bt

---

### Post by drinkmocha on 2009-01-14
cool, thanks. i found a fix for the weird trackpad issue here:  [http://slacy.com/blog/2008/12/vertical-scrolling-fix-for-lenovo-s10-ubuntu/](http://slacy.com/blog/2008/12/vertical-scrolling-fix-for-lenovo-s10-ubuntu/)

now i need to fix my audio, it's too soft/low.

---

### Post by drinkmocha on 2009-01-14
okay, i can't get the mic to work on skype. i already changed the settings to use 'pulse audio'. help anyone? please.

---

### Post by BIGtrouble77 on 2009-01-14
> **drinkmocha said:**
> okay, i can't get the mic to work on skype. i already changed the settings to use 'pulse audio'. help anyone? please.
I'm going to try and get skype working for me tomorrow.  Can't do it tonight, don't want to wake my wife up:p  When I get it working i'll report back.

If you are still having audio issues follow this thread:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

It fixed all of my audio issues.  Before applying the fix I was having a lot of weird audio issues related the bugs mentioned in that thread.  After going through it they all went away.

---

### Post by dkitty on 2009-01-15
Mic problems? Really? I had none.

I don't use skype but occasionally use Ventrilo under wine. I was surprised that the mic worked for me in vent. So few do.

---

### Post by Jole on 2009-01-15
I can't make Skype to see the front mic too. I can see it in the control panel like a "front mic", but skype only tries to connect to the line in mic. I don't see many topics with Ubuntu running on Lenovo S10. Is really we're not too many of them ?

---

### Post by nilfilter on 2009-01-20
I got the internal microphone working (incl. Skype) by installing the 2.6.27-11 kernel from the "proposed" repo.

HTH

---

### Post by //yardo on 2009-01-20
Thanks for the replies. I read a blog a while back where the guy was able to get a refund on his xp license. It was an incredibly tedious process and he only saw it through to prove a point and definitely not because it was convenient.

Knowing that, it's not that important to me.

I've been running 8.10 on my s10 for about 4 weeks now and it's pretty much worked flawlessly. Compiz effects work beautifully which was a surprise to me. I expected latency or for it not to work AT ALL.

Wireless network worked outta the box. I love this thing. I carry it EVERYWHERE.

For those that want to create a usb install download an ISO and use UNETbootin to create the boot usb disk.

It was that simple for me. I tried to use the "Create a USB Start Up Disk" option from the "System" drop down menu and it did not work.

---

### Post by sambarluc on 2009-01-22
It was shipped with a really ugly suse enterprise. Installed from a USB stick Ubuntu 8.10 on a 160gb (single boot) with no problem at all. Everything works out of the box (except card reader, not tested). Sound volumes are indeed very low, but killall pulseaudio solved the issue. With headset it is just fine out of the box.
Looks like a great machine.

---

### Post by dkitty on 2009-01-22
They're shipping with SUSE pre-installed now?

:confused:

---

### Post by LowSky on 2009-01-22
> **dkitty said:**
> They're shipping with SUSE pre-installed now?

:confused:

Commerecially no... The version for government use, yes. its technically called the S10e (e: meaning education model). Anyone can order it, it just not listed on the Home/Small busineess purchasing site.

I just ordered mine, and Windows XP was the only option. I can't wait to dual boot this thing. I would wipe XP entirely but I bought this for XP so I can use Vag-Com which wont work with Wine, and TV watching, which many network websites wont work with Linux...

I got a great Deal on the S10 in Red, with 512Ram and 80 Gig hard drive. I already ordered 2GB of RAM to max the machine out and a internal bluetooth  off ebay, as the US model is lacking this feature. Should have it sometime next week. I cant wait.

---

### Post by drinkmocha on 2009-01-23
I'm having a problem with my fan on my S10. It's just too loud at startup and when the computer is having a 'hard time' doing something.

Is there anything I can do to quiet down the fan a little? Thanks to anyone who can help.

---

### Post by simon_wrafter on 2009-01-29
> **nilfilter said:**
> I got the internal microphone working (incl. Skype) by installing the 2.6.27-11 kernel from the "proposed" repo.

HTH

2.6.27-11 has now hit the "normal" repos, and the front mic is working perfectly! for skype to function change the Sound In setting to "HDA Intel (hw:Intel,0)" under Sound Devices.

Finally every thing works OOTB on S10e!

---

### Post by ions on 2009-01-31
Installed with Wubi last night and so far everything has worked perfectly - including wireless.  Only thing I haven't tried is the mic(I never use em).  Nice little machine and now that it has a good OS on it it's even better.  :)

---

### Post by Raptormn on 2009-02-08
well i got my s10 in the mail the other. did the usb install. worked great. no problems. wifi works. which was key since that is the only type of connect available. also popped a 2gb stick of ram in it.

---

### Post by TwiceOver on 2009-02-11
Installed 8.10 on my S10e yesterday and everything works extremely well with the exception of being able to turn off bluetooth.

The fn+f5 combo doesn't work, and pressing the green wireless button enables/disables both bluetooth and wifi rather than cycling through them like Windows does.

All in all, a much better system with Ubuntu on it than XP.

---

### Post by simon_wrafter on 2009-02-11
Although almost everything is working fine, I've noticed that every once in a while when I boot my computer the temp sensors are telling me the temperature is in the region of 70 C which is very false. Because of the high output my fan goes wild but nothing changes, temp stays where it started. has any one else had this problem? or maybe a tip of how to prevent it?

PS. love my S10e :D

---

### Post by NOOBIEST on 2009-02-11
I dunno why i think it's cuz i am noobie to all ubuntu and netbook trent but i can't seem to get my ubuntu cd boot from a usb dvd drive am i doing something wrong?just to have ubuntu on my s10 i actually bought a $100 lg slim usb dvd drive but nothing any help???

---

### Post by henge on 2009-02-12
got mine 2 days ago and everything is working fine.
just have one question...

what are you guys doing about the screen size

many program like thunderbird in addressbook and evolution
same problem can't see the lower part of dialogbox.
so problems with save cancel buttons

---

### Post by joec3 on 2009-02-13
> **henge said:**
> got mine 2 days ago and everything is working fine.
just have one question...

what are you guys doing about the screen size

many program like thunderbird in addressbook and evolution
same problem can't see the lower part of dialogbox.
so problems with save cancel buttons

1. Stack windows(desktops) in the pager(window selector) vertically (2 rows) then drag the offending window to overlap the two.This works in Mint so I asume will work with staight Ubuntu.

2. Try dragging window with Alt-Rt click

---

### Post by Borbus on 2009-02-13
I can't find the S10 that isn't tainted with windows. Is it easy to get a refund from Lenovo when I refuse to accept the EULA? And does the windows sticker come off easily?

---

### Post by dkitty on 2009-02-15
Someone posted earlier in this thread about getting a refund on the pre-installed WinXP. It doesn't sound fun. I despise red-tape, so I'm not going to bother.

But yes, the Windows sticker comes off relatively easy. I very carefully used my pocket-knife to remove the sticker and then a little alcohol with a plastic dish scrubber to remove the sticky residue.

---

### Post by vauge on 2009-02-19
Installing Ubuntu 8.10 was very pleasurable experience. Simple and within minutes I was up and running.

Wireless out of box!

Zero issues. 
Have not tested the mic, but cam works well with cheese.

Edit:
Free wireless is not an issue. Login to home WEP or WPA has zero issues - works flawlessly.

WPA2 - College wireless that requires authentication using wpa_supplicant, freezes then locksup requiring battery removal.
I think I read it is an issue with Intrepid and 2.6.27-11-generic kernel.

---

### Post by nekr0z on 2009-02-23
My girlfriend's Lenovo S10 is having trouble waking up from hibernate - touchpad stops working. Has anybody else met this issue?

---

### Post by pkeegan on 2009-03-01
When I do a clean install of Ubuntu 8.10 (on a separate hard drive) applications on the S10 don't run smoothly. ie. Flash videos on CNN are jerky and sound is spotty. Even a simple low bitrate mp3 has sound issues. I'm using the Macromedia flash plugin.

I don't have any of these issues with the hard drive that has Windows installed on it.

I've reinstalling Ubuntu several times but have no joy. It acts as if the CPU is being limited. Any ideas?

---

### Post by k@e on 2009-03-03
> **nekr0z said:**
> My girlfriend's Lenovo S10 is having trouble waking up from hibernate - touchpad stops working. Has anybody else met this issue?

Yes, I have too but there is a simple workaround to this. If the screen flickers after waking up from hibernate, press FN+Up or Down to change brightness, which should promptly show you the login screen.

My recommendation: to hibernate your Ideapad, use the option from the panel. Closing the lid to hibernate will cause the problems above.

---

### Post by nekr0z on 2009-03-03
> **k@e said:**
> My recommendation: to hibernate your Ideapad, use the option from the panel. Closing the lid to hibernate will cause the problems above.
I tried doing it from the panel, I tried doing it with the lid, I even tried setting the "power" button so that it would hibernate the machine. The result is still the same.

---

### Post by SyDiko on 2009-03-13
I'm a new user of Ubuntu, but a moderately skilled PC/Linux user.. When you get around the GUI, everything is basically the same.

My install was weird, but went flawlessly. 

Basically, I wanted to see if I could get a working copy of Ubuntu on my S10 with just a thumb drive. First, I actually installed Ubuntu using a virtual drive~ DaemonTools from XP home, which was successful, but my intentions were to get into linux to make my thumb drive bootable, because updating the kernel gives you a little bit of trouble. After I got into Ubuntu via dual boot... I promptly made my 2g thumb drive bootable and install Ubuntu cleanly onto my freshly partitioned 160ger.

My IT counter-part here at work, is begging me to switch back to XP, because he hates Linux... However my arguement is that, the only thing I use this guy for is to browse the internet. So why should I bog down half my system's resources with Microsoft's clunkly services and startup applications, plus anti-virus, malware, spyware and other garbage just to browse the internet? XP on a netbook just doesn't make much sense to me!

I've knocked my RAM up to 1.5gs, so now the only upgrade is a 6-cell battery for a longer discharge time.


> **dkitty said:**
> 
But yes, the Windows sticker comes off relatively easy. I very carefully used my pocket-knife to remove the sticker and then a little alcohol with a plastic dish scrubber to remove the sticky residue.

With all due respect, your method for removing the stickers is a bit exaggerated in this case and someone with a shaky hand could scratch the plastic case!

Just use your finger nails! Even after a month, the adhesive, which is extremely light, does not leave much, if any, left behind residue and if there is residue; a damp paper towel will wash it away. :D

---

### Post by bossdak on 2009-03-17
got mine last saturday, removed intel/windows sticker put 500gb hd and installed 8.04 hardy! initially no wireless but connected to wired network, updated and rebooted, then i have wireless working. only thing not tested is the expresscard and webcam, but i think it should work.

---

### Post by dustrho on 2009-04-07
How is the battery life on this laptop? I'm thinking about getting one, but I'm hoping to get at least 2 hours of battery life out of this.

Thanks.

---

### Post by dkitty on 2009-04-07
I've had my S10 for 4 months now and still reliably get 2.5-3.5 hours of use out of the battery. Mind, I turned off desktop effects. I thought about buying the 6-cell battery but haven't needed it yet.

---

### Post by HotCupOfJava on 2009-04-13
Just got mine today. Tested out Ubuntu on a persistent 8.10 version on a thumb drive. It worked very well. Almost all of the comments I've read regarding the S10 and Ubuntu were very positive, so I took the plunge and did a full install (I hardly ever use Windows on my partitioned machine, anyway). It works great! All the hardware seems to function properly - wifi, bluetooth, etc. Huge difference from the way things used to be (like [this]("http://www.horstmann.com/linux-thinkpad-r40.html")).

If you want some laughs, follow the link. Its quite amusing.

---

### Post by Marat89 on 2009-04-23
anyone tested s10 with ubuntu 9.04 jaunty?

---

### Post by Hoora on 2009-04-26
> anyone tested s10 with ubuntu 9.04 jaunty?
I installed dual-boot XP and Ubuntu 9.04 netbook remix on my Lenovo s10e today and everything went very well, not a single problem! Wireless (with WPA2) and everything ok. Performance is very good and the boot time is extremely fast.

Very happy with the UNR Jaunty!

---

### Post by liborw on 2009-04-27
I have just installed Ubuntu 9.04 on S10e and the mic doesn't seems to work and also I have no idea how to enable bluetooth, the Alt+F5 just switch on and off wifi have no affect on bluetooth.

I will be thankfull for all your help.

---

### Post by dustrho on 2009-04-27
How is the processing power on these with Jaunty? Does it feel the least bit sluggish? How is it as a media player, meaning does it play movie files without any frame loss?

I'm really tempted with getting one of these.

---

### Post by Obi Wan Tin on 2009-04-29
I have mine S10e with winXP/Ubuntu Netbook Remix 9.04. With 6-cell battery I've got 5+ hours with no problem. Everything works fine excepts for microphone. I hope some update will help with that.

And I've got a question: does anybody know, if wifi in S10e supports monitor mode? I wasn't able to run kismet with any driver.

---

### Post by vauge on 2009-04-29
> **vauge said:**
> Installing Ubuntu 8.10 was very pleasurable experience. Simple and within minutes I was up and running.

Wireless out of box!

Zero issues. 
Have not tested the mic, but cam works well with cheese.

Edit:
Free wireless is not an issue. Login to home WEP or WPA has zero issues - works flawlessly.

WPA2 - College wireless that requires authentication using wpa_supplicant, freezes then locksup requiring battery removal.
I think I read it is an issue with Intrepid and 2.6.27-11-generic kernel.

Issue remains for Jaunty and authentication for college wireless. Everything else, is flawless and I'm amazed at the processing of this netbook. I can run on the guest account at college, but if I am authenticated it would be better. 

I've had OpenOffice work processor opened, Gimp editing 2 pics, and FireFox with 5 tabs, all while listening Banshee streaming 128k signal. Not a bit sluggish. It would have been sluggish on 8.10.
I have 2G memory stick but stock 160 HD.

> How is the processing power on these with Jaunty? Does it feel the least bit sluggish? How is it as a media player, meaning does it play movie files without any frame loss?
I've watched an AVI file without skipping and sounded great. 

I love this thing!!

---

### Post by lemmyc on 2009-05-02
Hi,
I am dual booting XP Home and Ubuntu Netbook Remix (Jaunty) on my S10e.
UNR is looking really good so far.
One issue I've found is trying to get audio working under Wine. 
I wanted to try Spotify with UNR - but I'm not getting any sound out of the Wine config panel.
Anyone had success with audio in Wine? If so what settings did you use?
Thanks.

---

### Post by lemmyc on 2009-05-03
OK, my mistake. The Wine "test audio" button doesn't make any noise, but sound in Spotify works fine anyway.

---

### Post by Hoora on 2009-05-05
Hey what about the two-finger touchpad that this machine is capable of on XP? And scrolling while doing the circle? Is it possible to enable it or is it just *not supported* yet? 

I have tested the built-in mic on skype but it does not record the sound. You can only make it to "hear" the sound and directly sending it to the speaker, making it to feedback. Has anyone tested the alternative soundsystem to ALSA, OSS if I remember the name correct?

---

### Post by exorcism on 2009-05-08
i just got my s10e today an immediately put ubuntu on it over the suse enterprise it came with.

i must admit i tried the netbook remix first but i personally didn't like the feel, so i just installed jaunty desktop edition. 

out of the box everything worked. the only problem i experienced was making the internal mic work with skype. it was clearly recognized as hardware, since when going to audio properties you could adjust its level, both microphone and internal mic, with respective boost levels. 

after searching and searching i tried upgrading the alsa as instructed here:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

rebooted and then worked.

it was really important to me to make skype work. otherwise, after using for about half the day i can say i really like my ideapad with jaunty:)

---

### Post by exorcism on 2009-05-08
btw... i forgot to mention i really hate how loud the fan is...

searching around many people mention that an upgrade to bios 57 would do the trick and allow to set the three step temperature limits from bios. 

mine got delivered with the 51 bios version.  i've never done a bios update.

anyone has any experience with this? what bios version did your S10e )mind the E :) come with?

---

### Post by jrc4ever on 2009-05-08
I'm using the newest UNR, but I somehow cant get my Mic to work :-(

Can someone help me please?

---

### Post by thedigger on 2009-05-09
Just found this thread on a google search for "ubuntu s10 microphone skype", looks like a lot of people are having the same issue I was getting.

I found this page:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344627)

Post from Oliver Horn advises adding:

```
options snd-hda-intel model=basic
```
 into /etc/modprobe.d/alsa-base.conf

This worked for me on 9.04 :guitar:

---

### Post by Donnut on 2009-05-20
I got the lenovo a week ago, and at first had no problems, just this morning the battery icon stopped working.  After a couple of unsuccesful restarts, I figured it out, it'd not ubuntu's fault, rather the hardware.  Shut down ubuntu on battery, plug the book in, wait for the orange charge light to pop on, then start up the 'book.  Works perfectly!

---

### Post by daveb272 on 2009-06-10
Has anyboudy had any issues wih installing ubuntu on the s10?  I have tried multiple cd's, different burning speeds, different versions of ubuntu on a flash drive, but it all boils down to a input/output error durring install.  Anyone had this problem?

---

### Post by NuahHuan on 2009-06-17
I have recently installed UBUNTU 9.04 onto a Lenovo S10e Ver 4068-4AG - Absolutely no experience with UBUNTU and still thinking that most posts are speaking a different language I quote "2.6.27-11-generic kernel" doh... maybe with time this speak will become familiar.

Everything works OK WIFI, LAN Card Reader, Sound, webcam, screen resolution, sleep and hibernation modes - to be honest was easier to put UBUNTU onto it than to get it to work with Windows XP Pro which I have installed onto a separate 120Gb SATA disk. 

I now know everything on the S10e works with XP Pro albeit after a lot of searching for drivers etc althougth most can be downloaded off the lenovo site - even managed to flash the BIOS but had to use the Windows application for this as my expertise with UBUNTU is miniscule but this is why I purchased the notepad - to learn UBUNTU - Linux etc - as the S10e was supplied with SUSE Linux - but I found this more problematic to register for some unknown reason - although I managed it in the end but I did not like the idea of a paid support subscription just to learn LINUX hence why I went for UBUNTU.

The only problem I have is with the internal microphone - it works as is testiment to the feedback squeal I get with the controls up high - but it will not work with sound recorder and it refuses with SKYPE. I have tried messing with the various input volume settings etc but no success!!

I have read some of the posts re how to fix the microphone problem which appears to be something others have experienced - but to be honest - I don't understand how to implement the proposed solutions

I have also downloaded the UBUNTU studio .iso have extracted it but for the life of me have not a clue how to install it. Read about synaptic package manager - sorry - it uses a different logic to what I am used to with Windows XP where I could have sorted the installation in seconds.

Anyone with any suggestions for how I can solve the problem with the microphone (simple speak please!!!) I would be most grateful as I can then use SKYPE videocalls as the video and sound does work

If there is a good link to describe (again simply) how to install the Ubuntustudio.iso which I have extracted then that would be great.

Having said that - I am surprised how good UBUNTU is - even synchronises with our exchange server at work using Evolution mail - very impressed 

Hence a personal "Goodbye" to OUTLOOK 2003 although I will have to use it for work

Goodbye and that ends my first ubuntu post hope it is helpful to someone - hope someone can help me!!

):P

---

### Post by nilfilter on 2009-06-18
As a beginner, you did *very* well so far, but you will definitely need to read up the basics of managing a Ubuntu system. As you said, it is totally different to XP.

> **NuahHuan said:**
> The only problem I have is with the internal microphone - it works as is testiment to the feedback squeal I get with the controls up high - but it will not work with sound recorder and it refuses with SKYPE. I have tried messing with the various input volume settings etc but no success!!IIRC, this problem is due to the old Alsa version (1.0.18) used in Ubuntu 9.04. Skype works fine on my S10e, but I am using self-compiled kernels (2.6.29.1 & 2.6.30) which come with newer Alsa drivers (Alsa = Advanced Linux Sound Architecture). Sound quality over the internal microphone is acceptable but not great. 

**My best advice for the moment is to use a headset until you have sorted out the internal microphone issues.**

> **NuahHuan said:**
> I have read some of the posts re how to fix the microphone problem which appears to be something others have experienced - but to be honest - I don't understand how to implement the proposed solutionsHave you read the *[Alsa Upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")* thread? Yes, it's a rather lengthy thread but I am afraid you will need to read the first post from cover to cover ;)
It basically involves downloading the *AlsaUpgrade* script and executing it. Extract the file to your home folder, open a terminal and make it executable:
chmod +x name-of-the-extracted-file
Then run it:
sudo ./name-of-the-extracted-file
If you do run into problems, post your questions to that thread since it is more likely to be heard by people who can answer your questions.

> **NuahHuan said:**
> I have also downloaded the UBUNTU studio .iso have extracted it but for the life of me have not a clue how to install it. Read about synaptic package manager - sorry - it uses a different logic to what I am used to with Windows XP where I could have sorted the installation in seconds.You don't need Ubuntu Studio to make Skype work. It is a distribution of its own such as Xubuntu, Kubuntu etc., and is aimed towards musicians, DJs.
Distributions such as Ubuntu provide Linux software in so-called packages. Use Synaptic package manager to install/remove/update software:
*System | Administration | Synaptic Package Manager*

Good luck!

---

### Post by treeingwalker on 2009-06-23
I have also seen this while using SSH.  This was, however, only with the wired connection.  Not had any problems with the wireless.

---

### Post by treeingwalker on 2009-06-23
Using UNR based on Jaunty, and have not experienced any significant problems.  Most issues I have experienced have been due to insufficient understanding of the capabilities of the hardware.

---

### Post by mgmiller on 2009-06-27
> I have also downloaded the UBUNTU studio .iso have extracted it but for the life of me have not a clue how to install it. Read about synaptic package manager - sorry - it uses a different logic to what I am used to with Windows XP where I could have sorted the installation in seconds.

You don't need to download stuff off the net and then install it.  This package is in the repositories for Ubuntu.  Think of them as trusted libraries of software.

To install it, run Synaptic Package manager as you did before, put ubuntustudio in the quick search box and scroll down to ubuntustudio-desktop.  Put a check in the box next to it and then click the big green apply button at the top.

This will automatically keep the ubuntu studio up to date as well as install it easily.

As noted earlier, you don't need this package to run skype.  I assume you want it for something else.

---

### Post by treeingwalker on 2009-07-31
I get about 4 hours of battery, more like 4.5 to 5 with the backlight off, and the CPU at half speed.

---

### Post by Yee1 on 2009-08-18
Hi everyone 
I recently installed UBUNTU on my S9 Ideapad but I am getting a lot of problems with the internal mic. I am new using this kind of system. I have expended several hours trying to figure it out but I haven’t been able to.  I tried most of the sugestions in this forum but still nothing
Does anyone have an advice?

---

### Post by plainfaced on 2009-10-26
1st post. I thought I would post here.
 
Just setup Ubuntu NBR on my S10.. I had actually done it months ago, but bricked it - Well as far as i was concerned it was bricked... Im very much a Linux noob.
 
I almost bricked again today.. It seem whenever I play with gparted, i will go to reset, and the S10 doesnt boot??? Anyway.
 
Pretty much everything works out of the box with Ubuntu NBR. I love the layout of NBR.
 
I just now have to learn -
some sudo commands
how to install software with the various tools/update utilities
and almost everything else.
 
Will be asking a few questions in the next few weeks im sure. But wanting a new hobbu, and i think Linux is going to be it. :p

---

### Post by ydeardorff on 2012-02-29
I installed ubuntu 11.10 from a USB thumb drive, with a nearly perfect install.

However I can find no solution for fixing the audio.

When I type in terminal aplay -l i get 
aplay: device_list240: no soundcards found...

Any help here?

On another thread I found the lenovo ideapad is supposed to use the conextant 5051 drivers.

Id really like to get this last thing fixed

Thanks

---

