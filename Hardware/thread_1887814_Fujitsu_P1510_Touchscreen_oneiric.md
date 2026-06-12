---
title: "Fujitsu P1510 Touchscreen oneiric?"
date: 2011-11-27
forum: Hardware
---

### Post by psixpsi on 2011-11-27
Hi all! I've just successfully installed oneiric on my Fujitsu P1510.
Any ideas how to install the touchscreen? The known procedure
[http://ubuntuforums.org/showpost.php?p=7180185&postcount=37](http://ubuntuforums.org/showpost.php?p=7180185&postcount=37)
which has worked for me 100% ok up to 9.04 does not seem to work now (I 
can't install the X11::GUITest via the described method, I get a message that I do not allow connection to the internet to look for CPAN mirrors).

I've tried to take another route and installed the package xserver-xorg-input-fujitouch (Natty version) from

[https://launchpad.net/~fujitouch/+archive/ppa](https://launchpad.net/~fujitouch/+archive/ppa)

Sorry for a naive question but what do I do with this package now?
THanks for any input,
psi

---

### Post by psixpsi on 2011-12-02
Sorry for a shameless bump, but has anyone attacked the problem?
Thanks!
psi

---

### Post by psixpsi on 2011-12-09
So I see touchscreen app in my startup session.
I've created xorg.conf.new with X :1 -configure
and modiffied it per
instructions: added the touchscreen section:

Section "InputDevice"
    Identifier "touchscreen"
    Driver "fujitsu"
    Option "Device" "/dev/ttyS0"
    Option "DeviceName" "touchscreen"
    Option "MinX" "82"
    Option "MinY" "146"
    Option "MaxX" "4036"
    Option "MaxY" "3999"
    Option "SendCoreEvents" "On"
EndSection

and

InputDevice "touchscreen" "CorePointer"

in the ServerLayout
and removed corepointer from the mouse.
Still no result...

---

