---
title: "Matrox G200EH on 14.04"
date: 2014-05-06
forum: Hardware
---

### Post by Jason_Canup on 2014-05-06
Hi all-

Im having some issues with an HP Proliant GL320 G* server with a Matrox g200eh graphics card.  Ubuntu just runs horribly on it.  Every window that I open just lags while opening.  I've already tried to to turn off window animation using Unity, but Unity doesnt seem to apply any changes that I make.  Ubuntu is practically unusable at this point.

Any ideas?

---

### Post by ibjsb4 on 2014-05-06
Try running a different desktop.  Flashback
```
sudo apt-get install gnome-session-flashback
```
Reboot and at the login window click on the icon and  choose 'flashback (metacity)'

---

### Post by Jason_Canup on 2014-05-08
That did the trick.  Thanks!

---

### Post by ibjsb4 on 2014-05-08
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by jason88 on 2014-05-28
> **Jason_Canup said:**
> That did the trick.  Thanks!

It didn't work for me.  I'm trying to get 14.04 working on a Supermicro X9DRW-iTPF and switching to XFCE or Gnome helps greatly, but windows are choppy and sluggish when dragging them.  

I have two identical boxes running 12.04 and they're much snappier.

---

### Post by andromalius on 2014-07-22
Hi! You could try to force vesa driver in the xorg.conf

/etc/X11/xorg.conf :

```

Section "Device"
        Identifier "Matrox Graphics, Inc. MGA G200EV"
        Driver "vesa"
        Option "OldDmaInit" "True"
EndSection

Section "Monitor"
        Identifier "PlugAndPlay"
        Option "DPMS"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "Matrox Graphics, Inc. MGA G200EV"
 Monitor "PlugAndPlay"
 DefaultDepth 24
 SubSection "Display"
            Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```

---

### Post by sleepyhollows on 2014-09-15
> **andromalius said:**
> Hi! You could try to force vesa driver in the xorg.conf

/etc/X11/xorg.conf :

```

Section "Device"
        Identifier "Matrox Graphics, Inc. MGA G200EV"
        Driver "vesa"
        Option "OldDmaInit" "True"
EndSection

Section "Monitor"
        Identifier "PlugAndPlay"
        Option "DPMS"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Device "Matrox Graphics, Inc. MGA G200EV"
 Monitor "PlugAndPlay"
 DefaultDepth 24
 SubSection "Display"
            Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection
```


I looked high and low for this solution. Changing colour depth, running X -configure, completley breaking ubuntu in the process, etc.

This is THE fix for linux on HP servers.

Shame on HP. The video sux under windows too (VNC type remote control solutions are sluggish and bog the whole system down)

---

