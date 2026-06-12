---
title: "CCSM Trouble Installing"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by Talynz on 2009-09-19
Alright when i type this in the terminal 

sudo apt-get install simple-ccsm

i get this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

What does this mean and how do i fix it?
please help

---

### Post by raymondh on 2009-09-19
> **Talynz said:**
> Alright when i type this in the terminal 

sudo apt-get install simple-ccsm

i get this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

What does this mean and how do i fix it?
please help

Open terminal and try to run/type the command.
```

dpkg --configure -a
```

Post back any error or success.

---

### Post by Talynz on 2009-09-19
ok i typed dpkg --configure -a and this came up 

Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...

then i typed sudo apt-get install simple-ccsm

then this came up

E: Couldn't find package simple-ccsm

what do i do now? thanks.

---

### Post by raymondh on 2009-09-19
> **Talynz said:**
> ok i typed dpkg --configure -a and this came up 

Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...

then i typed sudo apt-get install simple-ccsm

then this came up

E: Couldn't find package simple-ccsm

what do i do now? thanks.

In terminal, 

```
sudo apt-get update
sudp apt-get upgrade
```

close terminal and open synaptic (system > admin > synaptic > type your password). Search for (it's there, just checked) simple-ccsm and install thru synaptic.

---

### Post by Partyboi2 on 2009-09-19
> **Talynz said:**
> ok i typed dpkg --configure -a and this came up 

Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...

then i typed sudo apt-get install simple-ccsm

then this came up

E: Couldn't find package simple-ccsm

what do i do now? thanks.
Open up Software Sources (System>Admin>Software Sources) and check that you have the 'Uninverse' repository enabled under the first tab.

---

