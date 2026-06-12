---
title: "Mouse Scroll Button Problem"
date: 2005-12-02
forum: General Help
---

### Post by ankitmalik on 2005-12-02
I am using a simple SAMSUNG SMP2100WX mouse. It's a PS/2 scroll mouse. It was automatically detected by X during installation.

But when I click on a link in Firefox using the scroll button [ to open a link in a new tab] it registers it as more than one click. So I have two or more tabs opening the same links which gets frustrating! So any idea how I can mend this.

The problem isn't with the mouse because it doesn't register multiple clicks in Firefox/Win2k.

Also, when I 'scroll click' on a tab in Firefox/Windows, it closes the tab. Any idea how to set this up in Firefox/Kubuntu ?

An excerpt from /etc/X11/xorg.conf

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device"		"/dev/input/mice"
    Option         "Protocol"		"ImPS/2"
    Option         "Emulate3Buttons"	"true"
    Option         "ZAxisMapping"		"4 5"
EndSection
```

Thanks

---

### Post by Qrk on 2005-12-02
I have a guess or two. 

First, try doing it by pressing both the left and the right mouse buttons at once. That should do the same thing as pressing the scroll wheel. 

If that still has the same problem, try changing the "Emulate3Buttons" to false.

That may fix it.

---

### Post by ankitmalik on 2005-12-03
I checked out GNOME. This problem ain't present in GNOME. So that means KDE is the culprit ;-) . So changing xorg.conf won't help

---

