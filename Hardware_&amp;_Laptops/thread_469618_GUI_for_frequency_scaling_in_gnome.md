---
title: "GUI for frequency scaling in gnome"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by koenya on 2007-06-10
I have a lot of problems wit powermanagment in ubuntu feisty, therefore I have installed Kpowersave under gnome because the default doesn't seem to have an adjustable power scheme editorin a GUI. But is there a gnome that offers the same detailed opt!ions, I haven't found one....

---

### Post by ramjet_1953 on 2007-06-10
[COLOR="Blue"]System>Preferences>Power Management[/COLOR]

This works for me!

Do you need something specific that is not in this application?

With CPU frequency scaling, if it is working automatically, it is best left alone, even though you can manually control it, because manually controlling CPU Frequency Scaling requires the applicion to run with root privileges. 

It is not good practice to run any application continually in root mode, as it poses a security risk.

You can add an icon to either your your top or bottom bar  to monitor your frequency scaling, by just right clicking on either bar, select [COLOR="Blue"]add to panel[/COLOR] and then select  the CPU Frequency Scaling applet.

Regards,
Roger :cool:

---

### Post by neptho on 2007-06-10
If you do this in a terminal:

```
sudo dpkg-reconfigure gnome-applets
```

Then say 'Yes' to allow it to install SUID, you can use the Gnome CPU Frequency Scaling monitor applet, it's as simple as two clicks.

---

### Post by koenya on 2007-06-10
thanks mate!!!!

---

