---
title: "anyone get Jaunty to work with ATI hd2400 pro"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by hockman5 on 2009-04-28
I seem to have been getting closer to getting it to work. I actually can see the desktop and it looks like good quality but then the screen turns white and everything freezes. I have to do ctrl-alt-f1 to get to terminal and reboot. I'm stuck using windows until I can get this corrected.
I have read so many posts on here and tried so many different things that I don't even know where I stand now. I have no clue what is running, what is not, what drivers I am using....What a mess.  I might do a fresh install back to 8. but I am hoping I don't have to.

---

### Post by hockman5 on 2009-04-29
I installed the WUBI ubuntu and it works with my ati card. Why can't I get it to work with the upgrade from 8.10? What is different between the WUBI distro and the upgrade?

---

### Post by alphacrucis2 on 2009-04-29
> **hockman5 said:**
> I seem to have been getting closer to getting it to work. I actually can see the desktop and it looks like good quality but then the screen turns white and everything freezes. I have to do ctrl-alt-f1 to get to terminal and reboot. I'm stuck using windows until I can get this corrected.
I have read so many posts on here and tried so many different things that I don't even know where I stand now. I have no clue what is running, what is not, what drivers I am using....What a mess.  I might do a fresh install back to 8. but I am hoping I don't have to.

Have you tried: System Administration Hardware Drivers. If the fglrx driver is offered enable it. Then start up a terminal and type:

```
sudo aticonfig --initial -f
```

Reboot.

---

### Post by StuartN on 2009-04-29
> **hockman5 said:**
> I installed the WUBI ubuntu and it works with my ati card. Why can't I get it to work with the upgrade from 8.10? What is different between the WUBI distro and the upgrade?

Can you try the instructions at [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver) and report back? These steps clear out previous fglrx settings that interfere with the open source driver, hence a new install or wubi work while upgrading does not.

---

### Post by emarkay on 2009-04-29
Let's get all the Jaunty 9.04 ATI HD 2 series card data on one post to get this solved:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by hockman5 on 2009-04-30
I did a fresh Jaunty install but will post my replies to the referenced thread even though it is for upgrading to Jaunty from 8.

---

### Post by cdeobald on 2009-05-01
I had my ATI hd2400 Pro working under Intrepid with a dual-monitor configuration.  When I upgraded to Jaunty it continued to work fine.  *I am using the proprietary ATI driver*.  The only thing that doesn't work is tha the ATI Catalyst Control Center doesn't save my dual monitor configuration.  On each re-boot, it returns to cloned displays, and I have to set it to an expanded desktop.

---

