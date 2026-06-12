---
title: "Lost Sound and Monitor Detection"
date: 2009-07-01
forum: Hardware
---

### Post by HDTimeshifter on 2009-07-01
I lost sound a week or so ago.  I tried rebooting several times with no help.

When I rebooted yesterday, my system no longer recognizes the monitor.  When this used to happen, another reboot would usually recognize the monitor and I could reset to high resolution 1600x1200 through nVidia XServer settings, but now it won't no matter how many times I reboot.  The highest resolution available under the generic CRT is 1152something.

I think I can manually edit the XServer settings file to set it back to default (I think I did that some time ago), to restore the video, but I've never had the sound fail on me like this.  In the past it was only Flash 10, but now I get no sound even through the alsa sound control panel test does nothing but a faint higher pitch whine.

I'm running the latest version (upgraded a couple of months ago to 9.04 and just installed the latest updates this morning with no help).
64-bit Ubuntu
ASUS P5Q Pro motherboard
ASUS EN9500GT nVidia video card
Gateway 21" CRT

---

### Post by HDTimeshifter on 2009-07-02
Anybody have a clue?

I can live without sound for a while, but the low resolution makes it nearly impossible to read mail.

---

### Post by HDTimeshifter on 2009-07-04
Fixed the video by shutting down completely and rebooting twice.

I hooked up my speakers from my Windoze PC to make sure the speakers weren't blown, and played a music CD and can just barely hear the music when I crank the volume to max.  Maybe it's a line level issue?  I'm just using the front out analog output from the onboard audio into a 2.1 system.

Anybody know how to take a screen snapshot in Ubuntu?  I would post my sound control panel settings, but here is what they are set to:
Sound Events
  Sound Playback:  Autodetect
Music and Movies
  Sound Playback:  ALSA

I tried testing with various settings and none worked any better.  There is no volume level adjustment in the control panel.  The only way I have is through the speaker system hardware volume control.

---

