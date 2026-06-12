---
title: "Memory useage"
date: 2005-12-05
forum: General Help
---

### Post by Ocxic on 2005-12-05
I added a system monitor to my menu bar for memory usage, and it always stays at 100% after running a few things, doesn't matter what, it always stays at the current level or goes higher. i assume this means ram, tho i don't see a drop in performance this does bother me. it should not stay at 100%.right now it says 100% in use 75% is cache. what is going on here?

---

### Post by amohanty on 2005-12-06
For some bizzare reason its always way off on my box. 
Look at Application->System Tools->System Monitor->Resources and compare the memory monitor in it with the panel. If its the same, then you can probably shutdown some stuff, but methink's something is rotten in the panel applet.

---

### Post by moberry on 2005-12-06
This is pretty common. I think I am write when I say this, a kernel hacker should acknowledge this, or correct me. Linux has basically all your ram cached shortly after boot. I think this happens with the way virtual memory is mapped to processes.  typing "free -h" in a terminal should confirm this. Short answer.... goto the preferences of your panel applett, and change the color for cached ram to black. Fixes it quick. I dont think this is a bug, 2.4 kernels did not allocate memory like that. The code is probably left over from that.

---

### Post by mhs on 2005-12-07
do i use 876mb of ram or 250mb ?
```

             total       used       free     shared    buffers     cached
Mem:          1012        876        135          0         39        586
-/+ buffers/cache:        250        762
Swap:          368         12        356


```

---

### Post by doclivingston on 2005-12-07
[QUOTE=mhs]do i use 876mb of ram or 250mb ?
```

             total       used       free     shared    buffers     cached
Mem:          1012        876        135          0         39        586
-/+ buffers/cache:        250        762
Swap:          368         12        356


```[/QUOTE]

Depends how you define "use", but in the way you probably mean it, you are "using" 263 Mb (876 + 12 - 39 - 586).

---

### Post by RAOF on 2005-12-07
100% ram usage is both perfectly normal and, indeed, desirable.  You notice that it says "100% ram usage, 75% buffers".  This means that 25% of your ram is being used by programs (and loaded libraries etc) and the other 75% is being used to cache (frequently used) data.  **This** means that when your programs read from or write to files, there's a good chance that the file in question is actually being cached (temporarily stored) in RAM, and so access to that file is roughly 1000 times faster than if it needed to be read from/written to the harddrive.

Should your programs later need more ram, the ram that was being used as cache gets freed and re-assigned to the program.

Basically, there's no point in having RAM if it's not being used :)

---

