---
title: "ATI support for pre-Radeon (rage IIc)?"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by cipher_nemo on 2006-10-29
I just recently install xubuntu edgy (6.10) (via the alternate install CD-ROM) on an older PC with an ATI Rage IIc video chip, and am having problems with the default "ati" driver for X.

**[FONT=Arial][SIZE=2]* Problem:*[/SIZE][/FONT]** I am testing this PC on a 1280x1024 native res, 75Hz max LCD monitor. xubuntu automatically set the correct res and refresh for my NEC LCD (at 75Hz), but the card is actually putting out around 80Hz and forcing my monitor to give the 'out of sync' message. When I get to a login screen, it is obvious the signal is slightly out of sync (multiple image ghosting and ripple movements).  I was able to change my user's profile to use 70Hz at 1024x768 without problems, but I'm seeing black-line artifacts near the desktop Applications menu. The rest of the screen is fine. What makes this odd is that Fedora Core runs X and Gnome just fine with this Rage IIc chip.

[FONT=Arial][SIZE=2]*** Question:***[/SIZE][/FONT] I'd like to try a driver other than the default "ati" one, such as DRI's driver. ATI doesn't release a driver for their chipsets on Linux that pre-date Radeon (ie: no Rage anything). Is there a package I can use (ie: restricted ones) for an ati driver that will work with Rage IIc, or at least a binary? DRI appears to be a 'roll your own' source distribution, and I hate having to build things myself. I wouldn't mind it if there was some step-by-step walkthrough for it. Also, even with the default ati driver, I don't seem to get any 2d acceleration (dragging windows around is laggy). Any ideas?

I'm trying to salvage this old PC and put it to use (you'll see why I want to use Xfce).

[FONT=Arial][SIZE=2]***Hardware:***[/SIZE][/FONT][LIST]
[*]Mobo: A real slow Trigem Florida-c (Socket 370) mini-atx
[*]Northbridge: Intel 440LX
[*]CPU: Intel Celeron 366MHz
[*]RAM: 384MB PC-100
[*]Video: ATI Rage IIc AGP w/ 4MB RAM (built-in)
[*]Sound: Crystal CS4280 (built-in)[/LIST]I'd rather not have to throw in a PCI video card (no AGP slot, even though on-board is by AGP bus). Other than this video issue, xubuntu seems to run just fine. :)

---

### Post by po0f on 2006-10-29
cipher_nemo,

Look up your monitor's horizotnal sync and vertical refresh settings and try manually adding them to your xorg.conf:
```
Section "Monitor"
    HorizSync min - max
    VertRefresh min - max
EndSection
```

---

### Post by cipher_nemo on 2006-10-29
That completely hosed my system :-/

I replaced "min" and "max" with my horizontal refresh rates, but are you sure the dash/minus sign "-" is supposed to be there?

---

### Post by po0f on 2006-10-29
Yes, you can use a dash to specify a range of frequencies ([reference](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/xorg.conf.5.html#sect9)).  Are you sure the values you entered are correct?  And please be more specific about your system being "hosed".

---

### Post by cipher_nemo on 2006-11-02
po0f, thx for helping... unfortunately, it seems that xubuntu (specifically the "nv" driver in Xfce?) is incorrectly communicating with this ATI Rage IIc chip. If I enter 75 (Hz) for the max horizontal rate, xubuntu is telling this video chip to run around 79.x Hz. I know this number because my monitor is able to report the refresh rate it is attempting to use (even though running my LCD at 79.x Hz is quite tough to view).

This doesn't seem to be a problem with Debian and Xfce or Fedora Core and Xfce, as those correctly set the max refresh rate to 75Hz.

So, I've dumped xubuntu since there is obviously something incorrectly configured with it in edgy, using the nv driver (or a bug). Thanks again for trying to help.

---

### Post by po0f on 2006-11-02
cipher_nemo,

The nv driver is the driver for NVIDIA cards, not ATi.  Did Xorg just happen to pick this driver for you?

---

### Post by cipher_nemo on 2006-11-04
po0f, no, it runs the "ati" driver on there. I use other PCs with nVidia chipsets, so I'm used to refering to the "nv" or "nvidia" driver. :) It was a typo.

---

### Post by zibletop on 2006-11-07
Hi,

With my ati rage mobility, I have suceffully suppress this kind of artifact with the SWCursors option (see [http://xorg.freedesktop.org/archive/X11R6.8.0/doc/ati5.html#6](http://xorg.freedesktop.org/archive/X11R6.8.0/doc/ati5.html#6) )

Now my Device section looks this

Section "Device"
    Identifier    "ATIRAGE"
    Driver        "ati"
    Option        "SWCursor"
    BusID        "PCI:1:0:0"
EndSection

---

### Post by cipher_nemo on 2006-11-08
zibletop, thanks for the tip! :) I'll hook up a spare HDD, install xubuntu again and give it a shot.

---

