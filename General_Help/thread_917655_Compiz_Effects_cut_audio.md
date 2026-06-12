---
title: "Compiz Effects cut audio"
date: 2008-09-12
forum: General Help
---

### Post by Dejai on 2008-09-12
Using compiz effects for opening and minimizing windows such as the burning effect of the 3d cube seem to cut music or make it choppy. I am running Ubuntu 8.04. Its nothing really important but something to think about. Anyone have a fix?

---

### Post by prshah on 2008-09-12
> **Dejai said:**
> Using compiz effects for opening and minimizing windows such as the burning effect of the 3d cube seem to cut music or make it choppy. I am running Ubuntu 8.04. Its nothing really important but something to think about. Anyone have a fix?

You can turn down the "intensity" of certain effects using System-Preferences-Advanced Desktop Effects Settings-Animations-Effect Settings-"Animation Timestep for intense effects". (Note: you have to INCREASE the timestep to REDUCE the load on your system)

However, I don't think this is your problem; music plays fine for me when using cube / burning effects, even though I'm only using Intel onboard display.

I'd suggest looking at your graphics subsystem; specifically, is direct rendering enabled? Open a terminal: Applications-Accessories-Terminal; and give the below command to check```
glxinfo | grep -i direct
```

---

