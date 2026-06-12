---
title: "Logitech Click!: Fourth mouse button"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by Absurd on 2007-01-02
Is there a way that I can make use of the fourth button on my Logitech Click! mouse? On windows I had it set to minimize the active window. Is there a way to configure X so it'll do the same?

---

### Post by Absurd on 2007-01-02
Ok, so I was reading [this](https://help.ubuntu.com/community/ManyButtonsMouseHowto) guide and got the fourth (or sixth) button to actually function but for now, kicker treats it like another right click.

Now I'm confused about how to configure imwheel. I see stuff like 

> "^XTerm"
Alt_L,		Up,		Shift_R|Page_Up
Alt_L,		Down,	Shift_R|Page_Down
Alt_L,		Left,	Control_L|A
Alt_L,		Right,	Control_L|E
#Shift_L,	Down,	Shift_L|1

Can someone explain to me what each parameter means?

---

### Post by saxofoner on 2007-01-02
There's probably a setting in xorg.conf... Try googling for multibutton mouse options.

---

### Post by Absurd on 2007-01-02
Well, like I said, I was able to make the extra button work I just don't know how to map anything to it. By reading the imwheel readme I was able to learn that the first parameter is a modifier and the last one contains the keys to send to the window. I don't know what the second parameter is.

Does anyone know how I would set firefox to receive ctrl+win+down from the extra button (button #6)?

---

### Post by Absurd on 2007-01-03
bumpity bump

---

### Post by tweedledee on 2007-01-06
> **Absurd said:**
> bumpity bump

Try this thread instead of messing with imwheel - I don't think you need something that complicated for what you are trying to do: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441)

---

