---
title: "No sound!"
date: 2008-07-26
forum: General Help
---

### Post by Error 404 on 2008-07-26
Ok, I've recently installed XFCE as my window manager for Ubuntu 7.10, as Gnome was too slow.
In Gnome, I was able to access volume control and use the shortcuts on my keyboard to control sound. I can't do that in XFCE!
My sound card is an ESS Maestro 3, I think.
Does anyone know why I can't get sound?

---

### Post by ProbablyX on 2008-07-26
Can you try opening a terminal and use
```

alsamixer

```

Can you turn on your sound there?

You mark speakers using the arrow keys, right, left and increase the volume with the up arrow. Press ESC to quit

---

### Post by Error 404 on 2008-07-26
No luck with alsamixer, I'm getting absolute silence.
I'll try a Gnome session, to see if its a hardware problem; my Inspiron is slowly falling apart.:(

Update: Gnome has sound, the volume control works fine.

---

### Post by northern lights on 2008-07-26
Can you please post the output of ```
cat /proc/asound/cards
```

Thank you.

---

### Post by Error 404 on 2008-07-26
Output is:

```
0 [PCI             ]: Maestro3 - ESS Maestro3 PCI
                      PCI at oxd800, irq 5
``` 

When I logged back into XFCE, the sound still worked. It seems I can't control the sound volume in XFCE...

---

### Post by mali2297 on 2008-07-26
How do you test the sound? Have you tried different applications?

---

### Post by Error 404 on 2008-07-26
> **mali2297 said:**
> How do you test the sound? Have you tried different applications?

I use Amarok, which worked fine in Gnome.
Usually to control volume I use either the volume control icon in the panel, or the keyboard shortcuts (Fn + Page Up, Fn + Pg Down).
There doesn't appear to be a volume control icon in XFCE.

Update: I dont know why, but now Alsamixer works! It could have been Amarok, but that was working in Gnome.

---

