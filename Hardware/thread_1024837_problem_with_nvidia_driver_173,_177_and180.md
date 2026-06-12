---
title: "problem with nvidia driver 173, 177 and180"
date: 2008-12-29
forum: Hardware
---

### Post by funnypanks on 2008-12-29
i have a 8800gs in my computer and whenever i install any driver the system freezes. In windows only the 169.xx drivers work, the rest cause a system freeze after only a couple of minutes of use. 
i was wondering if it is possible to install the 169.xx drivers in intrepid and add my id of 10de 0606 to that driver, since my card was not originally supported by that driver, but other g92 cards were.

---

### Post by hotweiss on 2008-12-29
Try installing the 177 drivers using Envy:

[http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

---

### Post by funnypanks on 2008-12-29
> **hotweiss said:**
> Try installing the 177 drivers using Envy:

[http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

thanks for the help. but why would that make a difference? it seems like the drivers are working. just they aren't stable on my configuration. i don;t mind going to hardy where 169.xx drivers are compatible, but can i add my card's id into the nvidia driver?

---

### Post by hotweiss on 2008-12-29
> **funnypanks said:**
> thanks for the help. but why would that make a difference? it seems like the drivers are working. just they aren't stable on my configuration. i don;t mind going to hardy where 169.xx drivers are compatible, but can i add my card's id into the nvidia driver?

I'm not an expert, but Envy usually fixes all of my graphic card problems.

---

### Post by funnypanks on 2008-12-30
> **hotweiss said:**
> I'm not an expert, but Envy usually fixes all of my graphic card problems.

that didn't help. is there any way to add the id's to the drivers? like in windows its possible to add to the inf file.

---

### Post by funnypanks on 2009-01-01
> **funnypanks said:**
> that didn't help. is there any way to add the id's to the drivers? like in windows its possible to add to the inf file.

bump

---

### Post by funnypanks on 2009-01-05
bump

---

### Post by hotweiss on 2009-01-09
> **funnypanks said:**
> bump

Try this command to get new id's:

> sudo update-pciids

---

