---
title: "Ubuntu 12.04 HP Deskjet 2514"
date: 2015-02-18
forum: Hardware
---

### Post by Xaerooo on 2015-02-18
Hallo,

i tried to get my Deskjet 2514 running on Ubuntu 12.04. (USB)

Steps i did:

1. Installed hplip and hplip-gui
2. Run sudo hp-setup -i

[PHP]
HP Linux Imaging and Printing System (ver. 3.12.2)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

(Note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.)


--------------------------------
| SELECT CONNECTION (I/O) TYPE |
--------------------------------

  Num       Connection  Description                                               
            Type                                                                  
  --------  ----------  ----------------------------------------------------------
  0*        usb         Universal Serial Bus (USB)                                
  1         net         Network/Ethernet/Wireless (direct connection or JetDirect)
  2         par         Parallel Port (LPT:)                                      

Enter number 0...2 for connection type (q=quit, enter=usb*) ? 1

Using connection type: net

error: No device selected/specified or that supports this functionality.
[/PHP]


In addition i tried to install the printer over the setup of ubuntu. 

If the installation is complete and i trie to print a testpage i got following error message: Rendering completed

But the Printer does nothing.


Has anyone an idea how to fix it?

---

### Post by kc1di on 2015-02-18
Try setting it up using Cups webpage. 
in your favorite browsers address line type```
localhost:631
```
follow instructions there and add the printer. The see if it works. 
good luck. 
p.s. you may be asked for your user name and password. try ```
root <usr> and your ubuntu password
```

---

### Post by ajgreeny on 2015-02-18
You need a newer version of hplip (3.12.6) for that all in one printer from [http://prdownloads.sourceforge.net/hplip/hplip-3.15.2.run](http://prdownloads.sourceforge.net/hplip/hplip-3.15.2.run) then follow the instructions at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

It might seem a bit overwhelming if you don't like the terminal, but the system does all the work for you if you follow carefully everything you're told there.

---

### Post by mörgæs on 2015-02-18
Another option is wait a few days until you find Ubuntu 14.04.2. If you install this one you will automatically get the correct hplip.

Not that I don't trust the advice above, it's only if you find the process too complicated.

---

### Post by ajgreeny on 2015-02-18
> **mörgæs said:**
> Another option is wait a few days until you find Ubuntu 14.04.2. If you install this one you will automatically get the correct hplip.

Not that I don't trust the advice above, it's only if you find the process too complicated.
Yes, I agree with that as well; 14.04 is generally a better OS than 12.04, but no doubt that will be partly hardware dependent.

---

