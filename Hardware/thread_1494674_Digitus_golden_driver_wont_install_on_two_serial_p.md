---
title: "Digitus golden driver wont install on two serial port PCI card"
date: 2010-05-27
forum: Hardware
---

### Post by cebif on 2010-05-27
[SIZE="2"]I am having trouble getting the driver istalled for a 2x serial port Digitus PCI2S550 card.
The instructions are to first, untar the driver package in /temp:
```
sudo tar xvfz golden* 
cd golden
sudo make clean ; make install
```
After this in the Terminal I see a continuous error retrying to enter the driver folder in golden/.
When I then force the Terminal to quit. I then try to apply permissions recursively so it can enter driver with:
```
sudo chown -R root.root golden
```
When I try again:
```
sudo make clean ; make install
```
it has the same problem. The chown command does not seem to work. What can I do to get the driver installed?
[/SIZE]

---

### Post by cebif on 2010-05-28
Can anyone please help.

---

