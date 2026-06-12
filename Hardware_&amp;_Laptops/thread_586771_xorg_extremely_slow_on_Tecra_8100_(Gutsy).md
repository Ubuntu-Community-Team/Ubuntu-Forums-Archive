---
title: "xorg extremely slow on Tecra 8100 (Gutsy)"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by borkbork on 2007-10-22
I finally got 7.10 installed on my Toshiba Tecra 8100 laptop the other day and am having some serious problems with X performance. I'm using the savage driver, which matches the video card, but it actually runs about the same speed as using the vesa driver. For instance, on the gdm login screen it takes it about a second to just paint the background image. It looks like all the hardware acceleration is disabled for some reason.

XFCE is actually slower than Gnome. When I log in with the former and have the just the system manager running in the taskbar it basically pegs the cpu with the process monitor and Xorg processes splitting the cpu time.

This laptop is not _that_ old, so I can't see any reason for it to be running this slow.

Anyone else run into a similar issue or have some ideas? thanks

---

### Post by munka on 2007-10-23
Hi borkbork

This is not so much a reply than a chorus, I  have exactly the same laptop, and I am suffering the same problem, it's like the device is moving through molasses, it takes about 20 min to boot, though I fear that my problem maybe hardware, as this slowdown coincided with a bios update, never the less I will watch this thread with interest for some hint of a solution.
cheers Munka

---

### Post by borkbork on 2007-10-23
Glad to hear I'm not completely out of my mind.

I'm not convinced it's a hardware problem because I've tried some other live cd's (for instance, Puppy Linux) and everything is quite snappy. The has to be some (or multiple) settings that are causing the issues, I just can't seem to figure out what they are.

I'll keep you up to date with what I figure out, but it's looking like I might just have to go with another distribution. Bummer...

---

### Post by munka on 2007-10-23
This gets stranger and stranger, because I had done a bios update it had reset all the conditions previously set by the Toshiba common app's and windows/Toshiba bios tweaks, I ran CPU benchmarks, and my CPU was running at a blistering 114.82mhz.

I installed XP on a second partition and reinstalled the common app's and Toshiba bios tweaks, and now under XP it is working fine, full speed, but gutsy is still so slow as to be unusable, but here is where it gets strange, if I throw in a feisty live CD it runs full speed??

borkbork have a look at toshutils [http://www.buzzard.me.uk/toshiba/index.html](http://www.buzzard.me.uk/toshiba/index.html) that may help your problem, I spent the best part of the day trying to get my gutsy install to work again, must do some work today, but I will get back here to check in.

---

### Post by borkbork on 2007-10-25
Finally had some time to look at this a little more. It's definitely not limited to X. I ran hdparm to test the disk performance and it's incredibly slow (8-15 Mb/s) so that miight be a root cause. I'll poke around and see if there's another thread that provides a hint about what might be wrong here.

---

### Post by borkbork on 2007-10-29
So I 'fixed' this by rolling back to edgy, which performs fine. The problem seems to be with the new kernel which uses SCSI drivers to emulate support for the older PATA disks, and the performance is crap.

There are any number of threads describing the problem (just search for slow hard drive, etc), but disappointingly no concrete solutions. I tried a couple of the recommended fixes, but nothing worked. Given that there is no shortage of people with this problem, maybe future updates will improve the situation. But for now it looks like I have to run a version that has an older release of the kernel.

---

### Post by Szelev71 on 2007-10-31
Dear All,

I am hapy to not facing alone with mentioned problem and found this topic.
I am totally new at Xubuntu.
Can you please recommend which older version can work by normal speed on Toshib Tecra 8100 (600MHZ, 12GB HDD, 256MB RAM, 8 MB VGA)
Thank you!

---

### Post by Craigus on 2007-10-31
I had this issue on my Toshiba 3490CT (700 MHz Pentium M, 256 Mb). I ended up going back to Dapper / Xubuntu, which runs nicely.

Interestingly, I installed Fluxbuntu 7.10 on my Toshiba Satellite PRO 4300 (600 MHz Pentium M, 192 Mb) and that runs fine.

---

### Post by arisjr on 2007-11-05
toshiba m45-s355, after upgrading, became extremely slow. 

Doing a scroll-down on a window is absolutely painfull and slow. Other things became slow also. 

I have 1gb of mem, and it never gets fully used. processor also is not the problem. 


Upgrading to Gutsy was indeed a bad idea.

---

### Post by borkbork on 2007-11-06
From the other threads that mention the harddrive speed issues, it appears the problem was introduced with kernel version 2.6.20. Anything prior to that appears to work fine, which is why I'm using edgy which has 2.6.17.

I'm not sure that other package versions aren't important as well, but the kernel version definitely seems to be the big issue.

---

### Post by Ahti30708 on 2007-12-17
Workaround: keep using Gutsy but downgrade the kernel to 2.6.20-16.

* * *

On my Tecra 8100 Gutsy works fine with kernel 2.6.20-16. Hdparm reports 7.67 MB/sec. With the 2.6.22-14 kernel hdparm reports about 2 MB/sec.

I have a similarly configured Fujitsu-Siemens Lifebook C series which I used to troubleshoot the Tecra 8100 - both have the Intel BX chipset and a 500 MHz CPU. The Lifebook has no problems with the 2.6.22-14 kernel so it could be a compatibility problem between the BIOS and the SCSI driver.

* * *

I use Xubuntu with some packages from Kubuntu (kcontrol, kwlan, konqueror, kpat).

---

### Post by ubu-wan on 2007-12-23
Same here: Toshiba Tecra 8100 with 700 MHz and 384 MB. This is what I am using -- Gutsy but with the earlier kernel from Feisty, as I first installed Feisty and then upgraded to Gutsy. It's a pity this problem exists with the 2.6.22-14 kernel on these (and other) perfectly capable machines. It means that for now, there is no further upgrade possibility on this laptop unless the next kernel resolves this!

ubu-wan

---

### Post by dmizer on 2008-03-23
bump for this.  same problem.

700mhz pIII with 256 meg of ram running xubuntu.

gutsy:
takes over 10 minutes just to boot.
log in screen draws.
after log in, xfce takes another 5 minutes to load.
terminal takes more than a minute to load.
typing at anything over 10 words a minute fills the buffer very quickly.
machine is basically useless.

in dapper:
less than a minute to boot.
can play DVDs without thinking twice.
extremely responsive, usable machine.

don't even know where to start troubleshooting this one, and there's little to no help in google.

---

### Post by dmizer on 2008-03-23
found the culprit.

disabling acpi enables the machine to boot and function quite quickly.

HUGE problem with that.  the tecra 8100 bios REQUIRES acpi in order to allow the cpu fan to function.  without it, the notebook simply cooks to death.

any ideas?

---

### Post by dmizer on 2008-03-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/138423](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/138423) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				sorry, double post to add possible bug link from launchpad.

report is that this problem has been fixed in Hardy.  there are no plans for a back fix for gutsy.

---

### Post by ubu-wan on 2008-03-24
> **dmizer said:**
> found the culprit.

disabling acpi enables the machine to boot and function quite quickly.

HUGE problem with that.  the tecra 8100 bios REQUIRES acpi in order to allow the cpu fan to function.  without it, the notebook simply cooks to death.

any ideas?

Thanks, I just tried this and it does indeed run as well with the 2.6.22-14 Gutsy kernel as with the 2.6.20-16 one I kept from Feisty.

Only thing is, mine seems to be cycling the fan on and off normally, so not cooking itself! Just the battery information is missing but apart from that it is usable.

Hope this helps with the permanent fix...


ubu-wan


:guitar:

---

### Post by dmizer on 2008-03-24
thanks for the info.  i will try again, but my experience with this laptop has been that the fan does indeed come on, but far too late, and far too short.  in fact, early in my linux experience the laptop got hot enough to damage a pcmcia wireless adapter.

edit:
had to upgrade to the hardy kernel in order to get the cpu fan to work correctly.  obviously, the good news is that the problem seems to be fixed in hardy.

---

### Post by ubu-wan on 2008-03-25
Hi dmizer,

Good info on the too little, too late fan operation; one to watch I think! I only tried it once to see if it worked but would be great to have it permanently fixed as wireless etc. in Gutsy kernel is far better automated for my Draytek PC card.

I am taking your caution about the possibility of damage to the PC cards seriously! I assume you are using a beta of Hardy? I couldn't see anywhere to download it, although not long now until release anyway... At least as you say the issue should be fixed in that one!


Regards, ubu-wan


:guitar:

edit: found the mirrors for the beta, but will probably wait for release

---

### Post by dmizer on 2008-03-25
> **ubu-wan said:**
> I assume you are using a beta of Hardy? I couldn't see anywhere to download it, although not long now until release anyway... At least as you say the issue should be fixed in that one!
no, i did not upgrade to hardy, i only upgraded the kernel.  here's the howto i used:

[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755)

i had 3 of these machines.  one burned through a memory slot.  one got so hot as to warp the plastic below the processor (same one that damaged the pc card).  it seems that the cpu will continue to run even if the critical temperature levels are reached.

with a working acpi, i simply add this command:
```
echo "force_on:1" > /proc/acpi/toshiba/fan
```
to /etc/rc.local which causes the fan to stay on at full speed.  initially, i had tried multiple methods to control the fan, but they were often flaky.  so i just left the thing running all the time.  my thinking is that it's better to have a constantly running fan than a dead computer.

---

### Post by ubu-wan on 2008-03-25
> **dmizer said:**
> with a working acpi, i simply add this command:
```
echo "force_on:1" > /proc/acpi/toshiba/fan
```
to /etc/rc.local which causes the fan to stay on at full speed.  initially, i had tried multiple methods to control the fan, but they were often flaky.  so i just left the thing running all the time.  my thinking is that it's better to have a constantly running fan than a dead computer.

Interesting... when I tried running with acpi=off I specifically went looking in /proc and there was no /acpi directory, hence no /toshiba directory either. There was a /proc/apm though :confused:
Back to 2.6.20-16 and /proc/acpi was back...

I think I will wait for release!


Regards, ubu-wan


:guitar:

---

### Post by dmizer on 2008-03-25
> **ubu-wan said:**
> Interesting... when I tried running with acpi=off I specifically went looking in /proc and there was no /acpi directory, hence no /toshiba directory either. There was a /proc/apm though :confused:

if you run with the "acpi=off" kernel option, then there will be NO /proc/acpi directory.  the hardy kernel will allow you to run with acpi _enabled_ (no kernel options other than "ro" and "splash" are necessary), thereby giving you the /proc/acpi/toshiba directory.

iow "acpi=off" makes the machine work at speed in gutsy, but does not allow the fan to work.  if you upgrade to the hardy kernel, the "acpi=off" option is not necessary, and the fan /should/ function normally, though i would keep an eye on the temperature and if it gets out of hand, you can try the fix i posted earlier.

---

### Post by ubu-wan on 2008-05-04
Update: upgraded to 8.04 release and all is resolved. My Tecra 8100 chugs along nicely now with the 2.6.24-16 kernel. I will wait to give it a good test before ditching the old 2.6.20-16 though... :KS


Regards,


ubu-wan

:guitar:

---

### Post by Szelev71 on 2008-05-23
I can also confirm:
2.6.20-16 generic kernel solved temporary the 'very slow' problem but now Hardy Heron (8.04) solved it for first installing. Works fine and no problem! :) :lolflag:

Thanks Hardy Heron you are really HARDY!

---

