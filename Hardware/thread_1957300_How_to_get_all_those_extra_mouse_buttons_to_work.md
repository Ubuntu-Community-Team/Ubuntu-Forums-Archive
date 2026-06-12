---
title: "How to get all those extra mouse buttons to work"
date: 2012-04-12
forum: Hardware
---

### Post by $am on 2012-04-12
I just bought a logitech m510 mouse. It has extra buttons. The scroll wheel even has a side to side click thingy. I'm wondering how to make use of these extra buttons--in particular when activating compiz effects. I know button1 is left click, and button2 is right click, and I also see button3 (i think this is pressing down the scroll wheel) and button4 (i think this is scrolling up), but what about the buttons on the side of the mouse (there are 2 on the left side and none on the right, and I think the extra articulations on the scroll wheel count as some sort of buttons as well).

On a similar note, I remember back in 2010 when I was trying ubuntu that I was able to initiate the ever famous desktop cube by holding down button1 and button2 at the same time, but I can't find out how to set that up again (I know the cube has issues in the new desktop, but knowing how to activate SOMETHING using this combination would help me.)

---

### Post by Mark Phelps on 2012-04-12
See the attached link on remapping keys -- if xev shows button info when pressing the buttons, there is hope for you:

[http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys]("http://askubuntu.com/questions/24916/how-do-i-remap-certain-keys")

---

### Post by Xgen on 2012-04-12
I use the M510 on my laptop with a combination of 'xbindkeys' and 'xautomation'...both installable from synaptic or terminal.
I use a custom file in my home profile (.xbindkeysrc) that uses a combination of keys and buttons or remapping buttons to keys (e.g. back and forward). Here is an example .xbindkeysrc:

```

# use 'xev' to find key codes.
# xbindkeys for button assignments.
# xautomation (xte) for key assignments.

# b:1  -  left mouse button
# b:2  -  wheel button
# b:3  -  right mouse button
# b:4  -  mouse wheel up
# b:5  -  mouse wheel down
# b:6  -  mouse wheel left
# b:7  -  mouse wheel right
# b:8  -  back side button
# b:9  -  forward side button


# Exit Programs
"xte 'keydown Control_L' 'key F4' 'keyup Control_L' "
  b:2

# Shutdown
"sudo shutdown -h now" 
  Alt + Control + b:2
# Reboot
"sudo init 6" 
  Control + mod4 + b:2   #mod4 = Super
# Terminal
"gnome-terminal"
  Control + b:2
"gksu gnome-terminal"
  Alt + b:2

# Internet
"firefox-trunk -P trunk"
  b:8
"firefox -P firefox"
  Control + b:8

# File Browsers
"nautilus"
  b:9

# History Back & Forward
"xte 'keydown Alt_L' 'key Left' 'keyup Alt_L' "
  b:6
"xte 'keydown Alt_L' 'key Right' 'keyup Alt_L' "
  b:7


```

---

### Post by $am on 2012-04-13
I just noticed that firefox recognized the extra buttons already. The side to side scroll wheel clicks scroll side to side (who knew!) and the two buttons on the side are the back and forward buttons. I just wanted to know that "numbers" each of these buttons where so I can take advantage of them in other apps.

---

### Post by someonestolemyname on 2012-04-24
XGen: Just wanted to thank you for that. BTNX isn't in 12.04 anymore, which is what I used to use. It was nice that it was graphical, but this was impressively easy and fast to set up.

---

