---
title: "Compaq n610c: need suspend and/or hibernate support"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by oldtappan on 2005-11-12
I installed OpenSuse 10 on a Compaq n610 laptop and Hibernate worked.  I installed Ubuntu Breezy on the same exact hardware and Hibernate freezes and I have to do a hard reset.  How can I get hibernate to work?  Ideally, I would love to get Sleep or Suspend to RAM working.  Win XP on the same hardware supported all of these features flawlessly.   Help....

---

### Post by strawman on 2005-11-12
First check your /etc/default/acpi-support file and uncomment the following:

```
# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem
```

see how that goes.  I have a nc8000 and suspend still does not function properly, hibernate does.  Keep on trying.:)

---

### Post by oldtappan on 2005-11-12
I made the changes you suggest and ran /etc/acip/sleep.sh.  The system went to sleep but when I press the power button it starts up but the screen is blank.  So I'm half way there. :)  Any more suggestions?

---

### Post by NightVision on 2005-11-14
same here although its a different laptop.  echo 3 > /proc/acpi/sleep then I turn on the fan turns on but no monitor.:(

---

### Post by chele on 2005-11-15
Hibernate seems to work on this nw8000, but it seems slow and clunky, at least in comparision to the suspend that worked smoothly on my old iBook running debian. Difference in the quality of hardware, I guess. x86 is so broken :-)

Under hoary, suspend did not work for this machine, (it suspended but the screen never came back up) I am trying it now under breezy, we will see how it goes...

later, 3 hard reboots later....

:-( no luck, suspend to ram does not resume, or, better said, the lcd does not wake up (lazy bastard).

---

### Post by quietglow on 2005-11-24
I have this same laptop (see my sig!) and hibernate work very well--especially when you have the orinoco driver unloaded before hibernate. I have yet to get suspend to ram working, but I'm messing with it right now and will post if I figure something out.

---

### Post by roberto.pierpaoli on 2005-11-25
Hi guys,

I have got a Compaq Presario R3000Z and I'm experiencing the same thing:

- suspend to disk is ok, but really slow
- suspend to ram apperas to work, but the screen does never wake up

I intend to work on this in the next days ... but I'm afraid that it is a very low level hardware problem, so that only a kernel patch could do something about it ... and I'm not able to produce one :( 

I'll keep in touch, hope that someone will soon be lucky.

---

### Post by lowlymarine on 2005-11-25
I haven't been able to get suspend to work on my Dell Inspiron 9300, either.  Same issue as you guys: LCD won't come back up.

The strange thing is, it works fine on my AVEREATEC 3270 running kubuntu 5.10, and that machine is an utter POS that nothing is fully compatable with (I have the graphics hacked, the wireless has to be connected manually, the battery monitor is largely useless, the USB ports only run at 1.1 speeds most of the time, and the built-in SD card reader is broken).  I have no idea why, frankly.

---

### Post by quietglow on 2005-11-25
I spent some time playing with using a different sleep level (s1 instead of s3 I think?) yesterday, but got not loving. I'm pretty much resigned to the fact that suspend to ram isn't going to work on my machine. Suspend to disk is lots better than simply having to reboot though!

---

### Post by ranf on 2005-11-25
What graphics cards do you guys have?
```
lspci | grep VGA
```

---

### Post by quietglow on 2005-11-25
ati mobile radeon 7500 here

I'm learning to dislike ATI more and more...I'll make my next laptop choice based largely around graphics (since centrino in the main kernel now more or less has us set for wireless)

---

### Post by utcamperj on 2005-11-25
Intel i830 here on a Dell C400.  Same problem; suspend works but video doesn't come back.

---

### Post by quietglow on 2005-11-25
I should clarify: I have the same problem of suspend appearing to work with the exception of a dark screen. I assume I'm also having a video issue. Is this an ATI video issue? Has anyone tried a different driver maybe? Or added the driver to the "remove before suspend" list? I'm gonna mess with it.

---

### Post by iitywygms on 2005-11-25
Hey everyone
I have a Presario 2100, same issue as above.  Suspend to ram is the ONLY thing keeping me from being windblows free.
This is my card
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
Any suggestions?

---

### Post by quietglow on 2005-11-26
So you boot into windows to suspend your computer :-) kidding!

---

### Post by ranf on 2005-11-26
[QUOTE=quietglow]ati mobile radeon 7500 here
[/QUOTE]
In `/etc/default/acpi-support' there is a `radeontool' mentioned:
```
# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

```

I don't know what that is. But I'd search these forums for this.

Aha, it is a package in universe:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=radeontool&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=radeontool&searchon=names&subword=1&version=breezy&release=all)

---

### Post by ranf on 2005-11-26
[QUOTE=utcamperj]Intel i830 here on a Dell C400.  Same problem; suspend works but video doesn't come back.[/QUOTE]
I'd try playing with these settings in `/etc/default/acpi-support':
```

SAVE_VBE_STATE=true
POST_VIDEO=true
DOUBLE_CONSOLE_SWITCH=true

```

---

### Post by iitywygms on 2005-11-27
tried playing with the settings.  Still no video on resume.  I think the keyboard is dead also, at least I cant see any results when pressing keys.  If i could get my laptop to suspend, windblows will be gone.

---

### Post by KoenJ on 2005-11-28
The same problem here on my Acer Travelmate 290 with ATI 9200. Computer reacts, but with a black screen.

---

### Post by quietglow on 2005-11-28
[QUOTE=iitywygms]tried playing with the settings.  Still no video on resume.  I think the keyboard is dead also, at least I cant see any results when pressing keys.  If i could get my laptop to suspend, windblows will be gone.[/QUOTE]

Do you have hibernate working? I've more or less given up on suspend on this machine, but hibernation works perfectly. It takes somewhat less time than rebooting, everything you're doing is saved and it uses no battery while out.

I tend to move around a good bit--especially at work--so suspend would REALLY be nice, though!

---

### Post by iitywygms on 2005-11-28
Yeah i was able to get hibernate to work but the resume time is as long as a full reboot.  With windblows, i close the lid it suspends, when i open it i am back here i left off in 5 seconds.  Oh well, Ubuntu is great in every other aspect, I will just keep reading and hopefully find something.  I hope the next release has the suspend issue solved.

---

### Post by iitywygms on 2005-11-28
[QUOTE=quietglow]ati mobile radeon 7500 here

I'm learning to dislike ATI more and more...I'll make my next laptop choice based largely around graphics (since centrino in the main kernel now more or less has us set for wireless)[/QUOTE]

Has anyone tried a different video driver?  My guess is that the ati card is a big issue.  I dont think my keyboard or mouse is coming back either but I have no way to really know until the video works.

---

### Post by quietglow on 2005-11-28
Yeah, I tried the fglrx driver and the issue is still there.

I've got another thread (asking about the framebuffer) where I try some other stuff. Basically the problem with the Radeon 7500 card seems to be with the framebuffer. I've gone through the process of disabling mine with no joy...I too wish I could get suspend working. I'm coming from mac land...in OSX the desktop is ready to work by the time the lid is all the way open.

But that's what $120 9-month OS release cycle buys you I suppose :-) 

I'm still workin on it and will post any positive results I get.

---

