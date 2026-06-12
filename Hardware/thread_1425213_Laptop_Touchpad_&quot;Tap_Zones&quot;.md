---
title: "Laptop Touchpad &quot;Tap Zones&quot;"
date: 2010-03-08
forum: Hardware
---

### Post by youarefunny on 2010-03-08
I was trying to configure my laptops "Tap Zones" using the following post:

[http://ubuntuforums.org/showthread.php?t=518826](http://ubuntuforums.org/showthread.php?t=518826)

I created my touchpad settings in xorg.config

```
Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option        "SendCoreEvents" "true"
    Option        "Device" "/dev/psaux"
    Option        "Protocol" "auto-dev"
    **Option      "RBCornerButton" "2"**
    Option        "HorizScrollDelta" "0"
    Option        "SHMConfig" "true"
EndSection

```But, i was wondering if you can set the tap zones to launch a program or type a key sequence.

Also chaning the size of the zones would be nice if you are able to.

Thank you.

---

### Post by Enterpart on 2011-10-15
I have answered these two questions here and Im posting it as reference for future users

I know your a fan of easystroke but I bet you didnt know you can do this with it. Set up the corner tap zones on laptops to perform as keystrokes or even scroll wheels. Check it out if your interested

link [http://ubuntuforums.org/showthread.php?t=1859936]("http://ubuntuforums.org/showthread.php?t=1859936")

and how to configure the tap zones

[http://ubuntuforums.org/showthread.php?t=1824870]("http://ubuntuforums.org/showthread.php?t=1824870")

---

