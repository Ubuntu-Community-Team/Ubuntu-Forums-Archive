---
title: "switchable gpu"
date: 2011-10-16
forum: Hardware
---

### Post by ankitbhardwaj on 2011-10-16
I have a lenovo y560 which have  two gpu one is of intel and other is of ati.
In windows 7 i have driver to control and switch between these two. But in ubunto even ati drivers doesnt worked. It also make my compiz stop working.
Please help me....

---

### Post by fantasm!c on 2011-10-16
You are not the only one with this problem, switchable graphics and linux (or better say, xserver) is still not very nice.

[http://ubuntuforums.org/showthread.php?t=1861541](http://ubuntuforums.org/showthread.php?t=1861541)

And according to this bugreport: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/813809](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/813809) it is not a very high priority issue so if you want to use an ATI/Intel switchable graphics solution you have to stick to the opensource drivers and use the vgaswitcheroo command to disable the ATI and use the Intel. The opensource AMD/ATI drivers are not to fast but at least they are stable.

For the switcheroo commands look here:
[http://phoronix.com/forums/showthread.php?21979-Hybrid-ATI-ATI-Intel-ATI-solution-small-switcheroo-how-to](http://phoronix.com/forums/showthread.php?21979-Hybrid-ATI-ATI-Intel-ATI-solution-small-switcheroo-how-to)

---

### Post by nlion on 2011-10-16
I also have a switchable GPU laptop (HP Envy 14 beats) but I'm not even able to run ANY openGL applications. 

As soon as I attempt to open an application that uses openGL it just instantly closes on me. (This includes even basic games like gl-117)

Any help on this?

edit: Here is where gl-117 dies, I think this is probably useful info
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  13
  Current serial number in output stream:  13
Segmentation fault

```

---

### Post by ankitbhardwaj on 2011-10-17
its not only I can't switch between the two gpus.
after installing the ATI drivers my compiz stop working.
did anyone know about this problem...?

---

