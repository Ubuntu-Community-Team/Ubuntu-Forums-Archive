---
title: "problem with ipw3945 with gusty on hp dv6500"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by yakovyarmo on 2007-10-31
on feisty everything worked like a charm. but since i upgraded to gusty i get a lot of wifi problems.
sometimes i cant find my network. sometimes it disconnect from the network and cant find it again.
any suggestions?

---

### Post by ubukool on 2007-10-31
Hi,

I've had problems with this too, especially when the network doesn't restart after a suspend.  I did some searching around on the forum and found an answer that might work.  When you lose your wifi try this command in terminal:

sudo modprobe ipw3945

then if you left click on the network manager applet, hopefully you will see a list of wireless networks you can connect to.

Like you, everything worked great on Feisty, but I've had problems since upgrading to Gutsy. Hopefully time will fix things, I've noticed a few error reports on this subject so let's hope it gets sorted out soon.

---

### Post by simbloke on 2007-10-31
I solved this problem on my HP 6510b (same wireless module) after a bit of searching around the web.

I created a file called[FONT="Courier New"]** /etc/pm/sleep.d/15-ipw3945**[/FONT]

The contents are:
```
#!/bin/bash

case $1 in
        suspend)
                /sbin/ipw3945d-$(uname -r) --kill ;
                modprobe -r ipw3945
                ;;
        resume)
                modprobe ipw3945
                ;;
esac
```

The kill line in there is just to make sure!

---

### Post by Golem XIV on 2008-01-01
This is for a Dell Inspiron and not an HP, but it may help:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues)

Good luck!

---

