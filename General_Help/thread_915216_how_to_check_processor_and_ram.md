---
title: "how to check processor and ram"
date: 2008-09-09
forum: General Help
---

### Post by taimur on 2008-09-09
how cani check ram and porcessor in ubuntu?

---

### Post by fooman on 2008-09-09
you mean where to check your cpu and memory *usage*? .... system > administration > system monitor > resources tab.

---

### Post by WRDN on 2008-09-09
To find all the hardware information, open the Terminal and type:

```
lshw
```

To get detailed information on the CPU, type:

```
cat /proc/cpuinfo
```

For detailed information on the memory (RAM) type:

```
cat /proc/meminfo
```

---

### Post by ilrudie on 2008-09-10
There is also a nice gnome panel applet which can monitor CPU, memory, swap, network and disk use.  To get it just right click on a gnome panel and select "add to panel" from the resulting context menu.  Then in the "Add to Panel" windows scroll down until you see "System Monitor".  Highlight the system monitor and then click the +add button at the bottom of the window.  By default it will only display CPU I think but you can go into the Preferences by right clicking on the System Monitor applet and use the check boxes to change what gets displayed.

---

### Post by muteXe on 2008-09-10
Typing "ps" or "top" into the command line might be of some use to you as well.

---

### Post by taimur on 2008-09-11
thanks you all people for wonderfull info

---

### Post by scoob8000 on 2008-09-11
My personal favorite tool is to install gkrellm from synaptic.

You can set it up to monitor your disks, network, ram, cpu, etc in a nice graphical display similar to Windows task manager.

You can also go as far as to monitoring your case and cpu temps with it.

---

### Post by fasilkaks on 2009-06-30
Thanks to u guys..... This is really helpful

---

