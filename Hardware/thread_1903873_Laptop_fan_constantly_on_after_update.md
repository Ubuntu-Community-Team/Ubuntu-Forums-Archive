---
title: "Laptop fan constantly on after update"
date: 2012-01-03
forum: Hardware
---

### Post by Joshua Swink on 2012-01-03
I updated my packages today, and after rebooting the laptop's fan is constantly running. Two questions:

1) Is it reasonable for the fan to be running constantly with this sensors output?
2) Which package is likely responsible for changing the fan's behavior?

Note 1: I don't think it's the kernel because I rebooted to the previous kernel version and the fan is still going.
Note 2: "top" shows the CPU is 98% idle.

Sensors output is:

acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +105.0°C)                  
temp2:       +34.0°C  (crit = +105.0°C)                  
temp3:       +29.2°C  (crit = +110.0°C)                  
temp4:       +85.0°C  (crit = +110.0°C)                  
temp5:       +30.0°C  (crit = +110.0°C)

The packages updated were:

Start-Date: 2012-01-03  10:24:09
Install: linux-headers-2.6.32-37-generic (2.6.32-37.81), linux-image-2.6.32-37-server (2.6.32-37.81), linux-headers-2.6.32-37 (2.6.32-37.81), linux-headers-2.6.32-37-server (2.6.32-37.81)
Upgrade: lib32bz2-1.0 (1.0.5-4ubuntu0.1, 1.0.5-4ubuntu0.2), libpurple0 (2.6.6-1ubuntu4.3, 2.6.6-1ubuntu4.4), libgweather1 (2.30.0-0ubuntu1, 2.30.0-0ubuntu1.1), apt-transport-https (0.7.25.3ubuntu9.8, 0.7.25.3ubuntu9.9), libgtk2.0-common (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), bzip2 (1.0.5-4ubuntu0.1, 1.0.5-4ubuntu0.2), update-notifier-common (0.99.3, 0.99.3ubuntu0.1), gcalctool (5.30.0.is.5.28.2-0ubuntu2, 5.30.0.is.5.28.2-0ubuntu3), libgail18 (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), libarchive1 (2.8.0-2, 2.8.0-2ubuntu0.1), libldap-2.4-2 (2.4.21-0ubuntu5.5, 2.4.21-0ubuntu5.6), unattended-upgrades (0.55ubuntu5, 0.55ubuntu6), libpurple-bin (2.6.6-1ubuntu4.3, 2.6.6-1ubuntu4.4), bind9-host (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), update-notifier (0.99.3, 0.99.3ubuntu0.1), linux-server (2.6.32.34.40, 2.6.32.37.43), dnsutils (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), libbz2-1.0 (1.0.5-4ubuntu0.1, 1.0.5-4ubuntu0.2), libdns64 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), icedtea-6-jre-cacao (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), apport (1.13.3-0ubuntu2, 1.13.3-0ubuntu2.1), sun-java6-bin (6.26-1lucid1, 6.26-2lucid1), openjdk-6-jre-lib (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), libfreetype6 (2.3.11-1ubuntu2.4, 2.3.11-1ubuntu2.5), libgweather-common (2.30.0-0ubuntu1, 2.30.0-0ubuntu1.1), firefox-branding (3.6.23+build1+nobinonly-0ubuntu0.10.04.1, 3.6.24+build2+nobinonly-0ubuntu0.10.04.1), libisccc60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), apt-utils (0.7.25.3ubuntu9.8, 0.7.25.3ubuntu9.9), linux-headers-server (2.6.32.34.40, 2.6.32.37.43), update-manager (0.134.11, 0.134.11.1), update-manager-core (0.134.11, 0.134.11.1), openjdk-6-jre-headless (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), sun-java6-jdk (6.26-1lucid1, 6.26-2lucid1), acpid (1.0.10-5ubuntu2.2, 1.0.10-5ubuntu2.5), app-install-data-partner (12.10.04.4, 12.10.04.5), sun-java6-jre (6.26-1lucid1, 6.26-2lucid1), apt (0.7.25.3ubuntu9.8, 0.7.25.3ubuntu9.9), firefox (3.6.23+build1+nobinonly-0ubuntu0.10.04.1, 3.6.24+build2+nobinonly-0ubuntu0.10.04.1), liblwres60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), libt1-5 (5.1.2-3build1, 5.1.2-3ubuntu0.10.04.1), python-problem-report (1.13.3-0ubuntu2, 1.13.3-0ubuntu2.1), xulrunner-1.9.2 (1.9.2.23+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.24+build2+nobinonly-0ubuntu0.10.04.1), tzdata-java (2011m-0ubuntu0.10.04, 2011n-0ubuntu0.10.04), linux-headers-generic (2.6.32.34.40, 2.6.32.37.43), libbind9-60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), sun-java6-plugin (6.26-1lucid1, 6.26-2lucid1), flashplugin-installer (11.0.1.152ubuntu0.10.04.1, 11.1.102.55ubuntu0.10.04.1), libgail-common (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), libservlet2.5-java (6.0.24-2ubuntu1.7, 6.0.24-2ubuntu1.9), ldap-utils (2.4.21-0ubuntu5.5, 2.4.21-0ubuntu5.6), libjasper1 (1.900.1-7, 1.900.1-7ubuntu0.10.04.1), libisccfg60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), gtk2-engines-pixbuf (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), tzdata (2011m-0ubuntu0.10.04, 2011n-0ubuntu0.10.04), python-apport (1.13.3-0ubuntu2, 1.13.3-0ubuntu2.1), python-papyon (0.4.8-0ubuntu2, 0.4.8-0ubuntu2.1), linux-image-server (2.6.32.34.40, 2.6.32.37.43), linux-libc-dev (2.6.32-34.77, 2.6.32-37.81), libgtk2.0-bin (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1), libisc60 (9.7.0.dfsg.P1-1ubuntu0.3, 9.7.0.dfsg.P1-1ubuntu0.4), openjdk-6-jdk (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), apport-gtk (1.13.3-0ubuntu2, 1.13.3-0ubuntu2.1), openjdk-6-jre (6b20-1.9.9-0ubuntu1~10.04.2, 6b20-1.9.10-0ubuntu1~10.04.2), firefox-gnome-support (3.6.23+build1+nobinonly-0ubuntu0.10.04.1, 3.6.24+build2+nobinonly-0ubuntu0.10.04.1), libgtk2.0-0 (2.20.1-0ubuntu2, 2.20.1-0ubuntu2.1)
End-Date: 2012-01-03  10:33:37

---

### Post by Joshua Swink on 2012-01-03
More information:

I downgraded acpid to the previous version (1.0.10-5ubuntu2), but this had no effect (fan still running constantly after rebooting).

I added "acpi=off" to the kernel command line. After rebooting, the fan was no longer running constantly.

---

