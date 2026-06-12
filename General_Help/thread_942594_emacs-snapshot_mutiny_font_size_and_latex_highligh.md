---
title: "emacs-snapshot mutiny: font size and latex highlighting"
date: 2008-10-09
forum: General Help
---

### Post by fmhoyt on 2008-10-09
I am using emacs-snapshot via Alexandre Vassalotti's "Pretty Emacs" package ([http://peadrop.com/blog/2007/01/06/pretty-emacs/](http://peadrop.com/blog/2007/01/06/pretty-emacs/)) on Hardy, using Monotype-10 as the default font. 

Just this morning some appearance wierdness: I started it up using the following options: 

emacs-snapshot-gtk -bg black -fg white <file>

Afterwards, *all versions* of emacs (emacs-snapshot and emacs22, both in gtk and x11 versions) starts using these options with a black background and white foreground, even if I do not specify as such, and with the font at a much larger size. 

I am not in fact able to start it up without these options. For example, the following still produces a black background and a white face: 

emacs-snapshot-gtk -bg white -fg black <file>

The Monotype font doesn't show up in the shift+left-button list, so if I want a smaller font size, I have to give up the font. 

Also, the latex font-lock has somehow turned itself off, and when I re-enable it, the colors are different. 

It looks like resource settings are getting saved somewhere and possibly corrupted. I have deleted auto-save files, and backups of the file that I was working on. 

I also notice that my .emacs file seems to have gone missing. 

And suggestions as to where else I can look? 

Thank you

---

