---
title: "Reducing ubuntu to bare minimals"
date: 2008-09-06
forum: General Help
---

### Post by civillian on 2008-09-06
I just upgraded my pc (now I'm dual core 64 bit capable :D) and I was thinking of doing a clean install of ubuntu when I realised that most of the time with a fresh install of ubuntu I get rid of lots of the stuff that comes with ubuntu.

I was thinking about starting with/reducing down ubuntu as just a command line so I can just install the desktop environment and the apps I know I'll use (which I can add to if and when I feel the need). I did some searches on google and the forums and it came up with two possibilities. 

Either I can use the minimal CD image and ONLY install the command line environment, or I could do a standard install and run the following code 
```
sudo apt-get remove --purge x11-common perl python && sudo apt-get autoremove --purge
```

I was wondering what the pros and cons would be of each option, as well as wether or not the minimal install CD would have the same hardware/network recognition as a standard ubuntu live/install CD.

Thanks in advance

civ

---

### Post by Vivaldi Gloria on 2008-09-06
> **C!V!NT said:**
> Either I can use the minimal CD image and ONLY install the command line environment, 

That's the right way.

> or I could do a standard install and run the following code 

But that leaves tons and tons of stuff behind.

> minimal install CD would have the same hardware/network recognition as a standard ubuntu live/install CD.

Yes it has. 

Read CLI in my sig.

---

### Post by civillian on 2008-09-06
> But that leaves tons and tons of stuff behind.

Thats what I thought might be the case, thanks for the reply (as soon as I put together the machine I'll be postin' somewhere, lol)

---

