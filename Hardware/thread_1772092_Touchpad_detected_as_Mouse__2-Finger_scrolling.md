---
title: "Touchpad detected as Mouse / 2-Finger scrolling"
date: 2011-05-31
forum: Hardware
---

### Post by Andreas Riedel on 2011-05-31
Hello Users.

Since I have installed the newest Ubuntu 11.04 on my new Dell 6520 all works great, even the Touchpad. But the problem is, that the Touchpad is detected as Mouse. And therefore I'm unable to activate the 2-finger scrolling on Touchpad.

Any idea?

TIA
  Andreas

---------------------------------
Found in other solutions:

[LIST]
[*]Editing /etc/xorg.conf inpossible, file doesn't exist.
[*]Run synclient ended up in 'Couldn't find synaptics properties. No synaptics driver  loaded?'
[/LIST]
---------------------------------
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; [COLOR=Magenta]ImPS/2 ALPS GlidePoint                  	id=11	[slave  pointer  (2)][/COLOR]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=12	[slave  keyboard (3)]

even if glidepoint is detected, the folder Touchpad is missing.

---

### Post by FiyM on 2011-07-20
Maybe you could goof in gconf-editor: /desktop/gnome/peripherals/touchpad
I have a similar problem. But mine is actually recognized as a mouse...
```
~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB 2.0 UVC VGA WebCam                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

```

---

### Post by dixoncx on 2011-08-14
Am also has same problem...

"xinput list" gives:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sony Visual Communication Camer             id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```

---

### Post by Mattlcape on 2011-08-16
Bump. 

Same on my samsung NF110. recognised as ps/2 mouse

---

### Post by Psycho67 on 2011-08-25
bump.  looking for the same answer.

---

### Post by Clicksights on 2011-09-26
Bumb

msi dx460dx also seen as a mouse not a touchpad.

xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

seems like a lot of people have problems with there touchpad...

---

### Post by MarjaE on 2011-09-27
If you're worried about scrolling ... your touchpad WORKS (!) except for that one little thing (!)?

Mine doesn't work, it just causes trouble, and won't even stay turned off. The system detects the Alps Gidepoint as a PS/2 mouse, and detects pressure variations as button1 clicks. I keep turning it off so I can type without it interfering. And I have a mouse so I can move the cursor without it randomly clicking along the way.

---

