---
title: "Display exceeds screen dim. after NVidia update..."
date: 2013-05-02
forum: Hardware
---

### Post by danielakkerman on 2013-05-02
Hello everyone!
I am running a Ubuntu 12.04(LTS) installation, 64bit, with a GeForce GT240; the latter connected via HDMI to a Sony Bravia, 42'' TV.
 Recently, after an Nvidia driver update(on which I had dithered and delayed for quite a while) I've encountered a strange and irresolvable phenomenon: at the given resolution(1280x720 -- perfectly standard) the display overruns the monitor; in other words, the panels, taskbar and other features of the display go beyond the screen's edges, and are therefore "cut" in half(see enclosed photos). This has never happened, before!
The present NVidia version is 304-current.
Furthermore, removal of the driver, and using the default(Nouveau/built-in) one resolves the problem completely, although, naturally, this means I am not getting the full Hardware acceleration component of my card.
What should I do?
Where do you reckon the problem is?
Yours most beholden,
Thanks!
Daniel
Attaching xorg.conf:
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "built-ins"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "kmsdev"                    # <str>
        #Option     "ShadowFB"                  # [<bool>]
        Identifier  "Card0"
        Driver      "nvidia"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
        Identifier  "Card0"
        Driver      "nvidia"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

---

### Post by gordintoronto on 2013-05-02
It might be possible to fix this with a menu setting in the TV.

---

### Post by papibe on 2013-05-02
> **gordintoronto said:**
> It might be possible to fix this with a menu setting in the TV.
+1

Hi danielakkerman.

That look like [Overscan]("http://en.wikipedia.org/wiki/Overscan"). The best solution is to change your TV settings.

In a Sony Bravia:
```
Menu/Home -> Settings/Options -> Screen
```
Change that setting to either 'Full Pixel', 'Normal' or 'Full Scan'.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by danielakkerman on 2013-05-03
Guys, your suggestions worked fantastically!
(Great step-by-step explanation, papibe!)
You'll have to excuse my ignorance of such a simple solution(I really thought it was "it" for my setup, and that I would have to reinstall the whole thing from scratch).
Question is, why do you suppose it happened, to begin with? Previously, my card would detect the TV's scan rate flawlessly, and it is only **after** the Nvidia upgrade that these issues surfaced.
At any rate,
I am immeasurably grateful,
Thanks again!
Daniel
P.S.
How do I mark this as solved? :D

---

### Post by papibe on 2013-05-03
Glad you sorted it out :)

It has nothing to do with the card, the machine, or even Ubuntu (or Windows if it were the case). Unfortunately it is how most, if not all, TVs are set by default. It seems to be a practice inherited from analog TV.

Note that the setting you just changed applies only for the input you set it on. You are probably still seeing a overscan signal on your other inputs (DVD, etc.), and even on your regular TV signal. To get rid off it completely, you need to repeat the process for every input.

Regards.

P.S.: for 1080i TV signal the name is the same (Full Pixel), but for 720p the names are different: the overscan settings are called -1, and -2 and the overscan free is called 'Normal'.

---

