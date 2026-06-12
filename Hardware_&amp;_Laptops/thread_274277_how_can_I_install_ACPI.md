---
title: "how can I install ACPI?"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by karloslambchop on 2006-10-09
Hello all,

I am running ubuntu server version and fluxbox on my dell laptop to keep things to a minimum

Before you think I am crazy, I am doing this so I can run Windoze within VMware and conserve resources.

Only problem is that when running on battery I get no warning and the machine instantly dies when the charge runs out...

my questions are as follows, 

What ap-get packadges do I need to install to get battery monitor running in fluxbox?

How can I confirm if ACPI is loaded?  I have run lsmod, but I am not sure what to look for?  Do I need to add any switches to menu.1st?

Thank you very much for taking time to read this,

karloslambchop.

---

### Post by mark_g on 2006-10-09
I think you just need to install the packages acpi, acpid and acpid-support. You can check if they are running by executing

> lsmod | grep acpi

You don't have to alter your menu.lst to get them to load, they'll do so automatically.

---

### Post by karloslambchop on 2006-10-09
Wow!

Thank you for a spot on, very quick response.

Karlos.

PS  Do you know of a good battery package that will beep or flag up when the battery is about to go?  I think fluxbox will support kde based apps?

---

### Post by mark_g on 2006-10-10
I personally use KLaptop and you can run that in Fluxbox too, just like any other KDE/Gnome app (don't know if it'll minimize to the kicker (taskbar) properly though), but if you really want to keep your system lean, you can use a bash script to monitor your battery.
This one I found on the web is great:

> [http://swicked.net/pages/bat_mon.html](http://swicked.net/pages/bat_mon.html)

You could edit it so it'll play a sound if the battery is almost empty.

PS: You might want to test your hibernate and alike functions before using them in a production system, because they may not work properly for your system.

---

