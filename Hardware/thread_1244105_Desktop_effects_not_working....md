---
title: "Desktop effects not working..."
date: 2009-08-19
forum: Hardware
---

### Post by JigglyWiggly_ on 2009-08-19
Ok I am getting mad, here is what is happening: I have 2 montirs on an x800 xt platinum, no problems in a working OS like Windows 7. So I added both dispalys with the display manager after a lo of hell, and often when I reboot my left monitor is in like 8 colors. It's awful. Then when I finally get htem setup and try to enable fancy desktop effects, doesn't work. Here is the compiz output I mean what hte hell? This isn't a hard thing to do.
1 montior is 1680x1050 and the other is 1600x1200
```
harris@harris-jaunty:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (3280x1200) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 


```

---

### Post by JigglyWiggly_ on 2009-08-19
I saw this [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

 and tried this ./ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/jaunty

then got stupid *** permission denied and it doesn't matter if I do su. I mean seriously wh is such a simple thing like this impossible? I mean I've used Ubuntu on my server and it works nicely but using it as a desktop is just becoming so damn stupid. No wonder 1% market share.

---

