---
title: "installing ubuntu extras"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by garrynigel on 2008-12-29
hi
i wrote dis command sudo apt-get install ubuntu-restricted-extras and dey wer gettin downloaded and installed..
while dey wer getting installed.. the power cut off and evryting stopped..
now after starting the computer again i ran d command again but it gives me a message"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
"
so wat do i do how do i run dis command.. i mean wats the syntax or anyting help me out...

---

### Post by taurus on 2008-12-29
Run these commands from a terminal.

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by garrynigel on 2008-12-29
alrite after dat command i want to run d command again to start from wer i stopped.. do i have to type d command again..like sudo apt-get ubuntu-restricted-extras.. wat will it do start from wer it stopped or.. i mean all the packages wer downloaded but do i have to download again or just type d above command and it will conntinue installing

---

### Post by taurus on 2008-12-29
You can run that command again to install the "restricted" package if you wish.

---

### Post by cariboo on 2008-12-29
You may be able to get away with typing in a terminal:

```
sudo apt-get install -f
```

That should download any missing packages and continue with the installation.

Jim

---

