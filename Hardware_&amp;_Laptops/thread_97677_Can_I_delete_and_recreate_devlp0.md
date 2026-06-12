---
title: "Can I delete and recreate /dev/lp0 ???"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by Moloko on 2005-12-01
Hi all, my HP Laserjet 1100 was workinf fine for a time but since a week ago doesn't work. Diferent tools detects the printer conected to the parallel port, but there is not way to use this device.

I've tried to configure the printer with de gnome-cups-manager, with [http://localhost:631](http://localhost:631), with printtool and other utilities that I don't remember, but at the end always there is a message taking about the parallel port:

I'm member of lp and lpadmin groups and I changed the permissions of /dev/lp0 to 777 ... nothing works.

I was lookint in linuxprinting.org and in this forum, there's more people with similar problems using Breezy, I want to try to delete/recreate /dev/lp0.

Thanks in advance.

---

### Post by jliedeka on 2005-12-01
I wouldn't think deleting and re-adding the device file would help anything.  Parallel ports should be well supported.  The technology hasn't changed significantly in several years.

Check your /var/log/dmesg file for references to lp0, parport or parport0.  They should be all together.  See if that tells you anything.  I wouldn't expect to see any problems with the driver but you never know.

It might help us diagnose the problem if you could post the exact text of your error message.

---

### Post by Moloko on 2005-12-02
Hi jliedeka, thankls for your answer. 

dmseg ouput:

[B][4294752.113000] parport: PnPBIOS parport detected.
[4294752.113000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[4294752.127000] parport0: faking semi-colon
[4294752.127000] parport0: Printer, Hewlett-Packard HP LaserJet 1100
[4294752.153000] lp0: using parport0 (interrupt-driven).[/B]

If I try to install the printer with CUPS ([http://localhost:631](http://localhost:631)) or the gnome-cups-manager, when I should choose the conection there are 3 options:

[B]hp no_device_found
Parallel Port #1 (CANON)
Parallel Port #1 (EPSON)[/B]

I don't know why CANON  and EPSON are in the list :confused: . If I run the foomatic-gui there is a queue called "lp@localhost" that I can't delete, and if I try to add another for the LaserJet-1100 the console output is:

[B]/usr/bin/foomatic-gui:591: GtkWarning: gtk_tree_view_get_cell_area: assertion `G TK_WIDGET_REALIZED (tree_view)' failed
  self.maker_treeview.scroll_to_cell((i,), None, True, 0.5, 0)
/usr/bin/foomatic-gui:591: GtkWarning: gtk_tree_view_scroll_to_point: assertion `GTK_WIDGET_REALIZED (tree_view)' failed
  self.maker_treeview.scroll_to_cell((i,), None, True, 0.5, 0)
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Foomatic/D B.pm line 3432.
sh: /usr/sbin/lpadmin: No existe el fichero o el directorio
Could not set up/change the queue "hp_laserjet_1100"!
Usage: /etc/init.d/cupsd {start|stop|restart|force-reload}
invoke-rc.d: initscript cupsys, action "reload" failed[/B].

Now I'm looking if foomatic-gui I can solve something. 
Regards.

---

### Post by Moloko on 2005-12-02
Hi again, after spend more than a week trying to solve the problem I decided to go for the "hard" way.

I removed an reinstalled all the packets related with:

* CUPS
* hpijs / hpoj / hplip (I'm using now only hpijs driver)
* foomatic

After this I used the web CUPS interface to setup a new printer, like a fresh installation, now I can see the **Parallel Port #1 HP LaserJet 1100**, various USB ports and JetDitec, http, ipp and LDP-LPR are availabe to setup new printers ... the CANON and EPSON ports doesn't are now in the list. In the gnome-cups-manager now the printer is detected too.

This is not the best solution for me because I solved the problem without know really what hapened :???: , but I think that was something related to CUPS, because I removed hp drivers an foomatic before and didn't solve the problem.

As **jliedeka** said before the problen was not related to /dev/lp0 ... Thanks again.

---

### Post by salahx on 2005-12-09
I ran into the same problem as you, but with a USB PSC 1315. I was able to solve the problem by
```

dpkg-reconfigure cupsys

```
which fixed the probem.

---

