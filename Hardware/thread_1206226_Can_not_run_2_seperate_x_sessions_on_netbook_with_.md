---
title: "Can not run 2 seperate x sessions on netbook with external monitor"
date: 2009-07-06
forum: Hardware
---

### Post by Dave_Connor on 2009-07-06
I wanted to set up my sister's monitor as a seperate monitor just for a learning experiance but this is currently very hard to do for atleast for me. I Tried this on my big laptop and I get the same results with just a cloned copy of my internal display and fails with enabling Xinerama. Is this an issues with my cards with Xinerama ?
For my netbook my card is Intel Moble 945GME and has a second VGA port open on the side for an addition monitor. 

Here is my xorg.conf, I know it is really basic and doesn't have custom settings yet but I am trying to work from the ground up.

```
Section "Monitor"
        Identifier      "EEEPC"
EndSection

Section "Monitor"
        Identifier      "EXTERN"
EndSection

Section "Device"
        Identifier      "Card1"
        Driver          "intel"
        BusID           "00:02:00"
EndSection

Section "Device"
        Identifier      "Card2"
        Driver          "intel"
        BusID           "00:02:1"
EndSection

        Device          "Card1"
        SubSection "Display"
                Modes "1024x600"
                Depth 24
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Monitor         "EEEPC"
        Device          "Card1"
        SubSection "Display"
                Modes "1024x600"
                Depth 24
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen2"
        Monitor         "EXTERN"
        Device          "Card2"
        SubSection "Display"
                Modes "1024x600"
                Depth 24
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "Screen1" 0 0
        Screen 1        "Screen2" RightOf "Screen1"
        Option          "Clone"         "off"
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "Module"
        #Load   "dri"
        Load    "dbe"
EndSection

```

---

### Post by shatterblast on 2009-07-07
I don't think any special editting is required.  I have previously used my computer for big-screen presentations and entertainment.  You might try holding down CTRL and SHIFT on your keyboard and then pressing something like F7, F8, or F9.  One of those Function keys may do the trick hopefully.  The ones on the far left though are for the complicated stuff.

---

