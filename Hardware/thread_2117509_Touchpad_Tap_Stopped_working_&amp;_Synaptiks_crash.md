---
title: "Touchpad Tap Stopped working &amp; Synaptiks crashing"
date: 2013-02-18
forum: Hardware
---

### Post by cmt29 on 2013-02-18
Hi,

Having followed the instructions [here]("http://ubuntuxtreme.com/howto/how-to-fix-your-amd-graphics-in-ubuntu-12-10/") to enable proprietary video drivers for my laptop, it appears that my touchpad tap function has stopped working under KDE. Any help to get it back working would be appreciated. Here are the details:

Laptop: Acer Aspire 5920
Kubuntu & Ubuntu 12.10
Xorg Downgraded to 1.12 to allow use of legacy ATI drivers.

Tapping works fine in Ubuntu; it just fails in KDE.

Error output when running 'synaptiks' from console:
```
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
```

Output of xinput -list
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=13   [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                id=12   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Power Button                              id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; Acer Crystal Eye webcam                   id=10   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=11   [slave  keyboard (3)]

```

"synclient | grep Tap" produces:
```
    MaxTapTime              = 180
    MaxTapMove              = 221
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    TapButton1              = 0
    TapButton2              = 0
    TapButton3              = 0
    TapAndDragGesture       = 1
```

Things I've tried:
[LIST]Re-installed kde-config-touchpad[/LIST]

I think I just need to enable tapping in Xorg, but not sure how to go about this.

Also, should I file a bug report with KDE regarding Synaptiks crashing? If so, how to I go about getting them the right information?

Thanks.

---

### Post by cmt29 on 2013-02-20
Well, I've not been able to get synaptiks workings, so I'll probably try file a bug report with them.

However, after some looking around I've managed to create a custom xorg.conf file in /etc and it contains:

```
 Section "InputClass"
       Identifier "touchpad"
       Driver "synaptics"
       MatchIsTouchpad "on"
              Option "TapButton1" "1"
 EndSection
```

This enables TouchPad tapping across the board in X.

For others investigating such things, then [this page]("https://wiki.archlinux.org/index.php/Touchpad_Synaptics") is helpful.

---

