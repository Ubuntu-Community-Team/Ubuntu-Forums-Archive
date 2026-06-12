---
title: "Laptop overheating! in Karmic"
date: 2009-11-04
forum: Hardware
---

### Post by Drood on 2009-11-04
HI, ever since Karmic Koala, when I do any Mildy CPU intensive task my laptop over heats and shuts down. Ex: Moving different sets of files form one partition to another, watching long flash videos (5min ++), among others. I know its not a laptop specific problem since playing WC3 on Windows 7 works fine for long periods of time and I bet thats more CPU intensive or at least more video intensive than playing a flash video. Anyways, I have a Toshiba L355D-S7901 . 

Again, this is only since Karmic. Also, my laptop has a AMD Turion x2 64 bit processor, I'm running Karmic 32bit. Any suggestions?

---

### Post by 00ber n00b on 2009-11-04
For frequency scaling what do you have it set to?  Performance?  I have the same problem, if I leave it on performance mode it over heats...I have to put it in ondemand mode so it won't over heat.

---

### Post by Drood on 2009-11-04
I do not know where to change this option but, I added the CPU frequency monitor to the panel, and when I mouse over it says *Frequency*OnDemand

---

### Post by 00ber n00b on 2009-11-04
> **Drood said:**
> I do not know where to change this option but, I added the CPU frequency monitor to the panel, and when I mouse over it says *Frequency*OnDemand

Is it still over heating when set to ondemand?

---

### Post by Drood on 2009-11-05
Yeah, well as far as I know. I have not changed it, it has been on onDemand all along.

---

### Post by Gawains Green Knight on 2009-11-05
It could be frequency scaling - I use cpufrequtils to manage mine (I have a cloudbook which is another story).

May be unrelated, but I used to have update manager go crazy and cause my computer to fry... have you typed top to see whats running? Even on performance it shouldn't get hot if nothing is running.

---

### Post by 00ber n00b on 2009-11-05
> **Gawains Green Knight said:**
> It could be frequency scaling - I use cpufrequtils to manage mine (I have a cloudbook which is another story).

May be unrelated, but I used to have update manager go crazy and cause my computer to fry... have you typed top to see whats running? Even on performance it shouldn't get hot if nothing is running.

Mine gets hot with just firefox open and shuts off in a matter of seconds.

---

### Post by 00ber n00b on 2009-11-05
I have to scale down my cpu so it won't over heat.  It would be ok but, while im in ondemand mode embedded youtube playback is really glitchy.

---

### Post by Drood on 2009-11-06
Yup, it keeps overheating. How do you use that tool you mentioned (cpufrequtils )?

---

### Post by schiotz on 2009-11-06
Often, when a laptop overheats it is due to dust accumulating on the CPU cooler plate.  You can get cans of compressed air in electronics equipment stores, blowing air in through the air outlet of the laptop (while turned off!) will often loosen this just, and blow it out.   I had success with an overheating Dell Inspiron doing just that.

/Jakob

PS.  Windows probably just detects the problem, and throttles down the cpu.

---

### Post by 00ber n00b on 2009-11-07
Wish mine would throttle down...instead it just shuts down.

---

### Post by 00ber n00b on 2009-11-07
I don't know what its called.  Just go to a panel, right click, select freq. scale monitor.

---

### Post by JBAlaska on 2009-11-07
Are you sure it's the CPU overheating and not the GPU? The reason I ask is that watching flash video makes my laptop GPU temp go way up. If this is the case, that would be the reason CPU scaling has no effect on your problem.

If you install lm-sensors and GNOME Sensors Applet or gkrellm, you can monitor your CPU, chipset, GPU and HD temps and see which is causing your shutdowns.

Also if your lappy is free of dust etc, you might try a cool pad, they can help quite a bit.

---

### Post by 00b00nt00 on 2009-11-07
Check for fluff and other stuff blocking the vents (they do get choked eventually).

That said, a laptop should be able to run at full throttle continuously without shutting down. Maybe there is a hardware problem?

---

### Post by Vince N on 2009-11-15
Just adding my two cents.  I have an Acer aspire doing the same thing.  It's only been since Karmic so whats the deal?  It runs fine with Windows or previous versions of Ubuntu and I keep my laptop well maintained so I don't think you can blame it on the hardware.

---

### Post by Vince N on 2009-11-15
Try this

Apparently the issue has to do with some kernal updates that were done that caused the fan support in the Acer Aspires to regress causing the fans to slow down or not work at all.  They have a fix in place with a newer kernal thats not part of the main repositories yet.  I'm running it right now and my CPU is running much cooler though I haven't tested it under load yet.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)

---

### Post by radixor on 2009-11-25
I am having this exact same problem, I had to switch to Windows so I can watch videos again. 

I normally run 9.04 @ work and on my desktop PC, but I like to do some coding on my laptop sometimes and maybe watch some youtube. 

Any more than 5 minutes watching a flash video, and the laptop just  overheats considerably. Also, it doesn't run as quiet as when it is on Windows. 

I can see it go up by writing a small python script to constantly poll for sensors and detect a variance of greater than 5 degrees, and my laptop goes from 58 degrees when idle to a whopping critical 105 degrees and proceeds to shut down.

I am, like the OP, also using AMD Turion x2 64bit Karmic and it has ATI Radeon graphics. The laptop is a Toshiba Satellite L305S-S5983 and it's exactly one year old -- so not exactly an old model.

Any help, advice, or steps to remedy this issue would be much appreciated!

---

### Post by tliketea on 2009-11-25
...same problem here, after a kernel update my system became USELESS ^^ I have 90% system load and more than 10° increase in CPU temperature on a plain desktop -- nice development ubuntu guys! :-S 

"Hello Windows!"

...


Btw: everything was fine before, so it's no hardware issues.

---

### Post by Vince N on 2009-11-25
> **radixor said:**
> I am having this exact same problem, I had to switch to Windows so I can watch videos again. 
 
I normally run 9.04 @ work and on my desktop PC, but I like to do some coding on my laptop sometimes and maybe watch some youtube. 
 
Any more than 5 minutes watching a flash video, and the laptop just overheats considerably. Also, it doesn't run as quiet as when it is on Windows. 
 
I can see it go up by writing a small python script to constantly poll for sensors and detect a variance of greater than 5 degrees, and my laptop goes from 58 degrees when idle to a whopping critical 105 degrees and proceeds to shut down.
 
I am, like the OP, also using AMD Turion x2 64bit Karmic and it has ATI Radeon graphics. The laptop is a Toshiba Satellite L305S-S5983 and it's exactly one year old -- so not exactly an old model.
 
Any help, advice, or steps to remedy this issue would be much appreciated!
 
Are the fans running in the laptop at all when it's overheating?  If not did you try the kernel update above?
 
Also just in case it IS the hardware did you take a can of air to vents just to make sure it wasn't dust buildup?  COuln't hurt in any event.

---

### Post by yossell on 2009-11-25
My own practice for my dell1330 - which has the infamous problematic nvidia8400 chip, is to run powertop - [http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

Without this, my computer used to run hotter and the battery life was shorter. It may be of some help, although I'm not sure if it will make a big difference if the computer is continually being stressed.

---

### Post by radixor on 2009-11-25
> **Vince N said:**
> Are the fans running in the laptop at all when it's overheating?  If not did you try the kernel update above?
 
Also just in case it IS the hardware did you take a can of air to vents just to make sure it wasn't dust buildup?  COuln't hurt in any event.

Fans look like they're running, but I think it's only some fans that are running. Maybe not GPU fans? Although since this is a laptop, it's most likely embedded. Since it's AMD as well, I can almost be 99% positive of this.

I tried a few things, like modifying grub to have acpi = off, but that didn't do anything substantial. I honestly do think that maybe the fans aren't running full speed?

I'll try the can of air, you're right it probably wouldn't hurt.

---

### Post by Groszman on 2009-11-26
I had the same problem because I'm also an acer aspire 5315 user. After I had done the kernel updates everything went out ok. But then I did the routine update and found myself right at the beginning. Then I reinstalled the kernel updates as desscribed but the laptop 5315 still keeps turning off because the cpu is overheating.

---

### Post by Vince N on 2009-11-27
I recently did some system updates and found my fans not working again.  A quick restart seemed to resolve it and now my system is running ok.

I seriously think there's something buggy with these Aspire's though I wish we could pin down exactly what it was.

---

### Post by Groszman on 2009-11-27
Now something great happend: I tried to reinstall the kernel updates. during the reinstallation of hte linux-image the laptop overheated again and the system crashed. now I'm unable to open synaptic or to reinstall the linux-image. synaptic says I should report the problem. any Idea how to go on?

---

### Post by Groszman on 2009-11-27
Update Manager could uninstall the incomplete linux-image file and I could reinstall it. but anyway: since the latest update my fans are only working when the laptop shut down one time an I restart it immediately. seems like the update made the former kernel updates useless.

---

### Post by mhstn on 2009-11-27
why don't you just edit your reply and describe how you solved the problem?
 
might help somebody else with the same problem

---

### Post by johny_ on 2009-11-28
Exactly! Mhstn is right.

---

### Post by szopin on 2009-11-29
Same problem on Asus F3 laptop. After upgrade started shutting down randomly. Anybody knows if this has been reported/is being worked on? Not sure whether to reinstall Jaunty, or wait for updates.

---

### Post by Groszman on 2009-11-30
The discussion on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337) already went a bit further:
My problem seems to be the latest kernel update which installed 2.6.31-15-generic on my lap. Me and other users have no idea how to get back to the 14-apw.
The other thing with acer laptops is, that there is a BIOS update neccessary. Currently I' using BIOS 1,3x. According to other users Version 1.43 fixes the problem. But: BIOS Update seems to be a highly complicated issue. up till now the manual to do that postet on launchpad ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337/comments/41](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337/comments/41)) didn't worked for me.

---

### Post by Groszman on 2009-12-02
I have finally solved the fan problem for my laptop. Most of the Acer modells need a BIOS update if you want to run it with ubuntu. but you have to take care - using the worng bios can damage your computer to stop functioning at all. the latest BIOS versions according to laptop modells can be found in the notebook folder here:
[http://support.acer-euro.com/drivers/ftp/ftp.html](http://support.acer-euro.com/drivers/ftp/ftp.html)

If you run a parallel windows system, you can download an .exe file which will flash your BIOS. If not, you need to create a FREE DOS iso image containing the BIOS driver. How to do that can be found here:
[http://www.tummy.com/journals/entries/jafo_20080920_234755](http://www.tummy.com/journals/entries/jafo_20080920_234755)

If you're user of an acer aspire 5315, you can use the iso file, angel garcia created. it worked properly for me. Do the following:
1. Download iso file from:
[http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz](http://dl.dropbox.com/u/221701/FDOS_v1_43.iso.tar.gz)
2. Burn it
3. Reboot laptop and hit F2 directly in the first screen to enter BIOS. Make sure that your CD Drive ist the first boot drive. Save and Exit
4. Choose: "1) Continue to boot FreeDOS from CD-ROM"
5. Choose: "1) Install to harddisk using FreeDOS SETUP"
6. Don't be afraid: Setup won't install Free Dos to harddrive. Instead you end up on prompt X: - change directory to firm (enter: "cd firm")
7. start "if50.bat" by entering it. That'll flash your BIOS. Afterwards your fans should work properly.

---

### Post by Drood on 2010-11-25
Fnny, a year later I did a search on google for the problem with the laptop/fan overheating and ran into my post. I am still having the same problem. I do not know if this matters but out of curiosity I ran the command fan and got this:


@alx-laptop:~$ fan
fan: laptop does not have cooling fan or kernel module not installed.

Are there any known solutions at this point ? 

Update, I am now running 10.10 on my laptop, and still have the same problem.

---

