---
title: "Modifying contextual menus"
date: 2008-10-27
forum: General Help
---

### Post by rmcellig on 2008-10-27
Is there a way to modify Contextual menus in Ubuntu 8.04. I would like to be able to add things to the Contextual menus. Something like Finderpop in OSX.

---

### Post by teaker1s on 2008-10-27
not sure I fully understand,if your asking for ability to add and alter applications menu
terminal
```
sudo apt-get install alacarte 
```

```
 gksudo alacarte
```

---

### Post by Sam on 2008-10-27
> **teaker1s said:**
> not sure I fully understand,if your asking for ability to add and alter applications menu
terminal
```
sudo apt-get install alacarte 
```

```
 gksudo alacarte
```

It's installed by default with 8.04. Right click on "Applications" > "Edit Menus".

---

### Post by rmcellig on 2008-10-27
When you right mouse click you are presented with a menu. This is the menu I was wondering if you could modify like add apps etc... to it.

---

### Post by rmcellig on 2008-10-27
After I install alacarte, where can I find it?

---

### Post by Sam on 2008-10-27
> **rmcellig said:**
> After I install alacarte, where can I find it?

Right click on "Applications" > "Edit Menus".

Or
```
alacarte
```
in a terminal.

---

### Post by bryonak on 2008-10-27
I think he means the context menu you get when you right-click anywhere.

This depends on the application... right clicking on the desktop is managed by Nautilus, your file browser.
Open Synaptic (Main Manu -> System -> Administration -> Synaptic Package Manager) and search for "nautilus", there are some context menu extensions there.
Or if you prefer the command line, try 'aptitude search nautilus-', which will list nautilus-actions, nautilus-cd-burner and similar extensions.
I don't know of any simple (graphical) way to make your own custom menu entries, though they are scripted in a straightforward manner AFAIK, so it shouldn't be too hard if you're willing to learn how to change the markup.

As for other programs... as I said, every application has it's own context menus.

---

