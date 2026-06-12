---
title: "Configuring Logitech Performance MX mouse in Ubuntu 14.10"
date: 2014-12-02
forum: Hardware
---

### Post by i_am_a_toothbrush on 2014-12-02
Hi&#8212;I have a Logitech Performance MX, and I'd like to configure the extra buttons so that they work in Ubuntu.
  I have searched before posting, but everything I find is at least two years old and doesn't work. Following [a guide]("http://forums.logitech.com/t5/Mice-and-Pointing-Devices/Guide-for-setup-Performance-MX-mouse-on-Linux-with-KDE/td-p/517167") on the Logitech forum, I've installed xbindkeys and have created .xbindkeysrc. However, the step after that doesn't work:[INDENT] 
7) We need to add our button-to-key configurations. For example, I have the following:
  [SIZE=2]
#Back[/SIZE]
  "xte 'keydown Alt_L' 'key Left' 'keyup Alt_L'" b:8
  [SIZE=2]
#Forward[/SIZE]
"xte 'keydown Alt_L' 'key Right' 'keyup Alt_L'"  b:9
  [B][SIZE=2]
[/SIZE][/B][SIZE=2]#Present desktops[/SIZE]
"xte 'keydown Control_L' 'key F8' 'keyup Control_L'"  b:13
  [B][SIZE=2]
[/SIZE][/B][SIZE=2]#Present windows[/SIZE]
"xte 'keydown Control_L' 'key F10' 'keyup Control_L'"  b:10


 [/INDENT]
Buttons 8 and 9&#8212;back and forward&#8212;worked without having had to install  xbindkeys. I'm looking to program button 13 as a shortcut to the  Expose-like program (Super+W). I'm not sure what I want to do with  button 10, but I'd appreciate it if somebody could help me configure  button 13 and teach me how it is done so that I can configure button 10  on my own later.
  Thanks.

---

### Post by i_am_a_toothbrush on 2014-12-03
If it helps, here is my .xbindkeysrc file:

> # For the benefit of emacs users: -*- shell-script -*-
###########################
# xbindkeys configuration #
###########################
#
# Version: 1.8.6
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

# The release modifier is not a standard X modifier, but you can
# use it if you want to catch release events instead of press events

# By defaults, xbindkeys does not pay attention with the modifiers
# NumLock, CapsLock and ScrollLock.
# Uncomment the lines above if you want to pay attention to them.

#keystate_numlock = enable
#keystate_capslock = enable
#keystate_scrolllock= enable

# Examples of commands:

"xbindkeys_show" 
  control+shift + q

# set directly keycode (here control + f with my keyboard)
#"xterm"
#  c:41 + m:0x4

# specify a mouse button
#"xterm"
#  control + b:2

#"xterm -geom 50x20+20+20"
#   Shift+Mod2+alt + s
#
## set directly keycode (here control+alt+mod2 + f with my keyboard)
#"xterm"
#  alt + c:0x29 + m:4 + mod2
#
## Control+Shift+a  release event starts rxvt
#"rxvt"
#  release+control+shift + a
#
## Control + mouse button 2 release event starts rxvt
#"rxvt"
#  Control + b:2 + Release

"xte 'key Control_L'"
b:10 

##################################
# End of xbindkeys configuration #
##################################

---

