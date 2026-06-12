---
title: "Apc ups"
date: 2008-09-29
forum: General Help
---

### Post by maxers76 on 2008-09-29
I am trying to test the status of my APC UPS running on Hardy. I have configure the apcupsd.conf file. 
And started the daemon (/etc/init.d/apcupsd).
But when I run apcaccess I get the following error

FATAL ERROR in apcaccess.c at line 41
tcp_open: cannot connect to server localhost on port 3551.
ERR=Connection refused

I have tired changing the IP as suggested in other forums and a few of the other config changes but nothing has made a difference.

Any other suggestions?

---

### Post by bbunge on 2008-11-15
OK, so I was wrong in my original post. The correct thing to do is to edit /etc/default/apcupsd, find the line ISCONFIGURED=no and change no to yes. Additional information can be found here: [https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)


(There is a small error in the file /etc/init.d/apcupsd. Edit the file and look for the line CONFIG=/etc/default/apcupsd. Remove /default from that line and another place furthur down. This will enable the apcupsd to start and give you more specific messages if your config file is not right.)

---

