---
title: "ThinkPad Fan Control Problem"
date: 2014-03-29
forum: Hardware
---

### Post by Mn1945786 on 2014-03-29
I have Lenovo ThinkPad W500 and Ubuntu 12.10 installed. Its fan was not running at full speed, so I installed ThinkPad Fan Control software (tpfc0.5).  I launch it by executing tpfc_start.sh in terminal and entering my password. 
Here's a screenshot of the program:
[https://www.mediafire.com/?76yc1qnmkcn30vh](https://www.mediafire.com/?76yc1qnmkcn30vh)

When I try to set the fan speed by either Automatic Control or Manual Control, the fan goes to full speed for about 5 seconds, and then it goes back to slow speed. Is there something that I'm missing? Please help me so that the fan remains at full speed all the time until I set it down to a low speed.
Thanks.

---

### Post by tgalati4 on 2014-03-29
I have tpfan running on a T43p and it may behave differently on your machine.  Check BIOS for any fan settings and change them so they don't interfere with tpfan.  The full speed for a few seconds is usually a boot indicator to tell you that your fans are working during boot.  So perhaps the ACPI hardware gets reset or there is a conflict with the settings that you are using.

Install *acpitool* and run it to see what the fans are doing.

---

