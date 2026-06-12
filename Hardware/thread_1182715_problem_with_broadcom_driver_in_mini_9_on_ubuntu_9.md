---
title: "problem with broadcom driver in mini 9 on ubuntu 9.04"
date: 2009-06-09
forum: Hardware
---

### Post by akaguma on 2009-06-09
hello can anbody help with the following problem? every time i try to reload the fwcutter it fails and i cannot connect to wireless

	 	 timothy@timothy-laptop:~$ lspci -vnn | grep 14e4  
 03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)  
 	Subsystem: Broadcom Corporation Device [14e4:04b5]  
 timothy@timothy-laptop:~$ sudo apt-get install b43-fwcutter  
 [sudo] password for timothy:  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 b43-fwcutter is already the newest version.  
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.  
 1 not fully installed or removed.  
 After this operation, 0B of additional disk space will be used.  
 Setting up b43-fwcutter (1:011-5) ...  
 Error parsing proxy URL [http://localhost:4001](http://localhost:4001) : Bad port number.  
 dpkg: error processing b43-fwcutter (--configure):  
  subprocess post-installation script returned error exit status 1  
 Errors were encountered while processing:  
  b43-fwcutter  
 E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by snowpine on 2009-06-09
Ubuntu 9.04 Jaunty supports Mini 9 wireless out of the box. b43 does not support the bcm4312; and is not necessary in any case...

I am typing this from Ubuntu 9.04 live CD on my mini 9.

---

### Post by akaguma on 2009-06-09
please forgive my ignorance but what part of your answer will help me to get my wireless working?

---

### Post by snowpine on 2009-06-09
Your wireless should work out of the box with no additional steps. Maybe check that it is enabled in the bios?

---

### Post by snowpine on 2009-06-09
or possibly 'modprobe wl'? (wl is the correct module, provided by Broadcom for the bcm4312)

I do not know exactly what fwcutter does or how to recover from any damage it may have caused, sorry... :(

---

### Post by akaguma on 2009-06-09
yes many things should happen. it is enabled in BIOS and yet it does not work

---

### Post by akaguma on 2009-06-09
tried that, says permission denied

---

### Post by snowpine on 2009-06-09
How about System-Administration-Hardware Drivers, make sure to activate Broadcom STA Wireless Driver.

Did your wireless ever work? If so, what did you do right before it stopped working? ;) Does it work running from the Live USB? (And who told you to use b43-fwcutter?)

---

### Post by snowpine on 2009-06-09
> **akaguma said:**
> tried that, says permission denied

my bad, try 'sudo modprobe wl'

---

### Post by snowpine on 2009-06-09
Having any luck?

---

