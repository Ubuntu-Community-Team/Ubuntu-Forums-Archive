---
title: "Brother MFC 7440N Printer and Scanner working USB-Connection"
date: 2019-12-19
forum: Hardware
---

### Post by lenovo51 on 2019-12-19
sudo nano /lib/udev/rules.d/40

ACTION!="add", GOTO="libsane_rules_end"
ENV{DEVTYPE}=="usb_device", GOTO="libsane_create_usb_dev"
SUBSYSTEMS=="scsi", GOTO="libsane_scsi_rules_begin"
SUBSYSTEM=="usb_device", GOTO="libsane_usb_rules_begin"
SUBSYSTEM!="usb_device", GOTO="libsane_usb_rules_end"

# Kernel >= 2.6.22 jumps here
LABEL="libsane_create_usb_dev"

# For Linux >= 2.6.22 without CONFIG_USB_DEVICE_CLASS=y
# If the following rule does not exist on your system yet, uncomment it
# ENV{DEVTYPE}=="usb_device", MODE="0664", OWNER="root", GROUP="root"

# Kernel < 2.6.22 jumps here
LABEL="libsane_usb_rules_begin"

# Brother MFC-7440N
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01e6", MODE="664", GROUP="scanner"

ENV{libsane_matched}=="yes", RUN+="/bin/setfacl -m g:scanner:rw $env{DEVNAME}"

LABEL="libsane_usb_rules_end"

sudo ln -sfr /usr/lib64/libbrscandec* /usr/lib/x86_64-linux-gnu

sudo ln -sfr /usr/lib64/sane/libsane-brother* /usr/lib/x86_64-linux-gnu/sane

// Reboot computer and scanner via power switch and then you ar done.


UPDATE

For network scanner and printer add this instead.

ACTION!="add", GOTO="libsane_rules_end"
ENV{DEVTYPE}=="scsi_device", GOTO="libsane_create_scsi_dev"
SUBSYSTEMS=="scsi", GOTO="libsane_scsi_rules_begin"
SUBSYSTEM=="scsi_device", GOTO="libsane_scsi_rules_begin"
SUBSYSTEM!="scsi_device", GOTO="libsane_scsi_rules_end"

# Kernel >= 2.6.22 jumps here
LABEL="libsane_create_scsi_dev"

# For Linux >= 2.6.22 without CONFIG_USB_DEVICE_CLASS=y
# If the following rule does not exist on your system yet, uncomment it
# ENV{DEVTYPE}=="scsi_device", MODE="0664", OWNER="root", GROUP="root"

# Kernel < 2.6.22 jumps here
LABEL="libsane_scsi_rules_begin"

# Brother MFC-7440N
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="01e6", MODE="664", GROUP="scanner"

ENV{libsane_matched}=="yes", RUN+="/bin/setfacl -m g:scanner:rw $env{DEVNAME}"

LABEL="libsane_scsi_rules_end"

sudo ln -sfr /usr/lib64/libbrscandec* /usr/lib/x86_64-linux-gnu

sudo ln -sfr /usr/lib64/sane/libsane-brother* /usr/lib/x86_64-linux-gnu/sane


REBOOT PRINTER AND COMPUTER

---

### Post by lenovo51 on 2019-12-21
I have done this on my Ubuntu 19.10 x64. Supposed to work on other Ubuntu's as well.

[https://download.brother.com/welcome/dlf006893/linux-brprinter-installer-2.2.1-1.gz](https://download.brother.com/welcome/dlf006893/linux-brprinter-installer-2.2.1-1.gz)

Replace USB with SCSI if you have a network printer and scanner.

---

