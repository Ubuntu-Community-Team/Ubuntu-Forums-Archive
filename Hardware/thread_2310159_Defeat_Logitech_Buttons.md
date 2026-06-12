---
title: "Defeat Logitech Buttons"
date: 2016-01-16
forum: Hardware
---

### Post by lile001 on 2016-01-16
I'm using a Logitech M705 mouse in a CAD application, and it has an annoying issue.  In Bricscad (really good ACAD clone by the way) one needs to press the scroll button to pan.  This is common to many auto-cad-like programs and I need to keep it this way.  (I have to switch between several computers and various operating systems and CAD programs - it is a whole lot easier if the buttons always do the same thing at each station.)  

But this mouse also has two very sensitive side buttons on the scroll-press, and activating them zooms in and out.  It is almost impossible to press the scroll wheel button fast without activating one of the side buttons.  In CAD, panning is a very frequent operation, and it is annoying as heck if the program zooms so far your work is invisible every time you pan.  Bricscad has only very limited mouse-button customization.   So I had to look outside the program for some help.  

So I decided to de-activate those pesky side buttons.  I looked at several programs including solaar, and lomoco.  Neither of them could accomplish this. 

I'm not posting this because I need an answer, particularly, but because I didn't find anyone else with exactly this problem on the interwebs and these forums, but I did find solutions just similar enough that they would almost work here.  So maybe this hack will be useful for the next guy to face this problem.  Meanwhile, someone will perhaps look at this and say "Here is a better way!"  [ This thread]("http://askubuntu.com/questions/556345/configure-logitech-mouse-with-xbindkeys") comes pretty close, but not quite spot on, to what I need.  


 Here is what I have tried that seemed to work - someone else can probably suggest a better way: 

Installed xbindkeys
```
sudo apt-get install xvkbd xbindkeys

```

Configure xbindkeys with a default configuration file:

```
[COLOR=#000000][FONT=courier new]xbindkeys --defaults > ./.xbindkeysrc[/FONT][/COLOR]
```

This configuration file starts with everything commented out. 

Run xev to capture relevant mouse input:

Xev:[INDENT]ButtonRelease event, serial 37, synthetic NO, window 0x5200001,[/INDENT]
[INDENT]    root 0x258, subw 0x5200002, time 188574051, (41,53), root:(930,131),[/INDENT]
[INDENT]    state 0x10, **button 7**, same_screen YES[/INDENT]
[INDENT]
[/INDENT]
[INDENT]ButtonRelease event, serial 37, synthetic NO, window 0x4400001,[/INDENT]
[INDENT]    root 0x258, subw 0x4400002, time 188630895, (34,34), root:(35,69),[/INDENT]
[INDENT]    state 0x10, **button 6**, same_screen YES[/INDENT]

... and a lot of other irrelavent garbage

Button 6 and 7 are the ones bedeviling me.  

Install xte which allows one to send keyboard and mouse events
```
 sudo apt-get install xte 
```

Now we can use xte to send a different code if button 6 and 7 are pressed.  Here is where I am greatly cponfused - don't know how to tell xte to send "nothing".  I tried sending "button6 up" instead and this hack seems to be working.

add this line to ./xbindkeysrc


```
## Control the B:6 key (scroll side button) to do nothing (send the button 6 up)
"xte 'mouseup 6'"
 b:6


## Control the B:7 key (scroll side button) to do nothing (send the button 7 up)
"xte 'mouseup 7'"
 b:7


```

Now test it: 

```
killall xbindkeys  && xbindkeys


xev 

```

Now operate the left and right scroll wheel in the little box put up by xev.  You will find it is reading a different output from the mouse, not button 6 & 7.

Then 
```
killall xbindkeys 
xev

```

and you find pressing the side scroll buttons once again produces the button6 and button 7 signal. 

Of course add xbindkeys to startup to make this a permanent change.  

OK, how can you improve on this hack? So far it seems to work OK in Bricscad, although the scroll wheel is still a little oversensitive.  Is there a better way to defeat one of the mouse buttons?  Is there a different command I should be sending to xte - one that literally does nothing?


Another pesky thing about the Logitech M705 is the scroll wheel keeps going after you stop rolling it.  For a normal webpage it just rolls to the bottom of the page, but in CAD it continues to zoom either to infinity or infinitesimal.  Is this an issue that can be fixed with xinput, or tricky xbindkeys?  no.  There is a big dumb button on top of the mouse that stops it from scrolling after you let go.   Duh?  Who'da thunk it.

---

### Post by bwanaaa on 2016-02-13
I found that xte is flakey.
My sequence for mapping the the thumb button of my logitech 518 to 'control W' to close tabs and windows never worked well with xte not sequencing properly.
For example this failed:
```
"xte 'keydown Control_L' 'w' 'keyup Control_L'"
 b:8
```

as did this:
```
"xte 'keydown Control_L' 'w' 'keyup Control_L'"
 b:8 + release
```

I also noticed that xte was SLOOOW.
I tried xvkbd and it works well.

OF course you have to get xvkbd with this:
```
sudo apt-get install xvkbd
```

Put this in your .xbindkeysrc file in your home directory
```

"xvkbd  -text '\C\[w]'"
m:0x0 + b:8
```


and restart xbindkeys
pkill -f xbindkeys  && xbindkeys

---

