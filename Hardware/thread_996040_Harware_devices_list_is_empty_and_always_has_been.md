---
title: "Harware devices list is empty and always has been"
date: 2008-11-28
forum: Hardware
---

### Post by MountainX on 2008-11-28
I'm running Hardy with nvidia. I installed Hardy while it was in beta. My hardware devices list was empty from the first day even though I use the proprietary nvidia driver (and it was installed). 

I have installed nvidia using EnvyNG, using the usual Ubuntu method and even directly from nvidia (compiling with their installer). In all cases, my hardware devices list is empty. Currently I'm using the EnvyNG-installed driver.

How can I resolve this so that my hardware devices list is correct? Thanks.

---

### Post by MountainX on 2009-02-02
bump

---

### Post by luvr on 2009-02-02
You mean that the list in the *Hardware Drivers* utility is empty?

Must have something to do with some sort of *nvidia-glx* package not being installed. Could you verify if any of those packages are installed? (E.g., open the *Synaptic Package Manager,* and search for *nvidia-glx.*) I have a feeling that the *Hardware Drivers* list is related with these types of packages.

---

### Post by MountainX on 2009-02-02
> **luvr said:**
> You mean that the list in the *Hardware Drivers* utility is empty?

Must have something to do with some sort of *nvidia-glx* package not being installed. Could you verify if any of those packages are installed? (E.g., open the *Synaptic Package Manager,* and search for *nvidia-glx.*) I have a feeling that the *Hardware Drivers* list is related with these types of packages.

Yes, sorry. I meant *Hardware Drivers*. The list is empty.

Synaptic shows that I have nvidia-glx-new-envy installed as well as 3 related packages (dev, source, settings).

---

### Post by Yashiro on 2009-02-02
The built in applet is pretty poor. It only really cares about the drivers it knows about. Don't worry about it.

---

