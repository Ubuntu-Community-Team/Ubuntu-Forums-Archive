---
title: "Clean Uninstall of Evolution"
date: 2008-07-16
forum: General Help
---

### Post by jake1017 on 2008-07-16
Is there any way to do a clean uninstall of Evolution?

---

### Post by bp1509 on 2008-07-16
by clean do you mean a complete removal?  In Synaptic you can right click on the following entries:

evolution
evolution-common
evolution-data-server
evolution-data-server-common
evolution-plugins
evolution-webcal

and select Complete Removal

---

### Post by scragar on 2008-07-16
hmn, I checked```
sudo apt-get --purge remove evolution-*
```but that want's to remove way more than it should(the panels, quick user switch applet etc)

you could try just removing the packages manualy:
```
sudo apt-get --purge remove evolution evolution-common evolution-data-server-common evolution-data-server evolution-webcal
```

---

### Post by Stebanoid on 2008-07-18
you could try just removing the packages manualy:
```
sudo apt-get --purge remove evolution evolution-common evolution-data-server-common evolution-data-server evolution-webcal
```[/QUOTE]

this doesn't solve the problem. that want's to removethe panels, quick user switch applet etc anyway

---

### Post by joanmunoz on 2009-02-22
Hi!

I've the same problem (want to remove Evolution and Synaptics wants to remove more stuff). So I did:

sudo apt-get --purge remove evolution-common

And that's all! Just 1 packet erased and 97 Mb free. Hope this helps.

Regards!

Joan

---

