---
title: "gnome-power-manager not responding in 8.10"
date: 2008-10-30
forum: Hardware
---

### Post by nray on 2008-10-30
Hi, I have an Acer Aspire One (hard drive model) and I've been running Ubuntu 32-bit since 8.04.1, and had no trouble with gnome-power-manager there.

8.04.1 had issues with sound and wireless, and so I upgraded to 8.10 beta and sound has worked great and with the ath5k drivers in 8.10 the wireless works too, but ever since I upgraded to 8.10 beta through the release (I'm now fully up-to-date) I have issues where the gnome-power-manager stops responding for periods of time and then comes back.  The symptoms as a result of that are the power management icon in the notification area appearing and disappearing, suspend and hibernate appearing and disappearing as options, having to force close gnome-power-manager on shutdown or restart if it's in it's not responding state, etc.  I was hoping it was a bug that was known about and that the release of 8.10 would fix it, but it's still there.

Is this a known problem, or is there something else I need to do because I upgraded from 8.04.1 to 8.10 to get gnome-power-manager to work properly on my notebook?

---

### Post by shirokuro on 2008-10-30
Hi nray,

I'm having the exact same issue.  I have a Panasonic Let's Note CF-R3 (Japanese model).  This didn't happen to me on 8.04.

I had upgraded from 8.04 -> 8.10 and saw this issue - although in that case, when power manager crashed/died/hung/whatever, it did NOT come back unless I manually kill the gnome-power-manager process.

I then did a complete system wipe and clean install with 8.10 CD, but the issue reoccurs.  Sometimes it recovers by itself, and sometimes not.  When the issue occurs, the battery icon on the menubar becomes unresponsive, and when launching System->Preferences->Power Management it takes a minute or two for the control panel to appear, and when it does, the battery pane (indeed ANY mention of battery) is absent.

Also, my screen brightness seems to slowly decrease!

Everything seems stable on AC - the issues seem to be only when on battery power.  Still, it's pretty frustrating!

---

### Post by shirokuro on 2008-10-31
Well, after a couple of hours forum-hunting for solutions to this, I've come up blank, and unfortunately decided to re-scratch my system back to 8.04.

The biggest problem I have with this issue is that, likely due to the confusion it seems to have realising when there is and is not a battery, is that suspend/resume dont work.  Since I want to use my little Panasonic basically as a netbook, this is pretty much a showstopper issue for me.

I'll be sticking with 8.04 until a patch or fix for this issue is found.  I liked what I saw with 8.10, and hope to be able to try it again soon :-)

---

### Post by nray on 2008-10-31
Thanks for confirming that the problem isn't just me or my configuration... I don't think I'm going to go back to 8.04 anytime soon (the sound and wireless issues were too frustrating), and I mostly use my notebook on AC power, so I'm going to stick with 8.10 for now.

I'm thinking I should probably file a bug report though... anyone know where the best place to do that is?

---

### Post by shirokuro on 2008-10-31
Hi nray,

I'm a newbie to Ubuntu and have never filed a bug report myself.  I did I search though, and this link seems to detail the various options for filing a bug.

Hope this helps.  I should have filed a bug myself too before wiping 8.10 and going back to 8.04 :-)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by DigitalRonin on 2008-11-08
Just FYI, I'm having the same problems with my Panasonic CF-R4, also since 8.10 (8.04 was fine).

If I find a fix, I'll post here.

Cheers

David

---

### Post by thor2002ro on 2008-11-08
it seems it unresponsive fo 15-20s then responds for a while then its unresponsive again and so on .... haveing thins problem for a while now ... bun its not that anoying...

---

### Post by AllBuntu on 2008-11-08
I have a get-around for you guys,

after requesting suspend or hibernate and nothing happens,

launch Preferences > Power Management
this is going to take anywhere from 30 seconds to 3 minutes
(do it once, it will take for ever for the window to actually show up)
at the time that window finally comes up, the suspend/hibernate moment has arrived and will execute as will any queued-up requests
(gnome-power-manager is periodically blocking in the background on something)

If you otherwise try suspend/hibernate and what not, commands queue up for when gnome-power-manager is finally available, such as when you do shut down. on wake-up it will execute the plenty hibernate or suspend you ordered a long time ago 

AspireOne uses some skunk-work power set-up that's likely why this does not work very well

sometimes wi-fi is not working on resume from suspend, symptom:
sudo ifconfig wlan0 up
gives you an error message, and no networks are found
I think hibernate-resume takes care of it, or at least a system restart

---

### Post by alex42 on 2008-11-10
I've written a bug report:

[https://bugs.launchpad.net/bugs/296451]("https://bugs.launchpad.net/bugs/296451")

---

### Post by ether1231 on 2008-11-11
I've just installed Ubuntu 8.10 on my Sony Vaio VGN-NR110E and encountered the same issue as you guys, but I think I may have found a temporary fix.

When I unchecked "Reduce backlight brightness" and "Dim display when idle" under the battery tab in the Power Management Preferences the g-p-m does not appear to stop responding anymore.

You'll need to set the backlight brightness manually by doing it this way for now, but it should do the trick until a permanent solution is found.

---

### Post by nray on 2008-11-12
> **ether1231 said:**
> I've just installed Ubuntu 8.10 on my Sony Vaio VGN-NR110E and encountered the same issue as you guys, but I think I may have found a temporary fix.

When I unchecked "Reduce backlight brightness" and "Dim display when idle" under the battery tab in the Power Management Preferences the g-p-m does not appear to stop responding anymore.

You'll need to set the backlight brightness manually by doing it this way for now, but it should do the trick until a permanent solution is found.

I just tried it, and yes, it looks like gnome-power-manager is no longer hanging.  Thanks!

I can't remember when I customized the settings for backlight brightness and display dimming, but it was around the time I installed 8.10, so it's possible that this bug in gnome-power-manager predates 8.10.

I'm just happy to have gnome-power-manager responsive again!

---

### Post by DigitalRonin on 2008-11-16
> When I unchecked "Reduce backlight brightness" and "Dim display when idle" under the battery tab in the Power Management Preferences the g-p-m does not appear to stop responding anymore.
Brilliant! That worked for me too. Many thanks.

---

### Post by barrangatan on 2008-11-24
Just to say that I was also having the same issue with my 8.10 install on a Latitude D410 laptop.  Some of the symptoms are the same as what had been reported thus far:

- When on battery power, the brightness of the LCD screen seems to dim on its own even when not idle;
- gnome-power-manager stops responding, or very slow in responding.  Typically, this will mean a 15-20 seconds delay in popping up the Shutdown/Suspend options window after pressing the Power button. Or, the same delay after selecting Shutdown from either the Main Menu or the User Panel Plugin
- Also, when gnome-power-manager hangs or slows in responding, right-clicking on the Battery Plugin Icon in the Gnome Panel also does nothing
- My initial workaround was to kill the gnome-power-manager process using 'killall' from the commandline, then start Power Management from the System Menu.  
- I've just turned off screen-dimming for both AC and Battery Power and will see if the issue goes away for me, as it did for others. 

There is clearly an issue with gnome-power-manager in this build and I hope the bug will receive some attention in the near future. 

Thanks.

~ Barrangatan

---

### Post by MonsterDigital on 2008-11-28
> **ether1231 said:**
> When I unchecked "Reduce backlight brightness" and "Dim display when idle" under the battery tab in the Power Management Preferences the g-p-m does not appear to stop responding anymore.


First, Excuse me for may english, is really bad... 

Anyway, I just only say Thank you very much... this is the solution perfectly for me, buy I hope that this problem (bug) will be fixed...
Thanks, and see you later.

NOTE: If anybody can correct my english, is welcome...

---

### Post by necronwarrior on 2008-12-02
I recently installed Ubuntu 8.10 as a fresh install on my Lenovo R61 Thinkpad and I am having the same problem.
1.After running the computer for about two hours the gnome power manager stops responding.n the power management window.
2. No battery icon is displayed in the notification area.
3.I cannot adjust the display brightness.
4.There is no "On Battery" tab in the power managment dialogue box.
3. when I shut down it displays a "Gnome Power Manager Not Responding" dialogue box before logging out.
4.When the Ubuntu boot screen is displayed the shut down process hangs at about 70%.I have to press the power button for 10 secs. to switch off.

I Have Already Tried The Above mentioned Solutions!!

---

### Post by jsully1 on 2008-12-18
> **ether1231 said:**
> I've just installed Ubuntu 8.10 on my Sony Vaio VGN-NR110E and encountered the same issue as you guys, but I think I may have found a temporary fix.

When I unchecked "Reduce backlight brightness" and "Dim display when idle" under the battery tab in the Power Management Preferences the g-p-m does not appear to stop responding anymore.

You'll need to set the backlight brightness manually by doing it this way for now, but it should do the trick until a permanent solution is found.

Thanks so much for finding this - you're a lifesaver!

---

### Post by Freq18Hz on 2008-12-29
I am having the same exact issue....

After setting my screen to dim with the slider, and changing the time until my monitor shuts off, now power management hangs consitently and the battery meter dissapears.

What is more frustrating is that everytime I login (even after a cold boot) my screen starts to slowly dim, until it is completely black.

I am unable to change the screen dimming options, because when I finally am able to launch the power management window, the options I need to change are not displayed/populated in the window.  


Any help would be greatly appreciated...

-Freq

---

### Post by dilidon on 2009-01-04
> **necronwarrior said:**
> 
4.There is no "On Battery" tab in the power managment dialogue box.
3. when I shut down it displays a "Gnome Power Manager Not Responding" dialogue box before logging out.

Edited: found a solution to Freq18Hz-s 4th problem, and that of mine.
Once I manually edited the settings for gnome-power-manager to not dim the screen on battery power via gconf-editor the "On battery" tab magically reappeared after a restart, and also the power problems are gone as the fix of this thread suggests.
gconf-editor : /apps/gnome-power-manager/backlight -> uncheck battery_reduce
--
Have you found a way to access the "on battery" settings yet to try out some of the solutions mentioned above?

I upgraded from 8.04 to 8.10 yesterday in the hope that hibernation would start working (read some hints here and there suggesting that could be the case). Instead, I now have the exact same symptoms as you on my Acer Aspire One 150. In addition the power button has stopped working, and I cannot even suspend the computer.:P

---

### Post by nw@pS on 2009-01-16
> **ether1231 said:**
> 
When I unchecked "Reduce backlight brightness" and "Dim display when idle" under the battery tab in the Power Management Preferences the g-p-m does not appear to stop responding anymore.


Absolute champ! Works for me too. I installed 8.10 Intrepid on my Dell Mini Inspiron 9 yesterday and couldn't figure out why the g-p-m was being difficult. Painlful bug but I guess I can do without dimming for now.

FWIW, I had some issues unchecking 'Reduce backlight brightness' the first time: gpm hung and I had to open it from the System menu (and wait about 20 secs). After a reboot it hadn't actually changed even though I know I unchecked it. I repeated the process and this time it stuck. Appears to be doing fine now.

Ta!

---

### Post by LoSt180 on 2009-01-17
I've got the same problems with 8.10 on my Aspire One as well. Clean install of 8.10, using the netbook remix theme. Glad I found this thread. My symptoms were pretty much the same as necronwarrior's.

1.The gnome power manager stops responding in the power management window.
2. No battery icon is displayed in the notification area.
3.I cannot adjust the display brightness.
4.There is no "On Battery" tab in the power managment dialogue box.
5. When I click the Quit icon, nothing responds for up to 2 minutes before the Logout/Shutdown dialogue box pops up (I can't open anything during this freeze time, firefox, etc)
6. when it does shut down it displays a "Gnome Power Manager Not Responding" dialogue box before logging out.

I just set the battery settings as recommended above, so we'll see if it fixes the problem. But this happens while on AC power sometimes as well.

---

### Post by meistercobbman on 2009-01-17
I have an IBM LENOVO R61 THINKPAD. The hardware works great in Ubuntu. I love it. The laptop may not look as sleek or as sexy as some other manufactures, but the hardware is SOLID, and COMPATIBLE with Ubuntu (Including the power management daemon). If you are thinking of buying a new Laptop, go Lenovo. (I used to have ASUS but it took me a long time before I got all the little stuff working in Ubuntu, whereas with my Lenovo I'm up and running right away :)

---

### Post by tjeremiah on 2009-02-03
> **LoSt180 said:**
> I've got the same problems with 8.10 on my Aspire One as well. Clean install of 8.10, using the netbook remix theme. Glad I found this thread. My symptoms were pretty much the same as necronwarrior's.

1.The gnome power manager stops responding in the power management window.
2. No battery icon is displayed in the notification area.
3.I cannot adjust the display brightness.
4.There is no "On Battery" tab in the power managment dialogue box.
5. When I click the Quit icon, nothing responds for up to 2 minutes before the Logout/Shutdown dialogue box pops up (I can't open anything during this freeze time, firefox, etc)
6. when it does shut down it displays a "Gnome Power Manager Not Responding" dialogue box before logging out.

I just set the battery settings as recommended above, so we'll see if it fixes the problem. But this happens while on AC power sometimes as well.

same. Only difference is that im using a SonyVaio.

---

### Post by txapelgorri on 2009-02-14
Hi:

I have an Acer Aspire One too (ZG5, 120GB SATA hard disk model), and the proposed solution solved my problem with G-P-M, so thank you very much for this workaround.
When I was looking for a solution, I found a similar solution at this website: [https://sites.google.com/a/mg8.org/ubuntu-aa1/hw/power](https://sites.google.com/a/mg8.org/ubuntu-aa1/hw/power)
Take a look at it if you want to tune the power consumption of your AAO (very tricky tips!).

Cheers, Ibon.

---

### Post by nekr0z on 2009-02-23
My girlfriend has recently received a Lenovo S10 as her birthday present, and installed Ubuntu 8.10 (we both are heavy Ubuntu users). She had an issue with g-p-m, which is now solved thanks to this thread, but there's one more issue that's still bugging her (and she's bugging me about it). The problem is, when S10 wakes from Suspend-to-Disk (a.k.a. hibernate), touchpad stops working altogether, and only works after a reboot. Suspend-to-RAM (a.k.a. sleep) doesn't cause any trouble, but StD does.

Does anybody has a clue about how to fix this? I had a similar trouble on my Lenovo 3000 N100, and that was fixed by adding "i8042.nomux" option to /boot/grub/menu.lst, but on S10 this solution does not help.

---

### Post by jengelsm on 2009-03-02
I am having a problems with the gnome power manager as well, but mine is registering 650,000+ hours at 100% charge and 10,000+ hours of use just minutes before the computer suddenly powers off, realisticly I am doing well if I get 1.5  hours on the battery.
I have no idea what to do about this

---

### Post by necronwarrior on 2009-03-09
Have you found a solution yet, LoSt180???
Well I haven't and the problems have just got worst.
Gnome Power Manager now stops responding everytime i switch from ac power to battery.
Sometimes the laptop completely frezees!!nothing works(keyboard,mouse). the only option is to switch off the power directly and reboot the system.

Please throw some light on the matter!!!!>>>>>:(:(:(:(

---

### Post by weboide on 2009-03-14
This bug has been reported to gnome bugzilla already. But they say the cause would be from Xorg server.

[http://bugzilla.gnome.org/show_bug.cgi?id=571006](http://bugzilla.gnome.org/show_bug.cgi?id=571006)

---

### Post by nderic77 on 2009-03-24
does anybody know if the gnome-power-manager and (related) laptop overheating problems are anticipated to be resolved in 9.04? I really enjoy running Intrepid on my Dell Inspiron 1526, but the overheating can be a pretty major problem. It seems to be worse when I am running my XP VM on VMWare Server 2.0. Especially if I try to listen to a podcast via the VM's shared folders.

---

### Post by necronwarrior on 2009-03-28
Well I still haven't found a solution to the problem, but the best method to get the G-P-M up and running was to open up system monitor(add it to your panel or System--> Administration --> System monitor) and kill the G-P-M process. Then restart it using the run application command(press alt+F2 and type in gnome-power-manager), it starts and runs sucessfully.
If anyone else has any other solution please post it....

---

### Post by fuzzyworbles on 2009-03-28
I had power manager hanging issues, but i just sort of tolerated it. i noticed however that after i upgraded to the latest acer one bios that the power manager stopped hanging, the battery icon appeared faster in the systray, etc..

after reading up more about the original bios shipped with the ZG5, i've found that it was complete garbage. among it's garbage qualities was power management.

so, upgrade to the latest bios and shift the blame away from gnome.

---

### Post by Saghaulor on 2009-04-14
> **MonsterDigital said:**
> First, Excuse me for may english, is really bad... 

Anyway, I just only say Thank you very much... this is the solution perfectly for me, buy I hope that this problem (bug) will be fixed...
Thanks, and see you later.

NOTE: If anybody can correct my english, is welcome...

I believe what you wanted to say is the following:

First, Please excuse me for my English, it is really bad.

Anyway, I only wanted to say thank you very much, this solution worked perfectly for me, but I hope that this problem (bug) will be fixed.
Thanks, and see you later.

NOTE: In anybody would like to correct my English, I welcome you to do so.

---

### Post by MonsterDigital on 2009-04-27
> **Saghaulor said:**
> I believe what you wanted to say is the following:

First, Please excuse me for my English, it is really bad.

Anyway, I only wanted to say thank you very much, this solution worked perfectly for me, but I hope that this problem (bug) will be fixed.
Thanks, and see you later.

NOTE: In anybody would like to correct my English, I welcome you to do so.

Thanks, really sounds better, jeje...

---

