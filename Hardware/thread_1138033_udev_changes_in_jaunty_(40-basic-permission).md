---
title: "udev changes in jaunty (40-basic-permission)"
date: 2009-04-26
forum: Hardware
---

### Post by scheuri on 2009-04-26
Good day to all

I am using Ubuntu 9.04 (Jaunty) as 32bit on a Lenovo T400 and I received an USB stick from my bank to use it to make e-banking.

They offer information about what is needed to be changed in ubuntu 7.04, 7.10 and 8.04 and above. 
Without these changes a message appears telling me to change that when trying to start ebanking.

Now, the changes they suggest to make are the following:
Open file /etc/udev/rules.d/40-basic-permissions.rules and change the MODE for the usb-subsystem:

```

SUBSYSTEM==“usb“, <…> MODE=“0664“
change to
SUBSYSTEM==“usb“, <…> MODE=“0666“ 

```

That is not much of a problem. However, in Jaunty that file does NOT exist.
I created that file (using the information of ubuntu 8.04)  and rebooted. The message that changes are needed is still there, so I guess it did not work.

Does anyone have an idea why that file did not exist in the first place and where I need to make those changes instead to make ebanking work (or potentially work concerning udev)?

Thanks a lot!
cheers
scheuri

---

### Post by scheuri on 2009-04-27
Does that file really exist on every one elses installation?
Am I the only one that does not have that file or didnt know about the changes introduced to udev?

:)

---

### Post by JohnnySkidmark on 2009-04-27
I'm just now discovering that, as of Jaunty, the [FONT="Courier New"]udev[/FONT] rules have apparently moved from [FONT="Courier New"]/etc/udev/rules.d[/FONT] to [FONT="Courier New"]/lib/udev/rules.d[/FONT].  Even so, no, I don't have that file anywhere on my Ubuntu Server 9.04 system.

[FONT="Courier New"]/etc/udev/rules.d/40-basic-permissions.rules[/FONT] *does* exist on my Ubuntu Server 8.10 system:

```
# This file establishes permissions and ownership of devices according
# to Ubuntu policy.  See udev(7) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",                MODE="0664"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console",                      MODE="0600"
KERNEL=="ptmx",                         MODE="0666"
KERNEL=="tty",                          MODE="0666"
LABEL="vc_end"

# Miscellaneous devices
KERNEL=="null",                         MODE="0666"
KERNEL=="zero",                         MODE="0666"
KERNEL=="full",                         MODE="0666"
KERNEL=="random",                       MODE="0666"
KERNEL=="urandom",                      MODE="0666"
KERNEL=="inotify",                      MODE="0666"

```

---

### Post by scheuri on 2009-04-28
Hello JohnnySkidmark

Thanks a lot for your response and I am sorry for not replying earlier.

Thank you for those information. That reassures me that I am not that much mistaken that this files does not exist anymore.

Now the question is:
Is there another file where those usb-rules are mentioned (and need to be altered accordingly to make ebanking work) or do I need to make a new file with those information.
If latter is the case I wonder how to name the file and where to put it to make udev read and execute it and if the syntax changed.

EDIT:
Seems that usb udev rules are now in /lib/udev/rules.d/50-udev-default.rules
I can not test it right now, but I will this evening and post my findings.

Thanks again
scheuri

---

### Post by skcams on 2009-05-04
> **scheuri said:**
> Hello JohnnySkidmark
Now the question is:
Is there another file where those usb-rules are mentioned (and need to be altered accordingly to make ebanking work) or do I need to make a new file with those information.
If latter is the case I wonder how to name the file and where to put it to make udev read and execute it and if the syntax changed.

EDIT:
Seems that usb udev rules are now in /lib/udev/rules.d/50-udev-default.rules
I can not test it right now, but I will this evening and post my findings.

scheuri

Hi,

I modify this file and it works !
  sudo gedit /lib/udev/rules.d/50-udev-default.rules
 change MODE="0664" to  MODE="0666" on line with SUBSYSTEM=="usb"  (line 53 in my file)

This trouble is the same than with ubuntu 8.10 and I don't know why it is not the default mode for usb :-(
It is a bug or a bad driver configuration (libsane ?).
NB : I use brscan2 from brother.

---

### Post by curtlee2002 on 2009-09-12
A better solution would be to set permissions for only that device.  This is how I did that:

sudo nano /etc/udev/rules.d/99-permissions-avr.rules

```
#AVRISP mkII
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", SYSFS{idVendor}=="03eb", SYSFS{idProduct}=="2104", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="0666"

```

Good Luck to any future AVR programmers

---

