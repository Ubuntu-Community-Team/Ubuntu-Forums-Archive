---
title: "Touchpad hotkey toggle doesn't work"
date: 2021-04-09
forum: Hardware
---

### Post by julio-netu on 2021-04-09
Hotkey toggle doesn't work with Ubuntu 20.10 on my Lenovo L340. I tried to use 2 workarounds I found online: creating a script* to manually switch xinput and xdotool, then creating a new shortcut. Both work in the terminal, but won't work properly once I create the shortcut!
The shortcut using xinput only DISABLE the touchpad. But if a run the very same script on terminal, it will enable it back. 
The command xdotool key XF86TouchpadToggle seems to not work at all once set the shortcut, but works on the terminal.

guides I followed:
[https://askubuntu.com/questions/1165445/is-there-a-way-to-toggle-touchpad-on-off-with-a-command-keyboard-shortcut](https://askubuntu.com/questions/1165445/is-there-a-way-to-toggle-touchpad-on-off-with-a-command-keyboard-shortcut)
[https://goinglinux.com/articles/ToggleTrackpadTouchPad_en.htm](https://goinglinux.com/articles/ToggleTrackpadTouchPad_en.htm)

*This is the exact script I used:
[INDENT]
if [[ $(xinput list 13 | grep -Ec "disabled") -eq 1 ]]; then
    xinput enable 13
else
    xinput disable 13
fi

exit 0
[/INDENT]

---

### Post by vanadium on 2021-04-10
Just use the standard "Keyboard settings" under "Settings" to assign the script to a shortcut key.

---

### Post by julio-netu on 2021-04-12
Hi! I tried to use a script assigned to a shortcut, it works but only to deactivate the touchpad. When I run the very same script on the terminal, it works properly

---

### Post by vanadium on 2021-04-14
Strange. IF the script runs well, it should run equally well from a shortcut. Can you activate the touchpad from a shortcut with only the command " xinput enable 13"?

---

