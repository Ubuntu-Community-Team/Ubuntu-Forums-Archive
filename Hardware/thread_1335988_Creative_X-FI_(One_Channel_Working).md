---
title: "Creative X-FI (One Channel Working)"
date: 2009-11-24
forum: Hardware
---

### Post by sfrappier on 2009-11-24
Hello everyone:

I have a Creative XFI on my computer and I'm noticing an issue - basically I only get sound out of one channel.

When doing soundtest and checking "Front Left" it's silent, and then with "Front Right" it states it.

I have done a default installation with the only change to add flash to the 64bit platform.  I'm using the Optical out from the Creative Labs drive station to an external amplifier.  I changed the sound to Digital Output device in the sound settings but I'm still not having any luck.

Does anyone know of this issue and how to resolve it?  It does work in Windows 7 without issues.

Thanks!

- Scott

---

### Post by linds2009 on 2009-11-24
I have also encountered the same problem
This is a bad phenomenon

---

### Post by sfrappier on 2009-11-25
*BUMP*
 
Am I just out of luck - I really wanted to possibly use Ubuntu as my primary OS (using VMWare as well) but this kind of makes it impossible to do so...

---

### Post by sfrappier on 2009-11-25
Also note:

When I run "speaker-test -Dplughw:0,0 -c2" I can get left and right sounds - is there a configuration file that I need to change by chance?

- Scott

---

### Post by sfrappier on 2009-11-25
Fixed it! :)

What I did:

1.) Manually installed the ALSA 1.0.21 base ([http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)) - outdated but worked.
2.) Edited the "daemon.conf" file located in /etc/pulse so that it had the following uncommented:
[I]
# # #
default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 2[/I]
# # #

3.) Went into the dreaded default.pa file in the /etc/pulse directory.  Added the following line:

# # #
[I]### Scott Frappier Manual Edit
load-module module-alsa-sink device=hw:0 channels=5 channel_map=front-left,front-right,rear-left,rear-right,lfe
[/I]# # #

4.) Killed the pulseaudio daemon and let it restart

# # #
*sudo kilall pulseaudio*
# # #

Now I'm enjoying audio with now issues - not a fun thing to tackle (sorry - Windows is way easier to do this with) but none-the-less it now works.

- Scott

---

