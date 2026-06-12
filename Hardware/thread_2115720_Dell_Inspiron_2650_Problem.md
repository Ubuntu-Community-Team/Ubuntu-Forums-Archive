---
title: "Dell Inspiron 2650 Problem"
date: 2013-02-13
forum: Hardware
---

### Post by l3lu3753 on 2013-02-13
Hello all,
      I'm fairly new to Linux but have a good basic understanding. This might be a simple fix but have come up fairly empty in my searching. 

Device is an Inspiron 2650 running Xubuntu 12.10. I know acpi doesn't work with this device and have disabled it with 'acpi=off' (I tried pci=noacpi but it failed to boot). It runs excellent otherwise until the session is around the 2 hour mark or extended idle periods. It will completely lock up and the Caps and Num Lock leds are blinking. Only fix is a hard reboot. Any ideas?

---

### Post by ahallubuntu on 2013-02-13
~

---

### Post by l3lu3753 on 2013-02-13
> **ahallubuntu said:**
> Perhaps it is going into suspend to save power?  Or do you have that disabled?  You can't suspend (sleep) with ACPI disabled.

Is the screen set to blank after a set period - or did you change/disable that too?

Try telling the computer to Suspend directly.  Does the same behavior happen?

What happens if you don't disable ACPI?  Did you have to do that to get it to boot/install at all?

Screen/System are set to never sleep/suspend/hybernate.  Telling the system to pm-suspend through command line does nothing. Telling the system to pm-hibernate brings the system to down to a blank screen with a blinking cursor and stalls.

I'm going to replicate it and grab some logs.

Acpi=off was mandatory for install and boot. Without it system stalls with a blinking cursor. And from my research this is for every Insp 2650, but I haven't seen anyone else with my problem. Maybe people just don't let it sit and idle for hours *shrug*.

---

