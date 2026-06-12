---
title: "[SOLVED] Open stickynotes with a keypress"
date: 2008-07-30
forum: General Help
---

### Post by tamias on 2008-07-30
Hi all,

I'm a big fan of the Gnome Stickynotes applet ([http://www.novell.com/coolsolutions/feature/11854.html](http://www.novell.com/coolsolutions/feature/11854.html)) -- I much prefer using it to Tomboy or similar.

One thing the applet lacks is a keypress to open all notes. So I set about working out how to do it myself.

This can be achieved by installing the *wmctrl *package and then executing the command ```
for item in `wmctrl -xl | grep "Stickynotes_applet" | awk '/0x.*/ {print $1}'`; do wmctrl -i -a $item$; done
```

If you are using Compiz (or indeed, Metacity), you can then add this to one of the *command* entries and assign it a keypress. I use F7 to open the notes. Sometimes some of the notes open underneath the other windows on the desktop. If this happens, just hit the key again and they'll pop to the top.

I think it's a lot nicer and smoother than having to reach for the mouse and find that little icon on the panel every time. Hope someone else finds it useful!

Mark

---

