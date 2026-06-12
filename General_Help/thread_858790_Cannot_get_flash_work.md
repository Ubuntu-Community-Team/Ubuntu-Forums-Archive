---
title: "Cannot get flash work"
date: 2008-07-13
forum: General Help
---

### Post by Nexusx6 on 2008-07-13
Hello,

I've been at it for days - literally. When I first installed Kubuntu Hardy I had followed the directions [here]("http://ubuntuforums.org/showthread.php?t=766683") and for a time flash worked alright. I was having problems with Pulseaudio though, and while trying to get it working, I had installed Flash v10, the beta. Once I did that, instead of having weird sound issues with Flash, I lost flash completely and I can't get it back. You can imagine how inconvenient it is browsing the internet without a flash player/plugin :(

Does anyone have suggestions? I've got it to the point where I can "play" flash video's, but no sound or picture will come out.. just a black box with the elapsed time counter moving . . .

---

### Post by alsamman on 2008-07-13
I fixed my flash problems by doing what is told on this site:
[http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html](http://www.ubuntugeek.com/fix-for-firefox-crashes-on-flash-contents-when-using-libflashsupport-in-hardy.html)

try it out and see what happens

---

### Post by SlalomMan on 2008-07-14
I've had problems with sound in flash, and I've found that my issue is conflicting sound apps. For instance, when RhythmBox or VLC is playing, flash in firefox won't have any sound. I have to close RhythmBox or whatever other app and then relaunch firefox to get sound. And I'm pretty sure that it works the other way, too. If flash is open in firefox, rhythmbox won't play. I haven't found a workaround to this, though.

If that doesn't help, I went into sound options and switched from ALSA to PulseAudio, try it, it may work.

---

