---
title: "Gnome panel customization"
date: 2008-08-17
forum: General Help
---

### Post by alphaakenny1 on 2008-08-17
I'm trying to make a custom panel and I have two questions:

1.) Whenever I uncheck the "Expand" box in the properties of a panel two "handles" come on the ends of the panel, I was wondering how to remove them or make them as transparent as the rest of the panel.

2.) There's a default applet called "Window List," is there a way to configure it so that it only shows the icon of the application rather than the text associated with it.  I know I could use AWN but I don't want to use compiz.

Thanks.

---

### Post by dje on 2008-08-17
sorry i dont know any solutions to your questions but you could use the metacity compositor if you dont want to use compiz, it only has basic drop shadows etc. so doesnt use much ram or processor and allows use of awn etc. To enable it press alt + f2 and run:
```
gconf-editor
```
navigate to apps >> metacity >> general and tick compositing_manager

dje

---

### Post by alphaakenny1 on 2008-08-17
Is there anyway to do this without using a compositor?

---

### Post by dmacdonald111 on 2008-11-23
I would also like to get rid of those annoying grey bars that appear when the toolbar is not expanded. There must be some way of getting rid of them. I really don´t see how there is no option for this yet.

Perhaps some clever person out there knows of a way? Or can design one?

---

### Post by brandon88tube on 2008-11-23
I was wondering if there were any custom keys you could create in gconf-editor that would allow for this or any other custom key values to customize the dock.

---

