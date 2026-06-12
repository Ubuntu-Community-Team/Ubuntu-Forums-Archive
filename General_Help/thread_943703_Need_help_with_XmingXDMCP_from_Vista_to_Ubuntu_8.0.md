---
title: "Need help with Xming/XDMCP from Vista to Ubuntu 8.04 (hardy)"
date: 2008-10-10
forum: General Help
---

### Post by kedmond on 2008-10-10
Thanks for reading my post.

I am on a LAN at work, and I have a laptop running Vista and a desktop machine running Ubuntu 8.04. I would like to start a remote session with the Ubuntu machine using XDMCP.

I am using Xming and Xlaunch on my Vista computer.  I am able to launch Xming and, using putty with X11 packet forwarding, launch linux applications such as xterm and firefox on my laptop.

However, I have never been able to get XDMCP working via the Xlaunch application.  I've opened up the correct ports (TCP: 6000, 16001 and UDP: 177) in the windows firewall.

I've followed the instructions found here: [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Remote_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Remote_Desktop)

When I login to the Ubuntu machine, the gray desktop opens, I see Gnome's spinning wheel, and then the whole Xming session closes only to reopen again, and it repeats this behavior indefinitely until I go to Task Manager to kill Xming.exe.

The Xming error log follows:

```
glWinInitVisuals:1509: glWinInitVisuals
init_visuals:1055: init_visuals
glWinScreenProbe:1388: glWinScreenProbe
fixup_visuals:1301: fixup_visuals
init_screen_visuals:1334: init_screen_visuals
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409) 
(--) Using preset keyboard for "English (USA)" (409), type "4"
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
(--) 3 mouse buttons found
Could not init font path element C:\Program Files\Xming/fonts/CID/, removing from list!
winProcEstablishConnection - Hello
winProcEstablishConnection - Xdmcp enabled, waiting to start clipboard client until fourth call.
winProcEstablishConnection - Hello
winProcEstablishConnection - Xdmcp enabled, waiting to start clipboard client until fourth call.
winProcEstablishConnection - Hello
winProcEstablishConnection - Xdmcp enabled, waiting to start clipboard client until fourth call.
glWinResetExtension:1487: glWinResetExtension
winDeleteNotifyIcon
(==) FontPath set to "C:\Program Files\Xming/fonts/misc/,C:\Program Files\Xming/fonts/TTF/,C:\Program Files\Xming/fonts/Type1/,C:\Program Files\Xming/fonts/CID/,C:\Program Files\Xming/fonts/75dpi/,C:\Program Files\Xming/fonts/100dpi/"
(==) Logfile set to "C:\Users\kedmond\AppData\Local\Temp\Xming.0.log"
glWinInitVisuals:1509: glWinInitVisuals
init_visuals:1055: init_visuals
glWinScreenProbe:1388: glWinScreenProbe
fixup_visuals:1301: fixup_visuals
init_screen_visuals:1334: init_screen_visuals
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409) 
(--) Using preset keyboard for "English (USA)" (409), type "4"
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
(--) 3 mouse buttons found
Could not init font path element C:\Program Files\Xming/fonts/CID/, removing from list!
winProcEstablishConnection - Hello
winProcEstablishConnection - Xdmcp enabled, waiting to start clipboard client until fourth call.
winProcEstablishConnection - Hello
winProcEstablishConnection - Xdmcp enabled, waiting to start clipboard client until fourth call.
winProcEstablishConnection - Hello
winProcEstablishConnection - Xdmcp enabled, waiting to start clipboard client until fourth call.
glWinResetExtension:1487: glWinResetExtension
winDeleteNotifyIcon
(==) FontPath set to "C:\Program Files\Xming/fonts/misc/,C:\Program Files\Xming/fonts/TTF/,C:\Program Files\Xming/fonts/Type1/,C:\Program Files\Xming/fonts/CID/,C:\Program Files\Xming/fonts/75dpi/,C:\Program Files\Xming/fonts/100dpi/"
(==) Logfile set to "C:\Users\kedmond\AppData\Local\Temp\Xming.0.log"

```

This log file repeats in this fashion indefinitely...

Any help would be appreciated, thanks.

-Kazem

---

