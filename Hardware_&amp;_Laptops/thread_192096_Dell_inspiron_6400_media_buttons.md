---
title: "Dell inspiron 6400 media buttons"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by ponkarthik on 2006-06-08
Hi ,

  I recently installed Ubuntu 6.06. Seems to be absolutely great. My wireless and card reader were working out of the box. 

 I was able to use the media buttons on the front in Ubuntu( the mute,volume,stop etc) out of the box. They do not work in Kubuntu. Can anyone tell me how to make it work.

Regards and Thanks in advance

Karthik

---

### Post by spiffytech on 2006-08-05
I now have a Dell Inspiron e1405, and I, too, have the media buttons. My volume buttons work, but not the payback controls. Is there a way for me to customize the mappings for these buttons to match the hotkeys for controlling Amarok? (e.g. the "play/pause" button equals pushing "win-c")

---

### Post by patrickfromspain on 2006-08-05
It's a kde issue. On my laptop, Toshiba L10-161, and on my desktop with genius keyboard, the same happens: gnome works, but xfce and kde don't.

---

### Post by spiffytech on 2006-08-05
I'm using Ubuntu, not Kubuntu, so that shouldn't be a problem.

---

### Post by Frostmourne on 2006-08-05
Try going into Preferences > Keyboard Shortcuts, clicking the appropiate action, and pressing the corresponding media button. That's all I had to do for my E1505.

---

### Post by spiffytech on 2006-08-05
That worked perfectly for Rythmbox! I would prefer the buttons worked in Amarok, but I'll give Rythmbox a a try and see how I like it.

---

### Post by spiffytech on 2006-08-05
*smack's own head* All I had to do to make them work in Amarok was go (in Amarok) to Settings -> Configure Global Shortcuts and create an alternate shortcut for each by pushing the button. Now all I need to figure out is how to set Amarok as the default media player, so that when I hit the "MediaDirect" button, Amarok launches instead of RythmBox.

---

### Post by ramzai on 2007-02-19
I've been fighting with my 6400 media buttons for a while, so here is a "quick'n'dirty" solution for (at least) amarok.

My situation: Gnome, I want to use amarok, mute/sound up/sound down work fine, play-pause/prev/next/stop/MediaDirect work in Gnome, but don't work in KDE apps/amarok.

```
aptitude install xbindkeys xbindkeys-config
```

After that you can manually set up xbindkeys via xbindkeys-config utility, or use my config (save it a $HOME/.xbindkeysrc)

```
###########################
# xbindkeys configuration #
###########################
#
# Version: 0.1.3
#
# If you edit this, do not forget to uncomment any lines that you change.
# The pound(#) symbol may be used anywhere for comments.
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h 
# The XK_ is not needed. 
#
# List of modifier (on my keyboard): 
#   Control, Shift, Mod1 (Alt), Mod2 (NumLock), 
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll). 
#
# Another way to specifie a key is to use 'xev' and set the 
# keycode with c:nnn or the modifier with m:nnn where nnn is 
# the keycode or the state returned by xev 
#
# This file is created by xbindkey_config 
# The structure is : 
# # Remark 
# "command" 
# m:xxx + c:xxx 
# Shift+... 




#keystate_numlock = enable
#keystate_scrolllock = enable
#keystate_capslock = enable



#MediaDirect
"amarok"
    m:0x0 + c:237
    NoSymbol 

#Play/Pause
"dcop amarok player playPause"
    m:0x0 + c:162
    XF86AudioPlay 

#Prev
"dcop amarok player prev"
    m:0x0 + c:144
    XF86AudioPrev 

#Next
"dcop amarok player next"
    m:0x0 + c:153
    XF86AudioNext 

#Stop
"dcop amarok player stop"
    m:0x0 + c:164
    XF86AudioStop 

#
# End of xbindkeys configuration
```

Finally, add xbindkeys to Gnome startup (Control Center -> Sessions)

---

### Post by vesaliuz on 2008-05-29
WOW

Worked like a charm

thanks :guitar:

---

