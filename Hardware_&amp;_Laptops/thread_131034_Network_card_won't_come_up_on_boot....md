---
title: "Network card won't come up on boot..."
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by s'neil on 2006-02-15
and it used to.

I have to sudo network-admin and enable it from there and it goes just fine.

its a 3com 905 nic, and i can't think of doing anything network related that would break it.

why does my card not come up on boot but will once im in X ?

---

### Post by jamesr on 2006-02-15
Goto the console and Type 

ifconfig -a

lspci

and post results
Is the NIC being seen automatically. Normally the 3com905 should be seen but the 3com509 is a different matter.

---

### Post by s'neil on 2006-02-15
right

---- fresh reboot ----
ifconfig reveals nothing
---- after enabling via network-admin
ifconfig reveals all the interfaces (eth0 eth1 lo)

lspci lists all the cards at anypoint

---

### Post by jamesr on 2006-02-15
After a fresh boot see if you can 

sudo modprobe 3c905

I would believe it should work

 then ifconfig -a should show eth0 but no address yet

sudo dhclient 

sudo ifconfig -a

should show address information.
 
Then check the file /etc/modules there should an entry for the 3c905
If not present in the file make a copy of the file

sudo cp /etc/modules /etc/modules_bak

First edit modules file
sudo nano /etc/modules

and add a line
3c905
at the line of the file


Second edit interfaces file having made a copy

sudo nano /etc/network/interfaces

add lines
auto eth0
iface eth0 inet dhcp

With respect to the  eth1 what is the other card?

I hope that this helps. I am a great believer in doing the process in stages with copies then if you have screwed up you can go back a stage.

---

### Post by s'neil on 2006-02-16
thanks for the help, i shall try it later.

eth1 is an integrated motherboard jobbie that I don't use

---

### Post by jamesr on 2006-02-16
Any Particular reason why you do not use it?

 I am curious.

So many people seem to having this problem, I am going to write a crib sheet which I can copy and paste into replies.

---

### Post by baustiech on 2007-11-28
Check /etc/iftab

That file manually maps MAC addresses to eth device names.  It always causes weird problems after changing NICs, many more than its intended purpose should allow it to cause.

---

