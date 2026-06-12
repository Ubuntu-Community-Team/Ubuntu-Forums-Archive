---
title: "software installation problem using terminal"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by keedaiit on 2009-03-26
when i am using sudo apt-get install command i am alwasy getting the following error  message 

Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 

what should i do for this?:confused:

---

### Post by x33a on 2009-03-26
it means that another process is using dpkg at the moment. do you have synaptic open when you are trying the install via the command line?

---

### Post by kpatz on 2009-03-26
Is Update Manager or Synaptic running at the same time?  Or another instance of apt-get or aptitude?

---

### Post by keedaiit on 2009-03-26
no it is not

---

### Post by keedaiit on 2009-03-26
no its not they are not open

---

### Post by x33a on 2009-03-26
post the output of 
```
ps aux | grep apt*
```

---

### Post by keedaiit on 2009-03-27
root       207  0.0  0.0      0     0 ?        S<   Mar25   0:10 [kswapd0]
avahi     5557  0.1  0.1   3264  1716 ?        Ss   Mar25   4:31 avahi-daemon: running [pratik-laptop.local]
root      5776  0.0  0.0   6820  1116 ?        S    Mar25   0:00 /usr/bin/python /usr/share/ntlmaps/main.py -c /etc/ntlmaps/server.cfg
root      6205  0.0  0.0  20716   992 ?        Ss   Mar25   0:01 /usr/sbin/apache2 -k start
www-data  6283  0.0  0.0  20716  1228 ?        S    Mar25   0:00 /usr/sbin/apache2 -k start
www-data  6284  0.0  0.0  20716  1208 ?        S    Mar25   0:00 /usr/sbin/apache2 -k start
www-data  6285  0.0  0.0  20716  1292 ?        S    Mar25   0:00 /usr/sbin/apache2 -k start
www-data  6286  0.0  0.0  20716  1340 ?        S    Mar25   0:00 /usr/sbin/apache2 -k start
www-data  6287  0.0  0.0  20716  1212 ?        S    Mar25   0:00 /usr/sbin/apache2 -k start
pratik    6401  0.0  0.4  16668  6652 ?        S    Mar25   0:01 bluetooth-applet --singleton
pratik    6419  0.0  0.3  15172  4660 ?        S    Mar25   0:00 tracker-applet
pratik    6428  0.0  0.3  24124  5524 ?        S    Mar25   0:06 python /usr/share/system-config-printer/applet.py
pratik    6432  0.0  0.7  25360 10728 ?        S    Mar25   0:38 nm-applet --sm-disable
pratik    6550  0.0  0.6  26100 10212 ?        S    Mar25   0:01 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=23
pratik    6603  0.0  0.5  24120  8360 ?        S    Mar25   0:02 /usr/lib/gnome-applets/battstat-applet-2 --oaf-activate-iid=OAFIID:GNOME_BattstatApplet_Factory --oaf-ior-fd=25
pratik    6607  0.0  0.6  26268  9728 ?        S    Mar25   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=30
www-data 12940  0.0  0.0  20716  1328 ?        S    Mar25   0:00 /usr/sbin/apache2 -k start
pratik   13501  0.0  0.0   3008   796 pts/0    S+   21:50   0:00 grep apt*

---

### Post by snova on 2009-03-27
If you're certain nothing else is running, then remove the lock file manually:

```
sudo rm /var/lib/dpkg/lock
```

---

