---
title: "[SOLVED] rhythmbox pulseaudio alsa alsa-oss hardy"
date: 2008-07-06
forum: Hardware
---

### Post by FishRCynic on 2008-07-06
After several interesting months of attempting to have a flawless 
hardy installation of Hardy on a toshiba A70 (including a custom dsdt, several upgrades (backup working gusty and install) and several clean installs, following the various & sundry sound fixes etc, I have come to 
the conclusion that rhythmbox/alsa may actually have interrupt issues with ?? (touchpad/mouse devices both usb and ps2? , usb in general? ).
Unfortunately due to the restricted bios on the A70, the actual hardware
cannot be tweaked through the bios.

Sound card atiixp (150) ac97 codec

Totem movie player works fine
under pulseaudio, alsa and alsa-oss sound settings 

so Rhythmbox should work fine too.
Unfortunately under both Pulseaudio and Alsa (and anything other than OSS) a song will play for up to 30 seconds (ranges from 0-30 seconds song independent)and then rhythmbox waits (or hangs basically as it never returns)and has to be forced closed. Interestingly enough with sound set to
OSS - Rhythmbox works albeit with the familiar crackles etc.
 
i had issues in Gutsy with sound, but pulseaudio actually fixed them.

this happens whether Compiz is enabled or not
discrete mouse used or not
wlan (atheros) enabled or not
on battery or on a/c

presently this is not a big issue as the OSS allows me functionality
but i find more than passing strange that the Alsa does not work
directly but through OSS compatibility.

to reiterate i have done the various howto multimedia, sound etc found in
these forums (also tried experimental versions from various other sites)
reinstalled alsa from source, reinstalled alsa from hg  etc no joy

uptodate with latest hardy including proposed

any thoughts would be welcome.

---

### Post by FishRCynic on 2008-07-06
having now installed alsa development version alsa-driver-1.0.17rc3 and associated files - sound is better - however rhythmbox -d yields

[slider_moved_callback] rb-header.c:553: slider is not dragging
to which there is a bug 

i can continually crash rhythmbox playback by holding the mouse button (default left in my case) on another window slider for a period of approx 2-10 seconds. however i do not have to force quit

this behaviour is also exhibited using alsa only i have to force quit

using oss does not do this - the song skips seconds now 


might be related to 
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/228763](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/228763)

---

### Post by FishRCynic on 2008-07-06
being somewhat confused with this
i have installed Audacious

interestingly enough it is exhibiting the same behavior as Rhythmbox
until i enabled "bypass all of signal processing if possible"

so now i use Audacious

guess not - it still can be affected too

---

### Post by FishRCynic on 2008-07-06
i have fixed my issues to some degree

[http://ubuntuforums.org/showthread.php?t=851608](http://ubuntuforums.org/showthread.php?t=851608)

---

