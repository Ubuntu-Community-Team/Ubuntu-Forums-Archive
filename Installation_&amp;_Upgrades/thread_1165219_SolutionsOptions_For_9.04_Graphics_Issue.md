---
title: "Solutions/Options For 9.04 Graphics Issue"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by redjam on 2009-05-20
Hi,

So I have upgraded to 9.04 and now I have no display and thus my machine is broken.

I have an Dell Inspiron 530n with ATI Radeon HD 2400 PRO graphics card; is there any chance that putting in a new card would fix the problem?

If so, what should I buy? Needs to be relatively inexpensive.

If not, what are the other options? Fresh install of 8.* is one but that means loosing all the work I've put in setting it up over the past year.

Is it worth waiting to see if a solution emerges in the next few days? (I can't wait much longer than that).

Thanks.

---

### Post by doas777 on 2009-05-20
just a quick check before proceeding. have you unplugged the monitor from the wall for a minute, and tried plugging it back in and powering it on? I have one monitor that fritzes at boot, but if I unplug it for 20 secs, it comes right up when i plug it back in.

another thing to check, is whether the vid signal may be going to another output. this is only a problem if you have an onboard vid port, but use an expansion vid card instead. 

Do you get ANY monitor output at ANY stage of the boot? BIOS? Grub? Splash?
how about if you boot off live CD?


Did this issue occur as soon as you upgraded?

I personally am against upgrades (as opposed to clean installs), because if your system state is not exactly what the installer thinks it should be,  then it will cause bizarre and usually unrepairable aberrations.

if your bios splash does not show, then you have a hardware problem (dead card or monitor).

---

### Post by redjam on 2009-05-20
Hi, thanks a lot for your reply.

Sorry, should have said. Everything is fine - boots up as normal until it gets to the login screen then screen goes black with some random bits of crap here and there (I'm sure there's a name for this?)

Started doing this as soon as I upgraded so it is definitely the fault of the new OS. I have noticed many other people are having the same problem and nobody seems to have an answer. That is why I am asking what I should do next.

---

### Post by doas777 on 2009-05-20
ok, first things first.
lets reset your xorg.conf to default. once you are done with the splash, wait a second, and hit Ctrl + Alt + F1 to switch to a tty.

run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot
```

after rebooting ubuntu should be running with VGA drivers.
once you get logged in, go to System -> Administration -> Synaptic Package Manager. just open it and close it, or if you want instead, run 'sudo apt-get update' to refresh your repo lists. 

after that, hopefully a restricted driver will turn up in your System -> Administration -> Hardware Drivers applet. install it and reboot. with luck the problem willbe gone.

what kind of vid card do you have?

---

### Post by redjam on 2009-05-21
Hi, thanks for replying again.

Ctrl+Alt+F1 doesn't even work - still just a black screen with fragments of random stuff.

There is a thread about it here:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

So to return to my original question, what should I do?

Buy a new graphics card? Will that work?
Wait and see if there's a fix soon?
Give up and wipe everything?

---

### Post by doas777 on 2009-05-21
> **redjam said:**
> Hi, thanks for replying again.

Ctrl+Alt+F1 doesn't even work - still just a black screen with fragments of random stuff.

There is a thread about it here:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

So to return to my original question, what should I do?

Buy a new graphics card? Will that work?
Wait and see if there's a fix soon?
Give up and wipe everything?

well assuming your hardware is functional and at least minimally compatible, then buying new stuff would be a waste. your probably closer to the answer than you think.

reboot and at the grub menu select your kernels Recovery Mode. once your in, run the command I posted above, to reset the xorg, and reboot.

what kind of video card do you have? ATI or Nvidia or Other.

once you have xorg reset, we'll reinstall the driver and see where that leaves us.

oh and BTW, I've in past had trouble with just the GDM login screen. if you login blind, does the video kick back in?

---

### Post by redjam on 2009-05-21
I meant to say that I did run the command in Recovery Mode - no change.

I even tried manually setting my xorg.conf to the failsafe file at one point. No difference.

Card is an ATI Radeon HD 2400 PRO.

Think I managed to login one time judging by the noises my machine was making but still nothing.

---

### Post by doas777 on 2009-05-21
> **redjam said:**
> I meant to say that I did run the command in Recovery Mode - no change.

I even tried manually setting my xorg.conf to the failsafe file at one point. No difference.

Card is an ATI Radeon HD 2400 PRO.

Think I managed to login one time judging by the noises my machine was making but still nothing.

ok. can you post your current xorg?

---

### Post by redjam on 2009-05-21
I'm not at home just now but I will do when I get back.

Thanks again!

J.

---

### Post by redjam on 2009-05-24
OK, here it is:

Section "Device"
 Identifier "Configured Video Device"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection

Any further thoughts?

---

### Post by PCZahra on 2009-05-24
I have the same xorg.conf file before and after resetting it. My card is an ATI 9200SE that worked just fine in earlier versions but now I'm stuck in low graphics mode.

The boot screen will show the progress bar all the way to the end, then it displays some terminal status messages before going black for 5-10 seconds. It does this three times, then displays a default Gnome style message box saying it couldn't configure my hardware. It then gives me a list of options to fix it and I've tried them all. This is from a fresh install of 8.10 upgraded to 9.04 not 2 hours after literally passing initial tests with flying colours.

Based on previous experiments, I believe it may have something to do with visual effects, but have so far been unable to find the config file to manually turn them off.

---

### Post by doas777 on 2009-05-24
> **PCZahra said:**
> I have the same xorg.conf file before and after resetting it. My card is an ATI 9200SE that worked just fine in earlier versions but now I'm stuck in low graphics mode.

The boot screen will show the progress bar all the way to the end, then it displays some terminal status messages before going black for 5-10 seconds. It does this three times, then displays a default Gnome style message box saying it couldn't configure my hardware. It then gives me a list of options to fix it and I've tried them all. This is from a fresh install of 8.10 upgraded to 9.04 not 2 hours after literally passing initial tests with flying colours.

Based on previous experiments, I believe it may have something to do with visual effects, but have so far been unable to find the config file to manually turn them off.


well if you can get to a cli, try ```
metacity --replace
```
(if you get an access denied, run again with sudo).

that should turn off compiz and or emerald.

---

### Post by redjam on 2009-05-25
Right, so there is no fix for this.

Does anyone know if it's worth trying a new graphics card?

---

### Post by doas777 on 2009-05-25
> **redjam said:**
> Right, so there is no fix for this.

Does anyone know if it's worth trying a new graphics card?


another card may help, just because nvidia tends to work a little better with ubuntu. no gaurentees that that is where the problem is, but it may work with less of a headache than trying to configure the ati card. I wouldn't say there is no fix per se, but i'm still waiting to look at your xorg. 


good luck, and let us know how it works out.

---

### Post by Ethelbert2 on 2009-05-26
[COLOR="DarkOliveGreen"][FONT="Tahoma"][SIZE="3"]I would like to understand this too. I have recently returned to trying Ubuntu after a two year absence - putting it on an old computer.(Pentium III 450Mhz - 512MB RAM)  None of the 9.04 flavours would work. All run through to the point where you wait for the login screen and just display a jagged colour line image. Impossible to get command line or anything.  Other distributions like Puppy just give a blank screen. Various start options achieve nothing. Was going to give up on Linux again.

DSL worked but did not find wifi.  That is Linux 2.4.
Absolute worked but did not find the network card or wifi.

Eventually I tried the older Xubuntu 8.04 - this worked nicely (took a while to work out a wifi card driver install but have done that). Did an experimental upgrade to 8.10 with trepidation but it works ok too (am writing this from there).

Dare not go to 9.04 but of course would like to upgrade.

So it seems to be a video card thing as far as I can deduce - either from Ubuntu or from the Linux kernel???

My card is a Radeon 7000 (Radeon VE family) according to hardware listing.


Does anyone know why this will not work?

Or if it can be made to work - how to get the drivers in before 9.04 freezes in jagged lines (therefore making it impossible to get anything installed).

Buying a new video card would kind of invalidate the reason for using Linux in the first place which is to give an old computer new life. (Though actually it can survive with Win XP which seems to run it fine.)


[/SIZE][/FONT][/COLOR]

---

### Post by PCZahra on 2009-05-31
> **doas777 said:**
> well if you can get to a cli, try ```
metacity --replace
```
(if you get an access denied, run again with sudo).

that should turn off compiz and or emerald.

Well that did something good. Not sure if it's completely fixed yet, but we'll see.

---

### Post by mr_raider on 2009-05-31
If you have rebuilt the failsafe xorg.conf file, it's possible Ubuntu can't find the open source drivers fro your ATI card.

Boot into recovery mode and go to command line option. Try running the command

```
sudo apt-get install xserver-xorg-video-ati
```

Then try to start the x server

```
startx
```

---

### Post by PCZahra on 2009-06-10
ok, xserver-xorg-video-ati was already installed, and startx eventually did bring up the desktop even slower than low graphics mode. it did seem to be a little more responsive, though.
also it didn't start gdm with it (I noticed that when I tried to run.. anything). I ran gdm separately and found the original problem: the screen blanks out for several seconds, goes back to previous (in this case, the desktop that startx opened, which still worked) and then dies with the same message, "ubuntu is running in low graphics mode" with the same options as before.
Now, I'm doing this with two computers, they both have ati 9200SE cards (different types though), one is a slow pentium 3, the other is a faster athlon. the pentium is once again working as it always has (read: barely), so I'd prefer to get the athlon working just as well (read: faster than the pentium). What is confusing is that what works on one does not work on the other.

---

### Post by PCZahra on 2009-06-10
upon further rebooting, it would seem startx is just a long way to get a black screen.

---

### Post by PCZahra on 2009-06-14
what about the old driver from 8.10? is there a way I can get that back and use it instead?

---

### Post by PCZahra on 2009-11-12
bump. was this fixed in 9.10? I'm having cd burner issues atm.

---

