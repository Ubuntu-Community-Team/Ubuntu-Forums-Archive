---
title: "Laptop fan seems to spin too much"
date: 2008-04-29
forum: Hardware
---

### Post by Nyr on 2008-04-29
Hello,

I have a small problem (or so I think) with my laptop fan. I apologize in advance is there is already such a subject, but all I could find dealth mainly with fans being on all the time. This isn't the case here.

First and foremost, the laptop in question is a Toshiba U300 with a 1.6ghz Dual core cpu and 2 gig of ram (in case in matters). I installed Hardy Heron on it a few days ago and everything works amazingly well. I mean, not one bit of hardware has given me any sort of trouble... except for the fan. I'm especially interested in solving this problem because I'm this close to be able to fully be Windows free. 

The problem is this: The laptop fan seems to work by bursts. For example, I'm in Firefox, typing this message. The fan is idle, the laptop is quiet, all is well.  If I switch to another tab, the fan gives a short (about 3 to 5 seconds) burst of activity. It gets *really* annoying, and fast. It didn't do that under Windows XP, so I'm basically wondering... how do I tell the fan to chill? (bad pun!). I'm pretty sure I'm not doing anything that is so resource intensive that it makes the cpu work that hard. Case in point, when the fan spins, the graph of CPU activity in System Monitor almost always shows the CPU load (assuming that'd the right term) to be below 25%. 

So where can I go in Ubuntu to fix this? The laptop does that even when plugged into the wall (it rarely runs on battery power), so editing acpi-support and setting laptop mode to true probably wouldn't change anything (unless I'm wrong, that's only for when the laptop is battery powered).

Thank you all in advance,

Nyr

---

### Post by subzero316 on 2008-04-29
Chk These FAN control script  . Refer [<<---THIS LINK--->>]("http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Variable_speed_control_scripts")  It not specific to your laptop but i guess it will work.

---

### Post by Nyr on 2008-04-29
Thanks! Will try and see if that works. 

As a side note, it seems the problem occurs mostly with Firefox. Other apps don't seem to cause that.

In any case, thanks again.

---

