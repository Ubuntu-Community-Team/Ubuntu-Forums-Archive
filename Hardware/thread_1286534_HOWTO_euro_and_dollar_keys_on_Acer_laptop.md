---
title: "HOWTO: euro and dollar keys on Acer laptop"
date: 2009-10-09
forum: Hardware
---

### Post by ororo on 2009-10-09
I have an Acer Aspire 5612WLMi, with Ubuntu 9.04 Jaunty Jackalope. I had  problems in making the two keys "$" and "&#8364;" work. Most of the guides online use "xmodmap" to remap these keys, but actually it seems that xmodmap is not compatible with evdev, the keyboard driver in Jaunty:
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5610]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5610")

This is how I solved the problem (still not completely).

(1) find the keycodes to use. 
Watching /usr/share/X11/xkb/keycodes/evdev, I found out that all the keycodes are already used. I decided to overwrite the 126 and 129.

(2) associate the keycodes with the correct symbols: in
/usr/share/X11/xkb/symbols/it (just because my keyboard is italian)
I added:

```
key <I126> { [ EuroSign ] };
key <I129> { [ dollar ] };
```

The same keycodes were already used in /usr/share/X11/xkb/symbols/inet,
so I had to mask some lines in that file:
```
//  key <I126>   {      [ plusminus             ]       };
//  key <I129>   {      [ KP_Separator          ]       };
```

(3) Reboot

(4) associate the scancodes with the keycodes. The keycodes used by setkeycodes are "-8" w.r.t. the keycodes used by X:
```
sudo setkeycodes e033 118
sudo setkeycodes e034 121
```

Ok now they work! I still have one problem: the point (4) must be repeated after each boot, I am not able making a script to run it at boot-time.

---

### Post by ororo on 2009-10-09
Oh, the last problem was simpler than I thought. Just add the lines:
```

setkeycodes e033 118
setkeycodes e034 121

```
into /etc/rc.local.

---

