---
title: "frostwire isn't working"
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by josh_g on 2006-07-30
well I believe I installed frostwire correctly but I could be wrong. It shows up in my Internet applications tab but when I click on it it doesn't open anything, it just sits there and does nothing.

---

### Post by croak77 on 2006-07-30
Open a terminal and run 'frostwire' from there. Post any error messages.

---

### Post by josh_g on 2006-07-30
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by croak77 on 2006-07-30
Do you have Java installed?

  sudo apt-get install sun-java5-bin

---

### Post by josh_g on 2006-07-30
Reading package lists... Done
Building dependency tree... Done
sun-java5-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.



?

---

### Post by cstudent on 2006-07-30
Enter from a terminal:

```

sudo update-alternatives --config java

```

Follow the instructions on changing to sun java.

---

### Post by adamkane on 2006-07-30
EasyLinux:
[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

JRE:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

Frostwire:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_P2P_Gnutella_Client_.28FrostWire.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_P2P_Gnutella_Client_.28FrostWire.29)

---

