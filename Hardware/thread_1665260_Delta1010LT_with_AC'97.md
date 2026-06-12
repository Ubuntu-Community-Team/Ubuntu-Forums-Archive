---
title: "Delta1010LT with AC'97"
date: 2011-01-12
forum: Hardware
---

### Post by mmartoncik on 2011-01-12
I'm an oldschool linux slackware user just geting back into it after installing Win7 and realizing that either the new releases are getting more and more wack or theyre just passing me by, i decided to go back to the command prompt.  After installing Unbuntu 10.10 I was impressed at how far the gnunix has come.  However I am a musician and need my soundcard to work [Delta1010lt].  I see that it is being picked up by the resident driver, but it is not working at all.  I have an AC'97 Sound card that I would like to use as well (they have different applications and my studio monitors dont plug into them lol)  Ive seen a bunch of fixes for this by disabling the AC'97 in the BIOS, but that will not work because I use XP on another HD and dont want to change the BIOS for each boot.  Is there a way to get these both going?  FYI: I have both Jack and PulseAudio installed :)  any help would be appreciated!

---

### Post by cchhrriiss121212 on 2011-01-12
The delta line requires a fix in order for it to work with pulse:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

If I were you, I would leave the onboard as my regular sound card, and the delta as a production only sound card using jack.
If you just want to use it with jack then you only need to select it as the interface in qjackctl setup, then raise the volume levels using the analogue volume tab of envy24control. If you want a multitrack recorder then take a look at Qtractor.

Note that jack does not have native support for multiple soundcards. This program was designed as a workaround:
[http://manpages.ubuntu.com/manpages/lucid/man1/alsa_in.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/alsa_in.1.html)

---

