---
title: "HP Quickplay volume control slider issue"
date: 2009-10-17
forum: Hardware
---

### Post by Iehova on 2009-10-17
Hi everyone,

I first came across this issue during jaunty development, and initially posted this in the jaunty devel forum. It didn't get much response at the time though so I thought i'd try my luck here. The issue actually re-occurs in Karmic, but I can't even begin to get it solved without knowing what the related piece of software would be (edited and updated for clarity):

> Hi,

I have an hp pavilion dv9000 laptop which features touch sensitive hotkeys for volume control, play/pause etc ([seen here](http://daniel1.com.ar/ventas/photos/dv9000_3.jpg)). When I first installed jaunty (beta) the volume control hotkey worked as expected - sliding your finger one way increased the volume, the other decreased it.

[...] Now the volume control no longer works properly. If you place your finger on the right hand side of the hotkey the volume increases rapidly, if you place it on the left it decreases. Sliding your finger doesn't do anything except insofar as whilst your finger is on one side of the slider the volume changes rapidly.

My question is - what is it that controls the hotkey behaviour (so i can either revert to a previous version or preferably file a bug report)?

Thanks.

---

### Post by Iehova on 2009-10-19
*Bump*

It should be noted that the left and right hand sides of the slider (where the - and + buttons are) are mapped to decrease and increase volume respectively in System>Preferences>Keyboard Shortcuts. Unfortunately there's no option for 'slide volume' or anything similar. Disabling increase and decrease volume completely disables the slider.

I hope that information helps someone to offer a solution.

---

### Post by cocopuffz on 2009-10-19
I've got a HP HDX16 and have the same problem. Been asking the same question for a while and have had no answers. I'm not sure anyone knows. If they do... they aren't sharing. =(

---

### Post by Iehova on 2009-10-19
Hi cocopuffz,

I guess it's good (in a way) that I'm not alone in having this problem, there's a certain strength in numbers i guess. :P

I booted up into 8.04.1 and ran 'showkey' in a tty. I got the following scancodes when attempting various things:

volume + == 0x73 0xf3
volume - == 0x72 0xf2
slide to increase volume == 0x73 (repeated according to movement along slider)
slide to decrease volume == 0x72 (repeated as before)

The result of this is that, as the scancode 0x73 is assigned to increase volume, movement along the slider rightwards will generate repeated 'keypresses' and hence result in the desired behaviour. Likewise for decreasing volume.

I then tried the same thing in Karmic:

+ == 115 (generates a press and a release)
- == 114

An important change in behaviour here is that holding your finger on either the plus or minus generates rapidly repeating scancodes.

slider increase: 115 repeating in the same manner as with intrepid
slider decrease: 114 as before.

Importantly, when you stop moving along the bar no more scancodes are generated, and when you reverse direction the correct scancodes are generated. You would expect, then, that behaviour to be replicated in terms of the actual change in volume, but it is not, rather the movement of the on-screen slider is incredibly erratic, with a tendency to either shoot up or down and to carry on changing even when your finger stops moving along the slider.

If anyone can offer any insight it would be greatly appreciated.

EDIT: It strikes me that it is whatever is in charge of translating those scancodes to volume changes that is responsible for the problem, and if someone could tell me what that would be I could install the intrepid version and see if that solves the issue. I even know more or less to the day when the thing *stopped* working in jaunty's development cycle and so it should be trivial to point to the exact change which is causing the problem.

---

### Post by Iehova on 2009-10-19
Sorry to spam this topic but I have what I think is an important update.

The wiki article [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting) lists a number of different pieces of software responsible for hotkeys:

> Packages involved in acting on hotkey events:

    * gnome-power-manager - handles brightness and power hotkeys. Displays a popup 'OSD' display
    * gnome-settings-daemon (handles visual feedback of volume changes, display toggling)
    * gnome-control-center (gnome-sound-properties, gnome-keybinding-properties)
    * acpi-support (deprecated, being phased out)
    * gdm (until Ubuntu 9.04; 9.10 uses gnome-power-manager in gdm) 

I booted up into jaunty and began installing the intrepid versions of these packages, solving dependency issues as they arose and restarting x after each one to check the effect.

Gnome-control-center, gnome-power-manager and acpi-support had no noticable effect, but when I installed gnome-settings-daemon I appear to have more or less replicated the correct behaviour, that is I can increase the volume by sliding my finger, reverse direction and decrease the volume and so on. **EDIT: I take back what I said about gnome-settings-daemon. It seems that the difference was merely perceived rather than actual.**

Interestingly, there still seems to be an issue with how my movements themselves are interpreted, that is, if I hold my finger on either the + or - then volume will increase or decrease respectively, and at a very rapid rate. Further, if I start with my finger on another part of the slider and then move it, that initial position appears to be 'zeroed' and sliding my finger to one side or another of that initial position results in rapid change of the volume. Sliding my finger at a constant speed also seems to change the volume slowly at first, and then building up to a very rapid rate. However, other packages are supposedly responsible for the way these movements are collected, so I'll try those out next.

**EDIT:** This is the real issue. The following packages are responsible to varying degrees with collecting and propagating hotkey events:

> # linux kernel
# udev (model specific keycode to key symbol mapping)
# xserver-xorg-input-evdev
# xkeyboard-config
# acpi-support (deprecated, being phased out)
# hal (until Ubuntu 9.04; deprecated)
# hal-info (until Ubuntu 9.04; deprecated)
# hotkey-setup (until Ubuntu 9.04; deprecated)

Unfortunately these are a lot harder to install on a jaunty setup. Udev relies on far too many other packages being of an earlier version, and xserver-xorg-input-evdev also has conflicts. Acpi-support doesn't solve the issue, and hal, hal-info and hotkey setup don't apply to Karmic. I guess, at least, that that narrows the problem down to 4 packages.

**EDIT:** I just don't understand how, when showkey (in a tty) shows exactly the right behaviour (but for generating repeated scancodes if I just press and hold either the + or the - but NOT (correctly) if I slide my finger onto the + or - and hold it there) and yet that doesn't seem to correlate AT ALL with the on-screen behaviour within X. >=(

---

### Post by idef1x on 2009-11-18
Hi there Iehova,

Any progress on this issue? I've got a HP HDX16-1380ED recently and encounter the same issues as you :(
[s]Another strange thing i noted is that after removing the Pulseaudio engine and replacing it for esound (works better for me), breaks the volume + or - key completely. Reinstalling Pulseaudio gives the control back again...[/s]

The other touch keys don't work at all :(

This is for Ubuntu and as well for Kubuntu...

Cheers

---

### Post by alexfish on 2009-11-23
> **idef1x said:**
> Hi there Iehova,

Any progress on this issue? I've got a HP HDX16-1380ED recently and encounter the same issues as you :(
[s]Another strange thing i noted is that after removing the Pulseaudio engine and replacing it for esound (works better for me), breaks the volume + or - key completely. Reinstalling Pulseaudio gives the control back again...[/s]

The other touch keys don't work at all :(

This is for Ubuntu and as well for Kubuntu...

Cheers

this link may help

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
Step 9

If you are using a dual boot system (even with Windows and Ubuntu installed on separate partitions), then make sure to set the sound volume in Windows to a high level before booting into Ubuntu. Also make sure to use the special function keys in Windows to make sure the loudspeakers are physically switched ON and working properly in Windows before installing and testing Ubuntu. This step is necessary with certain Toshiba Tecra laptops.

---

### Post by idef1x on 2009-11-24
Thanks for the link. Strangely enough the touch keys do work now with PulseAudio. I reinstalled the laptop from scratch (wanted to encrypt the disk) and only the treble/bass slider doesn't do anything. Also not when pressing it in the keyboard shortcut settings.

---

### Post by Iehova on 2010-05-07
OK, this is an epic bump but I figured there's a lot of potentially useful information in this thread. In Lucid I still have the same problem where the volume slider does not work correctly (ie slide one way to increase, another to decrease volume). What I'm really asking is if anyone knows what piece of software is responsible and/or why the scancodes, which are generated correctly, are interpreted incorrectly.

Thanks.

---

### Post by Iehova on 2010-05-07
Curiouser and curiouser. It appears that showkey in a tty and xmodmap use totally different keycodes, with gnome sticking to xmodmap's version. Perhaps this is expected but it's news to me.

According to showkey when I decrease the volume using the slider that generates keycode 114 and an increase is 115. According to xmodmap these keycodes actually map to the right arrow and the end key (which themselves are 106 and 107 according to showkey). Xev likewise shows xmodmap's keycodes, but doesn't show any keycode when I use the volume slider.

Why on earth is this the case? Showkey, remember, has the right behaviour for the volume slider.

EDIT: Ah... "A little background note: When you hit a key on your keyboard, the linux kernel generates a raw scancode for it (if it is assigned). Each scancode can be mapped to a keycode. This is at kernel level. X has a (quasi) total independent way of mapping keys: X reads the kernel keycode table at startup, then maps the keycode to its independent keycode table (it is the same as the kernel keycodes but different :)). Then each keycode can be mapped to a keysym, i.e. a string which represent a key or suggest an action. Thus to have our keys fully functional, they need a kernel scancode/keycode plus a X keycode/keysym. It may seem weird, but X developers have their reason to keep a separate keyboard mapping from the kernel. It is not difficult at all, just a quite tedious procedure."

OK, so, the kernel assigns a scancode and a keycode (114 and 115). On top of that, X then assigns keycodes of 122 and 123 and keysyms of "XF86AudioLowerVolume" and "XF86AudioRaiseVolume" and it is in X's interpretation of these "keypresses" that the problem occurs. Has anyone got any suggestions?

---

### Post by yoshim on 2010-09-23
*bump*
ok, so im a new user, so I didnt understand much of what was in this thread. i have quickplay volume controls that were working for a little while -- then they stopped. they dont even show up on xev. (the Fn key and the touchpad). does that mean the computer doesn't even see the keys?

---

