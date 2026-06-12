---
title: "gfx"
date: 2008-07-25
forum: General Help
---

### Post by Jaxite on 2008-07-25
ok i found a script in terminal:
```

jack@jack-laptop:~$ wget http://blogage.de/files/4359/download -O compiz-check
--20:29:41--  http://blogage.de/files/4359/download
           => `compiz-check'
Resolving blogage.de... 78.46.34.206
Connecting to blogage.de|78.46.34.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 27,814 (27K) [application/force-download]

100%[====================================>] 27,814        --.--K/s             

20:29:41 (181.41 KB/s) - `compiz-check' saved [27814/27814]

jack@jack-laptop:~$ chmod +x compiz-check
jack@jack-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) y

```
How do i install my proper drivers?

---

### Post by psyopper on 2008-07-25
If you are trying to run Compiz with an SIS chipset it unfortunately will not work, even with the latest SIS driver installed.

---

### Post by Jaxite on 2008-07-27
damn
i need to update anyway because like i have a really bad screen resolution

---

### Post by wallas on 2008-08-07
Hi

Search in the Synaptic for "video sis". I did it and found 2 packages installed. Although I can't use 3d effects, my resolution is quite good.

W.-

---

