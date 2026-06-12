---
title: "[HOW-TO] Compiz CCSM and many button mouse"
date: 2010-10-15
forum: Hardware
---

### Post by schlameel on 2010-10-15
I have a mouse with many buttons (Logitech MX700) and like to use the thumb wheel to flip between workspaces.  When I did a fresh install of 10.10, I had to set this up again which should be easy via CompizConfig Settings Manager.  However, CCSM only lists buttons 1-9 and if you try to edit it manually with the pencil icon to "Button13", CCSM throws out your edit and changes it to "disabled".

Not very helpful, but I found the manual workaround: **gconf-editor**

My configuration:
[LIST]
[*]Dell XPS 600
[*]Ubuntu 10.10 Maverick Meerkat 64-bit
[*]Logitech MX700 mouse
[/LIST]

If you need to figure out which button is assigned which number you can use:
```
me@computer:~$ xev
```
It opens a window in which you can click and it will display a message in the terminal window identifying the button number clicked.  

If you don't already have CCSM, install it with:
```
me@computer:~$ sudo apt-get install compizconfig-settings-manager
```
Sure, my point here is that it doesn't work for setting these high button numbers, but it useful for setting most other options.

Start gconf-editor:
```
me@computer:~$ gconf-editor &
```

Navigate to *apps->compiz->plugins->rotate->allscreens->options*, click in the Value column of *rotate_left_button* and enter **Button13** (or whatever button number you want to use).  I set *rotate_right_button* to **Button15** and *initiate_button* to **Button17**.

**NOTE** - This specific fix is to rotate the cube. You can use the same technique to assign high numbered buttons to other functions, but you'll have to find the path to your function.

---

### Post by mutrax on 2011-03-17
Thank you! This also applies to lucid!

---

### Post by phubert28 on 2011-06-16
I got into the Configuration Editor, but somehow I can't relate what I see to the buttons (and wheels) on my MX Revolution mouse.

Is everything -like this- (unsupported stuff) under Linux just GUESSWORK?

On mainframes I was used to specific documentation for specific hardware. But THERE the OS vendor supported its own hardware and I'm sure 'foreign' hardware would be difficult in the same way we see it under Linux.

I -know- this isn't a problem with Linux, but I'd love to find some source of documentation I could more directly relate to the components in Linux and how they can be related TO the 'errant' hardware.

I tried xev, but the strings it was putting out didn't make any sense to me!

E.g.:
LeaveNotify event, serial 30, synthetic NO, window 0x5a00001,
    root 0x15a, subw 0x0, time 17457709, (10,-1), root: (25,890),
    mode NotifyNormal, detail NotifyAncestor, same_screen YES,
    focus YES, state 16

Can anyone point me to reference material for xev, xconf, Configuration Editor, etc. that would help me put this all together?????

---

