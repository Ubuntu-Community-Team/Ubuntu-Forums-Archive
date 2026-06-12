---
title: "3D Box in Ubuntu 8.0.4 the Hardy Heron"
date: 2008-09-28
forum: General Help
---

### Post by m4noob on 2008-09-28
Hello Linus-Fans 
I have a question:
How can i make a 3D Box in Ubuntu 8.0.4 Hardy Heron?
Thank you for all answerses:)

---

### Post by howefield on 2008-09-28
You mean the rotating 3D cube ?

Assuming that your graphics card can do it, you need to install compizconfig-settings-manager, either from terminal or Synaptic Package manner. 

From terminal type

```
sudo apt-get install compizconfig-settings-manager
```

All being well, you'll then have an Advanced Desktop Effects Settings option in your System > Preferences menu, you want to enable 3D cube and Rotate Cube options, there are a ton of other effects in there for you to play with.

---

### Post by overdrank on 2008-09-28
Hi and welcome m4noob, you may look at the sticky at the top of this forum FAQ' or the link in my signature that will help alot. :)

---

### Post by Kevbert on 2008-09-28
> **m4noob said:**
> Hello Linus-Fans 
I have a question:
How can i make a 3D Box in Ubuntu 8.0.4 Hardy Heron?
Thank you for all answerses:)

What display card do you have ?  Intel, ATI or Nvidia will work in most cases.  You can find out what card you have by using
```
lspci
```
in Applications-Accessories-Terminal. It's normally the last item listed.

---

### Post by davidryder on 2008-09-28
What's the shortcut to start the cube?

---

### Post by howefield on 2008-09-28
> **davidryder said:**
> What's the shortcut to start the cube?

press the scroll wheel down on an empty part of the desktop, then move the mouse.

---

### Post by m4noob on 2008-09-28
> **Kevbert said:**
> What display card do you have ?  Intel, ATI or Nvidia will work in most cases.  You can find out what card you have by using
in Applications-Accessories-Terminal. It's normally the last item listed.
I Have nVidia GeForce 8800 GTS


I Have a question again how can i start the 3D cube?with scrolling doesn't work-.-

---

### Post by binbash on 2008-09-28
ctrl+alt+ move the mouse

if it doesn't work.You dont have compiz running or desktop cube enabled.There are lots of howtos at tutorial section about enabling compiz-fusion.

If you are sure you compiz enabled make sure you have 4 desktops(system>preferences> compiz settings manager> General Options > Desktop Size > make horizontal virutal size =4

---

### Post by BeauBridges on 2008-09-28
I'm not even going to bother using the rotating cube on my computer, the video card isn't really good. Everything else is pretty decent.

---

### Post by davidryder on 2008-09-28
I wasn't really impressed with the cube. Doesn't seem very productive IMO...

Makes for a neat demo though.

---

