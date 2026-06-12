---
title: "ttyS0 permission"
date: 2008-05-04
forum: Hardware
---

### Post by jay_565 on 2008-05-04
I needed to use ttyS0 for my serial printer.  I wonder why for 7.10  the permissions (ex. chmod a+x /dev/ttyS0) I gave ttyS0 is not restored upon reboot, it returns back to the orignal permissions.

---

### Post by freymann on 2008-05-26
> **jay_565 said:**
> I needed to use ttyS0 for my serial printer.  I wonder why for 7.10  the permissions (ex. chmod a+x /dev/ttyS0) I gave ttyS0 is not restored upon reboot, it returns back to the orignal permissions.

Same thing happens to me with 8.04. Every time I reboot I have to:

sudo chmod o+rwx /dev/ttyS0

in order for some of my X10 stuff to work. I would like to automate that step as well!

---

### Post by sisco311 on 2008-05-26
In order to get read/write permission on /dev/ttyS0 add your user to the dialout group.
```
sudo addgroup $USERNAME dialout
```You can set the permissions of /dev/ttyS0 by editing the /etc/udev/rules.d/40-permissions.rules file:
```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```Add this line:
> KERNEL=="ttyS[0-9]",            GROUP="dialout", MODE="0777"
restart udev:
```
sudo /etc/init.d/udev restart
```done,

---

### Post by freymann on 2008-05-26
> **sisco311 said:**
> In order to get read/write permission on /dev/ttyS0 add your user to the dialout group.
```
sudo addgroup $USERNAME dialout
```You can set the permissions of /dev/ttyS0 by editing the /etc/udev/rules.d/40-permissions.rules file:
```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```Add this line:
restart udev:
```
sudo /etc/init.d/udev restart
```done,

Beauty. Exactly what I needed. Thanks!

---

### Post by jessejazza on 2012-08-28
> **sisco311 said:**
> In order to get read/write permission on /dev/ttyS0 add your user to the dialout group.
```
sudo addgroup $USERNAME dialout
```You can set the permissions of /dev/ttyS0 by editing the /etc/udev/rules.d/40-permissions.rules file:
```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```Add this line:
restart udev:
```
sudo /etc/init.d/udev restart
```done,

I really appreciate you posting this. I've used a serial modem for faxing with 8.04 and 10.04, when i installed 12.04 i had a problem "access denied".

Until i read your post kindly passed to me from a xubuntu list member i was lost. I tried what's below but never thought about permissions.

<snip>
Steps so far: i need to check that the serial port is recognised.
mgetty installed from repos.
james@james-System-Product-Name:~/Desktop$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    0.285326] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.700570] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
james@james-System-Product-Name:~/Desktop$ setserial -g /dev/ttyS[01]
/dev/ttyS0: Permission denied
/dev/ttyS1: Permission denied

I didn't find the last line on restart seemed to work for  me i got errors so just rebooted the computer. efax could send... what joy!

What i'd be interested to know is why did this 'permission' required come into being?

---

