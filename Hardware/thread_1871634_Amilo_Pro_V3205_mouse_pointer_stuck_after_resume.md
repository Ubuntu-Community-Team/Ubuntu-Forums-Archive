---
title: "Amilo Pro V3205 mouse pointer stuck after resume"
date: 2011-10-29
forum: Hardware
---

### Post by Schr on 2011-10-29
Hi,

The touchpad mouse pointer on my Amilo Pro V3205 gets stuck always after resuming it from hibernation or sleep.

And in deep the touchpad disappears from the xinput --list after resume

```

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=11   [slave  pointer  (2)]
&#9116;   &#8627; Mouseemu virtual mouse                    id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
    &#8627; Mouseemu virtual keyboard                 id=13   [slave  keyboard (3)]

```

```

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Mouseemu virtual mouse                    id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=10   [slave  keyboard (3)]
    &#8627; Mouseemu virtual keyboard                 id=13   [slave  keyboard (3)]


```

Changes to Xorg.0.log look this this after resuming

```

> [   260.654] (II) intel(0): EDID vendor "CMO", prod id 4624
> [   260.655] (II) intel(0): Printing DDC gathered Modelines:
> [   260.655] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
> [   260.655] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
> [   266.060] (II) AIGLX: Suspending AIGLX clients for VT switch
> [   270.087] (II) config/udev: removing device SynPS/2 Synaptics TouchPad
> [   270.088] (II) UnloadModule: "synaptics"
> [   270.088] (II) Unloading synaptics
> [   270.165] (II) Open ACPI successful (/var/run/acpid.socket)
> [   270.165] (II) AIGLX: Resuming AIGLX clients after VT switch
> [   270.165] (EE) intel(0): Couldn't create pixmap for fbcon
> [   270.180] (II) intel(0): EDID vendor "CMO", prod id 4624
> [   270.180] (II) intel(0): Printing DDC gathered Modelines:
> [   270.180] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
> [   270.180] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
> [   277.430] (II) XKB: reuse xkmfile /var/lib/xkb/server-AC832CF0C4F9C1AF1A9A69B15468A0672B277D4C.xkm


```

Is there a way to reload the disappeared synaptics module or stop it from being unloaded in the first place

Edit: specified touchpad in the subject.

---

### Post by Schr on 2011-10-31
Anyone? Any ideas?

---

### Post by Schr on 2011-11-08
No hope for my lappy :(

I've tried removing unnecessary input drivers (sudo apt-get remove <package>):

xserver-xorg-input-wacom
xserver-xorg-input-vmmouse

and even:

xserver-xorg-input-synaptics

And only thing that changes is that after remving the synaptics package the trackpad speed is a bit too high, even though settings for it's acceleration are at the lowest possible.

---

