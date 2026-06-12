---
title: "Xbindkeys and mouse button 10"
date: 2012-01-06
forum: Hardware
---

### Post by crscoles on 2012-01-06
Hi Everyone,

I am hoping someone out there can help with this issue in Ubuntu 11.10 running Gnome3-shell.  Here is the synopsis.  

I recently bought a Logitech M705 Mouse and want to get the thumb button (b:10) to act as the super key.  I have the following line in my .xbindkeysrc. 

#Activities Button
"xte 'key Super_L'" 
  b:10

but is doesn't seem to work.  If I run the xte command in terminal, it works fine. When xbindkeys is not running xev sees b:10 without any problems.  When xbindkeys is running, xev sees the following when b:10 is pressed:

LeaveNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x14f, subw 0x0, time 13177611, (161,149), root:(164,264),
    mode NotifyGrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

FocusOut event, serial 34, synthetic NO, window 0x3400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x3400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  79  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

EnterNotify event, serial 34, synthetic NO, window 0x3400001,
    root 0x14f, subw 0x0, time 13179915, (161,149), root:(164,264),
    mode NotifyUngrab, detail NotifyAncestor, same_screen YES,
    focus YES, state 0

Any ideas what is causing this?  Buttons 8 & 9 function perfectly as workspace up and down with the following commands.

# workspace up
"xte 'keydown Control_L' 'keydown Alt_L' 'key Up' 'keyup Control_L' 'keyup Alt_L'"
  b:9

# workspace down
"xte 'keydown Control_L' 'keydown Alt_L' 'key Down' 'keyup Control_L' 'keyup Alt_L'"
  b:8

Chris

---

### Post by escentrix on 2012-02-23
Also having the same trouble.

I like having one of my side buttons open my activities screen in Gnome3

My current **.xbindkeysrc** is very simple:
```
"xte 'key Super_L'"
b:8
```

Like crscoles said, **xte 'key Super_L'** works perfectly in termial. I have also verified with xev that I am using the correct mouse button. If I modify my **.xbindkeysrc** to:
```
"xte 'key BackSpace'"
b:8
```
then it works; my side button acts as a backspace. So, I know that everything *should* work!

Here's the output of **xbindkeys -v**
```
**$ xbindkeys -v**
displayName = :0
rc file = /home/myhome/.xbindkeysrc
rc guile file = /home/myhome/.xbindkeysrc.scm
getting rc guile file /home/myhome/.xbindkeysrc.scm.
WARNING : /home/myhome/.xbindkeysrc.scm not found or reading not allowed.
1 keys in /home/myhome/.xbindkeysrc

min_keycode=8     max_keycode=255 (ie: know keycodes)
"xte 'key Super_L'"
    m:0x0 + b:8   (mouse)
starting loop...
Button press !
e.xbutton.button=8
e.xbutton.state=16
"xte 'key Super_L'"
    m:0x0 + b:8   (mouse)
got screen 0 for window 15a
Start program with fork+exec call
Button release !
e.xbutton.button=8
e.xbutton.state=16
```

I read somewhere that there may be an issue with the super key passing through. If anyone can shed some light on this, though, it would be greatly appreciated!

Edit: Woring with Ubuntu 10.04 Alpha 2 x64, Gnome 3.3.90, Kernel 3.2.0-17, xbindkeys 1.8.5, xte v1.03

---

### Post by escentrix on 2012-02-23
Good news crscoles! After writing that post I did more internet scouring and playing with configs and found what we were looking for!

I derived my solution from [http://www.ict.griffith.edu.au/anthony/info/X/Event_Handling.txt]("http://www.ict.griffith.edu.au/anthony/info/X/Event_Handling.txt")
(Specifically the *_Generating X Keyboard Events (Global Keyboard Macros)._* section.)

Also reading through all the configs and documantation over at [http://www.nongnu.org/xbindkeys/]("http://www.nongnu.org/xbindkeys/")

To summarize, when xbindkeys sees our mouse button pressed it passes it to xte, BUT in reality my mouse button 8 (your mouse 10) is still in the keydown position. X sees this as **'mouse 8 + left super'** and not just left super, which is not the same thing!

**_Solution!_**
Only send the xte super key action after the mouse key has been released.
```
"xte 'key Super_L'"
b:8 **+ release**
```
*(of coarse, in your case make it b:10)*

Hopefully that helps!

---

