---
title: "BIOS warning for Toshiba Owners!"
date: 2007-02-13
forum: Hardware
---

### Post by ThrobbingBrain66 on 2007-02-13
I have a Satellite laptop, but I'm sure the new BIOS upgrades have been released for other models.  Within the last few days Toshiba released a BIOS upgrade (v1.80).  This upgrade tweaked the BIOS for Vista as well as fixing a couple other issues. It claims that after you upgrade to 1.80 you CANNOT return to 1.70.

[COLOR="Red"][SIZE="7"]DO NOT UPGRADE!!![/SIZE][/COLOR]

I upgraded my BIOS to 1.80 and my Edgy install would boot to the Gnome splash and no further.  The startup music's first note went on an endless loop.  I wasn't too worried at this point, thinking that a fresh install may take care of the problem (wishful thinking, I know).  That didn't work either, so at this point, I'm sicker than a dog thinking I just turned my laptop into a brick.

My last attempt to save my laptop was reverting to 1.70.  Luckily for me this worked and my laptop is up and running again.  I've always heard the warnings that you should not upgrade your BIOS unless you're having issues, but I personally had never had anything go wrong until today.  In the future I shall be more careful.

I hope I save some people from what I had to deal with.

---

### Post by Brainfart on 2007-02-14
yikes... thanks for the warning, I'm just reinstalling everything already, don't want to do it twice :x

---

### Post by some_random_noob on 2007-02-14
Thanks... I don't have a Toshiba, but I mindlessly upgrade stuff even when I have no problems. Obviously not a good habit. 

How did you revert the BIOS if they said you couldn't??

---

### Post by Grey on 2007-02-14
Thanks for the warning.  I rarely ever update the BIOS (for that very reason), but that's very good to know.  I am typing on a Toshiba Satellite at this very minute as I dist-upgrade to Feisty.

---

### Post by adam.tropics on 2007-02-14
Not too long after I got my Toshiba, I took it to the service centre to get a couple bits done, and asked them if, while they have it in under warranty anyway, they could update the bios. "Of course we can sir"....great, me thinks.

A day or so later I got a call to say all the work that was originally specified had been completed, but the laptop wouldn't be ready for collection for 2 weeks! "I beg your pardon???!!", yes 2 weeks. Turned out a number of models suffered a bug with the bios whereupon any attempt to update, even with full battery, and plugged into the mains, would result in the machine thinking the power was dead and shutting off......mid update. Since this kind of left you with half a bios, it had become a brick. They replaced the motherboard in the end. (at there expense) The 2 weeks was to account for god awful delivery times up here.

If you're gonna flash the bios, get someone else to do it, who can be held liable for rendering you machine about as useless as a chocolate radiator.

---

### Post by xyz on 2007-02-14
Thanks for posting this! I have a Toshiba Satellite A 40.

---

### Post by Onyros on 2007-02-14
I have never upgraded the BIOS of any laptop I've ever had, and I will never ever unless some problem renders it useless to start with.

There are too many horror stories about BIOS upgrades, which kind of make them totally forbidden for my machines.

To start with, I would never upgrade my BIOS for some Vista tweaks... Why would I, if I'm not gonna run Vista in the first place? ;)

Anyway, thanks for the heads-up!

---

### Post by ThrobbingBrain66 on 2007-02-14
> **some_random_noob said:**
> Thanks... I don't have a Toshiba, but I mindlessly upgrade stuff even when I have no problems. Obviously not a good habit. 

How did you revert the BIOS if they said you couldn't??

I'm not really sure how I was able to do it.  The only thing I can imagine is that you are only unable to revert the BIOS if you are running Vista.

---

### Post by ThrobbingBrain66 on 2007-02-14
> **Onyros said:**
> I have never upgraded the BIOS of any laptop I've ever had, and I will never ever unless some problem renders it useless to start with.

There are too many horror stories about BIOS upgrades, which kind of make them totally forbidden for my machines.

To start with, I would never upgrade my BIOS for some Vista tweaks... Why would I, if I'm not gonna run Vista in the first place? ;)

Anyway, thanks for the heads-up!

I didn't upgrade for the Vista tweaks.  There was mention of some general ACPI fixes in the changelog as well.

---

### Post by ckipel on 2007-04-09
Just for future reference to anyone still trying to find answers and coming across this thread:

You can revert to 1.7 by burning the iso to a CD and inserting it into the laptop. It will automatically flash and when it reboots, you will need to quickly eject the CD.

Hope this helps someone.

---

### Post by ckipel on 2007-04-18
The new 2.00 bios also breaks Ubuntu. Do not upgrade.

---

### Post by JSorrell on 2007-04-18
I read this an hour too late. Thanks for posting, I was rather worried. I'm having the exact same problem you did. Going to downgrade...

---

### Post by forcesofhabit on 2007-04-19
I have a strange issue... I "upgraded" to Vista, and it did change my BIOS. I hated it and went back to XP along with my standard dual boot of Ubuntu. Now my sound doesn't work in my Toshiba laptop. 

What is this iso trick you speak of? Are you saying just putting in a standard Ubuntu disc will solve my problem or ??

---

### Post by k0rv3n on 2007-04-19
I have Toshiba Satellite P100-208 and I upgraded to the 3.30... is there a way for me to downgrade?
I can't get sound to work at all in Ubuntu :(

---

### Post by ckipel on 2007-04-19
Try looking at this thread for the P100:

[http://ubuntuforums.org/showthread.php?t=412986](http://ubuntuforums.org/showthread.php?t=412986)

---

### Post by ckipel on 2007-04-19
> **forcesofhabit said:**
> I have a strange issue... I "upgraded" to Vista, and it did change my BIOS. I hated it and went back to XP along with my standard dual boot of Ubuntu. Now my sound doesn't work in my Toshiba laptop. 

What is this iso trick you speak of? Are you saying just putting in a standard Ubuntu disc will solve my problem or ??

If you have an A105 series laptop, download the 1.70 firmware from Toshiba's website. When the launcher.exe runs, choose CD ROM boot. The iso will be located in the C:\[firmware_folder]. Burn that onto CD and reboot your laptop from CD. It will automatically flash.

---

### Post by tubasoldier on 2007-04-19
Yeah, i found this thread two months after it happened to me. The laptop works. Fortunately I had a good install of Edgy on it. But now my CDROM is no longer functional and my PCMCIA slots are also non-functional. Upgrading to fiesty on my laptop is out of the question. If something goes wrong I can not fix it. All I can do is use edgy until Toshiba pulls their head out and fixes all of their BIOS problems.

---

### Post by BetaguyGZT on 2007-04-20
That's a bit scary. Buy a new rig (laptop or otherwise), flash the BIOS, and end up with a boat anchor....

Even if you have one of those boards that will reset the flashed BIOS with its' original one (and some do, thankfully...), it's still dodgy..

---

### Post by ciscosurfer on 2007-04-24
@ThrobbingBrain66,

I've included a word of caution to my BIOS upgrade HOWTO and cited this thread as a reference.  Thanks!

---

### Post by Compucore on 2007-04-24
Looks like MS is in cahoots with the motherboard manufacturerers for that so they can run vista on it. It is ashame when you see that happen from a company like MS. They can't leave the others alone. They are messing around with everything tweak wise.

Compucore

---

### Post by fasttimes on 2007-08-01
Same results on my Toshiba A105 S2712, just like [this thread]("http://ubuntuforums.org/showthread.php?t=384239"). v1.7 works, v1.8 and 2.0 broke.
2.0 (and v1.8?) does fix the Fn-Fx backlight controls though!

---

### Post by ThrobbingBrain66 on 2007-08-01
How do you know that the Fn-Fx keys are fixed? v2.0 doesn't allow me to even finish a boot sequence.

---

### Post by fasttimes on 2007-08-02
The gnome desktop hangs, but you can still load openbox using the "options -> select session" option on the login screen.  Sound still FUBAR, but backlight control works, but buggy.

BTW, I wonder if KDE hangs as well?

There is also a blog post at [http://www.adamztech.com/adamzblog/?p=45](http://www.adamztech.com/adamzblog/?p=45) that covers the problem we are having.

---

### Post by davesmith on 2007-10-02
hallo

i have feisty 7.04 on a tosh Satellite A30, it works well using the bios it came out of the box with. 

Ive read this thread with interest, because there is a new bios update for it on toshiba's europe website, ver1.80 and ive been thinking about flashing it. I believe it resolves some ACPI issues to allow this m/c to run Vista, however there is no documentation to that effect with the download. Not that I want to run Vista, but apparently there are other changes too....

It does say in the bios description that it provides increased functionality.....so i'm tempted to try it. Has anyone tried this particular upgrade (its dated 08/08/2007) on an A30 or would the communty recommend to leave well alone?

The model is 4 years old now and I do wonder why Toshiba are issuing a bios update for such and old model

DaveS

---

### Post by original_jamingrit on 2007-10-02
Hey, to the OP, thanks for the tip.  I've been thinking about flashing my BIOS, but since I have no real reason to, I'm better of not taking the risk.

Although it looks like it might stink for people trying to dual-boot with Vista, if they can't make use of the tweaks without sacrificing a Linux install.

---

### Post by Ptero-4 on 2007-10-14
I'm thinking about getting a toshiba L45 SP2046 laptop (was cheaper to buy than the macbook), but I want to ask two things.

Does it run linux (I saw a bunch of intel stuff in the Vista device manager like Celeron, GMA950, intel wifi, etc)?

Does it come with the 1.70 BIOS (or any other known linux frinedly version)?

---

### Post by prairiedog6791 on 2007-12-14
Hi All,

I'm late showing up to this thread, but I have information that may help.

I run GNOME on a Toshiba A100 (PSAA0C-LE400E) laptop with openSUSE 10.3 (yes, I know this is an Ubuntu site).  

All was well, but a kernel update left me without network and unable to log into GNOME, with the system stuck repeating the first note of the login music seemingly as described by ThrobbingBrain66.

It was possible to log in using XCFE, so I checked the output of dmesg using "dmesg | grep try" and it recommended two kernel options:

pci=routeirq
irqpoll

With those passed to the kernel, it works again.  It's possible that the Vista BIOS update may require some adjusted kernel options to make all work properly.  Can anyone confirm this?

I've been contemplating the latest "Vista" BIOS  update to improve power management and restore panel brightness control. If I get the nerve to try it on mine, I'll post the results.

-Mike

---

### Post by no_mosquitos on 2008-04-16
Hi everyone.

We've got a slightly different problem here. After upgrading bios, Vista fails to load, while gnome starts ok. Could you please give instructions were to get v1.70 to with iso to revert the bios.

Thanks.

---

### Post by dcc24 on 2008-10-09
I've just flashed my BIOS on a Satellite A200 and I thought I should share this.

It's a year old laptop and this was the first BIOS update that I've performed on this machine. I have a never-ever-used Vista installation in a small partition so I booted it and performed the update from there.

Everything went smoothly. I confirm that the following stuff keep working after the update:

ALL ACPI features
ALL of my hardware
Sound works (though there are some people claiming otherwise)
Everything gnome-related works.

What does NOT work is the microphone, but I'm not sure if it's related to the BIOS upgrade.

I've also checked /var/log/messages, dmesg and some other logs. Everything seems to be working as usual.

---

### Post by K.Mandla on 2008-10-09
Moved to Hardware and Laptops.

---

