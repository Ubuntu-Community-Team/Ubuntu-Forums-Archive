---
title: "ACPI issues with Dell 640m"
date: 2009-07-20
forum: Hardware
---

### Post by opto09 on 2009-07-20
Greetings Ubuntu Forum-ers!

I'm having a bit of trouble with my Dell 640m laptop running Jaunty. Basically Ubuntu refuses to run in either LiveCD or installed mode if ACPI is on. Just to clarify, I can run it fine if I include acpi=off at boot. With ACPI on, the computer restarts itself as soon as I reach the login page.

What I'd like to know is if this it is possibly a hardware problem or some software settings. 

I've found a link to an article online at [http://www.brighthub.com/computing/linux/articles/39504.aspx](http://www.brighthub.com/computing/linux/articles/39504.aspx), and followed some instructions there. So far as I can tell, the compute will only work if acpi=off and reboots itself for any other parameters (including acpi=ht). Any thoughts?

---

### Post by opto09 on 2009-07-20
I should also give a bit of background in case it helps. The laptop was initially configured to dual boot Windows and Ubuntu Gutsy. It was working until one bad crash in Windows. Since then I have not been able to get Windows working on it (similar symptoms, the laptop would restart upon login), and no amount of liveCD attempts would get Ubuntu working on it again. It was lying there dormant for awhile before I finally tried Jaunty, which magically brought it back to life as long as I boot with acpi=off.

There is one other strange fact. It seems that if I use the Battery Charge Monitor (panel applet), it detects the state of the laptop wrong. For example, when plugged in, the battery monitor tells me that there is 0% charge and 0:00 mins remaining, but when unplugged from mains, the monitor tells me it is on AC power. So I can't tell if this is a hardware or software issue.

---

