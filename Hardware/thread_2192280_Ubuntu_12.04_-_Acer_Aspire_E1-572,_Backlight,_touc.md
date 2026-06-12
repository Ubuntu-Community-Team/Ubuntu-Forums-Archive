---
title: "Ubuntu 12.04 - Acer Aspire E1-572, Backlight, touchpad, Ethernet"
date: 2013-12-07
forum: Hardware
---

### Post by simhavcs on 2013-12-07
**1. Brightness control**
/etc/default/grub

then change

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
[B]

To default set the brightness control at boot
gksudo gedit /etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 85 > /sys/class/backlight/intel_backlight/brightness
exit 0

Replace 85 with your requirement of brightness level

2. Latest kernel upgrade to 3.10(Ref: [http://ubuntuhandbook.org/index.php/2013/10/linux-kernel-3-10-17-upgrade-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2013/10/linux-kernel-3-10-17-upgrade-ubuntu-linux-mint/))
mkdir mainline_3.10[/B]

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.17-saucy/linux-headers-3.10.17-031017-generic_3.10.17-031017.201310181435_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.17-saucy/linux-headers-3.10.17-031017-generic_3.10.17-031017.201310181435_amd64.deb)

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.17-saucy/linux-headers-3.10.17-031017_3.10.17-031017.201310181435_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.17-saucy/linux-headers-3.10.17-031017_3.10.17-031017.201310181435_all.deb)

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.17-saucy/linux-image-3.10.17-031017-generic_3.10.17-031017.201310181435_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.17-saucy/linux-image-3.10.17-031017-generic_3.10.17-031017.201310181435_amd64.deb)

sudo dpkg -i linux-headers-3.10.17-*.deb linux-image-3.10.17*.deb

Reboot
[B]
3. Ethernet Driver( Broadcom Corporation NetXtreme BCM57786 Gigabit Ethernet PCIe)[/B]
[https://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php](https://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php) (tg3)

Download driver from broadcom - linux-3.133d.zip
unzip
tar xvzf tg3-<version>.tar.gz
cd src
make
insmod tg3.ko
make install

check with ifconfig in the terminal


**4. Touchpad**
rmmod psmouse
modprobe psmouse proto=imps
vim /etc/modprobe.d/touchpad.conf
options psmouse proto=imps
[B]
5. Enable Hibernation mode[/B]

Shell prompt
sudo pm-hibernate

gksu gedit /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
[Enable Hibernate]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

Logout and Login

This will add the Hibernate option in system settings , hibernate, shutdown, suspend

Regards,
Vinay Simha BN

---

### Post by marc13 on 2014-06-16
> **simhavcs said:**
> [B]
3. Ethernet Driver( Broadcom Corporation NetXtreme BCM57786 Gigabit Ethernet PCIe)[/B]
[https://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php](https://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php) (tg3)

Download driver from broadcom - linux-3.133d.zip
unzip
tar xvzf tg3-<version>.tar.gz
cd src
make
insmod tg3.ko
make install

check with ifconfig in the terminal



Regards,
Vinay Simha BN

insmod tg3.ko fails. Either file is corrupt or its not compatible with the kernel update above.

---

### Post by jeremy31 on 2014-06-16
> **marc13 said:**
> There is no src folder after tar command. The folder simply does not exist and I cannot commit to a make. Any solution for this problem?

Is there a /src folder in the extracted files?

---

### Post by marc13 on 2014-06-16
I solved it. The /src folder was not there, the folder layot was different, but the approach is similar.

---

### Post by simhavcs on 2014-08-18
Upgrading 12.04 to 14.04 - Acer Aspire E1-572

1. Upgrage using the 14.04 .img (Default kernel 3.13 have some issues regarding brightness, uart, wifi, display drivers, so upgraged to 3.15)

2. Dowload the kernel - 3.15.0-031500-generic
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb)

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500_3.15.0-031500.201406131105_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-headers-3.15.0-031500_3.15.0-031500.201406131105_all.deb)

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-image-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/linux-image-3.15.0-031500-generic_3.15.0-031500.201406131105_amd64.deb)

sudo dpkg -i linux-headers-3.15.0-*.deb linux-image-3.15.0-*.deb

Reference :- [http://ubuntuhandbook.org/index.php/2014/06/install-upgrade-linux-kernel-3-15/](http://ubuntuhandbook.org/index.php/2014/06/install-upgrade-linux-kernel-3-15/)

3. For brightness control
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

Regards,
Vinay Simha BN

---

