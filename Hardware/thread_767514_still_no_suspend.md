---
title: "still no suspend?"
date: 2008-04-25
forum: Hardware
---

### Post by phoenix5002 on 2008-04-25
I started with Ubuntu in Gutsy 7.10.  and I spent a lot of time trying to get suspend to work.  I finally gave up (because hardy was only about a month away) so I was certain that (seeing how many people with laptops were having suspend issues) that they would actually have it fixed in hardy.  I switched to hardy early and suspend still didn't work.  someone said that it would probably be a good idea to do a fresh install so I did...  I just downloaded hardy heron, burned to a cd and did a complete fresh install of it on my laptop today: 04/25/08.

still no suspend...  I cannot believe it!
can anyone PLEASE HELP ME!!  I can't take it anymore I really need suspend, I was able to bite my lip and get through it when I at least had some hope that hardy would have suspend fully working, but now it's here and suspend is just as broken for me in hardy as it was in gutsy.   :mad:

I have a "RADEON IGP 345M" video card, on a sony VAIO laptop.  using GNOME if you need any more info I'd be very happy to provide it.

---

### Post by Patsoe on 2008-04-25
Are you using the proprietary ATi video driver?

On my machine (which has an older chipset though), suspend didn't use to work with that driver, while it did work with the open-source driver. So it was sort of a trade-off: a working suspend function or faster 3D graphics...

After installing hardy I didn't even bother checking out the proprietary driver. Suspend works.

---

### Post by phoenix5002 on 2008-04-25
I'm using the open source drivers that Ubuntu gave me.  I'm on a completely fresh install of Ubuntu 8.04 havn't really changed anything yet.
I've tried the proprietary drivers though on gutsy and hardy before I reinstalled hardy, and neither worked.
but ya, I'm currently on open source ATI drivers.

---

### Post by noynac on 2008-04-25
I have a plain-jane Dell computer with a quite common nVidia video card. I've been using Ubuntu since Dapper, and suspend has never worked on my computer. On a number of occasions, I've tried suggestions from threads in this forum but to no avail. I finally decided it just wasn't going to happen.

---

### Post by twright on 2008-04-25
it finally works well for me at least,

for feisty i needed to change a setting but it worked ok
for gutsy i needed to use envy and it crashed after a few suspends
but in hardy i just needed to use hardware drivers to install the ati driver and it is both fast and reliable

submit a bug report, someone will probably be able to help

---

### Post by phoenix5002 on 2008-04-27
if someone can help me get hibernate working, then that would be great too.  I think the only issue I'm having there is my USB mouse doesn't work after I resume.

---

### Post by Patsoe on 2008-04-27
I just remembered how I got suspend working with my ATi integrated chipset (that was since 5.10 I think). It's worth trying because you don't need to make any permanent changes at first: at the GRUB boot menu, edit the kernel parameters (to edit hit e) and remove "splash" from the list. This gives you a framebufferless boot process so the boot messages aren't as nicely formatted. After that, Gnome should just look as it always does.

This allowed me to resume from suspend properly. The only downside I see is that my consoles are now low-resolution, but actually I always work in Gnome terminals anyway...

Totally forgot about this when I first looked at this thread :)

---

### Post by jaburr on 2008-04-28
@ phoenix5002 - 

"I think the only issue I'm having there is my USB mouse doesn't work after I resume."

Ditto.  Fresh install of Hardy, but I noticed that the USB mouse had stopped working after suspend for the last few weeks of the pre-release version too.  Probably going to file a bug report if I can't find any solutions on my own.

JB

---

### Post by jaburr on 2008-04-28
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/216633](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/216633)

Yep, looks like there's already bug reports filed.

---

### Post by r32inc on 2008-04-29
I have a HP tx2000 runing ubuntu-8.04-amd64 and i alo can't suspend nor hibirnate the laptop all I get is is a black screen on the LCD once I wake up the laptop from suspending and hibirnating.  Tried reinstalling serval times both i386 versions and amd64 and with and without nvidia drivers.

Bummer

---

### Post by Dakiraun on 2008-04-29
I have a Compaq R3000 with an Athlon64 3200, 1.25g RAM, a 64M nVidia 440  GO and a fresh 100g PATA drive in it that I just got Hardy on.  Been using Ubuntu for ages on the work laptop and the main PC, finally got it on the laptop since I figured it'd be time to change on getting the new drive.

Only big problem thus far is the suspend issue.  It would not go into suspend properly, and thus not come out.  

Using the terminal, I edited /etc/default/acpi-support (you must do this with "sudo" to elevate your privileges for those not familiar with *nix OS's), and changed POST_VIDEO=true to POST_VIDEO=false.  This usually takes are the the issue with some systems, but only half fixed it for me.  The laptop now goes into Suspend just fine, but it doesn't come back out fully (the screen stays blank). 

I'll keep tinkering to see if I find any other things to try - in the mean time, if anyone else has figured it out on this family of laptops, feel free to chime in.

---

### Post by zzottt on 2008-04-30
I tried the verious ideas posted here and I still have problems suspending my HP/Compaq 6910p

It does not have any restricted drivers
the thing that bugs me the most is that it works "sometimes" but never works right even if it kinda works. If it comes back from suspend it doesnt initialize the wireless or does other odd things... could it be the wireless driver? Again Im not using any restricted drivers and pretty much a default install of 8.04

:confused:

---

### Post by twright on 2008-04-30
try looking here:
[http://people.freedesktop.org/~hughsient/quirk/](http://people.freedesktop.org/~hughsient/quirk/)

---

### Post by andrewbrown22 on 2008-04-30
Same issue for me. Dell Inspiron E1505, after going in to suspend, I have no control over the mouse or keyboard.  From doing some reading, this is apparently an issue that has been around for a while.
I edited a file last night (from a suggestion on these forums), I'll have to look to see what it was, it seemed to work for a while, but earlier this afternoon the issue came back.

---

### Post by Dakiraun on 2008-05-04
> **twright said:**
> try looking here:
[http://people.freedesktop.org/~hughsient/quirk/](http://people.freedesktop.org/~hughsient/quirk/)

Aye, tried many of the things already mentioned in this write as well as the script, which just tells me that the nVidia binary that I'm running is not supported.  Additional testing with some other option tweaks has also not been useful.

When I resume, there is a screen that comes up for maybe a second indicating an ALSA error - I pulled out the camera and managed to catch it:

[IMG]http://publish.uwo.ca/~aaronm/pub-forum/suspend-issue-R3000.jpg[/IMG]

I've tried removing the snd_intel8x0 module to resolve it, but still get the same error.  Given that the laptop goes in and out of Suspend many times a day as well as Hibernate, this may unfortunately mean I have to go back go XP (much as that turns my stomach).  Anyone else having any luck?

---

### Post by Dakiraun on 2008-05-04
Got it!

Okay - I have Suspend and Hibernate now working reasonably well.  The final tricks were right on our door step here:

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

In addition to what's mentioned in that article, I also set the wireless and part of the sound sub-system for removal under my modules in /etc/default/acpi-support:

```
MODULES="b43 snd_intel8x0"

```

Does this work perfectly?  Not quite.  Sometimes it works perfectly, but more often then not there's a minor issue where when you come out of suspend, you see only a coloured screen and your mouse cursor instead of the window prompting you for your password.  I found that it actually **still is** waiting for you to input your password, it just isn't showing as such.  Enter your password, and you end up back in X/gnome as before.

Edit: One other thing I've noticed is that when it comes out of standby, the wireless light is on (I usually have wireless disabled since I neither like or use wireless).  Seems Ubuntu doesn't remember the state it was last in on reloading the module.

Here are the contents of my acpi-support file (less comments):

```

ACPI_SLEEP=true

ACPI_HIBERNATE=true

ACPI_SLEEP_MODE=mem

MODULES="b43 snd_intel8x0"

MODULES_WHITELIST=""

SAVE_VBE_STATE=false

VBESTATE=/var/lib/acpi-support/vbestate

POST_VIDEO=false

SAVE_VIDEO_PCI_STATE=true

USE_DPMS=true

HIBERNATE_MODE=shutdown

LOCK_SCREEN=true

STOP_SERVICES=""

RESTART_IRDA=false

ENABLE_LAPTOP_MODE=false

SPINDOWN_TIME=12

```
Now... I'll probably continue to tinker to see if I can get that odd issue of the screen not showing the password prompt to go away, but for the most part, this finally resolves the issue for the AMD R3000 in Hardy.  If anyone already knows how to get around the issue, please post. :)

---

### Post by starcannon on 2008-06-18
I had suspend issues on this Dell Inspiron | 5100 mostly resolved by adding:
```

Section "Device"
	Identifier	"Configured Video Device"
        Option          "VBERestore"    "true"
EndSection

```

The VBERestore part to my xorg.conf, it always resumes from suspend, though it does sometimes complain.

---

