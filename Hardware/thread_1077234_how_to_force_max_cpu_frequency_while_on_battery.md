---
title: "how to force max cpu frequency while on battery?"
date: 2009-02-22
forum: Hardware
---

### Post by roberta_aguilles on 2009-02-22
Hi,

Just a simple question - how to max the cpu frequency while on battery? 
My machine is capable of running at either 500Mhz, 1100Mhz, and 2100Mhz.
I found out that no matter what I do, while on battery, it won't run faster than 1100Mhz - whichever method I use it to set (either through gnome cpu scaling applet, or through direct setting via /sys/devices/system/cpu/cpufreq manipulation). 

cpufreq-info tells me that the scaling policy is limited to 500Mhz - 1100Mhz, and trying to change that by setting scaling_max_frequency gives no error, but the value remains at 1100Mhz.

/etc/defaults/acpi-support doesn't seem to have settings to control cpu freq, and /etc/acpi/events has none as well.

rmmod-ing cpufreq and powernow-k8 doesn't seem to have any effect.

Do I miss anything? I'm quite sure that the machine is quite capable of running 2100Mhz while on battery - because the other linux distro (puppy linux) can be configured to do it (and it drains the battery like crazy and the fan sounds like jet engine, but that's another matter altogether). 

While on ac power, this is not a problem, I can go to the max simply by using the gnome cpu scaling applet. The restriction only happens while I'm battery, and while I'm happy that Ubuntu tries to give me longer battery life, there are times that I must absolutely run at highest CPU speed regardless of whether I'm battery or on ac. 

For information, I'm using Intrepid amd64 with HP Pavilion tx2500 tablet, which uses AMD64 Turion x2 CPU.

Any helps appreciated.:popcorn:

---

### Post by binbash on 2009-02-22
Does this work ? :

sudo cpufreq-selector -g performance

---

### Post by roberta_aguilles on 2009-02-22
Thanks, but I have tried that, and that didn't work. 

Even if the governor is already set as "performance", the cpu speed is still limited to 1100Mhz because the scaling_max_frequency is set at that 1100Mhz while on battery - and whatever higher value I dump to it, it always reads as 1100Mhz while on battery.

---

### Post by Favux on 2009-02-23
Hi roberta_aguilles,

Sorry I don't have an answer.  But if you don't get an answer here after a while you might consider posting to:

[http://ubuntuforums.org/showthread.php?t=845911&page=53&highlight=tx2*]("http://ubuntuforums.org/showthread.php?t=845911&page=53&highlight=tx2*")

The folks on the thread are usually pretty helpful.

---

### Post by roberta_aguilles on 2009-02-23
Thanks Favux, I will try that - reason I post it here is because I don't think it's tx2500-specific. I will re-post my "problem" there to see if anybody has a clue.

BTW I got my tx2500 working exactly from the thread you mentioned - thanks to you and the others also who did the hard work figuring out things :D

---

### Post by ProNux on 2009-02-24
Try installing emifreq cpu scaling...

---

### Post by roberta_aguilles on 2009-02-25
Thanks ProNux, but it doesn't help. I can set the frequency to 2100Mhz but after checking it's still 1100Mhz. 

I think the issue is deeper, I can think of a few:
a) there is a daemon somewhere that resets scaling_max_freq to 1100Mhz when it's on battery. 

b) there is a control built somewhere in the cpufreq / powernow-k8 / acpi module which restricts the frequency setting when it's on battery. This control may be configurable, or may be not.

I have tried to kill all process which I think may be doing a) above (I have killed tried to kill acpid, gnome-power-manager, hald (so that hald-addon-acpi is killed too), but to no effect --- I can't get it set to 2100Mhz on battery no matter what.

So my suspect is now it's b), and I hope the setting is not compiled nor forced by BIOS acpi settings, but can be overriden by configuration file of some sorts. However I'm running out of ideas to move forward - google doesn't seem to help much (perhaps because what I'm trying to do is the reverse of what others normally do).

---

### Post by Favux on 2009-02-25
Hi roberta_aguilles,

Have you tried using powernowd?  It should be installed, but if not try Synaptics Package Manager.  It uses AMD's PowerNow! technology and the sysfs (or is it attrs now?) interface in kernel v. 2.6.  To get the manual type "man 1 powernowd" in a terminal.  Users can modify "/etc/default/powernowd" to add personal options according to a comment in "/etc/init.d/powernowd".

---

### Post by roberta_aguilles on 2009-02-26
Thanks Favux.

I'll give it a spin. I know it's installed but not sure whether it's running. I'll let you know ...

In case anybody is wondering I need the full-power, I plan to use this little machine as my portable audio studio --- apart from the usual mundane usage. Running jackd, fluidsynth, rosegarden, jamin and time-machine. (I even tried to install linux-rt but it seems to be broken in Intrepid). All these - especially jamin - require a lot of cpu horse power.

I don't want to have to plug in my ac power if I'm only testing the setup for 15 mins or so, because it's rather stupid and will make the battery die faster.

cheers!

---

### Post by roberta_aguilles on 2009-03-01
Tried, still no joy :( I tried to run powernowd in the foreground to see what it's doing - sudo powernowd -d -m 3 -vvv

I can see that when the load is increased, it tries to set the feq to 2100Mhz, but unfortunately for whatever reason, the actual value set is only 1100Mhz (obtained by reading /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq (for both cpu0 and cpu1) - just like what all the other methods I have tried.

I'm sure there is an explanation behind this behaviour :(

---

### Post by Favux on 2009-03-02
Hi roberta_aguilles,

I'm sorry it didn't pan out.  Whatever the explanation is it eludes me.

Good luck!

---

### Post by PippoSniffo on 2009-03-06
Have You tried to remove any cpu frequency package ?

In this manner maybe the cpu goes ever at the maximum freq.

---

### Post by cenzorrll on 2009-03-15
i think this issue goes very deep, i have also come into this problem (using a tx2500) I'm dual booting vista (barf) and intrepid. My processor governs in 500, 1000, and 2000 mhz and when unplugged it doesn't go above 1000. so my guess is it has something to do with the bios.

this is with both vista and ubuntu.

---

### Post by roberta_aguilles on 2009-03-17
Thanks to everyone who has helped.

I would rather say that it's not BIOS. The BIOS may "suggest" the OS to do this, but it's entirely up to to the OS whether to follow it. 

I know because I have another Linux installed (Puppy Linux) and it happily goes to the max once I use the "performance" as the scaling governor, ac or battery. No artificial limitation.

PippoSniffo, I don't want to remove the cpufreq things, I need and want them. I just want to be able to run at max speed when I want it. This it the use case:
a) I'm doing some audio work on power, so full performance (e.g. recording)
b) accidentally, the power cable is kicked out, so power is lost. Laptop now runs on battery.

In this scenario, I would like to the laptop to continue to run at full performance until I say otherwise (ie, until I finish my recording), rather than automatically throttle down and cause my audio applications stalled halfway.

In other times (when I'm not doing audio work, only browsing for example), it's perfectly normal and *expected* for the cpu to throttle down.

I still don't have a solution ... anyway Jackalope is coming, perhaps I should wait for it and see.

---

### Post by Favux on 2009-03-30
roberta_aguilles,

Just a stray thought.  Have you checked with the HP site that you have the latest bios for the TX2500?  I know what you said above but I just saw a poster with a similar problem (on another machine) saying that's what fixed it for him.  So...

---

### Post by roberta_aguilles on 2009-04-06
Thanks favux, can you point me to the thread? I'm very very reluctant to upgrade the BIOS unless it's absolutely necessary - as, you know, one failed update and I have a brick in my hand. My BIOS version is F.05 and the latest one available seems to be F.0B.

---

### Post by Favux on 2009-04-06
Hi roberta_aguilles,

The link is here:  [http://ubuntuforums.org/showthread.php?t=1109244&highlight=cpu+bios](http://ubuntuforums.org/showthread.php?t=1109244&highlight=cpu+bios)

Is that F.08?  I never had any problem flashing my bios from windows but I guess mileage varies.  As you know just be sure it's the bios for your machine.

---

### Post by roberta_aguilles on 2009-04-10
Thanks Favux. I'll have read the thread and downloaded the BIOS update. It's F.0B (the letter bee not the number eight), released Feb 2009. I followed HP prompts and  am quite sure it's meant for my model (tx2522au). If I do flash the BIOS, I'll post here to let you know about the result.

cheers!

---

### Post by Favux on 2009-04-10
Good luck!

---

### Post by roberta_aguilles on 2009-04-16
Ok, I took the plunge. Update it to F.0B (latest as available from HP's website). I was kind of hoping that it would allow me to backup the current BIOS first --- but it didn't !! Anyway, I did it, boot Intrepid on battery, change the governor to performance - and voila I got it at 2.1 Ghz (my max frequency).

Yes, I'm happy, thanks everyone - especially to you Favux :KS (I also read your posts to get my tablet working much earlier before I posted anything here) :p

Apparently ubuntu kernel follows BIOS information more faithfully than others, no? 

And so far so good with the new BIOS ... :)

---

### Post by Alexis Phoenix on 2009-04-16
You could try running laptop mode - you can configure it to use the governor you want depending on the ACPI status.  OTOH - the same problem may stop it from working too.  It may be a silly question, but did you check that the correct governor module is loaded?

(crawls back under skirting board)

Alexis

---

### Post by Favux on 2009-04-16
Hi roberta_aguilles,

Outstanding!  I am happy for you.

That turned out to be a monumental struggle didn't it.  But you triumphed!

---

