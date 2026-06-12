---
title: "Audio/video problems with IBM ThinkCentre MT-M 8187-F4F"
date: 2014-02-06
forum: Hardware
---

### Post by deadfraggle on 2014-02-06
This PC has a pentium 4 processor and 1 gb of memory.  It also has internal speakers which functioned in XP. The installation of Ubuntu 12.04 and updates completed without a hitch, and for the most part the OS runs smoothly.  However, flash video is scrambled and split, and audio is not enabled (though there is an audio control icon.)  I tried reinstalling flash, and installed the restricted extras, but it did not solve anything.

I'm guessing I am in need of proper drivers, though I'm not sure where to find the windows versions.  The MT-M 8187-F4F is not something listed at Lenovo's website.  If I did find them, would they be compatible with Ubuntu, and is there a general guide somewhere that explains how to install them?

---

### Post by sudodus on 2014-02-06
I have a similar Thinkcentre, and the following tweak improved the graphics with version 13.10. I have no problems with 12.04 LTS. You can always try it :-)

> John Hupp <lubuntu@prpcompany.com> wrote:

There was this helpful bug report on file at [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982).

It described behavior on Dell PC's with integrated Intel graphics, in which Adobe Flash Player would display only with shades of purple and green in a horizontally compressed window (or at least that's how I would describe what I see on a Dell Dimension 2400).

The work-around (Comment #1) was to change the Xorg acceleration method to UXA. 

User reported a work-around:

-o-

Edit (or create) [FONT=courier new]**/etc/X11/xorg.conf **[/FONT]as follows: (ugh, can't format, should be a tab before each line except the first and the last).

```

Section "Device"
            Identifier "Intel Graphics"
            Driver "intel"
        Option "AccelMethod" "uxa"
EndSection

```
Restart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

-o-

I forgot to include, however, that the bug workaround messes up the login screen (LightDM).  You can make out an entry box that one assumes is for the password entry, but everything else is largely unidentifiable.

So as a workaround it leaves a lot to be desired, unless we can also figure out how to fix the login screen.


This method works for me to restore good graphics in an old IBM Thinkcentre with Lubuntu Saucy alpha-2 and the following Intel graphics.

VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

There is no issue with the login screen.[/QUOTE]

---

### Post by deadfraggle on 2014-02-06
Beautiful!  That fixed the problem with flash.  Thank you!  

Now for the audio.  Will it help if I open the unit and find out model number of the mothterboard, and use that to determine which audio chipset it is using?

---

### Post by sudodus on 2014-02-06
Opening the unit and checking what is written is one method, but you can also use software, try

```
sudo lshw
``` and*** hardinfo*** to get information about the audio system.

I don't know much about it, but if you post specs about the audio system, chances are that someone else will chip in and help you.

---

### Post by deadfraggle on 2014-02-06
Nice.  It's in French but I think it has the required info:

```
*-multimedia
             description: Multimedia audio controller
             produit: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             fabriquant: Intel Corporation
             identifiant matériel: 1f.5
             information bus: pci@0000:00:1f.5
             version: 02
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             ressources: irq:17 portE/S:1c00(taille=256) portE/S:18c0(taille=64) mémoire:e8080c00-e8080dff mémoire:e8080800-e80808ff
```

---

### Post by sudodus on 2014-02-07
I have only a general tip: Use ***pulseaudio*** and ***pavucontrol***. Install them if you don't have them already. Use the graphical interface of pavucontrol to test all possible combinations of settings while running some audio file. Finally you might find what settings that work.

Otherwise, let us hope that someone else will chip in and help you. Someone who knows more about audio.

---

### Post by deadfraggle on 2014-02-07
You are awesome!  That did it.  Thank you.

---

### Post by sudodus on 2014-02-07
You are welcome and congratulations :KS

---

### Post by deadfraggle on 2014-02-07
I really think it's the best option for the client's PC.  XP is too vulnerable to malware, and MS is ending support for it in April.  Ubuntu extends it's life and gives her kids a something nice to play with.

---

