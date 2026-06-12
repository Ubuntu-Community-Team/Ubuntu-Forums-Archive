---
title: "Why can I change my screen's brightness in my BIOS, but not in Ubuntu?"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by rainwalker on 2008-02-03
I've looked in my BIOS and I can set how bright my laptop's screen will be when on battery power or AC power, but when I try to use the brightness applet (right-click on a panel, "Add to Panel...") to change the brightness in Ubuntu, it doesn't work. Why not?

---

### Post by cdtech on 2008-02-03
What happens when you go to Applications > System Tools > Configuration Editor then select apps > gnome-power-manager > backlight and adjust it there? If you double click, adjust then select ok it should adjust on the fly.

---

### Post by dedmonds on 2008-02-03
I have a similar problem on my ThinkPad T61 laptop. The brightness is unaffected by pressing the hardware brightness buttons. There is an indication on the screen that the brightness is being changed, but the actual brightness does not change. I have found that if I hit Ctrl-Alt-F2 to get to a console, the brightness buttons do affect the actual brightness of the screen. I can then hit Ctrl-Alt-F7 to leave the console, and the change remains. I've been using this trick to change the brightness on my laptop for a while now.

---

### Post by rainwalker on 2008-02-03
> **cdtech said:**
> What happens when you go to Applications > System Tools > Configuration Editor then select apps > gnome-power-manager > backlight and adjust it there? If you double click, adjust then select ok it should adjust on the fly.

That doesn't work, but it does have the right numbers from my BIOS (100% on AC power and 70% on battery). Nothing happens when I change them, though.

---

### Post by cdtech on 2008-02-03
Sounds to me that the bios needs to be overridden. I don't know your bios settings but it should be bypassed through bios. Isn't there a switch in bios for that?

---

### Post by rainwalker on 2008-02-03
> **cdtech said:**
> Sounds to me that the bios needs to be overridden. I don't know your bios settings but it should be bypassed through bios. Isn't there a switch in bios for that?

I really have no clue....I haven't messed around with my BIOS that much :???:

---

