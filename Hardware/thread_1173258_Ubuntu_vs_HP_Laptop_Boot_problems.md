---
title: "Ubuntu vs HP Laptop Boot problems"
date: 2009-05-29
forum: Hardware
---

### Post by zuerston on 2009-05-29
**Hello**
I post this in hopes that someone will figure it out, this bug has been posted in many many forums, including the almost *worthless* HP forums,,also I have read on **this** very forum about this problem in a couple posts,with no solutions seen.

Ok,
my  HP DV6810us (6800 series) laptop will not boot Ubuntu (any version) without tapping keys on the keyboard or being run on the ac  charger!  thats it in a nutshell either **beat the keyboard** or go home and **boot from AC power**. No problems with any versions of Micro$oft .,but** I want Ubuntu!**  other than that all is fine,everytrhing works even Virtual box running XP.

HP DV6810us laptop
AMD Turon X2 64bit 2 gig dual core CPU
2 gig ram
Nvidia GeForce Go 7150M   (tried all drivers)
160 gig HD

Ubuntu 9.04 32 bit  OS  (Johnny Jackalot):)

Any ideas?
HELP!
:p

---

### Post by SunnyRabbiera on 2009-05-29
Did you try to edit the BIOS?

---

### Post by zuerston on 2009-05-29
> **SunnyRabbiera said:**
> Did you try to edit the BIOS?
hello
I have  tried everything I can access,I even upgraded the  bios to .34 and thats the latest for this unit.
very little to access/set in bios settings on this laptop.
running the latest Nvidia drivere too.

---

### Post by Zimmer on 2009-05-29
> **zuerston said:**
> **Hello**
.

Ok,
my  HP DV6810us (6800 series) laptop will not boot Ubuntu (any version) without tapping keys on the keyboard or being run on the ac  charger!  thats it in a nutshell either **beat the keyboard** or go home and **boot from AC power**. No problems with any versions of Micro$oft . other than that all is fine,everytrhing works even Virtual box running XP.

:p
Not sure I fully understand exactly how 'beating the keyboard' allows you to boot Ubuntu :)

Are you dual booting? Is the MBR ok ?

Have you considered using a 3rd party boot manager?

[http://www.multibooters.co.uk/managers.html](http://www.multibooters.co.uk/managers.html)

[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by zuerston on 2009-05-29
> **Zimmer said:**
> Not sure I fully understand exactly how 'beating the keyboard' allows you to boot Ubuntu :)

Are you dual booting? Is the MBR ok ?

Have you considered using a 3rd party boot manager?

[http://www.multibooters.co.uk/managers.html](http://www.multibooters.co.uk/managers.html)

[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You have to continusly tap on a key on the keyboard when booting up on battery ,or it just hangs there,maybe it will finish boot in 15-20 minutes if I dont tap a key. read my first post carefully. OR this is not needed to do if I am running on ac power. I know its strange but thats how it is,, I have seen the same thing posted right   here on this forum somewhere else and no replys
I  just call it "beating the keyboard" because thats what I feel like doing sometimes :p
So I will retract the statement and clarify ..."keek tapping onany key" on keyboard.

NO not dual booting,MBR is fine has nothing to do with MBR ,have to beat the damned keys :evil: ALL the way thru the boot up to make it continue loading the OS.
All other OS tried on here load quickly with zero problems.just Ubuntu is doing this.
**The little** **Ubuntu bootup pic with the little line that progresses to bootup stalls** unless a key  is tapped many times while loading.
I just cant explain it any better.
:popcorn:

---

### Post by zuerston on 2009-05-29
here is a thread with the same problem

[http://ubuntuforums.org/showthread.php?t=1146581&highlight=tap+key+boot](http://ubuntuforums.org/showthread.php?t=1146581&highlight=tap+key+boot)

---

### Post by zuerston on 2009-05-29
I guess I found it but I still  dont know what to do  to  fix it! old buddy Bill I  guess is messing with new computers!


```

```xaaxa@xaaxa-laptop:~$ dmesg | grep MSFT
[    0.000000] ACPI: DSDT 77F5C13A, 880C (r1 NVIDIA    MCP67  6040000 MSFT  3000000)
xaaxa@xaaxa-laptop:~$ 

```

```
My brain is sore,anyone tell me what to do (quick fix) on this? if not I will get it fixed sooner or later!!

Bet its why the HP forums dont help,,they in cahoots with Micro$oft yup,there outta be a law!
](*,)

---

### Post by zuerston on 2009-05-29
All fixed!! it boots like lightening now!!! oohhh happy day :p:p:p:p:p

tnx
zuerston off and clear


[SIZE=1]"click"[/SIZE]

ps: the answer lies in the link above.

:popcorn:

---

