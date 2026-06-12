---
title: "karmic, disabling tapping on elantech touchpad"
date: 2009-11-07
forum: Hardware
---

### Post by udutronik on 2009-11-07
Hello community,

I've installed ubuntu 9.10 on my ASUS k40in laptop

it has an elantech touchpad and I'm looking for a solution to disable tapping

I've tried installing gsynaptics, following [these instructions]("https://help.ubuntu.com/community/SynapticsTouchpad"), with no luck

Browsing these forums, there seems to be issues but I have difficulty finding if they are solved in Karmic

anybody can help?

Thanks

---

### Post by kop316 on 2009-11-16
Hey,

I found it from here:

[http://ubuntuforums.org/showthread.php?t=1287077](http://ubuntuforums.org/showthread.php?t=1287077)

---

### Post by udutronik on 2009-11-24
Thanks Kop for your help

The thread you pointed at suggest to open the System->Preferences->Mouse application. Select the Touchpad page and deselect 'Enable mouse clicks with touchpad' 

If it was that simple... The problem is that I have NO touchpad tab on the System->Preferences->Mouse menu

---

### Post by Niila on 2009-11-26
I have 2009 MacBook with multitouchpad and the same problem. I do have touchpad tab in Mouse menu and but it doesnt work! :frown: But the multitouch works luckily..

---

### Post by orengolan on 2010-01-25
udutronik and anyone else here,

There is a problem with Elan touchpad.
I submitted the bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192](https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192)

Please go there and change the status to 'Confirm' so Ubuntu developers will understand that it's a hardware issue and not something specific to me.
Also mention your hardware.

Thanks you so much!

---

### Post by udutronik on 2010-01-27
> **orengolan said:**
> udutronik and anyone else here,

There is a problem with Elan touchpad.
I submitted the bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192](https://bugs.launchpad.net/ubuntu/+s...cs/+bug/512192)

Please go there and change the status to 'Confirm' so Ubuntu developers will understand that it's a hardware issue and not something specific to me.
Also mention your hardware.

Thanks you so much!

Thanks to you for taking the time to file a bug. I left a message on the bug you've filed stating :

I can confirm this bugs also affects my ASUS UL80-VT which also has an elantech touchpad
Xinput list shows the touchpad is erroneously recognized as "ImPS/2 Logitech Wheel Mouse"

I can also state that this is not a distro-related bug as I have experienced the same problem with OpenSuse
As a matter of fact I did file a bug report here : [https://bugzilla.novell.com/show_bug.cgi?id=558225](https://bugzilla.novell.com/show_bug.cgi?id=558225)

Hope this gets fixed soon cause its really annoying, I have to disable touchpad in order to be able to enjoy my Linux :-)

---

