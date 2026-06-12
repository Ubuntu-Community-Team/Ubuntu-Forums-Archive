---
title: "compiz wont work"
date: 2008-11-19
forum: General Help
---

### Post by Russty of Oz on 2008-11-19
I have compiz and emerald installed but I can't seem to get it to work.  When I type compiz into the terminal I get this response, can anyone advise me on what is required from this?

russty@russty-desktop:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.




Russty

---

### Post by Russty of Oz on 2008-11-19
Doesn't anyone have any suggestions?

Russty

---

### Post by oldos2er on 2008-11-19
Have you tried "compiz --replace"?

---

### Post by Russty of Oz on 2008-11-20
This is what I got for that:

russty@russty-desktop:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.


It seems to be something to do with Xgl not being there, I had a look in the package manager and there is no Xgl there, just the nvidia glx which is installed.

Russty. :confused:

---

### Post by philinux on 2008-11-20
> **Russty of Oz said:**
> I have compiz and emerald installed but I can't seem to get it to work.  When I type compiz into the terminal I get this response, can anyone advise me on what is required from this?

russty@russty-desktop:~$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Russty

Those are normal messages. Compiz running fine here and i get the same.

---

### Post by Russty of Oz on 2008-11-20
well if I then click on something with the terminal still open I get the additional Error lines in the terminal as shown here:

Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Focus event.

---

