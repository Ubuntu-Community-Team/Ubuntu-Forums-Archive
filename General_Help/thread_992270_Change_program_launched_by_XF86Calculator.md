---
title: "Change program launched by XF86Calculator"
date: 2008-11-24
forum: General Help
---

### Post by bismark on 2008-11-24
Is it possible to change the program launched by by my keyboards calculator key (XF86Calculator).  I have looked through all of the multimedia keyboard howto's and helps that I could find but most of those deal with the keys not working at all.  Mine work, it just launches the gnome calculator program which I would like to change to grpn.

System->Preferences->Keyboard shortcuts lets me change the keys to start calculator but not which calculator.

---

### Post by Elvis99 on 2011-01-21
I know I'm excavating a thread, but I'm having the same issue:

I removed the default calculator and would like to launch another one with the calculator button on my keyboard, but I have no idea where to tell Ubuntu what program to launch. Could sb plz help?

Thanks :)

---

### Post by Ethereal Winter on 2011-01-31
I too, would like to know how to do this. I want to bind an RPN calculator program instead of the standard one, I already have The RPN calculator installed but I don't know how to bind keys. I've tried compizconfig but no luck.

EDIT: 
SOLVED

In System->Preferences->Keyboard shortcuts, disable the default Calculator command. Click add and create your own command to the calculator you wish to add i.e. /usr/bin/free42dec and assign XF86Calculator to it.

---

### Post by pastalavista on 2011-01-31
Maybe try editing the 'Keyboard Shortcuts' app by changing the Calculator shortcut to a different key/combo (or just delete the shortcut) and add your own calculator to the list as the X86Calculator key

---

