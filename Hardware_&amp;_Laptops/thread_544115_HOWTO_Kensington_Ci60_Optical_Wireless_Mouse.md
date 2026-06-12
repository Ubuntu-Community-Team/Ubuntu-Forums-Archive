---
title: "HOWTO: Kensington Ci60 Optical Wireless Mouse"
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by riverfr0zen on 2007-09-05
---
Edit: The following method essentially brings the forward/backward mouse button functionality into place for browsing with Firefox, which was really my only concern, personally. I'm not sure if it will work system-wide, and it may cripple any existing apps that already do work as desired with those buttons. Basically, make a backup of your settings before trying this.
---

The following worked for me on Feisty at the point in time this post is being written, though it should work on any X11 installation as of now. 

The problem was to get all 5 mouse buttons on this mouse to work as expected. The following edit to the mouse section in /etc/X11/xorg.conf works for me perfectly:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 6 7"
        Option          "Emulate3Buttons"       "true"
EndSection

```

However, the following MAY be what you prefer (I do): This mouse retardedly comes with the 'back' and 'forward' buttons switched by default - so, in Windoze, for e.g., you would hit the front side button to go 'back' and the back side button to go forward. How nice, then to be able to switch those in X, thus:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "4 5"
        Option          "ButtonMapping"         "1 2 3 7 6"
        Option          "Emulate3Buttons"       "true"
EndSection

```

---

### Post by reemM on 2008-05-02
Thank you so much,

it worked like a charm on my Kensington Ci70 Wireless Mouse!

RTM

---

