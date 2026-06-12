---
title: "&quot;ls&quot; command going off the page!"
date: 2008-08-03
forum: General Help
---

### Post by bks on 2008-08-03
I am attempting to install Xubuntu on a Compaq Armada 1530DM (aka really old) and the installer can not detect my cd-rom. So, I'm in the terminal trying to read the list of devices in /dev, but everytime I type *ls*, most of the list flys up and off the screen! Is there any option to go page by page?

---

### Post by Seti on 2008-08-03
try
```
ls | more
```

---

### Post by mb_webguy on 2008-08-03
Sure.  Just pipe the *ls* into *more*:

*ls /dev | more*

The command *more* takes some input (usually from another command through a pipe, the "|" character) and lets you scroll through bit by bit.  You can exit out any time by typing the letter "q".

---

### Post by 3rods on 2008-08-03
I prefer less over more.

```
ls /dev | less
```


Seriously. It's a program called less.

---

### Post by K2712 on 2008-08-03
Or you could pipe the output to a text file:

```
ls /dev > dev_contents
```

```
gedit dev_contents
```

One of the great things about linux, there's almost always multiple solutions to a problem!:)

---

### Post by tacutu on 2008-08-03
or Shift-PgUp to scroll the terminal output

---

### Post by 3rods on 2008-08-04
> **tacutu said:**
> or Shift-PgUp to scroll the terminal output

Does that work in a real terminal?

---

### Post by K2712 on 2008-08-04
As long as it's bash...

---

### Post by tacutu on 2008-08-04
> **3rods said:**
> Does that work in a real terminal?

it sure does.

---

