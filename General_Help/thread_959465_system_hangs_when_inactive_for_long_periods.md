---
title: "system hangs when inactive for long periods"
date: 2008-10-26
forum: General Help
---

### Post by spiperman on 2008-10-26
Hi all - I have a problem that appears to be a power management conflict of some type.  If I leave the system on, but inactive for a while (unknown how long this takes) the system will hang and require a reset / reboot.  

How this goes...
After routine use for several hours I either go to bed or to my "day job."
Upon return, the screen saver (it doesn't seem to matter which one) is shown frozen on the screen and the system is totally locked.
The keyboard (PS2 connection) and mouse (USB connection) appear inoperative (none of the leds on the keyboard respond) and the led in the (optical) mouse is off. 
Checking from my windows machine, both apache and samba are unresponsive.
Press the reset button / reboot and get back to work. 

While generally annoying -it just means that I never leave anything open on the desktop and I back-up my work to a usb drive real often.  Neither of which are bad practices.

I am running a currently patched Ubuntu 7.10.

The machine specs are as follows - 
Via MBd
AMD 2400+ processor
1GB DDR RAM
160GB Drive
CD/DVD RW (off brand)

To solve a shutdown problem -the acpi=force parameter has been added to the boot.  Other than that - nothing special has been done.

Using "Power Management" I have set the computer and monitor to "never" sleep. I still suspect the problem is related to power management settings - possibly in the BIOS?

Any suggestions on how to fix this are welcome.

Thanks.

---

### Post by ragtag on 2008-10-26
The logs ( /var/log/messages ) might give you a clue as to what is happening.

Have you tried disabling the screensaver too?

---

### Post by spiperman on 2008-10-26
ragtag - thanks for the suggestion. 

In looking at the messages file the only entry in prior to the hang point is the --MARK-- entry (every 30 minutes).

e.g. "Oct 26 15:26:35 ubuntu-svr-1 -- MARK --"

The amount of time it takes for the system to hang is hard to tell because the MARK line is inserted regardless of whether I'm working or not.

Now to be honest, unless a line in the messages file said warning or failure or something equally dire, I wouldn't know if any of the other entries were abnormal or not.

I have disabled the screen saver previously and what happens is the monitor goes into power saver mode (which I can't turn off) and because there is no change in the input level it just goes right back to power saver even if I toggle the power switch.

---

