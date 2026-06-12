---
title: "Configuring Logitech Performance MX mouse extra buttons..."
date: 2013-11-21
forum: Hardware
---

### Post by donotspamme532 on 2013-11-21
I'm trying to configure the extra buttons on my Logitech Performance MX mouse.  I have found other posts here and elsewhere that give ways to accomplish this.  Since the method that seems to come up most often is to use xautomation and xbindkeys, that is the method I have been trying to use.

Now the mouse itself already has functional back and forward buttons, but since I never use them for that purpose, I want to remap them.  This works perfectly well.  But what I cannot get to work is the remapping/reconfiguring of the buttons that do not have a basic functionality already.  Specifically, the application switcher (button 10 according to xev) and the zoom button (button 13 according to xev).  I have independently confirmed through terminal that the xte commands I'm using *do* work exactly as I want to create a left-click or a right-click as the case may be.

I'd really appreciate some help getting this to work.  Following is my current .xbindkeysrc file content, xev output for button 10 without xbindkeys running, and xev output for button 10 with xbindkeys running.  Also, while xbindkeys in theory could allow me to specify mouse buttons using the button release state, I don't think that would work in this case because the release state "0x10" is the same for all of the extra buttons 6-10 and 13 (note, there does not appear to be a button 11 or button 12 that I can find).  Also, please note that my remap of button 8 is working correctly.

.xbindkeysrc
```
# For the benefit of emacs users: -*- shell-script -*-
###########################
# xbindkeys configuration #
###########################
#
# Version: 1.8.5
#
# If you edit this file, do not forget to uncomment any lines
# that you change.
# The pound(#) symbol may be used anywhere for comments.
#
# To specify a key, you can use 'xbindkeys --key' or
# 'xbindkeys --multikey' and put one of the two lines in this file.
#
# The format of a command line is:
#    "command to start"
#       associated key
#
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h
# The XK_ is not needed.
#
# List of modifier:
#   Release, Control, Shift, Mod1 (Alt), Mod2 (NumLock),
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll).
#
#
# The release modifier is not a standard X modifier, but you can
# use it if you want to catch release events instead of press events
#
# By defaults, xbindkeys does not pay attention with the modifiers
# NumLock, CapsLock and ScrollLock.
# Uncomment the lines above if you want to pay attention to them.

#keystate_numlock = enable
#keystate_capslock = enable
#keystate_scrolllock= enable




##################################
#      Examples of Commands      #
##################################

#"xbindkeys_show" 
#  control+shift + q
#
# set directly keycode (here control + f with my keyboard)
#"xterm"
#  c:41 + m:0x4
#
# specify a mouse button
#"xterm"
#  control + b:2
#
#"xterm -geom 50x20+20+20"
#   Shift+Mod2+alt + s
#
## set directly keycode (here control+alt+mod2 + f with my keyboard)
#"xterm"
#  alt + c:0x29 + m:4 + mod2
#
# Control+Shift+a  release event starts rxvt
#"rxvt"
#  release+control+shift + a
#
# Control + mouse button 2 release event starts rxvt
#"rxvt"
#  Control + b:2 + Release

##################################
##################################




##################################
#  ReMap Logitech PerformanceMX  #
##################################

#bind lower thumb (app-switcher) button to left-click
"xte 'mouseclick 1'"
  b:10

#bind upper thumb (zoom) button to right-click
"xte 'mouseclick 3'"
  b:13

#bind back button to windows list grid
"xte 'keydown Control_L' 'key F10' 'keyup Control_L'"
  b:8

##################################
##################################




##################################
# End of xbindkeys configuration #
##################################


```

xev output *without* xbindkeys running
```
EnterNotify event, serial 36, synthetic NO, window 0x400001,
    root 0xde, subw 0x0, time 6559273, (17,29), root:(981,855),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  4294967262 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 36, synthetic NO, window 0x400001,
    root 0xde, subw 0x400002, time 6559369, (17,29), root:(981,855),
    state 0x10, button 10, same_screen YES

LeaveNotify event, serial 36, synthetic NO, window 0x400001,
    root 0xde, subw 0x0, time 6559369, (17,29), root:(981,855),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

```

xev output *with* xbindkeys running
```
EnterNotify event, serial 36, synthetic NO, window 0x5400001,
    root 0xde, subw 0x5400002, time 6708717, (23,22), root:(987,848),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  4294967262 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

```

Please note that there is no LeaveNotify event triggered when xbindkeys is running, nor are there any ButtonPress or ButtonRelease events triggered.

It seems to me that perhaps xbindkeys doesn't work correctly with the b:10 or b:13 input, but I'm not sure why this would be the case.  One post for how to configure this specific mouse uses those two buttons, but assigns them to keyboard combinations instead of mouseclicks, but I don't see why this should be an issue since it is not xbindkeys that is sending the input signals, but rather it makes a call to xautomation through the xte command and xautomation sends the signals.  Since I've confirmed that the xautomation commands *do* work, I'm not sure what the problem could be... basically, xbindkeys seems to work, xautomation seems to work, xbindkeys seems to successfully call xautomation, and the system does recognize and register button events from the two buttons in question (unless xbindkeys is running), so the buttons themselves seem to work.  I'm pretty new to linux, and I'm now at a loss for what to try next.

If anyone has any ideas how I can get this working, I'd really appreciate it.

Thanks,
Drake

---

### Post by donotspamme532 on 2013-11-22
No one has any ideas?  Please, I'd really like to get this working.  Even suggestions of other software for mouse remapping that has been useful to people would be welcome.

Thanks,
Drake

---

### Post by donotspamme532 on 2013-11-23
Really, I'd like to get this working please.  There has to be somebody around here that knows something about making extra mouse buttons work.  Please help.

Thanks,
Drake

---

