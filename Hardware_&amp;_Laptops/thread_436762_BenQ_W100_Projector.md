---
title: "BenQ W100 Projector"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by Daminator on 2007-05-08
Anyone know the best way to set up my screen to use this projector with Ubuntu?

It's connected via a DVI-D cable and is the only screen attached.

---

### Post by jjordan on 2007-05-08
The short answer is whatever the native resolution of the projector is which a quick Internet search indicates is 854x480.  24 bit color depth and a high refresh rate of 75hz or better is probably important in this case. What video card are you using?  That is going to be a pretty low resolution for most things, are you planning to use this a an HTPC? 

- j

---

### Post by Daminator on 2007-05-08
Thanks for that.

I had that much info, but was wondering how others has set theirs up. I've heard that sending a HD resolution to this projector produces a noticably better image.

Is there an easy way to set resolution option in Ubuntu? Any util I can install to help? I find it very un-user friendly. I found KDE better, but don't really want to mess up all my menu's by installing that on top of Gnome.

This is going to be a HTPC yes. I'm setting up MythTV with it.

I'm using a nVidia 5200 card and am based in the UK (PAL) if that's needed for anyone offering set up advice.

Cheers
Damian

---

### Post by jjordan on 2007-05-08
HDTV resolutions come in several flavors usually referred to by the number of vertical rows.  480p, 720p, 1080i and 1080p.  To get the number of horizontal rows divide by 9 and then multiply by 16.   So, a 480p has a horizontal resolution of 854.  Your projector is a 480p HD display.  Now, the little p indicates progressive and the little i indicates interlaced.  Interlaced means that it displays every odd or even line of the picture every cycle.  Your monitor is capable of displaying 480 progressive and 1080 interlaced.  Those resolutions should look very good.  720i should work but will not look as good.  If the projector will even accept a 1080p input then it is scan converting it internally and once again it probably not look as good.

I use Kubuntu and do most of my video setup by editing the xorg.conf file.  There is a tool called "nvidia-settings" available in the the repositories and you can install it using apt-get or Synaptic.
 I believe that will give you a GUI to adjust the settings.
-j

---

