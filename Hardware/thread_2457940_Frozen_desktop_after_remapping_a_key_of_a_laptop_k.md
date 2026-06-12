---
title: "Frozen desktop after remapping a key of a laptop keyboard"
date: 2021-02-12
forum: Hardware
---

### Post by angelo16 on 2021-02-12
Hi, my laptop dell 1525, has a key which is not detected (slash-question mark). 

following this link   [https://dev.to/0xbf/remap-keys-in-the-keyboard-in-ubuntu-5a36](https://dev.to/0xbf/remap-keys-in-the-keyboard-in-ubuntu-5a36)

I could fix this editting the line for the keycode 105 which is now

keycode 105 = slash question slash question questiondown dead_hook questiondown

but 10-15 sec after typing the command >    xmodmap .Xmodmap
the desktop freezes and only the terminal window is responsive.


is this method the correct procedure to remap a  key ?

---

### Post by guiverc on 2021-02-12
You've provided no release details, thus we don't know which desktop you're using yet.

(I'm also unsure what your actual command is, with no quotes or <#> code blocks used).

---

### Post by angelo16 on 2021-02-12
Hi, it is Lubuntu 20.04

The commands are the same of the link provided. 

```
[FONT=var(--ff-monospace)]xmodmap -pke > .Xmodmap[/FONT]
```

then I edited and saved the file .Xmodmap as said in 1st post.

 to finish:

```
[COLOR=#000000]xmodmap .Xmodmap [/COLOR]
```

---

