---
title: "No sound, except startup sound in 12.04"
date: 2012-09-05
forum: Hardware
---

### Post by glawton on 2012-09-05
Hello, I'm on a dell inspiron 1520 laptop, and all of a sudden the sound has stopped working. I tried repeatedly restarting, and the startup sound plays on the logon screen, but this is the only sound that will play. 

I'm sure this is not due to it being muted, or other sound settings.

I tried the fixes found here, but no luck. [http://sathyasays.com/2007/12/09/fixing-no-sound-bug-on-dell-inspiron-1520-in-ubuntu-gutsy/](http://sathyasays.com/2007/12/09/fixing-no-sound-bug-on-dell-inspiron-1520-in-ubuntu-gutsy/)

If anyone has any help, I'd be very appreciative. Thanks!

---

### Post by MoebusNet on 2012-09-08
I know you said that this is not due to sound settings, but I noticed that some of the updates changed the output setting for my laptop from "Speakers - Built-In Audio" to "Digital Output (S/PDIF) - Built-In Audio".

In Ubuntu 12.04 with updates, I found that out by right-clicking the Volume Control icon in the upper taskbar right side, selecting "Sound Settings", selecting the "Sound" tab (if required), selecting the "Output" tab and clicking "Speakers - Built-In Audio" under the "Play Sound Through" window. You can test the audio to see if it is working by clicking the "Test" button after making sure the mode is set to "Analog Stereo Output" and the "Output volume" slider is set above the mid-point with the "Mute" box unchecked.

In Ubuntu 10.10, there should be a similar GUI option to confirm audio settings.

Hope this helps :)

---

