---
title: "[SOLVED] removing leftover dependancies"
date: 2008-11-02
forum: General Help
---

### Post by nix4me on 2008-11-02
I installed virtualbox and decided later that i don't like it.  How do I remove all of the dependancies that were installed?  Using synaptic to remove virtualbox does just that, then leave all of the qt libraries behind.  Is there a log file of what got installed?  Or another way to identify the orphan packages?

Tnanks

---

### Post by Idefix82 on 2008-11-02
There is a tool which identifies orphaned packages. Have a look at this tutorial: [http://ubuntuforums.org/showthread.php?t=140920]("http://ubuntuforums.org/showthread.php?t=140920")
Be careful though, sometimes it reports something as orphaned although you need it. Just because it's not a dependency of anything else on the system, doesn't always mean it's useless. I find the deborphan filter in Synaptic very handy. It's all in the tutorial.

If you want to be extra safe, before removing an orphaned package go to File->History in Synaptic and find it there. If it was installed on the same day as something that you know you have removed since, chances are that you really don't need it.

---

### Post by meindian523 on 2008-11-02
Or in terminal```
sudo apt-get autoremove
```It gives a list of what shall be removed too,so you can say no if you see something you still need but reported as not required.

---

### Post by stoneage on 2008-11-02
> **nix4me said:**
>  Or another way to identify the orphan packages?

Tnanks

deborphan

---

### Post by nix4me on 2008-11-02
History in synaptic was most helpful.  Thanks for the hint.  I will try deborphan in the future.

Thanks.

---

### Post by Idefix82 on 2008-11-02
You are welcome! Can you mark the thread as solved then?

---

