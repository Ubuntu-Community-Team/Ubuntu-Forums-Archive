---
title: "Connecting Asus External Slim Optical Drive to Asus Laptop"
date: 2013-10-20
forum: Hardware
---

### Post by minnaaralex on 2013-10-20
I have an Asus zenbook running on Ubuntu 13.04 and I am trying to connect an Asus External Slim Optical Drive.  I have connected it via USB and inserted a disc but nothing is happening.  Can anyone help me out with this?

Thanks,

---

### Post by xiccarph on 2013-10-20
Hi,
Could be alot of things.

With the Asus Optical Drive unpluged,
Open a terminal (maximize it so you have a large output area) and type: 
[B][FONT=courier new]tail -f /var/log/syslog

[/FONT][/B]Then plug in your Asus drive.
[FONT=courier new][/FONT]The command will display the output of the system log. As a USB device you should see some output very soon after you plug in the drive that tells you whether the drive is being recognized, and where the device is located under /dev.
Post that specific output here and I will try to help.

---

