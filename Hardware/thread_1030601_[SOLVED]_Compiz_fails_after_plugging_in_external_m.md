---
title: "[SOLVED] Compiz fails after plugging in external monitor"
date: 2009-01-04
forum: Hardware
---

### Post by johnnyloot on 2009-01-04
Hi all,
I'm running Intrepid on a Dell Inspiron 640M which has an Intel GMA950. I plugged in an external monitor to my laptop and everything was working fine (compiz included). I then removed the external monitor and compiz no longer starts. 
Startup message is as follows:

> 
~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

I know that XGL is in fact present since Compiz ran correctly previously and I did not installing/removing between now and then. I tried restarting X and no change. 

I am wondering if has to do with the virtual screen resolution which happens when it goes multi-monitor. 

Any help would be appreciated.

---

### Post by johnnyloot on 2009-01-04
Reposted to Desktop Effects forum. Dont see an option to delete post, so I marked it as solved.

Mods please delete.

---

### Post by starwed on 2009-06-30
I found an explanation of this problem here: [Dual monitor with desktop effects in 8.10](http://codebaboon.com/taxonomy/term/45).

---

