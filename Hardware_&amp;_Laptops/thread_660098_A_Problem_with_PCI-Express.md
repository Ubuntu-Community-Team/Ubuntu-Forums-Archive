---
title: "A Problem with PCI-Express"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by swazidoughman on 2008-01-06
one day i booted up to windows to test my new graphics card (8800GT)  with some games.
I also decided to start up CPU-Z so i could get some info on the new proccessor a recently bought, I then noticed that it said "PCI express width- 8x max supported width-16x" this seemed strange so i went into my BIOS & i guess Acer computers (premade computer) has their own little locked up BIOS that they decided to make the PCI-Express only run at 8x speed, sadly there was no option in the bios for changing it to 16x, so need some help on this little issue on getting my pci express on 16x, a link to a program would be nice.

---

### Post by Yellow Pasque on 2008-01-06
I doubt you'l find a solution if it's locked in the BIOS (short of updating the BIOS). Do you know what kind of motherboard you have? If not:
```
dmidecode | more
```
Mobo info should be near the beginning. Use the space bar to see the next screen and press 'q' to quit out of the more display and go back to the prompt.

---

### Post by swazidoughman on 2008-01-06
Nvidia MCP61 Nforce 405 is the model

CPU-Z says that it can do 16x but its only doing 8x

oh i almost  forgot, its an AM2 socket  board so its for AMD procs

---

### Post by Yellow Pasque on 2008-01-06
That's the chipset, but I was looking for the mobo model. Look on Acer's page for your system model and see if it uses a regular mobo or something made specially for Acer. It's probably the latter.
Alos, look for BIOS updates.

---

### Post by swazidoughman on 2008-01-07
the model is the EM61SIWEM61PM. I think its a nomral mobo, but it has a custom BIOS made for Acer computers

---

### Post by swazidoughman on 2008-01-09
bump (plz dont kill me)

---

