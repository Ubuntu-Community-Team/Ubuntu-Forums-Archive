---
title: "QSynaptics driver problem"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by xnszxdotnet on 2008-02-06
I'm havin a problem with qsynaptics. I have edited my /etc/X11/xorg.conf file to look like this```

...
Section "InputDevice"
  Driver  	"synaptics"
  Identifier  	"TouchPad"
  Option	"Device"  	"/dev/psaux"
  Option	"Protocol"	"auto-dev"
  Option	"LeftEdge"      "1700"
  Option	"RightEdge"     "5300"
  Option	"TopEdge"       "1700"
  Option	"BottomEdge"    "4200"
  Option	"FingerLow"	"25"
  Option	"FingerHigh"	"30"
  Option	"MaxTapTime"	"180"
  Option	"MaxTapMove"	"220"
  Option	"VertScrollDelta" "100"
  Option	"MinSpeed"	"0.09"
  Option	"MaxSpeed"	"0.18"
  Option	"AccelFactor"	"0.0015"
  Option	"SHMConfig"	"true"
EndSection
...

```
I then restarted and install qsynaptics from package manager, when I run the app i get this
 [IMG]http://assets.drop.io/download/47aa75ba/2f59c33d033db61acdb0f0a976edd15b5f14fe90/731bfea0-b757-012a-1521-00127994f632/9b290670-b757-012a-64c6-ffb19ec0ba73/screenshot-qsynaptics.png[/IMG]

errors about the drivers and enabling X shared memory. please help. Thanks.

---

