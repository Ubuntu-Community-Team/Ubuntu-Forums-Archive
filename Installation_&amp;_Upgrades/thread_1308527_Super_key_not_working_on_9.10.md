---
title: "Super key not working on 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by superdif on 2009-10-31
Hi all,
I have a strange problem since I have upgraded Kubuntu 9.04 to 9.10 (both 64 bits): the Super keys are not working.

I did the upgrade over a total clean install of 9.04 (since I had problems with the direct clean install of 9.10, I did a clean install of 9.04 and immediately upgraded after the first login).

xmodmap is reporting the keys:

```
$ xmodmap -pke | grep Super_L
keycode 115 = Super_L NoSymbol Super_L NoSymbol Super_L
keycode 127 = NoSymbol Super_L NoSymbol Super_L NoSymbol Super_L

```

and

```
$ xmodmap -pke | grep Super_R
keycode 116 = Super_R NoSymbol Super_R NoSymbol Super_R
```

But xev does not detect them (if I click them nothing happen).

I first noticed the problem when I tried to add the combination Super+r to the run dialog window.

I tried to add the key code to ~/.Xmodmap:
```
$ cat .Xmodmap | grep Super_L
keycode 115 = Super_L NoSymbol Super_L NoSymbol Super_L
keycode 127 = NoSymbol Super_L NoSymbol Super_L NoSymbol Super_L
```

and

```
$ cat .Xmodmap | grep Super_R
keycode 116 = Super_R NoSymbol Super_R NoSymbol Super_R
```

But it doesn't work.

I have a new (about 3 weeks old) keyboard and it was working up to yesterday on 9.04


P.S. (**it is probably related**): the keyboard is a "Logitech G15" and not only it is not working with the default Kubuntu settings (the main concern of this topic), but also with the specific guide ([https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15) and others) I was using with 9.04; also the mouse (Logitech G9) is not working as for the guide I followed ([http://ubuntuforums.org/showthread.php?t=1092352](http://ubuntuforums.org/showthread.php?t=1092352)) with success with Kubuntu 9.04

---

### Post by superdif on 2009-10-31
I forgot to mention that is the only major problem I am having with Karmic, so it would be regretful to have to roll back to Jaunty.;)

---

### Post by JC Cheloven on 2009-11-02
Bump.
I've got the same problem. I used to assign alt + superL to the main menu of the panel, but now I can't. Can anyone help?

---

### Post by Omen_20 on 2009-11-03
I have the issue as well. I miss having Super L as Window Picker and Super R as Terminal.

---

### Post by Clopin on 2009-11-07
Same problem for me on Ubuntu 9.10

---

### Post by FlamingSR-71 on 2009-11-07
I have this issue as well in Ubuntu 9.04

---

### Post by neondiet on 2009-11-09
I came across a [YouTube vid]("http://www.youtube.com/watch?v=BJuWq9UsV-w&feature=autoshare_twitter") that shows how to fix this.

---

### Post by superdif on 2009-11-10
> **neondiet said:**
> I came across a [YouTube vid]("http://www.youtube.com/watch?v=BJuWq9UsV-w&feature=autoshare_twitter") that shows how to fix this.

Useful for many.

Unfortunately I am using Kubuntu and therefore KDE.

---

