---
title: "display UNCLAIMED Ubuntu 14.04"
date: 2014-08-19
forum: Hardware
---

### Post by zebraTango on 2014-08-19
After running sudo lshw too make sure everything works I noticed my GT 840M was coming back UNCLAIMED, link: [http://pastebin.com/F0Niks6e](http://pastebin.com/F0Niks6e).  I installed Synaptic Package Manager and installed the latest drivers but it still comes back UNCLAIMED, has anyone got a solution to this?      EDIT: I also found this gem, link: [http://pastebin.com/GYX0ZDmv](http://pastebin.com/GYX0ZDmv)

---

### Post by Bashing-om on 2014-08-20
zebraTango; Hi !

Per the spec sheet:
> 
Supported Technologies  ->Optimus, PhysX, CUDA, FXAA, Direct Compute


Are you running with hybrid graphics (I.E. Optimus ) ?
Be aware the OEMs do not support us with drivers for their hardware for hybrid graphics.
If you are hybrid, that is one thing, with several solutions;
Else. will have to work on it to see.

In any event show us what we are working with.
Post back the outputs of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

And we will advise on solutions.
[INDENT][INDENT][INDENT]all in knowing how
[/INDENT][/INDENT][/INDENT]

---

