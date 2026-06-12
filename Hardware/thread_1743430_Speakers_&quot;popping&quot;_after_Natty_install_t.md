---
title: "Speakers &quot;popping&quot; after Natty install: troubleshooting help?"
date: 2011-04-29
forum: Hardware
---

### Post by ixregardo on 2011-04-29
Hello, all! I hope I put this thread in the right place.

I have been having occasional speaker problems before, but since I installed Natty they have gotten more regular. What happens is this:

When a sound happens, the speakers "pop" (a funny clicking sound). As long as the sound is engaged (playing music, watching videos, multiple IMs in quick succession), there's no problem. But once the speakers are given a chance to "rest," they have to pop again when there is a new sound.

I really want this to be a hardware problem, but I doubt it is considering the changes when I installed Natty. I'm not sure the best way to troubleshoot here, so any advice would be greatly appreciated!

_Specs_: 
Lenovo Thinkpad T61 (aka worst production run ever)
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
...not sure what else to put here, so ask if you need something more.

Thank you!!:o

---

### Post by legitmatemustard on 2011-04-30
I'm having the same problem with my HP Pavilion Entertainment PC. I only have this problem when my laptop is on battery power.

---

### Post by TangoKilo421 on 2011-04-30
I am having the same problem as well, since Natty upgrade.  A google search turned up a problem with previous versions having to do with a power save feature for the audio chip, which had identical symptoms.  The fix was to "comment out" that line, but the instructions are outdated.

---

### Post by ixregardo on 2011-04-30
Thanks for the input, guys!

@Tangokilo, do you have the link for that article? I'd like to have a look...

@LegitimateMustard, wow, mine is doing the same thing--it's only a problem on battery power.

I found a pretty simple workaround--if you open the sound preferences it engages the speakers and seems to keep them engaged. This helps for me when I'm IM-ing and have sound coming out at random times.

If anyone else has ideas, let me know!

Thanks!

---

### Post by TangoKilo421 on 2011-04-30
If you google "ubuntu popping noise" numerous references and even a youtube vid will appear.  Here's one: [http://tinyurl.com/5rr5b87](http://tinyurl.com/5rr5b87)

Either Natty doesn't have the Intel chip power-down feature, or its somewhere other than alsa-base.conf, so the instructions shown won't be that useful.  It sure sounds like the same thing though.

Oh, and FWIW, mine occurs on both battery and AC power.

---

### Post by ixregardo on 2011-04-30
Thank you! I'll have a look. :)

---

### Post by billiard on 2011-05-01
Same here can not find a fix. I have ATI IXP SB400 Audio Controller

---

### Post by broseman on 2011-05-11
Same here:

HP Pavillion tx2500
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
Only on battery

Has anyone opened a bug on launchpad on this?

---

### Post by ixregardo on 2011-05-11
No... I think I'm going to leave that to someone with a better understanding of the underlying problem. ^^;

---

### Post by cryptonit on 2011-05-15
I think it's due to a kernel bug.

Today I've downgraded my kernel the maverick one (2.6.35-29.51) and didn't experienced one single "pop".

Could you downgrade your kernel and confirm please?

FYI, I've manually installed:

linux-headers-2.6.35-29-generic-pae_2.6.35-29.51_i386.deb
linux-headers-2.6.35-29-generic_2.6.35-29.51_i386.deb
linux-headers-2.6.35-29_2.6.35-29.51_all.deb
linux-image-2.6.35-29-generic-pae_2.6.35-29.51_i386.deb

---

### Post by ixregardo on 2011-05-16
Hi there!

I tried to downgrade the kernel, but I'm not entirely sure how to go about it, or where you got those packages from. In my package manager I only have linux-image (and so on) for version 2.6.38.8.22, which I suspect is the current version. Do I need to add another repository or something like that?

I've mostly come to terms with this bug, so if someone else would like to take on this verification, I'd appreciate it :)

---

### Post by wilhelmschumann on 2011-05-21
I have Upgraded some packages on My laptop ( HP Pavilion DV 9000 ) and that annoying popping noise has stopped .
I think is something related with Xorg, Xorgserver or X11.

Cheers!

Those Packages updated are:


Upgraded the following packages:
apturl (0.4.2ubuntu5) to 0.4.2ubuntu5.1
apturl-common (0.4.2ubuntu5) to 0.4.2ubuntu5.1
firefox (4.0.1+build1+nobinonly-0ubuntu0.11.04.2) to 4.0.1+build1+nobinonly-0ubuntu0.11.04.3
firefox-gnome-support (4.0.1+build1+nobinonly-0ubuntu0.11.04.2) to 4.0.1+build1+nobinonly-0ubuntu0.11.04.3
flashplugin-installer (10.2.159.1ubuntu1) to 10.3.181.14ubuntu0.11.04.1
geoclue (0.12.0-1ubuntu to 0.12.0-1ubuntu8.1
gnome-nettool (2.32.0-0ubuntu1) to 2.32.0-0ubuntu1.1
im-switch (1.20ubuntu3) to 1.20ubuntu3.1
language-pack-en (1:11.04+20110421) to 1:11.04+20110509
language-pack-gnome-en (1:11.04+20110421) to 1:11.04+20110509
language-selector-common (0.34) to 0.34.2
language-selector-gnome (0.34) to 0.34.2
libgeoclue0 (0.12.0-1ubuntu to 0.12.0-1ubuntu8.1
libntrack-qt4-1 (011-1ubuntu1) to 011-1ubuntu1.1
libntrack0 (011-1ubuntu1) to 011-1ubuntu1.1
libtelepathy-logger2 (0.2.6-1ubuntu1) to 0.2.6-1ubuntu1.2
ntrack-module-libnl-0 (011-1ubuntu1) to 011-1ubuntu1.1
python-papyon (0.5.5-1ubuntu1.1) to 0.5.5-1ubuntu1.2
software-center (4.0.1) to 4.0.2
telepathy-logger (0.2.6-1ubuntu1) to 0.2.6-1ubuntu1.2
x11-common (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xorg (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xorg-dev (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-common (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-xorg-core (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg-dev (2:1.10.1-1ubuntu1) to 2:1.10.1-1ubuntu1.1
xserver-xorg-input-all (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1
xserver-xorg-video-all (1:7.6+4ubuntu3) to 1:7.6+4ubuntu3.1

---

### Post by ixregardo on 2011-05-21
Hmmm... this didn't work for me. Still popping.

---

### Post by adney on 2011-05-31
My speakers pop occasionally with 11.04 on startup and shutdown, but they also pop a lot whenever my computer is on battery power.  I blacklisted the intel-audio-powersave pm-utils module to prevent my card from going into power_save mode and that fixed the vast majority of my "pops" (all that came from being on battery power).

To blacklist this module, create a file with any name in /etc/pm/config.d containing this text: ```
HOOK_BLACKLIST="intel-audio-powersave"
```

---

### Post by ixregardo on 2011-06-01
This seems to have worked! Thank you!

For anyone else who was confused, the file doesn't need to have any extension.

---

