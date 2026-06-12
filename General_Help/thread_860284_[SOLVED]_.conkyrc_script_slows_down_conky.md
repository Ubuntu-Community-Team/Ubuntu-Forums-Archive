---
title: "[SOLVED] .conkyrc script slows down conky"
date: 2008-07-15
forum: General Help
---

### Post by Budoc on 2008-07-15
Hi,

I have spent the last few days discovering and fiddling around with conky so that I can have essential information to hand on my desktop whilst not overloading my system resources.

I have noticed that my current .conkyrc script slows conky down so that it now only updates every 10-30 seconds, despite update_interval being set to 5.0 seconds. conky itself uses barely any CPU or Memory. I initially thought that the slowness could be due to conky trying to find information about drives that are unmounted as launching conky via the terminal yields messages such as:

```
Conky: statfs '/media/my_passport': No such file or directory
```

However, after killing conky and deleting the code from .conkyrc that references the unmounted drives, conky is still slow to update.

Next, I thought that the slowdown could be due to a script that .conkyrc accesses to find out my WAN IP address. However, after deleting the line of code in .conkyrc that executes the ip script, conky is still no quicker.

If I move .conkyrc from my home directory so that conky now runs its default configuration file, conky now updates at normal speed. Thus, I think that the problem must be my sloppy coding in my .conkyrc file. 

Does anybody have any idea where I have gone wrong with my .conkyrc file? I have attached a copy of my .conkyrc and my wan-ip.sh files. I am running Ubuntu 8.04 with default appearance settings. 

Thanks in advance!

---

### Post by Budoc on 2008-07-15
Strangely, after shutting down my computer and powering back on, the problem with the conky script seems to have stopped. I'm not sure why I had this problem originally, but whatever caused it seems to have stopped.

---

