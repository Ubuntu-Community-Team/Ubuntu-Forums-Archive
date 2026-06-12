---
title: "ppa: evdev driver with code remap"
date: 2012-09-26
forum: Hardware
---

### Post by qwazix on 2012-09-26
I have an HP 2710p convertible and I wanted to use the side info key as Super so that I can open the dash while in tablet mode. This generates a keycode greater than 255, I have been compiling the patched version of the evdev driver found here [http://www.thenautilus.net/SW/xf86-input-evdev/](http://www.thenautilus.net/SW/xf86-input-evdev/) since oneiric but the process was hard to do each time (and it broke my upgrade from oneiric to precise) so I decided to give it a try and create a ppa with that code. The package is for quantal.

This is my first try in ubuntu packaging so many things may not be as expected. The package seems to work for me, however my system is not "clean", so your mileage may vary.

I am kindly asking some brave person to test this package, but beware that it may cause your keyboard to stop working, and thus make input impossible. (A wacom tablet uses another driver so that is a good way to work around and reinstall official evdev in case something goes wrong)

The ppa is here:
[https://launchpad.net/~qwazix/+archive/evdev-code-remap](https://launchpad.net/~qwazix/+archive/evdev-code-remap)

I apologize if this is posted in the wrong place.

Additional info:
[http://www.mythtv.org/wiki/Remapping_remote_control_key_codes_greater_than_255](http://www.mythtv.org/wiki/Remapping_remote_control_key_codes_greater_than_255)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/969495](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/969495)

---

### Post by Favux on 2012-09-29
Hi qwazix,

So the kernel keycode is within 8 of 255 so it produces an X keycode above 255?

Have you tried assigning the kernel scancode directly to the kernel keycode corresponding to the X Super keycode in rc.local?  Since:
```
keycode 133 = Super_L NoSymbol Super_L
keycode 134 = Super_R NoSymbol Super_R
```
and 133 - 8 = 125.  I suppose it should look something like:
```
setkeycodes xxxx 125
```
With xxxx depending on what value you get.  As in the example in "Appendix 3: HP Elitebook Tablet PC Thumb Scroll Bezel Button" on the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830").

---

### Post by qwazix on 2012-10-02
Unfortunately it produces keycode 358 which is not visible at all neither in showkey nor in xev. Thus the need for modified drivers.

---

### Post by The Carpenter Ant on 2012-10-06
Hi Guys

Sorry for jumping in on this conversation, but I too am having issues with keycodes >255 and the blessed input-evdev.  My point is:  I found that in the change log for xserver-xorg-input-evdev from those tricky devils at X, that the following is listed:


xserver-xorg-input-evdev (1:2.5.0-1) experimental; urgency=low

  [ Robert Hooker ]
  * New upstream release.
  * Bump xutils-dev build dep for new util-macros.

  [ Cyril Brulebois ]
  * New upstream release fixes some bugs:
     - Forward keycodes > 255 (Closes: #500096).
     - No longer list README.mouse (Closes: #590529).

So is it forwarding keycodes greater than 255, or am I missing something 'cos I having all the usual problems.

Cheers

---

### Post by qwazix on 2012-10-14
As I understand it that would only be for keycodes 255 - 263 because that behaviour would have undesired effects for greater keycodes (e.g. 264 would overlap keycode 9)

---

### Post by J0llyr0ger on 2012-11-11
Uh Oh   I get:

W: Failed to fetch [http://ppa.launchpad.net/qwazix/evdev-code-remap/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/qwazix/evdev-code-remap/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/qwazix/evdev-code-remap/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/qwazix/evdev-code-remap/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/qwazix/evdev-code-remap/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/qwazix/evdev-code-remap/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

