---
title: "Upgrade 8.04 - 9.04"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by gmoreno on 2009-04-29
I upgraded to 8.10 and that worked well...

Now that I've upgraded to 9.04 X does not work.  It boots up to a scrambled mess..

I've started my box in recovery mode and tried xfix with no luck.  

I then did apt-get install --reinstall xserver-xorg.. No luck.

I've tried failsafe xorg config ...no luck

Anyone have any ideas?  I'm running Ubuntu ona HP NC6000.

TIA

---

### Post by prshah on 2009-04-29
> **gmoreno said:**
> It boots up to a scrambled mess..

I'm using the Intel 945, and though I had some [similar troubles]("http://ubuntuforums.org/showpost.php?p=7132514&postcount=2") I was able to set it right by manually specifying the settings in xorg.conf (details in linked post).

This is not really a good solution, since ubuntu is moving away from dependence on xorg.conf (and other such static files), but in the absence of any other suitable tools (like displayconfig-gtk in Hardy), this seems to be the only recourse when using hardware that does not follow specifications (such as VESA) properly.

With Jaunty onwards, a new acceleration method has debuted for Intel chipsets, called UXA/DRI2; maybe enabling that will help; post back for details if the above solution does not work.

If the linked solution does not work out for you, please post back the following output: Open a terminal (Applications-Accessories-Terminal) and give the commands```
cat /var/log/Xorg.0.log | grep -E -i driver\|accel

```

---

### Post by gmoreno on 2009-04-29
I tried:
```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection      "Display"
                Modes   "1024x768@60"
        EndSubSection
EndSection
```

With same results.

I'm using:

VESA chipsets,  Not sure if that's what I was using before the upgrade or not.

---

### Post by prshah on 2009-04-30
> **gmoreno said:**
> I tried:
```

                Modes   "1024x768@60"

```
With same results.

VESA chipsets,  Not sure if that's what I was using before the upgrade or not.

If you are using the VESA driver, then you need to change to the correct driver. From the specs, it looks like you have the ATI mobility Radeon graphics controller; unfortunately, I don't know how to enable this driver.

Maybe someone else can jump in? A bump may be a good idea.

---

