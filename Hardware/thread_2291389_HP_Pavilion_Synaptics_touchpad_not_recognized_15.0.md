---
title: "HP Pavilion Synaptics touchpad not recognized 15.04"
date: 2015-08-19
forum: Hardware
---

### Post by magtrask on 2015-08-19
[COLOR=#333333][FONT=Ubuntu]HP Pavilion with Ubuntu 15.04 cannot two finger scroll. No options in Mouse and Touchpad application.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
Synaptics not recognized, asks if driver is installed.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]silas@hp:~$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]silas@hp:~$ xinput list
&#9121; Virtual core pointer id=2    [master pointer (3)]
&#9116; &#8627; Virtual core XTEST pointer id=4    [slave pointer (2)]
&#9116; &#8627; A4TECH USB Device id=9    [slave pointer (2)]
&#9116; &#8627; A4TECH USB Device id=10    [slave pointer (2)]
&#9116; &#8627; PS/2 Generic Mouse id=13    [slave pointer (2)]
&#9123; Virtual core keyboard id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard id=5    [slave keyboard (3)]
    &#8627; Power Button id=6    [slave keyboard (3)]
    &#8627; Video Bus id=7    [slave keyboard (3)]
    &#8627; Power Button id=8    [slave keyboard (3)]
    &#8627; HP Truevision HD id=11    [slave keyboard (3)]
    &#8627; AT Translated Set 2 keyboard id=12    [slave keyboard (3)]
    &#8627; HP Wireless hotkeys id=14    [slave keyboard (3)]
    &#8627; HP WMI hotkeys id=15    [slave keyboard (3)]

# dmidecode 2.12
# SMBIOS entry point at 0x7c7e0010
/dev/mem: Operation not permitted
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid
Linux hp 3.19.0-18-generic #18-Ubuntu SMP Tue May 19 18:31:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
Tried all recomendations found in forums. You folks have been very helpful in the past. I've tried with LaunchPad, no success. Please advise, thank you.[/FONT][/COLOR]

---

