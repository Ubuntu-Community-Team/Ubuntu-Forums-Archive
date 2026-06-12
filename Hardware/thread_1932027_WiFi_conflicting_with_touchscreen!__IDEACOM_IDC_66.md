---
title: "WiFi conflicting with touchscreen??!  IDEACOM IDC 6651 and Ralink ra3090"
date: 2012-02-26
forum: Hardware
---

### Post by danielkabrinski on 2012-02-26
Ubuntu 11.10 on an Acer Aspire All-in-One AZ3771

This is a very strange issue.  This is what xinput list shows:

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; IDEACOM  IDC 6651                           id=8    [slave  pointer  (2)]
&#9116;   &#8627; Primax Wireless Device                      id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=9    [slave  keyboard (3)]
    &#8627; Primax Wireless Device                      id=10    [slave  keyboard (3)]
    &#8627; ITE8713 CIR transceiver                     id=12    [slave  keyboard (3)]
```IDEACOM  IDC 6651 is my touchscreen.  Right now, it behaves like a touchpad...  a very unresponcive one.  I can move the mouse pointer but I can't click.

I installed calibrate touchscreen and I get this:

```
Error: No calibratable devices found.
```Ok.  So I figured I could fix the issue by removing the package "xserver-xorg-input-synaptics" thinking this is what is setting my touchscreen as a mouse.  I remove this and "xserver-xorg-input-all" (I have to I guess) then reboot.

xinput list gives me this (same thing):

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; IDEACOM  IDC 6651                           id=8    [slave  pointer  (2)]
&#9116;   &#8627; Primax Wireless Device                      id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; 1.3M WebCam                                 id=9    [slave  keyboard (3)]
    &#8627; Primax Wireless Device                      id=10    [slave  keyboard (3)]
    &#8627; ITE8713 CIR transceiver                     id=12    [slave  keyboard (3)]
```AND calibrate touchscreen NOW detects my IDEACOM hardware which still works like a touchpad (can't calibrate it, but it's a better start).  However, doing this messes up my ralink ra3090 wifi card where it will detect networks but struggle like crazy to connect, but never will.

So how to I get my touchscreen to STOP working like a touchpad ALL without losing my wifi capabilities?

I would really appreciate some assistance here.  I've tried everything I could and STILL can't figure out how to get my touchscreen to work correctly.

Whats funny:  The Ideacom IDC 6651 is supposedly "[On a certified system]("http://www.ubuntu.com/certification/catalog/component/input:10B11-TOUCH")" and I would assume that means that it works.  Why is this?

---

### Post by danielkabrinski on 2012-02-26
Bump, I've been working on this for hours now and I still can't figure it out.

---

