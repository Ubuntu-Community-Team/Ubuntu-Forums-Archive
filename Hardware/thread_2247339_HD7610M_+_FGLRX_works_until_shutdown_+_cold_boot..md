---
title: "HD7610M + FGLRX works until shutdown + cold boot."
date: 2014-10-07
forum: Hardware
---

### Post by richierich1986 on 2014-10-07
So I have a Toshiba C855-255 laptop with Radeon HD7610m graphics and I have a problem that I haven't
come across on any forum or google search.

I've had this problem on numerous clean installs and the following happens:

1. I install Ubuntu 14.04.1 on my laptop and reboot.
2. I install all pending updates and reboot.
3. I install fglrx-updates and fglrx-amdcccle-updates and reboot. 
(I've tried regular fglrx and fglrx-amdcccle as well. This seems to make no difference to the result.)
4. I reboot and open catalyst control centre (the one with root access) and apply my preferred settings.
5. I can reboot and reboot one after another without any problems. Everything works wonderfully.
6. But then I shutdown and do a cold boot. After I shutdown+cold boot, from now on on every reboot or 
cold boot I'll have distorted graphics and I can't read the text very well, but I can login. After login though, 
clicking stuff does nothing andthe only thing left for me is ctrl+alt+F2 and uninstall fglrx-updates and 
fglrx-amdcccle-updates, so that on the next boot, I use the open source radeon driver again.

This has been the case ever since I bought this laptop a few years ago, so from Ubuntu 12.04 up untill now.
I figured a newer kernel and newer proprietary drivers would eventually fix this, but as far as I've read, 
the Radeon HD7610m chip should be working okay with Ubuntu 14.04 and the provided drivers.

I have no deep understanding of hardware and driver software, but seeming everything continues to work,
even on reboots, just not after shutdown+cold boot, maybe certain settings aren't saved properly or at all?

Any help at all or even just finding out why it can't work or if it's brand related would be a big help. I would
like to use the proprietary driver because it just works a lot better with games and since my favorites are
all supported on Linux as of lately, I like to get it to work.

Thanks!

---

### Post by richierich1986 on 2014-10-17
Hasn't anybody got a clue as to what might cause this?

---

### Post by richierich1986 on 2015-02-11
So I still have my problem and I thought maybe a few photo's would ring a bell for anyone
and clarify my issue.

[https://drive.google.com/file/d/0BxM1l6r_gvv5SFc3MFpWa0NSU1k/view?usp=sharing](https://drive.google.com/file/d/0BxM1l6r_gvv5SFc3MFpWa0NSU1k/view?usp=sharing)

[https://drive.google.com/file/d/0BxM1l6r_gvv5UHl5a1Y0c293M1E/view?usp=sharing](https://drive.google.com/file/d/0BxM1l6r_gvv5UHl5a1Y0c293M1E/view?usp=sharing)

I tried the fglrx-core and fglrx packages from the AMD driver site this time, version 14.501,
packaged for ubuntu 14.04, but the result is exactly the same as with the versions in the repositories.
Everything functions, and games like cs:go work, but it's just that the screen always looks like this.

the black bar in the middle is seen as the screen edge, so I can't cross that with the pointer.

Any ideas, anyone?

BTW: I realise this is Linux Mint, but it does the exact same thing in Ubuntu 14.04 and Elementary OS Freya.

---

### Post by QIII on 2015-02-11
Hello!

Even a hot reboot shuts down the OS and restarts it, so it does not seem to me that the problem is with the driver.

This sounds more like a hardware problem.

Would you be willing to try an experiment?

---

### Post by richierich1986 on 2015-02-11
yes, sure!

what do you have in mind?

The GPU worked fine in windows 7 and 8 btw, which I tried a while
back after I started this thread, just in case that helps.

---

### Post by QIII on 2015-02-11
Hmmmm.  That may make the test pointless.  I suspected a thermal component.

Let's try anyway.

Install the driver.  Do a cold reboot.  Instead of shutting down right away, let the machine run for 5 or 10 minutes to warm up and see if things are as they should be on a warm reboot from there.

---

### Post by richierich1986 on 2015-02-11
the test made no difference. it ran for about 20 min while i was on this pc
and a reboot changed nothing. 

I did discover that closing the laptop lid and letting the laptop go into sleep mode,
then opening the lid fixes all the glitches although the wallpaper shows sometimes
and other times is a sort of static noise like on old tv screens, but the effects and
interface still work without glitches.

btw: fglrxinfo shows a correct output without mesa errors or anything.

---

### Post by QIII on 2015-02-11
That is definitely intriguing!

Unfortunately I don't have a laptop with AMD graphics to do any testing on.  The one I did have died, so some of its innards were repurposed.

---

### Post by richierich1986 on 2015-02-11
So I've tried it a dozen more times and every time I boot or reboot the screen is distorted,
while every time I close the lid and it goes into suspend and I open the lid again to wake
from suspend, everything works fine. Really stable actually and the driver works very smoothly
with lower GPU temps, slick graphics and no distortion.

It would seem like some wrong settings or something are loaded on boot which would be corrected
when loading from suspend. This is a UEFI system by the way. Secure Boot is disabled and fast boot
is enabled, but this seems to make no difference compared to normal boot and/or Secure Boot enabled.

anyone any experience with this laptop (toshiba c855-255) or maybe toshiba, uefi and ati chips in general?

---

### Post by richierich1986 on 2015-02-12
New development today:

I noticed today that before suspend, after boot and login, in amdcccle the display type is LVDS,
but after suspend it says it is a DDC display.

EDIT: nevermind. After a reboot, It still says DDC before and after suspend.

I've a link to the output of my Xorg.0.log: [http://pastebin.com/yebPPJGu]("http://pastebin.com/b8r74RRT")

---

