---
title: "Xonar Soundcard - no HDMI-sound"
date: 2013-01-06
forum: Hardware
---

### Post by whocares02 on 2013-01-06
I'm running a fresh installation of the newest mythbuntu and have trouble with my asus xonar-soundcard. 

The alsa-driver is working well - but without hdmi-output. I'm using Asus Xonar HDAV 1.3 slim. It has only two outputs: SPDIF and HDMI. Because My PC comes with a front-panel, I could plugin some headphones to check for sound. It is indeed playing but only in poor stereo.  The card was pretty expensive and usually supports 7.1-dts. Headphone-usage is not intended.  

I need sound over HDMI because I'm using the soundcard in an HTPC.

---

### Post by gordintoronto on 2013-01-06
Run Sound Settings and check Hardware, then Output device and connector.

---

### Post by whocares02 on 2013-01-07
No, no it's a driver problem. The hdmi-output is not supported by the driver. I found an[ old threat]("http://ubuntuforums.org/showthread.php?t=1717265") with recommendation to install a new kernel:

> The guy who who wrote the driver for this card had this to say[ in 2009:]("http://www.spinics.net/linux/fedora/alsa-user/msg07956.html")
     Quote:
                                                 The driver supports all hardware features, except HDMI,                                 
However, in January of this year he updated the ALSA database page for [ASUS]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus"), and [changed HDMI status]("http://www.alsa-project.org/main/index.php?title=Matrix:Vendor-Asus&diff=prev&oldid=2264") from "no support" to "untested support" with the kernel 2.6.38. Not a definite answer but it gives you something to try out.

To install the newer kernel see here:
[http://askubuntu.com/questions/30196...nel-with-10-10]("http://askubuntu.com/questions/30196/is-it-possible-to-use-a-2-6-38-kernel-with-10-10")
It's almost two years old and the present kernel is newer than the testing-version from this time, hence this threat. 

In meantime, I'm happy I found out that SPDIF is working and it makes it possible to connect the PC to the Hifi-Receiver to get sound at all. 
Just for watching recordings  on the TV however, this setup is annoying. Without sound over HDMI I always have to power-on the receiver along with the TV to get sound.

---

