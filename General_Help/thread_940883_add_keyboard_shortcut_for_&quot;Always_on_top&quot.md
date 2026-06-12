---
title: "add keyboard shortcut for &quot;Always on top&quot;"
date: 2008-10-07
forum: General Help
---

### Post by smain on 2008-10-07
Hi all

I'm a big fan of keyboard shortcuts, therefore I wanted to add one that when pressed, made the selected window to "Always on top"...

But when I went to System -> Preferences -> Keyboard Shortcuts, I couldn't find the always on top... I find this rather strange, since all the other options from the window-menu is there...

Does anyone know how to add this so that when I e.g. res alt+ctrl+t, then I turn the option Always on top on/off?

Smain

---

### Post by schmendrick on 2009-03-30
Yes I too would be delighted to have this!

The only workaround I found for this would be something found here:

[http://linux.byexamples.com/archives/306/makes-your-windows-stay-on-top-toggle-it/](http://linux.byexamples.com/archives/306/makes-your-windows-stay-on-top-toggle-it/)

But is there a "native" way how to do is?

---

### Post by VexaAE on 2009-07-22
ALT + SPACE usually brings up the windows option menu. Then press T and "Always on Top" checkbutton should toggle on/off. Practice a few times and you'll get the hang of it in no time :p

---

### Post by geoffm on 2010-05-15
run **gconf-editor** Goto **apps** -> **metacity** -> **windows_keybindings**, the corresponding value of Always on top is **toggle_above**

---

### Post by demosthenese on 2010-05-15
If you have wmctrl installed you can bind the following command to a key to toggle the 'above' property on and off for the active window:

```
wmctrl -r :ACTIVE: -b toggle,above
```

---

