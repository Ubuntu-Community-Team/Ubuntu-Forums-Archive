---
title: "touchpad not working: &quot;No synaptics driver load&quot;"
date: 2013-02-14
forum: Hardware
---

### Post by Poliseno on 2013-02-14
i'm running on 12.04.01 and my touchpad suddenly stopped working.
running ```
 sudo modprobe -r psmouse 
``` and ```
 sudo modprobe psmouse 
``` has no effect. As well as checking the "touchpad enabled" option in dconf-editor.
Running ```
synclient -l
``` I get the message > Couldn't find synaptics properties. No synaptics driver loaded?.
Any hint?
Thank you

---

### Post by schragge on 2013-02-14
Are there any errors in */var/log/Xorg.0.log*?
```

grep EE /var/log/Xorg.0.log

```

---

### Post by Poliseno on 2013-02-20
this is the result:

> 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.085] (II) Loading extension MIT-SCREEN-SAVER
[    27.129] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    27.129] (EE) Failed to load module "nv" (module does not exist, 0)
[    27.129] (EE) Failed to load module "vesa" (module does not exist, 0)
[    27.129] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    27.130] (EE) Failed to load module "nouveau" (module does not exist, 0)
[    27.130] (EE) Failed to load module "nv" (module does not exist, 0)
[    27.130] (EE) Failed to load module "vesa" (module does not exist, 0)
[    27.131] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    30.240] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm


---

