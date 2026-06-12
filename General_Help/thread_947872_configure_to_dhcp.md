---
title: "configure to dhcp?"
date: 2008-10-14
forum: General Help
---

### Post by grayfox444 on 2008-10-14
I just moved into an apartment that has verizon avenue, and they can't set up my Internet unless my computer is In dhcp, can someone help me do this? I'm clueless.

---

### Post by bodhi.zazen on 2008-10-14
First take your network down

```
sudo /etc/init.d/networking stop
```You will lose internet connections ....

Next edit /etc/network/interfaces.

```
gksu gedit /etc/network/interfaces
```Make the line for your network care (usually eth0) look like this :

```
auto eth0
iface eth0 inet dhcp
```Save and exit the file.

Restart you network

```
sudo /etc/init.d/networking start
```

---

### Post by grayfox444 on 2008-10-14
I did the network stop command and got
Reconfiguring network interfaces....       [OK]
Then did the edit line, when I did this the file was completely blank, is this normal?

---

### Post by grayfox444 on 2008-10-14
I tried and it said 
Could not save the file /etc/networking/interfaces
Unexpected error: File not found

---

### Post by bodhi.zazen on 2008-10-14
Ooops, my mistake,

The file you want to edit is

/etc/network/interfaces

I will edit my previous post ...

---

### Post by grayfox444 on 2008-10-15
it's still blank. 

If I choose open ok gedit I can select esd.conf or sources.list

---

### Post by bodhi.zazen on 2008-10-15
What command are you using exactly ?

---

### Post by grayfox444 on 2008-10-15
itwent through. Thanks

---

### Post by Iowan on 2008-10-15
Theoretically... you should be able to select Manual Network Configuration>Wired Connection>Properties and select "Automatic network configuration (DHCP)" from the pulldown.  You'd still need to restart networking.  Personally, I prefer the more direct approach already presented (although I use **sudo nano** instead of **gksu gedit**).

---

