---
title: "LSI RAID Controller problem"
date: 2014-03-31
forum: Hardware
---

### Post by bladepif2 on 2014-03-31
Hello,

I have installed an LSI [COLOR=#000000][FONT=arial]SAS3041E-FSC RAID Controller to my HP Sever
RAID 1 Is up and running, Ubuntu server 12.04 was installed with no problem.

Now after the fist reboot, i can not login because of an repeatting error message in the terminal saying:

SAME WRITE faile. Manually Zerooing on sdb1

The error is printed on the screen all the time and I suppose also in some log, and will sooner or later, fill the logs.

My searchs in google give me the information that the system is trying to use a function that is not present in my RAID Controller et that I should dissable this functionality.
But how can I do this? Do I need to recompile some kernel to do this?

Is there a way to stop the printing of the error on the screen, so I can login and at least look for some errors in boot logs O perhaps try to install some other Kernel

Thanks for the help

CU Online

[/FONT][/COLOR]

---

### Post by bladepif2 on 2014-04-07
Hello,

I did not found any solution for this, so I retuned the controller and order some adapter that works fine now

CU Online

---

