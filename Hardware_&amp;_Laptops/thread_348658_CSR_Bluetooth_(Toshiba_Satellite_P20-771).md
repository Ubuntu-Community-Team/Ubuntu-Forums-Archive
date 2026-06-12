---
title: "CSR Bluetooth (Toshiba Satellite P20-771)"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by test02 on 2007-01-29
Hi folks! I'm new to ubuntu and linux in general, but I have to say that is as far the best Linux Distro around here.

Now, here is the issue: bluetooth on my notebook doesen't work! As the title, I have a integrated USB (CSR chip) bluetooth adapter. The problem is that my BT Adapter is not recognized by ubuntu (or kubuntu) (when I try to open the bluetooth applet in System Settings I get "DCPO error, unable to call services() ).

I have also one thing to notice: on Windows there is an application called "Toshiba BT Monitor", mandatory to enable BT with non-Toshiba stacks. The reason for that is the BT controller is attached also to the ACPI one for energy saving purposes, and this app enables the ACPI switch and Windows detects the BT Device otherwise it will not.

Any ideas?   Thanks!

EDIT 1: 

The BT service is set to autostart at boot, but is always stopped. No matter if I start or restart it.

EDIT 2:
[http://newsletter.toshiba-tro.de/main/](http://newsletter.toshiba-tro.de/main/)

On this page I've found instructions on how to enable bt. There is a program available, dmabt, that enables the BT module. The problem is that it need ToshUtils (I have installed it by repo with Adept, not sure if it's working...), but when I try to run ./dmabt as the readme says I get: "bash: ./dmabt: command not found". I have found this program exploring the "OS Machine compatibility" section (this site prevents hotlinking), and selecting my notebook's model (Toshiba Satellite P20-771). Any help on how to run the dmabt?

EDIT 3:
How can I be sure that Toshutils is working correctly? I chose to install it from repositories with Adept because I tried to install it manually but I coulden't compile it... (GTK+ libraries not found - even that I had them installed...).

Thanks in advance.

EDIT 4:
I've managed to run DMABT, but it says: "BT Available key not supported! BT Wireless Switch check failure! Your BT Device isn't ready!!". I think it depends on the wrong toshutil installation...

---

