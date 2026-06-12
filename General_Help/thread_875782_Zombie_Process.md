---
title: "Zombie Process"
date: 2008-07-31
forum: General Help
---

### Post by Dthdealer on 2008-07-31
Whenever I open System Monitor a process (lsb_release) is displayed momentarily before disappearing. According to its status it is a zombie, which I believe relates to my install of Ubuntu being compromised by a botnet or zombie mail-spammer.
Does anyone know what this process is and why it is only listed for a few seconds after I open the System Monitor?

---

### Post by iaculallad on 2008-07-31
I guess it would be safe to ignore the zombie lsb_release process. In fact, there seems to be a command "lsb_release" that gives information about the Distributor ID. If I execute the command on my machine, it would display:

> ian@gutsy-gibbon:~$ lsb_release
No LSB modules are available.

but if I add the -i switch:

```
ian@gutsy-gibbon:~$ lsb_release -i
Distributor ID: Ubuntu

```

For further reading regarding this: do a man

> man lsb_release

---

### Post by justleen on 2008-07-31
zombie proccesses are a normal thing under *nix. 
[http://en.wikipedia.org/wiki/Zombie_process](http://en.wikipedia.org/wiki/Zombie_process)
This wiki also explains why you see it disappearing when you look at it.. (hmm wouldnt schrodinger proccess be more acurate? :) )

---

### Post by Dthdealer on 2008-07-31
Thankyou - I really was worried.
I'm guessing the zombie would have been created by System monitor as it started, either that or it is something hiding its process when I open system monitor. Unlikely though.

> adopted by init (process ID 1), which waits on its children.
How nice of it. :KS

---

