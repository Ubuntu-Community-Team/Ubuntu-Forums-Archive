---
title: "Computer will not wake after Hibernate/Suspend"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by mjtate10 on 2009-11-02
I have a Dell Mini 9 and upgraded to 9.10 this weekend.  Everything is ok so far except the computer does not wake up after is goes into hibernation or suspend mode.  I have to power on and off to get it running again.  Any ideas?

Thanks

---

### Post by jet29 on 2009-11-02
I also have the same problem on my desktop it freezes and then screen goes blank and i have to reset, and then the system doenst load up again, i'm having to many problems with this supposed updated version.

---

### Post by Marlonsm on 2009-11-02
Same happens here. It goes to sleep normally, the power LED starts blinking (just as it should do). But when I press the power button, the computer just turns on normally as if it was powered off.

The very same thing happened in the early days of 9.04, but it got fixed with the updates.

---

### Post by mjtate10 on 2009-11-02
> **Marlonsm said:**
> Same happens here. It goes to sleep normally, the power LED starts blinking (just as it should do). But when I press the power button, the computer just turns on normally as if it was powered off.

The very same thing happened in the early days of 9.04, but it got fixed with the updates.

Not the exact problem I am having.  If I press the power button, nothing happens.  Does not restart, does not wake up.  I have to hold the power button down for a few seconds to get the computer to do a hard shutdown, then press power again for it to reboot.  I currently have it set to never sleep or suspend if the screen is not closed, so I have a work around, but this is not practical going forward.  If I close the laptop, then only way to get is it working again is to do a hard shut down.

---

### Post by Liquen on 2009-11-02
I have a similar problem. I'm not sure if it will work for you, but here my quick-and-dirt workaround: when returning from Suspend and a blank screen appears, press ctrl-alt-F1 and then ctrl-alt-F7; screen will then reappear.

---

### Post by mjtate10 on 2009-11-03
Alt-Ctrl+F1 then F7 did not work.  Still not working.

---

### Post by bronxbomberz41 on 2009-12-22
Same issue here.  won't wake after hibernate/suspend on HP dv7-1240 us.  If anyone has a simple fix for this it would be appreciated

---

### Post by Hydrosis on 2010-01-02
I'm having the same problem.

I get a solid black screen.  My mouse lights still work and the computer is blinking like it should be, but the computer acts as if it is off.  I have to hard reset.

I'm having so many problems with Karmic that I fail to see how this is an upgrade.  Audio dies when playing games (NES/SNES ROMS, AssaultCube, UrbanTerror etc), Ubuntu doesn't detect native screen resolutions (600x800 on a 22" monitor sucks), can't listen to mic/line-in through speakers in Karmic (seriously), can't play games without major lag (all work fine in Windows w/ same machine), can't Hibernate etc.

Hell, I hate to say it but even my Windows XP install on this machine is vastly superior to Karmic.

If anyone finds a fix for this or any of my other problems feel free get get a hold of me.  It would be greatly appreciated and might even save me from Microsoft.

---

### Post by ZenBeam on 2010-01-02
> **Hydrosis said:**
> I'm having the same problem.

I get a solid black screen. My mouse lights still work and the computer is blinking like it should be, but the computer acts as if it is off. I have to hard reset.
[..]
If anyone finds a fix for this or any of my other problems feel free get get a hold of me.  It would be greatly appreciated and might even save me from Microsoft.I have this hibernate/suspend problem with 9.10, and had it with 9.04 as well.  I recently installed the latest Linux Mint, which is based on Ubuntu 9.10, and it can suspend and hibernate pretty well.  Sometimes when it comes out of hibernation, it immediately goes to sleep, but that's much less of an annoyance than no hibernation at all.   It also *occasionally* goes to sleep when the battery finishes charging, or if I remove the AC power cable.

You could try a Live CD, and see if your audio/video problems go away.  I don't think you can test the sleep/hibernate functioning with a Live CD though.  (well, it'll sleep and hibernate, but for me it just rebooted from the CD when I woke it up;  That was one of the first things I tried with it.)

---

### Post by penkoster on 2010-01-04
Hello, I'm new to Ubuntu and the only problem I have is re-activating after hibernation mode. 

When I hit the hibernate button on my keyboard the computer goes to hibernation mode, but when I move the mouse or press any key on the keyboard to re-activate the computer (it worked on Win-XP!) it does not react, I have to push the on-off switch to reactivate the computer (from then on it works ok). 

Is there a way for a computer (Ubuntu) freshman to resolve this problem.

---

### Post by alpha-buntu on 2010-01-08
> **jet29 said:**
> I also have the same problem on my desktop it freezes and then screen goes blank and i have to reset, and then the system doenst load up again, i'm having to many problems with this supposed updated version.

count me again.

hibernate does sometime work (if I hibernate directly for testing purpose after restarting the system).
 
but in 9/10 times, after working some hours on ubuntu, doing hibernate and waking up from hibernate, the system hangs on boot up with the white ubuntu logo. no response via keyboard possible (terminal, ctrl - c, etc.). just stuck.

system is homegrown core2duo, 3 gig ram, etc..

---

### Post by projnet on 2010-01-16
Same problem, HP NX6125 (AMD Turion 64 bit CPU), Karmic x64 installed.

Splash screen comes up OK but then screen goes black and system will not respond, hard power off/power on required to restart system.

---

### Post by recluce on 2010-01-16
...if you have the "black screen of death" problem on resume under Karmic and you have ATI graphics, check out the solution I posted here:

[http://ubuntuforums.org/showthread.php?t=1371844](http://ubuntuforums.org/showthread.php?t=1371844)

---

### Post by RBertrand on 2010-02-02
> **recluce said:**
> ...if you have the "black screen of death" problem on resume under Karmic and you have ATI graphics, check out the solution I posted here:

[http://ubuntuforums.org/showthread.php?t=1371844](http://ubuntuforums.org/showthread.php?t=1371844)

Having the correct and working video drivers is important. When that's OK in your situation, you might want to see whether using an ext4 partition hinders hibernation too. See my experiences in this post: [http://ubuntuforums.org/showthread.php?t=1042946&highlight=hibernation](http://ubuntuforums.org/showthread.php?t=1042946&highlight=hibernation)

Some of the comments in this thread (e.g. not being able to resume after a suspend) do look a lot like what I experienced...

---

### Post by nikkkko on 2010-03-01
Count one more.  Both hibernate and suspend lead to black screen with blinking cursor and a reboot.

This on a Dell M1330 which I recently wiped and upgraded to 9.10. It was bought with ubuntu pre-installed and suspend/resume worked up until 9.04

---

### Post by Gerard08 on 2010-03-02
Just adding my own frustrations. If I try to shut down normally, the log-in screen appears. I have to go to the lower right shut-down icon to end session. I can suspend in the same way. After a few suspends though, the system does not boot fully and has to be turned off. I would post a log but I do not know which one is relevant. Thanks!

---

### Post by prouddad1 on 2010-03-02
I'm using a Thinkpad.  I have to use the hot keys to wake.  Fn + F4

laptop doesn't wake from any other keys or power button

---

### Post by QuimO on 2010-03-04
I fixed uninstalling grub2 and installing grub [with this instruccions]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

---

### Post by nikkkko on 2010-03-05
> I fixed uninstalling grub2 and installing grub

There appear to be a lot of instances of this problem and no solutions, except yours.  Are you saying that the suspend, hibernate / resume problems we are all seeing are due to the new version of grub?

---

### Post by Maverick52 on 2010-03-30
> **Liquen said:**
> I have a similar problem. I'm not sure if it will work for you, but here my quick-and-dirt workaround: when returning from Suspend and a blank screen appears, press ctrl-alt-F1 and then ctrl-alt-F7; screen will then reappear.

Big problem: 

Yesterday I installed my first linux distro ever, chose Ubuntu Studio 9.10 Karmic Koala. It was a clean install from the start, as I chose to totally replace Vista in my Toshiba Satellite A305D laptop. First thing I thought: "Why didn't I switch before?".

Today I'm living every newbie's nightmare.

I closed the laptop, which made it hybernate, I suppose. Now, when I try to get it running it's like a vegetable, no activity, no drivers, no processing, just black screen. Well the leds turn on, but that's the only sign it's turned on.

If I do a hard shutdown, wait and turn it on again, same thing. I don't think controllers or drivers are being loaded at all.

Tried booting it with the live DVD - nothing.
Also tried "ctrl-alt-F1 and then ctrl-alt-F7", no screen, it's like it was off.

Help! I want to make it work on linux, I really do, but I need it working at all, first!

---

### Post by asw24 on 2010-04-30
just installed 10.04. Hibernate does not work. Rest is OK, so no big issue. On the 32 bits install (another pc; core duo) it works flawless. I had hoped that with the work done on the fat upstart things would be solved but no. As said pc works OK, this is a nice to have but no disaster.

---

