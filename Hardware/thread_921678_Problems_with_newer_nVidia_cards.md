---
title: "Problems with newer nVidia cards"
date: 2008-09-16
forum: Hardware
---

### Post by dboze on 2008-09-16
I've been using an ATI X800 XL for my Ubuntu machine. I have the following problems with their proprietary drivers:

1) no compiz effects with dual monitors
2) random mouse lockups (which according to these forums are related to the ATI proprietary drivers somehow

I've always heard nVidia cards are better for Linux, which isn't hard to believe considering what a headache ATI cards have been.

As a result, I purchased an 8400 GS. As nVidia lists this card as compatible, I figured I should be fine. I could not for the life of me get this card to use nVidia drivers in any capacity. Many users on this forum have expressed similar feelings towards this card. After installing the nVidia drivers (through apt, from nvidia's website, even beta drivers), every time the computer would reboot, then the monitor would idle to off as it detects no video device. I've used 3 monitors, including a CRT.

Figuring it was just the card, I pulled my 9600 GT out of my Windows box. Same problem. I've tested extensively with both of these cards. I've even formatted multiple times. Here's what I've done more or less each time:

1) Install Ubuntu 32-bit edition
2) Allow all third-party repositories
3) apt-get update
4) apt-get upgrade
5) apt-get install build-essential
6) install via apt or nvidia installers
7) fail

Any ideas? The only thing I can think of left to try is update my bios (though I'm not looking forward to this as I have no floppy drive).

Also, sometimes I'll install nvidia-glx-new but the Restricted Drivers Manager shows no available drivers to activate.

I'm at a complete loss of words. (And very frustrated :))

Thanks!
Daniel

---

### Post by phidia on 2008-09-16
This shouldn't be happening and I think if you try ibex (still in alpha) you will find it does detect and set up your 8 & 9 series nvidia cards. 
I have seen many threads on problems with those cards but people often claim to get them working with [envy]("http://albertomilone.com/nvidia_scripts1.html").

Edit: BTW there's a related thread [here]("http://ubuntuforums.org/showthread.php?t=868623&highlight=8400gs"), and the Ubuntu wiki on video card set up [here]("https://help.ubuntu.com/community/Video").

---

### Post by dboze on 2008-09-16
"EnvyNG ERROR: Envy does not recognise your card as compatible[...]"

Manual install of newest drive resulted in the same scenario.

So... I guess I'm forced to "upgrade" to alpha software now. Wonderful.

---

### Post by phidia on 2008-09-16
I do understand that this is frustrating, but if everyone trying to run the recent nvidia cards reported their problems at [launchpad]("https://launchpad.net/ubuntu") I think we might see some action-ok maybe that's naive-I don't know. Related(?) bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/231989").
Your xorg.0.log file will be useful to have if you decide to do that.

I should have mentioned manually installing the latest nvidia driver from [here]("http://www.nvidia.com/object/unix.html"). That  could work for you and is really the best way IMO on pure debian. Check out the Ubuntu specific areas of [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") also.

---

### Post by dboze on 2008-09-16
Sorry for coming off as so sour... The frustration was getting to me, that's all. It has been one of those weeks where I'm sending off an aura of computer-breaking (I usually do the opposite).

Thanks a lot for your help! I really appreciate it.

I've installed about every driver available on the nvidia website. My computer is currently updating to 8.10, so I'll let you know how that goes.

Honestly, my work will buy me a new card, so all I really need to know is what works WELL out of the box.

Your signature says you have a 7-series. Is that card working well for you? No trouble installing? Dual monitors + stability is my primary goal. And eye candy will be nice if I can get that. My price range is ~40 USD.

---

### Post by phidia on 2008-09-16
40USD? that's not a lot IMO but I haven't checked gpus much recently. 
I do play one game that requires some fps ability but nothing like the big gamers.
I have a 7600 in my desktop & a 7150M in a laptop and both work fine for my use-I don't have any problems. I'm using 8.10 x86_64 right now and the nvidia driver (installed through hardware drivers-the ubuntu way) works well.

I don't use dual monitors though on either of these setups. I have seen here that installing the nvidia-settings package-appears to be installed by default in 8.10-is the way to get dual support.

Let the thread know how 8.10 works out for you. I'm hoping it does well.

---

### Post by dboze on 2008-09-16
Thanks for the help! I updated 8.04 - 8.10, updated, restarted, went to the Restricted Drivers Manager, enabled the drivers (8.10's proprietary drive manager is a vast improvement), restarted, and BAM! Everything works great. There's even a thermal sensor for my video card!

The machine isn't for gaming actually, so I don't actually need a fancy card. I just plopped my 9600 in there out of frustration. If only I knew everything I know now... I would have bought a 6xxx or 7xxx card instead of that 8400! But I'll stick with this setup for now so my boss doesn't kill me for breaking my machine all the time. Now to find out what 8.10 breaks that I can't live without :) Tis the Linux way.

Thanks mate!

---

### Post by phidia on 2008-09-16
Hey that's good news! I'm happy it works for you!
So far 8.10 testing seems to be a real improvement in proprietary driver management, and since alpha 4 or so I haven't seen any long term or hard to fix breakage either.
Happy Ubuntuing to you!

---

