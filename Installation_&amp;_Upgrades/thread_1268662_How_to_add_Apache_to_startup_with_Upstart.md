---
title: "How to add Apache to startup with Upstart?"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by TDK800 on 2009-09-17
Previously I did the below to add Apache to startup, what is the procedure with Upstart that replaces init in Karmic?


---------
cp /etc/httpd/bin/apachectl /etc/init.d/

sudo chmod +x /etc/init.d/apachectl


# edit apachectl and add the 2 lines to the top of file leaving the # marks in front 

# otherwise "/sbin/chkconfig --add apachectl" command says "service apachectl does not support chkconfig".



nano -w /etc/init.d/apachectl 



#!/bin/sh

#

# chkconfig: - 85 15

# description: Apache is a Web server.

#

 

sudo /usr/sbin/update-rc.d apachectl defaults

---

