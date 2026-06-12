---
title: "USB audio (partly) broken on Toshiba laptop"
date: 2010-01-17
forum: Hardware
---

### Post by gward on 2010-01-17
I'm having a weird problem with USB audio on my 6-year-old Toshiba Satellite M30 laptop.  I've been using this machine quite happily with a Stereo-Link 1200 USB audio device for at least 4 years and many versions of Ubuntu.  It just kept working, upgrade after upgrade ... until the other day.

Now Toshiba + karmic + Stereo-Link does not work anymore.  I've been running karmic since November, so I'm pretty sure that upgrade is not the problem.  And the mode of failure is peculiar: the laptop and kernel still recognize the USB audio device; I get all the usual stuff in /var/log/kern.log when I plug it in, new device files (OSS and ALSA) appear, etc.  In particular, applications can still open the audio device, send audio data to it, and they appear to think that they are playing something.  But nothing comes out.  Also, the little LED that lights up on the Stereo-Link to say "yep, I'm getting an audio signal" no longer lights up.

BTW, I have purged pulseaudio from my system, so any audio apps write to the hardware directly.  I also booted into single-user mode and used command-line apps (aplay, sox, mpg123) to be sure that no extraneous software was getting between me and the audio hardware.

Process of elimination #1: does the Stereo-Link still work?  Yes, just fine, both with my girlfriend's shiny new Mac and with my crappy generic desktop PC (also running karmic).

Process of elimination #2: kernel upgrade?  I first observed the problem with 2.6.31-18, which is fairly recent.  So I rebooted into the oldest kernel still on the laptop, 2.6.31-15: same behaviour.  (This was entirely in single-user mode with command-line players only.)

Process of elimination #3: I happen to have another USB audio device, an Edirol E-100.  So I plugged it in and it works just fine with the laptop.

Any suggestions?  I suppose I should try another operating system on the laptop to be sure that it's not a software problem, but that will be a lot of fuss and bother.  It sure doesn't seem to be a problem with the Stereo-Link itself, since it works fine with two other computers.  (And the fact that one of them is also running karmic is another argument against this being a bug in Ubuntu's kernel.)  If it is a hardware problem with the laptop, it's a very subtle one, since the Stereo-Link is recognized just fine by the kernel, showing up in /dev and so forth.  I'm stumped.

---

