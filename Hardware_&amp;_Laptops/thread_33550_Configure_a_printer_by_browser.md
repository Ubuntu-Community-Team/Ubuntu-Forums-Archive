---
title: "Configure a printer by browser"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by tirog on 2005-05-11
Hello.

How unlock configure a printer by browser (localhost:631)? I must try to do configure my printer by localhost:631, but in Ubuntu this option is disabled :(

Help me  :-k 
tirog

---

### Post by harryc on 2005-05-11
Is there any particular reason that you can't just run gnome-cups-manager from a terminal and add your printer that way?

---

### Post by Kurse on 2005-05-11
Disabled? Disabled how? Do you get page not found? if so, cups isnt running. You can start it by typing "/etc/init.d/cupsys start" in a terminal.

---

### Post by darrenh on 2005-05-11
I assume you're used to using a browser to configure CUPS. You should be seeing a warning like

"Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing."

at the top of the screen.

Can you not do this? It runs gnome-cups-manager as mentioned by harryc.

The only reason I can see to enable configuration via browser is if you want to configure a remote machine. You mention localhost:631, so I guess not.

Darren

---

### Post by tirog on 2005-05-12
I configure my printer according to [http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php). After 
"Enter this command to restart the Common UNIX Printing system (CUPS):
# killall -HUP cupsd"
I'll run gnome-cups-manager, but:
"The CUPS server could not be contacted"

May configure by localhost:631 run?

---

