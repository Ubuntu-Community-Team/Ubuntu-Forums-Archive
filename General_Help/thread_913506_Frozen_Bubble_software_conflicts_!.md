---
title: "Frozen Bubble software conflicts ?!"
date: 2008-09-07
forum: General Help
---

### Post by bogamol on 2008-09-07
On attempting to install Frozen Bubble from "Applications-Add/Remove Software" after a clean installation of Ubuntu 8.04 Hardy, I recieved this message when trying to click on the select box.

```
Cannot install 'frozen-bubble'

This application conflicts with other installed software. To install 'frozen-bubble' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
```


I have a
Dell Inspiron 6000
Dual booting with Windows XP Professional
40GB available to Ubuntu
35GB for Windows

What could be conflicting with Frozen Bubble? It was the 2nd application I tried to install from the repository that wasn't stock with Hardy? The other was Xournal (I don't have the Wacom set up yet) what could be conflicting?

---

### Post by Sef on 2008-09-07
> What could be conflicting with Frozen Bubble?

Applications > Accessories > Terminal

then paste or type in this code:

```
sudo apt-get update && sudo apt-get install frozen-bubble
```

Paste any error message you receive in a new post.

---

### Post by bogamol on 2008-09-08
Edit: solved. I forgot to set up the software sources...  :oops:

```
ID10T: Problem Exists Between Chair and Keyboard
```

Thanks for the Quick Response. By the way.

---

