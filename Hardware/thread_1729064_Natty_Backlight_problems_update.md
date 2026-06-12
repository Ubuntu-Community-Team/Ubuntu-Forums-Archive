---
title: "Natty Backlight problems update"
date: 2011-04-14
forum: Hardware
---

### Post by travissparks1307 on 2011-04-14
Hello Forum!

I have previously posted about the lack of back lighting with Natty Beta 1. When I first discussed this issue I was directed to this bug.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611)

But it is NOT the issue. This bug affects Dell Studio 1558 brightness control. The bug I am referring to, is a complete lack of back lighting on an Acer Aspire 5734Z laptop. I would like to point out that in Alpha 1 this was not a problem. It began being a problem with Alpha 2. My hopes were that subsequent development would solve the issue. This has not been the case. I would like to report this as a bug on Launchpad, however, I can't run ubuntu-bug on a system where I'm completely blind. 

I have explored several fixes. Running with ACPI turned off returns backlighting, but uses GNOME as the desktop instead of Unity, and the screen resolution is wrong. I am aware that these things are because of Natty running in a "safe" VGA mode. These problems are the same in Natty Beta 2. 

I believe this to be a very serious bug. I do not know how many other systems are possibly affected by this. 

Any and all assistance or attention to this matter is greatly appreciated. All constructive suggestions, instructions, and ideas are welcome.

---

### Post by travissparks1307 on 2011-04-26
UPDATE: On a whim I decided to try a distribution upgrade to 11.04 from a fresh install of 10.10. The short of it is, same problem. HOWEVER! (This is where it gets interesting) I accessed the grub boot menu after, and found "Previous Versions" I ran the 2.6.35 kernel and BEHOLD! Backlight AND Unity! For all intents and purposes 11.04 is running, but with the older kernel from 10.10 I think this proves that the bug is in the kernel. 

Other than that, everything is working great! I am continuing my work on this however. My next step is to get the latest stable kernel from kernel.org and install it. I also intend to re-compile the stock kernel that comes with Natty and see what happens.

I will continue my work, and keep the community/forums informed of my progress.

---

### Post by docmark777 on 2011-04-28
It sill isn't fixed.  

I have the same problem in my aspire 5732Z

---

### Post by awam66 on 2011-04-28
I have this problem also on Dell Dimension C521 amd64 64bit and 32 bit(on external USB drive). Removing splash and quiet does not make any difference. System boots OK but blank screen throughout booting. Most annoying if it does a disk check and the boot take for ever.

---

### Post by lucazade on 2011-04-28
Have you tried with "acpi_backlight=vendor" kernel parameters?

what is the output of:
ls /sys/class/backlight/

---

### Post by CharlesA on 2011-04-29
Moved to hardware and laptops, since it seems to be a "hardware" problem.

---

### Post by euchrid on 2011-06-15
I have an Acer Apsire 5336, and struggled with this for days. I found a decent workaround in this thread:
[http://ubuntuforums.org/showthread.php?p=10943621](http://ubuntuforums.org/showthread.php?p=10943621)

Hope this helps someone. I agree that this is a very serious issue - it appears that the screen is not working unless you happen to shine a light on it. I found it was definitely NOT a driver or brightness issue for my laptop, and no suggestions other than the one in the above thread were of any help.

---

### Post by travissparks1307 on 2011-08-14
Howdy Forums!

Well, I decided to give the latest build of Oneiric  a shot. Guess what? SAME PROBLEM!

I first reported this in Natty's testing phase, but it found its way into the production release. I have been working on it. The only way I found that works is a fresh install of a previous release, either Lucid or Maverick, and then doing an upgrade, and booting with an older kernel.

I have also found out this bug affects derivatives based on Natty. The problem came up with Kubuntu 11.04, as well as Linux Mint 11.

I'll be firing up Oneiric in "safe mode" and running ubuntu-bug to report it to Launchpad as soon as I finish this post. I sincerely hope that this issue is resolved soon. At least by the time Oneiric sees production release.

I will follow this post with a link to the bug report.

---

### Post by travissparks1307 on 2011-08-14
Back from Launchpad. It's officially filed. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/826386](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/826386)

---

### Post by tiggsy on 2013-05-01
Samsung Notebook NC110 with same problem on 12.04.2

However, if you select "recovery mode" and then "normal boot" it works fine.

What seems to happen is that the backlight is turned off at the start of the boot process if you don't go the recovery route, and never gets turned back on.

---

### Post by tiggsy on 2013-05-01
The grub file isn't at /etc/default/grub where else might it be? Or if I need to get it from somewhere else first, what options are available if you don't have a disk drive?

---

### Post by overdrank on 2013-05-01
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

