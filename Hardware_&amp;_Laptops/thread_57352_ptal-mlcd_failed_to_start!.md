---
title: "ptal-mlcd failed to start!"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by cogs28 on 2005-08-16
Hi
I am trying to setup hpoj to work with an HP OfficeJet T65 all in one printer. Printing works fine so I am trying to configure scanning with xsane. I ve got Horay 5.04.
I read the instructions from the hpoj site and also the wiki and threads at the ubuntu forum. I tried all of the suggested solutions but nothing work. 
When I run ptal-init setup the message I get is:
*** ptal-mlcd failed to start!  Check syslog file for error messages.
I have checked the error messages and nothing is there. I have deleted the printer and rebooted the pc. I think this must be some setup problem with Ubuntu that stops hpoj communicating with the parallel port.
There has to be a solution with this since I installed Fedora Core 4 before and hpoj and scanning with xsane worked fine with the same printer.
Does anyone have an idea how can I solve this problem because I really enjoy using Ubuntu and I dont want to change back to Fedora. Thanks in advance

---

### Post by cogs28 on 2005-08-16
Thanks,
I read the following thread:
[http://ubuntuforums.org/showthread.php?t=15142&highlight=ptal-mlcd](http://ubuntuforums.org/showthread.php?t=15142&highlight=ptal-mlcd)
This solved my problem by removing hpoj from synaptic and installing warty hpoj
Scanning now and xsane works ;-)

---

