---
title: "[SOLVED] Host name conflict"
date: 2008-09-22
forum: General Help
---

### Post by Peter K Nicol on 2008-09-22
Ubuntu Hardy 8.04
I have installed the maths program wxMaxima (and Maxima). On starting wxMaxima I get the message "not connected to Maxima!". On a Dutch forum I found that if I change the host name to "127.0.0.1 localhost" it works.
Unfortunately this causes other problems.
To be able to open Synaptic or Update Manager the host name has to be set to "127.0.0.1 peter-laptop". 
Is there a way out of this conundrum?:(

---

### Post by jerome1232 on 2008-09-22
> **Peter K Nicol said:**
> Ubuntu Hardy 8.04
I have installed the maths program wxMaxima (and Maxima). On starting wxMaxima I get the message "not connected to Maxima!". On a Dutch forum I found that if I change the host name to "127.0.0.1 localhost" it works.
Unfortunately this causes other problems.
To be able to open Synaptic or Update Manager the host name has to be set to "127.0.0.1 peter-laptop". 
Is there a way out of this conundrum?:(

This doesn't seem right to me, my hosts file already has that entry and everything works fine, the computers hostname is lifebane respectivly
```
127.0.0.1       localhost
127.0.1.1       lifebane
```

---

### Post by Peter K Nicol on 2008-09-22
Thanks Jerome -it works perfectly.

---

