---
title: "Brother MFC8890 wireless install instructions!!"
date: 2011-02-18
forum: Hardware
---

### Post by freesparks on 2011-02-18
Hello all,

    I am trying to install MFC 8890 on a Windows network.  I just need to know how to go about doing this step by step.  In the past I have installed HP printers via CUPS, and wired.  However, I am not familiar with the Brother manufacturer's install process.  So far, I have downloaded the cupswrapper along with the brother drivers from this site:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html),
however, I am not clear on what I need to do and how to launch the driver once I have done these steps in my Terminal:

```
:~$ sudo aa-complain cupsd
 Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
:~$ sudo mkdir /usr/share/cups/model
:~$ sudo mkdir /var/spool/lpd
r:~$  dpkg  -l  |  grep  Brother
```

Any help on this would be greatly appreciated.  I tried installing it via CUPS in my browser and specified the ppd file after I specified the IP address but have had no luck.

Best Regards,

freesparks

---

