---
title: "[SOLVED] Extending the &amp;quot;Check Forced&amp;quot; mounting times?"
date: 2008-11-24
forum: General Help
---

### Post by iheartubuntu on 2008-11-24
Every couple weeks I get the 
> 
checking root File system...

/dev/sda1 has been mounted 25 times without being checked, check forced.

Is there any way to extend this to 50 times, instead of 25? That way it will run the check every month or so for me. I can always force a check myself if I need be by pressing ESC and going into the recovery mode if need be.

---

### Post by pennacook on 2008-11-24
Use tune2fs. 

```
tune2fs -c 50 /filesystem
```

---

### Post by rondackcpu on 2008-11-24
There is a command "tune2fs" which will do just what you want.  Read "man tune2fs" to get more information about the command, but you might start with "sudo tune2fs -c 50 /dev/sda1" in a terminal.  I usually pick an even larger number, say 87, to delay even further.

CRS

---

### Post by iheartubuntu on 2008-11-24
> **rondackcpu said:**
> There is a command "tune2fs" which will do just what you want.  Read "man tune2fs" to get more information about the command, but you might start with "sudo tune2fs -c 50 /dev/sda1" in a terminal.  I usually pick an even larger number, say 87, to delay even further.

CRS

Great, thanks!

---

