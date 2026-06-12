---
title: "ati radeon 9000 on hardy"
date: 2008-09-30
forum: Hardware
---

### Post by Aeron on 2008-09-30
Hello guys!
I'm trying to install the owners drivers for my ati radeon 9000.
i downloaded them here
[http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html](http://ati.amd.com/support/drivers/linux/previous/linux-r-8-28-8.html)

now. the problem is that when i run the drivers, the installer tell's me that it can't find the xserve. I beleive that all this is due to the fact that hardy has a new xorg server which should be the 1.4.4.90(correct me if i'm wrong). But the installer is looking for the 7. I don't know how to see what version of xseve i'm running.

Anybody knows what could i do to install these drivers?

I'm new, and i don't know much about linux...i'm a litte bit lost here.

help...
thanks

---

### Post by travm on 2008-09-30
Nope, not the problem.
You should find a guide for installing the drivers.  Its not as simple as running the driver install program.  
you need to generate installer packages.  
That old version of the driver most likely does not support ubuntu.
I would recommend using the open source radeon driver.

---

### Post by Aeron on 2008-10-01
OK, but i thin that ubuntu already comes with them doesn't it? If not where can i find them?
Anyway the driver package i tryed to install it is suppoused user friendly it should install with a wizard, but the wizard won't start, because of the x-server
I havent' installed any driver yet, and it lags.....do you know anyone using the radeon 9000 properly?

---

### Post by eswahlstedt on 2009-02-13
I am also trying to get my ati radeon 9000 card to work on ubuntu 8.10, but after I go throught the terminal it just stops after it says x server unable to detect

Anyone have any ideas?

---

### Post by M_Mungo on 2009-02-18
I too have fallen victim to non functioning ATI Radeon 9000 syndrome.  Ubuntu Hardy 8.04 using integrated graphics now.  Purchased a new GPU Card.  Tried ATI driver from ATI website as well.  Tried many other solutions and managed only to bog down the entire system which lead to a reinstallation.  Is there an expert out there that can help us?

---

### Post by eswahlstedt on 2009-02-27
I know that sabayon recognizes the ati radeon 9000 video card.  Is there anyway I can use the fact that it works in sabayon to use it in ubuntu 8.10?

---

### Post by bnc9 on 2009-02-27
hmm sorry for the double post details on post #8

---

### Post by bnc9 on 2009-02-27
> **Aeron said:**
> OK, but i thin that ubuntu already comes with them doesn't it? If not where can i find them?
Anyway the driver package i tryed to install it is suppoused user friendly it should install with a wizard, but the wizard won't start, because of the x-server
I havent' installed any driver yet, and it lags.....do you know anyone using the radeon 9000 properly?
Yes ubuntu comes with the open source drivers but you might have to enable them enter 
```
gksu displayconfig-gtk

```
and check what driver is running

---

### Post by eswahlstedt on 2009-05-06
Does anyone know if this card still works with ubuntu 9.04 or is it a lost cause at this point?

---

