---
title: "Mapping buttons to Up and Down keys on keyboard"
date: 2010-12-28
forum: Hardware
---

### Post by Checkka on 2010-12-28
I have a few unmapped buttons on my tablet that I want to map to the Up and Down keys on my keyboard (for scrolling through documents).  Ideally pressing the buttons would be equivalent to pressing the up arrow and down arrow on my keyboard.  

I've tried assigning the buttons with 'Keyboard Shortcuts' using 'xdotool' and 'xsendkeys'.  Neither method appears to work.  Anyone have any suggestions?

---

### Post by pi/roman on 2010-12-29
You can figure out the keycode for your unmapped buttons with xev.
Just type xev in terminal, press enter, then press the unnassigned keys you want to use and look for the keycode in the output and write it down.

Then use xmodmap to assign instructions to those keys.  For instance, say you found a key you want to use and it has a keycode of 256.  Use xmodmap in this format:
```
xmodmap -e 'keycode 256 = Up NoSymbol Up'
```There is actually no such keycode as 256 so this will not do anything but if there were it would assign the up arrow to that key. Likewise:
```
xmodmap -e 'keycode 257 = Down NoSymbol Down'
```would assign the down arrow to the key using keycode 257 if that existed but get your actual keycodes using xev.

You can see a listing of all your key assignments by using:
```
xmodmap -pke
```Then you can create a file where they will be loaded upon boot up. press Alt/f2 for the "run application" dialog then enter "gksudo gedit .Xmodmap" which should create the file .Xmodmap in your home folder.  If it doesn't then it needs to be placed there. Edit .Xmodmap in the following format:
```
keycode 256 = Up NoSymbol Up
keycode 257 = Down NoSymbol Down
```using of course your own keycodes you found using xev.  Whatever you have in .Xmodmap should take hold after restarting.

---

