---
title: "Can't disable mouse clicks with touchpad"
date: 2008-08-18
forum: General Help
---

### Post by mfrag on 2008-08-18
Howdy,

I've been unable to disable the mouse click feature on my touchpad when using a different window manager.  I can disable it just fine in a gnome session but when I use ratpoison it appears to stay functional.  I'm a command line only kind of guy and do most of my work with xterm alone.  However, I do run firefox to browse the web and when I open up firefox while in a ratposion session, the touchpad keeps thinking I'm trying to click on things when I'm not.  I ran gnome-mouse-properties from the command line and it tells me the mouse click feature is disabled, but it isn't.  Anybody got any ideas?  

Quite ironic I'm looking for help with mouse problems while I'm using ratpoison, huh.  :)

Thanks for any help.

mfrag

---

### Post by squaregoldfish on 2008-08-18
I you like messing with your config files, have a look in your xorg.conf file. There should be a section with the line:

```
Identifier "Synaptics"
```

Add the following line to this section, and the click will be disabled:

```
Option "MaxTapTime" "0"
```

If you'd prefer a GUI for this stuff, you can try GSynaptics ([http://gsynaptics.sourceforge.jp/]("http://gsynaptics.sourceforge.jp/")). I haven't tried it myself, but it looks like the sort of thing that would work.

Steve.

---

### Post by mfrag on 2008-08-21
Worked like a charm!  Thanks for your help.  The file 

```

/etc/X11/xorg.conf

```

looked like this:

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

```

and I added:

```

        Option          "MaxTapTime"            "0"

```

just before EndSection.

Again, thanks.

mfrag

---

### Post by sporkubus on 2008-10-30
So I tried this and my mouse clicks are STILL not disabled. I feel like I've tried everything... any ideas?

---

### Post by roger_1960 on 2008-10-30
Hi

Thanks squaregoldfish, it worked for me. Sporkubus, did you reboot?

---

### Post by sporkubus on 2008-10-31
Hey guys,

Well it DID work after I rebooted a second time, BUT... then I installed 8.10 and now my xorg.conf is completely different and doesn't contain all that stuff about my touchpad, so I don't know how to replicate the process now.

---

### Post by sporkubus on 2008-10-31
edit: doublepost

---

### Post by sporkubus on 2008-11-02
bump!!! hello??

---

### Post by squaregoldfish on 2008-11-02
Have you tried plonking the InputDevice section shown above back into your xorg.conf file? I can't say exactly where it should go, but a bit of sniffing round the net should turn something up.

That's the only thing I can suggest - I haven't upgraded yet, so I can't help any further.

Steve.

---

