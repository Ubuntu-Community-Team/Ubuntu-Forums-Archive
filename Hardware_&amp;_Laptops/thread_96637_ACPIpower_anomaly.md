---
title: "ACPI/power anomaly"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by Raoul Duke on 2005-11-29
I wonder if anyone else has seen this, or knows what it means:

In the acpid log (/var/log/acpid) I get the following exactly every 17 seconds:

[> Tue Nov 29 09:47:01 2005] received event "battery BAT1 00000080 00000001"
[Tue Nov 29 09:47:01 2005] notifying client 6924[111:111]
[Tue Nov 29 09:47:01 2005] executing action "/etc/acpi/power.sh"
[Tue Nov 29 09:47:01 2005] BEGIN HANDLER MESSAGES
[Tue Nov 29 09:47:01 2005] END HANDLER MESSAGES
[Tue Nov 29 09:47:01 2005] action exited with status 0
[Tue Nov 29 09:47:01 2005] completed event "battery BAT1 00000080 00000001"


This is the event to signify when ac power is turned on/off. It occurs whether I am running on battery or ac power. Fortunately the power.sh script sees the correct state of things and nothing untoward happens...still, I'd like to know what it could mean and how to fix it.

---

### Post by jakev383 on 2005-11-29
[QUOTE=Raoul Duke]I wonder if anyone else has seen this, or knows what it means:

In the acpid log (/var/log/acpid) I get the following exactly every 17 seconds:

[

This is the event to signify when ac power is turned on/off. It occurs whether I am running on battery or ac power. Fortunately the power.sh script sees the correct state of things and nothing untoward happens...still, I'd like to know what it could mean and how to fix it.[/QUOTE]

Mine does the same thing. I think it's checking the state (battery or power) every 17 seconds to make sure nothing has changed.

---

### Post by Raoul Duke on 2005-11-29
Well not according to the script that gets executed ( /etc/acpi/power.sh ), it is only for ac power removal/connection. 

What laptop have you got? Mine is Toshiba Satellite 2450

---

### Post by jakev383 on 2005-11-29
[QUOTE=Raoul Duke]Well not according to the script that gets executed ( /etc/acpi/power.sh ), it is only for ac power removal/connection. 

What laptop have you got? Mine is Toshiba Satellite 2450[/QUOTE]

I'm on a Dell Inspiron 600m (the cheap one with the lower resolution). I looked at the script (truth told, glanced over it) and saw where it checks the state to see if it should go into "laptop mode" or not. I assumed this was it checking to see if it was plugged in or not (in case the daemon missed it) and those were the log entries you were seeing.  I'll take a better look at the script this evening or tomorrow morning and see if I can't make some more sense of it.

---

