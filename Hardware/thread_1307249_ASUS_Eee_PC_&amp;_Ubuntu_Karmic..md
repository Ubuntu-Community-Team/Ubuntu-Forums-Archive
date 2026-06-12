---
title: "ASUS Eee PC &amp; Ubuntu Karmic."
date: 2009-10-30
forum: Hardware
---

### Post by 00b00nt00 on 2009-10-30
I want to start this thread to inform users of said computers of potential difficulties with Karmic. Here goes:

Eee PC 900HA:

* Wireless adapter will toggle off but not on again. Reboot required to get Internet.

* Loss of network activity after suspend. Needs reboot to recover Internet.

* F5 does not toggle between panel & external display.

---

### Post by cypresstwist on 2009-10-31
Also, my Karmic doesn't mount SD cards automatically on my EeePC 701.

---

### Post by Saiph on 2009-10-31
my karmic work fine, since beta
When I install it, some packages are downloading. It was about 380MB and then all OK, but external output do not work.
Any sugestion about it?
I use eeePC 901. BOOT is about 10 seconds.

---

### Post by coffeecat on 2009-10-31
> **cypresstwist said:**
> Also, my Karmic doesn't mount SD cards automatically on my EeePC 701.

It seems that experience varies. My EeePC 701 with a fresh install of Karmic NBR is mounting SD cards just fine.

> **00b00nt00 said:**
>  Eee PC 900HA:

* Wireless adapter will toggle off but not on again. Reboot required to get Internet.

* Loss of network activity after suspend. Needs reboot to recover Internet.


I know you are using a 900, but just for the record, on my 701 I don't have to do a reboot for either of those. Wireless toggles back on with Fn+F2 and NM reconnects after wake-up from suspend.

---

### Post by bornagainpenguin on 2009-10-31
I can confirm the F2-WiFi bug...

Fewt warned us about this on his blog:[http://www.fewt.com/2009/10/dear-mr-shuttleworth-canonical-and.html](http://www.fewt.com/2009/10/dear-mr-shuttleworth-canonical-and.html)

He says the developers were told about the issue but decided it was more important to release on time than to deliver a working product.  I'm really disappointed with them on that.  I'm considering moving to Debian with the eeebuntu team when they do, so as to avoid this kind of thing.

--bornagainpenguin

PS: for absolutely no known reason Straw Feed Reader works again in this release.  As far as I can tell nothing has changed, but now it works again.

---

### Post by riseringseeker on 2009-10-31
> **Saiph said:**
> my karmic work fine, since beta
When I install it, some packages are downloading. It was about 380MB and then all OK, but external output do not work.
Any sugestion about it?
I use eeePC 901. BOOT is about 10 seconds.

I sure wish I could say that about the boot time.  A clean install of 9.10 on our 900 at least *quintupled* the boot time (now well over a minute), shut down time also significantly worse.  

I too am getting the battery broken message another poster reported, though the battery icon says it's fully charged, and has run for 30 minutes or so on just the battery.  

Overall I am not at all happy with the install - I am going to put 9.04 back on, unless someone has an idea how to cut the boot time down to a reasonable number of seconds, and/or has a way of fixing the broken battery report...

Did anyone have a "crash detected" during the install?  I had this on both UNR and regular 9.10 while installing on the 900, I wonder if the usb writer hosed something, but it did say there was already a bug report for it - though I did not see a crash while installing on a laptop from a CD. (desktop will have to wait a couple of days.)

---

### Post by whitefort on 2009-11-01
Well...  APART from on my EEEPC, Karmic has performed brilliantly so far on all my other machines (except for a much longer boot time than Jaunty).  

But on my EEEPC 901 it's been an utter nightmare.

First the install process kept failing for various reasons (never the same twice).  Then when I finally got it to install (using ext2 on the disks was the only thing that seemed to work), it was fine up to log-on.  

After logging on, it can be up to 4 minutes before the desktop appears.

Then it gives that message to tell me my battery is damaged or broken (it isn't).

And then it appears to be totally random whether it will see my wifi card or not.

Jaunty was superb on this little machine, but I've really fed up with all this messing about.  Karmic can stay on my other machines, but the EEEPC is going back to Jaunty as soon as I finish typing this.

(at least I'll have a pretty, professional looking login screen again, instead of that ugly spotlight thing)

Shame, because the EEEPC is the one I carry around specifically to WOW my Windows friends with the Linux eye candy.

(PS, Riseringseeker - yes, I noticed that crash icon during install too.)

---

### Post by riseringseeker on 2009-11-02
> **whitefort said:**
> Well...  APART from on my EEEPC, Karmic has performed brilliantly so far on all my other machines (except for a much longer boot time than Jaunty).  

But on my EEEPC 901 it's been an utter nightmare.

First the install process kept failing for various reasons (never the same twice).  Then when I finally got it to install (using ext2 on the disks was the only thing that seemed to work), it was fine up to log-on.  

After logging on, it can be up to 4 minutes before the desktop appears.

Then it gives that message to tell me my battery is damaged or broken (it isn't).

And then it appears to be totally random whether it will see my wifi card or not.

Jaunty was superb on this little machine, but I've really fed up with all this messing about.  Karmic can stay on my other machines, but the EEEPC is going back to Jaunty as soon as I finish typing this.

(at least I'll have a pretty, professional looking login screen again, instead of that ugly spotlight thing)

Shame, because the EEEPC is the one I carry around specifically to WOW my Windows friends with the Linux eye candy.

(PS, Riseringseeker - yes, I noticed that crash icon during install too.)

Well, though I am sorry it did not work for you, I am glad to hear I am not the only one with troubles on an eeePc.  Was beginning to think it was something I did.

I did give it every chance I could.  New clean install, re-install 9.04 and upgade, different images, loaded the image on to the USB stick differently.  Tried the same thing with 9.10 desktop and had the same problems.

The installation itself took forever.  When I was putting 9.10 (either version), particulary on the partitioning screen, it took a **long** time to scan and rewrite the partitions.  Having switched back and forth I would say it took at **least** 3 times as long on that screen alone.

I have gone back to 9.04 on the netbook.  I **love** 9.10 on my laptop.  Boot time on the laptop is not significantly different for me, and I would have to install 9.04 again to take a stop watch and see if one is faster than the other.  My guess is it **might** be a few seconds slower.

I assume I will on my desktop as well, once I tackle that chore.  I am waiting for information on why the desktop does not have sound with the live CD, as well as just being installationed out.  

The great thing is that I purchased both the laptop and desktop from [System76]("http://www.system76.com/"), they do a fantastic job of supporting linux on all their machines.  I expect an e-mail from them today about the sound thing.

---

### Post by fewt on 2009-11-02
> **riseringseeker said:**
> Well, though I am sorry it did not work for you, I am glad to hear I am not the only one with troubles on an eeePc.  Was beginning to think it was something I did.

I did give it every chance I could.  New clean install, re-install 9.04 and upgade, different images, loaded the image on to the USB stick differently.  Tried the same thing with 9.10 desktop and had the same problems.

The installation itself took forever.  When I was putting 9.10 (either version), particulary on the partitioning screen, it took a **long** time to scan and rewrite the partitions.  Having switched back and forth I would say it took at **least** 3 times as long on that screen alone.

I have gone back to 9.04 on the netbook.  I **love** 9.10 on my laptop.  Boot time on the laptop is not significantly different for me, and I would have to install 9.04 again to take a stop watch and see if one is faster than the other.  My guess is it **might** be a few seconds slower.

I assume I will on my desktop as well, once I tackle that chore.  I am waiting for information on why the desktop does not have sound with the live CD, as well as just being installationed out.  

The great thing is that I purchased both the laptop and desktop from [System76]("http://www.system76.com/"), they do a fantastic job of supporting linux on all their machines.  I expect an e-mail from them today about the sound thing.

When you go back to Jaunty or Eeebuntu 3 and follow the xorg and kernel update thread over at Eeebuntu and your Eee will run a hell-of-a-lot better than it will with karmic on it.

[http://forum.eeebuntu.org/viewtopic.php?f=7&t=3866](http://forum.eeebuntu.org/viewtopic.php?f=7&t=3866)

When you are done you'll have 2.6.30, and xorg intel drivers 2.9.  There will be little other advantage to upgrading to 9.10 except Gnome 2.28, and lots of bugs.

---

### Post by WenSes on 2009-11-02
How does somebody made karmic boot in 10 sec? In my 901 takes about 50/45 sec (ntbk remix)

However, eveything seems to be working fine...

---

### Post by Saiph on 2009-11-03
well I try install the version 9.10 now and it is bit more longer booting 20sec, so I install ubuntu notebook remix and its booting time is 30sec. I dont understand it.
I have got eeePC901. :) too

---

### Post by jpc2769 on 2009-11-05
I tried installing Karmic on my 1005, I want to go back to Jaunty, but I can't!  When I installed Jaunty I used a USB stick, and I had left the computer set to boot from the USB first, but now not only does it not boot from the USB, but I don't have the option to hit F12 when I first turn the computer on!  The first thing I see is GRUB.  Can anyone help me?

Thanks.

Jason

---

### Post by WenSes on 2009-11-05
I don't know that model of eee, but maybe try to keep pressing esc as soon you turn your pc on will lead u to boot menu. Hope u can solve your problem.

---

### Post by jpc2769 on 2009-11-05
> **WenSes said:**
> I don't know that model of eee, but maybe try to keep pressing esc as soon you turn your pc on will lead u to boot menu. Hope u can solve your problem.

That gets me to GRUB, but unfortunately on my machine GRUB does not give me the choice of booting off the USB stick rather than the hard drive.  Is there some way to configure GRUB to do this?

---

### Post by egalua on 2009-11-05
Hi all.

Here I have a 900 eeepc and I installed karmic (netbook remix) on an external SD card.

At present I didn't try it extensively, nor I will in the next week, due lack of time :-(

Nevertheless:

Problems: 
- the annoying message reporting a broken battery (it isn't)
- it is _very_ slow to boot: standard 9.04 on the SD took about 45 seconds, now it is nearly 2 minutes!!

On the other side:
every other thing I tried up to now works seamless. 
wifi, webcam, all the function keys (included wifi on/off), lcd+external monitor (this one, better than xandros).
Shutdown is very quick.

I would like to substitue xandros with UNR, but I need to solve the booting time problem, at least.

I didn't try suspension (I never use it) nor hybernation.

---

### Post by WVillet on 2009-11-05
Ive got a EEE 2gb surf and want to install it on a SD card.Managed to do that with all the previous versions and easy peasy. But the installer just hangs wehn gparted starts up during the installation process its almost more annoying than the blue screen of death.

anyone who can help please give advice I think the new netbook remix looks awesome and its live boot speed is impressing

---

### Post by skotos on 2009-11-06
My 901 installation went well from the beginning - see [http://ubuntuforums.org/showthread.php?p=8257071#post8257071](http://ubuntuforums.org/showthread.php?p=8257071#post8257071) for the steps I have followed.

I found three problems:

[LIST=1]
[*]broken battery (false)
[*]wrong second external LCD support (in non mirrored output)
[*]broken (at some point!) wireless connectivity
[/LIST]

---

### Post by barrieluv on 2009-11-15
> **egalua said:**
> Hi all.

Here I have a 900 eeepc and I installed karmic (netbook remix) on an external SD card.

- it is _very_ slow to boot: standard 9.04 on the SD took about 45 seconds, now it is nearly 2 minutes!!

I didn't try suspension (I never use it) nor hybernation.

I installed to SSD, boot time is appoximately 40 secs. 
However, I initially installed to a Sandisk Class 6 SDHC and boot time was knocking on 2m30s!

All of my hardware works well (and has done since Alpha 6) and the new video drivers are excellent.

Most of the hotkeys are supported:

Fn+F1 works perfectly, rejoining my wireless network on return from sleep.
Fn+F2 also works perfectly.
Fn+F3 + F4 (brightness down/up ) work and an OSD appears.
Fn+F5 works. I hooked up the TV and cycled through some different modes. It needs configuring somewhere along the line, but it does work.
Fn+F6 is untested. I don't really know what it's supposed to do.
Fn+F7 + F8 + F9 (sound mute/down/up) work and an OSD appears.

I do, however, suffer from the Broken Battery pop-up on login.

Overall, the best fully featured distro I've tried on this machine.

---

### Post by chrisme52 on 2009-11-15
I'm looking to buy an 701. Whats the best release to run with? Everthing works fine on these models?

---

### Post by Sven6210 on 2009-11-16
I haven been using Ubuntu NBR 9.10 as a Beta since 11th October and was very happy with the installation. I never faced any real problem and nearly everything worked out of the box on my EeePC 900a. I only needed to do one patch in order to get the microphone to work and this patch was already required in Ubuntu 9.04

This weekend I reinstalled the final release of Ubuntu 9.10 one more and it once more went smoothly without any problem and I only needed the one microphone patch.

All things that work well:

[LIST]
[*]SD card reader
[*]wireless key (I can even toggle it on and off)
[*]all other function keys
[*]Sleeping mode and on wake up the wireless connection is reestablished
[*]the external screen works very well
[/LIST]
Since I patched the ALSA configuration file also the microphone and Skype are working very well.

EeePC users that have not yet tried Ubuntu 9.10 should try and not get demotivated from this forum. I think Ubuntu 9.10 is the best Ubuntu ever and I am amazed by the out of the box support for my EeePC 900a. I used to use eeebuntu 3.0 NBR but I abandoned it since Ubuntu 9.10 works so well out of the box.

Please do not hesitate to contact me if you have further questions.

---

### Post by jocheem67 on 2009-11-17
;)
I ditched Ubuntu for Arch on my 1005HA-H..I was unhappy with the speed of UNR Karmic, and I prefer a standard gnome over the netbook interface.
I was impressed nonetheless by UNR, very user-friendly and pretty stable..

---

### Post by madengineer on 2009-11-17
I actually had the same issue with wireless not coming back after suspend/resume on my Eee 900A with Debian. I was able to fix it using the suggestion on [http://elijahr.blogspot.com/2008/03/debian-eeepc-suspend-issues-with.html](http://elijahr.blogspot.com/2008/03/debian-eeepc-suspend-issues-with.html) to add lines to /etc/acpi/actions/suspend.sh. The suspend.sh on my computer was a little different from what was described; instead of
```
pm-suspend --quirk-s3-bios --quirk-dpms-on
``` it said ```
$SUSPEND_METHOD $SUSPEND_OPTIONS
``` However, the principle was the same: before that line, which does the actual suspend, add ```
/etc/acpi/actions/wireless.sh off
/etc/init.d/dbus stop
``` and after it, add ```
/etc/init.d/dbus start
/etc/acpi/actions/wireless.sh on
``` This shuts down the wireless and then stops the network manager program (Wicd in my case) by stopping DBus, and then reenables them in reverse order after the machine comes back from suspend. I don't know if this will work if you can't turn wireless back on using Fn+F2, but it seems worth a shot.

---

### Post by skotos on 2009-11-18
> **chrisme52 said:**
> I'm looking to buy an 701. Whats the best release to run with? Everthing works fine on these models?
I think the best release is always the latest one, currently Karmic.
Since I haven't got a 701 I think you should check the hard disk drive size.
Installing Karmic on a 3.74 GiB like mine (a 900) works well if only it is fully dedicated to the OS and the swap partition and the /home subtree are rearranged on the second and bigger hard drive.
If you do not act like this, the OS will immediately begin complaining and low disk space will continuously annoy you.

HTH :D

---

### Post by egalua on 2009-11-18
> **barrieluv said:**
> I installed to SSD, boot time is appoximately 40 secs. 
However, I initially installed to a Sandisk Class 6 SDHC and boot time was knocking on 2m30s!

My card is the same you have: Sandisk Class 6 SDHC.

Now I installed NBR on the second SSD: boot time decreased to a minute.

> 
All of my hardware works well (and has done since Alpha 6) and the new video drivers are excellent.


I also agree that all the rest works very well. I would like to erase Xandros and substitue it with NBR but I will not do this until I will have a faster boot (<30 sec) and the annoying broken battery popup bug is fixed.

BTW: is there a way to decrease the "living time" for all the popups? I find they are a little bit too persistent.

---

### Post by barrieluv on 2009-11-20
> **egalua said:**
> My card is the same you have: Sandisk Class 6 SDHC.

Now I installed NBR on the second SSD: boot time decreased to a minute.



I also agree that all the rest works very well. I would like to erase Xandros and substitue it with NBR but I will not do this until I will have a faster boot (<30 sec) and the annoying broken battery popup bug is fixed.

BTW: is there a way to decrease the "living time" for all the popups? I find they are a little bit too persistent.

Don't forget that the second, 16gb, SSD on the 900 is horribly slow.  If you were to install 9.10 on the 4gb, where you currently have Xandros, you should see a boot time of around forty seconds.

---

### Post by GeneralSpecific on 2009-11-20
Fresh install on [COLOR="Blue"]900A[/COLOR]

Installed on built in 4GB SSD with /home on SD card

Everything works very well, compared to Eeebuntu Jaunty. 
All Fn keys work, wifi works, and will reconnect at wake, screen rotates, Boot/suspend/wake/shutdown faster  

There are currently only **2 problems, both with Wifi**

Wifi will not toggle back on with the Fn+F2, but I had the same issue with Eeebuntu jaunty and had to add a command to grub/menu.lst  Following these suggestions [http://forum.eeebuntu.org/viewtopic.php?f=48&t=4004]("http://forum.eeebuntu.org/viewtopic.php?f=48&t=4004")
I'm not sure how to do similar with grub2...

Also Wifi signal strength registers about 30% lower ...though I'm not sure if that is a problem, since even with signal strength running at 40% internet seems pretty quick.  Maybe going back to the old driver from jaunty would help, but there are other threads discussing this.

I'm very happy with the install, and I'm sure that I'll get these problems fixed.

--Ryan

---

### Post by WVillet on 2009-11-21
> **chrisme52 said:**
> I'm looking to buy an 701. Whats the best release to run with? Everthing works fine on these models?

Ive got the 701 2gb surf and im running 9.10. First thing you have to be honest there is better netbooks on the market,but the 701 is really cheap and its moneys worth and so much fun.Not fun as in playing games you can buy a flash disk and a SD-Card and experiment with other linux operating systems to your hearts content.Ive got mine for 6 months now and Ive learnt more in this 6 months about linux and the tricks of the trade than the previous 3 years that ive been running ubuntu

OK back to your question.
Default Xandros: First thing the wireless and wired network manager might just be the best one ive ever seen on a open source operating system. Other features such as office works nicely but dont expect any updates. Except for solitaire games are lame but who cares. boot time is extraordinary so if your looking just to do something quickly on the internet this os is for you

next I bought a 8 gig SD card and a 4 Gig flash-disk booting from the flash disk and installing the dedicated partition on the memory card.

Easy-Peasy: A very comfortable version of ubuntu's netbook remix that is modified for eee users.I was running this version for a few months becuase i found all the traditional ubuntu versions(Netbook remix eeebuntu ect) to be very slow and shortcuts not to work as they should.Boot time was faster and shortcuts was working wich means this was the prime os for me.the only thing which irritated me was the wireless manager which it inherited from ubuntu 9.04.

Pupeee: this is a very interesting os wich loads the whole os in its ram wich makes it amazingly fast.except for the wireless connectivity theres nothing to recommend.

I am currently running ubuntu 9.10 with the netbook remix interface installed over it. Very very fast(keeping in consideration the specs of my netbook).Very very stable.Very very pretty and the best of all the wireless manager was rewritten and Im so impressed. the eee shortcuts working perfectly which means no more easy peasy. so bottemline i would recommend the ubuntu 9.10 or the netbook remix

hopes this help there is other OS Available(Cruncheee) but you will receive more support from a ubuntu based OS.

---

### Post by fugyfudy on 2009-11-22
I keep getting kernel panics with Karmic on the 1005ha.  I remembered that I had linux-backports-karmic installed, so I removed that and just let the eee stay on for a couple days.  I got to a 6 day uptime and then the wireless stopped working, I restarted and it was working fine.  Ever since I restarted it though, I've been having the kernel panics over and over again.

---

### Post by jpkotta on 2009-11-22
> **madengineer said:**
> I actually had the same issue with wireless not coming back after suspend/resume on my Eee 900A with Debian. I was able to fix it using the suggestion on [http://elijahr.blogspot.com/2008/03/debian-eeepc-suspend-issues-with.html](http://elijahr.blogspot.com/2008/03/debian-eeepc-suspend-issues-with.html) to add lines to /etc/acpi/actions/suspend.sh. The suspend.sh on my computer was a little different from what was described; instead of
```
pm-suspend --quirk-s3-bios --quirk-dpms-on
``` it said ```
$SUSPEND_METHOD $SUSPEND_OPTIONS
``` However, the principle was the same: before that line, which does the actual suspend, add ```
/etc/acpi/actions/wireless.sh off
/etc/init.d/dbus stop
``` and after it, add ```
/etc/init.d/dbus start
/etc/acpi/actions/wireless.sh on
``` This shuts down the wireless and then stops the network manager program (Wicd in my case) by stopping DBus, and then reenables them in reverse order after the machine comes back from suspend. I don't know if this will work if you can't turn wireless back on using Fn+F2, but it seems worth a shot.

I have a 1000HE.

This didn't work for me.  I instead put this at the bottom of /etc/acpi/sleep.sh:
```

/etc/init.d/wicd stop
/sbin/modprobe -r ath9k
pm-suspend
/sbin/modprobe ath9k
/etc/init.d/wicd start

```

The ath9k module was not behaving nicely when coming out of suspend; there was an error on the console from it and as soon as that error was printed, the USB mouse (not the touchpad) started misbehaving too.  If I unload the module before suspend, everything works great so far.

Karmic does have a lot of bugs.  I don't care about boot time because I *always* suspend.  I reboot for kernel updates and not much else.  But now that I fixed this, the suspend time and graphics drivers of Karmic are worth it to keep.  I wish they hadn't taken out PySol though.

**EDIT**
A better way to do it is to add ath9k to the list of modules that get unloaded at suspend.  There is no need to stop wicd.

/etc/pm/config.d/01unload_modules
```

# unload these modules before suspend and reload after resume
SUSPEND_MODULES="ath9k"

```

---

### Post by harsaphes on 2009-11-22
Noob here....just wanted to report i installed the Netbook Remix on my Asus N10J and everything is running great...no problems so far..sound and wifi are working...still feeling my way around but so far so good.

---

### Post by egalua on 2009-11-25
> **barrieluv said:**
> Don't forget that the second, 16gb, SSD on the 900 is horribly slow.  

Yes, I know.
> 
If you were to install 9.10 on the 4gb, where you currently have Xandros, you should see a boot time of around forty seconds.

Removing some useless service, I reduced boot time to about 50 seconds even from the second SSD: maybe on the first I can get close to 30...

Nevertheless, I decided to erase Xandros only when I will see a distribution working completely  bugless out of the box. Maybe I need to wait 10.04...

---

### Post by derim on 2009-11-25
After a failed initial install and some partitioning problems with the installer (I ended up using an alternate lpia image), I finally got it installed and LOVE the increase in battery life from the lpia version, as well as the WPA and WEP both working out of the box. Only 2 problems:

1) Fn-F2 wireless crash bug. Seems everyone has this though, not a big deal

NOTE: eee-control is great. solves everything. Just make sure to disable the first silver hotkey from monitor off so that it doesn't conflict with the "lock" function turned on by default in Karmic. Otherwise you can't come back too easily.

2) Where did 3-finger right clicks go? Anyone know how to get them back? I've heard changes in the .fdi file don't makke a difference, and don't even know where to start.

NOTE: there's a good post on eeeuser forum about this. And it does work!

[http://forum.eeeuser.com/viewtopic.php?pid=662717#p662717](http://forum.eeeuser.com/viewtopic.php?pid=662717#p662717)

Somehow the 2nd and 3rd clicks got switched when a patch was removed. I hope this helps! synclient needs shmconfig enabled to work.

---

### Post by madengineer on 2009-11-28
> **jpkotta said:**
> 
**EDIT**
A better way to do it is to add ath9k to the list of modules that get unloaded at suspend.  There is no need to stop wicd.

/etc/pm/config.d/01unload_modules
```

# unload these modules before suspend and reload after resume
SUSPEND_MODULES="ath9k"

```

This works on my 900 (running Debian) as well, substituting ath5k for ath9k. Thanks for the more elegant solution!

---

### Post by rkid on 2009-12-14
I have an Asus eee pc 1005ha, with ubuntu nbr karmic. 
I can't get the wireless to work, it recognises the signal and asks for the password, but there is no connection.
I have installed the backports as mentioned here:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA)

to no avail. 

Does anyone have any advice?

---

### Post by imaqt55 on 2009-12-15
I just upgraded from 9.04 NBR to 9.10 NBR on my Eee 1005-HA and am having two major problems:

1) The fan is not working right - it doesn't turn on when it should or off when it should - it only appears to turn on or off when the computer is restarted.  More detail in my post here: [http://ubuntuforums.org/showthread.php?p=8501949#post8501949](http://ubuntuforums.org/showthread.php?p=8501949#post8501949)

2) Periodically, I get disconnected from my wireless network and then it acts as if there are no wireless networks available (even though there is and it is working fine). It still shows the wireless adapter as being on.  The only thing that seems to fix it is to restart.

---

### Post by technoboi on 2009-12-16
I have an Eee PC901. Everything on the Karmic Remix works fine except for the WiFi. It does connect to the wifi but it slowly degrades and thus downloads get painfully slow. Starts on full bars, then it might jump to 2 bars, then back to full...but eventually it drops to nothing and then disconnects. I then can't reconnect unless I reboot. I can however run the 'radar scan' app. and it picks up my network and other networks in my area. I can, in the same position in my house, always get a good signal on my N95 (wifi).
So, I think that this is a software problem.
Can anyone offer any advice please?

---

### Post by nachtland on 2010-01-07
Hey all. 
I am at the end of my resources and patients. I installed ubuntu NBR karmic on my eee pc 701 4G and the sound does not work. When I run system test the sound test aplication just keeps running without making a noise or finishing. Can anyone suggest any fix?

---

### Post by technoboi on 2010-01-07
> **nachtland said:**
> Hey all. 
I am at the end of my resources and patients. I installed ubuntu NBR karmic on my eee pc 701 4G and the sound does not work. When I run system test the sound test aplication just keeps running without making a noise or finishing. Can anyone suggest any fix?

Have you checked the mixer settings?
Either install the Alsa Mixer GUI or simply type alsamixer on the command line. Check that the appropriate controls are turned up - including the headphone control. 
I'd be interested to know the result. I have the 901 but a friend has the 701. I put 8.04 on it for him but I also did a bit of fiddling by following some workarounds.
Karmic Remix on my 901 seems to be perfect, the WiFi seems OK now, just think it was a poor signal.

---

### Post by derim on 2010-01-07
Also make sure that none of your open programs (skype, pidgin, for example) are not "stealing" the audio focus. I've noticed that sometimes only one program can use the output device at the same time. While not a solution, in the interim making sure that onl the application using sounds is open can at least test whether or not your output is working.

---

### Post by spinstartshere on 2010-01-09
> **madengineer said:**
> This works on my 900 (running Debian) as well, substituting ath5k for ath9k. Thanks for the more elegant solution!

This worked for my Acer Aspire 6530G running Lucid.  Thanks.

---

### Post by arawaca on 2010-02-09
Hello everybody.  I have an eee pc 701 4G and was having some of the symptoms described on this thread: 
* Karmic crashing during install when creating partitions.  Jaunty installed ok but the partition manager took very long time (~10min). 
* SD card recognized (sometimes) but not mounted, with 'hardware error' messages in the log.   
* Crash during boot if the SD card was inserted. 
* Sound card problems, like microphone not recognized.  

What solved *all* these problems for me was to update to the latest BIOS (March/2009) from [support.asus.com. ]("http://support.asus.com")A clean install of Karmic after this update went perfect!  Wireless, SD card, sound all works well.  The new BIOS firmware disabled the webcam so I had to change that.

I hope this helps you.

---

### Post by mhpathfinder on 2010-02-10
> **WenSes said:**
> How does somebody made karmic boot in 10 sec? In my 901 takes about 50/45 sec (ntbk remix)

However, eveything seems to be working fine...
As of this writing, I believe that the 10-second boot-up goal is yet to be achieved, but it is being developed for the Ubuntu LTS 10.04 release.  LTS is short for "Long Term Support."  However, that being said, my boot-up time in Ubuntu Netbook REmix 9.10 Karmic Koala, with an Asus EEE PC 100HE, is relatively short, usually thirty seconds or less.  "Quick Boot" should be enabled in your Asus EEE PC BIOS, accessed by hitting the F2 key continuously on boot-up.  Go the Boot menu and it will be there.

Release date for Ubuntu LTS 10.04 is for April 2010.  Until then, be patient with the extra seconds of boot-up time.  It's still comparably short to the minutes of boot-up time I became accustomed to with an MS Windows system.

---

### Post by H3R3T1K on 2010-04-06
Hey guys,

I'm running the Netbook Remix of Karmic on my EEE 1005HA. Everything seems to work fine except for two things. WLAN works but it seems much slower than on my desktop (WIN XP). Sometimes I get 700 kb/s down using Transmission and the next second it's down to 0 kb/s. The other thing is that Karmic doesn't find my external DVD burner so I can't install the drivers for my printer :(

Hope you guys can help me. I'm new to Linux und Ubuntu.

---

### Post by WenSes on 2010-04-06
@H3R3T1K: I found a thread that may be useful to you, to solve your wifi problem: [http://art.ubuntuforums.org/showthread.php?t=1263764](http://art.ubuntuforums.org/showthread.php?t=1263764)

Drivers for printers usually are recognized by ubuntu itself, so try pluging the printer right to your netbook. Most of the time, the recognized hardware on ubuntu doesn't requires you to install drivers. Anyway, try searching this forum by the models of your printer and dvd burner, probably you'll be finding something. 

Good luck with your troubleshooting!

---

### Post by jpkotta on 2010-04-08
> **H3R3T1K said:**
> Hey guys,

I'm running the Netbook Remix of Karmic on my EEE 1005HA. Everything seems to work fine except for two things. WLAN works but it seems much slower than on my desktop (WIN XP). Sometimes I get 700 kb/s down using Transmission and the next second it's down to 0 kb/s. The other thing is that Karmic doesn't find my external DVD burner so I can't install the drivers for my printer :(

Hope you guys can help me. I'm new to Linux und Ubuntu.

Are you sure that there are printer drivers for Linux on the DVD?  What WenSes said is usually the case in my experience.  There was one printer at work that needed a ppd file, which is apparently the same across OSes.  I used the CUPS web configuration tool to install it.

As a workaround, you can clone the DVD to a file with another computer and copy the DVD image to the netbook (with a flash drive or network or something else).  K3B is what I usually use for optical disc copying and burning.

---

### Post by welshmike on 2010-04-16
I took delivery of an ASUS Eee PC 1000P Netbook yesterday that has XP on it.
I run dual boot Karmic and XP on my old laptop and am very happy with Karmic.
I want to install Karmic on the Netbook (dual boot with XP) and have some questions.
I booted from a Karmic live CD to see the partitioning of the Netbook's hard drive shown below.
Q1. What is partition /dev/sda2 used for please? 
Q2. Can I use the GParted in the Karmic live CD to reformat /dev/sda2 to ext4 and then install Karmic in that partition?
Q3. Is anyone running Karmic on an ASUS Eee PC 1000P Netbook or similar netbook and what is their experience please?

Many thanks in advance
Mike

[IMG]http://www.eacott.org.uk/Screenshot.png[/IMG]

---

