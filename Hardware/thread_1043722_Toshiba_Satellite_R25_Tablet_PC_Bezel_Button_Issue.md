---
title: "Toshiba Satellite R25 Tablet PC Bezel Button Issues"
date: 2009-01-18
forum: Hardware
---

### Post by vilkacis on 2009-01-18
Finally fed up with how muggy my WinXP install was getting, I decided to re-install. My Tablet PC didn't ship with a recovery CD or an OS CD, and all attempts to get the right version of WinXP Tablet PC Edition that will work with my product key failed.

Long story short, I've installed Ubuntu, and it's pretty much doing all the things I use this Tablet PC for. The Pen works, I can configure the Wacom settings, I've even got a little script that I can run to rotate the display for when I'm in Tablet Mode. Even the Power-save, lid, Media and Fn keys are working.

However, the keys on the bezel are... odd. I've not been able to figure out how to configure them. The thing is, they're clearly recognized by the system. By default, the 'd-pad' (up/down/left/right) functions by setting a zoom-level, depending on which way I press it. 'Up' zooms in, 'Left' zooms in even closer, 'Down' returns the zoom-level to normal and 'Right' doesn't do anything. And the key which, in windows, would normally pull up TaskManager now brings up a window that will shut down the computer.

So they are clearly being recognized by the system. But I have no idea how to configure them, nor do I know what program or script is causing the zooming so I could turn it off. Theoretically I could use any number of hotkey programs to bind these to the d-pad directions they're supposed to be bound to, and set one of the keys up to do the screen rotations for me. But unless I turned off this default 'zooming' feature, it would just do both.

What program does this zooming? Can I turn it off, so I can set these to something else? Where would I configure these keys? I've scoured the boards and documentation as much as I could. The weird thing is that they work, but I don't know where or by what they're working. Usually it can also detect the rotation when I fold it down upside-down in Tablet mode, but I'd settle just for having a working d-pad and rotation button.

Anyone have any experience with this? Or have any idea what program is doing this zooming?

---

### Post by Favux on 2009-01-19
Hi vilkacis,

I think first you'd want to find the key codes the bezel keys are producing.  In a terminal type "xev" and then press the bezel keys and record their key codes.

Then go to keyboard shortcuts, or compiz or metaticity and see if the key code for the bezel key is associated with zoom or whatever command.

A little information for key binding is located at:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

Hope this is helpful.

---

### Post by vilkacis on 2009-01-21
Thanks for the response Favux.

I can't make heads or tails of the xev output. I'll post it here in two cuts, and maybe you can help decypher it. I had to increase the number of lines it saves so I could fit all of this.

I did up, left, right, down, 'd-pad press', rotation button, 'key' button, browser button, email button and got this:

```

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1237039, (248,-37), root:(255,14),
    state 0x0, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967253 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1237200, (111,-28), root:(118,23),
    state 0x40, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1237937, (-6,-51), root:(1,0),
    state 0x0, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1238101, (-7,-15), root:(0,36),
    state 0x40, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1238708, (-7,-2), root:(0,49),
    state 0x0, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1238709, (-7,-2), root:(0,49),
    state 0x40, keycode 13 (keysym 0x34, 4), same_screen YES,
    XLookupString gives 1 bytes: (34) "4"
    XmbLookupString gives 1 bytes: (34) "4"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1238927, (-7,-2), root:(0,49),
    state 0x40, keycode 13 (keysym 0x34, 4), same_screen YES,
    XLookupString gives 1 bytes: (34) "4"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1238930, (-7,-2), root:(0,49),
    state 0x40, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1239558, (-7,-2), root:(0,49),
    state 0x0, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           64  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1239759, (-7,-2), root:(0,49),
    state 0x40, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1241138, (-7,-2), root:(0,49),
    state 0x0, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1241139, (-7,-2), root:(0,49),
    state 0x40, keycode 14 (keysym 0x35, 5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"
    XmbLookupString gives 1 bytes: (35) "5"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1241140, (-7,-2), root:(0,49),
    state 0x40, keycode 14 (keysym 0x35, 5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1241145, (-7,-2), root:(0,49),
    state 0x40, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1243342, (-7,-2), root:(0,49),
    state 0x0, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1243343, (-7,-2), root:(0,49),
    state 0x40, keycode 15 (keysym 0x36, 6), same_screen YES,
    XLookupString gives 1 bytes: (36) "6"
    XmbLookupString gives 1 bytes: (36) "6"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1243344, (-7,-2), root:(0,49),
    state 0x40, keycode 15 (keysym 0x36, 6), same_screen YES,
    XLookupString gives 1 bytes: (36) "6"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1243349, (-7,-2), root:(0,49),
    state 0x40, keycode 134 (keysym 0xffec, Super_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1244165, (-7,-2), root:(0,49),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1244166, (-7,-2), root:(0,49),
    state 0x4, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   0   0   0   32  0   0   0   1   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1244411, (-7,-2), root:(0,49),
    state 0xc, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x6600001,
    root 0x7e, subw 0x0, time 1244414, (-7,-2), root:(0,49),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 34, synthetic NO, window 0x6600001,
    atom 0x19d (_NET_WM_ICON_GEOMETRY), time 1244630, state PropertyNewValue

FocusIn event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyNormal, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  126 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 34, synthetic NO, window 0x6600001,
    atom 0x19d (_NET_WM_ICON_GEOMETRY), time 1248392, state PropertyNewValue

ConfigureNotify event, serial 34, synthetic NO, window 0x6600001,
    event 0x6600001, window 0x6600001, (5,49), width 178, height 178,
    border_width 2, above 0x180000a, override NO

ConfigureNotify event, serial 34, synthetic YES, window 0x6600001,
    event 0x6600001, window 0x6600001, (5,49), width 178, height 178,
    border_width 2, above 0x2601c78, override NO

ConfigureNotify event, serial 34, synthetic NO, window 0x6600001,
    event 0x6600001, window 0x6600001, (5,49), width 178, height 178,
    border_width 2, above 0x180000a, override NO

ConfigureNotify event, serial 34, synthetic YES, window 0x6600001,
    event 0x6600001, window 0x6600001, (5,49), width 178, height 178,
    border_width 2, above 0x2601c78, override NO

ConfigureNotify event, serial 34, synthetic NO, window 0x6600001,
    event 0x6600001, window 0x6600001, (5,49), width 178, height 178,
    border_width 2, above 0x180000a, override NO

FocusOut event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyGrab, detail NotifyNonlinear

ConfigureNotify event, serial 34, synthetic YES, window 0x6600001,
    event 0x6600001, window 0x6600001, (5,49), width 178, height 178,
    border_width 2, above 0x2601c78, override NO

FocusIn event, serial 34, synthetic NO, window 0x6600001,
    mode NotifyUngrab, detail NotifyNonlinear

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ConfigureNotify event, serial 34, synthetic NO, window 0x6600001,
    event 0x6600001, window 0x6600001, (5,49), width 178, height 178,
    border_width 2, above 0x180000a, override NO

ConfigureNotify event, serial 34, synthetic YES, window 0x6600001,
    event 0x6600001, window 0x6600001, (5,49), width 178, height 178,
    border_width 2, above 0x2601c78, override NO

ClientMessage event, serial 34, synthetic YES, window 0x6600001,
    message_type 0x13d (WM_PROTOCOLS), format 32, message 0x13b (WM_DELETE_WINDOW)

```

There's some extra keystrokes at the end, as I was trying to get the browser and e-mail buttons to do anything. They don't produce any response in xev.

I have no idea how to check the shortcut keys in metacity and/or compiz. I've checked the default Keyboard Shortcuts under System > Preferences > Shortcut Keys, but nothing is listed under 'zoom', so I'm still not sure what is doing that.

Any of the above help?

---

### Post by Favux on 2009-01-21
Hi vilkacis,

I by no means claim to be an xev or key mapping guru.  But you said you had 9 keys, and I count 6 keycodes.
```
keycode 134
keycode 13
keycode 14
keycode 15
keycode 37
keycode 64
```
So it would seem you should be able to bind some keys.  Although tedious it might be helpful to do one bezel key at a time in xev.  Then you could annotate it, above each output saying "I pressed the up key" or whatever.  Then you could assemble it.  Because you're right, its easy to loose track in that output.  And I can't tell which key associates with what output.

If you have Compiz the key bindings should be in System>Preferences>CompizConfig Settings Manager.  In the General Options you'll see a tab called Key bindings.  I haven't used metacity but I think there is a similar section.  If you don't see either go to System>Preferences>Main Menu and see if you have to check its box to enable it the the menus.

---

### Post by Favux on 2009-01-23
Hi vilkacis,

I thought I'd mention in my System>Preferences>Keyboard Shortcuts in the Desktop section at the bottom are Zoom In and Zoom Out.  They are labeled disabled in my system.  Are they labeled disabled in yours?

---

### Post by DudeMiester on 2009-01-28
I had the same problem and I figured it out. The Compiz enhanced zoom plugin uses super-1/2/3 shortcuts, causing the tablet PC button to trigger zoom levels. I just disabled the plug in as I have no use for it, but you can remap them to something else if you desire.

Oh, you'll have to install the compizconfig-settings-manager package if you haven't already.

Incidentally, the keycodes generated by standard tablet pc buttons are all Super_R (aka Mod4) + :
1 - up
2 - left
3 - down
4 - right
5 - direction press
6 - rotate button

The "key" button produces crtl-alt-del.

Right now I'm using xbindkeys to configure them, but I need to create a script for rotation yet. I'm a major linux noob, so any help on how to generate a keyboard event via a command? For example, I want my up button to produce the up keypress/keyup events, but what command can I use for that?

EDIT:
Nevermind, I figured out how to do it using xmacro

---

