---
title: "Experiences with Asus UL30"
date: 2009-10-25
forum: Hardware
---

### Post by avilella on 2009-10-25
Hi,

Has anyone installed Linux on an Asus UL30?

---

### Post by avilella on 2009-10-25
I've seen in a non-Linux forum that 2 users report an almost fully working system with Karmic 9.10.

Can anyone confirm this?

> But the best of all is:
The lastest Kubuntu Karmic 9.10 Linux (Alpha 6) works like a charm! Everything is running out of the box, incl sound, lan, wlan, suspend, keys. (hdmi to be tested...)
> 
An update on the ubuntu upside-down webcam issue: the fix linked earlier in the discussion does not work on ubuntu 9.10, and the linux video developers have explicitly discouraged that approach because it requires kernel modifications. Instead, it can be fixed with a 32-bit build of libv4l version 0.6.2 or later. I built it from source and installed it to /usr/lib32. Then when running skype, I use the following command:
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype &

and presto! I no longer look like an antipode!
other webcam-using apps can be similarly prefixed with the LD_PRELOAD on the command line, and it might even be possible to put LD_PRELOAD into the systemwide profile, haven't investigated yet. Anyways, hopefully this will help someone somewhere.

Unrelated topic: I updated the BIOS to 206 to get the BIOS overclock setting. It works smoothly at 4%, but at 5% gnome fails to start on my laptop. I get a running linux and command prompt, but no gui. Maybe 5% is more than some circuitry in the Intel GMA4500 can handle?

I also have a weeeeak wifi signal with lots of connection drops.

> **avilella said:**
> Hi,

Has anyone installed Linux on an Asus UL30?

---

### Post by Magnesium on 2009-10-25
Hi avilella!

I am interested in this laptop also...we'll see if anyone here has tried it.

What's the link to that forum you quoted from? I've looked and looked and can't find it. :confused:

Thanks,
Mg

---

### Post by avilella on 2009-10-26
There seems to be 2 different Linux users on notebookreview.com:
[http://forum.notebookreview.com/showthread.php?t=418429](http://forum.notebookreview.com/showthread.php?t=418429)

But that forum is probably not the best to gather Linux users...

> **Magnesium said:**
> Hi avilella!

I am interested in this laptop also...we'll see if anyone here has tried it.

What's the link to that forum you quoted from? I've looked and looked and can't find it. :confused:

Thanks,
Mg

---

### Post by neehilo on 2009-11-03
Hi,

I installed Karmic Koala (9.10) 64 bits and it works very well out of box, including Ethernet and Wi-Fi (Atheros 9285). To get a stable and fast Wi-Fi connection, it is advised to install "linux-backports-modules-karmic-generic" packet, since the included ath9k driver is much better than the default one.

For now, the only little problem I encountered is the webcam image flipped up/down (I saw something on the net to fix it but did not test yet).

SD card reader is ok. Did not test HDMI output for now.

And the UL30A is very responsive under Karmic, quiet as fast as my previous laptop (Core2Duo T8100), and quicker than under Win 7, and very very quiet. An extremely good laptop IMHO.

   Neehilo

---

### Post by Magnesium on 2009-11-03
> **neehilo said:**
> Hi,

I installed Karmic Koala (9.10) 64 bits and it works very well out of box, including Ethernet and Wi-Fi (Atheros 9285). To get a stable and fast Wi-Fi connection, it is advised to install "linux-backports-modules-karmic-generic" packet, since the included ath9k driver is much better than the default one.

For now, the only little problem I encountered is the webcam image flipped up/down (I saw something on the net to fix it but did not test yet).

SD card reader is ok. Did not test HDMI output for now.

And the UL30A is very responsive under Karmic, quiet as fast as my previous laptop (Core2Duo T8100), and quicker than under Win 7, and very very quiet. An extremely good laptop IMHO.

   Neehilo

Hi Neehilo,

I'm glad to hear that Linux works well on the UL30. Have you had a chance to see if suspend and hibernate work correctly? Also, is there a VGA port on that laptop, or just the HDMI?

Thanks,
Mg

---

### Post by groner on 2009-11-04
Hi,

> 
I installed Karmic Koala (9.10) 64 bits and it works very well out of box, including Ethernet and Wi-Fi (Atheros 9285). To get a stable and fast Wi-Fi connection, it is advised to install "linux-backports-modules-karmic-generic" packet, since the included ath9k driver is much better than the default one.


Thanks for the tip.  I'll try that.

The HDMI output works ok, but there were a few issues:
- Chunky looking text, some of the time.  I didn't see this with the VGA output.
- Disappearing mouse cursor, some of the time.

HDMI Audio works, and the video looks fine.

> 
I'm glad to hear that Linux works well on the UL30. Have you had a chance to see if suspend and hibernate work correctly? Also, is there a VGA port on that laptop, or just the HDMI?
Suspend has had no problems for me, I haven't tried to hibernate.

I haven't found a way to disable the touchpad while I'm typing.  The Elantech PS/2 touchpad driver does not recognize it, so there is no configuring it for now.  On the plus side the default settings for the touchpad are pretty good.


Kai

---

### Post by Magnesium on 2009-11-04
Hooray...suspend works! I must be really unlucky or something, because none of the computers I have now suspend correctly under Linux. Maybe I'll break down and buy the UL30.

Where did y'all purchase yours from? You can't get it in stores, right?

Mg

---

### Post by neehilo on 2009-11-04
> **Magnesium said:**
> Hooray...suspend works! I must be really unlucky or something, because none of the computers I have now suspend correctly under Linux. Maybe I'll break down and buy the UL30.

Suspend and hibernate both work flawlessly for me. Wireless connection comes back quickly, and even the BtnX daemon with my special mouse buttons configuration is restored. Much better than before.


> **Magnesium said:**
> Where did y'all purchase yours from? You can't get it in stores, right?


From an internet shop, since the UL30 was not available in stores in my town (I am living in France), and the web shop configuration was better.

Since the 24 month on site warranty is performed by Asus, buying in store or web shop did not matter for me.

   Neehilo

---

### Post by digitalshaman on 2009-11-08
I have Asus UL30A, Ubuntu 9.10 problems that i couldnt fix:
- Touchpad Elantech Smartpad recognised as Logitech Ps\2 mouse
- Hibernate doesent work.

---

### Post by derkegel on 2009-11-08
Same here:
Asus UL30A + Ubuntu 9.10 and still not working:

- Touchpad Elantech Smartpad recognised as Logitech Ps\2 mouse

This Touchpad issue is really anoying because you can use synaptics-touchpad capabilities. For example I can change the "sensitivity" of my touchpad and this is pretty anoying when typing and accidentally touching the pad.

Otherwise, everything else works pretty fine after all the workarounds discussed here.

ad

---

### Post by TomtheWombat on 2009-11-08
I read that the Dell Mini 10 (or the Mini 10v, one of them) has an Elantech Smartpad.  I believe someone mentioned that Dell ships it out with special software.  It would be nice to use the multitouch scrolling.

I may buy a UL30a (or other ULXXa) in the next week.

---

### Post by spacecaps on 2009-11-08
Hello,

I'm looking at getting a UL30 to use with ubuntu.  Can anyone comment on battery life with light/moderate usage?

---

### Post by neehilo on 2009-11-09
> **spacecaps said:**
> Hello,

I'm looking at getting a UL30 to use with ubuntu.  Can anyone comment on battery life with light/moderate usage?

Hi spacecaps,

I get between 8 to 9 hours of battery power, with 7 to 10% remaining when I plug the AC adapter (based upon my experience, Li-Ion batteries really hate going too low on power).

I have Wi-Fi on, the USB receiver of my wireless mouse plugged-in, and use mainly Firefox, Thunderbird, Eclipse, several services (Apache, MySQL), Virtual machines (VirtualBox), and OpenOffice some times.

Neehilo

---

### Post by Magnesium on 2009-11-09
> **neehilo said:**
> Hi spacecaps,

I get between 8 to 9 hours of battery power, with 7 to 10% remaining when I plug the AC adapter (based upon my experience, Li-Ion batteries really hate going too low on power).

I have Wi-Fi on, the USB receiver of my wireless mouse plugged-in, and use mainly Firefox, Thunderbird, Eclipse, several services (Apache, MySQL), Virtual machines (VirtualBox), and OpenOffice some times.

Neehilo
That's interesting...Asus claims a battery life of 12 hours, however, I'm sure that is an idealized number (no wifi, not really using the computer at all). It would be interesting to see what the "real world" battery life is in Windows...after all, Asus may have some special Windows drivers designed to prolong battery life.

neehilo, there's some kind of physical hardware switch on the UL30 to switch it from "performance mode" to "powersave mode," right? Did that happen to do anything in Linux?

Mg

---

### Post by TomtheWombat on 2009-11-09
Reviews state about 10.5 hours total with wifi on and modest usage.  I don't think that I have seen a review state much less than 10 hours unless the screen brightness was up and they were streaming high quality video.  The ultimate battery test (DVD watching) won't work on this computer because it lacks a drive.

I have seen reviews state 13+ hours for idle, screen at minimum brightness with wifi off.  Remember that the ul30a-x#'s have smaller batteries than the ul30a-a#'s.

---

### Post by Magnesium on 2009-11-09
> **TomtheWombat said:**
> Reviews state about 10.5 hours total with wifi on and modest usage.  I don't think that I have seen a review state much less than 10 hours unless the screen brightness was up and they were streaming high quality video.  The ultimate battery test (DVD watching) won't work on this computer because it lacks a drive.

I have seen reviews state 13+ hours for idle, screen at minimum brightness with wifi off.  Remember that the ul30a-x#'s have smaller batteries than the ul30a-a#'s.
Ah, I didn't realize that there were different battery sizes in the UL30 line...I'll keep that in mind!

[Here]("http://reviews.cnet.com/laptops/asus-ul30a-a1-core/4505-3121_7-33772104-2.html?tag=txt;continue") Cnet got 6:41 on their video playback test.

Mg

---

### Post by TomtheWombat on 2009-11-09
Also reviews on Windows 7 always show better battery life than Vista and slightly better than XP.

There are three batteries, 4-cell 2200mah, 8-cell 4400mah, 8-cell 5600mah.  Up until recently all black models were ul30a-x# series with 4400mah battery and silver models were ul30a-a# series with 5600mah batteries.  However, I have seen ul30a-x4 that is silver on newegg and ul30a-a3b on Amazon that is black.  It appears that the x series sits flush with the table, but the a series battery sticks out a bit (I cannot confirm this except in pictures.)

I have seen a report that [multitouch works by default on an ul80vt]("http://forum.notebookreview.com/showpost.php?p=5461916&postcount=102") in 9.10.  It is important to note that the ul80vt switchable graphic card does not work properly in linux.  It is currently (and in the foreseeable future) not possible to disable the discrete graphics card in the bios either.  No graphics card switching currently works under linux.  That may rule out waiting for the ul30vt for linux users.

---

### Post by TomtheWombat on 2009-11-09
Also, they are quoting less battery life for the ul30a-a3b so I'm not 100% sure that the a-series always has the 5600mAh battery.  If it comes with the 4400mAh battrey, then I'm not sure how to tell if you are getting the bigger or smaller battery.  The battery details aren't always listed in the specs.

This is like when you walk into a car dealship with the EPA mileage stickers for manual transmissions on vehicles with auto (or ever worse: a different engine.)

---

### Post by neehilo on 2009-11-09
> **Magnesium said:**
> That's interesting...Asus claims a battery life of 12 hours, however, I'm sure that is an idealized number (no wifi, not really using the computer at all). It would be interesting to see what the "real world" battery life is in Windows...after all, Asus may have some special Windows drivers designed to prolong battery life.

neehilo, there's some kind of physical hardware switch on the UL30 to switch it from "performance mode" to "powersave mode," right? Did that happen to do anything in Linux?

Mg

The 8 to 9 hours I get is with a real use, with very few idle times.

I have the 8 cell 5600mAh battery, and always plug the AC adapter when reaching about 7-10%, which could give quiet 1 hour more. So my "real world" use could last about 10 hours, which I find pretty good.

With Seven, the battery gauge states about 10 hours also, and I don't known if it is accurate since I did not use Seven for so much time.

Of course in Linux you don't have Asus Powergear. I let the energy settings to the default ones, and my screen brightness is usually around 20 to 30 percent.

Neehilo.

---

### Post by neehilo on 2009-11-09
> **TomtheWombat said:**
> I have seen a report that [multitouch works by default on an ul80vt]("http://forum.notebookreview.com/showpost.php?p=5461916&postcount=102") in 9.10.

I've just tested that, multi-touch scrolling with the touchpad also works with the UL30A and Karmic Koala. I did not noticed that before since I quiet always use a mouse.

Neehilo.

---

### Post by boom2k1 on 2009-11-09
I'm using a UL30A and recently quite disturbed by the screen brightness bug. On battery, idling causes the laptop to change screen brightness. Changing the setting from power management to prevent dimming while idling apparently doesn't work. Because I worked under low light environment, I set brightness to really low. When idling, it actually changes my brightness up!

Moreover, there also seems to be another problem moving my cursor after "dimming". The expected behaviour of the laptop should be to make the laptop to return to previous setting. However, it seems to reset it to something else (probably the default under power management)!

---

### Post by TomtheWombat on 2009-11-14
> **derkegel said:**
> Same here:
Asus UL30A + Ubuntu 9.10 and still not working:

- Touchpad Elantech Smartpad recognised as Logitech Ps\2 mouse

This Touchpad issue is really anoying because you can use synaptics-touchpad capabilities. For example I can change the "sensitivity" of my touchpad and this is pretty anoying when typing and accidentally touching the pad.

Otherwise, everything else works pretty fine after all the workarounds discussed here.

ad
Here is something on fixing your touchpad in Karmic.  I don't know if it will work for the Elan pad.

[http://www.ubuntugeek.com/howto-fix-touchpad-issues-after-karmic-upgrade.html](http://www.ubuntugeek.com/howto-fix-touchpad-issues-after-karmic-upgrade.html)

---

### Post by seigenblues on 2009-11-18
Hey all,

just got the UL-30 and promptly put ubuntu on it.  Only real complaint is that the touchpad fixes don't work, and the random taps are really driving me nuts.  Any progress on this would be fantastic...

if anyone's curious, i can show you what i've tried so far.

cheers!

-seigen

---

### Post by b3n87 on 2009-11-21
> **seigenblues said:**
> Hey all,

just got the UL-30 and promptly put ubuntu on it.  Only real complaint is that the touchpad fixes don't work, and the random taps are really driving me nuts.  Any progress on this would be fantastic...

if anyone's curious, i can show you what i've tried so far.

cheers!

-seigen

Hey, im thinking of getting this laptop, can you tell me what works, and what doesnt? and What the laptop is like generally? :D

---

### Post by paf0 on 2009-11-24
> **seigenblues said:**
> Hey all,

just got the UL-30 and promptly put ubuntu on it.  Only real complaint is that the touchpad fixes don't work, and the random taps are really driving me nuts.  Any progress on this would be fantastic...

if anyone's curious, i can show you what i've tried so far.

cheers!

-seigen
 
Agreed on touchpad. I can't stand it. I tried this patch:
[https://lists.launchpad.net/asus-ul30/msg00006.html](https://lists.launchpad.net/asus-ul30/msg00006.html)

It did not work for me but perhaps it will work for someone else.

My touchpad is still being detected as a "ImPS/2 Logitech Wheel Mouse" :-(

---

### Post by fde on 2009-11-26
Does the following trick work?

[http://www.array.org/ubuntu/elantech.html](http://www.array.org/ubuntu/elantech.html)

EDIT: Of course there is a problem with the /etc/modprobe.d/eeepc file. Is there an equivalent on the UL30?

EDIT2: Maybe another solution here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882/comments/33)

EDIT3: They seem to claim it is fixed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/123775?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/123775?comments=all")
> Changed in linux-source-2.6.22 (Ubuntu):
status: 	Won't Fix &#8594; Fix Released

---

### Post by TomtheWombat on 2009-11-26
> **fde said:**
> Does the following trick work?

[http://www.array.org/ubuntu/elantech.html](http://www.array.org/ubuntu/elantech.html)



I tried to pass the elantech option, but psmouse says that it is an invalid option.

---

### Post by fde on 2009-11-27
What about that?

[http://arjan.opmeer.net/elantech/](http://arjan.opmeer.net/elantech/)

And for the previous solution, did you install the gsynaptics-elantech package?

---

### Post by TomtheWombat on 2009-11-27
> **fde said:**
> And for the previous solution, did you install the gsynaptics-elantech package?

Package was not available in the repository for amd64.  I can't figure out where the package originates from.

---

### Post by fde on 2009-11-27
> **TomtheWombat said:**
> Package was not available in the repository for amd64.  I can't figure out where the package originates from.

It's from the array.org repository.

---

### Post by TomtheWombat on 2009-11-27
The kernel config in my /boot directory says that elantech is enabled in psmouse module.

When I do a `dmesg | grep elantech' as suggested on the patch developers page, I do not get any results.  Therefore it appears that the elantech is not being detected by psmouse.  I tried to insmod psmouse with the option elantech=1, but that fails.

---

### Post by TomtheWombat on 2009-11-27
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418282](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418282)

According to the reports in this bug, it appears that the touchpad in our computers does not match type 1 or type 2.  Hopefully the patch developer will answer someone, and he can fix it without having the actual hardware.

EDIT: elantech.c only checks the firmware version.  Our touchpads may just have a new firmware.  I am recompiling the kernel now with the firmware check disabled to see for myself.

---

### Post by TomtheWombat on 2009-11-29
It appears that some work has started to debug the elantech trackpads.

[http://ubuntuforums.org/showthread.php?p=8300337&highlight=elantech#post8300337](http://ubuntuforums.org/showthread.php?p=8300337&highlight=elantech#post8300337)

---

### Post by ketilkn on 2009-11-29
I got a UL30A qx165v yesterday. Everything that matters seems to work. Booting, suspend, VGA/HDMI out, sound, mic, vmx.

I find the touchpad less annoying than this thread first had me anticipate. The button to turn it off does not work. 

linux-backports-modules-karmic-generic fixed the wireless issue for me as well. Though there seem to be the occational packet loss as evident when using secure shell.

I have now removed all stickers (lots) anvd intend to keep the laptop. The machine is great. After the "Asus recommends Windows" website and Asus dropping Linux on netbooks in Scandinavia I was sure I would never buy their products again. Glad I put my issues aside. My Macbook Pro is dead to me now :)

---

### Post by Magnesium on 2009-11-29
> **ketilkn said:**
> My Macbook Pro is dead to me now :)

So would you want to sell it then? I've been thinking about buying a MBP. Didn't know how serious you were about that...;)

Mg

---

### Post by Enigmatic on 2009-11-29
How are you guys finding the screen? My laptop is 3.5 years old and I'd like to upgrade, but I have been spoiled by the IPS screen. I'm pretty sure no other laptop will be able to match it.

---

### Post by ketilkn on 2009-11-30
> **Magnesium said:**
> So would you want to sell it then? I've been thinking about buying a MBP. Didn't know how serious you were about that...;)

I would but it is more accurately owner by my employer. But thank you for the offer. 

As for the screen it is OK. I think it is less bright than other laptops I have owned but no big deal. Might not work as good in the sun outdoors but I rarly do that.

---

### Post by TomtheWombat on 2009-11-30
> **Enigmatic said:**
> How are you guys finding the screen? My laptop is 3.5 years old and I'd like to upgrade, but I have been spoiled by the IPS screen. I'm pretty sure no other laptop will be able to match it.

It depends on what you are doing.  At work I tend to sit my laptop to my left at an angle.  I much prefer my old IPS laptop in this condition, but I don't do this very often so I can let it go.  It is also much more difficult to show people pictures, etc.  Again, I can make due.

I really wish that Asus included an IPS.  It would have been worth the price premium, and lets face the facts.  This laptop is nowhere near a bargain in the 11-13" CULV category anyway.

---

### Post by TomtheWombat on 2009-11-30
EDIT:  I want to also mention that the touchpad issue has started to annoy me over time.  Good posture kept my wrists off the touchpad at first.

My only gripe about linux on this laptop is the power management support.  There is no possible way that you could squeeze the same life out of the battery in Linux as in Windows.

These things work:

- CPU frequency scaling.  You can clock the processor at 800mhz to save on a lot of power.
- HDD spin down.  Although it is so active that it will never actually spin down.

These things don't work:

1. Adjusting brightness of the screen.  Gnome-Power-Manger dims the LCD after a few seconds, but it returns it to the default setting afterwards instead of your previous settings.  This only works if the default settings are good for your lighting conditions.
2. Disabling wireless doesn't turn off the wireless light in the front.  I'm not 100% sure that the radio has been disabled in order to save power.
3. Freq scaling of the intel GPU.  I can't find a way to do this.  In Windows it will underclock the GPU and turn off aero to save power.
4. Hibernate is uselessly slow unless you're turning off your computer for a long amount of time, but sleep works just fine.

#1 and #4 are general problems with Linux.  #3 is also pretty general.  I'm not sure how specific to the ul30a #2 is.  My previous laptops didn't have this problem, but their hardware was dramatically different.

---

### Post by Enigmatic on 2009-12-01
I have the same issues with wireless (button doesn't turn off the light) on my Asus V6VA. 

Do you have any estimates of what battery life is like under Linux?

---

### Post by TomtheWombat on 2009-12-01
I should note that by all other indications the wireless and radio are turned off, but the light on the front remains lit.

I get similar battery performance in Windows in the 'normal' cases.  However, more power savings settings are available in Windows.  I estimate that my battery life in Linux has varied between 4.5 hours (720p movie) and 10 hours (mostly idling) thusfar.  I have not drained by battery past 40% so it is very difficult to estimate.

---

### Post by boom2k1 on 2009-12-09
It seems that the laptop brightness problem went away for me.
I read in the launchpad that somebody suggested removing the gnome-power-manager. I removed it, but it seemed that gnome-power-manager actually controls a lot of things, so I installed it back. Surprisingly, it might have solved the desktop brightness problem!
Can anyone test this out and report the finding?

Uninstall gnome-power-manager. (i know it sounds scary)

sudo apt-get remove gnome-power-manager 
in the terminal.

It will affect some other things, but it will just be temporary.
then maybe do a reboot

and then do

sudo apt-get install gnome-power-manager

to reinstall it back!

See if it works. I am now thinking maybe this procedure would over-ride the default setting.

---

### Post by boom2k1 on 2009-12-09
My second tip is related to the wifi dropping connections. I can confirm with a user posted earlier that punching this command in the terminal fixed the connection droppings.

sudo apt-get install linux-backports-modules-karmic

Try it!

---

### Post by boom2k1 on 2009-12-09
I know writing yet another post is excessive, but I also have another tip that you might consider if you want longer battery time.

Referring to [http://www.arsgeek.com/2008/01/16/cpu-scaling-ubuntu-battery-life-and-you-how-to-scale-your-cpu/](http://www.arsgeek.com/2008/01/16/cpu-scaling-ubuntu-battery-life-and-you-how-to-scale-your-cpu/)
,

it seems that the only thing that I need to do is to right click a blank area of the top panel and select Add to Panel... , and inside that window search and activate the CPU Frequency Scaling Monitor.
After that, you should see a new item on the panel listing your CPU frequency. If you left click on it, you will see several power saving options as well as explicit option to change your CPU speed between 1300MHz and 800MHz. 
 - Hopefully someone would report how long the 5600 battery can last using the power saving option! Hopefully we can get close to the approximately 9 hours we could get in Windows running the power saving mode.

One thing to note is that right now I set the overclocking to 0% in the BIOS. I haven't tested whether they still let us manipulate the CPU frequency if we overclock the processor in the BIOS.

Try it!


I am not sure if it will increase the battery much because perhaps Ubuntu has been in the On-demand mode all along.
But I still wonder why under Windows we can get more usage under the Powersaving mode.

---

### Post by svD on 2009-12-10
Thanks for your tip about the wlan drops, just installed it. some days later i'll write about the (positive) effects.

previous to my ul30a (with ubuntu 9.10) i had an sony vaio notebook and used some great working power saving options in the module laptop-mode.
" - laptop-mode enabled (package 'laptop-mode-tools'): intel-sata-powermgmt, sched-mc-power-savings and usb-autosuspend."


i haven't tweaked some power options until now, but next days i'll try to.
currently (according to my power consumption stastics) the power rate in battery mode idle is roundabout 13W, in power mode idle ~18W. maybe some other can post their power rates so we can compare and tweak :P
ps: with my sony vaio (with a very strong cpu and bright display) i got power rate down to ~8W, maybe this is possible for the asus ul30a, too.

EDIT: 15 minutes ago i started to tweak, funny :P now down to 8W... i only put on laptop-mode-tools and enabled intel-sata-powermgmt and sched-mc-power-savings (and one more that i forgot)

[IMG]http://img121.imageshack.us/img121/7884/bildschirmfotoenergiest.png[/IMG]

---

### Post by spacecaps on 2009-12-13
Hi again.

Can anyone comment on 2D video performance in karmic?  (HD)Flash or HD video?

I know the 4500MHD is supposed to suck for games but I don't care about that performance, just 2D video.  Possibly on a high resolution external monitor (via HDMI or VGA)?

I am considering the ul30a but also the ul30vt, but the graphics switching doesn't work in the vt with ubuntu.  For that matter I'm not sure I would even need a dedicated card for 2D.


It seems so strange that everything wouldn't work in this day and age...

---

### Post by svD on 2009-12-13
currently watching an flash-hd-video @ youtube and it works without lags. (flash10-x64)
i think hd videos will work too, because the intel graphic adapter got an hd decoder to do it...
according to the manual and advertisements it can scale up to full hd on an external display, but i haven't tested until now.
compiz and all the other built-in eyecandy working without any problems, i think most of the performance drops are caused by the cpu, e.g. too much open firefox-tabs to work on.

---

### Post by TomtheWombat on 2009-12-13
> **spacecaps said:**
> I am considering the ul30a but also the ul30vt, but the graphics switching doesn't work in the vt with ubuntu.  For that matter I'm not sure I would even need a dedicated card for 2D.

The recently released 64bit version of flash is functional.  If you use the 32bit flash included in Karmic, then you are going to run into trouble even on non-HD flash.

I have found 720p playback to be mixed.  If I set the CPU frequency scaling to performance, then I can play 720p content with minimal skipping.  I have only had problems with a very high quality 720p h264 during intense action scenes.

These things all work great in Windows.  The Asus has an Intel gpu that handles h264 decoding.  There are no issues with HD videos or HD flash using the 10.1beta on win7.

---

### Post by heian on 2009-12-16
Hi,

Just an question,

After reading this long thread about the Asus UL30, i got abit confused on the end.

I like this machine very much, but before buying one, i want to know which problems are still not solved at this moment.

Do i need to check something while buying? Model, type, configuration or so?
Other things that i need to know before going out to get one?

Many thanks in advance,

heian

---

### Post by avilella on 2009-12-17
Hi heian,

For what I've seen since the Asus UL30/UL80 models have been available, it's a great laptop series with very good performance for the price tag.

There are already 24 linux users (17/12/2009) with this laptop, and although there are still small glitches like the ones mentioned in the launchpad group ([http://launchpad.net/~asus-ul30](http://launchpad.net/~asus-ul30)), it's very feasible that these will be solved as they come.

We still don't know how to switch on/off the nvidia card of the UL80Vt/UL30Vt models, but we should be able to do it with proper DSDT table dumps in the future.

> **heian said:**
> Hi,

Just an question,

After reading this long thread about the Asus UL30, i got abit confused on the end.

I like this machine very much, but before buying one, i want to know which problems are still not solved at this moment.

Do i need to check something while buying? Model, type, configuration or so?
Other things that i need to know before going out to get one?

Many thanks in advance,

heian

---

### Post by viniosity on 2009-12-18
I have the UL30VT with the switchable graphics (intel and nvidia G210M).  The laptop works really well out of the box with two exceptions:

1. No idea how to disable the click on the trackpad

2. Only the intel graphics work. I've installed the included 185 driver as well as the recently released 190 and the beta 195 driver.. none of which seem to work.

Has anyone managed to get the nvidia card working on the UL30VT? If so I'd be very interested in how you managed.

---

### Post by palletguru on 2009-12-21
I have the ul30vt as well, and have been using it nonstop since the 8th of December. Karmic runs well (I had no wifi issues out of the box like others have reported). Screen brightness control and trackpad are the only downsides now. Battery life is about 4 hours (although the screen brightness is too high and I can't adjust it), which leads me to believe that discrete graphics are being used: not the onboard GMA. Running windows 7 in reduced power consumption, I DO get about 10 hours with normal use.

Relatively new to ubuntu and first posting on this forum.

---

### Post by tla123 on 2009-12-26
I'm running karmic on a UL30.

Has anyone had the problem of the consoles freezing, i.e. no keypress response, after unplugging the network cable.

It seems to be related to this thread:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=559577]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=559577")

I'm using the latest 64-bit kernel: 2.6.31-16-generic

---

### Post by avilella on 2009-12-28
One of the Linux users has found a solution to switch off the nvidia card in the UL30Vt models, which by the looks of the DSDT tables, will also work for the UL50Vt and UL80Vt models with nvidia card.

It uses the ACPI P0P1.VGA._OFF method, which is the same for all 3 models.

The code file, "asus_nvidia.c" is derived from "lenovo_acpi.c" by
Sylvain Joyeux.

Here is the original post and another one that adds hibernation support:
[http://forum.notebookreview.com/showpost.php?p=5663702&postcount=1239](http://forum.notebookreview.com/showpost.php?p=5663702&postcount=1239)
[http://forum.notebookreview.com/showpost.php?p=5664880&postcount=1244](http://forum.notebookreview.com/showpost.php?p=5664880&postcount=1244)

[http://launchpad.net/~asus-ul30](http://launchpad.net/~asus-ul30)

---

### Post by elchicosinhada on 2009-12-28
I have a UL50VT and here's my method to disconnect the touchpad.
It's ugly, but it works.
Create a script with this code:
```

#!/bin/bash                          
if [ -n "$(lsmod | grep psmouse)" ]; then
        rmmod psmouse                    
else                                     
        modprobe psmouse                 
fi      

```
And save as touchpad.

sudo mv tocuhpad /usr/bin/touchpad
sudo chmod +x /usr/bin/touchpad

This will disable or enable the touchpad module each time you run. You will need to be root to do this.
If you do not want to ask the root password, just add a 
/etc/sudoers

```
<user> ALL=(ALL) NOPASSWD:/usr/bin/touchpad

```
And then assign it to a hotkey (ctrl+F9 for example) to toggle easily and ready using command *sudo touchpad*.

Sorry by the english... google translator....

---

### Post by wentzr on 2009-12-30
I'm also having major issues with NVIDIA's G210M. have tried every driver released from NVIDIA for linux since this laptop was released and no dice. 

fastest route to a solution for everyone??? 

[B]Submit a bug report to Nvidia!!
[/B]
[B]From Nvidia's web site:
To submit Linux bug reports please email (In English only) [email]linux-bugs@nvidia.com[/email] or [email]linux-nforce-bugs@nvidia.com[/email] please attach an nvidia-bug-report.log, which is generated by running "nvidia-bug-report.sh".[/B]

---

### Post by spacecaps on 2010-01-01
Does anyone know how to increase the maximum touchpad sensitivity?  I'm actually not sure what driver 9.10 is using but I have the sensitivity maxed out and it is still too low.  However multitouch works great!

---

### Post by chicgeek on 2010-01-02
> **spacecaps said:**
> Does anyone know how to increase the maximum touchpad sensitivity?  I'm actually not sure what driver 9.10 is using but I have the sensitivity maxed out and it is still too low.  However multitouch works great!

Multitouch works great for you, even horizontal?
I installed karmic today on my UL30A-A2. Vertical scrolling multitouch worked immediately but no love with horizontal. Anyone have any fixes for this?

---

### Post by chicgeek on 2010-01-03
I have an Asus UL30A-A2 running Karmic. For owner present and future, here is what I'm experiencing:

**Dimming:**
Not really a solution, but I just turned off automatic dimming for both AC and battery power. I prefer to keep my screen at 25% and change it manually depending on what I'm doing. Guess I'm just not picky.

**Multitouch:**
I've scoured these forums and a couple of other threads on the interwebs and all I read is that "multitouch works great". My vertical scrolling works well but not horizontal. I've seen to specific mentions of this elsewhere to indicate functionality - can someone test this on their UL30/UL80? Three-finger right click works well.

**Touchpad:**
Just a note to the world that I don't mind it's sensitivity. Maybe because I don't have big man hands and have learned to change my resting posture, but to me this is not worth fixing. 
(Edit: with [some help]("http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=8431344&postcount=14"), I've re-implemented my touchpad toggle button. It's a bit cleaner than El Chico's version.)

**Webcam:**
I've read the kernel fixes posted in various places including the [Launchpad Team]("https://launchpad.net/~asus-ul30"). I think I'm going to leave this be for now. I very rarely use the webcam anyway.

**Battery Power:**
With brightness at ~25%, wifi, and basic internet use, I get 8-9 hours of battery with my A2 (8-cell) in karmic, and I haven't tweaked anything really. That's freaking sexy.

---

### Post by elchicosinhada on 2010-01-04
Works the hdmi? I read that works, but in kranrd only I see VGA... I use Debian Testing + asus_nvidia module
In windows works only with nvidia, but in Linux the nvidia graphics no works...

---

### Post by jlakser49 on 2010-01-10
hey all I am using 9.10 on my ul30a and have loved it so far. Just thought id let you all know there is one more user lurking these boards.

I had  an idea to fix the track pad. 

what if there was some sort of program that could turn of the keypad whlie typing?

prob not possible but...

see this link: [http://www.ubuntu-inside.me/2009/03/howto-disable-touchpad-while-typing.html](http://www.ubuntu-inside.me/2009/03/howto-disable-touchpad-while-typing.html)

---

### Post by elchicosinhada on 2010-01-16
Well, I configured my UL50VT in Debian with brightness and touchpad hotkey (FN + F5, FN+F6 and FN+F9).

The scripts I have obtained from [https://launchpad.net/~asus-ul30](https://launchpad.net/~asus-ul30) and I set acpi events.
I hope you find them useful.

---

### Post by avilella on 2010-01-19
Hi all,

Just want to mention that according to the numbers I am compiling, the Asus UL30/UL80 series is now the most popular Ultra-thin laptop in the Linux community. On a time-scaled basis, it has just surpassed the Acer Timeline and Sony Vaio Z-series laptops in popularity.

[http://linux-macbook-air-killers.blogspot.com/](http://linux-macbook-air-killers.blogspot.com/)

Cheers!

---

### Post by MichaelRX8 on 2010-01-31
I was thinking of getting the Asus UL50VT-RBBBK05 this friday from Best Buy,witch I believe has about the same hardware. I really don't want to get it if the iNvidia gpu will not work though. Any news on this?

     Thanks.

---

### Post by avilella on 2010-02-01
Hi,

In terms of switching on/off, there has been a successful report that it works by doing this:

For Ubuntu Karmic, download and install this package:

[http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb](http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb)

Then once installed, run the following command on a terminal:

    sudo modprobe nvidia_g210m_acpi

More details here:
[http://linux-macbook-air-killers.blogspot.com/2010/01/asus-ul20-asus-ul30-ul30vt-ul50-ul80.html](http://linux-macbook-air-killers.blogspot.com/2010/01/asus-ul20-asus-ul30-ul30vt-ul50-ul80.html)

and here:
[https://lists.launchpad.net/asus-ul30/msg00054.html](https://lists.launchpad.net/asus-ul30/msg00054.html)

In terms of nvidia binary drivers, I would say that if they don't work *now* they will work soon. The nouveau driver will give you basic 2D acceleration, and some 3D support.

Cheers

> **MichaelRX8 said:**
> I was thinking of getting the Asus UL50VT-RBBBK05 this friday from Best Buy,witch I believe has about the same hardware. I really don't want to get it if the iNvidia gpu will not work though. Any news on this?

     Thanks.

---

### Post by MichaelRX8 on 2010-02-01
avilella; Thanks for the response. So nvidia isn't working yet. Does Ubuntu access the integrated intel out of the box? I guess I'm asking if 3d acceleration will work. Are the   
the nvidia drivers just not working or are the duel graffics cards just confusing things.
 I really want to get this laptop (I really like the form factor), but I'm also considering the Sony CW series. I've got to make up my mind by Friday, so any input you guys can give would be very helpful.

  Thanks.

---

### Post by avilella on 2010-02-02
The nouveau drivers will give *some* support for sure, but they are not up to the closed-source binary nvidia drivers yet. The closed-source drivers will surely provide support at some point in the future, but it's difficult to say when, since it's up to the nvidia linux drivers team to decide. Ubuntu provides good intel support even if you don't switch off the nvidia card. Switching off the nvidia card helps in giving an extra 40% battery life.

> **MichaelRX8 said:**
> avilella; Thanks for the response. So nvidia isn't working yet. Does Ubuntu access the integrated intel out of the box? I guess I'm asking if 3d acceleration will work. Are the   
the nvidia drivers just not working or are the duel graffics cards just confusing things.
 I really want to get this laptop (I really like the form factor), but I'm also considering the Sony CW series. I've got to make up my mind by Friday, so any input you guys can give would be very helpful.

  Thanks.

---

### Post by avilella on 2010-02-03
I've just noticed that Fedora is incorporating nouveau patches faster than Ubuntu. Ubuntu Lucid alpha 3 is something like 3 weeks delayed with respect to Fedora, so if people want to try the latest downloadable Fedora, we will have an idea of nouveau's support in asus UL*0Vt laptops.

I apologize for posting this in an Ubuntu-specific forum. This email will apply to Ubuntu in 3 weeks time.

---

### Post by Maggma on 2010-02-04
I picked up a UL30A last month and recently installed Karmic on it. I haven't tested everything out yet (no idea what the battery life is like) but the only thing that's really bugging me is Power Management doesn't seem to work. I want to stop it from turning off the display when inactive on AC Power, but it's not working. I only read through the last few pages for this thread, but does anyone know a work around for this?

Thanks.

---

### Post by iloutzu on 2010-02-05
> **Maggma said:**
> I picked up a UL30A last month and recently installed Karmic on it. I haven't tested everything out yet (no idea what the battery life is like) but the only thing that's really bugging me is Power Management doesn't seem to work. I want to stop it from turning off the display when inactive on AC Power, but it's not working. I only read through the last few pages for this thread, but does anyone know a work around for this?

Thanks.

I thought I had the same problem, but then I noticed it was actually the screensaver (set on Blank Screen by default), and disabled it. Did you try that?

---

### Post by elchicosinhada on 2010-02-11
> **elchicosinhada said:**
> Works the hdmi? I read that works, but in kranrd only I see VGA... I use Debian Testing + asus_nvidia module
In windows works only with nvidia, but in Linux the nvidia graphics no works...

Works the hdmi yet?

---

### Post by chicgeek on 2010-02-13
Question:

I have both Karmic and Win 7 installed, though both my fastboot and recovery partitions are intact. I want to recover my computer back to factory settings (for whatever reason) and have used F9 while booting for this previously.

Ubuntu seems to have changed the boot so that using F9 to access the recovery partition no longer works. How do I access (or rather... use) this recovery process with this altered grub menu?

Any and all help is greatly appreciated!

---

### Post by Kegetys on 2010-02-16
Has anyone with the UL30VT tried the newest BIOS from asus site (208)? I seem to have a problem with waking up from suspend with this BIOS in Ubuntu 9.10, the whole system freezes on wakeup. Sometimes I get to the desktop but nothing works anymore as if the root drive is not accessible, sometimes I just get a black screen with the mouse cursor visible. If I flash back to bios 204 it works fine again... I'd like to use the newest BIOS since it fixes an annoying fan control issue in Windows side for me.

---

### Post by ubuntoide on 2010-02-25
I am using 208 bios and i don't have any problem with suspend except for the fact that the nvidia card is not turned off when waking up. I use the driver provided in[this thread]("http://ubuntuforums.org/showthread.php?p=8573101")
Anyway I have issues with backlight, hope new kernel will fix that, it's quite annoying..

---

### Post by cucisan on 2010-03-16
hey there,

planning to get one of those myself..

i read that those ul30A's (the ones with intel only) get up to 7-9hrs of battery life.. i wonder if someone with a ul30VT (intel+nvidia) gets the same battery life when using the acpi hack to turn off the nvidia card..

anyone with a VT can answer this for me?


to all: how is the intel gfx performance on this thing? with either 9.10 or 10.04 alpha - is it enough for a 720p movie and for smooth flash movies (SD and HD) ? do simple 3d games work like neverball or quakelive ...

thanks for answers in advance!

---

### Post by TomtheWombat on 2010-03-16
> **cucisan said:**
> to all: how is the intel gfx performance on this thing? with either 9.10 or 10.04 alpha - is it enough for a 720p movie and for smooth flash movies (SD and HD) ? do simple 3d games work like neverball or quakelive ...

First, I don't use this computer as my main computer.  I only have a few experience with the things that you mentioned, but here is my opinion:

1) 720p movie:
A lot of the 720p h264 podcasts that I download have worked without any problems.  I don't think that I have tried to watch any Apple trailers.  I d/l Star Trek mkv 720p to test, and it was choppy in some spots (I assume this is due to the much higher quality and higher bitrate.  I definitely would have missed a couple small parts of the movie if I hadn't already seen it.)

720p plays great in Windows because of the GPU decoding.

2) Flash is alright on YouTube high quality.  I haven't tried 720p quality.

Flash runs great on Windows due to GPU decoding.

3) I have played quakelive.  I don't think that it was running on low quality, but it definitely wasn't running on high!  I think that I had it running at the native LCD resolution, but don't quote me on that!  Gameplay was smooth and I could be competitive.  I'm not sure how hard I pushed it.

FYI: I would still be happy if none of this worked, so I may not be the best source.

---

### Post by joenix on 2010-03-17
I have a question concerning the fan operation under Ubuntu.

In most of the reviews I have read, it is stated that the fan of the UL30a is off most of the time and that when it is on, it is very quiet.

Now, my experience with notebooks says that the situation under Ubuntu in this respect is in general worse than under Windows.

Is this the case with this model? Does the fan turn on at all under light use? At what level? Can you hear the fan in a room with no background noise during e.g. surfing or word processing?

---

### Post by TomtheWombat on 2010-03-17
> **cucisan said:**
> planning to get one of those myself..

I want to mention that I would have gotten the VT, but it wasn't yet available and GPU switching wasn't working as well when I purchased.

> **joenix said:**
> Does the fan turn on at all under light use? At what level? Can you hear the fan in a room with no background noise during e.g. surfing or word processing?

I haven't never noticed the fan, but I'm not very sensitive to it.  My last laptop was a tx2000z where the BIOS was updated to run the fan all of the time!  I was almost happy when that $1,000 kicked 12 months and 5 days after I bought it.

Will this laptop burn up just like the rest of them?  I don't know.  I can say that I have not experienced any `symptoms' of damage.  My tx2000z started showing signs of issues in July '08.  (I purchased in April '08, and it didn't break until May '08.)  My ul30a is still running fine.  However, the tx2000 got more use than my ul30a, and my ul30a hasn't seen ambient temperatures over 65 degrees, yet...

---

### Post by ubuntoide on 2010-03-19
> **cucisan said:**
> 
i read that those ul30A's (the ones with intel only) get up to 7-9hrs of battery life.. i wonder if someone with a ul30VT (intel+nvidia) gets the same battery life when using the acpi hack to turn off the nvidia card..


Hi, I got a VT and with the acpi hack you can get exactly the same battery life as the standard version, the discrete GPU is completely shut off.

About flash performance, it can handle youtube @720p without any issue (using x64 flavor).
If you like gaming, I can run Mass Effect 2 @ native resolution on windows 7 (using G210 card), if you want an all-round light notebook, that's your choice

PS the fan is almost silent, and the chassis cool, except for the area around the exhaust fan, which is less than warm..

---

### Post by cucisan on 2010-03-19
ok thx you 2 for the answers... nice

the VT model is just 25bucks more than the A version, thats why i asked :)

---

### Post by orionid on 2010-04-02
> **avilella said:**
> Hi,

Has anyone installed Linux on an Asus UL30?




 Installing Ubuntu 9.10 karmic, 64 bits, kernel 2.6.31-20-generic, on an ASUS UL30A (Intel Core2 Duo ULV U7300 1.30 GHz 3Mb L2 cache,  4 Gb RAM, 500 Gb HDD, webcam)
 --------------------------------------------------------------------------

 Installation went flawlessly. The ASUS comes with 3 partitions:

- 1st (FAT32) of about 15 Gb containing the Express Gate system (which is a fast booting -7 secs- partition in which you can browse the Internet, use Skype, listen to audio and watch videos.

- 2nd (NTFS) of 120 Gb containing Windows 7 64 bits Home Premium

- 3rd (NTFS) of 335 Gb: empty

  I installed Ubuntu on the third partition, so I did not have to touch any of the windows that come pre-installed.  Used ext4 filesystem on all linux partitions: /boot (250 Mb), /(15Gb), swap (4Gb),
  /home (130Gb), /data (~185).


Installation (from an external USB Asus DVD drive) went flawlessly:

 Things that worked out of the box:
   - Touchpad    (good response, two-finger vertical scrolling and three-finger right menu)

   - Wireless    But had to install linux-backport-modules to fix weak wifi signal and frequent drops of the connection. First go to Administration > Software Sources > Updates and enable "Unsupported Updates (karmic-backports) 
Then: sudo apt-get install linux-backports-modules-karmic 

   - Microphone  Just need to go to Sound Preferences (right click under volume control in panel), select Input tab, and in Connector button select Microphone 2. Adjust volume to your liking.

   - SD Card reader 

   - Suspend  (suspend Fn - Zz button and closing lid when on battery)

   - Volume and screen brightness buttons

   - Wifi On/Off button

  SOFTWARE:
  *********
  Being a professional astronomer, I installed other software in addition to the stanrdard things (web browsing, e-mail, video/music, etc).

   - Firefox 3.5.3 comes preinstalled and works great. I installed XMarks...works fine.

   - I installed Java using Ubuntu Software Center, and then installed Topcat, which is an application for dealing with tabular data, and the Aladin Sky Atlas. Everything worked without a hitch.

   - Installed Thunderbird + Lightning (Calendar Add-On). Worked fine.

   - Skype worked out of the box, except for video. I downloaded the Ubuntu 8.04+ 64 bit version. Though video was ok from the beginning, I was upside down!  It took me a while to fix this, since  several recommended solutions I tried did not work. Finally, what seemed to do the trick was to follow Hans de Goede´s instructions ([http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)), and restart.
(just in case, go to the Synaptic Package Manager in System -> Administration, open it, search for libv4l, and reinstall the libv4l- libraries: libv4l-0, libv4l-dev, lib32v4l-0, lib32v4l-dev)
     I run skype with a script that contains the following lines:
     #!/bin/bash
     #LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
     export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

   - I installed SuperMongo (compiled for 64 bits):
     SuperMongo ([http://www.astro.princeton.edu/~rhl/sm/sm.html](http://www.astro.princeton.edu/~rhl/sm/sm.html)) is an interactive plotting programme with a flexible command language.
     As a professional astronomer I use it for my everyday work...though more people are migrating toward other software like gnuplot, pgplot, or IDL. I followed these instructions:

     by superluminique - 01/28/2009 - 11:46
    
    This problem is not unique to Fedora and it did happen to me on Ubuntu 8.04 as well. Here's how I solved it:
    
    1. Using your package manager (apt, dpkg, synaptic, etc.) make sure that you install the "bison" package.
    
    2. Run ./set_opts as usual.
    
    3. Go to the sm2_4_XX/src directory and edit Makefile.
    Make sure that:
    YACC = /usr/bin/bison -y
    
    Change:
    all_src : Bison, sm
    for:
    all_src : sm
    (i.e. remove Bison) This will prevent the make script to try to compile Bison from the source code included with SM, which, for some reason, crashed at compilation.
    
    
    3. Run ./set_opts and at the question:
    """
    You are on linux using the
    cc -Wall -Dlinux -DNEED_SWAP
    compiler; is this OK? [y|n]
    """
    
    Answer no (i.e. type "n")
    Then set_opts will prompt you with:
    
    """
    type compiler command or q to exit
    """
    
    You should type "cc -Wall -Dlinux -DNEED_SWAP -fPIC -L/usr/lib64 -lX11¨
    
    
    4. Run "make" as usual.
    
       Came out with errors, but I still went ahead and installed successfully:
       ...
       x11.c: In function ‘x_clear_pixmap’:
       x11.c:1376: error: expected declaration specifiers before ‘Display’
       x11.c:1377: error: expected declaration specifiers before ‘Pixmap’
       x11.c:1379: warning: implicit declaration of function ‘XFillRectangle’
       x11.c:1379: error: ‘SMX11’ has no member named ‘erase_gc’
       x11.c:1380: error: ‘SMX11’ has no member named ‘width’
       x11.c:1380: error: ‘SMX11’ has no member named ‘height’
       make[2]: *** [x11.o] Error 1
       make[2]: Leaving directory `/home/briceno/linux/graphics/sm2_4_1/src/devices'
       make[1]: *** [Devices] Error 2
       make[1]: Leaving directory `/home/briceno/linux/graphics/sm2_4_1/src'
       make: *** [sm] Error 2
    
    
    5. Run "make install" as usual.
    
    
    6. Edit .sm file to define appropriate locations of libraries: e.g. /usr/local/lib/sm
       in case you installed in /usr/local
    
    7. I have tested it with various of my existing SuperMongo scripts and found no problems yet.
    
    --------------------------------------------------------------------------
    Note that "make install" might fail to copy the python module
    """cp: cannot stat `swigInterfaces/{_smLib*,*.py}': No such file or directory
    make: *** [install] Error 1
    """
    In this case, simply copy the files manually:
    cp sm2_4_30/swigInterfaces/_smLib* /usr/local/lib/
    cp sm2_4_30/swigInterfaces/*.py /usr/local/lib/
    --------------------------------------------------------------------------

   - Installed f77 compiler: sudo apt-get install fort77

   - Installed PGPLOT (requires f77 compiler)
     The PGPLOT Graphics Subroutine Library ([http://www.astro.caltech.edu/~tjp/pgplot/](http://www.astro.caltech.edu/~tjp/pgplot/)) is a 
     Fortran- or C-callable, device-independent graphics package for making simple scientific graphs. 
     It is intended for making graphical images of publication quality with minimum effort on the part  of the user. As an astronomer I use it often, specially with the WIP graphical application.

     1 Create target directory: sudo mkdir /usr/local/pgplot

     2 cd /home/briceno/linux/astronomy/pgplot/

     3 sudo vi drivers.list  and uncomment postscript, null and XWINDOW drivers

     4 From target directoru run:
     sudo /home/briceno/linux/astronomy/pgplot/makemake /home/briceno/linux/astronomy/pgplot linux fort77_gcc

     5 sudo vi makefile and fix typo: instead of FCOMPL=for77 should be  FCOMPL=fort77

     6 sudo make  (some errors came out, but still intallation seems to work just fine)

     7 sudo make cpg
         This creates three files:

          cpgplot.h       (ANSI C header file)
          libcpgplot.a    (library containing the C binding)
          cpgdemo         (demonstration program)

        which are needed in order to compile WIP (later)
     Test PGPLOT by running one of its demos, e.g.: pgdemo1

   - Installed WIP ([http://bima.astro.umd.edu/wip/](http://bima.astro.umd.edu/wip/))
     WIP is a graphics software package intended to be used to generate high quality graphics 
     (using the PGPLOT graphics library) with a minimum of effort. 

     1. Dowload WIP from [ftp://ftp.astro.umd.edu/progs/morgan/](ftp://ftp.astro.umd.edu/progs/morgan/)  

     2. Uncompress and untar 
 
     3. In the directory where you untared wip, run:  
        makewip -wip source_directory -pgplot directory_where_pgplot_is_installed -xlib /usr/lib

        in my case: makewip -wip /home/briceno/linux/astronomy/wip -pgplot /usr/local/pgplot -xlib /usr/lib

     WIP worked ok.

   - Installed Kile using the Ubuntu Software Center. I use Kile for editing and working with LaTeX. Works great.

   - Installed Acrobat Reader (see [http://plagatux.es/2009/01/adobe-acrobat-reader-en-ubuntu-64-bits/):](http://plagatux.es/2009/01/adobe-acrobat-reader-en-ubuntu-64-bits/):)
     sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) –output-document=/etc/apt/sources.list.d/medibuntu.list
     Add CPG key: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

     Install using ¨sudo apt-get install acroread¨

   - Adobe flashplayer: installed the 64 bits alpha version from
     [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
     follow installation instructions there

   - Movies work in all formats I´ve tested: avi, wmv, mpg, mpeg4, rmvb, using Totem, which will download and install the required decoders as needed.

   - YouTube works great....no video problems, great sound.

   - Music sounds great in Rhythmbox

   - Installed Screenlets (desktop eye candy) from Ubuntu Software Center. Works great.

   - Installed IRAF (Image Reduction and Analysis Facility). 
     IRAF is a free software widely used by professional astronomers worldwide to process and analyze astronomical data (images, spectra, data cubes).   I used a simple installation file created by favilac in [http://ubuntuforums.org/archive/index.php/t-912583.html](http://ubuntuforums.org/archive/index.php/t-912583.html).
     Its a 232 Mb file that contains IRAF 2.14, ds9, etc.  Download it, open it with Ark or other archiver tool. Extract the deb folder, the IRAF source file iraf.tar.gz and the appropriate installer script. In my case
     I used install-ubuntu64.sh.  Then just run it as root: sudo sh install-ubuntu64.sh
     It will download all the files it needs, create the iraf user and home directory, install IRAF, the FITS image visualizer ds9, xgterm for command line control, etc.
     When finished, just do an mkiraf in your iraf directory (or create a /home/xxxx/iraf directory) and select xgterm as your preferred command line shell. Then launch iraf normally.  Depending on your Internet connection, the whole process should only take from a few to maybe 20 min.
     (I do it with the following alias:
      xiraf ´ds9 | cd /home/briceno/iraf ; xgterm -fg black -bg grey -fn 8x13bold -sb -cr red -title IRAF -e ecl &´
      which I defined in my .cshrc file)
      Iraf installed this way runs without any problems I have been able to detect so far.

  - Installed WCSTools 3.8.1. 
    WCSTools is a package of programs and a library of utility subroutines for setting and 
    using the world coordinate systems (WCS) in the headers of the most common astronomical image formats

    1. Download the latest version from: [http://tdc-www.harvard.edu/wcstools/](http://tdc-www.harvard.edu/wcstools/)

    2. Ucompress and untar it. cd to wcstools-3.8.1

    3. make  (some warnings but programs seem to run ok)

    4. Make sure the path to the wcstool-3.8.1/bin directory is in your path
 

   - I also installed XPDF and Okular, and Qalculate (an advanced calculator) from the Ubuntu Software Center. 
     They all run fine.

   ******* After the install, and after updating packages, my system boots into linux in roughly 32 sec.
   (thats from hitting the power button till I get a fully loaded desktop, including wireless connection,
   and screenlets) NOT BAD!!! *******

---

### Post by The Flying Penguin on 2010-04-10
Very informative thread.

I think I can live with not being able to use the G210M in Ubuntu. As long as the onboard graphics can handle most of my movies/tv and youtube videos I'll be happy. I do all my gaming in Windows anyway and I can always jump to Windows if I want to watch the occasional 1080p movie. IMO it is just a matter of time before Nvidia releases a Linux driver with G210M support anyway.

My main concern at this point is the brightness control. When you guys/gals say you can't adjust the brightness do you mean via the keyboard shortcuts or not at all? You can manually adjust it via Ubuntu correct?

---

### Post by Hobbes on 2010-04-11
I've gotten brightness controls to work both from my keyboard and from manually inputting brightness levels through the terminal.  I did it with the acpi events (also turning touchpad off is a must because it really is sensitve/annoying while typing) posted above (i think, it was a few days ago). Anyway basically everything works here except that I get some weird graphics corruption occasionally on the bottom half of my screen.  I'm using lucid and updating a bunch of stuff now, we'll see if it helps.

---

### Post by Cierreics on 2010-04-13
Hi all!!

I didn't like the default touchpad feeling, too slow at short movements, then accelerating too fast, so I've readed this wiki: [http://www.x.org/wiki/Development/Documentation/PointerAcceleration#head-863ae9c52fe3658e800daa0e93d3e434190b732d]("http://www.x.org/wiki/Development/Documentation/PointerAcceleration#head-863ae9c52fe3658e800daa0e93d3e434190b732d")

After a bunch of tests, I've wrote an hal setting file that, imho, gives much better feeling, almost perfect to me.

Try it! ;)

sudo gedit /etc/hal/fdi/policy/asus-X11-touchpad.fdi

Paste this:

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
  <match key="info.product" string="ImPS/2 Logitech Wheel Mouse">
    <merge key="input.x11_options.AccelerationProfile" type="string">7</merge>
    <merge key="input.x11_options.VelocityScale" type="string">1000</merge> 
  </match>
</device>
</deviceinfo>

```

save, then reboot....

Now go to gnome mouse preferences and set the touchpad as you like! 
I'm feeling good with acceleration at 65-70% and full sensibility, if it's too fast for you, reduce acceleration.

Touchpad is much faster, with linear and limited acceleration, I can move the pointer side by side with a single movement, as I like it. 

That gnome setting is also good for an external mouse, I'm feeling good with mine, try to reach a good balance with acceleration...

If you don't like my touchpad setting, remove .fdi file:

sudo rm /etc/hal/fdi/policy/asus-X11-touchpad.fdi

then reboot.

Bye! ):P

---

### Post by crash20 on 2010-04-15
I've had Ubuntu on my UL30 for about a week now, and I really enjoy most of it so far. But I'm running into some issues that maybe one of you guys know how to help me with. 

One of the problem's I've had is with brightness. Once I've set the brightness to a certain level, the screen would randomly jump back to the previous level minutes later. I thought it had something to do with the power management options, but it doesn't even show a bar to set when on battery power, and I've already unchecked the "Dim display when idle" option. So I really don't know what's the problem now. 

Another issue is the Wifi. It says I would be connected to a wireless network, but when I try browsing the internet on Firefox, the pages would load terribly slowly, or sometimes not at all. This is especially troublesome when I want to access my gmail. I don't think it's the fault of my wifi card, because I've had good connection when using Windows 7. 

Finally, does anyone know how to use Amarok? I downloaded, but I cant seem to play any music files with it. I keep clicking on the file, and trying to import the music from other folders, but nothing works. 

Hope someone can help me out here,
Thanks.

---

### Post by AXBX7C on 2010-04-15
I just bought the Asus UL30 after 4.5 years of using a bulky HP Pavilion laptop... So far I'm really impressed with it.

Also, I'm really new to Ubuntu. I've been a Windows user since 3.0 times... But with my new laptop in my hands I thought I give it a shot and surprise surprise I actually like it. It's fast...Very fast...I don't like to wait for programs to start up but I think I'm a bit peculiar when it comes to that. 

Everything seems to work fine apart from that brightness issue most people have. Switching off the &quot;dim display brightness&quot; option should do it, though. 

@crash20: I had the same problem with Amarok. I finally got it to play audio files (there's a bunch of additional codecs you need to download. Sorry I forgot...) But a quick Google search should help... I finally gave up on it though since I couldn't get my music (which is on a separate partition) to import into my collection. Anyway, I'm using Rythmbox and OSD-Lyrics now which is fine for me...  
 
 Edit:  Check out [https://wiki.ubuntu.com/LaptopTestingTeam/Old/AsusUL30A](https://wiki.ubuntu.com/LaptopTestingTeam/Old/AsusUL30A)

---

### Post by Cierreics on 2010-04-20
The Ubuntu wiki workaround for brightness issue, using xbacklight, works very well!! :guitar:


Some tips for increasing battery life:

sudo gedit /usr/lib/pm-utils/power.d/usb-autosuspend

paste this:

```
#!/bin/bash
if [ "$1" = "true" ]; then

  for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
  done

  for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "2" > $i
  done

fi
```

save and close, then:

sudo sudo chmod +x /usr/lib/pm-utils/power.d/usb-autosuspend

This script forces the usb autosuspend for all devices, in our case we have to do this for webcam, it saves at least 0.5 watt.

Another setting:

sudo gedit /etc/rc.local

BEFORE "exit 0", paste:

```
rfkill block bluetooth
echo 0 > /proc/sys/vm/swappiness
echo 60000 > /proc/sys/vm/dirty_expire_centisecs
echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
echo 60 > /proc/sys/vm/dirty_background_ratio
echo 95 > /proc/sys/vm/dirty_ratio
```

save and close. I say it again, the file HAVE TO end with "exit 0", paste before it!!

This setting will:
1. turn off the bluetooth at startup, but when you need it you can turn it on again any time with the gnome-panel applet in notification area; 
2. disable swappiness, our notebook has 4GB of ram, swap is really unnecessary, we need a swap partition only for hybernation;
3. set virtual memory usage to save power.

Reboot and watch the difference, with these settings, with no wifi and backlight at minimun, compiz enabled and docky, my power drain at idle is only 7,6 watt!! :guitar::guitar:

But I've replaced the stock hard disk with a 32GB Patriot Warp SSD, much faster and probably better in power consumption...

---

### Post by AXBX7C on 2010-04-21
I just noticed that my battery capacity is at 98 percent. I'm wondering if this is normal because I bought my laptop only 2 weeks ago...

Also, using the function key to switch off wireless works but the wireless led is still on. The question is, does the function key really disable the adapter?

---

### Post by Cierreics on 2010-04-22
> **AXBX7C said:**
> I just noticed that my battery capacity is at 98 percent. I'm wondering if this is normal because I bought my laptop only 2 weeks ago...

My battery capacity is 100%, maybe your battery is defective...if the capacity drop is too fast, you could try to contact Asus for a warranty replace.

Make a complete discharge to reset the fuel gauge: use the system until auto-hybernation, then reboot, press F2 to enter the bios, stay in the bios until notebook goes off. Then plug to AC power, reboot and look if full capacity is restored...

Useful tips to increase battery life:

1. recharge the battery when it reachs about 7%: using battery al low % stress it and increase capacity drop during time;

2. once a month, make a complete discharge to reset battery fuel gauge;

3. when you work on AC power, remove the battery when it's full charged to avoid overheating: modern notebooks should avoid battery overheating, but removing it's always a good choice to reduce heat and increase battery life. If you are scared of power blackouts, don't remove the battery but unplug the power adapter when battery is full charged;

4. if you plan to not use the battery for a long period of time, the best way to store it is to charge the battery at about 40%, put it in a plastic vacuum bag and store it in your fridge!! :cool:


> **AXBX7C said:**
> Also, using the function key to switch off wireless works but the wireless led is still on. The question is, does the function key really disable the adapter?

I don't know if it's really disabled, but power consupmtion decreases a lot, so it works!! :guitar:

---

### Post by AXBX7C on 2010-04-22
wow thx for all your tips! I'll try that battery capacity check...

I think the main reason to switch to Linux is a very supportive community. Just great how everyone helps each other. I never had this impression with the 'Windows community'...Awesome!

Regarding the WiFi adapter. I checked the energy consumption both with the adapter on and off and you're right, consumption is much lower when wifi is switched off! That tells me that the adpater is also disabled...

---

### Post by Hobbes on 2010-04-23
Thanks for the script/tips on power saving, I will give it a go.  How are you measuring your power consumption btw?

---

### Post by Cierreics on 2010-04-23
> **Hobbes said:**
> Thanks for the script/tips on power saving, I will give it a go.  How are you measuring your power consumption btw?

sudo apt-get install powertop

then

sudo powertop

On battery power, you'll see real-time power consumption. 
Powertop also gives some tips, but don't follow them, some are deprecated....if you use my settings, the only tip you'll see is the min_power sata setting, and maybe the usb_autosuspend setting.
Don't follow them, usb is already autosuspending and the min_power sata setting brokes suspend to ram on Karmic...maybe it will be fixed in Lucid, but I found out that this setting don't reduce consumption at all, so it's pretty useless...

---

### Post by Benoe on 2010-04-23
Hi!

Do you think ASUS' Turbo33 feature will be available to ubuntu as well?

I think that feature only increases FSB. Is it possible under linux/ubuntu?

---

### Post by Benoe on 2010-04-23
Guys, with UL*0Vt!

I have read, that there is a way to enable the nVidia card during boot:

"go into your bios and set the hard disk to compatible mode.
boot into snow leopard, it will automagically uses the nvidia gpu."

It is from a hackintosh forum, but the situation might be the same with ubuntu.

---

### Post by AXBX7C on 2010-04-27
I'm wondering if there is any benefit from switching to a 64 Bit Linux version? Right now I'm using 9.10 (32 Bit) but I'm considering to switch with the new release... Even though, I'm not sure whether 1 GB more usable Ram would make any difference.

Anyone here who has a 64 Bit version installed on their Asus UL30a?

Thx for your thoughts!

---

### Post by Cierreics on 2010-04-27
> **AXBX7C said:**
> I'm wondering if there is any benefit from switching to a 64 Bit Linux version? Right now I'm using 9.10 (32 Bit) but I'm considering to switch with the new release... Even though, I'm not sure whether 1 GB more usable Ram would make any difference.
Anyone here who has a 64 Bit version installed on their Asus UL30a?


Yes, I use a 64bit Karmic! 

It works very well, the only thing I suggest is to install the alpha 64bit Flash player plugin: the 32bit version has too much crashes.
The alpha 64bit version works well, never crashes, but has problems in some fullscreen videos: on some platforms, like YouTube, when you use video controls on fullscreen mode, video becomes choppy and the system hangs fore some seconds, but on other platforms, like Megavideo, video controls work well even on fullscreen...

The 1 GB of ram you can get with a 64bit OS would not make much difference, unless you make heavy image or video editing, or 3d animations, but I don't think you're crazy enough to do that stuff on a 13.3" display...:biggrin:

Another way to fill 4GB of ram is to virtualize a Windows 7 machine giving it 3GB of ram...:rolleyes:

---

### Post by AXBX7C on 2010-04-30
Hello!

I just upgraded to 10.04 but now my function keys are not working properly. I can't adjust my screen brightness. Also some function keys seem to activate two functions at the same time... Anyone else who's had the same problem?

Edit: I posted my issue to the general forum...

---

### Post by IdealVithVodka on 2010-05-03
Hi,

Yeah, I got the same problem with 10.04 on my UL30A... The keys don't work - but the wireless works without a problem :P I switched back to 9.10... I will wait till they sort out all of those issues... 

BTW: someone told me that every release of ubuntu is made from scratch... Is the true ?? If so then the guys spend lots of time on resolving the same problems all the time... Or I'm wrong ?

the best way to check if they have done any progress with the keys would be to download the image in about 1 month and check if anything changed in the live session :)

---

### Post by AXBX7C on 2010-05-03
@IdealVithVodka:

There's a solution to the function key issue. See:

[http://ubuntuforums.org/showthread.php?t=1466758](http://ubuntuforums.org/showthread.php?t=1466758)

Someone said it didn't work for him but it did for me. So give it a try... On the other hand, if you have gone back to 9.10 you won't need it anyway....

Some also suggested that updating to a newer kernel would help: 

Quote:
"After upgrading to some more recent kernel (.33, .34rc6 atm) all the
issues with non-working brightness controls / Fn keys were gone as well.
You can get recent kernel from the Mainline ppa:
 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") 

 
As a sidenote, i think my battery lasts way longer with .34 - powertop
shows power draw below 6W sometimes. I never had such figures with
9.10 / kernel .31."[FONT=Verdana]
Unquote

I haven't tried that though...
[/FONT]

---

### Post by foobarth on 2010-05-05
Hey,

> **AXBX7C said:**
> 
Quote:
"After upgrading to some more recent kernel (.33, .34rc6 atm) all the
issues with non-working brightness controls / Fn keys were gone as well.
You can get recent kernel from the Mainline ppa:
 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") 


I was the one suggesting this kernel upgrade via the UL30 Mailinglist. Although it does solve the issues with brightness and screen flicker, i find the above posted solution much cleaner. So i reverted to Lucid stock kernel and your suggested fix. It works fine and now i even got a nice bar popup while changing brightness.

Cheers,
Ralf.

---

### Post by The Flying Penguin on 2010-05-08
Hey guys. I thought I would give a little bit of an update about how things have been going for me using Ubuntu on my ul30vt. This may be a bit long but I thought my experience may be useful for people trying to get Ubuntu running smoothly on the vt series.

I bought this laptop about a week or so before Lucid came out so I was running Karmic. I didn't do a whole lot of tweaking under Karmic because I knew I would be wiping it off as soon as Lucid came out. I did do the touch pad and nvidia shut down hacks and those worked very well under Karmic. Also, when using Karmic, I found the wireless to be somewhat unstable. I probably had half the signal strength as I did under Win7. The solution was to download "linux-backports-modules-karmic" from the repositories. Using Lucid, my wifi seems to work perfect right out of the box. I had no need to download the backport modules.

Onto my experience running Lucid:

First off, let me just say how fast the install was. I did the whole install in less than 25 minutes, probably close to 20. I didn't time Win7 but something tells me it wasn't near as fast. I dual boot with Lucid/Win7 btw. I may have to consider doing a tripple boot with Lucid/Win7/XP since Win7 doesn't seem to like playing older games via lan with my friends who still use XP. But thats another topic.

Graphics:
From all my reading I have determined that you cannot use the nvidia card under Linux at the moment. That's ok because there is a way to disable it and use the onboard Intel graphics so you can at least save some battery life. The Intel graphics under Ubuntu seem to work fine for the most part. I haven't tried any Hulu out but I was able to play 720p youtube with no issues and other 720p movies streaming over wifi from my server. I haven't had a chance to test out 1080p playback except under Win7 using the nvidia card which was FLAWLESS. Btw, I'm using the 64 bit version of flash in Ubuntu.

The one issue I have had is that every now and then the screen will flicker a little and when I drag a window with compiz on there is some tearing on the title bar. That is no biggie though. It's nothing I can't live with.

To disable the nvidia graphics card (thanks to avilella in post #66 on page 7 for the info on this fix):

Download (I know it says its for Karmic but it worked for me under Lucid)
[http://launchpadlibrarian.net/384580...karmic_all.deb](http://launchpadlibrarian.net/384580...karmic_all.deb)

After installing, run the following in the terminal:
sudo modprobe nvidia_g210m_acpi

One caveat though is that once you suspend or hibernate, the card comes back on and this command will not work. You will have to restart the system to be able to use it again. Someone provided updated code with hibernation support but you will have to compile it. Here is the link [http://forum.notebookreview.com/5664880-post1244.html](http://forum.notebookreview.com/5664880-post1244.html)

Brightness:
No, the brightness control does not work out of the box. Neither the hotkeys or the software controls worked for me. I tried a few different solutions but none really worked. What worked for me was using the scrip provided by elchicoshinhada in post #63 on page 7 of this thread. My hotekeys now work yay! Sometimes you have to press them in 1 second intervals or the brightness bounces around and sometimes they work perfect but who cares? They work! It actually seems to work better after installing that package for turning off the nvidia card.

Touchpad:
My last two ultraportables/netbooks, Dell X300 and MSI Wind U230 had great touchpads. This touchpad, not so much. The multitouch is really nice but it seems slow and unresponsive no matter what OS I use. That was until Cierreics: in post #85 on page 7 provided a nice little hal file that makes it much more usable. Still not the best trackpad but that is more a design/hardware issue then it is a software issue now.

In terminal type:
sudo gedit /etc/hal/fdi/policy/asus-X11-touchpad.fdi

Then paste:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
  <match key="info.product" string="ImPS/2 Logitech Wheel Mouse">
    <merge key="input.x11_options.AccelerationProfile" type="string">7</merge>
    <merge key="input.x11_options.VelocityScale" type="string">1000</merge> 
  </match>
</device>
</deviceinfo>

```Save and reboot.

Now adjust your touchpad settings and enjoy!

Also, be sure to check out Cierreics other post, #88, for some addtional power saving tips!

Misc:
Most everything other then what I have posted about seems to work out of the box, at least what I have tested. I have not tested hdmi yet but a couple of users have said it does not work. Wifi, bt, suspend, hibernate, card reader, and most everything else seem to work. I'm not sure if the Intel graphics card's hd decoder works uner Ubuntu or not. I was able to play 720p though so maybe it is.

The 64bit version of Ubuntu is really a joy to run on this machine. I dual boot to play most of my games under Win7. I also run Wine and VirtualBox for games and programs like dvd decryptor and utorrent. This machine runs XP under VirtualBox very well. I am able to run XP at 1360x768 with no lag. I can even play some older games like Pharaoh with no problems.

If you are considering buying one of the vt series, stop considering and go buy it. With a little tweaking this machine is quite capable of many modern day tasks and certainly is Linux friendly.

Hopefully, nvida will realease a Linux driver that supports hybrid graphics so I can switch between cards like in Win7. That would allow me to play more of my games in Ubuntu instead of rebooting to 7.

Sorry to type your eyes off but hopefully someone will get some good info out of my post.

---

### Post by Cierreics on 2010-05-10
Hi all, finally I've installed Lucid!! \\:D/

It works very well, I've installed the 2.6.34-rc7 kernel: very fast, less power consumption and no problems with backlight, only some screen glitches...

The HAL system is deprecated in Lucid, so my previous touchpad settings on post #85 doesn't work. I've tried to write a udev rule and a xorg.conf file instead, with no luck, but the solution is really simple, using xinput!!

Open a terminal and paste this:


xinput set-prop "ImPS/2 Logitech Wheel Mouse" "Device Accel Velocity Scaling" 1000.000000


it will gives the feeling of my previous settigs, you can try to reduce the value to find a good balance with gnome mouse settings.

Once you've found out your perfect value, put that command in a new entry on System->Preferences->Startup applications.


My previous power settings on post #88 are still valid, there's only one thing you should do:


sudo gedit /usr/lib/pm-utils/power.d/powersave-policy-dirty-writeback


change the values 6000 and 1500 to both 60000 and save.

Bye! ):P

---

### Post by sbike on 2010-05-11
> **The Flying Penguin said:**
> 
Onto my experience running Lucid:

Graphics:
From all my reading I have determined that you cannot use the nvidia card under Linux at the moment. That's ok because there is a way to disable it and use the onboard Intel graphics so you can at least save some battery life.


In BIOS just set SATA to compatible mode.  Then the nvidia driver works.  

> **The Flying Penguin said:**
> 
Brightness:
No, the brightness control does not work out of the box. Neither the hotkeys or the software controls worked for me. I tried a few different solutions but none really worked. What worked for me was using the scrip provided by elchicoshinhada in post #63 on page 7 of this thread. My hotekeys now work yay! Sometimes you have to press them in 1 second intervals or the brightness bounces around and sometimes they work perfect but who cares? They work! It actually seems to work better after installing that package for turning off the nvidia card.


I believe this script improves the 1 second interval and the bouncing around a bit.  If you want the screen brightness to pick up where you left when you last logged off add the command:
/usr/bin/brightness to your startup.

Here's the script:
```

#!/bin/bash
export SEED=6
if [ ! -f ~/.brightness ]; then
        /bin/echo 99 > ~/.brightness;
fi
case "$1" in
        "up")
                export BRIGHTNESS=$[$BRIGHTNESS+$SEED];
        ;;
        "down")
                export BRIGHTNESS=$[$BRIGHTNESS-$SEED];
        ;;
        *)
                export BRIGHTNESS=`cat ~/.brightness`
        ;;
esac
if [ "$BRIGHTNESS" -gt "255" ]; then
        export BRIGHTNESS=255;
fi
if [ "$BRIGHTNESS" -lt "0" ]; then
        export BRIGHTNESS=0;
fi
echo $BRIGHTNESS > ~/.brightness
export hexbright=`/usr/bin/printf "%X" $BRIGHTNESS`
sudo setpci -s 00:02.0 F4.B=$hexbright

```

Then:
```

echo "brightness up" > /etc/acpi/asus-brn-up.sh
echo "brightness down" > /etc/acpi/asus-brn-down.sh

```

---

### Post by Orcie on 2010-05-14
On my ul30a my touchpad works great. However the thing that really bothers me now is power management. I get a 11 watts from powertop. Whereas in windows seven this was around 7.5 watts. I mostly went through the tips that are in this topic but the reported 6 or 7 watts measured in this topic I cannot get. Not even in kernel 2.6.34rc7. Also I blacklisted the webcam to prevent it from consuming power when not used. I am curious on you power achievements on this laptop.

---

### Post by Cierreics on 2010-05-14
> **Orcie said:**
> On my ul30a my touchpad works great. However the thing that really bothers me now is power management. I get a 11 watts from powertop. Whereas in windows seven this was around 7.5 watts. I mostly went through the tips that are in this topic but the reported 6 or 7 watts measured in this topic I cannot get. Not even in kernel 2.6.34rc7. Also I blacklisted the webcam to prevent it from consuming power when not used. I am curious on you power achievements on this laptop.

That's strange!! :confused:

I get 6.9 watts on idle (but I have an SSD), with screen brigthness at minimun, bluetooth and wireless off, and I get about 9 watts with wireless on....maybe you have some software running in background that drains some power....have you disabled Ubuntu One on Startup applications? Disable every daemon you don't need.

---

### Post by Orcie on 2010-05-14
> **Cierreics said:**
> That's strange!! :confused:
 
I get 6.9 watts on idle (but I have an SSD), with screen brigthness at minimun, bluetooth and wireless off, and I get about 9 watts with wireless on....maybe you have some software running in background that drains some power....have you disabled Ubuntu One on Startup applications? Disable every daemon you don't need.
 
 
I have an intel ssd aswell. Now disabled ubuntu one but still 10.6 watts. What kernel (did you recompiled it or installation from .deb?), version of ul30, and script are you running? Do you also have the load balancing thick? This causes a lot of interupts for me (25%). However it seem that this is kernel related and not yet fixed.

---

### Post by Cierreics on 2010-05-17
> **Orcie said:**
> I have an intel ssd aswell. Now disabled ubuntu one but still 10.6 watts. What kernel (did you recompiled it or installation from .deb?), version of ul30, and script are you running? Do you also have the load balancing thick? This causes a lot of interupts for me (25%). However it seem that this is kernel related and not yet fixed.

I have a Patriot Warp SSD, my Asus is an UL30A-QX194V, I have installed the 2.6.34-rc7 kernel from .deb, here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/")

I use the tips I have posted in this thread, do you really get 10.6 watts even on minimum brightness and wifi off? Can be the Intel SSD? That's strange, but maybe it causes too many kernel loads....have you done the tips for SSD disks on linux?

---

### Post by Orcie on 2010-05-17
> **Cierreics said:**
> I have a Patriot Warp SSD, my Asus is an UL30A-QX194V, I have installed the 2.6.34-rc7 kernel from .deb, here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-rc7-lucid/")

I use the tips I have posted in this thread, do you really get 10.6 watts even on minimum brightness and wifi off? Can be the Intel SSD? That's strange, but maybe it causes too many kernel loads....have you done the tips for SSD disks on linux?


What tips are you refering to? And yes I also done all the tips from this topic. !0.6 Is with wifi on.

You guys also have messed up graphics when coming back from hibernate?

---

### Post by Cierreics on 2010-05-19
[B][COLOR="Red"]
These settings are tested for Ubuntu Lucid, it's possible that some scripts doesn't work with Ubuntu Maverick.
I will write a new post for Maverick when I'll have time to upgrade!!

I will keep this post updated with all new tips and kernel upgrades!![/COLOR][/B] :KS


Here there are Asus UL30 tips for kernel, vga, backlight, power saving, touchpad, bluetooth and to run Linux on SSD (Solid State Disk). Most of these tips are also valid for other notebooks with > 2GB ram.


KERNEL and VGA
*************

Install 2.6.35 kernel and new mesa and drm libraries, wich improves Intel VGA performance, there are 2 repositories for that:

```
sudo add-apt-repository ppa:guido-iodice/guiodiclucid
```

then

```
sudo add-apt-repository ppa:guido-iodice/best-intel
```

then

```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y install linux linux-generic linux-headers-generic linux-image linux-image-generic
```

With latest kernel all screen flickerings are gone, backlight works perfectly on UL30A (with below tip), backlight notification works too!!

The guiodiclucid repository will also update some apps to maverick dev ones, ie calculator, brasero, ubuntu-software-center, volume indicator applet...

*******


BACKLIGHT
*********

It works on Asus UL30A, I've no solution for UL30VT:

```
sudo gedit /etc/default/grub
```

look at line 9, change to this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

save and close, then:

```
sudo update-grub
```

*******


POWER SAVING
*************

```
sudo apt-get install ethtool
```

This will install a tool we need.

*******

```
sudo gedit /etc/rc.local
```

add this BEFORE "exit 0":

```

rfkill block bluetooth
ethtool -s eth0 wol d
iwconfig wlan0 power timeout 500ms
echo 1 > /sys/module/snd_hda_intel/parameters/power_save
echo 0 > /proc/sys/vm/swappiness
echo 60000 > /proc/sys/vm/dirty_expire_centisecs
echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
echo 60 > /proc/sys/vm/dirty_background_ratio
echo 95 > /proc/sys/vm/dirty_ratio
echo 50 > /proc/sys/vm/vfs_cache_pressure

```

save and close.

This will turn off bluetooth at startup, disable wake on lan, enable wireless power saving, enable sound card power saving, tune virtual memory to save power.

*******

```
sudo gedit /etc/init.d/ondemand
```

paste this:

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
    	start-stop-daemon --start --background --exec /etc/init.d/ondemand background
        ;;
    background)
	sleep 60 # probably enough time for desktop login

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done
	;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```

This will correct the init script for cpu governor, default one is bugged!!
You can reduce the time value at line 22, default is "sleep 60". 
I have an SSD and my boot time is very fast, so I use "sleep 20", you can try this: 
add CPU frequency applet to your panel, reboot, login as fast as you can and look when your CPU governor switch from "performance" to "ondemand"; you can reduce the "sleep" time to a value that make governor switch appen some seconds after login, maybe "sleep 30" or "sleep 40" for a mechanical hard disk. 

*******

```
sudo gedit /etc/pm/power.d/powersave-policy-dirty-writeback
```

paste this:

```
#!/bin/sh -e
# increase dirty_writeback to ten minutes
# Author: Martin Pitt <martin.pitt@ubuntu.com>

WB=/proc/sys/vm/dirty_writeback_centisecs

[ -w $WB ] || exit 0

if [ "$1" = true ]; then
    echo 60000 > $WB
else
    echo 60000 > $WB
fi
```

save and close, then:

```
sudo chmod +x /etc/pm/power.d/powersave-policy-dirty-writeback
```

*******

```
sudo gedit /usr/lib/pm-utils/power.d/usb-autosuspend
```

paste this:

```

#!/bin/bash
if [ "$1" = "true" ]; then

  for i in /sys/bus/usb/devices/*/power/level; do
	[ "$(cat $i)" = "auto" ] && continue
	echo "auto" > $i
  done

  for i in /sys/bus/usb/devices/*/power/autosuspend; do
	[ "$(cat $i)" -ge 0 2>/dev/null ] && continue
	echo "2" > $i
  done

fi

```

save and close, then:

```
sudo chmod +x /usr/lib/pm-utils/power.d/usb-autosuspend
```

This script forces usb autosuspend for all devices.

*******

```
sudo gedit /etc/fstab
```

add this line:

```
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```

then add "commit=100" option to ext partitions, look at this fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f450fc7b-f218-4c0c-bb63-5afa69608ab4 /               ext4    commit=100,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6de7b138-6ef1-4f4a-bea0-74268a4b302c /home           ext4    commit=100,defaults        0       2
# swap was on /dev/sda5 during installation
UUID=25e066d9-6950-49ac-b078-5547ca161bfb none            swap    sw              0       0

#tmp su ram
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```

save and close.

With this setting the system will use RAM instead of disk to write temporary files, less disk usage will save power. The commit option will reduce filesystem kernel accesses.

*******

```
sudo gedit /etc/default/grub
```

look at line 10, change to this:

```
GRUB_CMDLINE_LINUX="rootflags=commit=100"
```

save and close, then:

```
sudo update-grub
```

This will reduce filesystem kernel accesses.

*******

Open Firefox, on the url bar write about:config, open it and create a new string:

```
browser.cache.disk.parent_directory
```

set the value to /tmp

This will set Firefox to write it's cache over RAM.

*******

There are two Evolution daemons that may drain some power, they keep running even after you have closed Evolution, you can uninstall them if you don't need Exchange sync and Ubuntu One calendar and contacts sync:

```
sudo apt-get purge evolution-exchange evolution-couchdb
```

*******


TOUCHPAD
*********

```
sudo gedit /etc/modprobe.d/psmouse.conf
```

paste this:

```
options psmouse force_elantech=1
```

save and close, then:

```
sudo add-apt-repository ppa:yurivkhan/proposed
```

then:

```
sudo apt-get update && sudo apt-get -y upgrade
```

This will enable our elantech touchpad for synaptic driver and install a patched gnome-settings-daemon we need.

*******

To get working disable touchpad (Fn+F9) button:

```
sudo gedit /etc/acpi/asus-touchpad.sh
```

delete everything and paste this:

```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi
```

save and close.

*******

Now we have to add an option to grub to solve touchpad problems after suspension (DON'T APPLY THIS IF YOU HAVE 2.6.35-14 OR SUCCESSIVE KERNEL, IT'S ONLY NEEDED WITH EARLIER KERNELS):

```
sudo gedit /etc/default/grub
```

look at line 9, change to this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor i8042.reset"
```

save and close, then:

```
sudo update-grub
```

*******

Reboot (apply SSD tips first if you have one), go to mouse preferences, now there's a "Touchpad" tab!!
Enable two finger scrolling and horizontal scrolling.

You'll notice that 2 finger and 3 finger tap is inverted now, let's fix it:

```
gconftool-2 --set "/desktop/gnome/peripherals/touchpad/tap_button_2" --type int "2" && gconftool-2 --set "/desktop/gnome/peripherals/touchpad/tap_button_3" --type int "3"
```

Now let's set up touchpad feeling. 
To me, this is the best setting, open a terminal:

```
synclient MinSpeed=1 MaxSpeed=1 AccelFactor=0
```

if touchpad is too speedy, reduce MinSpeed and MaxSpeed to 0.7, find your values!!

Once you've found good values, put that command in a new entry on System -> Preferences -> Startup Applications

*******


BLUETOOTH RESUME FIX
*******************

```
sudo gedit /etc/pm/sleep.d/asus-bluetooth
```

paste this:

```
#!/bin/bash
case "$1" in
 hibernate|suspend)
  invoke-rc.d --quiet bluetooth stop
  ;;
 thaw|resume)
  invoke-rc.d --quiet bluetooth start
  ;;
 *) exit $NA
  ;;
esac
```

save and close, then:

```
sudo chmod +x /etc/pm/sleep.d/asus-bluetooth
```

This will fix bluetooth switch on panel indicator applet not working after resume from suspend-hibernate.

*******


SSD TIPS
********

```
sudo gedit /etc/default/grub
```

look at line 10, change to this:

```
GRUB_CMDLINE_LINUX="elevator=noop rootflags=commit=100"
```

save and close, then:

```
sudo update-grub
```

*******

```
sudo gedit /etc/fstab
```

add "noatime" option to ext partitions, look at my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f450fc7b-f218-4c0c-bb63-5afa69608ab4 /               ext4    noatime,commit=100,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6de7b138-6ef1-4f4a-bea0-74268a4b302c /home           ext4    noatime,commit=100,defaults        0       2
# swap was on /dev/sda5 during installation
UUID=25e066d9-6950-49ac-b078-5547ca161bfb none            swap    sw              0       0

#tmp su ram
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```

save and close.

*******

I think that's all, obviously you have to reboot to apply all tips! :)

---

### Post by mric on 2010-05-20
> **AXBX7C said:**
> I just noticed that my battery capacity is at 98 percent. I'm wondering if this is normal because I bought my laptop only 2 weeks ago...

Also, using the function key to switch off wireless works but the wireless led is still on. The question is, does the function key really disable the adapter?


mine is at 97% .. discharged it completely after i bought it. will keep an eye on this.

great community btw, will try the energy saving tricks as mine still on 14w when idle

---

### Post by Cierreics on 2010-05-20
Sorry, I've messed up with bluetooth stuff, you have NOT to edit the bluetooth resume script, my previous post is wrong!! ](*,)

I've edited it, if you have already applied my tips, revert bluetooth resume script to original:

```
sudo gedit /usr/lib/pm-utils/sleep.d/49bluetooth
```

delete all and paste this:

```

#!/bin/sh
# IBM specific hack to disable/enable bluetooth.
# TODO: Doesn't the working USB suspend/resume functionality
#       make this code more or less obsolete?

. "${PM_FUNCTIONS}"

[ -f /proc/acpi/ibm/bluetooth ] || exit $NA

suspend_bluetooth()
{
	if grep -q enabled /proc/acpi/ibm/bluetooth; then
		savestate ibm_bluetooth enable
		echo disable > /proc/acpi/ibm/bluetooth
	else
		savestate ibm_bluetooth disable
	fi
}

resume_bluetooth()
{
	state_exists ibm_bluetooth || return
	restorestate ibm_bluetooth > /proc/acpi/ibm/bluetooth
}

case "$1" in
	hibernate|suspend)
		suspend_bluetooth
		;;
	thaw|resume)
		resume_bluetooth
		;;
	*) exit $NA
		;;
esac

```

save and close.

Sorry again!!


With all my settings I get 6.3 - 6.4 watts on idle with wifi ON, thanks to wireless power saving!! :guitar:

One strange thing is that after suspend there's 0.2 - 0.3 watts power conspumption increase....don't know why....:confused:

---

### Post by Hobbes on 2010-05-21
Thanks again for all the tips.

I have enabled nvidia driver and card on my ul30vt as explained by a previous poster.  I then applied most of the power-saving tricks given here (not all the ram ones because i only have 2gb ram and no swap space right now so i'm hesitant to write too much to ram in case it fills up).

Also upgraded to newer kernel, my power usage is now about 11 watts with wifi on (though this is after a suspend, and for some reason it is now saying my webcam is always on, that message i haven't seen before). Still pretty good considering a discrete graphics card is being used, my battery life is estimated at around 6-7 hours.

My brightness keys aren't working after kernel upgrade (opposite of everyone else :), so maybe i need to undo the patch I used to get them to work before the upgrade. Everything else works as far as I can tell (touchpad disable, etc)

---

### Post by AXBX7C on 2010-05-21
Great tips! I managed to get my power consumption down to about 6 W idle. With WiFi enabled and some Web surfing / Word processing it hardly goes over 8-9 W. I think that's pretty good. 

I'm not sure whether buying a SSD makes sense. Prices are too high and capacities to low for my personal taste. I believe this will change soon, though...

@mric: My battery health is around 98%. According to Asus' customer support, values between 95 and 100 percent are supposed to be normal for a newly purchased battery.

---

### Post by mediamind on 2010-05-21
Hi all - thanks very much for all the great tips! I have a UL30VT-X1 and am running Lucid (2.6.34-3-generic - via Cierreics' Post #110).

I'm having trouble getting my screen brightness hotkeys to work. I downloaded elchicosinhada's scripts (Post #63 - P.7) and used them to replace my own ACPI scripts. I can now turn the touchpad on/off with Fn+F9. 

However, using Fn+F5 or Fn+F6 doesn't affect the screen brightness at all. What am I doing wrong?

---

### Post by Cierreics on 2010-05-21
Hi all, I've noticed there are two Evolution daemons that may drain some power, they keep running even after you have closed Evolution, you can uninstall them if you don't need Exchange sync and Ubuntu One calendar and contacts sync:

```
sudo apt-get purge evolution-exchange evolution-couchdb
```



> **mediamind said:**
> However, using Fn+F5 or Fn+F6 doesn't affect the screen brightness at all. What am I doing wrong?

I have an UL30A, with Intel VGA, I don't know how to get working brightness controls on UL30VT...:(

---

### Post by KlavKalashj on 2010-05-22
My battery capacity is 84,4%, and I bought this laptop in end of september. I guess it's kind of normal usage. I have been really careful with it though, not charing it below/above 40/60% when I don't need, and remove it from computer when on AC and enough charge. Sorry for bad english, I hope you understand anyway :D

---

### Post by The Flying Penguin on 2010-05-24
Hmmm. I'm getting around 11.9- 14 watts for power consumption with your new power saving tips Cierreics. I don't have a SSD though.

What do you have your screen brightness set to?

Sadly, I am unable to adjust my brightness now after installing the nvidia drivers. I did that hot key fix for when I was using the Intel card. How would I go about resolving this issue?

I'm sure If I could turn my brightness down I would see a nice improvement in battery life.

---

### Post by mediamind on 2010-05-24
> Sadly, I am unable to adjust my brightness now after installing the nvidia drivers. I did that hot key fix for when I was using the Intel card. How would I go about resolving this issue?

A workaround for controlling screen brightness is to add the Power Manager Brightness Applet to your panel (Right click on the panel > Add to Panel... > Brightness Applet). Once installed, you can click on the Brightness Applet and then control the screen brightness with the Page Up and Page Down arrows on your keyboard.

---

### Post by The Flying Penguin on 2010-05-24
> **mediamind said:**
> A workaround for controlling screen brightness is to add the Power Manager Brightness Applet to your panel (Right click on the panel > Add to Panel... > Brightness Applet). Once installed, you can click on the Brightness Applet and then control the screen brightness with the Page Up and Page Down arrows on your keyboard.

Upgrading to this new kernel seems to have caused some issues for me. I can't add anything to my panel. I click add and nothing happens. Also, none of my programs are showing on my bottom bar at all so I have to use ALT+TAB to switch between them. I don't really care for how the file manager looks either. It's quite different in appearance then when I first installed Lucid.

EDIT: So I left my computer for like 10 minutes and now I have a whole bunch of applets on my bar from all the times I clicked add when nothing happened and my programs are back in the bottom bar. I restarted and I can still add applets with no problems now and my programs are back in the bottom bar. Must have just been a glitch?

And the brightness applet doesn't work. When I click on it the slider pops up but once I click on that, it disappears. The next time I click the brightness applet, the slider appears all the way on the far left side of the screen.

---

### Post by mediamind on 2010-05-24
> And the brightness applet doesn't work. When I click on it the slider pops up but once I click on that, it disappears. The next time I click the brightness applet, the slider appears all the way on the far left side of the screen.

It appears the Brightness Applet can only be operated via the keyboard. Click on the applet once to highlight it and then try moving the slider with your Page Up or Page Down Arrow keys to adjust the brightness level. 

Not a perfect solution but it has given me some control over the screen brightness when running on battery. I've tried this approach with success using both 2.6.32-22-generic and 2.6.34 (I installed this kernel via the instructions in Cierreics' post #110).

---

### Post by The Flying Penguin on 2010-05-24
Thank you very much sir!

With the brightness turned all the way down I get around 8.4 watts with occasional spikes up to about 10 but most of the time it never goes above 9. With the brightness turned up to a usable level and Firefox open I get in the 10 range. Once I turn the brightness up to a more comfortable level with Firefox open I'm getting in the 11-12 range . So it looks like battery life is now around what I was getting with the Intel graphics as long as I turn compiz off. If I turn on compiz I'm using around 15 watts with the brightness set at a comfortable level and Firefox open. 

So I'll just turn off compiz when on battery. No biggie. It appears I should be able to get between 6-7 hours on battery but I try not to let the battery drain that low so probably more like 5 or so.

Good deal if you ask me. :)

---

### Post by Hobbes on 2010-05-25
yeah i hadn't thought about compiz off as a useful saving feature.  My other major issue with nvidia drivers on is that suspend takes a lot longer to come back from, and startup is possibly marginally slower than before.  But at least both work fine, so not a huge deal.  Not having to worry about nvidia card coming back on after suspend without being able to turn it back off like before when intel card was the one actually working is a nice point in favor of it always on :)

Also perhaps slightly warmer.

*update* I also had an issue where couldn't view video in movie player, vlc, mplayer... had to switch the video output, though in mplayer it is now one of the outputs which won't expand to fullscreen :(  Anybody know if/how to get vdpau working with this card?

---

### Post by Cierreics on 2010-05-27
Hi all, kernel 2.6.34-4 is out (look at my post [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") to add repository for this kernel):

```
sudo apt-get update && sudo apt-get install linux-headers-2.6.34-4 linux-headers-2.6.34-4-generic linux-image-2.6.34-4-generic
```


Last week there was an update for pm-utils, so one of my tips was overwritten, here is a solution to restore it and to prevent future overwrites:

```
sudo gedit /etc/pm/power.d/powersave-policy-dirty-writeback
```

paste this:

```
#!/bin/sh -e
# increase dirty_writeback to ten minutes
# Author: Martin Pitt <martin.pitt@ubuntu.com>

WB=/proc/sys/vm/dirty_writeback_centisecs

[ -w $WB ] || exit 0

if [ "$1" = true ]; then
    echo 60000 > $WB
else
    echo 60000 > $WB
fi
```

save and close, then:

```
sudo sudo chmod +x /etc/pm/power.d/powersave-policy-dirty-writeback
```


That update also removed the powersave-sata-link-power script, they probably figured out that script brokes suspension with an SSD!! :)
So I've also updated my post [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") to these modifications.

---

### Post by The Flying Penguin on 2010-05-27
> **Hobbes said:**
> 
*update* I also had an issue where couldn't view video in movie player, vlc, mplayer... had to switch the video output, though in mplayer it is now one of the outputs which won't expand to fullscreen :(  Anybody know if/how to get vdpau working with this card?

I was having problems with video too but now they work great with vdpau.
[http://ubuntuforums.org/showthread.php?t=1478589](http://ubuntuforums.org/showthread.php?t=1478589)

Here's what I did:
1) Install "libvdpau1" from the package manager.
2) Open a terminal and type "gstreamer-properties" and then under the video tab set the default output plugin to "X Window System (No xv)".
3) Set SMPlayer's video output driver to "vdpau".

Now after restarting (maybe you don't have to but I did) SMPlayer you should be all good to go!

Let me know if that works for you.

---

### Post by Cierreics on 2010-05-27
I forgot one thing, with last kernel you have to do this to have working backlight controls on UL30A:

```
sudo gedit /etc/default/grub
```

look at line 9, change to this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash, acpi_backlight=vendor"
```

save and close, then:

```
sudo update-grub
```

then reboot.

---

### Post by TomtheWombat on 2010-05-27
> **Cierreics said:**
> Hi all, kernel 2.6.34-4 is out

I guess that 2.6.34 has some support for the new elantech touchpads if you force it.  See here: [http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

I haven't tried it, though.

---

### Post by Cierreics on 2010-05-27
> **TomtheWombat said:**
> I guess that 2.6.34 has some support for the new elantech touchpads if you force it.  See here: [http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

I haven't tried it, though.

Yes!! Thank you VERY much!! I've missed that thread!! :guitar:

I've tried it, with 2.6.34 kernel it's really simple, now finally horizontal scroll works and touchpad is disabled while typing!! :guitar:


Here's an how-to (you have to install 2.6.34 kernel first):

```
sudo gedit /etc/modprobe.d/psmouse.conf
```

paste this:

```
options psmouse force_elantech=1
```

save and close.


Let's enable fn+F9 button:

```
sudo gedit /etc/acpi/asus-touchpad.sh
```

delete everything and paste this:

```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

if (! test -x /usr/bin/xinput)
then
logger "Error: Please install package xinput to enable toggling of touchpad devices."
exit 0
fi

# if this is the right behavior, then this should be moved out of acpi-support
# to hal (or whatever is replacing hal for such events)
getXconsole

XINPUTNUM=`xinput list | grep 'ETPS/2 Elantech Touchpad' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`

[ -f /usr/share/acpi-support/state-funcs ] || exit 0

# get the current state of the touchpad
TPSTATUS=`xinput list-props $XINPUTNUM | awk '/Synaptics Off/ { print $NF }'`

# if getting the status failed, exit
test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 0 ]; then
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 1
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 0 > /sys/class/leds/asus::touchpad/brightness
   fi
else
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 0
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 1 > /sys/class/leds/asus::touchpad/brightness
   fi
fi
```

save and close.


Now reboot, go to mouse preferences, now there's a "Touchpad" tab!! :guitar: 
Enable two finger scrolling and horizontal scrolling.


You'll notice that 2 finger and 3 finger tap is inverted now, so let's revert it and set up touchpad feeling. 
To me, this is the best setting, open a terminal:

```
synclient MinSpeed=1 MaxSpeed=1 AccelFactor=0 TapButton2=2 TapButton3=3
```

if touchpad is too speedy, reduce MinSpeed and MaxSpeed to 0.7, find your values!!

Once you've found good values, put that command in a new entry on System -> Preferences -> Startup Applications


I've also updated my [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post. ):P

---

### Post by Cierreics on 2010-05-28
There's a problem in my previous setting: if you plug a usb mouse, the tap buttons revert again!! I don't know why, but there's a fix, you have to install a patched gnome-setting-daemon, there's a repository for that:

```
sudo add-apt-repository ppa:yurivkhan/proposed
```

then:

```
sudo apt-get update && sudo -y apt-get upgrade
```

Now end your session and login again, then:

```
gconftool-2 --set "/desktop/gnome/peripherals/touchpad/tap_button_2" --type int "2" && gconftool-2 --set "/desktop/gnome/peripherals/touchpad/tap_button_3" --type int "3"
```


I've also updated my [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post. :guitar:

---

### Post by drk0t on 2010-05-29
Hi all!
How to enable sound through hdmi?
Thanks!

---

### Post by The Flying Penguin on 2010-05-29
> **drk0t said:**
> Hi all!
How to enable sound through hdmi?
Thanks!

[http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

I think that should do it but I haven't tried it out yet.

---

### Post by elchicosinhada on 2010-05-30
> **The Flying Penguin said:**
> [http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

I think that should do it but I haven't tried it out yet.

Has anyone found the correct code for our laptop?

---

### Post by Cierreics on 2010-05-30
> **elchicosinhada said:**
> Has anyone found the correct code for our laptop?

Do you have a UL30VT? I have an UL30A and the HDMI audio is shown under audio preferences, but I can't test it 'cause I don't have an hdmi cable to plug on my monitor :(

But I've read somewhere that HDMI audio works fine on UL30A if you select it in audio preferences...

---

### Post by Hobbes on 2010-05-30
> **The Flying Penguin said:**
> I was having problems with video too but now they work great with vdpau.
[http://ubuntuforums.org/showthread.php?t=1478589](http://ubuntuforums.org/showthread.php?t=1478589)

Here's what I did:
1) Install "libvdpau1" from the package manager.
2) Open a terminal and type "gstreamer-properties" and then under the video tab set the default output plugin to "X Window System (No xv)".
3) Set SMPlayer's video output driver to "vdpau".




THANKS!! Didn't have to restart and now watching the same video that in totem/old way took 40-50% cpu only needs 9-10% with mplayer+vdpau.  Great :)

I'll try the trackpad fix(es) in a bit. Thanks for the updates guys (2.6.34-5 is out by the way so i went straight to that, don't know if anything will be different with this kernel)

---

### Post by elchicosinhada on 2010-05-31
> **Cierreics said:**
> Do you have a UL30VT? I have an UL30A and the HDMI audio is shown under audio preferences, but I can't test it 'cause I don't have an hdmi cable to plug on my monitor :(

But I've read somewhere that HDMI audio works fine on UL30A if you select it in audio preferences...

I have a UL50VT, it is equal that UL30VT.
In kmix (KDE), I have Nvidia HDA and Intel HDA, but when I plug the HDMI to TV, it don't sound.

---

### Post by Cierreics on 2010-05-31
> **elchicosinhada said:**
> I have a UL50VT, it is equal that UL30VT.
In kmix (KDE), I have Nvidia HDA and Intel HDA, but when I plug the HDMI to TV, it don't sound.

Try to add your user to audio group!

If you switch to Intel vga, does audio works?

---

### Post by FrezoreR on 2010-05-31
I by accident touches the mouse pad while typing on the keypad, which changes focus or moves the typing cursor.

How do I change at what pressure level the mouse pad activates in ubuntu 10.4?

Is there any ways to do advanced setup of the mouse pad as I can under Windows?

---

### Post by mediamind on 2010-05-31
> Thanks for the updates guys (2.6.34-5 is out by the way so i went straight to that, don't know if anything will be different with this kernel)

Dumb question - how exactly did you install 2.6.34-5?

---

### Post by The Flying Penguin on 2010-06-01
> **mediamind said:**
> Dumb question - how exactly did you install 2.6.34-5?

First, add the repository:
> 
sudo add-apt-repository ppa:guido-iodice/guiodiclucid

Then:
> 
sudo apt-get update && sudo apt-get install linux-headers-2.6.34-5 linux-headers-2.6.34-5-generic linux-image-2.6.34-5-generic

You can then go through and delete the old kernels.

Restart for changes to take effect.


Now, I have my own question. It seems after the last kernel upgrade my power usages has spiked. I have the brightness turned almost half way down and I'm using 15 watts of power. Does this new kernel undo the power saving scripts you posted Cierreics?

---

### Post by loko on 2010-06-01
hello you ul30-owners.

i own one myself (ul30a). my mic is really bad. in fact, it's almost unusable to record any voice. there is a very bad noise all the time while recording.
It's also happening with Windows 7, so it could be that the mic is bad in gerneral - or it is broken.

is somebody experiencing the same problem or is my mic just broken?

---

### Post by mediamind on 2010-06-02
I haven't experienced any mic issues with my UL30VT - sounds like yours may indeed be broken.

---

### Post by Cierreics on 2010-06-03
Hi all, I was very busy this week...](*,)

2.6.34-5 kernel is out, The Flying Penguin already wrote how to install it :guitar:


I have some new tips, one of them is very important!

*******

```
sudo apt-get install ethtool
```

This will install a tool we need.

*******

```
sudo gedit /etc/rc.local
```

modify my previous settings to this:

```

rfkill block bluetooth
ethtool -s eth0 wol d
iwconfig wlan0 power timeout 500ms
echo 1 > /sys/module/snd_hda_intel/parameters/power_save
echo 0 > /proc/sys/vm/swappiness
echo 60000 > /proc/sys/vm/dirty_expire_centisecs
echo 60000 > /proc/sys/vm/dirty_writeback_centisecs
echo 60 > /proc/sys/vm/dirty_background_ratio
echo 95 > /proc/sys/vm/dirty_ratio
echo 50 > /proc/sys/vm/vfs_cache_pressure

```

save and close.

I've added wake on lan disable setting, cache vm setting, and REMOVED cpu scaling governor settings (this is important!!). 

*******

This is important!!

```
sudo gedit /etc/init.d/ondemand
```

paste this:

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
    	start-stop-daemon --start --background --exec /etc/init.d/ondemand background
        ;;
    background)
	sleep 60 # probably enough time for desktop login

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done
	;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```

This will correct the init script for cpu governor, default one is bugged!!
You can reduce the time value at line 22, default is "sleep 60". 
I have an SSD and my boot time is very fast, so I use "sleep 20", you can try this: 
add CPU frequency applet to your panel, reboot, login as fast as you can and look when your CPU governor switch from "performance" to "ondemand"; you can reduce the "sleep" time to a value that make governor switch appen some seconds after login, maybe "sleep 30" or "sleep 40" for a mechanical hard disk.

*******

```
sudo gedit /etc/fstab
```

add "commit=100" option to ext partitions, look at this fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f450fc7b-f218-4c0c-bb63-5afa69608ab4 /               ext4    commit=100,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6de7b138-6ef1-4f4a-bea0-74268a4b302c /home           ext4    commit=100,defaults        0       2
# swap was on /dev/sda5 during installation
UUID=25e066d9-6950-49ac-b078-5547ca161bfb none            swap    sw              0       0

#tmp su ram
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```

save and close.

The commit option will reduce filesystem kernel accesses.

*******

```
sudo gedit /etc/default/grub
```

look at line 10, change to this:

```
GRUB_CMDLINE_LINUX="rootflags=commit=100"
```

save and close, then:

```
sudo update-grub
```

This will reduce filesystem kernel accesses.



If you have an SSD, here's some modifications to my previous tips:

```
sudo gedit /etc/default/grub
```

look at line 10, change to this:

```
GRUB_CMDLINE_LINUX="elevator=noop rootflags=commit=100"
```

save and close, then:

```
sudo update-grub
```

*******

```
sudo gedit /etc/fstab
```

add "noatime" option to ext partitions, look at my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f450fc7b-f218-4c0c-bb63-5afa69608ab4 /               ext4    noatime,commit=100,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=6de7b138-6ef1-4f4a-bea0-74268a4b302c /home           ext4    noatime,commit=100,defaults        0       2
# swap was on /dev/sda5 during installation
UUID=25e066d9-6950-49ac-b078-5547ca161bfb none            swap    sw              0       0

#tmp su ram
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

```

save and close.

---

### Post by Cierreics on 2010-06-03
> **FrezoreR said:**
> I by accident touches the mouse pad while typing on the keypad, which changes focus or moves the typing cursor.

How do I change at what pressure level the mouse pad activates in ubuntu 10.4?

Is there any ways to do advanced setup of the mouse pad as I can under Windows?

Follow my touchpad guide in [this]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post.

It will enable elantech driver, wich will auto-disable touchpad when typing!! :guitar:

---

### Post by Cierreics on 2010-06-03
> **The Flying Penguin said:**
> Now, I have my own question. It seems after the last kernel upgrade my power usages has spiked. I have the brightness turned almost half way down and I'm using 15 watts of power. Does this new kernel undo the power saving scripts you posted Cierreics?

That's strange, with 2.6.34-5 kernel I'm on ~6.5 watts on idle...

Try my new settings for cpu scaling governor, and it's better if you check and reapply all settings, I've updated [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post. :KS

---

### Post by nico-ar on 2010-06-09
with the new kernel 2.6.34, can you switch the gpu? or disable the nvidia gpu? how?
thanks

---

### Post by mediamind on 2010-06-11
> with the new kernel 2.6.34, can you switch the gpu? or disable the nvidia gpu? how?


Not easily. I'm running the Nvidia driver/card on my UL30VT (Lucid 64-bit) and here's one clunky way I've found to switch to the Intel card:

1. Reboot
2. Enter BIOS (press F2) and switch the IDE Configuration/SATA Operation Mode back to "Enhanced" from "Compatible." Press F10 to save and exit.
3. The system will attempt to boot. When the "Ubuntu is running in low-graphics mode dialog window appears, select "OK" and then select "Run Ubuntu in low-graphics mode for just one session." 

Everything seems to work (720p on YouTube, suspend and resume from suspend, etc) using this method. The one downside is that both graphics cards are active which obviously impacts battery life. You can confirm this with: ```
lspci |grep VGA
```

Clearly this is not a practical approach to switching between cards. I personally would love to be able to run the Nvidia driver using "Enhanced" mode - the slower boot and resume from suspend times are a bit of drag under "Compatible" mode.

---

### Post by Cierreics on 2010-06-14
Hi all, you will find 2.6.35 kernel on Guiodic repo, I've tried it but it's not stable yet, I get a system freeze everytime I try to watch fullscreen flash videos with firefox...I'm back to 2.6.34-5 kernel. ):P

---

### Post by mediamind on 2010-06-15
> Hi all, you will find 2.6.35 kernel on Guiodic repo, I've tried it but it's not stable yet, I get a system freeze everytime I try to watch fullscreen flash videos with firefox...I'm back to 2.6.34-5 kernel.

I'm running 2.6.35.999 from the [**Ubuntu Mainline Archive**]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/") on my UL30VT (Lucid 64-bit) with the Nvidia card activated and haven't experienced any freezes yet...full screen flash videos on firefox seem to work fine.

---

### Post by mediamind on 2010-06-15
Btw, in case anyone else has experienced the gnome-power-manager going into hibernate rather than suspend on idle (when on battery power) I thought I would share an easy workaround. As I just mentioned, I have a UL30VT running Lucid 64-bit (2.6.35.999) with the Nvidia card activated.

1. Open the Configuration Editor by opening a terminal (or pressing Alt+F2) and typing: 
```
gconf-editor
```

2. Navigate to apps > gnome-power-manager > actions sleep_type_battery

3. Click on "hibernate" and replace the text with "suspend"

Fyi, there is already a [**bug report filed on Launchpad**]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/576698") - thanks to James Adney for the workaround.

---

### Post by Cierreics on 2010-06-15
> **mediamind said:**
> I'm running 2.6.35.999 from the [**Ubuntu Mainline Archive**]("http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/") on my UL30VT (Lucid 64-bit) with the Nvidia card activated and haven't experienced any freezes yet...full screen flash videos on firefox seem to work fine.

I've installed 64bit alpha flash player, do you use regular one?

---

### Post by mediamind on 2010-06-15
> I've installed 64bit alpha flash player, do you use regular one?

Yes (10.1.53.64). I installed it via ubuntu-restricted-extras.

---

### Post by Cierreics on 2010-06-15
> **mediamind said:**
> Yes (10.1.53.64). I installed it via ubuntu-restricted-extras.

Tnx, I was on 64bit alpha (wich was 10.0 version) cause I got problems with 32bit 10.0 standard version...now I've installed the new 32bit 10.1 version, it works perfectly, much better than 64bit alpha, now all problems I had with previous 32bit 10.0 version are gone, and no freezes with 2.6.35 kernel!! :guitar:

---

### Post by Cierreics on 2010-06-15
Two weeks ago Guiodic made another repository for mesa and drm libraries, wich improves Intel VGA performance, I've installed them last week and everything works perfectly, here there are:

```
sudo add-apt-repository ppa:guido-iodice/best-intel
```

then:

```
sudo apt-get update && sudo -y apt-get upgrade
```


Note that you have to install 2.6.34 or 2.6.35 kernel first!! ):P

---

### Post by Cierreics on 2010-06-16
Too bad, even with new flash plugin, sometimes I have system freezes...it seems random...I'm back again to 2.6.34-5 kernel, wich works perfectly... :mad:

---

### Post by mediamind on 2010-06-16
>  Too bad, even with new flash plugin, sometimes I have system freezes...it seems random...I'm back again to 2.6.34-5 kernel, which works perfectly... 

Sorry to hear that Cierreics. I'm using the Nvidia driver/card in my UL30VT which may be preventing the system freezes on the newer kernel. Hopefully in the future we'll be less dependent upon Flash as more of the web adopts the [**HTML5 standard**]("http://www.html5video.org/") for video.

---

### Post by Cierreics on 2010-06-16
> **mediamind said:**
> Sorry to hear that Cierreics. I'm using the Nvidia driver/card in my UL30VT which may be preventing the system freezes on the newer kernel. Hopefully in the future we'll be less dependent upon Flash as more of the web adopts the [**HTML5 standard**]("http://www.html5video.org/") for video.

Yes, I can't wait for a stable Firefox with HTML5 support!! :cool:

---

### Post by The Flying Penguin on 2010-06-16
> **Cierreics said:**
> Two weeks ago Guiodic made another repository for mesa and drm libraries, wich improves Intel VGA performance, I've installed them last week and everything works perfectly

I was under the impression you were using the nvidia card. Are you using the Intel card or switching between cards?

And while on the topic of flash. I currently run the 64bit alpha and it works pretty well. There are a few Hulu videos that won't play but I rarely use that anyway. I tried installing Flash 32 in Firefox under Wine just for backwards compatibility but couldn't get it to work. I'll try playing around with it more and see if I can give it to work. It should work. You can even install it under Winetricks.

My one question regarding flash 64 is, does it utilize hardware acceleration under Linux?

---

### Post by Cierreics on 2010-06-16
> **The Flying Penguin said:**
> I was under the impression you were using the nvidia card. Are you using the Intel card or switching between cards?

And while on the topic of flash. I currently run the 64bit alpha and it works pretty well. There are a few Hulu videos that won't play but I rarely use that anyway. I tried installing Flash 32 in Firefox under Wine just for backwards compatibility but couldn't get it to work. I'll try playing around with it more and see if I can give it to work. It should work. You can even install it under Winetricks.

My one question regarding flash 64 is, does it utilize hardware acceleration under Linux?

I have an UL30A, with Intel VGA only! :p

I suggest you to install 32bit 10.1 flash plugin (sudo apt-get install flashplugin-nonfree), it works better than 64bit alpha to me!! :KS

You only have to do a minor fix if you have problems with mouse click responding on flash player buttons: 

```
sudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

delete all and paste this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

save, close and restart your browser.


Unfortunately hardware acceleration is not supported under linux, let's hope for the next release, HD video playback is still a little choppy.... :mad:

---

### Post by mric on 2010-06-16
i was able to get a long term ( surfin, video ) of around 9.2W and in idle state 7.8 with all the power saving tips listed here and kernel 2.6.35 .. however youtube 1080p and or 720p fullscreen is not good at all .. any ideas? ( using the 32bit plug in  mentioned in the thread earlier )

cheers
mike

---

### Post by Cierreics on 2010-06-16
> **mric said:**
> i was able to get a long term ( surfin, video ) of around 9.2W and in idle state 7.8 with all the power saving tips listed here and kernel 2.6.35 .. however youtube 1080p and or 720p fullscreen is not good at all .. any ideas? ( using the 32bit plug in  mentioned in the thread earlier )

cheers
mike

Yes, 1080p videos are unwatchable, 720p are watchable but a little choppy....a good workaround is to leave youtube open with video set to 1080p (or 720p), then go with Nautilus to your browser cache folder, find the flash video and open it with Totem!! Fullscreen playback works perfectly!! :guitar: 

If you applied my tips you should find Firefox cache on /tmp, so you can add a bookmark to Nautilus sidebar to reach cached videos with a single click!! \\:D/

---

### Post by drk0t on 2010-06-19
CPU frequency applet shows that "Frequency Scaling Unsupported". This is normal?

---

### Post by mric on 2010-06-19
> **drk0t said:**
> CPU frequency applet shows that "Frequency Scaling Unsupported". This is normal?


depending on the model .. i think the ul30a with SU2300 doesn't support it


> **Cierreics said:**
> Yes, 1080p videos are unwatchable, 720p are  watchable but a little choppy....a good workaround is to leave youtube  open with video set to 1080p (or 720p), then go with Nautilus to your  browser cache folder, find the flash video and open it with Totem!!  Fullscreen playback works perfectly!! :guitar: 

If you applied my tips you should find Firefox cache on /tmp, so you can  add a bookmark to Nautilus sidebar to reach cached videos with a single  click!! \\:D/


your a star, works perfect !

---

### Post by drk0t on 2010-06-19
> **mric said:**
> depending on the model .. i think the ul30a with SU2300 doesn't support it

Thanks. But
> 
Intel® Celeron® Processor SU2300 (1M Cache, 1.20 GHz, 800 MHz FSB):
Essentials
Status	                Launched
Launch Date	        Q3'09
Processor Number	SU2300
# of Cores	        2
# of Threads	        2
Clock Speed	        1.2 GHz
FSB Speed	        800 MHz
Embedded Options Available	No
Supplemental SKU	        No
Lithography	        45 nm
Max TDP	                10 W
# of Processing Die Transistors	410 million
Sockets Supported	BGA956
Halogen Free Options Available	Yes

Advanced Technologies
Intel® Turbo Boost Technology	          No
Intel® Virtualization Technology (VT-x)	  Yes
Intel® Trusted Execution Technology	  No
Intel® 64	                          Yes
**Enhanced Intel® Speedstep Technology	  Yes**
Thermal Monitoring Technologies	          Yes
 
from [http://ark.intel.com/Product.aspx?id=42779&processor=SU2300&spec-codes=SLGSB,SLGYW](http://ark.intel.com/Product.aspx?id=42779&processor=SU2300&spec-codes=SLGSB,SLGYW)

---

### Post by hojgaard on 2010-06-19
> **Cierreics said:**
> Yes, 1080p videos are unwatchable, 720p are watchable but a little choppy....a good workaround is to leave youtube open with video set to 1080p (or 720p), then go with Nautilus to your browser cache folder, find the flash video and open it with Totem!! Fullscreen playback works perfectly!!  

If you applied my tips you should find Firefox cache on /tmp, so you can add a bookmark to Nautilus sidebar to reach cached videos with a single click!! 


Or just use MiniTube... Great fast app for watching youtube videos. Love to give flash my middle finger...

---

### Post by mric on 2010-06-24
> **Cierreics said:**
> Too bad, even with new flash plugin, sometimes I have system freezes...it seems random...I'm back again to 2.6.34-5 kernel, wich works perfectly... :mad:

same to me, 2.6.35 kernel causes system hangs in different szenarios  =/


fatal mistake!! i realized, that the laptop stops, freezes after approx 10min wathcing videos or mp3s .. i did realize that i have this issues when on battery power .. so i did check the power saving values again and it looks like that SPINNING DOWN HARDDISK kills everything .. i disabled it and voila .. worx so far. any ideas if this parameter is configurable eg.: spinning down harddisk when 1h idle orso?

cheers
mike

---

### Post by Cierreics on 2010-06-26
> **mric said:**
> same to me, 2.6.35 kernel causes system hangs in different szenarios  =/

Look at this: [http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1]("http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1") :(

Big troubles, I'll stay on 2.6.34 for a long time... :(

But if you want to use 2.6.35 for testing purpose, in the guiodic repo there are linux-headers, linux-headers-generic, linux-image, linux-image-generic packages, you can install them to get automatic updates for 2.6.35 kernel.

---

### Post by mediamind on 2010-06-26
> Look at this: [http://www.phoronix.com/scan.php?pag...635_fail&num=1](http://www.phoronix.com/scan.php?pag...635_fail&num=1)

Big troubles, I'll stay on 2.6.34 for a long time... 

It appears the 2.6.35 issue has been resolved. Check out [**this Phoronix blog post**]("http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ") from June 3-10.

Re 2.6.35, I've been testing mainline kernels on my UL30VT (64-bit) and have recently installed 2.6.35rc3 (June 12) from the Ubuntu mainline repository with no problems to report as of yet... 

To install this version, visit [**the mainline repository**]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/") and click on the links to install these 3 packages (use the following order to ensure all dependencies are met):
linux-image (pick your system: i386 or amd64)
linux-headers (all)
linux-headers (pick your system: i386 or amd64)

---

### Post by PatrickVogeli on 2010-06-26
> **drk0t said:**
> Thanks. But
 
from [http://ark.intel.com/Product.aspx?id=42779&processor=SU2300&spec-codes=SLGSB,SLGYW](http://ark.intel.com/Product.aspx?id=42779&processor=SU2300&spec-codes=SLGSB,SLGYW)
the SU2300 only has a P-state: 1200Mhz, it can't clock lower..

---

### Post by The Flying Penguin on 2010-06-27
> **PatrickVogeli said:**
> the SU2300 only has a P-state: 1200Mhz, it can't clock lower..

Hmm, glad I have the SU7300 :P

I wasn't even aware the SU2300 was available in the UL series.


Aside from that. I have a question for those of you using the UL series with the 2.6.34-5 kernel, specifically those with the SU7300 with the Nvidia graphics (I'm not sure if that matters).

Have any of you noticed an increase in the amount of time it takes to suspend/hibernate and resume? How about startup and shutdown times? All have dramatically increased for me. Hibernation takes a couple of minutes for me to get back to my desktop. Sometimes it even seems that its faster for me to turn the machine on and off then to use suspend. Sometimes it takes so long to get out of suspend or hibernate that the machine actually turns off before it can resume. I then have to turn the machine on again and then I actually have to go through grub and select Ubuntu but it does ultimately return me to what I was working on.

I'm having trouble remembering if this just started with the 2.6.34-5 kernel or if it was 2.6.34-4. It is pretty annoying.

---

### Post by mediamind on 2010-06-27
> Aside from that. I have a question for those of you using the UL series with the 2.6.34-5 kernel, specifically those with the SU7300 with the Nvidia graphics (I'm not sure if that matters).

Have any of you noticed an increase in the amount of time it takes to suspend/hibernate and resume? How about startup and shutdown times? All have dramatically increased for me. 

Using "Compatible" rather than "Enhanced" mode seems to degrade the I/O performance of the hard drive - hence the slower boot/resume times. I'm running 2.6.35rc3 on my UL30VT with the Nvidia driver and have also tested 2.6.34-5 along with a few other kernels including the stock kernel and can confirm that resume from suspend takes 20-30 seconds in all instances. The boot time is slower as well as is resume from hibernate.

I agree this is annoying - I would love to be able to run the Nvidia driver/GPU on Enhanced mode...

---

### Post by The Flying Penguin on 2010-06-27
So what is the reason for having to run compatible mode and not enhanced? Is this an Nvidia issue or a Linux one?

---

### Post by mediamind on 2010-06-27
> So what is the reason for having to run compatible mode and not enhanced? Is this an Nvidia issue or a Linux one? 


A good question. I believe it is a Linux issue and know there is at least **[one bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575750")** already. See **[mscan's comment #31]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575750/comments/31")** for a few more details...

---

### Post by The Flying Penguin on 2010-06-28
> **mediamind said:**
> A good question. I believe it is a Linux issue and know there is at least **[one bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575750")** already. See **[mscan's comment #31]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575750/comments/31")** for a few more details...

Very interesting. So basically turning on compatible mode is the only way to turn off the Intel card.

I'm sure someone is working on an alternative method to disable the Intel card via Linux without taking a disk performance hit. I'll just wait patiently. :popcorn:

---

### Post by mediamind on 2010-06-28
> I'm sure someone is working on an alternative method to disable the Intel card via Linux without taking a disk performance hit. I'll just wait patiently.

Yes, hopefully you're right!

The bug report hasn't received much feedback from the community. Could be valuable to add a brief comment and/or click on the green link at the top of the page indicating that "this bug affects you."

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575750?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575750?comments=all)

---

### Post by mric on 2010-06-29
i am still experiencing freezes and want to point to the following thread which seems to descrive the problem

>  X locks up but the mouse can still be moved.

[http://ubuntuforums.org/showthread.php?p=8516362](http://ubuntuforums.org/showthread.php?p=8516362)

---

### Post by Adavistic Puma on 2010-06-30
> I'm sure someone is working on an alternative method to disable the Intel card via Linux without taking a disk performance hit. I'll just wait patiently. 

Looks like it's probably going to be a bit more complicated than that:
I have tried removing the intel device from the PCI bus, by means of the fake pci hotplug driver:
(with nomodeset kernel option) rmmod i915 && modprobe fakephp  &&  echo 0 > /sys/bus/pci/slots/0000\:00\:02.0/power && modprobe nvidia-current

Yet that still doesn't seem to allow the nvidia card to be used in X;
information in Xorg.0.log looks almost the same as when specifying a BusID for the nvidia card

maybe another method, via setpci or something, would work better.

The funny thing is, the Intel device & i915 driver comes back when sending a power-on signal to the SATA controller:
echo 1 > /sys/bus/pci/slots/0000\:00\:1f.2/power

so, despite having different IRQs, these 2 devices do seem tied together somehow

I have started to add comments to this bug instead;  Seems more relevant:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/312756)

---

### Post by Cierreics on 2010-07-01
> **mediamind said:**
> It appears the 2.6.35 issue has been resolved. Check out [**this Phoronix blog post**]("http://www.phoronix.com/scan.php?page=news_item&px=ODMxNQ") from June 3-10.


Yeah, I was wrong, with new 2.6.35 updates on Guiodic repo and recent flashplayer updates, all freezes problems seem to be gone!! :guitar:

---

### Post by The Flying Penguin on 2010-07-07
I haven't had the chance to try out the 2.6.35 kernel but I'd like to do so if you guys can clear this up for me. Which repository should I install it from? Cierreics, I assume you use the Guiodic repo and Mediamind you say to use the Ubuntu mainline repo. Which one am I supposed to use? What is the difference? The one in the mainline repo says its rc3. Are these kernels just at different stages of development?

I also am curious as to the state of overclocking the U7300 under Ubuntu. Under Windows 7, Asus provides that Turbo 33 program that automatically overclocks the CPUs to 1.7GHz when you need the extra juice. Is Ubuntu capable of doing this?

I would be fine with having to manually select to overclock. Do I need to edit a config file to add 1.7GHz to the CPU scaling monitor app? It would really be nice to have a little extra juice when playing games under Wine.

---

### Post by mediamind on 2010-07-10
> I haven't had the chance to try out the 2.6.35 kernel but I'd like to do so if you guys can clear this up for me. Which repository should I install it from? Cierreics, I assume you use the Guiodic repo and Mediamind you say to use the Ubuntu mainline repo. Which one am I supposed to use? What is the difference? 

The mainline repo is maintained by the Ubuntu Kernel Team. I believe the Guiodic repo is maintained by an Italian developer - perhaps Cierreics can provide more details. 

> 
What is the difference? The one in the mainline repo says its rc3. Are these kernels just at different stages of development? 

I don't know much about the Guiodic repo - again Cierreics may be able to provide more details. Re the mainline kernels, check out [**this Ubuntu wiki page**]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds") for more info. 

Also, to install and test the most current kernel, try: **[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)**

> I also am curious as to the state of overclocking the U7300 under Ubuntu. Under Windows 7, Asus provides that Turbo 33 program that automatically overclocks the CPUs to 1.7GHz when you need the extra juice. Is Ubuntu capable of doing this? 

The BIOS provides some basic options for overclocking (I'm running version 210 though I believe this option has been available since version 206). The default setting seems to be "3" - I haven't tried altering this though I believe others have had success with "4" and mixed to poor results with "5." 

If you decide to experiment with overclocking, be sure to let us know what you learn.

---

### Post by Cierreics on 2010-07-11
> **mediamind said:**
> The mainline repo is maintained by the Ubuntu Kernel Team. I believe the Guiodic repo is maintained by an Italian developer - perhaps Cierreics can provide more details.

Guiodic repo contains latest kernel and some lucid updates at maverick development stage, ie new software center, new volume indicator applet, new calculator....

You can download 2.6.35 kernel from ppa mainline and install it manually, or you can add guiodic repo, the difference is that you have to wait some days to find latest kernel in guiodic repo, but you gain auto-updates if you install some packages (linux linux-generic linux-headers-generic linux-image linux-image-generic). 

Now I'm on 2.6.35-7 on guiodic repo, it solved all minor problems I had with previous 2.6.35 kernels, but probably you will find that touchpad is dead after suspend, and you have to use an usb mouse. To solve it you have to add "i8042.reset" option to grub:

```
sudo gedit /etc/default/grub
```

look at line 9, change to this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor i8042.reset"
```

save and close, then:

```
sudo update-grub
```

then shutdown and power on again, a simple reboot wasn't enough for me.

---

### Post by The Flying Penguin on 2010-07-13
Hmm, I finally decided to try the 2.6.35-7 kernel from the Guiodic repo and seem to be having some issues. It doesn't show up in Synaptic and when I try installing from terminal I get the error: "E: Couldn't find package linux-headers-2.6.35-7"

This is what I put in terminal:
```
sudo apt-get update && sudo apt-get install linux-headers-2.6.35-7 linux-headers-2.6.35-7-generic linux-image-2.6.35-7-generic 
```That is what I put in the last couple times (with the correct kernel I'm trying to install obviously) I've upgraded the kernel.

The Guiodic repo is in my list of added repos.

Should I just leave out the linux-headers-2.6.35-7? I need everything right?

---

### Post by Cierreics on 2010-07-14
> **The Flying Penguin said:**
> Hmm, I finally decided to try the 2.6.35-7 kernel from the Guiodic repo and seem to be having some issues.

You don't need to specify kernel version with guiodic repo, now it contains all metapackages you need to get auto-updates for latest kernel, follow my [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post:

```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y install linux linux-generic linux-headers-generic linux-image linux-image-generic
```

This will install latest kernel (now 2.6.35-7) and keep it updated.

---

### Post by The Flying Penguin on 2010-07-15
Hmm. I'm getting this back:
```
linux is already the newest version.
linux-generic is already the newest version.
linux-headers-generic is already the newest version.
linux-image is already the newest version.
linux-image-generic is already the newest version.

```

That is certainly not the case. I know for a fact I'm still on 2.6.34-5.

---

### Post by Cierreics on 2010-07-16
> **The Flying Penguin said:**
> Hmm. I'm getting this back:
```
linux is already the newest version.
linux-generic is already the newest version.
linux-headers-generic is already the newest version.
linux-image is already the newest version.
linux-image-generic is already the newest version.

```

That is certainly not the case. I know for a fact I'm still on 2.6.34-5.

Try to manually delete guiodic repo from source manager then add it again:

```
sudo add-apt-repository ppa:guido-iodice/guiodiclucid
```

Then if you run update-manager you should get directly update to 2.6.35-7 kernel...hope it works!! :)

---

### Post by The Flying Penguin on 2010-07-17
Hey, I manually removed the guiodic repo and then added it again. Update manager does not show a kernel upgrade and I can't do it via terminal either.

What should I do next? I'd like to upgrade the kernel...

---

### Post by Cierreics on 2010-07-18
> **The Flying Penguin said:**
> Hey, I manually removed the guiodic repo and then added it again. Update manager does not show a kernel upgrade and I can't do it via terminal either.

What should I do next? I'd like to upgrade the kernel...

Ok, I'm officially an IDIOT!! 2.6.35 kernel is NOT in guiodic-lucid repo BUT in guiodic-best-intel repo!! :mad::mad::mad:

```
sudo add-apt-repository ppa:guido-iodice/best-intel
```

Now you will find 2.6.35-8 kernel!!

---

### Post by Meizirkki on 2010-07-18
Hi.

I ordered ASUS UL50VT with the dual graphics card this morning. Thanks for this very informative thread, all the power saving tricks and such. :KS

EDIT: Got it this morning. A fully working Kubuntu took only 40 minutes to set up. Thanks for the tips and tricks :)

---

### Post by Cierreics on 2010-07-20
> **Meizirkki said:**
> Hi.

I ordered ASUS UL50VT with the dual graphics card this morning. Thanks for this very informative thread, all the power saving tricks and such. :KS

EDIT: Got it this morning. A fully working Kubuntu took only 40 minutes to set up. Thanks for the tips and tricks :)

Very good!! :cool::cool::cool:

---

### Post by wconstantine on 2010-07-23
In Windows there's an app that ships with this laptop that can put it into performance mode. It clocks the proc to 1,9 GHz if I'm not wrong. In Linux we only have 1,3 GHz and 800 MHz. Is there any tool for overclocking Intel proc's in Linux? I know the bios won't let us do it. Sadly. 

Also, I'm using the Nvidia card in my Ubuntu installation. The HDMI audio output is not working for me. Changed the options in sound preferences to HDMI output but still nothing. Anyone know something about how to fix this? I'm running kernel 2.6.34-020634-generic.

I'm sorry, if the solutions already exists in this thread. However, I haven't got the time to read through the whole thing and the searches I made proved futile.

---

### Post by Meizirkki on 2010-07-24
> **wconstantine said:**
> In Windows there's an app that ships with this laptop that can put it into performance mode. It clocks the proc to 1,9 GHz if I'm not wrong. In Linux we only have 1,3 GHz and 800 MHz. Is there any tool for overclocking Intel proc's in Linux? I know the bios won't let us do it. Sadly. 

I'm also interested in this, because i want to _underclock_ my 50vt. 2x800MHz in already than enough for my daily basis. I wonder how much power it would save clocking it down to 600MHz...

EDIT: Have you tried to enable the HDMI screen from nvidia-settings manager?

---

### Post by wconstantine on 2010-07-25
> **Meizirkki said:**
> I'm also interested in this, because i want to _underclock_ my 50vt. 2x800MHz in already than enough for my daily basis. I wonder how much power it would save clocking it down to 600MHz...

EDIT: Have you tried to enable the HDMI screen from nvidia-settings manager?

Yeah. I've got the video output to work from nvidia-settings. However, there's no sound options available there from what I saw.

---

### Post by weshallallbefree on 2010-07-25
Hi virtual Ubuntu and Asus friends

Returning to Ubuntu after a few years in a OSX galaxy far far away, found a 449&#8364; UL30 to host the return of the Linux Jedi. No further SW puns ever write I will . 

First challenge good old partition scheme and backing up Win 7 partition. Having no external DVD writer (or intention to ever buy one) I've decided to:

Part I:

[LIST=1]
[*] shrink Win7 partition to minimum, about 40gb via Disk Management in Win 7
[*] boot from USB [http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick](http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick)
[*] create image file of Win 7 partition w Partimage
[*] copy image to FAT32 partition on external 250gb USB drive
[*] copy image back to second partition on Asus harddrive
[*] boot from any USB live linux in order to test recovered, Win7 partition
[/LIST]
Part II:

[LIST=1]
[*]delete Asus 15gb recovery partition
[*] create 10 gb partition for Ubuntu + swap
[*]create extra 10gb partition for any other distro to try
[*]create huge FAT32 partition to hold day to day dox, pix, media, to be shared between Ubuntu and Win 7
[/LIST]
 To summarize goal:
- create image file of Win 7 partition in order to restore at any given time 
- create space for Ubuntu and one other optional distro
- share data between OS on a FAT32 partition (estimated 240gb)

Any comments highly appreciated before execution. Noob re. the image file stuff.

---

### Post by wconstantine on 2010-07-25
> **weshallallbefree said:**
> Hi virtual Ubuntu and Asus friends

Returning to Ubuntu after a few years in a OSX galaxy far far away, found a 449€ UL30 to host the return of the Linux Jedi. No further SW puns ever write I will . 

First challenge good old partition scheme and backing up Win 7 partition. Having no external DVD writer (or intention to ever buy one) I've decided to:

Part I:

[LIST=1]
[*] shrink Win7 partition to minimum, about 40gb via Disk Management in Win 7
[*] boot from USB [http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick](http://www.sysresccd.org/Sysresccd-manual-en_How_to_install_SystemRescueCd_on_an_USB-stick)
[*] create image file of Win 7 partition w Partimage
[*] copy image to FAT32 partition on external 250gb USB drive
[*] copy image back to second partition on Asus harddrive
[*] boot from any USB live linux in order to test recovered, Win7 partition
[/LIST]
Part II:

[LIST=1]
[*]delete Asus 15gb recovery partition
[*] create 10 gb partition for Ubuntu + swap
[*]create extra 10gb partition for any other distro to try
[*]create huge FAT32 partition to hold day to day dox, pix, media, to be shared between Ubuntu and Win 7
[/LIST]
 To summarize goal:
- create image file of Win 7 partition in order to restore at any given time 
- create space for Ubuntu and one other optional distro
- share data between OS on a FAT32 partition (estimated 240gb)

Any comments highly appreciated before execution. Noob re. the image file stuff.

Linux can read/write to NTFS partitions nowadays. Don't know if you need FAT32 partitions hence. :KS

---

### Post by weshallallbefree on 2010-07-26
> **wconstantine said:**
> Linux can read/write to NTFS partitions nowadays. Don't know if you need FAT32 partitions hence. :KS

- good news!

Following this guide for a start [http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

10.04 has landed after some gparted battles, looks really, really good. Great to be back in Ubuntu land.

---

### Post by Cierreics on 2010-07-26
Hi all!! Some news from [Guiodic blog]("http://guiodic.wordpress.com/2010/07/24/aggiornamento-a-vlc-1-1-1-upgrading-vlc-fron-guiodiclucid-ppa/"): if you have installed guiodic repo and VLC media player you have to do this:

"You could have an error upgrading VLC from my ppa today, because a slight difference between oldest and newest packages. To solve it please remove packages named vlc and vlc-nox by synaptic, then reinstall them. If you use  mozilla-plugin-vlc you should to reinstall it too."


Now I'm on 2.6.35-10 kernel, all is working well.

I think I've solved my last little issue, concerning bluetooth: I suspend to ram many times a day, and sometimes bluetooth switch on panel indicator applet stop to work after resume, and I have to press "Fn+F2" keyboard shortcut 2 times to reset wifi and bluetooth to solve it.
So I wrote this little script to force bluetooth reset at suspend-hibernate-resume, I've tested it for a week and it seems to work very well, never had that issue again, so here it is:

```
sudo gedit /etc/pm/sleep.d/asus-bluetooth
```

paste this:

```
#!/bin/bash
case "$1" in
 hibernate|suspend)
  invoke-rc.d --quiet bluetooth stop
  ;;
 thaw|resume)
  invoke-rc.d --quiet bluetooth start
  ;;
 *) exit $NA
  ;;
esac
```

save and close, then:

```
sudo chmod +x /etc/pm/sleep.d/asus-bluetooth
```


Now my UL30A is really 100% functional, very stable and productive, I think it's a perfect Ubuntu laptop!! :KS:KS

As usual, I've updated [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post.

---

### Post by Thryn on 2010-07-26
Hey, I've used most of the tips from page 11 on my UL30A (except the bluetooth and SSD tips, I think), and mostly it's nice and it certainly uses less power. So thanks. :)

But I can't turn on and off the touchpad with F9 any more than I could before (though there is now a setting to turn it off when typing, which is a help). Also, I used to be able to see a display of how bright the screen was when I used F5 or F6 to adjust it (I found a tip elsewhere on the grub settings to activate this feature). Now I can't, but it's not a big deal because the screen still gets brighter or darker.

Still, can anyone help me activate the F9 control? If it helps, I have Lucid 32-bit with 2.6.35-10-generic-pae.

Also, F2 (wireless on/off) seems to respond sluggishly. Or maybe it's just the wireless status applet that has this problem. Is this the case for anyone else?

---

### Post by Cierreics on 2010-07-27
> **Thryn said:**
> Still, can anyone help me activate the F9 control? If it helps, I have Lucid 32-bit with 2.6.35-10-generic-pae.

generic-pae?? I can't find it in synaptics...:confused::confused:

Try to install 2.6.35-10-generic kernel and check again all tips in [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post!!


EDIT:

Obviously I can't find generic-pae kernel because I have a 64bit system...#-o#-o

---

### Post by The Flying Penguin on 2010-07-27
So after running the 2.6.35-8 kernel for a few days and then the 2.6.35-10 kernel for another few days, I have noticed a substantial improvement in suspend/resume and startup/shutdown times. I was getting really frustrated with how long it would take me to resume especially if I had a lot of things open (which I often do). I have probably seen a 75% decrease in these times. I have no hard data to back it up but I swear its made a difference.

One issue though is now I keep getting a notice that not all updates can be installed and I need to run a partial upgrade. I keep doing that but I still get the message. I see I have two packages that are grayed out in the update manager:

Other updates (LP-PPA-guido-iodice-best-intel)
1) Userspace interface to nouveau-specific kernel DRM services -- runtime
2) A free implementation of the OpenGL API -- DRI modules

I've read posts about fixing this. I know I can go in and prevent it from giving me this error and basically ignore these updates but should I? Do I want these upgrades or are they irrelevant to me? I'm running the Nvidia card.

> **Meizirkki said:**
> Hi.
EDIT: Got it this morning. A fully working Kubuntu took only 40 minutes to set up. Thanks for the tips and tricks 

I was amazed at how fast Ubuntu installed on this machine.

> **wconstantine said:**
> Yeah. I've got the video output to work from nvidia-settings. However, there's no sound options available there from what I saw.

Yeah, video works great but audio doesn't work out of the box. Apparently, you have to follow: [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240&redirect=no](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240&redirect=no) to get audio over HDMI working. That appears to be for the desktop version though. I'm not sure if the mobile version is any different. Try it out and let me know. ;) I haven't had the chance to monkey around with it. I've just been plugging in audio separate to my hdtv.

> **weshallallbefree said:**
> 
- share data between OS on a FAT32 partition (estimated 240gb)


> **wconstantine said:**
> Linux can read/write to NTFS partitions nowadays. Don't know if you need FAT32 partitions hence. 

Yeah Ubuntu (and I think most modern Linux distros) read NFTS partitions just fine. No problems whatsoever. It's windows that has a problem reading Linux's file system (the ext file system). I've used this driver: [http://www.fs-driver.org/](http://www.fs-driver.org/) for Windows XP in the past to read ext3. I think it will work with ext4 too. It supports Vista x64 so it may work with 7 x64.

> **Thryn said:**
>  I have Lucid 32-bit with 2.6.35-10-generic-pae.

Any reason you're not using the 64 bit version? Did your version only come with 2GB Ram? This machine is the first I have ever run 64 bit on and I was a little nervous at first because of various compatibility issues I read about but it runs great on this machine! Being able to utilize 4GB ram is wonderful especially since when I run a VM I can give 2GB to Ubuntu and 2gb my guest OS. I'd recommend going x64 if you have the memory to utilize such a feature. Otherwise, stick to 32bit.

> **Thryn said:**
> Also, F2 (wireless on/off) seems to respond sluggishly. Or maybe it's just the wireless status applet that has this problem. Is this the case for anyone else?

No delay whatsoever for me.

> **wconstantine said:**
> In Windows there's an app that ships with  this laptop that can put it into performance mode. It clocks the proc to  1,9 GHz if I'm not wrong. In Linux we only have 1,3 GHz and 800 MHz. Is  there any tool for overclocking Intel proc's in Linux? I know the bios  won't let us do it. Sadly. 

There is an option in my BIOS but I haven't seen anything to make me believe it is actually happening in Ubuntu. In Windows, that AMD app your talking about will OC to 1.73GHz on demand. Very nice for gaming.

I would like to get this working as well for gaming in Ubuntu. It would be nice to be able to select 1.7Ghz in addition to  1.3 and 800.

---

### Post by Cierreics on 2010-07-27
> **The Flying Penguin said:**
> One issue though is now I keep getting a notice that not all updates can be installed and I need to run a partial upgrade. I keep doing that but I still get the message. I see I have two packages that are grayed out in the update manager:

Other updates (LP-PPA-guido-iodice-best-intel)
1) Userspace interface to nouveau-specific kernel DRM services -- runtime
2) A free implementation of the OpenGL API -- DRI modules

I've read posts about fixing this. I know I can go in and prevent it from giving me this error and basically ignore these updates but should I? Do I want these upgrades or are they irrelevant to me? I'm running the Nvidia card.

Have you tried to remove those packages then install them again?

---

### Post by The Flying Penguin on 2010-07-27
> **Cierreics said:**
> Have you tried to remove those packages then install them again?

I just went into Synaptic and manually upgraded the nouveau package. Doing that allowed the update manager to work properly and it upgraded the other package on its own.

I had a complete lapse in memory because I had to do this once before with another package. I should have just remembered to do that instead of waisting bandwidth on a question I already had the answer too. :(

But thank you!

---

### Post by Meizirkki on 2010-07-28
Sound stopped working after the -10 kernel upgrade it seems...

---

### Post by Thryn on 2010-07-29
> **Meizirkki said:**
> Sound stopped working after the -10 kernel upgrade it seems...

It works on mine in Rhythmbox, but Amarok segfaulted when I tried to play an mp3.

Also, I'm having issues with the touchpad now - it freezes up sometimes, and I have to reactivate it with F9. So F9 works for me to turn on the touchpad, but not to turn it off... bizarre. And so far I haven't been able to get my tablet to work, even though I've made it work with previous kernels...

I am seriously tempted to go back to the kernel I was using before (undoing the touchpad-related changes which cause the touchpad to not work at all with that kernel). I'm also considering the recommended move to 64-bit (which sounds like a bit of a pain - have to do a fresh install right?). Honestly I don't need it though - I never seem to use more than 1 gb of RAM at a time on Ubuntu. The bottleneck for me is the integrated graphics, really, although it's not that big of deal because there are still plenty of games I can play.

The reason I didn't use 64-bit off the bat is that the main website recommended against it. I heard there were some issues with it. Of course I picked netbook remix as well and that was a bad idea. I ended up not liking the interface and now use the regular ubuntu one.

I'm going to have to do more research before I jump to 64-bit, but my computer has 4 gb RAM, so no issues there. Might try it out though.

---

### Post by The Flying Penguin on 2010-07-29
> **Meizirkki said:**
> Sound stopped working after the -10 kernel upgrade it seems...

Sorry, I can't help much with this but I would try checking your sound preferences and just double check that the right device is selected for your sound output. I seem to remember this getting changed on my once causing me to lose sound. I can't remember the conditions that led to the change though.

I had no sound issues with the 2.6.35-10 kernel. The 2.6.35-12 kernel is out now. Try updating to that and see if it fixes your sound issue. I installed it yesterday and it's running fine for me so far.

> **Thryn said:**
> 
I never seem to use more than 1 gb of RAM at a time on Ubuntu

Most of the time I don't either but you can never have too much RAM and its always nice to have it available in case you need it. I find it to be very useful when I run a VM though. I allocated 2GB to Ubuntu and 2GB to the guest OS (usually XP). This way I am able to have TONS of things open in both systems without any slowdown.

I feel that the advantages of 64bit outweigh the disadvantages.

I think the reason 64

> **Thryn said:**
> 
The reason I didn't use 64-bit off the bat is that the main website recommended against it. I heard there were some issues with it.

I think one of the reasons it recommends the 32 bit version is because of two reasons:
1) The "average" computer user won't benefit from running 64bit so they may as well avoid potential problems.
2) There are certain compatibility issues that can arise with a 64 bit OS and dealing with them may be too much for a new user of Linux or someone who isn't very computer savvy.

Let me elaborate on the compatibility issues:
 64bit and 32bit use different drivers for hardware. Sometimes 64bit drivers are not available for certain hardware but this shouldn't be much of issue since you won't be installing new hardware inside your laptop. Some 32bit drivers will work with a 64bit OS but it is a "hit and miss" kind of thing.

The Asus Ul series ships with 64bit Win 7. The laptop is pretty much built for 64bit OS. While they had Win7 in mind I can assure you that Linux has all the 64bit drivers you need for this laptop.

It's the same thing with software. 32bit software won't be able to take advantage of 64bit but generally will run just the same. Many versions of software have 64bit versions that is optimized to take advantage of the 64bit architecture. You really won't notice much of a difference though except in things like media editing and processing. Also, some 64bit software isn't quite as well developed as its 32bit counterpart. I haven't had any software or games that wouldn't run because they were designed for 32bit except for a couple codecs 



Quite frankly, you shouldn't have any problems with 64bit on this laptop. It shipped with a 64bit OS. I really don't think you need to do much research, just take take the plunge lol. It takes next to no time to install Ubuntu so just try it out and go back to 32bit if you have problems.

---

### Post by Mr_Troglodyte on 2010-08-01
> **Meizirkki said:**
> Sound stopped working after the -10 kernel upgrade it seems...

I had that problem.  I'm pretty sure it was something else which muted the main audio output when i upgraded.  Try running alsamixer from the command line.  That's the only way i could see the muted channel.

---

### Post by Meizirkki on 2010-08-01
> **Mr_Troglodyte said:**
> I had that problem.  I'm pretty sure it was something else which muted the main audio output when i upgraded.  Try running alsamixer from the command line.  That's the only way i could see the muted channel.

Nothing was muted. Spotify couldn't even start the playback so there clearly was a problem with opening the audio device.

But I'll check if there are new updates, if not I'll just use the -8 kernel which works fine.

---

### Post by Hobbes on 2010-08-02
> **The Flying Penguin said:**
> I just went into Synaptic and manually upgraded the nouveau package. Doing that allowed the update manager to work properly and it upgraded the other package on its own....


So you are running the nouveau driver for the ULX0vt? How is performance? battery life / power drain? 

I switched from nvidia drivers back to intel only because of super slow resume from suspend times mostly.. extra 1-2 hours of battery is nice too, but it glitches and is slow occasionally, not sure if it is a video problem or cpu with meerkat kernel, and I miss vdpau for low cpu drain when watching videos.

---

### Post by wconstantine on 2010-08-02
> **Hobbes said:**
> So you are running the nouveau driver for the ULX0vt? How is performance? battery life / power drain? 

I switched from nvidia drivers back to intel only because of super slow resume from suspend times mostly.. extra 1-2 hours of battery is nice too, but it glitches and is slow occasionally, not sure if it is a video problem or cpu with meerkat kernel, and I miss vdpau for low cpu drain when watching videos.

How fares the integrated when watching 720p flash? Stuttering? Bad framerate?

---

### Post by The Flying Penguin on 2010-08-03
> **Hobbes said:**
> So you are running the nouveau driver for the ULX0vt? How is performance? battery life / power drain? 

I switched from nvidia drivers back to intel only because of super slow resume from suspend times mostly.. extra 1-2 hours of battery is nice too, but it glitches and is slow occasionally, not sure if it is a video problem or cpu with meerkat kernel, and I miss vdpau for low cpu drain when watching videos.


I guest I didn't really realize what nouveau even was. I just looked it up and found that it's the open source nvidia driver. I don't have it installed but for some reason have libdrm-nouveau1. I supposed I could go ahead and remove it?

I'm using the proprietary Nvidia driver, which I'm very pleased with. I get around 4-6 hours battery life. The only thing I dislike is the resume/suspend times. The 2.6.35-10 kernel seemed to improve these times substantially but now with 2.6.35-12 the times seemed to have increased slightly. I wasn't getting any time outs when trying to resume and now I am again.

I can't get by without using the Nvidia driver because I need vdpau since I watch 1080p movies. The whole reason I bought the VT was because I wanted the dedicated graphics. I can live with the slower resume/suspend times and the slight loss in battery life (I carry my charger and a power inverter in my laptop bag at all times anyway).

---

### Post by Hobbes on 2010-08-04
i just tried a youtube 720 video and it seemed to work alright. Haven't really tried enough to be sure though.

Unfortunately i think the last kernel upgrade or maybe one before (-13 or -14) broke the module to disable the nvidia card so now i'm back down to like 3.5-4 hours battery instead of 7-8 because both cards are on all the time :(  If this keeps up i might as well go back to just nvidia on and deal with the slow suspend/resume/etc times but enjoy medium battery life and good video performance...

---

### Post by Thryn on 2010-08-05
I've installed 64-bit, and indeed it works. It's nice to see all of my memory available, and GIMP at least starts up noticeably faster (Yay!). It was a bit harder than on 32-bit to eliminate the screen flicker, but I think I've gotten that ironed out.

I do have a small problem though. When I wake the computer up, it can't reconnect with the wireless network. It's invisible, or whatever you call it - the computer doesn't 'see' it unless I've entered its name and so forth at some point. On 32-bit I've had no problem with it except when I tried Kubuntu (complete failure to detect the network), but on 64-bit it tries and fails repeatedly to reconnect, although it connects fine on startup.

I'm using the standard kernel (2.6.32-24-generic). After my previous experience with 2.6.35-10, I'm loath to try it again.

Perhaps the problem is partly with the network itself, but it works for all the other computers on it (usually) so I don't want to mess with it. Any idea what might be happening?

---

### Post by Meizirkki on 2010-08-05
> **Thryn said:**
> I've installed 64-bit, and indeed it works. It's nice to see all of my memory available, and GIMP at least starts up noticeably faster (Yay!). It was a bit harder than on 32-bit to eliminate the screen flicker, but I think I've gotten that ironed out.

I do have a small problem though. When I wake the computer up, it can't reconnect with the wireless network. It's invisible, or whatever you call it - the computer doesn't 'see' it unless I've entered its name and so forth at some point. On 32-bit I've had no problem with it except when I tried Kubuntu (complete failure to detect the network), but on 64-bit it tries and fails repeatedly to reconnect, although it connects fine on startup.

I'm using the standard kernel (2.6.32-24-generic). After my previous experience with 2.6.35-10, I'm loath to try it again.

Perhaps the problem is partly with the network itself, but it works for all the other computers on it (usually) so I don't want to mess with it. Any idea what might be happening?

Try if Fn+F2 brings it back.

Also, There is no problem in Kubuntu itself, wlan works pefectly for me.. as well as the screen brightness shortcuts and ondemand profile. Out of the box without hacks.

---

### Post by Thryn on 2010-08-05
> **Meizirkki said:**
> Try if Fn+F2 brings it back.

Also, There is no problem in Kubuntu itself, wlan works pefectly for me.. as well as the screen brightness shortcuts and ondemand profile. Out of the box without hacks.

Actually it does. Well, I have to press it twice (turn wireless off then on again), then select the connection, and enter the WEP key again (for some reason)... but otherwise I wouldn't be able to post this.

And I don't know why it doesn't work for me in Kubuntu (32 bit, installed in Ubuntu Netbook) but it doesn't. No problem seeing the visible networks (used by my neighbors) but couldn't see mine for some reason, and I checked several times that I'd entered the right info. We've also had issues with DHCP on this network, and had to assign an IP address manually for one of the computers that use it regularly (a Mac Mini). For what it's worth Lucid Puppy doesn't detect the network properly either.

---

### Post by Cierreics on 2010-08-11
Hi all, It's bad some of you have problems with audio and wifi, I don't know how to help...:(

I had an issue with 2.6.35-14 kernel, touchpad sometimes stop to work after resume from suspend. I've had this same problem some time ago with an earlier kernel, I fixed it adding "i8042.reset" option to grub. Removing this fix seems to solve this issue now:

```
sudo gedit /etc/default/grub
```

look at line 9, remove "i8042.reset":

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor _i8042.reset_"
```

save and close, then:

```
sudo update-grub
```

---

### Post by rdjse on 2010-08-13
After reading in this thread it looks like everyone got their UL30 working great in Ubuntu.

I cant even disable the Nvidia card, I get this error:
```
FATAL: Error inserting nvidia_g210m_acpi (/lib/modules/2.6.32-21-generic/updates/dkms/nvidia-g210m_acpi.ko): Kernel does not have module support 
``` 
(see this thread: [http://ubuntuforums.org/showthread.php?t=1552248](http://ubuntuforums.org/showthread.php?t=1552248) )

And the fan seems to be at full RPM the whole time even if the CPU is in 667MHz. I'm about to give up the Linux dream on it and stick with Windows 7, where I will get more then 3 hours of battery time. :/

I have the UL30JT version btw...

//rdj

---

### Post by Meizirkki on 2010-08-14
Huh! JT version has some neat HW specs :P

I want to clock my CPU down to 667 too :/

You could try installing a better kernel from the repos mentioned in this post [http://ubuntuforums.org/showpost.php?p=9328344&postcount=110](http://ubuntuforums.org/showpost.php?p=9328344&postcount=110)

---

### Post by rdjse on 2010-08-14
> **Meizirkki said:**
> Huh! JT version has some neat HW specs :P

I want to clock my CPU down to 667 too :/

You could try installing a better kernel from the repos mentioned in this post [http://ubuntuforums.org/showpost.php?p=9328344&postcount=110](http://ubuntuforums.org/showpost.php?p=9328344&postcount=110)

Yeah it's very neat, it's both fast and has a good battery time (atleast in Windows for now)

I'm going to try the kernel stuff in your link as soon as I boot back to Ubuntu. Thanks!

---

### Post by rdjse on 2010-08-14
> **Meizirkki said:**
> Huh! JT version has some neat HW specs :P

I want to clock my CPU down to 667 too :/

You could try installing a better kernel from the repos mentioned in this post [http://ubuntuforums.org/showpost.php?p=9328344&postcount=110](http://ubuntuforums.org/showpost.php?p=9328344&postcount=110)

Okey I tried with the example from the thread you linked but I wasn't able to install the kernel because of dependency problems. 
```

The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.35-15-generic but it is not installable
  linux-image-generic: Depends: linux-image-2.6.35-15-generic but it is not installable
E: Broken packages

```

When I try to install the nvidia_g210m_acpi module with one of the Ubuntu kernels everything works fine except for loading the module, I get this error message:
```

rdj@rdjbook:~$ sudo modprobe nvidia_g210m_acpi
FATAL: Error inserting nvidia_g210m_acpi (/lib/modules/2.6.32-24vegeneric/extra/nvidia_g210m_acpi.ko): Kernel does not have module support

```

And the third thing I tried was to download a kernel from the mainline reps and installed it, but when I try to install the nvidia_g210m_acpi module with that it just tells me it cannot find the kernel source to compile the module, but I have both the kernel, kernel source and kernel-headers installed and located in /usr/src. 
```

Loading tarball for module: nvidia-g210m-acpi / version: 0.1.0

Loading /usr/src/nvidia-g210m-acpi-0.1.0...
Creating /var/lib/dkms/nvidia-g210m-acpi/0.1.0/source symlink...

DKMS: ldtarball Completed.
Installing prebuilt kernel module binaries (if any)

Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

```

So right now I'm thinking about removing Ubuntu and go for Win7 for a year or two. I have no idea what to try next. :( Too bad tho, I really wanted a nice Linux laptop. :/

---

### Post by angel12 on 2010-08-14
so it looks like the new kernel 2.6.35-15-generic is uninstallable at the moment, just tried installing it and i get this:

```
The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.35-15-generic but it is not installable
  linux-image-generic: Depends: linux-image-2.6.35-15-generic but it is not installable
E: Broken packages
```

could be that the package is not available at the moment i guess.

Edit: i just got everything working fine with the 2.6.35-14 kernel, here is the command you need to install it if you get the error above with the 2.6.35-15 kernel install:

```
sudo apt-get install linux-image-2.6.35-14-generic
```

---

### Post by rdjse on 2010-08-15
> **angel12 said:**
> so it looks like the new kernel 2.6.35-15-generic is uninstallable at the moment, just tried installing it and i get this:

```
The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.35-15-generic but it is not installable
  linux-image-generic: Depends: linux-image-2.6.35-15-generic but it is not installable
E: Broken packages
```

could be that the package is not available at the moment i guess.

Edit: i just got everything working fine with the 2.6.35-14 kernel, here is the command you need to install it if you get the error above with the 2.6.35-15 kernel install:

```
sudo apt-get install linux-image-2.6.35-14-generic
```

Looks like I'm screwed until that works again. But even then I doubt I will solve this problem... :(

---

### Post by avilella on 2010-08-15
Is the acpi_call module working?

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

---

### Post by rdjse on 2010-08-15
> **avilella said:**
> Is the acpi_call module working?

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

WOOT! I think that worked! I was able to load the module, run the script and the output told me it worked. And Powertop showed a big drop in power usage. Thanks!! :D

---

### Post by Mr_Troglodyte on 2010-08-17
> **rdjse said:**
> WOOT! I think that worked! I was able to load the module, run the script and the output told me it worked. And Powertop showed a big drop in power usage. Thanks!! :D

Does that mean you can switch between the intel and nvidia card?  I really want to be able to use the nvidia card without slowing my hard drive down.

---

### Post by The Flying Penguin on 2010-08-20
> **Meizirkki said:**
> Huh! JT version has some neat HW specs :P



Ah, yes it does. I knew it was coming out about three months ago when I bought my VT but I needed a new laptop right away. Now, I am so tempted to put my VT up for sale and get a JT. It's only a hundredish more than I paid for my VT and packs a lot more power. In my opinion the G210 in the VT packs quite a punch for an ultraportable in this price range but the G230 with 1GB DDR3?! :D

> **Mr_Troglodyte said:**
> Does that mean you can switch between the  intel and nvidia card?  I really want to be able to use the nvidia card  without slowing my hard drive down.

I think that is just so you can disable the nvidia card to save power. Am I correct?

You still have to run in compatible mode to use the nvidia card right?

Someone want to clear this up?

---

### Post by Meizirkki on 2010-08-21
It seems like it's possible to switch between the cards now... Xorg restart still needed. And no idea if it works with closed source nVidia drivers.

---

### Post by The Flying Penguin on 2010-08-21
> **Meizirkki said:**
> It seems like it's possible to switch between the cards now... Xorg restart still needed. And no idea if it works with closed source nVidia drivers.

So does this mean you can run in enhanced mode instead of compatible even with the nvidia card on?

How does the open source driver work with the G210? Does vdpau work and is 3d support anywhere near the level it is with the proprietary driver?

---

### Post by Meizirkki on 2010-08-22
> **The Flying Penguin said:**
> So does this mean you can run in enhanced mode instead of compatible even with the nvidia card on?

How does the open source driver work with the G210? Does vdpau work and is 3d support anywhere near the level it is with the proprietary driver?


I'm interested in the enchanged mode too.

Open Source nVidia driver? I have never heard of that.. we can use nVidia card with some generic standard drivers but there will be no 3D acceleration at all. vdpau might work, it isn't dependent on the drivers, is it?

EDIT: [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/) no 3D acceleration yet it seems :/

---

### Post by bvgd on 2010-08-22
I have used the post #110 for my UL30A and Ubuntu 10.04 (both i386 and AMD64). It's an excellent job, Cierreics is GREAT!
I have still a problem with a touch-pad on/off using Fn + F9. It worked for me not until I have used two tips shown [**here**]("https://bugs.launchpad.net/ubuntu/+bug/41828") and [**here**]("http://lug32.org.ru/mediawiki/index.php/%D0%A2%D0%B0%D1%87%D0%BF%D0%B0%D0%B4_%D0%B8_%D0%BC%D1%8B%D1%88%D0%BA%D0%B0").
Additionally to the file /etc/acpi/asus-touchpad.sh (shown by Cierreics) I have corrected the file 
/etc/acpi/events/asus-touchpad:
```
sudo gedit /etc/acpi/events/asus-touchpad
```
delete everything and paste this:
```
# /etc/acpi/events/asus-touchpad
# This is called when the user presses the touchpad button and calls
# /etc/acpi/asus-touchpad.sh for further processing.
event=hotkey ATKD 0000006b
action=/etc/acpi/asus-touchpad.sh
```
save and close.
Now I can really turn the touch-pad on and off, but... there is an another problem! If I try to turn this thing OFF and use a keyboard, it will be automatically turned ON again. :( 
Any ideas?

---

### Post by Cierreics on 2010-08-23
> **bvgd said:**
> I have used the post #110 for my UL30A and Ubuntu 10.04 (both i386 and AMD64). It's an excellent job, Cierreics is GREAT!


:rolleyes::rolleyes:

> I have corrected the file 
/etc/acpi/events/asus-touchpad:
.....
Now I can really turn the touch-pad on and off, but... there is an another problem! If I try to turn this thing OFF and use a keyboard, it will be automatically turned ON again. :( 
Any ideas?

I didnt need to modify /etc/acpi/events/asus-touchpad file, but, oh my, it's true!! Touchpad turns on every time you use a keyboard, even an external one.....I haven't disable touchpad for a while, one month ago it worked, now, maybe due to a kernel upgrade, it's completely useless!! ](*,)](*,)

I will investigate...:-k

---

### Post by bvgd on 2010-08-23
> **Cierreics said:**
> :rolleyes::rolleyes:



I didnt need to modify /etc/acpi/events/asus-touchpad file, but, oh my, it's true!! Touchpad turns on every time you use a keyboard, even an external one.....I haven't disable touchpad for a while, one month ago it worked, now, maybe due to a kernel upgrade, it's completely useless!! ](*,)](*,)

I will investigate...:-k

The ppa:guido-iodice/best-intel repository gives 2.6.35-17 kernel version now. It seems me to work really good. 
The file /etc/acpi/events/asus-touchpad is from the base lucid lynx, is't true? And this file in original version contains:

```
event=hotkey (ATKD|HOTK) (0000006[ab]|00000037)
action=/etc/acpi/asus-touchpad.sh
```

Means this that an event Fn + F9 with a code 0x6b wil be recognized and processed using this code?

---

### Post by wconstantine on 2010-08-24
2.6.35-14-generic broke the multi-touch.

---

### Post by Cierreics on 2010-08-25
> **bvgd said:**
> The ppa:guido-iodice/best-intel repository gives 2.6.35-17 kernel version now. It seems me to work really good. 
The file /etc/acpi/events/asus-touchpad is from the base lucid lynx, is't true? And this file in original version contains:

```
event=hotkey (ATKD|HOTK) (0000006[ab]|00000037)
action=/etc/acpi/asus-touchpad.sh
```

Means this that an event Fn + F9 with a code 0x6b wil be recognized and processed using this code?

Yes....are you good in scripting? I'm trying to write a new script wich use gconftool to switch true-false the touchpad_enabled parameter, it works if I launch it in a terminal, but I can't make it work with Fn+F9...is anyone good at this? :-k:-k

---

### Post by Cierreics on 2010-08-25
> **wconstantine said:**
> 2.6.35-14-generic broke the multi-touch.

Are you talking about touchpad? 

Today 2.6.35-19 kernel is out, try it! ;)

---

### Post by ubuntoide on 2010-09-05
just tried the acpi_call method and it works great. I added the two commands to the rc.local so it runs every boot.

**Resuming from suspend/hibernate still powers up the Nvidia card anyway.. is there a way to run the script automatically just after resume**?

---

### Post by Cierreics on 2010-09-05
> **ubuntoide said:**
> just tried the acpi_call method and it works great. I added the two commands to the rc.local so it runs every boot.

**Resuming from suspend/hibernate still powers up the Nvidia card anyway.. is there a way to run the script automatically just after resume**?

Yes, you can write a bash script like this:

```
#!/bin/bash

case $1 in
    resume)
        command 1
        command 2
        ;;
esac
```

and put it in /etc/pm/sleep.d

;)

---

### Post by ubuntoide on 2010-09-07
> #!/bin/bash

case $1 in
    resume)
        insmod /opt/acpi_call/acpi_call.ko
	sh /opt/acpi_call/test_off.sh
        ;;
esac

tried this but it doesn't work.. I named the file nvidia_kill and put it in /etc/pm/sleep.d

**EDIT: I messed with permissions, now it runs great! Thank you!**

---

### Post by Cierreics on 2010-09-07
> **ubuntoide said:**
> tried this but it doesn't work.. I named the file nvidia_kill and put it in /etc/pm/sleep.d

**EDIT: I messed with permissions, now it runs great! Thank you!**

Does it run ok with hibernation?

Can you write a little guide for nvidia switchoff so I can add it in [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post? :KS

---

### Post by rdjse on 2010-09-12
Hello again!

It's been a while since I posted to this thread but I just have to
tell you all that I got Suspend working on my Asus UL30JT now. I came
across this thread on the Ubuntuforums:
[http://www.ge.ubuntuforums.org/showthread.php?t=1569380](http://www.ge.ubuntuforums.org/showthread.php?t=1569380)
I then followed the steps described under "Fix Suspend". After
creating that script suspend works as it should! I hope that will
solve your problems too!

//rdj

---

### Post by ubuntoide on 2010-09-12
> **Cierreics said:**
> Does it run ok with hibernation?

Can you write a little guide for nvidia switchoff so I can add it in [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post? :KS

Hibernate doesn't work, as stated in the link posted above, you can can update your guide with the steps from that link anyway

---

### Post by Cierreics on 2010-09-14
> **ubuntoide said:**
> Hibernate doesn't work, as stated in the link posted above, you can can update your guide with the steps from that link anyway

Hibernation doesn't work at all with nvidia card?

---

### Post by Hott Dogg on 2010-09-15
Hi guys! I need your help
I after linux image 2.6.35-x installed, I have two-finger tap replaced with three-finger tap on touchpad. So two fingers are now for right click and three are for middle click. Any solution to return them back?

---

### Post by Cierreics on 2010-09-15
> **Hott Dogg said:**
> Hi guys! I need your help
I after linux image 2.6.35-x installed, I have two-finger tap replaced with three-finger tap on touchpad. So two fingers are now for right click and three are for middle click. Any solution to return them back?

Yes, look at TOUCHPAD section on [#110]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") post!! :KS

---

### Post by The Flying Penguin on 2010-09-19
I have had no luck getting audio over HDMI working. I have a G210 based card in my HTPC and I managed to get sound to work. I had to follow a few different guides and take bits and pieces from each though. No one guide worked.

Following the same guides on the VT seems to kill the sound completely. I just tried to recompile Alsa 1.0.23 because that's what I had to do on my HTPC. Now I have no sound at all. No sound device shows up. I'm going to install the Meerkat beta today so I'm not worried about troubleshooting.

Has anyone actually been able to get audio via HDMI working with the Nvidia card?

I really think its just a matter of unmuting the correct S/PDIF (there several shown in alsamixer if my memory serves correct) and entering the correct values for /etc/asound.conf and /etc/modprobe.d/options.conf.

Here is what I entered on my HTPC running Lucid x86 with the N210-MD512H and 260.19.04 driver:

/etc/asound.conf
```

pcm.!default hdmi:NVidia
pcm:iec958 hdmi:NVidia
```/etc/modprobe.d/options.conf
```
options snd-hda-intel enable_msi=0 probe_mask0xfff2
```These settings result in no sound at all on my VT.

---

### Post by Cierreics on 2010-09-19
Finally I get some time to make a working script for disable touchpad button (Fn+F9), after some searching it was very simple:

```
sudo gedit /etc/acpi/asus-touchpad.sh
```

delete everything and paste this:

```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi
```

save and close.

Now it works again!! :guitar:

---

### Post by cb_rex on 2010-09-30
I'm a new member of the ubuntu ul30 club, my model is the UL30A-QX328V with built in mobile broadband SIM card slot. 

Thanks to everyone who has contributed to this thread to help improve support for the ul30, especially Cierreics for the excellent [walkthrough of everything you need to do to get ubuntu working smoothly on the asus ul30]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110").

I've so far only had some minor issues. After enabling the "disable touchpad when typing" option I noticed that it sometimes disables when I'm not typing, preventing the touchpad working until I depress and release any key. This tends to happen after I have not been using the touchpad for a short while, if I'm reading something or watching a video etc. Has anyone else experienced this? I'm thinking this could be due to the Elantech driver being fairly new.

---

### Post by Cierreics on 2010-10-01
> **cb_rex said:**
> Has anyone else experienced this? I'm thinking this could be due to the Elantech driver being fairly new.

No, but I have another touchpad issue: sometimes, when I leave the laptop with closed lid for a long time (not suspended, only closed lid), when I open the lid again touchpad goes crazy, I can't point anything, it goes at random directions when I try to move the pointer.
I have to simply disable and enable it again with Fn+F9 and it returns normal.

---

### Post by cb_rex on 2010-10-03
> **Cierreics said:**
> No, but I have another touchpad issue: sometimes, when I leave the laptop with closed lid for a long time (not suspended, only closed lid), when I open the lid again touchpad goes crazy, I can't point anything, it goes at random directions when I try to move the pointer.
I have to simply disable and enable it again with Fn+F9 and it returns normal.

I've not had that happen on me yet.

I found that hibernation isn't very useful as it takes a lot longer than shutting down and restarting, and I just have the standard HDD. I usually just close the lid when I'm not using it for a while, the battery hardly goes down at all. The 2 finger scroll is a bit tricky in a spreadsheet but overall I'm loving ubuntu on this laptop. The Win7 partition will definitely be getting formatted when 10.10 is released.

---

### Post by Cierreics on 2010-10-06
Hi all, I've got some problems with wi-fi since 2.6.35-22 kernel, so I've tried to install backports modules last week and all issues are gone, I suggest it:

```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

---

### Post by asphy on 2010-10-07
> **cb_rex said:**
> I'm a new member of the ubuntu ul30 club, my model is the UL30A-QX328V with built in mobile broadband SIM card slot. 


I've got the exact same model, supplied from o2. Just out of interest, does your mobile broadband work? I can see the modem just fine, and even talk to it to some limited extent but I can't seem to turn the radio on at all. I've read through all of the Huawei documentation (according to what it's telling me, it's a Huawei EM770) and noticed that it has two radio kills, a soft kill that you can disable by setting full card functionality (AT+CFUN=1) and a hard kill that I can't seem to disable anywhere. I have rfkills for bluetooth and wlan just not for 3g. Calling AT+CFUN=1 returns ERROR and looking at the output of AT^RFSWITCH? shows me its because of the hard kill.

Basically, I've a modem that I can talk to but cant do anything with as its radio is forcefully off, any ideas?

*edit 11/10/10*

I've figured out this issue, its related to two missing rfswitches that are not implemented in the asus-laptop platform driver. I've worked with the guys over at acpi4asus to get these implemented, you can find a patch for the issue here : 

[http://dev.iksaif.net/issues/108](http://dev.iksaif.net/issues/108)

---

### Post by cb_rex on 2010-10-11
> **asphy said:**
> I've got the exact same model, supplied from o2. Just out of interest, does your mobile broadband work? I can see the modem just fine, and even talk to it to some limited extent but I can't seem to turn the radio on at all. I've read through all of the Huawei documentation (according to what it's telling me, it's a Huawei EM770) and noticed that it has two radio kills, a soft kill that you can disable by setting full card functionality (AT+CFUN=1) and a hard kill that I can't seem to disable anywhere. I have rfkills for bluetooth and wlan just not for 3g. Calling AT+CFUN=1 returns ERROR and looking at the output of AT^RFSWITCH? shows me its because of the hard kill.

Basically, I've a modem that I can talk to but cant do anything with as its radio is forcefully off, any ideas?

*edit 11/10/10*

I've figured out this issue, its related to two missing rfswitches that are not implemented in the asus-laptop platform driver. I've worked with the guys over at acpi4asus to get these implemented, you can find a patch for the issue here : 

[http://dev.iksaif.net/issues/108](http://dev.iksaif.net/issues/108)

I bought mine cheap off ebay without the mobile contact and SIM so haven't tried it. However when a phone company gets around to offering good value pay as you go mobile broadband SIM cards then I'll deffinatly start using it. Nice one for looking into it and getting it working!

Out of interest seeing as you have exaclty the same model as me, do you get issues with your touchpad disabling when your not typing and only coming alive after pressing a key, as described earlier?

---

### Post by asphy on 2010-10-11
> **cb_rex said:**
> 
Out of interest seeing as you have exaclty the same model as me, do you get issues with your touchpad disabling when your not typing and only coming alive after pressing a key, as described earlier?

As a matter of fact, I've just had to hit a key in order to be able to move the mouse to the "quote" key! What seems like exactly the same issue as you're having. I've not had much of a chance to look into it just yet but i'll agree it's really very irritating.

I'm guessing it could be related to these issues in my kernel log:

[11726.163529] psmouse.c: Touchpad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[11731.430445] psmouse.c: resync failed, issuing reconnect request

I'll have a look into it when I'm finished up with work :)

Just so everyone's aware, according to the guys over at acpi4asus, the fix for wimax and wwan through asus-laptop is being pushed into linux 2.6.37.

*edit*

Possibly setting i8042.nomux=1 as a kernel parameter is listed as a possible fix for this issue. I've got some long running tasks going right now so cant restart to test but i'll try later.

*another edit*

Okay setting i8042.nomux borked my system.. however, looks like a new 10.10 kernel was pushed out recently. I haven't had the freezing mouse problem since touch wood...

*yet another edit*

Okay, the new kernel didn't help either but...

I've tried a few things here, I upgraded the bios on the ul30a to Ver 212 which helped, then I decreased the value of "Asus Easy Overclock" in the bios from its default 3% to 0%. This has dramatically reduced the mouse freezing problem.. I would say eliminated it but I've only been testing for a couple of hours, still I've not seen it happen again so far.

---

### Post by pyjeon on 2010-10-12
I have a pretty new Ul30a and it is running 10.04. I can't get my integrated microphone to work. In sound preferences, there is no device to select in the "input" tab. It seems like most people seem to have an out-of-the-box working mic, and I don't know why mine is different, but I'd greatly appreciate any advice on how to go about fixing this problem.

This forum has been tremendously helpful to me as a computer terminal noob, so much that I have not had to register to ask a question for years, but now I'm at a loss.

---

### Post by asphy on 2010-10-13
> **pyjeon said:**
> I have a pretty new Ul30a and it is running 10.04. I can't get my integrated microphone to work. In sound preferences, there is no device to select in the "input" tab. It seems like most people seem to have an out-of-the-box working mic, and I don't know why mine is different, but I'd greatly appreciate any advice on how to go about fixing this problem.

Sounds like your soundcard might be set to output and not full duplex. In sound preferences, under the Hardware tab, select "Internal Audio" (or whatever the name of your sound devices is, mines that) and make sure it's profile is set to "Analogue Stereo Duplex" (also what mine's currently set to). The see if you have anything under the Input tab.

--asphy

---

### Post by pyjeon on 2010-10-13
> **asphy said:**
> Sounds like your soundcard might be set to output and not full duplex. In sound preferences, under the Hardware tab, select "Internal Audio" (or whatever the name of your sound devices is, mines that) and make sure it's profile is set to "Analogue Stereo Duplex" (also what mine's currently set to). The see if you have anything under the Input tab.

--asphy

YES thank you thank you thank you so much. ubuntuforums wins again. No more booting into windows to video chat =D.

---

### Post by asphy on 2010-10-13
> **pyjeon said:**
> YES thank you thank you thank you so much. ubuntuforums wins again. No more booting into windows to video chat =D.

Glad you got it working man :) enjoy!

---

### Post by MathMcC on 2010-10-14
Hey

This is exactly what I needed. I've followed your instructions exactly but no joy. Any idea what I might be doing wrong?

Math

> **Cierreics said:**
> Finally I get some time to make a working script for disable touchpad button (Fn+F9), after some searching it was very simple:

```
sudo gedit /etc/acpi/asus-touchpad.sh
```delete everything and paste this:

```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi
```save and close.

Now it works again!! :guitar:

---

### Post by Cierreics on 2010-10-14
> **MathMcC said:**
> Hey

This is exactly what I needed. I've followed your instructions exactly but no joy. Any idea what I might be doing wrong?


Is your asus-touchpad.sh file executable? Have you enabled the elantech driver?

---

### Post by MathMcC on 2010-10-15
> **Cierreics said:**
> Is your asus-touchpad.sh file executable? Have you enabled the elantech driver?

I'm not sure what I've done exactly but now the touchpad doesn't work at all. I normally use a mouse so it doesn't matter too much. I'll look into your suggestions soon though.

---

### Post by ekarasik on 2010-10-15
First of all, thanks a lot Cierreics for your solutions.

10.10 broke your touchpad script.

To fix it, 
```

sudo gedit  /usr/share/acpi-support/power-funcs

```change 
```

    if [ x"$user" != x"" ]; then
               userhome=`getent passwd $user | cut -d: -f6`
            export XAUTHORITY=$userhome/.Xauthority
    else
        export XAUTHORITY=""
    fi

```to
```

export XAUTHORITY=`ps a | grep -v grep | grep X | sed -n 's/.*-auth \(.*\)/\1/p' | cut -f 1 -d ' '`
```

(credits to [https://launchpad.net/~frederic-danis](https://launchpad.net/~frederic-danis))

---

### Post by Cierreics on 2010-10-15
> **ekarasik said:**
> First of all, thanks a lot Cierreics for your solutions.

10.10 broke your touchpad script.


Tnx for the fix :KS

MathMcC, are you on Ubuntu Maverick? Does it fix your problem?

I'm still on Lucid, now I don't have time to upgrade, I'll do it in a couple of weeks. Then I will fix all the scripts for Maverick!! :KS

---

### Post by kummy on 2010-10-19
> **asphy said:**
> Sounds like your soundcard might be set to output and not full duplex. In sound preferences, under the Hardware tab, select "Internal Audio" (or whatever the name of your sound devices is, mines that) and make sure it's profile is set to "Analogue Stereo Duplex" (also what mine's currently set to). The see if you have anything under the Input tab.

--asphy

i use Ubuntu 10.10, and i've set the profile to "Analogue Stereo DUplex". But my voice is so quite.. the input tab, the input volume bar is set to 100%, but the input level of my voice is only 1 bar or even 2-3 bar when i set the input volume to max. how can resolve this?

---

### Post by asphy on 2010-10-20
> **kummy said:**
> i use Ubuntu 10.10, and i've set the profile to "Analogue Stereo DUplex". But my voice is so quite.. the input tab, the input volume bar is set to 100%, but the input level of my voice is only 1 bar or even 2-3 bar when i set the input volume to max. how can resolve this?

I can see from alsamixer that the UL30A has two "mic boost" parameters. I'm not quite sure how these can be set in a gui environment but if you're happy using the terminal to some limited extent then you can try the following. (I apologise in advance if this seems a little patronising but I'm not sure of how well acquainted you are with linux so I'll keep it basic :)

Open the terminal (Applications > Accessories > Terminal)

Run alsamixer by typing 'alsamixer' at the prompt (without the quotes obviously), this will present you with a friendly(ish) interface to your alsa mixer settings. If the program doesn't run you may have to install the alsa-utils package first.

Use the arrow keys to scroll right to "IntMic Boost" then use the up and down keys to increase / decrease the boost level by 1/3 each time.

Check your record levels (you might now find they're too high, adjust the input level in Sound Preferences to compensate) to see if they have improved at all. They should, mine did. Experiment to find a nice compromise between mic boost and input level that gives you good levels with the lest background noise.

Quit alsamixer by hitting the escape key.

You should now save your mixer settings so they can be restored when you boot up next. In the same terminal you want to type 'sudo alsactl store 0' (again, without the quotes) and enter your password when requested. What this does is instruct alsactl (as the superuser with sudo) to store the settings for soundcard number 0.

That should sort out your record levels :)

Hope that helps!

--asphy

*edit*

Testing this on mine a little, I find its really hard to get a sweet spot in terms of background noise, the internal mic is REALLY noisy. I might compare it with record levels in windows at some point.

On the flip side, recording line level sources from the mic plug (with no boost) actually sounds quite good for a small laptop.

---

### Post by kummy on 2010-10-20
> **asphy said:**
> I can see from alsamixer that the UL30A has two "mic boost" parameters. I'm not quite sure how these can be set in a gui environment but if you're happy using the terminal to some limited extent then you can try the following. (I apologise in advance if this seems a little patronising but I'm not sure of how well acquainted you are with linux so I'll keep it basic :)

Open the terminal (Applications > Accessories > Terminal)

Run alsamixer by typing 'alsamixer' at the prompt (without the quotes obviously), this will present you with a friendly(ish) interface to your alsa mixer settings. If the program doesn't run you may have to install the alsa-utils package first.

Use the arrow keys to scroll right to "IntMic Boost" then use the up and down keys to increase / decrease the boost level by 1/3 each time.

Check your record levels (you might now find they're too high, adjust the input level in Sound Preferences to compensate) to see if they have improved at all. They should, mine did. Experiment to find a nice compromise between mic boost and input level that gives you good levels with the lest background noise.

Quit alsamixer by hitting the escape key.

You should now save your mixer settings so they can be restored when you boot up next. In the same terminal you want to type 'sudo alsactl store 0' (again, without the quotes) and enter your password when requested. What this does is instruct alsactl (as the superuser with sudo) to store the settings for soundcard number 0.

That should sort out your record levels :)

Hope that helps!

--asphy

*edit*

Testing this on mine a little, I find its really hard to get a sweet spot in terms of background noise, the internal mic is REALLY noisy. I might compare it with record levels in windows at some point.

On the flip side, recording line level sources from the mic plug (with no boost) actually sounds quite good for a small laptop.

Thanks a lot.. i use ALSA Mixer, and i use intMic Boost.. it's acceptable.. but yeaahh.. quite noisy..but it's better than before.. thanks for your help.. ;):popcorn:

---

### Post by asphy on 2010-10-20
> **kummy said:**
> Thanks a lot.. i use ALSA Mixer, and i use intMic Boost.. it's acceptable.. but yeaahh.. quite noisy..but it's better than before.. thanks for your help.. ;):popcorn:

Glad it's working better for you, if I find out anything more regarding the noise level I'll update my earlier post (keeps everything in one place then should someone else have the same problem :) )

It brings up an interesting point though, the Sound Preferences panel could really do with an "Advanced" tab for things just like this. I can see it's trying to emulate the OSX style interface which is great, I think OSX does it very well, a LOT better than Windows anyway. However, Apple designed that thing knowing full well it'll only ever have to support a limited set of sound hardware. It clearly wasn't designed to manage the intricate setup of hundreds, if not thousands, of different models!

---

### Post by MathMcC on 2010-10-21
> **Cierreics said:**
> Tnx for the fix :KS

MathMcC, are you on Ubuntu Maverick? Does it fix your problem?

I'm still on Lucid, now I don't have time to upgrade, I'll do it in a couple of weeks. Then I will fix all the scripts for Maverick!! :KS

Nope still on Lucid.

---

### Post by MathMcC on 2010-10-21
Just to confirm I've checked and double checked I've done all of the following and still no touch pad unfortunately.

> **Cierreics said:**
> 

TOUCHPAD
*********

```
sudo gedit /etc/modprobe.d/psmouse.conf
```paste this:

```
options psmouse force_elantech=1
```save and close, then:

```
sudo add-apt-repository ppa:yurivkhan/proposed
```then:

```
sudo apt-get update && sudo apt-get -y upgrade
```This  will enable our elantech touchpad for synaptic driver and install a  patched gnome-settings-daemon we need.

*******

To get working disable touchpad (Fn+F9) button:

```
sudo gedit /etc/acpi/asus-touchpad.sh
```delete everything and paste this:

```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi
```save and close.

*******

Now we have to add an option to grub to solve touchpad problems after  suspension (DON'T APPLY THIS IF YOU HAVE 2.6.35-14 OR SUCCESSIVE KERNEL,  IT'S ONLY NEEDED WITH EARLIER KERNELS):

```
sudo gedit /etc/default/grub
```look at line 9, change to this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor i8042.reset"
```save and close, then:

```
sudo update-grub
```*******






I have kernel version 2.6.32-25 so I presume I was ok doing the final change to grub.

---

### Post by The Flying Penguin on 2010-10-22
> **Cierreics said:**
> Hi all, I've got some problems with wi-fi since 2.6.35-22 kernel, so I've tried to install backports modules last week and all issues are gone, I suggest it:

```
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

I already have it installed but I'm having problems on 10.10. I'm on a hotel wifi and 80% of the time I click a link the loading indicator starts to move and then just stops. I'll click the link a few more times and the page still won't load. If I wait a minute and then click the link, the page loads! I'll be good for another page load or so and the same thing happens again. I was having a similar problem on my home wifi but my DSL has been going on the fritz in the evening the last couple of weeks. If I remember correct, it was working fine during the day when my DSL works correctly.
 

 I plugged my Touch Pro 2 into my laptop to use it as a WiFi card and have had no problems running off the same hotel WiFi for over three hours now. I tried connecting my laptop's internal wifi card and immediately have the same problem.
 

 Any idea what's going on here?
 

 Other than that, 10.10 and runs great. I have noticed a considerable increase in suspend/resume times despite running in compatible mode. Most of the time I don't even notice the slowdown. Everything just seems to be a lot more snappy.

---

### Post by Cierreics on 2010-10-22
> **MathMcC said:**
> Just to confirm I've checked and double checked I've done all of the following and still no touch pad unfortunately.



I have kernel version 2.6.32-25 so I presume I was ok doing the final change to grub.

Here is your problem!! Elantech driver is in 2.6.35 kernel!! You have to install it, follow my guide!! :)

---

### Post by Cierreics on 2010-10-22
> **The Flying Penguin said:**
> I already have it installed but I'm having problems on 10.10. I'm on a hotel wifi and 80% of the time I click a link the loading indicator starts to move and then just stops. I'll click the link a few more times and the page still won't load. If I wait a minute and then click the link, the page loads! I'll be good for another page load or so and the same thing happens again. I was having a similar problem on my home wifi but my DSL has been going on the fritz in the evening the last couple of weeks. If I remember correct, it was working fine during the day when my DSL works correctly.
 

 I plugged my Touch Pro 2 into my laptop to use it as a WiFi card and have had no problems running off the same hotel WiFi for over three hours now. I tried connecting my laptop's internal wifi card and immediately have the same problem.
 

 Any idea what's going on here?
 

Try to remove backports modules, I had problems too with latest 2.6.35-22 kernel, now it works fine.

---

### Post by The Flying Penguin on 2010-10-23
> **Cierreics said:**
> Try to remove backports modules, I had problems too with latest 2.6.35-22 kernel, now it works fine.

I removed the backport modules but I'm still having the same problem.

Any ideas?

---

### Post by MathMcC on 2010-10-23
> **Cierreics said:**
> Here is your problem!! Elantech driver is in 2.6.35 kernel!! You have to install it, follow my guide!! :)

Are you referring to this section of your guide?

> **Cierreics said:**
> 

TOUCHPAD
*********

```
sudo gedit /etc/modprobe.d/psmouse.conf
```paste this:

```
options psmouse force_elantech=1
```save and close, then:

```
sudo add-apt-repository ppa:yurivkhan/proposed
```then:

```
sudo apt-get update && sudo apt-get -y upgrade
```This   will enable our elantech touchpad for synaptic driver and install a   patched gnome-settings-daemon we need.


Because I've done all this and its the only reference I can find to Elantech...

---

### Post by Cierreics on 2010-10-24
> **MathMcC said:**
> Are you referring to this section of your guide?



Because I've done all this and its the only reference I can find to Elantech...

I refer to the first section of my guide:

You have to at least add guiodic "best-intel" repository:

```
sudo add-apt-repository ppa:guido-iodice/best-intel
```

then:

```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y install linux linux-generic linux-headers-generic linux-image linux-image-generic
```

---

### Post by MathMcC on 2010-10-25
Sorted! Thank you so much :)

> **Cierreics said:**
> I refer to the first section of my guide:

You have to at least add guiodic "best-intel" repository:

```
sudo add-apt-repository ppa:guido-iodice/best-intel
```then:

```
sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y install linux linux-generic linux-headers-generic linux-image linux-image-generic
```

---

### Post by Berto on 2010-10-26
The guides here are great.  I had some issues with 10.04, so I went to 10.10 on my UL30A - I do NOT recommend you do this until there are better guides for it.

I can't get my touchpad to stay off while I have a mouse connected (Fn-F9 script not working now), and I had Amarok14 which doesn't play well now.

If anyone can update these touchpad scripts so that it'd work on the UL30A in 10.10, I'd be forever indebted.  Or maybe I'll send you a fiver like on fiver.com :)

---

### Post by Berto on 2010-10-27
> **Berto said:**
> The guides here are great.  I had some issues with 10.04, so I went to 10.10 on my UL30A - I do NOT recommend you do this until there are better guides for it.

I can't get my touchpad to stay off while I have a mouse connected (Fn-F9 script not working now), and I had Amarok14 which doesn't play well now.

If anyone can update these touchpad scripts so that it'd work on the UL30A in 10.10, I'd be forever indebted.  Or maybe I'll send you a fiver like on fiver.com :)

Update:  Ubuntu Maverick 10.10 on the UL30A is an absolute disaster.  DO NOT UPGRADE.

1.  Audio skips - doesn't matter what mp3 player I use or what I'm doing.

2.  I can't disable the track pad for more than a minute at a time

3.  The battery indicator doesn't work - it constantly says "estimating.."

4.  When a mouse is attached, the left button stops working once every hour or so.  Jamming on all the buttons and the trackpad eventually clear it up.

5.  Mouse scrolling pretty much doesn't work.  It goes 2 steps forward, one step back.

I'm sure there's fixes for all of these, but I don't have time to deal with this when 10.04 was rock solid.

So I'm going to backup all of my stuff, including VirtualBox VMs, and go back to 10.04.  It's LTS, it's super stable, the guides here rock, and there's absolutely no reason to upgrade.  Learn from my mistakes.

---

### Post by MathMcC on 2010-10-28
Can someone let me know how to change the brightness settings? The screen dims after just a few seconds of being idle. Its kind of annoying if you're reading something. I wouldn't mind knowing where to change the other power settings too.

---

### Post by ubuntoide on 2010-10-28
> **Berto said:**
> Update:  Ubuntu Maverick 10.10 on the UL30A is an absolute disaster.  DO NOT UPGRADE.

1.  Audio skips - doesn't matter what mp3 player I use or what I'm doing.

2.  I can't disable the track pad for more than a minute at a time

3.  The battery indicator doesn't work - it constantly says "estimating.."

4.  When a mouse is attached, the left button stops working once every hour or so.  Jamming on all the buttons and the trackpad eventually clear it up.

5.  Mouse scrolling pretty much doesn't work.  It goes 2 steps forward, one step back.

I'm sure there's fixes for all of these, but I don't have time to deal with this when 10.04 was rock solid.

So I'm going to backup all of my stuff, including VirtualBox VMs, and go back to 10.04.  It's LTS, it's super stable, the guides here rock, and there's absolutely no reason to upgrade.  Learn from my mistakes.

Have you tried this guide?

anyway, the touchpad freeze at boot seems to be back with kernel 2.6.36.1 on Lucid

---

### Post by Berto on 2010-10-28
> **ubuntoide said:**
> Have you tried this guide?

anyway, the touchpad freeze at boot seems to be back with kernel 2.6.36.1 on Lucid

What guide?  Cierrics?  I've done it and half of it doesn't work right for 10.10.  It rocks for 10.04 though.

The music skipping thing is not unique to 10.10 - it happens on a ton of different machines.  In my opinion, it's simply a dumpster of a distribution after looking at so many bug reports.

Stay at 10.04 and you'll get all the stability that's been baked in over time.  My mistake, not the end of the world...

---

### Post by DrMouse on 2010-10-29
Hello there,

Having ASUS UL30Vt notebook with 10.04 and then 10.10 installed. Not happy story. Random freezes, ferquent segfaults and other staff which comes with overall system instability.

In advance of your questions:
1. Memtest is OK for 5-10 hours
2. Win7 runs smoothly and perfect (sorry linux people)
3. SMART state of HDD and filesystem are ok.
4. Have latest BIOS (211)

The only thing which is **completely fixing the above random freezes is "nolapic" kernel option**. Everybody who tried it on the multicore systems knows the horrible side effects of it:
- One core
- SW interruptions
- many HW related activity brings CPU to 100%

**Please advice!!!**

I know that many people have this ASUS UL30Vt notebook with Ubuntu 10.10(04) and happy.
It looks like ASUS can provide a slightly different HW configiration under the same model.

Any ideas from you gurus.

---

### Post by The Flying Penguin on 2010-10-30
p { margin-bottom: 0.08in; }  > **Berto said:**
> Update: Ubuntu Maverick 10.10 on the UL30A is an absolute disaster. DO NOT UPGRADE.

1. Audio skips - doesn't matter what mp3 player I use or what I'm doing.

2. I can't disable the track pad for more than a minute at a time

3. The battery indicator doesn't work - it constantly says "estimating.."

4. When a mouse is attached, the left button stops working once every hour or so. Jamming on all the buttons and the trackpad eventually clear it up.

5. Mouse scrolling pretty much doesn't work. It goes 2 steps forward, one step back.

I'm sure there's fixes for all of these, but I don't have time to deal with this when 10.04 was rock solid.

So I'm going to backup all of my stuff, including VirtualBox VMs, and go back to 10.04. It's LTS, it's super stable, the guides here rock, and there's absolutely no reason to upgrade. Learn from my mistakes.

1. Strange. I have no skipping. Is this just with mp3 or all audio files?
 
 3. I have noticed the same thing. Very odd behavior. I haven't had time to look into it.
 
 4. I have the same issue except simply pressing the left mouse button on my trackpad fixes the issue. One trackpad click and my USB mouse works again.
 
 5. Hmmm, Scrolling seems to work perfectly for me.

I have ul30vt but most of the hardware should still be the same. I find it odd how some people seemingly have no issues and others do. There must be some variables in the mix somewhere.

  > **MathMcC said:**
> Can someone let me know how to change the brightness settings? The screen dims after just a few seconds of being idle. Its kind of annoying if you're reading something. I wouldn't mind knowing where to change the other power settings too.

Go to System > Preferences > Power Management

There is a check box that says "Dim display when idle". Its under both AC and battery power. I turn it off completely and set my display to go to sleep after about 10 minutes when on battery power. Works rather well.


 On a side note, it seems my battery went defective. As soon as I unplug my charger the laptop dies. Both Windows 7 and Ubuntu 10.10 tell me it may be damaged or defective. This battery is barely 6 months old so needless to say, this is a little frustrating.
 
I just hope Asus doesn't expect me to send in the whole laptop. I don't feel comfortable letting them hold onto almost 500gb of my data.
  

 I also have a question about GRUB. Is there a way that grub can detect whether I am in Enhanced or Compatible mode and boot to Win7 if in Enhanced or Ubuntu if in compatible? That would be super handy!

---

### Post by Berto on 2010-11-03
Offtopic, but has anyone found a good locking solution for the UL30A?

There is a useless triangular hole that nothing good will fit through:
[http://vip.asus.com/forum/view.aspx?id=20100108200911343&board_id=15&model=A-45GA&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20100108200911343&board_id=15&model=A-45GA&page=1&SLanguage=en-us)

Not sure what to do here...

---

### Post by The Flying Penguin on 2010-11-07
Has anyone tried using wireless N yet?

I have a Linksys WRT150N router and I just tried connecting to it in 10.10 64bit. I was only transferring to my Freenas server at about 530 KB/sec! The speed was slowly increasing in the couple minutes I let it run but not by any substantial amount. I get about 1 MB/sec when the router is in B/G mixed mode so this is obviously a decrease in performance.

I booted into Windows 7 64bit and I am getting speeds around 2.50-3 MB/sec.

Is there something I need to manually configure?

---

### Post by cb_rex on 2010-11-08
I have a N router too and had wondered if the laptop had wireless N. If you right click on the wireless icon it doesn't even detect the N network, so I figured that my ul30 wasn't N enabled. Although the manufacturer features lists the machine as having wireless N.

If there was a way of getting wireless-N working that would be great.

---

### Post by TomtheWombat on 2010-11-08
I have an ASUS RT-N16 802.11n router.  I was getting about 2.5m/s with 10.04.  Now that you mention it, my speeds have definitely dropped with 10.10, but I am not sure that they have dropped all the way to the 1-1.2m/s that I associate with 802.11g.  (Note that I haven't done any significant scientific studies to support these conclusions.  Wireless speeds are always hit or miss for me.)

---

### Post by zombiepig on 2010-11-14
Has anyone had any luck solving this problem?

> **Berto said:**
> Update:  Ubuntu Maverick 10.10 on the UL30A is an absolute disaster.  DO NOT UPGRADE.

1.  Audio skips - doesn't matter what mp3 player I use or what I'm doing.



It's driving me insane. I've tried everything I can think of to solve this one. I don't think it's a problem in maverick's kernel, since running the mainline 2.6.36 kernel has no effect on the problem. 


> **Berto said:**
> 
3.  The battery indicator doesn't work - it constantly says "estimating.."


This one is [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258) . A good workaround is to install the patched upower & gpm packages from [https://launchpad.net/~brian-rogers/+archive/power](https://launchpad.net/~brian-rogers/+archive/power) . That fixes it for me.

---

### Post by evolution167 on 2010-11-19
> **zombiepig said:**
> Has anyone had any luck solving this problem?



It's driving me insane. I've tried everything I can think of to solve this one. I don't think it's a problem in maverick's kernel, since running the mainline 2.6.36 kernel has no effect on the problem. 

Thank god I'm not the only one. It started with video and has spread to audio as well. I'm going nuts and I can't seem to find anything that will fix it.

---

### Post by nfbsk on 2010-11-20
Hi everyone, 

I'm new to ubuntu and like how it works so far. I have a question regarding the touchpad, how do I restore two finger middle click and 3 finger right click? I used the procedure here: [http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT#Tap_Clicking ]("http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT#Tap_Clicking")and actually worked for a while until I installed IRAF and it no longer works. I tried the instructions again to no avail. Can anyone help me here? Thanks.

---

### Post by Cierreics on 2010-11-20
Hi all!! I'm very busy these weeks, sorry....I've installed Maverick 2 weeks ago, everything is working GREAT, better than Lucid!! Maybe I'm lucky, but I haven't had any issue with battery, sound or anything else...:KS

I hope I'll have time to post a new guide for Maverick next week, see ya!! :popcorn:

---

### Post by evolution167 on 2010-11-21
> **Cierreics said:**
> Hi all!! I'm very busy these weeks, sorry....I've installed Maverick 2 weeks ago, everything is working GREAT, better than Lucid!! Maybe I'm lucky, but I haven't had any issue with battery, sound or anything else...:KS

I hope I'll have time to post a new guide for Maverick next week, see ya!! :popcorn:

Haha so you come on here and just gloat about your easy installation :P

---

### Post by Berto on 2010-11-23
> **zombiepig said:**
> Has anyone had any luck solving this problem?



It's driving me insane. I've tried everything I can think of to solve this one. I don't think it's a problem in maverick's kernel, since running the mainline 2.6.36 kernel has no effect on the problem. 


This one is [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258) . A good workaround is to install the patched upower & gpm packages from [https://launchpad.net/~brian-rogers/+archive/power](https://launchpad.net/~brian-rogers/+archive/power) . That fixes it for me.

I still haven't gone back to 10.04 because I wasn't traveling and didn't need the audio.  Now I'm back on the road being driven nuts again.

I think it might be pulseaudio, which has never been too stable for me, but I can't change the volume without it and don't want to spend time on it.

Would love to see how to disable the touchpad still.  There's been updates here and there, but I'm still very bearish on this distribution.

Thanks for the battery update, will mess with that later.

---

### Post by cobra11 on 2010-11-25
Which version is better? 10.10 or 10.04? I need version that will work out of box i have now 10.10 upgraded from 10.04 but its working very sluggish... Brightness control problems,hibernation problems, cannot turn on/off mouse and soo on..

---

### Post by evolution167 on 2010-11-27
> **cobra11 said:**
> Which version is better? 10.10 or 10.04? I need version that will work out of box i have now 10.10 upgraded from 10.04 but its working very sluggish... Brightness control problems,hibernation problems, cannot turn on/off mouse and soo on..

I started with 10.10 on the UL30A. While the touchpad and brightness etc seemed to work, video and audio play was impossible. I've now had to install 10.04. Video and music now work but at the sacrifice of touchpad controls. It's pissing me off but I'll have to learn to type with my wrists in the air. 

Hibernation always seems to be a problem with this laptop. I just use standby now and thanks to the brilliant battery it seems to be viable alternative.

Damn mouse.

---

### Post by The Flying Penguin on 2010-11-27
I'm wondering if some of you who are having problems with 10.10, upgraded or did a clean install? Upgrades don't always go smoothly which is why I always fresh install.

I definitely noticed an increase in performance after doing a fresh install of 10.10 and I'm running in compatible mode because of my nvidia graphics!

I do have that battery estimating issue that many people seem to be having though but my battery broke so that may have something to do with it.

---

### Post by christianco on 2010-11-28
ul30vt here.

I have no problems with 10.10 - intel card works great, sound, compiz etc. except i am still having the same problems that I had with 10.04 - I can't get the nvidia card working exclusively - not with compatibility mode, with the nvidia driver, not on 32 or 64 bit, no matter if i run nvidia-xconfig. 

if I do run nvidia-xconfig, my boot hangs about where X starts I think - somewhere after the boot. If I delete xorg.conf i can boot all the way in, but I'm pretty sure the Intel card is being used. lspci | grep VGA reports both cards running. plus I can't enable compositing for some reason. this is a mystery to me.

I'm not sure what I do wrong exactly but I suspect it is inexperience of some kind. I'm really looking forward to Cierreics Maverick post which I hope will fix me. 

Meanwhile, anyone have a clue what I am doing wrong?

---

### Post by christianco on 2010-11-28
Come to think of it, my experience is really strange and goes counter to everything that i have read: With bios set to Compatibility Mode, lspci shows both cards as active. Can anyone else confirm?

---

### Post by Holymoly on 2010-11-28
curious, any chance that ubuntu can be made to support zoom, rotate, 3-finger-swipe/scroll with the UL30 touchpad? they were added in the last ElanTech drivers, i really miss the forward/backward shortcuts :D

---

### Post by The Flying Penguin on 2010-11-29
> **christianco said:**
> Come to think of it, my experience is really strange and goes counter to everything that i have read: With bios set to Compatibility Mode, lspci shows both cards as active. Can anyone else confirm?

I just checked and only my Nvidia card shows as active.

All I had to do was switch to compatibility mode, activate the Nvidia driver under additional drivers, and then nvidia-xconfig (can't remember if that was before or after reboot).

What is your BIOS version? Perhaps you have a different version that requires you to turn the Intel card off in a different way or doesn't even allow it? Maybe you need to update it? I have version 208 but I see that 211 is now out.

---

### Post by cobra11 on 2010-11-29
I have testing ubuntu 10.04 and 10.10 better is 10.10 for my. I get everything working,i installed mod for only intel graphic soo i get about 5-8W in powertop,wery good.. Other things works really good except i need to type in terminal synclient TapButton2=2 every time i turn off,suspend or hibernate laptop because i want to have middlebutton when i press with two fingers. And other thing is i cant get working fn+f9 for turn off touchpad.

---

### Post by christianco on 2010-11-30
> Come to think of it, my experience is really strange and goes counter to everything that i have read: With bios set to Compatibility Mode, lspci shows both cards as active. Can anyone else confirm?

and this:

> What is your BIOS version? Perhaps you have a different version that requires you to turn the Intel card off in a different way or doesn't even allow it? Maybe you need to update it? I have version 208 but I see that 211 is now out.

If anyone else runs into my problem, it's the BIOS. I had bios 204 flashed. An upgrade to 211 fixed the problem with no negative side effects that I have detected thus far. Thanks "The Flying Penguin"!

---

### Post by zombiepig on 2010-12-02
Here's my bug report about sound issues on the ul30a - 
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/677709](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/677709)

Lots of troubleshooting steps, but unfortunately nothing which has had a noticeable effect yet :(

---

### Post by The Flying Penguin on 2010-12-02
> **christianco said:**
> and this:
If anyone else runs into my problem, it's the BIOS. I had bios 204 flashed. An upgrade to 211 fixed the problem with no negative side effects that I have detected thus far. Thanks "The Flying Penguin"!

Glad I could help :D

---

### Post by cobra11 on 2010-12-02
Fix for touchpad on/off:

sudo gedit /etc/acpi/asus-touchpad.sh 
and copy:
```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi
```

than
sudo gedit  /usr/share/acpi-support/power-funcs
and delete this:
```
  if [ x"$user" != x"" ]; then
               userhome=`getent passwd $user | cut -d: -f6`
            export XAUTHORITY=$userhome/.Xauthority
    else
        export XAUTHORITY=""
    fi
```
and paste this:
```
export XAUTHORITY=`ps a | grep -v grep | grep X | sed -n 's/.*-auth \(.*\)/\1/p' | cut -f 1 -d ' '`
```

Now i can turn On/Off touchpad on Asus UL30VT in Ubuntu 10.10 :)

---

### Post by cobra11 on 2010-12-02
The only problem is that i cant get working Two finger tap as middle click, does anybody know fix for that?

---

### Post by mric on 2010-12-03
> **The Flying Penguin said:**
> 

I do have that battery estimating issue that many people seem to be having though but my battery broke so that may have something to do with it.


think this was due to the upgrade 10.04 -> 10.10 i belive and still not fixed. in addition empathy has issue with ICQ ( need to look for the bugreport )

beside that the sporadic freezes which might be related to "pulseaudio" are gone on my system

for xmas i want to upgrade to SSD .. i know some of you have already SSD built in so i wonder if its worth and i ca expect in regards to battery life

cheers
mike

---

### Post by finalatk on 2010-12-27
Hello everyone.  I'm considering buying the ul30a but I am curious how fast Ubuntu is booting for you and also how well HD video is playing on the GMA 4500.  Anyone care to share?  Thanks!

---

### Post by The Flying Penguin on 2010-12-29
> **finalatk said:**
> Hello everyone.  I'm considering buying the ul30a but I am curious how fast Ubuntu is booting for you and also how well HD video is playing on the GMA 4500.  Anyone care to share?  Thanks!

Ubuntu boots very fast on this machine if you are just running a single card. I have the ul30vt though so I have to run in compatible mode because I have hybrid graphics and its the only way to exclusively use the Nvidia card. Even with compatible mode enabled, boot times are respectable. Sorry I don't have numbers for you. 

I can't comment as to how the GMA 4500 performs for HD video because I honestly can't remember. I only used it for a couple days on 9.10 before 10.04 came out. I've been using the Nvidia card ever since. It runs flawless as far as HD video is concerned.

---

### Post by christianco on 2010-12-29
> I can't comment as to how the GMA 4500 performs for HD video because I honestly can't remember. I only used it for a couple days on 9.10 before 10.04 came out. I've been using the Nvidia card ever since. It runs flawless as far as HD video is concerned.

the GMA runs great. Compiz great, youtube 1080 great, even runs SecondLife OK.

---

### Post by Meizirkki on 2011-01-01
> **christianco said:**
> the GMA runs great. Compiz great, youtube 1080 great, even runs SecondLife OK.

Intel GMA runs Secondlife OK?? Video or it didn't happen. Even Compiz and lags on my UL50

---

### Post by christianco on 2011-01-02
> **Meizirkki said:**
> Intel GMA runs Secondlife OK?? Video or it didn't happen. Even Compiz and lags on my UL50

Am I lying? no. I have the ul30vt. and I swear, by all things free and open, that Second Life works without a lag on my machine's GMA. does it look fantastic? no. but it runs.

I am definitely using the GMA. the ul30vt also has an nvidia card but this i am not using. i don't want to make a video. let's pretend I did though cause why would i lie?

---

### Post by bvgd on 2011-01-03
> **cobra11 said:**
> The only problem is that i cant get working Two finger tap as middle click, does anybody know fix for that?
On 10.04 it works:
[http://blog.sidewaysmilk.com/post/338402210/swap-2-finger-and-3-finger-tap-in-linux](http://blog.sidewaysmilk.com/post/338402210/swap-2-finger-and-3-finger-tap-in-linux)

---

### Post by cobra11 on 2011-01-05
Yes but on Ubuntu 10.10 still doesnt work. Damn they need to fix this problem cause i really hate three finger tap as middle click..

---

### Post by Meizirkki on 2011-01-06
> **cobra11 said:**
> Yes but on Ubuntu 10.10 still doesnt work. Damn they need to fix this problem cause i really hate three finger tap as middle click..

I had dualtap middleclick when using kubuntu 10.10. It was on by default. Could this be just about the k prefix or..? I mean, it should work?

---

### Post by krushaaa on 2011-01-06
Hey guys thank you all for your generell help on asus ul30-all variants.
I just wanted to ask whether it would be possible if anyone could post the normal/original code from the

/etc/acpi/asus-brn-down.sh && /etc/acpi/asus-brn-up.sh 

since i have quite unfortunately a script there and do not have the orignial code anymore but i would really like to have proper working backlight control which does not react 2 seconds after pressing.

krushaaa

---

### Post by krushaaa on 2011-01-07
> **Meizirkki said:**
> I had dualtap middleclick when using kubuntu 10.10. It was on by default. Could this be just about the k prefix or..? I mean, it should work?

hey just use

```
synclient TapButten2=2 TapButton3=3
```

this should change double finger press to middleclick and triple finger press to right click :)

---

### Post by cobra11 on 2011-01-08
> **krushaaa said:**
> hey just use

```
synclient TapButten2=2 TapButton3=3
```

this should change double finger press to middleclick and triple finger press to right click :)

Jeah know that,but how to make it permanent? 
I try everything,but nothing seems to get work right..

---

### Post by wapko on 2011-01-08
I have a ul30vt and i speedread this thread. and found nothing about fn+f5&f6 brightness adjustments when using only the g210m. i want the nvidia card active for vdpau. and i rarely need 10+ hours of battery. 

but i wanted the brightness buttons to respond, and fast.. found some info on a gentoo forum about echoing values to /proc/acpi/video/VGA1/LCDD/brightness. if you `cat` it, it tells you the different brightness levels.

every press on brightness key combo sends 2 signals. one for press and one for release. if you want all 16 brightness levels just uncomment the lines in the script.

enjoy ! :D


**this is my /etc/acpi/asus-brn-up.sh**
```

#!/bin/bash
#levels:  5 11 17 23 29 35 41 47 53 59 65 72 79 86 93 100
acpi_fakekey $KEY_BRIGHTNESSUP
# --- if you want all 16 brightness levels, uncomment the next 2 lines
#if [ -f /dev/shm/brup ]; then rm /dev/shm/brup; exit 0; fi
#touch /dev/shm/brup
levels=([0]=5 [1]=11 [2]=17 [3]=23 [4]=29 [5]=35 [6]=41 [7]=47 [8]=53 [9]=59 [10]=65 [11]=72 [12]=79 [13]=86 [14]=93 [15]=100)
CLvl=`grep -i current: /proc/acpi/video/VGA1/LCDD/brightness | cut -f2 -d" "`

for ite in {0..15}
do
	if [ ${levels[$ite]} -eq $CLvl ]; then
		if [ ${levels[$ite]} -ne "100" ]; then CLvl=${levels[$ite+1]}; fi
		break
	fi
done

echo $CLvl > /proc/acpi/video/VGA1/LCDD/brightness

```

**this is my /etc/acpi/asus-brn-down.sh**
```

#!/bin/bash
#levels:  5 11 17 23 29 35 41 47 53 59 65 72 79 86 93 100
acpi_fakekey $KEY_BRIGHTNESSDOWN
# --- if you want all 16 brightness levels, uncomment the next 2 lines
#if [ -f /dev/shm/brdn ]; then rm /dev/shm/brdn; exit 0; fi
#touch /dev/shm/brdn
levels=([0]=5 [1]=11 [2]=17 [3]=23 [4]=29 [5]=35 [6]=41 [7]=47 [8]=53 [9]=59 [10]=65 [11]=72 [12]=79 [13]=86 [14]=93 [15]=100)
CLvl=`grep -i current: /proc/acpi/video/VGA1/LCDD/brightness | cut -f2 -d" "`

for ite in {0..15}
do
	if [ ${levels[$ite]} -eq $CLvl ]; then
		if [ ${levels[$ite]} -ne "5" ]; then CLvl=${levels[$ite-1]}; fi
		break
	fi
done

echo $CLvl > /proc/acpi/video/VGA1/LCDD/brightness

```

ohh. and the power information notification gets REALLY annoying if you spam the brightness combo with the brightness at 100%, it keeps popping up.. HALP?

---

### Post by krushaaa on 2011-01-08
hey guys,

i changed all scripts and settings just as discribed in post #110.
but unfortunately the brightness functions quiete frankly will  not work for me could anyone help?

---

### Post by The Flying Penguin on 2011-01-08
> **christianco said:**
> Am I lying? no. I have the ul30vt. and I swear, by all things free and open, that Second Life works without a lag on my machine's GMA. does it look fantastic? no. but it runs.

I am definitely using the GMA. the ul30vt also has an nvidia card but this i am not using. i don't want to make a video. let's pretend I did though cause why would i lie?

I downloaded SL once and it ran on a graphics card FAR less capable than the GMA 4500.

If you used the Nvidia card you could bump up the graphics quite a bit. I can run The Sims 3 and Perfect World International under Wine at max resolution and max graphics no problem. I've even hooked it up to my HDTV via HDMI and run the games at 1920x1080. Plus I can watch 1080p movies while my CPU keeps busy with other activities.

So your using VA API then? That work out of the box? Nice to know that card can handle HD in Linux. Now I wish I had bought my mom the laptop for Christmas that had that card. 

Oh, by the way. It took Asus almost a full month to get me my replacement battery and it is for a UL50!

---

### Post by krushaaa on 2011-01-11
> **cobra11 said:**
> Jeah know that,but how to make it permanent? 
I try everything,but nothing seems to get work right..

hey i did not try this, as i like it as it is, but this seems to be working for some people
[http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT#Tap_Clicking](http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT#Tap_Clicking)

hope it works
--------------------------- Edit---------
hey just tried it and it works perfectly + it is permanent

---

### Post by bilallucky on 2011-01-11
[B][Asus UL30/ul80]("http://www.letmedefine.com/asus-ul80vt-wx077v/") is a 100% Linux compatible ultra-thin laptop, with no  reported problems from the current user base. From personal to business  use.You can check the model and details of you laptop with these commands:
sudo dmidecode -s system-product-name
sudo dmidecode -s system-version
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' [/B]

---

### Post by Meizirkki on 2011-01-16
> **krushaaa said:**
> hey just use

```
synclient TapButten2=2 TapButton3=3
```

this should change double finger press to middleclick and triple finger press to right click :)

I think you misunderstood. I meant it was always that way _by default_, I never had to change anything.

---

### Post by bvgd on 2011-01-18
> **Cierreics said:**
> [B]
These settings are tested for Ubuntu Lucid...[/B]
I'm still using 10.04 (kernel 2.6.37-12-generic-pae) on UL30A with adjustments from the post #110. 
Today I have started a powertop utility and found 8.7W power consumption. But after an 'S' command in the powertop window (SATA powersave mode ON) I have got 8.2W. 
My question: is it possible to turn this mode automatically on?

---

### Post by ubuntoide on 2011-01-19
> **bvgd said:**
> I'm still using 10.04 (kernel 2.6.37-12-generic-pae) on UL30A with adjustments from the post #110. 
Today I have started a powertop utility and found 8.7W power consumption. But after an 'S' command in the powertop window (SATA powersave mode ON) I have got 8.2W. 
My question: is it possible to turn this mode automatically on?

It should work automatically if you use pm-powersave-utils, don't trust powertop too much, it's quite outdated. Power readings are correct but its hints and tips are quite off for ubuntu 10.10 for example.

Anyway, I found a weird thing right now. If you check carefully on side exhausting there is no air flow meaning that the system fan doesn't spins, so is completely passively cooled. That's wrong and dangerous imo, temperature is around 45°C at idle, when on Windows I can run as low as 30°C.
Is there a way to have it run? do I have to file a bug somewhere?

---

### Post by Th3Pr0ph3t on 2011-01-24
> **asphy said:**
> I've got the exact same model, supplied from o2. Just out of interest, does your mobile broadband work? I can see the modem just fine, and even talk to it to some limited extent but I can't seem to turn the radio on at all. I've read through all of the Huawei documentation (according to what it's telling me, it's a Huawei EM770) and noticed that it has two radio kills, a soft kill that you can disable by setting full card functionality (AT+CFUN=1) and a hard kill that I can't seem to disable anywhere. I have rfkills for bluetooth and wlan just not for 3g. Calling AT+CFUN=1 returns ERROR and looking at the output of AT^RFSWITCH? shows me its because of the hard kill.

Basically, I've a modem that I can talk to but cant do anything with as its radio is forcefully off, any ideas?

*edit 11/10/10*

I've figured out this issue, its related to two missing rfswitches that are not implemented in the asus-laptop platform driver. I've worked with the guys over at acpi4asus to get these implemented, you can find a patch for the issue here : 

[http://dev.iksaif.net/issues/108](http://dev.iksaif.net/issues/108)

I have the same model, from O2 UK. I am currently running ubuntu 11.04 alpha 1 with kernel 2.6.37-12.
I have tried everything I could to get it to work, but sadly nothing happened, the radio is still off on my device. The patch was merged to mainline ages ago and the wwan file has 1 in it as in "enabled". Now since you managed to get it to work can you tell us how you did it please? I also tried on 10.10 etc, but nothing.
Or indeed if anyone else with the integrated 3g modem knows how to get it to work please help me I'm at a loss. :-(

---

### Post by krushaaa on 2011-02-18
hey all you with an asus ul30VT here i found this page which gives apperently a patch that enables the backlight function keys.

[http://dev.iksaif.net/issues/79](http://dev.iksaif.net/issues/79)

but unfortunatly I am rather a linux noob so i don't know how to install the patch any help would be appreciated.

---

### Post by koleoptera on 2011-02-25
So I ve got a U31F specs can be seen here [http://www.asus.com.au/product.aspx?P_ID=OV45sT3DY56akobY](http://www.asus.com.au/product.aspx?P_ID=OV45sT3DY56akobY)
10.04 64 bit..although I think I ll move back in 32..
Still in both architectures,I ve got 2 issues:

1) Following the instructions on post 82, which worked for everyone, nothing happens. Skype starts as it should but the video remains flipped...Any ideas?

2) Powertop when used as sudo freezes the system..is anybody else facing the same?

Any ideas would be great....

---

### Post by Hobbes on 2011-05-08
Anyone want to update with what does/doesn't work on 11.04? (UL30 / UL30VT)

(mine is UL30VT)
I couldn't turn off nvidia without it freezing starting a good while back, so I have switched to nvidia only...

I like the ability to watch movies with vdpau (low cpu usage, etc) especially when hooked up to 1080p monitor... but the battery life is obviously worse and I don't like how it takes forever to boot-up or resume :(

Just re-installed 11.04 from scratch whereas up until now I had updated from 10.10 so most stuff was still working....

hopefully i can at least get two-fingered scrolling... brightness and other things are secondary for me.

---

### Post by mric on 2011-05-08
Suspension\Hibernation works, however power usage is up again .. need to see what can be tweaked.

---

### Post by chicgeek on 2011-05-08
I'm very very pleased with how Natty works with my UL30A-A2.  It's actually fixed a lot of issues that I had with Lucid and Maverick.  Some notes:

[LIST]
[*]I did a clean install. A new Ubuntu version is as good a reason as any to back up and start with a clean slate.
[*]It disabled my two-finger scrolling.  **Hobbes:** Just go into *mouse settings > touchpad* to sort this out from there. Simple.
[*]Video is MUCH smoother. In Maverick I had issues with full-screen video jumping around, so much so that I resorted to my Win7 partition for watching video.  Now I don't need to do that, the graphics management has gone from unusable to nearly perfect. Happy bunny.
[*]Strangely enough, the Unity launcher is EXACTLY how I've set up my desktop for the past two years, whether on Windoze or Ubuntu: simple top panel with program icons on a left panel. Just added some left auto-hide action, reduced icon size, and perfect.
[*]Not UL30-related, but I also hid desktop icons, places/workspace launcher buttons. Clean clean clean.
[/LIST]
Anyone found any other surprises (good or bad) with the UL30s and Natty?  And did you upgrade or install anew?

---

### Post by unchain on 2011-05-09
This is my first install of ubuntu, I haven't used Linux in a long while (since maybe, Slackware 11.0?) but decided to dual boot it with Win7 on my new-used UL30VT. I'm running Natty without any major issues.

Nearly everything on this page: [http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT](http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT) has been extremely helpful and still applicable to Natty even though it was intended for Maverick.

As far as turning off the nVidia card, I followed the guide, however, I'm still seeing both cards when using ```
lspci |grep VGA
```That said, my power usage according to PowerTop has dropped very, very significantly, from around 13-15 watts consumption down to around 8-11 watts consumption, which leads me to believe that the nVidia card is disabled, despite lspci showing otherwise.

The tutorial provided to enable screen brightness controls with the Fn+F5 and Fn+F6 keys works great for me, as does the linked tutorial to use Fn+F9 to disable and enable the touchpad.

I had the issue with the webcam displaying upside down in both Ubuntu and Windows 7, but a re-install of the webcam drivers fixed the issue in Windows, and now I am no longer encountering it in Ubuntu. Very strange, but I won't complain.

---

### Post by unchain on 2011-05-09
Actually, I spoke too soon, I forgot about one thing - I can't seem to get Unity to load properly. Boo.

**EDIT:** And minutes later, I fixed it. I still had the nVidia driver installed, so I removed it. Now I'm able to load Unity, run glxgears, etc. Hurrah! 

Also, I was able to confirm that only the Intel VGA card is on by using:```
sudo lshw -C video
``` As a result I got: ```
  *-display               
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:fcc00000-fcffffff memory:d0000000-dfffffff ioport:cc00(size=8)

```Pretty sure that means the nVidia card is off, haha.

Yeah, so now in 11.04 all my Fn keys on my UL30VT work (not sure about Fn+F8, I have yet to use it), I'm using the Intel VGA card only with success, I have very low power consumption, very good performance and really, it's working better than I could have expected it to be! No complaints.

---

### Post by The Flying Penguin on 2011-06-04
Hybrid graphics appear to be functional now in 11.04, at least as far as I can tell. I am able to swap between the Intel card and Nvidia with little effort, although it does require a restart. Best of all, I am able to use the Nvidia proprietary driver!

Here is what I did on my ul30vt running the 64bit version of 11.04

1) Change BIOS to compatibility mode which will turn off the Intel card.
2) Install the Nvidia proprietary driver using Ubuntu's driver finder (Additional Drivers) and then reboot.
3) Reboot and change the BIOS setting to "Enhanced".
4) Now boot into Ubuntu just like normal. Unlike previous versions of Ubuntu, you shouldn't be greeted by a blank screen or some kind of lock up. You should be able to log in just like normal. Now, you should already be using the Intel card and its driver but the Nvidia card is also on. We need to turn it off in order to enjoy the battery savings the Intel card provides.

5) Download and install this deb file: [http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1~ppa-karmic_all.deb]("http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb") from this thread: [http://ubuntuforums.org/showthread.php?t=1366605](http://ubuntuforums.org/showthread.php?t=1366605) Thanks Avilelle and Blackmoon105!
6) Enter this into your terminal:
```
[COLOR=#000000][FONT=Times New Roman][FONT=sans-serif]sudo modprobe nvidia_g210m_acpi[/FONT][/FONT][/COLOR]
```That will turn off your Nvidia card and you should only be using the Intel card.

7) To confirm you are using the Intel card paste into terminal:
```
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]sudo lshw -C video[/FONT][/FONT][/COLOR]
```It should only show the Intel card and driver.

Use powertop to verify power savings.

Note this is not persistent and your Nvidia card will turn back on if you shutdown/restart the machine. Also, suspend and hibernation seemed to result in the Nvidia card being turned back on. I'm not sure if that was fixed in that deb file or not. From now on, whenever you want to use the Intel card you will have to switch to "Enhanced" mode and enter the command in step 6.

Switching back to the Nvidia card is even simpler. Just reboot, change the BIOS to "compatible", and log into Ubuntu like normal. You will automatically be running the Nvidia card with appropriate driver.

As far as I know this didn't work at all in previous versions of Ubuntu. It would always lock up or give me a blank screen if I tried to run Ubuntu in "enhanced" mode after installing the Nvidia proprietary drivers. Sure it requires a couple steps and reboot every time but its certainly better than being stuck with one card.

There is another possible option for anyone who is interested. You can find it at [https://github.com/awilliam/asus-switcheroo](https://github.com/awilliam/asus-switcheroo) There is a readme that explains it. Nicias in this thread: [http://ubuntuforums.org/showthread.php?t=1366605&page=13](http://ubuntuforums.org/showthread.php?t=1366605&page=13) claims it works perfectly for him using the Nvidia proprietary driver.
_______________________________________________________________________

Aside from good news in the hybrid graphics department, I have noticed 11.04 has made noticeable improvements when it comes to performance. Note, I am not running Unity. I'm still rocking the Gnome 2/Ubuntu interface. 

So far I've noticed:
1) Programs load quicker and navigation feels much snappier. Overall it just feels like a smoother experience.
2) Startup and shutdown times are noticeably faster even when running in "compatible" mode.
3) Flash video plays extremely well. I am able to play 1080p flash in fullscreen with both the Intel and Nvidia card. There is no stuttering at all once the video gets past the first few seconds. The first few seconds will sometimes drop a few frames ever so slightly when I first press play. 1080p flash stuttered in 10.04 and 10.10 to the point I didn't even bother playing it.
4) Streaming Netflix fullscreen inside a XP vm using VirtualBox is smoother than it was under 10.04 and 10.10. It's almost perfect now. A solid 9/10 vs what was a 7-8/10.

I'm really happy with the improvements 11.04 has made when it comes to compatibility and performance. I certainly recommend anyone with our laptops strongly consider upgrading.

---

### Post by cobra11 on 2011-08-30
Finaly i get to work two finger tap as middle click in Ubuntu 10.10, i think it will work i newer versions too. 
I just added this as /etc/pm/sleep.d/99_touchpad (don't forget to chmod +x.) 
#!/bin/sh
PATH=/sbin:/usr/sbin:/bin:/usr/bin
case "${1}" in
        hibernate)
                ;;
        resume|thaw)
        DISPLAY=:0.0 su <username> -c /home/<username>/touchpad.sh
                ;;
esac
Substitute your own user name of course. My touchpad.sh (which is also called via "Startup Applications") is

#!/bin/bash
dev="ETPS/2 Elantech Touchpad"
# Use xinput --list-props "ETPS/2 Elantech Touchpad" to list data
xinput set-prop "$dev" "Synaptics Tap Action" 8, 9, 0, 0, 1, 2, 3
xinput set-prop "$dev" "Synaptics Locked Drags" 1
xinput set-prop "$dev" "Synaptics Locked Drags Timeout" 500

to set locked dragging and two-finger middle click.

---

### Post by Ribl on 2011-10-16
Anyone else considering problems with Gnome3 / Ubuntu 11.10?

Things I encounter these:

Touchpad:
Detected as Elantech Touchpad but:
TapButton2 and 3 are inverted as always...
 TapButton3 isn't working at all. (Synclient TapButton2=2 TapButton3=3 won't help)
As there is no gconf (gnome3 uses dconf), no xorg.conf (I own that ul30a without nvidia graphics, only intel) and I cannot add these TapButton change to dconf, I'm unable to switch the TapButtons during Gnome3 startup. 

Screensaver:
Not able to wake up after the screen went black. => Hard reboot

Battery life:
Decreased to about 60% the lifespan of Ubuntu 10.10

CPU load:
Seems to be way more.
720p flash videos ran flawlessly on Ubuntu 10.10 but now they are kind of Michael J. Fox'ish... :/

By the way, the webcam is running perfect. No more upside down :)

---

### Post by groner on 2011-10-16
> **Ribl said:**
> Anyone else considering problems with Gnome3 / Ubuntu 11.10?

Things I encounter these:

Screensaver:
Not able to wake up after the screen went black. => Hard reboot


The backlight on my UL30A does not automatically come back on, but after unlocking the display with my password Fn+F6 brings it back.

The backlight does turn on if I switch to another virtual console, but returning to the X11 virtual console it turns off again.

I'm using Gnome Shell.

---

### Post by s13_mills on 2011-10-26
I have recently installed 11.10 on my UL30VT, and have had a generally positive experience:

- No trouble installing
- Used the 'Compatible' mode in BIOS workaround to get NVidia card working
- HDMI audio is working (Change to HDMI nr2 in sound settings)
- Speed and responsiveness are generally good
- Touchpad seems fine (unless I have another mouse at boot, see below)
- Wireless works great (well in G mode anyway)

Some negatives:

- I have to use the nvidia-settings to get the HDMI output to work (not supported by the normal display settings manager)
- If I have another mouse plugged in at boot, I have to log in/out to get the touchpad to work
- My webcam was upside-down to start with, but was fixed by [this workaround]("http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT")

I found the install of Ubuntu and MythTV pretty easy on this laptop (I am using it mainly as a MythTV box). Couldn't comment on battery life because I always have it plugged in, and not really set up to conserve battery anyway.

---

### Post by Gskellig on 2011-11-29
> **cobra11 said:**
> Finaly i get to work two finger tap as middle click in Ubuntu 10.10, i think it will work i newer versions too. 
I just added this as /etc/pm/sleep.d/99_touchpad (don't forget to chmod +x.) 
#!/bin/sh
PATH=/sbin:/usr/sbin:/bin:/usr/bin
case "${1}" in
        hibernate)
                ;;
        resume|thaw)
        DISPLAY=:0.0 su <username> -c /home/<username>/touchpad.sh
                ;;
esac
Substitute your own user name of course. My touchpad.sh (which is also called via "Startup Applications") is

#!/bin/bash
dev="ETPS/2 Elantech Touchpad"
# Use xinput --list-props "ETPS/2 Elantech Touchpad" to list data
xinput set-prop "$dev" "Synaptics Tap Action" 8, 9, 0, 0, 1, 2, 3
xinput set-prop "$dev" "Synaptics Locked Drags" 1
xinput set-prop "$dev" "Synaptics Locked Drags Timeout" 500

to set locked dragging and two-finger middle click.

If you have the synaptics drivers you can use ```
synclient tapbutton2=2
synclient tapbutton3=3
``` to fix the buttons. Also synclient -l lists a ton of settings you can change to suit your needs. It is VERY useful.

---

### Post by The Flying Penguin on 2011-12-14
Does anyone know how to apply the HDMI audio fix to 11.04?

---

### Post by cobra11 on 2011-12-15
> **Gskellig said:**
> If you have the synaptics drivers you can use ```
synclient tapbutton2=2
synclient tapbutton3=3
``` to fix the buttons. Also synclient -l lists a ton of settings you can change to suit your needs. It is VERY useful.

I tried this a billion of times, but problem is it wont work permanently... Than i use this script and work permanent without problem.

---

### Post by mpw on 2012-04-01
Hello,

if I have an Asus ul30vt aswell. Since the upgrade from 10.04 to 11.10 (fresh install), the fan is so loud I can hardly work on the laptop. That is so anoyying.

The CPUs do nothing and the fan run all the time. In both bios modes (compatible, enhanced) with Intels GPU and with nvidia.

Do you experience this? Any driver updates or kernel parameters to fix it?

 Bye
MPW

---

### Post by tomsecret on 2012-05-07
> **mpw said:**
> Hello,

if I have an Asus ul30vt aswell. Since the upgrade from 10.04 to 11.10 (fresh install), the fan is so loud I can hardly work on the laptop. That is so anoyying.

The CPUs do nothing and the fan run all the time. In both bios modes (compatible, enhanced) with Intels GPU and with nvidia.

Do you experience this? Any driver updates or kernel parameters to fix it?

 Bye
MPW

Sorry for a late reply. One thought: Did you disable the nvidia card? When the bios mode is set to enhanced, both graphic cards are active, and the nvidia card must be switched off after booting into ubuntu, as explained in this thread: [http://ubuntuforums.org/showthread.php?t=1366605]("http://ubuntuforums.org/showthread.php?t=1366605"). If not the fan will work quite hard, even when idle :)

---

### Post by cb_rex on 2012-06-01
How are people coming along with 12.04 on the Asus ul30a?  

A lot of things seem to work perfect straight away and from pressing the power button it only takes 15s to boot with a SSD!  Also the camera is the right way round and the touchpad works great.  The only issue for me is the backlight doesn't seem to auto dimm instantally when I switch from mains to battery power. Has any one else had this issue?  It does dim when inactive for about a minute but brightenes back up when you move the cursor.

I added acpi_backlight=vendor after quiet splash in the /etc/default/grub file which sorts the function keys and notifications out, (as discussed in earlier posts on this thread), but I'm not sure how to sort out the lack of auto dimming.

---

### Post by mlpinto on 2012-08-03
Hi,

I'm running 12.04 on my UL30a with very few problems. I've not noticed the auto dim moving from AC to battery, but I don't do that very often. I'll check.

I do have an issue where I can't write to any SD cards or USB sticks that I connect. I'm sure I didn't have this issue in older versions. Any suggestions would be appreciated!

---

### Post by Procrastes on 2013-04-16
> **mlpinto said:**
> Hi,

I'm running 12.04 on my UL30a with very few problems. I've not noticed the auto dim moving from AC to battery, but I don't do that very often. I'll check.

I do have an issue where I can't write to any SD cards or USB sticks that I connect. I'm sure I didn't have this issue in older versions. Any suggestions would be appreciated!

Just to chime in and say I'm seeing the same problem after and upgrade from 10.04 -> 12.04. 

I was able to use and SD or SDHC card on in the media bay in 10.04 just minutes before the switchover.  I haven't tried a stick yet, but saw the problem with an IPOD nano that worked fine in 10.04.

I just upgraded, so if I get a chance to troubleshoot it this weekend, I'll post the result here.

---

