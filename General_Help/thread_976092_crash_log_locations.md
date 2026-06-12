---
title: "crash log locations"
date: 2008-11-09
forum: General Help
---

### Post by starcraft2fan on 2008-11-09
I was playing around with the v8 javascript shell when it crashed -- in Mac I could look up Crash Reporter and see the stack trace, but the Ubuntu equivalent of apport didn't log anything.

The only info I could find were segfault messages in /var/log/kern.log and I don't want to fire up gdb to get a similar stack trace manually everytime this occurs, I want to look at the stack traces later. Is there a location where they are stored in Ubuntu?

---

### Post by guatebus on 2009-09-17
Hope this helps, comes from [http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)


Linux Log files and usage

=> /var/log/messages : General log messages

=> /var/log/boot : System boot log

=> /var/log/debug : Debugging log messages

=> /var/log/auth.log : User login and authentication logs

=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file

=> /var/log/dmesg : Linux kernel ring buffer log

=> /var/log/dpkg.log : All binary package log includes package installation and other information

=> /var/log/faillog : User failed login log file

=> /var/log/kern.log : Kernel log file

=> /var/log/lpr.log : Printer log file

=> /var/log/mail.* : All mail server message log files

=> /var/log/mysql.* : MySQL server log file

=> /var/log/user.log : All userlevel logs

=> /var/log/xorg.0.log : X.org log file

=> /var/log/apache2/* : Apache web server log files directory

=> /var/log/lighttpd/* : Lighttpd web server log files directory

=> /var/log/fsck/* : fsck command log

=> /var/log/apport.log : Application crash report / log file

---

