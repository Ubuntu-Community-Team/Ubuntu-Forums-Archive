---
title: "[SOLVED] !!! BIG BIG BIG Problem - I've got no GUI !!!"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by sevenearths on 2008-03-15
I have been messing around with trying to install a driver for my ATI Radeon Xpress M200 on my laptop for the last couple of hours and it's all gone very wrong.

someone recommended downloading and installing this package (envy) to solve my driver problems (which I have just realized after cutting and pasting the URL won't solve squat because it got nvidia in the title)

[http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu7_all.deb]("http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu7_all.deb")

But before I embarked on this mission I removed ATI as my selected driver from the 'restricted driver' window and then uninstalled (sorry... 'complete remove') 'xserver-xorg-video-ati' from synaptic. BAD IDEA!!!!! no I can get a login screen or GUI up... nothing :(

I popped in the ubuntu cd (7.10) and copied across it's xorg.conf file (/etc/X11/) and tried rebooting.

I am thinking if I can reinstall the 'xserver-xorg-video-ati' package from the cd I might get the GUI back (how do I install packages from the CD?)

any ideas of how to get back to a default video driver?



(I really don't want to reinstall the OS again just because of a video driver problem. but if I do will it retain my home directory and other folders I have in the root if I don't select 'format' during the installation?)

...

[sometime later]

I tried re-enabling the ati driver from the restricted drivers window after booting up from the cd... but to no avail... i think it only installs the drivers for the current os, which isn't much help when you are booting from the cd


...

[additional]

I can't get packages from the web because I'm using wirless WAP :(

---

### Post by enfeiris on 2008-03-15
New to Ubuntu, so don't yell at me if I'm wrong, but when I fixed my video resolution, I had Ubuntu regenerate my xorg.conf file.

Try this: 

sudo dpkg-reconfigure -plow xserver-xorg

Then hit CTRL-ALT-BACKSPACE to restart X.

I got these commands from [https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

I hope this solves your problem!

---

### Post by sevenearths on 2008-03-15
I'll try this now - cheers

---

### Post by towelie4365 on 2008-03-15
I just encountered the same problem. I installed the restricted driver (ATI Accelerated graphics driver), and I have no long in screen/ gui. I have a Radeon x800 xl vid card.

---

### Post by sevenearths on 2008-03-15
> **towelie4365 said:**
> I just encountered the same problem. I installed the restricted driver (ATI Accelerated graphics driver), and I have no long in screen/ gui. I have a Radeon x800 xl vid card.

Tell me about... how am i supposed to know what to do on a command line, especially when I've got no web

---

### Post by sevenearths on 2008-03-15
> **enfeiris said:**
> New to Ubuntu, so don't yell at me if I'm wrong, but when I fixed my video resolution, I had Ubuntu regenerate my xorg.conf file.

Try this: 

sudo dpkg-reconfigure -plow xserver-xorg

Then hit CTRL-ALT-BACKSPACE to restart X.

I got these commands from [https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto").

I hope this solves your problem!

Yeah I tried it. The video card ive got (or anything I reconise for that matter) was not in the list, so I installed (video card) for the intel chip set (wise? - you decided!) and for the rest of the stuff I just pressed return. I've got a feeling that this process might have dug me a deeper hole :( I'll probabily get the card up and running but no keyboard of mouse knowing my luck :o

---

### Post by enfeiris on 2008-03-15
Why not try the different video card selections and see if any of them work?  Failing that, you should be able to uninstall the package you installed through synaptic in text-based mode.

I believe the command is sudo apt-get remove xserver-xorg-video-ati.  If I'm wrong, I'm sorry.  Still new to Linux.

---

### Post by sevenearths on 2008-03-15
> **enfeiris said:**
> Why not try the different video card selections and see if any of them work?  Failing that, you should be able to uninstall the package you installed through synaptic in text-based mode.

I believe the command is sudo apt-get uninstall xserver-xorg-video-ati.  If I'm wrong, I'm sorry.  Still new to Linux.

Unfortunatly this whole problem arose because I uninstalled >xserver-xorg-video-ati<. Also If i tryed all the different graphic modes I would be in the command line for a very long time

---

### Post by enfeiris on 2008-03-15
> Also If i tryed all the different graphic modes I would be in the command line for a very long time 

Fair enough.  I don't know what else can be done.  Sorry I can't be more of a help.:(

---

### Post by ugm6hr on 2008-03-15
OK.

Envy works with Nvidia and ATI cards.  So it might be worth trying to install the latest ATI driver using Envy.  However, that does require the laptop to be connected online - which I gather it is not at present.

As a first step - try this again:
```
sudo dpkg-reconfigure xserver-xorg
```

And select the VESA driver.  This should hopefully work, and give you a basic universal graphics driver.

---

### Post by sevenearths on 2008-03-15
> **ugm6hr said:**
> OK.

Envy works with Nvidia and ATI cards.  So it might be worth trying to install the latest ATI driver using Envy.  However, that does require the laptop to be connected online - which I gather it is not at present.

As a first step - try this again:
```
sudo dpkg-reconfigure xserver-xorg
```

And select the VESA driver.  This should hopefully work, and give you a basic universal graphics driver.

I'll try that now. Cheers!

---

### Post by sevenearths on 2008-03-15
Quick update before I try the above

I rebooted and typed the following in to the command line:

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

because I read something like that on the link suggested above:

[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

I got back the following error:

```

fatal server error
no screens found
```

---

### Post by sevenearths on 2008-03-15
> **ugm6hr said:**
> OK.

Envy works with Nvidia and ATI cards.  So it might be worth trying to install the latest ATI driver using Envy.  However, that does require the laptop to be connected online - which I gather it is not at present.

As a first step - try this again:
```
sudo dpkg-reconfigure xserver-xorg
```

And select the VESA driver.  This should hopefully work, and give you a basic universal graphics driver.

Thank you! Thank you! Thank you! I now have a GUI from which I can work :) :) :)

---

### Post by ugm6hr on 2008-03-15
Glad you can *see* your way around Ubuntu again!

I have seen your other post here: [http://ubuntuforums.org/showthread.php?t=722358](http://ubuntuforums.org/showthread.php?t=722358)

Note that VESA driver will not support Compiz-Fusion - you need either:
1. ATI restricted driver and fglrx
or
2. Latest ATI driver (Envy should get it for you) which has AIGLX

I would recommend the latter.

Uninstall fglrx (from Synaptic), then run Envy (as per instructions).

Then reboot (with fingers crossed).

---

### Post by sevenearths on 2008-03-15
> **ugm6hr said:**
> Glad you can *see* your way around Ubuntu again!

I have seen your other post here: [http://ubuntuforums.org/showthread.php?t=722358](http://ubuntuforums.org/showthread.php?t=722358)

Note that VESA driver will not support Compiz-Fusion - you need either:
1. ATI restricted driver and fglrx
or
2. Latest ATI driver (Envy should get it for you) which has AIGLX

I would recommend the latter.

Uninstall fglrx (from Synaptic), then run Envy (as per instructions).

Then reboot (with fingers crossed).

No worries. I managed to find my way back. It's just with out a a working web conection and GUI I'm lost.

---

### Post by sevenearths on 2008-03-18
> **ugm6hr said:**
> Glad you can *see* your way around Ubuntu again!

I have seen your other post here: [http://ubuntuforums.org/showthread.php?t=722358](http://ubuntuforums.org/showthread.php?t=722358)

Note that VESA driver will not support Compiz-Fusion - you need either:
1. ATI restricted driver and fglrx
or
2. Latest ATI driver (Envy should get it for you) which has AIGLX

I would recommend the latter.

Uninstall fglrx (from Synaptic), then run Envy (as per instructions).

Then reboot (with fingers crossed).

I did the same thing again...:sad:

I installed envy and updated my driver but now all my videos play slow (vlc, totem, etc...) So I'm going through the whole thing again, though this time I think I'm going to stick with the one the restricted driver manager recomends

---

