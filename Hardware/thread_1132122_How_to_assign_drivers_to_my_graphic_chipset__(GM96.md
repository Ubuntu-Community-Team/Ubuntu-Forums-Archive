---
title: "How to assign drivers to my graphic chipset ? (GM965/GL960)"
date: 2009-04-21
forum: Hardware
---

### Post by Guillaumeb on 2009-04-21
hello,

I have a Dell Vostro 1510 with the GM965/GL960 Integrated graphic controller.

I have installed Ubuntu 9.04

As I wanted to activate desktop effects I got the error message telling they "could not be enabled".

Following[ a previous thread]("http://ubuntuforums.org/showthread.php?t=1131978"), it seems that everything should be in place except that the built-in driver are not assigned to the hardware.

Running the command line sudo lshw -C display returns:

*-display:0 UNCLAIMED
description: VGA compatible controller
product: Mobile GM965/GL960 Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 0c
width: 64 bits
clock: 33MHz
capabilities: msi pm bus_master cap_list
configuration: latency=0
*-display:1 UNCLAIMED
description: Display controller
product: Mobile GM965/GL960 Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2.1
bus info: pci@0000:00:02.1
version: 0c
width: 64 bits
clock: 33MHz
capabilities: pm bus_master cap_list
configuration: latency=0

Also in the Hardware Drivers menu I have no video driver listed.

Do you think you can help me here ?

Thank you very much

---

### Post by cariboo on 2009-04-21
Have a look at the [Jaunty Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/904"), under Other Known Issues.

You won't find anything under System-->Administration-->Hardware Drivers, as the intel graphics drivers are open source.

Jim

---

### Post by Guillaumeb on 2009-04-21
Thanks for your reply Cariboo. I did try to revert back to the old version from Intrepid following the tutorial but it did not produce any changes.

---

### Post by Guillaumeb on 2009-04-22
Bump!

---

### Post by Guillaumeb on 2009-04-24
Bump ?

---

### Post by jordan420 on 2009-04-24
hey man. so you have X up and running, your just having problems with compiz? i would suggest updating to the jaunty intel-xorg package. and enabling UXA accelerating in your xorg.conf. i've been on UXA for the past three days and its faster. the only problem is it tends to lag at times and consume CPU. if anyone else has info please post.

---

### Post by Guillaumeb on 2009-04-25
Well the thing is, the system driver does not seem to be assigned to my chipset. i'm wondering if

- it's serious

- it's specific to 9.04,if so i would downgrade to 8.10 or 8.04

> its faster. the only problem is it tends to lag at times and consume CPU

>>not sure I understood well here :)

---

### Post by jordan420 on 2009-04-26
well if you have X running you must have some driver enabled. try running: SKIP_CHECKS=yes compiz --replace

---

### Post by Shwan.c on 2009-04-26
> **jordan420 said:**
> well if you have X running you must have some driver enabled. try running: SKIP_CHECKS=yes compiz --replace

There is a bug in X / driver , Compiz i blacklisted for now  until the fix i released , other updates don't help , 
Please wait and live whitout Compiz maybe a week or so or go back to Jaunty beta!
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/363821](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/363821)
please search before posting

---

### Post by jordan420 on 2009-04-26
i have the same graphics card in  my dell vostro. it works fine but it requires a kernel update. and a few other packages involving X need to be upgraded. Probly the best performance ive gotten out  of this card in linux. However it is pretty bleeding edge stuff so if you dont think you wanna mess with it you probly dont. then again you'll never learn if you dont tinker around a little.

---

### Post by Androv on 2009-04-27
I have the exact same problem. Installed 9.04 on my Dell 1510 yesterday and desktop effects can't be enabled. Compiz lists device as blacklisted.
It all worked 100% on 8.10

Does anyone have a remedy for this please?

- Andrew

---

### Post by jordan420 on 2009-04-29
hey man in case you havent figured it out yet just run ::   SKIP_CHECKS=YES compiz --replace

---

### Post by richdup on 2009-04-29
> **jordan420 said:**
> i have the same graphics card in  my dell vostro. it works fine but it requires a kernel update. and a few other packages involving X need to be upgraded. Probly the best performance ive gotten out  of this card in linux. However it is pretty bleeding edge stuff so if you dont think you wanna mess with it you probly dont. then again you'll never learn if you dont tinker around a little.

Can you give more details on those packages, I have the same graphic card on my dell vostro 1500, and the exact same output as Guillaume with "lshw -C display" (unclaimed). I have upgraded the kernel to 2.6.30 and installed xorg-edgers ppa. I found a way to activate compiz but that's not my goal, I'm trying to get a better framerate for Warcraft. It was working fine on windows, framerate was low but playable on intrepid 8.10, it's just too low to play on jaunty.

---

### Post by jordan420 on 2009-04-29
@ rich: hey guy. check out this site [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html) make sure to read it all. and if you are 64 bit like me (vostro 1400) than make sure to replace the "i386" with amd 64 in the package names and the kernel packages should all be rc3... not rc2. the thread is a little outdated. this is where you will find the newest kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/") it also makes mention of having to update your mtrr ranges before you update. which can be done with a simple echo command:   echo "base=0xc0000000 size=0x10000000 type=write-combining" > /proc/mtrr                       now the mtrr needs to be updated everytime you restart X. lemme know if you need help automating it.

---

### Post by jordan420 on 2009-04-29
o sorry i didnt mean to put a space between amd and 64 it is just _amd64_

---

### Post by richdup on 2009-04-29
Thanks for the reply.

I tried everything in the link you gave me and on this one too [http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+driver](http://ubuntuforums.org/showthread.php?t=1130582&highlight=intel+driver) and apart from a few problematic reboots, nothing seems to change anything. I get the same framerate no matter what, except when I add *Driver "intel"* in my xorg.cong I see a difference, for the worst. I'm lost.

---

### Post by jordan420 on 2009-04-30
are you using WoW as a frame rate indicator or did you try the method with tux racer? WoW might be lagged down by compatibility issues.

---

### Post by densou on 2009-04-30
> **jordan420 said:**
>  it also makes mention of having to update your mtrr ranges before you update.

or:
- do a backup of your xorg.conf 
- run *sudo dpkg-reconfigure -phigh xserver-xorg*
- upgrade the kernel
- now, system should recognize correct MTRR ranges
- replace the generic xorg.conf with your old one

not sure if it works at 100%, anyway :(

---

### Post by richdup on 2009-04-30
I just installed and tried *extreme tux racer* and it seems to be running just fine, extremely well I should say, no graphic problems at all.

@densou: I already updated my kernel, but I'll give it a try when I have more time (I'll revert to 2.6.28 and try your process).

Thanks all for the help, keep it coming if you have more ideas.

---

### Post by jordan420 on 2009-05-01
sweet man. WoW might not play so well with it. wine and video drivers dont play nice. out of curiousity what is your tuxracer FPS?

---

### Post by zevans on 2009-05-01
> **jordan420 said:**
> and the kernel packages should all be rc3... not rc2. the thread is a little outdated. this is where you will find the newest kernel [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc3/")

Careful - RC3 has a known regression over RC2 - might or might not affect you, but if you get weirdness or even more slowness with RC3, try going back to RC2.

---

### Post by richdup on 2009-05-02
@jordan: It varies between 20 and 30 fps.

After all these manipulations I retried using opengl for WoW and it's finally playable, no lower than 10 fps, average of about 16, it goes up in the 40's in an indoor environment with no characters or objects around. But I got some glitches like I can't see the sky (I see it with direct X but lower fps) and my mounts act funny. I think updating the kernel and using the xorg-edgers ppa drivers helped.

The important thing is I can finally play, I'm so addicted.

@zevans: I tried the rc3 packages but could only install half of them and it was indeed causing major issues so I reverted to rc2. I tried it because of the output I got with *lspci -v*

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Dell Device 0228
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at fea00000 ([COLOR="Red"]64-bit[/COLOR], non-prefetchable) [size=1M]
	Memory at e0000000 ([COLOR="Red"]64-bit[/COLOR], prefetchable) [size=256M]
	I/O ports at efe8 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

I guess this is outside of my knowledge. But man do I love using linux. I started using windows again because of work, what a pain.

Anyways, I appreciate the help, sorry I take so long to reply, quite busy.

---

### Post by jordan420 on 2009-05-03
arent we all.. haha. well ive been asking in all the threads that are talking about this. does anyone here have problems with compiling the broadcom wireless drivers that come with these cards o so often? i cant seem to get them to compile i keep getting what i believe is a dependency error.

---

### Post by densou on 2009-05-04
> **jordan420 said:**
> does anyone here have problems with compiling the broadcom wireless drivers that come with these cards o so often? i cant seem to get them to compile i keep getting what i believe is a dependency error.

no .bin/.deb avaiable ?

Someone might create it for you (with checkinstall), ask :)

(I made a mess with build-dep so I can't helpful at all this time) :P

---

