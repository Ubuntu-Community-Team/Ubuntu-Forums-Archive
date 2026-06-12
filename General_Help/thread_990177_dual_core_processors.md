---
title: "dual core processors"
date: 2008-11-22
forum: General Help
---

### Post by StOoZ on 2008-11-22
Im using ubuntu 8.10 (not the 64bit version) on a lenovo 3000 C200 with a core 2 duo processor , does the two cores are functional by default?
how can I see how the usage of each core?? (in % or something similar)

---

### Post by braacken on 2008-11-22
> **StOoZ said:**
> Im using ubuntu 8.10 (not the 64bit version) on a lenovo 3000 C200 with a core 2 duo processor , does the two cores are functional by default?
how can I see how the usage of each core?? (in % or something similar)

Right click panel, add to panel, select cpu scaling monitor.
You can now monitor their usage and change scaling.

---

### Post by lonce on 2008-11-22
Or you can go to your system admin menu and pull up the system monitor.  It should show the 2 cores.  

It should recognize them with no issues at all.

---

### Post by Krupski on 2008-11-22
> **StOoZ said:**
> Im using ubuntu 8.10 (not the 64bit version) on a lenovo 3000 C200 with a core 2 duo processor , does the two cores are functional by default?
how can I see how the usage of each core?? (in % or something similar)

To see how many cores you are using, try this:

```

sudo cat /proc/cpuinfo | grep -i processor

```

You will see something like this for a dual core:

```

processor       : 0
processor       : 1

```

And for a quad core of course:

```

processor       : 0
processor       : 1
processor       : 2
processor       : 3

```


You can also try this:

```

sudo dmesg | grep -i brought

```

You will see something like this:

```

[    0.570027] Brought up 2 CPUs

```

For a quad core of course...

```

[    0.570027] Brought up 4 CPUs

```

Note: The numbers in the brackets are likely to be different than the examples above... it's the "2 cpus" or "4 cpus" that are relevant.

-- Roger

---

### Post by hyper_ch on 2008-11-22
or you could isntall htop and run it from the terminal, that will tell you the load on each core.

---

