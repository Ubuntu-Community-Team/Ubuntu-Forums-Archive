---
title: "tweaking the keyboard driver"
date: 2014-01-06
forum: Hardware
---

### Post by George Heine on 2014-01-06
Recently acquired a Dell Optiplex gx620 Desktop and installed Ubuntu 12.04 LTS, using the "U.S. English" option (I live in the USA).  The keyboard, however, is non-US.  (Appears to be Portugese/Brazilian.)  The alphanumeric keys use the QWERTY layout, so that is no problem.  However, most of the punctuation keys are marked with a different symbol than the character they produce when typing in a terminal.

For example, the key to the left of the "1" key is marked with a single and double quote, but when pressed, it produces a grave accent (`), and when pressed with the shift key, it produces a tilde(~).

Here is the output of showkey for this key:
```

$sudo showkey
`keycode  41 press\ keycode  41 release
$sudo showkey -s
`0x29 0xa9
$sudo showkey -a
`        96 0140 0x60
```
and here is an extract from dumpkeys
```
....
keycode  41 = grave
        shift   keycode  41 = asciitilde
        control keycode  41 = nul
        shift   control keycode  41 = nul
        altgr   control keycode  41 = nul
        shift   altgr   control keycode  41 = nul
        alt     keycode  41 = Meta_grave
...
```

My first step was to construct a paper keyboard diagram and write in the characters produced, and I can get by with that for the time being.  However, in the long run I would prefer the Linux keyboard driver in sync with the actual characters marked on the physical keys (with a few exceptions, see Questions 2 and 3).

The man pages for setkeycodes and loadkeys imply that it might be possible to use these tools, but some examples would be helpful.  Here are some specific questions:

QUESTION 1:  How can I instruct the keyboard driver to cause the key with
scan code 0x29 to generate the grave-accent character (0x60) when
pressed alone, and the tilde character (0x7e) when pressed with the shift key?

QUESTION 2: How can I instruct the keyboard driver to cause the key with
scan code 0x27 (to the right of the "L" key) to generate an n-tilde
(0xc3b1, 0xc391) as in the Spanish keyboard layout?

QUESTION 3: Is there any way to disable the shift-lock key (scan code 0x3a)?

As always, thanks for any assistance.

---

### Post by George Heine on 2014-01-09
In Unity Desktop, under "System Settings/Keyboard Layout/Options", there are a large number of settings to control keyboard behaviour, including "Disable Caps Lock".  I am still looking for a way to do this with command line shell script (as well as the other keyboard tweaks), but will use this for now.

There is a Linux HOWTO at [http://www.tldp.org/HOWTO/Keyboard-and-Console-HOWTO.html](http://www.tldp.org/HOWTO/Keyboard-and-Console-HOWTO.html) which may have some of the answers.

---

### Post by George Heine on 2014-01-11
After a bit of research I was able to successfully remap the keyboard.

It turns out that Xwindows has its own key mapping, entirely different from the mapping in the kernel.  So the solution presented here will only work under X. Okay with me, since this a workstation and X is on all the time anyway.  For non-X situations, such as Ubuntu Server or booting into rescue mode, lower-level functions such as setkeycodes and loadkeys would probably be necessary.  

The first step is to identify the X keycodes of the keys whose mapping needs to be changed.  The tool for this is "xev".  Typing xev in a terminal will result in a small white window popping up; to exit xev, close this window.  Here is the output of xev when the key currently mapped to the semicolon/colon key was pressed:

```
KeyPress event, serial 36, synthetic NO, window 0x3600001,
    root 0xab, subw 0x0, time 1555487, (650,493), root:(651,545),
    state 0x10, keycode 63 (keysym 0x3b, semicolon), same_screen YES,
    XKeysymToKeycode returns keycode: 61
    XLookupString gives 1 bytes: (3b) ";"
    XmbLookupString gives 1 bytes: (3b) ";"0
    XFilterEvent returns: False 

```

So the X keycode for this key is 63 (third line, second item).  This is a decimal number.  The output from xev is voluminous; I needed to tee or pipe the output to a log file to find what I was looking for.

Having identified the keycodes, the next step is to write a set of mapping instructions.  The instructions are in the format
```
keycode xx = value1 value2 value3 value4

```

where xx is the keycode value from xev; (it can be written in decimal, octal, or hex).  The values can either be ASCII or Unicode numbers, or an appropriate mnemonic (or to map keys to latin letters or digits, just use the letter or digit).   To get the mnemonic for keys that are already mapped, you can use 
```
xmodmap -pk
```

A complete list of mnemonics used by X is found in the file /usr/include/X11/keysymdef.h.  Here is a sample line from that file
```
#define XK_semicolon                     0x003b  /* U+003B SEMICOLON */
```
If you want to map a keycode to the semicolon, you may use the word "semicolon" or the hex value 0x003b or the unicode string "U003B".

Each keycode may be mapped to a set of four values (actually seven are allowed, but the last three are seldom used).  The first value is the mapping you want when the key is pressed by itself.  The second is the mapping you want when the key is pressed with the shift key.  The third and fourth values are used with a "mode switch" key, with and without the shift key.  I haven't yet played with mode shifting, but it seems like it might be useful if you need to mix symbols from two different alphabets.  Most keys on my system are mapped to the same values with and without the mode shift.

Here is my file of keymappings:
```
! Remap punctuation keys on an IFO Portuguese keyboard

keycode 49 = apostrophe quotedbl apostrophe quotedbl
keycode 34 = grave acute grave acute
keycode 35 = bracketleft braceleft bracketleft braceleft
keycode 47 = ccedilla ntilde ccedilla ntilde
keycode 48 = asciitilde asciicircum asciitilde asciicircum
keycode 51 = bracketright braceright bracketright braceright
keycode 94 = backslash bar backslash bar
keycode 61 = semicolon colon semicolon colon
keycode 97 = slash question slash question
```

Now just run
```
xmodmap mykeymaps.txt
```

This will remap the keyboard for all X windows on your system.  The remapping goes away when the system is restarted. To make it permanent,  append the xmodmap command to .profile .

---

### Post by George Heine on 2014-10-22
To disable CapsLock in 14.04, see [http://askubuntu.com/questions/462021/how-do-i-turn-caps-lock-into-an-extra-contrl-key](http://askubuntu.com/questions/462021/how-do-i-turn-caps-lock-into-an-extra-contrl-key)

---

