---
title: "Toshiba laptop woes"
date: 2009-05-27
forum: Hardware
---

### Post by Tomlin on 2009-05-27
Okay, I spent my day:

1) installing 9.04 on a Toshiba Satellite.
2) uninstalling when I realized the ATI video driver sucks and wouldn't let me run compiz under 9.04.
3) installing 8.10 and spending the morning getting the Atheros wireless working (using ndiswrapper).
4) downloading 200+ MB worth of updates and setting up my environment......


......only to have it freeze up every 15 - 20 minutes; black screen, unresponsive, can only shut it down by holding down power button until it shuts off.

Before I totally give up and just run vi$ta, is there anything that I may be overlooking?

I'm running 8.10 on my desktop and it's fine. I realize laptops can be finicky, but I can't see spending another day (or more) trying to get Ubuntu to work if my reward is more frustration. What's maddening is I have 8.10 running on a POS Gateway that was given to me, and it works like a charm - except the battery is shot and it needs to be plugged in to operate. A new battery is almost $200, that's why I spent an extra $200 and bought the Toshiba.

Sorry for the rant, but it's been a LONG (wasted) day.

---

### Post by theozzlives on 2009-05-27
I get tired of people threatening to go to virus and malware ridden Windows. Install 9.04, google compiz-check, run it... if your video is blacklisted, override it and see what happens.

---

### Post by mwm1998 on 2009-05-28
At least malware, bug infected windows works.  You can watch video, you can print to about any printer you want to use.  You don't get frustrated by spending hours (I literally mean many hours) of trying to get linux distros to perform the basic tasks.  

Just help the guy out and quit throwing stones.  

It is very frustrating for anyone fairly new to get everything going.  I havent been able to do it yet after several weeks of trying various distros.

---

### Post by BooDaddy on 2009-05-28
Im in the same boat. I had to dual boot to XP because I cant get ubuntu to display anything after running the ATI driver update from ATI.  All I can get is the ubuntu logo and then thats it. the display goes black.  Been working for hours trying to get ubuntu back.

---

### Post by natman on 2009-05-28
I have a toshiba satellite a300 21h under kubuntu, with intel gfx they are not perfect but work ok, but i found this page of [COLOR="Red"]experimental[/COLOR] drivers , if you want to give them a  chance?
[http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html](http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html)

If they work, remove the repos an dbe happy, otherwise you may update the driver to a version that is not as good as the previous one!

---

### Post by jdos2 on 2009-05-28
I've found that after years and years of experimenting with Linux that switching distributions never gives quick payoffs in terms of useability. Each distro does much right, and what they do wrong is a true Pain in the Butt, but switching distributions just switches bugs. Choose which bugs are fixable takes judgment and time.

Though you probably paid a license for an operating system on your laptop, playing with Linux is still fun. If you need Linux, you'll know it- like decent free 64 bit compilers (the line I personally draw for my Thinkpad X61T). Otherwise, pick your poison and work through the problems. The choice eventually comes down to what you want to do- and if a perfectly seamless operating system is what you want, you'll never get it with ANYTHING.
If you NEED your laptop to be fully functional in a particular way that is simply not easily done on Linux, then Windows is your answer- and a dual boot is just fine and works well. That might give you the time to fix enough things (taking notes!) that you might be able to someday dump windows. It really doesn't take too long to install both OS's compared to the amount of time you can spend making them both right!

Create a text file and start writing down the bugs- one line at a time, and then log how you fix them, including copy-pasting in URL's to backtrack and help you do it again when it comes time to update your system. You'll almost certainly need to, as upgrading in Linux is rarely painless (again, my experience, and compared with both AIX and Solaris). Prioritize your bugs. Figure out what you need to do.

For me on my X61, I have to have the tablet working with rotation and xrander. That's a top priority, and when 9.04 came out... Well, Ubuntu broke those so badly that I had to go to a different distro, OR SIMPLY NOT UPGRADE. My choice. Sadly not discovered until afterwards (as many did), but that's GNU/Linux, and that's why I have a good backup of my home directory, and why I keep a list of how to get things working in each distro/revision. Several weeks later there are workarounds, but really, 9.04 isn't all that attractive, with the Intel driver "fixes", &c, so I don't run it. Earlier versions, on the other hand, cater better to my priorities.

Work, then, on the broken things one at a time, until you make an improvement. When I had my Toshiba, sound was terrible and needed new ALSA just to GO, not that the sound card was new (again, welcome to Linux!). This was back in the 7.04 days, and the best part were the kernel upgrades that force me to reinstall drivers from source. I keep a ~/dev directory ("development") just for that occasion to this day, but only rarely do I have to recompile drivers anymore, and none on the current distribution (Debian Squeeze on the laptop).
I also remember that I had to download a different kernel to use ndispluginwrapper- something about kbuffs, but I don't have document on the Toshiba anymore...

Keep at it and you'll learn a lot about Linux and the various personalities that seem to drive the little bits that make up the system. It's like trying to keep a drunken party moving forward, sometimes, and you have to talk with everyone just to make the simple steps in the direction things should go. It's also the price we pay for free software. I'm betting (having been part of large software creation) that it's exactly the same inside the halls of MS- but we don't hear about it like we do in the mailing lists, and at least someone does set direction, even if it's wrong ("nailed firmly crooked")

Now if I could just get my microphone to digitize my voice instead of simply passing through the system and out the speakers... But that's an ALSA issue, and on my list.

---

### Post by Tomlin on 2009-05-28
@theozzlives

I'm not threatening anything. I'm just saying that a computer that doesn't work is of no use to me, just as a car that stalls every few minutes would not be something I'd use if I needed to get to work every day. But thanks for your help & insight :rolleyes:

For anyone else who's having similar problems...after checking the /var/log/user.log file, it appears that the same message appears over and over approx. the time the system freezes:
May 27 16:42:02 intrepid-laptop pulseaudio[5756]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

I checked the web and found this thread on ubuntuforums:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

I followed the instructions and have had no further freezes. I'll continue testing. Some of you may want to try this fix.

I also found out that updating the kernel from 2.6.27-7 to 2.6.27-14 caused the laptop to not bootup. It would stop with:

update-binfmts: warning: couldn't load the binfmt_misc module
# checking battery state.......[OK]

Then the screen would black out for 5-6 seconds, come back on, then  off....repeat.

I went back to 2.6.27-7

Good luck.

---

### Post by BooDaddy on 2009-05-28
I got my computer going again.  I was having video issues. Check this thread and read my post on how I got my computer going:

[http://ubuntuforums.org/showthread.php?p=7362450#post7362450](http://ubuntuforums.org/showthread.php?p=7362450#post7362450)

---

### Post by welshmike on 2009-07-19
Apologies. I'm a newbie to this forum and don't know how to start a new thread.
I'm running Ubuntu 9.04 dual boot on my Toshiba laptop.
The system freezes at random times sometimes as soon as 30 minutes after booting. I then have to power off and reboot.
How do I go about finding what the problem is.

---

