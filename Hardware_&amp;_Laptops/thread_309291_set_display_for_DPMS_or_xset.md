---
title: "set display for DPMS or xset"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by shoofy on 2006-11-29
I use Edgy with Beryl. I have the fairly popular problem where my monitor doesn't turn off when it's supposed to (i.e. when I close the lid or after X number of minutes), but I think I'm on my way to a solution. I need some help though.

First of all, it should be known that I am using an ATI X1400 Radeon Mobility card in a Dell E1505 laptop. It should also be known that DPMS (the power management system) works normally under plain Gnome.

In Beryl, when I run ```
~$ xset -q
```I get (the relevant part): ```
DPMS (Energy Star):
  Display is not capable of DPMS
``` and when I run ```
~$ xset dpms force off
``` I get ```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  146 (DPMS)
  Minor opcode of failed request:  6 (DPMSForceLevel)
  Serial number of failed request:  10
  Current serial number in output stream:  12
```

Now I figured out by picking things up in other threads in this forum, that if I run ```
~$ DISPLAY=:0 xset -q
``` I get (again just the relevant part) ```
DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 2400
  DPMS is Enabled
  Monitor is On
``` and when I run ```
~$ DISPLAY=:0 xset dpms force off
``` the onitor actually turns off! If I change DISPLAY=:0 to DISPLAY=:1 in these last 2 commands, I get the same results as if I didn't include the DISPLAY part at all, like in the first cases.

This leads me to believe that I need to find some way to tell xset or DPMS that it needs to always use DISPLAY=:0 and my monitor will start turning off again. I tested in a normal Gnome session to see if changing this would make it stop working and it worked fine with the DISPLAY=:0 commands. So basically I'm asking if anyone can tell me how to change this setting for xset or DPMS (whichever is needed)?

UPDATE: I tried "~$ export DISPLAY=:0" but it messed up some parts of beryl/emerald. It did make the "xset dpms force off" command work, but the screen did not turn off when I closed the lid.

---

