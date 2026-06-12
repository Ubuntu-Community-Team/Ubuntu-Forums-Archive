---
title: "How do I find out what my graphics card is?"
date: 2008-11-14
forum: Hardware
---

### Post by kundalinikat on 2008-11-14
Hello, I've been using Ubuntu for a couple years now, but now I am stumped. I am simply trying to find out the make and model of my graphics card. As far as I can tell there's no way to do this with the GUI?? Is there a method in GNOME or on the command line to find out what model my PC's graphics card is?

---

### Post by rossmoore on 2008-11-14
I don't know about the GUI. I think you can read (or grep) the output of lspci if I remember correctly.

---

### Post by Gausian on 2008-11-14
```
sudo lshw -C video
```

---

### Post by rossmoore on 2008-11-14
Brilliant, much better answer. Thanks Gausian.

---

### Post by Brandel Valico on 2008-11-14
You can also (For a GUI Method) install Sysinfo via add/remove applications (It's in the system tools area) then open it and goto hardware. Use the drop down menu there to go to graphic card and it should give you make and model. It's also useful for a bunch of other System information also.

---

### Post by prshah on 2008-11-14
> **kundalinikat said:**
>  As far as I can tell there's no way to do this with the GUI?? Is there a method in GNOME or on the command line to find out what model my PC's graphics card is?

System-Preferences-Hardware Information

== OR ==

lshw as suggested

== OR ==```

lspci | grep -i -E graphics\|vga
```

---

### Post by Mardoct909 on 2008-11-14
If you have Windows installed, you can also try "dxdiag" in the run box and get information on it.

---

