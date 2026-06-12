---
title: "Hard Drive Clicking"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by Jbloudg20 on 2007-01-04
Hey all,

I have a brand new laptop (three days old), Lenovo 3000 N100. I have edgy installed, and everyhting is working fine (except the fingerprint reader, but thats for another time). 

The problem is somethign is accessing the harddrive every 5 seconds or so. I confirmed this using Gkrellm. Everytime whatever it is access, it makes the harddrive make a clicking sound. Any idea what it cold be? I did notice it after I installed gkrellm (I like to use it anyway), but I jut removed it to see if that caused the clicking. I'm about to reboot to check it out.

I'd like to note, it does not click while sitting at the login screen.

---

### Post by earobinson on 2007-01-04
this sounds like a hw problem no?

---

### Post by Jbloudg20 on 2007-01-04
No.

The drive is being accessed... it is not clicking on its own.

I just verified it does not click in either Windows or Fedora Core 6

---

### Post by hardyn on 2007-01-04
"click" isn't a great discription. most notebook drives "park" more often than desktop drives, if you purchase a new notebook drive most of the documentation tells you to expect some noise.

that said, a hard disk is going to fail right away, or after a really long time; keep backed up.  you will have 1-2 years of warranty on the machine, so don't get too excited just yet.  however do watch for bad sectors, odd LED behaviour or changes in the noise.

---

### Post by Jbloudg20 on 2007-01-04
I Don't think you are listening to me. I'm not worrying about hardware failure. I am about 99% sure the drive is fine. It is something wrong with UBUNTU. 

this isn't drive parking... it makes a fairly audioble click every 5 seconds. I'm not talking about normal noises here. I DO know what I'm tlaking about, I DON't know what the cause is.

Windows and fedora core are perfectly fine. Ubuntu is the cause of the problem.

---

### Post by hardyn on 2007-01-04
their are ALOT of IBM / linux specific forums, tried any of those yet?

---

### Post by Jbloudg20 on 2007-01-04
I have not yet, but if I continue to have this problem I may have to try it, although its not a linux problem perse.

As I said, Fedora works fine.

---

### Post by jmakus on 2007-01-04
I saw this problem from the battery applet on my computer.  However this was under Fedora Core 5.

Maybe check that out?

Thx
Jeff

---

### Post by Jbloudg20 on 2007-01-04
I will check that out. Thanks!

I think it may have been gkrellm, though. I removed it and I don't hear the loud clicking anymore...

I'm also being paranoid since this is my brand new laptop :)

---

### Post by Jbloudg20 on 2007-01-28
It wasn't gkrellm, as I'm sitting here, listening to this loud clicking.

---

### Post by rphelps on 2007-02-03
I am experiencing the same annoying problem. Something is accessing the harddrive every few seconds. I thought maybe slocate or locate was update the database (a similar problem I noticed with Suse some years ago) but I have not figured out what is causing it.

---

### Post by rasmusbp on 2007-02-21
I seem to have the same problem. It's only been a problem since after I upgraded to Edgy. The click sounds every 5-10 seconds.  No clicking in Windows or at the log-in screen. 

Someone please help... 

Thanks,
Rasmus

---

### Post by serag on 2007-02-21
This also happens to my new HP DV9010 with 6.10 64 bit.  HD clicks and HD led lights up every 5 seconds or so(it doesn't do it all the time, but once it starts it continues until i reboot/shutdown).  Confirmed that it doesn't happen in WinXp and did ran the HD test in the HP bios and it confirmed that the drive is fine.

---

### Post by gmarton on 2007-02-23
I confirm clicking on Lenovo 3000 N100 - Dapper.
I re installed the OS for a different reason and it stopped for about a week, now its back again :(

---

### Post by jotagab on 2007-02-23
Check /var/log/messages and /var/log/syslog to see if whatever is accessing your disk leaves a trace...

---

### Post by gmarton on 2007-02-23
Shows no activity with that time interval...

---

### Post by rfdparker2002 on 2007-02-25
I, myself, have just (on the 16th) got a Lenovo 3000 n100 from 'The Linux Emporium' which came with Ubuntu 6.06.1, but I'm pretty sure the sound of the hard drive being accessed has got quite louder since upgrading it to 6.10, but I'm not sure about the amount it gets accessed. Also I ran the Ubuntu Device Database program (I *think* it was after upgrading to edgy), but the  website has very little info on it and thinks its a desktop: [http://hwdb.ubuntu.com/?xml=d1b0fe0f1de0add10d39465af746ab7b](http://hwdb.ubuntu.com/?xml=d1b0fe0f1de0add10d39465af746ab7b)

---

### Post by esaym on 2007-02-25
> **Jbloudg20 said:**
> I Don't think you are listening to me. I'm not worrying about hardware failure. I am about 99% sure the drive is fine. It is something wrong with UBUNTU. 

this isn't drive parking... it makes a fairly audioble click every 5 seconds. I'm not talking about normal noises here. I DO know what I'm tlaking about, I DON't know what the cause is.

Windows and fedora core are perfectly fine. Ubuntu is the cause of the problem.

Yes it is a problem with the 2.6 kernel in general:

[http://ubuntuforums.org/showthread.php?t=79055](http://ubuntuforums.org/showthread.php?t=79055)

You got to disable it with hdparm -B255 or B254 or B0 (which ever works, hard drives are all different.)

---

### Post by Talz on 2007-02-25
i had a problem like this also   the hd on my hp dv6000t was doing the same thing
i found the solution by editing the read ahead settings in the laptop mode config file

the file is in ect/laptop-mode/
labled laptop-mode.conf

if u open your text editor with sudo

about a third of the way down you should find the read ahead settings   
try settin them both (LM and NOLM) to 3072

your lines look like this
LM_READAHEAD=3072
NOLM_READAHEAD=3072

make sure right above thoes that CONTROL_REASAHEAD = 1

so 

that should solve your problem

if not   it wont hurt anything

---

### Post by rasmusbp on 2007-03-01
Talz, I tried to use your advice reg. the "readahead" parameter, but I experience no change or effect, sorry. 

By the way, the clicking sounds (on my laptop) sounds EXACTLY like the sounds the hard drive makes the second before the laptop shuts down (as Ubuntu has finished its shutdown process). Don't know if this will mean anything to someone... 

Cheers
Rasmus

---

### Post by esaym on 2007-03-01
> **rasmusbp said:**
> Talz, I tried to use your advice reg. the "readahead" parameter, but I experience no change or effect, sorry. 

By the way, the clicking sounds (on my laptop) sounds EXACTLY like the sounds the hard drive makes the second before the laptop shuts down (as Ubuntu has finished its shutdown process). Don't know if this will mean anything to someone... 

Cheers
Rasmus

Did you see the thread I posted above?  The heads in the laptop hard drive are parking.  The 2.6 kernel causes them to do it in about 5 seconds of inactivity.  In windows for what ever reason it is set to something more like 60 seconds of inactivity.

Since the heads are parking when they are not supposed to it will wear out within a year or so.  The hard drive is only rated for so many parks.

This IS a bug.

Until this problem is fixed you can disable this "feature" with

```
sudo hdparm -B254 /dev/hda
```

or
for sata drives
```
sudo hdparm -B254 /dev/sda
```

---

### Post by rasmusbp on 2007-03-02
hey easym, thanks a bunch! i did notice the part about "hdparm" earlier on, but since I'm a completely noobie, I didn't realize the significance of it... but I'm grateful for your advice, I would have been sad to have destroyed a fine hard drive over something as silly as that!

My output from the hdparm command - I assume it's ok if I don't get any comments...

> rasmus@rasmus-laptop:~$ sudo hdparm -B254 /dev/hda

/dev/hda:
 setting Advanced Power Management level to 0xFE (254)


Thanks again - let's hope a new and improved kernel is coming soon!
Rasmus

---

### Post by drpaul on 2007-03-02
I'm working on a HP dv6150us with a MATSHITA hd.

Tried the hdparm trick with 254, 255, and 0. None affected the clicking. :confused: 

Paul

---

### Post by drpaul on 2007-03-02
More data:
unplugging the power cord stops the clicking.

I just changed the readahead parametei, rebooted on battery, and plugged in power cord.
     ==>no clicking!

So for me there is a solution.

Thanks.

Paul

---

### Post by esaym on 2007-03-03
> **rasmusbp said:**
> 

My output from the hdparm command - I assume it's ok if I don't get any comments...


The comment you should have gotten is the hard drive not clicking anymore if it worked:)

---

### Post by esaym on 2007-03-03
> **drpaul said:**
> More data:
unplugging the power cord stops the clicking.

I just changed the readahead parametei, rebooted on battery, and plugged in power cord.
     ==>no clicking!

So for me there is a solution.

Thanks.

Paul


Interesting, I have also never heard of a "MATSHITA hd" ?

---

### Post by treesurf on 2007-03-04
> **esaym said:**
> Did you see the thread I posted above?  The heads in the laptop hard drive are parking.  The 2.6 kernel causes them to do it in about 5 seconds of inactivity.  In windows for what ever reason it is set to something more like 60 seconds of inactivity.

Since the heads are parking when they are not supposed to it will wear out within a year or so.  The hard drive is only rated for so many parks.

This IS a bug.

Until this problem is fixed you can disable this "feature" with

```
sudo hdparm -B254 /dev/hda
```

or
for sata drives
```
sudo hdparm -B254 /dev/sda
```


This solves the problem for me perfectly, thank you!  However, I have to reenter the command each time I reboot.  Is there any way to have this run automatically at start up?

---

### Post by Rui Pais on 2007-03-04
> **treesurf said:**
> This solves the problem for me perfectly, thank you!  However, I have to reenter the command each time I reboot.  Is there any way to have this run automatically at start up?

hi,
add the hdparm value that worked to the file /etc/hdparm.conf (notes inside file are self explanatory)

---

### Post by esaym on 2007-03-04
> **Rui Pais said:**
> hi,
add the hdparm value that worked to the file /etc/hdparm.conf (notes inside file are self explanatory)



I always just use the file /etc/rc.local

Just paste the whole command above "exit 0" and it will execute it on every boot

---

### Post by treesurf on 2007-03-04
Thank you!!

---

### Post by seldenthuis on 2007-03-04
> **drpaul said:**
> More data:
unplugging the power cord stops the clicking.

When you unplug the power cord the laptop_mode_enable function in /etc/acpi/power.sh is executed. This function call a.o. hdparm -S 12 and hdparm -B  1. This will spin the hard drive down after 5 seconds, so you won't hear the clicks.

When you plug the power cord back in the laptop_mode_disable function gets called, which disables the spinning down and runs hdparm -B 255, so this is solution is basically the same as the one esaym posted.

Just to clear things up a bit.

---

### Post by rasmusbp on 2007-03-06
Thanks again esaym! Since I've put the hdparm B254 into the /etc/rc.local file, there are no problems with clicking.  I still feel a bit uncomfortable with the whole thing, though...

Cheers

---

### Post by GordSellar on 2007-03-24
I've discovered something deeply weird. 

I had the click when I started using my PC, but then it went away when I played with some of the configs mentioned here. 

And then, when I started using the supplementary 12-cell battery I bought for the PC, the click returned. Switching back to my old battery got rid of the click. Any thoughts on that? Seems pretty weird to me!

---

### Post by GordSellar on 2007-03-24
weirdly enough, the click returned overnight. I know this is a solvable problem, because I solved it before, though not by anything obvious. Any ideas out there?

---

### Post by zeus77 on 2007-03-27
I can confirm this same clicking sound with my Lenovo N100 3000 (0768 A53 model) running Edgy with kernel 2.6.17-11-generic.  For me, it seems to appear after the computer has been on (plugged into AC) for an extended period of time.  The aforementioned 'hdparm' trick does **not** solve the problem for me.

Switching to battery power solves the problem, as does rebooting (until the clicking comes back hours later).  

Has the hdparm trick solved the clicking for everyone else?

Does everyone else have the clicking at boot up, or only after the computer has been on for awhile?


EDIT: Once the computer has decided to start clicking, a simple (soft) reboot doesn't fix it.  I actually need to power off the whole computer, and then turn it back on.

EDIT2: Since my original posting, I have noticed the following: If I turn on the computer without the AC adapter attached, and then plug it in, it starts making the clicking (and a complete power cycle is needed to stop it).  On the other hand, if I turn on the computer *with* the AC adapter attached, I don't have any clicking (at least not immediately... if I leave it on overnight, I often get clicking the next day).

---

### Post by GordSellar on 2007-04-16
Yes, that's the same as mine. And sometimes I can turn it off, and the clicking starts again, but if I run Windows or leave the PC off for a while, it goes away. It's quite troubling, really. I don't get it overnight very often,but I do sometimes get it, and I do wish it'd stop happening!

---

### Post by zeus77 on 2007-04-17
I upgraded to Feisty beta a week or two ago, and can report the same problem...

I haven't been able to identify any real pattern that causes it... just seems sporadic.   fortunately, it's usually not there, and a power cycle is all it takes to fix it.  still, it's annoying.

---

### Post by weth on 2007-04-18
hi all, I have had the same problem since I bought a laptop (dell inspiron 2200, Hitachi MG2OA5EA hdd) and firstly installed Suse 10.0 and after that Kubuntu and now finally Ubuntu 6.10...I noticed the clicking sound but, well, thought it was the way laptops work :))) and I wasn't worried, though annoyed. I am thankful that today I accidentally came upon this thread and by running 

sudo hdparm -B254 /dev/hda

it seems the problem has been solved, no more clicking :)

btw, it may sound stupid, but is this an issue only with laptops or with desktop hdds too?

thanks a lot again :)

---

### Post by aberry5555 on 2007-04-18
If you want a Winows style Processes list open a terminal and type 

```
top
```

then look for whatever is taking up cpu regularly, as this will more than likely be the culprit.

---

### Post by esaym on 2007-04-19
> **aberry5555 said:**
> If you want a Winows style Processes list open a terminal and type 

```
top
```

then look for whatever is taking up cpu regularly, as this will more than likely be the culprit.

I killed a ton of processes once (killed x and everything) and I still had the problem.  I think it is just random swap file stuff.  The problem is not hard drive access though.  The problems is that for what ever reason the hard drive head parking feature gets a real low time limit on linux versus windows.  I really think a bug report needs to be filed on this. I have never filled one out though.  There are lots of other threads just like this one though....

---

### Post by ShinjiLeery on 2007-04-24
i don't know if it's the same issue, but every time i shut down the laptop the hard disk make the clicking noise as if i press the power button. The problem exists in AC mode or battery mode

Do you have any clue?

---

### Post by drpaul on 2007-04-24
The clicking that most in this thread are talking about comes from the OS parking the hard drive about every 5 sec.

With the latest Edgy kernel, this is happening less frequently than it used to, but when it does kick in the changes to hdparm do not seem to have any effect. the only ways to stop it [for me, hpdv6150us] is unplug the power supply or close down and reboot.

HTH

Paul

---

### Post by fxjr on 2007-04-24
Hi, have you seen this bug report? [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)

I also have this problem and doing the stop_on_shutdown config did the trick for me, at least for while.

I hope it helps.

---

### Post by drpaul on 2007-04-24
Thanks. Obviously a lot of people have the shutdown problem, too. The weird thing about the 5 sec click is it comes and goes. I haven't a clue how to reproduce it. I'm not aware of a bug being filed on it.

Paul

---

### Post by KKTrigger on 2007-04-29
Hi! I have the same problem with my Asus PRO31Jm (and the command sudo hdparm -B254 /dev/sda hasn't resolved the clicking), but I have also a different one. ](*,)  Every time I make an operation or I start an application for the first time I can hear a "loud" noise coming from the hard disk. For example, when I launch Firefox for the first time the hard drive start working an clicking pretty hard for a few seconds. Of course in winxp the harddisk is completely silent (as it should be). How can I resolve this situation? [-o< 

Is my problem connected with the hard drive clicking bug?

Thank you all!! :-)

---

### Post by drpaul on 2007-04-29
That noise when an application starts doesn't sound like the same thing to me.. The clicking that I experience seems to be related to power management code. It disappears on battery operation.

BTW, the occurrence of clicking has decreased greatly with kernel  2.6.17-11-generic #2 SMP on Edgy.

HTH

Paul

---

### Post by Rui Pais on 2007-04-29
> **KKTrigger said:**
> Hi! I have the same problem with my Asus PRO31Jm (and the command sudo hdparm -B254 /dev/sda hasn't resolved the clicking), but I have also a different one. ](*,)  Every time I make an operation or I start an application for the first time I can hear a "loud" noise coming from the hard disk. For example, when I launch Firefox for the first time the hard drive start working an clicking pretty hard for a few seconds. 

I have an identical problem, but in my case it only happens on new SATA drives... haven't the faintest idea why.
The most strange thing is that it seems that only happens when i start apps, not when i read/write data files.

I ended by make all OSs installations on my old ATA drives and /home/* on SATA, a scheme that reduced a lot the noise (btw, not a clicking, but a trrrt-trrrt-trrrt continuously :()

---

### Post by KKTrigger on 2007-04-29
> **Rui Pais said:**
> I have an identical problem, but in my case it only happens on new SATA drives... haven't the faintest idea why.
The most strange thing is that it seems that only happens when i start apps, not when i read/write data files.

I ended by make all OSs installations on my old ATA drives and /home/* on SATA, a scheme that reduced a lot the noise (btw, not a clicking, but a trrrt-trrrt-trrrt continuously :()

I have a SATA too!

I've reported this problem on Launchpad. So if you would like to give your experience, take a look at it ;) : [https://bugs.launchpad.net/ubuntu/+bug/110995](https://bugs.launchpad.net/ubuntu/+bug/110995)

---

### Post by Rui Pais on 2007-04-29
> **KKTrigger said:**
> I have a SATA too!

I've reported this problem on Launchpad. So if you would like to give your experience, take a look at it ;) : [https://bugs.launchpad.net/ubuntu/+bug/110995](https://bugs.launchpad.net/ubuntu/+bug/110995)

Done.
Thanks for reporting it (it sounds so strange that i was reluctant even to decide if its a Linux issue or some weird hardware behavior.

---

### Post by zeus77 on 2007-04-30
As I reported previously, once the clicking starts (which is sporadic, and fortunately happens only about 10% of the time) I actually have to **shutdown** the entire computer to get the clicking to stop... with a warm reboot, the clicking is still there.  It turns out, I have a dual-boot system with Windows.  So, today when the clicking started in Ubuntu, I (warm) rebooted into Windows (without powering off) to see if the clicking persisted.  It did!

I rarely use Windows, so I have no idea if the clicking state would ever get triggered there [i.e. indicating that the problem may be hardware related], but once the clicking gets going under Ubuntu, it does so in Windows, too.  Interesting... 

On a whim, I installed the recent BIOS update for the Lenovo 3000 C200/N100 (v1.07 63ET61WW), though I doubt this will solve the problem... I'll keep my fingers crossed, however.  As an aside, the README for the new BIOS claims the following:  "This BIOS contains a critical processor microcode update to improve system reliability. Lenovo highly recommends that you apply this BIOS update."  

zeus77

---

### Post by KKTrigger on 2007-05-01
> **zeus77 said:**
> As I reported previously, once the clicking starts (which is sporadic, and fortunately happens only about 10% of the time) I actually have to **shutdown** the entire computer to get the clicking to stop... with a warm reboot, the clicking is still there.  It turns out, I have a dual-boot system with Windows.  So, today when the clicking started in Ubuntu, I (warm) rebooted into Windows (without powering off) to see if the clicking persisted.  It did!

I rarely use Windows, so I have no idea if the clicking state would ever get triggered there [i.e. indicating that the problem may be hardware related], but once the clicking gets going under Ubuntu, it does so in Windows, too.  Interesting... 

Zeus do you have a SATA? It seems that this kind of problem appears only with sata hdd... isn't it?

---

### Post by zeus77 on 2007-05-01
yep, i have a SATA.  it's a Fujitsu MHV2120BH.

perhaps you have the same one?  i thought i 
saw somewhere that you had a 2.5" 120GB
drive, which i believe this is...

---

### Post by zeus77 on 2007-05-01
was doing a little searching, and indeed it seems 
people with these Fujitsu drivers running Windows 
are also reporting the same periodic clicking sound.
thus, i am starting to wonder if there is a problem 
with the Fujitsu MHV2xxx series.

as expected, upgrading my BIOS didn't fix the problem.
however, i just found an upgrade for the firmware 
on the SATA drive (old version: 00840029, new version:
0084002A), so maybe this will fix it...

---

### Post by drpaul on 2007-05-01
I've got a 120 GB Matsushita SATA and it certainly used to do the ckicking. Haven't experienced it in a few days, but I don't think that I've had kernel or driver updates since my last clicking episode.

FWIW

Paul

Correction: that's a Fujitsu.

---

### Post by zeus77 on 2007-05-02
well, the Fujitsu firmware update didn't solve it... still clicking away.

---

### Post by Pwwn3d on 2007-05-03
I hope this can be sorted soon, this is a pretty worrying noise. I have access to quite a few FUJITSU MHV2xxxxx hard drive based laptops.

I can confirm this problem is existant on kubuntu, and windows too in some cases. Surely all the drives can't be faulty?

---

### Post by Pwwn3d on 2007-05-03
Hmm, 

```
sudo laptop_mode start
```

Seems to make the clicking much less frequent, its still there and needs a proper solution though.

---

### Post by Ramas on 2007-05-30
Hi to all, first post here!

I also have the HD clicking issue, I resolved with the hdparm -B 254 command, but I have also this problem under Vista.

I found [here]("http://www.dellcommunity.com/supportforums/board/message?board.id=insp_harddrive&thread.id=38562&view=by_date_ascending&page=1") in the dell forum,  there is an Hitachi utility to write down parameters into the HD firmware.

I think it should fix this problem definitely, but in this moment I can not follow the procedure (no ADSL at home); can anyone try and see it it fixes the HD clicking?

I'll post my experience in two weeK (when the ADSL will be activated).

Cheers,
Ramas

---

### Post by drpaul on 2007-05-30
Do you expect the Hitachi program to work with other manufacturer's HDs?

Paul

---

### Post by Ramas on 2007-05-30
@ drpaul:

I think it should be used the proper software.

For example for fujitsu HD I found this page:

[http://www.fujitsu.com/us/services/computing/storage/hdd/support/utilities.html](http://www.fujitsu.com/us/services/computing/storage/hdd/support/utilities.html)

Perhaps there is a suitable program to modify HD parameters.

Cheers,
Ramas

---

### Post by wieman01 on 2007-08-21
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695")

---

### Post by deimios on 2007-09-18
Confirming that the hdparm -B254 /dev/hda command resolves the clicking issue on a Fujitsu Siemens Amilo A1667G laptop.

---

### Post by screaminj3sus on 2007-10-20
I actually stopped to listen to my drive and you are correct, clicks at regular intervals of like 5 seconds.. This should be fixed.

---

### Post by wieman01 on 2007-10-21
> **screaminj3sus said:**
> I actually stopped to listen to my drive and you are correct, clicks at regular intervals of like 5 seconds.. This should be fixed.
See post #3 of this thread:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

---

### Post by gottferdamnt on 2007-10-21
I haven't this issue anymore with Gutsy.

---

### Post by wieman01 on 2007-10-21
> **gottferdamnt said:**
> I haven't this issue anymore with Gutsy.
So Gutsy has solved the problem for you? Did you have that issue in Feisty? I really hope it won't reoccur after an upgrade.

---

### Post by paulten on 2007-10-21
Same problem on my Dell m1330. 

 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       39
However I have very few load cycles, which other people report that they have alot of.

The hdparm command solves this for me, however I don't quite understand how it resolves it.

---

### Post by gottferdamnt on 2007-10-21
> **wieman01 said:**
> So Gutsy has solved the problem for you? Did you have that issue in Feisty? I really hope it won't reoccur after an upgrade.

Yes I had this issue in Feisty but It was because of hdparm. To fix It, I put these command lines in /etc/hdparm.conf:
```

command_line {
hdparm -S0 -B255 /dev/sda
}

```

No problem in Gutsy. I do not use laptop-mode anymore too.

---

### Post by ranigta on 2007-10-22
I'm having the same problem, but a bit worse.  I'm running Kubuntu 7.04 with all Western Digital drives: one 40GB IDE and four 500GB SATAs.  I *think* the problem is only affecting the IDE drive, but it's hard to tell.  

I am unable to use the "hdparm -B 254" workaround posted here -- I'm not sure if my drives don't support it or what:

```
$ sudo hdparm -B 254 /dev/hda

/dev/hda:
 setting Advanced Power Management level to 0xFE (254)
 HDIO_DRIVE_CMD failed: Input/output error
```

This happens for ANY value of -B (I tried them all).  Perhaps the drive doesn't support this command?  The hdparm info output:

```
$ sudo hdparm -i /dev/hda

/dev/hda:

 Model=WDC WD400BB-22JHC0, FwRev=05.01C05, SerialNo=WD-WMAM9LK51429
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=66
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=78165360
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma3 udma4 *udma5
 **AdvancedPM=no** WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode
```

I noticed the "AdvancedPM=no", which doesn't sound good.  Any other way to attack the problem?  

Some additional details:

I've noticed that it does not click while in single-user ("recovery") mode.  Also, "smartctl -a" doesn't include item 193 (parkings), which means the drive doesn't keep track, so I have no way of knowing how many I've gone through.  I've tried a lot of things to make it stop, all of which failed:

- Booted with "acpi=off apm=off" in kernel parameters
- Turned off apm and acpi daemons
- Edited laptop_mode.conf to adjust readahead and HD_POWERMGMT
- Edited hdparm.conf to include "apm=255" and other values
- Tried not logging in (thinking that something loaded by KDE could be related)

No dice.  Any other way to turn off parking, perhaps at the kernel level?

---

### Post by gertin on 2007-10-22
This sounds like a rather critical bug (especially if it shortens the lifespan of drives), so why hasn't it been fixed yet? A [bug report](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) was filed over a year ago.

---

### Post by Jbloudg20 on 2007-10-23
I ahve since moved on from Ubuntu. Both fedora 6 and 7 didn't give me this problem.

---

### Post by viduliya on 2007-11-07
You may find the following links to be useful regarding this problem:

[http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions]("http://www.linux-hero.com/rant/ubuntu-hard-drive-explosions")

---

### Post by mblind on 2007-11-23
How would you undo the command hdparm -B254 /dev/hda ??

Just in case you wanted to go back to the original configuration?

---

### Post by wieman01 on 2007-11-24
> **mblind said:**
> How would you undo the command hdparm -B254 /dev/hda ??

Just in case you wanted to go back to the original configuration?
Just reboot the computer...

---

### Post by mblind on 2007-11-24
Sorry, I'm confused.. So every time I reboot it gets rid of the hdparm -B254 /dev/hda command.

So If I DO want to use this to fix my hdd clicking problem I have to enter this after every reboot? That doesn't sound right..

Please clarify.. 


Thanks .

---

### Post by wieman01 on 2007-11-24
> **mblind said:**
> Sorry, I'm confused.. So every time I reboot it gets rid of the hdparm -B254 /dev/hda command.

So If I DO want to use this to fix my hdd clicking problem I have to enter this after every reboot? That doesn't sound right..

Please clarify.. 


Thanks .
Every time you reboot you need to reenter the command, because the change does not stick. However, if you want to avoid reentering it, please see post #3 of this thread for a solution:

[http://ubuntuforums.org/showthread.php?t=531866]("http://ubuntuforums.org/showthread.php?t=531866")

You basically create a startup script which executes the command for you while you boot the PC.

---

### Post by mblind on 2007-11-24
Great, Thanks for the quick reply.. I am new to Ubuntu.. But I am LOVING IT..

One more little question.. when I put in hdparm -B254 /dev/sda    I get the error
/dev/sda: Permission Denied

Does anyone know why?

---

### Post by gertin on 2007-11-24
You need to be superuser to change parameters with hdparm.
```
sudo hdparm -B254 /dev/sda
```

---

### Post by mblind on 2007-11-24
That worked!! Thanks so much.. Forum support is really great here..  :)

---

### Post by zeus77 on 2007-12-07
I had previously reported (in posts #35, #50) that my Fujitsu MHV2120BH on a Lenovo 3000 N100 had this problem with Feisty... and it was pretty bad.

However, it seems like it's fixed in Gutsy without any hdparm power management changes.  Here is the current hdparm output:

```
zeus77@somewhere:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=FUJITSU MHV2120BH PL   , FwRev=0084002A, SerialNo=NW9ST7126EJG
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode
```

Anyone else having better luck with Gutsy?

zeus77

---

### Post by drpaul on 2007-12-08
Interesting. I run up to date Edgy 6.10 and have the same drive in an HPdv6150us. I get

:~$ sudo hdparm -i /dev/sda
Password:

/dev/sda:
 HDIO_GET_IDENTITY failed: Inappropriate ioctl for device

I'm surprised that it fails so badly.

Paul

---

### Post by Belerophon on 2008-01-21
Hi!
I have a toshiba satellite A-100(PSAA9), running Ubuntu 7.01 and Vista.

The hard drive is(what appeared in the BIOS):
HTS541080G9SA00

Three days ago, I made a BIOS update (released in 26 November 2007), and I started hearing those annoying clicks on the hard disk. I was glad to find this thread!! :D
I solved the problem changing the hdparm.conf file:
apm = 255

Did anyone else had this problem, updating the BIOS and having this issue???

When I update to Hardy, will hdparm.conf file be overwritten??

This workaround does not harm our hard disk in long term?? I use my portable to work, but I usually let him turned on many hours without using it (and suspend and hibernate do not work with ubuntu :( )...is there any problem with that???
Should I start to turn off the computer more often???

(By the way, Vista started to do clicks too, but much less often than Ubuntu...does anyone have this problem in Vista too?)

Thanks!!!

---

### Post by wieman01 on 2008-01-21
> **Belerophon said:**
> When I update to Hardy, will hdparm.conf file be overwritten??
No, an update won't overwrite it. If it does, you'll notice immediately and can redo those steps.
> **Belerophon said:**
> This workaround does not harm our hard disk in long term?
No, it won't. Just use the HD as you like. This command has no negative impact on your harddrive as far as I can tell. In fact quite the opposite should be true.

---

### Post by oldsmobile_mike on 2008-02-13
Hi guys,

I also had the hard drive clicking problem (Sager 5600P laptop).  What resolved it for me was enabling hdparm under System -> Administration -> Services, and adding this code to hdparm.conf in /etc:

command_line {
       hdparm -S 0 /dev/sda1
        hdparm -B 254 /dev/sda1
}

...I found that solution somewhere else in the forums, but as there are numerous "possible solutions", I just thought I'd post which one worked for me.  Hope they get this fixed in the next release!

---

### Post by drpaul on 2008-02-20
O...mike

Thanks for post. I have been struggling for a week or more since upgrading to Gutsy.  The old syntax in the hdparm.conf file didn't work, and aping the syntax suggestions in the file didn't either. The "command line" snippet in your post works!

Without -B 254 I pile up Load Cycles at an alarming rate, even when it isn't clicking. :shock:

They really ought to improve the default hdparm.conf file.

Paul

---

### Post by speel on 2008-02-20
Why is this not being fixed?

---

### Post by drpaul on 2008-02-20
Darned good question. I have no answer. The problem has been around for over 1 year. I guess the powers that be are not concerned about users wearing out their HDs prematurely.

??????????????

Paul

---

### Post by speel on 2008-02-20
> **drpaul said:**
> Darned good question. I have no answer. The problem has been around for over 1 year. I guess the powers that be are not concerned about users wearing out their HDs prematurely.

??????????????

Paul

makes you think of how updates are prioritized.

---

### Post by drpaul on 2008-02-20
From reading responses in different places, this seems to an issue that the Ubuntu folks think isn't their doing; yet it seems as if other distros may not have this problem.

:confused:

Paul

---

### Post by speel on 2008-02-20
[SIZE="4"]Ubuntu developers: We as users love Ubuntu, but as you can see the majority of us laptop users have this "parked" hard drive problem. Please fix it. Thank you.[/SIZE]

---

### Post by echou127 on 2008-04-03
sudo hdparm -B254 thing works and I put the code into rc.local as well and there is no clicking when I start up my laptop but when I revive it from hibernate or standby, the clicking comes back.  Pls advise.

---

### Post by drpaul on 2008-04-03
Unless someone with greater insight than I have can tell what script gets executed when you restart, you could always execute the command from the command line.

Paul

---

### Post by treesurf on 2008-05-05
> **echou127 said:**
> sudo hdparm -B254 thing works and I put the code into rc.local as well and there is no clicking when I start up my laptop but when I revive it from hibernate or standby, the clicking comes back.  Pls advise.


I have the same problem.  Any solutions would be appreciated.

---

### Post by kaurman on 2008-05-05
Hi!

You could try using laptop mode... Not sure if it works but I am using it and have noticed no problems with clicking (after resuming) since.

Firstly sudo apt-get install laptop-mode-tools

From terminal type:

sudo gedit /etc/laptop-mode/laptop-mode.conf

Firstly, check that you have:

```

# Enable laptop mode when on battery power.
#
ENABLE_LAPTOP_MODE_ON_BATTERY=1


#
# Enable laptop mode when on AC power.
#
ENABLE_LAPTOP_MODE_ON_AC=0

```


Then look for:

```

# Should laptop mode tools control the hard drive power management settings?
#
CONTROL_HD_POWERMGMT=1


#
# Power management for HD (hdparm -B values)
#
BATT_HD_POWERMGMT=x
LM_AC_HD_POWERMGMT=x
NOLM_AC_HD_POWERMGMT=x

```

You should use 254 instead of what x equals.


PS I am assuming you have a laptop not a tower.

---

### Post by Rui Pais on 2008-05-11
> **treesurf said:**
> I have the same problem.  Any solutions would be appreciated.

Hi, 
i created a cron job for every 15 secs check if it's hdparm -B254 and set it if not. 
That way, after restart i only have at most 15 secs (or can be set for less if wanted) of extra parking activity... 
Not the most elegant solution but at least work well.

---

