---
title: "Hibernate &amp; Suspend do not work"
date: 2007-08-23
forum: Hardware &amp; Laptops
---

### Post by Kortalh on 2007-08-23
I've spent the last couple days scouring the internet for a solution to my problem, but from what I've read, getting Hibernate and Suspend to work seems to be completely luck of the draw. Making matters worse, I'm a *complete* Linux newb. Call me a Vista refugee. :wink:

Anyway, my problem, obviously, is that I can't seem to get Hibernate or Suspend to work on my laptop -- a Sony Vaio PCG-FRV37, purchased around 2004. Both Hibernate and Suspend work marvelously in Windows XP, so presumably the hardware is *capable* of doing it.

Here's what happens...

When I try to Suspend, the laptop seems to successfully go into suspension. The speakers click (as they normally do when powering down), the screen turns off, the fan stops humming, and the PCMCIA wireless card's lights turn off. Unfortunately, when I try to reawaken it, it comes to a standstill -- the fan kicks in, the wireless card's lights start blinking, but the monitor stays off and nothing else happens. The only option is to power it down and reboot.

When I try to Hibernate, the video flickers and goes black, then displays a line of red gibberish-dots, about 10px tall, across the top of my screen. A few moments later, I'm looking at the Lock Screen password prompt. After logging in, it returns me to the shutdown menu. Occasionally it warns me that I have a problem with HAL.

I tried typing "sudo open /bay/doors" into the terminal, but that didn't seem to do anything. :wink:

Other things I tried, based on these forums and elsewhere:
- I played with a number of variables in /etc/default/acpi-support, but nothing seemed to effect anything.
- I installed uswsusp and ran the s2disk command. It says that it's taking a snapshot, then the screen goes black (but doesn't power down) and the system freezes. The only option is to reboot.

Does anyone have any other suggestions?

---

### Post by whirl on 2007-08-24
My girl friends laptop has the exact same problem as you with the hibernate. Only difference it tries to take the system pic but in few seconds gives you the logging screen and when you log in it gives error in finnish saying something like HAL-command failed.

So anyone got a solution or tips for this?

Cheers!

---

### Post by tewe on 2007-08-24
im the same problem (suspend works, but dont wake up) on Thinkpad R60e with Gutsy, i tried acpi_sleep=s3_bios into the grub menu.lst, but didnt worked. i've tried s2ram too, but the result was the same...

---

### Post by fcastillo on 2007-08-24
I have the same problem, hibernate or stand by doesn't work in my laptop. I have a HP dv500 with Intel Centrino Duo 1.83GHz, and 2Gb of RAM. I can't believe that everything else is working except this... Any help out there??

---

### Post by robeec on 2007-08-24
same problem on my dell dimension running feisty. i successfully can put the pc to sleep or hibernation but cannot wake it up--have to restart every time.

anybody figured this out?

---

### Post by rainwalker on 2007-08-24
Hibernate and suspend don't work for me either on my Inspiron 8600.
Hibernate worked fine back when I ran Dapper on an Inspiron 7500, but not in Edgy or Feisty (I don't know if that's useful, but I figured I might as well share it).

---

### Post by spier on 2007-08-24
Some thoughts that may help:

Edit /etc/default/acpi-support and try different settings, particularly those:

the default installation`s comments are self -explanatory;
uncomment settings work on my sony vaio fs series laptop.

```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
# ACPI_SLEEP_MODE=standby
ACPI_SLEEP_MODE=mem

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation -> platform or shutdown or ?
# HIBERNATE_MODE=shutdown
HIBERNATE_MODE=platform 

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true 
```

---

### Post by ntlam on 2007-08-24
> **spier said:**
> Some thoughts that may help:

Edit /etc/default/acpi-support and try different settings, particularly those:

the default installation`s comments are self -explanatory;
uncomment settings work on my sony vaio fs series laptop.

```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
# ACPI_SLEEP_MODE=standby
ACPI_SLEEP_MODE=mem

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation -> platform or shutdown or ?
# HIBERNATE_MODE=shutdown
HIBERNATE_MODE=platform 

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true 
```

I tried this

did not work.

I tried suspend before and my laptop got frozen. I had to press the power button for a while to shut it down

---

### Post by Kortalh on 2007-08-27
> **spier said:**
> Some thoughts that may help:

Edit /etc/default/acpi-support and try different settings, particularly those
<snip>

Thanks for the suggestions. I've already toggled pretty much every relevant option in that file, but I gave it another shot using your setup -- unfortunately, it didn't seem to change anything.

This whole thing has me pulling out my hair... I really want to use Ubuntu to keep me on task when I'm working on assignments for college (windows has too many distractions), but the lack of hibernate functionality is a pretty major inconvenience for me.

At this point, I'd do just about anything for a working solution. :(

---

### Post by mpphilli on 2007-08-27
Try adding the following repository to your sources.list

[http://download.tuxfamily.org/3v1deb/dists/feisty/suspend2/index.html]("http://download.tuxfamily.org/3v1deb/dists/feisty/suspend2/index.html")

From the webpage:
   Ubuntu feisty kernels patched with suspend2
This repository contains all the ubuntu kernel related packages containing both the ubuntu patches and the suspend2 support to improve your hibernation (to ram/disk) experience!
This repo is actually under development, so use it with caution

Using this repository my suspend works great. I have not tried to use hibernate yet.

MIKE

---

### Post by tewe on 2007-08-29
> **mpphilli said:**
> Try adding the following repository to your sources.list

[http://download.tuxfamily.org/3v1deb/dists/feisty/suspend2/index.html]("http://download.tuxfamily.org/3v1deb/dists/feisty/suspend2/index.html")

From the webpage:
   Ubuntu feisty kernels patched with suspend2
This repository contains all the ubuntu kernel related packages containing both the ubuntu patches and the suspend2 support to improve your hibernation (to ram/disk) experience!
This repo is actually under development, so use it with caution

Using this repository my suspend works great. I have not tried to use hibernate yet.

MIKE

ok, but what about gutsy?
i use gutsy, but the problem is the same ...
(Thinkpad R60e)

---

### Post by sunspots on 2007-08-29
I have been testing Gutsy Gibbon Tribe-5 and found the sleep to work but not the hibernate. Actually, it hibernates but I can't revive the system from hibernation.

Have a look at the following bug report.
[https://bugs.launchpad.net/ubuntu/+bug/135088](https://bugs.launchpad.net/ubuntu/+bug/135088)

It would be good if you applied your comments to it. It is unlikely that it will be fixed on anything before Gutsy. I had similar comments on another problem I found, but they fixed it for Gutsy Tribe-5.

If you can test Gutsy and contribute to the bug reports it would help us all for the future versions of Ubuntu.

---

