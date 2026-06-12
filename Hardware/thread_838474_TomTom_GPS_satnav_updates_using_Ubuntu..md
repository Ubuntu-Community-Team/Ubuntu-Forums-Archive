---
title: "TomTom GPS satnav updates using Ubuntu."
date: 2008-06-23
forum: Hardware
---

### Post by chris_andrew on 2008-06-23
Hi,

I have an old TomTom satnav unit, and I'd like to upgrade the firmware and/or maps.  

I can't use TomTom HOME, because it only supports Windo$e and Mac.  Has anyone found a way to get updates and copy them to TomTom's, using USB?

Cheers,

Chris.

---

### Post by buddah1620 on 2008-06-25
Me, and my dad are having the same problem.  This one of the few things that keep us from going windows free.

---

### Post by buddah1620 on 2008-06-25
Ok what I have learned is: Tomtom's themselves are Linux based.  HOWEVER.... Tomtom home will only run on Windows, and mac.  Won't run in Wine, or virtual box. :(  I wrote a letter to Tomtom support:

I am not complaining, or bashing.  However I would respectfully request you please begin Linux support for TomTom Home.  I can't seem to run it in Wine, or in windows emulators.  I understand TomTom's themselves are Linux based.  Myself, I run Ubuntu Linux Version 8.04 Hardy Heron.  With the dissatisfaction of Vista, XP becoming obsolete, and the price of either of them being inhibitive(and ridiculous); Linux is gaining popularity as a mainstream operating system.  Ubuntu Linux especially since it is free, and has excellent support via web based forums.  Once again, would you please consider creating a Linux distribution of TomTom home.  If you need any help or advice please feel free to contact me,  [http://www.ubuntu.com/](http://www.ubuntu.com/) or the thousands of programmers at [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)

My regards,
Buddah

The only thing I can think of is to send this or your own version to Tomtom.  I'm going to start a new thread titled Tomtom petition. That has this same letter, with a link to Tomtom.

---

### Post by Peter09 on 2008-06-26
I use virtualbox to run a copy of XP for my TomTom.

PC

---

### Post by buddah1620 on 2008-06-27
really?  I had read posts of others having problems doing this.  Maybe they weren't configuring it right or something.  But still doesn't it seem a bit ironic that a Linux based program, doesn't run in linux?

---

### Post by spegru on 2008-08-31
I would also like to do this.
Yes it seems the tomtom device runs linux.
Look at [http://www.tomtom.com/page.php?Page=gpl](http://www.tomtom.com/page.php?Page=gpl) for details. Loads of stuff thee ad I note in particular that is can run mplayer for video!

Anyway. There is no special surprise about the tomtom software supporting only windows (I guess we're all used to that) - but what it does show is that it is highly probable that a standard protocol is used to communicate with the device, and also probably with tomtom servers. Now if we could just find out what it is.........
 
What's the bet it's FTP or HTTP to connect to the servers, and that then the new image is placed into the root of the device using USB (like so many MP3 players) so that it reboots into the new version

Just need a few details. I am sure it cant be that hard.
Maybe running the tomtom software on a captive XP in virtualbox will reveal something...........

---

### Post by IntuitiveNipple on 2008-08-31
This is an interesting issue :)

Can you capture some information for me, it might help figure things out so TomTom Home can detect the device.

Run this command and then plug the TomTom device in:
```

sudo udevmonitor --environment | tee tomtom.log

```
Press Ctrl+C to interrupt the program.

Create a compressed log file:
```

gzip tomtom.log

```
and attach the resulting "tomtom.log.gz" to a message here.

I installed the current [latest TomTom Home 2](http://download.tomtom.com/sweet/application/home2latest/TomTomHOME2winlatest.exe) (v23.1.92). The installer throws a couple of error-dialogs about missing C runtime libraries but just pressed the Okay button and carried on; it completes the install.

I ran TomTom Home from Wine (v1.1.2) and it starts fine.
```

wine "C:\Program Files\TomTom HOME 2\TomTomHOME.exe" 

```
There appears to be an issue with connecting to the TomTom manual site ("Read the manual for my device"). It tries to open the link [https://home.tomtom.com/urlredirect/1?locale=en-GB&country=GB](https://home.tomtom.com/urlredirect/1?locale=en-GB&country=GB) but wine's iexplore locks-up without a window. Checking the running tasks it looks like the remote procedure call service is getting stuck.

There's another issue at exit which also causes it to remain in memory and requires killing.

---

### Post by spegru on 2008-09-01
I made the logs (attached to this post) as you suggested but I do not know what to make of them.

On the other hand I can report that TomTom Home installs and runs ok, both under Wine and Virtualbox. 

_Virtualbox_
However, the virtualbox version  is unable to connect to the TomTom device so far. I assume there is something wrong with USB. It seem there is a special module for virtualbox that I do not have.

_Wine_
The Wine version can see the device ok - but I was reluctant to enter any updates to it becuase my TomTom Home CD is v1.6 which dates from May 15 2007 and it certainly seems out of date expecially since my device 720T is not listed (the closest one seems to be the 715). Surprising since this is the one it came with.

At first I was unable to download any update for Tom Tom Home from their website. however i discovered that although the link did not appear in either Opera or Firefox for linux (even when set to identify as Internet Explorer), it does appear for both browsers when on Windows

So I had to use windows to get link to the specific url, rather than the select windows, apple etc - and then I could enter it directly into opera for linux. BTW this is the link: [http://download.tomtom.com/sweet/application/home2latest/TomTomHOME2winlatest.exe](http://download.tomtom.com/sweet/application/home2latest/TomTomHOME2winlatest.exe)

However although I sucessfully installed the new TomTom Home software under Wine it did not recognise the device


**Conclusion**
So I am stuck again!

BTW I am running Kubuntu 8.10 and everything is default.

---

### Post by spegru on 2008-09-01
My log file failed to attach. Maybe it will this time

spegru

---

### Post by IntuitiveNipple on 2008-09-01
> **spegru said:**
> My log file failed to attach. Maybe it will this time

spegru
That's great, thanks. I'll find some time to do some experimentation see if I can find a permanent solution for connecting devices. 

I run TomTom Navigator 7 on a Toshiba E800 PDA so updates for it are handled totally differently, but it will be interesting to see if I were to plug in the memory-card that has TomTom on it, whether I can fake some udev rules to make TomTom Home think it is a TomTom device.

---

### Post by nicedude on 2008-09-01
Hey Budda sorry to hear of your troubles but when you say this

 But still doesn't it seem a bit ironic that a Linux based program, doesn't run in linux?

Its not a linux based program it is a device that uses linux for its OS, but the application that they have written to load it and manage it is written for Windows and MAC not Linux and that is where the problem comes in. 

I really like your letter to them as if more of the people who run into these sorts of non support complained then I think companies would listen. I always like to point out one of their competitors that does support Linux and say that I am sorry that the next such gadget will regretfully have to be that company and I will have to suffest that company to clients and friends as well. Lost sales etc is about all that ever will make a corporation do something as they worship the dollar and don't care much past that.

Goodluck with your problem though

---

### Post by spegru on 2008-09-01
> **IntuitiveNipple said:**
> That's great, thanks. I'll find some time to do some experimentation see if I can find a permanent solution for connecting devices. 
.

In fact the tomtom does appear under linux and you can see all the innards of the device. With an SD card inside (this model has a slot), that does too. So I am sure it's posible to add/update anything - if we just knew what to do.

It would all be automatic if we could just use the tomtom home software - so it's disappointing that whereas the older version of tomtom home under wine could see the device, (although you had to select the model from a list - and mine was not listed) the new version (also under wine) cannot - it's trying to auto detect the model

so near and yet so far...........

---

### Post by Peter09 on 2008-09-01
I am running the TOMTOM application in XP in VirtualBox. It works fine. The only thing you must make sure of is that it does attach to the USB drive when the TOMTOM is attached. Read the VirtualBox manual for use of the USB drives - it works well.

PC

---

### Post by buddah1620 on 2008-09-02
wow, I'm subscribed to the thread, and just got an email now saying I have replys.... Thank you nice dude for your reply.  As for virtual box.. that seems like the best solution(for other things as well), I've had problems getting that working.  I haven't had the time to tinker with it due to girlfriend and college semester starting.  something about I am not authorized user or something.... I read something about being able to add users in the menu but didn't see that option...  Anyhoo I'll get to it one of these days...  What I think would be better is if Tom tom made the interface software to support Linux.  Ubuntu specifically.  Since it is custom written (device and interface), and they use Linux kernal with the device its self, you know those software engineers know how to do it... it is possible.

---

### Post by Ubunt2_User on 2009-03-17
Hello everyone. First Time Poster.  I have VirtualBox running, with USB support.  I can see my TT ONE XL in the virtual WinXP sp3, but I cant get the latest version of TT Home to install!  I dont even get any error messages...nothing seems to happen.  This is frustrating because it is now my last link to Windoze.

Thanks in Advance!

=============
Intrepid Ibex
2x AMD Turion(tm) 64 X2 Mobile Technology TL-60
GeForce 7000M / nForce 610M/PCI/SSE2/3DNOW! 177.82
ATA Hitachi HTS54252 / Optiarc DVD RW AD-7530B

---

### Post by euriconeto on 2009-03-26
Hi There,

I have signed the petition and was wondering if there any news about Linux support for TomTom One. Does any one has learnt how to install TomTom Home at Ubuntu?

Cheers

---

### Post by Markus498 on 2009-10-12
I found a really useful How To guide for getting USB to work with Virtual Box. Hope this helps.

[http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu)

---

### Post by buddah1620 on 2009-10-14
Thanks Markus!  Unfortunatly, someone busted out one of my wifes windows to steal my tomtom only a few days before our wedding this last may.  So I can not test this method for myself.  Readin th site it seems to have worked for at least one person.  Maybe someone from the forums could try it for us.

---

### Post by Payteer on 2010-03-18
Has anyone followed up on this, as it seems to have been going somewhere.

---

### Post by buddah1620 on 2010-03-19
I still have not gotten a tom tom. And no one has pm'd me or messaged me.

---

### Post by spegru on 2010-04-06
I am around and just re-found this thread. I havn't been in for a while due to not using my car much recently but my wife has been on at me to update the device and I myself am sick of poor performance from the bluetooth hands free due to too low volume - so back into harness or at least investigation mode again.

I'm running Ubuntu 9.10-based Linux Mint 8 now and can report that as before I can see into the guts of the device and its on board SD card, either with either a usb simple cable or the tomtom dock. 
Loads of linuxy stuff in there, but what to do to do updates etc?

I'd love to be able to fiddle with the audio level settings. It seems tomtom dont like you to use the external audio connections for hands free - I guess because they are worried about feedback.

One thing I already did is to splice in a 3.5mm line audio jack to the internal speaker so that I can connect it externally (mono only unfort - but ok for phone). A hardware hack.

I still want to update firmware maps etc without resorting to windose though.....

---

### Post by spegru on 2010-08-03
Anyone?

---

### Post by Kixtosh on 2010-09-27
> **spegru said:**
> Anyone?Echo back at ya!

Hé hé! It seems like you might be shouting into the void. I have a TomTom XL340S Live (very similar to the One, I think, but in XL format, and with an optional monthly subscription for Live Services, such as traffic, fuel prices, red light cameras, Google search, weather, ...). I'll give this a shot later on and see how it goes. Some features only work properly when the device is updated once a week, every week.

Like someone else already posted "it seemed that this was going somewhere", and now that buddah1620 is happily married, but unhappily without a TomTom, everything does seem to have ground to a halt. It's like watching paint dry. Heck, even Logitech Harmony remotes will work with Ubuntu ... since 2008!

[http://ubuntuforums.org/showthread.php?t=781059](http://ubuntuforums.org/showthread.php?t=781059)

C'mon buddah1620! It's time to get a new TomTom, you know you really want one! You can even find them for about $100 these days, and they're even better than ever. That thief really did you a favor when you think about it!

Subscription added to keep an eye on any developments in the thread. The tag for tagged search is already there. I'll post back with my experience once I get my new desktop ordered and set up to experiment with.

---

### Post by spegru on 2010-10-05
I guess it would be educational to use linux to look into the guts of the machine, update it on windows and then look again to see what changed
It might even be possible to look into the windows installation discs to see what's there

---

### Post by Kixtosh on 2010-10-06
> **spegru said:**
> I guess it would be educational to use linux to look into the guts of the machine, update it on windows and then look again to see what changed
It might even be possible to look into the windows installation discs to see what's thereThat might be OK for updating maps and stuff, but I'm not sure about Live Services. You have to log in to TomTom Home with your account e-mail address and password for Live Services to be correctly updated (basically, it has to be able to check whether you are currently paying the optional monthly subscription for premium services).

---

