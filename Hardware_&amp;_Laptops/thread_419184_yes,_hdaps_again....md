---
title: "yes, hdaps again..."
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by hsjC on 2007-04-22
after dozens of failures, I'm now just one inch away from getting hdaps fully working with queue freezing.

My feisty won't let me login after I patched the kernel and recompiled it. GDM says it can't write to the authentication file.

Just wondering, has anyone gotten queue freezing working? How exactly should I recompile the kernel?

---

### Post by airbornespent on 2007-08-10
These instructions worked nicely:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Disk_Protection](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Disk_Protection)
Only problem is that hdapsd doesn't want to work right.

EDIT: I got the hdapsd working! There is a note on the thinkwiki page I linked to above that mentions using gcc-3.4 to compile hdapsd, I ignored it at first but then I checked synaptic. You must install gcc-3.4 then when compiling hdapsd use:```
gcc-3.4 -o hdapsd hdapsd-*.c
sudo cp hdapsd /usr/local/sbin/
```

At this point you can run the command "hdapsd" to see the options, ex. "hdapsd -d sda -s 15" 

Now I simply need to figure out where is te best place to start the daemon on startup. rc.local is one place, but I'd personally like it to start ASAP after boot, which means as close to when the tp_smapi modules are loaded as possible.

---

