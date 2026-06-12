---
title: "Ubuntustudio 9.04 hangs"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by wlodarek1 on 2009-05-04
[LEFT]When launching a new freshly installed ubuntustudio works well.
[LEFT]When you configure the Internet connection and want to install software completely hangs system .[LEFT]I can only do a hard reset the computer.
[LEFT]I would like to use 64-bit ubuntustudio better because I think as always likes ubuntu.
[LEFT]Ask for help, why 64-bit ubuntustudio 9.04 hangs so often I can not use it?:([/LEFT]
[/LEFT]
[/LEFT]
[/LEFT]
[/LEFT]

---

### Post by hlaford on 2009-05-18
i may be having the same issue. with a fresh install of studio 9.04 32-bit (and 64-bit), my system will freeze a few minutes after logging in. (i have not checked to see if it hangs without logging in.)

it appears to freeze no matter what i'm doing at the time. i thought it was the update manager until it froze while i was researching the problem.

has anyone found and fixed a hanging problem on a fresh install before?

---

### Post by subdancer on 2009-05-27
im having the exact same problem. the system hangs after a couple minutes. 
i guess it hast something to do with the network driver or rtkernel.. something like that, cause if i do an update it starts downloading but only a couple percent then freeze completly. so it doesnt even let me update..

i tried 32 bit and 64 bit versions.. makes no difference

the bug is reproduceable on all my systems.
the mainboards i tried is an socket 939 Asus A8N-SLI Deluxe with nforce4 chipset (Athlon X2 4800) and and socket AM2 Asus M3A78-T with an amd 790GX chipset(Athlon X2 6000+)

some help or infos would be great. i can also post logs.

---

### Post by Cthulhu_Dreams on 2009-07-11
I'm having this problem too....

---

### Post by Norami on 2009-08-22
So evidently there are a lot of people having this problem with Ubuntu Studio Jaunty, but no one seems to want to help. I've posted a thread with no replies about the issues, and several others have as well with no real answers. I thought these forums were supposed to be some sort of help.

I'm assuming that it would be a lot easier to just install Ubuntu 9.04, and then just install all the packages for the media software through Add/Remove. There's no problems with my hardware, and I have enough resources, so there's no reason why it would freeze and lock-up.

ANY IDEAS ON THE MATTER WOULD BE AWESOME.

---

### Post by profshadoko on 2009-08-24
I have the same problem too with two different machines: a Mac mini and a Dell Studio XPS 435MT (qith a Intel i7 920 quad core). Once the machine hangs, the only way to restart it is to physically turn it off.
This renders Ubuntu Studio completely unusable as far as I'm concerned.

On the Mac Mini the freezes occured pretty randomly, but on the Dell, they seem to occur systematically when I attempt certain operations, like installing ca-certificates-java (for some reason), or like trying to play music with rhythmbox.

On the Mac Mini, I ended up wiping Ubuntu Studio and installing 64Studio 3.0 beta_3 (which worked great).
However, 64Studio won't install on the Dell (64Studio boot image has no drivers for the Sata DVD and HD in the Dell), hence a fix for Ubuntu Studio hangs would be much appreciated.

I'm guessing it has something to do with the rt kernel.

Has anyone tried to install plain vanilla Ubuntu, and then install the rt kernel and the music apps manually?
Do you experience the same problem?

---

### Post by abelbrito on 2009-10-20
ok, so if the "solution" would be to install the Ubuntu Studio packages on Ubuntu 9.04 Jaunty (standard), then what's the point of having an Ubuntu Studio release? wouldn't that make it a bit redundant?

---

### Post by abelbrito on 2009-10-20
so....after several failed attempts with Ubuntu Studio i decided to go back to standard jaunty...i'll just get the studio packages on that... sigh..

hopefully the karmic release will be more stable..

---

