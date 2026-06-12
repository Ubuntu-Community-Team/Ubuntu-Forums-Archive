---
title: "Two finger scrolling working in 12.04 but not in 11.04"
date: 2012-02-19
forum: Hardware
---

### Post by parth.s on 2012-02-19
I have an ASUS K53E laptop. my laptop touchpad is being recognized as a PS/2 mouse in 11.04. And hence I can't see the touchpad tab in the System Settings>Mouse.

Here's the output of the 'xinput list' command in 11.04:

parth@parth-K53E:~$ xinput list
&#9121; Virtual core pointer         	 id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse         id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard          id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard id=5	[slave  keyboard (3)]
    &#8627; Power Button               id=6	[slave  keyboard (3)]
    &#8627; Video Bus                  id=7	[slave  keyboard (3)]
    &#8627; Sleep Button               id=8	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera             id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard id=10[slave  keyboard (3)]

But recently I tried to boot 12.04 off a live cd (actually a thumb drive), the trackpad worked. I can now see the touchpad tab in System Settings>Mouse. Here's is the output of the xinput list command:

parth@parth-K53E:~$ xinput list
&#9121; Virtual core pointer           id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad   id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard          id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard id=5	[slave  keyboard (3)]
    &#8627; Power Button               id=6	[slave  keyboard (3)]
    &#8627; Video Bus                  id=7	[slave  keyboard (3)]
    &#8627; Sleep Button               id=8	[slave  keyboard (3)]
    &#8627; USB 2.0 Camera             id=9	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys           id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard id=11 [slave  keyboard (3)]

Any ideas?

---

### Post by ahallubuntu on 2012-02-19
You could try to figure out which module is being loaded in 12.04 for your touchpad and try to build that out in 11.04.  Figuring out the exact device might help - it's an Elantech touchpad it seems?  Maybe lspci or lshw would help.

Or...just live with it in 11.04 til 12.04 is released.

---

### Post by parth.s on 2012-02-19
both lspci and lshw are showing me all the hardware info other than the trackpad and keyboard...

---

### Post by parth.s on 2012-02-26
Its working in 11.10 too. So currently I have shifted to 11.10 but I still want to know if I can get it to work in natty..
Thanks

---

