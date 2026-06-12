---
title: "The great OSS dilema!!!!"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by corepusher on 2005-07-26
First of all I want to start saying that Im a newbie in what Ubuntu sound config refers. I have no sound at all in my computer neither from the web. My OSS device seems to be malfunctioning. Whenever I try to start Totem It will display this message "the OSS device is already in use by other app... bla bla bla" and of course I've checked out that NO OTHER APP is using it!!!!.
In my several researchs looking for a solution to my problem I could actually configure Beep Media Player and XMMS to play Mp3 files but from alsa. Eventhough whenever an mp3 is not playing, I can hear this background sound, it is like if you were hitting a steel pipe with a stone repeatedly and it wont go off until you turn down the computer.

PLEASE I NEED SOMEONE TO HELP ME!!!!!! IM ALMOST IN THE EDGE OF MADNESS!!! I NEED TO FIX THIS SOUND PROBLEM QUICK!!! I CANT STAND IT ANYMORE!!!!

I want to know what is really happening and how can I fix it!!!!
if you want more details just ask...

thanks.

---

### Post by varunus on 2005-07-26
Can you post the output of the following in a terminal:

lspci

lsmod | grep snd

This will let us know what sound card you have and what drivers are being loaded for it.

Ubuntu should not be using OSS for sound; Ubuntu uses ALSA (the advanced linux sound architecture) to provide sound.  Try installing the package "libesd-alsa0" from synaptic; it might fix some of your problems.

Also, head over to [www.ubuntuguide.org](www.ubuntuguide.org) and try this howto out, it might help you...
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

---

