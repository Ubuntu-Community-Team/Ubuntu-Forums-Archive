---
title: "Canon MP110 on x64 Natty - Not Showing In Printer App"
date: 2011-05-08
forum: Hardware
---

### Post by Crucias on 2011-05-08
Howdy,

I have a canon MP110 isn't behaving properly.

[http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/driverpackages#Preparation_of_LSB-compliant_distributions](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/driverpackages#Preparation_of_LSB-compliant_distributions)

[http://www.openprinting.org/printer/Canon/Canon-PIXMA_iP5000](http://www.openprinting.org/printer/Canon/Canon-PIXMA_iP5000)


Ok i deleted a lot of stuff there because i reinstalled cups and it detected the printer immediately. Now when i try print things i get errors. Here is the cups error log in /var/log/cups

```
E [10/May/2011:21:50:15 +1200] Filter directory "/usr/lib/cups/filter" for printer "Canon_MP110" has insecure permissions (040777)
E [10/May/2011:21:50:15 +1200] Filter directory "/usr/lib/cups/filter" for printer "PDF" has insecure permissions (040777)
E [10/May/2011:21:50:15 +1200] PID 7876 (/usr/lib/cups/filter/pstocanonbj) crashed on signal 11!
```

Now i have tried rather a few solutions to these, mostly involving commands like

```
rk@gobi:~$ sudo chmod 755 /usr/bin/foomatic-rip
 rk@gobi:~$ ll /usr/bin/foomatic-rip
 -rwxr-xr-x 1 root root 97976 2010-02-15 18:02 /usr/bin/foomatic-rip*
 rk@gobi:~$ sudo /etc/init.d/cups restart
  * Restarting Common Unix Printing System: cupsd
```
[Source]("http://ubuntuforums.org/showpost.php?p=9525054&postcount=11")

and 

```
sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend
```
[Source]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/436544/comments/8")

None of these work unfortunately

---

### Post by Crucias on 2011-05-10
Bumping - I fixed half the problem and now can ask for help in a more accurate fashion. Instead of making a new thread i am re-purposing the old one.

---

