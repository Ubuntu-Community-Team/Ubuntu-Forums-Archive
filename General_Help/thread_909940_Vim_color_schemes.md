---
title: "Vim color schemes?"
date: 2008-09-04
forum: General Help
---

### Post by ~LoKe on 2008-09-04
I managed to get the colors to change, but they're not what they're supposed to be.  They're supposed to look like [this](http://aimeta.deviantart.com/art/dwm-on-freebsd-74430457).

He gave me the config, [here](http://www.vim.org/scripts/script.php?script_id=1326).  Is that the wrong script or am I just doing something wrong?

Is there somewhere I can get vim color schemes and see a preview?

---

### Post by crwmike on 2008-09-04
I downloaded the file and installed. It works with the console version, but not with gvim. Opening the file, I can see that it only has cterm definitions, no GUI defs.

A good place for downloads is here...

       [http://www.vim.org/scripts/script.php?script_id=625](http://www.vim.org/scripts/script.php?script_id=625)

For Screenshots of color schemes, here is the Vim Color Scheme Test.

       [http://www.cs.cmu.edu/~maverick/VimColorSchemeTest/](http://www.cs.cmu.edu/~maverick/VimColorSchemeTest/)

---

### Post by ~LoKe on 2008-09-04
I'm using the console version but the colors don't seem to come out the way they're shown in the screenshot.  This is what I'm looking at...[text](http://img155.imageshack.us/img155/1520/vimyw2.jpg)

---

### Post by crwmike on 2008-09-04
Edit impact.vim, add the line...
[CODE]let g:impact_transbg=1[CODE]
Put it after the the line 'let g:colors_name="impact"'

---

### Post by ~LoKe on 2008-09-04
Didn't help.  I feel like I'm doing something stupid.

---

### Post by crwmike on 2008-09-04
Are you using Gnome Terminal, what colors is the terminal set to. The problem  appears to be that the terminal is displaying black as grey.

From the Terminal menu, go to Edit > Current Profile. click on the Colors tab. In the Color pallette section, the uper left color should be black, double-click on it and change its value to #000000.

I'm sure that there similar settings in Konsole.

---

### Post by ~LoKe on 2008-09-04
I'm using urxvt so it must be related to Xdefaults; I can't see any other reason for it.

---

