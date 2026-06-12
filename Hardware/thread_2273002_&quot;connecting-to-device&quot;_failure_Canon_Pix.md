---
title: "&quot;connecting-to-device&quot; failure Canon Pixma iP 90v on UBuntu 14.10"
date: 2015-04-10
forum: Hardware
---

### Post by edringschellmann on 2015-04-10
My printer does not print. There is this error message. Who has an idea?

---

### Post by pdc on 2015-04-11
so that is a senior printer; from 2007; and the driver used is likely gutenprint; [http://gimp-print.sourceforge.net/p_Supported_Printers.php](http://gimp-print.sourceforge.net/p_Supported_Printers.php) they feel it should be supported; 

if you click on this link [http://localhost:631/printers/](http://localhost:631/printers/) is there an entry in the left-hand column that is called QUEUE NAME for your ip90v please? and if so, is gutenprint mentioned in the right-hand column? 

.......... are you using 32bit ubuntu? 

______________--

can you **_copy_** this command, and **_paste_** it into a terminal please; if any of this is not understood, please ask us to explain .......

```
dpkg -l | grep cups
```

__________

and can you please copy the result and then paste it back here using the # sign above to open the code box; and if you paste the result in there 

can you also paste this command ```
lsusb
``` and again copy the result and paste back here please;

---

