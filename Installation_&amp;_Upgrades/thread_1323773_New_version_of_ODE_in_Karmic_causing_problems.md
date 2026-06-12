---
title: "New version of ODE in Karmic causing problems?"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by mindstorm23 on 2009-11-12
I recently installed Karmic, and some development that I do involves the Open Dynamics Engine (ODE), programming in Electro using Lua. I have code that worked perfectly on Jaunty, which had an ODE package called libode0-dev, but when I try to run the same code in Karmic, I get errors along this line:

```
ODE INTERNAL ERROR 2: Bad argument(s) in dxSphere()
Aborted
```

I noticed that the package for ODE in Karmic was simply libode-dev (no "0"), and the ODE runtime library was libode1. How different are these libraries? Would these difference cause the problems I'm seeing? If I need to install an older version of ODE, would I have to do that from source?

---

### Post by mindstorm23 on 2009-11-12
Update: I've tried compiling ODE from source, both the newest version and the 0.9 version. No luck yet, though I've found that if I change ODE to be compiled with --enable-double-precision, I get a different error:

```
ODE Message 2: mass must be > 0 in dMassCheck() File mass.cpp Line 44

ODE INTERNAL ERROR 1: assertion "dMassCheck(mass)" failed in dBodySetMass() [ode.cpp]
Aborted
```

I'm still not sure hot to proceed. Which one of these errors is "closer" to working? What do they mean? Google hasn't helped much :-(

Thanks.

---

### Post by MacacaQQ on 2009-12-29
I have the same problem too...happens in the simspark simulator.

I even tried to add jaunty libode0-dev package but still in vain.

I decide to install jaunty again for now....

---

