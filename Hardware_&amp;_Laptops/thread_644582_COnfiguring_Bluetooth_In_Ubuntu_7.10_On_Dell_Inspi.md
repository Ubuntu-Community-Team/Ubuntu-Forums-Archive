---
title: "COnfiguring Bluetooth In Ubuntu 7.10 On Dell Inspiron 1420N"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by dnvikram on 2007-12-19
Hi Folks!

I have Dell Inspiron 1420 notebook with Ubuntu 7.10 installed on it.I have Gnome and KDE desktop(s) installed on this machine.I would like to know ,

1)How to enable or configure bluetooth on this machine from Ubuntu 7.10,such that any cellphone with bluetooth feature can talk to the ubuntu machine?
2)How do I first check if the bluetooth module on this machine has been detected by Gutsy?
3)Are there any packages needed to be installed to get the bluetooth up & running?

This is the only thing currently not setup on my gutsy laptop.Would really be grateful if someone could help me out with this.

Thanks a lot.

---

### Post by linuxwizard on 2007-12-19
look over this

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by dnvikram on 2007-12-19
Those steps mentioned in the link you arent working on my machine.Installed every concievable blutooth package for gnome and still couldnt get this up and running.The lsusb and dmesg|grep -i bluetooth commands show that the bluetooth module has been detected and initialized.But,the hcitool doesnt show any device or can detect any device.I guess there is a workaround or a fix for this kind of problem.When I run /etc/init.d/bluetooth start (or) restart,it shows it has restarted or started the bluetooth services successfully.But,still not able to detect my bluetooth enabled phone in its vicinity.

Kindly suggest.

Thanks.

---

### Post by Lord Magnus on 2008-02-07
Why there is no information about this problem?
I have a Dell Latitude D620, with exactly the same problem.

The System simply does not recognize my bluetooth card, by it works perfectly fine in Windows.

About the steps in this link ([https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)), they are not applicable for 7.10, and it says that the 7.10 should detect the card with no problem. But if it doesn't? I have found a lot of people with the same problem, with no solution.

Any ideas?

---

### Post by Lord Magnus on 2008-02-07
I can't believe I'll have to install Windows to make my bluetooth work again...
Nobody have figure it out?

---

### Post by fdofdo on 2008-02-11
I have a Dell Latitude D410 in the same situation. Of course, I delete Win XP...so I can't do what has been suggested. Is there any chance of using something like NDISwrapper to install the drivers?

---

