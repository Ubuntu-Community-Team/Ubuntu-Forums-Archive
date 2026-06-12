---
title: "Acer spin sp111-33"
date: 2019-02-07
forum: Hardware
---

### Post by johnejurgess on 2019-02-07
I installed 18.04.1 on this laptop.  I have been unable to get the touchscreen to work.  This is a 2 in 1 laptop- it would be nice to be able to put it in tablet mode.  Here are some output of some of the commands

[COLOR=#424242][FONT=&quot]Bus 001 Device 004: ID 8087:0aaa Intel Corp. [/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]Bus 001 Device 003: ID 0bda:5648 Realtek Semiconductor Corp. [/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller[/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and 


[/FONT][/COLOR][COLOR=#424242][FONT=&quot]john@johnmini[/FONT][/COLOR][COLOR=#424242][FONT=&quot]:/proc$ xinput[/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]&#9121; Virtual core pointer                        id=2    [master pointer  (3)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]&#9116;   &#8627; 06CB0001:00 06CB:CD3F Touchpad              id=12    [slave  pointer  (2)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]&#9123; Virtual core keyboard                       id=3    [master keyboard (2)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]    &#8627; Power Button                                id=6    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]    &#8627; Video Bus                                   id=7    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]    &#8627; Power Button                                id=8    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]    &#8627; VGA WebCam: VGA WebCam                      id=9    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]    &#8627; Acer WMI hotkeys                            id=11    [slave  keyboard (3)][/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]john@johnmini[/FONT][/COLOR][COLOR=#424242][FONT=&quot]:/proc$ xrandr[/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192[/FONT][/COLOR]
[COLOR=#424242][FONT=&quot]eDP-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 256mm x 144mm
[/FONT][/COLOR][COLOR=#424242][FONT=&quot]
any ideas would be helpful.  I have also tried Fedora and same issue..

[/FONT][/COLOR]

---

