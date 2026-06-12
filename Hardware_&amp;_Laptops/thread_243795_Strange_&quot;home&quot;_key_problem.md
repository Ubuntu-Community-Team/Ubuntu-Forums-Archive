---
title: "Strange &quot;home&quot; key problem"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by xiko on 2006-08-25
When my ubuntu starts, the "Home" key isn´t working.

So, I go to gnome-keyboard-properties and go to layout options and just click ok and it is fixed.

Anyone has ANY idea? I have to make this every reboot.

---

### Post by Woei on 2006-08-25
> **xiko said:**
> When my ubuntu starts, the "Home" key isn´t working.

So, I go to gnome-keyboard-properties and go to layout options and just click ok and it is fixed.

Anyone has ANY idea? I have to make this every reboot.

I think this is in the wrong forum, as the home key has no drivers of its own and is merely a part of the obviously working keyboard, otherwise you couldn't have posted this.

Anyhow. You haven't told us exactly where the home key doesn't work. It is only nonfunctional in graphical applications like Firefox ? It is only not working on a graphical terminal like xterm or gnome-terminal (lots of historical reasons why that could be), or doesn't it work on the getty's (alt-F<1-6>) ? Also, please provide any relevant output of dmesg. Specifically warnings by the kernel about keycodes, as it's entirely possible your keyboard has some weird keymappings that will have to be made explicitly clear to X and the kernel through things like xmodmap.

---

### Post by xiko on 2006-08-25
It doesnt work in terminal, or gedit, or firefox or getty.
Im using abnt2 keymappings.

My dmesg | grep key doesnt show anything wrong.

(yeah I realized now that it is the wrong forum, can a admin move it to the right one?)

---

