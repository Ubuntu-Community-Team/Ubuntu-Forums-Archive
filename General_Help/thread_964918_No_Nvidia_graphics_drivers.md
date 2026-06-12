---
title: "No Nvidia graphics drivers"
date: 2008-10-31
forum: General Help
---

### Post by Russty of Oz on 2008-10-31
I have just upgraded from 8.04 to 8.10 but I don't have any graphics drivers in use.  I have tried installing all the different variants in Synaptic from 93 to 177 but nothing shows up in the Hardware Drivers section.  How do I get my Nvidia MX440 to work properly?

Also, in my boot list it is still showing as 8.04, is there any way I can update this?

Russty

---

### Post by AdrianVeidt on 2008-10-31
Due to changes in the X server, Nvidia hardware prior to the GeForce 5k series is currently not supported by the Nvidia binary driver in Intrepid. However, Nvidia has a few days ago released updated drivers for your hardware, and they will be added to Intrepid soon.

---

### Post by Russty of Oz on 2008-10-31
Thanks for the info, at least knowing that something will eventually be done makes me feel better. At least I can still use it at the moment.

Russty.

---

### Post by shane19174 on 2008-10-31
In the meantime, you can always test the beta legacy driver, which you can download from nvidia here: [http://www.nvnews.net/vbulletin/showthread.php?t=122139]("http://www.nvnews.net/vbulletin/showthread.php?t=122139")

---

### Post by zeiz on 2008-10-31
Thanks! I have GeForce3-Ti200 (nvidia 96xx) that perfectly serves everything I need except latest extreme games (I can live without it :). 
I am in doubts ... should I upgrade, since Ubuntu is my work OS.
Does new driver support my card? 

So far I upgraded Kubuntu, it runs so-so (notable X-problems) and didn't find Firefox in it again. Konqueror is great but not recognized by some sites :(  
Why Kubuntu ignores Firefox?

Update. The site above is great. Almost all nvidia cards are supported.
the beta driver provides not everything but now my desktop is stable though startup screen shows red "failed" against nvidia driver and then hardware applet shows "No proprietary drivers installed". However nvidia-setting is working and shows desirable configuration. Thanks again, shane19174!

---

### Post by Glugglug on 2008-10-31
I installed 8.10 yesterday got the nvidia drivers  I used 177 (recommended)
al worked fine . This morning I plugged in a serial modem and broke something  .so had to do a reinstall and now I can't get the drivers back.

I have ticked the third party software box  in  Software sources if that makes any difference.

---

### Post by Sponzenbroekske on 2008-10-31
```
sudo apt-get install envyng-core envyng-qt
```

For installing nVidia drivers and ATI drivers if they are available.

To launch the app in a GUI
```
envyng -k
```

---

### Post by shane19174 on 2008-11-01
I don't believe envy is finding the legacy beta drivers yet, is it? As far as I know, a manual installation is still required for the 71 and 96 series drivers. Correct me if I'm wrong, though.

---

### Post by Russty of Oz on 2008-11-03
I am trying to install the Beta drivers but it keeps telling me it has to be run as root.  I have tried doing sudo then the file location but it wont work.  How is this done?

---

### Post by shane19174 on 2008-11-03
Short answer:

do a CTRL-ALT+F1 and type the following after logging in:

```
sudo /etc/init.d/gdm stop
```

Then, assuming you're in the directory with the downloaded driver:

```
sudo sh <insert the full name of the driver here, or type "NVIDIA" (without quotes), followed by the TAB key to complete the name, which should end with .run>
```

Answer yes to all and when finished restart.

The long answer: Read [here]("https://help.ubuntu.com/community/NvidiaManual").

Hope this helps.

---

