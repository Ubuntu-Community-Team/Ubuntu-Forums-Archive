---
title: "Can I install 9.10 on my PC or not???"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by darkod on 2009-11-06
Hello all.
Can someone please advise me whether I can install desktop 9.10 on my PC or not.

I downloaded the images, all three of them (32bit, 64bit and Remix).
On my netbook I installed first Remix and then Desktop 32bit. Working fine and loving it.

Here is the problem:
1. Burned the 64bit image on CD. Booted my desktop with the CD and selected the Try Ubuntu option just to check how the hardware would behave.
2. After selecting the option, the black screen with the white logo stays there for a while, looking normal.
3. When you expect to see the desktop (login screen), the brown screen with Ubuntu written shows up just for a split second and then the PC reboot itself.
4. Tried the above 3-4 times, no luck. Always rebooting itself at the same point.
5. Created a USB stick with the 32bit image. Tried it in my PC, the same result, rebooting at the same point. Installed Desktop 32bit on my netbook with the very same USB stick, worked perfect.

From googling around, there seem to be an issue sometimes with an integrated Radeon HD3200, just what I've got. But I could not find explicit statement that Desktop 9.10 would not work on HD3200. On the contrary, few posts mentioned that 9.10 would have good drivers for HD3200 by default.

So I am totally confused now. I haven't try the Install option because I don't think it will work then the Try option is failing. Would it? I don't want to repartition my drive to make space for Ubuntu just to find out it can't be installed on my PC. I would rather know in advance. That was the point of the Try Ubuntu option and that's not working.

Some pople with HD3200 mention different drivers, radeon or fxglr, etc. But in my situation I don't have already working Ubuntu, to try with different drivers for better results. How can I select drivers for Try Ubuntu option? Or for Install option? Any advanced options that could help in the main menu of the Ubuntu CD?

Should I just give up? I want to install Ubuntu on my desktop too but with the CD and USB stick failing what are the options? While typing this I am downloading the 9.04 image to see if that will work but even if it does I prefer the latest release.

Why wouldn't it work on HD3200? (assuming that's the issue here)

Thanks a lot for any thoughts. Cheers.

---

### Post by khelben1979 on 2009-11-06
Get your ATi drivers [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English") and make sure to follow the installation instructions and it should work.

---

### Post by darkod on 2009-11-06
Thanks for the prompt answer.

I visited the ATI link and read the Installer Instructions if that's what you meant, but I didn't see instructions how to install them before even Ubuntu is installed. Or I am missing something?

I am new to Ubuntu so I might not know something that is considered general knowledge. :p

---

### Post by khelben1979 on 2009-11-06
Okay, then I think that installing the drivers through [EnvyNG]("http://en.wikipedia.org/wiki/EnvyNG") is a better choice for you. [Check out this video]("http://www.youtube.com/watch?v=zPgqVyhZF4Y").

---

### Post by darkod on 2009-11-06
Sorry to be a pain but it seems we are talking about different situations.
The ATI instructions were not too complicated for me. It's just that browsing them I did not see a situation specified where you install them WHILE STILL/BEFORE INSTALLING UBUNTU ITSELF. The instructions assumed a running version of Ubuntu, which I don't have.
The same for the EnvyNG package. You need to install it from within Ubuntu, right?

I do not have a running version, the Ubuntu CD just reboots my PC. First I'm trying to find out whether the installation can be successful at all because the Try Ubuntu option fails, and that option exist so that you could see how and whether Ubuntu would work on your computer.

If I start the installation, it will either work and then I can try various drivers, or it will fail which will mean I repartitioned my drive for nothing. And that's what I'm trying to avoid. The live CD fails. Is there a way to know if the installation will work or fail?

---

### Post by PRC09 on 2009-11-06
I believe you can try the alternate install cd but you would to still have to partition your drive to use it.

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by darkod on 2009-11-06
Thanks, I'll read more about it.

---

