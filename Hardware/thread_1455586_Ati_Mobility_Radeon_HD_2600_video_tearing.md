---
title: "Ati Mobility Radeon HD 2600 video tearing"
date: 2010-04-16
forum: Hardware
---

### Post by Tuchkata on 2010-04-16
Hi. I'm new in forum and comparatively new in Ubuntu. I have an irritating problem with this video card and Ubuntu 9.10 Karmic Koala. The problem is that when I watch video with VLC player or in youtube there is video/screen tearing. You can just ignore it but when you know that there is tearing you just look only at it. I installed the ATI driver from the website and I have Ati Catalyst Control Center and I also installed the fglrx driver which Ubuntu offered me. What I find strange is that when I disable or uninstall all drivers the video is working great but I don't have Compiz and all this stuff. Thanks in advance for your help :) 

P.S. Here is my xorf.conf file :)

---

### Post by Tuchkata on 2010-04-16
Anyone ? Some suggestions ?

---

### Post by Tuchkata on 2010-04-17
*bump*

---

### Post by Tuchkata on 2010-04-17
bummmp

---

### Post by lidex on 2010-04-18
Have you tried disabling compiz (desktop effects) when playing video? Check out this page:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Tuchkata on 2010-04-25
I've disablet Compiz and all desktop effects and put OpenGL Output in Vlc and it works. The problem is that Flash videos sometimes still have this annoying problems. Youtube or stream videos for example Veetlee videos. Any suggestions or has anyone tried ATI 10.3 with Ubuntu 10.04 ? Is it better ?

---

### Post by moviemaniac on 2010-04-25
I have a 2600XT and use the open source driver in lucid - no video tearing, no problems and compiz works too - no need for fglrx ;)

---

### Post by Tuchkata on 2010-04-26
I'll try it for sure when I have time :) Thanks for the advice. And how is Recordmydesktop ? Is it work properly ?

Edit : I installed it. What I find strange is that I don't have anything in my xorg.conf file. I don't have any tearing now but I can't enable compiz as well. Suggestions ?

---

### Post by moviemaniac on 2010-04-26
The xorg.conf is supposed to be empty unless you want one with custom properties - the Xserver doesn't need it anymore ;)

I don't know about recordmydesktop, just try it now that you've installed the driver.

Personally I'd advise against using Compiz if you plan on playing many videos (using the machine as a DVD playback device) - Compiz does tend to also lead to minor tearing - I disabled it on my machine for that very reason.

---

### Post by logan85 on 2010-05-06
you should add this patch...

# Adding a PPA to your Ubuntu system(for knowledge of PPA, see [https://help.launchpad.net/Packaging...tware#Overview](https://help.launchpad.net/Packaging...tware#Overview))
> sudo add-apt-repository ppa:launchpad-weyland/ppa

# then
> sudo apt-get update
> sudo apt-get upgrade

---

### Post by Tuchkata on 2010-05-08
What is this patch about ?

Edit : I've tried it. With compiz enabled it works faster th&#1072;n before I mean the compiz effects but there's still video tearing when I watch videos. Any oder ideas ?

---

### Post by lidex on 2010-05-08
OK. Try this. Open CCSM and go to 'General Options>Display Settings'. **Deselect** 'Detect Refresh Rate' and manually set your rate using the slider. Use whatever your monitor is actually set to now. In your outputs - if not already there - put in your info. Mine is '1680x1050+0+0'. Finally, enable the 'Sync to Vblank' option at the bottom.

---

### Post by Tuchkata on 2010-05-09
The problem is that without compiz effects I still have tearing when I watch Youtube sometimes or online streams. VLC is with OpenGL output and works fine. Any ideas ? Is it better with radeonhd drivers ?

---

### Post by Tuchkata on 2010-05-11
Okay I removed the FGLRX driver and now I'm using the "radeon" driver. There is no tearing, the compiz effects working pretty good, no more lag with recordmydesktop and etc. And of course there is one problem. The 3d games are not working properly but I think it's not a big problem. If there is a fix about it it will be really perfect :) Any ideas ? 

Edit : I already noticed that when I watch video the processor temperature is a little bit high 75-80 Celsius.

---

