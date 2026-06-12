---
title: "Need help with ASUS L1000 series laptop sound"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by Arcadian on 2006-12-04
Hi Everyone,

I hope this is the correct forum, here goes...

I've been using Suse 9.3/10.1 on my Asus L1400B (L1000 series laptop) for quite sometime now & after liking Ubuntu 6.10 Edgy Eft on my desktop decided to take the plunge! :p 

The one big hurdle I've had from the live CD & local install is the sound (the one thing I use my laptop for mainly, a music jukebox!). This worked perfectly under Suse.

What happens is this...
- Boot normally
- Sound at login/greeter screen (the bongos)
- Login & no sound at login banner
- No sound at all until reboot & go back to login greeter

I've been digging through the forums & tried a number of things mentioned but nothing has worked. The sounds DOES work, but only the once. ](*,) 

I've tried all the volume controls (alsamixer too), and enabled everything I can find. I've even changed what I can in the BIOS to no avail.

Here's what I have...

APLAY -L gives me
"**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0"

LSPCI -V gives me 
"00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1493
        Flags: bus master, medium devsel, latency 0, IRQ 4
        I/O ports at e000 [size=256]
        I/O ports at e100 [size=64]

00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: ASUSTeK Computer Inc. Unknown device 1496
        Flags: medium devsel, IRQ 4
        I/O ports at e500 [size=256]
        I/O ports at e600 [size=128]"

LSMOD | GREP SND gives me
"snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm"

Does any Ubuntu wizard have any ideas at all?:confused: 

FYI - I've NEVER been able to get the modem to work (smartlink winmodem rubbish), even under Suse. From memory there was some OSS type conflict with the modem (embedded into the sound card?) that could prevent sound from other apps or the modem itself from working if things weren't done properly. Does that sound right to anyone? Is there any easy way of getting Ubuntu to completely ignore the modem?:-k 

Thanks to anyone who has the time to help me with this. I hope this will help somebody else also.

Yours endebted,
Arcadian

---

### Post by Arcadian on 2006-12-10
Hi Everyone,

Just a quick update. After reading further forum posts I decided to check out what my headphone socket was doing, hey presto, got sound  through there. For some reason the driver/module/alsa/whatever seems to switch sound from the speakers to the headphone jack when I log in. Mighty weird...

I've found some options for the intel8x0 module (ac97_quirk option specifically) that will allow you to play how the headphones are handled (e.g. swap the speakers & headphones around). There are a few options to try, but I should have another update posted tomorrow.

Cheers,
Arcadian.

---

### Post by Arcadian on 2007-01-01
Ah, the update as promised...

Well, I'm so close I can taste it (well hear it!). Here's what I've found...

If I boot up in maintenance mode from the GRUB menu, login as ROOT, run STARTX, I have full sound under X, everything works! :p 

What this tells me, is, that if I bypass the GDM greeter, I have no problems! The question is, what is happening in & around the GDM greeter that's causing my problem. Normally I do have sound in the GDM greeter, but only the once (well, through the speakers anyways, it's all headphones after that). It's almost as if the internal amp is being turned off or bypassed (and there's no mixer setting for that!)

Here's what I've tried & found out so far...
- It's not ALSA, the mixer settings or my hardware. I've run ALSA under SUSE & knoppix before, with no troubles.
- I've updated to ALSA 1.0.13 & still found that it's not the cause. Sound is working perfectly normally. Support for my card has been in since 0.9.6.
- I've tried turning off sound in the GDM/Greeter config, manually & through the GDMSETUP app, no difference.
- I've tried bypassing the GDM prefetch, no change
- I've looked in the var/logs but found nothing strange. Remember, the sound does work, but at such low levels I can only get sound via headphones.

It must be some script or something that's doing something to ALSA/Sound at the time (or conflicting library?). How do I track this down?:confused: 

One last thing to note. If I do my maintenance mode bypass trick, and get into X as root (with sound, yay!), I can run GDM & launch another GDM/X session on another display & **get sound working perfectly!** What the heck is going on here???](*,) 

Another interesting thing, I get a "HAL Error!" when I do this. What is this from?

Can someone tell me where I can find any Ubuntu/GDM startup scripts? This has to be an Ubuntu special issue I have to say..:???: 

Can anyone please help me? I don't want to give up on Ubuntu just yet,,, I'll see if I get sound from the Kubuntu live CD next (Suspect I will),

Cheers all!

Arcadian;)

---

### Post by Arcadian on 2007-01-08
Hi All,

Another minor update. It doesn't seem to be anything to do with the GDM greeter. I've tried Kubuntu & get exactly the same problem. So, I'm now guessing it's something a startup script or service is doing. Other distros like knoppix/suse don't have this problem, so maybe it's an ubuntu special?:-? 

Am going to experiment:-k , but any ideas anyone?

Cheers!

---

### Post by Arcadian on 2007-01-19
Okay, disabled as many startup services & scripts as I could (without breaking anything I wanted) and still had the same issue.

Found one other thing... if I'm at the GDM greeter, I get the bongos to start, if I don't enter any username & press enter I get the bongos again! :eek: 

As soon as I enter a username & hit enter the sound stops.](*,) 

Any ideas anyone? Is there another form of GDM or alternative I could use?

Cheers!

---

### Post by Arcadian on 2007-02-12
*[COLOR="Red"]**NEWSFLASH**[/COLOR]*

Okay, so I gave up, turned to the dark side a bit :evil: and tried out SUSE 10.2 for a while. Sounds, hard disk spin down & just about everything working sweet. Except that it was slow... I missed my [COLOR="SandyBrown"]**Ubuntu**[/COLOR]...:guitar: 

Then I found out Feisty 7.04 RC1 was out and downloaded the i386 desktop ISO in anticipation...\\:D/ 

Only to find that it had exactly the same problem.. #-o 

But then I started playing around & noticed that the new GNOME had a slightly different services control applet. I started turning things off once again, until I got something that actually [COLOR="Lime"]**friggin worked!**[/COLOR]

In the end I found that if I disabled **ACPID**, and put all other services back to normal, I had working ***SOUND!!! *** All that was left was the battery/suspend/powersave features. (BTW the sound always worked, something just changed it to headphone level loud during startup!)

I then found out that if I re-enabled the **ACPID** service I could actually have **BOTH** running at the same time. :popcorn: Sound out of my speakers!

Huzzah! :cool: 

It turns out in the case of my ASUS L1000B laptop, delaying the ACPID service startup may be the answer! All I have to do know is find a setting that works (and how to do it).

Does [COLOR="Cyan"]*ANYONE*[/COLOR] have even the faintest idea why ACPID powersave daemon may be making my sound card only good for headphones?:-k 

I've seen numerous posts on sound issues like this, where only headphones give you sound. If this is you, perhaps try disabling ACPID to see if that brings you any joy.

I'll post my findings once I find out how to get things playing together nicely!

Good luck one & all ):P 

P.s. As I said, I'm now running 7.04 RC1. Great work team UBUNTU! I you haven't already had a nosey, I highly recommend it. It is a release candidate though, so be careful!

---

### Post by Arcadian on 2007-02-15
Okay, I'll be honest (and just a little bit smug:tongue: ), *[COLOR="Lime"][SIZE="3"]**I'm a LEGEND!**[/SIZE][/COLOR]* :guitar: 

For a guy who's turned from the dark side (yes, I have an [COLOR="Red"]MCSE[/COLOR]:twisted: ), I'm doin' damn well!

I've just figured it out, I hope this helps many of you out there with similar issues!

If you are having low sound output (headphones only, or none), and find that disabling ACPI (either the service or using the ACPI=off kernel option) fixes the sound but then kills all your powersave features (like ME), give **[SIZE="3"]*this*[/SIZE]** a try...

[LIST=1]
[*]Edit the file /etc/default/acpid as root (e.g. sudo gedit /etc/default/acpid)
[*]You should see a line with MODULES="all" at the bottom
[*]Put a # in front of it to comment it out
[*]There's a line further up with #MODULES="battery ac processor button fan thermal"
[*]Remove the # in front to uncomment it
[*]Save the file & reboot (make sure ACPID service is enabled again, ACPI=off option removed)
[/LIST]

(apologies, I'll post up the actual file once I get wireless sorted on the laptop, have only just started with feisty)

If this works for you, I'm so pleased! =P~ 

What I found earlier is that if I run the ACPID service manually after everything else had started, I had sound & powersave features. When the service is started automatically, for some reason, it would be different.

Tracking everything back (through numerous posts) I find there are all manor of scripts being run at startup, in /etc/init.d. The file /etc/init.d/acpid has a link to the file /etc/default/acpid which is included as a startup parameter for the ACPID service/daemon. 

When I looked in this file I noticed the 2 MODULES lines, one saying "all" the other being more specific. I obviously guessed correctly :idea: that this is likely to load a module that *may* be incompatible with my hardware & do something wrong. Once I swapped the MODULES options around, I was staggered to find that I was absolutely spot on. Not only that, but everything (suspend etc) all worked as expected!

[COLOR="Orange"]PHEW![/COLOR]:lolflag: 

If you find that this works for you, please let me know. From what I've read in researching this problem, it is common (and not just restricted to Ubuntu to be fair). Having said that, I seriously recommend that Ubuntu/Debian revisit using the MODULES="all" option.

Apart from that, Ubuntu is indeed the "[_[COLOR="RoyalBlue"]king of distros[/COLOR]_]("http://www.osnews.com/story.php?news_id=16681")" and [COLOR="DarkOrchid"]Feisty *ROCKS!*[/COLOR] :cool: 

Good luck!

---

### Post by Vermind on 2007-08-27
Hello,
Thanks, this seems to have solved my excessively weird problem on a recently Feistified originally Edgy laptop.
The nature of the problem was that every time the laptop was booted without the AC cable plugged in, all sound was 20% slower than usual, and the pitch was affected proportionally. It was interesting listening to Enya sounding almost like a man...
So I figured it had something to do with power management, and at some point stumbled on this thread.
Loading only the few ACPI modules I need was the solution (I think).
I also removed laptop-mode (not laptop-mode-tools) and laptop-net (since NetworkManager does its work very well anyway).

The laptop is a Pentium 4 2.4Ghz with 1G of memory and a shared-memory ATI Mobility 9200 (RV250) with integrated sound using the intel8x0 driver.

Anyway,
Thanks.
--
Vermind

---

