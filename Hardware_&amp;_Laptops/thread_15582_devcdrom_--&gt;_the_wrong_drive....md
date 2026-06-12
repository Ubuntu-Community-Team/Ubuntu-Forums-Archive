---
title: "/dev/cdrom --&gt; the wrong drive..."
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by Román on 2005-02-15
Hi all, I am not sure if this is the right forum for this question but here it is:

I have a CD-R and a CD-RW.  The CD-R is connected to the sound chip and its in the filesystem as /dev/hdb.  The CD-RW is /dev/hdc

However, at boot time the wymlink /dev/cdrom is created as /dev/cdrom--->/dev/hdc.

Wich is annoying because when I click the "open drive" in the CD-Player applet it opens the CD-RW and of course it won't play any music.

My solution to this is a script wich does the obvious: 

```
rm /dev/cdrom
link /dev/hdb /dev/cdrom
```  

(or viceversa, I always have to run link --help before linking  :-? )

and run the script (sudo cd.sh)

But of course what I want is a "change this once and be happy" solution

¿anyone knows that answer, or where I should ask the question, or if it was asked before?

TIA!!!

Román

---

### Post by rmjokers on 2005-02-15
Could you just set the device path to /dev/hdb in the applet preferences (right click on applet)?  I dont have an audio CD to try this myself.

---

### Post by Román on 2005-02-15
[QUOTE=rmjokers]Could you just set the device path to /dev/hdb in the applet preferences (right click on applet) (...)[/QUOTE]
  
  I could, but if there is a symlink for the cd it fells logical for the cd player to look for it.
  
  Anyway, today it started ok... /dev/cdrom ---> /dev/hdb... 
  
  Does anyone know who creates that link at boot time?

---

