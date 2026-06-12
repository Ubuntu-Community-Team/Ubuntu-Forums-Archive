---
title: "Is there a &quot;Uninstall&quot; program in ubuntu?"
date: 2008-10-05
forum: General Help
---

### Post by Vertoxic on 2008-10-05
is there anything like that? for example i want to delete Counter Strike Source completely and steam, how can i go about that?

---

### Post by Forbees on 2008-10-05
you should beable to remove it with uninstall from wine/crossover

---

### Post by Sponzenbroekske on 2008-10-05
> **Vertoxic said:**
> is there anything like that? for example i want to delete Counter Strike Source completely and steam, how can i go about that?

wine application can be uninstalled trough wine itself and native linuxprograms can be remove in synaptic or adeptmanager (choose complete removal to remove the config files too), or the terminal (sudo apt-get remove PROGRAMTHATYOULIKETOBEREMOVED

---

### Post by hansdown on 2008-10-05
Hi Vertoxic.

If you go to system> administration> synaptic package manager you can search for the programs you wish to uninstall.

Click on the box of the installed program, and it will give you the option of reinstalling, mark for complete removal, etc.

Be careful that other packages don't share dependancies.

---

### Post by OutOfReach on 2008-10-05
You can remove programs throught Synaptic: System>Administration>Synaptic Package Manager and search for the package that you want to remove.

Or you can do it throught a terminal like so:
```
sudo apt-get remove PROGRAM_NAME
```

---

### Post by porchrat on 2008-10-05
> **OutOfReach said:**
> You can remove programs throught Synaptic: System>Administration>Synaptic Package Manager and search for the package that you want to remove.

Or you can do it throught a terminal like so:
```
sudo apt-get remove PROGRAM_NAME
```

He wants to uninstall counterstrike from Wine somehow I doubt he is going to find that in synaptic

---

### Post by Vertoxic on 2008-10-05
yah i could not find the CS in SP, however i was able to remove CS tru wine it self thank you guys!

---

