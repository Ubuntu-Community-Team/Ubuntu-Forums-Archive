---
title: "Full Screen App/Game issue"
date: 2008-07-30
forum: General Help
---

### Post by d3drocks on 2008-07-30
hey,
some full screen apps (some linux full screen apps, all windows fullscreen apps in wine) cause my screen to go black, and send me a message that says "out of Sync". i cant do anything when this happens, cause i cant see anything and i have to hard reboot. (which is really bad cause im on Wubi). it had somthing to do with the hrz of the refresh i think. is there any way to fix this?
all help is greatly appreciated, as my games run faster in wine then on XP.

---

### Post by CatKiller on 2008-07-30
Modern monitors do this when they are given a resolution or refresh rate that they don't understand. It is probably possible to configure those programs to use a different resolution that won't cause you this issue.

In any event, you don't need to do a hard reboot. If there aren't keyboard shortcuts to exit whichever application you're using, **Ctrl-Alt-Backspace** will kill and restart X, closing all your applications and taking you back to the login screen. Or you could press **Ctrl-Alt-F1** to go to a virtual console, log in, and **kill** whichever process it is that you want to stop. **killall *<appname>*** will usually work, and remember that you can use Tab-completion to get the name of the process.

Failing that, you can hold Alt&SysRq and type R-E-I-S-U-B (**R**aising **E**lephants **I**s **S**o **U**tterly **B**oring) to restart your computer more gracefully.

---

### Post by d3drocks on 2008-08-01
see, the thing is though that windows XP doesnt have this issue. is there no option to force all programs to conform to a set standard?

---

### Post by CatKiller on 2008-08-01
> **d3drocks said:**
> see, the thing is though that windows XP doesnt have this issue. is there no option to force all programs to conform to a set standard?

I'm not sure I really understand your point. The reason Windows XP knows which resolutions and refresh rates your monitor can do is because you've installed a "monitor driver" from the monitor manufacturer, which is, really, a list of the resolutions and refresh rates that the monitor can do. Without this list, Windows is similarly required to guess what these numbers might be.

There is a [set standard]("http://en.wikipedia.org/wiki/EDID") for **hardware** that makes this irrelevant, but in the 14 years since it was developed, many manufacturers still do not implement it properly.

It is certainly possible to enter this information manually, and is actually quite straightforward. You need to put the relevant numbers for your monitor as **HorizSync** and **VertRefresh** in **/etc/X11/xorg.conf**. There is quite detailed information about how to do so on this forum, but without knowing what your monitor is, or which resolutions you are trying to achieve, it is impossible for us to tell you what those numbers should be.

---

### Post by d3drocks on 2008-08-02
> **CatKiller said:**
> I'm not sure I really understand your point. The reason Windows XP knows which resolutions and refresh rates your monitor can do is because you've installed a "monitor driver" from the monitor manufacturer, which is, really, a list of the resolutions and refresh rates that the monitor can do. Without this list, Windows is similarly required to guess what these numbers might be.

There is a [set standard]("http://en.wikipedia.org/wiki/EDID") for **hardware** that makes this irrelevant, but in the 14 years since it was developed, many manufacturers still do not implement it properly.

It is certainly possible to enter this information manually, and is actually quite straightforward. You need to put the relevant numbers for your monitor as **HorizSync** and **VertRefresh** in **/etc/X11/xorg.conf**. There is quite detailed information about how to do so on this forum, but without knowing what your monitor is, or which resolutions you are trying to achieve, it is impossible for us to tell you what those numbers should be.

ok, i know what my monitor is. right on the front, it says LG Flatron L1752TQ (should be called Craptron, as it cant go to 1600x1200). thing is tho, i just assumed XP had no issue, as i have never had to install drivers for it.

---

### Post by CatKiller on 2008-08-02
First of all, open a Terminal; Applications -> Accessories -> Terminal. Make a copy of your existing xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

If it doesn't work, you can restore your backup from the command line with ```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

Next, use ```
gksudo gedit /etc/X11/xorg.conf
``` to edit this file. In the **Monitor** section, add the lines ```
        HorizSync       30-83
        VertRefresh     56-75
``` (I got the numbers from [this page]("http://www.lge.com/products/model/detail/L1752TQ.jhtml"))

You could also put the line ```
        Option          "UseEDID"                       "False"
``` at the end of the **Device** section to tell X to ignore whatever your video card reports.

Restart X with **Ctrl-Alt-Backspace** to have the new settings take effect.

LCD screens, as I understand it, have a native resolution based on the physical properties of the screen, and all other resolutions look pretty bad. So even though you can get your monitor to display other resolutions, it is probably worthwhile to configure all of your fullscreen applications to run in 1280x1024 anyway.

---

### Post by jonian_g on 2008-08-02
Open a terminal and type:

```
sudo displayconfig-gtk
```

On the window that comes up look if your monitor model is next to "Model:". If its not, click on it and find it in the list.
If its not in the list, instert in the drive the disc that came with your monitor, click "add" and locate the .inf file in the disc.

This way you will have:

> a "monitor driver" from the monitor manufacturer, which is, really, a list of the resolutions and refresh rates that the monitor can do.

No need to manualy edit xorg.conf

---

### Post by CatKiller on 2008-08-02
> **jonian_g said:**
> No need to manualy edit xorg.conf

Excellent. I'd only configured graphics devices before the recent upgrades to X, so I had no experience of how/if they worked.

Although, since it's a graphical application, it is a good habit to use **gksudo** rather than **sudo**. See, for example, [this page]("http://www.psychocats.net/ubuntu/graphicalsudo").

EDIT: I did just try this and, although my monitor was listed, selecting it meant that when I logged out per the instructions, the GDM login screen was no longer in the right place, the highest resolution was no longer available, and the irritating NVidia logo was restored. So although this tool is much nicer for the new user than manually configuring X, it is not yet optimal. Still a huge advance on just a couple of years ago, though!

---

### Post by jonian_g on 2008-08-02
I always use sudo for all apps and gksudo when using Alt+F2. I see what the problems might be, reading the link you provided, but using just sudo is a two years habbit for me. Maybe I have to change that though I never had problems using sudo with graphical apps.

---

