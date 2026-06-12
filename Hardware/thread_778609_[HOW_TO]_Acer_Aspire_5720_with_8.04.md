---
title: "[HOW TO] Acer Aspire 5720 with 8.04"
date: 2008-05-02
forum: Hardware
---

### Post by LeDieu on 2008-05-02
Hello,

For the people who have a Acer Aspire 5720 and cant get the new (k)ubuntu working here a small how to with the problems i got during the installation.
I know it works with kubuntu. For the other distributions I'm not sure.

Problem 1: A black/blank screen after the loading screen of (k)ubuntu and before the login screen.

> Solutions: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way)
Problem 2: The shutdown/logout/hibernate/suspend/restart option's won't work.

> Solutions: Execute the command: 
sudo /usr/sbin/update-rc.d -f atieventsd remove 

I hope i could help.
If not.... post your question and we can take a look at your problem ;).

Greetz,
LeDieu

---

