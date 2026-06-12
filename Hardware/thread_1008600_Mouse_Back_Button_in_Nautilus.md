---
title: "Mouse Back Button in Nautilus?"
date: 2008-12-11
forum: Hardware
---

### Post by sandman3838 on 2008-12-11
Hello ):P

I asked this question along time ago and I thought I would bring it up again?
Especially now that some time has passed and I'm using Ubuntu 8.10.

It's all a matter of Mouse buttons in "My Computer" - "Nautilus".
Has any one out there been able to at least get the "back" button to function?

My mouse is a Logitech MX Cordless Laser.

Thank you.

---

### Post by carthage on 2009-01-02
I've tried and it worked fine for me [http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

PS : my mouse isn't the same type as yours

---

### Post by Casper Hansen on 2009-01-02
1. Install xbindkeys, xvkbd and xev.
2. Run "xev" from the Terminal.
2a. Press on the back and forward buttons in the popup window.
2b. There'll appear some lines in the Terminal like:"state 0x10, button 8, same_screen YES". 
3.Edit the file ~/.xbindkeysrc. If there's no .xbindkeysrc then make it.
3a. Insert:

```
#nautilus back
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8

#nautilus forward
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```

4. Run xbindkeys and test if it works.
4a. If it works then add xbindkeys to Sessions.

---

### Post by Copernicus1234 on 2009-01-02
I can confirm this works if done right. **First time I didnt read the part about the forum messing up the capital L and R in the words Left and Right, so it didnt work**. But when I went through it again, it worked.

Also its important to note that the entire step 1 can be skipped if mouse buttons already works in Firefox (like they did for me, but not in Nautilus).

My .xbindkeysrc (working) for a Logitech MX510 mouse (although it shows Left as left and Right as right which is wrong)

```

"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/X11R6/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

```

---

### Post by sandman3838 on 2009-02-01
Thanks guys I finally had the time to sit down and work on this.

I did have to create a .xbindkeysrc

With what you said and this link it seems to be working just fine!

[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)

---

