---
title: "[SOLVED] Canon LBP2900 doesn't work after upgrading."
date: 2008-11-02
forum: Hardware
---

### Post by Kroops on 2008-11-02
I've upgraded to 8.10:
[[IMG]http://www.picamatic.com/show/2008/11/02/12/33/1292750_bigthumb.png[/IMG]](http://www.picamatic.com/view/1292750_&#1057;&#1085;&#1080;&#1084;&#1086;&#1082;-&#1057;&#1074;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;_&#1087;&#1088;&#1080;&#1085;&#1090;&#1077;&#1088;&#1072;_«LBP2900»_&#1085;&#1072;_localhost/)
"... unable to start filter "pstocapt" - No such file or derectory"
How can I solve this problem? Sorry for my English, I'm Russian.

---

### Post by Kroops on 2008-11-04
Can anybody help me?

---

### Post by fyazici on 2008-11-04
same problem

> **Kroops said:**
> Can anybody help me?

---

### Post by fyazici on 2008-11-04
Problem was solved. Commands;

sudo /usr/sbin/lpadmin -x LBP2900
sudo /usr/sbin/ccpdadmin -x LBP2900
sudo dpkg -P cndrvcups-common
sudo dpkg -P cndrvcups-capt
sudo dpkg -i cndrvcups-common_1.60-1_i386.deb
sudo dpkg -i cndrvcups-capt_1.60-1_i386.deb
sudo /etc/init.d/cups restart
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0

for ccpd autostart, add  this line "KERNEL=="lp*", RUN+="/etc/init.d/ccpd restart" to the line before last line in "/etc/udev/rules.d/85-hpjl10xx.rules"


> **fyazici said:**
> same problem

---

### Post by Kroops on 2008-11-04
Thanks a lot!

---

