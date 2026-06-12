---
title: "Wacom Tablet (Intuos Pro) - Multiple Monitors"
date: 2018-10-19
forum: Hardware
---

### Post by m-knichel on 2018-10-19
I just purchased a wacom intuos pro tablet. Running Xubuntu 18.04 using xfce. The tablet is recognized fine, but spans all 3 screens. I tried a script to change display:

```

[FONT=monospace][COLOR=#18B2B2]#!/bin/sh[/COLOR]
[COLOR=#18B2B2]#using xrandr we get the list of monitors[/COLOR]
[COLOR=#18B2B2]#using xinput we get the list of connected devices[/COLOR]

wacom[COLOR=#18B218]=[/COLOR][COLOR=#000000]xinput [/COLOR][COLOR=#18B218]| [/COLOR][COLOR=#5454FF]**grep**[/COLOR][COLOR=#000000] -i Intuos [/COLOR][COLOR=#18B218]| [/COLOR][COLOR=#5454FF]**awk **[/COLOR][COLOR=#FFFF54]**'{ print $9 }' **[/COLOR][COLOR=#18B218]| [/COLOR][COLOR=#5454FF]**awk**[/COLOR][COLOR=#000000] -F [/COLOR][COLOR=#FFFF54]**'=' **[/COLOR][COLOR=#FFFF54]**'{ print $2 }'**[/COLOR]
[COLOR=#18B218]for[/COLOR][COLOR=#000000] id [/COLOR][COLOR=#18B218]in [/COLOR][COLOR=#FF5454]**$wacom**[/COLOR]
[COLOR=#18B218]do[/COLOR][COLOR=#000000] xinput map-to-output [/COLOR][COLOR=#FF5454]**$id**[/COLOR][COLOR=#000000] DP-0 [/COLOR]
[COLOR=#18B218]done[/COLOR]
[/FONT]
```
The tablet still spans all 3 displays. I only want it on my main display (DP-0)
I have verified that the $id's are correct for all of the wacom id's in xinput.

Any help is appreciated.

---

### Post by m-knichel on 2018-10-19
Got it working, not sure what was wrong, but I re-typed the code and it works now.

---

