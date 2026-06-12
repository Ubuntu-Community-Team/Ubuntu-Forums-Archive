---
title: "Intrepid won't restart or shut down..."
date: 2008-11-01
forum: Hardware
---

### Post by mtylerb on 2008-11-01
I am having troubles with my newly upgraded 8.10 Ubuntu distro.

I upgraded from 8.04LTS last night and now when I shut down or restart, it hangs at a black screen and the shutdown/restart never happens.

Any ideas?  I'm not sure how to troubleshoot this.

---

### Post by mtylerb on 2008-11-01
Anyone?

---

### Post by npsken on 2008-11-01
I'm actually having the same problem. Except ever since I installed the nvidia drivers I've been getting a white-noise screen instead of a black screen.

---

### Post by rhcm123 on 2008-11-01
try shutting down from a shell prompt:
```
sudo shutdown -P now
```

---

### Post by Jerk1 on 2008-11-04
I have upgraded 2 Ubuntu machines to 8.1 at this point, a tower and a laptop, and the tower will not shut down correctly or restart, whenever I try to do either I get the Ubuntu log out and power off screen, then it just goes to acpid:exiting and hangs, I have to manually hold down the power button for 5 seconds. Initially I was getting the same results from the laptop as well, but after a few restarts, the issue seems to have resolved itself. Never had this problem with 8.04.

---

### Post by SLA_leandrin on 2008-11-04
Same problem here, computer not shuting down... not even with the command sudo shutdown -P now

---

### Post by talkin on 2008-11-05
> **Jerk1 said:**
> ... power off screen, then it just goes to **acpid:exiting** and hangs, I have to manually hold down the power button ...

The same happens for my laptop. Booting with **pci=noacpi** didn't help.
Any solutions?

---

### Post by aaronLund on 2008-11-08
I'm having the same issue after upgrading from 8.04 Ubuntu Studio to 8.10.


I'm thinking it has something to do with Nvidia video drivers as my newly upgraded 8.10 machine first tells me that it couldn't find the drivers.  Then, if I go in and edit xorg.conf to list the Nvidia driver as "nv" as opposed to "nvidia" it would boot correctly.


Anyone know why I have to do that ^^?


I cannot, however, get 3d effects on this now. Didn't have that problem with 8.04.

---

### Post by Jerk1 on 2008-11-16
I've been updating regularly on both of my machines running 8.1 and no change, still shutting down the system, but the machine remains on with simply a black screen and a cursor in the upper left corner. I see some people suspect an Nvidia driver or .xorg issue, both of my machines have Nvidia cards and they are both workstation or borderline workstation caliber machines (I am a 3d artist, I use these machines for work quite often, I need this kind of bugginess to go away as soon as possible)

---

### Post by Jerk1 on 2008-11-16
correction: half of the time when I shut down, the system exits and then I just get acpid: exiting in the upper left corner, and the other half of the time I get a cursor

---

### Post by redmilkvan on 2008-11-17
I have an Asus V3-M2NC61S that after an upgrade to 8.10 experienced the same issue during  a shutdown or reboot. acpid: exiting. It would sit there and not shutdown or reboot.
After much reading a poking around, I decided to look at the bios level.
Asus had updated the bios.
The upgraded bios fixed the issue.

hth

---

### Post by Jerk1 on 2008-11-18
Thanks for the suggestion, but both of these machines have had their bios flashed recently, so I doubt that is the issue

---

### Post by rhcm123 on 2008-11-19
try this command, a more, shall we phrase it, blunt :) shutdown command:
```
sudo halt
```
That should do it.

---

### Post by OzzyFrank on 2008-11-21
For you guys who can get a Shutdown button but can't actually shutdown, have you tried Ctrl+Alt+Backspace? Coz until I upgraded to 8.10 today, when shutting down I would only get as far as panels and icons etc disappearing (leaving the desktop wallpaper) and the exit sound (which let me know it was OK for the key combo). After that, it would just continue to shut down or reboot, not take me to the login window (which would happen if I Ctrl+Alt+Backspace while still in a session).

Now to find how to get all the options back for logging out! And this has happened to me before... and to many others... in many versions... so I kinda wish they would factor this in when creating new versions! (Just a tad annoying!).

---

### Post by OzzyFrank on 2008-11-21
OK, what seems to be happening is that there is now actually a **Log Out** button and a **Shut Down** one... and (don't ask me why) it seems the default button is now the former rather than the latter, as it should be. This is EASILY fixed, not like when this happened in other versions (had to manually fix it or wait for an update).

Right-click your panel, choose **+Add To Panel**, scroll down till you find "**[COLOR="Red"]Shut Down...[/COLOR]**" and drag that to your panel. You can then delete the logout one, though note that the shutdown one no longer has options for switching user (ie: just logging out to the login screen)... for those who find that a problem: keep both buttons; for the rest of you: if you ever need to log out only, do it from the System menu (no big deal really for most of us).

Hope this helps! Cheers.

---

### Post by Jerk1 on 2008-11-22
nice idea, but that is just swapping around icons, the problem is that the machines just do not shut down, the system logs off and shuts down, but the power to the drive and display remain on. I have to hold the power button for both machines down for 5-6 seconds to force them to power down completely.

---

### Post by OzzyFrank on 2008-11-22
> **Jerk1 said:**
> nice idea, but that is just swapping around icons, the problem is that the machines just do not shut down, the system logs off and shuts down, but the power to the drive and display remain on. I have to hold the power button for both machines down for 5-6 seconds to force them to power down completely.

I thought it was obvious that info was for those who had lost the Shutdown option and could only log out. Sorry I can't help those with a Shutdown button but no ability to do so... I thought I may as well help those who just lost their Shutdown/Restart buttons, as they will no doubt end up at this page because of the title.

---

### Post by Jerk1 on 2008-11-22
thanks anyhow, tho. Very strange, I can't log off user and reboot only seems to work 1 out of 3-5 times, very annoying, I would do a clean install, but it is the same with my tower AND my laptop, so I really don't think they BOTH have corrupted systems, they were just clean installs less than a month ago

---

### Post by OzzyFrank on 2008-11-22
Cripes! Don't do a fresh install or anything that drastic (yet)... wait and see if a fix pops up. Or an update fixes it. But yeah, that's a strange error - coz you can in fact "shutdown" as such, but the power stays on! At least it seems to shut down OK, meaning the OS itself has shutdown gracefully so no errors every time you boot up. I would say as long as that is all OK, then holding the button for 5 secs is a small price to pay (I've had Windows systems that were supposed to power off all the way but I had to do the same).

As for you guys who can partially shutdown, do try Ctrl+Alt+Backspace, since many don't know that can help the shutdown or restart process to continue.

---

### Post by OzzyFrank on 2008-11-22
> **Jerk1 said:**
> thanks anyhow, tho. Very strange, I can't log off user and reboot only seems to work 1 out of 3-5 times, very annoying, I would do a clean install, but it is the same with my tower AND my laptop, so I really don't think they BOTH have corrupted systems, they were just clean installs less than a month ago

Agreed it is weird it is happening on both systems! Is there something special/somewhat-iffy that you set up on both systems that could be helping this to happen?

I wish I could just blame Intrepid, but for me it actually fixed me having to Ctrl+Alt+Backspace my way out of each session.

---

### Post by peakpc on 2008-11-22
I have noted this same problem on my compaq laptop (AMD ATI) with both upgrade from 8.04 to 8.10 and fresh install of 8.10 so I just sticking with 8.04 for a while longer unless someone comes up with surefire fix. All the rest of 8.10 seem good stuff.

---

### Post by NiBu on 2008-12-01
Is there a bug report about this problem on launchpad? I have the problem with reboot and shutdown on two different pcs after upgrading from 8.04 to 8.10 and i know i am not the only one who has this problem. This is a really sad bug making people scream.

---

### Post by Jerk1 on 2008-12-01
not sure if this is reported on launchpad, but yes, it is a sad bug

---

### Post by mitchellcipriano on 2008-12-01
I have a similar problem now as well. I had my system, ThinkPad R51, working fine under 8.10. Then an update came two nights ago and I cannot shutdown, restart or suspend. Also my sound is gone.

---

### Post by Jerk1 on 2008-12-13
Hey there, I experienced the same sound issue with my tower and found that one of the updates, for whatever reason, had simply muted my sound in the control panel. Simply turning the sound output back on in the volume controls fixed the issue. However, unfortunately, none of the ensuing updates have resolved my logout, reboot, or shut down issues, I am still holding the power button for 5 seconds whenever I need to shut down. Please, somebody fix this. I am dying to get a new machine over the holidays and make the move to linux once and for all, but I am afraid that if both of my ubuntu boxes are having the same issue, I may need to look into another distro, which would suck, the ubuntu community is the best.

---

### Post by Jerk1 on 2008-12-13
One thing I am curious about, to any others experiencing this sort of problem out there, I am running Ubuntu studio and I wonder if perhaps that is part of the problem. It sounds like there are a few others having similar issues and I wounder if it is more typical of any of the specific different flavors of ubuntu or if they are all experiencing similar issues?

---

### Post by Triple88a on 2008-12-16
Just switched over to dual boot Ubuntu last night.  I have the exact same problem.  I saw u guys thinking it might be ur video card.. have ATI Redeon video card and the person on the other page has Nvidia.. so.. problem seems to be universal.

I get the same problem when i try to log off and switch users as well.

---

### Post by Triple88a on 2008-12-16
well after messing arround w/ this all day today i installed the updates and changed all my sounds to ALSA and the black screen problem seems to have gone away.):P

---

### Post by StudioDave on 2008-12-17
I have an HP G60-125NR notebook running Ubuntu 8.10. Generally I like the system, but I have spent in inordinate amount of time resolving difficulties with it, the latest of which is this incredibly annoying shutdown problem. If I use the logout command once to close an xterm it destabilizes the entire system. At that point I have to hold the power button down on the machine to get out of the corrupted system.

Btw, this machine includes an nVidia 8200M GPU. I've installed the proprietary driver via the Hardware Manager.

I am determined to resolve this issue. I've tried all the posted solutions, none work. I also have the Shutdown problem, i.e. it doesn't work either, the system just stops after the "Will now halt" message. I've been using ctrl-alt-del at that point so I can reboot into recovery mode and shut down the machine cleanly.

So what do the devs want/need from me and my machine to work towards a resolution ? I've applied all the official updates, but I'll try anything else to get a clean logout and a working shutdown.

---

### Post by Triple88a on 2008-12-17
Did you install the updates?  Also what sound settings are you using?  I have confirmed that my computer shuts down now with no problems.

---

### Post by Ng Oon-Ee on 2008-12-17
> **StudioDave said:**
> I have an HP G60-125NR notebook running Ubuntu 8.10. Generally I like the system, but I have spent in inordinate amount of time resolving difficulties with it, the latest of which is this incredibly annoying shutdown problem. If I use the logout command once to close an xterm it destabilizes the entire system. At that point I have to hold the power button down on the machine to get out of the corrupted system.

Btw, this machine includes an nVidia 8200M GPU. I've installed the proprietary driver via the Hardware Manager.

I am determined to resolve this issue. I've tried all the posted solutions, none work. I also have the Shutdown problem, i.e. it doesn't work either, the system just stops after the "Will now halt" message. I've been using ctrl-alt-del at that point so I can reboot into recovery mode and shut down the machine cleanly.

So what do the devs want/need from me and my machine to work towards a resolution ? I've applied all the official updates, but I'll try anything else to get a clean logout and a working shutdown.
With my machine (I know its different to yours) shut down works fine IF I remember to right-click the network icon and disable networking. This is a known bug in launchpad.

Not everyone would be having issues because of that, though. There are a couple of shutdown/hibernate/suspend bugs going round that complicate matters much.

---

### Post by mtps37 on 2008-12-18
I have the same problem with my Asus F5SL, but no black Screen.

I can see the splash screen of Ubuntu while shutting down the system, but never finished.

So I change to text mode by pressing some keys (maybe ALT+6?) and I can see what is happenig: the system stops when is trying to shut down the ALSA system:

* Shutting down ALSA................

I wait for hours but anything else happens :confused:

Javi

---

### Post by Ng Oon-Ee on 2008-12-18
Ah, an ASUS F5, I'm using Asus F8, and the problem is COMPLETELY resolved just by disabling the network BEFORE shutting down. You should try that. The reason is that the shutdown routine is borked, it seems, it would shut down the network interface and then a few steps later try to disconnect from the network.

---

### Post by dcviana on 2008-12-18
Same problem here, but I have an ATI 9600 PRO videocard, so the problem is not only with nVidia cards.

My motherboard is updated with the latest BIOS, it's an old Shuttle MN31N nForce 2 based motherboard and it worked with previous versions of Ubuntu (haven't tested with 8.04).

---

### Post by dcviana on 2008-12-18
> **Ng Oon-Ee said:**
> With my machine (I know its different to yours) shut down works fine IF I remember to right-click the network icon and disable networking. This is a known bug in launchpad.

Not everyone would be having issues because of that, though. There are a couple of shutdown/hibernate/suspend bugs going round that complicate matters much.

Do you know the issue number on launchpad? I would like to take a look and see if I can contribute to something. Thanks.

---

### Post by Ng Oon-Ee on 2008-12-18
I believe it is[this bug.]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/138691") Or maybe [this bug.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/278927") Apologies, I'm not really sure which, as its been a long time since I started using this workaround.

---

### Post by Jerk1 on 2008-12-29
I finally found something that seems to work, it's an old thread, but it worked for me.   [http://ubuntuforums.org/archive/index.php/t-5193.html](http://ubuntuforums.org/archive/index.php/t-5193.html)
hopefully that will still be the case in a day or 2

---

### Post by Jerk1 on 2008-12-29
correction, the solution presented in my previous post fixed the issue for 2 whole reboots, ugh

---

### Post by benotpower on 2009-01-03
same problem!

simple question, how do you disable the splash screen on shutdown, so you can see what's causing the system to hang?

thanks!

Benoit

---

### Post by Jerk1 on 2009-01-04
since my previously posted solution does in fact work every now and then, I have noticed that, when correctly shutting down, the wifi powers down completely before the machine does, when shutdown hangs, the wifi remains on (suggesting this is wifi or network manager related?), I've run some tests disabling the network manager and this seems to fix it, but really, that just seems like cutting off your nose to spite your face, as they say. Not much of a solution if you ask me

---

### Post by jeffus_il on 2009-01-05
Don't bother, just do > ctrl-alt-F1 to a console, and type > sudo poweroff
(reply to [benotpower]("http://ubuntuforums.org/member.php?u=740877"))

---

### Post by Jerk1 on 2009-01-05
neet, another workaround, I'll put it in the pile. Sorry to be so sarcastic, but this is not a fix. This was never a problem for me in 8.04, is it really such a big deal to ask your OS to correctly shut down your machine?

---

### Post by benotpower on 2009-01-09
> **jeffus_il said:**
> Don't bother, just do  to a console, and type 
(reply to [benotpower]("http://ubuntuforums.org/member.php?u=740877"))

thanks for the tip jeffus_il... but that does not get me very far. I explain : I get the terminal, sudo power down, and the screen freezes just after the next line :

```
[337.196502] Power down
```

I have :
- Kernel 2.26.27-9 generic
- all updates I could find
- tried ACPI=force and apm tricks, no luck
- tried suspend, hibernate, shutdown, halt, poweroff... nothing works

I just don't know what else I can do :confused:

It's a shame because everything else works so fine... frustrating!

---

### Post by HDTimeshifter on 2009-01-11
It seem like whenever an update requires a reboot, my system will shutdown, but on reboot, it hangs on the startup screen with just a solid green Ubuntu progress bar.  I then have to press the hardware reboot button and my system will restart, but in low resolution.  I then have to reset my nVidia X Server settings back to 1600x1200.  I noticed that it seems after the first reboot, the X Server settings is not auto-detecting my monitor, but a 2nd reboot does.  I'm running 8.10 64-bit with latest nVidia update on an ASUS P5Q Pro, Core 2 Quad Q6600, and ASUS EN9500GT.

---

### Post by Jerk1 on 2009-01-19
the suggestion here [http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes)
seems to have done the trick for my laptop, haven't had time to try with the home tower yet

---

### Post by Jerk1 on 2009-01-19
however logout and switch user are still extremely buggy, they both hangup and just plain do not work at least 75% of the times I have tried

---

### Post by Jerk1 on 2009-01-27
OK, so, everything that has come before has been, at best a mildly successful workaround or fix that works a few times, but not after sustained use. Opening up the backports and installing the updates has actually remedied the non-shutdown and logout issues for going on 3 days now. Just sudo apt-get install linux-backports-modules-intrepid-generic

---

### Post by Jerk1 on 2009-01-27
[http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/)

---

### Post by vshailesh on 2009-02-04
This seems to happen on only certain motherboards.

adding **reboot=b** as a kernel parameter worked for me.

1. For steps to do this, see message by marcobra on 2008-03-03 at 
[https://answers.launchpad.net/ubuntu/+question/3857]("https://answers.launchpad.net/ubuntu/+question/3857")

2. For details of this **reboot=b** kernel parameter, 
read the section named **Rebooting** at
[http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt]("http://www.mjmwired.net/kernel/Documentation/x86_64/boot-options.txt")

---

### Post by HDTimeshifter on 2009-02-05
> **Jerk1 said:**
> the suggestion here [http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes)
seems to have done the trick for my laptop, haven't had time to try with the home tower yet

I did the VGA Output Resolution fix at the URL above and haven't had it freeze or go into low resolution on reboot since, however yesterday, my PC had gone into hibernation and wouldn't wake on mouse, keyboard, or reset or power switch.  I forget which hardware switch, reboot or power on made it reboot completely rather than simply wake from hibernation.

---

### Post by 123_854 on 2009-03-18
> **Jerk1 said:**
> the suggestion here [http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Shutdown_freezes_sometimes)
seems to have done the trick for my laptop, haven't had time to try with the home tower yet

  I dual-boot on a Sony Vaio with Intel WiFi card. Sometimes it restarts/powers off, sometimes it doesn't. I tried the acpi=force and it didn't do anything. 
  I noticed the light on my wifi card blinking after it froze so I changed the alsa-utils. So far it works flawlessly. Thanks for the link :)

---

