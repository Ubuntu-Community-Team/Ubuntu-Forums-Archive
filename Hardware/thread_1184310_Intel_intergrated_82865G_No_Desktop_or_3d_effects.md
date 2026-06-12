---
title: "Intel intergrated 82865G No Desktop or 3d effects"
date: 2009-06-11
forum: Hardware
---

### Post by Ravernomina on 2009-06-11
Hello, I installed ubuntu 9.04 jaunty jackolpe on a friends Micro desktop (Hp dc5000 MT). And no matter what i do i cannot get 3d or desktop effects to work. Any help would be great thanks. TYVM!!!!
    Ravernomina

---

### Post by Ravernomina on 2009-06-11
Bump

---

### Post by Ravernomina on 2009-06-11
Bump

---

### Post by Ravernomina on 2009-06-11
Bump

---

### Post by PRC09 on 2009-06-11
You might give this a try....

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by prshah on 2009-06-11
> **Ravernomina said:**
> And no matter what i do i cannot get 3d or desktop effects to work. 

We need more information for troubleshooting. For this, please open a terminal (Applications-Accessories-terminal) post back the results of the following command```
compiz --replace
```

The errors (if any) will give us a clue as to why you cannot enable desktop effects.

---

### Post by Ravernomina on 2009-06-11
this is what i got back from the code.


```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```

---

### Post by Ravernomina on 2009-06-11
Bump

---

### Post by densou on 2009-06-11
no way you'll able to run compiz in a decent manner with a mere i8xx on Jaunty.

Have you followed the guide provided in the thread posted by PRC09 ?

---

### Post by Ravernomina on 2009-06-14
Bump

---

### Post by Ravernomina on 2009-06-15
Bump

---

### Post by Ravernomina on 2009-06-16
Bump

---

### Post by kendrick on 2009-06-19
Reverting your intel driver to version 2.4 will get compiz working again. I have the same chip as you and this worked for me. I suggest restarting after installing the package instead of restarting X because X didn't restart for me.
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

