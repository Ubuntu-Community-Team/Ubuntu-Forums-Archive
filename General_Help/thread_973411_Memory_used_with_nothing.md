---
title: "Memory used with nothing"
date: 2008-11-06
forum: General Help
---

### Post by firetree on 2008-11-06
When I am execute top command.  It shows that I am using most of my memory. When I sort the applications according to their memory usage, there exists no application which can create such a usage. Memory is showed as consumed mostly in used part, not in cached or buffers part. 
Why is my memory is used that much?  If I open several applications, I start to use swap and my computer slows. How can I solve that?

top command:
```

Tasks: 131 total,   3 running, 128 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.7%us,  0.3%sy,  0.0%ni, 93.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1546340k total,  1286524k used,   259816k free,   195796k buffers
Swap:  1510068k total,   339832k used,  1170236k free,   406176k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
24547 umut      20   0  185m  71m  22m R  1.7  4.7   1:21.58 firefox            
24120 root      20   0  390m  42m 8020 S  3.7  2.8   2:08.64 Xorg               
24259 umut      20   0 87276  35m  14m S  0.0  2.4   0:03.37 nautilus           
24582 umut      20   0 48232  27m  11m S  0.0  1.8   0:00.80 evince             
24258 umut      20   0 48264  24m  13m S  0.0  1.6   0:03.84 gnome-panel        
24501 umut      20   0 65360  18m  10m R  0.7  1.2   0:02.14 gnome-terminal     
24327 umut      20   0 24172  16m 7020 S  0.7  1.1   0:09.06 compiz.real        
24443 umut      20   0 43848  14m 9920 S  0.0  1.0   0:00.29 mixer_applet2      
24332 umut      20   0 25000  13m 9052 S  0.0  0.9   0:00.20 update-notifier    
24367 umut      20   0 24984  12m 8856 S  0.0  0.8   0:00.18 trashapplet        
24447 umut      20   0 25152  12m 8700 S  0.0  0.8   0:00.20 fast-user-switc    
24346 umut      20   0 24156  11m 7120 S  0.0  0.8   0:00.16 python             
24477 umut      20   0 20840  11m 7300 S  0.0  0.8   0:03.00 gtk-window-deco    
24345 umut      20   0 23048  10m 7688 S  0.0  0.7   0:01.26 nm-applet          
24336 umut      20   0 62336  10m 8604 S  0.0  0.7   0:00.07 evolution-alarm 

```

free -m command
```

             total       used       free     shared    buffers     cached
Mem:          1510       1259        250          0        191        396
-/+ buffers/cache:        671        838
Swap:         1474        331       1142

```

---

