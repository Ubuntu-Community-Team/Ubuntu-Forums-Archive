---
title: "Apt-get problem"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by whitef0x on 2009-03-30
kk. This is my problem. I'm trying to install the automake package from ubuntu on the terminal with the apt-get (using sudo) command. For some reason it doesn't work and all it get is this message:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is there another process that is using it?

thx in advance

- the f0x

---

### Post by simtaalo on 2009-03-30
do you have synaptics open? or add/remove programs?

---

### Post by elnetotaca on 2009-03-30
do this;

sudo apt-get autoclean
 sudo apt-get autoremove
 sudo apt-get clean  
 sudo apt-get update
 sudo apt-get upgrade
 sudo apt-get install -f
 sudo apt-get remove --purge nvu

then will be ready to do whatever you want.
sorry my bad English.
Neto.

---

### Post by simtaalo on 2009-03-30
all those apt-get commands are no use at all if the problem is the OP has synaptics open, from the error message that does seem to be the problem.

---

