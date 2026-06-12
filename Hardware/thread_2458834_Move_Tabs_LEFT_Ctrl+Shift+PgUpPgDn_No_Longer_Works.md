---
title: "Move Tabs: LEFT Ctrl+Shift+PgUp/PgDn No Longer Works After System Update"
date: 2021-03-04
forum: Hardware
---

### Post by OzzyFrank on 2021-03-04
Hi. I'm currently using Firefox 86.0 in Ubuntu 20.04 64-bit and for aeons I've been using [COLOR=#a52a2a]**Ctrl+Shift+PgUp/PgDn**[/COLOR] to **move tabs left and right**, but a couple of system updates ago I lost the ability to do so. Actually, I should say using the _**LEFT**_ Ctrl and Shift buttons no longer work together, as I ended up trying the right ones and it turns out I can still re-order tabs that way. At first I thought it was a Firefox issue, as I've only ever reordered tabs in Firefox, and I didn't notice any changed keyboard behaviour elsewhere, but just before I opened some extra tabs in a Nautilus window, and sure enough I can move tabs but only with the **right Ctrl+Shift buttons**. Opened Chromium, and same thing there.

I've searched all over the web for a remedy, but see no info that helps. I've looked in **Keyboard Settings**, but do not see that key combo at all, nor any mention of moving tabs.I know I can just use the right Ctrl+Shift buttons, but I'm really used  to my left hand being on the left side of the keyboard, and I'd like to  get this default behaviour back (and not understanding what is going on  is driving me nuts!). So if anyone knows a fix for this, or a way around it, like defining a new global keybinding or whatever, please let me know.

---

### Post by OzzyFrank on 2021-11-18
Been a while without any replies, so I thought I'd update this with some more info. I ran **gsettings list-recursively | grep Terminal.Legacy.Keybindings** and it shows:
[COLOR=#0000ff]org.gnome.Terminal.Legacy.Keybindings move-tab-right '<Ctrl><Shift>Page_Down'
org.gnome.Terminal.Legacy.Keybindings move-tab-left '<Ctrl><Shift>Page_Up'[/COLOR]

However, the left keys still do nothing together, only the right ones. But I found that using the left [COLOR=#a52a2a]_**Ctrl+Alt**_[/COLOR] with **[COLOR=#a52a2a]Page Up/Down[/COLOR]** moves the tabs in Nautilus and other Gnome file managers (with the only noticeable difference being that in Caja the toolbar flickers once every time you use that combo). I've looked all through **dconf** , **Compiz** settings, **Gnome Keyboard Shortcuts**, and either there is no mention of moving tabs or that key combo, or it confirms **Ctrl+Shift+PgUp/PgDn** are the correct combos.

So I'm really at a loss as to why the left **Ctrl+Shift **do nothing any more, and where it is defined that the left **Ctrl+Alt** now move tabs (at least in the file managers - in Firefox that combo does nothing either, and it can't be used to move tabs in the terminal as it takes it as input). Any clues on what is happening, and how to rectify it, would be most welcome.

---

