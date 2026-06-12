---
title: "Not sure if my 4850 driver is working correctly"
date: 2009-04-09
forum: Hardware
---

### Post by AllRadioisDead on 2009-04-09
Hi, this problem has a bit to do with a problem I received when I tried running Halo: Custom Edition in wine.  You can view my post [URL="http://ubuntuforums.org/showthread.php?p=7038849#post7038849"]here.
[/URL] My graphics card is a Radeon HD 4850, and whenever I run anything in wine, I always see this: ```
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
```I don't think this is specific to wine, but with my graphics driver. Video's are a bit choppy, and when I used to run gnome, wobbly windows were also a bit choppy. Whenever I try and install the latest driver from Ati's website, I am presented with a back screen upon login, and I need to reinstall. I am using crunchbang linux 8.10.02 (Basically ubuntu), with openbox. I had my drivers working perfectly in 8.04, would it be a smart decision to downgrade? Help would be appreciated, thank you.

---

### Post by askreet on 2009-04-09
It sounds like you arn't using the ATI Binary driver package.  The default ati/radeon drivers in linux use a minimal set of features and generally don't have true 3D rendering support.

Open a terminal and enter this:
$ glxinfo|grep direct

You should see something like:
direct rendering: Yes

If it says No, or you see nothing, that means you're not using the GLX graphics driver, and true 3D rendering is disabled.

Go to:
System > Administration > Hardware Drivers

You should see a driver for your video card available.

HTH,
askreet

---

### Post by AllRadioisDead on 2009-04-09
Here are my results, sorry for the late response.

---

### Post by AllRadioisDead on 2009-04-10
Bump :(

---

### Post by AllRadioisDead on 2009-04-10
Bump :(

---

