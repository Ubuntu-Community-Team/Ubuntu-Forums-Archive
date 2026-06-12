---
title: "cann't Enable Desktop Effects in OPTIPLEX 755"
date: 2008-10-16
forum: General Help
---

### Post by brijith on 2008-10-16
hai All,

I have installed **[COLOR="DarkOrange"]Ubuntu Hardy 8.04[/COLOR]** in DELL OPTIPLEX 755 PC. Everything is fine except I cannot enable Desktop Effects.
When I try to enable it, it simply says *Desktop effects cannot be enabled*.. 

What to do .....? 


[COLOR="DarkOrange"]**Thanks**[/COLOR]

---

### Post by prshah on 2008-10-16
> **brijith said:**
> 
Everything is fine except I cannot enable Desktop Effects.
When I try to enable it, it simply says *Desktop effects cannot be enabled*

Open a terminal (Applications-Accessories-Terminal) and post the output of the command ```
compiz --replace 
``` This will try to enable desktop effects manually, and give a relevant error message if it cannot be enabled.

---

### Post by brijith on 2008-10-16
```

coreubuntu@coreubuntu:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:94c1 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

---

