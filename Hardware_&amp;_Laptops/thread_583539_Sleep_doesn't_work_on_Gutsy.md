---
title: "Sleep doesn't work on Gutsy"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by Jaxilian on 2007-10-20
It used to work flawless on Ubuntu 7.04, but now on 7.10 it just hangs after getting the screen all black. No keys make it respond either.

Hoping for a upgrade/fix real soon :mad:

---

### Post by Jaxilian on 2007-10-20
Correction:  Suspend (Sleep) AND Hibernate doesn't work. Both freeze with a black screen and harddrive-lamp still lite and buzzing like it's working.

Bad move from Ubuntu team to regress backwards like that.

---

### Post by cam2009 on 2007-10-20
Exact same problem with my Toshiba Satellite A105 laptop. Need to manually hold down the power button and restart to do anything. Worked fine in Feisty. I tried replacing a line in  /etc/default/acpi-support, but that did nothing. I've heard it has to do with Compiz, which makes since, but I don't want to just retry with it off until I have some more info.

---

### Post by jsully1 on 2007-10-20
What type of graphics card do you have?

---

### Post by Jaxilian on 2007-10-20
> **jsully1 said:**
> What type of graphics card do you have?

ATi radeon mobility x600 (128mb)

---

### Post by sixstorm on 2007-10-20
I have a Compaq C714NR and when I close the lid, the screen turns off but the computer is still running.  Hopefully there will be a patch/fix for that soon!  I'd like to keep Ubuntu up and not have to turn it off/switch back to Vista.

---

### Post by stringbean82 on 2007-10-20
Is there an update or solution for this problem now?
I have sort of the same problem with my Dell Inspiron 6400.

It doesnt hang, but its goes blacks and nothing happends until I move the mouse again and then it goes back to a different to normal login screen. 

This happends with suspend and hibernation mode.

---

### Post by Childe on 2007-10-20
Apparently, this was known about before 7.10 was released.  Bug report is here:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

I've got the same problem on a Toshiba Satellite M55 with an ATI Radeon Xpress 200M.

---

### Post by amphoterous on 2007-10-20
I also have this same problem with a Gateway MX6453 with an ATI Radeon Xpress. Hopefully we can figure out a solution!

---

### Post by Childe on 2007-10-20
They've given the bug a "wishlist" status, AFAIK, and are waiting on AMD (who now owns ATI).  I'm not sure that there'll be a solution before the next version.

I'm considering rolling back to 7.04, honestly.

---

### Post by Phoenix on 2007-10-20
I'm having the same problem with a Dell Latitude D610 and a Radeon Mobility X300

There's GOT to be something we can do about this isn't there? I've seen a fix posted elsewhere for those with Nvidia cards but are we just out of luck? (I have a separate post on this as well somewhere)

I really don't want to have to regress to 7.04....I like 7.10 a lot besides this one thing.

---

### Post by ColombianGold on 2007-10-20
hey everyone!):P

I have a thinkpad T60 with an ati x1300 with the same issue....:evil: Unfortunately there isn't a real fix yet...You can blacklist fglrx and get back suspend but loose 3D acceleration. Some peolple are trying things with the kernel but I havent seen a stable solution.

The best thing you can do is use the previous kernel...just pick it in GRUB. You will have 7.10 but with 7.04 kernel's. You will get suspend back to normal! but no tickless kernel.

This is all ati's fault...this bug was known way before Gutsy's release and they didn't deliver! Last time I purchase junk from amd/ati...they have the crappiest linux support.Lets how long they leave people hanging.

Checkout Gutsy's release notes, look for Susppend to ram
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

There some workarounds here, including blacklisting.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653) 

Hope this helps

CG

---

### Post by ravenon on 2007-10-20
Yes, one can use the Feisty 2.6.20 kernels; you have to build fglrx module. Suspend and Hibernate then work as in Feisty. However, for what ever reason, USB flashdrives fail to mount. All other usb devices (printer, camera) work fine.

---

### Post by Radh77 on 2007-10-20
Same problem here. I have Asus Z62F with Intel 945GM video... Whenever I put the laptop to suspend or hibernate it locks up. Actually it looks like the computer is correctly suspended/hibernated but when it tries to wake up all I get is a blank screen.. The HDD led is on for about 30 secs and then it goes off. The only way to get out of this is power down the laptop.
Anyone any ideas?

---

### Post by meldroc on 2007-10-20
Same here, Asus A8Js with Nvidia Geforce Go 7700 video.  I try to suspend, then when I try to wake back up, hangs with a blank screen.

And who was the tool that decided this was a "wishlist" problem?  For me, this is a big deal.  It used to work on Feisty.  Reliably.  I need this functionality - it's a must-have for me with a laptop - I should be able to shut the lid, have it go to sleep, then when I open it up in a cafe somewhere, it should wake up every single time and Just Work.  This is ********.

**** you Nvidia.  Every time you release a new Linux driver as of late, you do nothing but introduce new bugs.  None of the new releases fix any of the bugs we bitch about, or give a **** about.

---

### Post by amphoterous on 2007-10-20
Well it's not just Nvidia, since I have an ATI video card. I do agree though that it should be more than just a "wishlist" status.

---

### Post by deez on 2007-10-20
Same for me

HP Nc4010 and an ati card.  

Do y'all have any problems with laptop-mode.  I can't seem to get my enabled.  Cheers

---

### Post by Jaxilian on 2007-10-21
WOW! So basically everyone has this problem then?! That's not very nice to release Ubuntu with that bug. A lot of people use the suspend/hibernate function....if they have laptops that is. (like myself)

Do we have any official answer from Ubuntu team?

---

### Post by stringbean82 on 2007-10-21
Doesn't matter if it is ATI or Nvidia, I have an Intel chipset for my video inside my laptop. :-k

---

### Post by Lil on 2007-10-21
Not wishing to come across negatively but there have been a couple of right howlers bug wise introduced with Gutsy. One being the splash screen not appearing and boot apparently freezing until you strike Alt + F1 or similar because Usplash has been configured it appears for 1280x1024 which an XGA LCD cannot display. And this one, I've heard of a few other ThinkPad users with this issue as they use the fglrx driver which Gutsy flashes up saying "Hey, install me for..."

At the moment whilst I love the inclusion of Xorg 7.3 and XrandR 1.2, the new print subsystem and a few other Gutsy features; I do think 2-3 critical bugs have been left in place to gett Gutsy out in time; and I'm not saying this to be nasty to the hard work so many people have done; I just think these things should have been fixed. Hopefully a revised ISO of 7.10 will be pushed through when these biggies are fixed. My money is therefore on saying that 7.04 was a more stable release at launch.

Imagine if Microsoft or Apple did the same with their operating systems? The haters would be all over them like a swarm of flies decrying their ineptitude. There is so much to like about Gutsy and so much to really rave over; but when big regressions like this make it through... :(

Unfortunate thing is I've tested Gutsy through Tribe, Beta and Release Candidate stages and at no point did the boot splash issue creep in until the final version...

---

### Post by jsully1 on 2007-10-21
No luck getting it to suspend here, I've tried whitelisting fglrx and applying a few other tweaks I used with Feisty.  I've also passed acpi_sleep=s3_bios to the kernel in grub - the screen shuts off but then the sleep light just flashes indefinitely.

---

### Post by amphoterous on 2007-10-21
> **jsully1 said:**
> No luck getting it to suspend here, I've tried whitelisting fglrx and applying a few other tweaks I used with Feisty.  I've also passed acpi_sleep=s3_bios to the kernel in grub - the screen shuts off but then the sleep light just flashes indefinitely.

Does your laptop wake up after it goes to sleep? I know that when using Windows and my laptop goes to sleep, the sleep light flashes.

---

### Post by El Chupacabras on 2007-10-21
I you're using compiz, you might want to turn off the Sync to VBlank option. 
That's what fixed it in my case.

---

### Post by Niels Olson on 2007-10-21
If you loaded Gutsy on your Dell 820, loaded the nvidia driver, and were then wowed by the beauty but then devastated when suspend didn't work on your laptop, pretty much making the most beautiful operating system ever absolutely useless on a practical level, like [Tomas Restrepo]("http://www.winterdom.com/weblog/2007/10/19/HelloGutsy.aspx") and I were, then you'll want to check out these [modifications of xorg.conf and acpi-support from Geoffroy Carrier]("http://koon.fr/wiki/suspend_to_ram_on_the_dell_d820_proprietary_nvidia_drivers_under_ubuntu_gutsy"), a fine french fellow. Similar directions are posted for the thinkpad  T61 if you read through this [bug report]("http://https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/139089").

---

### Post by mtierney on 2007-10-22
> **El Chupacabras said:**
> I you're using compiz, you might want to turn off the Sync to VBlank option. 
That's what fixed it in my case.

I'm using a Lenovo T60 and haven't been able to make sleep or hibernate work with Gutsy yet. Based on other BB posts, it seems like your solution seems to be the most popular work around; however, I'm not sure where to change the SyncToVBlank option -- could you point out how I change this?

Thank you!

---

### Post by Lord_Dicranius on 2007-10-22
My system: Gateway MX7525 w/ ATI Mobility Radeon X600

I've had problems with my laptop suspending/hibernating too.  I had this problem back in tribe, so I just disabled it from going into suspend/hibernate mode in the Power Management window.  But somewhere along the way I reverted to the basic display driver (not the fglrx).  But just the other day I noticed my desktop effects weren't there anymore.  So I started up the Restricted Driver Manager and enabled the ATI driver, and that's when my problem started up again.  Suspend/hibernate are still disabled, but my screen will go black after a bit, or when I close my laptop lid.  It's not everytime, but most of the time after awhile I'll come back to it and my caps lock light at the bottom of the toucpad will be blinking, and that's when I know I won't be able to wake it up.  I have to push/hold the power button to power it down, then power it back up to get back into the desktop.

> I'm not sure where to change the SyncToVBlank option -- could you point out how I change this?
I found this option after opening Syste>Preferences>Advanced Desktop Effects Settings, then clicking on "General Options" at the top, then on the "Display Settings" tab you'll find the "Sync to VBlank" option there.  I checked mine to see if I could disable it, and mine was already unchecked.

**UPDATE**
Also, in the [7.10 release notes](http://www.ubuntu.com/getubuntu/releasenotes/710), there's a bit about ATI hardware and blank screens:
> 
**Blank screen with some ATI hardware**
    *People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf. [Bug #132716](https://bugs.launchpad.net/bugs/132716)

I read the notes on the bug page and it sounds like that's just for those with issues when trying to start X?  Did I read that correct?

---

### Post by kamitsukai on 2007-10-22
same using ati.....

---

### Post by mtierney on 2007-10-22
> **Lord_Dicranius said:**
> 

I found this option after opening Syste>Preferences>Advanced Desktop Effects Settings, then clicking on "General Options" at the top, then on the "Display Settings" tab you'll find the "Sync to VBlank" option there.  I checked mine to see if I could disable it, and mine was already unchecked.

**UPDATE**
Also, in the [7.10 release notes](http://www.ubuntu.com/getubuntu/releasenotes/710), there's a bit about ATI hardware and blank screens:

Blank screen with some ATI hardware
*People with ATI display adapters may get a blank screen when loading X due to the driver being unable to initialize certain hardware. Upstream is working on it, and hopefully we'll be able to release an update for 7.10 soon after the release. In the meantime, add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf.



I'm not exactly sure where in the xorg.conf file to add the suggested line. I tried doing it in the fglrx driver section, but this did not resolve my gutsy's inability to sleep =/

Does anyone have a precise location suggestion for the xorg.conf edit?

Thanks =)

---

### Post by Lord_Dicranius on 2007-10-22
> **mtierney said:**
> I'm not exactly sure where in the xorg.conf file to add the suggested line. I tried doing it in the fglrx driver section, but this did not resolve my gutsy's inability to sleep =/

Does anyone have a precise location suggestion for the xorg.conf edit?

Thanks =)
I believe that's the correct location in the xorg.conf file to put that.  But that's why I was asking the question there at the end: if that fix is just for ppl who aren't able to load X at all (upon bootup).  I think that it is only for those who can't bootup X, so I don't think it'd be a fix for those of us with suspend/hibernate issues.

---

### Post by mtierney on 2007-10-23
Aw shucks... =(

Yeah, not a fix for a Lenovo T60.

(( Does anyone have a solution? ))

---

### Post by emodro on 2007-10-23
well i had a similar problem in feisty and then i followed this guide [http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)   and everything worked great, it uses uswsusp. i tried it in gutsy with no luck because the version has changed... they don't have s2ram anymore, only s2disk and s2both (which is suspend to ram but it also makes an image so if your battery dies you are not sunk) i however have had little luck, i even tried installing the feisty version of uswsusp and nothing really happened either; however maybe this is motivation for one of you all to try it out and find something that works

---

### Post by Lambert on 2007-10-23
Networkmanager seemed to be my problem. I uninstalled it and suspend/sleep now works for me. The only hitch I have is the top panel has a weird graphical line under it when brought back up.

This is on an ibm thinkpad r50p.

---

### Post by amphoterous on 2007-10-23
Well I'm not too sure that I want to lose networking functionality to regain sleep. I'm pretty sure laptop user requires both functions. Can networking be disabled before going to sleep or something else that doesn't require uninstalling important software?

However, nice find and hopefully we'll figure out a better solution.

---

### Post by Lambert on 2007-10-24
> **amphoterous said:**
> Well I'm not too sure that I want to lose networking functionality to regain sleep. I'm pretty sure laptop user requires both functions. Can networking be disabled before going to sleep or something else that doesn't require uninstalling important software?

However, nice find and hopefully we'll figure out a better solution.

You don't lose network function by removing network manager. It's just a gui to control connections, I still had full control/connection using command line. 

I've installed wicd as a a replacement gui and that's working fine for me. The lines on resume were due to compiz. I removed the desktop effects and everything seems to be working fine for me now (except printing to my canon mp610 :( )

---

### Post by mtierney on 2007-10-24
Unfortunately, uninstalling the network-manager does not as a solution on the T60 =( 

:: sadness :: (How can we suspend Ubuntu?)

---

### Post by #Reistlehr- on 2007-10-24
try addding

nosmp 

to the boot line.

---

### Post by amphoterous on 2007-10-24
Uninstalling network-manager did not work for me either. My laptop will still go to sleep but is unable to wake up.

---

### Post by #Reistlehr- on 2007-10-24
These two threads are almost the exact same:

Perhaps we can merge to one of the threads to keep it less disorganized?
[http://ubuntuforums.org/showthread.php?t=588239&page=4](http://ubuntuforums.org/showthread.php?t=588239&page=4)

---

### Post by amphoterous on 2007-10-24
Maybe a moderator could lock this thread and point to the other one?

---

### Post by Jaxilian on 2007-11-03
Suspend/Hibernate still doesn't work. Anyone know any status on this or do we have to wait until Ubuntu 8.04?

---

### Post by jeremija on 2007-11-19
i have a t60p with an ati firegl v5250 and suspend doesn't work after upgrading from fiesty to gutsy (64-bit version).
the screen just goes blank and the moon-like light under the display just flashes and i have to manually restart the pc :(

---

### Post by technikalKP on 2007-11-19
Same problem here.  Dell Inspiron 700m with integrated intel graphics.  Occasionally, seeming randomly, the machine will lock up when attempting to suspend to ram.  The machine will act like it's suspending, turn off the screen, then just completely lock up.  I did not have this issue with 7.04.  i've tried all kinds of changes, and nothing seems to fix it.

---

### Post by Donalbain on 2007-11-19
Same here for Lenevo Thinkpad Z60t (Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)). 

Also: It's not possible anymore to switch between internal/both/external monitor.

Feisty was so much better, i think, I'll have to downgrade. Shame...

Jörg

---

### Post by ltorgo on 2007-11-19
> **Donalbain said:**
> Same here for Lenevo Thinkpad Z60t (Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)). 

Also: It's not possible anymore to switch between internal/both/external monitor.

Feisty was so much better, i think, I'll have to downgrade. Shame...

Jörg

I have the same problem and I agree it is a shame... :-( this sounds to look like the Vista -> XP must downgrade path ;-)

I've a Vaio TZ21XN/B (C2D U7600, 1.2GHz, 2Gm, 100 Gb 4200rpm, Intel 945GM/GMS), and it really annoys me not having suspend and being able to switch with Fn+F7 between the laptop LCD and a LCD projector without having to reboot. These are two musts for me in terms of using a laptop. Hibernate I can leave without as this beautiful machine has incredible battery life. On top of that I don't have sound... not easy to stay on Gutsy... I think I'll have a try with Feisty but if things are the same I'll have to go back and  install Windows on this machine, and I REALLY WOULDN'T LIKE TO DO THAT! 

Help/hints is/are most welcome,
Luis

---

### Post by jeremija on 2007-11-20
> **jeremija said:**
> i have a t60p with an ati firegl v5250 and suspend doesn't work after upgrading from fiesty to gutsy (64-bit version).
the screen just goes blank and the moon-like light under the display just flashes and i have to manually restart the pc :(

update: i managed to make the pc go to standby, by disabling the ati graphics driver in restricted drivers manager (i think that it uses fglrx)... after enabling it, it doesn't work...
i read somewhere that this is because of a bug in the driver...
is there some kind of workaraund for this problem? :(

EDIT: i just saw this [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Attention:_Suspend.2FHibernation_will_not_work")
"The problem has been solved in the AMD Catalyst 7.11 driver release (fully supporting the 2.6.23 and the SLUB allocator kernel)"
did anyone manage to get this work with these new drivers?

---

### Post by tux2005 on 2007-11-26
> **jeremija said:**
> update: i managed to make the pc go to standby, by disabling the ati graphics driver in restricted drivers manager (i think that it uses fglrx)... after enabling it, it doesn't work...
i read somewhere that this is because of a bug in the driver...
is there some kind of workaraund for this problem? :(

EDIT: i just saw this [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Attention:_Suspend.2FHibernation_will_not_work")
"The problem has been solved in the AMD Catalyst 7.11 driver release (fully supporting the 2.6.23 and the SLUB allocator kernel)"
did anyone manage to get this work with these new drivers?

I just tried the AMD Catalyst 7.11 driver with my Lenovo T60, ATI Mobility Radeon X1400, no luck on sleep support. It starts to go into sleep mode but crashes once the display turns off and keyboard input stops working (caps lock does not light up). 

uname -r:
2.6.22-14-generic

:(

---

### Post by Jaxilian on 2007-11-27
Oh my god! This problem still remains? I moved to another distro cause of this problem. If Suspend/Hibernate isn't working on a laptop it isn't worth running.

I hope Ubuntu team will look into this soon, but I think nothing will happen until 8.04 comes out next year. It doesn't seem like Laptops are a priority nowadays :confused:

---

### Post by jsully1 on 2007-11-27
Same problem here, T60 with an ATi X1300.  I'm a sad panda :(

---

### Post by Tomas_IV on 2007-11-27
**Today it started working with old kernel!**
I have Compaq Presario V5105 with Ati Radeon XPRESS 200m, I'm using the restricted X video driver (fglrx)  and 32bit system. After upgrade to Gutsy the suspend stopped working for me the same way as for many others. I have kept older kernel after upgrade, so now I have possibility to choose from the old kernel or the latest one in grub. Suspend had not worked with either of the kernels since now, but I have kept the older one, because I have text consoles with it, unlike with the latest one. I tried several things like using the open source nv driver, uninstalling networkmanager, tweaking acpi scripts, but nothing worked.
Today I tried some tips from this thread and other sources (noapic option and killing network manager) and it seemed to work, but finally I found it works regardless of these changes (out of the box), but only with the older kernel. Probably some recent update helped.
So try to install kernel 2.6.20-16-generic from Feisty to try if it helps also for you.
The easiest way is probably to search for the string 2.6.20-16-generic in first search form on page  [http://packages.ubuntu.com/#search_packages](http://packages.ubuntu.com/#search_packages) and install linux-image-2.6.20-16-generic and linux-restricted-modules-2.6.20 by clicking on links to the packages in Firefox. Do not forget to select search in Feisty.
So suspend to RAM works for me now and it seems to be even faster than in Feisty. I did not tried hibernating so far (it did not work even in Feisty), I have to go to sleep **myself** ;)...

---

### Post by defenestratos on 2007-11-28
Got a similar problem on my benq joybook. Stats below. I had it before Gutsy though. Ever since Dapper when I migrated. I close the lid to suspend and on opening it and touching a couple of keys I am prompted to give my password. The problem is my keyboard is about half the time locked and I need to reboot.

---

### Post by Tomas_IV on 2007-11-29
Just to specify more details to my previous post. The suspend to RAM and wake-up now works for me in Gutsy with Feisty kernel, though sound is off afterwards. 
This:
```
sudo /etc/init.d/alsa-utils restart
```
restores the sound to working state. I have to tweak the acpi scripts to restart alsa and I should be fine then. 
Hibernate does not works. The computer seems to hibernate OK, but when switched-up again it starts to normal login screen, not restoring previous state. This is the same behavior I experienced in Feisty.

---

### Post by hardran3 on 2007-11-29
I have been having the sleep problem as well. It would resume, but lock up the screen and keyboard ~30 seconds after boot. Upon reading my logs I noticed ntpd was always the last thing in the logs. I added ntp as a service to stop and restart under /etc/default/acpi-support, and I have done about 50 suspend-resume cycles with no lockups. :guitar:

```
# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="ntp"
```

---

### Post by MariusSilverwolf on 2007-11-29
I'm using a work-issued HP/Compaq nc6000.  Every attempt following every guide and every software package failed to enable a working Suspend or Hibernate mode.  The closest I came was starting to Suspend to RAM then immediately resuming and holding at that state.

So ran a clean install of Feisty.  Works just fine now.  ^_^

---

### Post by tux2005 on 2007-12-25
With the recently released AMD Catalyst 7.12 drivers my Lenovo T60 now suspends and resumes without problems :)

---

### Post by scotartt on 2008-01-09
> **Niels Olson said:**
> If you loaded Gutsy on your Dell 820, loaded the nvidia driver, and were then wowed by the beauty but then devastated when suspend didn't work on your laptop, pretty much making the most beautiful operating system ever absolutely useless on a practical level, like [Tomas Restrepo]("http://www.winterdom.com/weblog/2007/10/19/HelloGutsy.aspx") and I were, then you'll want to check out these [modifications of xorg.conf and acpi-support from Geoffroy Carrier]("http://koon.fr/wiki/suspend_to_ram_on_the_dell_d820_proprietary_nvidia_drivers_under_ubuntu_gutsy"), a fine french fellow. Similar directions are posted for the thinkpad  T61 if you read through this [bug report]("http://https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/139089").


Yes hello, I've got a Dell Inspiron 8500, about 2003 vintage. It has an "nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]" graphics card which has always given me issues with wake-from-sleep with nearly every Ubuntu distro version I tried (7.10 was the first 7.x release I had installed) with either driver (proprietry or not). However doing exactly as described in the page above seems to to cure it for the nvidia proprietry driver. 

Kudos to Tomas.

thanks
scot

---

### Post by Thyzer on 2008-01-09
> **sixstorm said:**
> I have a Compaq C714NR and when I close the lid, the screen turns off but the computer is still running.  Hopefully there will be a patch/fix for that soon!  I'd like to keep Ubuntu up and not have to turn it off/switch back to Vista.

Does it lock up or does it return to normal if you move the mouse or touch the touchpad? Because if you go to power management you can change the setting for what happens when you close the lid.

For my own problems, I have the same problem on my Dell Inspiron 1521. If I hit suspend or hibernate the screen goes black, but the power light stays on, and nothing will make it come back, so I just have to hold down the power button. However, this was not the case when I first installed Ubuntu. When I first installed it, it worked fine. However, when I first installed Ubuntu, my graphics driver and wireless driver weren't functioning because since I was not hooked to the internet none of the items on the source list were verified and so they were all commented. After uncommenting them and downloading the 200 some odd updates, which fixed my graphics card and wireless (not my sound though still working on that :( haha), I came across this problem.

As for it having do with Compiz, if Compiz is what I think it is (the advanced desktop effects? correct me if i'm wrong), then it isn't that because I just installed that a few minutes ago, and I've been having this problem for a couple days (I installed Ubuntu on Monday, I believe) It may have something to do with the graphics card, or driver, I think I'm going to try deactivating the driver and see if it fixed the problem, just so we can get a lead on it.

---

