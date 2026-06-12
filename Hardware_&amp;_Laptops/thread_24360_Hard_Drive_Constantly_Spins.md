---
title: "Hard Drive Constantly Spins"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by thechitowncubs on 2005-04-06
I have noticed that my hard drive is constantly spinning only while in Hoary. It doesn't do this in windows for some reason. It is concerning me because I want this thing to last as long as it possibly can. It also generates much more heat because of this.

Any remedy to this or is this common?

thanks

---

### Post by skoal on 2005-04-06
I'd like to figure out why my IDE light goes off every ~1.5 seconds as well.

---

### Post by thechitowncubs on 2005-04-06
[QUOTE=skoal]I'd like to figure out why my IDE light goes off every ~1.5 seconds as well.[/QUOTE]
 For me, my light stays off when there is no read/write activity but it "spins" constantly.

---

### Post by thechitowncubs on 2005-04-07
Any got any ideas?

---

### Post by rostved on 2005-04-08
[QUOTE=thechitowncubs]I have noticed that my hard drive is constantly spinning only while in Hoary. It doesn't do this in windows for some reason. It is concerning me because I want this thing to last as long as it possibly can. It also generates much more heat because of this.

Any remedy to this or is this common?

thanks[/QUOTE]
I've disabled *laptop-mode* to stop the hard drive from sleeping (and spinning).
First try this, to see if it stops your hard drive from spinning:
```
sudo laptop-mode stop
```
If it does and you don't want laptop-mode to start automatically, then set ENABLE_LAPTOP_MODE to "no" in /etc/default/laptop-mode

---

### Post by rostved on 2005-04-14
Did it solve your issue? 
I'm not sure if this is the right way to do it, but it worked for me.  :smile:

---

### Post by Diego F. on 2005-04-14
I have the same problem with my hd. It didn't happen in 
warty, though the laptop mode was active

---

### Post by mohaham on 2005-04-16
i'm not sure what ur complaining about...
1. whether its the frequent Spin-down and Spin-up  of the hard-disk
or
2. the constant spinning of the hard-disk

if its the first problem thats bothering u.. then u can stop the laptop-mode..
su laptop-mode stop

if its the second problem thats bothering u need to enable the laptop-mode..
su laptop-mode start

**NOTE**: Constant spinning of the Hard-disk causes** lesser wear and tear **of ur hard-disk  than its frequent Spin-up and Spin-down..

---

