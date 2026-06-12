---
title: "Laptop boot issues : I'm stumped"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by novusopiate on 2007-08-09
I have a Dell Latitude D600 (beast of a machine, I know) I have installed Ubuntu 7.04 and it has been running like a champ. This a a laptop I use for work (it's actually a comp pc but who's keeping track) an I have had no problems.

When I have the unit plugged into the AC power source, it boots great, and actually fairly quickly. But If try to boot off of battery, it will hang after the ubuntu splash screen and before the login screen. Now I know the battery is fine because after it boots, I can remove the ac power and run off of battery for a nice long time. Oddly enough, I can even do a restart when I run it like that, but if the unit completely shuts down, turns off, then turns back on, it has to have ac  power. 
I have tried the **noapic** thing and have had no luck. Does anyone have a suggestion?


Thanks,

Mike

---

### Post by tgalati4 on 2007-08-09
Fit Alt-F1 during the boot to see the boot commands as they are executed.  What is the last statement before the hang?

---

### Post by novusopiate on 2007-08-09
Configuring network interfaces.....

---

### Post by novusopiate on 2007-08-09
bump?

---

### Post by digitalbenji on 2007-08-09
Hi, I've had this problem also.  To resolve it, do this (it will save you 30 seconds at least off of boot):

edit the networking boot file

Code:
```

sudo kedit /etc/rcS.d/S40networking

(if you got no kedit use gedit or something)

now, put "##" in your code as follow:
(or simply overwrite your code with those lines respectively)
Code:

[HTML][HTML]case "$1" in
start)
	log_action_begin_msg "Configuring network interfaces"
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
##	if [ "$VERBOSE" != no ]; then
##	    if ifup -a; then
##		log_action_end_msg $?
##	    else
##		log_action_end_msg $?
##	    fi
##	else
##	    if ifup -a >/dev/null 2>&1; then
		log_action_end_msg $?
##	    else
##		log_action_end_msg $?
##	    fi
##	fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
	;;

stop)

```

---

### Post by novusopiate on 2007-08-09
I tried editing the network boot file to no avail... It still seems to hang on the configuring network interfaces...

---

### Post by fredj on 2007-08-10
What are the network interfaces i.e what network cards or devices are you using. Since it
hangs when configuring the network does it not timeout after 3 minutes and continue booting?
When it boots up with AC power is it connected to the network?

---

### Post by novusopiate on 2007-08-16
There are two network interfaces:
NetXtreme BCM5705M Gigabit Ethernet (eth0)
BCM4309 WLAN Interface (wlan0)

It does not matter if the netwrok is connected or not, it still hangs. And does not boot after three minutes. Is there a way to check the timeout length?

---

### Post by dcollamore on 2007-08-21
I'm running into the very same issue with an Inspiron 8600 and a broadcom 4306 wireless adapter...have you had any luck?

---

### Post by StevoG7 on 2007-12-08
I have reached the same problem running a Latitude D600 with broadcom ethernet adapter.  In windows when unplugging the power cord the internal network card is disabled.  Could this be a root of the problem for Ubuntu?

---

### Post by StevoG7 on 2007-12-09
Hey I've found a fix for this on my machine.  When turning on the computer enter the bios setup screen (f2).  Find the quick boot bios option and disable it, or if it is set to minimal boot set it to thorough.  It takes a few more seconds to load the bios and boot but nothing thats a problem.  Try it out, it worked for me, good luck.

---

