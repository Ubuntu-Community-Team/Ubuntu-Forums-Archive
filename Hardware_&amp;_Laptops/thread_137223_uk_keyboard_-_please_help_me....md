---
title: "uk keyboard - please help me..."
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by chris90uk on 2006-02-27
ubuntu seems to think i have a us keyboard! e.g. when i try to do a '@' sign i actually get a ' " ' sign...and when i try to change it to uk layout in the keyboard options, it says that its uk layout, but in practice nothing changes and the keys are still wrong....


please help me get the keyboard right? pweese?

---

### Post by r4ik on 2006-02-27
Try system - preferences - keyboard remove us and add uk.
Good luck.

---

### Post by chris90uk on 2006-02-27
[QUOTE=r4ik]Try system - preferences - keyboard remove us and add uk.
Good luck.[/QUOTE]

aww i tried that but cheers anyway

---

### Post by r4ik on 2006-02-27
Oke leave us in add uk mark it and move it to the top you should see your
desktop "working" a little.

---

### Post by chris90uk on 2006-02-27
[QUOTE=r4ik]Oke leave us in add uk mark it and move it to the top you should see your
desktop "working" a little.[/QUOTE]

no luck...

---

### Post by r4ik on 2006-02-27
In Synaptic do you have xkeyboard-config installed ?

---

### Post by chris90uk on 2006-02-27
[QUOTE=r4ik]In Synaptic do you have xkeyboard-config installed ?[/QUOTE]

i got none of that....sorry i never said - i need things explained in dumbed down terms i'm not exactly proficient in this stuff

---

### Post by r4ik on 2006-02-27
System - management - synaptic right click it and put it to the panel.
You are gonna need that one.
And do the search.
If in the meantime a strong command-line user is watching to solve this
hop on the bus please. :)

---

### Post by marmite1972 on 2007-01-10
Hope this helps, works for me

# setxkbmap -keymap xkb_keymap "gb"
# setxkbmap -rules xorg -model pc104 -layout gb

---

### Post by F W Adams on 2007-11-03
I had the same problem, with the " @ characters, the post above came up with an error message when I tried it. I solved it like this

Go into terminal

sudo gedit /etc/X11/xorg.conf

Look for some thing like:

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

The name referring to the keyboard may vary

Insert two lines
  Option "XkbModel" "pc102"
  Option "XkbLayout" "gb"

making

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
	Option "XkbModel" "pc102"
	Option "XkbLayout" "gb"
EndSection

save the file, reboot

---

