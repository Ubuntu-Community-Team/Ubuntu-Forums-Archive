---
title: "INCREDIBLY bad performance of new machine with gutsy"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by pete.dawgg on 2007-11-09
i'm a first time ubuntu-user and installed gutsy (alternate cd) on a friend's  brand-new laptop which should be really powerful (core2duo, 2gb ram, ...). after some hardware-trouble (ati is cheap S**T) i got it running (kinda), but the performance really sucks big time.
i started one cpu-intensive program (k9copy, dvd-requantizing) and the rest of the computer turned unusuable in a really bad way: the mouse lagged way behind, terminals took 30secs to open, task-switching/focuschange with alt-tab or mouseclick took 10+ sec, ...
compiz and desktop-effects is completely turned off (thx ati :( ) and really nothing else ran.

same thing happened when running vobcopy on tty2, of course things get slow under heavy io on the same disk, but this was way to bad; and that did not change after running hdparm/sdparm.

i checked the procs and saw that only ONE cpu is used, but with apt  smp-kernels only for older processors are available :confused:

i noticed that about 2000 modules for hardware not even there are loaded and running processes - what for? :confused:

i wanted to check the kernel-config for smp, proctype, ticks, schedulers, ... no /proc/config.gz and no source matching the running kernel-version - where can i get that? or a kernel that fits this machine? i could tolerate all the useless modules, but using BOTH processors is a must.
is there something that must be appended in grub?

i was very disappointed, because when i do the same thing on an old p4 with wannabe-SMP (ht) and only one quarter of the ram, i can run k9copy and work on the desktop (ffox, tbird, ...) without  noticing too much of it, and the requant is finished after about 30-40 mins (but that's a different distro)
(the process yesterday was killed after about 45 having produced no noticeable results except cpu-hogging)

pls help me get a kernel that uses the feature the machine offers - maybe the reason is the alternate install (only for generic, very old computers?)

(also, i told my friend "you get somthing really good and nice, much better than vista,", and he, computer-indifferent windoze-user said, "cool, if it works and i can use it,  great."  :)  )

---

### Post by Vadi on 2007-11-09
Did you install the 64bit version of Ubuntu there or 32bit?

---

### Post by pete.dawgg on 2007-11-13
sorry 4 the late answer - i was away for the weekend.

i picked 32bit because of driver compat. afaik this is completely unrelated to the number of processors your kernel supports (CONFIG_SMP and related). i have a (similar, but much weaker) thinkpad that runs in 32bit with 2 processors just fine and much faster and smoother (but different distro).

do you happen to know where i can get the kernel-config for the running kernel?

thx for your help.

---

### Post by mcduck on 2007-11-13
If you are even able to see 2 processors listen anywhere, you have a working support for SMP. And this has been enabled by default in all Ubuntu kernels since 6.06, so there's no more different kernels for different CPUs any more.

If the programs you use are only coded to run in single thread, they cannot use more than one CPU/core. Nothing you do to your system can change that, no matter what OS you run.

I suppose the performance problems are caused by something else than the kernel. You could check if any program is using insanely much resources. Go to System/Administration/System Monitor and check the Processes-tab.

Also if swap isn't working correctly it an cause problems, run 'free -m' to check your memory & swap usage, and to confirm that some swap space is recognized. Even when you have enough RAM to never actually need to swap, some things may not work correctly if no swap is present.

Also, have you installed correct drivers for the graphics card? Missing them can often cause some lag on desktop interface.. Go to System/Administration/Restricted Drivers Manager.

---

### Post by dabl on 2007-11-13
It sounds like X server configuration (aka video driver) is probably the real culprit -- that is the "visible" performance.  The Linux underneath is probably running along full speed ahead.

Check your running version with the console command ```
uname -a
```

Check your running processes for resource hogs with the console command ```
top
```

Probably you will see xorg.conf at the top of the list most of the time -- it should not be using more than a few percentage points of your resources.

I personally would have gone with the 64-bit version, but that is somewhat a matter of taste -- it certainly won't make much difference in visible performance.

I'd recommend you attack it from the video driver angle first -- what is the video chip and what is the recommended driver?  If in doubt, and you want to see an immediate performance improvement (but no eye-candy), configure a VESA display using the script.  Since you say it is some kind of ATI chip, go download the Envy script installer and, once it is installed, run it to install a good ATI driver for whatever chip it is.  Get Envy here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


Configure a VESA display with this script:

```
sudo dpkg-reconfigure xserver-xorg
```

HTH!  :)

---

### Post by pete.dawgg on 2007-11-13
THX for all ur help!! :)

(i'm not at the machine right now but i'm burning to get that issue solved)

XORG/VGA: i'm certain i have the right video-drivers installed (radeon express sth.) because w/out these there would be no X or gnome, had to do the alternate install due to bad vga-chip and uncommon display.
the latest (from apt) version of the fglrx-drivers is installed and loaded by xorg; i'd rather not test witrh VESA because  i couldn't get that to run at all when i reconfigured xorg the first time (bad chip/display: "no screens...")

could things get better if i explicitly set the chip's memory in xorg.onf (it uses shared memory from ram)?

if i don't run anything at all (no visible gui-app ;) ) xorg is at the top of top but the system is 99%+ idle

i know about multi-threaded apps etc, but when i look at /proc/cpuinfo i should at least see cpu0 and cpu1 - which i clearly DON'T SEE.
```
uname -a 
```does NOT tell me anything about SMP - which it should. (on my other boxes it's sth like (...) SMP PREEPMT)


there's another problem: the network-if does not start automagically. (accidentally posted iot as hardware problem elsewhere - i'm gonna delete it) when the box is switched on the if is there, but has no ip-address, even though all the values are set correctly by the network manager (manual config). opening and closing it does not change a thing. i only get an adress and route bey setting it manually with the command-line. the only thing that's persistent is the dns-server, it does not have to be re-added  manually.
what's going on there?

---

### Post by dabl on 2007-11-13
> **pete.dawgg said:**
> 

```
uname -a 
```does NOT tell me anything about SMP - which it should. (on my other boxes it's sth like (...) SMP PREEPMT)



OK, that's not right -- you should indeed see that it is a SMP kernel.  So there's a problem.

> 

there's another problem: the network-if does not start automagically. (accidentally posted iot as hardware problem elsewhere - i'm gonna delete it) when the box is switched on the if is there, but has no ip-address, even though all the values are set correctly by the network manager (manual config). opening and closing it does not change a thing. i only get an adress and route bey setting it manually with the command-line. the only thing that's persistent is the dns-server, it does not have to be re-added  manually.
what's going on there?

Hmmmmm -- some of that doesn't sound right either, and it's not obvious what is wrong, because network configuration normally happens during installation, if the network connection is active.

:confused:

Not knowing any more than this, I think I'd be downloading my Alternate Install 64-bit ISO image, and getting ready to give it another shot.  :lolflag:

---

### Post by pete.dawgg on 2007-11-14
SOLVED (most of) IT :)

(btw: reinstallation because of such minor misconfigurations is absolutely out of any question for me. is there an M$-tag hidden somewhere that i didn't catch? ;) )

1. KERNEL/SMP: i had installed a ....-386-kernel alongside the ...-generic-kernel. i guess that happened when i tried to install the kernel-sources with apt (i'm not so apt with apt yet, i guess). without any question or comment grub was configured to boot the 386 non-smp-kernel.
so that is fixed (commented out), and i also removed [COLOR="RoyalBlue"]quiet[/COLOR] and [COLOR="RoyalBlue"]splash[/COLOR] from grub.conf (menu.lst), because it screwed up the console anyway aand i like to see what happens during boot.
i also added [COLOR="RoyalBlue"]all-generic-ide[/COLOR] because of the "intel" marvell-pata-chip.

2. no NETWORK after boot: called the iniscript by hand and it told what it was missing (dir and pidfile in /var/run) created/touched it by hand - now it works. (i still miss the status and zap-options to the initscripts, though)

3. k9copy's bad performance may have been due to bad/scratched dvds. i'm copying one now and will test the requant later with fioes on the hd.

tonite my friend's gonna get his machine and he'll be happy i saved him from vista ;)

thx again for all ur help!

---

