---
title: "hp fingerprint device"
date: 2012-08-15
forum: Hardware
---

### Post by bhoopal on 2012-08-15
```
yogesh@yogesh-PC:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 003: ID 138a:0005 Validity Sensors, Inc. VFS301 Fingerprint Reader
Bus 002 Device 004: ID 5986:0198 Acer, Inc 

```

hi guys, i have already installed fingerprint gui, but as i was guessing, it did not recognize the fingerprint device. my laptop is an hp pavilion dv6 3075ei, core i5, 4gb ram, radeon hd 5650..with ubuntu 12.04 64bit.
I did browse for a solution, but in vain. can anyone help me fix this please.

---

### Post by Whoopie on 2012-08-15
You have to compile the vfs301 driver. It can be found at [https://github.com/andree182/vfs301/](https://github.com/andree182/vfs301/), but it's still experimental.

---

### Post by bhoopal on 2012-08-15
thanks for replying. could you guide me with the installation please?

---

### Post by bhoopal on 2012-08-16
the install seems complicated, can anyone help me out with it please! on my own i'll mess things up

---

### Post by barrieluv on 2012-11-05
Did you ever get it going?
This is the reply to lsusb from my DV6 (we have the same reader):

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 007 Device 002: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 006 Device 002: ID 138a:0005 Validity Sensors, Inc. VFS301 Fingerprint Reader

And the reply to uname -a (so you can see which kernel is running):

Linux mintyhp 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 athlon i386 GNU/Linux


So, and I'm running Linux Mint 13, here's how I got mine to work.

Go to the Fingerprintgui page: [https://launchpad.net/~fingerprint/+archive/fingerprint-gui]("https://launchpad.net/~fingerprint/+archive/fingerprint-gui")

You'll see that your device is supported.

Add the ppa by opening a terminal and entering:
sudo add-apt-repository ppa:fingerprint/fingerprint-gui

and then:
sudo apt-get update

Then open Synaptic or whatever software manager you're using and install fingerprint-gui.  Or do it via the terminal.  Whatever.
Synaptic took care of all the dependencies and the Fingerprint Gui appeared in my System preferences.
Open it and then go through the tabs in the order in which they appear.
On the password tab, I inserted a spare SD card and then set my password.

And that was it.

If you have already installed it and need to change stuff, read the webpage for what to get rid of.

---

