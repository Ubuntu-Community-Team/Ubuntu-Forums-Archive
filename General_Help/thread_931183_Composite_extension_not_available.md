---
title: "Composite extension not available"
date: 2008-09-27
forum: General Help
---

### Post by jokakid on 2008-09-27
ok well i cant get my desk top effects enabled 

Compiz check gives me this noob here so help me out 

```

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [FAIL]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Composite manually disabled 

Would you like to know more? (Y/n) Y

 It has been detected that the "Composite" option of your /etc/X11/xorg.conf
 has been set to "Disable" 

 Open the file being root and change "Disable" to "Enable"
 Then restart X and try again. 
```

---

### Post by chavanak on 2008-09-27
Hi,
Open a terminal.(Application--> Accessories--> Terminal)
Type in "sudo gedit/etc/X11/xorg.conf"(without quotes)
Search for  "Composite" "disabled"
Change disabled to enabled and press ctrl+alt+backspace.
Now try to run compiz.

Use extreme caution while editing the file just edit what i told you to edit, otherwise you can brick your system.
Cheers

---

