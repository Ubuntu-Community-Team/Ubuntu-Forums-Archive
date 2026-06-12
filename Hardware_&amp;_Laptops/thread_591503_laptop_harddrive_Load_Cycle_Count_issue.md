---
title: "laptop harddrive Load_Cycle_Count issue"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by ubuntu_demon on 2007-04-19
**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperate and make sure it remains below the maximum temperature specification of your harddrive. [COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

This thread continues here :
[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)

---

### Post by stealthbox on 2007-10-03
After the bug found in the kernel that feisty uses which causes your hardrive to make a pop sound when it shuts down , i have been hessitant to install ubuntu on my laptop.

i did install gutsy beta, but suspend/hibernate dont work which are really important and i could help to notice that my hardrive was making noise. the hardrive is being accessed every 10 seconds without me doing anything and it has a weird noise to it. with XP on the same laptop i dont hear anything, not even when im accessing files.

whats going on with ubuntu on laptops, why does it run so crappy compared to the desktop.

---

### Post by Circus-Killer on 2007-10-03
to be dead honest, i have had no such problems with my laptop. so it could just be a problem with your laptop, or with the make of harddrive. but as for running ubuntu on a laptop, mine runs like a dream. and there are plenty of other people who also run ubuntu on their laptops without problems.

---

### Post by trippinnik on 2007-10-03
I've never heard about abug in the kernel cause a hard drive pop, and never heard it happen on my laptop.  Why do you think this problem exists?  Is there any confirmation from kernel devs?  I'd recommend backing up your data because you're hard drive may be dying if you are hearing sounds like that.

---

### Post by Linicks on 2007-10-03
The bug referred to can be found here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)

Doesn't seem to be much to worry about - just annoying.

Nick

---

### Post by Rob500 on 2007-10-03
It wont be around for much longer anyway, Gutsy final is out in 3 or so weeks.

---

### Post by steve987 on 2007-10-03
hello,

I have the same 'click' noise when shutting down my IBM T41 running Feisty. I read somewhere (can't remember where :-/) that it _may_ harm the harddrive.

- Steve

---

### Post by vikrant82 on 2007-10-03
sudo smartctl --device=ata --attributes /dev/sda

Power-Off_Retract_Count = 379 :confused: [Makes a perfect number for a 5 month Ubuntu usage.]

Anyone else ? Basically all feisty users should have been affected by this ?
If Gutsy solved the problem , the counter should be more or less stable from now on .. 

Lets see.:(

I finally wrote about the two bugs [here.]("http://kakku.wordpress.com/2007/10/29/s-m-a-r-t-parameters-for-hard-disk-possible-ubuntu-bugs-with-handling-laptop-hard-disks-laptop-hardisks-being-killed/")

---

### Post by Linicks on 2007-10-03
> **vikrant82 said:**
> sudo smartctl --device=ata --attributes /dev/sda

Power-Off_Retract_Count = 379 :confused: [Makes a perfect number for a 5 month Ubuntu usage.]

Anyone else ? Basically all feisty users should have been affected by this ?
If Gutsy solved the problem , the counter should be more or less stable from now on .. 

Lets see.:(

If you read the launchpad link above, there is a temporary fix to stop the spin-up/power-off:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)

I will be trying this when I get home tonight.

Nick

---

### Post by vikrant82 on 2007-10-03
Just checked , Although there is no "click" or "pop" sound , but Power-Off_Retract_Count has increased on shutdown. [380]

Let me try that fix and report again ..

---

### Post by rickycodie on 2007-10-03
i've had no problems like this and i run ubuntu on three different laptops.

---

### Post by Linicks on 2007-10-03
> **vikrant82 said:**
> Just checked , Although there is no "click" or "pop" sound 

Well, my Dell Inspiron is only a month old, and I did wonder why I get a 'donk' when it shuts down and powers off.  Maybe newer drives are a bit more silent.

Nick

---

### Post by vikrant82 on 2007-10-03
The script doesnt seem to work for me. 
I tried both by adding in link to script from init.d to rc0.d [S00XXX] as well as rcS.d [S99XXX]

So the counter "Power-Off_Retract_Count" still increases if I *shutdown*. However if I restart it stays the same.

Anyways , I am just concerned about this post where he suggests that "Power-Off_Retract_Count" is an indication of "Emergency unload". Although he is not sure.

"Emergency unload is intended to be invoked in rare situations. Because
this operation is inherently uncontrolled, it is more mechanically
stressful than a normal unload. A single emergency unload operation is
more stressful than 100 normal unloads. Use of emergency unload
reduces the start/stop life of the drive at a rate at least 100 times
faster than that of normal unload and may damage the drive." 

from , 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/102](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/102)

Anyone to confirm this ?

---

### Post by vikrant82 on 2007-10-03
Can people post result of , 

```
sudo smartctl --all /dev/sda | grep Power-Off_Retract_Count
```

You might install it if its not there ,
    
```
 sudo apt-get install smartmontools
```

---

### Post by dinub1 on 2007-10-03
> **stealthbox said:**
> After the bug found in the kernel that feisty uses which causes your hardrive to make a pop sound when it shuts down , i have been hessitant to install ubuntu on my laptop.

i did install gutsy beta, but suspend/hibernate dont work which are really important and i could help to notice that my hardrive was making noise. the hardrive is being accessed every 10 seconds without me doing anything and it has a weird noise to it. with XP on the same laptop i dont hear anything, not even when im accessing files.

whats going on with ubuntu on laptops, why does it run so crappy compared to the desktop.

I do not hear any special sound from my laptop's HDD. Its an approx 1 yr old (upgraded) Hitachi 100 GB 5400 RPM. works like a whisper with this Kubuntu 7.10 beta. Maybe your HDD is failing regardless of the OS. Pls. check it.

---

### Post by zach12 on 2007-10-03
some older lappy harddrives are crap in ubuntu

---

### Post by dinub1 on 2007-10-03
> **Linicks said:**
> If you read the launchpad link above, there is a temporary fix to stop the spin-up/power-off:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)

I will be trying this when I get home tonight.

Nick

So apparently there might be a problem with this HDD parking at shutdown. But it does not happen with my laptop. But prhaps the fix as sugested in this link may help. Thanks,

---

### Post by dinub1 on 2007-10-03
> **Linicks said:**
> Well, my Dell Inspiron is only a month old, and I did wonder why I get a 'donk' when it shuts down and powers off.  Maybe newer drives are a bit more silent.

Nick

I don't think so. Yours is newer than mine, yours is 1 month  old while my laptop HDD is approx 9-10 months old.  However the laptop, a HP is model 2002. It served me excellently and trouble free so far. I just upgraded the HDD for higher capacity and recently its original battery died after 5 yrs of usage. It still does not make any clicks while shutting down. 

Have you tried running Windows XP on it? Or a Live CD by any other Linux vendors, say PCLinus2007? Just for comparison. If other OS's do not exhibit the same problem, then it must be Ubuntu dependent. Additional posts suggest here, there is a fix for that "click" problem. 

I also found that Feisty is buggy. I had the famous overheating problem that others reported too. Just from upgrading from 7.04 to 7.10. The only thing that solved the issue was to wipe off my Linux partitions (after backing up) and reinstalling 7.10 beta from scratch. Now it works like a KING :) Temps are normal, fan is not over running and OS works very pleasantly. No clicks or noises etc. I am pleased.

---

### Post by Linicks on 2007-10-03
**[SIZE="4"]Report update[/SIZE]**

OK, running:

sudo smartctl --device=ata --attributes /dev/sda

I got:

```
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always     -     39
```

...which seems about right for a laptop 20 days old.

I shutdown - Ubuntu shuts down cleanly, but right as the power light goes out ~ "DING" noise from the hard drive.

Powering back up, I see:

```
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always     -     40
```

:!:

Applying the temporary fix here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)

I shut down.  Ubuntu shuts down cleanly, power light goes out - NO DING!!! - In fact, deadly silence!!

:)

Looking again at smartctl attributes afterwards:


```
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always     -     40
```

:cool:

So, for my instance, it looks like I had the shutdown bug that wrote cache to disk, spun it down, then shutdown spins it up again just as 'power-off' is issued and the emergency head mechanism kicked in.

The fix works for me.

So thanks to **stealthbox** for alerting and bringing this to everybody's attention - I didn't know, and thought it was just the noise my hard drive made at shutdown and wouldn't have guessed it was an issue.

Nick

---

### Post by dinub1 on 2007-10-03
Hey Linicks,

Pretty comprehensive research. I am glad that posted tip works in your case. As you may know this is depeedent on the machine in use. However it is apparently a Ubuntu 7.10 (software) bug. As I said, on mine, it does not act with those clicks :) But I am going to type the same commands on mine to see what it reports. Congrads and thanks.

---

### Post by Linicks on 2007-10-03
Remember (sorry, I didn't state this), I am on 7.04:

Linux palantir 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

The newer kernels in gutsy (etc.)  have the fixed kernel patches included.

***EDIT***:  Remember, this only affects **shutdown**, not *restart*!

Nick

---

### Post by CAD-MAN on 2007-10-03
There's some discussion, as well as a fix, for this 'unhealthy clicking noise' in this thread (about the Dell Inspiron 1520, but it may work for you...)

[http://ubuntuforums.org/showthread.php?t=501195&page=40]("http://ubuntuforums.org/showthread.php?t=501195&page=40")

---

### Post by dinub1 on 2007-10-03
> **Linicks said:**
> Remember (sorry, I didn't state this), I am on 7.04:

Linux palantir 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux

The newer kernels in gutsy (etc.)  have the fixed kernel patches included.

***EDIT***:  Remember, this only affects **shutdown**, not *restart*!

Nick

OK. No prob. I am using Gutsy, 7.10 beta. I tried using your command (smrtctl) it did not recognized. I made a search in Synaptic and is SMART tools :) I installed and this is what I get. Remember, I have no clicks on shutdown and I never had any with any previous versions of Ubuntu, and I am with it since version 5.

dinu@ubuntu710:~$ sudo smartctl --device=ata --attributes /dev/hda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       84857
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       26345472
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       366
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       8589934592000
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       3134
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Seconds        0x0032   087   087   000    Old_age   Always       -       6752h+04m+59s
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       366
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       86
193 Load_Cycle_Count        0x0032   086   086   000    Old_age   Always       -       295638
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       43 (Lifetime Min/Max 18/52)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       477
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       456392704
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       16361
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       429517111565

dinu@ubuntu710:~$

---

### Post by dinub1 on 2007-10-03
> **CAD-MAN said:**
> There's some discussion, as well as a fix, for this 'unhealthy clicking noise' in this thread (about the Dell Inspiron 1520, but it may work for you...)

[http://ubuntuforums.org/showthread.php?t=501195&page=40]("http://ubuntuforums.org/showthread.php?t=501195&page=40")

CAD_MAN,
Yes I saw the discussions and the fix. I do not have the issue. Thank you anyway.

---

### Post by Linicks on 2007-10-03
[QUOTE=dinub1]

192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       86
[/QUOTE]

Well, you have had 86 counts of where the disk was powered off whilst in spin state (or not ready to shutdown), but I guess as you have had the laptop a long time, that will happen with the occasional lockup etc.

But would be good to keep an eye on that count next time you 'shutdown'.

**EDIT:**  I also see your device is /dev/hd* - this issue also only affects the scsi emulation devices on /dev/sd*

Nick

---

### Post by dinub1 on 2007-10-03
> **Linicks said:**
> Well, you have had 86 counts of where the disk was powered off whilst in spin state (or not ready to shutdown), but I guess as you have had the laptop a long time, that will happen with the occasional lockup etc.

But would be good to keep an eye on that count next time you 'shutdown'.

**EDIT:**  I also see your device is /dev/hd* - this issue also only affects the scsi emulation devices on /dev/sd*

Nick

well, I shut down the laptop once in a while while in the middle of the operation. This happened both with Ubuntu or with Windows XP. Yes t can be, though I expereince no clicks of any kind during shotdown. Thanks for bringing it to my attantion. 

The dev/hda is how Ubuntu named my HDD. The sda is usually an external device and this is not the case. By example when I hook up an external USB HDD it is detected as sda1.

---

### Post by dinub1 on 2007-10-03
OK I see. My internal laptop HDD is a P-ATA (IDE) device and not SATA. Your is newer and therefore SATA. Nost newest laptops come with SATA HDD's.

---

### Post by stealthbox on 2007-10-04
guys i have an inspiron 1501 and i finally found the problem

[http://www.linuxquestions.org/questions/showthread.php?t=588770](http://www.linuxquestions.org/questions/showthread.php?t=588770)

> SHORT VERSION

Anyone know where I could find some documentation explaining the -B option of hdparm and it's implications regarding hard disk shock resistance and wear and tear? Or perhaps you have an explanation of your own? The man page is quite limited. =/


LONG VERSION

I recently noticed a clicking sound coming from my laptop's (Ubuntu 7.04) hard drive every few seconds. Google showed me I was far from being alone - seems tons of GNU/Linux users have encountered this problem. It also seems to be a pretty dangerous thing, as AFAICT it eats away at the hard disk's life. FWIW, it's a confirmed issue in Ubuntu's bug thing (I assume on other distros too):

[https://bugs.launchpad.net/ubuntu/+bug/104535](https://bugs.launchpad.net/ubuntu/+bug/104535)

[https://bugs.launchpad.net/ubuntu/+s...ort/+bug/59695](https://bugs.launchpad.net/ubuntu/+s...ort/+bug/59695)


---

### Post by infra_red_dude on 2007-10-04
for my laptop this is the status:

Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       872

i haf a Pata 80GB hdd, been using fiesty since may this year. i don't haf a clicking sound while shutting down. but the count is very high. i'm confused!

---

### Post by Linicks on 2007-10-04
> **infra_red_dude said:**
> for my laptop this is the status:

Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       872

i haf a Pata 80GB hdd, been using fiesty since may this year. i don't haf a clicking sound while shutting down. but the count is very high. i'm confused!

That means the drvie has be powered off 872 times before shutting down correctly - exactly the symptoms expected.

Keep an eye on that figure - if you see it count up everytime you shutdown, then you need to fix it up with the temporary fix.

I wouldn't be too worried though - it seems although the behaviour isn't right, it doesn't seem to really harm laptop drives otherwise we would see hundreds (if not thousands) of people with disk failures all shouting.

Nick

---

### Post by infra_red_dude on 2007-10-04
the problem is that i can't apply the temporary fix as my PATA HDD is mapped to /dev/hda. any solutions?

---

### Post by Linicks on 2007-10-04
> **infra_red_dude said:**
> the problem is that i can't apply the temporary fix as my PATA HDD is mapped to /dev/hda. any solutions?

But does the count go up?  It maybe a legacy count (i.e. doesn't happen no more).

What Ubuntu you running?  The latest kernel in Gutsy fixes it up.

Nick

---

### Post by vikrant82 on 2007-10-04
Hi Nick,

I cant seem to apply the fix, 
I get a permission denied at startup. [Have linked  rcS.d/S99XX to script /etc/init.d/XX]

I dont have a file, "stop_on_shutdown" under /sys/class/scsi_disk/0\:0\:0\:0 and I cant seem to create it watever i may try.

---

### Post by vikrant82 on 2007-10-04
> The latest kernel in Gutsy fixes it up.

I am on latest kernel and still count increases if I shutdown.

---

### Post by Linicks on 2007-10-04
OK, stop what ever you are doing.  Reading through, it appears it only affects /dev/sda drives...

So undo what you have done and relax... don't do anything as messing here could trash your hard drive.

The fix is in Gutsy, as the bug report is updated.  We need to see what to do if the HD is on /dev/hd*

Can you post output of:

> mount

and

> sudo fdisk -l

(NOTE!  above -l  is lowercase L )

Nick

---

### Post by vikrant82 on 2007-10-04
Ofcourse my drives are /dev/sda*

- "Linux Kx-VMZ 2.6.22-12-generic" and my count increases ..

---

### Post by infra_red_dude on 2007-10-05
> **Linicks said:**
> But does the count go up?  It maybe a legacy count (i.e. doesn't happen no more).

What Ubuntu you running?  The latest kernel in Gutsy fixes it up.

Nick
yes, the count goes up. its become 873 now! i'm using a Pata hdd mapped to /dev/hda. am on fiesty  with kernel ver.2.6.20-16. can anyone plz help me in applying the fix?

---

### Post by Linicks on 2007-10-05
I don't know, as reading the bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)

it appears that drives showing up as /dev/hd*  are **not** affected by this.

Also, without having any drives myself on /dev/hd*, I cannot debug.

Nick

---

### Post by viking777 on 2007-10-05
I have just read this particular post, although I have contributed to others like it. My laptop (evesham voyager c530rd) has been impossible to shut down since I first installed Linux on it (I use the word Linux since this is not a Ubuntu problem it occurs with every Linux version I have ever tried - and that is a lot). Not only does it not shut down but it does not hibernate or suspend and Ctl/Alt/Backspace just freezes it. 

As an experiment I installed the smartctl software and found that my  Power-Off_Retract_Count has now reached 787, increases every time I shut down and always 'pops' when I do so (mind you that is perhaps not surprising since I have to use the power button for every shutdown otherwise it just hangs with the processor cooling fan going at full speed). Incidentally, my laptop is 10 months old.

The main point of the post (apart from the vain hope that somebody might know how to cure it) is to say that I am a current user of Gutsy with its much vaunted 'solution' to this problem. I have the 'shutdown workround' file included in my current distribution but it makes not one whit of difference to anything. 

The usual response to this query is that it must be a 'peculiarity' of my laptop. Sorry but I don't buy this. Windows (though I hate it vehemently) shuts down or hibernates or suspends my laptop perfectly every time so it is not a problem with my laptop it is a problem with Linux ACPI which unlike most of the Linux kernel is just not up to the same standard as Windows.

BTW, just in case you are tempted to reply to this, in order to save your time I should tell you now that  I have tried every boot cheat code you have ever heard of and not one of them makes any difference, so no point in suggesting those as a solution they don't work either. However if you know of anything else that might work I would love to hear it. 

Like others contributing to this post I do wonder how much damage I am doing to my hard drive with this, and the very fact that I and others could be causing damage to our machines should give this defect the highest priority in the Linux development framework. Unfortunately this does not seem to be the case.

---

### Post by Linicks on 2007-10-05
Yes, it is a sorry state of affairs, but I wouldn't blame the Linux devs.

Remember, hardware is proprietry, and MS enter NDA (and vice versa) with hardware manufacturers to get the specs (or even get the hardware manufacturers to write the drvier code) so everything is known and will work.

The Linux devs 99% of the time have to back engineer and what not to do this, as as hardware manufacturers are scant in technical information, so it must be a tough job to get anything to work.

As to my situation with the HD issue (whicj is now 100% resolved), I guess Dell with the pre-installed Ubuntu used hardware that has (the true) specification published, so the fixes (et al) work.

Nick

---

### Post by viking777 on 2007-10-06
> **Linicks said:**
> Yes, it is a sorry state of affairs, but I wouldn't blame the Linux devs.

Remember, hardware is proprietry, and MS enter NDA (and vice versa) with hardware manufacturers to get the specs (or even get the hardware manufacturers to write the drvier code) so everything is known and will work.

The Linux devs 99% of the time have to back engineer and what not to do this, as as hardware manufacturers are scant in technical information, so it must be a tough job to get anything to work.

As to my situation with the HD issue (whicj is now 100% resolved), I guess Dell with the pre-installed Ubuntu used hardware that has (the true) specification published, so the fixes (et al) work.

Nick
Please don't think I am in the business of blaming anyone. I have a free distro that works most of the time and I happen to love it, I wouldn't have put up with bad shutdowns for the last 10 months if I didn't want to use it. My only gripe is this. Immense amounts of effort seem to be put into making windows wobble and making games work, neither of which are actually life and death situations with respect to hard drives, whereas as far as I know hardly any effort is put into fixing a problem that could well cost people a good deal of time and money (ie a broken hard disk). Now of course if you are working on Linux in your spare time and probably for free, then you have every right to code whatever turns you on, so if games or wobbly windows float your boat then that is what you will choose, perhaps coding for ACPI implementations is extremely boring or hard - I wouldn't know. However there are people out there that are employed by various firms (Canonical for instance) to work on commercial versions of Linux and these are the people who should be taking this problem more seriously. If I owned a company and had just switched over to Linux as a commercial OS and I found out that in doing so I have inadvertantly shortened the lifespan of every laptop in the company, I wouldn't be too pleased.

---

### Post by Linicks on 2007-10-06
> **viking777 said:**
> However there are people out there that are employed by various firms (Canonical for instance) to work on commercial versions of Linux and these are the people who should be taking this problem more seriously. If I owned a company and had just switched over to Linux as a commercial OS and I found out that in doing so I have inadvertantly shortened the lifespan of every laptop in the company, I wouldn't be too pleased.

Yes, but what I was saying is they do try.  If you google this hard drive issue, and read the LKML threads, basically they know the issues, but nobody seems to know what causes it.  There are several mentions to BIOS doing it, but nobody knows why (or can even investigate why).

So I wouldn't say it is ignored - but rather unobtainable at the present until somebody does crack what this closed source firmware is doing.

Nick

---

### Post by infra_red_dude on 2007-10-06
I haf no clue whats happening on my hdd. As I said, I haf Seagate 80GB Momentus IDE HDD (P-ATA) mapped onto /dev/hda. The Power-Off_Retract_Count now shows a value of 877 (up from 872 when I first posted!!!) :(

---

### Post by Gremlinzzz on 2007-10-06
Just upgrade kernel see if your drive pops,
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by dinub1 on 2007-10-06
*Yes, it is a sorry state of affairs, but I wouldn't blame the Linux devs.*

Yes, it is... :(

*Remember, hardware is proprietry, and MS enter NDA (and vice versa) with hardware manufacturers to get the specs (or even get the hardware manufacturers to write the drvier code) so everything is known and will work.*

Yes that may be true, it has its advantages. Linux developers may not have that advantage unless it's involved with financial deals.

*The Linux devs 99% of the time have to back engineer and what not to do this, as as hardware manufacturers are scant in technical information, so it must be a tough job to get anything to work.*

Yes, for sure.

[I]As to my situation with the HD issue (whicj is now 100% resolved), I guess Dell with the pre-installed Ubuntu used hardware that has (the true) specification published, so the fixes (et al) work.

Nick[/I]

I believe this cannot reach to the point where it can be dangerous to the life span of the HDD or machine in usage. it shouldn't happen. why doe it happen, only a developer may know. But in my case, problem has been solved by competing reinstalling Ubuntu 7.10 beta from scatch. I have no CPU overload/overheating issues. So this is therefore a software realted issue. Windows XP does not have this issue.

---

### Post by paulten on 2007-10-21
Hi all.

I have a strange sound from the hdd on my brand new Dell xps m1330. 
I get some (hard to explain) ticks from my harddrive every ten seconds or so, and each time the hdd light on my front panel lights up. I've noticed this on my other computers, that even though not doing anything the hdd light lights up every now and then. I have not put any thought to it before now when these sounds from the hdd appeared.

I'm running a pretty vanilla Gutsy installation..
Harddrive : Model: ATA SAMSUNG HM160HI

Has anyone experienced something like this?
It's almost as the hdd spins up and spins down, so quick that all it has time to do is make a tick :-)
When I put some load on the hdd I does not make a sound (like run updatedb).
I do not think this is a hardware problem.
I've watched top, if maybe one process is making these sounds, but they appear to be random. No error messages in any of the log files..
Are there any harddrive diagnostic tools, with a very verbose output so I can see what happens every second?

Thank you!
Kind regards Paul

---

### Post by Linicks on 2007-10-21
Yes, there is two things you can do.  Mount the partition with 'noatime' (recommended for laptops), and also stop  APM spinning down the disk every few seconds.

Mounting with noatime.

In /etc/fstab, add the noatime option to your disk;  change to similar, depending on your fstab file:
```

# /dev/sda6
UUID=f2bbc557-23c0-4afd-bf8b-d0e5d0957956 /  ext3 defaults,errors=remount-ro,**noatime** 0  1
```

After reboot, 'mount' should show it is applied:

```
nick@palantir:~$ mount
/dev/sda6 on / type ext3 (rw,noatime,errors=remount-ro)
```

To stop the disc spindown/up every few seconds, add this to the bottom of /etc/hdparm.conf

```
# Nick - 04/10/2007 - stop apm drive spin down/up
/dev/sda {
  apm = 254
}
```

Then at next reboot, all should be good to go!

Nick

BTW, if you wish to see what UUID is for what disk, issue this as normal user:
```

ls -l /dev/disk/by-uuid
```

---

### Post by paulten on 2007-10-21
Great!!
Really thanks for the quick reply, the mount noatime option did the trick.


Thanks 
Paul

---

### Post by paulten on 2007-10-21
I was a bit to quick..
Sorry about that, I don't think the spindown timeout is the problem afterall.
I tried the hdparm settings.

Any other suggestions?

Thanks
Paul

---

### Post by Linicks on 2007-10-21
Please show all output of:

> mount

Nick

---

### Post by paulten on 2007-10-21
/dev/sda6 on / type ext3 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)


for sata drives
Code:

sudo hdparm -B254 /dev/sda


from this post solved it :
[http://ubuntuforums.org/showthread.php?t=331418&highlight=harddrive&page=3](http://ubuntuforums.org/showthread.php?t=331418&highlight=harddrive&page=3)

Thank you for your patience.

Kind Regards
Paul

---

### Post by Linicks on 2007-10-21
So it's sorted?  I can't make out from your post?

Nick

---

### Post by paulten on 2007-10-22
I ran hdparm -B254 /dev/sda - The clicking stopped. 

Your command with apm = 254 i hdparm.conf - should that not do the same thing?
Strange as it sounds, the settings from hdparm.conf was not loaded (even thou I restarted) but running the command hdparm -B254 /dev/sda. 

After alot of gooogling I found that this was a pretty common problem, mostly solved by hdparm.

The forum link from my last post have a discussion about it.

Thanks
Paul

---

### Post by gertin on 2007-10-22
I have the M1330 too, I'm not hearing any strange ticks though and I don't have the same hard drive as you, but I would like to find out if I'm having the same issue. I have a FUJITSU MHW2160BJ drive, 160GB, 7200RPM.

Here is the output of smartctl:
```
martin@xps:~$ sudo smartctl -A /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       35175
  2 Throughput_Performance  0x0004   100   100   000    Old_age   Offline      -       26607616
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       2
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       30
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       8589934592000
  7 Seek_Error_Rate         0x000e   100   100   000    Old_age   Always       -       888
  8 Seek_Time_Performance   0x0004   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       26
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       30
191 G-Sense_Error_Rate      0x0012   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       3
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       38 (Lifetime Min/Max 9/46)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       11
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       447479808
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000e   100   100   000    Old_age   Always       -       21047
201 Soft_Read_Error_Rate    0x0010   100   100   000    Old_age   Offline      -       0
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       1533294673484
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       839
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0
```

---

### Post by yodha on 2007-10-22
[FONT="Courier New"]I'm running **Xubuntu *Gutsy Gibbon*** on a **Fujitsu S7021** laptop. The harddisk is a **Hitachi MK6025GAS**. I'm seeing (rather hearing) the same problem as above.

The disk makes a noise similar to clearing one's throat (!) and then follows it up with a click. This happens once within every 5-10 seconds. By the sound I'm guessing the disk heads are being parked (as observed in this and other similar posts). Further more, this click is the same kind I hear when Windows XP powers down on the same laptop. I don't hear this kind of sound when Windows XP is running though.

Anyway, running the -B254 line (from the above replies) on the command line fixes the problem. However, please note that adding the lines to **/etc/hdparm.conf** (to apply it on every boot) doesn't work. I tried with **command_line{}** and also a naked **apm = 254** line. None of them work. Maybe they're being overridden by the settings in **/etc/acpi/power.sh**

For now, I've added the **hdparm -B254 /dev/sda** line to **/etc/rc.local** (just above the **exit 0** line). It works.

If anyone knows a more elegant fix, please do reply.[/FONT]

---

### Post by gertin on 2007-10-22
> **yodha said:**
> [FONT="Courier New"]I'm running **Xubuntu *Gutsy Gibbon*** on a **Fujitsu S7021** laptop. The harddisk is a **Hitachi MK6025GAS**. I'm seeing (rather hearing) the same problem as above.

The disk makes a noise similar to clearing one's throat (!) and then follows it up with a click. This happens once within every 5-10 seconds. By the sound I'm guessing the disk heads are being parked (as observed in this and other similar posts). Further more, this click is the same kind I hear when Windows XP powers down on the same laptop. I don't hear this kind of sound when Windows XP is running though.

Anyway, running the -B254 line (from the above replies) on the command line fixes the problem. However, please note that adding the lines to **/etc/hdparm.conf** (to apply it on every boot) doesn't work. I tried with **command_line{}** and also a naked **apm = 254** line. None of them work. Maybe they're being overridden by the settings in **/etc/acpi/power.sh**

For now, I've added the **hdparm -B254 /dev/sda** line to **/etc/rc.local** (just above the **exit 0** line). It works.

If anyone knows a more elegant fix, please do reply.[/FONT]
Setting the least aggressive power management fixed it for me too. But I'm wondering why this bug hasn't been fixed yet. It seems like it's rather critical and even if it doesn't affect every brand in the same way, it can't be good for any drive to be spun up and down this much. I'm just glad I noticed this so quick, got my latop on Friday and it already has a load cycle count of 851.
```
sudo hdparm -B 254 /dev/sda
```

I think I finally found a more elegant solution.
Edit /etc/hdparm.conf and add the following:
```
/dev/sda {
  apm = 255
  spindown_time = 0
}
```
The reason /etc/hdparm.conf doesn't get read is because the hdparm init script doesn't run by default.
Run sudo update-rc.d hdparm defaults and it will run at boot.
The drive will now never spin down and power management will be turned off.

---

### Post by dimbulb1024 on 2007-10-24
I found this article:
[Explanation of Ubuntu Hard Drive Wear and Tear]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear")
[INDENT]"A recent bug report for Ubuntu Linux has confirmed that both the Feisty and Gutsy versions of Ubuntu cause some unnecessary wear and tear on a hard drive. ..."[/INDENT]
and was wonder what some you more knowledgeable Linux/Ubuntu users think.
As a relative newbie it was an eye catcher but I was not sure whether I should be concerned and/or follow the instructions.

Your insight is appreciated :)

---

### Post by hardyn on 2007-10-24
they author did not mention whether or not he/she uses 'laptop-mode'.

if so... the hard disk spin down is set very agressively by default, and can be easily adjusted by modifying the /etc/laptop-mode/laptop-mode.conf file.  i have set min to 240 seconds.

if we are talking about the same problem, hdparm is a really agressive way of solving it.

---

### Post by dimbulb1024 on 2007-10-24
Thanks hardyn for the location of what file to look at.
So looking at my HD settings, does the "=1" mean laptop mode is turned on for timeout settings? If so are you suggesting increasing the 20 seconds to 240 seconds?

 ```
# Should laptop mode tools control the hard drive idle timeout settings?
#
CONTROL_HD_IDLE_TIMEOUT=1


#
# Idle timeout values. (hdparm -S)
# Default is 2 hours on AC (NOLM_HD_IDLE_TIMEOUT_SECONDS=7200) and 20 seconds
# for battery and for AC with laptop mode on.
#
LM_AC_HD_IDLE_TIMEOUT_SECONDS=20
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=20
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200


#
# Should laptop mode tools control the hard drive power management settings?
#
CONTROL_HD_POWERMGMT=0


#
# Power management for HD (hdparm -B values)
#
BATT_HD_POWERMGMT=1
LM_AC_HD_POWERMGMT=255
NOLM_AC_HD_POWERMGMT=255
```

---

### Post by hardyn on 2007-10-24
change LM_BATT_HD_IDLE_TIMEOUT_SECONDS = 240
and that is it for this file.

then..

in  /etc/default/acpi-support
way at the bottom... change ENABLE_LAPTOP_MODE=true

good luck

---

### Post by a grain of Alt. on 2007-10-24
I just read the article too and came looking to the forums for advice...

Would this affect desktop users or people with SATA hard drives?

---

### Post by hardyn on 2007-10-25
i somehow doubt it... and hdparm does not control many SATA features.

---

### Post by magicman5421 on 2007-10-25
i have been confused by this for some time...what exactly does laptop mode do?

---

### Post by hardyn on 2007-10-25
enables the spinning down of the hard disks after a preset amount of time, and throttles the cpu when the machine is running from battery power.

spinning down the hard disk is worth about 45min of battery life on my computer

---

### Post by djrobthaman on 2007-10-25
I found [this article]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear") on digg today and now I'm a little concerned.  2 or 3 years is a long time, and I've kinda made a pact with myself to upgrade my PC with more frequency than that, but it would be nice to keep the HDs for as long as possible.

So, does anybody know whether this is a genuine concern and whether the "fix" proposed (it's written below)  in the post works and doesn't have some sort of adverse effect on the system.  Just to give an example, I've noticed that (at least with my system) when I use vlc in fullscreen mode the power management settings don't get bypassed and after about 10/20 minutes the screen will go on standby mode.  One way to fix it is to edit the xorg.conf to set the standby time and off time etc, so that the screen never turns off.  Adverse effect - the screen never turns off.  This is obviously a minor problem and a trivial example, but would running this command do something similar, where maybe I wouldn't be able to access the HD all the time because it will take longer to spin or not spin at all to keep in line with the new setting???

Thanks for the info




fix: hdparm -B 255 /dev/sda (I suppose you would run this command for each drive)

---

### Post by Shiva88 on 2007-10-25
I'm also concerned by this news.  I haven't really heard anybody authoritative comment on it though.  Definitely eager for more news on this issue!

---

### Post by andylawrence on 2007-10-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I also read the post.  I ran sudo smartctl -a /dev/sda and my Load_Cycle_Count is at 107593 which concerns me because I just got this laptop 4 months ago.

The fix I used was to add the following to the end of /etc/hdparm.conf

/dev/sda {
  apm = 255
  spindown_time = 0
}

and then add it to the boot process with:

sudo update-rc.d hdparm defaults

It works, I've been monitoring my Load Cycle Count since and it has drastically slowed the count.

BTW this does the same thing as the fix in the first post only sets it automatically every time your machine boots.

---

### Post by isaacj87 on 2007-10-25
Crap,

Well I already disable my APM settings....using hdparm -B 255 /dev/sda

How can I return to the default settings?

---

### Post by isaacj87 on 2007-10-25
or does hdparm reset itself after a suspend, hibernate, reboot or shutdown...

---

### Post by toasty_ghosty on 2007-10-25
I saw this and wanted to know what you guys thought...

[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)

---

### Post by skrimpy on 2007-10-25
I suggest reading this thread: 

[http://ubuntuforums.org/showthread.php?t=590596&highlight=hdparm](http://ubuntuforums.org/showthread.php?t=590596&highlight=hdparm)

which also links to this developer response:

[http://mjg59.livejournal.com/77672.html](http://mjg59.livejournal.com/77672.html)

---

### Post by ezak on 2007-10-25
Well I read this article yesterday, from Digg. While it is an informative article, the problems stated in it merely pertain mostly to laptop harddrives. 

Most Desktop users with standard harddrives don't need to worry about this issue or type in the command listed. 

While it does help, it's for the longevity of the harddrive rather than Gutsy being really hard on the drive itself over a long period of time.

So for laptops, I would definately recommend using it, since laptop drives crap out pretty easily!

---

### Post by HangLoose on 2007-10-25
First of all I'm not here to make any flame wars or instigate users against the distro that I use in a everyday basis: at work and home. I use it in my laptop as in my desktop. Hours straight being my main system. Using windows just to play some games and that is it. Also I can't say that if it's a kernel bug or being identified just in Ubuntu.

Im just want to notify people that DON'T know which bug might be "killing" their hard disks.

I've noticed several "clicks" on my laptop when Im using Ubuntu (since Feisty and Gutsy) and I got annoyed by it. Even when I leave my laptop downloading something the clicks here so high that really made me pissed. Those are load/unload cycles of the hard drive. In Ubuntu this was a known bug but somehow not solved since Feisty.

The good news is that it can be solved with just a simple command:
```
# sudo hdparm -B 255 /dev/sda
```

/dev/sda being the hard disk in question.

After doing this Ive noticed a lower "clicking" rate in my system.

It's pitty that Ive been using Ubuntu for so long and trusting my equipments to it, even friends this somehow simple problem, correct me developers/maintainers if Im wrong, passed unnoticed for the majority of the users.

links:
[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)
[https://bugs.launchpad.net/ubuntu/+bug/104535](https://bugs.launchpad.net/ubuntu/+bug/104535)

---

### Post by gilgongo on 2007-10-25
What brand is your HD?

---

### Post by isaacj87 on 2007-10-25
bumping for answer...

---

### Post by Daelyn on 2007-10-25
When I do the hdparm -B 255 on my Fujitsu HDD it says "setting APM to Disabled".

But, when doing a hdparm -i on the HDD it shows up as Setting: 128.

Have inputted the hdparm value in init.d so it loads at every boot too, still no deal.


Any ideas? Getting seriously annoyed by this too.

---

### Post by toasty_ghosty on 2007-10-25
I bought a Western Digital about a month back, died within a week. Of course, I don't think it was Ubuntu related, but still. I wish harddrives were a little more rubust.

---

### Post by mk04 on 2007-10-25
So..I have two questions:

1) How do we find out how many load/unload cycle a drive has? 

2) For the command that was posted on the article, do we run it for only the partition that Gutsy is located on (hdparm -B 255 /dev/hda3) or for the whole drive (hdparm -B 255 /dev/hda)?

---

### Post by jack handy on 2007-10-25
whats the default value for hdparm -B ?

---

### Post by gmos on 2007-10-25
If you read some of the comments listed under the first article linked in the top post, you'll see that its not a specific Ubuntu problem.

My laptop has always had constant HDD activity - even while running Win XP for its first year.  (was initially concerned by this, but told by ACER support that it was normal for that model).

After switching to Ubuntu a year ago, HDD activity was exactly the same: on off on off several times a minute and the clicking was audible.  So, excessive HDD activity was same despite different OSs.

The comments suggest that it's the BIOS settings that are to blame, that Ubuntu is simply defaulting to those APM settings found in the BIOS at startup.

Did the sudo hdparm -B 255 /dev/sda  and the HDD is now calm and quiet. Much nicer !!!!

Can someone suggest _where/how exactly to place the hdparm command so that it overides the setting taken from the BIOS at startup_?

Perhaps Ubuntu devs could look at this issue (I prefer a long life for my laptop, not aggressive power management).

---

### Post by 444 on 2007-10-25
This appears to be a BIOS issue, ie the "default" values are from the BIOS, different on every laptop (this never happens on mine). They're debating on whether they should overwrite those values in Ubuntu all the time, to something more sane.

> **mk04 said:**
> So..I have two questions:

1) How do we find out how many load/unload cycle a drive has? 

2) For the command that was posted on the article, do we run it for only the partition that Gutsy is located on (hdparm -B 255 /dev/hda3) or for the whole drive (hdparm -B 255 /dev/hda)?

You need to install smartmontools.
 sudo smartctl -a /dev/sda | grep Load_Cycle_Count
And the command runs on whole disks, not just partitions.

---

### Post by gmos on 2007-10-25
> **hardyn said:**
> change LM_BATT_HD_IDLE_TIMEOUT_SECONDS = 240
and that is it for this file.

then..

in  /etc/default/acpi-support
way at the bottom... change ENABLE_LAPTOP_MODE=true

good luck

Just tried this, rebooted,  no change to HDD behaviour ! As if both these files or changes are simply ignored. There must be another setting somewhere that will stop/change HDD settings. ??

sudo hdparm -B 255 /dev/sda  works, but has to be done after each boot. Can this command be inserted somewhere that will overide previous settings on startup?

---

### Post by JKyleOKC on 2007-10-25
Yes; put the command into the rc.local file, just before the existing "exit" command -- and leave off the "sudo" since rc.local executes as root already.

---

### Post by isaacj87 on 2007-10-25
> **gmos said:**
> Just tried this, rebooted,  no change to HDD behaviour ! As if both these files or changes are simply ignored. There must be another setting somewhere that will stop/change HDD settings. ??

sudo hdparm -B 255 /dev/sda  works, but has to be done after each boot. Can this command be inserted somewhere that will overide previous settings on startup?

First, How could you tell it was working? and Secondly, how'd you know it resets everytime you boot?

---

### Post by HangLoose on 2007-10-26
Mine is a HItachi

---

### Post by softtower on 2007-10-26
If you look around in your ACPI settings there is a thing called "laptop mode". I had it turned on but I got rid of it. The description for that module says exactly that: it tries to power down your hard drive as often as possible.

The entire "problem" is solved by apt-get remove.

Unfortunately I don't remember the package name nor configuration files. As I said it was a while ago and I don't have it anymore.

Try locating it with 
> dpkg-query -l laptop*

---

### Post by gmos on 2007-10-26
> **isaacj87 said:**
> First, How could you tell it was working? and Secondly, how'd you know it resets everytime you boot?

Pretty easy - just observing the amount of HDD activity (indicator light and clicking sounds). 

 Normally the HDD activity light is going on and off several times a minute (actually on more than off), even when the machine is idle, and I can hear the clicks as it powers up and down. This is the behaviour set by all that laptop mode APM stuff.

After setting hdparm, all that excessive activity stops. Peace and quiet till the HDD is actually being used to access something.

The suggested changes to those two files didn't change the HDD behaviour at all, and when using the hdparm command, the HDD behaviour returns to its excessive ways after rebooting - hence needing to be set again.

---

### Post by gmos on 2007-10-26
> **JKyleOKC said:**
> Yes; put the command into the rc.local file, just before the existing "exit" command -- and leave off the "sudo" since rc.local executes as root already.

Thanks, will give this a try.  -- Is this file /etc/rc.local ?? or /etc/init.d/rc.local ?

---

### Post by jespdj on 2007-10-26
> **gmos said:**
> Can someone suggest _where/how exactly to place the hdparm command so that it overides the setting taken from the BIOS at startup_?
I have not done it myself yet, but [Launchpad bug #59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) suggests that this setting is in **/etc/acpi/power.sh**, so that would probably be a good place to fix it.

*edit*: Hmmm, it looks like changing it there doesn't always work, according to the comments in that bug report. But there are some other fixed suggested there, so read the comments in the bug report.

---

### Post by HangLoose on 2007-10-26
```
sudo apt-get remove laptop-mode-tools
```

Thanks for the tip man...

But it is still a problem, cos it's something unusual and harmful for the equipment.
We are talking about this now cos he know about it but imagine how many people doesn't know.

---

### Post by jespdj on 2007-10-26
See this thread:
[ Ubuntu bug reducing Hard Drives life time](http://ubuntuforums.org/showthread.php?t=591564)

---

### Post by jespdj on 2007-10-26
Also see this thread:
[ Ubuntu bug reducing Hard Drives life time](http://ubuntuforums.org/showthread.php?t=591564)

---

### Post by zakeen on 2007-10-26
What do you guys think about this with SSD drives? also a problem?

---

### Post by zakeen on 2007-10-26
When you guys say that you hear the HDD start and stop does the light go on also? As Ive got a SSD drive and I cant here but would like to know if its getting some type of access some how.

---

### Post by HangLoose on 2007-10-26
Yep, the led DOES lighten up a bit.

---

### Post by JKyleOKC on 2007-10-26
It's /etc/rc.local although you could add it in the other one, which simply calls the /etc/rc.local script if it exists. Simpler, though, to add commands to /etc/rc.local because it doesn't have to follow the init.d conventions...

---

### Post by DARKGuy on 2007-10-26
Does this "bug" affects desktop HDs too?

---

### Post by jespdj on 2007-10-26
I've now checked out what's happening on my laptop. Yes, I can hear the harddisk click a few times every minute, so my laptop is suffering from the problem.

I first installed smartmontools:
```
sudo apt-get install smartmontools
```
WIth that, you can check various parameters, such as how many on/off power cycles your harddisk has had, how many hours it has been on and how many load cycles it has done. My laptop, which is only 10 days old, shows the following:
```
jesper@jesper-laptop:~$ sudo smartctl -d ata -a /dev/sda
...(snip)...
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       72
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       59
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       74
193 Load_Cycle_Count        0x0022   097   097   000    Old_age   Always       -       6678
```
This means the harddisk has been powered on 74 times, has been in use for 59 hours (the laptop is still new!) and the load cycle count is already 6678.

The high number for Load_Cycle_Count is the problem.

The solution is to set a parameter with hdparm:
```
sudo hdparm -B 200 /dev/sda
```
This works for my harddisk; the number 200 can be anything between 1 and 255, the higher the less aggressive the power management is set, 255 means: switch off power management completely. I tested out different numbers (160, 180, 200) and on 160 or 180 the problem stays, but it is solved with 200.

Now to solve it permanently, I added the following lines to the file /etc/hdparm.conf (at the bottom of the file):
```
/dev/sda {
    apm = 200
}
```
Then I ran the following command to make the change permanent:
```
sudo update-rc.d hdparm defaults
```
That should solve the problem permanently.

---

### Post by HangLoose on 2007-10-26
Very nice post and mine is in already 91693... :mad:

---

### Post by hardyn on 2007-10-27
there is also a /boot/hdparm.conf file if im not mistaken, every time i have played with hdparm it has been there.

Im not sure why your notebook would not listen to the laptop-mode settings, mine does and it is very obvious it is effective... are you using sudo?  is your notebook ACPI enabled?  are you disabling ACPI?

---

### Post by gmos on 2007-10-27
Thanks JKyleOKC, 
saw the rc.local solution on another thread as well.  Works like a charm, a nice quiet well mannered HDD that shows no unneccessary activity. As my laptop is already 2 years old and has always had the extra activity (even its first year running win XP), I hope its life will be extended.

hardyn - yes used sudo to edit those files, can't edit them otherwise. 
I've never touched any ACPI setting - just a default setup, and I don't even know where to enable/disable ACPI, perhaps it is disabled by default (read in a comment from one of the articles on this subject that Ubuntu defaults to the BIOS power management settings, that the devs assume that the comp manufacturer knows the best settings for hardware - so this might explain laptop-mode settings being ignored).

Anyway, if you can advise what and where to look, I'll give it a go.
Thanks.


Just used smartmontools -  Load cycle was already nearly 511,000 !!! Really really annoyed

---

### Post by Polmac on 2007-10-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There has been lots of controversy on this issue. If you don't know what is this about, you might want to see:

[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)
[http://ubuntuforums.org/showthread.php?t=591230](http://ubuntuforums.org/showthread.php?t=591230)
[http://ubuntuforums.org/showthread.php?t=591230](http://ubuntuforums.org/showthread.php?t=591230)

I think this is a serious issue and I don't think the devs are paying enough attention to it. And, furthermore, it is affecting the popularity of Ubuntu (+1000 diggs at digg.com, for example: [http://digg.com/linux_unix/Explanation_of_Ubuntu_Hard_Drive_Wear_and_Tear](http://digg.com/linux_unix/Explanation_of_Ubuntu_Hard_Drive_Wear_and_Tear) ). A bug report was filled a year ago, and I am astonished to see it tagged as 'wishlist'. Do you also think this tagging is absurd or I'm getting a bit paranoid?

---

### Post by takowl on 2007-10-27
Also, could I ask anyone voting that 'wishlist' is sufficient to explain their reasoning, either here or on the bug report?

(I would ask the same for "No" voters, but I think the reasoning is quite obvious)

---

### Post by clem-vangelis on 2007-10-27
lucky you gmos i have Load_Cycle_Count = 613559... and my laptop is only 1 year...what a shame for GNU/linux community and especially maintainer of those scripts...
but has smartctl give me :
  9 Power_On_Hours        ...      348909
my laptop should be running for 39 years...I dunno if smart information are reliable but it's still abnormal...

---

### Post by Masteroc on 2007-10-27
will this reduce the amout of "wear and tear" on a regular 3.5" HD as well?

---

### Post by Polmac on 2007-10-27
By the moment four people have voted "yes", but no luck: no one has cared to stop and explain their position. 

I still don't understand why could be a **wish** to ask Ubuntu not to damage your hardware irreversibly.

---

### Post by louieb on 2007-10-27
I voted to wishlist it.  From what I've read it a power management use issue for laptops. Save power at the expense of extra wear and tear on the hardware. I've also read there are configuration changes that can be made. For now it look to like its all about choices.  Should any Linux distro go fiddle with the decisions made by the PC maker and its BIOS vendor.

---

### Post by Polmac on 2007-10-28
> **louieb said:**
> I voted to wishlist it.  From what I've read it a power management use issue for laptops. Save power at the expense of extra wear and tear on the hardware. I've also read there are configuration changes that can be made. For now it look to like its all about choices.  Should any Linux distro go fiddle with the decisions made by the PC maker and its BIOS vendor.

Well, in fact the rest of linux distros (at least some of them) ignore the value of the BIOS as it is a bit absurd (see [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/119](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/119)). Windows ignores it as well, and if my laptop is "designed for Windows XP" I would think that this is the right thing to do.

---

### Post by takowl on 2007-10-28
Yes, it's related to power management, but these are default settings. The defaults should not be set to save power so aggressively that some people's drives are reaching their lifetime use limits in 6 months.

It is configurable, but not easily. It involves going in and messing around with configuration files and shell scripts, and there does not yet seem to be one agreed method for quickly and permanently resolving the problem. 
Given that Ubuntu is aiming to be Linux for the general user, we cannot expect users to fix this problem themselves (as a *choice*), or even to be aware of it, unless their hard drive happens to be one of those that noticeably clicks on parking the heads.

Finally, I would have to agree with what Polmac has already said. Laptops are designed for Windows XP. If Ubuntu wants to access the drive in a different pattern, it may well need to override some defaults to work best. Also, from reading the comments on the bug report, we do not seem to be of one accord that it is BIOS settings. Some people are still arguing that the settings are being set by Ubuntu.

Wow, long post. Summary:
1) Power use vs drive lifetime is a choice, but setting the defaults so extreme is a **problem**.
2) It doesn't matter whether it is BIOS settings - if Ubuntu trashes your drive and windows doesn't, it's Ubuntu's problem. And we can fix Ubuntu a lot easier than BIOS defaults.

---

### Post by HangLoose on 2007-10-28
[http://ubuntudemon.wordpress.com/2007/10/28/laptop-hardrive-killer-bug-how-to-discover-whether-you-are-affected/#comment-31379](http://ubuntudemon.wordpress.com/2007/10/28/laptop-hardrive-killer-bug-how-to-discover-whether-you-are-affected/#comment-31379)

---

### Post by ubuntu_demon on 2007-10-29
I'm blogging about this issue to get awareness and raise the status (IMHO it should be critical)of the bug. My blog : [http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

People with laptops who haven't enabled laptop-mode and think they are suffering from this problem might consider adding the following information to the bug report :
* the output of $sudo smartctl -a /dev/sda
* the age of your disk 
* an estimate of the total hours your disk has been running since you started using it  (to compare to Power_on_Hours because that value might be off)
* an estimate of the average increase of Load_Cycle_Count during one hour on AC

this is the bugreport we are talking about :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by ubuntu_demon on 2007-10-29
I'm blogging about this issue to get awareness and raise the status (IMHO it should be critical)of the bug. My blog : [http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

People with laptops who haven't enabled laptop-mode and think they are suffering from this problem might consider adding the following information to the bug report :
* the output of $sudo smartctl -a /dev/sda
* the age of your disk 
* an estimate of the total hours your disk has been running since you started using it  (to compare to Power_on_Hours because that value might be off)
* an estimate of the average increase of Load_Cycle_Count during one hour on AC

this is the bugreport we are talking about :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by ubuntu_demon on 2007-10-29
I'm blogging about this issue to get awareness and raise the status (IMHO it should be critical)of the bug. My blog : [http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

People with laptops who haven't enabled laptop-mode and think they are suffering from this problem might consider adding the following information to the bug report :
* the output of $sudo smartctl -a /dev/sda
* the age of your disk 
* an estimate of the total hours your disk has been running since you started using it  (to compare to Power_on_Hours because that value might be off)
* an estimate of the average increase of Load_Cycle_Count during one hour on AC

this is the bugreport we are talking about :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by ubuntu_demon on 2007-10-29
I'm blogging about this issue to get awareness and raise the status (IMHO it should be critical)of the bug. My blog : [http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

People with laptops who haven't enabled laptop-mode and think they are suffering from this problem might consider adding the following information to the bug report :
* the output of $sudo smartctl -a /dev/sda
* the age of your disk 
* an estimate of the total hours your disk has been running since you started using it  (to compare to Power_on_Hours because that value might be off)
* an estimate of the average increase of Load_Cycle_Count during one hour on AC

this is the bugreport we are talking about :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by ubuntu_demon on 2007-10-29
I'm blogging about this issue to get awareness and raise the status (IMHO it should be critical)of the bug. My blog : [http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

People with laptops who haven't enabled laptop-mode and think they are suffering from this problem might consider adding the following information to the bug report :
* the output of $sudo smartctl -a /dev/sda
* the age of your disk 
* an estimate of the total hours your disk has been running since you started using it  (to compare to Power_on_Hours because that value might be off)
* an estimate of the average increase of Load_Cycle_Count during one hour on AC

this is the bugreport we are talking about :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by TheSlayerIsBack on 2007-10-29
> **stealthbox said:**
> After the bug found in the kernel that feisty uses which causes your hardrive to make a pop sound when it shuts down , i have been hessitant to install ubuntu on my laptop.

i did install gutsy beta, but suspend/hibernate dont work which are really important and i could help to notice that my hardrive was making noise. the hardrive is being accessed every 10 seconds without me doing anything and it has a weird noise to it. with XP on the same laptop i dont hear anything, not even when im accessing files.

whats going on with ubuntu on laptops, why does it run so crappy compared to the desktop.

i had ubuntu on my external HDD and it's makeing a pop sound when it's  under load and i installed it on my laptop and it runs great beside the usual sound problems but otherwise no poping sound

---

### Post by arkara on 2007-10-29
i read this on the internet

[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear")
and there must be done something on this subject to fix this small unoticable bug that slowly kills all our hard drives

the solution to this is

```
sudo hdparm -B 255 /dev/sda
```
whereever /dev/sda is the hard disk device that you want to save :D

plz ubuntu team fix this

---

### Post by arkara on 2007-10-29
i have a toshiba laptop and because of a sound problem i always boot with acpi=off do i need to worry about any of this problem?

---

### Post by RAOF on 2007-10-30
So, you'd be talking about [bug 59695](https://bugs.edge.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) (it's a terrible bug report, because so many people have added useless comments; it's now almost impossible to actually **use** that report.  **Please do not add any more comments to it, unless you have some *useful information*** - no, complaining about it's wishlist priority is **not** useful information :)).

However, the important, take home message is: Ubuntu by default does **not** change your hard drive's power management settings.  Enabling laptop mode (which is not enabled by default) will enable aggressive power management when you're on battery, and this will have such a tradeoff (but *may* allow your harddrive to spin up/spin down less often, for a net lifespan increase).  Barring laptop-mode, your harddrive is using the manufacturer-default configuration.

There are a bunch of other, hardware, bugs on that report - it seems a couple of brands of harddrive use 255 for aggressive power management, rather than "off" (so the OP's suggestion will **not** increase your drive's lifespan) - these people may want to set -B 254 if they're going to set anything.

---

### Post by MidBSD on 2007-10-30
I'm not sure if this is extra info or not but I'm using an Acer Aspire 5103 and my laptop mode is disabled yet my load cycle count goes up by one every 5 seconds.

I can confirm that:

sudo hdparm -B 255 /dev/hda

does indeed stop it incrementing.

---

### Post by dptxp on 2007-10-30
Do we have to run the command after every boot ?

---

### Post by MidBSD on 2007-10-30
> **dptxp said:**
> Do we have to run the command after every boot ?

Yes you will.

There is a way of putting it into a script and then having Ubuntu automatically run it every time you boot but I haven't taken the time to work it out yet.

---

### Post by hexion on 2007-10-30
> **MidBSD said:**
> Yes you will.

There is a way of putting it into a script and then having Ubuntu automatically run it every time you boot but I haven't taken the time to work it out yet.

/etc/rc.local
Add the line before the "exit 0"

---

### Post by arkara on 2007-10-30
i have bought a toshiba laptop.
and i get this from the command line

aris@laptop-linux:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       42392

is this much?
considering that i have this laptop for about 4 months
and it's working many hours and it has gone through many formats.
is my hd dying?

i also boot on acpi=off. does this effect the problem in any way?

---

### Post by 23meg on 2007-10-30
It's nowhere near critically high, but pretty high for four months. Do you have laptop-mode enabled?

---

### Post by MidBSD on 2007-10-30
> **hexion said:**
> /etc/rc.local
Add the line before the "exit 0"

Thanks, hexion. Hadn't realised it was as easy as that.

Do you know how the rc0.d, rc1.d, etc folders work?

---

### Post by hexion on 2007-10-30
> **MidBSD said:**
> Thanks, hexion. Hadn't realised it was as easy as that.

Do you know how the rc0.d, rc1.d, etc folders work?

They are the power-on /shutdown scripts executed in each level of execution. But you surely won't need to touch any of those files..

---

### Post by ubuntu_demon on 2007-10-30
> **arkara said:**
> i have a toshiba laptop and because of a sound problem i always boot with acpi=off do i need to worry about any of this problem?
$sudo aptitude install smartmontools
$sudo smartctl -a /dev/sda | grep Load_Cycle_Count

The last number is your Load_Cycle_Count

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

Also look at how fast your Load_Cycle_Count increases.

---

### Post by arkara on 2007-10-30
> **23meg said:**
> It's nowhere near critically high, but pretty high for four months. Do you have laptop-mode enabled?

i dont think i have laptop-mode enabled because i am on acpi=off and i always use ac power on my laptop.

check this file this is my /etc/laptop-mode/laptoo-mode.conf

###############################################################################
# When to enable laptop mode
# --------------------------
#
# "Laptop mode" is the mode in which laptop mode tools makes the computer
# consume less power. This includes the kernel "laptop_mode" feature, which
# allows your hard drives to spin down, as well as various other settings which
# can be tweaked by laptop mode tools. You can enable or disable all of these
# settings using the CONTROL_... options further down in this config file.
###############################################################################


#
# Enable laptop mode when on battery power.
#
ENABLE_LAPTOP_MODE_ON_BATTERY=1


[B][I][U]#
# Enable laptop mode when on AC power.
#
ENABLE_LAPTOP_MODE_ON_AC=0 (i am always on ac power)
[/U][/I][/B]

#
# Enable laptop mode when the laptop's lid is closed, even when we're on AC
# power? (ACPI-ONLY)
#
ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0

---

### Post by maharbA on 2007-10-30
I think the wording of this poll is a bit vague.
At first I thought that the vote was to put this issue on the wishlist or to do nothing.

Maybe the vote could be to leave it on the wishlist or to give it more priority.
2cents

---

### Post by AceRimmer on 2007-10-30
Wishlist?  How about Critical Issue?

---

### Post by formulajay on 2007-10-30
I was wondering how exactly people have come up with a typical hard drive life span is about equal to 600,000 load cycles? I just recently acquired a new(read:hand-me-down) laptop, and I just installed Ubuntu on it, and today I was just reading over at slashdot and saw this 'Ubuntu Killer' post and read a little about it. I then proceeded to check the load cycle count on this newly acquired laptop only to find a cycle count more than double what is considered the average life span of a hard drive. My load cycle count is at 

225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       1387419

Almost 1.4 million cycles. I also do not seem to be experiencing any odd symptoms or misbehavior from the computer. I am unsure if this is anything to be concerned about.

---

### Post by David A Knight on 2007-10-30
> **arkara said:**
> i read this on the internet

[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear")
and there must be done something on this subject to fix this small unoticable bug that slowly kills all our hard drives

the solution to this is


Disabling power management is not a real solution, unless of course you aren't worried about the more expensive piece of hardware in a laptop, called a battery.

The number given in the rants / the launchpad bug of 600,000 or even 300,000 for older drives is IMO plain scare mongering.  My basis for this? I have an old laptop that has been running continuously for the past 27 months, it was in more normal use as a laptop before this.  The load cycle count?


[HTML]193 Load_Cycle_Count        0x0012   038   038   000    Old_age   Always       -       628814[/HTML]

38 is quite some way from 0, and as you can see, I am well past 600,000.  The drive is IC25N020ATCS04-0, an IBM/Hitachi Travelstar.

---

### Post by Baby Boy on 2007-10-30
> **arkara said:**
> i dont think i have laptop-mode enabled because i am on acpi=off and i always use ac power on my laptop.

check this file this is my /etc/laptop-mode/laptoo-mode.conf

###############################################################################
# When to enable laptop mode
# --------------------------
#
# "Laptop mode" is the mode in which laptop mode tools makes the computer
# consume less power. This includes the kernel "laptop_mode" feature, which
# allows your hard drives to spin down, as well as various other settings which
# can be tweaked by laptop mode tools. You can enable or disable all of these
# settings using the CONTROL_... options further down in this config file.
###############################################################################


#
# Enable laptop mode when on battery power.
#
ENABLE_LAPTOP_MODE_ON_BATTERY=1


[B][I][U]#
# Enable laptop mode when on AC power.
#
ENABLE_LAPTOP_MODE_ON_AC=0 (i am always on ac power)
[/U][/I][/B]

#
# Enable laptop mode when the laptop's lid is closed, even when we're on AC
# power? (ACPI-ONLY)
#
ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0

That's how my laptop-mode.conf looks too. I also have nearly identical output from 
> sudo smartctl -a /dev/sda | grep Load_Cycle_Count
> 
193 Load_Cycle_Count        0x0012   097   097   000    Old_age   Always       -       32540
225 Load_Cycle_Count        0x0012   097   097   000    Old_age   Always       -       32540

and I have my laptop for about 3-4 months. 

I am guessing I should keep laptop-mode **off** since I'm running on AC power all the time as well?

---

### Post by kazuya on 2007-10-30
i voted yes, however, I believe it should be a critical item. It may scare alot of laptop users off. How true is this concept of hard drive damage.. Is this damage limited to just Hitachi hard drives? How do you know if it is damaging your hard drive?

Is this related to the kernel? Could this be fixed by a kernel upgrade?

---

### Post by Linicks on 2007-10-30
I voted no.

I also see it is on /. now, oh dear.

This isn't a Ubuntu issue at all.

Also, has anybody had a hard drive get [sic] 'killed' by this?  Any reports?  Any information that this did kill a HD with evidence?

According to the popularity of this mis-report, there should be 1000's by now.  I haven't seen anybody report one yet?

Nick

---

### Post by siloko on 2007-10-30
For Information Only

My Toshiba Equium M70 is about 18 monthes old. It has pretty much only run Edgy, Feisty and now Gutsy. I rarely run my laptop on battery power, although I occassionally (every month or so) drain the battery because of my superstitious belief that it helps keep it's charge capacity.

sudo smartctl -a /dev/sda | grep Load_Cycle_Count

returns

193 Load_Cycle_Count        0x0012   030   030   000    Old_age   Always       -       706142

I have now turned APM off (hdparm -B 255 /dev/sda) and the Load_Cycle_Count which previously was going up several times a minute is now static. I am still open minded about the trade off between proper power management and HD lifecycle but it stands to reason that the more times the heads "park and unpark" - the closer that disk is to the end of its life. I'm interested in peoples thoughts on this issue.

incidentally

grep ENABLE_LAPTOP_MODE /etc/default/acpi-support

returns FALSE whether or not the power lead is plugged in.

---

### Post by #Reistlehr- on 2007-10-30
I don't know why people blame it on ubuntu. It's more than just Ubuntu.

My logs read out
```

  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       1620
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1037
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       373
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       43598

```

According to this, over the past 68 days or total drive usage, there have been 43.5k cycle counts. ftr, it's a fujitsu drive.

I'm not worried.

---

### Post by lxowle on 2007-10-30
I've been trying to stop my load_count from incrementing - but it keeps going up - I was hoping someone could help me here.

I'm using a laptop, on ac power. I've installed smartctrl, and I use the following command to output my load count to a file:

```

echo `sudo smartctl -a /dev/sda2 | grep Load_Cycle_Count` " | " `date` >> load_count
```

This outputs the following:

```
225 Load_Cycle_Count 0x0012 068 068 000 Old_age Always - 331400  |  Wed Oct 31 10:23:13 EST 2007

```

And this number increments several times a minute.

I've tried using the following command to stop this (also with sda1,sda2,sda3 - 'cos I don't know what I'm doing):

```
sudo hdparm -B 255 /dev/sda
```

And I get the following output:
```

/dev/sda:
 setting Advanced Power Management level to disabled

```

However, when I recheck the load cycles, they still have gone up.

Anyone with any ideas?

---

### Post by ghotra on 2007-10-30
With the recent [talk]("http://hardware.slashdot.org/article.pl?sid=07/10/30/1742258") of too many HD cycles, I am trying to figure out if I have this problem as well:

Here is a sample of my load cycle...is this climbing too fast?

```
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163813  |  Tue Oct 30 12:22:27 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163818  |  Tue Oct 30 12:24:26 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163819  |  Tue Oct 30 12:30:42 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163834  |  Tue Oct 30 12:41:11 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163839  |  Tue Oct 30 12:56:51 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163841  |  Tue Oct 30 13:00:19 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163855  |  Tue Oct 30 13:10:02 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163870  |  Tue Oct 30 13:18:09 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163874  |  Tue Oct 30 13:21:46 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163874  |  Tue Oct 30 13:25:56 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163879  |  Tue Oct 30 13:44:34 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 163882  |  Tue Oct 30 14:05:07 PDT 2007
193 Load_Cycle_Count 0x0032 084 084 000 Old_age Always - 164155  |  Tue Oct 30 16:35:55 PDT 2007

```

Seems like I'll hit 600000 pretty soon.

---

### Post by aztektum on 2007-10-30
Got this number off my X41. Does this count off starting from OS install or is it cached on the HDD? I have used Ubuntu on here since Edgy, but wiped for Gutsy.

```
193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       426007094159

```

That seems awful high. Although my drive does make a pretty hard click sound rather frequently. It has bugged me in that "Hm that's not right." way.

---

### Post by RAOF on 2007-10-30
> **aztektum said:**
> Got this number off my X41. Does this count off starting from OS install or is it cached on the HDD? I have used Ubuntu on here since Edgy, but wiped for Gutsy.

```
193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       426007094159

```

That seems awful high. Although my drive does make a pretty hard click sound rather frequently. It has bugged me in that "Hm that's not right." way.

It's stored on the hard drive (that's SMART data which is provided by the hard drive itself).  Given your hard drive reports 4x10^11 cycles (ie: many, many million), I'd be inclined to suspect that your drive misreports this particular SMART data :).

---

### Post by kfazz on 2007-10-30
something tells me this is bad...
ken@ubuntu-laptop:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   001   001   050    Old_age   Always   FAILING_NOW 1843146/1842722
(from my ancient EOL compaq armada)

---

### Post by robzon on 2007-10-30
My about 18-month acer says:

193 Load_Cycle_Count        0x0012   086   086   000    Old_age   Always       -       140916

and I'm running default ubuntu config both on AC and battery. Is this a problem for all hardware? My laptop seems to be doing just fine.

---

### Post by RAOF on 2007-10-30
> **robzon said:**
> ...
and I'm running default ubuntu config both on AC and battery. Is this a problem for all hardware? My laptop seems to be doing just fine.

No, it's not a problem on for all hardware.  Ubuntu by default doesn't mess with your hard-drive power management, so only hard drives/bioses that set aggressive power management by default will be affected.

---

### Post by Hortinstein on 2007-10-31
just curious if there is a list of Bios that do that...I am running a dell inspirion 1501 that I bought a few months...I have never upgraded the BIOS or anything

---

### Post by ubuntu_demon on 2007-10-31
**I’m a big fan of Ubuntu. I don’t want to see Ubuntu hurt because it’s not Ubuntu who is setting these aggressive power management defaults.**

**Some background of the problem :**

If your harddrive spins down and spins up again your Load_Cycle_Count increases by one. If your harddrive head parks and unparks again your Load_Cycle_Count increases by one.

You don’t want your Load_Cycle_Count to increase too fast.

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

**Ubuntu is NOT causing aggressive power management.**

The following things might instead cause aggressive power management settings :

* your (laptop) harddrive firmware might have aggressive power management defaults (operating system independent)
* your (laptop) BIOS might set your harddrive to use aggressive power management (operating system independent)
* you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

These aggressive power management settings are set by your BIOS or harddrive firmware. Windows and/or Mac OS X might be overriding these settings which might make Ubuntu look bad if Ubuntu doesn't override these settings.

Read here what Matthew Garret an experienced and well known Ubuntu Developer has said about this problem :
[http://www.advogato.org/person/mjg59/diary/82.html](http://www.advogato.org/person/mjg59/diary/82.html) 

for more information see :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Some background of the problem :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)[/B]

I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Some background of the problem :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)[/B]

I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Some background of the problem :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)[/B]

I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Some background of the problem :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)[/B]

I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Some background of the problem :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)[/B]

I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by nocturn on 2007-10-31
This is not an Ubuntu bug (though Ubuntu could fix it) unless laptop mode was enabled (it is not so by default).

Without laptop mode, the settings from your bios remain unchanged and they are probably causing the frequent unloads.

---

### Post by ubuntu_demon on 2007-10-31
**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperate and make sure it remains below the maximum temperature specification of your harddrive. [COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

[B]This thread continues here :
[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)[/B]

Explanation of the problem :
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=1](http://ubuntuforums.org/showpost.php?p=5031046&postcount=1)

Unofficial Ugly fix for Gutsy :
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=2](http://ubuntuforums.org/showpost.php?p=5031046&postcount=2)

Unofficial Ugly fix for Hardy :
[http://ubuntuforums.org/showpost.php?p=5031046&postcount=3](http://ubuntuforums.org/showpost.php?p=5031046&postcount=3)

[B]This thread continues here :
[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)[/B]

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperate and make sure it remains below the maximum temperature specification of your harddrive. [COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Now to determine whether you actually suffer from this problem and the ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
[/B]
I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Now to determine whether you actually suffer from this problem and the ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
[/B]
I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Now to determine whether you actually suffer from this problem and the ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
[/B]
I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Now to determine whether you actually suffer from this problem and the ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
[/B]
I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Now to determine whether you actually suffer from this problem and the ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
[/B]
I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by weblordpepe on 2007-10-31
Ok my load_cycle_count kept going up by 1 every 30 seconds or so.

i did has you suggested. It now seems to have stopped incrementing. I have no clue whats going on really. Well sorta. But if it breaks well Im stummped :P

---

### Post by ubuntu_demon on 2007-10-31
> **weblordpepe said:**
> Ok my load_cycle_count kept going up by 1 every 30 seconds or so.

i did has you suggested. It now seems to have stopped incrementing. I have no clue whats going on really. Well sorta. But if it breaks well Im stummped :P
If your Load_Cycle_Count goes up it means that your harddrive has made one
spin-down/spin-up cycle or one park-head/unpark-head cycle. Your harddrive is specified for a limited number of these cycles. 

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

---

### Post by MidBSD on 2007-10-31
> **hexion said:**
> They are the power-on /shutdown scripts executed in each level of execution. But you surely won't need to touch any of those files..

You'e right, I won't need to touch any of those :)

Just curious and want to learn what I can. Thanks again.

---

### Post by MidBSD on 2007-10-31
> **siloko said:**
> I rarely run my laptop on battery power, although I occassionally (every month or so) drain the battery because of my superstitious belief that it helps keep it's charge capacity.


It is a superstitious belief. :)

You usually do that with Nickel-Cadmium batteries because of what's called the 'memory effect'. In Lithium Ion batteries, you can actually damage your battery by discharging completely if you do it often.

A battery is made up of several smaller batteries (cells) and if one discharges completely before the rest, it'll start to be reverse charged by the remaining cells - it's the reverse charging that damages them.

...but that's a little off topic. Maybe someone will start a blog post entitled "Ubuntu Explodes My Battery!" :(

---

### Post by MidBSD on 2007-10-31
> **RAOF said:**
> No, it's not a problem on for all hardware.  Ubuntu by default doesn't mess with your hard-drive power management, so only hard drives/bioses that set aggressive power management by default will be affected.

Perhaps it should be overridden in Ubuntu or users could be allowed to set it in the Power Management applet?

Those two things ought to be enough to placate all users.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Some background of the problem :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)[/B]

I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-10-31
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Now to determine whether you actually suffer from this problem and the ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
[/B]
I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by rogirwin on 2007-10-31
> **ubuntu_demon said:**
> Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

My laptop is a HP 6710b and was brought new in July. From then until the 18th of Oct it has been running Slackware 12. It was then upgraded to gusty and been running it ever since. The Load_Cycle_Count of 337032 seems very high? How is this possible? It's hasn't changed in the 15 mins.

Device Model:     ST9120822AS
Firmware Version: 3.ALB
User Capacity:    120,034,123,776 bytes

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       325844
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       59
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   073   062   030    Pre-fail  Always       -       23863322
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       480
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       59
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   053   046   045    Old_age   Always       -       791019567
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       42
**193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       337032**
194 Temperature_Celsius     0x0022   047   054   000    Old_age   Always       -       47 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   077   061   000    Old_age   Always       -       160277953
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

---

### Post by arkara on 2007-10-31
so what i have seen from all this i dont know what to believe anymore.
does smart provide credible data?

also is there a commant to see if we are all on laptop mode?

---

### Post by ubuntu_demon on 2007-10-31
> **rogirwin said:**
> My laptop is a HP 6710b and was brought new in July. From then until the 18th of Oct it has been running Slackware 12. It was then upgraded to gusty and been running it ever since. The Load_Cycle_Count of 337032 seems very high? How is this possible? It's hasn't changed in the 15 mins.

Device Model:     ST9120822AS
Firmware Version: 3.ALB
User Capacity:    120,034,123,776 bytes

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       325844
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       59
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   073   062   030    Pre-fail  Always       -       23863322
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       480
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       59
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   053   046   045    Old_age   Always       -       791019567
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       42
**193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       337032**
194 Temperature_Celsius     0x0022   047   054   000    Old_age   Always       -       47 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   077   061   000    Old_age   Always       -       160277953
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0
to rogirwin :

Keep watching that value. Sometimes the value is not a simple counter. There's a way to automatically watch your Load_Cycle_Count :
[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/#comment-31724](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/#comment-31724)

Your WORST is very close to the THRESHOLD you might consider backing all your data and running the diagnostic tool of your harddrive's manufacturer.

---

### Post by ubuntu_demon on 2007-10-31
> **arkara said:**
> so what i have seen from all this i dont know what to believe anymore.
does smart provide credible data?

also is there a commant to see if we are all on laptop mode?
laptop-mode is disabled by default. You are not running in laptop-mode unless you have enabled it yourself in /etc/default/acpi-support

To see whether you are in laptop mode :
$ cat /proc/sys/vm/laptop_mode
$ sudo laptop_mode status

The following things might instead cause aggressive power management settings :

 * your (laptop) harddrive firmware might have aggressive power management defaults (operating system independent)
 * your (laptop) BIOS might set your harddrive to use aggressive power management (operating system independent)
 * you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

The smartctl values aren't always easy to interpret. If the Load_Cycle_Counter value behaves as a counter and is below impossible to reach values it's probably the right number. 

You can also look at "WORST" and "TRESHOLD"  (|more instead of |grep to easily see which value is "WORST" and which value is "TRESHOLD") :
$ sudo smartctl -a /dev/sda | more

If "WORST" is near TRESHOLD or if WORST is lowering (too fast) than you might be suffering from this problem. You can roughly calculate how long it will take for WORST to reach TRESHOLD if you keep watching those values daily/weekly.

---

### Post by DBAlex on 2007-10-31
Im on a laptop but /dev/sda doesn't exist but when I executed the following I got this result:

```
alex@alex-acer-laptop:/dev$ sudo smartctl -a /dev/hda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0012   099   099   000    Old_age   Always       -       18673

```

Should I be worried? (This laptop was bought in January, and has previously been running XP which swapped to the hard drive _a_lot_ ...

Thanks for any info :)

---

### Post by MidBSD on 2007-10-31
> **arkara said:**
> so what i have seen from all this i dont know what to believe anymore.
does smart provide credible data?

also is there a commant to see if we are all on laptop mode?

Everything you've read about Load_Cycle_Count incrementing on some systems is true. It's increasing rapidly for some but it's not affecting others.

Manufacturers claim their drives have an expected lifetime. Expected lifetimes will be dependent on model and manufacturer.

It appears that the problem is caused by the BIOS setting an overly aggressive energy saving policy but that's not the fault of Ubuntu. It's also the reason I suggest that it should be overridden by Ubuntu. I'm guessing that it's what happens in other OS as I know I don't have this problem in Windows and I dual boot.

Ultimately, if you suffer from this problem, set your hdparm to suit your needs.

BTW, great posts ubuntu_demon - you've done a great job in gathering all the relevant info in one place :)

---

### Post by ubuntu_demon on 2007-10-31
> **MidBSD said:**
> 
BTW, great posts ubuntu_demon - you've done a great job in gathering all the relevant info in one place :)

Thanks :)

I will add comments with small things I find to :
[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

 I won&#8217;t blog again about this problem until new information arises because I don't want to spam planet.ubuntu.com

You should also take a look here :
[https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216)

---

### Post by sliwowitz on 2007-10-31
```
225 Load_Cycle_Count        0x0012   068   068   000    Old_age   Always       -       323915
``` This laptop is about 20 months old and I use it every day. Now I'm trying to at least stop the count from increasing...

[rant]
 I use linux for about 4 years, so I'm pretty used to having to solve problems myself, but this time, I am extremely frustrated with the complete ignorance from responsible developers. The problem here is, that no matter, what some proud developer says, if other systems do not kill the hardrive, while ubuntu does, it is obviously an ubuntu problem. **If you install some other system, your drive will not wear so soon. If you install ubuntu, your drive will soon die.** The implication is obvious no matter who is to blame. There is nothing more to say about it. This is what I have to tell all of my friends, to whom I installed ubuntu in past two years. I have to apologize to them for their soon-to-be lost data etc. 

The worst part is, there is nothing I can do about it. The fixes are already known, it's just the develpers, who decided it's not an important issue. Gross. Do they realize how expensive could a harddrive be in some parts of the world? That here, taking an average salary and 8 workhours a day, one has to work for two full weeks to afford one such harddrive? That somewhere it is even more expensive?

For all those people, it would seem to be much easier to buy a Windows licence for a price of an average harddrive, than to have to buy a new drive every two years. And they would be definitely right.
[/rant]

---

### Post by ubuntu_demon on 2007-10-31
> **DBAlex said:**
> Im on a laptop but /dev/sda doesn't exist but when I executed the following I got this result:

```
alex@alex-acer-laptop:/dev$ sudo smartctl -a /dev/hda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0012   099   099   000    Old_age   Always       -       18673

```

Should I be worried? (This laptop was bought in January, and has previously been running XP which swapped to the hard drive _a_lot_ ...

Thanks for any info :)
18.673 is a fine value for a laptop which you have since january. But just in case keep monitoring your Load_Cycle_Count the next following days to watch how fast it increases.  You can calculate yourself whether your Load_Cycle_Count increases too fast or not.

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

---

### Post by ubuntu_demon on 2007-10-31
> **sliwowitz said:**
> ```
225 Load_Cycle_Count        0x0012   068   068   000    Old_age   Always       -       323915
``` This laptop is about 20 months old and I use it every day. Now I'm trying to at least stop the count from increasing...

[rant]
 I use linux for about 4 years, so I'm pretty used to having to solve problems myself, but this time, I am extremely frustrated with the complete ignorance from responsible developers. The problem here is, that no matter, what some proud developer says, if other systems do not kill the hardrive, while ubuntu does, it is obviously an ubuntu problem. **If you install some other system, your drive will not wear so soon. If you install ubuntu, your drive will soon die.** The implication is obvious no matter who is to blame. There is nothing more to say about it. This is what I have to tell all of my friends, to whom I installed ubuntu in past two years. I have to apologize to them for their soon-to-be lost data etc. 

The worst part is, there is nothing I can do about it. The fixes are already known, it's just the develpers, who decided it's not an important issue. Gross. Do they realize how expensive could a harddrive be in some parts of the world? That here, taking an average salary and 8 workhours a day, one has to work for two full weeks to afford one such harddrive? That somewhere it is even more expensive?

For all those people, it would seem to be much easier to buy a Windows licence for a price of an average harddrive, than to have to buy a new drive every two years. And they would be definitely right.
[/rant]

**Ubuntu is NOT causing aggressive power management.**

The following things might instead cause aggressive power management settings :

* your (laptop) harddrive firmware might have aggressive power management defaults (operating system independent)
* your (laptop) BIOS might set your harddrive to use aggressive power management (operating system independent)
* you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

These aggressive power management settings are set by your BIOS or harddrive firmware. Windows and/or Mac OS X might be overriding these settings which might make Ubuntu look bad if Ubuntu doesn&#8217;t override these settings. I agree that Ubuntu should override these settings.

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000

In your case watch how fast your WORST is approaching your THRESHOLD after applying the fix to calculate a rough estimate of how much lifetime your disk has left. To be safe backup all your data and test your harddrive with the diagnostic tool of your manufacturer.

---

### Post by kazuya on 2007-10-31
It does not phase me as I have not experienced this. I believe if it be a FUD, then it should be addressed or answered. Some folk made the comment and it is out there in slashdot, etc. If a counter argument is not mentioned or a fix if applicable for laptop users is not announced then that may lead to some panicking, perhaps for no true danger...

This is the link:
[http://hardware.slashdot.org/hardware/07/10/30/1742258.shtml](http://hardware.slashdot.org/hardware/07/10/30/1742258.shtml)

wwrmn writes 
"There's a debate going on over at bugs.launchpad.net on whether it's the Ubuntu, BIOS, hard-drive manufacturer, or pick-any-player's fault, but Ubuntu (and perhaps any OS) may be dramatically shortening the life of your laptop's hard drive due to an aggressive power-saving feature / acpi bug / OS configuration. Regardless of where the fault lies or how it's fixed, you might want to take some actions now to try to prevent the damage."

They say a fix has been posted at the forum:

[https://launchpad.net/bug59695.html](https://launchpad.net/bug59695.html)

---

### Post by ubuntu_demon on 2007-10-31
I added a bit of information about WORST and THRESHOLD relevant to your Load_Cycle_Count.

---

### Post by meldroc on 2007-10-31
How the hell do I fix this:?

I just ran "sudo smartctl -d ata -a /dev/sda"

I believe the relevant line is:

193 Load_Cycle_Count        0x0012   031   031   000    Old_age   Always       -       692741

692471: WTF :mad::eek:

This will ******* fry my hard drive!

Developers, don't tell me "It's not my problem."  If you have the means to fix this, than DO IT!

---

### Post by rybu on 2007-10-31
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       713621

I have no idea what Load_Cycle_Count is measuring.  On my laptop which I bought in August it's at 713621 and going up by about 24 units every 30 seconds.   

I'm not hearing any clicks, and my hard drive hasn't failed.

---

### Post by rybu on 2007-10-31
> **#Reistlehr- said:**
> I don't know why people blame it on ubuntu. It's more than just Ubuntu.

My logs read out
```

  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       1620
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1037
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       373
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       43598

```

According to this, over the past 68 days or total drive usage, there have been 43.5k cycle counts. ftr, it's a fujitsu drive.

I'm not worried.

That's interesting.  My laptop has been on for a shorter time, but has a way higher load_cycle_count.   What might be the cause of that?

```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   107   089   034    Pre-fail  Always       -       105738978
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       352
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       36790154
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1392
 10 Spin_Retry_Count        0x0013   100   092   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   032    Old_age   Always       -       141
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   001   001   000    Old_age   Always       -       5850
190 Temperature_Celsius     0x0022   068   044   045    Old_age   Always   In_the_past 588775456
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       3169
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       713776
194 Temperature_Celsius     0x0022   032   056   000    Old_age   Always       -       32 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   061   048   000    Old_age   Always       -       105738978
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0


```

---

### Post by jongkind on 2007-10-31
This Ubuntu Wiki page pretty much summarizes the situation. 

[https://wiki.ubuntu.com/DanielHahler/Bug59695]("https://wiki.ubuntu.com/DanielHahler/Bug59695")

---

### Post by SeanBlader on 2007-10-31
> **#Reistlehr- said:**
> I don't know why people blame it on ubuntu. It's more than just Ubuntu.

According to this, over the past 68 days or total drive usage, there have been 43.5k cycle counts. ftr, it's a fujitsu drive.

I'm not worried.

You're looking at under 2 years of total drive lifetime if it's designed to go to 600k load cycles. If it's going to crash at 300k load cycles you're looking at replacing your hard drive every year. My laptop is 5 years old and I have 209k cycles.

I'll worry for you.

Oh and I voted for it not being a wishlist item. If there's an option to extend the lifetime of your main hard drive to years instead of months with a software setting, then it should definitely be a mission critical item.

---

### Post by ubuntu_demon on 2007-10-31
> **rybu said:**
> 193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       713621

I have no idea what Load_Cycle_Count is measuring.  On my laptop which I bought in August it's at 713621 and going up by about 24 units every 30 seconds.   

I'm not hearing any clicks, and my hard drive hasn't failed.
If your Load_Cycle_Count goes up it means that your harddrive has made one
spin-down/spin-up cycle or one park-head/unpark-head cycle. Your harddrive is specified for a limited number of these cycles.

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

In your case you have a Load_Cycle_Count of 713.621 which is a lot.

smartctl is reporting that your "WORST" (1) is almost on your "THRESHOLD" (0).

You should consider backing up all your data and running the diagnostic tool of your harddrive manufacturer on your harddrive.

To see what each value means :
$sudo smartctl -a /dev/sda | more

---

### Post by houstonbofh on 2007-10-31
I did not vote.  There is a lot of talk and panic, and almost no hard information.  I do know that all of my laptops have been on Ubuntu for several years, and my hard drives are still running well.  If this kills a hard drive in a year, I should have replaced them all 2-3 times...  I also know that SMART numbers are often totally off.  One time my SMART temperature was below ambient on a running machine.  Later it was over 200f on the same drive.  We need a lot more information to know if this is an Ubuntu bug, a BIOS bug, a hard drive bug, or nothing at all.  However, this publicity is an Ubuntu *problem* in that everyone is looking for the sky to fall!

---

### Post by Kow on 2007-10-31
I am surprised that this fuss has received as much attention as it has. I always thought people knew that hard drive spin-up/spin-down is harsh and reduces the lifespan of the drive. What made me mad about this was the slashdot article blaming ubuntu for this. Anyways, another option to try if you want to maximize your hard drive life and dont care about up-to-date timestamps would be to modify /etc/fstab as superuser and add the "noatime" option to your root partition (mounted as /). After doing this and letting ubuntu sit on the desktop I noticed a sharp decline in hard drive access. The atime feature will usually cause a quick hard drive access every 20-30 seconds and this in itself is not a problem, but couple it with aggressive power mode settings then the hard drive strain can be greatly increased.

It seems correct to allow hard drive manufactures to determine the best settings, until now. I think all of this hard-drive commotion is directed towards the wrong people...

---

### Post by houstonbofh on 2007-10-31
I think there is a lot more panic than real problem.  I mean this is not exactly a new problem, yet I have not heard of massive Linux hard drive failures.  (I know mine haven't)  I think this is mainly panic, and slashdot has not helped this at all

---

### Post by Offoffoff on 2007-10-31
I think this is nonsense You wrote. I use my laptop with laptop-mode and I enabled ENABLE_LAPTOP_MODE in /etc/default/acpi-support... And what's happened? it works fine! maybe /dev/hands?

---

### Post by vikrant82 on 2007-10-31
I think its potentially dangerous for hard disks. However the fix is easy. My count hasn't changed much after i applied the fix. I was averaging 40/hour with value of 450500. 

However, I was also curious about another count which is Power-Off_Retract_Count, which increases only when I shutdown from Ubuntu. 

Anyways, more on these two [here.]("http://kakku.wordpress.com/2007/10/29/s-m-a-r-t-parameters-for-hard-disk-possible-ubuntu-bugs-with-handling-laptop-hard-disks-laptop-hardisks-being-killed/")

Sorry, I just posted this on other thread. Surely, not trying to spam.

---

### Post by icedtea on 2007-10-31
My laptop is also having this problem and no matter what I do, I can't stop Load_Cycle_Count from increasing.

I ran sudo hdparm -B 254 /dev/sda and it slowed down the increase but hasn't stopped it. I noticed that if I don't access my hard drive for a long time, the count doesn't increase for the first ~5 minutes, but then starts increasing about 1 count per minute, until I access my hard drive again.

I've tried other values of -B, including 255, and they aren't any better. And when I check the -B value with hdparm -I, it confirms that it is at the value I set. My laptop hard drive is a Toshiba MK8026GAX.

Any suggestions? Maybe a script to make the hard drive do something every 5 minutes?

Oh, and the spindown value is set at 0, so it shouldn't be spinning down. Other values don't help either. Also, this is happening on AC power with laptop mode disabled.

---

### Post by dimbulb1024 on 2007-10-31
Since originally posting this thread I have been reading as much as I can.
I have checked my BIOS (Dell Inspiron 6000) and I can find nothing there that jumps out to as controlling the hard drive (Hitachi Travelstar 5K100).  As for as my hard drives firmware, I am lost.
I have installed the smart monitor tools and in the past hour my Load_Cycle_Count has increased by about 30. My current Load_Cycle_Count is 115121 on a hard drive maybe 1.5 years old (and I have only been using Linux/Ubuntu since January 07 - is this when this count actually began or does it go back to when I was running XP?).

Now as someone who is nervous about doing the things that ubuntu_demon amongst others suggests am I just left to let my Load_Cycle_Count skyrocket?

---

### Post by dimbulb1024 on 2007-10-31
This is from a Post to a Thread I started on Absolute Beginner Talk
[http://ubuntuforums.org/showthread.php?t=589936](http://ubuntuforums.org/showthread.php?t=589936)

> Since originally posting this thread I have been reading as much as I can.
I have checked my BIOS (Dell Inspiron 6000) and I can find nothing there that jumps out to as controlling the hard drive (Hitachi Travelstar 5K100). As for as my hard drives firmware, I am lost.
I have installed the smart monitor tools and in the past hour my Load_Cycle_Count has increased by about 30. My current Load_Cycle_Count is 115121 on a hard drive maybe 1.5 years old (and I have only been using Linux/Ubuntu since January 07 - is this when this count actually began or does it go back to when I was running XP?).

Now as someone who is nervous about doing the things that ubuntu_demon amongst others suggests am I just left to let my Load_Cycle_Count skyrocket?

To me it is not a wishlist item but critical for a newbie.

---

### Post by ubuntu_demon on 2007-10-31
> **Offoffoff said:**
> I think this is nonsense You wrote. I use my laptop with laptop-mode and I enabled ENABLE_LAPTOP_MODE in /etc/default/acpi-support... And what's happened? it works fine! maybe /dev/hands?
That's great for you. I've never said that everyone suffers from this problem. If you haven't enabled laptop-mode only specific harddrives and specific BIOS'es are setting aggressive power management settings.

The following things might instead cause aggressive power management settings :

    * your (laptop) harddrive firmware might have aggressive power management defaults (operating system independent)
    * your (laptop) BIOS might set your harddrive to use aggressive power management (operating system independent)
    * you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

---

### Post by ubuntu_demon on 2007-10-31
> **dimbulb1024 said:**
> Since originally posting this thread I have been reading as much as I can.
I have checked my BIOS (Dell Inspiron 6000) and I can find nothing there that jumps out to as controlling the hard drive (Hitachi Travelstar 5K100).  As for as my hard drives firmware, I am lost.
I have installed the smart monitor tools and in the past hour my Load_Cycle_Count has increased by about 30. My current Load_Cycle_Count is 115121 on a hard drive maybe 1.5 years old (and I have only been using Linux/Ubuntu since January 07 - is this when this count actually began or does it go back to when I was running XP?).

Now as someone who is nervous about doing the things that ubuntu_demon amongst others suggests am I just left to let my Load_Cycle_Count skyrocket?

Let's hope there will be an official fix within a few days which is the best solution if your Load_Cycle_Count only grows moderately. 

But if you are experiencing a Load_Cycle_Count increase of a couple of thousands per day (as some people are experiencing) then you shouldn't wait too long.

---

### Post by ubuntu_demon on 2007-10-31
> **icedtea said:**
> My laptop is also having this problem and no matter what I do, I can't stop Load_Cycle_Count from increasing.

I ran sudo hdparm -B 254 /dev/sda and it slowed down the increase but hasn't stopped it. I noticed that if I don't access my hard drive for a long time, the count doesn't increase for the first ~5 minutes, but then starts increasing about 1 count per minute, until I access my hard drive again.

I've tried other values of -B, including 255, and they aren't any better. And when I check the -B value with hdparm -I, it confirms that it is at the value I set. My laptop hard drive is a Toshiba MK8026GAX.

Any suggestions? Maybe a script to make the hard drive do something every 5 minutes?

Oh, and the spindown value is set at 0, so it shouldn't be spinning down. Other values don't help either. Also, this is happening on AC power with laptop mode disabled.
You should try both of these things :
* Try whether your BIOS has any options regarding power management and turn them off. 
* The manufacturer of your harddisk might also have a tool available for download which can tune default power management settings of your harddrive.

Good luck!

---

### Post by ubuntu_demon on 2007-10-31
> **houstonbofh said:**
> I think there is a lot more panic than real problem.  I mean this is not exactly a new problem, yet I have not heard of massive Linux hard drive failures.  (I know mine haven't)  I think this is mainly panic, and slashdot has not helped this at all
Some people are reporting an increase of a couple of thousand Load_Cycles per day. For those people it is a serious problem.

---

### Post by Linicks on 2007-10-31
Dear all,

I am pretty concerned with the negative press this [supposedly Ubuntu only] saga is causing with the APM/power-save management on hard drives.

[COLOR="DarkRed"]So, please **ONLY** reply to this thread if you have had a hard drive failure that can be atrributed to this issue **with proof**.[/COLOR]

I personally think if it was as bad as people make out it is, we should be seeing HD's failing left, right and centre.

Nick

---

### Post by ubuntu_demon on 2007-10-31
> **nocturn said:**
> This is not an Ubuntu bug (though Ubuntu could fix it) unless laptop mode was enabled (it is not so by default).

Without laptop mode, the settings from your bios remain unchanged and they are probably causing the frequent unloads.
Indeed. laptop-mode is disabled by default. For most people aggressive power management settings are set by the BIOS or by the harddrive firmware.

---

### Post by ddrichardson on 2007-10-31
I know you are looking for proof, but I've been investigating this thoroughly over the last few days and I can debunk one thing as a myth - [Windows doesn't do things]("http://blog.lynxworks.eu/?p=36") any differently - it's not an Ubuntu only issue.

---

### Post by richq on 2007-10-31
My laptop has only ever been used on AC. I got it in August. Its Power_On_Hours of 358 is about right. The  Load_Cycle_Count was 20699 when I discovered the furore surrounding this bug. That's 57 cycles an hour, almost once per minute. 

Although at that rate it would last around 6 years if 600,000 is the limit, I don't want to take any chances. It took me about 5 minutes to disable, by which time the load cycle count had gone up to 20705, which is where it has remained constant since. The laptop_mode option is disabled everywhere (I haven't touched the defaults). In August I had a laptop die on me due to HD problems, on a laptop which had pretty much only ever been used with Ubuntu. I wonder if it wasn't a coincidence.

---

### Post by dimbulb1024 on 2007-10-31
> **ubuntu_demon said:**
> Let's hope there will be an official fix within a few days which is the best solution if your Load_Cycle_Count only grows moderately..
I'll keep my fingers crossed!

---

### Post by rogirwin on 2007-10-31
> These aggressive power management settings are set by your BIOS or harddrive firmware. Windows and/or Mac OS X might be overriding these settings which might make Ubuntu look bad if Ubuntu doesn’t override these settings. I agree that Ubuntu should override these settings.

Then this must be a bug in Linux rather than Ubuntu. I just went and checked my old laptop that has been running Slackware for the last few years. It has a Load_Cycle_Count of close to a Million! The count was going up by one every few seconds until I applied the fix. All linux distributions/operating systems need to apply a setting to override this.

This is not a Ubuntu problem or even unique to Ubuntu as some may think. Shouldn't the fix to this be applied at kernel level?

---

### Post by Linicks on 2007-10-31
Well, I don't really care what MS does here.  I am just trying to establish what this really means.

People are reading posts without facts.

I looked up my hard drive specs (Travelstar 5K160 Specification v1.1):

[http://www.hitachigst.com/tech/techlib.nsf/products/Travelstar_5K160](http://www.hitachigst.com/tech/techlib.nsf/products/Travelstar_5K160)


What it says is this:
> 
6.3.6       Load/unload

The **product supports a minimum of 600,000** normal load/unloads.
Load/unload is a functional mechanism of the hard disk drive. It is controlled by the drive micro code. Specifically,
unloading of the heads is invoked by the following commands:
            Hard reset
            Standby
            Standby immediate
            Sleep

So, it supports a **minimum**...

So where are people getting the idea that 600,000 is DEAD DRIVE?  I read this as it can do a lot, lot more than this - hence why the default APM that BIOS/HD firmware people do.  They (should) know what they are doing more than any of us in here/in the press.

So, lets see people that have dead drives from this post here with proof of it.

Nick

---

### Post by dashnak on 2007-10-31
I believe I have this problem as well, kinda frustrating, and scary.... hehehe

---

### Post by ddrichardson on 2007-10-31
> **Linicks said:**
> Well, I don't really care what MS does here.  I am just trying to establish what this really means.I have covered this but it does matter what MS do - for the simple reason that I've already shown that in Vista at least the same issue is present. No one is running around accusing Windows of killing drives, so the issue *has* to be bogus for most drives.

If you think about it, it bears all the hallmarks of FUD:
1. A technical looking description that looks serious but is vague in substance.
2. Directed solely at Ubuntu (which as we've shown is incorrect).
3. People we've never head of disputing data from sources we have who have reputable opinions in this area.

The funny thing is that no-one is suggesting this is the drive manufacturers fault - the one group of people who stand to profit from it.

---

### Post by arkara on 2007-10-31
how many cycles-increase is normal for an full-time working hd per day?

---

### Post by Linicks on 2007-10-31
I am confused with your blog entry:

> Well being the kind of person I am I thought I&#8217;d do a little investigation. Now after disabling the cycles from Ubuntu, I let the system run for fifteen minutes and noted that there was no increase where previously there had been.

Now I rebooted in Windows Vista Home Premium, let the system run for fifteen minutes and rebooted into Ubuntu. After taking measurements again, surprisingly there was a ten cycle increase.

So the only conclusion I can draw **here is that Windows Vista does not alter these settings either**.

You mean that it doesn't change the APM settings to stop parking the heads, not that it changes the load_cycle_count?

Nick

---

### Post by ubuntu_demon on 2007-10-31
> **rogirwin said:**
> Then this must be a bug in Linux rather than Ubuntu. I just went and checked my old laptop that has been running Slackware for the last few years. It has a Load_Cycle_Count of close to a Million! The count was going up by one every few seconds until I applied the fix. All linux distributions/operating systems need to apply a setting to override this.

This is not a Ubuntu problem or even unique to Ubuntu as some may think. Shouldn't the fix to this be applied at kernel level?
to rogirwin :

The bug is that manufacturers are setting too aggressive power management defaults either in the laptop BIOS or in the laptop harddrive firmware. (Ubuntu could also take a look at what kind of processes are causing the disk to wake up/unpark/spin up too minimize the effect of aggressive power management defaults)

You can also experience a fast increasing Load_Cycle_Count if you have enabled laptop-mode which is disabled by default.

---

### Post by Gruntler on 2007-10-31
What is really dissapointing about this bug is the rush to the conclusion that Ubuntu does not have anything to do with it but that is caused by manufacturer defaults. In my laptop both Ubuntu and Windows run with the same APM default as reported by hdparm  (128 which is Hitachi's default for my HDD) so neither OS  touches the default.

Under windows load/unload cycle count increases once every 4 or five minutes. This can be considered an agressive default by the manufacturer (and Hitachi is infamous for this) but is reasonable as far as it means that my HDD will still have an acceptable lifespan. With Ubuntu however that very same APM setting causes the HDD to go thru 3 or 4 load/unload cycles per minute (AC or battery  it doesn't change) . Ubuntu is wearing my laptop's HDD down at 12 to 20 times the rate Windows is under the same default APM setting.

It is not a question of a bad manufacturer default. It is a question of how the OS  (daemons, filesistems, acpi implementation) and the default APM level interact and in the case of Ubuntu (at least in many laptop HDD models) this interaction causes unacceptable results.

Anyone that has a dual boot installation can run a similar test to the one described above and come to his own conclusions. You can download hdparm for windows from this link if you need it:

[http://hdparm-win32.dyndns.org/hdparm/](http://hdparm-win32.dyndns.org/hdparm/)

There is also a link to smartmontools for windows in the same page.

---

### Post by ubuntu_demon on 2007-10-31
> **arkara said:**
> how many cycles-increase is normal for an full-time working hd per day?
Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

Choose yourself what to aim for and do the math :)
Aiming for less than 200.000 Load_Cycles in three years means 180 Load_Cycles per day.

---

### Post by ddrichardson on 2007-10-31
Well, the suggestion that was being raised was that Ubuntu should take the Windows approach and use so called "sane values". This appears to be wrong in that Windows is not altering these settings - as the load unload cycle count is increasing under Windows use.

---

### Post by rev_b on 2007-10-31
Sorry, but I find it hard to believe this issue is true. So, Ubuntu is to blame because it doen't touch the manufacturer custom bios settings for hard drive power management? Would OEM's ship laptops that would have a hardrive life expectancy of a few months on regular use? Where are all those dead hardrives on people using Linux/Ubuntu?

I thinks it's just FUD, and it surely won't stop me using Ubuntu on my laptop since 6.10. It's 4 year old and still not dead.

---

### Post by rogirwin on 2007-10-31
> **ubuntu_demon said:**
> The bug is that manufacturers are setting too aggressive power management defaults either in the laptop BIOS or in the laptop harddrive firmware. (Ubuntu could also take a look at what kind of processes are causing the disk to wake up/unpark/spin up too minimize the effect of aggressive power management defaults)


My point is that this is bigger than just Ubuntu as published on various websites including [Slashdot.]("http://hardware.slashdot.org/article.pl?sid=07/10/30/1742258") Others are effected. We as the "Linux Community" have none or little influence as to what manufacturers do and what they should do. Yes, It's "there fault" but pointing fingers won't fix the issus.

Surly the only way to truly fix this for everyone is a patch in the kernel.

---

### Post by ubuntu_demon on 2007-10-31
> **rev_b said:**
> Sorry, but I find it hard to believe this issue is true. So, Ubuntu is to blame because it doen't touch the manufacturer custom bios settings for hard drive power management? Would OEM's ship laptops that would have a hardrive life expectancy of a few months on regular use? Where are all those dead hardrives on people using Linux/Ubuntu?

I thinks it's just FUD, and it surely won't stop me using Ubuntu on my laptop since 6.10. It's 4 year old and still not dead.
I'm not blaming Ubuntu. Ubuntu is NOT causing aggressive power management.

Now that we know some laptop/harddrive manufacturers might be setting too aggressive defaults Ubuntu can start overriding them where necessary,

It doesn't mean this is not an issue if this doesn't affect you. There are people who are seeing Load_Cycle_Counts increasing very very fast. Some laptop BIOSes set too aggressive power management defaults. Some laptop harddrive firmwares set too aggressive power management defaults.

---

### Post by lxowle on 2007-10-31
I posted earlier in the thread about how the hdparm command does nothing to stop my load cycle count from increasing a few times a minute (I'm running on AC).

This is still the case, and I was wondering if perhaps this actually means that on some systems, the load cycle count has nothing to do with power saving?

As far as I can tell, my hard drive is behaving normally - I can't hear it powering up and down, and there is no lag in its use due to spin up time. Furthermore, according to what I've read here, it shouldn't be in aggressive power saving mode anyway as I'm on AC.

Do you think that this load cycle count might be being misreported on some systems?

---

### Post by maruchan on 2007-10-31
```
193 Load_Cycle_Count    0x0032   086   086   000 Old_age   Always   -   29224
```

Is this high? I have no idea - I bought the laptop in August.

---

### Post by robzon on 2007-10-31
@maruchan

it's not a lot, but I guess it could be a little lower. it took about 2 months to get 30k, so to get to the point of 600k it would need like.. 40 months, which is over 3 years.
someone has reported that their harddrive started to fail after 200k, so that would give you only 1 year.
From what I see these numbers aren't really that meaningful and may be misleading.

---

### Post by jody.palmer on 2007-10-31
One more question... isn't there a tradeoff between drive temperature and Load_Cycle_Count?  If I set hdparm -B 254, my smartctl reported temp climbs alarmingly quickly.  
Can I safely play with hdparm -B values to find the right balance through observation?

---

### Post by arkara on 2007-10-31
> **ubuntu_demon said:**
> Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

Choose yourself what to aim for and do the math :)
Aiming for less than 200.000 Load_Cycles in three years means 180 Load_Cycles per day.

on offense my friend. but your hard drive might be sucky..
could you tell me the brand of your hard drive?
i have a toshiba laptop with a toshiba harddrive

---

### Post by rogirwin on 2007-10-31
> **rev_b said:**
> Sorry, but I find it hard to believe this issue is true. So, Ubuntu is to blame because it doen't touch the manufacturer custom bios settings for hard drive power management? Would OEM's ship laptops that would have a hardrive life expectancy of a few months on regular use? Where are all those dead hardrives on people using Linux/Ubuntu?

I thinks it's just FUD, and it surely won't stop me using Ubuntu on my laptop since 6.10. It's 4 year old and still not dead.

You may well be right. I have a laptop with a Load_cycle_Count of 975,500 and it came back 100% A OK. My guess is that this bug doesn't actively kill drives but may contribute to the longterm failure of a drive. eg Smoking won't kill you in the short term but it increases the chance of a premature death.

If I left my Load_Cycle_Count ticking over to a couple of million over the next year. Would it die? Who knows.. I think it possibly wouldn't. By Patching the bug I'm sure it will help to increase the life of it if only slightly.

I find it hard to believe that it could kill a drive in a couple of weeks as some people have suggested. Premature failure happens.

---

### Post by _oOMOo_ on 2007-10-31
Whatever the rights and wrongs of the slashdot article, I have to say I'm seriously pleased I got to hear about this as my laptop is only 3 months old and I'm already seeing nearly 140,000 cycles. And all this on AC! Since setting hdparm -B at 255 it hasn't risen at all.


```
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2897
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       831
193 Load_Cycle_Count        0x0032   031   031   000    Old_age   Always       -       139546

```

---

### Post by arkara on 2007-10-31
this is weird..
average uptime per day?? do the math and tell us if this reliable..
it is 1 cycle per 5 seconds.

---

### Post by dirkmegabyte on 2007-10-31
**This post could be related to an Ubuntu bug filed at**: bug59695 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Is 'harddrive killer' really a problem? I have my doubts after reading some documentation from Hitachi. Check it out for yourselves:

http://www.hitachigst.com/tech/techlib.nsf/techdocs/9076679E3EE4003E86256FAB005825FB/$file/LoadUnload_white_paper_FINAL.pdf

Dirk

---

### Post by _oOMOo_ on 2007-10-31
> **arkara said:**
> this is weird..
average uptime per day?? do the math and tell us if this reliable..
it is 1 cycle per 5 seconds.

I never turn it off... but it was a refurbed laptop. Even so the usage hours for the drive seem a little high admittedly.

Not sure where you get 1 cycle every 5 secs:

2897 hours = 173,820 minutes

Cycles recorded is 139546; that's less than 1 a minute.

---

### Post by arkara on 2007-10-31
this is weird...:-k

---

### Post by techstop on 2007-10-31
I voted No. This absolutely should be a critical fix. I have tried changing settings in my bios with no effect, when it comes down to it, this is an Ubuntu issue. I have stopped using Gutsy until it is fixed. I can't afford not to. My cycle count is 80000 on a 6 month old laptop which has only been running Linux for about the last 6 weeks. It also doesn't matter if I am running on battery power or not, that cycle count just keeps going up.

---

### Post by houstonbofh on 2007-10-31
> **ubuntu_demon said:**
> Some people are reporting an increase of a couple of thousand Load_Cycles per day. For those people it is a serious problem.
Assuming SMART is reporting correctly.  This is a big assumption as I have found the numbers to be demonstrably wrong on many occasions. (In Windows as well)  I am not saying that this is not a problem...  I am saying that I am skeptical when the only evidence is the SMART reporting tools and a very small handful of failed hard drives.  But I am following the threads as well.  We just need more facts.

---

### Post by nrfool on 2007-10-31
When reading digg today, I came across this:
[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)
checked on my laptop, got a load cycle count of 1 every min. With the current count and current rate of increasing count. My hard drive will reach 600,000 limit in just one year.
Follow up reading show that this bug has been discovered and reported since Feisty, but it persists until this day. For a hardware damaging problem like, it is extremely disappointing.
Even if this bug can not be fixed with an update, shouldn't it at least be a sticky post n the forum and warn ignorant new users like me?

---

### Post by GeekMom on 2007-10-31
Yes,
If only to help those of us who are too new to Ubuntu to know which "ugly fix" to apply or how.  I've personally gotten myself into a "fix" by attempting to follow advice on another forum on how to generate the load cycle count report.  Now I need to find assistance [under another thread] to undo those changes.

---

### Post by techstop on 2007-11-01
> **GeekMom said:**
> Yes,
If only to help those of us who are too new to Ubuntu to know which "ugly fix" to apply or how.  I've personally gotten myself into a "fix" by attempting to follow advice on another forum on how to generate the load cycle count report.  Now I need to find assistance [under another thread] to undo those changes.

Shouldn't you have voted "No" then? It is currently tagged as wishlist (not critical). The question is "Do you think the bug should be wishlist?". If you don't think it should be wishlist, then you must think it should be critical. If you voted "Yes", then you effectively think the current situation is acceptable.

---

### Post by eode on 2007-11-01
I lost two drives to this (during the loss of the second was when I realized it was a bug of some sort).  It seems to be a combined problem of:

1) overly aggressive apm for hw defaults (NOT Ubuntu)
2) Ubuntu touches the HD and un-parks the heads just after they park (Ubuntu)

I am *not* saying that this is Ubuntu specific, in fact, it is something that happens at least on Gentoo as well.

Also, one must have particular hardware that is/gets overly aggressive with its APM.

Mainly, I wanted to note:  Different HW Manufacturers store SMART values differently.  Check your Load_Cycle_Count before and after a park -- if the difference is more than 1, it's a pretty safe bet that you can divide the number by that amount.

---

### Post by GeekMom on 2007-11-01
I read the many posts today - not just to jump on the "fear bandwagon" but because my HD just seems to be constantly running and I thought this may be the reason.  So this is what I tried:

***copied from the  ubuntudemon.wordpress.com  forum*****
To discover whether you suffer from this problem :

First install smartmontools to be able to query your harddrive :
$ sudo aptitude install smartmontools

To find your Load_Cycle_Count do this (the last number is the number we are interested in) :
$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count

If this number is growing rapidly (more than 90 per day) then you might be suffering from this problem.
**************
the install of smartmontools seemed to go fine - except that after the install it THEN gives you the message that your mail program will not function until you reconfigure it *(&^??

So I just continue forward with the next command line to do the load cycle count report and all I get is an invalid command message to smartctl.  Plus now I get an error message when trying to send/receive mail through evolution.

Lastly - I try the second command line; $ grep Load_Cycle_Count - My harddrive stops the wild cycling immediately, and has not been making much noise since.  
Now I'm just confident enough to be dangerous..so I'm suspecting that I'll regret something I did eventually.  After all this command was supposed to give you a report - not fix the problem.

I just went on to the "newby how to" section of this forum to see if I could figure out how to REMOVE smartmontools.  It seemed to work, it uninstalled in the terminal - but I still get the error message in evolution.

---

### Post by hockeyfighter09 on 2007-11-01
how do i read the info on my hard drive in the terminal? is the number under Load_Cycle_Count the current number of spins my hard drive has had?

---

### Post by nrfool on 2007-11-01
To view that, you just need to install "smartmontools" using synaptic. Then type the command
"$sudo smartctl -a /dev/sda | more", use "z" key on the keyboard to page down the list and look for an entry Load_cycle_count. Check it again a little later. Based on that, you can calculate the frequency of the load_cycle_count. If you get something as frequent as 1 once a minute, you might need to look for work arounds

[http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/](http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/)

---

### Post by hockeyfighter09 on 2007-11-01
all right mine is currently over 300000 on a one year old laptop....:(

---

### Post by Jaco Du Toit on 2007-11-01
For those looking for the work around, I tried the following (from a post on Slashdot) and it stopped the once a minute load_cycle increase:

Create a text file called: 99-hdd-spin-fix.sh
In this text file add the commands:

> 
#!/bin/sh
hdparm -B 255 /dev/sda


make this file executable (by chmod +x 99-hdd-spin-fix.sh)

and then copying it into the following three directories:

/etc/acpi/start.d
/etc/acpi/resume.d
/etc/acpi/suspend.d

Then reboot.

EDIT: Incidentally, before doing this my cycle count was 27175 on a 2month old laptop and steadily increasing at about once every minute. Now it is steady, and only increases when I reboot the machine or resume from suspend mode - as it should.

---

### Post by hockeyfighter09 on 2007-11-01
what should be the average cycles per on a harddrive? just wondering so i can increase my knowledge to know more of this problem.

---

### Post by weblordpepe on 2007-11-01
uh oh :/

Having multiple solutions and multiple threads with different howtos is confusing me.

---

### Post by neilius on 2007-11-01
I can confirm that this isn't Ubuntu's fault, but the default setting of the HDD's firmware itself. I downloaded the Drive Feature Tool from Hitachi's website and used it to turn off APM and haven't had this problem since. I also disabled Acoustic Management whilst I was there, so now the drive is slightly noisier but performs better... both of these features were enabled by the manufacturer (Dell) by default. A few minutes of battery life for potential extra years of HDD life... a fair trade I think!

For those of you who don't own Hitach/IBM drives, there is the Ultimate Boot CD - [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) - that contains other manufacturer's utilities that do the same thing for their drives. You shouldn't have to change anything in the OS to fix this although you might need to if there is no utility for your particular HDD. I know some of those manufacturers have released firmware updates that fix this on their drives.

Regards,

Neil.

---

### Post by _oOMOo_ on 2007-11-01
> **houstonbofh said:**
> Assuming SMART is reporting correctly.  This is a big assumption as I have found the numbers to be demonstrably wrong on many occasions. (In Windows as well)  I am not saying that this is not a problem...  I am saying that I am skeptical when the only evidence is the SMART reporting tools and a very small handful of failed hard drives.  But I am following the threads as well.  We just need more facts.

Well in my case I can hear the hard drive. I'm a little surprised there hasn't been a fix committed, I just booted into Windows for a while and I can confirm that this is only happening in Ubuntu. If this is indeed something that has been set in the BIOS (why would a manufacturer do that??? - although I have to say based on other issues that my BIOS was probably knocked up in the pub on a Friday afternoon) then MS clearly knew about it.

As regards power management I do find it strange that some users report that this only happens after unplugging the battery; for me it happens non-stop. On the desktop running Gutsy there is no issue, which does rather point to settings above and beyond Ubuntu's.

---

### Post by neilius on 2007-11-01
Please see my post from another thread about this: [http://ubuntuforums.org/showpost.php?p=3682524&postcount=22](http://ubuntuforums.org/showpost.php?p=3682524&postcount=22)

Warm regards,

Neil.

---

### Post by tkb on 2007-11-01
I've been using Ubuntu 7.04 for about 2 months on a acer 3270.  Saw yesterday that the Load Count was at ~50,000! Love ubuntu but this problem scares me, since this is my work laptop  and I can't have it crash  in less than 2 years.  Does anyone know if this an Ubuntu problem or are other Linux OSs effected as well?

---

### Post by neilius on 2007-11-01
Hi all, this is pretty much OS independant, please see my post regarding this issue here: [http://ubuntuforums.org/showpost.php?p=3682524&postcount=22](http://ubuntuforums.org/showpost.php?p=3682524&postcount=22)

Warm regards,

Neil.

---

### Post by vikrant82 on 2007-11-01
More on the same bug and another one [here.]("http://kakku.wordpress.com/2007/10/29/s-m-a-r-t-parameters-for-hard-disk-possible-ubuntu-bugs-with-handling-laptop-hard-disks-laptop-hardisks-being-killed/")

---

### Post by Jaco Du Toit on 2007-11-01
> **hockeyfighter09 said:**
> what should be the average cycles per on a harddrive? just wondering so i can increase my knowledge to know more of this problem.

According to manufacturers most hard drives can take 600000 cycles before giving problems. Now let's look at the output of:

```
sudo smartctl -a /dev/sda
```

It results in something similar to this:

```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   100   100   000    Old_age   Offline      -       1353
  3 Spin_Up_Time            0x0007   178   178   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       165
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       477
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       162
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       30
193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       27179
194 Temperature_Celsius     0x0002   137   137   000    Old_age   Always       -       40 (Lifetime Min/Max 17/52)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       27179

```

Now a couple of columns are of interest. The first one that everybody checks is the raw_value column, but that just gives you an indication as to the actual current value. To really see when a drive will give problems examine the four columns called VALUE WORST THRESH and TYPE. Basically the way it works is that VALUE gives you the current value, WORST gives you the worst ever value and THRESH tells you when it becomes a problem.  If VALUE is less than or equal to THRESH then the condition in TYPE will occur. For instance, on the dump above if the VALUE in Load_Cycle_Count (Currently 098) becomes 000 (in THRESH) then my drive would be considered in Old_age. Likewise if Raw_Read_Error_Rate VALUE (Currently 100) becomes less than 062 (THRESH) then my drive would be in Pre_fail . 

Hope this helps.

---

### Post by NotTheMessiah on 2007-11-01
Well...not to be controversial or anything but when i boot into my XP partition the hard drive light goes nuts(ok so it's normal on boot up) but then the desktop is loaded and then you wait another 3-4 minutes of continual HArdDrive burn(and CPU burn - svchost.exe) before it stabilizes with the occasional light up at Idle for no good reason. And all this is happening when i wake my laptop from Hibernate!!! This can't be ideal

But when i boot up my Feisty things are noticeably  more peaceful, and orderly.

So i think this might be blown out of proportion a little bit.

---

### Post by neilius on 2007-11-01
This is not an Ubuntu issue, it's an issue with the default firmware settings on the HDD itself and/or BIOS settings that override them. Please see my post: [http://ubuntuforums.org/showpost.php?p=3682524&postcount=22](http://ubuntuforums.org/showpost.php?p=3682524&postcount=22)

Ubuntu doesn't touch the drive settings at all, unless Laptop Mode is enabled and it isn't by default, even for laptops.

Warm regards,

Neil.

---

### Post by Raffo on 2007-11-01
I have experienced the same problem on a desktop computer with a 80 GB IDE Maxtor. I have two linux distro installed on this computer and only ubuntu has this problem. It seems we've a problem to fix...

---

### Post by ubuntu_demon on 2007-11-01
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Some background of the problem :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)[/B]

I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by ubuntu_demon on 2007-11-01
[B]I&#8217;m a big fan of Ubuntu. I don&#8217;t want to see Ubuntu hurt because it&#8217;s not Ubuntu who is setting these aggressive power management defaults.

Now to determine whether you actually suffer from this problem and the ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
[/B]
I moved this information to a single post instead of multiple threads with the same post because it's easier to maintain that way.

---

### Post by Jaco Du Toit on 2007-11-01
Ah but you see it is not just hard drive activity that "kills the hdd". What happens in this case is the hard drive literally goes to sleep and then gets woken up less than a minute later. This stop/start motion shortens the life of the HDD.

You are correct however that this is blown out of proportion in the sense that it happens with ALL operating systems as it is something on the HDD itself that causes it. It just so happens that Microsoft Windows and OSX overwrites the manufacturer defaults and implements their own sleep/suspend cycles for the hard drive. Ubuntu and other distro's listen to the hardware manufacturer. 

Bottom line is, if you run on a battery this aggressive power management is bad for your HDD.

---

### Post by techstop on 2007-11-01
> **neilius said:**
> This is not an Ubuntu issue, it's an issue with the default firmware settings on the HDD itself and/or BIOS settings that override them. Please see my post: [http://ubuntuforums.org/showpost.php?p=3682524&postcount=22](http://ubuntuforums.org/showpost.php?p=3682524&postcount=22)

Ubuntu doesn't touch the drive settings at all, unless Laptop Mode is enabled and it isn't by default, even for laptops.

Warm regards,

Neil.

Thanks for the tip about the Hitachi drive management tool. I turned off acoustic management and set APM to 254 (performance). I have not had a load cycle increment in the last 15 mins. Cheers....

On the other hand, I still think it's an issue that Ubuntu (Linux in general?) needs to address. If they don't, then Linux will kill HDDs by default, which presumably is not happening with other operating systems (I'll have to look at my SMART values next time I'm in Vista). When the default is to damage hardware, something needs to be done.

If the default is to have HDD firmware that allows such rapid cycling of load / unload, then surely Ubuntu should be proactive in eliminating the potential for damage if that is what happens to users of that OS?

EDIT: My laptop mode was off, but I was still getting 3 cycles a minute prior to changing the settings with the Hitachi tool.

---

### Post by NotTheMessiah on 2007-11-01
Ok...so what about people(like me) that have HDrives that don't have the SMART capability? THey can't use
 the monitor tools...can't check the cycle(spin) whatever.

---

### Post by arkara on 2007-11-01
i will make a poll to see if the smart data on the hard drives is reliable.

---

### Post by arkara on 2007-11-01
there has been a discussion on this thread.
this poll is refered in order to see if the smard hard drive data is reliable.

the original thread is here

[http://ubuntuforums.org/showthread.php?t=596602]("http://ubuntuforums.org/showthread.php?t=596602")

---

### Post by arkara on 2007-11-01
we can continue the discussion here
and vote about the S.M.A.R.T data here.

[http://ubuntuforums.org/showthread.php?t=599280]("http://ubuntuforums.org/showthread.php?t=599280")

---

### Post by arkara on 2007-11-01
there is an active discussion here my friend..

[http://ubuntuforums.org/showthread.php?t=596602]("http://ubuntuforums.org/showthread.php?t=596602")

and a poll about this here

[http://ubuntuforums.org/showthread.php?t=599280]("http://ubuntuforums.org/showthread.php?t=599280")

---

### Post by NotTheMessiah on 2007-11-01
Thanks for that mate... it gave me a message: Advanced Power Management disabled  so i guess it worked.

So this is Laptop specific (hardware problem) but people blame this squarely on Ubuntu whether the developers are right or not.

Whatever....i am still convinced that XP is brutal on CPU/HD 'management' if you can call it that. I don't speak out of hatred for all things Microsoft but from personal experience with the XP os.

---

### Post by Linicks on 2007-11-01
Guys, see my post here:

[http://ubuntuforums.org/showthread.php?t=598731](http://ubuntuforums.org/showthread.php?t=598731)

So far, zero, zilch, nobody has yet had a hard drive failure.

So until such this is no big deal.

Nick

---

### Post by Nessa on 2007-11-01
Does this happen to desktops?

---

### Post by NotTheMessiah on 2007-11-01
No only to laptops due of the aggressive power management (for saving battery power)

---

### Post by ubuntu_demon on 2007-11-01
> **Nessa said:**
> Does this happen to desktops?
to Nessa :

It can't hurt to check your desktop but as far as I can tell this affects laptop BIOSes and laptop harddrive firmwares who might be setting aggressive power management settings. External drives sometimes contain 2.5" laptop harddrives so they too might have too aggressive powermanagement.

It's not that every laptop harddrive firmware has too aggressive power management settings. It's not that every laptop BIOS has too aggressive power managmenet settings.

If your BIOS or harddrive set these aggressive power management settings it doesn't matter whether you are on battery or not.

If you have laptop-mode enabled which is **disabled by default** Ubuntu will set aggressive power management settings while on battery (which is good for battery life).

---

### Post by ubuntu_demon on 2007-11-01
> **arkara said:**
> on offense my friend. but your hard drive might be sucky..
could you tell me the brand of your hard drive?
i have a toshiba laptop with a toshiba harddrive

My harddrive just came with the laptop. For me the SAMSUNG HM080JI started dying within a year (first problems after 200.000 Load_Cycles after 10 months) maybe it was just a bad specimen or maybe the SAMSUNG HM080JI just isn't not very good in general. You can't say anything about one negative experience. But other people could have "sucky" hardddrives too.

Device Model: SAMSUNG HM080JI
Serial Number: S082J10YA48024
Firmware Version: YC100-04

Now I am the proud owner of a Western Digital WD2500BEVS.

---

### Post by ubuntu_demon on 2007-11-01
> **houstonbofh said:**
> Assuming SMART is reporting correctly.  This is a big assumption as I have found the numbers to be demonstrably wrong on many occasions. (In Windows as well)  I am not saying that this is not a problem...  I am saying that I am skeptical when the only evidence is the SMART reporting tools and a very small handful of failed hard drives.  But I am following the threads as well.  We just need more facts.
More information always helps. But since this is a potential critical issue we shouldn't dismiss it too soon.

I'm seeing all kind of users with harddrives with a high Load_Cycle_Count and a very low "worst" value close to the "threshold" meaning that their drives might die soon.

For example :
[http://ubuntuforums.org/showpost.php?p=3677732&postcount=19](http://ubuntuforums.org/showpost.php?p=3677732&postcount=19)

[quote=rybu]
193 Load_Cycle_Count 0x0032 001 001 000 Old_age Always - 713621

I have no idea what Load_Cycle_Count is measuring. On my laptop which I bought in August it's at 713621 and going up by about 24 units every 30 seconds.

I'm not hearing any clicks, and my hard drive hasn't failed.
[/quote]

Another example :
[http://ubuntudemon.wordpress.com/2007/10/28/laptop-hardrive-killer-bug-how-to-discover-whether-you-are-affected/#comment-31508](http://ubuntudemon.wordpress.com/2007/10/28/laptop-hardrive-killer-bug-how-to-discover-whether-you-are-affected/#comment-31508)

[quote=Sander]
I have a two-year old powerbook G4, with a Seagate Momentus 5400.2 series 100GB. They also report a minimal lifetime of 600,000 cycles ([http://www.seagate.com/docs/pdf/datasheet/disc/ds_momentus5400.pdf](http://www.seagate.com/docs/pdf/datasheet/disc/ds_momentus5400.pdf))

Mine is however already at 1,900,000! (more than three times as much), and still increasing rapidly. I use Ubuntu Gutsy at the moment.

I ran the following script:
while (true); do smartctl -a /dev/hda | grep 193 >> hw.txt; sleep 60; done

And the output was:
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897663
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897663
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897663
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897664
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897664
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897664
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897664
7 Seek_Error_Rate 0×000f 057 057 030 Pre-fail Always - 558423241934
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897670
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897671
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897674
193 Load_Cycle_Count 0×0032 001 001 000 Old_age Always - 1897677

So, once an error occured, and in 12 minutes it increased by 16! This does not look that good, doesn&#8217;t it?

Sander
[/quote]

---

### Post by ubuntu_demon on 2007-11-01
> **arkara said:**
> i will make a poll to see if the smart data on the hard drives is reliable.

The smartctl values aren&#8217;t always easy to interpret. If the Load_Cycle_Counter value behaves as a counter and is below impossible to reach values it&#8217;s probably the right number.

You can also look at &#8220;WORST&#8221; and &#8220;TRESHOLD&#8221; (|more instead of |grep to easily see which value is &#8220;WORST&#8221; and which value is &#8220;TRESHOLD&#8221;) :
$ sudo smartctl -a /dev/sda | more

If WORST is lowering (too fast) than you might be suffering from this problem. You can roughly calculate how long it will take for WORST to reach TRESHOLD if you keep watching those values daily/weekly. The closer WORST (starts at 100 or 200 from what I have seen) is to THRESHOLD the likelier it is for your drive to die from a high Load_Cycle_Count.

From [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/40](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/40) :
[quote=Brian Visel]

Something to bear in mind as well:

smartmon does not always report SMART values as you might think. Different values are stored in different ways by different manufacturers.

Namely, if you do the smartctl check, wait for the click, and do it again immediately after, you may find that the amount has increased by more than one. In this case, it&#8217;s a pretty safe bet that the number you&#8217;re seeing isn&#8217;t accurate.

Also, it&#8217;s a pretty safe bet (though not guaranteed) that you can get the real value by dividing by the amount it increments by. So, if the value you see first is 477,296, and then it clicks once, and the value is 477,312 (difference of 16), it&#8217;s a pretty safe bet that the number you&#8217;re really dealing with is more along the lines of 29,831 to 29,832, in which case you have no worries.

[/quote]

If you think you might be suffering from this problem you might want to apply the ugly fix :
[http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/#comment-31234](http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/#comment-31234)

If you think your harddrive might start dying soon you should make backups of all your data and run the diagnostic tool of your harddrive manufacturer.

---

### Post by ubuntu_demon on 2007-11-01
[quote=neilius]
Hi all, this is pretty much OS independant, please see my post regarding this issue here: [http://ubuntuforums.org/showpost.php...4&postcount=22](http://ubuntuforums.org/showpost.php...4&postcount=22)

Warm regards,

Neil.
[/quote]

The following things might instead cause aggressive power management settings :

    * your (laptop) harddrive firmware might have aggressive power management defaults (operating system independent)
    * your (laptop) BIOS might set your harddrive to use aggressive power management (operating system independent)
    * you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

These aggressive power management settings are set by your BIOS or harddrive firmware. Windows and/or Mac OS X might be overriding these settings which might make Ubuntu look bad if Ubuntu doesn&#8217;t override these settings.

See : [http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

---

### Post by ubuntu_demon on 2007-11-01
> **GeekMom said:**
> I read the many posts today - not just to jump on the "fear bandwagon" but because my HD just seems to be constantly running and I thought this may be the reason.  So this is what I tried:

***copied from the  ubuntudemon.wordpress.com  forum*****
To discover whether you suffer from this problem :

First install smartmontools to be able to query your harddrive :
$ sudo aptitude install smartmontools

To find your Load_Cycle_Count do this (the last number is the number we are interested in) :
$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count

If this number is growing rapidly (more than 90 per day) then you might be suffering from this problem.
**************


Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

If you aim for 90 per day that means that your Load_Cycle_Count will be less than 100.000 in three years. If you aim for 180 per day that means that your Load_Cycle_Count will be less than 200.000 in three years.

So you should roughly calculate what your Load_Cycle_Count will be in three years of harddrive use to determine whether you need to apply the ugly fix.

The smartctl values aren&#8217;t always easy to interpret. If the Load_Cycle_Counter value behaves as a counter and is below impossible to reach values it&#8217;s probably the right number.

You can also look at &#8220;WORST&#8221; and &#8220;THRESHOLD&#8221; (|more instead of |grep to easily see which value is &#8220;WORST&#8221; and which value is &#8220;THRESHOLD&#8221;) :
$ sudo smartctl -a /dev/sda | more

If WORST is lowering (too fast) than you might be suffering from this problem. You can roughly calculate how long it will take for WORST to reach THRESHOLD if you keep watching those values daily/weekly. The closer WORST (starts at 100 or 200 from what I have seen) is to THRESHOLD the likelier it is for your drive to die from a high Load_Cycle_Count.

From [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/40](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/40) :
> **Brian Visel]

Something to bear in mind as well:

smartmon does not always report SMART values as you might think. Different values are stored in different ways by different manufacturers.

Namely, if you do the smartctl check, wait for the click, and do it again immediately after, you may find that the amount has increased by more than one. In this case, it&#8217 said:**
> 

If you think you might be suffering from this problem you might want to apply the ugly fix.

If you think your harddrive might start dying soon you should make backups of all your data and run the diagnostic tool of your harddrive manufacturer.

For more information see : 
[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management)
[http://www.advogato.org/person/mjg59/diary/82.html](http://www.advogato.org/person/mjg59/diary/82.html)
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)


[QUOTE=GeekMom;3681889]
the install of smartmontools seemed to go fine - except that after the install it THEN gives you the message that your mail program will not function until you reconfigure it *(&^??

So I just continue forward with the next command line to do the load cycle count report and all I get is an invalid command message to smartctl.  Plus now I get an error message when trying to send/receive mail through evolution.

Lastly - I try the second command line; $ grep Load_Cycle_Count - My harddrive stops the wild cycling immediately, and has not been making much noise since.  
Now I'm just confident enough to be dangerous..so I'm suspecting that I'll regret something I did eventually.  After all this command was supposed to give you a report - not fix the problem.

I just went on to the "newby how to" section of this forum to see if I could figure out how to REMOVE smartmontools.  It seemed to work, it uninstalled in the terminal - but I still get the error message in evolution.

installing smartmontools can't hurt you. It is only used to get S.M.A.R.T. data from your harddrive or doing self-tests on your harddrive.

To see whether S.M.A.R.T. is enabled :
$sudo smartctl -I /dev/sda
To enable S.M.A.R.T. if it is disabled :
$sudo smartctl -s on /dev/sda
To get a rough estimate of harddisk health :
$sudo smartctl -H /dev/sda
To view all information :
$sudo smartctl -a /dev/sda | more
To view Load_Cycle_Count related information :
$sudo smartctl -a /dev/sda | grep Load_Cycle_Count

Maybe you shut down your computer while upgrading/installing or maybe you have enabled unofficial repositories (just guessing here). People shouldn't get problems with their email by installing smartmontools.

Try to fix it by :
$sudo dpkg --configure -a

If that doesn't work try this :
$sudo dpkg-reconfigure evolution -phigh

---

### Post by arkara on 2007-11-01
this is a tricky one.. 
we only time will tell.
i don't worry about my hd.. i have a 4 year guarantee witth my laptop. i worry about my files.

---

### Post by ubuntu_demon on 2007-11-01
The smartctl values aren&#8217;t always easy to interpret. If the Load_Cycle_Counter value behaves as a counter and is below impossible to reach values it&#8217;s probably the right number.

You can also look at &#8220;WORST&#8221; and &#8220;THRESHOLD&#8221; (|more instead of |grep to easily see which value is &#8220;WORST&#8221; and which value is &#8220;THRESHOLD&#8221;) :
$ sudo smartctl -a /dev/sda | more

If WORST is lowering (too fast) than you might be suffering from this problem. You can roughly calculate how long it will take for WORST to reach THRESHOLD if you keep watching those values daily/weekly. The closer WORST (starts at 100 or 200 from what I have seen) is to THRESHOLD the likelier it is for your drive to die from a high Load_Cycle_Count.

From [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/40](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/40) :
[quote=Brian Visel]

Something to bear in mind as well:

smartmon does not always report SMART values as you might think. Different values are stored in different ways by different manufacturers.

Namely, if you do the smartctl check, wait for the click, and do it again immediately after, you may find that the amount has increased by more than one. In this case, it&#8217;s a pretty safe bet that the number you&#8217;re seeing isn&#8217;t accurate.

Also, it&#8217;s a pretty safe bet (though not guaranteed) that you can get the real value by dividing by the amount it increments by. So, if the value you see first is 477,296, and then it clicks once, and the value is 477,312 (difference of 16), it&#8217;s a pretty safe bet that the number you&#8217;re really dealing with is more along the lines of 29,831 to 29,832, in which case you have no worries.

[/quote]

If you think you might be suffering from this problem you might want to apply the ugly fix.

If you think your harddrive might start dying soon you should make backups of all your data and run the diagnostic tool of your harddrive manufacturer.

---

### Post by ubuntu_demon on 2007-11-01
I merged all active threads relevant to the laptop harddrive Load_Cycle_Count issue. Upon merging these threads sadly the poll got lost.

The poll had the title : "Do you think bug about Ubuntu killing laptop hard drives should be 'wishlist"
Do you guys want the poll back in ? If so I'll ask an admin.

On purpose I haven't merged in the following threads :
* threads which had no replies in over a week. 
* the system76 thread about this issue : [http://ubuntuforums.org/showthread.php?t=594796](http://ubuntuforums.org/showthread.php?t=594796)
* this thread in absolute beginners : [http://ubuntuforums.org/showthread.php?t=598676](http://ubuntuforums.org/showthread.php?t=598676)

---

### Post by drf_av on 2007-11-01
So, my HP dv6560 reports almost 2000 cycles in about 4 months of life. I Don't think that's so much.

---

### Post by ubuntu_demon on 2007-11-01
> **drf_av said:**
> So, my HP dv6560 reports almost 2000 cycles in about 4 months of life. I Don't think that's so much.
You are probably fine :)

But please take a look at the "threshold" and "worst" values to be sure.

---

### Post by ubuntu_demon on 2007-11-01
To track Load_Cycle_Count trends you could put this into root&#8217;s crontab ($sudo crontab -uroot -e):

> 
echo `sudo smartctl -a /dev/sda | grep Load_Cycle_Count` &#8221; | &#8221; `date` >> /home/username/load_count


replace username with your username

I didn&#8217;t came up with this. This contribution is combined from :
[http://ubuntudemon.wordpress.com/2007/10/29/laptop-hardrive-killer-bug-should-get-critical-status/#comment-31494](http://ubuntudemon.wordpress.com/2007/10/29/laptop-hardrive-killer-bug-should-get-critical-status/#comment-31494)
[http://hardware.slashdot.org/comments.pl?sid=344745&cid=21174571](http://hardware.slashdot.org/comments.pl?sid=344745&cid=21174571)

---

### Post by vilator on 2007-11-01
When I type in 
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
nothing happens, it just goes to the next prompt. I installed the smartmontools, so whats the problem.

---

### Post by ubuntu_demon on 2007-11-01
> **vilator said:**
> When I type in 
sudo smartctl -a /dev/sda | grep Load_Cycle_Count
nothing happens, it just goes to the next prompt. I installed the smartmontools, so whats the problem.
Your harddrive might be called different. Use one of these commands to find the name of your harddisk :
$ df -h
$ sudo fdisk -l

Replace /dev/sda with the name of your harddisk.

To see whether S.M.A.R.T. is enabled :
$sudo smartctl -I /dev/sda
To enable S.M.A.R.T. if it is disabled :
$sudo smartctl -s on /dev/sda
To get a rough estimate of harddisk health :
$sudo smartctl -H /dev/sda
To view all information :
$sudo smartctl -a /dev/sda | more
To view Load_Cycle_Count related information :
$sudo smartctl -a /dev/sda | grep Load_Cycle_Count

---

### Post by vilator on 2007-11-01
wow thanks for the quiclk reply. yeah my smart was disabled.
193 Load_Cycle_Count        0x0032   094   094   000    Old_age   Always       -       62224

Its only 62000 and I've been using this hdd for 11months with xp, Isnt that kinda low. Anyways its going up by like 4 or 5 every couple minutes, so I should apply the fix then right?

---

### Post by ubuntu_demon on 2007-11-01
> **vilator said:**
> wow thanks for the quiclk reply. yeah my smart was disabled.
193 Load_Cycle_Count        0x0032   094   094   000    Old_age   Always       -       62224

Its only 62000 and I've been using this hdd for 11months with xp, Isnt that kinda low. Anyways its going up by like 4 or 5 every couple minutes, so I should apply the fix then right?
You should probably apply the fix if your Load_Cycle_Count is going up every 5 minutes even when you are on AC.

Is it going up by 1 or more than 1 roughly every 5 minutes ? What is the age of your disk ? How long have you been using Ubuntu after 11 months of XP ?

You might want to track Load_Cycle_Count trends :
[http://ubuntuforums.org/showpost.php?p=3683526&postcount=270](http://ubuntuforums.org/showpost.php?p=3683526&postcount=270)

---

### Post by ubuntu_demon on 2007-11-01
> **formulajay said:**
> I was wondering how exactly people have come up with a typical hard drive life span is about equal to 600,000 load cycles? I just recently acquired a new(read:hand-me-down) laptop, and I just installed Ubuntu on it, and today I was just reading over at slashdot and saw this 'Ubuntu Killer' post and read a little about it. I then proceeded to check the load cycle count on this newly acquired laptop only to find a cycle count more than double what is considered the average life span of a hard drive. My load cycle count is at 

225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       1387419

Almost 1.4 million cycles. I also do not seem to be experiencing any odd symptoms or misbehavior from the computer. I am unsure if this is anything to be concerned about.
Your WORST(1) is almost at your THRESHOLD (0) you should make backups of
all your data and run the diagnostic tool of your harddrive
manufacturer.

How old is your disk ?
Please let us know the outcome of the diagnostic tool.

---

### Post by vilator on 2007-11-01
> **ubuntu_demon said:**
> You should probably apply the fix if your Load_Cycle_Count is going up every 5 minutes even when you are on AC.

Is it going up by 1 or more than 1 roughly every 5 minutes ? What is the age of your disk ? How long have you been using Ubuntu after 11 months of XP ?

You might want to track Load_Cycle_Count trends :
[http://ubuntuforums.org/showpost.php?p=3683526&postcount=270](http://ubuntuforums.org/showpost.php?p=3683526&postcount=270)

It was going up by 4 or 5 every minute, but I applied the fix and it seems to have stopped now. I just started using linux this week. I think my hdd is about 3 years old, buts its only been really used for about 1, since it was a model that I bought used in january.

---

### Post by ubuntu_demon on 2007-11-01
> **formulajay said:**
> I was wondering how exactly people have come up with a typical hard drive life span is about equal to 600,000 load cycles? I just recently acquired a new(read:hand-me-down) laptop, and I just installed Ubuntu on it, and today I was just reading over at slashdot and saw this 'Ubuntu Killer' post and read a little about it. I then proceeded to check the load cycle count on this newly acquired laptop only to find a cycle count more than double what is considered the average life span of a hard drive. My load cycle count is at 

225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       1387419

Almost 1.4 million cycles. I also do not seem to be experiencing any odd symptoms or misbehavior from the computer. I am unsure if this is anything to be concerned about.

Regarding the Load_Cycle_Count information you have posted :

Your WORST(1) is almost at your THRESHOLD (0) you should consider making backups of all your data and running the diagnostic tool of your harddrive manufacturer to check your harddisk for problems. 

The good news is that the information you can provide might contribute to the solving of this bug. You might want to contribute some information to this bug :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216)

You should consider including this information :
 * the outcome of the diagnostic tool of your harddrive manufacturer
 * whether you have enabled laptop-mode
 * the output of $sudo smartctl -a /dev/sda
 * the age of the disk
 * an estimate of the total hours the disk has been running since you
started using it (to compare to Power_on_Hours because that value might
be off)
 * an estimate of the average increase of Load_Cycle_Count during one
hour on AC (before applying any &#8220;ugly fixes")
 * Load_Cycle_Count trends. for example by :
[http://ubuntuforums.org/showpost.php?p=3683526&postcount=270](http://ubuntuforums.org/showpost.php?p=3683526&postcount=270)
* use lm-profiler to get an idea for disk activity during normal use. see : [http://ubuntuforums.org/showpost.php?p=3685609&postcount=288](http://ubuntuforums.org/showpost.php?p=3685609&postcount=288)

If you need more support please ask in this thread.

Regards,

ubuntu_demon

---

### Post by ubuntu_demon on 2007-11-01
> **kfazz said:**
> something tells me this is bad...
ken@ubuntu-laptop:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   001   001   050    Old_age   Always   FAILING_NOW 1843146/1842722
(from my ancient EOL compaq armada)

Regarding the Load_Cycle_Count information you have posted :

Your WORST(1) is over your THRESHOLD (50) you should consider making backups of
all your data and running the diagnostic tool of your harddrive manufacturer to check your harddisk for problems. 

The good news is that the information you can provide might contribute to the solving of this bug. You might want to contribute some information to this bug :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216)

You should consider including this information :
 * the outcome of the diagnostic tool of your harddrive manufacturer
 * whether you have enabled laptop-mode
 * the output of $sudo smartctl -a /dev/sda
 * the age of the disk
 * an estimate of the total hours the disk has been running since you
started using it (to compare to Power_on_Hours because that value might
be off)
 * an estimate of the average increase of Load_Cycle_Count during one
hour on AC (before applying any &#8220;ugly fixes")
 * Load_Cycle_Count trends. for example by :
[http://ubuntuforums.org/showpost.php?p=3683526&postcount=270](http://ubuntuforums.org/showpost.php?p=3683526&postcount=270)
* use lm-profiler to get an idea for disk activity during normal use. see : [http://ubuntuforums.org/showpost.php?p=3685609&postcount=288](http://ubuntuforums.org/showpost.php?p=3685609&postcount=288)

If you need more support please ask in this thread.

Regards,

ubuntu_demon

---

### Post by ubuntu_demon on 2007-11-01
> **rogirwin said:**
> My laptop is a HP 6710b and was brought new in July. From then until the 18th of Oct it has been running Slackware 12. It was then upgraded to gusty and been running it ever since. The Load_Cycle_Count of 337032 seems very high? How is this possible? It's hasn't changed in the 15 mins.

Device Model:     ST9120822AS
Firmware Version: 3.ALB
User Capacity:    120,034,123,776 bytes

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       325844
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       59
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   073   062   030    Pre-fail  Always       -       23863322
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       480
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       59
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   053   046   045    Old_age   Always       -       791019567
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       42
**193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       337032**
194 Temperature_Celsius     0x0022   047   054   000    Old_age   Always       -       47 (Lifetime Min/Max 0/17)
195 Hardware_ECC_Recovered  0x001a   077   061   000    Old_age   Always       -       160277953
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

Regarding the Load_Cycle_Count information you have posted :

Your WORST(1) is almost at your THRESHOLD (0) you should consider making backups of
all your data and running the diagnostic tool of your harddrive manufacturer to check your harddisk for problems. 

The good news is that the information you can provide might contribute to the solving of this bug. You might want to contribute some information to this bug :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216)

You should consider including this information :
 * the outcome of the diagnostic tool of your harddrive manufacturer
 * whether you have enabled laptop-mode
 * the output of $sudo smartctl -a /dev/sda
 * the age of the disk
 * an estimate of the total hours the disk has been running since you
started using it (to compare to Power_on_Hours because that value might
be off)
 * an estimate of the average increase of Load_Cycle_Count during one
hour on AC (before applying any &#8220;ugly fixes")
 * Load_Cycle_Count trends. for example by :
[http://ubuntuforums.org/showpost.php?p=3683526&postcount=270](http://ubuntuforums.org/showpost.php?p=3683526&postcount=270)
* use lm-profiler to get an idea for disk activity during normal use. see : [http://ubuntuforums.org/showpost.php?p=3685609&postcount=288](http://ubuntuforums.org/showpost.php?p=3685609&postcount=288)

If you need more support please ask in this thread.

Regards,

ubuntu_demon

---

### Post by ubuntu_demon on 2007-11-01
> **rybu said:**
> 193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       713621

I have no idea what Load_Cycle_Count is measuring.  On my laptop which I bought in August it's at 713621 and going up by about 24 units every 30 seconds.   

I'm not hearing any clicks, and my hard drive hasn't failed.

Regarding the Load_Cycle_Count information you have posted :

Your WORST(1) is almost at your THRESHOLD (0) you should consider making backups of
all your data and running the diagnostic tool of your harddrive manufacturer to check your harddisk for problems. 

The good news is that the information you can provide might contribute to the solving of this bug. You might want to contribute some information to this bug :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216)

You should consider including this information :
 * the outcome of the diagnostic tool of your harddrive manufacturer
 * whether you have enabled laptop-mode
 * the output of $sudo smartctl -a /dev/sda
 * the age of the disk
 * an estimate of the total hours the disk has been running since you
started using it (to compare to Power_on_Hours because that value might
be off)
 * an estimate of the average increase of Load_Cycle_Count during one
hour on AC (before applying any &#8220;ugly fixes")
 * Load_Cycle_Count trends. for example by :
[http://ubuntuforums.org/showpost.php?p=3683526&postcount=270](http://ubuntuforums.org/showpost.php?p=3683526&postcount=270)
* use lm-profiler to get an idea for disk activity during normal use. see : [http://ubuntuforums.org/showpost.php?p=3685609&postcount=288](http://ubuntuforums.org/showpost.php?p=3685609&postcount=288)

If you need more support please ask in this thread.

Regards,

ubuntu_demon

---

### Post by bluedragon436 on 2007-11-01
I also get the pop sound when I shut down my Ubuntu laptop....I have read somewhere on here that Ubuntu for some reason causes the harddrives to spin way faster than normal...I am not sure if this is actually true, or if so why it does, but that is what I keep reading...I don't want to take a chance of my harddrive going belly up on my laptop so if anyone knows how to fix this issue it would be greatly appreciated....

---

### Post by ubuntu_demon on 2007-11-01
> **vilator said:**
> It was going up by 4 or 5 every minute, but I applied the fix and it seems to have stopped now. I just started using linux this week. I think my hdd is about 3 years old, buts its only been really used for about 1, since it was a model that I bought used in january.

Okay. The other numbers that are reported are also important. So it can't hurt to share this with us :
$sudo smartctl -a /dev/sda | grep Load_Cycle_Count

You can get an idea what the values mean by :
$sudo smartctl -a /dev/sda | more

You should also pay attention to the "worst" and "threshold" values. If worst comes close to threshold your harddrive is more likely (not guaranteed) to die.

---

### Post by drf_av on 2007-11-01
Full read is:

193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1926

I suppose that's good

---

### Post by ubuntu_demon on 2007-11-01
**If your WORST(1) is almost at your THRESHOLD (0)** you should consider making backups of all your data and running the diagnostic tool of your harddrive manufacturer to check your harddisk for problems.

The good news is that the information you can provide might contribute to the solving of this bug. You might want to contribute some information to this bug :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216)

You should consider including this information :
* the outcome of the diagnostic tool of your harddrive manufacturer
* whether you have enabled laptop-mode
* the output of $sudo smartctl -a /dev/sda
* the age of the disk
* an estimate of the total hours the disk has been running since you
started using it (to compare to Power_on_Hours because that value might
be off)
* an estimate of the average increase of Load_Cycle_Count during one
hour on AC (before applying any &#8220;ugly fixes")
* Load_Cycle_Count trends. for example by :
[http://ubuntuforums.org/showpost.php?p=3683526&postcount=270](http://ubuntuforums.org/showpost.php?p=3683526&postcount=270)
* use lm-profiler to get an idea for disk activity during normal use. see : [http://ubuntuforums.org/showpost.php?p=3685609&postcount=288](http://ubuntuforums.org/showpost.php?p=3685609&postcount=288)

If you need more support please ask in this thread.

[B]DO NOT REPLY TO THE BUGREPORT FOR SUPPORT QUESTIONS
DO NOT USE THE BUGREPORT AS A FORUM. USE THIS THREAD INSTEAD [/B]

All people who are subscribed to the bugreport will get an e-mail if you post something. If people are posting information developers can't use they will be more likely to ignore useful contributions.

---

### Post by ubuntu_demon on 2007-11-01
> **drf_av said:**
> Full read is:

193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       1926

I suppose that's good
That looks absolutely fine. Keep an eye on how fast your Load_Cycle_Count increases just to be sure.

note :
If your harddrive is only a couple of days old then this is not very good.

---

### Post by Benanov on 2007-11-01
My ThinkPad A22m is (seemingly) unaffected with a Gutsy Gobuntu install, mainly because I don't have laptop-mode enabled.  I'll have to do that.

Then again I did tweak BIOS settings and I think I got them correct.

The laptop isn't with me right now but I'll see if it or the ThinkPad A30's affected or not later tonight.

(Bah. Wrong thread.)

---

### Post by drf_av on 2007-11-01
Ok, also thanks for your effort in solving this. I can tell you I've not enabled laptop mode and my load cycle rarely increases. But, back in the days, I enabled laptop_mode in a Gutsy test install. Since it's been an hour since load cycle increased last time, I suppose that period gave a lot of Cycles. 

My HD is a Fujitsu, model MHW 2160B.

---

### Post by ice60 on 2007-11-01
i want to make a note of my Load_Cycle_Count so i can come back and check it. (i did notice the temp numbers passed the threshhold once so i installed some sensors to watch it now)

$ sudo smartctl -A /dev/sda | grep Load
193 Load_Cycle_Count        0x0032   092   092   000    Old_age   Always       -       17280

do some peole see that last number go up at an almost hourly rate? i've only had this laptop for about a month so i'm not sure if the numbers are really that good?? not terrible anyway!

---

### Post by ubuntu_demon on 2007-11-01
> **Benanov said:**
> My ThinkPad A22m is (seemingly) unaffected with a Gutsy Gobuntu install, mainly because I don't have laptop-mode enabled.  I'll have to do that.

Then again I did tweak BIOS settings and I think I got them correct.

The laptop isn't with me right now but I'll see if it or the ThinkPad A30's affected or not later tonight.

(Bah. Wrong thread.)
It's not only laptop-mode (**disabled by default**) which might cause aggressive power management settings.

Ubuntu is NOT causing aggressive power management settings!

The following things might instead cause aggressive power management settings :

    * your (laptop) harddrive firmware might have aggressive power management defaults (operating system independent)
    * your (laptop) BIOS might set your harddrive to use aggressive power management (operating system independent)
    * you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

---

### Post by ubuntu_demon on 2007-11-01
> **drf_av said:**
> Ok, also thanks for your effort in solving this. I can tell you I've not enabled laptop mode and my load cycle rarely increases. But, back in the days, I enabled laptop_mode in a Gutsy test install. Since it's been an hour since load cycle increased last time, I suppose that period gave a lot of Cycles. 

My HD is a Fujitsu, model MHW 2160B.
It's not only laptop-mode (**disabled by default**) which might cause aggressive power management settings.

Ubuntu is NOT causing aggressive power management settings!

The following things might instead cause aggressive power management settings :

    * your (laptop) harddrive firmware might have aggressive power management defaults (operating system independent)
    * your (laptop) BIOS might set your harddrive to use aggressive power management (operating system independent)
    * you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

---

### Post by ubuntu_demon on 2007-11-01
> **ice60 said:**
> i want to make a note of my Load_Cycle_Count so i can come back and check it. (i did notice the temp numbers passed the threshhold once so i installed some sensors to watch it now)

$ sudo smartctl -A /dev/sda | grep Load
193 Load_Cycle_Count        0x0032   092   092   000    Old_age   Always       -       17280

do some peole see that last number go up at an almost hourly rate? i've only had this laptop for about a month so i'm not sure if the numbers are really that good?? not terrible anyway!

Your WORST probably started out at 100 and is dropped to 92 in one months time. 

If your WORST it gets closer to 0 (your THRESHOLD) it will become likelier (**not guaranteed**) that your harddrive starts dying from a high Load_Cycle_Count.

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

It seems that your laptop BIOS and/or harddrive firmware have set too aggressive power management settings. Because if you look at your numbers then in roughly 11.5 months time your Load_Cycle_Count would approach 200.000 and your WORST would be approaching 0. Because 11.5 * 17280 = 198720 and 11.5 * 8 = 92.

You can make a better estimate if you look at Power_On_Hours (if these Power_On_Hours seem to be correct to you) and if you can give the exact number of days you have been using this harddrive.

```

$ sudo smartctl -a /dev/sda | grep Power_On_Hours

```

**Let's hope this issue turns out to be not so bad or that they will release a fix soon.**

---

### Post by m0shen on 2007-11-01
I have a dell m1210.  I have disabled the power management and even acoustic management in the bios, ensured myself that laptop-mode is off in /etc/defaults/acpi-support and even changed /etc/acpi/power.sh to HDPARM -B 254 in the potentially troublesome instances and I am still seeing increases of about 4 per minute.

Only when I issue the command manually does it stop:
```

hdparm -B 254 /dev/sda

```

I have had several flavors of linux on here as well as windows and I have to admit that this is the first time that I've paid any attention to this... I am fairly confident it is a new development.

Specifics..

9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       3112
193 Load_Cycle_Count        0x0032   090   090   000    Old_age   Always       -       106880

Which averages to 34/hour...

Is there any way to issue this command automatically?

Thank you for your help :(

---

### Post by ubuntu_demon on 2007-11-01
> **m0shen said:**
> I have a dell m1210.  I have disabled the power management and even acoustic management in the bios, ensured myself that laptop-mode is off in /etc/defaults/acpi-support and even changed /etc/acpi/power.sh to HDPARM -B 254 in the potentially troublesome instances and I am still seeing increases of about 4 per minute.

Only when I issue the command manually does it stop:
```

hdparm -B 254 /dev/sda

```

I have had several flavors of linux on here as well as windows and I have to admit that this is the first time that I've paid any attention to this... I am fairly confident it is a new development.

Specifics..

9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       3112
193 Load_Cycle_Count        0x0032   090   090   000    Old_age   Always       -       106880

Which averages to 34/hour...

Is there any way to issue this command automatically?

Thank you for your help :(

If your WORST started at 100 then you have used roughly 10%  of your Load_Cycle_Count and still 90% to go. If your WORST started at 200 then you have still 45% to go.This is just **a very rough estimate.**

If you decide to apply the ugly fixes then please read this and be sure to use 254 instead of 255 in your case :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

Please let me know if it doesn't work.

---

### Post by ubuntu_demon on 2007-11-01
To people who are experiencing a lot of wake ups :

If you would like to know what kind of things you see accessing your disk when you do the things you do normally you can run this (but **answer N** to all of these questions in order to not change anything) : 
```

$sudo lm-profiler

```

I have 2 GB of ram and 0 swap use. My result :

```

Profiling run started.
Write accesses at 7/600 in lm-profiler run: thunderbird-bin                 
Write accesses at 8/600 in lm-profiler run: thunderbird-bin                 
Write accesses at 25/600 in lm-profiler run: liferea-bin                    
Write accesses at 90/600 in lm-profiler run: liferea-bin                    
Write accesses at 118/600 in lm-profiler run: thunderbird-bin               
Write accesses at 154/600 in lm-profiler run: liferea-bin                   
Write accesses at 173/600 in lm-profiler run: thunderbird-bin               
Write accesses at 219/600 in lm-profiler run: liferea-bin                   
Write accesses at 230/600 in lm-profiler run: thunderbird-bin               
Write accesses at 282/600 in lm-profiler run: liferea-bin                   
Write accesses at 283/600 in lm-profiler run: thunderbird-bin               
Write accesses at 339/600 in lm-profiler run: thunderbird-bin               
Write accesses at 346/600 in lm-profiler run: liferea-bin                   
Write accesses at 392/600 in lm-profiler run: thunderbird-bin               
Write accesses at 410/600 in lm-profiler run: liferea-bin                   
Write accesses at 448/600 in lm-profiler run: thunderbird-bin               
Write accesses at 475/600 in lm-profiler run: liferea-bin                   
Write accesses at 503/600 in lm-profiler run: thunderbird-bin               
Write accesses at 540/600 in lm-profiler run: liferea-bin                   
Profiling run completed.                            

```

I had set the interval to get messages to 1 minute in thunderbird (2 accounts). If thunderbird tries to get new messages and there are no new messages there is still some disk activity Setting the update interval of thunderbird to a higher value (for example 10 minutes) removes unnecessary disk access.  Related bug report :
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/160466](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/160466)

Regarding liferea : Some feeds set feed specific intervals which might cause unnessary disk activity. Setting all feeds to a global update interval (for example 1 hour) helps. Bug report : [https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/160460](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/160460)

---

### Post by m0shen on 2007-11-01
> **ubuntu_demon said:**
> Read this and be sure to use 254 instead of 255 in your case :
[http://ubuntuforums.org/showpost.php?p=3675784&postcount=25](http://ubuntuforums.org/showpost.php?p=3675784&postcount=25)
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

Please let me know if it doesn't work.

Does the no spin down effect suspend? (forgive me if that's a stupid question...)

---

### Post by technomaniac on 2007-11-01
I type
sudo smartctl --all /dev/sda | grep Power-Off_Retract_Count
 and I get
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       831


Is this bad? how bad? and how do I solve it

---

### Post by dimbulb1024 on 2007-11-01
I have a Hitachi  hard drive and found this tool via the Dell Linux Forum for setting the parameters

[http://www.hitachigst.com/hdd/support/download.htm#FeatureTool](http://www.hitachigst.com/hdd/support/download.htm#FeatureTool)

I downloaded the .iso image and ran that.
For me APM was set at default which is halfway between performance and battery life, ie middle of the road. My feeling this would not be my ramp up on Load_Cycle_Count issue.

I still haven't found a way via my BIOS to adjust APM.

Anyway, just wanted to pass along the link for the Hitachi drive tool.

---

### Post by ice60 on 2007-11-01
> **ubuntu_demon said:**
> Your WORST probably started out at 100 and is dropped to 92 in one months time. 

If your WORST it gets closer to 0 (your THRESHOLD) it will become likelier (**not guaranteed**) that your harddrive starts dying from a high Load_Cycle_Count.

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances. My harddrive started to die slowly when at a Load_Cycle_Count of 200.000.

It seems that your laptop BIOS and/or harddrive firmware have set too aggressive power management settings. Because if you look at your numbers then in roughly 11.5 months time your Load_Cycle_Count would approach 200.000 and your WORST would be approaching 0. Because 11.5 * 17280 = 198720 and 11.5 * 8 = 92.

You can make a better estimate if you look at Power_On_Hours (if these Power_On_Hours seem to be correct to you) and if you can give the exact number of days you have been using this harddrive.

```

$ sudo smartctl -a /dev/sda | grep Power_On_Hours

```

**Let's hope this issue turns out to be not so bad or that they will release a fix soon.**thanks for all the help, ubuntu_demon :) 

i don't think it looks very good now, i get this -
```
$ sudo smartctl -a /dev/sda | grep Power_On_Hours
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       381
```
and now when i run the load command it's gone up one point, but i did turn it off and just booted up again to run this. does booting make that go up? i haven't read enough about it :(
```
$ sudo smartctl -A /dev/sda | grep Load
193 Load_Cycle_Count        0x0032   092   092   000    Old_age   Always       -       17281
```


i decided to use that fix, but i did this below. is this the same fix?

```
gksudo gedit /etc/hdparm.conf
```
and add this -
```
/dev/sda {
apm 254
}
```
and start it like this -
```
sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S07hdparm
```

[color=blue]EDIT[/color] i'm really confused now because i just checked System>Administration>Services and **hdparm** wasn't checked ?? so i put a check next to that as well!

---

### Post by ubuntu_demon on 2007-11-01
> **m0shen said:**
> Does the no spin down effect suspend? (forgive me if that's a stupid question...)

It shouldn't affect suspend-to-ram nor hibernate-to-disk. Although you need to add the 99-hdd-spin-fix.sh to the appropriate directories to make sure that your hdparm settings are still valid after  resume/attaching AC/attaching battery.

Remember to only do the ugly fix if you are affected (if your WORST will get to your threshold within three years or if your Load_Cycle_Count is increasing too fast... let's say faster than 180 per day until we have a better number).

---

### Post by ubuntu_demon on 2007-11-01
> **technomaniac said:**
> I type
sudo smartctl --all /dev/sda | grep Power-Off_Retract_Count
 and I get
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       831


Is this bad? how bad? and how do I solve it

Your Load_Cycle_Count is at 831. So I'm guessing your WORST probably started at 100 and is still at 100. If you have your harddrive longer than a couple of days you are perfectly fine.

In general we can see more if people give more information :
* how old their disk is
* how much time their laptop runs daily on average : Power_On_Hours (retrieve in same way as Load_Cycle_Count and please say whether you think this number is valid)
* full Load_Cycle_Count information of a couple of days

---

### Post by siloko on 2007-11-01
Apologies

---

### Post by ubuntu_demon on 2007-11-01
> **dimbulb1024 said:**
> I have a Hitachi  hard drive and found this tool via the Dell Linux Forum for setting the parameters

[http://www.hitachigst.com/hdd/support/download.htm#FeatureTool](http://www.hitachigst.com/hdd/support/download.htm#FeatureTool)

I downloaded the .iso image and ran that.
For me APM was set at default which is halfway between performance and battery life, ie middle of the road. My feeling this would not be my ramp up on Load_Cycle_Count issue.

I still haven't found a way via my BIOS to adjust APM.

Anyway, just wanted to pass along the link for the Hitachi drive tool.

Thanks for sharing your find. There's also the Ultimate Boot CD which contains a lot of these tools :
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by dachinster on 2007-11-01
do these problems affect desktops with sata drives also?
i frequently go into standby mode with my always-on desktop?

---

### Post by ubuntu_demon on 2007-11-01
> **ice60 said:**
> thanks for all the help, ubuntu_demon :) 


You are welcome :)

> **ice60 said:**
> 
```
$ sudo smartctl -A /dev/sda | grep Load
193 Load_Cycle_Count        0x0032   092   092   000    Old_age   Always       -       17281
```


If your WORST started at 100 you have aproximately 92% Load_Cycle_Count life left. It depends on how old your disk is how good this number is. You should want to be able to use a harddisk for three years. If you have your harddisk running with Linux for more than 3 months this is fine.

> **ice60 said:**
> 
i decided to use that fix, but i did this below. is this the same fix?

```
gksudo gedit /etc/hdparm.conf
```
and add this -
```
/dev/sda {
apm 254
}
```
and start it like this -
```
sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S07hdparm
```

[color=blue]EDIT[/color] i'm really confused now because i just checked System>Administration>Services and **hdparm** wasn't checked ?? so i put a check next to that as well!

You should only use fixes if you understand what they do and how they work. In your case you probably don't need the fix If you have your harddisk running with Linux for more than 3 months. If that's the case I recommend undoing the fix (remove the content you added in /etc/hdparm.conf and remove /etc/rcS.d/S08hdparm)

If you have your laptop harddrive for less than 3 months you can remove the fix and apply this fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
which also sets spindown time to 0 and sets hdparm values after resuming/attaching AC/starting to run on battery. But only do so if you understand what you are doing otherwise it might be best to wait for an official fix.

---

### Post by ubuntu_demon on 2007-11-01
> **dachinster said:**
> do these problems affect desktops with sata drives also?
i frequently go into standby mode with my always-on desktop?

Probably not. Unless you use an external drive cage with a 2.5" laptop drive in it.

---

### Post by ice60 on 2007-11-01
> **ubuntu_demon said:**
> You are welcome :)



If your WORST started at 100 you have aproximately 92% Load_Cycle_Count life left. It depends on how old your disk is how good this number is. You should want to be able to use a harddisk for three years. If you have your harddisk running with Linux for more than 3 months this is fine.



You should only use fixes if you understand what they do and how they work. In your case you probably don't need the fix If you have your harddisk running with Linux for more than 3 months. If that's the case I recommend undoing the fix (remove the content you added in /etc/hdparm.conf and remove /etc/rcS.d/S08hdparm)

If you have your laptop harddrive for less than 3 months you can remove the fix and apply this fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
which also sets spindown time to 0 and sets hdparm values after resuming/attaching AC/starting to run on battery. But only do so if you understand what you are doing otherwise it might be best to wait for an official fix.
thanks, ubuntu_demon :) i'll undo all the fixes i did and keep an eye on it

i thought i'd only had the laptop for a month or so, but this is the laptop i got in this thread, at the beginning of May lol i don't use it much so 3 months is probably about right.
[http://ubuntuforums.org/showthread.php?t=435207](http://ubuntuforums.org/showthread.php?t=435207)

---

### Post by newbie2 on 2007-11-01
HP laptop 6715b here...2 weeks old...heard also those 'abnormal clicks' from my hardrive...used this advise(and the 'clicks' stopped) :
> The fix?

hdparm -B 255 /dev/sda

and the spinning-down stops. I don't know what certain other OSes do with their drives at bootup, but the current behaviour is certainly deadly for the drive. Worse: nobody will notice, since smartmontools aren't installed by default. I noticed frequent clicking sounds earlier, but I didn't think those were spindowns since I hadn't specifically set the drive into any low-power mode. I only noticed this by accident after I got smartmontools working.
What does that command do? Let’s break it down.
hdparm: This is a linux command designed to fetch and set certain attributes of ATA/IDE hard drives.
The -B: Set Advanced Power Management feature, if the drive supports it. A low value means aggressive power management and a high value means better performance. A value of 255 will disable apm on the drive.
and /dev/sda is obviously the disk drive in question.
A relatively simple fix for a somewhat complicated problem. The only issue here is that battery life will be adversely affected, however that’s better than having a hard drive that’s dead two years after you bought it. It will be interesting to see how the Ubuntu team decides to handle this. As of yet, the trouble ticket is unassigned. 
[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)
[http://www.theregister.co.uk/2007/11/01/ubuntu_laptop_disk_issues/](http://www.theregister.co.uk/2007/11/01/ubuntu_laptop_disk_issues/)
:???:

---

### Post by technomaniac on 2007-11-01
To ubuntu_demon,
Thanks a lot for the reply. I was scared. My laptop is more than 10 months old. So I dont think I have a problems.Now I can run my fav OS(Ubuntu) in peace

---

### Post by Average_Joe on 2007-11-02
Hello --

I have age 15-months IBM Lenovo 3000 N100 laptop,
running Ubuntu 6.06 / 7.04 / 7.10 since day one.
As of installing 7.10 high-pitched constant whine of hard drive
making me like the crazy man.  maybe this thread is my problem?

Here are results.  I don't understand what (which?) fix to apply for me.
Lenovo 3000 N100    Toshiba HD -- model MK8032GS

[PHP]193 Load_Cycle_Count 0x0032 091 091 0  92096
222 Loaded_Hours     0x0032 096 096 0   1837
223 Load_Retry_Count 0x0032 100 100 0      0
224 Load_Friction    0x0022 100 100 0      0
226 Load-in_Time     0x0026 100 100 0    325

all above are listed "Old Age Always"
also, below are 
  9 Power_On_Hours   0x0032   094   094 0   2736
192 Power-Off_Retract_Count 0x0032   100      57[/PHP]

Thank you for suggest me any kind people the help !!!

---

### Post by eode on 2007-11-02
Noticed this on one of the bugreports concerning this issue, and figured I'd pass it on.  Good news for Hitachi-havers.  :-)

> Just to let you know: Hitachi uses quite special own technology to park
HDD heads outside of magnetic disks area to a special parking ramp. This
causes HDD heads not to suffer from parking - they're NEVER land on disk
surface during parking. So, actually, Hitachi HDDs can handle a LOTS of
starts\stops without any real problems (a bit like CD\DVD drives do).
Hitachi even recommending aggressive power management on their own to
certain degree due to this fact. However well, stopping HDD every minute
is an overkill anyway. And yes, not each and every HDD has such
wonderful heads parking system.

You can read more in following whitepaper:
http://www.hitachigst.com/tech/techlib.nsf/techdocs/9076679E3EE4003E86256FAB005825FB/$file/LoadUnload_white_paper_FINAL.pdf


---

### Post by bwiklak on 2007-11-02
Hi,

Yesterday in Poland, in one of the major papers "Gazeta Wyborcza" I found article about the fact that Ubuntu could possibly damage laptops Hard drives. I made some investigation i realized, that in my 4mounths old hd i have over 100000 load cycles. 

Do you think it`s a good commerial for Ubuntu? What should i tell friends whom I recommended and installed Ubuntu? It`s a shame that this bug in on whishlist for so a long time.

Could anyone resposible for whishlisting this bug answear this questions?

It`s not a shame to make a mistake, but why it is not soleved?!?!?!

Thanks in advance

---

### Post by ubuntu_demon on 2007-11-02
> **ice60 said:**
> thanks, ubuntu_demon :) i'll undo all the fixes i did and keep an eye on it

i thought i'd only had the laptop for a month or so, but this is the laptop i got in this thread, at the beginning of May lol i don't use it much so 3 months is probably about right.
[http://ubuntuforums.org/showthread.php?t=435207](http://ubuntuforums.org/showthread.php?t=435207)

You are welcome :)

Great. Keep an eye on it and only apply ugly fixes if you are heavily affected and understand what you are doing.

---

### Post by ubuntu_demon on 2007-11-02
> **newbie2 said:**
> HP laptop 6715b here...2 weeks old...heard also those 'abnormal clicks' from my hardrive...used this advise(and the 'clicks' stopped) :
 
[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)
[http://www.theregister.co.uk/2007/11/01/ubuntu_laptop_disk_issues/](http://www.theregister.co.uk/2007/11/01/ubuntu_laptop_disk_issues/)
:???:

If you are hearing a lot of those ticks you should probably do :

$sudo hdparm -B 255 /dev/sda
$sudo hdparm -S 0 /dev/sda

You can keep doing it manually but if you would like to automate it you might want to apply the ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

Only do so if you are heavily affected (you are hearing a lot of ticks or your Load_Cycle_Count increases very fast) and you understand what you are doing.

---

### Post by ubuntu_demon on 2007-11-02
> **technomaniac said:**
> To ubuntu_demon,
Thanks a lot for the reply. I was scared. My laptop is more than 10 months old. So I dont think I have a problems.Now I can run my fav OS(Ubuntu) in peace

You are welcome :). In your case there's absolutely nothing to worry about. Your BIOS and harddrive firmware are setting sane defaults which don't have to be overridden.

---

### Post by ubuntu_demon on 2007-11-02
> **Average_Joe said:**
> Hello --

I have age 15-months IBM Lenovo 3000 N100 laptop,
running Ubuntu 6.06 / 7.04 / 7.10 since day one.
As of installing 7.10 high-pitched constant whine of hard drive
making me like the crazy man.  maybe this thread is my problem?

Here are results.  I don't understand what (which?) fix to apply for me.
Lenovo 3000 N100    Toshiba HD -- model MK8032GS

[PHP]193 Load_Cycle_Count 0x0032 091 091 0  92096
222 Loaded_Hours     0x0032 096 096 0   1837
223 Load_Retry_Count 0x0032 100 100 0      0
224 Load_Friction    0x0022 100 100 0      0
226 Load-in_Time     0x0026 100 100 0    325

all above are listed "Old Age Always"
also, below are 
  9 Power_On_Hours   0x0032   094   094 0   2736
192 Power-Off_Retract_Count 0x0032   100      57[/PHP]

Thank you for suggest me any kind people the help !!!

It's better to give the whole output of your Load_Cycle_Count line.

In your case your harddrive has aproximately 45% of Load_Cyles left if WORST started at 200. Your harddrive has aproximately 91% of Load_Cycles left if WORST started at 100. So with a bit of luck you can use your harddrive for three years before your WORST (91 right now) approaches your THRESHOLD (0).

But since your Power_On_Hours is only 2736 this would mean 33 Load_Cycles per hour. I would recommend keeping an eye on your Load_Cycle_Count and not applying any fixes right now.

You should compare the numbers you are showing now with the numbers in one week.

---

### Post by ubuntu_demon on 2007-11-02
> **bwiklak said:**
> Hi,

Yesterday in Poland, in one of the major papers "Gazeta Wyborcza" I found article about the fact that Ubuntu could possibly damage laptops Hard drives. I made some investigation i realized, that in my 4mounths old hd i have over 100000 load cycles. 

Do you think it`s a good commerial for Ubuntu? What should i tell friends whom I recommended and installed Ubuntu? It`s a shame that this bug in on whishlist for so a long time.

Could anyone resposible for whishlisting this bug answear this questions?

It`s not a shame to make a mistake, but why it is not soleved?!?!?!

Thanks in advance

You can tell your friends that it is not Ubuntu who is setting aggressive power management defaults but that some laptop BIOSes and some laptop harddrive firmwares are affected.

The reason why Ubuntu isn't doing much about yet is probably because the manufacturers should know what their hardware is capable of. And it should be the job of the manufacturers to set sane defaults. I wrote something about this on my blog : [http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

---

### Post by bwiklak on 2007-11-02
> **ubuntu_demon said:**
> You can tell your friends that it is not Ubuntu who is setting aggressive power management defaults but that some laptop BIOSes and some laptop harddrive firmwares are affected.

The reason why Ubuntu isn't doing much about yet is probably because the manufacturers should know what their hardware is capable of. And it should be the job of the manufacturers to set sane defaults. I wrote something about this on my blog : [http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

I'm a big fanof ubuntu too. I used windows, MacOS( in school ) then mandrake, mandriva, opensuse and i thin ubuntus is the best. 
I dont understand, if manufacturers woul not set default aggressive power management current Ubuntu settings woult be ok?

Question2. If I set "hdparm -B 254" my load cycles dont rise so fast. Is may hard drive still safe or
 I shold  have to worry about HD heat, waking up and suspending ( in my case suspend doesnt work so I do not use it by my friends do )

---

### Post by ubuntu_demon on 2007-11-02
> **bwiklak said:**
> I'm a big fanof ubuntu too. I used windows, MacOS( in school ) then mandrake, mandriva, opensuse and i thin ubuntus is the best. 
I dont understand, if manufacturers woul not set default aggressive power management current Ubuntu settings woult be ok?


Ubuntu doesn't set these agressive power management settings so if your BIOS and your laptop harddrive firmware use sane defaults you aren't affected.

> **bwiklak said:**
> 
Question2. If I set "hdparm -B 254" my load cycles dont rise so fast. Is may hard drive still safe or
 I shold  have to worry about HD heat, waking up and suspending ( in my case suspend doesnt work so I do not use it by my friends do )

That might be a trade off to make. You should only apply the ugly fixes if you are seriously affected and your laptop harddrive manufacturer is not setting sane defaults.

When to consider applying ugly fixes :
* if you estimate that your &#8220;WORST&#8221; will approach your &#8220;THRESHOLD&#8221; within three years of use
* if you hear a lot of ticks while your laptop is running
* if your Load_Cycle_Counts rises very fast (in increments of one otherwise you have to divide your Load_Cycle_Count by the size of the increment). roughly faster than 180 per day if you aim for less than 200.000 Load_Cycle_Counts within three years. Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances.

In case of the ugly fix you probably want to set the power management value (-B) to somewhere between 128 and 254. If you are worried about power usage or heat you should try 128. You can experiment with values between 128 (low power usage) and 254 (best performance) although values below 254 still can do much head parks (depending on the harddrive) so you should keep watching your Load_Cycle_Count.

I set my power management to 128 somewhere between 16:20 and 16:40. Between 16:40 and 17:00 I see 42 Load_Cycles within 20 minutes. That&#8217;s 2 Load_Cycles per minute :
```

193 Load_Cycle_Count 0×0032 200 200 000 Old_age Always - 903 | Fri Nov 2
16:20:01 CET 2007
193 Load_Cycle_Count 0×0032 200 200 000 Old_age Always - 920 | Fri Nov 2
16:40:02 CET 2007
193 Load_Cycle_Count 0×0032 200 200 000 Old_age Always - 962 | Fri Nov 2
17:00:01 CET 2007

```

In general we can see more if people give more information :
* how old their disk is
* how much time their laptop runs daily on average : Power_On_Hours (retrieve in same way as Load_Cycle_Count and please say whether you think this number is valid)
* full Load_Cycle_Count information of a couple of days

---

### Post by ubuntu_demon on 2007-11-02
tferero received an email from Bruce Allen. For the whole story read :
[http://www.linuxquestions.org/questions/showthread.php?p=2945630#post2945630](http://www.linuxquestions.org/questions/showthread.php?p=2945630#post2945630)

[quote=Bruce Allen]
I think that the -B value of 255 is incorrect. You should use 254 for
maximum performance. 255 IS DOCUMENTED AS 'RESERVED' IN THE ATA/SATA
SPECS. THE BEHAVIOR OF -B 255 THUS IS NOT PREDICTABLE AND IT MAY HAVE NO
EFFECT. Also according to the ATA/SATA specs any value greater than or
equal to 128 will 'not permit the device to spin down to save power'. So
128 will reduce power use as much as possible but not permit spin-down.
[/quote]

Bruce Allen is :
* author of "Monitoring Hard Disks with SMART", Linux Journal, 2004) :
[http://www.linuxjournal.com/article/6983](http://www.linuxjournal.com/article/6983)
* maintainer of the website [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

blackhole54 notified us here about this here :
[http://ubuntuforums.org/showpost.php?p=3690862&postcount=15](http://ubuntuforums.org/showpost.php?p=3690862&postcount=15)

In case of the ugly fix you probably want to set the power management value (-B) to somewhere between 128 and 254. If you are worried about power usage or heat you should try 128. You can experiment with values between 128 (low power usage) and 254 (best performance) although values below 254 still can do much head parks (depending on the harddrive) so you should keep watching your Load_Cycle_Count.

The Load_Cycle_Count can still rise very fast when you set power management to 128. I set my power management to 128 somewhere between 16:20 and 16:40. Between 16:40 and 17:00 I see 42 Load_Cycles within 20 minutes. That's 2 Load_Cycles per minute.

```

193 Load_Cycle_Count 0x0032 200 200 000 Old_age Always - 903 | Fri Nov 2 16:20:01 CET 2007
193 Load_Cycle_Count 0x0032 200 200 000 Old_age Always - 920 | Fri Nov 2 16:40:02 CET 2007
193 Load_Cycle_Count 0x0032 200 200 000 Old_age Always - 962 | Fri Nov 2 17:00:01 CET 2007

```

---

### Post by bwiklak on 2007-11-02
Thank You for complete and kind answer,  I should know now what to do.

---

### Post by ntt on 2007-11-02
Hi all,

thanks for the info shared so far.

In my case (Ubuntu 7.10 on an HP 65xx laptop), setting a value of hdparm -B 255 (or 254) _does_ work. it stops the load_cycle_count from raising any further, otherwise every few minutes you can hear the HD heads doing nasty noises, and every time the load_cycle_count ticks upward.

May be you can hint me about another thing: I've modified /etc/hdparm.conf to include the following:

/dev/sda {
        apm = 255
}

In theory, the above code should automatically set the -B hdparm value to 255 every time the system boots; as a matter of fact it doesn't, and I'm forced to execute "sudo hdparm -B 255" by hand as soon as I've logged into Ubuntu.

Unfortunately there's no way that I know of to query for the current value of -B during the boot process, so I don't know whether is hdparm.conf not being executed during boot or something else resetting the -B value later on in the boot process.

Any suggestions about how to make  hdparm.conf working (or perhaps how to check for the current -B hdparm value)?

Thanks in advance.

--ntt

---

### Post by houstonbofh on 2007-11-02
Well here is some more information from the skeptic on the other side.  To begin, this is on a brand new machine.  It was built with all new components, and placed in service with the Gutsy daily build on 9/24/07.  I often leave my computer on for days at a time.  I have had no problems or errors that cause me to mount ro on this hard drive.  I installed smartmontools on this system and ran it.
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   175   175   021    Pre-fail  Always       -       6208
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       67
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       464
 10 Spin_Retry_Count        0x0012   100   253   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       65
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       200
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       275
194 Temperature_Celsius     0x0022   117   113   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

```

Looks bad, no?  But if my read error rate was that high, I would have seen fsck at least once, and had the drive go into read only.  Never happened.  That and the current, worst and raw have no realistic relation.  Spin up time also seems odd...  Reallocated sectors is also pre-fail with a raw of 0?  Keep in mind that this is a brand new, well performing drive, on a desktop.
```
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD5000AAKS-00TMA0
Serial Number:    WD-WCAPW2871057
Firmware Version: 12.01C01
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Nov  2 17:27:42 2007 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```
So, on paper I am on the verge of screaming death.  In reality I am on a screaming banshee gamer system.  The problem may be a bug in the smart reporting...  Or a massive misunderstanding by many people.
On the other hand, sleeping and touching a drive every 30 seconds just can't be a good thing.

---

### Post by jack handy on 2007-11-02
> **ice60 said:**
> 

i decided to use that fix, but i did this below. is this the same fix?

```
gksudo gedit /etc/hdparm.conf
```
and add this -
```
/dev/sda {
apm 254
}
```
and start it like this -
```
sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S07hdparm
```

[color=blue]EDIT[/color] i'm really confused now because i just checked System>Administration>Services and **hdparm** wasn't checked ?? so i put a check next to that as well!

how do i undo this fix?  specifically the last part:

```
sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S07hdparm
```

thank you

---

### Post by mc-rpg on 2007-11-02
@ubuntu_demon: Can you tell me which should be the ‘normal’ interval between each increase of the Load_Cycle_Count number? I know this number isn’t constant but tell me which you think it is, just to give an idea. It could be helpful to more than one.

Mines seems to be increasing one Load_Cycles every ten minutes but I don't know if that's the normal behavior. This is with the AC adapter unplugged, plugged the behavior seems to be worse. This is with the laptop mode disabled (by default). Does the AC adapter change the behavior of the hdds or is just me?

---

### Post by ubuntu_demon on 2007-11-03
> **ntt said:**
> Hi all,

thanks for the info shared so far.

In my case (Ubuntu 7.10 on an HP 65xx laptop), setting a value of hdparm -B 255 (or 254) _does_ work. it stops the load_cycle_count from raising any further, otherwise every few minutes you can hear the HD heads doing nasty noises, and every time the load_cycle_count ticks upward.

May be you can hint me about another thing: I've modified /etc/hdparm.conf to include the following:

/dev/sda {
        apm = 255
}

In theory, the above code should automatically set the -B hdparm value to 255 every time the system boots; as a matter of fact it doesn't, and I'm forced to execute "sudo hdparm -B 255" by hand as soon as I've logged into Ubuntu.

Unfortunately there's no way that I know of to query for the current value of -B during the boot process, so I don't know whether is hdparm.conf not being executed during boot or something else resetting the -B value later on in the boot process.

Any suggestions about how to make  hdparm.conf working (or perhaps how to check for the current -B hdparm value)?

Thanks in advance.

--ntt

Try 254. 

Also don't forget to add 99-hdd-spin-fix.sh to the appropriate places (especially if you suspend/hibernate sometimes) :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

Please note that you don't have to put any ugly fix in place if you are not heavily affected. (hearing strange clicking noises too much counts as heavily affected IMHO) Only do an ugly fix if you understand what you are doing.

---

### Post by ubuntu_demon on 2007-11-03
> **houstonbofh said:**
> Well here is some more information from the skeptic on the other side.  To begin, this is on a brand new machine.  It was built with all new components, and placed in service with the Gutsy daily build on 9/24/07.  I often leave my computer on for days at a time.  I have had no problems or errors that cause me to mount ro on this hard drive.  I installed smartmontools on this system and ran it.
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   175   175   021    Pre-fail  Always       -       6208
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       67
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       464
 10 Spin_Retry_Count        0x0012   100   253   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   253   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       65
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       200
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       275
194 Temperature_Celsius     0x0022   117   113   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

```

Looks bad, no?  But if my read error rate was that high, I would have seen fsck at least once, and had the drive go into read only.  Never happened.  That and the current, worst and raw have no realistic relation.  Spin up time also seems odd...  Reallocated sectors is also pre-fail with a raw of 0?  Keep in mind that this is a brand new, well performing drive, on a desktop.
```
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD5000AAKS-00TMA0
Serial Number:    WD-WCAPW2871057
Firmware Version: 12.01C01
User Capacity:    500,107,862,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Nov  2 17:27:42 2007 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```
So, on paper I am on the verge of screaming death.  In reality I am on a screaming banshee gamer system.  The problem may be a bug in the smart reporting...  Or a massive misunderstanding by many people.
On the other hand, sleeping and touching a drive every 30 seconds just can't be a good thing.

You don't suffer from this issue at all. There's nothing to worry about.

---

### Post by ubuntu_demon on 2007-11-03
> **jack handy said:**
> how do i undo this fix?  specifically the last part:

```
sudo ln -s /etc/init.d/hdparm /etc/rcS.d/S07hdparm
```

thank you

You should never apply any manual fixes if you don't understand what you are doing.
To undo the fixes :
* remove the 99-hdd-spin-fix.sh files if you have created them.
* remove /etc/rcS.d/S07hdparm
* remove the stuff you added in your /etc/hdparm.conf
* you can disable the hdparm service here : system->administration->services (it won't cause any overhead if you keep it running)
* if you editted some other files you should restore them to their old content

---

### Post by ubuntu_demon on 2007-11-03
> **mc-rpg said:**
> @ubuntu_demon: Can you tell me which should be the &#8216;normal&#8217; interval between each increase of the Load_Cycle_Count number? I know this number isn&#8217;t constant but tell me which you think it is, just to give an idea. It could be helpful to more than one.

Mines seems to be increasing one Load_Cycles every ten minutes but I don't know if that's the normal behavior. This is with the AC adapter unplugged, plugged the behavior seems to be worse. This is with the laptop mode disabled (by default). Does the AC adapter change the behavior of the hdds or is just me?

If you keep an eye on your Load_Cycle_Count values then you can make a rough calculation about when your WORST will reach your THRESHOLD. If you want to use your harddrive for three years then you should aim not to get your WORST to 0 or 1 before those three years have passed.

If your raw Load_Cycle_Count value acts as a counter and increments with 1 then you can also look at the specification of your harddrive (at the site of your harddrive manufacturer) and compare those numbers. Otherwise you would have to divide your raw Load_Cycle_Count value by the size of the increment to get to your real Load_Cycle_Count.

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances.

Personally I would aim for an increase of less than 180 Load_Cycles per day (on average) which would mean that you would have less than 200.000 Load_Cycles within three years.

---

### Post by ubuntu_demon on 2007-11-03
Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).

---

### Post by ntt on 2007-11-03
> **ubuntu_demon said:**
> Try 254. 

Already done that, thanks
.
Anyway in my situation 254 or 255 seem to have the same effect (HD heads stop clicking multiple times a minute); the only difference is when querying with hdparm -I, 255 makes it output "APM disabled", 254 generates "APM level: 254".

Also don't forget to add 99-hdd-spin-fix.sh to the appropriate places (especially if you suspend/hibernate sometimes) :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

I willl, thanks.

Please note that you don't have to put any ugly fix in place if you are not heavily affected. (hearing strange clicking noises too much counts as heavily affected IMHO) Only do an ugly fix if you understand what you are doing.

Fully agree, those off-place HD clicks make me uncomfortable. And in a moderately quiet environment you could hear the HD loudly clicking alarmingly often (but as soon as I force the HD APM off, no more).

Unfortunately, the bios of this laptop offers very few options  to control anything, so hdparm seems to be my only friend for the time being.

Dammit, this notebook's bios must have been specifically crippled for Vista (which was indeed preloaded on it).

thanks again.

--ntt

---

### Post by Simplicius on 2007-11-03
ubuntu_demon,

You have been very generous and you answered many questions form many people here and in your blog.

If you have a minute, could you have a look?

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   099   099   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   100   100   020    Pre-fail  Always       -       236
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   069   060   030    Pre-fail  Always       -       9613381
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       392
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   100   100   020    Pre-fail  Always       -       235
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   049   039   045    Old_age   Always   In_the_past 857473075
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       178
193 Load_Cycle_Count        0x0032   081   081   000    Old_age   Always       -       38618
194 Temperature_Celsius     0x0022   051   061   000    Old_age   Always       -       51 (Lifeti
me Min/Max 0/22)
195 Hardware_ECC_Recovered  0x001a   075   061   000    Old_age   Always       -       165868540
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

If I understand this, I have almost 100 Load cycles per hour.  That's a bit much, isn't it?

Thanks for any advice

EDIT: I have been doing some more reading and now I see that my load cycles seems definitely too high. I'll investigate further.

---

### Post by ubuntu_demon on 2007-11-03
> **Simplicius said:**
> ubuntu_demon,

You have been very generous and you answered many questions form many people here and in your blog.

If you have a minute, could you have a look?

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   099   099   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   100   100   020    Pre-fail  Always       -       236
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   069   060   030    Pre-fail  Always       -       9613381
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       392
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   100   100   020    Pre-fail  Always       -       235
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   049   039   045    Old_age   Always   In_the_past 857473075
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       178
193 Load_Cycle_Count        0x0032   081   081   000    Old_age   Always       -       38618
194 Temperature_Celsius     0x0022   051   061   000    Old_age   Always       -       51 (Lifeti
me Min/Max 0/22)
195 Hardware_ECC_Recovered  0x001a   075   061   000    Old_age   Always       -       165868540
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

If I understand this, I have almost 100 Load cycles per hour.  That's a bit much, isn't it?

Thanks for any advice

EDIT: I have been doing some more reading and now I see that my load cycles seems definitely too high. I'll investigate further.

Did you use your harddrive for 392 hours in total ? If that number is true then you should definitely use the ugly fix because your WORST is already at 82 which means you have used already about 18% of your available Load_Cycles if your WORST started out at 100.

---

### Post by Simplicius on 2007-11-04
> **ubuntu_demon said:**
> Did you use your harddrive for 392 hours in total ? 

Yes. I bought it less than two months ago. I'll try the ugly fix. Thanks!!!

---

### Post by spamzilla on 2007-11-04
If you enable the 'ugly fix' stated on post 26 (as well as in other posts) and you don't need to, will it cause any negative afftects towards the hard drive?

---

### Post by b0ng0 on 2007-11-04
I have just bought a Dell XPS M1330 and I was wanting to install Ubuntu on it but after reading all this stuff about the load cycles on the HD's i'm a bit apprehensive now. Could anyone inform me as to how safe it would be to install Ubuntu on my laptop and would I need to change anything to prevent Ubuntu from knackering the HD? Thanks.

---

### Post by vivedekananda on 2007-11-04
b0ng0, install windows version of smartctl and hdparm and check if you are not getting high cycle count under windows too. I was (under win xp).

---

### Post by b0ng0 on 2007-11-04
Presumably the laptop will be set up so that the cycle count is normal (it comes pre-installed with Vista Premium). How do I know what is a normal load on the HD?

---

### Post by ubuntu_demon on 2007-11-04
> **spamzilla said:**
> If you enable the 'ugly fix' stated on post 26 (as well as in other posts) and you don't need to, will it cause any negative afftects towards the hard drive?

You might use more power than needed and your harddrive might run at a higher temperature than needed.

Also don't forget that having your harddisk head park protects your harddrive if you experience any bumps (which is especially nice if you are on the road and therefor probably working on battery).

---

### Post by ubuntu_demon on 2007-11-04
> **b0ng0 said:**
> I have just bought a Dell XPS M1330 and I was wanting to install Ubuntu on it but after reading all this stuff about the load cycles on the HD's i'm a bit apprehensive now. Could anyone inform me as to how safe it would be to install Ubuntu on my laptop and would I need to change anything to prevent Ubuntu from knackering the HD? Thanks.

Ubuntu will not knacker your harddisk. Too aggressive power management settings set by BIOS or harddrive firmware might shorten the lifetime of your harddisk.

Ubuntu is NOT causing aggressive power management settings!

The following things might instead cause aggressive power management settings :

    * your (laptop) harddrive firmware might have aggressive power management defaults (operating system independent)
    * your (laptop) BIOS might set your harddrive to use aggressive power management (operating system independent)
    * you might have enabled laptop-mode in /etc/default/acpi-support (disabled by default) which will set your harddrive to use aggressive power management

So your BIOS and harddrive firmware can both set these aggressive power maangement settings. Your Load_Cycle_Count might increase too fast under any operating system which doesn't override settings which might be too aggressive.

---

### Post by ubuntu_demon on 2007-11-04
> **b0ng0 said:**
> Presumably the laptop will be set up so that the cycle count is normal (it comes pre-installed with Vista Premium). How do I know what is a normal load on the HD?

I'm not sure where the boundary lies exactly. But I can give you some raw estimates.

Harddrive manufacturers seem to claim most harddrives can handle at least 600.000 Load_Cycles but this is probably an average under ideal circumstances.

Less than 540 Load_Cycles per day is fine if you would aim for less than 600.000 Load_Cycles in three years.

Personally I would aim for less than 200.000 Load_Cycles in three years to be sure.Which means less than 180 Load_Cycles per day is absolutely fine.

---

### Post by houstonbofh on 2007-11-04
> **ubuntu_demon said:**
> You don't suffer from this issue at all. There's nothing to worry about.
I know this... :)  My point was questioning the demonstrably false information contained in SMART.  And I happened to be on my new desktop...  I am not saying that there is no problem.  I am, however, saying that the reaction so far outweighs the information available.  So far what I have been able to put together is this.

Power management will spin down the drives, and aggressive power management will spin them down quickly.

Some drives park the heads on spin down.

Ubuntu touches the drive frequently in moderate use.

Ubuntu touches the drive frequently while idle! (Frankly I think this is where the focus should be)

There is no GUI tool to adjust either of these functions.  (Perhaps here as well)

Some drives do not handle parking the drives more then 500000 times.  Some do.

The only tool to see what is happening is SMART. (Which is often inaccurate)

While turning off power management addresses one issue, it also user more power, deep cycles the battery more often, generates more heat, and is loud.  What about a quick and dirty fix to have Ubuntu stop touching the drive 5 times a minute?  I think everyone is focused on one SMART parameter to the exclusion of all else.  But I may be wrong...  This is why I am following this thread, and what Ubuntu_demon is doing.  And thanks for doing it!

---

### Post by ubuntu_demon on 2007-11-05
> **houstonbofh said:**
> I know this... :)  My point was questioning the demonstrably false information contained in SMART.  And I happened to be on my new desktop...  I am not saying that there is no problem.  I am, however, saying that the reaction so far outweighs the information available.  So far what I have been able to put together is this.

Power management will spin down the drives, and aggressive power management will spin them down quickly.

Some drives park the heads on spin down.

Ubuntu touches the drive frequently in moderate use.

Ubuntu touches the drive frequently while idle! (Frankly I think this is where the focus should be)

There is no GUI tool to adjust either of these functions.  (Perhaps here as well)

Some drives do not handle parking the drives more then 500000 times.  Some do.

The only tool to see what is happening is SMART. (Which is often inaccurate)

While turning off power management addresses one issue, it also user more power, deep cycles the battery more often, generates more heat, and is loud.  What about a quick and dirty fix to have Ubuntu stop touching the drive 5 times a minute?  I think everyone is focused on one SMART parameter to the exclusion of all else.  But I may be wrong...  This is why I am following this thread, and what Ubuntu_demon is doing.  And thanks for doing it!

You are welcome :)

It's not only spin-up / spin-down cycles that increment the Load_Cycle_Count. Head-park cycles without spinning down/up are probably causing the most Load_Cycles AFAIK.

If your harddrive head is parked it needs to be unparked before you can use the harddisk. 

For APM values above 128 (including 128) your harddrive will not spin down unless you set the spin down time to a value above 0 (0 will disable spin down). 

Your harddrive will park it's heads to safe power and protect the disk from bumps. AFAIK for APM values below 128 (including 128) your disk will do this the most.

If you minimize disk access too aggressive power management will hurt less. You might want to use lm-profiler to get an idea for disk activity during normal use. see : [http://ubuntuforums.org/showpost.php?p=3685609&postcount=288](http://ubuntuforums.org/showpost.php?p=3685609&postcount=288)
You might want to file bug reports if you see some application accessing the disk way too often. 

You can also atime by using noatime which prevents writing to the disk to update atime. Some programs such as some (console based) e-mail programs need atime.

And there are some values in /proc/sys/vm/ you might want to experiment with. You probably shouldn't enable laptop-mode but I used laptop-mode to check what kind of values it sets on my machine because they might be reasonable defaults :

```

/proc/sys/vm/dirty_ratio:   60
/proc/sys/vm/dirty_background_ratio:   1
/proc/sys/vm/dirty_expire_centisecs:   60003
/proc/sys/vm/dirty_writeback_centisecs:   60003

```

---

### Post by Gruntler on 2007-11-05
Ubuntu Demon. While appreciate your love and support for Ubuntu and your dedication to help its users I have to take issue with some of the things you are defending so hard.

1- Ubuntu does touch your APM settings when in laptop mode setting them to a very aggressive setting. 

2- The scripts handling APM are known to be buggy and have been known to enable agressive APM settings even in desktop systems without user intervention. (I have no experience of this but it has been discussed in Launchpad)

3- In the tests I have done in my laptop Windows does not override the default APM setting but does produce load cycle counts around 20 times lower than Ubuntu and Debian with same APM setting. With the same APM setting  Fedora 7  produces no increases in load cycle count when, watch this!, Gnome is running!. Under KDE and in console mode load cycle count increase rapidly, APM setting stays constant.

4- Similar results to those described above have been reported by other users that took the trouble to test the behavior or their systems running different OSs.

To Summarize:

- Ubuntu is setting agressive APM settings in some causes.
- The default manufacturer settings are not the problem.
- The rate of load cycle count increase under a given APM setting is highly             OS dependent
- There is something else at work here than just an APM setting. 

Finally I would like to add that while users are encouraged to just apply the ugly fix and nothing else is done to recognize the issue the bug will continue to exist. I am happy that at least other communities seem to have taken a more serious approach to this problem.

And do not get me wrong. I love Ubuntu. I am running Fedora 7 now since the ugly fix did not work for me and I miss Ubuntu and would love to see this issue resolved.

---

### Post by ubuntu_demon on 2007-11-05
I have updated my ugly fix to explain how to automatically change your APM value when on battery which will give you more protection from bumps and higher battery life.

ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

---

### Post by ubuntu_demon on 2007-11-05
> **Gruntler said:**
> Ubuntu Demon. While appreciate your love and support for Ubuntu and your dedication to help its users I have to take issue with some of the things you are defending so hard.

1- Ubuntu does touch your APM settings when in laptop mode setting them to a very aggressive setting. 


I know Ubuntu touches your APM settings if you use laptop-mode. See also :
[http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/](http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/)

However laptop-mode is disabled by default

> **Gruntler said:**
> 
2- The scripts handling APM are known to be buggy and have been known to enable agressive APM settings even in desktop systems without user intervention. (I have no experience of this but it has been discussed in Launchpad)


I haven't examined these scripts (are you talking about the package laptop-mode-tools ?). I have faith in Ubuntu Developers such as Matthew Garret that they try their best to maintain their packages. So you should file a bug report if you discover something. 

> **Gruntler said:**
> 
3- In the tests I have done in my laptop Windows does not override the default APM setting but does produce load cycle counts around 20 times lower than Ubuntu and Debian with same APM setting. With the same APM setting  Fedora 7  produces no increases in load cycle count when, watch this!, Gnome is running!. Under KDE and in console mode load cycle count increase rapidly, APM setting stays constant.


I have never said that windows does override these settings. I have used the word **might**.

Windows and/or Mac OS X might be overriding APM settings which might make Ubuntu look bad if Ubuntu doesn&#8217;t override these settings. I don't know whether this is the case. It might not be the case. It might be the case that Windows only overrides APM settings if they are below some value.

You might want to use lm-profiler to get an idea for disk activity during normal use. see : [http://ubuntuforums.org/showpost.php?p=3685609&postcount=288](http://ubuntuforums.org/showpost.php?p=3685609&postcount=288)
You might want to file bug reports if you see some application accessing the disk way too often. 

> **Gruntler said:**
> 
4- Similar results to those described above have been reported by other users that took the trouble to test the behavior or their systems running different OSs.

To Summarize:

- Ubuntu is setting agressive APM settings in some causes.


laptop-mode is disabled by default

> **Gruntler said:**
> 
- The default manufacturer settings are not the problem.


Part of the problem is that some applications might cause unnecessary disk activity. We can file bugs for that. 

I have mentioned this a couple of times already. See for example [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/19](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/19)
(top causes for spin up and top causes for unparks are probably the same top causes)

Another part of the problem is too aggressive power management settings for some (not for everyone).

Not all laptop BIOSes are affected. Not all laptop harddrive firmwares are affected. If some people report over very big Load_Cycle_Counts within a couple of months IMHO these people suffer from way too aggressive power management settings. 

Some examples :

[http://ubuntuforums.org/showpost.php?p=3676465&postcount=161](http://ubuntuforums.org/showpost.php?p=3676465&postcount=161)
193 Load_Cycle_Count 0x0032 001 001 000 Old_age Always - 337032
age : bought in July

[http://ubuntuforums.org/showpost.php?p=3677732&postcount=174](http://ubuntuforums.org/showpost.php?p=3677732&postcount=174)
[http://ubuntuforums.org/showpost.php?p=3677803&postcount=175](http://ubuntuforums.org/showpost.php?p=3677803&postcount=175)
193 Load_Cycle_Count 0x0032 001 001 000 Old_age Always - 713621
age : bought in August

> **Gruntler said:**
> 
- The rate of load cycle count increase under a given APM setting is highly             OS dependent


Yes. And it is also dependent on the applications that are used. And also dependent on  the user because everyone uses different applications and uses their applications in a different way.

> **Gruntler said:**
> 
- There is something else at work here than just an APM setting. 
.

Yes we can try to to reduce unnecessary disk activity. Let's file bugs if we find something.

> **Gruntler said:**
> 
Finally I would like to add that while users are encouraged to just apply the ugly fix and nothing else is done to recognize the issue the bug will continue to exist. I am happy that at least other communities seem to have taken a more serious approach to this problem.


What are you talking about ? Which communities ?

> **Gruntler said:**
> 
And do not get me wrong. I love Ubuntu. I am running Fedora 7 now since the ugly fix did not work for me and I miss Ubuntu and would love to see this issue resolved.

You can try different APM values for example 254. You can also try to disable power management in your BIOS and your harddrive manufacturer probably has a tool you can use (you might need to do both if the ugly fix doesn't work for you).

---

### Post by eode on 2007-11-05
> **Gruntler said:**
> 
1- Ubuntu does touch your APM settings when in laptop mode setting them to a very aggressive setting. 

EDITED:  At least as far as laptop-mode goes, this is incorrect.  It does not change the settings, even when using a laptop, and running on/changing to/from battery and AC.

> 2- The scripts handling APM are known to be buggy and have been known to enable agressive APM settings even in desktop systems without user intervention. (I have no experience of this but it has been discussed in Launchpad)

This is most likely a confusion with this same issue, and with hardware defaults.  But once one is sorted out, the other will become obvious, if it is two separate issues.

> 3- In the tests I have done in my laptop Windows does not override the default APM setting but does produce load cycle counts around 20 times lower than Ubuntu and Debian with same APM setting. With the same APM setting  Fedora 7  produces no increases in load cycle count when, watch this!, Gnome is running!. Under KDE and in console mode load cycle count increase rapidly, APM setting stays constant.

Good.  Most here don't run Fedora, although some may.  Perhaps someone can confirm this to be true or false -- that, on a system that has the problem while running Ubuntu, the same problem does not exist while running Fedora.

> 4- Similar results to those described above have been reported by other users that took the trouble to test the behavior or their systems running different OSs.

Gentoo may have this issue, and SuSe has this issue in their tracker.

> - Ubuntu is setting agressive APM settings in some causes.
- The default manufacturer settings are not the problem.
- The rate of load cycle count increase under a given APM setting is highly             OS dependent
- There is something else at work here than just an APM setting. 

A succinct response:
- EDITED: Ubuntu does indeed seem to set APM at all, at least via laptop-mode (unless laptop-mode has been enabled, which it isn't by default).  It is possible that it changes settings in some other way, but I haven't looked into it to know definitively or not.  Someone else said they made a script that checks for this, but that's quite quick to do, and I'll do it tonight or tomorrow.
- The default manufacturer settings are not the problem, but modifying them to be less aggressive is a good dirty workaround.
- The rate of load cycle count is indeed OS dependent, because it is dependent specifically on the frequency of disk access (which, with APM at a non-aggressive setting, is not a problem).
- The "Something Else At Work Here"(tm) is frequent disk access, and it is only a problem when combined with aggressive APM.
- Frequent disk access *is* a problem, and it does cause wear, and it should be dealt with, particularly considering that some systems have extremely aggressive APM as a '''manufacturer's default'''.  In fact, it is listed (ironically) as a disk-saving feature by some HW providers (such as Western Digital and Hitachi).
- This affects more distributions than Ubuntu.

> Finally I would like to add that while users are encouraged to just apply the ugly fix and nothing else is done to recognize the issue the bug will continue to exist. I am happy that at least other communities seem to have taken a more serious approach to this problem.

While users are encouraged to apply the ugly fix (because it prevents wear in the short term), there is a bug report that has people working on the issue.  It has, however, been sidelined for way too long.

> And do not get me wrong. I love Ubuntu. I am running Fedora 7 now since the ugly fix did not work for me and I miss Ubuntu and would love to see this issue resolved.

Understandable.  I'm doing my best to get things rolling.

-b

---

### Post by eode on 2007-11-05
I edited my previous post to be more accurate.  Namely, laptop-mode is not enabled by default, even on laptops (at least not on mine).  Thus, my settings are not altered during ACPI events such as switching to AC or Battery.

This also means that any modifications to laptop-mode won't work unless ENABLE_LAPTOP_MODE is set to "true" in /etc/default/acpi-support.

---

### Post by lordof7 on 2007-11-05
I have been following this topic with interest , and have observed the high reload-count increase rate on my testing laptop (4-6 yr old toshiba satellite with toshiba drive) with Xubuntu 6.10. 

Regarding the frequent disk access, I read in another thread that the frequent disk access is likely due to the journaling system of the disk format one uses.  In that thread it was pointed out that ext3 (which I use) has a default commit of 5 seconds.  I believe this means that the disk is touched every five seconds to somehow update the journal (please correct me if I'm wrong, or add details.)  Therefore, heads would park, and then unpark 5 sec later to do the commit thing.  Then, after the time determined by default API settings, they would park again, only to unpark again 5 seconds later.  On that thread they mentioned slowing down the commit rate, but that would have its own issues.  Clearly such a disk access isn't a big deal in a server situation where data integrity is important and the drive isn't going to get dropped (one hopes!), but in the laptop situation, things are different.  It was speculated that this journaling takes place even when no other activity is occuring.  I for one would like a way to stop the journaling and spin down the hdd (and blank the monitor) after a certain time to save power.  However, in a laptop environment, one may have to decide which is most important: journaling, battery power, or head protection in case of dropping.

Oh, and the ugly fix did stop the count increase for me.  And my 2 yr old Dell with toshiba harddrive has about 200k reload count, and it has only seen winxp.

---

### Post by lutra on 2007-11-05
Hi Ubuntu_Demon
I'm trying to figure out alone if I need the ugly fix or not reading all you posted here and in your blog but I'm a little puzzled by the results of smartctl on my laptop that is exactly one year old and that always had ubuntu installed.

The Load_Cycle_Count seems high but I'm not sure it advances only by single values, in fact sometimes after a "click" it advances by more than one but sometimes it advances by one.

Would not be better to change the APM values trough the tools provided by Hitachi rather than fixing it in the o.s.?

Is there any method to know if the "worst" value started from 100 or from 200?


```
=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HTS721010G9SA00
Serial Number:    MPCZN7Y0H26PEL
Firmware Version: MCZOC10H
User Capacity:    100,030,242,816 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Tue Nov  6 00:10:48 2007 WET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 645) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  50) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   115   115   000    Old_age   Offline      -       3419
  3 Spin_Up_Time            0x0007   209   209   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1157
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   116   116   000    Old_age   Offline      -       38
  9 Power_On_Hours          0x0012   092   092   000    Old_age   Always       -       3649
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1136
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       444
193 Load_Cycle_Count        0x0012   080   080   000    Old_age   Always       -       200535
194 Temperature_Celsius     0x0002   161   161   000    Old_age   Always       -       34 (Lifetime Min/Max 10/52)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         0         -
# 2  Short captive       Completed without error       00%         0         -

Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by tferero on 2007-11-05
Just thought I would add my comments on this problem.

I am running a Dell latitude C610, 128MB of ram. My drive is less than one year old, with light to moderate usage (a few hours a day since installing linux 2 months ago; a few hours a week prior to that.

I have load cycle counts of 58,704.  The counts were incrementing at ~5 per minute previously.  I set the hdparm to -B254 and that has stopped the cycling.  I *did not* do any of the suggested scripts.

**Now here is the interesting part:  the -B254 setting has remained sticky across shutdowns for me.**  I know this is not the case for everyone else, and I have no idea why this is for me.  I have shutdown and restarted several times, and I am still at 58,704.

Here is what I can tell you, for my system:

--Power management is disabled by Ubuntu
--Power management has been disabled in the BIOS
--My drive continues to increment heavily at values between 128 and 254, but slows down   slightly (to ~2-3 per minute) in this range.
--According to Smartmontools, I have over 28,000 hours on my drive (physically impossible for a drive less than one year old)

On the subject of hours, _please read the man pages _regarding this value.  Some drives actually report the time in minutes, while smartctl uses hours.  If you think your drive might do this, use this command to change the reading to minutes: 

```
sudo smartctl -d ata -A -v 9,minutes /dev/sda

```

where "-d ata" is used if the smartctl doesn't recognize your drive (you run a smartctl command and it fails), and /dev/sda is your drive (for some of you it might be /dev/hda). The -A switch tells smartctl to display vendor specific attributes and can be used instead of the -a switch. Please read the man pages for more info on this.  For those of you new to man pages, in Konqueror, type: [COLOR="Blue"]**man:smartctl **[/COLOR]  in the address bar.

NOTE:  While -B255 does seem to work for a lot of people, Bruce Allen from the Smartmontools  info site  emailed me and indicated that this value is reserved on most drives, and the right value to use is -B254.  He also indicates that values over 128 are supposed to stop spinning, although this was not the case with me.  Some drives may ignore -B255 value altogether, while others may work, but read back the setting as -B254.  **If -B255 doesn't seem to work for you, try -B254**

Mr. Allen's response to me is below:

**************************
 Hi T-,
 
 I just learned about this buzz from a colleague yesterday.
 
 I don't have any experience with your Samsung drive. I suggest that you
 run a sort self-test '-t short' and wait until it completes. The drive
 age should then be shown in the self test log. Then experiment with the
 different -v and -F options to see how the drive is storing its lifetime.
 
 IMPORTANT INFORMATION BELOW: PLEASE PASS BACK TO THE UBUNTU COMMUNITY
 
 I think that the -B value of 255 is incorrect. You should use 254 for
 maximum performance. 255 IS DOCUMENTED AS 'RESERVED' IN THE ATA/SATA
 SPECS. THE BEHAVIOR OF -B 255 THUS IS NOT PREDICTABLE AND IT MAY HAVE NO
 EFFECT. Also according to the ATA/SATA specs any value greater than or
 equal to 128 will 'not permit the device to spin down to save power'. So
 128 will reduce power use as much as possible but not permit spin-down.
 
 References:
 [http://www.t13.org/Documents/Uploade...7_Volume_1.pdf](http://www.t13.org/Documents/Uploade...7_Volume_1.pdf)
 PDF page 273 Document page 253
 Table 43 (and the paragraph immediately following it).
 
 So I suggest you try some different -B values such as -B 254 or -B 128.
 
 The hdparm man page says 'values of 255 will disable Advanced Power
 Management'. I think this is a mistake in the man page. According to the
 ATA/SATA specs referenced above, the value 255 is reserved and has vendor
 dependent meaning (or has no effect).
 
 Cheers,
 Bruce
 ***************************

---

### Post by dimbulb1024 on 2007-11-05
By a quirk I fixed my hyper growing Load_Cycle_Count with 7.10.

On a hunch I happened to remove Tracker Search Tool since I don't really use it (I pretty much know where everything is :) ).

My Load_Cycle_Count increase has dropped significantly! :popcorn:

---

### Post by ubuntu_demon on 2007-11-06
> **lordof7 said:**
> I have been following this topic with interest , and have observed the high reload-count increase rate on my testing laptop (4-6 yr old toshiba satellite with toshiba drive) with Xubuntu 6.10. 

Regarding the frequent disk access, I read in another thread that the frequent disk access is likely due to the journaling system of the disk format one uses.  In that thread it was pointed out that ext3 (which I use) has a default commit of 5 seconds.  I believe this means that the disk is touched every five seconds to somehow update the journal (please correct me if I'm wrong, or add details.)  Therefore, heads would park, and then unpark 5 sec later to do the commit thing.  Then, after the time determined by default API settings, they would park again, only to unpark again 5 seconds later.  On that thread they mentioned slowing down the commit rate, but that would have its own issues.  Clearly such a disk access isn't a big deal in a server situation where data integrity is important and the drive isn't going to get dropped (one hopes!), but in the laptop situation, things are different.  It was speculated that this journaling takes place even when no other activity is occuring.  I for one would like a way to stop the journaling and spin down the hdd (and blank the monitor) after a certain time to save power.  However, in a laptop environment, one may have to decide which is most important: journaling, battery power, or head protection in case of dropping.


By coincidence I have also started looking into this but I didn't see the thread your mention. Can you please post the url of this thread ?

> **lordof7 said:**
> 
Oh, and the ugly fix did stop the count increase for me.  And my 2 yr old Dell with toshiba harddrive has about 200k reload count, and it has only seen winxp.

You can look up the specs for your harddrive. If it says 600.000 Load_Cycles then you might want to wait a few days/weeks for an official fix. You probably won't be near the 600.000 lifecycles before your harddrive dies from something else (6 years seems a bit much for a laptop harddrive). I'm saying this because your harddrive is already two years old.

---

### Post by ubuntu_demon on 2007-11-06
> **lutra said:**
> Hi Ubuntu_Demon
I'm trying to figure out alone if I need the ugly fix or not reading all you posted here and in your blog but I'm a little puzzled by the results of smartctl on my laptop that is exactly one year old and that always had ubuntu installed.

The Load_Cycle_Count seems high but I'm not sure it advances only by single values, in fact sometimes after a "click" it advances by more than one but sometimes it advances by one.

Would not be better to change the APM values trough the tools provided by Hitachi rather than fixing it in the o.s.?

Is there any method to know if the "worst" value started from 100 or from 200?


```
=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HTS721010G9SA00
Serial Number:    MPCZN7Y0H26PEL
Firmware Version: MCZOC10H
User Capacity:    100,030,242,816 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 1
Local Time is:    Tue Nov  6 00:10:48 2007 WET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 645) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  50) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   115   115   000    Old_age   Offline      -       3419
  3 Spin_Up_Time            0x0007   209   209   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1157
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   116   116   000    Old_age   Offline      -       38
  9 Power_On_Hours          0x0012   092   092   000    Old_age   Always       -       3649
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1136
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       444
193 Load_Cycle_Count        0x0012   080   080   000    Old_age   Always       -       200535
194 Temperature_Celsius     0x0002   161   161   000    Old_age   Always       -       34 (Lifetime Min/Max 10/52)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         0         -
# 2  Short captive       Completed without error       00%         0         -

Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

You might want to wait a few days/weeks for an official fix. Because even if your WORST started at 100 then you will still have 4 years left before your WORST reaches your THRESHOLD. Probably your drive will die from something else before it is 5 years old.

---

### Post by ubuntu_demon on 2007-11-06
> **dimbulb1024 said:**
> By a quirk I fixed my hyper growing Load_Cycle_Count with 7.10.

On a hunch I happened to remove Tracker Search Tool since I don't really use it (I pretty much know where everything is :) ).

My Load_Cycle_Count increase has dropped significantly! :popcorn:

Thanks for sharing. 

Some **possible** culprits of unnessary disk activity. These bugs are possible contributors to the Load_Cycle_Count issue.

* the commit interval for the ext3 filesystem should be higher than 5 seconds for laptop users
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160448](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160448)

* ext3 partitions should be mounted with noatime or relatime for laptop users
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160450](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160450)

* acpid : Log output far too verbose
[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/31512](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/31512)

* liferea might cause unnecessary disk activity
[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/160460](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/160460)

* If thunderbird tries to get new messages and there are no new messages there is still some disk activity
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/160466](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/160466)

* tracker : the index delay should be set to a higher value for laptop users
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/160468](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/160468)

firefox might cause unnecessary disk activity when going to a new website
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/160513](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/160513)

hddtemp might cause unnecessary disk activity
[https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621](https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621)

Please contribute to these bug reports.

I would like to know if people find any other possible culprits for example by using lm-profiler :
[http://ubuntuforums.org/showpost.php?p=3685609&postcount=288](http://ubuntuforums.org/showpost.php?p=3685609&postcount=288)

---

### Post by dimbulb1024 on 2007-11-06
> **ubuntu_demon said:**
> Thanks for sharing. 

... * tracker : the index delay should be set to a higher value for laptop users
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/160468](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/160468)

Please contribute to these bug reports.]

Whatever my limited Linux knowledge can do to help :) - I have left a post to the tracker bug.

---

### Post by ubuntu_demon on 2007-11-06
> **dimbulb1024 said:**
> Whatever my limited Linux knowledge can do to help :) - I have left a post to the tracker bug.

Thank you very much

---

### Post by ubuntu_demon on 2007-11-06
to Eode :

Thanks for your help to get to the bottom of the Load_Cycle_Count issue.

According to you evolution might cause unnecessary disk activity. Could you please report a bug against evolution in roughly the same style as I did against thunderbird :
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/160466](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/160466)

You told us here that evolution might cause unnecessary disk activity :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/48](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/48)

Thanks :)

---

### Post by lordof7 on 2007-11-06
[quote=ubuntu_demon]By coincidence I have also started looking into this but I didn't see the thread your mention. Can you please post the url of this thread ?[/quote]

I can't find the exact thread I first saw the ext3 thing, but the following threads are somewhat informative:

This thread talks about ext3 causing many accesses for one, but not another guy.  Also, kernel and system logging seemed to cause hdd access. Additionally, one solution was to ENABLE laptop_mode via laptop-mode-tools
[http://ubuntuforums.org/showthread.php?t=36976&highlight=hdd+spindown](http://ubuntuforums.org/showthread.php?t=36976&highlight=hdd+spindown)

This thread shows that kjournald (a journaling process I guess) does access the harddrive alot.
[http://ubuntuforums.org/showthread.php?t=567876&highlight=harddrive+access](http://ubuntuforums.org/showthread.php?t=567876&highlight=harddrive+access)

at the end of this one, kjournald is again mentioned.
[http://ubuntuforums.org/showthread.php?t=5617](http://ubuntuforums.org/showthread.php?t=5617)

This page suggestes maybe paging software could be responsible:
[http://ubuntuforums.org/showthread.php?t=583483&highlight=hdd+access](http://ubuntuforums.org/showthread.php?t=583483&highlight=hdd+access)

Here is a page detailing the journaling aspect of the ext3 filesystem.  I couldn't understand 90% of it, but it did look like he suggested that journaling (or committing) might happen every 5-10 sec.
[http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html](http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html)

finally, this page talks about a possible fix.  Note that its pretty messy, but scroll down to where its says "mount options".  There is details how to change the journaling frequency, as well as disabling access time which is normally used to "keeps the kernel from logging every (read and write) access to the file. Which would have filled the write buffer with unneccessary write commands and spun up the disk earlier."  (Perhaps doing these two mount options alone would decrease disk accesses, although I don't know how wise it is to change the journaling settings.  Also, if you need file access data, you can't disable it.)
[http://gentoo-wiki.com/HOWTO_HDD_spindown_small_server](http://gentoo-wiki.com/HOWTO_HDD_spindown_small_server)

Here is another discussion on the journaling.  It is suggested that perhaps a non-journaling filesystem would be more appropriate for a laptop.
[http://linuxgazette.net/issue89/tag/2.html](http://linuxgazette.net/issue89/tag/2.html)

[quote=ubuntu_demon]
Quote:
Originally Posted by lordof7 View Post
Oh, and the ugly fix did stop the count increase for me. And my 2 yr old Dell with toshiba harddrive has about 200k reload count, and it has only seen winxp.
You can look up the specs for your harddrive. If it says 600.000 Load_Cycles then you might want to wait a few days/weeks for an official fix. You probably won't be near the 600.000 lifecycles before your harddrive dies from something else (6 years seems a bit much for a laptop harddrive). I'm saying this because your harddrive is already two years old.[/quote]

What I meant was, this computer is a non-ubuntu reference - it has ONLY seen winxp, and after 2 years of around 8-10 hours/day use has a load_cycle count of around 200k.  Therefore, although winxp will increase the load_cycle count (of course), it doesn't seem to be as rapid as what we're seeing here.  So xp may be handling things differently.  NTFS has some sort of journaling function, but only Microsoft knows for sure how it works (being a proprietary file system and all.)

---

### Post by lordof7 on 2007-11-06
And, 30sec later, I find the original post I saw the ext3 stuff in. 

[http://ubuntuforums.org/showthread.php?t=96687&highlight=ext3+spindown](http://ubuntuforums.org/showthread.php?t=96687&highlight=ext3+spindown)

---

### Post by ubuntu_demon on 2007-11-06
> **lordof7 said:**
> And, 30sec later, I find the original post I saw the ext3 stuff in. 

[http://ubuntuforums.org/showthread.php?t=96687&highlight=ext3+spindown](http://ubuntuforums.org/showthread.php?t=96687&highlight=ext3+spindown)

Thanks for all the links. I posted this :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/84](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/84)

I have reported and collected some bugs about possible unnessary disk activity including ext3 ones :
[http://ubuntuforums.org/showpost.php?p=3716058&postcount=348](http://ubuntuforums.org/showpost.php?p=3716058&postcount=348)

---

### Post by wylie348 on 2007-11-06
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       556

---

### Post by ubuntu_demon on 2007-11-06
> **wylie348 said:**
> 192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       556

You are probably fine unless you just got the disk a few days ago (then you should give more information).

In general people who want support or have questions should give at least the following information in this thread :
* the age of your disk
* Power_On_Hours (sudo smartctl -a /dev/sda | grep Power_On_Hours)
* Load_Cycle_Count (sudo smartctl -a /dev/sda | grep Load_Cycle_Count)

---

### Post by comfortablynumb on 2007-11-06
I just learned about a Load Cycle Bug that can effect the longevity of hard drives, I installed smartmon and ran sudo smartctl -a /dev/sda | grep Load_Cycle_Count, I haven't seen it move since installing it, it shows 

193 Load_Cycle_Count        0x0032   058   058   000    Old_age   Always       -       85555

Does that look normal? I installed this hard drive about 2 years ago, it's mainly had XP on it but I installed 7.10 Last week.

---

### Post by floke on 2007-11-06
Yep. Normal.
Don't panic.

---

### Post by ddrichardson on 2007-11-06
Actually, its pretty high but if it isn't moving then you're OK. I have written a lot about this recently on my blog (link in sig). Contrary to what you may have read this isn't a bug as such its a difference of opinion, and the one thing I can tell you is that after testing both OS's - Windows does it too.

It comes down to hard drive manufacturer - if the hdd uses landing zones then you may start to experience problems if it uses cams such as IBM, Hitachi and many others then its completely irrelevant.

---

### Post by kevykev on 2007-11-06
Hi All,

I think I have this problem too. The disk is brand new, only about 2 weeks old
(i replaced the existing drive in my laptop). 

Power_On_Hours=91
Load_Cycle_Count=18343

I wrote a shell script to measure cycle counts over a ten minute period and
found that 37 cycles occured in 10 minutes (about 220 an hour). 

There is another peculiarity however: My laptop doesn't make the characteristic
clicking sound of loading and unloading (described by other people with the same 
problem) very often at all. Even more strange - when i try the workaround of  
disabling APM (sudo hdparm -B 254 /dev/sda) the drive then begins clicking about
once every minute or so, but the load cycle count stops incrementing!

One final strange thing: The load count is described as attribute #ID 225 instead
of 193 (as others reported, and is documented in man pages). I dont know if this
is significant.

Anyway, I dont know whether to trust the reported load cycle count and enable
the workaround (ignoring the clicking when it's on), or just to assume the load
cycle count is somehow wrong.

The hdd is a Samsung HM250JI (Firmware: HS100-08 ) btw. I'm aware that some
samsung drives have firmware bugs and tried the -F samsung and -F samsung2
flags with smartctl, but this didn't seem to change the values. Any heap or advice
would be greatly appreciated!

Cheers

---

### Post by ubuntu_demon on 2007-11-06
I would like to see some btrace output from people who are suffering from the fastly increasing Load_Cycle_Count problem.

```

sudo aptitude install blktrace
sudo btrace /dev/sda

```

When I ran btrace myself I got this : "/sys/kernel/debug does not appear to be a debug filesystem"
That's probably because I have encrypted my disk during the installation (using the alternate cd)

I got this information here :
[https://launchpad.net/ubuntu/+bug/17878/comments/31](https://launchpad.net/ubuntu/+bug/17878/comments/31)

---

### Post by comfortablynumb on 2007-11-06
Actually I think I was reading it wrong not paying attention to the last line it's going up like crazy. I shut it down shortly after that post and just started it 15 minutes ago, [B]it's now at 85604 and was 85582 when I started it.
[/B]
Hard Drive 
 Seagate Momentus ST92811A 20GB 5400 RPM ATA-6

I have a backup IBM that came with my T23 Laptop when I got it used, but I ripped it out because it was slower and has less cache (2mb as opposed to 8 ) then this Seagate that  I was using my old laptop, should I put the IBM drive back in?

---

### Post by kevykev on 2007-11-06
> **ubuntu_demon said:**
> I would like to see some btrace output from people who are suffering from the fastly increasing Load_Cycle_Count problem.

```

sudo aptitude install blktrace
sudo btrace /dev/sda

```

When I ran btrace myself I got this : "/sys/kernel/debug does not appear to be a debug filesystem"
That's probably because I have encrypted my disk during the installation (using the alternate cd)

I got this information here :
[https://launchpad.net/ubuntu/+bug/17878/comments/31](https://launchpad.net/ubuntu/+bug/17878/comments/31)

I get the same message from btrace, but my filesystem 
is a standard ext3 with no encryption..

btw, i also tried running 

```
sudo hdparm -B n /dev/sda
```

for n = 1, 5, 100, 128, 250, and 253. However, the rate of increase of the
load unload count was not significantly impacted. Only a value of 254 
appears to make any difference on my drive, and that value causes the 
worrying clicking i mentioned

---

### Post by kevykev on 2007-11-06
> **kevykev said:**
> I get the same message from btrace, but my filesystem 
is a standard ext3 with no encryption..


Ah, apparently, this is cause you need to mount it as a debug filesystem first

```
sudo mount -t debugfs none_debug /sys/kernel/debug

```

then you can run btrace. 

It produces a lot of output, the vast majority seems to be [kjournald], with a couple
of [swapper] and [firefox-bin] ones thrown in. I can post a sample if you need it

---

### Post by ubuntu_demon on 2007-11-06
> **kevykev said:**
> Hi All,

I think I have this problem too. The disk is brand new, only about 2 weeks old
(i replaced the existing drive in my laptop). 

Power_On_Hours=91
Load_Cycle_Count=18343

I wrote a shell script to measure cycle counts over a ten minute period and
found that 37 cycles occured in 10 minutes (about 220 an hour). 

There is another peculiarity however: My laptop doesn't make the characteristic
clicking sound of loading and unloading (described by other people with the same 
problem) very often at all. Even more strange - when i try the workaround of  
disabling APM (sudo hdparm -B 254 /dev/sda) the drive then begins clicking about
once every minute or so, but the load cycle count stops incrementing!

One final strange thing: The load count is described as attribute #ID 225 instead
of 193 (as others reported, and is documented in man pages). I dont know if this
is significant.

Anyway, I dont know whether to trust the reported load cycle count and enable
the workaround (ignoring the clicking when it's on), or just to assume the load
cycle count is somehow wrong.

The hdd is a Samsung HM250JI (Firmware: HS100-08 ) btw. I'm aware that some
samsung drives have firmware bugs and tried the -F samsung and -F samsung2
flags with smartctl, but this didn't seem to change the values. Any heap or advice
would be greatly appreciated!

Cheers

You could try acoustic management. Keep watching your Load_Cycle_Count though. It might be that the clicks are still there but only less audible.

```

hdparm -M 128
hdparm -B 254 /dev/sda
hdparm -S 0 /dev/sda

```

If you don't hear any clicks and your Load_Cycle_Count doesn't increase anymore let's hope you are safe :)

If it works then just follow the ugly fix with the following changes.
ugly fix : [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

Making /etc/hdparm.conf look like this :

```

/dev/sda {
  apm = 254
  spindown_time = 0
  acoustic_management = 128
}

```

And making your 99-hdd-spin-fix.sh files look like this :
```

#/bin/sh
hdparm -M 128
hdparm -B 254 /dev/sda
hdparm -S 0 /dev/sda

```

Good luck and let us know

---

### Post by ubuntu_demon on 2007-11-06
> **kevykev said:**
> Ah, apparently, this is cause you need to mount it as a debug filesystem first

```
sudo mount -t debugfs none_debug /sys/kernel/debug

```

then you can run btrace. 

It produces a lot of output, the vast majority seems to be [kjournald], with a couple
of [swapper] and [firefox-bin] ones thrown in. I can post a sample if you need it

Thanks. It works for me too.

Now we can go and find top causes of disk activity.

---

### Post by chrischan on 2007-11-06
Hi everybody,

I have a VIA Epia board (EX10000EG) and a pretty new Western Digital 1 Terabyte WD10EACS drive. I am running Ubuntu 7.04, but I also tested with 7.10. No laptop mode, no fiddling with ACPI, just standard setup. Harddrive ACPI is disabled in BIOS. Nevertheless, can hear the drive load/unload every few seconds, my load cycle count is 5678 after 86 hours. The commonly mentioned fix "hdparm -B 254 /dev/hda" gives me

/dev/hda:
setting Advanced Power Management level to 0xFE (254)
HDIO_DRIVE_CMD failed: Input/output error

Can anyone comment on this latter issue or on the fact that I see this problem not on a laptop but on a desktop machine?

By the way,

mount -t debugfs none_debug /sys/kernel/debug
btrace (or blktrace, for that matter) /dev/hda

gives me:

BLKTRACESETUP: Inappropriate ioctl for device
Failed to start trace on /dev/hda

Best regards
Chrischan

---

### Post by ddrichardson on 2007-11-06
Apply the [fix]("http://blog.lynxworks.eu/?p=34") and then monitor it. If the drive is showing signs of failure then change it otherwise as long as you have a good backup routine you will be fine.

---

### Post by ubuntu_demon on 2007-11-06
> **chrischan said:**
> Hi everybody,

I have a VIA Epia board (EX10000EG) and a pretty new Western Digital 1 Terabyte WD10EACS drive. I am running Ubuntu 7.04, but I also tested with 7.10. No laptop mode, no fiddling with ACPI, just standard setup. Harddrive ACPI is disabled in BIOS. Nevertheless, can hear the drive load/unload every few seconds, my load cycle count is 5678 after 86 hours. The commonly mentioned fix "hdparm -B 254 /dev/hda" gives me

/dev/hda:
setting Advanced Power Management level to 0xFE (254)
HDIO_DRIVE_CMD failed: Input/output error

Can anyone comment on this latter issue or on the fact that I see this problem not on a laptop but on a desktop machine?


Your harddrive is known for aggressive power management. They use it as a selling point. They say :

> **Western Digital]
Reduced power consumption - By adjusting the rotational speed, using bigger data buffers, parking the drive's head, and optimizing how the drive seeks and caches data we have reduced the power consumption by up to 38 percent
[/quote]

In other words they try to park the head of the drive quickly which is atypical for the average desktop drive. That's probably why you suffer from the same problem.

Your harddrive is rated for 300.000 Load_Cycles. I got this from :
[http://www.wdc.com/en/library/sata/2879-701229.pdf](http://www.wdc.com/en/library/sata/2879-701229.pdf)

[QUOTE=chrischan said:**
> 
By the way,

mount -t debugfs none_debug /sys/kernel/debug
btrace (or blktrace, for that matter) /dev/hda

gives me:

BLKTRACESETUP: Inappropriate ioctl for device
Failed to start trace on /dev/hda

Best regards
Chrischan

How to help finding disk activity bugs with blktrace :
[http://ubuntuforums.org/showpost.php?p=3722850&postcount=375](http://ubuntuforums.org/showpost.php?p=3722850&postcount=375)
[http://ubuntuforums.org/showpost.php?p=3805320&postcount=479](http://ubuntuforums.org/showpost.php?p=3805320&postcount=479)

Please try and test the updated unofficial fix. Or you can try to use some Western Digital tool to turn down the aggressiveness of the power management. Maybe the tool you need is included on the Ultimate Boot cd-rom. See : [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by comfortablynumb on 2007-11-06
Thanks for the link, I'll make sure to do that

---

### Post by kevykev on 2007-11-06
> **ubuntu_demon said:**
> You could try acoustic management. 

Seems to have quietened a bit, but still happens every 10 or so minutes.

btw, i wrote a quick script to print top write hits from btrace output 
in a convienient form, incase it's useful (runs for 60 seconds, 
produces a file top.txt)

```

#!/bin/sh

time=60 #seconds
device=/dev/sda
bt_out=/tmp/bt-out
bt_procs=/tmp/bt-procs

sudo mount -t debugfs none_debug /sys/kernel/debug

sudo btrace -s -w ${time} ${device} | awk '$7 == "W" { print $5 }' > ${bt_out}

# Remove old file, if there
if [ -f ${bt_procs} ]; then
	rm ${bt_procs}
fi

# Iterate over btrace-output and translate pid's into process names
for line in `cat ${bt_out}`; do	
	if [ ${line} -eq 0 ]; then
		echo "swapper" >> ${bt_procs}
	else 
		echo `ps -p ${line} -o comm=` >> ${bt_procs}
	fi
done

# Count and sort
sort ${bt_procs} | uniq -c | sort -n -r > top.txt

sudo umount /sys/kernel/debug

```

looks like the culprits for me are the swapper, the file system journal
and pdflush. Seems to vary a bit tho, so maybe 60 seconds is too short.

I'll run it for a bit longer tomorro and see anyway

---

### Post by ubuntu_demon on 2007-11-06
> **kevykev said:**
> Seems to have quietened a bit, but still happens every 10 or so minutes.


You can also try the Ultimate Boot cd-rom with a bit of luck it includes the tool you need.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

You will have to check the website of your harddisk manufacturer to find out which tool you should use.

> **kevykev said:**
> 
btw, i wrote a quick script to print top write hits from btrace output 
in a convienient form, incase it's useful (runs for 60 seconds, 
produces a file top.txt)

```

#!/bin/sh

time=60 #seconds
device=/dev/sda
bt_out=/tmp/bt-out
bt_procs=/tmp/bt-procs

sudo mount -t debugfs none_debug /sys/kernel/debug

sudo btrace -s -w ${time} ${device} | awk '$7 == "W" { print $5 }' > ${bt_out}

# Remove old file, if there
if [ -f ${bt_procs} ]; then
	rm ${bt_procs}
fi

# Iterate over btrace-output and translate pid's into process names
for line in `cat ${bt_out}`; do	
	if [ ${line} -eq 0 ]; then
		echo "swapper" >> ${bt_procs}
	else 
		echo `ps -p ${line} -o comm=` >> ${bt_procs}
	fi
done

# Count and sort
sort ${bt_procs} | uniq -c | sort -n -r > top.txt

sudo umount /sys/kernel/debug

```

looks like the culprits for me are the swapper, the file system journal
and pdflush. Seems to vary a bit tho, so maybe 60 seconds is too short.

I'll run it for a bit longer tomorro and see anyway

Thanks for helping to get to the bottom of this.

---

### Post by comfortablynumb on 2007-11-06
Alright I applied the fix, I'm not sure if I require 255 or 244, but I put it on 255, It's still counting up from  85700 just a few minutes ago to  85709 now. urggg

Also on an interesting note I did your other command 

~$ sudo smartctl -d ata -a /dev/sda|grep Hours
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       3285

I can't believe my Laptop HD has 3285 hours on it :eek: :lolflag: I had to pull the receipt to see how old it was I thought was only 2 years but it's about 3.5 still thats alot of hours, I'll blame it on Windows install times :D

---

### Post by comfortablynumb on 2007-11-06
I changed it to 244, I tried to run sudo update-rc.d hdparm defaults to save the 244 but says it already exists...

Also I seen this mentioned on the Launchpad bug, would this work maybe?

[I]An alternative to the "99-hdd-spin-fix.sh" fix is to install and enable the package laptop-mode-tools,
then customize /etc/laptop-mode/laptop-mode.conf, setting

CONTROL_HD_POWERMGMT=1
[/I]

**EDIT**
**I just ran  hdparm -B 254 /dev/sda and the counting has stopped can this be the fix where after, I found that mentioned at [Thinkwiki]("http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking")**

---

### Post by DARKGuy on 2007-11-07
My question remains unanswered though...

Does this affect Desktop PCs too?...

---

### Post by ifixit on 2007-11-07
I've spent a fair bit of time today reading this thread, researching, experimenting, and taking a few notes.  I notice a few things:

First, is that nearly everyone is fixated on demonizing head unloading, but it doesn't *have to* be evil.  On a laptop machine, it can be a real advantage;  drop or jar a machine with the heads flying over top of Important Data, and you'll obviously have a much higher chance of losing that data than if the heads are parked somewhere intended to be mechanically secure (ie, unloaded).  Also, some drives seem able to perform additional power-saving tricks when the heads are unloaded, like reducing the rotational speed and other tricks that can't safely happen while the heads are near data (Bournouli Effect, etc).

Second, is that some seem to assume that just because the heads are unloaded, that the spindle spins down and stops.  This would quickly cause serious problems if it were happening a few hundred times per hour, but that doesn't seem to actually be the case -- I can put my ear up to the drive, and it *never* spins down in Ubuntu; it's simply far too busy of an operating system, poking this and reading that all the time, even with the filesystem mounted noatime, to let the disk idle long enough to spin down on its own accord.  (Which is itself a problem, particularly on a battery-operated computer; the drive really should spin down at some point on a seemingly-idle system, and should then stay that way for as long as possible.)

The real problem is that the heads seem to be unloading far too often, not that it happens at all (after all, we want them unloaded if the drive isn't going to be used for some time).  When listening closely (and comparing what I hear to the output of smartctl), the Hitachi HTS541616J9AT00 in my Inspiron 6000 unloads its heads immediately after every disk access, *unless* there are multiple accesses within a few seconds (which seems to cause the drive to back off a bit and be less aggressive for a short period of time).

This means that in its default state, with Gutsy idling with compiz, Thunderbird, and Firefox with several tabs, the heads do a load-unload cycle several times per minute (7, on average, according to my logs) without me touching the keyboard or mouse.

Maybe it's an Ubuntu problem, maybe it's a hardware problem.  Perhaps somewhat unpopularly, I suspect both -- a computer system is, after all, comprised of both hardware and software.  And, this particular system is eating itself rapidly.

Previous to Gutsy this drive had been running since May exclusively with Vista and (typically) at least half a dozen applications open.  In fact, with only about 30 hours (out of 3800 power-on hours total) in Ubuntu, this drive had already accumulated just over 100,000 cycles.

Obviously, the vast majority of these cycles belong to Vista.  So, at the rate Vista burns this drive (26 cycles per hour), it will take about three total years to hit the magic 600,000 cycle mark.  This seems to be a dreadfully short lifespan for such an otherwise well-behaved drive, but isn't horrific.

But, Gutsy allows the heads to undergo a load-unload cycle 420 times per hour.  Extrapolated by 600000/(420*24*365.25), this means that it will take 0.16 years (23 days!) to expend this drive when running Gutsy.

This is, of course, completely bloody absurd.  No, scratch that - it's simply insulting.  It may as well set the CPU on fire at the same time.  In fact, I'd prefer it - at least my data and OS installations would stand a chance at surviving if it's only a small fire.   :mad:

So, I've preemptively set APM high using hdparm.  I've found that this drive responds to values greater than 192 by substantially reducing load cycles, seemingly the same as a setting of 254, but it's too early to tell for sure if they're truly equal.

But I -want- the heads to unload when they can.  If the drive is good for 600k load cycles (it probably is) and that function can help save my data in the event of physical trauma (it almost certainly will) and let my battery live longer (for free!), then I think with proper management the system (which again includes both hardware and software) should be able to have a sustainable design life of at least 5 years, maybe more, while still keeping the data reasonably safe, and saving power to boot.

23 days, though.  Wow.

I will continue to experiment with different things.  My next move is to look into the various bits that are adjusted by putting the kernel into laptop mode, and attempting to find a decent way to balance this corner of the system between longevity, durability, and battery life.

---

### Post by infra_red_dude on 2007-11-07
> **ubuntu_demon said:**
> If you don't hear any clicks and your Load_Cycle_Count doesn't increase anymore let's hope you are safe :)
As I've said before, even I haf this problem. I had this in feisty, now am on guyst and the Load cycle count increases.

However, my case is strange. I haf a Seagate 80GB IDE drive (NOT SATA) and I also DO NOT hear any clicks but the Load Cyle Count has been on the rise. I'm fully confused. I thot after upgrading to Gutsy this problem would be solved. But No :(

---

### Post by ubuntu_demon on 2007-11-07
> **infra_red_dude said:**
> As I've said before, even I haf this problem. I had this in feisty, now am on guyst and the Load cycle count increases.

However, my case is strange. I haf a Seagate 80GB IDE drive (NOT SATA) and I also DO NOT hear any clicks but the Load Cyle Count has been on the rise. I'm fully confused. I thot after upgrading to Gutsy this problem would be solved. But No :(

If you are worried then you could apply the ugly fix or if that doesn't work then you could use the Ultimate Boot cd-rom to tell your drive to not use too aggressive power management. (if you use the latter approach you have to make sure that you use the tool your harddisk manufacturer recommends)

ugly fix :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

---

### Post by ubuntu_demon on 2007-11-07
> **DARKGuy said:**
> My question remains unanswered though...

Does this affect Desktop PCs too?...

No unless you have a laptop-like harddrive such as an external harddrive cage with a 2.5" laptop harddrive inside or a harddrive which uses power management as a big selling point such as the Western Digital WD Caviar GP aimed at Power Saving.

---

### Post by ubuntu_demon on 2007-11-07
> **ifixit said:**
> I've spent a fair bit of time today reading this thread, researching, experimenting, and taking a few notes.  I notice a few things:


thanks for your help to get to the bottom of this. 

You should read :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216)

> **ifixit said:**
> 
First, is that nearly everyone is fixated on demonizing head unloading, but it doesn't *have to* be evil.  On a laptop machine, it can be a real advantage;  drop or jar a machine with the heads flying over top of Important Data, and you'll obviously have a much higher chance of losing that data than if the heads are parked somewhere intended to be mechanically secure (ie, unloaded).  Also, some drives seem able to perform additional power-saving tricks when the heads are unloaded, like reducing the rotational speed and other tricks that can't safely happen while the heads are near data (Bournouli Effect, etc).


I know. IMHO parking the harddisk head quickly is particularly useful when on battery because it saves power and your laptop has the highest chance to experience bumps when on battery.

> **ifixit said:**
> 
Second, is that some seem to assume that just because the heads are unloaded, that the spindle spins down and stops.  This would quickly cause serious problems if it were happening a few hundred times per hour, but that doesn't seem to actually be the case -- I can put my ear up to the drive, and it *never* spins down in Ubuntu; it's simply far too busy of an operating system, poking this and reading that all the time, even with the filesystem mounted noatime, to let the disk idle long enough to spin down on its own accord.  (Which is itself a problem, particularly on a battery-operated computer; the drive really should spin down at some point on a seemingly-idle system, and should then stay that way for as long as possible.)


The Load_Cycle_Count increases both with spinning down/spinning up and parking/unparking of the head.

Luckily spinning down doesn't seem to happen too often according to the people who have responded in this thread and to the bug report(s).

> **ifixit said:**
> 
The real problem is that the heads seem to be unloading far too often, not that it happens at all (after all, we want them unloaded if the drive isn't going to be used for some time).  When listening closely (and comparing what I hear to the output of smartctl), the Hitachi HTS541616J9AT00 in my Inspiron 6000 unloads its heads immediately after every disk access, *unless* there are multiple accesses within a few seconds (which seems to cause the drive to back off a bit and be less aggressive for a short period of time).

This means that in its default state, with Gutsy idling with compiz, Thunderbird, and Firefox with several tabs, the heads do a load-unload cycle several times per minute (7, on average, according to my logs) without me touching the keyboard or mouse.

Maybe it's an Ubuntu problem, maybe it's a hardware problem.  Perhaps somewhat unpopularly, I suspect both -- a computer system is, after all, comprised of both hardware and software.  And, this particular system is eating itself rapidly.


This is both a problem of too aggressive power management set by (laptop) BIOS or (laptop) harddrive firmware AND too much unnecessary disk activity. 

> **ifixit said:**
> 
Previous to Gutsy this drive had been running since May exclusively with Vista and (typically) at least half a dozen applications open.  In fact, with only about 30 hours (out of 3800 power-on hours total) in Ubuntu, this drive had already accumulated just over 100,000 cycles.

Obviously, the vast majority of these cycles belong to Vista.  So, at the rate Vista burns this drive (26 cycles per hour), it will take about three total years to hit the magic 600,000 cycle mark.  This seems to be a dreadfully short lifespan for such an otherwise well-behaved drive, but isn't horrific.

But, Gutsy allows the heads to undergo a load-unload cycle 420 times per hour.  Extrapolated by 600000/(420*24*365.25), this means that it will take 0.16 years (23 days!) to expend this drive when running Gutsy.

This is, of course, completely bloody absurd.  No, scratch that - it's simply insulting.  It may as well set the CPU on fire at the same time.  In fact, I'd prefer it - at least my data and OS installations would stand a chance at surviving if it's only a small fire.   :mad:


If you would use your laptop 8 hours per day it would come to 178 days. But it is indeed absurd.

IMHO the Load_Cycle_Count shouldn't increase more than 22 per hour :

If you would use your laptop harddrive for 24 hours per day with 22 Load_Cycles per hour you wouldn't reach 600.000 in three years : 22 * 24 * 365 * 3 < 600.000 

If you would use your laptop harddrive for 12 hours per day with 22 Load_Cycles per hour you wouldn't reach 300.000  in three years : 22 * 12 * 365 * 3 < 300.000

> **ifixit said:**
> 
So, I've preemptively set APM high using hdparm.  I've found that this drive responds to values greater than 192 by substantially reducing load cycles, seemingly the same as a setting of 254, but it's too early to tell for sure if they're truly equal.


254 should disable parking/unparking on all drives.
values between 128 and 254 (including 128 and excluding 254) don't spin down the drive (unless you set the spindown value) and might park/unpark the drive.
How often parking/unparking will happen is drive independent. Maybe your drive doesn't park/unpark starting at 192.

> **ifixit said:**
> 
But I -want- the heads to unload when they can.  If the drive is good for 600k load cycles (it probably is) and that function can help save my data in the event of physical trauma (it almost certainly will) and let my battery live longer (for free!), then I think with proper management the system (which again includes both hardware and software) should be able to have a sustainable design life of at least 5 years, maybe more, while still keeping the data reasonably safe, and saving power to boot.

23 days, though.  Wow.

I will continue to experiment with different things.  My next move is to look into the various bits that are adjusted by putting the kernel into laptop mode, and attempting to find a decent way to balance this corner of the system between longevity, durability, and battery life.

IMHO Ubuntu should make fixing unnecessary disk activity bugs a high priority. We can all help finding unnecessary disk activity bugs.
IMHO Ubuntu should override too aggressive power management and make this also a high priority.
IMHO smartmontools should be installed on default. smartd should run on default with sane settings hooking into a notifier to notify users. At least some people who were affected might be warned in time to buy a new harddrive. Maybe this should be a Hardy goal ?

see also my next post :
[http://ubuntuforums.org/showpost.php?p=3722838&postcount=373](http://ubuntuforums.org/showpost.php?p=3722838&postcount=373) where I quote myself from :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/102](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/102)

---

### Post by ubuntu_demon on 2007-11-07
From [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/102](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/102) :

[quote=ubuntu_demon]
* (laptop) harddisk firmwares and (laptop) BIOSes might set too aggressive power management (operating system independent)
* The operating system and the applications running on it might cause too much unnecessary disk activity (multiple operating systems are affected. at least a couple of Linux distributions seem to have the same problem)
The result : is rapid parking/unparking cycles of the harddisk's head (a rapidly increasing Load_Cycle_Count).

IMHO this is the way Ubuntu should fix this :

IMHO Ubuntu should make fixing unnecessary disk activity bugs a high priority. We can all help finding unnecessary disk activity bugs.
IMHO Ubuntu should override too aggressive power management and make this also a high priority.
IMHO smartmontools should be installed on default. smartd should run on default with sane settings hooking into a notifier to notify users. At least some people who were affected might be warned in time to buy a new harddrive. Maybe this should be a Hardy goal ?

Laptop-mode with sane default settings can override too aggressive power management settings and can also prevent some unnecessary disk activity. Maybe Ubuntu should enable laptop-mode with sane default settings for laptops. What do you guys think ? What are sane default settings ?

Some suggestions for laptop-mode parameters :
[http://www.suselinuxsupport.de/wikka.php?wakka=HowToSaveYourLaptopHD](http://www.suselinuxsupport.de/wikka.php?wakka=HowToSaveYourLaptopHD)
[http://mishameteo.blogspot.com/2007/10/ubuntu-default-acpi-settings-decreases.html](http://mishameteo.blogspot.com/2007/10/ubuntu-default-acpi-settings-decreases.html)
[http://bbs.archlinux.org/viewtopic.php?pid=294594#p294594](http://bbs.archlinux.org/viewtopic.php?pid=294594#p294594)
[http://forum.mandriva.com/viewtopic.php?p=393299&sid=46e5b548a1693fcf6f7e15316f904360#393299](http://forum.mandriva.com/viewtopic.php?p=393299&sid=46e5b548a1693fcf6f7e15316f904360#393299)
[https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/63](https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/63)
[http://www.nabble.com/-Cooker--Laptop-hard-drives-and-unnecessarily-high-Load_Cycle_Count-t4730198.html](http://www.nabble.com/-Cooker--Laptop-hard-drives-and-unnecessarily-high-Load_Cycle_Count-t4730198.html)

Regarding smartd hooking into a notifier. I'm thinking of the following example situations when to warn a user :
* if the Load_Cycle_Count is increased with more than 22 cycles per hour (22 * 24 * 365 * 3 < 600.000) (to find people who are still affected)
* if smartctl assesses your harddrive as not healthy
* if more than X errors were found during the last self-test
* if Load_Cycle_Count's WORST is within Y of Load_Cycle_Count's THRESHOLD

I found the following wiki pages with similar ideas :
[https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/SMARTMonitoring](https://wiki.ubuntu.com/UbuntuDownUnder/BOFs/SMARTMonitoring)
[https://wiki.ubuntu.com/DiskMonitoring](https://wiki.ubuntu.com/DiskMonitoring)
[/quote]

---

### Post by ubuntu_demon on 2007-11-07
**btrace howto**

If you want to help find unnecessary disk activity bugs here's how to start.

```

sudo aptitude install blktrace
sudo mount -t debugfs none_debug /sys/kernel/debug
sudo /etc/init.d/sysklogd stop
sudo su
echo 1 > /proc/sys/vm/block_dump
exit
sudo btrace /dev/sda

```

optionally open a second terminal and type :
```

sudo lm-profiler

```
press control-C after the 600 seconds have elapsed (you don't want to temper with default settings because that might hide bugs)


open a third terminal and keep typing dmesg (can't this be done easier?) :
```

dmesg

```

once in a while you might want to clear your dmesg :
```

sudo dmesg -c

```

once you are done :
```

sudo su
echo 0 > /proc/sys/vm/block_dump
sudo umount /sys/kernel/debug
sudo /etc/init.d/sysklogd start

```

**More information :**

[B]This explanation continues here : 
[http://ubuntuforums.org/showpost.php?p=3805320&postcount=479](http://ubuntuforums.org/showpost.php?p=3805320&postcount=479)[/B]

[https://launchpad.net/ubuntu/+bug/17878/comments/31](https://launchpad.net/ubuntu/+bug/17878/comments/31)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/100](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/100)
```

cd /usr/share/doc/blktrace
gunzip blktrace.pdf.gz
evince blktrace.pdf

```

```

man btrace

```

**[COLOR="Red"]don't report pdflush, kjournald, kcryptd, swapper [/COLOR]** see also [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/100](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/100)

---

### Post by infra_red_dude on 2007-11-07
> **comfortablynumb said:**
> **EDIT**
**I just ran  hdparm -B 254 /dev/sda and the counting has stopped can this be the fix where after, I found that mentioned at [Thinkwiki]("http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking")**
How will this work on /dev/**sda**?? Is you IDE drive mounted as /dev/sdx?? My IDE drive is mounted as /dev/**hda**

---

### Post by ddrichardson on 2007-11-07
Well, obviously you need the correct device, if its worked with 254 we can assume it's a sata drive.

---

### Post by Fr@nKy on 2007-11-07
Guys just tell me (I'm lost os this trhead)... Is laptop-mode the guilty for this "bug"? If so when is it enabled? On a clena install on a laptop it comes disabled right? What if I switch to battery (turn off the AC), or start Ubuntu already using only battery power, will laptop-mode be used? Or laptop-mode is something that can only be enabled manually??

---

### Post by comfortablynumb on 2007-11-07
I can not figure out for the life of me why it's SDA, It's not an SATA type drive. If I go to device manager it's being recognized as SCSI

Same with my DVD drive, maybe I have chipset driver issue (Intel 82801CAM), I checked Thinkwiki, they state "This is a Intel ICH3-M I/O Controller Hub, This chipset is supported by recent 2.4 and 2.6 kernels"

Actually it's still not stopped completely. I've been up an hour it's gone up by one count it was 85758 and now it's 85759, but I think that's probably normal from shutting down and starting back up.

---

### Post by Fr@nKy on 2007-11-07
Help! I'm afraid of damaging my laptop :(

I'll install Ubuntu and see if it makes a lot of unload cycles... If so, what are the best HARD FIXES?

---

### Post by houstonbofh on 2007-11-07
> **Fr@nKy said:**
> Help! I'm afraid of damaging my laptop :(

I'll install Ubuntu and see if it makes a lot of unload cycles... If so, what are the best HARD FIXES?
From easiest...  Pick one.

1) Do not enable laptop mode.

2) Set hdparm to 254

3) Use hard drive tools to set drive to not use aggressive power management in the drive BIOS, and in your motherboard BIOS.

---

### Post by Fr@nKy on 2007-11-07
> **houstonbofh said:**
> From easiest...  Pick one.

1) Do not enable laptop mode.

2) Set hdparm to 254

3) Use hard drive tools to set drive to not use aggressive power management in the drive BIOS, and in your motherboard BIOS.

Ok that was my first option ;) BTW why is 254 better than 255?

---

### Post by Fr@nKy on 2007-11-07
And also... what's the best way to set hdparm -B to a certain value?? A script? Is is possible to change it directly on ACPI configurations so that it always boot with the same configuration?

And I've see hdparm -B but also some people talk about  hdparm -X (where X is another letter). Do I only need to change B?

EDIT:

sudo hdparm -B 254 /dev/sda
sudo hdparm -S 0 /dev/sda

I've see Ubuntu Demon recomending these settings... What's the purpose of hdparm -S?

---

### Post by lordof7 on 2007-11-07
Fr@nky and others who may be lost:

**Am I affected by this issue????** 
The answer is yes if you have a latop hard disk drive (hdd), or possibly other hdds with aggressive energy saving settings (like the Western Digital green products), and you have a default (X)Ubuntu installation. (I assume that this is true for Kubuntu as well, but I don't know for sure.)  

Most desktop hdd's are probably not affected.  However, a laptop hdd in a desktop would most likely be affected.

My understanding is that rapidly increasing Load_Cycle_Count does not depend on laptop-mode being active.  I believe laptop-mode is disabled by default (not sure about newest version.)  The (separate) issue with laptop-mode is that the battery setting for harddrive power management is VERY aggressive.

To know for sure if this issue affects you, follow these instructions to determine your S.M.A.R.T. readout.
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)
Note that you want to look at the rate the Load_Cycle_Count is increasing over time.  You should read on if you see a count increase of more than 1 per minute.

  

**The Issue:**
The issue is caused by a complication of behaviors, all of which contribute.  In my opinion, its not technically a bug, because all of these behaviors separately are intentional.  However, with laptop hard drives, these behaviors combine to form a highly undesirable behavior to many (but not all!)  These seem to be the behaviors involved:

1.  Laptop hard drive BIOS and/or laptop BIOS sets aggressive hdd settings to protect the physical drive from damage due to impact (dropping or bumping the laptop), as well as to save battery power.  These include parking/unparking the hdd heads. Jarring the hdd hard enough when the heads are over the platters may cause the heads to actually hit the platters, damaging them and causing data loss.  Keeping the heads in a parked state prevents this.  Therefore, laptop hdd's often park the heads after a short period of disk inactivity.  Also included is disk spindown, which saves battery power.  

2. (X) Ubuntu (and other distros)  does not override hardware settings by default.  Therefore, the hdd manufacturer settings are not modified normally.  This means that the manufacturer settings apply whether or not the laptop is plugged in, or on ac power, or in standby.  The manufacturer settings apply for laptops, desktops, servers, anything running a default Ubuntu install.  Enabling laptop-mode or installing laptop-mode-tools may modify these behaviors, but that would require user intervention.

3.  Linux based distros constantly access the hdd.  Some, but surely not all, processes include file system journaling (once every 5 sec. in ext3), access time logging,  file indexing, acpid output, thunderbird, etc.  In many cases these are desired behaviors.  File system journaling helps protect the integrity of your file system, and thus, your data.  Indexing has to do with file searching.  Beagle, for instance, is a real-time indexer, which allows constant hdd access.  Thunderbird may be accessing the hdd to check for new messages.

The problem is that these behaviors together (really, 1 and 3) are causing the issue.  Your hdd parks the heads  after a hdd access to protect the disk.  Very soon thereafter,  the heads unpark to access the disk (eg. ext3 journals every 5 sec).  So basically its a back-and-forth battle for control of the heads between the hdd/laptop BIOS and the OS.  Park to protect, unpark to access, park to protect, unpark to access.  This issue is NOT limited to Ubuntu.  Similar behavior has been observed with other linux based distros, and Windows OS's!  It does appear that the rate of Load_Cycle_Count increase on affected systems can be higher in linux based OS's (one comparison from ifixit:  ubuntu = 420/hr, vista = 26/hr.  Note that the rate increase under linux based systems does vary - best to check your own and decide if its a problem to you.)  

The problem with "fixing this bug" in Ubuntu is that decreasing the high rate of Load_Cycle_Count increase may require sacrificing desired functionality.  One may want to sacrifice drive life to have solid file system integrity.  Or, somebody may want aggressive head parking because that person is rough with their laptop.  And, somebody may want to preserve drive life by preventing head loading unloading.  In a more configurable distro (like Gentoo), its up to the user to determine what he/she wants and therefore, how to setup the OS.  However, Ubuntu is more of a "works out of the box" distro.  The tough thing for Ubuntu is that it must "work out of the box" for many different systems.  IMHO, maybe some usage questions during install could help customize the install for the particular computer.  Something like "User, are you installing Ubuntu on a laptop?"  If yes, allow aggressive settings on battery mode, but not on ac mode, or something like that. 

**The Ugly Fix**
If you wish to prevent aggressive hdd settings, and the resulting rapid increase in Load_Cycle_Count that may indicate premature hdd wear and tear, follow the directions here:
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

Anyone can feel free to correct this and repost it or wiki it or something, so that people can know whats going on without wading through 38 pages of posts.  (Although correcting any mistakes would be really important, then.)  Clearly, this post has been a collection of information in the previous 38 pages, as well as from the internet, and many others.  Ubuntu_demon is really to be commended for gathering information and fixes, and updating the bugtracking on this issue.

---

### Post by Fr@nKy on 2007-11-07
Thanks a lot... So that Ugly Fix Tutorial is the best currently around?... I think there should be a one post sticky where a tutorial would be maintained as the (almost) official solution to the problema and update as more info is discovered.

---

### Post by Fr@nKy on 2007-11-07
One more thing... how can I revert the tutorial ([http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)) if I want to??

---

### Post by ubuntu_demon on 2007-11-07
> **Fr@nKy said:**
> One more thing... how can I revert the tutorial ([http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)) if I want to??

You shouldn't apply any unofficial ugly fixes if you don't understand them and don't understand how to revert them. 

Also you need to make sure whether you are affected by the issue before applying any fixes.

If you need to revert the “ugly fixes” you need to edit your /etc/hdparm.conf and remove the lines you added (unless an official fix would set the same). You would also need to remove the 99-hdd-spin-fix.sh files.

---

### Post by ubuntu_demon on 2007-11-07
> **Fr@nKy said:**
> Thanks a lot... So that Ugly Fix Tutorial is the best currently around?... I think there should be a one post sticky where a tutorial would be maintained as the (almost) official solution to the problema and update as more info is discovered.

Right now IMHO it's the best one around because it's relatively straightforward.

IMHO a better (official?) fix might be through laptop-mode. Maybe it's possible to find sane defaults which work for everybody. See :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/102](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/102)

---

### Post by ubuntu_demon on 2007-11-07
> **lordof7 said:**
> Fr@nky and others who may be lost:
...........................
...........................
............................
Anyone can feel free to correct this and repost it or wiki it or something, so that people can know whats going on without wading through 38 pages of posts.  (Although correcting any mistakes would be really important, then.)  Clearly, this post has been a collection of information in the previous 38 pages, as well as from the internet, and many others.  Ubuntu_demon is really to be commended for gathering information and fixes, and updating the bugtracking on this issue.

Thanks :). 

Thanks for this great explanation. Thanks for helping people!

> **lordof7 said:**
> 
...............
Similar behaviour has been observed with other linux based distros, and Windows OS's!  It does appear that the rate of Load_Cycle_Count increase is much higher in linux based OS's (from ifixit:  ubuntu = 420/hr, vista = 26/hr).  
..............


You might want to improve this part of your explanation a little bit.

Not everyone is affected and not everyone is affected as heavily as some (it's different for everybody). You are making it sound a little bit as if everybody who is affected will have a Load_Cycle_Count increase of 420 per hour which is not the case.

---

### Post by ubuntu_demon on 2007-11-07
> **Fr@nKy said:**
> 
sudo hdparm -B 254 /dev/sda
sudo hdparm -S 0 /dev/sda

I've see Ubuntu Demon recomending these settings... What's the purpose of hdparm -S?

"hdparm -S 0" makes sure your drive doesn't spin down. It's not needed for "hdparm -B" values between 128 and 254 (including those numbers). But I included it just in case (for example if people manually set the spin down time during a session).

---

### Post by ubuntu_demon on 2007-11-07
> **Fr@nKy said:**
> Ok that was my first option ;) BTW why is 254 better than 255?

Because 255 is officially not defined and not all harddrives support it.

---

### Post by ubuntu_demon on 2007-11-07
> **houstonbofh said:**
> From easiest...  Pick one.

1) Do not enable laptop mode.

2) Set hdparm to 254

3) Use hard drive tools to set drive to not use aggressive power management in the drive BIOS, and in your motherboard BIOS.

Right now people probably shouldn't enable laptop mode with the laptop-mode defaults unless they know what they are doing. But not enabling laptop-mode doesn't guarantee that you don't suffer from the issue because both (laptop) harddrive firmware and laptop BIOS might set too aggressive power management settings. Not everyone is affected and not everyone is affected as heavily as some (it's different for everybody).

People should first check whether they are affected. If they are affected then they could either apply the ugly fix (2) OR (3) use the tool recommended by their manufacturer (which might be included on the ultimate boot cd-rom) OR wait for an official fix if they are not affected very heavily.

---

### Post by ddrichardson on 2007-11-07
One count per hour is fine.

---

### Post by comfortablynumb on 2007-11-07
> **ddrichardson said:**
> One count per hour is fine.

Yea I don't mind that to much, but with it showing SDA when it's not an SATA drive, will this be a problem?

---

### Post by floke on 2007-11-07
Actually - given the hours count - the load does seem high. I was going by the original 2 year figure, and my laptop is about 1 year old and has around half the load cycle. I don't have this issue so assumed that all was well in the ratios. Sorry. 

But given that the HD's are supposed to take around 600,000 load cycles, 80-90,000 in 3.5 years seems ok to me.

---

### Post by comfortablynumb on 2007-11-07
> **floke said:**
> Actually - given the hours count - the load does seem high. I was going by the original 2 year figure, and my laptop is about 1 year old and has around half the load cycle. I don't have this issue so assumed that all was well in the ratios. Sorry. 

But given that the HD's are supposed to take around 600,000 load cycles, 80-90,000 in 3.5 years seems ok to me.

No reason to be sorry :) I appreciate any help I can get on this issue.

---

### Post by ddrichardson on 2007-11-07
I think the main issue here is that many people are being unduly alarmed by something that is being unfairly presented as an Ubuntu "bug". It happens in Windows too and given the desktop dominance of Windows were it a major issue then we'd be seeing borked drives all over the place.

Load unload cycles are a method of preventing damage to data regions by landing the heads in a non-data area and many hard disk manufacturers don't even employ this system.

If the counts are no longer increasing at a high rate and the drive displays no signs of failure such as bad sectors or mechanical noises then there is nothing to worry about. Drives are mechanical components and one of the only moving parts in a computer hence they can fail.

The quoted 60,000 figure is also not a flat rate. Its not a case that the drive will fail as soon as it hits 60,000 - its a figure provided by manufacturer at the point that 50% of drives begin to display signs of failure. Also the failure beyond this point is not linear.

As for this issue with IDE appearing as /dev/sda this is a result of a recent change in kernel device naming as I understand it - theres an explanation [here]("http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce").

---

### Post by Fr@nKy on 2007-11-07
So this is something that happens because Ubuntu (btw is there any safe distro??) chooses not to override hardware defaults (like Windows does). Because of that if the hardware has a bad power management implementation (btw any brands "blacklisted"?) it will not be stopped by the OS from doing something wrong...

---

### Post by houstonbofh on 2007-11-07
> **ubuntu_demon said:**
> But not enabling laptop-mode doesn't guarantee that you don't suffer from the issue because both (laptop) harddrive firmware and laptop BIOS might set too aggressive power management settings.
This is quite frightening.  So if aggressive power management is called for in BIOS, it will happen in a stock system on A/C power?
> **Fr@nKy said:**
> So this is something that happens because Ubuntu (btw is there any safe distro??) chooses not to override hardware defaults (like Windows does). Because of that if the hardware has a bad power management implementation (btw any brands "blacklisted"?) it will not be stopped by the OS from doing something wrong...
Windows also appears to have this problem.  However, since Windows does not touch the hard drive as often, it does not look as bad.  However, **it seems this problem is effecting all operating systems to some extent.**

---

### Post by kevykev on 2007-11-07
Hi All,

After examining disk usage, I found that a lot of the disk activity
is caused by journaling and swapping. I experimented and found
a few ways to reduce load cycles. On my machine i got it down
to about 1 per minute (prolly around 3 years of battery use based 
on 9 hour days, 7 days a week on a 600,000 cycle hard disk) 
without needing to disable hard disk power management.

Here's what i did:

In /etc/sysctl.conf add

```

vm.swappiness=10

```

This reduces the systems tendancy to swap out rarely used pages.
It should be ok to do this if your laptop has plenty of RAM. Lowering
the swappiness also has another effect: when the kernel issues
a write, it is sometimes put in a page in memory, for the pdflush
process to write out at a later time. Apparently these "dirty pages"
are aggressively swapped, so reducing the swappiness should abate
this somewhat.

The second change I made is to reduce the commit interval for the
ext3 filesystem and stop the the filesystem keeping track of access
times. In /etc/fstab add the following options to the root filesystem

```

noatime,commit=60

```

The commit=60 means that metadata will only be committed every
60 seconds (default is 5), so in theory up to 60 seconds of metadata
could be lost in the event of a crash. However, in linux, the default 
interval for pdflush is also 60 seconds. This means that, by default,
if the system crashes up to 60 seconds of data could also be lost 
anyway, so i guess it's not such a big difference (?).

Note, however, the noatime will affect apps that rely on atime (eg. mutt).

Finally, I set the reduced the Index Delay to 10 minutes (600) in 
Indexing Preferences

I dont know if this will work so well on other systems, but it's helped
on mine. I wonder if setting the ext3 journaling mode to writeback 
would further reduce usage?

---

### Post by floke on 2007-11-07
I think the figure is 600,000 - not 60,000 - so you're a long way off it yet!

---

### Post by comfortablynumb on 2007-11-07
> **ddrichardson said:**
> 
As for this issue with IDE appearing as /dev/sda this is a result of a recent change in kernel device naming as I understand it - theres an explanation [here]("http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce").

Thanks for that link that explains a lot.

> **ddrichardson said:**
> I think the main issue here is that many people are being unduly alarmed by something that is being unfairly presented as an Ubuntu "bug". It happens in Windows too and given the desktop dominance of Windows were it a major issue then we'd be seeing borked drives all over the place.% of drives begin to display signs of failure. Also the failure beyond this point is not linear. 

O I'm sure it is a problem with Windows too, I had a Compaq Armada M700 that in one year alone went through three hard drives. This Seagate I'm using now was in that laptop for a couple of months before the mobo died.

---

### Post by djoser on 2007-11-07
> **ubuntu_demon said:**
> 
2) make sure the file contains the following 2 lines (fix it if you have PATA HDD):
```

#!/bin/sh
hdparm -B 254 /dev/sda
hdparm -S 0 /dev/sda

```


I have a  PATA HDD. I do not understand  what to change? Please tell me! :)

---

### Post by houstonbofh on 2007-11-07
> **djoser said:**
> I have a  PATA HDD. I do not understand  what to change? Please tell me! :)
In that case, are you sure you have the problem?  Have you run smartctl to see the count?  If so, sata is sda, and pata is hda.

---

### Post by djoser on 2007-11-08
> **houstonbofh said:**
> In that case, are you sure you have the problem?  Have you run smartctl to see the count?  If so, sata is sda, and pata is hda.

Okay, thanks. Yes, Im almost sure I have this problem. The load cycle count is increasing to fast. But using 'sda' everywhere seems to have fixed the problem. Isn't that weird?

---

### Post by ubuntu_demon on 2007-11-08
> **Fr@nKy said:**
> So this is something that happens because Ubuntu (btw is there any safe distro??) chooses not to override hardware defaults (like Windows does). Because of that if the hardware has a bad power management implementation (btw any brands "blacklisted"?) it will not be stopped by the OS from doing something wrong...

I'm not sure whether windows overrides aggressive power management settings of harddrives (set by BIOS or laptop harddrive firmware). That's why I typed something along the lines of : "windows ***might*** override these settings" in my explanations of the issue.

It ***might*** be the case that window generates a bit less disk activity because there's no journalling. It ***might*** be the case that people use different applications on the two platforms (ubuntu and windows).

---

### Post by ubuntu_demon on 2007-11-08
> **houstonbofh said:**
> This is quite frightening.  So if aggressive power management is called for in BIOS, it will happen in a stock system on A/C power?


Desktop BIOSes probably won't set too aggressive power management settings on the drive.

Some laptops are affected by too aggressive (harddrive) power management settings  set by BIOS or laptop harddrive firmware. Some laptops are more affected than others. Too aggressive power management will set the head to park too quickly. Too much disk activity  (for example accessing the disk every X seconds) will unpark the head too quickly. The problem is a combination of power management and disk activity resulting in too much parking/unparking. Too much parking/unparking might cause your harddrive to reach a Load_Cycle_Count of 600.000 before three years are over.

I got about 1 Load_Cycle per minute on my previous harddrive (Power_On_Hours was not a nice value so it's a rough estimate)
I got more than 1 Load Load_Cycle per minute on my current harddrive (no need to test for the exact number)

I haven't changed any BIOS settings from the defaults. There is a power saving option in my BIOS which is enabled by default. I haven't investigated further whether my BIOS is the culprit or my harddrive firmware is the culprit.

I could use WD's tool (probably included on the ultimate boot cd-rom) to turn down power management on my drive  and if the result isn't good enough I could also turn off the power saving option in my BIOS. But I don't want to do that because I want to see a proper fix which works for everybody (I don't want to explain 10 different tools and 20 different BIOSes).

---

### Post by ubuntu_demon on 2007-11-08
> **kevykev said:**
> Hi All,

After examining disk usage, I found that a lot of the disk activity
is caused by journaling and swapping. I experimented and found
a few ways to reduce load cycles. On my machine i got it down
to about 1 per minute (prolly around 3 years of battery use based 
on 9 hour days, 7 days a week on a 600,000 cycle hard disk) 
without needing to disable hard disk power management.

Here's what i did:

In /etc/sysctl.conf add

```

vm.swappiness=10

```

This reduces the systems tendancy to swap out rarely used pages.
It should be ok to do this if your laptop has plenty of RAM. Lowering
the swappiness also has another effect: when the kernel issues
a write, it is sometimes put in a page in memory, for the pdflush
process to write out at a later time. Apparently these "dirty pages"
are aggressively swapped, so reducing the swappiness should abate
this somewhat.

The second change I made is to reduce the commit interval for the
ext3 filesystem and stop the the filesystem keeping track of access
times. In /etc/fstab add the following options to the root filesystem

```

noatime,commit=60

```

The commit=60 means that metadata will only be committed every
60 seconds (default is 5), so in theory up to 60 seconds of metadata
could be lost in the event of a crash. However, in linux, the default 
interval for pdflush is also 60 seconds. This means that, by default,
if the system crashes up to 60 seconds of data could also be lost 
anyway, so i guess it's not such a big difference (?).

Note, however, the noatime will affect apps that rely on atime (eg. mutt).

Finally, I set the reduced the Index Delay to 10 minutes (600) in 
Indexing Preferences

I dont know if this will work so well on other systems, but it's helped
on mine. I wonder if setting the ext3 journaling mode to writeback 
would further reduce usage?

I was also experimenting along those lines. I'm keeping noatime because I don't rely on applications which use atime. 

IMHO it's probably safer to use ordered journalling than writeback so you probably shouldn't touch that.

commit=X settings should probably be left to be set by laptop-mode (once we find sane defaults). If you use commit=X you probably should also set /proc/sys/vm/dirty_writeback_centisecs to the same new interval (in hundreds of seconds)

**I don't want to advice people to mount their partitions with commit=X at this point.** This should probably be done through laptop-mode taking Bart Samwell's comment in consideration. Doing it with laptop-mode is safer because AFAIK it can undo these kind of settings automatically before the power of the battery runs out.

See :
[http://www.ussg.iu.edu/hypermail/linux/kernel/0208.1/0464.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0208.1/0464.html)
[http://linux.derkeiler.com/Newsgroups/comp.os.linux.portable/2005-11/0026.html](http://linux.derkeiler.com/Newsgroups/comp.os.linux.portable/2005-11/0026.html)

I have reported these bugs :
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160448](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160448)
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160450](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160450)

You should also read this :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/83](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/83)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/102](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/17216/comments/102)

---

### Post by ddrichardson on 2007-11-08
> **floke said:**
> I think the figure is 600,000 - not 60,000 - so you're a long way off it yet!Sorry I miss typed it.

---

### Post by swarog on 2007-11-08
Hello, members of Ubuntu community!
I was really worried when I first saw the thread on /. about this HDD excessive wastage issue, and read the corresponding posts on Matthew Garrett's LJ ([http://mjg59.livejournal.com/77672.html](http://mjg59.livejournal.com/77672.html)) and discussion here. So I decided to check if my system is affected by this abnormal behavior.

So here is what I've got, running Ubuntu Linux **7.04** on my **Toshiba Portege M400** laptop. It has 80GB TOSHIBA MK8032GSX drive, firmware ver. AS111G.
I usually work for 10 hours a day with few breaks when I usually switch my system to suspend mode. So in the morning I load up my system from Hibernate state, then work for some time. Then I sometimes unplug the power cord and move to another place where I can plug it on again or just work for some time using its battery. And I even switch my Toshiba into tablet PC mode and go somewhere reading something from the screen while holding it in my hands. I wrote that just for the sake of some clarification concerning  my laptop usage regime.

I measured the delta amount for Load_Cycle_Count during one day (including raising from Hibernate) and it appeared to be equal to 95. So with the given value of 300,000 as assumed "maximum" for this parameter and this particular harddrive, I can roughly estimate its **remaining lifetime as long as 8 years** which I consider a very unlikely to bear out. And Toshiba points out the value of 5 years or 20,000 Power On Hours for my harddrive.

But I must admit that I expected something lesser for Load_Cycle_Count. It's **now 33721** and if I take into account that **Power_On_Hours is 837**, than **I have 40 ticks/hr as an average speed of Load_Cycle_Count growth**. And if going that fast, my drive have will probably **die in 6750 hours of work**. And the **overall lifetime will be more than 2 times less as compared with the expected one** under "normal" circumstances.

Considering "disk-heavy" software I used. I used VMware with Windows XP and Visual Studio 2005 running inside it. I also used Kino to grab and encode my camcorder filmed videos. I even installed Oracle with JDeveloper and played for some time with them (very heavy applications).  And that's it.

Hope this post is helpful, even though as I understand it doesn't clarify the problem. I'm personally even not sure whether my drive is "dying" or not.

Please ask in case I've omit some important info about my system.

---

### Post by LostAngel on 2007-11-08
I have a new inspiron 1520 running ubuntu 7.10...when I run the following to see if I am affected by the load_cycle_count bug...I dont see load_cycle_count anywhere...below is my output....is this weird?

root@brandon-laptop:/home/brandon# smartctl -d ata -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM320JI
Serial Number:    S19FJD0PA03722
Firmware Version: 2SS00_00
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Thu Nov  8 10:30:45 2007 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (  32) The self-test routine was interrupted
                                        by the host with a hard or soft reset.
Total time to complete Offline 
data collection:                 ( 119) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 119) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       63
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2625
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       13057
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       115
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       99
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       5843
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       25
194 Temperature_Celsius     0x0022   136   094   000    Old_age   Always       -       34 (Lifetime Min/Max 12/48)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4584
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       111
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       251
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         2         -
# 2  Short offline       Completed without error       00%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Interrupted [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

### Post by Fr@nKy on 2007-11-08
I have two more questions... would acpi=off in boot parameters solve the problem (and what would happen with acpi turned off in terms of energy consumption and heating??)?

Second one is... for example Fedora 8 launched today suffers from the same problem?

---

### Post by ubuntu_demon on 2007-11-08
> **swarog said:**
> Hello, members of Ubuntu community!
I was really worried when I first saw the thread on /. about this HDD excessive wastage issue, and read the corresponding posts on Matthew Garrett's LJ ([http://mjg59.livejournal.com/77672.html](http://mjg59.livejournal.com/77672.html)) and discussion here. So I decided to check if my system is affected by this abnormal behavior.

So here is what I've got, running Ubuntu Linux **7.04** on my **Toshiba Portege M400** laptop. It has 80GB TOSHIBA MK8032GSX drive, firmware ver. AS111G.
I usually work for 10 hours a day with few breaks when I usually switch my system to suspend mode. So in the morning I load up my system from Hibernate state, then work for some time. Then I sometimes unplug the power cord and move to another place where I can plug it on again or just work for some time using its battery. And I even switch my Toshiba into tablet PC mode and go somewhere reading something from the screen while holding it in my hands. I wrote that just for the sake of some clarification concerning  my laptop usage regime.

I measured the delta amount for Load_Cycle_Count during one day (including raising from Hibernate) and it appeared to be equal to 95. So with the given value of 300,000 as assumed "maximum" for this parameter and this particular harddrive, I can roughly estimate its **remaining lifetime as long as 8 years** which I consider a very unlikely to bear out. And Toshiba points out the value of 5 years or 20,000 Power On Hours for my harddrive.

But I must admit that I expected something lesser for Load_Cycle_Count. It's **now 33721** and if I take into account that **Power_On_Hours is 837**, than **I have 40 ticks/hr as an average speed of Load_Cycle_Count growth**. And if going that fast, my drive have will probably **die in 6750 hours of work**. And the **overall lifetime will be more than 2 times less as compared with the expected one** under "normal" circumstances.

Considering "disk-heavy" software I used. I used VMware with Windows XP and Visual Studio 2005 running inside it. I also used Kino to grab and encode my camcorder filmed videos. I even installed Oracle with JDeveloper and played for some time with them (very heavy applications).  And that's it.

Hope this post is helpful, even though as I understand it doesn't clarify the problem. I'm personally even not sure whether my drive is "dying" or not.

Please ask in case I've omit some important info about my system.

Most harddrive manufacturers say your drive should be able to do 600.00 Load_Cycles. You should look it up for your specific harddrive to be sure.

40 per Hour is a bit high but considering you use it 9 hours per day it would take more than 4 years to reach 600.000 Load_Cycles.

40 * 10 * 365 * 4 < 600.000

You should not be in a hurry to apply unofficial fixes. You should keep an eye on your Load_Cycle_Count and look at how fast your WORST is approaching your THRESHOLD.

---

### Post by ubuntu_demon on 2007-11-08
> **Fr@nKy said:**
> I have two more questions... would acpi=off in boot parameters solve the problem (and what would happen with acpi turned off in terms of energy consumption and heating??)?

Second one is... for example Fedora 8 launched today suffers from the same problem?

I'm not sure what the exact consequences would be of turning of acpi but I'm quite sure it's not relevant for this problem because the power management defaults are set by BIOS or laptop harddrive firmware and Ubuntu doesn't touch them unless you use hdparm or laptop-mode. 

Turning off acpi could force you to press the power button after shutting down if you want some exercise :)

---

### Post by Fr@nKy on 2007-11-08
I have been testing and my disk is doing about 8 to 10 cycles every 10 minutes... (on AC power). I have entered hdparm -B 254 /dev/sda and it stopped going up. I'm just afraid of applying because I don't know if it will make my disk heat to much!

---

### Post by b0ng0 on 2007-11-08
Is there a way of determining the load cycles in Windows Vista? My new laptop has come pre-installed with Vista and I want to see what the load is like under Vista so that I can compare it with Ubuntu to make sure it's safe. Thanks.

---

### Post by bks on 2007-11-08
I didn't even know about load cycles until reading a /. article about it. I have a 5 year old Gateway 400SD, I wonder what its at? How do I find out?

---

### Post by ddrichardson on 2007-11-08
There's a fair bit covered on my [blog]("http://blog.lynxworks.eu/") including how to check. There's two posts on it.

---

### Post by kevykev on 2007-11-08
> commit=X settings should probably be left to be set by laptop-mode (once we find sane defaults). If you use commit=X you probably should also set /proc/sys/vm/dirty_writeback_centisecs to the same new interval (in hundreds of seconds)

I think it might be better to set /proc/sys/vm/dirty_expire_centiseconds instead. This way pdflush will still write out dirty pages if memory is low when it wakes, so you dont run out of ram. Also, I read that it is not a good idea to change dirty_writeback_centisecs at all here: [http://www.westnet.com/~gsmith/content/linux-pdflush.htm]("http://www.westnet.com/~gsmith/content/linux-pdflush.htm") 

Btw, is it possible to permanently change /proc/sys/vm/dirty_expire_centiseconds by putting vm.dirty_expire_centiseconds=XX into /etc/sysctl.conf ?

---

### Post by RAV TUX on 2007-11-08
...or do we need to do anything?

In reference to the "Storm in a Teacup"
> 
**Updated: Does Ubuntu shorten HDD life?**

**Nope.**

[IMG]http://mos.futurenet.com/people/524001-525000/524401-524500/524401-524410/524408/author/image/author-27-75.jpg[/IMG]
  **Dan Grabham**

  31 Oct 2007 11:52 GMT

  According to some forum posters, installing                           [Ubuntu]("http://www.tech.co.uk/computing/software/operating-systems/news/ubuntu-710-swings-into-view?articleid=743242608") could shorten the life expectancy of your laptop's hard drive. 
The                           [bugs forum]("https://launchpad.net/bug59695.html") at Launchpad contains a posting that says switching to battery power causes the drive to complete an entire load cycle in a minute.

** Storm in a teacup**

Another                           [posting]("http://ubuntudemon.wordpress.com/2007/10/30/ubuntu-is-not-causing-aggressive-power-management/") pours cold water onto the fear, however. It's not an Ubuntu problem. Instead, the blame lies with the settings on the laptop or hard disk. It seems that Ubuntu uses the default hardware settings, while Windows uses its own set of values.
                                                               
"Some people are getting a high Load_Cycle_Count because their laptop (BIOS or hard drive firmware) uses too aggressive powermanagement," said the Ubuntu Demon's Blog.
"Ubuntu doesn't touch your hard drive power management settings by default," added Linux dev Matthew Garrett on                           [Advogato]("http://www.advogato.org/person/mjg59/diary/82.html"). "In almost all cases, it's more likely to be your BIOS or the firmware on your hard drive."

[http://www.tech.co.uk/computing/software/operating-systems/news/does-ubuntu-shorten-hard-drive-life?articleid=794557536&print=true&page=1](http://www.tech.co.uk/computing/software/operating-systems/news/does-ubuntu-shorten-hard-drive-life?articleid=794557536&print=true&page=1)

---

### Post by -grubby on 2007-11-08
finally some sense out of this problem!

---

### Post by swarog on 2007-11-09
> **b0ng0 said:**
> Is there a way of determining the load cycles in Windows Vista? My new laptop has come pre-installed with Vista and I want to see what the load is like under Vista so that I can compare it with Ubuntu to make sure it's safe. Thanks.

You can try: 

1) Running smartmontools for Win32 (can be downloaded from here [http://sourceforge.net/project/showfiles.php?group_id=64297](http://sourceforge.net/project/showfiles.php?group_id=64297)). Although I'm not sure if it works in Vista;
2) (Preferable way) Use vendor specific tool for HDD testing. Vendors usually provide customers with such applications, they are usually self-booting programs that are to be burnt on a CD or raw-written on a floppy disk. At least IBM/Hitachi and Maxtor have such tools. I'm sure others do as well.

---

### Post by swarog on 2007-11-09
> **ubuntu_demon said:**
> Most harddrive manufacturers say your drive should be able to do 600.00 Load_Cycles. You should look it up for your specific harddrive to be sure.

Well, It seems like it's 300,000, at least tech. support guy from Toshiba Storage Device Division claims it is.  
> 
40 per Hour is a bit high but considering you use it 9 hours per day it would take more than 4 years to reach 600.000 Load_Cycles.

40 * 10 * 365 * 4 < 600.000

Yes, it's high for an **average** value and before Ubuntu I've been using preinstalled version of Windows XP Tablet Edition 2005. I didn't check S.M.A.R.T. by that time, but now nothing tells me that my Load_Cycle_Count grows faster than before Ubuntu. On the contrary I would say (given my current observation data) that I have "less wastage" of Load_Cycle_Count during my Ubuntu life. Still not sure but it seems very evidently that my disk is at least not more extensively used under Ubuntu. But still I keep tracking S.M.A.R.T now. 
> 
You should not be in a hurry to apply unofficial fixes. You should keep an eye on your Load_Cycle_Count and look at how fast your WORST is approaching your THRESHOLD.
Ok.

---

### Post by ubuntu_demon on 2007-11-09
> **kevykev said:**
> I think it might be better to set /proc/sys/vm/dirty_expire_centiseconds instead. This way pdflush will still write out dirty pages if memory is low when it wakes, so you dont run out of ram. Also, I read that it is not a good idea to change dirty_writeback_centisecs at all here: [http://www.westnet.com/~gsmith/content/linux-pdflush.htm]("http://www.westnet.com/~gsmith/content/linux-pdflush.htm") 

Btw, is it possible to permanently change /proc/sys/vm/dirty_expire_centiseconds by putting vm.dirty_expire_centiseconds=XX into /etc/sysctl.conf ?

I have added your suggestions to the bug report :
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160448/comments/3](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/160448/comments/3)

Yes you can make stuff permanent in /etc/sysctl.conf that way unless something overrides it later on. So be sure to check with
$sysctl  sysctl vm.dirty_expire_centisecs

I'm recommending **to not change these kind of settings** (commit,vm.dirty*). IMHO sane defaults should be found and used in laptop-mode.

---

### Post by ubuntu_demon on 2007-11-09
> **Fr@nKy said:**
> I have been testing and my disk is doing about 8 to 10 cycles every 10 minutes... (on AC power). I have entered hdparm -B 254 /dev/sda and it stopped going up. I'm just afraid of applying because I don't know if it will make my disk heat to much!

You can monitor your harddisk temperature with hddtemp. You should look up the operating conditions on your manufacturers website. In my case it's up to 60 degrees celcius. In my case the temperature doesn't reach 60 degrees celcius after making this change. (I still have to experiment with the right apm values for myself I'm currently using 254 when on AC and 128 when on battery).

$sudo aptitude install hddtemp

You don't have to use it as a daemon if you just want to query it occasionally :
$sudo hddtemp /dev/sda

To reconfigure hddtemp (for example to make it run as a daemon later on) :
$sudo dpkg-reconfigure hddtemp

You might want to use sensors-applet or gkrellm to continually display it (now hddtemp needs to be a daemon).

running hddtemp as a daemon might cause unnecessary disk activity :
[https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621](https://bugs.launchpad.net/ubuntu/+source/hddtemp/+bug/160621)

---

### Post by ubuntu_demon on 2007-11-09
> **b0ng0 said:**
> Is there a way of determining the load cycles in Windows Vista? My new laptop has come pre-installed with Vista and I want to see what the load is like under Vista so that I can compare it with Ubuntu to make sure it's safe. Thanks.

There's an exe file you can download. Look here and let us know whether it works under Vista :
[http://sourceforge.net/projects/smartmontools/](http://sourceforge.net/projects/smartmontools/)

swarog beat me to answering you :). Thanks swarog. 

swarog's answer :
[http://ubuntuforums.org/showpost.php?p=3736524&postcount=406](http://ubuntuforums.org/showpost.php?p=3736524&postcount=406)

---

### Post by ubuntu_demon on 2007-11-09
> **swarog said:**
> Well, It seems like it's 300,000, at least tech. support guy from Toshiba Storage Device Division claims it is.  

Yes, it's high for an **average** value and before Ubuntu I've been using preinstalled version of Windows XP Tablet Edition 2005. I didn't check S.M.A.R.T. by that time, but now nothing tells me that my Load_Cycle_Count grows faster than before Ubuntu. On the contrary I would say (given my current observation data) that I have "less wastage" of Load_Cycle_Count during my Ubuntu life. Still not sure but it seems very evidently that my disk is at least not more extensively used under Ubuntu. But still I keep tracking S.M.A.R.T now. 

Ok.

Keep an eye on it. Keep making rough calculations about when your WORST will reach your THRESHOLD if this is well within 3 years of harddrive life you should consider applying the unofficial fixes.

---

### Post by Fr@nKy on 2007-11-09
smartmontools doesn't work on Windows Vista :( Any alternative.

My hardrive has nearly 1000 Load Cycle and I have this laptop for about a month (using only Vista an Ubuntu for two days).

---

### Post by Fr@nKy on 2007-11-09
Also... is there anyway that I can do the same as I did in Ubuntu with hdparm -B 254 on Windows?

---

### Post by ubuntu_demon on 2007-11-09
Fr@nKy if you want to change the default settings of your harddrive you should go to the website of your harddrive manufacturer and find out what the recommended tools are for your harddrive. With a bit of luck they are included on the ultimate boot cd-rom. IMHO not parking your harddrive at all while on battery is not a good idea because your harddrive will be less well protected from bumps.

---

### Post by ubuntu_demon on 2007-11-09
I created a first post for this thread :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

Please give me feedback so I can improve it.

---

### Post by LostAngel on 2007-11-09
anyone?

---

### Post by mc-rpg on 2007-11-12
Does the ulgy fix affects the HDD temperature?

---

### Post by ubuntu_demon on 2007-11-12
> **mc-rpg said:**
> Does the ulgy fix affects the HDD temperature?

Yes. You should only apply 254 if you are heavily affected and you understand what you are doing. Otherwise you should experiment with lower values or don't apply the fix at all.  You should keep an eye on your harddrive temperature just in case (you can use hddtemp). You should look up the healthy operating temperature range for your harddrive. You should be careful when applying this fix when running on battery (I'm using 128 for battery myself).

---

### Post by kevinbsmith on 2007-11-13
> **ubuntu_demon said:**
> 
If hdparm solved your problem let's make these settings permanent.


In my case, hdparm did not solve the problem. Now what?

Device Model:     SAMSUNG MP0402H

225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       1256483

(and increasing by several per minute)

Smallest cycle increment: 1

kevins@misty:~$ date;sudo smartctl --all /dev/sda | grep ycle
Tue Nov 13 12:58:27 EST 2007
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1190
225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       1256630
kevins@misty:~$ date;sudo smartctl --all /dev/sda | grep ycle
Tue Nov 13 12:58:37 EST 2007
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1190
225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       1256631

Here are the hdparm commands I tried:

kevins@misty:~$ sudo hdparm -S 0 /dev/sda

/dev/sda:
 setting standby to 0 (off)

kevins@misty:~$ sudo hdparm -B 254 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)


kevins@misty:~$ laptop_mode status
(snip)
Laptop Mode is NOT allowed to run: /var/run/laptop-mode-enabled does not exist.

/proc/sys/vm/laptop_mode:
   0

I run on A/C power 98% of the time.

What should I try next?

Kevin

---

### Post by sagesparrow on 2007-11-13
I'm pretty much of a newbie, but I did a little experiment that might have some useful info (or not?):

I let my computer (Dell laptop latitude x300) stay on for about 30 minutes without performing any functions in 3 modes:

1.  Gutsy without disabling APM
     start HD 20 degrees
     load cycle count  5023

     end HD 33 degrees (normal warming up from start)
     load cycle count 5081

2.  Gutsy with APM disabled (set to 255)

     start HD 33 degrees
     load cycle count 5081

     end HD 39 degrees
     load cycle count 5085 

3.  Windows XP (same computer w. dual boot setup)

     start HD temp 39 degrees
     load cycle count 5085

     end HD temp  40 degrees
     load cycle count 5085

Is this info valid or am I missing something?  Why would Windows have zero spindowns?

---

### Post by EamonR on 2007-11-13
Hey... I was reading the posts about the Power-Off_Retract_Count being an emergency unload...and I ran 

sudo smartctl --all /dev/sda | grep Power-Off_Retract_Count

and got

192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1441814

Now the other guy to post his had 40 on a 20 day old laptop...mines over 1 million and I got it in the summer...would this be really really bad? The number seems ridiculous because I havent even turned it on that many times...

sudo smartctl --all /dev/sda | grep Load_Cycle_Count

returns this by the way:

193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       45122


Edit: My load cycle count has increased to 45161 since initially posting this 23 minutes ago.

---

### Post by ubuntu_demon on 2007-11-14
@sagesparrow:

You should disable apm by using 254 instead of 255.

Ubuntu/Linux might be a little bit more affected than windows because Ubuntu/Linux uses the harddrive differently than windows because other processes are running and other applications are running. Linux uses ext3 by default which is a journalling filesystem and commits each 5 seconds if there is anything to commit (it's safer for your data). Tracker might cause some unnecessary disk activity for some people so you can try to disable it or try setting the indexing interval to a higher value (for example 600 seconds).

Here's some more information :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185)

---

### Post by ubuntu_demon on 2007-11-14
@kevinbsmith:

First try comparing your Load_Cycle_Count between bigger intervals (an hour/a day) instead of after a minute. Look up how many Load_Cycle_Counts your harddrive can handle (most harddrives can handle 600.000 Load_Cycles but be sure to look it up). Calculate the average difference in Load_Cycle_Count per day. Now calculate what your Load_Cycle_Count will be in three years of harddrive use to determine whether you have a problem.

Secondly you can use the Ultimate Boot cd-rom which probably contains the tool for your harddrive to stop apm on default. You should make sure to run on apm while on battery to protect your harddisk from bumps. 

Thirdly you should keep watching your Load_Cycle_Count and the temperature of your harddrive and make sure it's below the maximum temperature specification of your harddrive.

---

### Post by ubuntu_demon on 2007-11-14
@EamonR:

Maybe your Power-Off_Retract_Count doesn't increment by ones but by a different number. Don't worry about it.

Look up how many Load_Cycle_Counts your harddrive can handle (most harddrives can handle 600.000 Load_Cycles but be sure to look it up). Calculate the average difference in Load_Cycle_Count per day. Now calculate what your Load_Cycle_Count will be in three years of harddrive use to determine whether you need to apply the ugly fix.

---

### Post by ubuntu_demon on 2007-11-14
[B]I have updated the first post of this thread. Please read it before asking any questions :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)[/B]

---

### Post by Caprica_Resistance on 2007-11-14
Hi,

I want just to add some facts in case someone could benefit from it, because all this Load_Cycle_Count grew to some kind of urban legend or I should say "Cyber Legend".

I am not professional, just user but I gathered some information:

1. No one seems to know exactly what it is all about this Load_Cycle_Count.
2. Load_Cycle_Count is rising only on battery - **wrong**. On my laptop, my wife laptop, my friend laptop it is rising steadily on AC power.
3. Only Ubuntu is affected - **wrong**. On my Vista (got dual boot) Load_Cycle_Count is growing pretty fast (55.000 in 6 month), On my wife Laptop (only windows XP) Load_Cycle_Count is growing "nicely" in 1 year 77.000 - 90% of working time is AC power, on my friend laptop (mainly XP sometimes Fedora in some years above 300.000).
4. Other OS handle Load_Cycle_Count better than Ubuntu - **wrong** as you can see above Load_Cycle_Count can increase on various systems whether on battery or not, look at my Load_Cycle_Count changing in Fedora 8:
[root@mothership daniel]# while true
> do
> /usr/sbin/smartctl -a /dev/sda | grep Load_Cycle_Count
> sleep 300
> done
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56554
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56566
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56579
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56595
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56597
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56600
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56607
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56610
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56616
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56624
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56635

You can see how it is increasing in every 5 minutes.
The Fedora development team knows about it, but they are ignoring this fact (I read it on fedora site, can't find it right now) since (like they say) the hard disk manufacturers set this APM setting.

I applied
#!/bin/sh
hdparm -B 254 $HDD on /etc/acpi/resume.d/ and /etc/acpi/start.d/ as recomennded:
[https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695)
and it stopped increasing though I don't know if it has any drawback.

To MS Windows users the only method I discovered to stop Load_Cycle_Count to go higher is to play some mp3 all the time :lol: from hard disk...

Of course I wish next release of Ubuntu will solve this problem somehow...

---

### Post by ubuntu_demon on 2007-11-15
> **Caprica_Resistance said:**
> Hi,

I want just to add some facts in case someone could benefit from it, because all this Load_Cycle_Count grew to some kind of urban legend or I should say "Cyber Legend".

I am not professional, just user but I gathered some information:

1. No one seems to know exactly what it is all about this Load_Cycle_Count.


Getting a rough understanding about this Load_Cycle_Count issue isn't very hard. Please read the start post and all the links in it (you don't have to read about the ugly fix). Ask again if you don't understand and please be specific so I can improve this start post :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

> **Caprica_Resistance said:**
> 
2. Load_Cycle_Count is rising only on battery - **wrong**. On my laptop, my wife laptop, my friend laptop it is rising steadily on AC power.


On default in Ubuntu (and all other distributions as far as I know) your Load_Cycle_Count will rise with the same speed while running on AC as while running on battery. (AFAIK most operating systems won't override the defaults set by the harddrive firmware. Some BIOSes might override the default settings set by the harddrive firmware)

Having your Load_Cycle_Count rise while on battery is important because it protects the disk from bumps and saves some power. Having your Load_Cycle_Count rise while on AC is less important assuming you need less protection from bumps and you care less about power usage and care more about harddrive lifetime. Most of the time laptops are using AC so if your Load_Cycle_Count rises too fast you should probably want to reduce this speed only when on AC.

> **Caprica_Resistance said:**
> 
3. Only Ubuntu is affected - **wrong**. On my Vista (got dual boot) Load_Cycle_Count is growing pretty fast (55.000 in 6 month), On my wife Laptop (only windows XP) Load_Cycle_Count is growing "nicely" in 1 year 77.000 - 90% of working time is AC power, on my friend laptop (mainly XP sometimes Fedora in some years above 300.000).

4. Other OS handle Load_Cycle_Count better than Ubuntu - **wrong** as you can see above Load_Cycle_Count can increase on various systems whether on battery or not, look at my Load_Cycle_Count changing in Fedora 8:
[root@mothership daniel]# while true
> do
> /usr/sbin/smartctl -a /dev/sda | grep Load_Cycle_Count
> sleep 300
> done
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56554
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56566
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56579
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56595
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56597
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56600
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56607
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56610
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56616
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56624
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       56635

You can see how it is increasing in every 5 minutes.
The Fedora development team knows about it, but they are ignoring this fact (I read it on fedora site, can't find it right now) since (like they say) the hard disk manufacturers set this APM setting.


The amount of harddrive's power management is operating system independent. 

Disk usage is depended on a lot of things. It depends on the operating system, the hardware, the applications which are run and the person using the laptop. Most Linux distributions seem to cause a bit more disk usage for example because of ext3 journaling. Most Linux distributions default to ext3 which uses journaling which is safe for your data but causes some extra disk activity. You might unknowingly have caused some unnecessary disk activity. You might have set your email client to check for email each minute. You might have set your feed reader (accidentally) to check some specific feed each minute. Some of these things might be bugs and are reported on launchpad. See : [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185)


> **Caprica_Resistance said:**
> 
I applied
#!/bin/sh
hdparm -B 254 $HDD on /etc/acpi/resume.d/ and /etc/acpi/start.d/ as recomennded:
[https://wiki.ubuntu.com/DanielHahler/Bug59695](https://wiki.ubuntu.com/DanielHahler/Bug59695)
and it stopped increasing though I don't know if it has any drawback.


[B]Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Parking the head of a laptop harddrive also protects it from bumps so you probably shouldn't turn off head parking entirely while on battery. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperate and make sure remains below the maximum temperature specification of your harddrive. Everything you do is on your own risk.
[/B]

The biggest drawbacks of "apm 254 style fixes" are :
* no head parking : increased heat which might shorten the lifetime of your harddrive (at the very least make sure the temperature stays below the maximum temperature specification)
* no head parking : no protectection from bumps which might shorten the lifetime of your harddrive
* no head parking : increased power usage
* some people apply unofficial fixes without understanding what they are doing, without understanding how to revert them and without understanding what the drawbacks are.
* some people apply unofficial fixes without needing them (you only need them if you understand what you are doing and you will reach your Load_Cycle_Count's lifetime within three years of harddisk usage)

The advantages of using "apm 254 style fixes" :
* no head parking : a little bit better harddisk performance (is only nicer than the drawbacks if you don't move your laptop at all)
* no head parking : Load_Cycle_Count doesn't increase  (is only nicer than the drawbacks if you are very heavily affected by the Load_Cycle_Count issue)

**Don't bump your laptop while using apm 254. Keep an eye on your Load_Cycle_Count. Keep an eye on your temperature. Don't use apm 254 while on battery.**

First read the start post and all the links in it :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

If you would apply this fix instead you can keep your harddisk parking while on battery :
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

> **Caprica_Resistance said:**
> 
To MS Windows users the only method I discovered to stop Load_Cycle_Count to go higher is to play some mp3 all the time :lol: from hard disk...


Causing permanent disk activity works in all operating systems but causing permanent disk activity is bad for performance and might also decrease harddisk lifetime a little bit. Maybe the music player you use in Ubuntu uses more caching and therefor accesses the disk less.

> **Caprica_Resistance said:**
> 
Of course I wish next release of Ubuntu will solve this problem somehow...

Let's try to get the priority of the bug higher than wishlist.

Currently the reasoning goes that manufacturers should set appropriate settings because they should know what their hardware is capable of. But they probably don't test their harddrives with (recent) Linux Distributions so sometimes these defaults might be a bit too aggressive. 

Getting a rough understanding about this Load_Cycle_Count issue isn't very hard but overriding power management defaults and reducing disk usage isn't trivial. Because it's hard to find sane defaults which would work for everybody :

The solution to the problem is hard because : 
* you don't want to reduce performance too much
* you want to protect your data as much as possible (turning off journaling is not an option)
* you don't to generate too much heat (which also reduces the lifetime of your disk) and you especially don't want to cause the temperature to go above the maximum temperature specification of the disk
* you don't to use too much power 
* you want to protect the harddisk from bumps (especially when on battery)
* finding sane apm defaults is hard

Finding sane apm defaults is very hard because :
* 128 is standardized as safing as much power as possible without spinning down (unless you set the spin down time) so parking the head as much as possible. But how much head parking is different for each disk. 
* 254 is standardized as using no power management and no head parking at all (which doesn't protect your harddrive from bumps and might generate too much heat). * Values in between 128 and 254 are different for each disk.

---

### Post by mc-rpg on 2007-11-15
I think you should add to your post how to go back to the defaults. We all know you recommended to not apply the changes if you don't know what you're doing but most people will apply it just to be sure that the problem doesn't affect them but when they see that they want the functionality lost they will want to go back to the defaults. My two cents to improve your post.

---

### Post by insulae on 2007-11-15
Ok! i dont have important data on my laptop disk :P, what filesystem is better to reduce disk activity? ext2, xfs or reiserfs?
my laptop increase the Load_Cycle_Count very very fast in laptop_mode (1 cicle in 5 second), if i put my ear in the laptop i hear the disk stop and 1 second later start again, i dont have much process and i remove syslog to, so i want to try with another fs, so wich one i must to use?

Grettings
insulae

---

### Post by swarog on 2007-11-16
> **insulae said:**
> Ok! i dont have important data on my laptop disk :P, what filesystem is better to reduce disk activity? ext2, xfs or reiserfs?
my laptop increase the Load_Cycle_Count very very fast in laptop_mode (1 cicle in 5 second), if i put my ear in the laptop i hear the disk stop and 1 second later start again, i dont have much process and i remove syslog to, so i want to try with another fs, so wich one i must to use?

Grettings
insulae

I guess you should try ext2, since it doesn't maintain journaling (and ext3, xfs and reiserfs do).

---

### Post by ubuntu_demon on 2007-11-16
> **mc-rpg said:**
> I think you should add to your post how to go back to the defaults. We all know you recommended to not apply the changes if you don't know what you're doing but most people will apply it just to be sure that the problem doesn't affect them but when they see that they want the functionality lost they will want to go back to the defaults. My two cents to improve your post.

Thanks for the suggestion. For now I rather not encourage people who don't understand what they are doing to apply any unofficial fixes. If they have messed up I would rather see them asking so we can help them here.

---

### Post by ubuntu_demon on 2007-11-16
> **insulae said:**
> Ok! i dont have important data on my laptop disk :P, what filesystem is better to reduce disk activity? ext2, xfs or reiserfs?
my laptop increase the Load_Cycle_Count very very fast in laptop_mode (1 cicle in 5 second), if i put my ear in the laptop i hear the disk stop and 1 second later start again, i dont have much process and i remove syslog to, so i want to try with another fs, so wich one i must to use?

Grettings
insulae

The answer to your question is ext2. Journaling is an extra layer of protection above ext2 so you would only have to edit your fstab to make it work. **But I recommend not doing this. **Worrying about the integrity of your data likely brought you to this thread so you shouldn't remove this layer of protection.

For more information about the Load_Cycle_Count issue please read this :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

---

### Post by insulae on 2007-11-16
ok! i change the ext3 with ext2 in my /etc/fstab, then i restart my laptop and i used for 1 hour without AC (only battery) and laptop_mode, and my Load_Cycle_Count don't increase anything, i start with 8477 cycles and i finish with 8477 cycles, so i am back with ext3 and i have now 8495 cycles, hehehe, a little extrange.

Grettings
insulae

---

### Post by bkraptor on 2007-11-16
I'm just curious, how does parking the heads help protect the hdd when on battery given that every 5 seconds the heads are unparked to commit ext3 journaling stuff ? What are the chances of you dropping the laptop just as the heads are parked?

---

### Post by houstonbofh on 2007-11-16
> **bkraptor said:**
> I'm just curious, how does parking the heads help protect the hdd when on battery given that **every 5 seconds the heads are unparked to commit ext3 journaling stuff ?** What are the chances of you dropping the laptop just as the heads are parked?
This is one of the problems we are trying to fix.

---

### Post by TuxCrafter on 2007-11-17
This issue killed one of my 2,5" hard disk and almost a second one, just posting my fixes here as extra information:

# step 32: Advanced Power Management level to disabled to stop clicking sound of parking heads
man laptop-mode.conf
sudo smartctl -A /dev/sda | grep Load_Cycle_Count
sudo smartctl -o on /dev/sda
sudo hdparm -B 254 /dev/sda

# step 34: Advanced Power Management level to disabled to stop clicking sound of parking heads (must also be done for usb disks)
man laptop-mode.conf
sudo smartctl -A /dev/sdb | grep Load_Cycle_Count
sudo smartctl -o on /dev/sdb
sudo hdparm -B 254 /dev/sdb

---

### Post by ubuntu_demon on 2007-11-18
**If you have applied the unofficial ugly fix you should read this.[COLOR="Red"] Your battery.d scripts only get called when switching to battery but not when you booted from battery. Be sure to use hdparm manually when booting from battery![/COLOR]**

---

### Post by manishsingh4u on 2007-11-18
Hi Ubuntu_Demon,

I have a Compaq Presario V3018TU laptop with Ubuntu 7.04 installed. I haven't made any kernel related changes so I am sure it's the default one which is 2.6.20-15-generic.

My hard drive's load cycle used to increase by one or two every minute and the hard drive used to produce a "Ding" sound at every shut-down the same way it does when someone forcefully turns off the laptop pushing the power button for 5 seconds.

So, I did these 2 fixes:
1) [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14)
2) [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)

Now the load cycle is under control and the hard drive has stopped making a Ding sound at power off.

So, now should I consider my hard drive to be free from unnecessary wear and tear? I am not sure how other Operating systems handle this but, I used to be a fan of SUSE 10.1 prior switching to Ubuntu 7.04. 

Please excuse me if I am asking this question in a wrong place but, would you recommend me to continue with Ubuntu 7.04 or may be switch to other ones like Ubuntu 7.10 or back to SUSE 10.1?

Thank you very much for your kind help.

Mann

---

### Post by ubuntu_demon on 2007-11-18
> **manishsingh4u said:**
> Hi Ubuntu_Demon,

I have a Compaq Presario V3018TU laptop with Ubuntu 7.04 installed. I haven't made any kernel related changes so I am sure it's the default one which is 2.6.20-15-generic.

My hard drive's load cycle used to increase by one or two every minute and the hard drive used to produce a "Ding" sound at every shut-down the same way it does when someone forcefully turns off the laptop pushing the power button for 5 seconds.

So, I did these 2 fixes:
1) [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14)
2) [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)

Now the load cycle is under control and the hard drive has stopped making a Ding sound at power off.

So, now should I consider my hard drive to be free from unnecessary wear and tear? I am not sure how other Operating systems handle this but, I used to be a fan of SUSE 10.1 prior switching to Ubuntu 7.04. 

Please excuse me if I am asking this question in a wrong place but, would you recommend me to continue with Ubuntu 7.04 or may be switch to other ones like Ubuntu 7.10 or back to SUSE 10.1?

Thank you very much for your kind help.

Mann

There's a good chance you would be equally affected running other distributions. So feel free to keep using 7.10. Be sure to use hdparm to set apm to 128 (or some other value which works for you) to make your harddisk park while on battery (which saves power and protects from bumps).

Here's some more information you might want to read :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

---

### Post by Arthur Archnix on 2007-11-18
Thanks UbuntuDaemon,

I was averaging 44 cycles per hour over 2000+ hours. I followed your tips and then had no cycles after 1 hour while plugged in. Oddly enough, my fan doesn't run constantly anymore, and runs quieter when it does kick in. That's strange.

My only complaint is that you called it an "ugly hack". Seemed like a pretty nice solution to me. ;)

---

### Post by manishsingh4u on 2007-11-18
> **ubuntu_demon said:**
> There's a good chance you would be equally affected running other distributions. So feel free to keep using 7.10. Be sure to use hdparm to set apm to 128 (or some other value which works for you) to make your harddisk park while on battery (which saves power and protects from bumps).

Thanks for the information. After reading a couple of articles you provided on the load cycles, it appears that they should not be disabled completely.

Also, its been only a week since I am using Ubuntu 7.04 after having Windows XP and SUSE alternatively where Windows XP was the one which have lived most of the time on it.

Now, if I calculate the average load cycles keeping away the numbers added by Ubuntu, the number goes to 25 / hour approximately.

I am aware that besides doing any configurations possible, this count will still increase by one every time I restart or start my laptop but if I am having it running it continuously for 5 hours, I wouldn't mind it cycling to 50 to 70 times in order to save power and also the damage to platters from bumps. At this point, it just stays at a particular number.

So, is there a way I can limit the number to say, ~15 / hour besides disabling it completely?

Please excuse me if my questions are not meaningful. I just don't feel good fiddling with the hardware defaults because, the manufacturers' certainly know more what's better for their product.

Thanks again.

---

### Post by ubuntu_demon on 2007-11-19
> **Arthur Archnix said:**
> Thanks UbuntuDaemon,

I was averaging 44 cycles per hour over 2000+ hours. I followed your tips and then had no cycles after 1 hour while plugged in. Oddly enough, my fan doesn't run constantly anymore, and runs quieter when it does kick in. That's strange.

My only complaint is that you called it an "ugly hack". Seemed like a pretty nice solution to me. ;)

It's not a nice solution but an ugly hack.

The biggest drawbacks of "apm 254 style fixes" are :
* no head parking : increased heat which might shorten the lifetime of your harddrive (at the very least make sure the temperature stays below the maximum temperature specification)
* no head parking : no protectection from bumps which might shorten the lifetime of your harddrive
* no head parking : increased power usage
* some people apply unofficial fixes without understanding what they are doing, without understanding how to revert them and without understanding what the drawbacks are.
* some people apply unofficial fixes without needing them (you only need them if you understand what you are doing and you will reach your Load_Cycle_Count's lifetime within three years of harddisk usage)

Be sure to manually set your APM to 128 (or another value which doesn't disable head parking) when booting of battery.

---

### Post by ubuntu_demon on 2007-11-19
> **manishsingh4u said:**
> Thanks for the information. After reading a couple of articles you provided on the load cycles, it appears that they should not be disabled completely.

Also, its been only a week since I am using Ubuntu 7.04 after having Windows XP and SUSE alternatively where Windows XP was the one which have lived most of the time on it.

Now, if I calculate the average load cycles keeping away the numbers added by Ubuntu, the number goes to 25 / hour approximately.

I am aware that besides doing any configurations possible, this count will still increase by one every time I restart or start my laptop but if I am having it running it continuously for 5 hours, I wouldn't mind it cycling to 50 to 70 times in order to save power and also the damage to platters from bumps. At this point, it just stays at a particular number.

So, is there a way I can limit the number to say, ~15 / hour besides disabling it completely?

Please excuse me if my questions are not meaningful. I just don't feel good fiddling with the hardware defaults because, the manufacturers' certainly know more what's better for their product.

Thanks again.

A combination of power management and disk activity cause head parks. So without any diskactivity even aggressive power management won't cause much Load_Cycles. But usually there is disk activity quite regularly. 

As long as you will remain below the specification of maximum Load_Cycles for your specific drive within three years of usage you shouldn't apply any fixes. If you are heavily affected you can optionally turn off head parking while on AC.

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Parking the head of a laptop harddrive also protects it from bumps so you probably shouldn't turn off head parking entirely while on battery. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperate and make sure remains below the maximum temperature specification of your harddrive. Everything you do is on your own risk.**

Currently the reasoning goes that manufacturers should set appropriate settings because they should know what their hardware is capable of. But they probably don't test their harddrives with (recent) Linux Distributions so sometimes these defaults might be a bit too aggressive.

---

### Post by Arthur Archnix on 2007-11-19
I guess my next question is, what would be a nice solution? As I understand your discussion and writing on the subject, Ubuntu (and Fedora too, I discovered) let the hardware determine these values. But if the values are bad, then the OS should step in. 

Vista must step in and over-ride these values. I suppose the elegant solution would be if hardware manufacturers chose sane values, but until such time as a hardware manufacturer decides to provide values that maximize the lifespan of a drive (thus increasing the time between purchases) intervention will be necessary. In which case, what better solution than your own?

---

### Post by ubuntu_demon on 2007-11-19
**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Parking the head of a laptop harddrive also protects it from bumps so you probably shouldn't turn off head parking entirely while on battery. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperate and make sure remains below the maximum temperature specification of your harddrive. [COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

**If you have applied the unofficial ugly fix you should read this.Your battery.d scripts only get called when switching to battery but not when you booted from battery. [COLOR="Red"]Be sure to use hdparm manually when booting from battery![/COLOR]**

---

### Post by ubuntu_demon on 2007-11-19
> **Arthur Archnix said:**
> I guess my next question is, what would be a nice solution? As I understand your discussion and writing on the subject, Ubuntu (and Fedora too, I discovered) let the hardware determine these values. But if the values are bad, then the OS should step in. 

Vista must step in and over-ride these values. I suppose the elegant solution would be if hardware manufacturers chose sane values, but until such time as a hardware manufacturer decides to provide values that maximize the lifespan of a drive (thus increasing the time between purchases) intervention will be necessary. In which case, what better solution than your own?

Please read the information in the start post including the information linked to :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

Some suggestions about what might be done :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185)

If you have any questions left after reading all of that please let us know.

---

### Post by Arthur Archnix on 2007-11-19
Your comments on the bug filed at launchpad have done an excellent job of answering all my questions. 

Many thanks,

---

### Post by ubuntu_demon on 2007-11-19
> **Arthur Archnix said:**
> Your comments on the bug filed at launchpad have done an excellent job of answering all my questions. 

Many thanks,

You are welcome

---

### Post by anotherdisciple on 2007-11-20
So, I followed this guide>>> [http://www.linuxlove.org/2007/10/31/hdd-wearing-and-tearing-down/](http://www.linuxlove.org/2007/10/31/hdd-wearing-and-tearing-down/)  <<< to make my hard drive not crap out in less than a year.

... but now when I type "sudo smartctl -a /dev/sda | grep Load_Cycle_Count" it says

193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       26809
225 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       26809



and then I will check it a few hours later... or even a few days later... and it still says

193 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       26809
225 Load_Cycle_Count        0x0012   098   098   000    Old_age   Always       -       26809



Is it bad that this never changes now? It seems like it should. I think someone said it should increase 3-5 per hour?

---

### Post by jespdj on 2007-11-20
When it doesn't change, your harddisk is not going in power save mode. That happens because you set the -B parameter of hdparm to 255, which means: completely switch off power management.

Completely switching off power management for the harddisk on a laptop is probably not a good idea.

See this: [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

---

### Post by bkraptor on 2007-11-20
I've read your post and applied your fix about 2 days ago. BTW, thanks for your great work.

Ever since then I've been playing around with hdparm -B.

My laptop is a Dell Inspiron with a Seagate Momentus 7200.2 160 GB SATA HDD, and using Ubuntu 7.10 32bit.

I've found that when APM is set to anything less than 254 (I've only tried with 192 to be honest, but I guess it's also valid for other values), Power-off_Retract_Count increases by 1 when shutting down, when either on AC or Battery. This does not happen for hdparm -B 254. From what I understand, that means the HDD is doing an emergency retract of the heads, which supposedly is very stressful for the mechanics inside the HDD. I can't experiment with hibernate, since the fglrx driver crashes.

However, on my girlfriend's laptop (Dell Latitude D630, Hitachi Travelstar 7K200-120 120GB SATA HDD), also running Ubuntu 7.10 32bit, with the same APM value of 192 (hdparm -B 192), when shutting down her HDD doesn't increase the Power-off_Retract_Count, so this could be an issue with Seagate HDDs or with my specific HDD model. Either way, I think it's best to let others know about this.

PS: completely offtopic, do you have any idea how I can send a fake event to acpid? I need to fix the booting-from-battery-doesn't-start-powersave-mode issue, and I think that's the only "clean" way of doing it. A more dirty way of doing it is posted by me here (last post).

---

### Post by ubuntu_demon on 2007-11-20
> **bkraptor said:**
> I've read your post and applied your fix about 2 days ago. BTW, thanks for your great work.

Ever since then I've been playing around with hdparm -B.

My laptop is a Dell Inspiron with a Seagate Momentus 7200.2 160 GB SATA HDD, and using Ubuntu 7.10 32bit.

I've found that when APM is set to anything less than 254 (I've only tried with 192 to be honest, but I guess it's also valid for other values), Power-off_Retract_Count increases by 1 when shutting down, when either on AC or Battery. This does not happen for hdparm -B 254. From what I understand, that means the HDD is doing an emergency retract of the heads, which supposedly is very stressful for the mechanics inside the HDD. I can't experiment with hibernate, since the fglrx driver crashes.

However, on my girlfriend's laptop (Dell Latitude D630, Hitachi Travelstar 7K200-120 120GB SATA HDD), also running Ubuntu 7.10 32bit, with the same APM value of 192 (hdparm -B 192), when shutting down her HDD doesn't increase the Power-off_Retract_Count, so this could be an issue with Seagate HDDs or with my specific HDD model. Either way, I think it's best to let others know about this.


Thanks for notifying people about a possible issue. 

Does this also happen for APM 128 (which is the default for my harddrive and maybe a lot of harddrives) ?

Do you have good references / links / information about Power-off_Retract_Count supporting your claim that it's a bad thing if it increases on shutdown ?

> **bkraptor said:**
> 
PS: completely offtopic, do you have any idea how I can send a fake event to acpid? I need to fix the booting-from-battery-doesn't-start-powersave-mode issue, and I think that's the only "clean" way of doing it. A more dirty way of doing it is posted by me here (last post).

Maybe laptop-mode will do it if we can find nice default values for laptop-mode. See also : [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185)

---

### Post by Arthur Archnix on 2007-11-20
Ubuntu Demon, I think I'm going to do a minimal install on a separate partition, which should only install base and leave me at a cli. I already know my hard-drive is affected. Then I'll follow you instructions for installing smartmon tools, and leave my laptop on and plugged in for about 8 hours to get an average load/unload. The next night I think I'll add 'noatime' to the fstab and redo the overnight average test. I'll repeat after installing ubuntu-desktop, which should add tracker into the mix and give another datapoint. I won't be runnning either firefox or thunderbird on it. The fourth night I'll uninstall tracker and get a final average load/unload count. If you have any suggestions that would make this little experiment more useful in terms of bug tracking please let me know.

---

### Post by bkraptor on 2007-11-20
About Power-off_Retract_Count being dangerous, I read about it in this very topic ([post #13](http://ubuntuforums.org/showpost.php?p=3468559&postcount=13)). That post links to a PDF from Hitachi which says that it is dangerous and possibly hundreds of times more stressful to the mechanics inside a HDD than a normal unload.

I've just tested APM 128 and Power-off_Retract_Count still increases. I don't have my girlfriend's laptop around to test on it too, but based on the experience with APM 192, her Hitachi HDD doesn't seem to be affected.

I want to stress the fact that Power-off_Retract_Count does increase on my Seagate HDD (see previous post for the exact model), and DOES NOT increase on my girlfriend's Hitachi HDD (see previous post) when using the same values (192) on both laptops.

---

### Post by ubuntu_demon on 2007-11-20
> **Arthur Archnix said:**
> Ubuntu Demon, I think I'm going to do a minimal install on a separate partition, which should only install base and leave me at a cli. I already know my hard-drive is affected. Then I'll follow you instructions for installing smartmon tools, and leave my laptop on and plugged in for about 8 hours to get an average load/unload. The next night I think I'll add 'noatime' to the fstab and redo the overnight average test. I'll repeat after installing ubuntu-desktop, which should add tracker into the mix and give another datapoint. I won't be runnning either firefox or thunderbird on it. The fourth night I'll uninstall tracker and get a final average load/unload count. If you have any suggestions that would make this little experiment more useful in terms of bug tracking please let me know.

Thanks for wanting to help out :)

IMHO there's two ways people can help out in reducing the Load_Cycle_Count of everyone. Either focusing on finding possibly unnecessary diskactivity using blktrace (costs a lot of time) or focussing on trying to find sane defaults for laptop-mode which work for everybody and not just for yourself (might be very hard).

I'll explain the approach to finding possibly unnecessary diskactivity. By reducing unnecessary disk activity we save power and prevent some unnecessary Load_Cycles. Try to find anything which accesses your disk regularly and could possibly be reduced in the amount it accesses the disk. Please start with step one and two because step three isn't very useful.

[B]
Read this blktrace howto :
[http://ubuntuforums.org/showpost.php?p=3722850&postcount=375](http://ubuntuforums.org/showpost.php?p=3722850&postcount=375)

Read this (especially the links to disk activity bug reports because you might want to report your disk activity bugs in a similar way) :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/185)
[/B]
**Step One** spend some time to blktrace your regular setup and regular way of working. Try one application at a time and try both using them like you normally would for a while and letting them idle for a while. Also try just booting into your desktop and not using any specific applications (other than blktracing ofcourse) Don't do anything else with your laptop. **I found some possible disk activity bugs in this way**

**Step Two** you could spend some time to blktrace all desktop applications included on default in Ubuntu one-by-one (this will take a lot of time but you might be able to find some good stuff). Some applications you might want to start with : **evolution**, invest (in panel), openoffice, gimp 

**Step Three** you could start blktracing very minimal idling setups **probably not very useful** because you would already have seen unnecessary disk activity running a full desktop but you might be able to find some more **obscure or minor**  disk activity bugs. (atime , ubuntu-minimal ubuntu-standard)

**quite useless but might be fun to know**. You could calculate how fast your Load_Cycle_Count increases under default apm settings under a clean installation running only ubuntu-standard and ubuntu-minimal while idling and compare this to a default cleanly installed desktop installation which is idling.

---

### Post by ubuntu_demon on 2007-11-20
> **bkraptor said:**
> About Power-off_Retract_Count being dangerous, I read about it in this very topic ([post #13](http://ubuntuforums.org/showpost.php?p=3468559&postcount=13)). That post links to a PDF from Hitachi which says that it is dangerous and possibly hundreds of times more stressful to the mechanics inside a HDD than a normal unload.

I've just tested APM 128 and Power-off_Retract_Count still increases. I don't have my girlfriend's laptop around to test on it too, but based on the experience with APM 192, her Hitachi HDD doesn't seem to be affected.

I want to stress the fact that Power-off_Retract_Count does increase on my Seagate HDD (see previous post for the exact model), and DOES NOT increase on my girlfriend's Hitachi HDD (see previous post) when using the same values (192) on both laptops.

Thanks. 

**editted : **
please read this : [http://ubuntuforums.org/showpost.php?p=3817772&postcount=489](http://ubuntuforums.org/showpost.php?p=3817772&postcount=489)

---

### Post by atomicdad on 2007-11-20
I've been following this and other threads pretty closely over the last few weeks. While i'm not familiar with the nitty gritty details you all have been discussing I have verified that my load_cycle_count is increasing at a rapid clip. I tried the hdparm -B fix, and found the load_cycle_count rate significantly decreased, but it sounded as if the HD was constantly spinning at fairly high rate as seemed to produce a high frequency hum that I didn't think sounded good. I also notice the loud "plink" noise on shutdown that I don't particularly like. 

While I might not have much insight into the various processes that you are investigating i can try some of the tracing programs that you suggested to provide you with additional research data from my laptop if that would be helpful. 

FYI, I have a Dell Inspirion 1520, with the Seagate 160 Gb, 7200 sata drive, running Fiesty Fawn 64 bit.

---

### Post by ubuntu_demon on 2007-11-20
> **atomicdad said:**
> I've been following this and other threads pretty closely over the last few weeks. While i'm not familiar with the nitty gritty details you all have been discussing I have verified that my load_cycle_count is increasing at a rapid clip. I tried the hdparm -B fix, and found the load_cycle_count rate significantly decreased, but it sounded as if the HD was constantly spinning at fairly high rate as seemed to produce a high frequency hum that I didn't think sounded good. I also notice the loud "plink" noise on shutdown that I don't particularly like. 

While I might not have much insight into the various processes that you are investigating i can try some of the tracing programs that you suggested to provide you with additional research data from my laptop if that would be helpful. 

FYI, I have a Dell Inspirion 1520, with the Seagate 160 Gb, 7200 sata drive, running Fiesty Fawn 64 bit.

If your Power-Off_Retract_Count increases and you hear a "ploink"  your hardisk **might** be doing some kind of emergency unpark which **might** be very bad. Use the default apm value / an apm value of 254 or an apm value of 128 (for my harddisk 128 is the default) to see whatever doesn't increase your Power-Off_Retract_Count and let us know.

If you can't get the emergency unpark problem to stop you might want to hide the ugly noises (this probably won't stop the emergency unpark problem) you might want to try "sudo apm -M 128 /dev/sda"

see :
[http://ubuntuforums.org/showpost.php?p=3805168&postcount=451](http://ubuntuforums.org/showpost.php?p=3805168&postcount=451)
[http://ubuntuforums.org/showpost.php?p=3805582&postcount=453](http://ubuntuforums.org/showpost.php?p=3805582&postcount=453)

---

### Post by ubuntu_demon on 2007-11-21
Debian is using a temporary "hdparm -B 254" fix. But Debian doesn't set apm 128 while on battery (yet?) which saves power and protects the disk from bumps.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=448673](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=448673)
read the end of the page of [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) such as : 
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/217](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/217)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/219](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/219)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/220](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/220)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/222](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/222)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/223](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/223)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/225](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/225)

---

### Post by ubuntu_demon on 2007-11-21
> **jespdj said:**
> When it doesn't change, your harddisk is not going in power save mode. That happens because you set the -B parameter of hdparm to 255, which means: completely switch off power management.

Completely switching off power management for the harddisk on a laptop is probably not a good idea.

See this: [http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

I've merged this thread into the support thread for the Load_Cycle_Count issue.

A good place to start reading this thread is the first post :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

The correct value to turn of power management altogether is 254. You shouldn't do this unless you understand what you are doing and if you are heavily affected (your Load_Cycle_Count will reach it's maximum specification within three years of usage).

When you decide to do this you should use an apm of 128 (or an other number which works for you and keeps parking your disk) while on battery because parking the disk protects it from bumps, saves power and makes your disk less hot.

---

### Post by ubuntu_demon on 2007-11-21
How old is your drive ? 

You can always try the tool specific for your harddisk which is probably included on the ultimate boot cd-rom. You probably won't be able to see Load_Cycle_Count information but you will know whether your harddrive is currently healthy.

---

### Post by ubuntu_demon on 2007-11-21
The support thread is here :
[http://ubuntuforums.org/showthread.php?t=591503](http://ubuntuforums.org/showthread.php?t=591503)

Please read the first post of this support thread :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

---

### Post by blackhole54 on 2007-11-22
> **ubuntu_demon said:**
> **If you have applied the unofficial ugly fix you should read this.Your battery.d scripts only get called when switching to battery but not when you booted from battery. [COLOR="Red"]Be sure to use hdparm manually when booting from battery![/COLOR]**

> Please give me feedback so I can improve this post.

It would be trivial to add a test to *rc.local* using **/usr/bin/on_ac_power** to set the disk APM to the desired value at powerup depending on whether the computer is on AC or battery.  I haven't worked out the details since this is not the route I am taking.

I appologize if I am duplicating somebody else's post.  I came to this post from the System76 thread, and if this is the very long "main thread," I have only made it through the first 300 posts so far.  (All in good time, I suppose.)

---

### Post by manishsingh4u on 2007-11-22
> **ubuntu_demon said:**
> Thanks. 

**[COLOR="Red"]Everyone please read this :[/COLOR]**

[B]Let's all keep an eye on our Power-Off_Retract_Count just in case.

If you experience bad noise from your harddisk during shutdown and your Power-Off-Retract_Count increases please report back to us whether using apm 254 solves this problem.[/B]

Nope, it doesn't fix the bad noise and the Power-Off-Retract_Count increases by one every time the machine turns off. As I mentioned earlier, I had to apply this [fix]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60") to make the sound go away and now the counter doesn't increase any more.

---

### Post by ubuntu_demon on 2007-11-22
> **manishsingh4u said:**
> Nope, it doesn't fix the bad noise and the Power-Off-Retract_Count increases by one every time the machine turns off. As I mentioned earlier, I had to apply this [fix]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60") to make the sound go away and now the counter doesn't increase any more.

This issue isn't related to Load_Cycle_Count in any way.

For people who are hearing a bad noise and/or see an increase in Power_Off_Retract_Count : Please upgrade to Gutsy. The issue should be solved in Gutsy. If you are running Gutsy but still have this problem please report it in the bug report.

Here's the bug report : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/)

Please continue the discussion about Power_Off_Retract_Count here :
[http://ubuntuforums.org/showthread.php?t=600697](http://ubuntuforums.org/showthread.php?t=600697)

---

### Post by ubuntu_demon on 2007-11-22
> **blackhole54 said:**
> It would be trivial to add a test to *rc.local* using **/usr/bin/on_ac_power** to set the disk APM to the desired value at powerup depending on whether the computer is on AC or battery.  I haven't worked out the details since this is not the route I am taking.

I appologize if I am duplicating somebody else's post.  I came to this post from the System76 thread, and if this is the very long "main thread," I have only made it through the first 300 posts so far.  (All in good time, I suppose.)

Thanks! I have improved the "unofficial ugly fix"

---

### Post by ubuntu_demon on 2007-11-22
**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperate and make sure it remains below the maximum temperature specification of your harddrive. [COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

**[COLOR="Red"]Everyone who is using the fix please use this updated unofficial ugly fix :[/COLOR]**
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

**This is important because it should always set your apm to 128 while on battery and to 254 while on AC. So it will do head parking while on battery (to protect your harddisk from bumps and save some power) and it will turn head parking off when on AC.** 
Please read why I'm recommending this : [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/232](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/232)

If your Load_Cycle_Count is already close to it's specification (and behaves as a normal counter thus increments by 1) or your WORST is already at your THRESHOLD or very close to your THRESHOLD you should consider changing the "number for apm while on battery" (128) to 254 but you will lose any protection from bumps.

**We need testers for this updated fix.** 

Please keep testing whether your Load_Cycle_Count increases while on AC after applying the updated fix. It should never do so after applying this fix except for suspending/hibernating which will increase it by one.

Please test whether apm is set to 128 while on battery. This should work without any problems for everyone who uses the updated fix but please test to make sure :
* booting from battery
* switching to battery (from AC)
* suspending on AC and resuming on battery
* hibernating on AC and resuming on battery

Please test whether apm is set to 254 while on AC.  This should work without any problems for everyone who uses the updated fix but please test to make sure :
* booting from AC
* switching to AC (from battery)
* suspending on battery and resuming on AC
* hibernating on battery and resuming on AC

Please keep testing whether your Load_Cycle_Count increases while on AC after applying the updated fix. It should never do so after applying this fix except for suspending/hibernating which will probably increase it by one.

My laptop doesn't do suspend and hibernate reliably the last time I checked. **So please test suspend and hibernate** to see how it affects your Load_Cycle_Count.


To see whether you are using 128 or 254 use :
```

sudo hdparm -I /dev/sda | more

```

254 looks like this for me :
*        Advanced power management level: unknown setting (0x00fe)*
128 looks like this for me :
*        Advanced power management level: unknown setting (0x0080)*

I would be interested in knowing how fast your Load_Cycle_Count increases (if it does behave as a counter which increments by 1) when using an apm of 128. I would also like an estimate for the total hours you use your laptop on battery. Please calculate what your Load_Cycle_Count would be after three years of usage if you would have applied this unofficial ugly fix immediately after you bought this harddrive. So in this case your Load_Cycle_Count starts at zero and only increases while on battery and each time you turn your laptop off/suspend it/hibernate it. Please let us know how this resulting number compares to the maximum Load_Cycle_Count your drive is specified for.

There is a relevant discussion at the end the bug report about using apm=128 while on battery starting at comment 232. If you have anything to contribute please share. The bug report :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

**Don't apply any unofficial ugly fixes unless you understand what you are doing and you understand how to revert. Only apply this fix if you are heavily affected. After applying this fix keep an eye on your Load_Cycle_Count and on your harddrive temperate and make sure it remains below the maximum temperature specification of your harddrive. [COLOR="Red"]Everything you do is on your own risk.**[/COLOR]

---

### Post by ubuntu_demon on 2007-11-22
> **blackhole54 said:**
> 
I appologize if I am duplicating somebody else's post.  I came to this post from the System76 thread, and if this is the very long "main thread," I have only made it through the first 300 posts so far.  (All in good time, I suppose.)

For people who don't want to read the whole thread I'm trying to keep the first post updated with the most important information :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

**I have just updated it. **

---

### Post by blackhole54 on 2007-11-23
> **ubuntu_demon said:**
> 
```

#/bin/bash
if on_ac_power = 1 ; then
hdparm -B 254 /dev/sda
else
# possibly on battery
hdparm -B 128 /dev/sda
fi
```

Hi ubuntu_demon

The above construction was not something I had seen before, so I tested out it out with a dummy payload.  Somewhat to my surprise it worked!  But it also did the same thing regardless what number is after the equal sign. So while **bash** does not appear to complain about the above construction, I believe the following is more traditional and more readable:

```

#/bin/bash
if on_ac_power; then
   hdparm -B 254 /dev/sda
else
# possibly on battery
   hdparm -B 128 /dev/sda
fi
```

If you want to test for all three possible return values from **on_ac_power**, you  could:

```

#!/bin/bash

on_ac_power; RET=$?
if [ $RET == 0 ]; then

#  we're on AC power (a return value of zero means "true")
   hdparm -B 254 /dev/sda

elif [ $RET == 1 ]; then

#  we'e on battery
   hdparm -B 128 /dev/sda

elif [ $RET == 255 ]; then

#  We can't determine battery vs AC
   :
else

#  All other values are *supposed* to be illegal!  But what the heck.
   :
fi

```

The last two branches aren't necessary;  I just included them for pedagogical reasons, using the dummy colon (:) command so **bash** doesn't complain.

**NOTE:  I did _not_ test the above code**

---

### Post by ubuntu_demon on 2007-11-23
> **blackhole54 said:**
> Hi ubuntu_demon

The above construction was not something I had seen before, so I tested out it out with a dummy payload.  Somewhat to my surprise it worked!  But it also did the same thing regardless what number is after the equal sign. So while **bash** does not appear to complain about the above construction, I believe the following is more traditional and more readable:
...................


Thanks for the feedback
IMHO it works because all positive numbers are *True* and I just wanted to check for *True*.

I improved the readability of the 99-hdd-ugly-fix.sh script and updated the unofficial ugly fix howto.

```

#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 128 /dev/sda
fi

```

I actually prefer python but for something small like this using python would be a bit silly :)

---

### Post by blackhole54 on 2007-11-23
> **ubuntu_demon said:**
> I actually prefer python but for something small like this using python would be a bit silly :)

True.
And message received! :)

I am not in a position to retest it right now, but when I was testing out your **if** construction, I think when I was trying different numbers, I also tried zero, and it made no difference.  It was as if **bash** was ignoring the equal sign and the number.  Maybe I need to crack the books again on bash.  :guitar::popcorn:

EDIT:  Dugh!  Boy do I feel stupid!  In the expression **on_ac_power = 1** The equal sign and 1 are being fed to **on_ac_power** as parameters where they are promptly ignored.  Ubuntu_demon, (if you read this) I am commenting with this edit instead of cluttering up this thread with another comment that is rather OT.  I agree about Debian -- good news.

---

### Post by ubuntu_demon on 2007-11-23
> **blackhole54 said:**
> True.
And message received! :)

I am not in a position to retest it right now, but when I was testing out your **if** construction, I think when I was trying different numbers, I also tried zero, and it made no difference.  It was as if **bash** was ignoring the equal sign and the number.  Maybe I need to crack the books again on bash.  :guitar::popcorn:

I'm not a bash expert but this is a tiny script and what we now have seems to work. Bart Samwel (maintainer of laptop-mode-tools and acpi-support in Debian) thinks it might be good to do something like this by default in acpi-support. We are making nice progress :)

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/232](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/232)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/233](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/233)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/234](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/234)

---

### Post by ubuntu_demon on 2007-11-23
chrischan I have updated my answer to you :
[http://ubuntuforums.org/showpost.php?p=3719857&postcount=370](http://ubuntuforums.org/showpost.php?p=3719857&postcount=370)

I have also used your case as an example (please read) : 
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/235](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/235)

---

### Post by kevinbsmith on 2007-11-23
> **kevinbsmith said:**
> In my case, hdparm did not solve the problem. Now what?

Device Model:     SAMSUNG MP0402H


I found the answer on a different forum (sorry, can't find the link now). Some Samsung drives will ignore all attempts to set -B and/or -S parameters unless you first do:

  sudo smartctl -o on /dev/sda

That enables offline data collection, which logically would have no effect, but definitely did. 

After doing that, my load cycle count immediately stopped increasing. Then, I was able to adjust the hdparm -S parameter to get it to at least do a load cycle if I Suspend. I assume if I play with relatime and/or laptop mode, I might be able to get it to park during normal usage "when appropriate", such as after 2 minutes of inactivity.

---

### Post by chichilalescu on 2007-11-24
Hello all.

I just saw this thread, and I remembered I didn't like the noise my harddrive made from time to time. I have a SAMSUNG MP0402H hard drive, on a "prestigio nobile 150" laptop that i bought in may 2006. i've been using only ubuntu on it eversince.
As I understand it, the limit of Load_Cycle_Count should be around 600000, but I have one of over 2 million:

```
smartctl -a /dev/sda | grep Load_Cycle_Count
225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       2103796
```

yes, it behaves like a counter (it increases by 1). i also checked the health:
```
smartctl -H /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
```

Should I be worried...?
I "installed" the ugly fix, and I even executed "smartctl -o on /dev/sda", but the counter goes up just as fast (went up from 796 to 820 as I wrote this message).
Theoretically the harddrive has a warranty of 3 years, and I couldn't find anything about a limit on load cycles.

By the way, I use a laptop to move from home to the office at the university easily, not because I need to use the battery.
Anyway, my load_cycle_count seemed kind of strange and I was curious.

---

### Post by ubuntu_demon on 2007-11-24
Please keep testing whether your Load_Cycle_Count increases while on AC after applying the updated fix. It should never do so after applying this fix except for suspending/hibernating which will probably increase it by one.

---

### Post by chichilalescu on 2007-11-25
After aplying the fix, it stayed still. it's been at 2103846 eversince.
However, I did suspend the computer today, and this did not increase it by one. Next time I use hibernate, I hope I'll remember to check if it grows, but I tend not to use hibernate because my sound dies after the computer hibernates.
On a side note, today was the first time in my laptops lifetime that it fell on the floor (from a chair), because my brother tripped on the network cable. Strange, even though i applied the fix, my harddisk is still alive :). Guess I was lucky.

---

### Post by jorges00 on 2007-11-25
Hi all,
I've been following this issue as both laptops (personal and work) I use exhibit this behavior. Right now I am using the ugly fix proposed by ubuntu_demon and while I understand this a palliative measure until a not-so-ugly one is found, I think it's only addressing one of the problems, i.e. too aggressive power management. The second problem, i.e. too frequent accesses to the disk, is left untouched. I think this last problem has to be addressed somehow too, otherwise the only way to avoid killing our disks will be to sacrifice saving power, as the ugly-fix does now. I've read somewhere that there are tweaks one can do to reduce disk accesses (mount partitions noatime or relatime, disable tracker, etc.), but in my opinion it would be better if there was a global option or such that consolidated all necessary low-level tweaks.
To sum up, we need to let the disk alone for more than a few seconds if we want more than just a quick fix. 
Thanks to all the people that have raised this problem and are looking for solutions. Many of us would just be left wondering why our disks failed so soon without them.

jorges

---

### Post by gettons on 2007-11-25
Hi to everybody, this is my output on an XPS M1210 dell , 6 months aged.

Should I concern about its hard disk status?


gettons@getbuntu:~$ sudo smartctl -H /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

gettons@getbuntu:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   079   079   000    Old_age   Always       -       42361


The Load_Cycle_Count seems too high.
By battery or ac they grow up about 1 each minute.


My hard drive is a seagate ST9120822AS  , in the specs 600,000 cycles guranteed
Laptop mode not enabled in ubuntu acpi config file.
I used only xp and gentoo 2007.1 on this laptop from June, and ubuntu since the Gutsy release.

Thanks a lot in advance

---

### Post by spier on 2007-11-25
Hi,

just posting a feedback: after applying the ugly fix (maybe it could be renamed to something nicer - debian as incorporated a fix like this, too) my Load_Cycle_Count increases by one only after suspend, hibernate or a restart. 
Testing on a vaio FS,  AC powered, tried many values between 128 and 254 and, apparently, 192 is the magic one  - 191 acts exactly like 128; 192 like 254.

---

### Post by blackhole54 on 2007-11-26
> **jorges00 said:**
>  ... I think it's only addressing one of the problems, i.e. too aggressive power management. The second problem, i.e. too frequent accesses to the disk, is left untouched. I think this last problem has to be addressed somehow too, otherwise the only way to avoid killing our disks will be to sacrifice saving power, as the ugly-fix does now. I've read somewhere that there are tweaks one can do to reduce disk accesses (mount partitions noatime or relatime, disable tracker, etc.), but in my opinion it would be better if there was a global option or such that consolidated all necessary low-level tweaks.

I concur that the focus on disk APM is a stop-gap measure and that there are deeper issues which need to be addressed.  It appears to me that an attempt has already been made to limit frequency of disk access when running on battery as evidenced by the file */etc/laptop-mode/laptop-mode.conf*.   In particular lines like the following (extracting selected lines rather than posting entire lengthy file):

```

ENABLE_LAPTOP_MODE_ON_BATTERY=1
ENABLE_LAPTOP_MODE_ON_AC=0
LM_BATT_MAX_LOST_WORK_SECONDS=600
CONTROL_NOATIME=0
LM_AC_HD_IDLE_TIMEOUT_SECONDS=5
[color=red]CONTROL_HD_POWERMGMT=0[/color]
[color=green]CONTROL_SYSLOG_CONF=0[/color]

```

The above lines contain the default settings as they are found in *edgy eft*.  As I understand the 3rd line above, it is trying to keep the hard drive quiet for periods of 10 minutes.   The line highlighted in red I believe is the (well advertised) line that, by default, prevents laptop-mode from changing the disk's APM settings.  I only noticed the line I've highlighted in green as I was posting this.  This _may_ be part of the issue of why the disk is accessed so often, even under battery.  I've not delved into this matter deeply, but at least until I noticed *CONTROL_SYSLOG_CONF*, I was going to say that even though the infrastructure to restrict disk access under battery was in place, it didn't seem to be working.  When I get a chance I might look into this SYSLOG setting further.  Maybe others can as well.  Please note that all of the above lines have comments in *laptop-mode.conf* that should be read before changing values.

I am also heartened that Debian developers are taking an interest in this topic.

EDIT:  I believe I mispoke above.  I think it is *ENABLE_LAPTOP_MODEM* in * /etc/default/acpi-support* that is the "well advertised" line,  instead of *CONTROL_HD_POWERMGMT*.  But I have done some limited experiments with *ENABLE_LAPTOP_MODEM=true* while preventing *laptop-mode* from setting the disk's APM level.  These experiments, with a disk APM of 128 and laptop running on battery, looked rather hopeful, but I don't know yet if it is adequate.  I will try to post the details later.

---

### Post by blackhole54 on 2007-11-26
In response to [jorges00's comment]("http://ubuntuforums.org/showpost.php?p=3837375&postcount=502")  about the need to reduce disk accesses,  [I commented earlier]("http://ubuntuforums.org/showpost.php?p=3840272&postcount=505")   about the fact that an infrastructure seems to already be in place, reflected in the */etc/laptop-mode/laptop-mode.conf* configuration file.  I did a simple experiment enabling laptop mode, which had some hopeful results regarding reducing disk access, which I am reporting in this post.  I think it would be useful if others, who are experienced and confident enough to wade into these waters, would try similar experiments to see what hope this existing infrastructure has for handling this issue.  Since *Load_Cycle_Count* for the drive on my machine is already above 600,000, I am restricting myself at this time to limited experiments that are closely supervised.

I am running *edgy eft*.  Rather than implimenting the much discussed "ugly fix" I simply set the disk's APM value to 254 (off) in */etc/rc.local*, which runs once at boot time.  I configure things so that even while enabling laptop-mode, nothing will automatically change this setting;  I retain manual control over the disk's APM.  Explanation of the variables and filenames I reference below can be found in the comments of *laptop-mode.conf*.

I used **lm-syslog-setup** to create the three alternate syslog.conf files (potentially) used with laptop-mode.  I then modify *syslog-on-battery.conf* such that **syslogd** will _not_ immediately sync its output to the disk.  This is done by adding (if not already there) a minus sign before each log's filename.  I then change the following lines in *laptop-mode.conf* from their default values to:

```

CONTROL_NOATIME=1
CONTROL_SYLOG_CONF=1

```

These suppress access time logging  and cause the modified syslog.conf to be used while on battery.

I will note in particular, three of the default values which I left unchanged:

```

LM_BATT_MAX_LOST_WORK_SECONDS=600
LM_BATT_HD_IDLE_TIMEOUT=5
CONTROL_HD_POWERMGMT=0

```

The second line sets the disk to spindown after 5 seconds of inactivity, while the first line then tries to keep the disk spun down for 10 minutes, both while on battery.  The last line prevents laptop mode from changing the disks APM values, which I wish to control manually in these experiments.

So with that in place I set *ENABLE_LAPTOP_MODE=true* in */etc/default/acpi-support*, go on battery power, and set the disk's APM value to 128 using **hdparm**.  From previous tests w/o laptop-mode enabled, I know that with my computer idle but the APM value at 128, in five minute tests *Load_Cycle_Count* will typically increase by about 10. (2/minute).  In this case, in a 20 minute test, it increased by only 4 (0.2/minute) while the computer was idling.  In some shorter tests while I was occasionly doing something on the computer (such as doing a graphical login -- these tests were done in a virtual terminal) the changes were a little bit higher, but still significantly under the 2/minute that was typical without laptop-mode trying to limit the number of disk accesses.  The other thing that was obvious -- and different -- was the delays when the disk needed to spin-up.

I will also note that if  *CONTROL_HD_POWERMGMT* is set to one, then I would think the existing laptop-mode structure could be controlling the switching of disk APM values between 128 and 254 that are currently being handled by the "ugly fix."  If that is the desired behavior, then *BATT_HD_POWERMGT* would need to be set to 128 instead of 1 and *NOLM_AC_HD_POWERMGMT* should be set to 254 instead of 255.

Before anything like this is widely adopted, I would think we should have more experimentation by people with the experience to safely do it.  So please, if you are totally confused by what I've posted here, don't try to impliment this at this time!

---

### Post by ubuntu_demon on 2007-11-27
> **kevinbsmith said:**
>  I assume if I play with relatime and/or laptop mode, I might be able to get it to park during normal usage "when appropriate", such as after 2 minutes of inactivity.

Maybe but that will depend on your usage. AFAIK the only way to **guarantee** a Load_Cycle_Count that doesn't increase to fast is using hdparm -B 255 (like this unofficial ugly fix does or using the tool recommended by your harddisk manufacturer).

Bart Samwel maintainer of acpi-support and laptop-mode-tools in Debian thinks that Ubuntu should adopt a similar fix (Debian already has it). See also :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/242](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/242)

IMHO it is still important to report bugs about unnecessary disk activity because we will save power and Load_Cycles while on battery.

see also :
[http://ubuntuforums.org/showpost.php?p=3847126&postcount=509](http://ubuntuforums.org/showpost.php?p=3847126&postcount=509)

---

### Post by ubuntu_demon on 2007-11-27
> **chichilalescu said:**
> Hello all.

I just saw this thread, and I remembered I didn't like the noise my harddrive made from time to time. I have a SAMSUNG MP0402H hard drive, on a "prestigio nobile 150" laptop that i bought in may 2006. i've been using only ubuntu on it eversince.
As I understand it, the limit of Load_Cycle_Count should be around 600000, but I have one of over 2 million:

```
smartctl -a /dev/sda | grep Load_Cycle_Count
225 Load_Cycle_Count        0x0012   001   001   000    Old_age   Always       -       2103796
```

yes, it behaves like a counter (it increases by 1). i also checked the health:
```
smartctl -H /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
```

Should I be worried...?
I "installed" the ugly fix, and I even executed "smartctl -o on /dev/sda", but the counter goes up just as fast (went up from 796 to 820 as I wrote this message).
Theoretically the harddrive has a warranty of 3 years, and I couldn't find anything about a limit on load cycles.

By the way, I use a laptop to move from home to the office at the university easily, not because I need to use the battery.
Anyway, my load_cycle_count seemed kind of strange and I was curious.

Are you sure you followed the instructions of the unofficial ugly fix exactly ?
[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

You should be using an apm of 254 instead of 255 (if you followed another fix).

If you followed the instructions exactly and it still increases while on AC please add it to the bug report or let me know here so I can add it to the bug report and you should use the tool recommended by your harddisk manufacturer which is probably included on the ultimate boot cd-rom to set apm to 254.

> **chichilalescu said:**
> After aplying the fix, it stayed still. it's been at 2103846 eversince.
However, I did suspend the computer today, and this did not increase it by one. Next time I use hibernate, I hope I'll remember to check if it grows, but I tend not to use hibernate because my sound dies after the computer hibernates.
On a side note, today was the first time in my laptops lifetime that it fell on the floor (from a chair), because my brother tripped on the network cable. Strange, even though i applied the fix, my harddisk is still alive :). Guess I was lucky.

So now the fix does work ? What did you change compared to when it didn't work ?

---

### Post by ubuntu_demon on 2007-11-27
@blackhole54 :

laptop-mode is disabled by default and can't be enabled by default. The reason is system hangs on some machines : [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224)

It is probably useful to enable laptop-mode while on battery for people who don't suffer from this "system hangs"  problem and are willing to risk the last ten minutes of work in an event of a system crash. 

First the system hangs problem of laptop-mode-tools needs to be fixed to be able to recommend using laptop-mode on default. Bart Samwel (Debian maintainer of acpi-support and laptop-mode-tools) thinks laptop-mode already uses sane defaults see :
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/225](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/225)

see also : 
[http://ubuntuforums.org/showpost.php?p=3847042&postcount=507](http://ubuntuforums.org/showpost.php?p=3847042&postcount=507)
[http://ubuntuforums.org/showpost.php?p=3847255&postcount=510](http://ubuntuforums.org/showpost.php?p=3847255&postcount=510)

---

### Post by ubuntu_demon on 2007-11-27
I reported a couple of related bugs :

laptop-mode-tools uses hparm -B 255 instead of 254 please sync laptop-mode-tools from Debian to fix this
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172282](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172282)

hdparm's feedback about -B values is misleading
[https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/172287](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/172287)

using laptop-mode causes system hangs for some people
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172293](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172293)

laptop-mode should default to *always* use relatime for ext3 partitions while keeping the CONTROL_NOATIME option
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172301](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172301)

---

### Post by ubuntu_demon on 2007-11-27
> **spier said:**
> Hi,

just posting a feedback: after applying the ugly fix (maybe it could be renamed to something nicer - debian as incorporated a fix like this, too) my Load_Cycle_Count increases by one only after suspend, hibernate or a restart. 


At this stage I don't want to encourage people to use this fix unless they are heavily affected and know and understand what they are doing. 

> **spier said:**
> 
Testing on a vaio FS,  AC powered, tried many values between 128 and 254 and, apparently, 192 is the magic one  - 191 acts exactly like 128; 192 like 254.

128 will reduce power use as much as possible but not permit spin-down unless you set the spin down value using hdparm -S.
254 will disable power management

values between 128 and 254 are different for each harddisk and therefor unsuitable for a solution which works for everyone.
255 is undefined and therefor you shouldn't use it.

---

### Post by ubuntu_demon on 2007-11-27
> **gettons said:**
> Hi to everybody, this is my output on an XPS M1210 dell , 6 months aged.

Should I concern about its hard disk status?


gettons@getbuntu:~$ sudo smartctl -H /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

gettons@getbuntu:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   079   079   000    Old_age   Always       -       42361


The Load_Cycle_Count seems too high.
By battery or ac they grow up about 1 each minute.


My hard drive is a seagate ST9120822AS  , in the specs 600,000 cycles guranteed
Laptop mode not enabled in ubuntu acpi config file.
I used only xp and gentoo 2007.1 on this laptop from June, and ubuntu since the Gutsy release.

Thanks a lot in advance

If your WORST started at 100 and is now at 79 you have used roughly one-fifth of your "guaranteed" Load_Cycles. Keep watching your Load_Cycle_Count if you are worried you might consider applying the unofficial ugly fix : [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26)

---

### Post by ubuntu_demon on 2007-11-27
Everyone : please keep testing whether your Load_Cycle_Count increases while on AC after applying the updated fix. It should never do so after applying this fix except for suspending/hibernating which will probably increase it by one.

My laptop doesn't do suspend and hibernate reliably the last time I checked. **So please test suspend and hibernate** to see how it affects your Load_Cycle_Count.

---

### Post by ubuntu_demon on 2007-11-27
> **jorges00 said:**
> Hi all,
I've been following this issue as both laptops (personal and work) I use exhibit this behavior. Right now I am using the ugly fix proposed by ubuntu_demon and while I understand this a palliative measure until a not-so-ugly one is found, I think it's only addressing one of the problems, i.e. too aggressive power management. The second problem, i.e. too frequent accesses to the disk, is left untouched. I think this last problem has to be addressed somehow too, otherwise the only way to avoid killing our disks will be to sacrifice saving power, as the ugly-fix does now. I've read somewhere that there are tweaks one can do to reduce disk accesses (mount partitions noatime or relatime, disable tracker, etc.), but in my opinion it would be better if there was a global option or such that consolidated all necessary low-level tweaks.
To sum up, we need to let the disk alone for more than a few seconds if we want more than just a quick fix. 
Thanks to all the people that have raised this problem and are looking for solutions. Many of us would just be left wondering why our disks failed so soon without them.

jorges

Please read this :
[http://ubuntuforums.org/showpost.php?p=3847042&postcount=507](http://ubuntuforums.org/showpost.php?p=3847042&postcount=507)

There are already quite some bugs about unnecessary disk activity and you can help finding them :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

It would also be very useful if people set the bugs to confirmed status **if** they are able to reproduce them.

---

### Post by Jojoba86 on 2007-11-27
> **ubuntu_demon said:**
> Everyone : please keep testing whether your Load_Cycle_Count increases while on AC after applying the updated fix. It should never do so after applying this fix except for suspending/hibernating which will probably increase it by one.

My laptop doesn't do suspend and hibernate reliably the last time I checked. **So please test suspend and hibernate** to see how it affects your Load_Cycle_Count.

I tried applying the fix for both my laptop drives (Toshiba P100-123), by doing;
```
#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda
  hdparm -B 254 /dev/sdb
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 254 /dev/sda
  hdparm -B 254 /dev/sdb
fi
```
and copying it to the 4 appropriate places (set both to 254 to test). It reduces the Load_Cycle_Count but still gives me one every few minutes (the first hard drive goes off more frequently which is for Windows and /boot, the second stays on mostly which is for /). It's probably acceptably low, as the first only comes on when I check it with smartctl, but any ideas why it doesn't stop Load_Cycle_Count increasing completely?

Jj

---

### Post by lupas on 2007-11-27
Well i have install the lastest Ubunmy 7.10 on my laptop and recently my friend had told me to take care cause Gusty version can damage a hdd in two yrs or less. I have read the first 2 pages and the last page and i think that he was right . Can someone conferm me that this bug is unfixed in this version? I have a risk that my data will someday be lost because of this problem ?

---

### Post by chichilalescu on 2007-11-27
my messages were confusing, sorry.

I first said that after applying the fix nothing happened, and then I said that it worked perfectly. That is probably because I rebooted the computer between the two messages.

I used "hdparm -B 254" and nothing happened (after installing the script). I then looked at kevinbsmith's message:
> I found the answer on a different forum (sorry, can't find the link now). Some Samsung drives will ignore all attempts to set -B and/or -S parameters unless you first do:

sudo smartctl -o on /dev/sda

That enables offline data collection, which logically would have no effect, but definitely did.

I issued this command, and rebooted. afterwards, the load_cycle_count stopped increasing completely for me too.

---

### Post by samuraiCat on 2007-11-27
Hi, everyone. I used this command:

>  ~$ smartctl -d ata -H /dev/sda 

and got this output -- what is up with my count?

> ~$ sudo smartctl -s on -d ata /dev/sda

smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

~$ smartctl -d ata -H /dev/sda

(snipped out  stuff)

=== START OF INFORMATION SECTION ===
Device Model:     FUJITSU MHW2100BH
Serial Number:    NZ40T7325J2R
Firmware Version: 8918
User Capacity:    100,030,242,816 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Tue Nov 27 21:07:53 2007 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

(snipped out stuff)

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       220530
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       28639232
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       414
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       8589934592000
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       3274
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       149
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       414
182 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
184 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
185 Unknown_Attribute       0x0010   253   253   000    Old_age   Offline      -       0
186 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   253   100   000    Old_age   Always       -       0
190 Unknown_Attribute       0x0022   065   052   000    Old_age   Always       -       606011427
191 G-Sense_Error_Rate      0x0032   253   099   000    Old_age   Always       -       16580609
[COLOR="Red"]192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       5636182
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       2820[/COLOR]
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       228
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       444727296
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       17318
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       2632801059786
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         6         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):


I really don't understand how this laptop, a refurbished Presario I've had for three months, could have been improperly shut down five million times, with only 2800 or so load cycles. 

Am I looking at this wrong?

On Edit:  Okay, so that's about 18 load cycles for each hour. Is that bad? The cases I read about in Ubuntu Demon's links were over 70 per hour.

---

### Post by ubuntu_demon on 2007-11-28
> **samuraiCat said:**
> 
.............
.............
.............
I really don't understand how this laptop, a refurbished Presario I've had for three months, could have been improperly shut down five million times, with only 2800 or so load cycles. 

Am I looking at this wrong?


Your retract-count probably doesn't behave as a normal counter and uses a different internal system (for example increment with some big number after each emergency retract).

> **samuraiCat said:**
> 
On Edit:  Okay, so that's about 18 load cycles for each hour. Is that bad? The cases I read about in Ubuntu Demon's links were over 70 per hour.

If your Load_Cycle_Count is specified for 600.000 (be sure to look it up) and your average is 18 Load_Cycles per hour then you will still be below 600.000 after three years of usage. You can do the math yourself :).

Your WORST values are at 100 be sure to keep looking at them. Be sure your WORST values don't reach 1 or 0 within three years of usage.

Right now you probably don't have to apply the ugly unoffical fix. Be sure to keep watching.

---

### Post by ubuntu_demon on 2007-11-28
> **lupas said:**
> Well i have install the lastest Ubunmy 7.10 on my laptop and recently my friend had told me to take care cause Gusty version can damage a hdd in two yrs or less. I have read the first 2 pages and the last page and i think that he was right . Can someone conferm me that this bug is unfixed in this version? I have a risk that my data will someday be lost because of this problem ?

Your friend was wrong because the problem is not Gutsy specific. But some people who use Linux suffer from a Load_Cycle_Count which might reach it's specification before three years of usage (depends on the person, the way he uses his/her computer and the harddrive).

Some harddrives use aggressive power management defaults which parks the heads of the disk very fast. Most Linux distributions access the disk quite often (partly because they use ext3 which is safer for your data).  Accessing the disk unparks the heads of the disk again. Lots of parking/unparking causes mechanical stress on the disk.

Please read this and the "READ THIS FIRST" links for a better explanation :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

If you are heavily affected and you understand what you are doing then you can use the unofficial ugly fix. 

Debian uses a similar "hdparm -B 254 style fix" in acpi-support. Bart Samwel probably will also include the "'hdparm -B 128' while on battery" in Debian's acpi-support. Once that's done we can ask that Ubuntu to sync acpi-support from Debian.

---

### Post by samuraiCat on 2007-11-28
> **ubuntu_demon said:**
> 
If your Load_Cycle_Count is specified for 600.000 (be sure to look it up) and your average is 18 Load_Cycles per hour then you will still be below 600.000 after three years of usage. You can do the math yourself :).

Your WORST values are at 100 be sure to keep looking at them. Be sure your WORST values don't reach 1 or 0 within three years of usage.

Right now you probably don't have to apply the ugly unoffical fix. Be sure to keep watching.

Okay, great. Thanks for the help, your infernal majesty!

Edited to add: By the way, are laptop hard drives just inherently more prone to shorter life spans due to their use? I have a Fujitsu hard drive in my desktop computer which I use as a scratch pad. It's lasted for ten years this January! This is back when 40 gigs was a decent size. It has to have gone way beyond 600K at this point. Why is it still going?

---

### Post by ubuntu_demon on 2007-11-29
> **samuraiCat said:**
> 
Edited to add: By the way, are laptop hard drives just inherently more prone to shorter life spans due to their use? I have a Fujitsu hard drive in my desktop computer which I use as a scratch pad. It's lasted for ten years this January! This is back when 40 gigs was a decent size. It has to have gone way beyond 600K at this point. Why is it still going?

In general laptop harddrives have shorter lifetimes than desktop harddrives (harder to get rid of heat, experiences more bumps which might damage your disk if it's not parked,parking/unparking is important to save power but causes some mechanical stress).

In general laptop harddrives can handle more Load_Cycles than desktop harddrives (unless you have one of those green desktop harddrives which behave like laptop harddrives (rapid parking) and can suffer from this Load_Cycle_Count issue).

Maybe you are just lucky with your desktop drive. Or maybe it just doesn't behave like a normal counter (increments by one). You can also look at your WORST value.

---

### Post by ubuntu_demon on 2007-11-29
> **Jojoba86 said:**
> I tried applying the fix for both my laptop drives (Toshiba P100-123), by doing;
```
#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda
  hdparm -B 254 /dev/sdb
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 254 /dev/sda
  hdparm -B 254 /dev/sdb
fi
```
and copying it to the 4 appropriate places (set both to 254 to test). It reduces the Load_Cycle_Count but still gives me one every few minutes (the first hard drive goes off more frequently which is for Windows and /boot, the second stays on mostly which is for /). It's probably acceptably low, as the first only comes on when I check it with smartctl, but any ideas why it doesn't stop Load_Cycle_Count increasing completely?

Jj

I have never seen a laptop with two harddrives. Are you sure you are using two harddrives ? 

Maybe your drives are called : /dev/hda ,  /dev/hdb
For some information type : $ mount

---

### Post by Revorge on 2007-11-29
I've just installed Ubuntu for the first time, on my new Laptop, and so far i'm liking it allot. (Have some Audio problems, but im gonna figure it out).

My Load Cycle Count after 2 hours on battery is 650, and its increasing by 2-3 every few seconds. That seems pretty extreme, from what I can understand, and frankly it's making me consider, installing MS Windows on the laptop instead, even though I think Ubuntu Looks great, as i dont wont to ruin a perfectly new harddrive. 

I've run the "$ sudo hdparm -B 254 /dev/sda" and that stopped it from increasing. Would my harddrive be safe from the "tear" if I apply the ugly fix? The laptop will problably be running for 2 hours on battery per day, and a daily increase of 650 - 800 still seems like quite a bit to me...

- Edit: I've just applied the fix, and now it increases by 3 pr minute while on battery, and not at all when on AC (So the fix seems to be working). So that would be 4 - 5 years before it wears out with my usage,
which seems more fair, instead of 250 days, without the fix.

---

### Post by samuraiCat on 2007-11-29
> **Revorge said:**
> I've just installed Ubuntu for the first time, on my new Laptop, and so far i'm liking it allot. (Have some Audio problems, but im gonna figure it out).

My Load Cycle Count after 2 hours on battery is 650, and its increasing by 2-3 every few seconds. That seems pretty extreme, from what I can understand, and frankly it's making me consider, installing MS Windows on the laptop instead, even though I think Ubuntu Looks great, as i dont wont to ruin a perfectly new harddrive. 

I've run the "$ sudo hdparm -B 254 /dev/sda" and that stopped it from increasing. Would my harddrive be safe from the "tear" if I apply the ugly fix? The laptop will problably be running for 2 hours on battery per day, and a daily increase of 650 - 800 still seems like quite a bit to me...

- Edit: I've just applied the fix, and now it increases by 3 pr minute while on battery, and not at all when on AC (So the fix seems to be working). So that would be 4 - 5 years before it wears out with my usage,
which seems more fair, instead of 250 days, without the fix.

Cool! Have you figured out the audio problem?

---

### Post by Revorge on 2007-11-29
> **samuraiCat said:**
> Cool! Have you figured out the audio problem?

I have sound now, but its not perfect, so i am probably going to reinstall ubuntu,
and make a clean alsa driver update... I hobe that will help.

- With laptopmode on, and CONTROL_HD_POWERMGMT=1 i'm now down at 1 cycle pr minute on battery. Laptopmode on so far looks stable. (Hmm... load cycle now seems to increase on AC)

---

### Post by ubuntu_demon on 2007-11-29
> **Revorge said:**
> I have sound now, but its not perfect, so i am probably going to reinstall ubuntu,
and make a clean alsa driver update... I hobe that will help.

- With laptopmode on, and CONTROL_HD_POWERMGMT=1 i'm now down at 1 cycle pr minute on battery. Laptopmode on so far looks stable. (Hmm... load cycle now seems to increase on AC)

IMHO it's better to not alter your /etc/laptop-mode/laptop-mode.conf (unless you understand exactly what you are doing).

---

### Post by blackhole54 on 2007-11-30
> **Revorge said:**
> (Hmm... load cycle now seems to increase on AC)

Since you have enabled *CONTROL_HD_POWERMGMT*, make sure *LM_AC_HD_POWERMGMT* and *NOLM_AC_HD_POWERMGMT* are set to 254 instead of 255.  The consesus seems to be that if they are set to 255, the behavior will vary with disk manufacturer.  Also, I would imagine that if you are going to enable this feature, you shouldn't also be using the "ugly fix."

You can double check what is happening on AC by running

```

hdparm -I /dev/<drive> | less

```

This will return (among a bunch of other info) what the drive's APM is set to.  It will probably have something about power management in the line, but I didn't pipe the output to **grep** because the exact wording may change from disk to disk.  If it returns a hexadecimal value only (mine also returns decimal):

0xff = 255
0xfe = 254

Ubuntu_Demon's caution about not enabling laptop mode if you aren't confident what you are doing sounds like wise advice to me.

---

### Post by ubuntu_demon on 2007-11-30
IMHO we should work to improve the unofficial ugly workaround to include something like this : 
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/266](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/266)

---

### Post by ubuntu_demon on 2007-11-30
I was mostly talking about not changing /etc/laptop-mode/laptop-mode.conf 

Worst case result for enabling laptop-mode is causing system hangs for some laptops (particularly some thinkpads) causing you to lose your latest work if it hasn't been written to disk yet. I'm not recommending laptop-mode it in the workaround because I don't want to cause system hangs for anyone.But for most people laptop-mode should save some Load_Cycles while on battery.

laptop-mode tries to delay disk activity so it should help regarding Load_Cycle_Count but you will have a slightly bigger risk on dataloss (if you system crashes you might lose your latest work if it hasn't been written to the disk yet). If you decide to enable laptop-mode please report back how it affects your Load_Cycle_Count while on battery. 

**But you probably shouldn't change the /etc/laptop-mode/laptop-mode.conf unless you understand what you are doing**. So you probably should set CONTROL_HD_POWERMGMT back to 0 to make sure you use the ugly unofficial workaround.

---

### Post by ubuntu_demon on 2007-11-30
> **blackhole54 said:**
> Since you have enabled *CONTROL_HD_POWERMGMT*, make sure *LM_AC_HD_POWERMGMT* and *NOLM_AC_HD_POWERMGMT* are set to 254 instead of 255.  The consesus seems to be that if they are set to 255, the behavior will vary with disk manufacturer.  Also, I would imagine that if you are going to enable this feature, you shouldn't also be using the "ugly fix."


This is fixed in Debian's laptop-mode-tools but not yet for Ubuntu. See :

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=451589](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=451589)
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172282](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/+bug/172282)

---

### Post by bkraptor on 2007-11-30
That's weird :(

"hdparm -I /dev/sda" returns this on my drive:

Advanced power management level: unknown setting (0x80fe)

I read that this error might happen, but I have no clue whether this is serious or not.

---

### Post by blackhole54 on 2007-12-01
> **bkraptor said:**
> That's weird :(

"hdparm -I /dev/sda" returns this on my drive:

Advanced power management level: unknown setting (0x80fe)

I read that this error might happen, but I have no clue whether this is serious or not.

My guess is that is just weird reporting and the setting is really 0xfe (254).  You can check that out by using **hdparm** to manually set the value to several values and see if the lower byte (lower two hexadecimal digits) tracks with the report back from

```

hdparm -I /dev/sda

```

I don't know if you are familiar with hexadecimal, but what I am talking about (for example) is if you see the following correlations:

```

hdparm -B 254 /dev/sda  ->  0x80fe
hdparm -B 128 /dev/sda  ->  0x8080
hdparm -B 192 /dev/sda  ->  0x80c0

```

If it tracks, I would just ignore the upper byte (80) and take it as a weird artifact of your drive.

---

### Post by Jojoba86 on 2007-12-01
> **ubuntu_demon said:**
> I have never seen a laptop with two harddrives. Are you sure you are using two harddrives ? 

Maybe your drives are called : /dev/hda ,  /dev/hdb
For some information type : $ mount
I'm 100% sure I have two hard drives, many (Toshiba) 17" laptops seem to have them these days (something to take a note of for the fix being implemented in Debian?). They are certainley mounted on /dev/sda and /dev/sdb, the fix basically stops the load count increasing too quickly but it doesn't stop it completely as expected. So it's fine as a fix but I'm intrigued as to why it's still increasing.

Jj

---

### Post by bkraptor on 2007-12-01
That's exactly what happens, but what if it's not just an error when reading/parsing that paramter?

---

### Post by blackhole54 on 2007-12-02
> **bkraptor said:**
> That's exactly what happens, but what if it's not just an error when reading/parsing that paramter?

If it were my hardware, that would be enough to satisfy me that it was working unless I saw some evidence to the contrary.  Maybe that's because I've used (and written/debugged! :redface: ) enough buggy code to know that these things happen.  If you want more, all I know is to observe behavior, contact the manufacturer, or Google to find out more info.

You should probably be monitoring *Load_Cycle_Count* for a while anyway.

---

### Post by ubuntu_demon on 2007-12-04
> **Jojoba86 said:**
> I'm 100% sure I have two hard drives, many (Toshiba) 17" laptops seem to have them these days (something to take a note of for the fix being implemented in Debian?). They are certainley mounted on /dev/sda and /dev/sdb, the fix basically stops the load count increasing too quickly but it doesn't stop it completely as expected. So it's fine as a fix but I'm intrigued as to why it's still increasing.

Jj

Your Load_Cycle_Count should increase while on battery , after hibernating , probably also after suspending (not sure) . 

If it still increases while on AC try the following things : 

* Are you sure you are using apm 254 instead of 255 ?

* Maybe you should try (this is needed for some samsung drives maybe also for you drives) :

> 
smartctl -o on /dev/sda
smartctl -o on /dev/sdb


If it doesn't work turn it off again :

> 
smartctl -o off /dev/sda
smartctl -o off /dev/sdb


Please let us know whether that worked

---

### Post by Jojoba86 on 2007-12-04
> **ubuntu_demon said:**
> Your Load_Cycle_Count should increase while on battery , after hibernating , probably also after suspending (not sure) . 

If it still increases while on AC try the following things : 

* Are you sure you are using apm 254 instead of 255 ?

* Maybe you should try (this is needed for some samsung drives maybe also for you drives) :



If it doesn't work turn it off again :



Please let us know whether that worked
Nope, tried this makes no difference (Toshiba drivers FYI). Neither foes the command to make it never spin down (hdparm -S0 /dev/sdx OTOH). /dev/sdb doesn't increase the count that much (contains / and swap) whereas /dev/sda does increase a fair bit, which has a windows partition (which shares odd stuff like Thunderbird profiles) and /boot.

Maybe it's just something in my bios kicking in automatically? I think I a quicker increase on Vista (/dev/sda only, Vista doesn't use /dev/sdb), but I haven't really tested it.

---

### Post by ubuntu_demon on 2007-12-05
> **Jojoba86 said:**
> Nope, tried this makes no difference (Toshiba drivers FYI). Neither foes the command to make it never spin down (hdparm -S0 /dev/sdx OTOH). /dev/sdb doesn't increase the count that much (contains / and swap) whereas /dev/sda does increase a fair bit, which has a windows partition (which shares odd stuff like Thunderbird profiles) and /boot.

Maybe it's just something in my bios kicking in automatically? I think I a quicker increase on Vista (/dev/sda only, Vista doesn't use /dev/sdb), but I haven't really tested it.

Are you using the latest version of the unofficial ugly fix ? Are you sure you didn't make any mistakes ?

Please check whether apm is disabled while running Ubuntu on AC. It should report an apm of 254 or 0x00fe. (sudo hdparm -I /dev/sda)

Does your Load_Cycle_Count increase while using Ubuntu on AC while hdparm is reporting 254 or 0x00fe ?

---

### Post by lupas on 2007-12-05
Hi, i'm a newbie and my first experience of Ubuntu was a 2 week ago. I install  it onto my laptop which is a MSI PR600. The first thing i want to ask to you is , am i in the risk of loosing my hardisk in a less than 2yrs and secondly , could be a wise decision to me to switch back to vista?.


Thanks ( Reply me in a simple way as possible ):)

---

### Post by houstonbofh on 2007-12-05
> **lupas said:**
> Hi, i'm a newbie and my first experience of Ubuntu was a 2 week ago. I install  it onto my laptop which is a MSI PR600. The first thing i want to ask to you is , am i in the risk of loosing my hardisk in a less than 2yrs and secondly , could be a wise decision to me to switch back to vista?.
I think you have a good chance of loosing your hard drive in 2 years, and it has nothing to do with Ubuntu.  I have 10 year old 6 gig drive that have been on 24/7 with no issues.  However, I have nothing over 20 gig that is really old.  Drives are just made more cheaply.  So I assume that my drive is going to die any day now, even when new.  I sync my key data (read home directory) between my laptop and desktop regularly.  That way when (not if) my drive fails I have lost nothing.

Now your real question is will Linux kill your drive faster than Vista?  No one can really answer this question yet.  Visat does have the same issue, but no one knows for sure how big a problem it is on these new drives.  But Vista does have a lot of other known problems that Linux (or even XP) solves.  This is why I run Windows in a VM on my Ubuntu system. :)

---

### Post by lupas on 2007-12-06
> **houstonbofh said:**
> I think you have a good chance of loosing your hard drive in 2 years, and it has nothing to do with Ubuntu.  I have 10 year old 6 gig drive that have been on 24/7 with no issues.  However, I have nothing over 20 gig that is really old.  Drives are just made more cheaply.  So I assume that my drive is going to die any day now, even when new.  I sync my key data (read home directory) between my laptop and desktop regularly.  That way when (not if) my drive fails I have lost nothing.

Now your real question is will Linux kill your drive faster than Vista?  No one can really answer this question yet.  Visat does have the same issue, but no one knows for sure how big a problem it is on these new drives.  But Vista does have a lot of other known problems that Linux (or even XP) solves.  This is why I run Windows in a VM on my Ubuntu system. :)


Thanks for the reply :KS

In conclusion , both Vista and Ubuntu does not harm disks but the cheap disks that are around fails within 2yrs. My vital data are copied onto other 2 pc and of course on several dvd , just in case that my laptop dies :)

---

### Post by ubuntu_demon on 2007-12-06
@lupas :

In general laptop drives live shorter than desktop drives (more aggressive power management , less space to get rid of heat, the laptop doesn't stay in one place).

laptop harddrives use more aggressive power management than desktop harddrives. Some laptop harddrives are using very aggressive power management (set by laptop BIOS or laptop harddrive firmware).

Aggressive power management will cause your laptop's harddrive head to park quickly. Too much unnecessary disk activity and usefull disk activity such as ext3 journalling (which is safer for your data) will unpark your harddrive head quickly. This combination of aggressive power management and disk activity is causing too rapidly increasing Load_Cycle_Counts for some people.

Please read this and "READ THIS FIRST" links (you can skip the bugs and "more information") :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

The issue that some harddisks set too aggressive power management defaults is operating system independent. Journalling filesystems such as ext3 (used on Linux) generate more wake ups than non-journalling filesystems but are safer for your data. How much you are affected also depends on yourself (amount of usage, pattern of disk activity you generate, programs you run).

If you want to keep an eye on your Load_Cycle_Count you can take action if you are heavily affected (something you can't do so easily with Vista).

---

### Post by lupas on 2007-12-06
> **ubuntu_demon said:**
> @lupas :

In general laptop drives live shorter than desktop drives (more aggressive power management , less space to get rid of heat, the laptop doesn't stay in one place).

laptop harddrives use more aggressive power management than desktop harddrives. Some laptop harddrives are using very aggressive power management (set by laptop BIOS or laptop harddrive firmware).

Aggressive power management will cause your laptop's harddrive head to park quickly. Too much unnecessary disk activity and usefull disk activity such as ext3 journalling (which is safer for your data) will unpark your harddrive head quickly. This combination of aggressive power management and disk activity is causing too rapidly increasing Load_Cycle_Counts for some people.

Please read this and "READ THIS FIRST" links (you can skip the bugs and "more information") :
[http://ubuntuforums.org/showpost.php?p=3733762&postcount=1](http://ubuntuforums.org/showpost.php?p=3733762&postcount=1)

The issue that some harddisks set too aggressive power management defaults is operating system independent. Journalling filesystems such as ext3 (used on Linux) generate more wake ups than non-journalling filesystems but are safer for your data. How much you are affected also depends on yourself (amount of usage, pattern of disk activity you generate, programs you run).

If you want to keep an eye on your Load_Cycle_Count you can take action if you are heavily affected (something you can't do so easily with Vista).

Thanks for this . :) I really appriciate this and this is one from many reasons i wish to stick with Ubuntu :) I will  figure out of how i can read my cycle count. 
Thanks !

---

### Post by ubuntu_demon on 2007-12-06
> **lupas said:**
> Thanks for this . :) I really appriciate this and this is one from many reasons i wish to stick with Ubuntu :) I will  figure out of how i can read my cycle count. 
Thanks !
To see your Load_Cycle_Count information please do the following and post the result of the second command in this thread.  Please also tell us how old the harddrive is and how many hours you use it per day on average.

```

sudo aptitude install smartmontools
sudo smartctl -a /dev/sda | grep Load_Cycle_Count

```

For a more thorough explanation please read the stuff I linked you to since you should always understand the commands when using sudo.

---

### Post by punischdude on 2007-12-06
I did not read all pages of this thread, but does anybody know, when this will be fixed in gutsy or hardy? It seems to be fixed in Debian.

---

### Post by houstonbofh on 2007-12-06
> **punischdude said:**
> I did not read all pages of this thread, but does anybody know, when this will be fixed in gutsy or hardy? It seems to be fixed in Debian.
Many people feel that the "Fix" in Debian has some significant issues as well.  The problem is that if we can trust the manufactures to pick safe values, what value can we pick that is universally safe for all drives?

---

### Post by blackhole54 on 2007-12-07
> **houstonbofh said:**
> The problem is that if we can trust the manufactures to pick safe values, what value can we pick that is universally safe for all drives?

I certainly don't feel that I have a good grip on all of the issues, and from the (relatively limited) amount I've read (even though I have read a substantial amount of this and other threads) I am not yet convinced that anybody has a thorough grip on all of the issues.  But with that disclaimer, IMHO I am not sure it is simply a matter of the manufacturer picking "safe" or "sane" values.  Specifically, it seems to me that picking an appropriate APM value has to take into account what the OS and other software running on the machine is going to be doing.  For example, a setting that makes sense for an OS that typically only occasionally accesses the disk, may be a disastrous setting for an OS that frequently reads or writes to the disk.

---

### Post by blackhole54 on 2007-12-07
> **ubuntu_demon said:**
> Too much unnecessary disk activity and usefull disk activity such as ext3 journalling (which is safer for your data) will unpark your harddrive head quickly.

Can you provide a reference for why a journaling file system would cause an increase in head unparking?  I am certainly no expert in *ext3* or journaling file systems, but that is not immediately obvious to me.  (Certainly more data gets written to the disk, but I don't understand why it would not all be written in one sequence w/o an intervening head park.)  I am just trying as best I can to understand the various issues at play here.

---

### Post by bkraptor on 2007-12-07
I finally gave up using this fix because of the temperatures generated.

I was constantly getting SMART alarms because the HDD was reaching 60+ C, while in Windows and in Ubuntu without the fix I am getting ~45-48 C. I'll just have to wait for a better way to fix this.

---

### Post by ntt on 2007-12-07
My solution (does not use that fix):

1) go to the System/Administration menu and launch Services
2) once in the Services Settings, tick the checkbox for "Hard Disk Tuning (hdparm)"
3) as root, edit the file /etc/hdparm.conf  and add the following at the end:

/dev/sda {
        apm = 254
}

This is assuming that your hard disk device is named /dev/sda; launch the command   mount   in a terminal to see the actual name of your device; most probably it will be /dev/sda or /dev/hda. In case, replace /dev/sda above with the actual name of your device.

After rebooting, your HD will take the value 254 for power management automagicall,; and will keep that value as long as you leave the hdparm service active in the Services menu.

NOTE: some HD may require the value 255 instead of 254; just try 254 first, and if you don't hear any more CLICKS, you're all set.

Besides from hearing clicks, for a more scientific approach digit the following in a console:

     sudo hdparm -I /dev/sda |grep -i advanced

and you'll see something like this:

        Advanced power management level: 254 (0xfe)
                Advanced Power Management feature set

For checking the "load_cycle" situation, you may use this command:

       sudo smartctl --all /dev/sda |grep -i load

My load_cycle stopped increasing like hell after I've adopted this workaround.

Hope this helps.

--ntt

---

### Post by Jojoba86 on 2007-12-07
> **ubuntu_demon said:**
> Are you using the latest version of the unofficial ugly fix ? Are you sure you didn't make any mistakes ?

Please check whether apm is disabled while running Ubuntu on AC. It should report an apm of 254 or 0x00fe. (sudo hdparm -I /dev/sda)

Does your Load_Cycle_Count increase while using Ubuntu on AC while hdparm is reporting 254 or 0x00fe ?
No mistakes, APM is definetly 254, count increases. To repeat again it mostly increases on /dev/sda, which has a used Windows partition (Thunderbird, docs etc.) and /boot. 254 'solves' the problem, in the sense that the increase is no longer enough to be a problem.

Jj

---

### Post by ctt1wbw on 2007-12-08
> **ntt said:**
> My solution (does not use that fix):

1) go to the System/Administration menu and launch Services
2) once in the Services Settings, tick the checkbox for "Hard Disk Tuning (hdparm)"
3) as root, edit the file /etc/hdparm.conf  and add the following at the end:

/dev/sda {
        apm = 254
}

This is assuming that your hard disk device is named /dev/sda; launch the command   mount   in a terminal to see the actual name of your device; most probably it will be /dev/sda or /dev/hda. In case, replace /dev/sda above with the actual name of your device.

After rebooting, your HD will take the value 254 for power management automagicall,; and will keep that value as long as you leave the hdparm service active in the Services menu.

NOTE: some HD may require the value 255 instead of 254; just try 254 first, and if you don't hear any more CLICKS, you're all set.

Besides from hearing clicks, for a more scientific approach digit the following in a console:

     sudo hdparm -I /dev/sda |grep -i advanced

and you'll see something like this:

        Advanced power management level: 254 (0xfe)
                Advanced Power Management feature set

For checking the "load_cycle" situation, you may use this command:

       sudo smartctl --all /dev/sda |grep -i load

My load_cycle stopped increasing like hell after I've adopted this workaround.

Hope this helps.

--ntt

Is this whole situation something new, because I have been running Ubuntu since 4.10 and never had this problem.  I never noticed it with Fedora 6/7/8 either.

BTW, I did your fix.  I'll post results soon.  Thanks!

---

### Post by ntt on 2007-12-08
Yes, this problem is new to *buntu Gutsy; it happens mostly on laptops, as far as I know, because of some power management settings (you can find details about the problem in other threads).

My laptops never had a problem with K/X/Ubuntu up to version 7.04 (Feisty); as soon as I've installed Gutsy, 2 laptops out of 3 began frequently emitting loud "CLICKS" from the hard disk heads (presumably); I could see the load_cycle_count value skyrocketing in a matter of hours.

Forcing the APM parameter of hdparm to either 254 or 255 seems to fix the problem; at least, it worked for me :-).

--
ntt


> **ctt1wbw said:**
> Is this whole situation something new, because I have been running Ubuntu since 4.10 and never had this problem.  I never noticed it with Fedora 6/7/8 either.

BTW, I did your fix.  I'll post results soon.  Thanks!

---

### Post by ctt1wbw on 2007-12-08
Well so far, so good.  I've been up and running for about an hour after your change and haven't heard any of the clicks from the drive heads.  I set the apm to 254 and that seems to have worked.

However, when I enter the command:

sudo smartctl -a /dev/sda | grep Load_Cycle_Count

I get no response after I enter the root password.  Where is the output of this command?

---

### Post by ntt on 2007-12-08
my bad, forgot to mention that you need to have the package  'smartmontools'  installed in order to issue the 'smartctl' command.

--
ntt

---

### Post by ctt1wbw on 2007-12-08
No, you didn't.  I saw it previously and installed it.  Still won't give me output, though.

---

### Post by ntt on 2007-12-08
strange... no output would be 'normal', so to speak, if you issued that command being an ordinary user.  But with sudo you definitely _should_ see the output of the smartctl command.

Perhaps you might try to issue the smartctl command directly as root, instead of using sudo, and see what happens.

Ah, that command would also silently fail if you  by any chance mistyped the device name... I was experiencing this right now, because my other laptop got a PATA hd (/dev/hda) and I was cutting&pasting the command from my SATA (/dev/sda) laptop :-)

--
ntt

---

### Post by SpinningAround on 2007-12-08
Would someone please help me, with understanding if my harddrive isn't  working correct.  It was on AC power when i tested this.

The secound one is 1 min after the first one.
```

Device Model:     Hitachi HTS541612J9SA00
4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       30
12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       29
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       959

```

```

Device Model:     Hitachi HTS541612J9SA00
4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       30
12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       29
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       966

```

---

### Post by ntt on 2007-12-08
According to your figures, your Load_Cycle_Count increased by 7 in 1minute: that means roughly once every 10 secs, which I would deem as high; in principle anything beyond a few units a day should be regarded as suspicious.

As a comparison, my hd [after the fix] increases its load_cycle_count by a few units a week.

--
ntt



> **SpinningAround said:**
> Would someone please help me, with understanding if my harddrive isn't  working correct.  It was on AC power when i tested this.

The secound one is 1 min after the first one.
```

Device Model:     Hitachi HTS541612J9SA00
4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       30
12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       29
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       959

```

```

Device Model:     Hitachi HTS541612J9SA00
4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       30
12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       29
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       966

```

---

### Post by blackhole54 on 2007-12-09
> **ctt1wbw said:**
> However, when I enter the command:

sudo smartctl -a /dev/sda | grep Load_Cycle_Count

I get no response after I enter the root password.  Where is the output of this command?

You might need to:

```

sudo smartctl [color=red]-d ata[/color] -a /dev/sda

```

I would also suggest not piping it through **grep** until you see that you are getting output.   Since the *-a* option will (presumably) produce lots of output, you might want to pipe the output to **less** (a fairly nice pager).  **grep** just selects a particular line of output.  It is possible your disk isn't producing that line (or maybe the wording is different), which is why I suggest you first look at the whole output.

---

### Post by ctt1wbw on 2007-12-09
> **blackhole54 said:**
> You might need to:

```

sudo smartctl [color=red]-d ata[/color] -a /dev/sda

```

I would also suggest not piping it through **grep** until you see that you are getting output.   Since the *-a* option will (presumably) produce lots of output, you might want to pipe the output to **less** (a fairly nice pager).  **grep** just selects a particular line of output.  It is possible your disk isn't producing that line (or maybe the wording is different), which is why I suggest you first look at the whole output.


Thanks.  This is the output:

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM320JI
Serial Number:    S19FJD0PB22864
Firmware Version: 2SS00_01
User Capacity:    320,072,933,376 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Sun Dec  9 07:33:15 2007 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (  32) The self-test routine was interrupted
                                        by the host with a hard or soft reset.
Total time to complete Offline 
data collection:                 ( 120) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 120) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       26
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2750
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       4211
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       115
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       14
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2452
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       4
194 Temperature_Celsius     0x0022   163   112   000    Old_age   Always       -       25 (Lifetime Min/Max 20/42)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       5455
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       106
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       53
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         2         -
# 2  Short offline       Completed without error       00%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Interrupted [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.



I'm not too sure what I am looking for here, but thanks for the help!

---

### Post by SpinningAround on 2007-12-09
Is it possible to know when a official fix will be released? I have a lot of problem in ubuntu with this, but don't understand the problem I wont try to do anything about it since it's quite risky and advanced.

I don't think it's my BIOS that cause it since i did check throw it and didn't find any thing about it and in the manual did i find that acpi is changed in the OS.

Stuck to Vista atm :(

---

### Post by SpinningAround on 2007-12-09
> **ctt1wbw said:**
> 
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       115
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       14


I don't really understand this problem but I think you maybe isn't affected, if I'm wrong someone please say so.

But by looking and the two data that i quoted do you have less then 1 count every 8 hour

---

### Post by blackhole54 on 2007-12-09
> **ctt1wbw said:**
> Thanks.  This is the output:

```

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       26
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2750
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       4211
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       115
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       14
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2452
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       4
194 Temperature_Celsius     0x0022   163   112   000    Old_age   Always       -       25 (Lifetime Min/Max 20/42)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       5455
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       106
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       53
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

```

I'm not too sure what I am looking for here, but thanks for the help!

I trimmed your output in the quote above to the section that would contain the info of interest.  I don't see it  (but we now know why **grep** didn't produce any output.  :) ); on my disk the Load_Cycle_Count is listed as id 193.  Is this a laptop disk?  I am far from an expert, but I noticed that while my (relatively new) laptop reported *Load_Cycle_Count*, my (relatively new) desktop did not, so I am wondering if this is an issue only with laptop drives.

Edit:  I find your *Start_Stop_Count*  troubling.  I _think_ this is the number of times your disk is spinning up.  (Perhaps your disk doesn't have a mechanism for unloading the head and is just spinning down instead.  I'm just speculating.  Maybe somebody else knows.)  If this number truly reflects spin-ups, then you have averaged something like 40 spin-ups per hour, which seems excessive to me.  You might want to check and see if this is still increasing at that rate since you made the adjustment.  You might also check your disk's specs to see how many spin-ups it can tolerate.

(Thanks to SpinningAround for his/her post.  Responding to that post made me take a second look at ctt1wbw's data.)

---

### Post by blackhole54 on 2007-12-10
> **SpinningAround said:**
> I don't really understand this problem but I think you maybe isn't affected, if I'm wrong someone please say so.

But by looking and the two data that i quoted do you have less then 1 count every 8 hour

I believe the figures you are looking at show how long the disk is powered up on average.  I.e.  *Power_Cycle_Count* will increase once every time power is applied to the disk, which I think will be the same thing as the number of times the computer is turned on.

---

### Post by ctt1wbw on 2007-12-10
Yep, this is a laptop drive.  I just got a new Inspiron 1520 two weeks ago and installed Gutsy on it.  After I applied a fix above into the hdparm.conf file, I haven't heard the clicking as often.

---

### Post by ctt1wbw on 2007-12-10
Here's the new results:

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       29
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2750
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       4211
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       129
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       15
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2865
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       5
194 Temperature_Celsius     0x0022   124   112   000    Old_age   Always       -       38 (Lifetime Min/Max 20/42)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       6319
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       106
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       54
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0



I didn't notice the start_stop_count decrease for some reason.

---

### Post by blackhole54 on 2007-12-10
> **ctt1wbw said:**
> I didn't notice the start_stop_count decrease for some reason.

It's a counter;  it's not going to decrease.  But it didn't increase either -- it is exactly the same even though the disk has been running an additional 14 hours.  You seem to have stopped  it increasing with time.

I would have thought a power cycle  (of which you had one) would have bumped that counter by 1, but I guess not.  Since it isn't changing, I think you have accomplished your goal.

(To turn the counter into a rate, divide it by *Power_On_Hours*.  To look at the rate between two points in time, divide the difference in *Start_Stop_Count* by the difference in *Power_On_Hours*.)

---

### Post by BandD on 2007-12-11
I'm relatively new to all the control one has in Linux.  I just switched from XP last month to Gutsy.  

I have a Sony Viao VGN-FS with a Hitachi DK23FA-80 drive.  It isn't a SATA drive, it's a ATA-5 drive, but I'm having the load cycle issue.  I haven't been able to find if others have this problem with ATA devices (I haven't ready through all 70 pages of this thread, I just don't have the time for that, google wasn't really helpful either).  I'm not really all that concerned because this drive has been acting up for some time and I'm going to be replacing it in another 2 weeks or so.  

My main concern is that the hdparm -B 254 (or 255) trick doesn't seem to remedy the problem.  I get a message saying that the settings have been changed, but my drive still spins down several time a minute.  

But I'm worried that the new drive will have similar problems.  Is there any way to know this before hand.  I'm looking at a[ Western Digital WD1200VE]("http://www.wdc.com/en/products/Products.asp?DriveID=164") Can anyone give me some advice?  

thanks,

Dustin

---

### Post by ctt1wbw on 2007-12-11
> **blackhole54 said:**
> It's a counter;  it's not going to decrease.  But it didn't increase either -- it is exactly the same even though the disk has been running an additional 14 hours.  You seem to have stopped  it increasing with time.

I would have thought a power cycle  (of which you had one) would have bumped that counter by 1, but I guess not.  Since it isn't changing, I think you have accomplished your goal.

(To turn the counter into a rate, divide it by *Power_On_Hours*.  To look at the rate between two points in time, divide the difference in *Start_Stop_Count* by the difference in *Power_On_Hours*.)

I'm happy with the results.  This drive is much much quieter now.  :)

---

### Post by ubuntu_demon on 2007-12-11
> **Jojoba86 said:**
> No mistakes, APM is definetly 254, count increases. To repeat again it mostly increases on /dev/sda, which has a used Windows partition (Thunderbird, docs etc.) and /boot. 254 'solves' the problem, in the sense that the increase is no longer enough to be a problem.

Jj

Please try 255 and see whether this works for your harddrive. **Please let us know.**
The reason why : [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/172287/comments/1](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/172287/comments/1)

---

### Post by henriquemaia on 2007-12-11
My laptop is 4 days old its cycle count is already at  6564. This is a bit too high, no?

I have a Desktop drive with 6+ years and its cycle count is 3971.

---

### Post by blackhole54 on 2007-12-11
> **henriquemaia said:**
> My laptop is 4 days old its cycle count is already at  6564. This is a bit too high, no?

Four days is a bit short to get good statistics, but it doesn't sound good.  At this rate you might expect failure in about 400-600 days (based on a limit of 600,000 - 1 million;  but don't take me as an authority on this).  Some drives appear to increase this value by more than one each time, in which case the the number is not as bad as it appears.  Elsewhere on this thread there is discussion about this as well as using "Worst Value" from **smartctl** to estimate failure, but I am not sure where that is.  [color=red](EDIT:  The link explaining checking for counter increasing by more than one each time and using "Worst Value" is [here]("http://ubuntuforums.org/showpost.php?p=3675960&postcount=26"))[/color]

@ubuntu_demon (or anybody else)
Is it possible to search a thread (such as this thread ;) ) as you would a file?  I would have thought such a function might be in "thread tools,"  but it isn't.  Nor do I see the ability in "advanced search."

---

### Post by blackhole54 on 2007-12-11
> **BandD said:**
> It isn't a SATA drive, it's a ATA-5 drive, but I'm having the load cycle issue.  I haven't been able to find if others have this problem with ATA devices (I haven't ready through all 70 pages of this thread, I just don't have the time for that, google wasn't really helpful either).

The problem can definitely occur with ATA (IDE).  I don't know whether the problem also exists with SATA.

> My main concern is that the hdparm -B 254 (or 255) trick doesn't seem to remedy the problem.  I get a message saying that the settings have been changed, but my drive still spins down several time a minute.

Take a look at post 572 on this thread.  You can also try setting the "S" (spindown) parameter to zero:

```

sudo hdparm -S 0 /dev/sda

```

I would suggest you try setting the S parameter manually to see if it helps before committing it to a script.  (If you do commit it to a script, the script will probably be running as *root*, so you wouldn't need **sudo**.)

The only thing I know about a replacement drive is to try it and see.  Maybe somebody else knows more than I (quite likely ;) ).  Also, *ubuntu_demon* says he is keeping the first post on this thread up to date so people don't have to read the whole thread.

---

### Post by BandD on 2007-12-11
Thanks for the info!  I'll give -S 0 a shot.  

It's really not such a huge deal to me.  It's kinda a pain if it indeeds causes the dirves to crash prematurely.  But hey, the way I see it, everything is free in the Linux community.  I can buy a better higher capacity hard drive than what is in my machine now for udner $100.  I'll save that much in a year not having to update various software subsrictions and what have you in Windows.  And if I have issues, I have a wonderful community like this to help me out!

I'm also confident that the issue will be resolved in the not too distant future.  On ward ho my good fellows!

---

### Post by BandD on 2007-12-11
Well it doesn't look like the -S 0 parameter works for this drive.  Before I ran it I tired the -B 254 paramater as well.  Here are the load cycle read outs over about a 40 minute period:

```
bandd@BandD-laptop:~$ sudo hdparm -S 0 /dev/sda
[sudo] password for bandd:

/dev/sda:
 setting standby to 0 (off)
bandd@BandD-laptop:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   082   082   000    Old_age   Always       -       112413/112381
bandd@BandD-laptop:~$ date
Tue Dec 11 20:05:58 PST 2007
bandd@BandD-laptop:~$ 


bandd@BandD-laptop:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   082   082   000    Old_age   Always       -       112427/112395
bandd@BandD-laptop:~$ date
Tue Dec 11 20:19:32 PST 2007
bandd@BandD-laptop:~$ 

bandd@BandD-laptop:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   082   082   000    Old_age   Always       -       112440/112408
bandd@BandD-laptop:~$ date
Tue Dec 11 20:42:43 PST 2007
bandd@BandD-laptop:~$ 
```

So I don't know.  But, like I said, it's not a huge deal with this drive because it's getting replaced in about 2 weeks.  I'm just worried about the replacement drive.  But, even then, it's not really a life and death issue for me.  I'm happy to be XP free!!!!!

Blessings to you all!

---

### Post by henriquemaia on 2007-12-12
> **blackhole54 said:**
> Four days is a bit short to get good statistics, but it doesn't sound good.  At this rate you might expect failure in about 400-600 days (based on a limit of 600,000 - 1 million;  but don't take me as an authority on this).  Some drives appear to increase this value by more than one each time, in which case the the number is not as bad as it appears.  Elsewhere on this thread there is discussion about this as well as using "Worst Value" from **smartctl** to estimate failure, but I am not sure where that is.

@ubuntu_demon (or anybody else)
Is it possible to search a thread (such as this thread ;) ) as you would a file?  I would have thought such a function might be in "thread tools,"  but it isn't.  Nor do I see the ability in "advanced search."

Thanks for your reply. I will keep an eye on my drive and check it regularly to see how this evolves. I applied the workaround proposed by the OP nonetheless, just in case.

---

### Post by lavinog on 2007-12-12
When I select recovery mode in grub this problem goes away
the heads park once and don't come off until I actually do something.

I have a Compaq presario v5000 with a western digital hd formated ext3, and  ATI 200m video card using the proprietary driver (figure i post the video card since is screws everything else up)

After I start gdm, the hard drive will be accessed every 5 seconds or so even when idle.

Since the disk activity starts prior to logging in, we could focus on processes that exist in this state.

With windows there was a program called filemon that would tell you the name of every program that makes an io write to the file system. Is there a similar program for linux?

unfortunately it is late and cannot put anymore energy into this tonight.

---

### Post by blackhole54 on 2007-12-12
> **BandD said:**
> So I don't know.  But, like I said, it's not a huge deal with this drive because it's getting replaced in about 2 weeks.  I'm just worried about the replacement drive.  But, even then, it's not really a life and death issue for me.

Yeah, it looks like your count is still increasing about once per minute, which seems rather high to me.  TMK, the response to the -B and -S parameters of **hdparm** are solely  determined by the drive, so perhaps your new drive will respond to these commands.

Good luck.

---

### Post by blackhole54 on 2007-12-12
lavinog,

Those are interesting observations.  The behavior in recovery mode (single user mode) is not surprising since most services are not running, but the observation about GDM is intriguing.

Some people have already speculated (or observed?) that *tracker* might be an issue.  I am not sure when that is started.

The *laptop-mode-tools* package contains a script for doing some monitoring  of disk accesses.  (I'm sorry, I don't remember the name of the script and I am currently at a public computer, so I can't check.  You should be able to find out the contents of the package though.)  The purpose of the script, however, is not perfectly aligned with what I think your goals are.  The purpose is to determine which services you may wish to turn off in laptop-mode.  As such, it does *not* report *everything* that accesses the disk.  When I tried to use it for determining what was accessing the disk, I was not happy with what it was *not* reporting.  Also, be sure and answer "no" to all questions if you don't wish to change the configuration of your computer.

That is the only tool I am aware of, but I haven't actually searched for others.

---

### Post by lavinog on 2007-12-13
> **blackhole54 said:**
> lavinog,

Those are interesting observations.  The behavior in recovery mode (single user mode) is not surprising since most services are not running, but the observation about GDM is intriguing.

Some people have already speculated (or observed?) that *tracker* might be an issue.  I am not sure when that is started.

The *laptop-mode-tools* package contains a script for doing some monitoring  of disk accesses.  (I'm sorry, I don't remember the name of the script and I am currently at a public computer, so I can't check.  You should be able to find out the contents of the package though.)  The purpose of the script, however, is not perfectly aligned with what I think your goals are.  The purpose is to determine which services you may wish to turn off in laptop-mode.  As such, it does *not* report *everything* that accesses the disk.  When I tried to use it for determining what was accessing the disk, I was not happy with what it was *not* reporting.  Also, be sure and answer "no" to all questions if you don't wish to change the configuration of your computer.

That is the only tool I am aware of, but I haven't actually searched for others.
Thank you for the info.
I will give it a try when I get home

---

### Post by lavinog on 2007-12-13
What I have done so far is to start in normal mode without gdm starting
after a couple of hours i get about 5 load cycles...so far so good.

then i started gdm with sudo gdm.
watched again for another couple of hours and got another 10 load cycles. ( This contradicts what i said before and for some reason I can't seem to recreate what I got last night.)

---

### Post by blackhole54 on 2007-12-13
> **lavinog said:**
> then i started gdm with sudo gdm

I am not sure what your command will do, but I thought the standard way of starting gdm was:

```

sudo invoke-rc.d gdm start

```

Except ...  I believe that would only start it if it would normally run in the current runlevel.  I have never figured out all of the options for **invoke-rc.d**, so if I need to force it, I "cheat" and just:

```

sudo /etc/init.d/gdm start

```

I don't know if that will make any difference in you observations.

EDIT:  Once I again I am not at a computer where I can check things.  I expect to have Internet service in my apartment again "any day now." :rolleyes:

---

### Post by JimmyK377 on 2007-12-14
I've had my laptop since the start of October, Ubuntu was installed at roughly the start of November and my cycle count is 22795, and even then Ubuntu has only really been on for a large amount of the time (I use vista for most things) during two weeks in which I used it to deal with assessments.

Put simply, should I be worried?

---

### Post by lavinog on 2007-12-14
Blktrace doesn't seem to output a reason for some of the hd activity.
my hd light blinks every 2-5 secs.
dmesg (with blktrace active) only reports something every 1-5 mins
usually it reports a dirty inode, kjournald, or nmbd
why would blktrace not report the other hd activity?
Maybe I'm not understanding how it works, but if it isn't detecting every io blk would that be an indication of a root kit?

---

### Post by blackhole54 on 2007-12-14
> **JimmyK377 said:**
> I've had my laptop since the start of October, Ubuntu was installed at roughly the start of November and my cycle count is 22795, and even then Ubuntu has only really been on for a large amount of the time (I use vista for most things) during two weeks in which I used it to deal with assessments.

Put simply, should I be worried?

I am reluctant to tell people what they should and shouldn't do on this issue.  But based on a limit of 600,000,  you might be about 1/30th of the way to failure.  You might want to check out the rate of increase (say counts/hour) in Ubuntu as well as in Vista and decide what is acceptable for you.  But a rate of say 65/hour (22795/2/7/24 for a very coarse estimate from what you've said) sounds rather high to me.  For more detailed info for evaluating this, take a look at [this thread]("http://ubuntuforums.org/showpost.php?p=3675960&postcount=26").

---

### Post by blackhole54 on 2007-12-15
> **lavinog said:**
> Blktrace doesn't seem to output a reason for some of the hd activity.
my hd light blinks every 2-5 secs.
dmesg (with blktrace active) only reports something every 1-5 mins
usually it reports a dirty inode, kjournald, or nmbd
why would blktrace not report the other hd activity?
Maybe I'm not understanding how it works, but if it isn't detecting every io blk would that be an indication of a root kit?

I've not used **blktrace**, but in searching for it I did notice a couple of things I will pass on, at the risk of telling you something you already know.  There is a *Blktrace Guide* [here]("https://secure.engr.oregonstate.edu/wiki/CS411/index.php/Blktrace_Guide").  I notice that it shows examing output by means other than **dmesg**.  I also noted that *CONFIG_BLK_DEV_IO_TRACE* must be enabled in the kernel for  **blktrace** to work, and according to [this bug (wish list) entry]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/118303") it is not enabled in the default *Gutsy* kernel.  I am not sure about the *Fiesty* kernel.

Inconsistentcies, of course, can be an indication of a root kit, but I don't know if it is quite time to jump to that (alarming) conclusion.  I suspect if you check around you will find a benign explanation.   If you are seriously worried, you might want to  check out *rootkit hunter* and/or *chkrootkit*.

---

### Post by lavinog on 2007-12-15
> **blackhole54 said:**
> 
Inconsistentcies, of course, can be an indication of a root kit, but I don't know if it is quite time to jump to that (alarming) conclusion.  

Why not...people have been jumping to the conclusion that Ubuntu is destroying their hds ;)

Thanks for the info though...I will keep messing with it
I backed up my laptop so I can do some more experiments without fear of losing anything.

---

### Post by lavinog on 2007-12-15
I think I solved it.
there is a process that i guess polls /dev/hdc every 2 secs
I guess this causes the hd to move the heads.

```
ps -Af | grep polling
```
should give you something like this:
```
107       6648  6205  0 10:36 ?        00:00:00 hald-addon-storage: polling /dev/hdc (every 2 sec)

```
after killing the above process the problem goes away

If you give me some time I will let my computer run for an hour with it running and without and I can compare the load cycles.

---

### Post by lavinog on 2007-12-15
disregard this

---

### Post by blackhole54 on 2007-12-16
> **lavinog said:**
> I think I solved it.
there is a process that i guess polls /dev/hdc every 2 secs
I guess this causes the hd to move the heads.

Is /dev/hdc your hard drive or an optical drive?  [Here]("http://lists.freedesktop.org/archives/hal/2006-March/004873.html") is an explanation of what that process does.

I do thank you for clearing up the mystery of why the drive light on the laptop I bought last Jan. kept blinking.  I had finally just accepted that that was the way the universe (or at least this laptop ;) ) worked and had stopped worrying about it.  Killing that process (on *edgy eft*) causes most of the blinking to stop.  But it also prevents the desktop from knowing when a CD is inserted, and so no CD icon appears on the desktop.  :)

EDIT:  My apologies.  I posted w/o seeing post #591 (neglected to turn the page ;) ).  Have you  verified that killing that process does affect the *Load_Cycle_Count* rate?  And was *Load_Cycle_Count* ever really increasing at 30 times/minute?

---

### Post by bkraptor on 2007-12-16
> **bkraptor said:**
> I finally gave up using this fix because of the temperatures generated.

I was constantly getting SMART alarms because the HDD was reaching 60+ C, while in Windows and in Ubuntu without the fix I am getting ~45-48 C. I'll just have to wait for a better way to fix this.

After giving up on using this fix, I realized that if my APM is anything than 254, I will get a +1 on the Power-Off_Retract_Count at each shutdown. I'm using a clean install Gutsy, and this issue is supposed to have been fixed, but not for me.

---

### Post by lavinog on 2007-12-16
> **blackhole54 said:**
>  Have you  verified that killing that process does affect the *Load_Cycle_Count* rate?  And was *Load_Cycle_Count* ever really increasing at 30 times/minute?
I was about to post my results but no it didn't fix the load_cycle count issue
But everything is starting to make sense now...I was getting really concerned about the blinking activity light with no reports from blktrace.

right now I am trying to do some more research on the issue.
What I am understanding is that this behavior with the load cycle count may actually be desired for laptops.
Here are some reasons I came up with:
600,000 cycles is a pretty large number. Since there doesn't seem to be much solid evidence that hard drives will fail after 600.000 this number could very well be 1 million.  Also from an engineering standpoint this 600k limit could be a worst case scenario meaning the heads have to travel full motion. I would suspect that most hd activity does not leave the heads near the inside of the cylinder.
Also laptop hardrives are smaller than desktop harddrives so it is possible that they can handle more cycles (but could also mean they are more fragile.)

I have had ubuntu on my laptop for just over a year now and smartctl reports:
Value: 186
Raw: 42443
After some research on how smart works, it is the Value you are supposed to pay attention to. It counts down from 253. When it reaches 0 your hard drive is then considered to be in an old age condition, but still does not mean immediate failure. (you should always backup your stuff anyway).
so with my data (1-186/253)*100% tells me that my hd has used about 26.4% of its life. So I have about 3 years left on my hard drive.
Now I don't leave my laptop on all of the time...For those that have much higher rates that show that they only have 2 years of total life...they should check their warranty...my wd hd has a 3 year warranty...so if it didn't survive I get a new one.

There is a trade off. If you use your laptop as a laptop like I do then you would want to have the heads park as much as possible. If they aren't parked and you jar the laptop then you are more likely to lose your hard drive. (Makes the issue of load cycling pretty minor)
Or if you have your laptop wrapped up in bubble wrap and are careful not to touch it you could use the ugly method, BUT with the heads always on the platter will generate heat. Just a 1 degree (C) change in the overall average operating temperature could reduce the life expectancy of the hd. I haven't seen any real data but I would guess that the drop in life expectancy due to heat would be far greater than due to load cycle counts...especially since hd manufacturers seemed to be more concerned with heat issues than load cycles.

I'm going to not worry about this much more and take my chances...I would be happy if my hd lasts 3 years...if not...I think I might replace it with one of those solid state hds.

---

### Post by bkraptor on 2007-12-16
You're assuming that your heads stay parked/unloaded, but they don't and that's what this problem is all about. Something is making the hdd unpark/unload the heads almost instantly after being parked, and that's NOT good.

---

### Post by lavinog on 2007-12-17
> **bkraptor said:**
> You're assuming that your heads stay parked/unloaded, but they don't and that's what this problem is all about. Something is making the hdd unpark/unload the heads almost instantly after being parked, and that's NOT good.

they do become instantly unparked it seems but after a while of being idle my system will stay parked for about 5-10 mins at a time...after doing anything they do the whole park unpark thing again.

i have noticed that /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg is the most common non-journal process that is accessing the hd when idle.
I killed this process and klogd and I am seeing how much of a difference it makes. (I am taking a risk on this one i'm sure)

I think also using blktrace reduces the number of cycles...but i need to do more tests to be sure (went from 26/hr to 14/hr)
Edit: My power keeps going out!!! (just for a good laugh I had my xmas lights on a battery backup just so I could be the only one in my subdivision with xmas lights...hehe)
ok I was also going to add that nmbd will frequently access the drive to write to browse.dat
gconfd-2 made a couple of accesses (btw did this problem become an issue when ubuntu started using gnome2?)

I am looking to rewrite my test script to work on a ramdisk to get more accurate results.

when I finish this test with klogd killed i should check to see if it is a write or a read that it does...i forgot to note that.
In either case: what part of that process needs to access the hd i would think that the kernel would cache dd in memory. /proc/kmsg and /var/run/klogd/kmsg are in virtual memory.

---

### Post by blackhole54 on 2007-12-17
> **lavinog said:**
> What I am understanding is that this behavior with the load cycle count may actually be desired for laptops.

Unloading the head is desirable for reasons both of power savings and increased immunity to damage from jarring.  However, _excessive_ loading/unloading is not desirable.  Yes, you are right:  it is a balancing act.  But some of our computers seem to be dangerously out of balance.

> 
600,000 cycles is a pretty large number. Since there doesn't seem to be much solid evidence that hard drives will fail after 600.000 this number could very well be 1 million.  Also from an engineering standpoint this 600k limit could be a worst case scenario meaning the heads have to travel full motion. I would suspect that most hd activity does not leave the heads near the inside of the cylinder.

Also laptop hardrives are smaller than desktop harddrives so it is possible that they can handle more cycles (but could also mean they are more fragile.)


Wrt 600,000 being a large number, my computer exceeded it in aprox. 10 months.  You can see the data [here]("http://ubuntuforums.org/showpost.php?p=3653021&postcount=1").  You _might_ be right about 1 million be a more realistic number for failure, and it is _possible_ that that is about what **smartctl** is telling me.  (More on that below).    In which case, w/o remediation, my drive might have died after about 15 months.

For the drives that have it (probably most laptops?), the unload feature actually moves the "slider" (carrying the head) up onto a ramp.  My understanding is the failure comes from the wear caused by friction between ramp and slider, so it isn't an issue of how far the head traveled.  Just that it unloaded.

> 
After some research on how smart works, it is the Value you are supposed to pay attention to. It counts down from 253. When it reaches 0 your hard drive is then considered to be in an old age condition, but still does not mean immediate failure. (you should always backup your stuff anyway).

If you have a reference for the starting value being 253, I would appreciate seeing it.  My understanding is that each HD manufacturer decides what the "START" and "FAIL"  ("normalized") values used with SMART are.  In my case, the "FAIL" value is indeed 0 (for this parameter) but for a variety of reason, I _suspect_ the "START" value was 100.  Since the value is now 34, I might expect that the 663,000+ counts I have represent about 2/3 of the disk's life.  Which would mean the manufacturer was expecting the drive to be capable of about 1 million unload/load cycles.

It sounds like you have made the type of analysis for your drive that people should make and came up with a corresponding plan of action (or inaction ;) ).  Since I don't yet feel like I have a good grasp of these numbers and this situation (I am not sure anybody does yet, but with developers interested, I have hope), I don't like advising anybody what they should and shouldn't do (as I indicated a few posts back to somebody who was asking for advice.)   Like you, I have analyzed (to the best of my understanding) my situation, and have taken the remediation that I deem appropriate at this time, which is a bit different from the now famous "ugly fix."  And I am "staying tuned" to see what yet I may learn about this.

---

### Post by lavinog on 2007-12-17
> **blackhole54 said:**
> Wrt 600,000 being a large number, my computer exceeded it in aprox. 10 months.  You can see the data [here]("http://ubuntuforums.org/showpost.php?p=3653021&postcount=1").  You _might_ be right about 1 million be a more realistic number for failure, and it is _possible_ that that is about what **smartctl** is telling me.  (More on that below).    In which case, w/o remediation, my drive might have died after about 15 months.
My 2 year old desktop hard drive died a month after I moved from California to Texas...I suspect the drastic change in humidity and temperature had a lot to do with it...but either way I am pretty sure it wasn't caused by unload counts...I still have it (I could have had it replaced through maxtor's warranty)  I lost my backup of all my pictures, and decided to try and recover what I can...I spent about a year with it hooked up to a external usb interface and a old laptop...it took about 2 hours before the laptop would recognize that it was a hd...after that I could run a script that would copy a certain amount of sectors...check them for valid data and repeat until I got a certain amount of data...it took about a week to get 1 gig data...then I ran a program that analyzed the data and extracted my pictures...(I recovered about 3 of the 9 gigs so far)...a lot of my friends were able to supply me with copies of abunch of the pictures i lost...and I think my memory pretty much forgot what the missing pictures were...so i don't miss much.
to sum this up...always backup what you think may be important...AND put your backups in a place where you can find them.


> 
For the drives that have it (probably most laptops?), the unload feature actually moves the "slider" (carrying the head) up onto a ramp.  My understanding is the failure comes from the wear caused by friction between ramp and slider, so it isn't an issue of how far the head traveled.  Just that it unloaded.

I believe there is a spring type mechanism that pulls it to the parked position (its been awhile since i opened a hd). I do agree that what you mention would cause failure. I would point out though that the returning force would accelerate the head...the angular velocity of the head when returning would be dependent on the initial position of it, thus increasing the impulse to the ramp.


> 
If you have a reference for the starting value being 253, I would appreciate seeing it.  My understanding is that each HD manufacturer decides what the "START" and "FAIL"  ("normalized") values used with SMART are.  In my case, the "FAIL" value is indeed 0 (for this parameter) but for a variety of reason, I _suspect_ the "START" value was 100.  Since the value is now 34, I might expect that the 663,000+ counts I have represent about 2/3 of the disk's life.  Which would mean the manufacturer was expecting the drive to be capable of about 1 million unload/load cycles.

taken from wikipedia:
[http://en.wikipedia.org/wiki/S.M.A.R.T.]("http://en.wikipedia.org/wiki/S.M.A.R.T.")
Attribute values can range from 1 to 253 (1 representing the worst case and 253 representing the best)
I had to suspect that it started from 253 on my hd since my value is 186 currently
and on one of my linux boxes it has this
```
 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0

```
don't ask me how it hasn't ever cycled. It is running ubuntu dapper server.


I am also suspecting that it could be a non-linear relationship from other users posts like this one:
```

225 Load_Cycle_Count 0x0012 001 001 000 Old_age Always - 1387419

```
Most likely manufacturers don't use the same standards, but I can only assume that it would make more sense to use the full range of values.
I think I might have my laptop log smartctl's output each day to see if i can find a relation ship.

here is another hd in another box (its a seagate drive):
```
190 Temperature_Celsius     0x0022   059   049   045    Old_age   Always       -       724107305

```
should I be concerned that this hd is as hot as the sun?
also I should also note that its starting values for many attributes (oddly load cycle is not listed) is 100 so it is possible that yours starts at 100.

---

### Post by lavinog on 2007-12-17
I noticed post 198: [http://ubuntuforums.org/showpost.php?p=3679667&postcount=198]("http://ubuntuforums.org/showpost.php?p=3679667&postcount=198")
kind of backs what i said about 600,000 not being a number to worry about.
> The product supports a **minimum** of 600,000 normal load/unloads.

also I am going to rewrite my test script to count the number of hd access attempts per hour instead of load cycles...after disabling nmbd and samba and leaving klogd on...I notice that the hd is constantly being accessed due to dd / klogd and not even giving the hd time to unload...this maybe an issue here.

I need to get more info on how klogd works...I'll work on that tomorrow.

---

### Post by blackhole54 on 2007-12-17
> **lavinog said:**
> I noticed post 198: [http://ubuntuforums.org/showpost.php?p=3679667&postcount=198]("http://ubuntuforums.org/showpost.php?p=3679667&postcount=198") ...


I have read the first 300 posts on this thread and plan to finish reading the rest ... sometime.  I knew somewhere in there, there was link to a Hitachi white paper on this issue, which is where I got some of the info I mentioned in my last post.  Thinking it was likely around the post you quoted, I check forward a few pages, and sure enough, post #218 contains  [the link]("http://www.hitachigst.com/tech/techlib.nsf/techdoc s/9076679E3EE4003E86256FAB005825FB/$file/LoadUnloa d_white_paper_FINAL.pdf").  You might be interested in reading it.

EDIT:  Now that I think of it, there is a lot of marketing fluff in that white paper.  But I remember there also being some good info.

---

### Post by lavinog on 2007-12-18
> **blackhole54 said:**
> I have read the first 300 posts on this thread and plan to finish reading the rest ... sometime.

I am on the same boat.
It seems that majority of the posts say the same things over and over again.

---

### Post by ubuntu_demon on 2007-12-20
New possible disk activity bugs :

* tracker and cronjobs (updatedb, update-notifer,...) fight for the hard disk
[https://bugs.launchpad.net/ubuntu/+bug/152051/](https://bugs.launchpad.net/ubuntu/+bug/152051/)

* Don't install slocate by default on Desktops
[https://bugs.launchpad.net/ubuntu/+bug/140493/](https://bugs.launchpad.net/ubuntu/+bug/140493/)

---

### Post by wilksm on 2007-12-20
I have a Dell Inspiron 2600 laptop with a 20GB Hitachi Travelstar drive that's up around 1.1 million load cycles.  I have tried all the suggestions I can find on this issue including the "ugly fix" and using hdparm -B, hdparm -S manually.  Nothing seems to stop this drive from loading/unloading constantly.  The BIOS doesn't seem to have an option to turn off power management (it seems pretty limited); is there anything else I can try?

Thanks,
Matt.

---

### Post by blackhole54 on 2007-12-20
> **wilksm said:**
> I have a Dell Inspiron 2600 laptop with a 20GB Hitachi Travelstar drive that's up around 1.1 million load cycles.  I have tried all the suggestions I can find on this issue including the "ugly fix" and using hdparm -B, hdparm -S manually.  Nothing seems to stop this drive from loading/unloading constantly.  The BIOS doesn't seem to have an option to turn off power management (it seems pretty limited); is there anything else I can try?

Have you tried both 255 and 254 as value of the -B option?  I suggest trying these manually first, and not commiting one to a script until you see it is working.  

You can try the -I option with **hdparm** to see whether the -B option "took," (and for any other hints that might be in the information), but I don't know what to tell you if the value didn't "take."

---

### Post by blackhole54 on 2007-12-20
> **ubuntu_demon said:**
> New possible disk activity bugs :

* tracker and cronjobs (updatedb, update-notifer,...) fight for the hard disk
[https://bugs.launchpad.net/ubuntu/+bug/152051/](https://bugs.launchpad.net/ubuntu/+bug/152051/)

* Don't install slocate by default on Desktops
[https://bugs.launchpad.net/ubuntu/+bug/140493/](https://bugs.launchpad.net/ubuntu/+bug/140493/)

These look to me like usability and user perception issues more than things that cause head unloading/loading.

For the record, this has not been any kind of an issue for me on my two installations of *edgy* on new (last Jan.) computers.  In fact I was surprised how fast the daily jobs, including updatedb, went.  On older (last centrury!) computers, I was used to these jobs taking several minutes and making a signifciant amount of disk noise.  On the newer computers, it is taking a fraction of a minute (seconds?) with no noticeable noise.  (Beagle, on the other hand, could run for hours w/o apparently accomplishing anything. I finally disabled it.)

---

### Post by wilksm on 2007-12-21
> **blackhole54 said:**
> Have you tried both 255 and 254 as value of the -B option?  I suggest trying these manually first, and not commiting one to a script until you see it is working.  

You can try the -I option with **hdparm** to see whether the -B option "took," (and for any other hints that might be in the information), but I don't know what to tell you if the value didn't "take."
Yes, I tried both of those (and a number of others..)  I'll fiddle with -I..  Thanks for the reply.

---

### Post by lavinog on 2007-12-21
> **wilksm said:**
> I have a Dell Inspiron 2600 laptop with a 20GB Hitachi Travelstar drive that's up around 1.1 million load cycles.  I have tried all the suggestions I can find on this issue including the "ugly fix" and using hdparm -B, hdparm -S manually.  Nothing seems to stop this drive from loading/unloading constantly.  The BIOS doesn't seem to have an option to turn off power management (it seems pretty limited); is there anything else I can try?

Thanks,
Matt.
could you post the output of this
```
 sudo smartctl -a /dev/sda
```
replace sda with hda if it doesn't work

how old is your drive?
If your drive is pretty old you should be prepared for it to fail...not necessarily from the load cycles though...there are other things that can go wrong on a drive.

it is also possible that your drive reports cycles weird...there are some posts that say that their drives will report 4 cycles for every actual cycle....if this is the case then divide your 1.1 million by 4

also there are a couple of posts regarding hitachi drives having a utility that helps this issue.

---

### Post by blackhole54 on 2007-12-21
wilksm,

Just for your reference, I have a HTS541080G9AT00 drive which is in the the Hitachi Travelstar 5K100 series.  **hdparm -B 254 /dev/sda** worked fine with it.  If **hdparm**'s -I (capital "aye") option tells you that parameter isn't "taking,"  you can use Hitachi's *feature tool* (downloadable [here]("http://www.hitachigst.com/hdd/support/download.htm#FeatureTool")) to change the default value of the APM parameter, among other things.  (Just make sure you understand what you are doing!  :) )

---

### Post by stopthewar24 on 2007-12-26
Hello all,

I have read this entire thread and the last 2/3rds of the Launchpad bug report.  I'm looking for clarification on a couple aspects of this issue that I have not seen definite answers about, although I may be looking in the wrong places (or the answers may be blindingly obvious to everyone else).  Specifically, I'm wondering about how Windows and Ubuntu differ in regard to hard drive head parking.

It seems to be a widely-held assumption that computers running Windows (for clarity, let's limit this to all flavors of XP and Vista) do not suffer from an excessively-high load cycle count.  As I see it, there are only two possible explanations for this.  Either...
[B]
The vast majority of Windows configurations do not touch the hard drive anywhere near as often as the vast majority of Ubuntu configurations[/B][I]

Meaning that Windows has virtually no idle-writers, most 3rd-party Windows programs are not idle-writers, and laptop hard drives running Windows are therefore parked most of the time.[/I]

Or...
[B]
The vast majority of Windows configurations do not park the hard drive anywhere near as often as do most Ubuntu configurations[/B]
[I]
Meaning that **either **Windows overrides default power saving for notebook hard drives **or **has enough idle-writers and other processes to create enough disk activity to prevent the disk from being parked.  Also, this would mean that most concerns about hard drives overheating on Ubuntu using the "ugly fix" with head-parking disabled are unfounded, or at least the hard drive would also overheat on Windows under normal use.[/I]

Am I pretty much right in my logic here?  I appreciate that this is a complicated issue and I know it's probably not as clear-cut as I'm making it out to be.  The forum posts I've read seem to indicate that the second scenario (Windows almost never parks the hard drive) is correct, but then why does there seem to be such a concern about excess heat damaging the drive under Ubuntu?  I know Windows is far from being a perfect operating system, but it is so widely used that I find it hard to believe that it inflicts much unreasonable harm on notebook hard drives.  It seems like it should be possible, and not exceedingly difficult, to find out approximately how often Windows computers park their hard drive heads.  If Ubuntu can be made to treat hard drives the same way Windows does, wouldn't this be a reasonable solution for the time being? 

Thanks for your time.

---

### Post by blackhole54 on 2007-12-28
stopthewar24,

I'll take a stab at answering your post with the following disclaimers:  1)  I am definitely not an authority on this subject, and 2)  the most recent MS software I have on any of my machines is Win95 (which I seldom boot into), so I don't know that much about MS software either (nor do I wish to become an expert).

You logic seems reasonable to me.  My take on what I have read on this issue is that MS software (by default, at least) leaves the APM of disk drives in their default state and simply disturbs parked heads less often.  Somewhere earlier on this thread (sorry, I don't know how to search this thread and don't remember where it was) I posted about my brief experiment with enabling *laptop-mode*.  This would seem to me to be a way that is designed, among other things, at unparking the head less frequently.  My brief experiments with it seemed encouraging.  But as was pointed out to me, there are issues with some laptops hanging with *laptop-mode* enabled.  IMHO, from what little I know at this point, *laptop-mode* would seem to be the correct way out of this issue in the Linux world.  But Linux based OSes are works-in-progress, so it may take a while before the snags in *laptop-mode* are worked out.  I believe developers are working on it.  In the meantime, there are the work-arounds you have seen discussed.

That is my take on the matter, recognizing I am nowhere near an authority on this. Others may, of course, disagree with my conclusion.

---

### Post by ntt on 2007-12-28
Hi,

I tend to look at this unfortunate problem from a different angle: to me, the point is just that Ubuntu 7.10 Gutsy had a bug. I'd like to highlight that this problem is related to Ubuntu 7.10 Gutsy only; not before Gutsy, and hopefully never again in the future.

In fact Gutsy introduced an aggressive default power management setting for hard disks, which - under certain conditions - caused excessive (unnecessary) heads parking movements, causing in turn some excessive strain of the HD components.

All in all, I wouldn't infer too much from this Gutsy bug: it' just a bug, it will be stomped, and we'll have learned something more in the process (if anything, now a lot of people knows about hdparm, SMART, power states and the like :-)).

One last thing: as far as I know, Windows accesses the hard disk at least as much as any Linux distribution, and possibly even a little more because of its long-standing 'vice' of abusing the swapfile. And that is by design, mind you, not because of bugs...

cheers,

--
ntt


> **stopthewar24 said:**
> Hello all,

I have read this entire thread and the last 2/3rds of the Launchpad bug report.  I'm looking for clarification on a couple aspects of this issue that I have not seen definite answers about, although I may be looking in the wrong places (or the answers may be blindingly obvious to everyone else).  Specifically, I'm wondering about how Windows and Ubuntu differ in regard to hard drive head parking.

It seems to be a widely-held assumption that computers running Windows (for clarity, let's limit this to all flavors of XP and Vista) do not suffer from an excessively-high load cycle count.  As I see it, there are only two possible explanations for this.  Either...
[B]
The vast majority of Windows configurations do not touch the hard drive anywhere near as often as the vast majority of Ubuntu configurations[/B][I]

Meaning that Windows has virtually no idle-writers, most 3rd-party Windows programs are not idle-writers, and laptop hard drives running Windows are therefore parked most of the time.[/I]

Or...
[B]
The vast majority of Windows configurations do not park the hard drive anywhere near as often as do most Ubuntu configurations[/B]
[I]
Meaning that **either **Windows overrides default power saving for notebook hard drives **or **has enough idle-writers and other processes to create enough disk activity to prevent the disk from being parked.  Also, this would mean that most concerns about hard drives overheating on Ubuntu using the "ugly fix" with head-parking disabled are unfounded, or at least the hard drive would also overheat on Windows under normal use.[/I]

Am I pretty much right in my logic here?  I appreciate that this is a complicated issue and I know it's probably not as clear-cut as I'm making it out to be.  The forum posts I've read seem to indicate that the second scenario (Windows almost never parks the hard drive) is correct, but then why does there seem to be such a concern about excess heat damaging the drive under Ubuntu?  I know Windows is far from being a perfect operating system, but it is so widely used that I find it hard to believe that it inflicts much unreasonable harm on notebook hard drives.  It seems like it should be possible, and not exceedingly difficult, to find out approximately how often Windows computers park their hard drive heads.  If Ubuntu can be made to treat hard drives the same way Windows does, wouldn't this be a reasonable solution for the time being? 

Thanks for your time.

---

### Post by lavinog on 2007-12-28
> **ntt said:**
> Hi,

In fact Gutsy introduced an aggressive default power management setting for hard disks, which - under certain conditions - caused excessive (unnecessary) heads parking movements, causing in turn some excessive strain of the HD components.


Where did you get this information?
I am pretty sure that it was pointed out that Gusty doesn't change the default power management setting for the hard disk at all...the problem is that hd manufacturers set the drives to park the heads aggressively and gusty doesn't do anything to stop it...

It has been a while since I have used windows on my laptop, but I don't remember ever hearing the clicking noise that I have become recently quick to recognize...which leads me to believe that the heads never get parked...I have to do some work using windows this weekend and I will keep a closer watch.

---

### Post by blackhole54 on 2007-12-28
> **ntt said:**
> Hi,

I tend to look at this unfortunate problem from a different angle: to me, the point is just that Ubuntu 7.10 Gutsy had a bug. I'd like to highlight that this problem is related to Ubuntu 7.10 Gutsy only; not before Gutsy, and hopefully never again in the future.

Part of the reason I have a different perspective is because I have a notebook which is now almost a year old.  Most of the time (90+ %) it has been running *edgy*.  The rest of the time it has run various live CDs or Knoppix from the HD, but otherwise like a live CD.  Before disabling APM on the drive, it had averaged aprox 3.5 load cycles/min to a total of over 600,000.  The data is [here]("http://ubuntuforums.org/showpost.php?p=3653021&postcount=1").  Also, I believe originally the *Load_Cycle_Count* issue was reported on *feisty*, not *gutsy*.

EDIT:  [Here]("http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear") is one of the early stories on this issue, dated Oct 24, 2007.  It reports both *feisty* and *gutsy* as having the issue.  (I believe some of the data in the  story, such as it being related to *lap-top* mode have since been shown not to be true.)

---

### Post by Arkku on 2007-12-29
I also have the increasing Load_Cycle_Count problem on my 64-bit desktop machine running Gutsy. I tried applying the "ugly fix" with hdparm -B 254 (and 255, 128, 192 and finally every value between 0 and 255). However, it doesn't appear to be supported for my drive, as it causes an error every time (with every value for -B):

```
# hdparm -B 254 /dev/sda
/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error

# dmesg | tail
[13700.775779] ata1: SATA link down (SStatus 600 SControl 300)
[13700.775785] ata1: failed to recover some devices, retrying in 5 secs
[13702.953980] ata1: hard resetting link
[13703.174523] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[13703.187888] ata1.00: configured for UDMA/133
[13703.187910] ata1: EH complete
[13703.188702] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[13703.188719] sd 0:0:0:0: [sda] Write Protect is off
[13703.188721] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
```

I also tried the hdparm -S 0, which I can successfully apply, but it doesn't help. Load_Cycle_Count still increases several times a minute (in increments of 1). As this machine is going to be on 24/7, and the Western Digital WD7500AACS drive is rated to 300,000 cycles, it would exceed the limit in less than a year.

I also tried tuning various settings to lessen the disk activity, but in the end found that I would need to set excessively long delays in ext3 commits (mount -t ext3 -o commit=xxxx) and /proc/sys/vm/dirty_writeback_centisecs, to alleviate the problem somewhat, and still it wouldn't go away entirely.

In the end, I set up the following even-uglier-than-the-other-ugly-fix -fix:

```
#!/bin/bash
DELAY=7
PIDFILE=/var/run/syncer.pid
echo $$ >"$PIDFILE"
trap "rm -f $PIDFILE" EXIT
while sync; do
    sleep $DELAY
done
```

I run the above script at all times and have a cron-job to restart it if it isn't running, as well as to log increases in Load_Cycle_Count... how's that for paranoia? =)

This keeps the drive busy just often enough that it doesn't park its heads at all. Load_Cycle_Count stopped increasing altogether after this. Drive temperature (as reported by smartctl) remains at a nice 28°C and the power drawn from the mains by the system is also pretty much the same. Yet, I wish there was a better fix available, so that I might stop this madness. Any suggestions?

---

### Post by ntt on 2007-12-29
I think to remeber I've read this somewhere, but can't remember where.

In any event, bear with me for a moment:

 I have 3 laptops, which I've upgraded from 7.04 to 7.10: none of them shown any problem with Feisty, but two of them started emitting the infamous CLICKs after installing Gutsy.
(why two yes and the 3rd no, it beats me... but they're from different brands, with completely different hardware - cpu, chipset, hard disk, you name it - so they're not the same)

Anyway none of my laptops ever emitted before the loud clicks I've noticed after installing Gutsy; as a matter of fact, the load_cycle_count of the two notebooks affected by the problem was still relatively low, meaning it started skyrocketing only with Gutsy.

thus the only possible explanation is that Gutsy introduced a change somewhere which caused the problem with certain hardware; considering that simply setting the APM of the hard disk to 254  fixed the problem, I would dare to say that the change Gutsy introduced should be in the power management department...

About Windows not causing the HD heads to click... well, neither OpenSUSE nor Ubuntu Feisty ever caused a single click from my two older laptops, for that matter :-)

I think it's just a Gutsy thing, at least judging from my own experience with (some of) my hardware.


> **lavinog said:**
> Where did you get this information?
I am pretty sure that it was pointed out that Gusty doesn't change the default power management setting for the hard disk at all...the problem is that hd manufacturers set the drives to park the heads aggressively and gusty doesn't do anything to stop it...

It has been a while since I have used windows on my laptop, but I don't remember ever hearing the clicking noise that I have become recently quick to recognize...which leads me to believe that the heads never get parked...I have to do some work using windows this weekend and I will keep a closer watch.

---

### Post by ntt on 2007-12-29
Hang on a moment... I recalled a fact: this (Gutsy, I mean) is the first time I've installed a **64-bit** version of Ubuntu on my laptops!

As Blackhole54 reported, the problem has already surfaced with Feisty; alas, 32-bit Feisty never caused a problem on my laptops, but 64-bit Gutsy definitely did raise hell for 2 out of the same 3 laptops.

Laptop-mod is not activated on my machines, so this isn't the right explanation for me.

This is pure speculation on my side, but is it possible that the problem is occurring on 64-bit versions of Ubuntu???

--
ntt

---

### Post by blackhole54 on 2007-12-30
> **Arkku said:**
> I also have the increasing Load_Cycle_Count problem on my 64-bit desktop machine running Gutsy. I tried applying the "ugly fix" with hdparm -B 254 (and 255, 128, 192 and finally every value between 0 and 255). However, it doesn't apper to be supported for my drive, as it causes an error every time (with every value for -B):

Hmmm.  This is the first time I remember seeing this issue reported on a *desktop* machine (not that I am any expert).  I have a desktop machine with a SATA drive which also reports an error for any attempt to use the -B option.  However, this drive also does not report *Load_Cycle_Count*.

One thing you might consider, is taking a look at the output of **hdparm** with the with "-I" (capital "aye" for information) option.  If it shows *Power Management Feature Set* enabled, you might see if there is a tool from the disk manufacturer that will allows you to disable this, and see if that helps.  You do this at your own risk.

---

### Post by blackhole54 on 2007-12-30
> **ntt said:**
> This is pure speculation on my side, but is it possible that the problem is occurring on 64-bit versions of Ubuntu???

From what I've seen and read, it sounds like this problem manifests itself differently on different hardware, if at all.  So, from my limited knowledge, I would think it is possible that on *your* hardware it might manifest itself on 64-bit version(s) but not 32-bit.  I can tell you I have had a problem on 32-bit *edgy*.  I believe there have been other people who have reported problems on 32-bit systems.

---

### Post by ntt on 2007-12-30
mmmm, then I have no clues. it definitely happened to me with Gutsy 64-bit, but of course I understand it's a severely *limited* sample to draw conclusions from.

for those of us still in deep... water - i.e. people with HW hdparm refuses to run on - we can only hope that a future update of the kernel (or APM, or whatever is causing the problem) will fix the problem for good.

I'd be curious to learn why hdparm doesn't work with some HW configurations, though.

> **blackhole54 said:**
> From what I've seen and read, it sounds like this problem manifests itself differently on different hardware, if at all.  So, from my limited knowledge, I would think it is possible that on *your* hardware it might manifest itself on 64-bit version(s) but not 32-bit.  I can tell you I have had a problem on 32-bit *edgy*.  I believe there have been other people who have reported problems on 32-bit systems.

---

### Post by Arkku on 2007-12-30
> **blackhole54 said:**
> If it shows *Power Management Feature Set* enabled, you might see if there is a tool from the disk manufacturer that will allows you to disable this, and see if that helps.  You do this at your own risk.

I actually tried this, too, but the tools from Western Digital don't seem to have the option to do so (if someone knows a tool for it, I'm all ears). I also tried other manufacturers' tools, but they refused to adjust power management for my drive, probably due to the same incompatibility as with hdparm. They probably try to adjust the *advanced* power management, which my drive doesn't seem to have as an option...

---

### Post by lavinog on 2007-12-30
> **ntt said:**
> 
(why two yes and the 3rd no, it beats me... but they're from different brands, with completely different hardware - cpu, chipset, hard disk, you name it - so they're not the same)

most likely the hard drives are made by different manufacturers and have different power management alogarithims

> 
Anyway none of my laptops ever emitted before the loud clicks I've noticed after installing Gutsy; as a matter of fact, the load_cycle_count of the two notebooks affected by the problem was still relatively low, meaning it started skyrocketing only with Gutsy.

There are a couple of different kinds of clicks a hard drive can make...the clicks that this thread is referring to should not be really loud...they are more like a single tap that occurs every couple of seconds. If you are getting a loud click (especially if it repeats more than once in two seconds) it could be an indication of head failure.
Just want to make sure you know.

> 
thus the only possible explanation is that Gutsy introduced a change somewhere which caused the problem with certain hardware; considering that simply setting the APM of the hard disk to 254  fixed the problem, I would dare to say that the change Gutsy introduced should be in the power management department...

The change would be introducing new and updated software (including a newer kernel)...I doubt it has anything to do with hardware drivers or power management, but software causing repeated activity on the hard drive.  Setting the APM of the hard disk to 254 is not a fix it just disables the power management for the hard drive...which is fine for some people...personally I would like to see if we can find the culprit to the repeated hard drive activity and see if we can get it to play better.

---

### Post by blackhole54 on 2007-12-31
[> **Arkku said:**
>  I also tried other manufacturers' tools, but they refused to adjust power management for my drive, probably due to the same incompatibility as with hdparm. 

I'll admit to being a novice in this area, but I wouldn't expect one manufacturer's software to work on another brand of drive.  In fact, I would think it would be dangerous to try.

See if  [this WD page]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=958&p_created=1050530240") is of any help.

---

### Post by anjilslaire on 2007-12-31
I realize this thread is huge, but I saw a post a while back that said the ugly fix only applies depending on what mode the laptop is booted in (AC or battery mode). To workaround this, couldb't we also drop this script into /etc/init.d/ to load on boot? Then it would determine what mode the laptop is in a set hdparm appropriately?

---

### Post by yesint on 2008-01-01
Dear All,
I'm worried about the issue of hard drive lifespan in Linux because I've swithed to Linux completely now. My drive seems to be affected. However, this thread is already so overloaded that it is not possible to understand what is going on now. 
I'd like to ask few stupid (or probably not so stupid) questions for technical people here:

1) As far as I understand the biggest problem in parking hard drive heads in Linux is that ext3 filesystem is constantly accessing the disk even if the user is doing nothing, while this is not the case in Windows. So, why not just use not-journalized fs on laptops? 
2) Are there any really consistent comparisons of the disk usage in Linux and Windows? If, so I think it would be interesting for everybody to read them.
3) The bug tracker says that this bug is fixed in Debian now (as far as I can understand). So what is the problem to port this fix to ubuntu and any other distribution?
4) Is the "ugly fix" the only way to deal with the problem now? Are there any plans to release an official update (hopefully not so "ugly") at some point?

I'm affraid that I have to think about going back to Windows because I don't want to use free software, which kills my hardware (which is not free)...

---

### Post by ogcub on 2008-01-01
I did little investigation on my laptop with hard drive, which is reported as affected and noticed few interesting things.
first
```

	Model Number:       HTS541060G9AT00                         
	Serial Number:      MPB3LGXGJRG33T
	Firmware Revision:  MB3OA60A

Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Vendor, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: 128 (0x80)
	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns

```
so by default apm is at 128
This bug is not present, disk never spins-down;

then I execute 
```
hdparm -B 1  /dev/sda
```
Still nothing, bug is not present, hard drive never spins down;
Then I reset apm to 128 and set spin down time to 10 seconds
```
hdparm -B 128  /dev/sda
hdparm -S 2  /dev/sda
```
bug appears, hard drive spins down after ten seconds and then spins up quickly because Ubuntu won't let it sleep;
then I try
```
hdparm -B 1  /dev/sda
hdparm -S 2  /dev/sda
```
same things happen, bug is present
then i try
```
hdparm -B 254  /dev/sda

```
and 
```
hdparm -B 255  /dev/sda

```
It doesn't help, bug still present
then i fix stand by time to bigger value
So for me bug is directly related to spin down time and not to apm values
```
hdparm -S 10  /dev/sda

```
bug disappears (because hard drive can't spin down at all, due to Ubuntu)

Well, whats interesting to me is how apm values are related to spin down time? for me if I set hard drive to spin down after ten seconds of inactivity it does that, no matter what.

---

### Post by Arkku on 2008-01-01
> **blackhole54 said:**
> 
I'll admit to being a novice in this area, but I wouldn't expect one manufacturer's software to work on another brand of drive.  In fact, I would think it would be dangerous to try.

See if  [this WD page]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=958&p_created=1050530240") is of any help.

Well, like I said, I couldn't find a WD tool to do this, so I checked other manufacturer's tools. For "standard" features (similar to those controllable by hdparm), they tend to work regardless of the make of the drive (e.g. I think IBM's Drive Fitness Test is a pretty good software for testing drives and setting the acoustic management, in cases where one can't (yet) boot to Linux). The linked page contains instructions on how to set the jumper which causes the drive to start up in "stand-by mode", i.e. the drive won't spin up for the first time until told by the software. It doesn't help in this case, especially as that power saving mode is off by default (and is required to be off for my computer to boot from the drive).

Meanwhile, I'm now going to try different values for the -S parameter in hdparm, as discussed in the post above this... I'll let you know if anything changes.

P. S. Happy new year, everyone. =)

---

### Post by blackhole54 on 2008-01-01
> **anjilslaire said:**
> I realize this thread is huge, but I saw a post a while back that said the ugly fix only applies depending on what mode the laptop is booted in (AC or battery mode). To workaround this, couldb't we also drop this script into /etc/init.d/ to load on boot? Then it would determine what mode the laptop is in a set hdparm appropriately?

Disclaimer:  I don't use the "ugly fix" and have not analyzed it in detail.

But from my casual examination of it, I_ believe_ it sets the disk's APM appropriately (as desired according to battery/ac_power) at boot time, as your proposal would do.  Unlike your proposal, however, I _believe_ it will also do this when the computer comes out of either type of suspend, and will dynamically change the setting when the power status (battery/ac) changes.

---

### Post by blackhole54 on 2008-01-01
> **ogcub said:**
> So for me bug is directly related to spin down time and not to apm values.

The problem (when it manifests) is caused by the OS quickly loading (think unparking) the head quickly after it has been unloaded (parked).  Apparently on your drive, setting a low APM level mysteriously does not cause the head to unload.  I believe spinning down the drive always will.  So what you say seems to be true for your machine.  But for many machines,  a low APM value will also cause it.

---

### Post by blackhole54 on 2008-01-01
Please note:  **I am not trying to tell anybody what they _should_ do with their computer.  I am trying to give information so people can make (hopefully) informed decisions themselves.  If you don't understand what you are doing, please don't do anything.**

> **yesint said:**
> 1) As far as I understand the biggest problem in parking hard drive heads in Linux is that ext3 filesystem is constantly accessing the disk even if the user is doing nothing, while this is not the case in Windows. So, why not just use not-journalized fs on laptops? 

I am not sure that the problem rests with the *ext3* filesystem or journaling.  (As always, I could be wrong.)  If you are experiencing this problem, you can disable journaling (changing *ext3* -> *ext2*) with the **tunefs** command and see if it helps.  **Do not do this if you don't know what you are doing.  I am not responsible for what happens.**  Also note that **the file sytem must not be mounted when you execute ***tune2fs*.  **The simplest way is to do this from a live CD.**   Please review the *man page* before proceeding.  Adjust the following commands to reflect the partition you wish to adjust.

You can disable journaling (*ext3* -> *ext2*) with:

```

tune2fs -O ^has_journal /dev/sda1

```

Disabling journaling means that your filesystem will need to be checked whenever the computer is improperly shut down.  You probably should also make sure it is set up to periodically check the filesytem.  Keep in mind the reason journaling file systems were created in the first place.

To enable journaling (*ext2* -> *ext3*):

```

tune2fs -O has_journal /dev/sda1

```

You may also want to use the -J (the letter "jay") option when enabling journaling.


> I'm affraid that I have to think about going back to Windows because I don't want to use free software, which kills my hardware (which is not free)...

The decision, of course, is yours.  But if **smartctl** shows that you have adequately remedied this problem, I don't know why you would want to.  I have not followed the Debian bugtracker, but my impression is their solution is much like the "ugly fix" talked about on this thread.

---

### Post by ogcub on 2008-01-02
> **blackhole54 said:**
> The problem (when it manifests) is caused by the OS quickly loading (think unparking) the head quickly after it has been unloaded (parked).  Apparently on your drive, setting a low APM level mysteriously does not cause the head to unload.  I believe spinning down the drive always will.  So what you say seems to be true for your machine.  But for many machines,  a low APM value will also cause it.

Thanks, now I have read all the posts here and in bug report, and see spin-down and head parking are not the same things. However bug was present at some time, because I have ~37000 load cycles in in 866 hours. Was something changed in hardy Alphas?

Well, I gues, it's time to install Gutsy again...

---

### Post by yesint on 2008-01-02
I was playing with this problem yesterday and did a lot of googling, so the situation is more or less clear for my hard drive now. I hope this will also be interesting for other users of such laptops.
**The hard drive of Dell xps 1330 (and probably all other in xps series) is affected by this bug. **The disk spins down every ~1min, which is clearly indicated by the clicks. After the click the cycle counter increases by 1. The bug is present in ubuntu/kubuntu and Mandriva 2008 (I didn't try other distros). 
There is a patch for laptop_mode proposed for Mandriva, which is doing essencially the same as the ugly fix for ubuntu.
After applying this fix (or an ugly fix) clicks dissappear, but you can feel that the temperature of the laptop is higher.
I've asked Dell tech support if they know about this issue and if it is solved in their remastered pre-installed ubuntu. I'll post a reply hear.

---

### Post by starise on 2008-01-02
I have a Dell XPS M1330 with hitachi 7k200 and I confirm this bug! :(

---

### Post by jespdj on 2008-01-02
Me too, my Dell XPS M1330 has a 160 GB Seagate harddrive and I too have the load cycle problem.

---

### Post by blackhole54 on 2008-01-02
> **ogcub said:**
> However bug was present at some time, because I have ~37000 load cycles in in 866 hours. Was something changed in hardy Alphas?

Well, I gues, it's time to install Gutsy again...

Whatever you decide to use, I suggest you monitor the situation for a while.  Your lifetime average is a little over 40 cycles/hour.  That means either you had an *extraordinarily* high spike for a short period of time, or you have had a significant rate for a *prolonged* period of time.  I would bet on the latter.  While I suggest monitoring, you probably have a long ways to go before you (potentially) get in trouble.

If you want to monitor, an easy way is to add one or more lines to your */etc/rc.local* file to log info on each boot.  Make sure to add them before the *exit* command!  (Yeah, I've made that mistake!)

Below are the lines that I use.  You can adapt them or create your own.  Whichever, verify that it logs what you want.  The **sed** command and the $REGEXP variable just shorten the logged line, leaving out some data I didn't care about.  You can omit them if you want the whole line.  This will log (at least on my drive)  *Power_On_Hours* (ID #9), *Power_Cycle_Count* (ID #12), *Power-Off_Retract_Count* (ID #192), and *Load_Cycle_Count* (ID #193).  The logged lines will be less than 80 charcters (that's what **sed** does) and will include ID#, parameter name, VALUE, WORST, THRESH, and RAW_VALUE.

```

SMART_LOG=/var/log/SMART.log
REGEXP="\\(.*\\)0x[[:xdigit:]]*[[:space:]]*"
REGEXP="${REGEXP}\\([[:digit:]][[:digit:][:space:]]*\\)"
REGEXP="${REGEXP}[^[:digit:]]*\\(.*\\)$"

date >> $SMART_LOG
smartctl -d ata -A /dev/sda | egrep "^  9|^ 12|^19[23]" | \
   sed "s/^$REGEXP/\1\2\3/"  >> $SMART_LOG
echo >> $SMART_LOG

```

EDIT:  If you go long periods of time w/o rebooting your computer, you could instead put the above lines in a script and add that script to the */etc/cron.daily* directory.  That way it will run once a day.  Just be aware that (by default) the script won't run while on battery.

---

### Post by yesint on 2008-01-02
One more important observation:
**The reason of the problem (at least at xps1330) seems to be the ext3 journalling! **
I've installed ubuntu with ext2 (dual boot) to free partition and the cycle counter doesn't increase at all if I'm working on ext2. I didn't try to switch journalling on ext3 off as was suggested, but I guess that this should resolve the problem as well.
Imho, developers should pay some attention to this. If this is really the case the best solution is to set ext2 as default file system for laptops and ext3 for desktops during the installation.

---

### Post by ogcub on 2008-01-02
I continued my investigation: installed fresh Gutsy and yeah the bug starts to shine. However i cant reproduce it on hardy alpha2. I'am starting to think that this bug is related not to apm, but to Kernel version. Hard disk setting are the same for all versions, but it happens on gutsy(2.6.22) and does not  happen on Alpha2 (2.6.24). However my Hardy is full of random software, which might prevent disk from idling.
I am starting to think this is kernel issue, rather than some apm settings

I suggest for everyone to try Hardy alpha2 and test this bug there.

---

### Post by yesint on 2008-01-02
> **yesint said:**
> One more important observation:
**The reason of the problem (at least at xps1330) seems to be the ext3 journalling! **
I've installed ubuntu with ext2 (dual boot) to free partition and the cycle counter doesn't increase at all if I'm working on ext2. I didn't try to switch journalling on ext3 off as was suggested, but I guess that this should resolve the problem as well.
Imho, developers should pay some attention to this. If this is really the case the best solution is to set ext2 as default file system for laptops and ext3 for desktops during the installation.

Ups, I'm sorry that's wrong. I had some task on the background which was using the disk heavily. The problem is still there for ext2. Sorry for mistake :(

---

### Post by yesint on 2008-01-02
> **ogcub said:**
> I continued my investigation: installed fresh Gutsy and yeah the bug starts to shine. However i cant reproduce it on hardy alpha2. I'am starting to think that this bug is related not to apm, but to Kernel version. Hard disk setting are the same for all versions, but it happens on gutsy(2.6.22) and does not  happen on Alpha2 (2.6.24). However my Hardy is full of random software, which might prevent disk from idling.
I am starting to think this is kernel issue, rather than some apm settings

I suggest for everyone to try Hardy alpha2 and test this bug there.

Can you test this on a clean Hardy system? I've just made a stupid mistake because of the background program accessing the disk...

---

### Post by ogcub on 2008-01-02
> **yesint said:**
> Can you test this on a clean Hardy system? I've just made a stupid mistake because of the background program accessing the disk...

Yep, I will test soon.

Meanwhile I was reading my drive specification and noticed few interesting things
```

 11.7 Advanced Power Management (ABLE-3) feature
This feature provides power saving without performance degradation. The Adaptive Battery Life Extender 3
(ABLE-3) technology intelligently manages transition among power modes within the device by monitoring access
patterns of the host.
This technology has three idle modes: Performance Idle mode, Active Idle mode, and Low Power Idle mode.
This feature allows the host to select an advanced power management level. The advanced power management level
is a scale from the lowest power consumption setting of 01h to the maximum performance level of FEh. Device
performance may increase with increasing advanced power management levels. Device power consumption may
increase with increasing advanced power management levels. The advanced power management levels contain
discrete bands, described in the section of Set Feature command in detail.
This feature set uses the following functions:
         • A SET FEATURES subcommand to enable Advanced Power Management
         • A SET FEATURES subcommand to disable Advanced Power Management
The Advanced Power Management feature is independent of the Standby timer setting. If both Advanced Power
Management level and the Standby timer are set, the device will go to the Standby state when the timer times out or
the device's Advanced Power Management algorithm indicates that it is time to enter the Standby state.
The IDENTIFY DEVICE response word 83, bit 3 indicates that Advanced Power Management feature is supported
if set. Word 86, bit 3 indicates that Advanced Power Management is enabled if set. Word 91, bits 7-0 contains the
current Advanced Power Management level if Advanced Power Management is enabled.
11.7.1 Performance Idle Mode
This mode is usually entered immediately after Active mode command processing is complete, instead of
conventional idle mode. In Performance Idle mode, all electronic components remain powered and full frequency
servo remains operational. This provides instantaneous response to the next command. The duration of this mode is
intelligently managed as described below.
11.7.2 Active Idle Mode
In this mode, power consumption is 45–55% less than that of Performance Idle mode. Additional electronics are
powered off and the head is parked near the mid-diameter of the disk without servoing. Recovery time to Active
mode is about 20 ms.
11.7.3 Low Power Idle Mode
Power consumption is 60–65% less than that of Performance Idle mode. The heads are unloaded on the ramp but
the spindle is still rotated at the full speed. Recovery time to Active mode is about 300 ms.
11.7.4 Transition time
The transition time is dynamically managed by the user's recent access pattern, instead of fixed times. The ABLE-3
algorithm monitors the interval between commands instead of the command frequency of ABLE-2. The algorithm
supposes that the next command will come with the same command interval distribution as the previous access
pattern. The algorithm calculates the expected average saving energy and response delay for next command in
several transition time case based on this assumption. And it selects the most effective transition time with the
condition that the calculated response delay is shorter than the value calculated from the specified level by Set
Feature Enable Advanced Power Management command.
[b]The optimal time to enter Active Idle mode is variable depending on the recent behavior of the user. It is not possible
to achieve the same level of Power savings with a fixed entry time into Active Idle because every user's data and
access pattern is different. The optimum entry time changes over time.
The same algorithm works for entering into Low Power Idle mode and Standby mode, which consumes less power
but needs more recovery time switching from this mode to Active mode.[/b]

```

```
When the Feature Register is 05h (=Enable Advanced Power Management) the Sector Count Register specifies the
Advanced Power Management level.
C0h-FEh                          The deepest Power Saving Mode is Active Idle
80h-BFh                          The deepest Power Saving Mode is Low Power Idle
01h-7Fh                          The deepest Power Saving Mode is Standby
00h, FFh                         Aborted

```

source
```
http://www.hitachigst.com/tech/techlib.nsf/techdocs/67F8F9143D6BD51C86256F72007629A4/$file/Enhanced_ABLE(9.05).pdf
```
That essentially means that it's impossible to set any times for head parking, because hard drive does that itself. I wasn't able to find any real world values for this. 
No I only need to test if kernel really forces hard drive to park heads for some reason. and if not, then why this isn't happening under windows.

---

### Post by bkraptor on 2008-01-02
Wow! That really explains why a value of 192 fixes the load cycle issue for me, while any other value under 192 doesn't. (C0h = 192)

---

### Post by blackhole54 on 2008-01-03
> **ogcub said:**
> No I only need to test if kernel really forces hard drive to park heads for some reason. and if not, then why this isn't happening under windows.

As I understand it, the OS (kernel plus) isn't, and probably can't, directly causing the head to park.  It is the disk's APM logic and/or spindown setting that does that.  And parking the head is, in and of itself, fine.  The problem occurs when the OS comes along and unparks the head shortly after it has parked.  I think that is where you will find the difference.  (IMHO and all of that.)

---

### Post by ogcub on 2008-01-03
I did the test using fresh  Hardy Alpha2 (2.6.24) and I CAN confirm the bug. So kernel is not guilty here. Then, I guess, I will also need to resort to -B 254.

---

### Post by b.q.wemer on 2008-01-03
Hi,

I got a strange issue after testing arount with powertop:

hparm -B 192 /dev/sda worked like a charm for me with Toshiba HD on ac. Load_cycle_counts only increased about 2 times on each power on/off or suspend.

After using powertop load_cycle_counts increase between 1 and 5 times in unregulary intervalls. I made none of powertops suggestions permanent.

I also tested arount with some tweaks on my motherboard after that thread:
[http://www.bughost.org/pipermail/power/2007-June/000639.html](http://www.bughost.org/pipermail/power/2007-June/000639.html)
But I cannot imagine that this has any influence on the HD.

Can anyone please help? Thanks in advance!

Oli

---

### Post by Daniel15 on 2008-01-03
> daniel@daniel-laptop:~$ sudo smartctl --attributes /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0012   096   096   000    Old_age   Always       -       49146
I guess I'm safe, then? Looks like the value is currently 49146. I've had this laptop (a Dell Inspiron 6400) since September 2006.

---

### Post by SnowflakeRV7 on 2008-01-03
This is my current response to the SMART.log script earlier in the thread:

```
Thu Jan  3 08:58:08 PST 2008
  9 Power_On_Hours          100   100   000    87
 12 Power_Cycle_Count       100   100   020    102
192 Power-Off_Retract_Count 100   100   000    87 
193 Load_Cycle_Count        099   099   000    3706
```

I take this to mean that i've got 3706 cycles in 87 hours of use, or 42.5 cycles/hour, which seems high.  Although, I was watching the Load_Cycle_Count number the other day, and it only went up by two in over four hours, with one reboot.  Is this problem worse when running on battery than on AC?

---

### Post by blackhole54 on 2008-01-04
> **SnowflakeRV7 said:**
> This is my current response to the SMART.log script earlier in the thread:

```
Thu Jan  3 08:58:08 PST 2008
  9 Power_On_Hours          100   100   000    87
 12 Power_Cycle_Count       100   100   020    102
192 Power-Off_Retract_Count 100   100   000    87 
193 Load_Cycle_Count        099   099   000    3706
```

I take this to mean that i've got 3706 cycles in 87 hours of use, or 42.5 cycles/hour, which seems high.  Although, I was watching the Load_Cycle_Count number the other day, and it only went up by two in over four hours, with one reboot.  Is this problem worse when running on battery than on AC?

That does seem borderline high.  At that rate you would hit 600,000 counts after 14000 hours of operation which works out to 588 days of actual "on" time.  My understanding is you've had various things installed on this computer.  So I suggest you watch how these values change with time with the setup you have decided to use.  (Look at difference in *Load_Cycle_Count * divided by difference in *Power_On_Hours*, perhaps over a period of several days.)  If you have put those lines in */etc/rc.local*, then those values will be logged everytime you boot.  That will make it easy to monitor how fast that value is changing.  And you can then decide whether to impliment the "ugly fix."

---

### Post by stopthewar24 on 2008-01-05
@blackhole54, ntt, & lavinog, thanks very much for your responses to my earlier post.  After reading about the problem some more, I tend to agree with lavinog -- that the hard drive heads rarely get parked on Windows.  lavinog, did you find out anything more because of the Windows work you said you had to do?

So I have a hypothesis now, and would like to test it.  The hypothesis is this:  Windows accesses the hard drive more frequently than Ubuntu Linux (and most other builds of Linux as well), and consequently, the heads are parked less frequently.  Windows does not modify power management settings.  Hard drive temperatures remain within normal operating ranges.  This also means that, even on laptops, and even on battery power, the hard drive heads are unparked for the vast majority of the time.

Under normal use on my computer running Windows Vista (Dell Inspiron 1520 dual-booted with Vista Home Premium and Ubuntu 7.10), the hard drive heads appear to park after ~7 seconds of inactivity.  They rarely stay parked for more than 5-10 seconds before Windows accesses the disk and the heads are unparked.  This head park/unpark routine occurs approximately 1 to 3 times a minute when the computer is relatively idle (such as now, when I'm typing into a web form in Firefox).  When I play music from my hard drive, for example, the heads rarely park -- once every 3 minutes, maybe.  I haven't observed any difference in this pattern whether my computer is plugged in or running on battery power, though I haven't tested this thoroughly.

I wonder, though I have not tested this at all, if disabling head parking (via apm 254 style fixes) has other effects on the hard drive as well that cause the temperature to increase -- as in, does constant slight disk access that completely prevents head parking result in a cooler-running drive than disabling head parking via hdparm? 

It seems to me that if Ubuntu accessed the disk every five seconds or so, this problem wouldn't occur.  It is, of course, really sloppy as a patch -- I'm thinking of a program that checks to see if the drive is being parked, say, more than once a minute, and if so, accesses the disk itself to keep the drive from becoming idle.  Something like Arkku's "uglier-than-ugly" fix (see [this post]("http://ubuntuforums.org/showpost.php?p=4034412&postcount=614")). 

Does anyone have ideas about how to test my hypothesis?  I'm thinking I'll monitor the number of times Windows parks the hard drive in, say, a half-hour, and then monitor how often Ubuntu parks the drive on the same computer, doing the same activity, for the same amount of time.  Then I'll try to create disk activity on Ubuntu (perhaps by playing music or something), and see if the drive is parked less often and stays within normal operating temperatures.

smartctl does not work on Windows Vista with my hard drive, and I don't know why (it works fine in Ubuntu).  However, by testing in Ubuntu, I have found that my system makes the characteristic "click" sound (that others have described) when it parks the heads, so that gives me a rough means to tell how often Vista increases the Load_Cycle_Count.  I don't know how to monitor disk reads/writes in Ubuntu -- does anyone have a good program for this?  For Windows, I'm using Vista's own Performance Monitor applet.  Also, does anybody know of a sure-fire way to cause constant disk access in Ubuntu?  Arkku, I'm new enough to Linux that I don't know how to run your uglier-than-ugly script.

Thoughts?  I realize, reading back over this post, that it's largely speculation and should be taken with a grain of salt.  Still, if anyone has ideas of how I can test the hypothesis more throughly (or knows of tests along these lines that have already been done), I would appreciate hearing.  Thanks!

---

### Post by vaxen on 2008-01-05
Dell XPS m1330 on kubuntu 7.10. Something really odd. There are a few times when I booted and there is no clicking noise and Load_Cycle_Count does not increase. Most of the time it does and I have to hdparm -B 254.

---

### Post by JellyXL on 2008-01-06
The laptop in question here is Vestel Ares, a similar barebone to this [http://www.rockdirect.com/viewNotebook.php?pName=PEGASUS%20670](http://www.rockdirect.com/viewNotebook.php?pName=PEGASUS%20670) . This one has a 160GB Seagate drive. Model ST9160821AS firmware version 3.ALC . It was affected by the bug in ubuntu ( 7.10 with latest updates ) but using ugly fix and setting hdparm -B 254 option fixed it. The notebook originally came with Vista Home Premium, i additionally installed XP and Ubuntu.. I noticed similar problem in XP though, as reported by Speedfan, Load_Cycle_Count was increasing rapidly in XP also. I used ( just now ) the windows version of hdparm to set -B 254 option in XP. I will continue to monitor the drive for increased temp etc. I couldn't find any official seagate utilities to alter these values. Also in the BIOS, no options to set APM values for hdd are present. I have already set hdd to never shut down in power options in windows.. I believe so that this problem exists in Windows also, at least in XP ( will try to see the behavior in Vista ) and its a big one.. Load_Cycle_Count is a performance and fitness characteristic of the drive, and it increases very rapidly, even in Windows.. Already from 5K value after finding the problem in Ubuntu and remedying it, the value has increased to 13K, after only two days of usage, with the laptop on mains and mainly idling.. i know its supposed to lower temps, and protect hdd from heads touching surface when a bump occurs, but i feel its badly implemented in the OSs. There should be some buffer to hold requests to hdd, so it doesn't park and unpark heads three or four times a minute...
I have tested behavior in Vista that came preinstalled with the laptop, Load_Cycle_Count doesnt increase... So its some setting in Vista, some acpi/apm driver, dont know, but the problem doesn't exist there

---

### Post by Arkku on 2008-01-06
> **stopthewar24 said:**
> Also, does anybody know of a sure-fire way to cause constant disk access in Ubuntu?  Arkku, I'm new enough to Linux that I don't know how to run your uglier-than-ugly script.

A simple way to start it up when booting is to include something along these lines in /etc/rc.local (and use the same line to start it manually so you don't have to reboot):

```
nohup /path/to/syncer.sh >/dev/null 2>&1 &
```

Meanwhile I've now replaced the original loop (while sync; do; sleep 7; done) with something like this:

```

#!/bin/bash
DELAY=5
SYNCFILE=/var/local/sync
while true; do
    touch "$SYNCFILE"
    echo "$SECONDS" >"$SYNCFILE"
    sleep "$DELAY"
done

```

It seems to work well enough, when /var/local is on an ext3 filesystem and there's no "commit" parameter in effect with a value greater than the default (5). The touch-line seems to be required for this to work (i.e. just the echo didn't suffice for me)... now the echo-line could be unnecessary, but I left it in just to have something change in the actual file (it's reassuring to see =).

The actual script I use is more complicated (e.g. it has a pid-file in /var/run and it runs as the user "sync"), and there's a hourly cronjob that checks that the script is running and records any changes in the Load_Cycle_Count, and other excessive bloat and paranoia. However, try this to see if it works for you.

The problem with the simple sync-loop is that it ends up syncing all filesystems entirely, while this one suffices to just cause some disk activity to keep it from parking. For me the temperature of the drive still remains at 28°C, but mine is a desktop machine... laptop users especially should check the temperature with any solution that disables or undermines power saving features.

Also, note that just because this happens to work for my drive and setup, doesn't mean it will work for you. So, test it first.

P. S. If you can apply the "ugly fix", do that instead, the only reason I'm doing this is that the hdparm -B doesn't work on my drive and hdparm -S doesn't help.

---

### Post by lavinog on 2008-01-06
I have somewhat "dropped the ball" on getting anymore data.
I have been unsuccessful so far at using scripts to benchmark different configurations. It appears that after an hour my load cycle count stops incrementing all together.
My script runs off of a ram drive to prevent introducing unwanted cycles.


I have verified that firefox does complicate the matter.  For instance there is some hd activity while typing a post.  I think I might focus my attention to why this is.

also good info ogcub:
```
When the Feature Register is 05h (=Enable Advanced Power Management) the Sector Count Register specifies the
Advanced Power Management level.
C0h-FEh                          The deepest Power Saving Mode is Active Idle
80h-BFh                          The deepest Power Saving Mode is Low Power Idle
01h-7Fh                          The deepest Power Saving Mode is Standby
00h, FFh                         Aborted
```

This info maybe quite helpful in finding a more attractive fix compared to the ugly fix.

The past couple of weeks of looking into this has made me less concerned about this issue.
I would also hope that there will be less attacks on the Ubuntu devs about this since we still have yet to see any evidence that Ubuntu is actually causing any damage.

---

### Post by blackhole54 on 2008-01-07
> **JellyXL said:**
> Already from 5K value after finding the problem in Ubuntu and remedying it, the value has increased to 13K, after only two days of usage, with the laptop on mains and mainly idling.. i know its supposed to lower temps, and protect hdd from heads touching surface when a bump occurs, but i feel its badly implemented in the OSs. **There should be some buffer to hold requests to hdd, so it doesn't park and unpark heads three or four times a minute...** (*emphasis added)*

I can't speak for MS, but in Linux, my understanding is that this sort of thing is what *laptop-mode* is supposed to do.  The problem seems to be that there are one or more unsolved bugs that cause some computers to crash under *laptop-mode*.  If you are a knowledgeable user and feels a bit adventurous, you can see [my post]("http://ubuntuforums.org/showpost.php?p=3843681&postcount=506") about the brief experiments I did with LTM.  They looked encouraging.  Also see my post immediately preceeding that one.

---

### Post by lavinog on 2008-01-08
On my WinXP install I can hear the clicks
it seems that the heads park about 5-10 seconds after disk activity, and they don't unpark until I do some sort of activity.
This means that windows doesn't dissable the apm  settings like it was suspected.
Unfortunately my laptop hdd activity light blinks like crazy due to cdrom polling (discovered in an earlier post) so getting the actual time that it waits before parking is difficult.

I am going to see if i can get actual times and compare them to ubuntu and see if they differ...if they don't then we can defiantly conclude that windows and ubuntu do things the same way.

I am thinking about setting up a ram drive and maybe see if i can redirect certain config files to it to see if I can get the hd activity to stop and allow the heads to be parked for a while.

but I can tell you all right now as I am typing this from my windows partition I have heard the heads park about 3 times already.

For those that don't experience this with windows it could be you have 3rd party apps running...I have a pretty minimalistic install of windows...no themes, barely any third party apps...etc

---

### Post by blackhole54 on 2008-01-09
> **lavinog said:**
> Unfortunately my laptop hdd activity light blinks like crazy due to cdrom polling (discovered in an earlier post) so getting the actual time that it waits before parking is difficult.

Your talking about in MS Windows?  I certainly ain't no MS expert, but you _might_ be able to stop the polling if you disable autorun (just a stab in the dark).  I think I've read that you can still do that in the recent versions of MS, but I've not done it.  IIRC, in win95 that was done from the hardware manager.  But I am sure you can find the info on the Internet.

> For those that don't experience this with windows it could be you have 3rd party apps running...I have a pretty minimalistic install of windows...no themes, barely any third party apps...etc

TMK, the only (generally) reliable way to tell if the head is parking is with SMART.  Apparently on machines like yours you can hear it park.  On my machine I never heard anything even though it was parking over 3 time/minute on average.  I just thought I would mention this so other people who have quiet drives aren't erroneously thinking their head isn't parking.

---

### Post by ubuntu_demon on 2008-01-09
I updated the unofficial ugly fix to issue both hdparm -B 254 and -B 255. Since -B 255 doesn't send APM command 255 but a "disable apm" command see [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/172287/comments/1](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/172287/comments/1). I hope this will work for harddrives which support either of them and/or both (it works for me). Please try this. If you think the ugly unofficial fix should be reverted back please elaborate in this thread and send me a PM to notify me about your post.

---

### Post by insulae on 2008-01-10
i am using ugly fix, and work perfectly so far, now if i remove the AC connector the disk is not parking.

i try runing manually:
```

sudo hdparm -B1 /dev/sda ( yes my disk is /dev/sda this is not the problem :P )

/dev/sda:
 setting Advanced Power Management level to 0x01 (1)

```

and the result is not head parking, the load cycle count is not counting.
i run a LiveCD and i have head parking, what can be wrong? i don't want to reinstall :D

Grettings
insulae

PD i want a SSD snif snif i dont want any more this primitive disk :P

---

### Post by lavinog on 2008-01-11
> **blackhole54 said:**
> Your talking about in MS Windows?  I certainly ain't no MS expert, but you _might_ be able to stop the polling if you disable autorun (just a stab in the dark).  I think I've read that you can still do that in the recent versions of MS, but I've not done it.  IIRC, in win95 that was done from the hardware manager.  But I am sure you can find the info on the Internet.

I tried disabling autorun using tweakui but it didn't help
the hardware manager might work...maybe i can just disable my cdrom drive and see if that stops it.


> 
TMK, the only (generally) reliable way to tell if the head is parking is with SMART.  Apparently on machines like yours you can hear it park.  On my machine I never heard anything even though it was parking over 3 time/minute on average.  I just thought I would mention this so other people who have quiet drives aren't erroneously thinking their head isn't parking.
I can hear the head park when the room is quiet and i am listening for it...my hard drive is located at the front of my laptop so that probably makes it easier to hear.
I think that being able to hear the drive park and unpark would be essential to finding possible causes. Running a program (smartctl) that is located on the hard drive would just complicate the troubleshooting.

also I have been trying to run tests with different things disabled, but I can't get consistent results just by measuring the number of cycles/hr...eventually it goes down to 1/hr (and I can only assume that smartctl is what is causing that 1 cycle)

Since some of us have concluded that the issue is due to hdd activity causing the heads to unpark right after they park, it would be handy to watch hdd activity patterns with different configurations.
This would allow me to disable apm on the drive so it doesn't go to sleep (which i suspect is the reason for the above)

The easiest way to do this would be a program that records a timestamp for every io
I'm sure there is some program that does this...I just haven't found one yet...(Windows has a program called filemon that keeps a log of every program that causes an io to the filesystem...this would be ideal). I have been experimenting with blktrace, but it has been giving me weird results. 
Its almost like ```
/etc/init.d/sysklogd stop
``` interferes with getting consistant results.

another idea is to hardwire a data logger to the hdd activity light...The benefit of something like this would be that it wouldn't interfere with the results, and could be filtered to only look at pulses and not continuous disk activity (since it is the pulses we are trying to reduce)
The downside is this would require that you have some experience in this area...and you need a data logger. A separate computer could be used.

Lately my laptop has become essential to a project at work so my time to spend on this is currently limited.

---

### Post by blackhole54 on 2008-01-11
> **lavinog said:**
>  I have been experimenting with blktrace, but it has been giving me weird results. 
Its almost like ```
/etc/init.d/sysklogd stop
``` interferes with getting consistant results.

I don't really understand what you mean by that, but reading it did make me think of something ...

If you are willing to change your conf files while you are doing your tests, you can change the logging behavior of *syslogd* by modifying */etc/syslog.conf*.  (I think you already know this, but for the benefit of anybody else reading this, it is a good idea when modifying conf files to save a copy of the original file, so you can go back to it.)  You can set it so that it doesn't log anything to your disk.  Alternatively, you can log to a Virtual Terminal and/or (I think) to another machine on the network.  I have never done it over the network but I think I remember reading about it.  As always, check the *man page* for details.  Or maybe you want to leave the existing logging the same but try to log your diagnostic tool's output somewhere else. ...  Just a thought.

After changing *syslog.conf*, you must either restart the service or send **syslogd** a **HUP** signal to get it to re-read the conf file.

---

### Post by blackhole54 on 2008-01-11
> **insulae said:**
>  ... and the result is not head parking, the load cycle count is not counting.
i run a LiveCD and i have head parking, what can be wrong?

The live CDs I have used won't access the HD unless you explicitly tell them to.  (Swap is a possible exception.)  Installed distros, on the other hand, normally are accessing the disk automatically.  One possible explanation for what you are observing is that the installed version is accessing the disk frequently enough that your particular disk's APM won't let the head park even with the APM set to one.

---

### Post by Fr@nKy on 2008-01-11
Will this problem be fixed by default on Hardy?

---

### Post by lavinog on 2008-01-12
> **blackhole54 said:**
> The live CDs I have used won't access the HD unless you explicitly tell them to.  (Swap is a possible exception.)  Installed distros, on the other hand, normally are accessing the disk automatically.  One possible explanation for what you are observing is that the installed version is accessing the disk frequently enough that your particular disk's APM won't let the head park even with the APM set to one.

I remember reading that the live cds will take advantage of a swap partition if it exists.

---

### Post by blackhole54 on 2008-01-13
> **lavinog said:**
> I remember reading that the live cds will take advantage of a swap partition if it exists.

It depends on the live CD.  Many of them will.  Knoppix certainly will unless you give it the *noswap* boot parameter, and probably most of the live CDs that trace their roots to Knoppix have the same behavior.  I have seen at least one live CD (gOS?) that by default doesn't use swap.  I don't know about the Ubuntu live CDs, and it is not conventient  right now for me to check it.  But it is easily checked using the **free** command to  see if the *total* (free + used) swap size is non-zero.

Even if the live CD does use swap space,  I wouldn't expect it to be accessing it except when you are actively doing something, if then.  Which was my point.  While an installed distro might be doing any manner of disk access w/o you doing anything, a live CD probably won't be.  So I was putting this forward as a _possible_ explanation for what *insulae* was seeing.

EDIT:  Ubuntu 6.10 live CD does _not_ use existing swap space by default.  (I don't know if that can be overriden.)  gOS 1.0.1 live CD _does_ use existing swap space on the HD by default.

EDIT2:  I think when I first tried the gOS live CD I noticed it wasn't using swap.  But I later discovered that my swap partition had somehow become corrupted and _no_ OS was using it, including my default installed OS on the computer.  And it had been that way for about a month before I noticed!  :o

---

### Post by Kaerper on 2008-01-16
> **Fr@nKy said:**
> Will this problem be fixed by default on Hardy?

hopefully

---

### Post by lamborghiniwang on 2008-01-18
Is there something wrong with my hard drive(6-month-old, Hitachi Travelstar 5k250):
```

  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   253   253   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       894
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       2022
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       406
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
**192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       29098062**
**193 Load_Cycle_Count        0x0012   087   087   000    Old_age   Always       -       135996**

```
I am running 64bit Gutsy on a Lenovo Thinkpad T61p. smartctl version is 5.37 .

---

### Post by Mondoman on 2008-01-18
Your Load_Cycle_Count / Power_On_Hours = about 67/hour, or more than 1/minute.  I'd be concerned.

---

### Post by fuoco on 2008-01-20
I just found out about this and i see my Load_Cycle_Count is already 676903 !!
dividing by Power_On_Hours I get about 55 per hour.
How bad is my situation?? what should I do now? this is a 2 year old iBook...

---

### Post by lamborghiniwang on 2008-01-21
I applied the ugly-fix, it seems the Load_cycle_count is not increase that fast now(only 3-4/hour), but another problem appears. The G-Sense_Error_Rate start to increase very fast. Here is the smartctl result:
```

  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   238   238   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       927
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       2056
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       420
**191 G-Sense_Error_Rate      0x000a   098   098   000    Old_age   Always       -       4**
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       29229135
193 Load_Cycle_Count        0x0012   087   087   000    Old_age   Always       -       136082
194 Temperature_Celsius     0x0002   152   152   000    Old_age   Always       -       36 (Lifetime Min/Max 17/45)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

```
When comparing to the data from my last post, you can see raw result of the G-sense_error_rate increased from 0 to 4 within 34 hours of power-on time ( the actually value droped from 100 to 98 ). With such a pace, the G-sense-error-rate would drop to 0 within a few months. 

Any suggestion?

Update:
It seems getting worse:
```

  9 Power_On_Hours          0x0012   096   096   000    Old_age   Always       -       2058
191 G-Sense_Error_Rate      0x000a   097   097   000    Old_age   Always       -       262146

```
Within 2 hours, the G-sense_error_rate dropped to 97. With such a rate, will my hard drive die in a few days?
Any suggestions?

---

### Post by fuoco on 2008-01-21
i solved the problem on my laptop by using -B 254 in /etc/hdparm.conf.
now my problem is that it's only effective when I bootup. After a suspend - resume I get again the problem of constant spindown/up. I tried of course the script in /etc/acpi/... but it didn't do any difference.
I also tried changing in /etc/apm/events.d/20hdparm but it also didn't help.

I am on an iBook PowerPC system - if that makes any difference. I just cannot find where the settings are read from after a resume.
any help?

---

### Post by blackhole54 on 2008-01-22
> **lamborghiniwang said:**
> 
Within 2 hours, the G-sense_error_rate dropped to 97. With such a rate, will my hard drive die in a few days?
Any suggestions?

I can't comment about the *G-sense_error_rate* itself.  (I don't even know what it is!)  But you can't tell anything about it dropping from 98 to 97, because your measurement has a resolution of one.  To illustrate, instead of thinking of it as the integer like it is reported as, think of it really being a floating point number.  So it is possible what you really saw was a drop from 98.000003 to 97.999998.  That doesn't sound so scary.  (Don't take those numbers litterally; I just made them up to illustrate.  The point is, you can't tell anything by seeing the number change by the size of its resolution -- in this case one.)

I suggest you continue to monitor the situation over the next few days.  And find out what *G-sense_error_rate* is if you don't already know.

---

### Post by blackhole54 on 2008-01-22
> **fuoco said:**
> i solved the problem on my laptop by using -B 254 in /etc/hdparm.conf.
now my problem is that it's only effective when I bootup. After a suspend - resume I get again the problem of constant spindown/up. I tried of course the script in /etc/acpi/... but it didn't do any difference.
I also tried changing in /etc/apm/events.d/20hdparm but it also didn't help.

I am on an iBook PowerPC system - if that makes any difference. I just cannot find where the settings are read from after a resume.
any help?

Pardon me if this is a stupid question, as I am unfamiliar with iBooks.  But does ACPI even apply to iBooks or is it just relevant to the x86/PC architecture?

---

### Post by fuoco on 2008-01-22
> **blackhole54 said:**
> Pardon me if this is a stupid question, as I am unfamiliar with iBooks.  But does ACPI even apply to iBooks or is it just relevant to the x86/PC architecture?

It does not as far as I know. What I did now which works, is add an hdparm line to the hal script that is used to suspend the machine (by gnome-power-manager) or something like that. hopefully this will fix it completely for me...

---

### Post by lamborghiniwang on 2008-01-22
> **blackhole54 said:**
> I can't comment about the *G-sense_error_rate* itself.  (I don't even know what it is!)  But you can't tell anything about it dropping from 98 to 97, because your measurement has a resolution of one.  To illustrate, instead of thinking of it as the integer like it is reported as, think of it really being a floating point number.  So it is possible what you really saw was a drop from 98.000003 to 97.999998.  That doesn't sound so scary.  (Don't take those numbers litterally; I just made them up to illustrate.  The point is, you can't tell anything by seeing the number change by the size of its resolution -- in this case one.)

I suggest you continue to monitor the situation over the next few days.  And find out what *G-sense_error_rate* is if you don't already know.

It seems the G-sense_error_rate goes up to 99 again this morning. I guess it does not accumulate. :D

---

### Post by lavinog on 2008-01-24
> **lamborghiniwang said:**
> It seems the G-sense_error_rate goes up to 99 again this morning. I guess it does not accumulate. :D

I suspect that g-sense error rate has to do with g-shock sensors...is this an ibm?
anyway, it is listed as a old-age category and not a pre-fail so when it drops to 0 it would just mean that your hd is old...not that it is about to fail

since it went back up i would wonder if it only takes data from a limited time frame.
you could try physically moving your laptop and see if it changes some.
EDIT: I see you have a lenovo...which is an ibm.
ibm usually has a safety that detects acceleration of the hd...to detect if the laptop fell off of a desk or something...in the event that it detects a rapid change in velocity it then parks the heads as a safety precaution.

---

### Post by lavinog on 2008-01-24
I am going to try a different approach to this:
i turned on the system monitor applet on my tray and enabled disk activity.
there are times when the computer is idle that i see repeated patterns in disk activity..something like this:
.  .|.  .  .|.   .  .|. 
it almost looks like a heartbeat, but it doesn't do this every time i let my computer idle.

So far what i did was:
touch testfile
then:
find /home -newer testfile

then i wait 5 mins or so and i use the find command again ...etc

what i found is that ~/.gconf/apps/gnome-screensaver/%gconf.xml
is modified almost every 5 to 15 mins

so i am watching this file and i am seeing that the power_management_delay entry is constantly being changed...at one point the value is 120 then it is 30 and the mtime changes every time too.

so I suspect this is an issue...I think I remember a bug report being filled on something like this so i will look into this....but this can be one cause of the cycle counts.

EDIT: Maybe everyone should try:
```
ls -l ~/.gconf/apps/gnome-screensaver/%gconf.xml 
```
and see if the modification time is within about 10 mins


I am going to try out a couple of things while firefox is running next.
which makes me wonder...how often does everyone leave firefox running in the background or when idle?

---

### Post by blackhole54 on 2008-01-25
> **lavinog said:**
> EDIT: Maybe everyone should try:
```
ls -l ~/.gconf/apps/gnome-screensaver/%gconf.xml 
```
and see if the modification time is within about 10 mins

Here's a simple script you can leave running to monitor changes:

```

#!/bin/bash

#  file:  monitor_ss_gconf
#
#  Log changes in modifcation time of $TARGET
#  The current time is guaranteed to be logged the first time through the loop
#  This script may miss some changes if more often than once/minute

TARGET=~/.gconf/apps/gnome-screensaver/%gconf.xml
LOG=/tmp/monitor_ss_gconf.log
TSTAMP=$(mktemp /tmp/ssgc.ts.XXXXXXXXXXXX)

touch -d "Jan 1, 1970" $TSTAMP

while : ;do
   if [ -n "$(find $TARGET -newer $TSTAMP)" ]; then
      ls -lh $TARGET >> $LOG
      touch -r $TARGET $TSTAMP
   fi
   sleep 60
done

```

_After_ I wrote the script I realized my $TARGET file had not changed modification time in the last 8 days!  (But I did then test the script with *syslog* as the target.  The script works.)  I should point out that I am running *edgy*  But in any case, a change every 5 to 10 minutes really wouldn't contribute very much to disk wakeups on the order of once a minute or more often.

EDIT:  I put the scipt's log file in /tmp for convenience.  Remember that /tmp gets wiped out on next boot!

---

### Post by lamborghiniwang on 2008-01-25
> **lavinog said:**
> I suspect that g-sense error rate has to do with g-shock sensors...is this an ibm?

I suspect the same thing. I tried to move my laptop around and I can reproduce the large g-sense error rate, but after a few reboots/days the number will goes back to normal.
> 
ibm usually has a safety that detects acceleration of the hd...to detect if the laptop fell off of a desk or something...in the event that it detects a rapid change in velocity it then parks the heads as a safety precaution.
A little bit off-topic, I remember the package hdapsd and hdaps-utils was working in Feisty+T60, but it is no longer working in Gutsy+T61p (which comes with an error msg on boot saying something like "not starting hdapsd: /sys/block/hda/queue/protect does not exist"). I don't know if it is because some changes in the hardware or software side.

---

### Post by Metaleks on 2008-01-25
I applied the updated ugly fix as stated in the beginning of this thread.  However, I don't understand my WORST and THRESHOLD numbers, or what Old_age means..  Can someone interpret them for me?  It would be greatly appreciated.

```
SMART overall-health self-assessment test result: PASSED
Please note the following marginal Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
190 Temperature_Celsius     0x0022   056   028   045    Old_age   Always   In_the_past 739639340

```

Also, this laptop is about 6 months old.  Got it last September.  So I'm thinking the HDD is pretty new.  My load count is 4691.

---

### Post by lavinog on 2008-01-25
> **Metaleks said:**
> I applied the updated ugly fix as stated in the beginning of this thread.  However, I don't understand my WORST and THRESHOLD numbers, or what Old_age means..  Can someone interpret them for me?  It would be greatly appreciated.

```
SMART overall-health self-assessment test result: PASSED
Please note the following marginal Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
190 Temperature_Celsius     0x0022   056   028   045    Old_age   Always   In_the_past 739639340

```

Also, this laptop is about 6 months old.  Got it last September.  So I'm thinking the HDD is pretty new.  My load count is 4691.

That does seem confusing...why would the worst be less than the value?
what kind of trends do you see with the value after the hard drive has been off for a while...does the value go up or down...if it goes down when it should be getting hotter then i wonder if the value is not the value...although it seems that it should be.

as far as the difference...from what i understand the worst is the worst value your hd has experienced...the thresh is the point where the type (in this case old age) is considered.
if the type was prefail and worst reached the thresh then that would mean that your hard drive is about to fail.
since temperature always fluctuates i wonder if the values for worst and thresh are computed by looking at some form of integral of temp...(looking at the temperature history)

---

### Post by lavinog on 2008-01-25
> **blackhole54 said:**
> Here's a simple script you can leave running to monitor changes:

_After_ I wrote the script I realized my $TARGET file had not changed modification time in the last 8 days!  (But I did then test the script with *syslog* as the target.  The script works.)  I should point out that I am running *edgy*  But in any case, a change every 5 to 10 minutes really wouldn't contribute very much to disk wakeups on the order of once a minute or more often.

EDIT:  I put the scipt's log file in /tmp for convenience.  Remember that /tmp gets wiped out on next boot!

I agree 5 to 10 mins doesn't seem like alot, but when you take into account the journal delayed write and the reading of the gconf file (since i already turned off writing of access times i can't check this yet)
if the journal is waiting too long to make the write this can cause at least two cycles per 5-10 min interval = 12 to 24 cycles per hour.

I actually don't understand why the screensaver would even do this...it seems so unnecessary

I also forgot to mention that the interval that it makes its writes seems to be what ever you have the screensaver set to.
and the information it changes in that file seem to be timestamps since it last checked for activity...i don't think it should be necessary to store that value on the hd, that is what memory is for.

---

### Post by hebetude on 2008-01-26
I applied these scripts, and they did slow down my load cycle a bit.  However, I left the laptop laying around with screen off for a while and when I came back the temp was 56C.

I immediately deleted the scripts and did a standby/resume to be sure they were ran, now 10mins later in use the hard drive is 43C.

Is there some 'real' fix in the works?  I already went over to the darksite and bought a laptop w/an nvidia video card, now do I have to drop $500 for a crappy version 1 SSD just so I can web browse.

So whats the plan...
Linux laptops come w/coolers glued to the bottom?
Put laptops on ext2?
Use the portable firefox tuning methods?

HP dv6775us
WD2500BEVS

-Guy with cooked legs

---

### Post by blackhole54 on 2008-01-27
> **Metaleks said:**
> I applied the updated ugly fix as stated in the beginning of this thread.  However, I don't understand my WORST and THRESHOLD numbers, or what Old_age means..  Can someone interpret them for me?  It would be greatly appreciated.

```
SMART overall-health self-assessment test result: PASSED
Please note the following marginal Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
190 Temperature_Celsius     0x0022   056   028   045    Old_age   Always   In_the_past 739639340

```

Also, this laptop is about 6 months old.  Got it last September.  So I'm thinking the HDD is pretty new.  My load count is 4691.

> **lavinog said:**
> That does seem confusing...why would the worst be less than the value?

(Pardon the format of this post.  I couldn't get *multipost* to work.)

I am not sure this is confusing at all.  My understanding is that the temperature is an instantaneous reading that goes up and down, and the "Worst" value simply shows it got hot sometime in the past.  Maybe I'm wrong, but I've always thought that it was listed as an "old age" value because (I am guessing here) disk drives start running hotter when they age. (Maybe bearings wearing out?)   As far as the raw value itself, the manufacturer seems to use some kind of strange internal representation that I wouldn't even hazard a guess at.

---

### Post by blackhole54 on 2008-01-27
> **lavinog said:**
> I actually don't understand why the screensaver would even do this...it seems so unnecessary

I also forgot to mention that the interval that it makes its writes seems to be what ever you have the screensaver set to.
and the information it changes in that file seem to be timestamps since it last checked for activity...i don't think it should be necessary to store that value on the hd, that is what memory is for.

I agree, it seems unnecessary.  And on my *edgy installation* it doesn't.  (They changed something on newer releases?)  My screen saver is set to activate after 7 minutes and change screensavers every 4 minutes until the screen is blanked after 30 minutes.  The time stamp (modification) on the file still reads Jan 16, 2008.  And the screensaver has activated multiple times since then.

EDIT:  Wrt your disk access analysis ..   I am certainly no expert on *ext3*, so I could be dead wrong.  But I don't know why (on a relatively inactive machine) there would be a delay between writing the journal and writing the final data to the disk.  Unless the disk is really  busy, I would think it would all be one operation.  If the disk is really busy, you don't need to worry about the head parking anyway.

---

### Post by jeyros12 on 2008-01-27
I've been running ubuntu a long time on my laptop.

Now I just did a SMART analysis and i got 324 000 Load Cycle Count whereas, acording to the manufacturer, the limit for my disk is 300 000...  :(

PLZ HELP...

Will my disk be useless soon?
Will i loose my datas?
How long will my disk last?

THX

---

### Post by blackhole54 on 2008-01-27
> **jeyros12 said:**
> I've been running ubuntu a long time on my laptop.

Now I just did a SMART analysis and i got 324 000 Load Cycle Count whereas, acording to the manufacturer, the limit for my disk is 300 000...  :(

PLZ HELP...

Will my disk be useless soon?
Will i loose my datas?
How long will my disk last?

THX

With regard to your 3 questions, I don't know and I doubt anybody on this forum can give you a definitive answer.  Backing up data is _always_ a good idea, whether you are facing a crisis or not.  I would _definitely_ suggest you do that now.

That said, it doesn't mean your disk is necessarily going to fail immediately.  You are in a [similar situation](http://ubuntuforums.org/showpost.php?p=3653021&postcount=1) to mine, where my *Load_Cycle_Count* had already exceeded the manufacturers spec.  You have to make your own decision about what to do, but my decision was to immediately try to stop the rapid increase.  So you might want to consider applying the "ugly fix" and see if it helps.  If it is any comfort, you will notice my post was Oct 28 of last year, and my drive is still running.

EDIT:    If you apply the "ugly fix," I suggest you monitor your *Load_Cycle_Count* and disk temperature for a few days.  [Some people have reported](http://ubuntuforums.org/showpost.php?p=4210187&postcount=680) that their disk drive starts running too hot after applying the fix.

---

### Post by Metaleks on 2008-01-28
> **blackhole54 said:**
> I am not sure this is confusing at all.  My understanding is that the temperature is an instantaneous reading that goes up and down, and the "Worst" value simply shows it got hot sometime in the past.  Maybe I'm wrong, but I've always thought that it was listed as an "old age" value because (I am guessing here) disk drives start running hotter when they age. (Maybe bearings wearing out?)   As far as the raw value itself, the manufacturer seems to use some kind of strange internal representation that I wouldn't even hazard a guess at.

Is value the current temperature?  If so, I think 58 is a bit hot, no?  Or is it the further the number in value from threshold, the better?  Please explain.  Since applying the "ugly fix" I have seen my load cycle count go up by only 4 in the past 4 days.  That, to me, seems incredible.  But if my HDD is burning up at the cost of this better load cycle, then the heat is more of a threat than the HDD parks.

---

### Post by dicecca112 on 2008-01-28
> **jeyros12 said:**
> I've been running ubuntu a long time on my laptop.

Now I just did a SMART analysis and i got 324 000 Load Cycle Count whereas, acording to the manufacturer, the limit for my disk is 300 000...  :(

PLZ HELP...

Will my disk be useless soon?
Will i loose my datas?
How long will my disk last?

THX

Check to see by what the disk count is going up.  Say its going up by 4/s then your count is actually 324000/4 or 82000.

---

### Post by jeyros12 on 2008-01-28
> **dicecca112 said:**
> Check to see by what the disk count is going up.  Say its going up by 4/s then your count is actually 324000/4 or 82000.

Actually  i've been running ubuntu for a while but i'm not running it anymore (i confess). So i can't figure out what the period of inceasing is (but Power On Hours Count is 10749).

Why would i have to divide by the period of increasing?


I've noticed that when i play some random music file, the count doesn't increase so i'm playing the same file all day long. But still the count increases from day to day (booting/shuting down process i guess).

---

### Post by blackhole54 on 2008-01-28
> **Metaleks said:**
> Is value the current temperature?  If so, I think 58 is a bit hot, no? 

The actual current temperature is in indicated under *RAW VALUE*.  Some disk manufacturers (like mine) express this as an easy-to-understand figure like "37 Celsius."  some manufacturers (like yours) use something much more cryptic.  I have no idea what your figure means.  (Perhaps your manufacturer's website or an Internet search would reveal the mystery.)

The numbers under *VALUE*, *WORST*, and *THRESH* are 'normalized' values, converted from the raw value according to a manufacturer's determined formula.  (See the description of the -A option in the [**smartctl** *man page*](http://man.linuxquestions.org/?query=smartctl&section=0&type=2) for more info.)  The higher the normalized value the better.  When the value drops below *THRESH* is when you have trouble.  On your drive, this happened sometime in the past when the normalized value dropped down to 28.  This is when your disk was actually unacceptably hot.  But there is no way to know when, or under what circumstances, that happened.

EDIT:  I mispoke slighly when I descirbed the temperature line on my machine.  Here is what the output looks like:

```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
194 Temperature_Celsius     0x0022   110   092   000    Old_age   Always       -       40

```

I think it is fairly certain that the current temperature is 40 C.

---

### Post by BandD on 2008-01-29
I've been following this thread for quite a while now.  What, in your opinions, is the benefit in NOT applying the Ugly Fix?  Unless there is some adverse effect like soaring HD temps or something.  

As far as I can figure there is NO benefit at this point in time in having your HD park its heads.  The point of having the heads park is to have them stay parked (as long as the drive is inactive) so that if the HD is jolted suddenly the potential damage to the disk is minimized.  But at this point, the heads don't stay parked, at least not for very much time for most of us.  So if the heads aren't going to stay parked anyway, then it seems much better to just apply the ugly fix.

And for most laptop users, the time when our computers are most apt to jolts is when we are transporting them around.  But most of us, I imagine, have our machines off (either entirely shutdown, Suspended, or Hibernating), in which case the heads are permanently parked.

I guess I'm really just trying to figure out the benefit of head parking in general.  Cause honestly, if we are working on our computers we, generally aren't moving around too much, and if we are moving around with our machines on, then we probably have some programs open that are keeping the drive busy and thus the heads are unparked when we need them most should we happen to trip and fall.

I wonder if Hardy should ship with the -B 254 option by default for laptops.

---

### Post by fuoco on 2008-01-29
Yes that makes a lot of sense to me. But I supposed always the first reason for parking the heads and spinning down was to save energy - how much and how effective that is I don't know... Certainly not much in a situation of constant spin down and up - since usually the first moment of spin up would probably cost extra energy compared to just keeping the spin.

Anyways I have another question related: it seems quite a few laptops (and I believe mine too) have the mechanism to automatically detect a fall and activate head parking to keep the disk safe - in this case is it not redundant to have to system spin down/park heads to minimize danger to the disk?

---

### Post by dhedrick on 2008-02-02
I don't understand how to check my load cycle count - can someone help me?  I have installed the smartmon tools, but don't understand the command to check (complete Linux newbie)

Help would be appreciated.

Thanks,
Dale

---

### Post by Belerophon on 2008-02-02
You need to use smartctl:
```
sudo smartctl -a /dev/sda 
```

where sda is your hard drive....it gives you a long list of things.
You can do :
```
sudo smartctl -a /dev/sda | grep Load_Cycle 
```

to get only the Load_Cycle line you want.

---

### Post by lavinog on 2008-02-03
Disregard this post...replied too soon

---

### Post by lavinog on 2008-02-03
> **BandD said:**
> 
I wonder if Hardy should ship with the -B 254 option by default for laptops.

> **fuoco said:**
> Yes that makes a lot of sense to me. But I supposed always the first reason for parking the heads and spinning down was to save energy - how much and how effective that is I don't know... Certainly not much in a situation of constant spin down and up - since usually the first moment of spin up would probably cost extra energy compared to just keeping the spin.

It has been pointed out that the -B 254 option can increase the operating temp of the hd...which some agree to be more damaging than head parking.

also this issue also doesn't seem to affect everyone.  Some hd manufactures have smarter algorithms for parking the heads.  It seems that disabling the power saving features on everyones laptop would be a little extreme.  Many people don't use their laptops on a desk. Instead they use them while traveling...sometimes on their laps (a situation where you want to protect the hd from shock and minimize power usage as much as possible)
also for some people they don't leave their laptops on for hours on end so they are less likely to exceed the manufactures specs.



> **fuoco said:**
> 
Anyways I have another question related: it seems quite a few laptops (and I believe mine too) have the mechanism to automatically detect a fall and activate head parking to keep the disk safe - in this case is it not redundant to have to system spin down/park heads to minimize danger to the disk?

I would wonder if  -B 254 would dissable the built in safety too?
Plus there is a energy savings here...with the heads parked, the platers can spin with less friction. The amount of friction is pretty significant: I have seen a desktop hd spin for about a minute with the heads off...with the heads in place they stopped almost instantly.

---

### Post by fuoco on 2008-02-03
well i'm not sure anymore about the motion sensors mechanism - there's a chance that it's a piece of hardware that requires a driver - and linux doesn't support it, so maybe it makes no difference at all...

---

### Post by kaway on 2008-02-03
Hi, I am concerned by this problem, and I have configured the laptop-mode in order to get rid of it. But I cannot access the Load_Cycle_Count value as it doesnt appear smartctl.
See the result:

```
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM250JI
Serial Number:    S133JD0PC45907
Firmware Version: HS100-11
User Capacity:    250 059 350 016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Sun Feb  3 22:30:49 2008 CET

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (  32) The self-test routine was interrupted
                                        by the host with a hard or soft reset.
Total time to complete Offline 
data collection:                 ( 103) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 103) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
[B]ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       1
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2562
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       2462
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       211
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       66
191 G-Sense_Error_Rate      0x0032   099   099   000    Old_age   Always       -       12596
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       12
194 Temperature_Celsius     0x0022   124   094   000    Old_age   Always       -       38 (Lifetime Min/Max 13/48)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       12201
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       228
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       682
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0[/B]

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         2         -
# 2  Short offline       Completed without error       00%         0         -
# 3  Short offline       Aborted by host               150%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Interrupted [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

It has been bothering me for a long time now and no one could help me on the french speaking forums. So if someone can figure what I should do to access the Load_Cycle_Count, be my guest :)

---

### Post by lavinog on 2008-02-03
> **kaway said:**
> Hi, I am concerned by this problem, and I have configured the laptop-mode in order to get rid of it. But I cannot access the Load_Cycle_Count value as it doesnt appear smartctl.
See the result:

```

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM250JI
Serial Number:    S133JD0PC45907
Firmware Version: HS100-11
...
==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

```

I would try the -F samsung thing and see if it changes anything
if not...it could be that samsung doesn't think that tracking load_cycle_counts is a big deal...since it is questionable that the drive would ever fail if it is exceeded.

---

### Post by kaway on 2008-02-03
I tried it. It didn't change a thing...
What do u mean by "it is questionable". I thought that every hard drive had a maximum amount of cycles?
plus you can see that the  ID# 193 is "jumped". It means that it is there somewhere, doesn't it?

---

### Post by lavinog on 2008-02-03
I have pulled out one of my old pentium 2 laptops...and ran smartctl on it.
Some history about it:
I got it back in 2001 used.
it had windows 98SE on it...upgraded to win ME after a couple of months...then put winxp on it in 2004...in may 2006 i put xubuntu dapper drake on it and in october of 06 it was retired (given to my wife...who put it in a drawer and never used it again)
Majority of its life was spent running windoze (approx 80-90% of its life)

```
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 5
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   096   093   062    Pre-fail  Always       -       327683
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   123   100   024    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0012   099   099   001    Old_age   Always       -       3140
  5 Reallocated_Sector_Ct   0x0033   079   079   005    Pre-fail  Always       -       252
  7 Seek_Error_Rate         0x000b   100   097   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   020    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   074   074   001    Old_age   Always       -       11549
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   001    Old_age   Always       -       2396
220 Disk_Shift              0x0026   083   062   001    Old_age   Always       -       329472
221 G-Sense_Error_Rate      0x000a   100   100   001    Old_age   Always       -       0
222 Loaded_Hours            0x0012   093   093   001    Old_age   Always       -       3364
223 Load_Retry_Count        0x000b   100   100   050    Pre-fail  Always       -       0
224 Load_Friction           0x0007   084   080   030    Pre-fail  Always       -       21103022
225 Load_Cycle_Count        0x0012   035   035   050    Old_age   Always   FAILING_NOW 650268
226 Load-in_Time            0x0007   090   090   020    Pre-fail  Always       -       3
227 Torq-amp_Count          0x0032   100   100   001    Old_age   Always       -       0
228 Power-off_Retract_Count 0x0032   100   100   001    Old_age   Always       -       96


```

i figure that dapper was running for no more than 200 of the 11549 hours.
surely majority of those load cycles had to come from windows.

This hard drive is still functional...(just small...4gigs). Yet notice that it is reporting that it is failing now...the limit according to dell is 300k (minimum.) 

I will see if i can find a friend with vista on his laptop to get the smart results.
I'm curious what that looks like.


I say *-B 254* is **not** the solution...
Sure the operating systems and software can be written to adapt to every different hard drive out there and find a optimal writing pattern for each make and model...but realistically it will take away from more important progress.
I think that it is the hard drive manufactures' responsibility to make their hard drives adapt to various writing patterns...for some they already have. Some hard drives track disk activity and predicts optimum times to park the heads...Hybrid drives that use solid state memory for frequent activity and the mechanical disk for long term storage will also minimize this issue.
Just like my ATI card...the problems with it were not caused by Ubuntu...it was ATI not supporting Linux (at the time...Now it works great thanks to AMD taking over)
I say we go to the hd manufacture forums and mention the load cycle issue...let one of them explain what this statitistic means instead of everyone guessing.
and like always...be prepared for anything...a brand new hard drive can fail just as easily as a old one...so keep backups of stuff you don't want to lose.  Many hds have up to a 3 year waranty...if it fails get a replacement at no cost.

I have to check the born on date for this hd but i am pretty sure it is comming up to its 10 year bday.

---

### Post by lavinog on 2008-02-03
> **kaway said:**
> 
What do u mean by "it is questionable". I thought that every hard drive had a maximum amount of cycles?
plus you can see that the  ID# 193 is "jumped". It means that it is there somewhere, doesn't it?

actually the hard drive specs that i have read for a couple of hard drives say they have a minimum amount of cycles.
which I understand to say that until that minimum is reached...failure due to head parking is not likely. After that there is no telling what can happen but it is likely you can get up to a million park cycles before your hd fails...hard drive manufacturers are not going to list a maximum because they might be held accountable for drives that fail below that maximum...and posting a low maximum could be bad marketing for the drive...would you buy a drive that has a maximum of 5 million cycles or 1 million cycles? ...the 1 million cycle could actually be a better drive that would out last the 5 million cycle one...(recalling quote from Black Sheep)...the manufacturer of the 5 million cycle one may just be playing the odds that only a small percentage of failures would have customers that would even look at the cycle count.

---

### Post by blackhole54 on 2008-02-04
> **kaway said:**
> It has been bothering me for a long time now and no one could help me on the french speaking forums. So if someone can figure what I should do to access the Load_Cycle_Count, be my guest :)

Disclaimer:  This post is pure speculation.  I really don't know any more than you  ...

About a year ago I bought both a laptop and a desktop from System76, both with *edgy eft* pre-installed.  When this issue surfaced I checked both computers using **smartctl**.  The laptop, with an IDE drive showed *Load_Cycle_Count* while the desktop with a SATA drive did not.  I inquired about this being absent on the desktop drive on the System76 forum, but unfortunately did not get an explanation.  My speculation at this point is that perhaps my desktop drive does not have the unloading mechanism and so there is nothing to report.  (No drive prior to about the mid '90s had such a thing IIRC the date correctly.)  Even though your computer is a laptop (I am presuming), perhaps it doesn't have an unloading mechanism.  Like I say, this is pure speculation.  I would like a definitive answer myself.

I agree with *lavinog* that it would be a good idea to get the HD manufacturers into this discussion.  Whether they are willing to accommodate us is another matter.  And I still think that ultimately the correct "solution" is getting laptop mode working for all machines.  But that would still have the issue of configuration.  (For example, should you turn off disk APM when on AC power, etc.)

---

### Post by psycosmyth on 2008-02-09
This is odd but I decided to run Dapper for a while and I noticed my heads park quite a bit in AC mode and more in Batt. I have used Pclos for some time and Mint before that and they did not do this. I have ran Dapper on this laptop before and not had this happen.
I did have this happen with Fiesty and Gutsy as well. I might have to pull up to Edgy.
There is that darn bug for several brands of hdd's including my Hitachi.

---

### Post by fuoco on 2008-02-09
How should one fix this in Hardy? I think in hardy the acpi system has changed? I could be wrong. Either way I'm on a powerpc ibook which has no acpi, it works a bit differently then, and I don't know how - where should I put these scripts?

---

### Post by Dynaflow on 2008-02-11
I applied the "ugly fix" to my Gutsy-running Compaq laptop.  It works well, only killing my hard drive little by little when it's uplougged from AC power, and switching back to normal when I plug it back in ...

Unless I hibernate.

If I hibernate (I can't say if it's happening with suspend because getting that to work is pretty much a lost cause), my laptop will continue to issue hard-drive "ticks" and rack up load cycles every ten or twenty seconds or so until it is rebooted, regardless of its being plugged in or not.

Can anyone offer some insight on why this might be happening?  I'm using uswsusp to hibernate, and the specs on my machine are [here]("http://ubuntuforums.org/showthread.php?p=4039646#post4039646").

---

### Post by b.q.wemer on 2008-02-11
Hi,

can someone tell me, what is the difference between disc head parking and spin downs? Are they both counted in the load_cycle_count numer? And what causes each of them?

Thanks in advance.

---

### Post by blackhole54 on 2008-02-11
> **Dynaflow said:**
> I applied the "ugly fix" to my Gutsy-running Compaq laptop.  It works well, only killing my hard drive little by little when it's uplougged from AC power, and switching back to normal when I plug it back in ...

Unless I hibernate.

If I hibernate (I can't say if it's happening with suspend because getting that to work is pretty much a lost cause), my laptop will continue to issue hard-drive "ticks" and rack up load cycles every ten or twenty seconds or so until it is rebooted, regardless of its being plugged in or not.

Can anyone offer some insight on why this might be happening?  I'm using uswsusp to hibernate, and the specs on my machine are [here]("http://ubuntuforums.org/showthread.php?p=4039646#post4039646").

I haven't fully analyzed your situtation and therefore I don't have a complete answer for you.  But I read the linked post and I have a couple of observations.

First, it sounds like you both applied the "ugly fix" _and_ enabled *laptop mode*.  I am not sure these two play well together.  I would think you would want to do one _or_ the other.  And if you enable *laptop mode*, make sure you understand what you are doing.   There are several parts to it, and it is (supposed to be) capable itself of switching values for the HD's APM (255 or 254 vs 128 or 1).

I also noticed you did some editing of scripts to impliment *uswsusp*.  Please note that this is speculation on my part,  but I suspect part of that editing resulted in the "ugly fix" script not getting called when you resume after hibernation.  I also suspect that *laptop* mode might also have problems because of this.  Continuing with the speculation, after you resume from hibernation, if you then change between AC and batter power (in either direction), I *supsect* you will be back in sync.

---

### Post by Fr@nKy on 2008-02-14
> **psycosmyth said:**
> This is odd but I decided to run Dapper for a while and I noticed my heads park quite a bit in AC mode and more in Batt. I have used Pclos for some time and Mint before that and they did not do this. I have ran Dapper on this laptop before and not had this happen.
I did have this happen with Fiesty and Gutsy as well. I might have to pull up to Edgy.
There is that darn bug for several brands of hdd's including my Hitachi.

Linux Mint doesn't have the bug?? Strange it's based on Ubuntu.

---

### Post by Fr@nKy on 2008-02-14
Is this bug fixed "well" enough with the ugly fix? I'm afraid I might have to change my Distribution.

---

### Post by harold4 on 2008-02-15
I downloaded [acpi-support]("http://packages.debian.org/unstable/admin/acpi-support") v0.103-5, extracted and copied to /etc/acpi.

It may be coincidental or broken, but after reboot, my Load_Cycle count has not gone up in six hours. (since I did this)

---

### Post by blackhole54 on 2008-02-15
> **harold4 said:**
> I downloaded [acpi-support]("http://packages.debian.org/unstable/admin/acpi-support") v0.103-5, extracted and copied to /etc/acpi.

It may be coincidental or broken, but after reboot, my Load_Cycle count has not gone up in six hours. (since I did this)

Quoting from the [changelog](http://packages.debian.org/changelogs/pool/main/a/acpi-support/acpi-support_0.103-5/changelog):

```

   * Set hdparm -B 128 while on battery in 90-hdparm.sh. Head parking is useful
     on the road for shock protection. Still set hdparm -B 254 while on AC.

```

That sounds to me like what the "ugly fix" does.

I note that this package is from the unstable branch of Debian.  So I believe it is appropriate to caution people to be sure they know what they are doing before installing this in Ubuntu and be aware of the possibility that it might break something.

---

### Post by harold4 on 2008-02-15
That it does.  I experienced a few positive side effects, so I thought I'd share.  On the Dell 1520, my volume media buttons now work and closing the lid actually turns the LCD backlite off.

---

### Post by Average Joe on 2008-02-15
I have also had some [issues with my hard disk]("http://ubuntuforums.org/showthread.php?p=1728044#post1728044") (Seagate Momentus). After a
```
sudo hdparm -B 192 /dev/sda
```
I got it fixed (a higher value is not necessary for me).

What is more, instead of using the full "ugly fix" I just added this line in my /etc/rc.local file (without the sudo), and that seems to solve the problem, independent whether I am using the battery or the AC plug on my laptop.

---

### Post by blackhole54 on 2008-02-16
> **Average Joe said:**
> What is more, instead of using the full "ugly fix" I just added this line in my /etc/rc.local file (without the sudo), and that seems to solve the problem, independent whether I am using the battery or the AC plug on my laptop.

Yeah, I originally did the same thing (different) value as a quick and dirty solution.  You (and other people) should be aware that with this arrangement the disk won't go to more agressive power management when on battery like the default "ugly fix" does.  (Depending on how bad your *Load_Cycle_Count* is, you might not want it to anyway.)  Also, if you use hibernate or suspend, you should check things after resuming.  I suspect you will find your disk's APM is back at the old value.

---

### Post by Fr@nKy on 2008-02-17
lik stated on the ugly fix post on this thread I see an increase of 10 or more load cycles but at most I heard one head park... smartmon seems to be wrong like stated there... With the uglyfix it stops increasing and each time I restart my computer I have 2 more load cyles than before (one when it shuts off other when it starts).

---

### Post by fuoco on 2008-02-17
Can anyone help me and tell me where should I do something similar to the ugly-fix on systems that don't have acpi (or acpi-support), for example powerpc... Right now when I resume from suspend I get again the old APM harddisk setting.

---

### Post by chavanak on 2008-02-17
i feel this ugly-fix is pretty good!!! Bcos after this patch my hdd load cycle count has stopped and my hdd temperature is around 44 deg...

---

### Post by p4c0 on 2008-02-21
Hello, 

I have same problem but hdparm doesn't seems to fix it, it just keep increasing, my hard drive is the same as kevinbsmith : SAMSUNG MP0402H

I had tried:
hdparm -B 254 /dev/sda
hdparm -B 255 /dev/sda
hdparm -S 0 /dev/sda

same result it increase by one in around 5 seconds, sometimes more sometimes bit less, also the smartctl -o on /dev/sda doesn't seem to work for me:

# smartctl -o on /dev/sda
smartctl version 5.36 [i486-slackware-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

# smartctl -d ata -o on /dev/sda
smartctl version 5.36 [i486-slackware-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
Error SMART Enable Automatic Offline failed: Input/output error
Smartctl: SMART Enable Automatic Offline Failed.

(I have to use smartctl -d ata -a /dev/sda to show the load cycle count)

My counter is close to 600k and i just had some bad sectors last night, which puts me on panic mode...

---

### Post by drpaul on 2008-02-21
p4c0

What version of the OS are you using?  smartctl didn't work for me [Fujitsu HD SATA] until I upgraded to 7.10.

I recently put 

hdparm -B 254 /dev/sda

in /etc/rc.local
so that I don't have to execute it each time I boot. Seems to work for me. Without it Load_Cycle keeps increasing even though I don't hear the clicks anymore.

HTH

Paul

---

### Post by Average Joe on 2008-02-21
> **blackhole54 said:**
> Yeah, I originally did the same thing (different) value as a quick and dirty solution.  You (and other people) should be aware that with this arrangement the disk won't go to more agressive power management when on battery like the default "ugly fix" does.  (Depending on how bad your *Load_Cycle_Count* is, you might not want it to anyway.)  Also, if you use hibernate or suspend, you should check things after resuming.  I suspect you will find your disk's APM is back at the old value.

Thanks for pointing that out. I just checked with my laptop, and after hibernation my hard disk APM settings are still fine. But as you suspected, after a suspend my hard disk APM setting is restored to the old value. I am not sure what APM will do if I run my laptop on the battery for a long time.

Since I actually never use the hibernation or suspend option, and I only use my laptop connected with the AC power plug, I don't think I need the full ugly hack. But is it good to know that my simple solution is somewhat limited.

---

### Post by MiataMuc on 2008-02-21
I used a Smart-configuration CD (bootable, downloadble from the manufacturer of my pc) which I used to switch to 254 (highest possible value). Thince then the counter goes up 2-3 a day, and not hundred times a day. The disk-image I used was a disk-configuration tool with an underlying Freedos - boot.

Flo

---

### Post by blackhole54 on 2008-02-22
> **p4c0 said:**
> Hello, 

I have same problem but hdparm doesn't seems to fix it, it just keep increasing, my hard drive is the same as kevinbsmith : SAMSUNG MP0402H

I had tried:
hdparm -B 254 /dev/sda
hdparm -B 255 /dev/sda
hdparm -S 0 /dev/sda

same result it increase by one in around 5 seconds, sometimes more sometimes bit less, also the smartctl -o on /dev/sda doesn't seem to work for me:


Bummer.  You might poke around Samsung's website and see if they provide any kind of tool for changing the default of the disk's APM so that the disk just powers up set to 254 or APM disabled.

---

### Post by jespdj on 2008-02-22
It looks like this kind of problem can also happen on Windows.

See this thread in the Notebook Review forums: [Clicking Noise issue](http://forum.notebookreview.com/showthread.php?t=168425)

Apparently the poster there solved it by installing a utility that allows him to set the power management settings of his harddisk, similar to what we are doing with hdparm.

---

### Post by frodon on 2008-02-23
Hum this bug is really strange, in my case i have it all the time (on battery as well as on sector) and with or without laptop mode.
The "hdparm -B 254" command is solving the issue however i have to type it each time after boot and this despites that i added the scripts as adviced in launchpad so i will just add the line in hdparm.conf file too and it should be good.

EDIT: i'm testing but it seems that just configuring laptop mode to control power management do the job, this way you can set -B 254 on sector and between 120 and 180 on battery where head parking is especially interesting to increase chock robustness.

---

### Post by ntt on 2008-02-23
be careful, those scripts have been reported as creating undesired side effects; donìt know how much of this is true, but nevertheless...

in my case I've used no scripts, just added the parameter to hdparm.conf and then enabled hdparm in the services. voila, problem gone. (there's a previous post here from me giving all the details, if ever needed).

I don't use laptop mode, though, so that may well be a better solution than the always-on hdparm.conf.

cheers,

--
ntt

---

### Post by frodon on 2008-02-23
laptop_mode is doing all i want for me, i set it to use -B 254 in AC mode and -B 195 on battery which i think is the best setting for me. With -B 195 i have 2 head parking per 20 minutes which is good to increase chock robustness on battery.
To do this i installed "laptop-mode-tools" package which allow to configure laptop mode then in the /etc/laptop-mode/laptop-mode.conf i use the following parameters to accomplish this :
```
#
# Should laptop mode tools control the hard drive power management settings?
#
CONTROL_HD_POWERMGMT=1


#
# Power management for HD (hdparm -B values)
#
BATT_HD_POWERMGMT=195
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254
```In addition the laptop mode configuration file allow to set a bunch of other usefull things like hdd idle timout and so on, it is really a great tool and a good way IMO to circumvent this annoying issue.

The french wiki have a full detailled documentation about this, i think it may be interesting to translate it :
[http://doc.ubuntu-fr.org/laptop_mode](http://doc.ubuntu-fr.org/laptop_mode)

---

### Post by ntt on 2008-02-23
I see, it's probably the way laptop-mode was meant to be used :-)

In the meantime I had a look to the French wiki you've mentioned, and it's very well done! Chocked full of info, yet probably understandable - or at least useable - even to the uninitiated. Which is important, in my scale of values.

I fully agree with you, it would be well worth the effort to translate it to English.

thanks.

--
ntt

---

### Post by frodon on 2008-02-23
> **ntt said:**
> I fully agree with you, it would be well worth the effort to translate it to English.

thanks.

--
nttI will try to contact the authors of this document to see if they agree if i make a translation of this document. I should have some time to take care of this next week.
The laptop mode is really powerfull, i'm impressed to see all the things you can configure with it,  documentation about this is really a must to have.

---

### Post by blackhole54 on 2008-02-24
> **frodon said:**
> laptop_mode is doing all i want for me ...

About a week ago I set up laptop-mode for evaluation.   For a one to two hour session on battery it seems to average about 30 to 40 incriments of *Load_Cycle_Count* per hour.  While that seems high, it is a lot better than the 200/hour I was getting from a default installation.  I think a lot of that is reading binaries and configurations off the disk, as the rate seems significantly higher closer to boot-up than later on (when it can probably retrieve a lot from cache rather than reading the disk again).

The problem, as I understand it, is that laptop-mode still has some bugs that crash some computers.  I've long thought that long term, the correct solution to this problem was to get laptop-mode working on all computers.  The downside as a universal solution is that there may still be a need to hand tweak its configuration for individual computers.

Speaking of tweaking, if you decide to try laptop-mode, make sure you follow the instructions (documented in /etc/laptop-mode/laptop-mode.conf) for enabling the use of different *syslog.conf* files so that the disk is not constantly woken up for logging.


(For reference, I am running *edgy*.  Yes, I know it is about to "expire.")

---

### Post by frodon on 2008-02-24
All that is explained in the french documentation the " lm-syslog-setup" script that come with laptop mode configure syslog for you, the noatime option is interesting too to avoid too much access on the hdd and there's also the "lm-profiler" profiler script which can check for you which process access too often your disk.
I wasn't aware of any crash related to the laptop_mode could you point some references. Anyway sadly your point about hand setting is true i guess that if you want something optimized you have no other choice than editing the file yourself however i think that an average configuration can be found which would fit most of computers.

Thanks

---

### Post by goombamd on 2008-02-25
**How do I find my load cycle count in a Hitachi 7200rpm 160gb drive? **


I run 
sudo smartctl -a /dev/sda | grep Load_Cycle_Count

and get

225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       94489287006


Obviously I don't think I've had 94489287006 load cycles.  This is a relatively new m1330 with a Hitachi 7200rpm 160 gb drive in it.   That brings up another question.  **What does "Old_age" mean? My hard drive is already considered old?**

Thanks!

---

### Post by jespdj on 2008-02-25
No, the "Old_age" does not mean that your laptop or your harddisk is considered old.

Try the command without the grep:
```
sudo smartctl -a /dev/sda
```
You'll get a lot of output, look through it to see if you can find more info about the load cycle count from it.

Btw, I have an M1330 with Seagate 160 GB, 7200 RPM harddisk, and it shows the load cycle count normally. It looks like some harddisks report the data in a different way than what smartctl expects, and then you see strange numbers.

---

### Post by johnnybirdman on 2008-02-25
I'vd tried almost all variation of fix that have been suggested in this post thus far but I'm still having the drive park every 60 sec. with no activity while on AC (I have no battery).  this is better than when I started and it was 3 to 5 new load cycles every 60 sec. or so.
I using an old dell CPxJ laptop with a new (er) toshibia drive.  It's not clicking or popping the way it was before.

Any of the experts here find this to be acceptable?

---

### Post by b.q.wemer on 2008-02-25
Hi,

placing the scripts in resume.d did not for me in Hardy. Obviously those scripts are not executed. I had to place them in /usr/lib/pm-utils/sleep.d. Scripts in start.d are still working. 

For details see:

[http://ubuntuforums.org/showthread.php?p=4404087](http://ubuntuforums.org/showthread.php?p=4404087)

Greets

@ johnnybirdman:

Try using hdparm -B 192 /dev/sda as recommended for toshiba-drives in thinkwiki:
[http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking#Toshiba_MK2035GSS](http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking#Toshiba_MK2035GSS)

It still have an increase of load_cycle_count but using hdparm -B 192 gives the best results for my toshiba-drive. 

BTW: When I started using the ugly-fix, I did not have an increase of load_cycle_count putting apm to 192. For some reason this has changed after some time. What may be the couse for that?

---

### Post by johnnybirdman on 2008-02-25
> **b.q.wemer said:**
> Hi,



@ johnnybirdman:

Try using hdparm -B 192 /dev/sda as recommended for toshiba-drives in thinkwiki:
[http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking#Toshiba_MK2035GSS](http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking#Toshiba_MK2035GSS)
 

BTW: When I started using the ugly-fix, I did not have an increase of load_cycle_count putting apm to 192. For some reason this has changed after some time. What may be the couse for that?

I tried the 192 setting and still no luck.

Could something have changed because of an update??

---

### Post by blackhole54 on 2008-02-26
> **goombamd said:**
> **How do I find my load cycle count in a Hitachi 7200rpm 160gb drive? **


I run 
sudo smartctl -a /dev/sda | grep Load_Cycle_Count

and get

225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       94489287006


Obviously I don't think I've had 94489287006 load cycles.  This is a relatively new m1330 with a Hitachi 7200rpm 160 gb drive in it.   That brings up another question.  **What does "Old_age" mean? My hard drive is already considered old?**

I agree, that's a very strange output.  First, I suggest reading the [**smartctl***man page*](http://man.linuxquestions.org/?query=smartctl&section=0&type=2) for interpreting the output.  I've given you a link, but you can also find it on your local machine:

```

man smartctl

```

In it you will find that "old age" is the *type* of  the *attribute* Load_Cycle_Count:

> 
The Attribute table printed  out	by  smartctl  also  shows  the 	      'Type' of the Attribute.	Pre-failure Attributes are ones which, 	      if less than or equal to their threshold values, indicate	 pending  disk failure.  Old age, or usage Attributes, are ones which 	      indicate end-of-product life from old-age or  normal  aging  and 	      wearout,	if  the	 Attribute  value is less than or equal to the	      threshold.

Your raw value is 94489287006 which does seem ridiculously high.  However, since your *normalized value* (100) is well above the *threshold value* (0) it is presumably OK.  (See man page for explanation.)  So I would imagine each time the head is parked, the *raw value* is incremented by significantly more than one.  It is within the SMART specification to do so and has been reported for some drives.

(Note:  If you pipe the output of **smartcl** to **less** instead of to **grep** you will see the column headings for the table.)

---

### Post by blackhole54 on 2008-02-26
> **frodon said:**
> All that is explained in the french documentation the " lm-syslog-setup" script that come with laptop mode configure syslog for you, ...

I am not at a Linux machine right now. (And I have not read the French documentation.)   I recall running some script which made copies of *syslog.conf*.  But you still had to hand edit one or two of those copies to suppress the disk writing you didn't want.  (Maybe that's not needed with a newer version of the script?)  You also have to enable the behavior in *laptop-mode.conf*.


> ...  the noatime option is interesting too to avoid too much access on the hdd ...

Yes, I forgot to mention that.

> ... and there's also the "lm-profiler" profiler script which can check for you which process access too often your disk.

I didn't find that one too useful.  YMMV.

> 
I wasn't aware of any crash related to the laptop_mode could you point some references.

I was posting off the top of my head.  Searching back on this thread, I find the phrase "system hangs" used instead of "crash."  This was in [post #509](http://ubuntuforums.org/showpost.php?p=3847126&postcount=509) in response to my post about *laptop-mode* in [post #506](http://ubuntuforums.org/showpost.php?p=3843681&postcount=506).  The bug report is [here](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224).

---

### Post by frodon on 2008-02-26
Thanks blackhole54 for the links, i wasn't aware of this system hang issue anyway i don't seem to have problem with this i'm run it for 3 days now and haven't noticed any difference about system stability (though my wifi drivers hard lock my computer from time to time when too high traffic as usual).

I have checked the created syslog files and it seems good, the minus character is already applied on almost all logs only some (i guess imporatant) don't have the minus character.

Lets cross our fingers for hardy to implement all that by default.

---

### Post by blackhole54 on 2008-02-27
> **frodon said:**
> I have checked the created syslog files and it seems good, the minus character is already applied on almost all logs only some (i guess imporatant) don't have the minus character.

That is the default configuration of *syslog.conf*.  I believe initially all of the created files are identitcal to the original.  I edited *syslog-on-battery.conf* such that all of the entries had the minus sign.  But now that I look at what those entries are, (auth, uucp, mail, and news), maybe in practice it doesn't make much difference.

EDIT:  **crond** can generate entries in *auth.log*.  I happen to have **crond** disabled while on battery, but that has to be an individual decision I would think.

---

### Post by wolfchri on 2008-02-27
I finally fixed the issue for me:

[http://vale.homelinux.net/wordpress/?p=199](http://vale.homelinux.net/wordpress/?p=199)

The Fujitsu drive in my NX6325 is extremely power economic even with power management turned off and does not get over 45 degrees Celsius. The Samsung drive in my webserver (running on a notebook, too)   however is going to fry with a B 254 setting..... 

Maybe this helps other NX6325 users.

---

### Post by arang on 2008-02-28
so far so good in here i bought a dell inspiron 1420 and installed ubuntu on it it has a western digital hard disk wd1200 like those that are said to be affected the most by this bug, what i discovered is that while on AC the load cycle doesnt increase as expected and temp is 37°C on battery though the load cycle count increase is between 30 to 34 per hour and temp around 35°C (its summer here right now and temp is more or less 30°C) so doing my calcs using the laptop on battery for 16 hours a day the hard disk should last 3.4 years anything else should i check guys? i still cant believe it isnt being a b***ch, in the other side, i have the hard disk running in ATA mode cos i disabled the AHCI mode on BIOS i might activate it for 1 hour on battery to see if it is the reason of this, cos i talked to a friend that worked for seagate in an asian country not so long ago and told me that it might be the misuse or incompatibility between that mode and the new hard disks.

any ideas?

---

### Post by rybu on 2008-03-01
I have a USB drive that is unresponsive to hdparm and smartctl.  Does anyone know if there's something that can be done for it? 

```
rybu@rybu-laptop:/etc/acpi/start.d$ sudo hdparm -B 254 /dev/sdb

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Invalid argument
rybu@rybu-laptop:/etc/acpi/start.d$ sudo smartctl -A /dev/sdb 
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

```

It seems to suffer from the same issue -- it gets parked about every 10 -- 15 seconds.  Sometimes the "clank" is loud, sometimes it's almost inaudible.  Even if it's not causing any damage to the drive, the clank annoys me and I'd like to make it less frequent when my laptop is docked and on AC power.

hdparm and smartctl work fine with /dev/sda.

---

### Post by ludi on 2008-03-02
> **wolfchri said:**
> I finally fixed the issue for me:

[http://vale.homelinux.net/wordpress/?p=199](http://vale.homelinux.net/wordpress/?p=199)

The Fujitsu drive in my NX6325 is extremely power economic even with power management turned off and does not get over 45 degrees Celsius. The Samsung drive in my webserver (running on a notebook, too)   however is going to fry with a B 254 setting..... 

Maybe this helps other NX6325 users.
Finally!  I followed the steps described there and guess what, it worked!
Not just that, but my processor's fan seems to be more steadier now, usually it would float [variate] between higher and lower RPMs.
I'm also split my syslog file using the lm-syslog-setup.
However, I'm using Ext2 mounted with the noatime option (so that noatime option in the laptop-mode config file is a bit useless for me).
The HD is running cooler on AC now than with the 'ugly' B 255 'fix'.

HD:  Western Digital Scorpio

---

### Post by anindya_m on 2008-03-14
I am using a Hitachi drive on my Dell, with laptop-mode off. The drive head was parking every 2 secs or so. This fix stopped it. I have the power management off even while on battery when the laptop is not going to be moved around much. Actually I did not even notice something was wrong before I stumbled across this thread. I just though I'll provide some feedback.

I can suspend and hibernate without issues, and suspend/resume increases the Load_Cycle_Count counter by one (also the power and start stop counters). Rebooting causes an increase of 2-3, and I think that happens during the 10 secs while grub counts down.

Temperature is around 35-37 degrees Celsius, and there is no noticeable change in battery life (it might have changed by a few percent, but then I can't really tell). The drive seems quieter than before; I only hear a little rattling sound (different from the soft clicking while parking) which happens during i/o and is normal.

---

### Post by anindya_m on 2008-03-14
> **rybu said:**
> I have a USB drive that is unresponsive to hdparm and smartctl.  Does anyone know if there's something that can be done for it? 

```
rybu@rybu-laptop:/etc/acpi/start.d$ sudo hdparm -B 254 /dev/sdb

/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Invalid argument
rybu@rybu-laptop:/etc/acpi/start.d$ sudo smartctl -A /dev/sdb 
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

```

It seems to suffer from the same issue -- it gets parked about every 10 -- 15 seconds.  Sometimes the "clank" is loud, sometimes it's almost inaudible.  Even if it's not causing any damage to the drive, the clank annoys me and I'd like to make it less frequent when my laptop is docked and on AC power.

hdparm and smartctl work fine with /dev/sda.

It does not seem to be easy at the moment. However, do have a look at the following URL's:

[http://smartmontools.sourceforge.net/#testinghelp](http://smartmontools.sourceforge.net/#testinghelp)
[http://www.nslu2-linux.org/wiki/FAQ/SpinDownUSBHarddisks](http://www.nslu2-linux.org/wiki/FAQ/SpinDownUSBHarddisks)

---

### Post by ubuntu_demon on 2008-03-21
Please vote in ideastorm regarding this issue :
[http://brainstorm.ubuntu.com/idea/288/](http://brainstorm.ubuntu.com/idea/288/)

---

### Post by Yoooder on 2008-03-30
I've been tracking this issue on my affected ThinkPad T61p with a Seagete ST910021AS 100GB 7200 rpm harddrive.  This machine is brand new (had for ~10 days) and its load cycle count is at 26,000 with smart reporting 87% of life left for this attribute.

I have applied the 'ugly' fix and confirmed that it is working for my machine under Ubuntu--one note is that setting 'hdparm -B' 128 still results in periods of high increases in the load cycle count (as much as 12/min), and setting the value to 192 has the same effect as 255.  I will be doing some tests soon to try and determine a good balance for my machine.

Of interest to me is that for the past few days I have been running Vista (dual-boot) and after returning to Ubuntu the Load_Cycle_Count has increased by nearly 10,000!!!  The machine has been on AC power under Vista the vast majority of time; although Vista is running Lenovo's harddrive 'airbag' utility which uses the laptop's accelerometer to determine if it needs to park the drive momentarily.

I am tempted to buy a second HDD from a different manufacturer to see if this issue is drive-agnostic in my particular scenario.

---

### Post by blackhole54 on 2008-04-01
> **Yoooder said:**
> Of interest to me is that for the past few days I have been running Vista (dual-boot) and after returning to Ubuntu the Load_Cycle_Count has increased by nearly 10,000!!!

Thanks for posting that info.  I do wish the hard drive manufacturers themselves would weigh in on this issue!

---

### Post by Arcamis on 2008-04-01
> **Yoooder said:**
> 
Of interest to me is that for the past few days I have been running Vista (dual-boot) and after returning to Ubuntu the Load_Cycle_Count has increased by nearly 10,000!!! 

Did you try [notebook hardware control]("http://www.pbus-167.com/nhc/nhc.htm") on Vista ? :)
I hope this issue will be resolved, I'm waiting for my new laptop :lolflag:.

---

### Post by wandlerer on 2008-04-01
Hi,

I bought a new hard drive and installed Beta 1 last week.  A new "Green" Wester Digital drive, 500GB 3.5" SATA desktop drive.

Turns out, I started hearing clicking....  smartctl tells me there are 5500 load/unload counts already, in less than a 100 hours of operation.

Sounds like the same power management problem.  

So I tried hdparm -B 254 /dev/sda on it as sudo, and it gives me an error [drive is the correct device]:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error

I'm thinking the green drives are using power management to save power by acting similar to laptop drives.  However the hdparm error bothers me.  

Any ideas?  

the model # is  WD5000AACS

---

### Post by Yoooder on 2008-04-01
> **Arcamis said:**
> Did you try [notebook hardware control]("http://www.pbus-167.com/nhc/nhc.htm") on Vista ? :)
I hope this issue will be resolved, I'm waiting for my new laptop :lolflag:.

Yeah, after realizing the problem exists there as well I installed it to monitor the issue.  The good/mixed news is that it looks like NHC does the same thing as the 'ugly' Ubuntu fix.

At the moment, with the above fix, the only benefit of running Windows vs. Linux (as far as this issue is concerned) is that the I can set windows to never park/spin-down and still have the Lenovo tool to detect bumps and automatically park the heads--so I get safety and performance.  And with the laptop being a T61 I don't have to worry about temperature :-D

---

### Post by Yoooder on 2008-04-01
> **wandlerer said:**
> Hi,

I bought a new hard drive and installed Beta 1 last week.  A new "Green" Wester Digital drive, 500GB 3.5" SATA desktop drive.

Turns out, I started hearing clicking....  smartctl tells me there are 5500 load/unload counts already, in less than a 100 hours of operation.

Sounds like the same power management problem.  

So I tried hdparm -B 254 /dev/sda on it as sudo, and it gives me an error [drive is the correct device]:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error

I'm thinking the green drives are using power management to save power by acting similar to laptop drives.  However the hdparm error bothers me.  

Any ideas?  

the model # is  WD5000AACS

Also try 255, and 192 as values for hdparm -B

255 -or- 254 should disable power management (and the output should tell you just that), and I've seen 192 seem to stop it as well on my Seagate.

---

### Post by wandlerer on 2008-04-01
I have tried various numbers, just did 192, 255, 254, 252.

All failed with the same error.

/dev/sda:
 setting Advanced Power Management level to 0xc0 (192)
 HDIO_DRIVE_CMD failed: Input/output error


I found an old bug for HDIO_DRIVE_CMD, but it appears to be two years old or so. Don't know if that is the cause.

hdparm is version 8.6

---

### Post by blackhole54 on 2008-04-02
> **wandlerer said:**
> I bought a new hard drive and installed Beta 1 last week.  A new "Green" Wester Digital drive, 500GB 3.5" SATA desktop drive.

[...]

So I tried hdparm -B 254 /dev/sda on it as sudo, and it gives me an error [drive is the correct device]:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 HDIO_DRIVE_CMD failed: Input/output error


SATA drives are different than IDE (ATA, aka PATA) drives.  (I am not even sure **hdparm** is the right tool to use for SATA, but I haven't gotten it all sorted out yet.)  Even if **hdparm** is an appropriate tool, I don't think SATA responds to the -B parameter.  In any case, I have a WDC WD2500KS-00MJB0 SATA drive which responds with the same error to the -B parameter.  I don't think the error is anything to worry about.  But I don't know what to tell you about your head unloading problem.  (My SATA drive doesn't even report a load/unload count.)

---

### Post by geocritter on 2008-04-02
I had applied the -254 fix to my toshiba laptop with a seagate momentus (momentum?) and it worked pretty well, it seems.  This was on Hardy alpha 4 or 5, then I dist-upgraded and it's back with a vengeance (without it, under alpha versions, I was getting 2 to 3 per minute; with the fix, it was once every several minutes at most).  Then, after upgrading to beta, it's now doing about 1 every 5 seconds!!

I'm confused right now about it..I know that they are switching to pm-utils; my question is, what does that mean for fixing this issue?  Will this be something that we have to wait, then go in and fix, or will this be fixed by the time it's released natively?

I'm at the point where I have to switch back to XP (yuck!) until it's resolved; I can't afford another hard drive (this is the second one as it is, in 2 years).  Can somebody enlighten me?  I've read a lot of the posts, but it's all running in circles...I just need to know what to do...

Thanks!

---

### Post by Lacrimstein on 2008-04-02
This is a really dumb question, but I'll ask it just in case: Are 64-bit Ubuntus affected by this as well? I know it shouldn't make a difference, but I'm kind of desperate for some kind of good news about this...

---

### Post by frodon on 2008-04-03
> **geocritter said:**
> I had applied the -254 fix to my toshiba laptop with a seagate momentus (momentum?) and it worked pretty well, it seems.  This was on Hardy alpha 4 or 5, then I dist-upgraded and it's back with a vengeance (without it, under alpha versions, I was getting 2 to 3 per minute; with the fix, it was once every several minutes at most).  Then, after upgrading to beta, it's now doing about 1 every 5 seconds!!

I'm confused right now about it..I know that they are switching to pm-utils; my question is, what does that mean for fixing this issue?  Will this be something that we have to wait, then go in and fix, or will this be fixed by the time it's released natively?

I'm at the point where I have to switch back to XP (yuck!) until it's resolved; I can't afford another hard drive (this is the second one as it is, in 2 years).  Can somebody enlighten me?  I've read a lot of the posts, but it's all running in circles...I just need to know what to do...

Thanks!Configuring laptop mode correctly is surely the best way to fix this and make the head parking efficient and useful.

---

### Post by jespdj on 2008-04-03
> **blackhole54 said:**
> SATA drives are different than IDE (ATA, aka PATA) drives.  (I am not even sure **hdparm** is the right tool to use for SATA, but I haven't gotten it all sorted out yet.)  Even if **hdparm** is an appropriate tool, I don't think SATA responds to the -B parameter.  In any case, I have a WDC WD2500KS-00MJB0 SATA drive which responds with the same error to the -B parameter.  I don't think the error is anything to worry about.  But I don't know what to tell you about your head unloading problem.  (My SATA drive doesn't even report a load/unload count.)
As far as I know hdparm -B works on SATA drives just as well as on IDE drives. It works as it should on my M1330 (which has a 160GB Seagate SATA harddisk). Using smartctl also works normally, the drive does report the Load_Cycle_Count (and lots of other parameters).
> **Lacrimstein said:**
> This is a really dumb question, but I'll ask it just in case: Are 64-bit Ubuntus affected by this as well? I know it shouldn't make a difference, but I'm kind of desperate for some kind of good news about this...
Yes, it doesn't make any difference if you have 32-bit or 64-bit Ubuntu.

---

### Post by blackhole54 on 2008-04-04
> **jespdj said:**
> As far as I know hdparm -B works on SATA drives just as well as on IDE drives. It works as it should on my M1330 (which has a 160GB Seagate SATA harddisk). Using smartctl also works normally, the drive does report the Load_Cycle_Count (and lots of other parameters).

It must depend on the drive then.  This one drive is the first SATA I have dealt with.  I purchased a laptop with an IDE drive at the same time and it behaves as expected wrt these two matters.  (Both computers came with *edgy* pre-installed.)

---

### Post by geocritter on 2008-04-04
Okay, so the questions in my mind run like this:

1.  Has Hardy switched now to pm-utils?

2.  If yes, then what steps/scripts/script locations do we follow to set the hard drive parameters, since obviously this new change didn't solve the problem.

I'm just trying to get a plan of action going with my laptop...I guess it all kind of depends on whether the switch from acpi  has already been made to pm-utils and just didn't work (or more like, there's something different that's wrong), or if we're still in the process and I just need to wait until the release to know whether it natively solved the problem or not.  I would guess that it already has been implemented, since it's in beta now, but I might be wrong.  

Thanks!

---

### Post by Yoooder on 2008-04-04
> **Yoooder said:**
> I've been tracking this issue on my affected ThinkPad T61p with a Seagete ST910021AS 100GB 7200 rpm harddrive.  This machine is brand new (had for ~10 days) and its load cycle count is at 26,000 with smart reporting 87% of life left for this attribute.

...

Of interest to me is that for the past few days I have been running Vista (dual-boot) and after returning to Ubuntu the Load_Cycle_Count has increased by nearly 10,000!!!  The machine has been on AC power under Vista the vast majority of time; although Vista is running Lenovo's harddrive 'airbag' utility which uses the laptop's accelerometer to determine if it needs to park the drive momentarily.

Follow-up:  I've been benchmarking the problem on Vista (Home Premium SP1), and using Notebook Hardware Control to try different power profiles.  

Setting the profile and lettings the machine site idle for 20 minutes produced:
 @ hdparm -B 1     equivalent: 60 Load/Unload Cycles = 3/minute
 @ hdparm -B 128 equivalent: 44 Load/Cycles = 2.2/minute
 @ hdparm -B 255 equivalent:   3 Load/Unload Cycles = .15/min

---

### Post by yakshbuntu on 2008-04-07
Hi Geo,

1. It seems Hardy Heron uses pm-utils and my fix is working
2. I created three scripts and explained that in the following blog for fixing the load cycle count issue in Ubuntu Hardy Heron Beta

[http://duopetalflower.blogspot.com/](http://duopetalflower.blogspot.com/)

Regards,
Sankaran

---

### Post by frodon on 2008-04-07
Is laptop_mode no more present in hardy ?

---

### Post by revelationman on 2008-04-08
I have reading this issue for the last several days. In the last several months I have gone through 3 hard drives now this is not Ubuntu issue, mostly bad drives and a stolen drive that was marked as new from Ebay.

Now I just purchased a Seagate Momentous  120 sta drive I am going to load Ubuntu on it,I am a bit concerned of this hard drive issue. 

There has been kernel updates lately has this corrected the issue. 

I do not want to load Windows I really do not need it to be honest Ubuntu does  everything for me.

But this hard drive issue is a worry I do not want to go through another drive. 

I love Ubuntu the more you use it the more you love it. 

So any information on this issue would be greatly appreciated.

:guitar:

---

### Post by frodon on 2008-04-08
> **revelationman said:**
> I do not want to load Windows I really do not need it to be honest Ubuntu does  everything for me.
Some reported this bug to affect windows too, it might not even solve the issue.

---

### Post by revelationman on 2008-04-08
Do you know if Hardy  will address these issues, I will install Gusty and just watch the load count,  and do the update to Hardy.

---

### Post by frodon on 2008-04-08
The problem is somewhat related to too permissive hard drive firmware so i guess you can have the problem too with hardy.
Anyway it's not a big deal, you can just enable laptop mode and configure it as needed to apply the wanted hdparm -B values while on battery or while supply cable plugged.
It took me 10 minutes to configure and now i'm done with this for long.

---

### Post by geocritter on 2008-04-08
@ yakshbuntu:  I followed your scripts; unless something's missing or something on your page, then the results were negative for me.  Made no difference on my machine.

@revelationman:  I feel your pain.  I'm actually in the same boat...I've used linux for about 8 years now, and for the first time, am having to look at getting out of it.  

@frodon:  Windows doesn't do this on my machine or any of the others that I've paid attention to.  

I don't know if MS has figured out a fix, or if they are in bed with the manufacturers.  But the linux community has to deal with it one way or the other.  Right now, from all my research, we are no closer to a real solution than we were when it broke loose.  I'm sorry, but linux used to not do this on my machine.  Frankly, I don't think we're any closer to solving the problem than we were two years ago when it surfaced.  And I don't have the time to keep doing this stuff, re-applying scripts that are dodgy at best every time I update my computer.  The best answer that I've seen is to not use a laptop, since desktops are pretty much unaffected by it.  Which is not reasonable these days.

Sorry to sound like a downer...but I'm just kind of depressed..to be stalled on such a detail after all these years of the most amazing development an OS has ever seen...

---

### Post by frodon on 2008-04-08
The problem as a solution already (at least for those who can use hdparm -B), use and configure laptop_mode that's it.

In addition the problem is more related to too permissive hard drive firmwares than to an OS so even i it's you're right to want an OS side fix you can't expect it to be the default as the default should be that hard drive firmware doesn't allow such heavy head parking usage and it is the case for many hard drives.

So for your issue try to configure your laptop_mode before thinking to anything else.

---

### Post by Arcamis on 2008-04-08
> **frodon said:**
> The problem as a solution already (at least for those who can use hdparm -B), use and configure laptop_mode that's it.

In addition the problem is more related to too permissive hard drive firmwares than to an OS so even i it's you're right to want an OS side fix you can't expect it to be the default as the default should be that hard drive firmware doesn't allow such heavy head parking usage and it is the case for many hard drives.

So for your issue try to configure your laptop_mode before thinking to anything else.

But what to do if you're on hardy (I don't know if it's still installed by default or not) ? Install laptop_mode and use the known fix ? What about pm-utils ? I was considering using hardy as it has better intel driver than gutsy, but I don't really know pm-utils and if it's compatible with laptop_mode...

---

### Post by geocritter on 2008-04-08
As far as I know, the "dirty fix" doesn't apply to hardy, not directly, anyway.  Some people say it works, or some combination of it, but my understanding is that you have to put the scripts in different locations.   

The other thing is the whole "laptop mode" thing...my laptop does this when plugged in, as well as when it's not.  Meaning, when it's plugged in, I don't NEED laptop mode.  And like it's been said, laptop mode seems to have changed now that they are using pm-utils.  So it's all very confusing...

>"In addition the problem is more related to too permissive hard drive firmwares than to an OS so >even i it's you're right to want an OS side fix you can't expect it to be the default as the default >should be that hard drive firmware doesn't allow such heavy head parking usage and it is the case >for many hard drives"

Ok...two points here, one I agree with and one I don't:

I agree that this might be partly the cause of the problem.  But...following that same logic, why isn't Windows having this problem (and it ISN'T.  If it was, it would have surfaced as a problem in a way that you can only imagine.  The outcry would be all over the news).  Again, I say, somehow Microsoft has this thing figured out.  And that's what we need to do as a linux community.  Personally, I wish there was a way to get into a windows box and figure out what IT is doing to work around this problem...

I disagree, however, that we shouldn't expect it to be done by default.  Again...if Windows can do it, we should expect that we can too, with linux.

I'm not trying to start an argument or upset anyone...we're all on the same team...heaven knows there's enough infighting on the net as it is.  I'm just saying how I personally see it after all this time of using linux.  It just seems to me that we need to admit there's a real problem (some haven't even accepted this yet as a problem), stop blaming hardware manufacturers for making things in a way that doesn't work with linux (because, by now, I think it's clear that they don't CARE about linux or bsd...it works with the OS that has, what, 98% or so popularity), and work around it as we always have on other things.  Obviously it CAN be done (Microsoft did it).  

Heh...we're liable to find out that it's some oddball driver that's doing it, like a video driver or something totally unrelated.  That wouldn't surprise me :-)

---

### Post by frodon on 2008-04-08
Rather than writting long posts test ans see, don't always believe what other says, it sometimes better to just try and see. So try to configure your laptop mode and see by yourself if it solve your issue or not. As for pm-utils/laptop_mode interaction i don't know, the quickest way to know is to try IMO.

For the rest of your post this is not based on facts as vista users reports same issues so i think you view is biased because on your windows install you don't have the issue.
e.g. :
[http://ubuntuforums.org/showpost.php?p=4620526&postcount=746](http://ubuntuforums.org/showpost.php?p=4620526&postcount=746)
[http://forums.seagate.com/stx/board/message?board.id=ata_drives&message.id=1026](http://forums.seagate.com/stx/board/message?board.id=ata_drives&message.id=1026)

So despite your belief it is really bad coded hard drive firmware as main cause although the OS can make that it deteriorates your drive even faster.
So if no one mail hard drive manufacturers we are more likely to never get a real solution as head parking is  a really useful feature if well used.

PS: in case any of you has forgotten this option, you can use your hdparm.conf file to force the -B value on a drive and activate the daemon to make it run on boot.

---

### Post by geocritter on 2008-04-08
> **frodon said:**
> Rather than writting long posts test ans see, don't always believe what other says, it sometimes better to just try and see. So try to configure your laptop mode and see by yourself if it solve your issue or not. As for pm-utils/laptop_mode interaction i don't know, the quickest way to know is to try IMO.

I think you may be missing my point.  If we could ISOLATE the problem, it wouldn't be so bad; if we can lay our fingers on "eureka! this is what's wrong!", then people don't mind applying fixes while they wait for the next update.  But right now, nobody has a clear answer on the problem.  None.  There's lots of "try this, run that script, put it here, there, and everywhere", but not a regular solution.The user shouldn't HAVE to do this (right or wrong though it may be).  And they will not.  They will say "screw this, man" and go back to windows.

> **frodon said:**
> For the rest of your post this is not based on facts as vista users reports same issues so i think you view is biased because on your windows install you don't have the issue.
e.g. :
[http://ubuntuforums.org/showpost.php?p=4620526&postcount=746](http://ubuntuforums.org/showpost.php?p=4620526&postcount=746)
[http://forums.seagate.com/stx/board/message?board.id=ata_drives&message.id=1026](http://forums.seagate.com/stx/board/message?board.id=ata_drives&message.id=1026)

Ok...you say that i'm biased because my windows box isn't doing it, but under linux it does?  That's kind of why I'm here, isn't it??  ;-)   I realize that there might be some bugs in the firmware...and I realize that there are some people with problems under windows too...but be honest...it's not a big problem with laptops under windows.  If it were, you would see enough class action lawsuits to keep a million lawyers employed for a decade.   That said...the "facts" you quoted...the first, doesn't show how much was based on Vista and how much was under linux...only, "vast majority of the time", which means little.  The second quote has more merit.  It does bring me to ask, though... how do you get various brands of the same crappy firmware, same problems?  One company, ok, I can see that.  But not a group at the same time.  I just now thought about that...I'm leaning back toward software control being the common denominator here...

> **frodon said:**
> So despite your belief it is really bad coded hard drive firmware as main cause although the OS can make that it deteriorates your drive even faster.
So if no one mail hard drive manufacturers we are more likely to never get a real solution as head parking is  a really useful feature if well used.

Again, I never disagreed that the hardware wasn't crappy.  But I don't buy into the argument that theis is their problem, not ours.  We may not agree with that, but that's how it is.  Now...as far as putting on pressure, that might be do-able.  But unless we find out exactly WHAT is wrong here, and unite behind it, it'll never happen.  It's incumbent on the linux community to prove that the firmware is crappy to the hard drive vendors.  Otherwise, they'll see us as a fringe "odd uses of hard drives" group with limited effect on the millions of HD's produced each year, and never pay attention.  We have to find out what's wrong here.

> **frodon said:**
> PS: in case any of you has forgotten this option, you can use your hdparm.conf file to force the -B value on a drive and activate the daemon to make it run on boot.

This is one thing I need to try to figure out...I still can't figure out the hdparm/pm-utils/acpi stuff that we've got going...which one goes with what.  In other words....I'm back to square one.

---

### Post by frodon on 2008-04-08
geocritter,please  stop posting such long posts, that's useless, we explained you what to try so just try it.

For the rest this belongs ubuntu cafe discussions not support area discussion so please let the thread continues on topic so that we can help people in need of help.

This thread is to help users to fix their problem not for debate.

---

### Post by lavinog on 2008-04-11
> **frodon said:**
> geocritter,please  stop posting such long posts, that's useless, we explained you what to try so just try it.

For the rest this belongs ubuntu cafe discussions not support area discussion so please let the thread continues on topic so that we can help people in need of help.

This thread is to help users to fix their problem not for debate.

Frodon, I agree with your responses, and I thank you for your patience with this thread.
This thread has really taken alot of my time in the past...In the end of it all I have determined that this behavior is ok with the hd manufacturers. There is no data to say excessive load cycles will actually cause a drive to fail. (even most SMART data has yet to provide accurate failure analysis.) Windows did have this issue on some of my laptops...as far as class action lawsuits goes...many windows machines have too many 3rd party software running to cause the problem to show not to mention that you cant get smart data with windows without installing a 3rd party program.  One of my windows machines had a head crash with no warning.

I would recommend closing this thread and maybe continuing it onto a new one...this one takes about a 6 months now to read all of the posts...many new posts have already been addressed.
I also feel that this thread scares too many users that don't understand what the SMART data says.

---

### Post by njk123 on 2008-04-19
```

nitin@nitin-laptop:~$ sudo nautilus
Initializing gnome-mount extension
nitin@nitin-laptop:~$ xchat
The program 'xchat' is currently not installed.  You can install it by typing:
sudo apt-get install xchat
bash: xchat: command not found
nitin@nitin-laptop:~$ sudo smartctl -a /dev/hda
[sudo] password for nitin:
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Smartctl open device: /dev/hda failed: No such file or directory
nitin@nitin-laptop:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HM160HI
Serial Number:    S14QJD0Q217080
Firmware Version: HH100-11
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Sat Apr 19 18:49:42 2008 IST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (  32) The self-test routine was interrupted
                                        by the host with a hard or soft reset.
Total time to complete Offline 
data collection:                 (  62) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  62) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       152
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2000
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       15497
  5 Reallocated_Sector_Ct   0x0033   099   099   010    Pre-fail  Always       -       10
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       254
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       152
191 G-Sense_Error_Rate      0x0032   095   095   000    Old_age   Always       -       57341
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       6
194 Temperature_Celsius     0x0022   112   100   000    Old_age   Always       -       42 (Lifetime Min/Max 23/46)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       14440
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       306
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       720
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       00%       246         1873120
# 2  Short offline       Completed: read failure       00%       245         1875990
# 3  Short offline       Completed: read failure       00%       245         1871685
# 4  Short offline       Completed: read failure       00%       244         1874555
# 5  Short offline       Completed without error       00%        17         -
# 6  Short offline       Completed without error       00%         2         -
# 7  Short offline       Completed without error       00%         0         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Interrupted [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

I got this output and the start_stop_count was increasing rapidly. So, I applied hdparm -B 254 /dev/sda and now its under control. But what about the 
"SMART Self-test log structure revision number 1" thing? I mean the failures? The laptop is under warranty, so should I opt for a new HDD?. Also, will this bug get removed in 8.04? I mean I recently shifted from opensuse to ubuntu and love this distro and expect this bug to be removed :)

---

### Post by Mguel on 2008-04-19
> **yakshbuntu said:**
> 
1. It seems Hardy Heron uses pm-utils and my fix is working
2. I created three scripts and explained that in the following blog for fixing the load cycle count issue in Ubuntu Hardy Heron Beta
[http://duopetalflower.blogspot.com/](http://duopetalflower.blogspot.com/)


Thanks!!!

This worked for me on Kubuntu Hardy! (tested with hibernate and suspend)

Cheers,
Mguel

---

### Post by Mguel on 2008-04-20
> **Mguel said:**
> This worked for me on Kubuntu Hardy! (tested with hibernate and suspend)

If I restart thought, the count starts going up quickly... so I added

hdparm -B 255 /dev/sda

into rc.local file, which make load_cycle_count not to increase after reboot. Not sure if it's the best way, but using yakshbuntu fix plus this works for me in Kubuntu Hardy Heron.

cheers,
Mguel

---

### Post by Yoooder on 2008-04-23
> **revelationman said:**
> ...Now I just purchased a Seagate Momentous  120 sta drive I am going to load Ubuntu on it,I am a bit concerned of this hard drive issue...

I have a Seagate Momentus in my ThinkPad (original HDD) and do experience the Load_Cycle_Count problem under both Ubuntu Gutsy and Vista (haven't checked XP).  I haven't tried any other hard drives in this laptop.  I have had success with the suggested 'dirty fix' from the 1st post in this thread.

---

### Post by Belerophon on 2008-04-24
Hi.
I'm currently using Ubuntu gutsy and a few months ago I installed the "ugly fix"...[http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26).

And it really worked, the clicks stopped.

Hardy came out...so I want to upgrade.

What should I do, uninstall the ugly fix before the upgrade, or just do the upgrade without worries?

(This problem isn't fixed yet in Hardy, is it?)

Thanks.

---

### Post by JimmyK377 on 2008-04-24
Hey all, I'm testing the ugly fix before I upgrade to Hardy. I have tried both:

sudo hdparm -B 254 /dev/sda
sudo hdparm -B 255 /dev/sda

Both seem to have done the trick (miraculously the temperature of the hd seems to have actually gone down on average by 1 degree) and the load_cycle_count has stopped increasing.

The only difference being the response when I first enter them into the terminal.

With -254 I get:
setting Advanced Power Management level to 0xfe (254)

With -255 I get:
setting Advanced Power Management level to disabled

Which one should I use, 255 looks logical, but is there actually any difference, is there any benefit elsewhere with APM level at 0xfe (254) compared to disabled?


Also, there seems to be conflicting reports, will the ugly (why is it called that anyway?) fix work in Hardy?


EDIT:
and is -128 a suitable value for the ugly fix when on battery? It cycles about once every five seconds!


Thankyou,
JimmyK

---

### Post by quanumphaze on 2008-04-26
I just upgraded to Hardy today and the load cycle bug is still unfixed.

You might as well keep the fix.

---

### Post by olskar on 2008-04-26
I cant get the fix to work in hardy :(

---

### Post by suxen on 2008-04-26
Same issue here,
the ugly fix does not work under hardy. Could someone please help before my harddrive gets screwed up? Or should I go back to gutsy?

Thank you

---

### Post by eode on 2008-04-26
In order to fix the problem in hardy:

This post has two attachments.  They need to go into some folders inside /etc/pm.

Download the files, and then from the location you downloaded to, type the following:

```

sudo cp config.d.disk.sh /etc/pm/config.d/disk
sudo cp power.d.disk.sh /etc/pm/power.d/disk
sudo chmod ug+x /etc/pm/*.d/disk

```

..you are installing scripts into your system.  Unless the person directing you to do so is someone you know and trust, or you have some other way to verify that the person you receive advice from is trustworthy, then you should have someone who knows shell script check them out, or, if you know shellscript yourself, you should have a look at the files yourself.  The more ubuntu-forums points someone has, the more *likely* they are to be at least reasonably trustworthy in this regard, however, this is no guarantee.


-B.x-

---

### Post by calc on 2008-04-27
I tried to see if this problem occurs for my laptop under Vista but the results were inconclusive. Vista would NEVER stop reading/writing to the drive even an hour after it had booted, with me doing nothing to the system. So there was no way it could park the head with all that disk io going on. Perhaps the solution to this problem is to make a vistaiod daemon to emulate the high disk i/o load that Vista causes. :lolflag:

---

### Post by blackhole54 on 2008-04-27
> **calc said:**
> Vista would NEVER stop reading/writing to the drive ... Perhaps the solution to this problem is to make a vistaiod daemon to emulate the high disk i/o load that Vista causes. :lolflag:

Yeah, that will really help with power saving and disk temperature!  ;)
Better be careful -- MS might sue you for patent enfringement.  :???:

---

### Post by calc on 2008-04-27
> **blackhole54 said:**
> Yeah, that will really help with power saving and disk temperature!  ;)
Better be careful -- MS might sue you for patent enfringement.  :???:

Well the interesting bit is that unless other people have tested and managed to get Vista to stop reading/writing their drive it may not be known whether this problem is actually with Linux/Ubuntu or if it is just a widespread firmware issue that isn't seen under Vista due to how often (non-stop) it writes to the drive.

---

### Post by revelationman on 2008-04-27
I just find it ridiculous that we have to go through all these steps. I surprised that this issue was never resolved,that being said I have went back to Windows Vista the problem is gone. 
Before the flaming and all that think of the seriousness of this problem. Hard Drives are not cheap I have personally gone through 4 them so when I seen my results I said enough. 
I still run Ubuntu on my workstation at home they are fine 
I can honestly that at this current time Ubuntu is not meant for Laptops,hopefully a new patch will come out fix this issue. 
I do find it funny to have people do patches and scripts sorry that does not make sense. Imagine a new user first time on Linux and tell the sudo this sudo that. 
I do love Ubuntu and I will keep a constant update on this issue but for now I cannot afford putting in hard drives.Battery time is horrible with Ubuntu my battery on Windows can last over 2 hours Ubuntu less then 45 minuts. 
Again there is nothing wrong with Ubuntu on my desktops they run amazing but it is the laptops that I find that Ubuntu still needs to work on. 

:guitar:

---

### Post by ipatec on 2008-04-27
I posted [here]("http://ubuntuforums.org/showthread.php?t=770402") my querries. I want to know if I need to install the patch?

---

### Post by calc on 2008-04-27
> **revelationman said:**
> I just find it ridiculous that we have to go through all these steps. I surprised that this issue was never resolved,that being said I have went back to Windows Vista the problem is gone.

When you run Vista does it ever stop reading/writing to disk for you? Check resource monitor in the disk section. If it doesn't then that definitely would indicate why it doesn't have the problem on Vista, Vista never lets it park the head because it doesn't ever stop using the drive, which might be even worse than constantly parking the head. At least on my machine Vista never stopped reading/writing to disk even after letting it sit there for an hour not doing anything to the machine.

---

### Post by blackhole54 on 2008-04-28
> **calc said:**
> Well the interesting bit is that unless other people have tested and managed to get Vista to stop reading/writing their drive it may not be known whether this problem is actually with Linux/Ubuntu or if it is just a widespread firmware issue that isn't seen under Vista due to how often (non-stop) it writes to the drive.

You are, of course, right. And, of course, I was just being flip (hence the smilies).  I believe I have seen reports eslewhere on this thread that indicated people had observed rapid increase in *Load_Cycle_Count* under older versions of MS Windows, but I also think I have seen that contradicted.  In other words, lack of consensus.  As I've said before, I wish HD manufacturers would weigh in on this as presumably they understand this issue (the consequences, if not the OS specific cause) better than anybody.

---

### Post by calc on 2008-04-28
> **blackhole54 said:**
> You are, of course, right. And, of course, I was just being flip (hence the smilies).  I believe I have seen reports eslewhere on this thread that indicated people had observed rapid increase in *Load_Cycle_Count* under older versions of MS Windows, but I also think I have seen that contradicted.  In other words, lack of consensus.  As I've said before, I wish HD manufacturers would weigh in on this as presumably they understand this issue (the consequences, if not the OS specific cause) better than anybody.

Under older versions of Windows it is a bit harder to tell if anything is writing to the disk without using other utilities. However, it is very easy to see under Vista since it is shown in the resource monitor. And as long as the OS is reading/writing more often than the disk would want to park the head then the head will never get parked and won't show up as having the problem whether it really does or not.

Under linux it at least appears we see this issue because linux is not nearly as crap about always writing to the drive and the drives get the chance to park the heads. However ext3 does sync often (every 5s?) for safety by default and this causes the head to become unparked which is probably why we see the cycle count increasing.

I have a feeling increasing the commit option for mounting the ext3 fs' on the system would cause how often it cycles to go down. However it would be more risky as well.

mount (man page)

commit=nrsec
 Sync all data and metadata  every  nrsec  seconds.  The  default
 value is 5 seconds. Zero means default.

---

### Post by calc on 2008-04-28
[ngflushd]("http://www.j-pfennig.de/ngflushd/index.html") looks interesting, I haven't had time to test to see if this would actually solve the problem though.

---

### Post by calc on 2008-04-28
> **calc said:**
> [ngflushd]("http://www.j-pfennig.de/ngflushd/index.html") looks interesting, I haven't had time to test to see if this would actually solve the problem though.

Oh yea I forgot to mention, depending on the results of my testing, if it is useful, I may package and upload ngflushd to Debian and Ubuntu so that people can install that on their systems. Unless I find that there are other better utilities than this to achieve the same result. If anyone knows of anything better already please feel free to follow up and/or private message me about the alternatives. :)

---

### Post by revelationman on 2008-04-28
[QUOTE=calc;4814553]When you run Vista does it ever stop reading/writing to disk for you? Check resource monitor in the disk section. If it doesn't then that definitely would indicate why it doesn't have the problem on Vista, Vista never lets it park the head because it doesn't ever stop using the drive, which might be even worse than constantly parking the head. At least on my machine Vista never stopped reading/writing to disk even after letting it sit there for an hour not doing anything to the machine.[/QUOT

All discs are read but the main thing that I do not hear with Vista is that clicking noise. That was a constant in Ubuntu,now again I am very surprised that this issue was never resolved.
It all comes back to Power Management and this sadly Microsoft still hase the advantage. But I still run Ubuntu on my desktops but again for now Microsoft will remain on this laptop till the issue is corrected. I can still run Ubuntu virtually in a Windows enviroment so I guess that will have to do for now.

---

### Post by calc on 2008-04-28
> **revelationman said:**
> [QUOTE=calc;4814553]When you run Vista does it ever stop reading/writing to disk for you? Check resource monitor in the disk section. If it doesn't then that definitely would indicate why it doesn't have the problem on Vista, Vista never lets it park the head because it doesn't ever stop using the drive, which might be even worse than constantly parking the head. At least on my machine Vista never stopped reading/writing to disk even after letting it sit there for an hour not doing anything to the machine.

All discs are read but the main thing that I do not hear with Vista is that clicking noise. That was a constant in Ubuntu,now again I am very surprised that this issue was never resolved.
It all comes back to Power Management and this sadly Microsoft still hase the advantage. But I still run Ubuntu on my desktops but again for now Microsoft will remain on this laptop till the issue is corrected. I can still run Ubuntu virtually in a Windows enviroment so I guess that will have to do for now.[/QUOTE]

Well that sorta was my point, Windows Vista at least in my case NEVER lets the drive go into power management mode since it reads/writes the disk so much that it can't go into low power mode. If it did it might end up looking like the Ubuntu/Linux issue. I am pretty sure that clicking noise you hear is the drive parking its head when it goes into low power mode, since you never hear it at all on Vista your drive probably never is allowed to even go into low power mode. So Microsoft doesn't have the advantage in power management if it truly is never going into low power mode at all. The bug appears to be under Linux that writes happen to often but not often enough to stop low power mode (parking the head) to happen, so it parks and unparks frequently. I am still working on testing it more under Vista by reinstalling Vista once I can get a pristine copy of Vista (instead of the bloatware OEM version I currently have) but so far it would seem to me it is just as likely to have the problem if it just let the drive go into low power mode at all (by stopping the constant read/write). The Ubuntu issue probably can be resolved by using ngflushd or using a different fs, I am going to try to test out various filesystems and see which ones cause the problem the most. Ext3 by default commits its journal every 5 seconds which means if nothing else is writing to the disk at all then the drive would potentially go into low power mode (park the heads, etc) then would get woken back up when ext3 commits its journal. On a completely idle system, you probably would need to have no major processes running, it would probably increment load_cycle_count every 5 seconds, or 17280 times per day. On my system under informal testing I was seeing it increment about every 9 seconds which meant something else was doing a little IO occasionally keeping it from parking the head as often as it probably would want to. Of course delaying the commit could leave the fs in a bad state, but probably is worth the tradeoff to set it somewhat above 5s, maybe to 5m, which would take at least 5.7 years of uptime to reach 600K cycles.

So the good news is I think I know how to solve this problem for 8.10, but I need to do a lot more testing.

---

### Post by revelationman on 2008-04-28
> **calc said:**
> Well that sorta was my point, Windows Vista at least in my case NEVER lets the drive go into power management mode since it reads/writes the disk so much that it can't go into low power mode. If it did it might end up looking like the Ubuntu/Linux issue. I am pretty sure that clicking noise you hear is the drive parking its head when it goes into low power mode, since you never hear it at all on Vista your drive probably never is allowed to even go into low power mode. So Microsoft doesn't have the advantage in power management if it truly is never going into low power mode at all. The bug appears to be under Linux that writes happen to often but not often enough to stop low power mode (parking the head) to happen, so it parks and unparks frequently. I am still working on testing it more under Vista by reinstalling Vista once I can get a pristine copy of Vista (instead of the bloatware OEM version I currently have) but so far it would seem to me it is just as likely to have the problem if it just let the drive go into low power mode at all (by stopping the constant read/write). The Ubuntu issue probably can be resolved by using ngflushd or using a different fs, I am going to try to test out various filesystems and see which ones cause the problem the most. Ext3 by default commits its journal every 5 seconds which means if nothing else is writing to the disk at all then the drive would potentially go into low power mode (park the heads, etc) then would get woken back up when ext3 commits its journal. On a completely idle system, you probably would need to have no major processes running, it would probably increment load_cycle_count every 5 seconds, or 17280 times per day. On my system under informal testing I was seeing it increment about every 9 seconds which meant something else was doing a little IO occasionally keeping it from parking the head as often as it probably would want to. Of course delaying the commit could leave the fs in a bad state, but probably is worth the tradeoff to set it somewhat above 5s, maybe to 5m, which would take at least 5.7 years of uptime to reach 600K cycles.

So the good news is I think I know how to solve this problem for 8.10, but I need to do a lot more testing.

Well that is good and hopefully some resolution can come out of this. Funny I called Seagate and was advised they do not recommend the use of their drives on Linux (what a load of crap I told the agent).  
So what your saying Ext3fs is the file system to use instead of the traditional Ext2fs .
I will do some research on this .

:guitar:

---

### Post by ipatec on 2008-04-28
Under openSUSE this problem is solved...

---

### Post by calc on 2008-04-28
> **ipatec said:**
> Under openSUSE this problem is solved...

What did they do to solve it? Turn off ext3 commit, turn off head parking, install something like ngflushd, or what? This is a problem but not due to something that Ubuntu is doing wrong, at least from what I know so far, it appears to be a problem due to an interaction between journaling filesystems and aggressive power management on drives. It can be worked around, but not completely solved since there are tradeoffs involved.

---

### Post by revelationman on 2008-04-28
> **calc said:**
> What did they do to solve it? Turn off ext3 commit, turn off head parking, install something like ngflushd, or what? This is a problem but not due to something that Ubuntu is doing wrong, at least from what I know so far, it appears to be a problem due to an interaction between journaling filesystems and aggressive power management on drives. It can be worked around, but not completely solved since there are tradeoffs involved.

I do agree with the aggressive power management on hard drives,I have been reading file systems on linux. Now I have ask a friend about ext3 this what he uses since he machines are on all day. But this does not solve laptops,
what angers me still is the non acceptance of linux, but for me that tells me that companies do not believe in choice.
I did find this interesting link that a ubuntu developer pointed the fault at the firmware [http://www.advogato.org/person/mjg59/diary/82.html](http://www.advogato.org/person/mjg59/diary/82.html)
Well I do feel we will get this fixed and corrected, in the mean time i will go back to Ubuntu. I just cannot stand Vista lolol

---

### Post by calc on 2008-04-28
> **revelationman said:**
> I do agree with the aggressive power management on hard drives,I have been reading file systems on linux. Now I have ask a friend about ext3 this what he uses since he machines are on all day. But this does not solve laptops,
what angers me still is the non acceptance of linux, but for me that tells me that companies do not believe in choice.
I did find this interesting link that a ubuntu developer pointed the fault at the firmware [http://www.advogato.org/person/mjg59/diary/82.html](http://www.advogato.org/person/mjg59/diary/82.html)
Well I do feel we will get this fixed and corrected, in the mean time i will go back to Ubuntu. I just cannot stand Vista lolol

I haven't investigated the problem enough yet to know for certain if the problem is caused by ext3 or something else that is running on the system causing infrequent disk access. If the drive firmware is 'buggy' it is likely only buggy in that it has a park time that is set too low (too aggressive) for what Ubuntu/Linux is writing to the disk. There may not be a correct setting for this though which is part of what I am investigating.

I managed to get Vista reinstalled earlier today and it now stops writing to my disk after a couple minutes of bootup, which is significantly better than it was when using the OEM from factory install. So I should be able to find out if a similar problem occurs under Vista.

---

### Post by calc on 2008-04-28
Ok, after running blktrace on an Ubuntu system that isn't logged into X it doesn't increase load_cycle_count nearly as much, only 2 in a 3 minute period shortly after boot, so it definitely is not the filesystem itself causing the problem. So it rules out the commit frequency being the problem, or at least looks like it so far. I will be looking into what is causing disk i/o on an idle logged in session soon.

---

### Post by blackhole54 on 2008-04-29
> **calc said:**
> However ext3 does sync often (every 5s?) for safety by default and this causes the head to become unparked which is probably why we see the cycle count increasing.

I believe by default the kernel tries to flush some dirty buffers (if any) to disk every 5 seconds. And I think this is independent of file system. (The commit for ext3 I believe is a different issue relating to journaling.)  If there is nothing new to write then there is no disk activity.  This can be altered "on the fly," and, inf fact, that is exactly what *laptop-mode* does with its **MAX_LOST_WORK_SECONDS* variables.  If enabled, by default, it will only flush every 600 seconds (10 minutes) when on battery.  And that is what I do on my (no longer under support) *edgy* installation.  (On AC I have *laptop-mode* set up to disable disk APM.)  On this computer, the default *edgy* install was cycling load count aprox 200/hour.  On battery on *laptop-mode* it seems to be between 10 and 50/hour depending on what I am doing.  Sadly, (TMK) there are laptops that still "hang" when *laptop-mode* is enabled.

---

### Post by blackhole54 on 2008-04-29
> **calc said:**
> I will be looking into what is causing disk i/o on an idle logged in session soon.

You might want to review the earlier posts on this thread.  IIRC, people have already posted some results related to this.

---

### Post by calc on 2008-04-29
> **blackhole54 said:**
> I believe by default the kernel tries to flush some dirty buffers (if any) to disk every 5 seconds. And I think this is independent of file system. (The commit for ext3 I believe is a different issue relating to journaling.)  If there is nothing new to write then there is no disk activity.  This can be altered "on the fly," and, inf fact, that is exactly what *laptop-mode* does with its **MAX_LOST_WORK_SECONDS* variables.  If enabled, by default, it will only flush every 600 seconds (10 minutes) when on battery.  And that is what I do on my (no longer under support) *edgy* installation.  (On AC I have *laptop-mode* set up to disable disk APM.)  On this computer, the default *edgy* install was cycling load count aprox 200/hour.  On battery on *laptop-mode* it seems to be between 10 and 50/hour depending on what I am doing.  Sadly, (TMK) there are laptops that still "hang" when *laptop-mode* is enabled.

It does that but only when there is actually something to write. Applications like Firefox do so much IO even while just sitting there not actively going to new pages that it causes the load cycle count to go up fairly quickly ~ 1 every 20s even without doing anything. So changing the commit time will probably help some but won't solve the entire problem.

Also even changing to hdparm -B 127 on my drive doesn't seem to help much if at all which may be what people were referring to when claiming the drives have firmware issues.

---

### Post by calc on 2008-04-29
Well I have found that this is definitely not specific to Ubuntu or even Linux.

It also happens on both [Windows]("http://forum.notebookreview.com/showthread.php?t=191167") and [MacOS X]("http://discussions.apple.com/thread.jspa?messageID=7055342"). They have ways to fix it for MacOS but it seems the fix for Windows is just make sure that your drive is never idle, or to use the utility to force mode 254, which is just a ugly workaround, which we are already using in this thread as well. :(

On the Hitachi 5K160 drive I have setting -B to anything other than 254 does not seem to slow down the cycling any. I looked at their 'Feature Tool' they provide and it doesn't expose any way to fix the problem there either. It only allows default setting of what hdparm -B does, which doesn't seem to help at all.

ngflushd helps some it caused my cycle times to be ~ 1 per 39s. However at this point it appears the drives are buggy as was originally noted. At least if I understand it correctly a drive should respond to -B (0x01 - 0x7F) by increasing the time to park the head as the number increases. It does not appear to do this though, at least on Hitachi drives.

---

### Post by blackhole54 on 2008-04-29
> **calc said:**
> Applications like Firefox do so much IO even while just sitting there not actively going to new pages that it causes the load cycle count to go up fairly quickly ~ 1 every 20s even without doing anything.

The upper end of the range I gave (i.e. aprox 50/hour) while using *laptop-mode* _on battery_ was when I was using Seamonkey (Firefox's cousin).  The default configuration the computer came in (with *edgy* pre-installed) was giving [~ 1 every 20s](http://ubuntuforums.org/showpost.php?p=3653021&postcount=1) when the machine was idle!

>  So changing the commit time will probably help some but won't solve the entire problem.

Reitterating my last post, I believe the flush time is much more important for this than the commit time.

> Also even changing to hdparm -B 127 on my drive doesn't seem to help much if at all which may be what people were referring to when claiming the drives have firmware issues.

I wouldn't expect it to.  IIRC, it is 128 and above that is guaranteed to not spin down the disk (other than using -S) but can still park the head like crazy.  Also, be aware that there are only a few ranges (changing the value within a range won't make any difference).  You might see a difference if you go up to 192.

I believe the firware remark referred to the value of 128 commonly being the default and that that parks the head too often.  (Disclaimer:  I wasn't the one who made the comment.)

---

### Post by calc on 2008-04-29
> **blackhole54 said:**
> The upper end of the range I gave (i.e. aprox 50/hour) while using *laptop-mode* _on battery_ was when I was using Seamonkey (Firefox's cousin).  The default configuration the computer came in (with *edgy* pre-installed) was giving [~ 1 every 20s](http://ubuntuforums.org/showpost.php?p=3653021&postcount=1) when the machine was idle!



Reitterating my last post, I believe the flush time is much more important for this than the commit time.



I wouldn't expect it to.  IIRC, it is 128 and above that is guaranteed to not spin down the disk (other than using -S) but can still park the head like crazy.  Also, be aware that there are only a few ranges (changing the value within a range won't make any difference).  You might see a difference if you go up to 192.

I believe the firware remark referred to the value of 128 commonly being the default and that that parks the head too often.  (Disclaimer:  I wasn't the one who made the comment.)

Changing the flush time which is what ngflushd essentially does will not help with disk reads though which is why even with ngflushd being used I was still only getting average of about 39s between cycles.

If I remember correctly my system had three ranges listed in the utility, 0x01 - 0x7F, 0x80 - 0xBF, 0xC0-0xFD, none of them helped any on the amount of cycling. Only setting it to 0xFE (254) helped.

---

### Post by calc on 2008-04-29
> **calc said:**
> Well I have found that this is definitely not specific to Ubuntu or even Linux.

It also happens on both [Windows]("http://forum.notebookreview.com/showthread.php?t=191167") and [MacOS X]("http://discussions.apple.com/thread.jspa?messageID=7055342"). They have ways to fix it for MacOS but it seems the fix for Windows is just make sure that your drive is never idle, or to use the utility to force mode 254, which is just a ugly workaround, which we are already using in this thread as well. :(

Oh yea I forgot to mention that the fix for MacOS X also appears to set the drive to 254 it just does it via a utility at boot up every time instead of requiring the user to change the defaults via the vendor's hd utility.

---

### Post by Belerophon on 2008-04-29
> **quanumphaze said:**
> I just upgraded to Hardy today and the load cycle bug is still unfixed.

You might as well keep the fix.

Yup, I've just upgraded to Hardy...the fix continues to work...
still it would be nice to see this problem solved.

---

### Post by calc on 2008-04-29
> **Belerophon said:**
> Yup, I've just upgraded to Hardy...the fix continues to work...
still it would be nice to see this problem solved.

Contact your hard drive manufacturer for a utility that changes the time to park the head. It is a bug in the drive firmware itself and shows up on all platforms as noted in a post (with links) I made earlier. The only other solution for all platforms (Windows/MacOSX/Linux) is to either never let the drive go idle (which Windows with bloatware is fairly good at) or to set the parameter to 254 (0xFE).

---

### Post by suxen on 2008-04-30
eode,
thanks for the scripts. anyway, the problem remains. After a fresh boot, the LoadCycle Count stays constant, but after hibernate or suspend, the old "clicks" are back and the LoadCycle increases by up to 10 counts per minute. This was already the case with the original "ugly-fix" under hardy.
Any idea or suggestions?

thanks, suxen

---

### Post by frodon on 2008-04-30
I already suggested this before, if all you want is to set -B 254 option you can use hdparm daemon and configure the option in hdparm.conf file.
I have not tried hardy yet but you have also the option to use and configure laptop_mode which is for me the most convenient way to set the best settings.

On my ACER 5720G i've set -B 254 when not on battery and -B 205 when on battery, i chose 205 when on battery after some testing, with this setting i have between 15-30 head parking per hour which is what i wanted.

---

### Post by Belerophon on 2008-05-01
> **calc said:**
> Contact your hard drive manufacturer for a utility that changes the time to park the head. It is a bug in the drive firmware itself and shows up on all platforms as noted in a post (with links) I made earlier. The only other solution for all platforms (Windows/MacOSX/Linux) is to either never let the drive go idle (which Windows with bloatware is fairly good at) or to set the parameter to 254 (0xFE).

So, you're telling me that Hitachi(my drive manufacterer) should have a utility to fix this?

I've tried that once, downloaded some prog, from hitachi, to change drive parameters under windows, it didn't work under Vista. They had some more utilities, some boot cds to change something about the drive...but i just didn't tried them because meanwhile I found NHC (notebook hardware control) which fixes the problem under windows(works very well by the way, so anyone who's having the problem under windows can use it. It's free too;).
I think it does the same thing that the ugly fix does under linux, we can change some parameter to the value 254 under NHC.

Well, someday i'll try other utilities to see if I can solve this thing for good.

---

### Post by calc on 2008-05-02
> **Belerophon said:**
> So, you're telling me that Hitachi(my drive manufacterer) should have a utility to fix this?

I've tried that once, downloaded some prog, from hitachi, to change drive parameters under windows, it didn't work under Vista. They had some more utilities, some boot cds to change something about the drive...but i just didn't tried them because meanwhile I found NHC (notebook hardware control) which fixes the problem under windows(works very well by the way, so anyone who's having the problem under windows can use it. It's free too;).
I think it does the same thing that the ugly fix does under linux, we can change some parameter to the value 254 under NHC.

Well, someday i'll try other utilities to see if I can solve this thing for good.

They should have some way to fix this yes, whether it is something they will give out to end users I do not know. I have written to Hitachi specifically since that is the manufacturer of the drive I have, asking them what they expect to happen when all these drives end up dead due to their overly aggressive head parking. I should have a response back tomorrow according to their webpage (2 day turnaround).

Yes, all the utilities that they have publicly available can only tweak the same variable as 'hdparm -B'. I have tested both the 'Feature Tool' which boots of CD and the Windows 'Power Booster' utility. The 'Power Booster' utility doesn't appear to work under Vista but I could tell by the user interface that it only changes the same parameter as 'hdparm -B'.

I'll post to the list what I end up finding out from Hitachi, though it may take a while of email back and forth to get the point across to them. Considering this is seen by both MacOS X and Windows users as well perhaps they really don't care they are killing drives by their setting... Depending on the outcome of the tech support request perhaps enlightening them to the potential of a class action lawsuit in the US, would cause them to reconsider their defective design. It appears at least for my drive that it would reach their MTBF load cycle count (600K) within 63 days of actual use, so definitely well within a year of real world usage.

---

### Post by Seba4.0 on 2008-05-02
Hi guys,

I have had a similar exchange of emails with Hitachi support, here is the transcript of the last email I got;

[I]Dear Sir,

Thankyou for your reply.
We have tested this further in our CASLab and would suggest the following :

Download the latest version of the Hitachi Feature Tool - v2.08 - from the following page :

[http://www.hitachigst.com/hdd/support/download.htm#FeatureTool](http://www.hitachigst.com/hdd/support/download.htm#FeatureTool)

Create the self booting diskette or CD and reboot your system. 
Once the program has started, selct your drive, and from the Features menu, select 'Change Advanced Power Mode'

Move the slider to the right until 'ACTIVE IDLE' appears on the display.
The actual value does not matter, we just need it to show ACTIVE IDLE.

Press the Save button and then shutdown the system. 
The system needs to be actually turned off for the changes to take effect, a warm reboot will mean
the changes have been lost.

Now when using in a Linux system the HDD will never unload the heads  
When this mode is entered the HDD power requirements will drop by between 45
and 55% so heat generated will also reduce.

The point at which the HDD changes to Active Idle mode is determined by the Host's access patterns to the disk.

Best regards

Adrian Cutler
Hitachi Technical Support Center[/I]

Now, as I have a Hitachi Travelstar 7K100, the advice above given to me, only applies to the specific power management of these specific drives.
Let's see what the next advice from Hitachi for another user will be.
Cheers, Seba

---

### Post by calc on 2008-05-02
> **Seba4.0 said:**
> Move the slider to the right until 'ACTIVE IDLE' appears on the display.
The actual value does not matter, we just need it to show ACTIVE IDLE.


For my Hitachi drive the entire range from 0xC0 - 0xFE is listed as ACTIVE IDLE. So unless I am mistaken they are effectively telling you to do the same thing as turning off power management completely, which is confirmed by them telling you it will never unload the head. Does the setting work for you and does it cause the temperatures to be lower than just using 0xFE (254) itself? It sounds like they are saying even high performance mode (0xFE) will save power when not in use?

I still haven't gotten a response back from them about the problem myself.

---

### Post by calc on 2008-05-02
This is the first response I got back from them. It appears their low level support doesn't even realize that it is their drive firmware that determines how quickly the drive head is parked... ](*,)

Their idea to have things write to disk less is valid in that it would help solve the problem. However changing the disk idle time required to park the head would also solve the problem.

I followed up to their response and will see what they have to say.

> Thank you for contacting Hitachi Global Storage Technologies.

Hitachi Travelstar 5K160's drive are tested with load and unload cycles up
to 600,000. Hard drives are able to function perfectly within the tested
number of cycles and the data integrity is kept. However, the T5K160 drives
have not yet been tested more than 600,000. We assume that after reaching
the limit, the drives are still going to function well.

For normal PC user, it usually takes 2-3 years before the load/unload
cycles has been reached.

In your case, I think there's a command that has been created to make your
Linux OS communicate with the hard drive every 5-9 second. I recommend you
to review the applications running on your computer and disable this
activity.

We have no utility that can force the arms/actuator to lessen the load and
unload activity because it is the command in your system that control the
drive. Also, we can not recommend any other utility to forcefully lessen
the load/unload activity unless your system is communicating with the
drive.

If you have further questions, please feel free to contact us.

---

### Post by calc on 2008-05-02
Now I think we might be getting somewhere. The first half of the response was just the typical disable anything useful. The second half mentions that there is way to change the timers for the IDLE and STANDBY modes but didn't actually say how it is done at the protocol level. I think that we might not be doing that and it is possible that could be the cause of this problem.

Does anyone recall where the link and page number referring to the spec where 0xFE is defined as being max performance? I read about it a few days ago but have misplaced the link.

> You can set the drive to Active Idle mode with our Feature tool.

The Hitachi Feature Tool utility is available for download from the Hitachi
Website. I have included a direct link to the software and its associated
User Guide below.

[http://www.hitachigst.com/hdd/support/download.htm#featuretool](http://www.hitachigst.com/hdd/support/download.htm#featuretool)

We recommend reading the Feature Tool User Guide to understand the
utility's options and capabilities.

In normal condition when the drive is set for Low Power Idle, it will
unload the heads as soon as it feel there is no additional activities.

If the you want to disable the drive managing Load / Unload, you need to
set the drive to Active Idle.

Active Idle will keep the heads over the media, and not unload when the
drive feel there is no additional activity.

Also if you want to have the drive unload the heads but at a less frequent
basis. Your system needs to set either the IDLE or STANDBY timers.

The timers will count from the last command. When they reach the desired
time, the drive will enter the appropriate state (IDLE or STANDBY). Each
command received by the drive will reset the timer.

Please let us know if we can be of further assistance.

---

### Post by calc on 2008-05-02
If I read the document I found properly the 'hdparm -S' should be changing the standby timer which apparently is what Hitachi is claiming should change the amount of time before the head is parked.

I tried doing:

hdparm -S 12 /dev/sda - 1 minute
hdparm -B 128 /dev/sda - default for my drive

It then proceeded to increment the load cycle count at roughly 1 per 8s. So if that is how it is actually supposed to work to change the timer then there is a firmware bug, or 'hdparm -S' just plain does not work?

I emailed Hitachi to clarify that issue and will follow up here with what I find out.

---

### Post by calc on 2008-05-02
I looked in [AT Attachment with Packet Interface - 7 : Volume 1 - Register Delivered Command Set, Logical Register Set]("http://t13.org/Documents/UploadedDocuments/project/d1532v1r4a-ATA-ATAPI-7.pdf") and found IDLE (p 176) and STANDBY (p 326). I noticed that 'hdparm -S' actually uses the opcode for IDLE instead of standby so I modified it to send both commands to the drive. I then tested to see if it made any difference with varying times of 1m (12) to 20m (240) and it did NOT make any difference at all.

I'm still waiting to hear back from Hitachi as to why setting the standby timer has no apparent effect, when they claim this is the proper way of using the drive.

---

### Post by blackhole54 on 2008-05-03
> **calc said:**
> For my Hitachi drive the entire range from 0xC0 - 0xFE is listed as ACTIVE IDLE. So unless I am mistaken they are effectively telling you to do the same thing as turning off power management completely, ...

That is correct.  I did this using v2.07 of *ftool* last year.  This just sets the power management value used at powerup.  It can still be (temporarily) changed with **hdparm**, *laptop-mode* etc.  I did this because I have several systems that can boot on this machine, and this way I know the disk is in a (fairly) safe state w/o having to fine tune each system.  On the system which boots by default, I now control things with *laptop-mode*.


>  ... which is confirmed by them telling you it will never unload the head. Does the setting work for you and does it cause the temperatures to be lower than just using 0xFE (254) itself? It sounds like they are saying even high performance mode (0xFE) will save power when not in use?

I have seen no noticeable difference in temperature (YMMV!) and I would say the difference in power consumption is probably less than one watt (based on the Gnome tool that charts this).  I find their statement about saving power to be a head scratcher!

For the record, **hdparm -I /dev/sda** tells me:

```

ATA device, with non-removable media
	Model Number:       HTS541080G9AT00                         
	Serial Number:      XXXXXXXXXXXXXX
	Firmware Revision:  MB4OA60A

```

---

### Post by Keyper7 on 2008-05-03
Sorry if that's been asked before, and for being the second time I post this, but I had no luck with the search function and now I realize that perhaps it's more adequate to post this question here, as it fits the subject.

What should I pay attention to if Load_Cycle_Count is simply not listed by smartctl?

Here's what I get:

```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       7
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       1937
  4 Start_Stop_Count        0x0032   079   079   000    Old_age   Always       -       213763
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       1779
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       284
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2277
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       31
194 Temperature_Celsius     0x0022   127   094   000    Old_age   Always       -       37 (Lifetime Min/Max 22/48)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       102854
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       795
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       2513
199 UDMA_CRC_Error_Count    0x0036   252   252   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   252   252   000    Old_age   Always       -       0

```

Start_Stop_Count seems ridiculously high... Should I be worried?

---

### Post by blackhole54 on 2008-05-04
> **Keyper7 said:**
> Start_Stop_Count seems ridiculously high... Should I be worried?

I don't claim to be particularly knowledgeable about this.  Evaluate for yourself whether what I say makes any sense and whether it is applicable.

My _speculation_ is that perhaps **smartctl** doesn't list *Load_Cycle_Count* because your drive doesn't have the ability to unload the head (move it up onto a ramp so it is physically removed from the disk; in operation it "floats above" the disk on a stream of air).  I observe  that Start_Stop_Count/Power_On_Hours is somewhat in excess of 100.  I note that this is in the neighborhood of what some of us have obvserved with *Load_Cycle_Count* when it has been a problem.  _Presumably_ (see the **smartctl** *man page*) you aren't in trouble until the number listed under *Value* reaches (or approaches) the number under *Thresh* (in your case, zero).  _If_ the number under *Value* started at 100, then it is decreasing by 1 for (aprox) every 10,000 the raw number increases.  That is exactly the behavior my drive shows wrt *Load_Cycle_Count*.

Short answer:  you might want to be concerned.

---

### Post by HunterThomson on 2008-05-04
My laptop is two months old but I have been using the computer far more often in the last month now that I have internet. 

However:
3 (30,000)/2 (two months) = 1.5  
1.5 X 12 (months)= 18    
100-18= 82
At that rate the hard drive should last for a vary long time, right?
That is not bad right?

ATA device, with non-removable media
        Model Number:       Hitachi HTS542525K9SA00                 
        Serial Number:      *****************
        Firmware Revision:  BBFOC31P

----------------------
193 Load_Cycle_Count        0x0012   097   097   000    
Old_age   Always       -       30880

---

### Post by HunterThomson on 2008-05-04
> **Keyper7 said:**
> What should I pay attention to if Load_Cycle_Count is simply not listed by smartctl?

I typed this to get the load cycle count

sudo smartctl -a /dev/sda | grep 193

---

### Post by Keyper7 on 2008-05-04
> **blackhole54 said:**
> Short answer:  you might want to be concerned.

Thank you, that's what I wanted to know.

If think it's very likely that the Start_Stop_Count started at 100. In that case, 79 is damn scary for a laptop that is only a couple of months old.

> **HunterThomson said:**
> I typed this to get the load cycle count
sudo smartctl -a /dev/sda | grep 193

That doesn't work. As you can see, 193 is not listed. Thanks anyway.

---

### Post by Keyper7 on 2008-05-04
Ah yes, did an hdparm -B 254 and now Start_Stop_Count is stable. Finally.

---

### Post by blackhole54 on 2008-05-05
> **HunterThomson said:**
> 3 (30,000)/2 (two months) = 1.5  
1.5 X 12 (months)= 18    
100-18= 82
At that rate the hard drive should last for a vary long time, right?
That is not bad right?

100/18 = 5.5 years

Realize that is a projection based on a limited sampling of one parameter.  Extrapolations are always a little risky.  And there are other causes of death.  But this one calculation would lead to an expectation in excess of 5 years ...

> My laptop is two months old but I have been using the computer far more often in the last month now that I have internet. 

... _except_, this change in usage pattern might mean you should reduce the above calculation by up to a factor of two.  Is less than 3 years acceptable to you?

Since your situation isn't critical, you could wait another month or two and get a better idea.  (In that case, compare the difference between now and then divided by the difference in time. I.e. just discard the first two months of data since you didn't have a stable usage pattern.)

---

### Post by haizaar on 2008-05-05
> **geocritter said:**
> @ yakshbuntu:  I followed your scripts; unless something's missing or something on your page, then the results were negative for me.  Made no difference on my machine.

He has got a small typo there. Look at my comments to his post (on blogspot)

---

### Post by AbtZ on 2008-05-05
Why hasn't this been fixed yet? I just installed Hardy on my laptop and the harddrive clicks every few seconds, increasing the Load_Cycle_Count like crazy.

---

### Post by frodon on 2008-05-05
> **AbtZ said:**
> Why hasn't this been fixed yet? I just installed Hardy on my laptop and the harddrive clicks every few seconds, increasing the Load_Cycle_Count like crazy.Because this is not the OS fault mainly ;)

The key point is too permissive drive firmware and this is independant of the OS. The problem exists also on windows and MACOSX.

THere're many different fix proposed in this thread though.

---

### Post by AbtZ on 2008-05-05
I'm dual booting this laptop. This does not happen in Windows for me.

---

### Post by frodon on 2008-05-05
Is this supposed to tell that for you it's not firmware related just based on the simple fact that you don't have the issue on windows ?

---

### Post by AbtZ on 2008-05-05
No, it may still be firmware related -- I don't know. But Windows doesn't destroy my harddrive. Perhaps it overrides the hardware defaults or something.

The issue is that Ubuntu is destroying my hard drive by allowing insane hardware defaults.

Also, I read somewhere that Debian has released a fix.

---

### Post by frodon on 2008-05-05
Anyway it takes 5 minutes to fix this, so it's up to you to fix your ubuntu or change distro.

---

### Post by ethanay on 2008-05-05
Abtz -- can  you check and see what the default apm setting for windows is on 1) boot 2) resume from suspend/hibernate 3) change power state (ac to battery, etc)?  there should be a similar cli-based utility for windows...

that would be very helpful overall, i think -- i have yet to see ANYONE post this information (just anecdotal stuff...) but admittedly i haven't ready EVERY single post :)

---

### Post by AbtZ on 2008-05-05
> **frodon said:**
> Anyway it takes 5 minutes to fix this, so it's up to you to fix your ubuntu or change distro.
Sure, it's 5 min for me to fix it, since I know about the issue. But my main gripe with it is that for someone else it might not be that obvious why their hard drive keeps making those "strange clicking sounds" and then they are (rightfully) gonna blame Ubuntu when their hard drive dies on them after only a year.

I've been seriously considering switching to Debian, or perhaps Arch. The problem is I like Ubuntu, and I also don't have the time currently to learn something new.

> **ethanay said:**
> Abtz -- can  you check and see what the default apm setting for windows is on 1) boot 2) resume from suspend/hibernate 3) change power state (ac to battery, etc)?  there should be a similar cli-based utility for windows...

that would be very helpful overall, i think -- i have yet to see ANYONE post this information (just anecdotal stuff...) but admittedly i haven't ready EVERY single post :)
I found smartmontools for windows, but I have no idea how to check "apm settings" with it. :confused:

However, I know that in windows my drive doesn't do that clicking sound a few times every minute. Also, back with Gutsy, I checked the Load Cycle Count in Ubuntu, rebooted into Windows, used it for about an hour, then booted back to Ubuntu. I don't remember the exact numbers, but the count hadn't risen by more than 3-4 tops. Compare this to Ubuntu where it can go up by 10 after only 5 minutes.

Anecdotal too, perhaps, but as I said, I don't know how else to check it.

---

### Post by calc on 2008-05-05
> **AbtZ said:**
> Sure, it's 5 min for me to fix it, since I know about the issue. But my main gripe with it is that for someone else it might not be that obvious why their hard drive keeps making those "strange clicking sounds" and then they are (rightfully) gonna blame Ubuntu when their hard drive dies on them after only a year.

I've been seriously considering switching to Debian, or perhaps Arch. The problem is I like Ubuntu, and I also don't have the time currently to learn something new.


I found smartmontools for windows, but I have no idea how to check "apm settings" with it. :confused:

However, I know that in windows my drive doesn't do that clicking sound a few times every minute. Also, back with Gutsy, I checked the Load Cycle Count in Ubuntu, rebooted into Windows, used it for about an hour, then booted back to Ubuntu. I don't remember the exact numbers, but the count hadn't risen by more than 3-4 tops. Compare this to Ubuntu where it can go up by 10 after only 5 minutes.

Anecdotal too, perhaps, but as I said, I don't know how else to check it.

There are two problems here, one is that at least some drives' firmware appear to be buggy. The other is that Ubuntu doesn't appear to set the standby timer by default.

Windows likely doesn't show the problem due to it not letting the disk become idle long enough to park, though it might set the standby timer. On my system the OEM install of Vista would never stop reading/writing to the disk, so there was no way to tell if the problem existed under Windows, since it could never activate power management mode.

The only fix for hard drives that have broken firmware is to completely disable head parking by sticking it into Active Idle mode, eg 'hdparm -B 254'. This really isn't a good solution though since it uses more power and if the drive is jolted too much it could cause the head to crash. Of course while the disk is doing io it would be suspectible to that issue even with power management on, but with head parking disabled anytime the system is on it would be at risk.

Ubuntu should be setting 'hdparm -S' to a useful value, and for people without buggy drives it should work fine to just add that to /etc/hdparm.conf.

I still haven't heard back from Hitachi about why their 5K160 drives don't properly work with the standby timer.

---

### Post by blackhole54 on 2008-05-06
> **frodon said:**
> Because this is not the OS fault mainly ;)

The key point is too permissive drive firmware and this is independant of the OS. The problem exists also on windows and MACOSX.

IMHO this situation would best be viewed as an interaction between disk settings, disk firmware, and OS.  Not simply the fault of one or the other.  Disk behavior that might be adequate or best for one OS might not be for another.  As an extreme example, very agressive power management would probably be fine for single tasking systems like MS-Dos or FreeDos.  Certainly these systems would not go unparking the head while the system was idling!

At another extreme, it appears the combination of default *edgy eft* and the laptop that I bought with it pre-installed was [a disaster](http://ubuntuforums.org/showpost.php?p=3653021&postcount=1) if, in fact, I could expect disk failure not long after a million head load cycles.  However, a certain confiugration of laptop-mode on that computer is fine on AC (with disk APM disabled) and marginally acceptable on battery with, at worst, slightly less than one cycle per minute.

I've read conflicting accounts of problems with MS products.  I've read no reports for Mac OS X.  (There's probably 200 -300 posts on this thread I've not yet read.)

It seems to me that the best long term solution has not yet been arrived at.  This might require meaningful consultation with the drive manufacturers themselves.  In the meantime, as you point out, this thread includes serveral work-arounds.

Anyway, that's my $0.02.

---

### Post by AbtZ on 2008-05-06
All right, I'm confused. I followed this [guide]("http://ubuntuforums.org/showpost.php?p=3675960&postcount=26") to the letter, and it seems to be working -- after a fresh boot. When I resumed after suspending, however, my HD started going crazy parking/unparking 10 times a minute again.

```
#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda
  hdparm -B 255 /dev/sda
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 128 /dev/sda
fi
```

I'm no programmer, but I assume this is because of the "else" parameter, i.e. it couldn't determine that the computer was on ac power and so reverted to ultra-aggressive power managment.

What's the battery mode equivalent of on_ac_power? "on_battery_power"? I'm gonna modify the code so that it only goes into power management mode if it knows it's running on *battery*, a better solution in my book.

---

### Post by calc on 2008-05-06
> **blackhole54 said:**
> I've read conflicting accounts of problems with MS products.  I've read no reports for Mac OS X.  (There's probably 200 -300 posts on this thread I've not yet read.)

[This]("http://discussions.apple.com/thread.jspa?messageID=7055342") appears to be the same issue under MacOS X, and they explain how to do what looks like the equivalent of 'hdparm -B 254' under MacOS X in the thread.

---

### Post by jakon on 2008-05-06
AbtZ, the guide of ubuntu_demon doesn't work anymore on Hardy.

The "normal" way to set your hd power management setting is through /etc/hdparm.conf. Unfortunately, because of [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/199094](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/199094) , these settings will be lost upon suspend/resume. But, i have posted a patch there that should fix this issue.

You could test the patch, stop the klicking, help fix bug 199094 by:

1. ```
sudo gedit /etc/hdparm.conf
``` Add ```
/dev/sda {
apm = 254
}
``` to the end of the file.

2. Save [http://launchpadlibrarian.net/14195287/30hdparm](http://launchpadlibrarian.net/14195287/30hdparm) to /tmp/30hdparm . Then,
```
sudo install /tmp/30hdparm /etc/pm/sleep.d/
```
(Note: /usr/lib/pm-utils/sleep.d/ also works, but /etc/ is the cleaner solution)

3. Suspend/Resume or reboot to make it take effect.

4. Report back here.

That's it. You can undo it by deleting /usr/lib/pm-utils/sleep.d/30hdparm . Don't forget that this makes your hd more vulnerable to bumps.

---

### Post by blackhole54 on 2008-05-06
> **AbtZ said:**
> ... and it seems to be working -- after a fresh boot. When I resumed after suspending, however, my HD started going crazy parking/unparking 10 times a minute again.

```
#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda
  hdparm -B 255 /dev/sda
else
  # either on battery or power status could not be determined
  # so quickly park the head to protect the disk
  hdparm -B 128 /dev/sda
fi
```

I'm no programmer, but I assume this is because of the "else" parameter, ...

No, if **on_ac_power** works on your computer at any time, it should work all of the time.  In fact, you can run it from the command line at any time:

```

on_ac_power
result=$?
echo "The result from on_ac_power is:  $result"

```

The **on_ac_power** *man page* will tell you how to interpret the result.  (Look at *EXIT STATUS*.)

What is almost certainly happening is that when you *resume* after *suspend*, the disk is back in its default state, and the script (which would correct things) does not get run.  One (not entirely satisfactory) solution is to run the script (not what I just posted!) manually, using **sudo**.  (You might want to try this at least once just to convince yourself it does work.)  The "correct" solution would be to put a copy of this script someplace where it will automatically get run when you *resume*.  I am not sure where that would be.  I _think_ I recall a discussion of that somewhere earlier on this thread, but the answer might have changed for *hardy heron*.

BTW, to my knowledge it is generally on desktops (w/o a battery) that **on_ac_power** returns "don't know."

---

### Post by AbtZ on 2008-05-06
OK, thanks guys. 

jakon, I installed your script and rebooted. It seems to work properly, even after resume.

However, it would be nice to have some power management going when I'm on battery. Is it at all possible?

Should I delete the files I installed from ubuntu_demons guide? I had the 99-hdd-ugly-fix.sh file installed to these locations:

```
/etc/acpi/suspend.d/
/etc/acpi/resume.d/
/etc/acpi/start.d/
/etc/acpi/ac.d/
/etc/acpi/battery.d/

```

It is a bit unfortunate that the first fix you find no longer works. Is something going to be done officially? Personally, I think that people will get more pissed if their hard drive stops working after less than a year than if they are clumsy and drop their laptop on the ground.

---

### Post by calc on 2008-05-07
It appears setting your drive (at least for Hitachi) into Active Idle (eg 192-254 for 5K160) and setting the standby timer works. Hitachi claims at least for their drives 255 disables the power management completely.

So something like this:

hdparm -B 254 /dev/sda (Active Idle - Max Performance)
hdparm -S 12 /dev/sda  (60 seconds)

Seems to cause the load_cycle_count to increase at a much slower rate but without completely disabling head parking.

I think the standby timer, if not set, defaults to disabled which is why 'hdparm -B 254' appears to fix the problem by turning off head parking, it actually doesn't but the fact that the standby timer is disabled causes it to not park the head.

What I still don't know is why the other power management ranges don't appear to take into account the standby timer. I will be asking Hitachi about that tomorrow.

---

### Post by nimphelos on 2008-05-07
I have a problem of understanding of Load_Cycle_Count on my laptop. I bought an HP 530 5 days ago. While I browsing into HP530 thread on forum I saw there people mentioned about Load_Cycle_Count issue. And I read all the articles about this bug. Not all this thread yet, but I'll read all thread as soon as I have time enough.

After reading related articles, I installed smartmon and I started to inspect Load_Cycle_Count. At first check it was (90) and it made me happy. After a few more checks I leave the laptop open for about 7 or 8 hours. Then I turned it off. Yesterday I made one more check and it was (3500!!). After that I read bug fix post again. And there I saw bug must be inspected for a week at least. Then I decided to wait and watch Load_Cycle_Count for a few days. 

After 3 days usage now my Load_Cycle_Count is (4400). Few minutes before posting this post, I opened a terminal and watched Load_Cycle_Count for about 5 minutes and in this time Load_Cycle_Count incrased for about 10 per minute. This is a huge incrase! I decided to reboot for a clean check. Actually I wanted to check which one of the running programs causing this huge incrase. After reboot suddenly everything is fixed. Now my Load_Cycle_Count stands still there. I opened lots of application in backround nothing happened.

Now I realized this is a hard to inspect issue actually. I need some advices here. Should I apply the fix, or should I wait and watch Load_Cycle_Count some more?

---

### Post by AbtZ on 2008-05-07
It was a bit sporadic for me too. Sometimes nothing happened for maybe 5 minutes, then in less than one minute the count would increase by 10 or more. I got the insane increase more often than not, however.

I tried turning off tracker, but it did not seem to help. In the end I figured -- why risk it? -- and applied the fix.

If you have gone from <100 to >4000 cycle counts in just a few days, I would advise you to fix it too.

---

### Post by jakon on 2008-05-07
AbtZ, power management can be achieved with laptop-mode. Do```
sudo gedit /etc/laptop-mode/laptop-mode.conf
``` and look for ```
#
# Should laptop mode tools control the hard drive power management settings?
#
CONTROL_HD_POWERMGMT=1


#
# Power management for HD (hdparm -B values)
#
BATT_HD_POWERMGMT=1
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254
```
Set CONTROL_HD_POWERMGMT=1 and the rest to whatever you like ( see [http://linux.die.net/man/8/laptop-mode.conf](http://linux.die.net/man/8/laptop-mode.conf) ).
It's a bit unclear for me who will win in setting the HD PM then (laptop-mode or 30hdparm) - when resuming on battery power for example. Tell me if you find out ;)
If laptop-mode does everything correctly you can try to remove my script.

> Should I delete the files I installed from ubuntu_demons guide? I had the 99-hdd-ugly-fix.sh file installed to these locations: These aren't executed on Gutsy anyway, it kind of doesn't matter.

---

### Post by BandD on 2008-05-08
jakon,

Thanks so much for your fix.  It works perfectly for me.  I was getting tired of manually changing the hdparm value everytime I resumed my computer.  And for some reason I couldn't get laptop-mode to control hdparm correctly either.  But this just works!  So thanks for sharing the info!

---

### Post by caraboy on 2008-05-08
Hello, I have a HP 530 laptop with a 160GB samsung HDD.

Running Ubuntu 8.04, dual boot with windows.

This is what smartctl outputs on my config:
```

193 Load_Cycle_Count        0x0012   095   095   000    Old_age   Always       -       60418
225 Load_Cycle_Count        0x0012   095   095   000    Old_age   Always       -       60418
 9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       155410

```I noticed that the Load_Cycle_Count increases by 10-15 per minute (from 60408 to 60418 in 1 min, for example).

Should I be worried?

---

### Post by frodon on 2008-05-08
In general we deem that a 30 head parking per hour ratio indicates a normal behaviour for a laptop. So calculate the ratio with your current *Load_Cycle_Count* and your current *Power_On_Hours*.

If your ratio is a lot above 30 then you may want to fix this.

---

### Post by calc on 2008-05-08
> **frodon said:**
> In general we deem that a 30 head parking per hour ratio indicates a normal behaviour for a laptop. So calculate the ratio with your current *Load_Cycle_Count* and your current *Power_On_Hours*.

If your ratio is a lot above 30 then you may want to fix this.

I did some testing and show the results below. First column is standby timer and the second is how often cycle count increases on average.

 5s - ~  22s
15s - ~  45s
30s - ~ 115s
45s - ~ 175s
60s - ~ 350s

This probably varies based on what applications the user is running, but it looks like 60s standby timer would likely be fine, at least for my machine. If it continued at that rate it would take 6.7 years of constant use to reach 600K cycles.

---

### Post by caraboy on 2008-05-08
> **frodon said:**
> In general we deem that a 30 head parking per hour ratio indicates a normal behaviour for a laptop. So calculate the ratio with your current *Load_Cycle_Count* and your current *Power_On_Hours*.

If your ratio is a lot above 30 then you may want to fix this.


Ok, so from what I read on a topic I should do something like *Load_Cycle_Count/**Power_On_Hours right? In my case this is 0,38, no way closer to 30.*

---

### Post by frodon on 2008-05-08
38 looks acceptable to me as head parking is interesting too, it's up to you in this case as 38 is not a bad ratio for a laptop.

---

### Post by AbtZ on 2008-05-08
> **caraboy said:**
> I noticed that the Load_Cycle_Count increases by 10-15 per minute (from 60408 to 60418 in 1 min, for example).

Should I be worried?
I would not compare my Load_Cycle_Count to Power_on_Hours were I you. It's not a good method, especially if you've been running Windows a long time before installing Ubuntu; Windows in my experience does not make your Load_Cycle_Count go insane.

Do this instead: 1. Start Ubuntu, check the Load_Cycle_Count. 2. Do whatever for an hour or so. 3. Check Load_Cycle_Count again. 4 Calculate. 5. If it's greater than 30/hour, apply fix.

---

### Post by frodon on 2008-05-08
> **AbtZ said:**
> I would not compare my Load_Cycle_Count to Power_on_Hours were I you. It's not a good method, especially if you've been running Windows a long time before installing Ubuntu; Windows in my experience does not make your Load_Cycle_Count go insane.This has been proven to be a false belief and this thread also reflect this.

> **AbtZ said:**
> Do this instead: 1. Start Ubuntu, check the Load_Cycle_Count. 2. Do whatever for an hour or so. 3. Check Load_Cycle_Count again. 4 Calculate. 5. If it's greater than 30/hour, apply fix.This would be a good way if you take at least a one month sample or several weeks.
30 is fictive limit, it can be more and perfectly normal.

---

### Post by AbtZ on 2008-05-08
Why do you need such a long time interval? I'd say a few hours usage is enough to give you a picture of what it's gonna be like in the future too.

> **frodon said:**
> This has been proven to be a false belief and this thread also reflect this.
My personal experience with the two laptops I own says otherwise. I will give it a go again, however, since you seem to be so sure about this.

EDIT: Okay, I went through the unpleasant experience of running Windows for approx 2 hours. During this time my load cycle count went up by 32. That is 16 load cycles an hour, including it going into suspend mode twice. This seems perfectly acceptable to me, and I will stick to what I said earlier: Windows, in spite of all its other faults, does not kill your hard drive like Ubuntu does.

---

### Post by frodon on 2008-05-09
> **AbtZ said:**
> This seems perfectly acceptable to me, and I will stick to what I said earlier: Windows, in spite of all its other faults, does not kill your hard drive like Ubuntu does.Basing arguments on a single experience is what killed this thread and still continues to kill it, it makes it difficult or nearly impossible to extract real information in the middle of a lot of misinformation and this is preventing unfortunately some of those willing to help to help.

I was not talking about your experience AbtZ neither saying that you should worry about your windows installation if it seems fine for you. I'm just saying that the problem has been shown to exist on any OS and this is an _indisputable fact_.
Considering this, talking about ubuntu saying that it kills your drive is misinformation and a bit flaming by itself especially considering the incredible amount of time some spent in this thread trying to clear misunderstanding/misinformation so that the legend of ubuntu killing your drive would disappear.

The bug report i filled about missing laptop_mode documentation is currently being dealt with and hopefully we will just be able to point users worried about head parking to this documentation to control accurately head parking the right way through laptop_mode.

---

### Post by blackhole54 on 2008-05-09
> **frodon said:**
> The bug report i filled about missing laptop_mode documentation is currently being dealt with and hopefully we will just be able to point users worried about head parking to this documentation to control accurately head parking the right way through laptop_mode.

At one time *laptop-mode* was reported to cause some computers to "hang."  My understanding was that this was the reason it was not the generally recommended solution to this issue.  Do you know if whatever the problem(s) was has been fixed?

---

### Post by frodon on 2008-05-09
This is part of the legend too, really few users have reported this, any software contains bug but for laptop_mode we are many to use it and really few users have had problems with laptop_mode and i'm not even sure this was proven to be related to laptop_mode.

See the full list of reported laptop_mode bugs since it is in ubuntu :
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/](https://bugs.launchpad.net/ubuntu/+source/laptop-mode-tools/)
[https://bugs.launchpad.net/ubuntu/+source/laptop-mode/](https://bugs.launchpad.net/ubuntu/+source/laptop-mode/)
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-laptop-mode/](https://bugs.launchpad.net/ubuntu/+source/ubuntu-laptop-mode/)

It says it all :)

---

### Post by Keyper7 on 2008-05-09
Geez, I was happy that the original fix works on my Gutsy machine, only to find out now that it does not work anymore in Hardy...

I'm a little bit confused now... In Hardy, which would be a proper, clean fix?

---

### Post by AbtZ on 2008-05-09
> **Keyper7 said:**
> I'm a little bit confused now... In Hardy, which would be a proper, clean fix?

jakon's fix worked fine for me: [http://ubuntuforums.org/showpost.php?p=4897802&postcount=842t](http://ubuntuforums.org/showpost.php?p=4897802&postcount=842t)

> **frodon said:**
> Basing arguments on a single experience is what killed this thread and still continues to kill it, it makes it difficult or nearly impossible to extract real information in the middle of a lot of misinformation and this is preventing unfortunately some of those willing to help to help.
So, because my experience wth my two laptops differs from what you say is the general consensus here in this thread, it means it is misinformation?

I will agree that stating that Ubuntu "kills hard drives" is unnecessary hyperbole, and I apologize for that.

But how does mucking about with laptop_mode fix this? If people have head parking problems with laptop_mode turned OFF, how will it help them if they turn it on? I'm not saying you're wrong, I'm just curious.

But nevermind, I'm happy now that my own disk now works fine, without crazy Load_Cycle_Counts. I will leave the solution to this problem to people more tech savvy than I. All in a great effort to avoid spreading more misinformation. :)

---

### Post by ctt1wbw on 2008-05-09
So I guess this is a kernel issue, not just a distro specific issue?  I want Fedora or Ubuntu or something, but last time I had Ubuntu on my laptop, I erased it and put Windows back on it because the hard drive parking issue and the related sonic booms it made drove me out of my fsking mind.

---

### Post by frodon on 2008-05-09
> **AbtZ said:**
> jakon's fix worked fine for me: [http://ubuntuforums.org/showpost.php?p=4897802&postcount=842t](http://ubuntuforums.org/showpost.php?p=4897802&postcount=842t)
But how does mucking about with laptop_mode fix this? If people have head parking problems with laptop_mode turned OFF, how will it help them if they turn it on? I'm not saying you're wrong, I'm just curious.It's where the misinformation succeed unfortunately as it is the exact laptop_mode purpose to control accurately your drive, and it's surely surely the best way to fix this head parking issue.

How ?

Configuring thoroughly the following parameters in laptop_mode.conf :
```
LM_AC_HD_IDLE_TIMEOUT_SECONDS     #number of seconds of inactivity before head parking on battery
LM_BATT_HD_IDLE_TIMEOUT_SECONDS   #number of seconds of inactivity before head parking when not on battery (laptop_mode active)
NOLM_HD_IDLE_TIMEOUT_SECONDS      #number of seconds of inactivity before head parking when not on battery (laptop_mode inactive)
CONTROL_HD_POWERMGMT              # allow laptop mode to control power management (hdparm -B parameter)
BATT_HD_POWERMGMT                 # hdparm -B value to use while on battery
LM_AC_HD_POWERMGMT                # hdparm -B value to use while not on battery (laptop_mode active)
NOLM_AC_HD_POWERMGMT              # hdparm -B value to use while not on battery (laptop_mode inactive)
```

---

### Post by Keyper7 on 2008-05-09
> **AbtZ said:**
> jakon's fix worked fine for me: [http://ubuntuforums.org/showpost.php?p=4897802&postcount=842t](http://ubuntuforums.org/showpost.php?p=4897802&postcount=842t)

Yeah, but it's still quite "hackish". I was more wondering if enabling laptop-mode and configuring it properly was enough for all cases (suspend, etc.). Did anyone test this already? I'm about to.

EDIT: heh, frodon beat me to it. :)

---

### Post by blackhole54 on 2008-05-09
> **frodon said:**
> This is part of the legend too, ...

Hmmm.  Of the bugs reported from your supplied links, [this](https://bugs.launchpad.net/ubuntu/+source/ubuntu-laptop-mode/+bug/127219[/url) seems to be the only one that sounds anything like a computer "hanging."  But I see no indication from the descriptions that it has anything to do with laptop-mode. So I searched to find out [where I was told](http://ubuntuforums.org/showpost.php?p=3847126&postcount=509) that this was a problem.  The poster referred to [this *launchpad* post](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224).

After initially being disuaded by this (and the fact that my drive had an advanced *Load_Cycle_Count* and I hadn't gotten my head around this yet), I decided to experiment with it a couple months ago.  As I have reported earlier it seems to be giving borderline acceptable results, with *Load_Cycle_Count* advancing 10 to 50 per hour when on battery (I have disk APM disabled on AC).  The high end of that range seems to be when I am browsing (using Seamonkey).

The comments in *laptop-mode.conf* seem pretty thorough, and adequate for users used to working at that level.  But for less advanced users, the documentation you have spurred might be needed.  Good luck on that. Since logging activity (particularly NetworkManager) can be rather heavy, I suggest people modify the logging behavior as described in *laptop-mode.conf*.  It is straightfoward, but one does need to read carefully and pay attention to detail.  And probably consult the syslog.conf *man page*.

Thanks for providing the links.  :)

EDIT: When I called behavior of *laptop-mode* on battery only *marginally* acceptable I was referring to the upper end of 50/hour.  But since (under my configuration) this can happen only on battery I don't think it is a real issue.  At least until my *Load_Cycle_Count* gets more advanced.

---

### Post by AbtZ on 2008-05-11
So basically I should enable laptop mode? Cool.

I'm not one of the advanced users. What are sensible values to assign to the relevant parts of the config file?

---

### Post by jakon on 2008-05-11
Yes, if you want different HD power management settings depending on the battery/AC state, you need laptop-mode.
I would recommend to not mess with settings you don't have any problems with. For me, HD standby for example never was a problem.
Just set these, they are kind of sensible: [http://ubuntuforums.org/showpost.php?p=4904541&postcount=848](http://ubuntuforums.org/showpost.php?p=4904541&postcount=848)

When i tried laptop-mode for HD PM in Gutsy, however, the settings were lost on suspend/resume. Is this fixed in Hardy?

---

### Post by blackhole54 on 2008-05-12
> **AbtZ said:**
> What are sensible values to assign to the relevant parts of the config file?

The values *jakon* linked to are the basics.  I would suggest after setting up *laptop-mode* you check what happens to *Load_Cycle_Count* when you are on battery to make sure it is not going wild; when you know you are going to be using your computer for an hour or two on battery, run **smartctl** before and after.  I see increases in the range of 10 to 50 per hour depending upon what I am doing.

---

### Post by art_s on 2008-05-12
Hi all,

I was just thinking that solution with drive power management settings is not always the right one. 
Basically, one cannot rely on the fact that power is plugged in - as an example you might be in a moving vehicle with laptop connected via adapter to a cigarette lighter power outlet.

I think my question is how to reduce unnecessary disk activity?
I'm new to ubuntu so my questions are quite generic - is it possible to reduce swap size to make os use more RAM instead?

Or just any other tricks which might help?

Thanks!

---

### Post by blackhole54 on 2008-05-14
> **art_s said:**
> Hi all,
... is it possible to reduce swap size to make os use more RAM instead?

If you're wanting to tweak that sort of thing, you  are probably better off changing [swappiness](http://kerneltrap.org/node/3000).  I rather doubt, however, that this is going to change much wrt the issue at hand.  On a system with 512 MB RAM running *edgy*, I observe the amount swapped out tends to be 17 MB or less (frequently 0).  My impression is once it gets swapped out it just sits there, seldom, if ever, to be swapped back in.  You can investigate the amount of swapping on your system with the [**vmstat**](http://man.linuxquestions.org/?query=vmstat&section=0&type=2) command.

---

### Post by art_s on 2008-05-14
> **blackhole54 said:**
> If you're wanting to tweak that sort of thing, you  are probably better off changing [swappiness](http://kerneltrap.org/node/3000).  

...


Thanks for your reply, I think I was looking for this sort of article:

[https://wiki.ubuntu.com/ReducedPowerUsage](https://wiki.ubuntu.com/ReducedPowerUsage)

---

### Post by ubuntu_demon on 2008-05-15
IMHO laptop_mode is not "THE" solution because it causes hangs on some machines.

I updated the first post of this thread with the following information :

**Unofficial Ugly Fix you can try on your own risk for Hardy **
[http://en.opensuse.org/Disk_Power_Management](http://en.opensuse.org/Disk_Power_Management)

The temperature of the disk seems a little bit higher for me in Hardy.

I'm experimenting with these values but you might need different values :
```

DEVICES_DISK_PM_POWERSAVE_OFF="hdparm -q -B 254 -q -S 0"
DEVICES_DISK_PM_POWERSAVE_ON="hdparm -q -B 128 -q -S 0"

```

**Idea #288: Fix Hard Drive Load Cycle Problem in Laptops**
* [http://brainstorm.ubuntu.com/idea/288/](http://brainstorm.ubuntu.com/idea/288/)

---

### Post by frodon on 2008-05-15
This "hang issue" sounds really marginal for me, on the french wiki the laptop mode well configured has been documented as the fix for this issue almost since the beginning which means that most french users searching documentation on this issue use laptop mode and till now there were no recurring "hang issue" problem reported.
I'm not even sure if this is still an existing issue with current laptop_mode version.

Anyway it's good to have the choice, the best for a long term solution would be something like laptop_mode installed and configured with safe values by default. Hope this goal will be reached soon.

---

### Post by ubuntu_demon on 2008-05-15
> **frodon said:**
> This "hang issue" sounds really marginal for me, on the french wiki the laptop mode well configured has been documented as the fix for this issue almost since the beginning which means that most french users searching documentation on this issue use laptop mode and till now there were no recurring "hang issue" problem reported.
I'm not even sure if this is still an existing issue with current laptop_mode version.

Anyway it's good to have the choice, the best for a long term solution would be something like laptop_mode installed and configured with safe values by default. Hope this goal will be reached soon.

It may be a marginal problem but it's the reason Debian put a workaround in acpi-support instead of laptop-mode-tools.

Initially I also thought using laptop-mode would be the best solution :

[quote=ubuntu_demon]
* maybe Ubuntu Hardy should enable laptop-mode by default while running on battery with sane defaults 
[/quote]

The author of laptop-mode-tools and maintainer of acpi-support Bart Samwell participates in the launchpad bug and answered me :

[quote=Bart Samwell]
Not this one. It was disabled for a good reason -- system hangs. Nobody
ever found the real reason, but this is a very real problem. :-/
[/quote]

This was from : [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/224)

Bart Samwell decided to put Debian's workaround in acpi-support instead of in laptop-mode-tools (using apm 254 while not on battery and apm 128 while on battery).

From [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/502](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/502) about this laptop-mode-tools bug :

[quote=Bart Samwell]
These were hard system hangs on Thinkpads. :-(
[/quote]

Using laptop-mode can be a good solution for a lot of people but can cause problems for some people so that's why I decided to recommend people to "fix" it by adding the ugly fix script to /etc/acpi/... a bit similar as Bart Samwell does in Debian see : 
https://launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/229

It's useful to read more of Bart Samwell's comments in the bug report since it takes less time than reading all the comments in the bug report and he has some good contributions.

---

### Post by frodon on 2008-05-15
Sure i did not know Bart Samwell confirmed this but this don't change the fact that most users don't have this issue.

It's the same for hardy kernel lockups, some are having real nightmares with hardy kernel but for most users hardy just work.

---

### Post by ubuntu_demon on 2008-05-15
> **frodon said:**
> Sure i did not know Bart Samwell confirmed this but this don't change the fact that most users don't have this issue.


The laptop mode fix has the benefit of being a bit smart and delaying I/O a bit when the disk is idle.

Everybody who has used laptop mode to fix this doesn't need to worry because they have a working fix. 

I like to recommend the fix which has the least chance of causing people problems. If I can prevent some hangs for some people even it's just a couple people I'll do that.

> **frodon said:**
> 
It's the same for hardy kernel lockups, some are having real nightmares with hardy kernel but for most users hardy just work.

I didn't read about that yet.

---

### Post by frodon on 2008-05-15
Hopefully the laptop_mode hang source will be found or equivalent of laptop_mode available, it's really a pity that there's no 100% supported tool to configure exactly how and when head park. We really need this, to solve this issue and to be more efficient with power saving.

---

### Post by v.stiff on 2008-05-19
Thanks Ubuntu! I've just bought brand new HDD after a year of usage of the previous one.

I wonder, why laptop manufacturers aren't selling their computers exclusively with ubuntu? upgrade once a year, it's a perfect!

It would be more fair to place a sign on ubuntu.com main page:
IF YOU ARE GOING TO USE IT ON A LAPTOP - INSTALL A [FIX]("https://wiki.ubuntu.com/DanielHahler/Bug59695") FIRST, OR YOUR HARD DRIVE WILL DIE SOON.

---

### Post by frodon on 2008-05-19
No need to be that nervous :)  take the time to browse this thread and you will see that it can impact any OS.

---

### Post by v.stiff on 2008-05-19
> **frodon said:**
> No need to be that nervous :)  take the time to browse this thread and you will see that it can impact any OS.

The first edition was muuuuuch more lovely. It is _the right_ approach to dealing with bug reports. "You bought new hdd? lol. go stay with windows. ahahaa"

---

### Post by Arthur Archnix on 2008-05-19
UDemon, I've followed the suse method and it works good. Except when resuming from suspend. Then it goes to 128. If I unplug or plug back in, it adopts the appropriate setting.

I'm looking for a way to work around this now, and I think maybe copying the disk script located in /etc/pm/power.d to /etc/default ... except that doesn't work.

What are your thoughts?

---

### Post by dodecaman on 2008-05-19
I want to say thanks to Ubuntu-Demon and all of you who have tried to find a solution for this issue.

I bought a new Dell in January - erased it and loaded Gutsy before I even booted Windows.  After about a week of listening to the weird click, I kicked off a google search and got dogpiled with FUD.  I love ubuntu, but I'm not a real command line commando, so I gave in and switched back to Windows (the clicking continued, btw).  After three months I'd had enough.  Hardy was out, and I figured I'd make it work.  I applied the fix outlined at SuSE's site (thanks for the link) and haven't had any more problems.  I installed hddtemp and a little Gnome applet to keep an eye on things.

Bottom line ... I don't think an operating system should override firmware straight out of the box (or iso, as the case may be).  But I wish it were an option.  The reason I choose to use Ubuntu is that I can tweak it to fit my needs.  If there's a way to program an interface into the next release, that would be wonderful, but if there isn't I'll ugly fix it myself.  It's worth it.

Thanks for the guidance, guys!

:KS

---

### Post by ctt1wbw on 2008-05-20
I just read the last few pages but didn't find the Suse link you're referring to.  Care to post a link?  I'm still getting the problem on my laptop and it's driving me insane right now.

---

### Post by Dynaflow on 2008-05-20
> **ctt1wbw said:**
> I just read the last few pages but didn't find the Suse link you're referring to.  Care to post a link?  I'm still getting the problem on my laptop and it's driving me insane right now.

[http://en.opensuse.org/Disk_Power_Management]("http://en.opensuse.org/Disk_Power_Management")

from

[http://ubuntuforums.org/showpost.php?p=4965173&postcount=873]("http://ubuntuforums.org/showpost.php?p=4965173&postcount=873")

---

### Post by caraboy on 2008-05-21
I am using the suse script right now. Well, from 39C hdd temp now  have 44C. Damn... I`ll try to enable laptop mode, maybe it will just work on my HP. :)

Later edit: what do you say about this guide: [http://siryes.blogspot.com/2008/05/high-frequency-disk-load-cycles-ubuntu.html](http://siryes.blogspot.com/2008/05/high-frequency-disk-load-cycles-ubuntu.html) It configures laptop-mode. I will try and test it and get back to you soon.

---

### Post by napalm brain on 2008-05-21
Does anyone know if something official will be done?

This entire issue is extremely troubling. I'm cycling around 193 times an hour. So much for running my laptop all the top. Turns out I will be shutting it down more often than not.

Just a small inquiry: if I were to revert back to an older version of Ubuntu, would this issue persist?

---

### Post by BandD on 2008-05-21
I know all these posts are pretty overwhelming, but the problem isn't with Ubuntu or Linux, rather it seems to be a problem with the harddrive manufacturer's firmware.  It's had for Ubuntu or Linux to do anything "official" because it is impossible to predict with harddrives are going to have these issues.  

If someone's drive doesn't have this issue then it's best to leave things the default way.  

The fixes proposed in this thread are really quite safe and generally pretty easy to undo.  And if Ubuntu or Linux was to do some sort of "official" fix, they would be doing something similar to this in all likely hood.

If you have specific questions, there are many people who follow this thread who would be more than willing to walk you through it.

---

### Post by napalm brain on 2008-05-21
Well, to be specific, the rate does not seem to be slowing down. I've tried writing a few of "ugly" scripts in order for the system to quit cycling.. which does not seem like it has done much. 

Like I said, I love Ubuntu. I've used it since December and haven't had any issues. This all seems so random.

---

### Post by plamen_todoroff on 2008-05-22
I found this very recent thread by nicedude in "hardware and laptops" section: [http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327) and it seems to be adressing the same issue as the current thread (which, i don't understand why, is in the archives).

There are some differences between the current thread and the new one, and I don't know which one to follow. The part that bothers me most is the locations to where to copy the script. In the current thread ubuntu_demon says that the script is to be copied in:

$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/resume.d/
$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/start.d/
[B]$sudo install 99-hdd-ugly-fix.sh  /etc/acpi/ac.d/
$sudo install 99-hdd-ugly-fix.sh /etc/acpi/battery.d/[/B]

but in the newer thread nicedude says it is to be copied here:

**sudo cp ~/Desktop/99-sda-load-count-fix.sh /etc/acpi**
sudo cp ~/Desktop/99-sda-load-count-fix.sh /etc/acpi/start.d
**sudo cp ~/Desktop/99-sda-load-count-fix.sh /etc/acpi/suspend.d**
sudo cp ~/Desktop/99-sda-load-count-fix.sh /etc/acpi/resume.d

(I've highlighted the differences)

???

And it gets even more complicated as I stumbled upon this post by the very same ubuntu_demon: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/232](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/232) , in which the locations vary again.

And one more question. The newer thread by nicedude says that the fix works in hardy. Why then ubuntu_demon suggest some suse-fix for hardy? Shouldn't the original ugly fix by ubuntu_demon be used in hardy?

Please, if someone can clear things up, because my load cycle count issue is closing to 20000 and it's month old laptop, i'd like to stop cycling before it hits 20000.

---

### Post by BandD on 2008-05-22
> **napalm brain said:**
> Well, to be specific, the rate does not seem to be slowing down. I've tried writing a few of "ugly" scripts in order for the system to quit cycling.. which does not seem like it has done much. 

Like I said, I love Ubuntu. I've used it since December and haven't had any issues. This all seems so random.


Which one's have you tried?  Things have gotten a little complicated because Hardy uses some different scripts for controlling HD power management.  

Also it is possible that your drive will not respond to a change in the HDPARM values.  If this is a the case, then there isn't a whole lot you can do.  You could try disabling the journalling aspect of the ext3 filesystem--some have had moderate success with that.  But it isn't recommended.

First thing to try is:

```
sudo hdparm -B 254 /dev/sda
```

If that doesn't stop it try a value of 255 instead.

If neither work, then there isn't really much you can do.  Call up the hard drive manufacturer and ask them if they have a fix for their power management firmware.

---

### Post by BandD on 2008-05-22
TO plamen_todoroff:

For the mean time you can change the hdparm value manually by entering the following code in a terminal:

```
sudo hdparm -B 254 /dev/sda
```

If 254 doens't work, then you can try a value of 255.

---

### Post by blackhole54 on 2008-05-23
@napalm brain

Try the **hdparm** commands that *BandD* suggests in the above posts.  Use a terminal to set it to 255 and use your computer for a while, using **smartct** before and after to monitor how fast the value increases.  If 255 doesn't slow it, try 254.  If neither one of these values slows the increase to a reasonable value, then no variation on the "ugly fix" will help you.  If one of these values does slow the increase, then if you want to try some variation of the "ugly fix," it is just a matter of finding the right places to put the script for your version Ubuntu.

If neither value helps you, your only options (that I know of) are to use *laptop-mode* as previously discussed on this thread or find a way to alter the settings on your hard drive specific to your HDD manufacturer.  If you decide to try *laptop-mode* it would be prudent to make sure you have a live CD on hand (the standard Ubuntu installation disk would work fine) to revert your configuration in case your's is one of the (apparently rare) computers that "hangs" with *laptop-mode*.

If none of this helps you out, you might try using the *search this thread* link (right above the top post on this page) and enter the name of the manufacturer of your drive to see if anybody has given vendor specific info that might be useful to you.

@plamen_todoroff

I hope the people who have posted conflicting info can clear things up for you.  But with *Load_Cycle_Count* at (only) 20,000 you don't need to panic quite yet.  If its any consolation, I didn't even find out about this issue until my value was over 600,000 (U.S. usage of comma -- so your eyeballs don't go cross-eyed!).

---

### Post by nicedude on 2008-05-23
I started a thread on this issue about 1 week ago since I didn't see this one and had no idea it existed and after seeing someone question this activity at first I thought he was wrong and there was no way anything like this could be affecting my system without having been warned by a sticky. To my surprise after I checked my system I figured out my drive was cycling over 120 cycles per hour and was potentially being silently destroyed, It made me both worried and angry. So after some off site reading of articles on this I made a thread on it with one goal, to warn others and try to help the best I could so they too could avoid the danger if they were affected. 

I had no intention of thread jacking Ubuntu Demon and I apologize for not searching more thoroughly here for his thread. In the last week I have answered 100+ PM's on this for users and spent 15+ hours trying to help others ( as I have one on one helped anyone with problems regarding my fix ). I don't mind this though and I actually enjoy helping others. But in general my thread has at times been a bit overwhelming and it has evolved as well since as I have gotten better test commands and was made aware of better locations for the script than I had previously recommended I made adjustments to my instructions as needed ( I now recommend the locations recommended here ). I would appreciate anyone here who has been helping with this issue to please look over mine and see if the advice and test procedure I am giving are as sound as I think they are. So I can at least know that anyone who is using my thread wont be getting bad advice, I think it now is as good as is available but I would like an expert opinion if possible to be sure. Also below I would like to share the test command a user sent to me that both gives the load cycle count and temp at once and gives a lifetime known temperatures range reading as I thought Ubuntu Demon might appreciate this command as well since it gives all the relevant info in one command.

My thread
[http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327)

Test command I now recommend and use myself.
date; sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'

Sample output of test command above on my machine.
193 Load_Cycle_Count        0x0012   083   083   000    Old_age   Always       -       171247
194 Temperature_Celsius     0x0002   141   141   000    Old_age   Always       -       39 (Lifetime Min/Max 11/54)


So if any Ubuntu gurus could make sure I am not steering anyone wrong I would greatly appreciate it. And Ubuntu Demon I once again apologize for starting a copycat thread of yours I did not find this before and my only intent was to help others to keep their equipment safe and functioning for as long as possible. I am also aware of this being a hardware problem & the laptop-mode configuration file fixes but am unsure about how well a fix of that nature would work since I have seen that it might not work for all machines affected and I was trying to give a fix that will work for all laptops with Ubuntu. Also I have been using the -B 200 value for my fix script and can report that only 5-6 people have had that value not work and out of those not one person yet that the 254 or 255 values did not work for to stop the negative activity. Also no one has yet to report a dangerous temp as a result of the hdparm command fix that has contacted me, most are reporting 0-3 C increases which is trivial in my opinion. 

Thanks to all who have been preaching this longer than me and thank you Ubuntu Demon for helping people long before I.

nicedude

---

### Post by blackhole54 on 2008-05-24
@nicedude

Thanks for taking the time to try to help others with this problem.  I read your first post on that other thread but not the entire thread.  So if this is already covered elsewhere in that thread, I appologize.

The only thing that really jumped out at me when I read your post has to do with passing a value of 255 for the **-B** option in **hdparm**.  As discussed elsewhere on this thread and on *launchpad*, the **hdparm** command handles 255 differently than all other values.  I.e. it sends a different command to the drive.  As a result, there are (IIRC) some drives for which a value of 254 will work but a value of 255 will not.  That said, there is a possibility on some or all drives that 254 will do the same thing as 200.  This is the first time I have heard of somebody using 200.

---

### Post by ubuntu_demon on 2008-05-24
We, forum staff, have decided to close this thread because it contains a lot of misinformation and confusion. 

[B]This thread continues here :
[http://ubuntuforums.org/showthread.php?p=5030999](http://ubuntuforums.org/showthread.php?p=5030999)[/B]

---

