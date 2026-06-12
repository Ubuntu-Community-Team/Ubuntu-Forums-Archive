---
title: "NVIDIA GeForce4 440 on an oldish laptop - driver problem"
date: 2008-06-28
forum: Hardware
---

### Post by azangru on 2008-06-28
Hi! I know there've been tons of such questions, but people tend to think that their questions are unique, and I am no exception. So here's the deal.

I'm very new to Ubuntu and to Linux in general. The very first time I installed Ubuntu 8.04 with Wubi and tried to enable desktop effects, I became aware that I had to install a proprietary NVIDIA driver. I let Ubuntu install the driver as it saw fit. I believe it was just enabling this driver:

[IMG]http://farm4.static.flickr.com/3008/2619148722_491da15fa9_o.png[/IMG]

Anyway, I was instructed to restart my computer, and during the boot-up the screen just whitened out. Sound familiar, right?

Since I had no clue what to do next and couldn't use the system without the working GUI, I had to reinstall Ubuntu. Now I summoned all my courage and am ready to try again, only this time I want to do it the right way. Can you please advise **how do I install the driver for NVIDIA GeForce4 440 on Ubuntu 8.04** and, importantly, if things go wrong and the X doesn't start, **how do I roll back to a working system**?

P.S. I watched [this screencast]("http://www.youtube.com/watch?v=HpcAbSviAwU") on YouTube. Perhaps I need not to let Ubuntu enable the driver it sees fit, but to specifically install one of the legacy drivers, since GeForce 4th series is rather old?

Please help! It's so upsetting to know that the 32 megs of the video card are not in use!

---

### Post by overdrank on 2008-06-28
HI and I have not used Wubi for installation but if you install the restricted drivers and get the white screen then you can try the key ctrl, alt, F1 and this will bring you to the command prompt. Login and then you can reconfigure your xorg and hopefully get back to the GUI. Use this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If this fails then when you boot the system and can choose window or Ubuntu highlight Ubuntu and press the esp key and it should give you more options to boot and choose recovery mode and use xfix to correct the issue.

---

### Post by azangru on 2008-06-28
Thanks very much for your advice. Perhaps you could always suggest which NVIDIA driver I should install? Because when I entered "nvidia" in apt-get's search field it returned several options, none of which seems specifically tailored for GeForce4. The info for the newest driver (highlighted on the screenshot) tells that I might need the nvidia.glx package. What is this package and how do I get it?

[IMG]http://farm4.static.flickr.com/3292/2618891223_0702e8191a_o.jpg[/IMG]

---

### Post by overdrank on 2008-06-28
Hi and i have never used add and remove for installing the nvidia drivers. The restricted drivers have always worked for me under system, administration.:)

---

### Post by azangru on 2008-06-29
OK, just wanted to report that I *did* manage to install the nVidia driver following this [awesome how-to]("http://blog.freshnewpage.com/2008/04/26/nvidia-geforce4-420-go-on-ubuntu-804-hardy-heron/"), so everything is good except my Totem Player now refuses to work :(. But I guess it's another story...

---

### Post by forger on 2008-06-29
> **azangru said:**
> OK, just wanted to report that I *did* manage to install the nVidia driver following this [awesome how-to]("http://blog.freshnewpage.com/2008/04/26/nvidia-geforce4-420-go-on-ubuntu-804-hardy-heron/"), so everything is good except my Totem Player now refuses to work :(. But I guess it's another story...

Maybe you have to disable desktop effects: System > Preferences > Appearance > Desktop effects > None

Also, it could be missing codecs. Enable software sources, such as universe and multiverse (System > Administration > Software sources)
Reload the repositories, and install/reinstall the following codecs:
> sudo apt-get install --reinstall lame vorbis-tools flac ffmpeg liblame0 gstreamer0.10-plugins-bad gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse libdvdread3 gstreamer0.10-x gstreamer0.10-fluendo-mp3

You might also want to install w32codecs or w64codecs from [www.medibuntu.org](www.medibuntu.org)

---

### Post by azangru on 2008-06-30
> **forger said:**
> Maybe you have to disable desktop effects: System > Preferences > Appearance > Desktop effects > None

Yep, that was precisely the issue. I was amazed to learn that I went through all that trouble to enable Compiz - and it screwed up the Totem player. Luckily, I found [this solution]("http://ubuntuforums.org/showthread.php?t=398121"). It helped.

---

