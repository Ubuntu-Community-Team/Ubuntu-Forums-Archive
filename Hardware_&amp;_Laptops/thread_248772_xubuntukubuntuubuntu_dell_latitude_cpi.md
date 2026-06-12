---
title: "xubuntu/kubuntu/ubuntu dell latitude cpi"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by newb_not_noob on 2006-09-01
iv bin getting the same problem with ubuntu/kubuntu/xubuntu on my dell latitude cpi. it will only boot 1/3 times. i tried more ram (taking it to 256) and a new hard drive (30GB) to get it to work, but now i have no idea whats causing this. any help would be greatly appreciated.

thanks

---

### Post by newb_not_noob on 2006-09-01
oh, i forgot to mention, when it doesent boot up, it gets stuck on "loading hardware drivers"

---

### Post by newb_not_noob on 2006-09-01
now it wont even boot 1/3 times, its less than that now!

---

### Post by thisguyiknow on 2006-09-01
Hey!  Sorry about your latitude problems.  
I'm no expert, but here's what I would wonder....

Do you have any peripherals that didn't come as stock equipment?  If so, disconnect them and see what happens.  If the problem goes away, try reconnecting them one at a time:  see if one makes the problem come back.  Hardware compatibility is the only issue holding linux back from immediate world domination, IMHO:=)

Did the behavior change ["now it wont even boot 1/3 times..."] immediately or soon after you put the new memory in?  Are you positive the dimm meets dell's specs exactly?  Try running the memtest86+ option on the grub menu [press the 'esc' key as soon as the dell logo screen fades]: you might have started out with a bad dimm in the first place.  The tests will probably take about 20 minutes to complete all passes.

Was some other, un-named, OS loaded on the machine originally?  Is the 30-gig drive replacing or in addition to the original hdd?  That is, is the machine booting from the original installation, or a fresh install.  Did you start with a clean installation [newly formatted /, /boot, and /swap directories]? 

Have you changed any of the driver modules that are loaded at startup?  Is this the stock kernel, or did you or a friend or someone else compile it?

Have you looked at the logs?  They may help identify where the problem is occurring.  Boot the machine into the rescue mode of the latest kernel version on grub's menu [press the 'esc' key immediately after the dell logo screen clears to view the menu]. Look in /var/log and use your preferred editor or "less" [$ less /var/log/LOGNAME] to check for reports of problems in: dmesg (which should have a record of the boot process, including modules loaded and any errors/failed's); kern.log; syslog [more for post-boot system information]; & messages [where some kernel messages are logged].  It's probably not an X problem [Xorg.0.log] -- X is so delicate that it will just crash with a message to the screen if there's a significant error in its config file.  

Forgive me if you've already done all that and more;

Good luck,
tgik

---

### Post by Melcar on 2006-09-02
I get that same problem when I try to load Ubuntu/Xubuntu on an old Latitude (gets stuck on the detecting hardware part).  Kubuntu loads up and installs just fine... weird.

---

### Post by newb_not_noob on 2006-09-02
well, the ram is fine, it reconised, and the new hard drive was recoonised by the installer. the 30GB had nothing on it, plus i wiped it with the installer on xubuntu (the first thing i installed) but, im not sure if my partitions were all ok.. i just told the installer to wipe the hard drive and put in stuff (i diddent realy read it tbh) but, now its booting 1/3 tiomes, i diddent remove or add anything.


the RAM was accepted and it showed up in the setup on the laptop.

---

### Post by newb_not_noob on 2006-09-02
perhaps some specs might help?

Internal cache: 256KB
System memory: 256MB
Video controller: NeoMagic 2200
Video memory: 2.5MB
Audio controller: NeoMagic 2200
Primary hard drive: 30GB

---

### Post by newb_not_noob on 2006-09-02
im just running the installer for kubuntu.... i came across a step that says "some pcmcia hardware needs special resource config options in order to work" and it mentions freezing and dell laptops

---

### Post by newb_not_noob on 2006-09-02
well, i installed kubuntu, i changed the partitions. (wipe disk, create partitions and ide (or something like that, the third option) and, when the pcmcia screen came up, i typed the code it mentioned for dell laptop on the screen, (exclude port 0x800-0x8ff)

now, it boots 2/5 times

---

### Post by thisguyiknow on 2006-09-03
> **newb_not_noob said:**
> well, i installed kubuntu, i changed the partitions. (wipe disk, create partitions and ide (or something like that, the third option) and, when the pcmcia screen came up, i typed the code it mentioned for dell laptop on the screen, (exclude port 0x800-0x8ff)

now, it boots 2/5 times
hey again,

i still think you ought to take a look at your logfiles.  One or another of them might just tell you exactly what's happening when the boot process halts -- that's what they're there for! ;-)  If you can start the x window system, try using the logfile viewer [System>Administration>System Log].  just look at one file, kern.log [in the log viewer, do Log>Open>(/var/log/)kern.log.  this will let you look at each step of each time you booted the machine during the past few days -- so the final entries for any of your failed boots may tell you which device is hanging the process.  at the very least, you should know exactly what step has been executed before the system hangs.  see whether it gives you an explicit message, like "blahblahblah is blahblahblahing: exiting".  then the culprit, as far as the kernel is concerned, is the device blahblahblah.  if, for example, it's got something to do with the pcmcia system, that's where the log should show the crash -- when it's trying to do [something] involving that system.  if it's way past loading and configuring the pcmcia system, and doing something seemingly unrelated, you can shift your troubleshooting focus to the something.  (not forgetting, though, that you've been warned that there's something buggy about pcmcia -- so maybe pcmcia is causing a conflict when the drivers for some other device are loaded, for example.)  if the log allows you to narrow your focus, you may suddenly see exactly the right thread/howto/tip to get past whatever's wrong.

really, it can't hurt and might be a great help!

best of luck,
tgik

---

### Post by arkhitekton on 2006-09-03
I've got a Latitude 266CPi which I've installed 6.06 on.  It's fairly vanilla - 40GB hard drive, 256MB RAM, CD-ROM.  I've had no problems once the 6.06 install worked.  The trick I found there was to use the Alternative Install CD, Text install.  I read on a forum/blog that this install works as the overhead is lower.  BUT once the installation has worked the CPi works fine with Gnome.

As mentioned previously in this thread, it may be some additional hardware that is causing a problem.  I put all the PCMCIA cards into the slots before running the install.  I run a PCMCIA Ethernet card which was detected on install straight out of box.  With respect to memory range exclusions, I've always accepted the default.  Also I did get a Linksys PCMCIA wireless card to work well under 5.10 using ndiswrapper.  (I even got the CPi to compile ndiswrapper straight from the latest source.)  I didn't bother this time as I found that each update requires ndiswrapper to rebuilt from the source as I didn't use the version that comes with the distribution.  (Of a varity of reasons I haven't got the CPi with me at the moment so I'm unable to give the exact hardware and card details.)

I'm not sure I've given any direct help.  But at least you know it is possible to get Ubuntu on a CPi 266.  (Because of my success with the CPi I've now put 6.06 with 686 SMP kernel on an Inspiron 9100 and Dimension 3100c.)

---

