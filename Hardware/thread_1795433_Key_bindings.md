---
title: "Key bindings"
date: 2011-07-02
forum: Hardware
---

### Post by spintriae on 2011-07-02
I've recently installed Ubuntu on a Chromebook which doesn't have PageUp, PageDown, Home and End keys, so I decided to bind ctrl+up/down/left/right to Prior/Next/Home/End respectively. I've ran into a couple of bugs.

1. Ctrl+[key] doesn't respond. I must enter Ctrl+[key]+[key] (tap it twice) to get the expected result.

2. Prior and Next do nothing in text documents. In the browser, they switch between tabs. Running xmacrorec on my desktop tells me these are the PageUp/PageDown keys.

Here's the guide I'm using: [https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

Here are my .xbindkeysrc file:

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



"xbindkeys_show"
   control+shift + q

"xmacroplay-keys :0.0 KeyStr Prior"
   m:0x4 + c:111

"xmacroplay-keys :0.0 KeyStr Next"
   m:0x4 + c:116

"xmacroplay-keys :0.0 KeyStr Home"
   m:0x4 + c:113

"xmacroplay-keys :0.0 KeyStr End"
   m:0x4 + c:114

#
# End of xbindkeys configuration
```

Any ideas on how to resolve this?

Thanks.

---

### Post by spintriae on 2011-07-02
Looks like the Home and End events don't do as they're expected either. They work fine in the browser, but in gedit, they move the cursor to the beginning and end of the document, as opposed to the beginning and end of the line.

---

### Post by spintriae on 2011-07-06
bump

---

### Post by spintriae on 2011-08-11
Anyone?

---

