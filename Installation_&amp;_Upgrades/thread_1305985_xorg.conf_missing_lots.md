---
title: "xorg.conf missing lots"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by crimius on 2009-10-30
Hi.  I just upgraded to 9.10 from 9.04, and decided I would do things the right way (setup a seperate home partition and copy my current home folder over to it).  Install went off without a hitch, and I'm loving how well things have worked so far.  My only issue is my xorg.conf file seemed to have a couple issues, so rather than try and fix them I deleted it and figured I would let Ubuntu rebuild it next time it started, and go from there.  now however, it is a very sparse file:
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection


```
that's it.  I was going to re-enable the dontzap feature, but as you can see, it isn't quite there for me to enable.  any ideas on how to rebuild this aside from manually?

---

### Post by mikewhatever on 2009-10-30
Is there a problem with your xorg? To get dontzap, read Karmic [release announcement]("http://www.ubuntu.com/getubuntu/releasenotes/910#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg,%20configured%20via%20XKB").

---

### Post by crimius on 2009-10-30
it seemed that it should be maybe 3 times the size that it is.  In the last release that was how it was, and I had a script setup to copy one file to my current xorg file to display on an external Gateway monitor (its a laptop), and then switch back to my laptop.  I find that both of these files are now invalid, as I'm assuming it's a new version of xorg.

I can't change my xorg via the nvidia-settings manager, since I'm using the proprietary nvidia driver and it makes sense to change it that way instead of editing it manually.  it errors as i launch the manager
```
unable to assign attribute [attribute here] on line[all lines 21-85] of configuration file '/home/xxxxx/.nvidia-settings-rc'
```
then when I apply the settings with a popup that reads "Failed to parse existing X config file '/etc/X11/xorg.conf'!" and in the terminal
```
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".
Segmentation fault

```

---

### Post by skotos on 2009-11-02
> **mikewhatever said:**
> ... read Karmic [release announcement]("http://www.ubuntu.com/getubuntu/releasenotes/910#Ctrl-Alt-Backspace%20disabled%20by%20default%20in%20Xorg,%20configured%20via%20XKB").

Thank you for the **dontzap** trick

---

