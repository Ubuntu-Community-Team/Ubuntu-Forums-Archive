---
title: "Logitech Keyboard and Mouse recognized twice"
date: 2009-07-26
forum: Hardware
---

### Post by euxneks on 2009-07-26
Hello all, I have this annoying problem with my mouse and keyboard sometimes doing whatever input (keypress, mouse press, whatever) twice. So I did a little bit of searching, and found out that my system has been upgraded to HAL, and apparently I could get more information by typing this:
```
xinput list | grep 'id='
```
I get these for my results:
```
"Virtual core pointer"	id=0	[XPointer]
"Virtual core keyboard"	id=1	[XKeyboard]
"G15 Extra Keys"	id=2	[XExtensionKeyboard]
"G15 Gaming Keyboard"	id=3	[XExtensionKeyboard]
"G15 Gaming Keyboard"	id=4	[XExtensionKeyboard]
"Logitech G9 Laser Mouse"	id=5	[XExtensionKeyboard]
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
"Logitech G9 Laser Mouse"	id=7	[XExtensionPointer]

```
You can see that I've got the Logitech Mouse twice and Macintosh mouse button emulation. I don't want macintosh emulation, I doubt I need that. and My keyboard is recognized twice!! :( can anyone offer any advice on this?

---

### Post by euxneks on 2009-08-03
Is there some where I can learn more about HAL in general? For instance, is this normal? It's driving me up the wall! :\

---

