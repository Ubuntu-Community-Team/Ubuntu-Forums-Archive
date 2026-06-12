---
title: "[SOLVED] Volume buttons have stopped working - HELP"
date: 2008-10-22
forum: General Help
---

### Post by callMeTom on 2008-10-22
This has been going on for a while, but only now have I gotten around to asking about it. When I push any of the volume buttons (up, down, mute) the on screen graphic responds correctly, however my volume does not change. When I change the slider in either the applet in Gnome or in the full on mixer in Gnome the volume does change. I am running 8.10 which is probably part of the problem but have all the current upgrades. I would appreciate any suggestions on this topic. My thought is that the buttons aren't set to control the correct channel in the mixer, but I don't know how to check that or change it. Thanks.

-Tom

---

### Post by skintythe1andonly on 2008-10-22
What harware are you using? Is it a HP laptop? I had similar problems with my HP dv2000. I basically hacked around in the Sound preferences until it worked (btw im using hardy). I got mine only to work when sound, music and moveis playback was set to ALSA. Audio conferencing was set to CONEXANT Analong. The Default mixer track was set to HDA NVidia....only then would my volume buttons work. The sound would play before but the buttons or the control in rhythmbox wouldnt work. Hope this helps....prob not if your using different hardware.

---

### Post by iheartubuntu on 2008-10-22
Are you getting any error messages like I am here...

[http://ubuntuforums.org/showthread.php?t=955679](http://ubuntuforums.org/showthread.php?t=955679)

or does your desktop now look like this?...

[http://ubuntuforums.org/showthread.php?t=955472](http://ubuntuforums.org/showthread.php?t=955472)

---

### Post by callMeTom on 2008-10-23
Thanks to all who responded. Turns out I just needed to play around with controls and pay close attention to things that looked right but weren't. On an update the mixer to control was set to input rather than output master. Looked right since it was set to master, but still wrong. I appreciate everyone's responses. 

-Tom

---

