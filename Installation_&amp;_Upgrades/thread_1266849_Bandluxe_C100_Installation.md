---
title: "Bandluxe C100 Installation"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by nine05lj on 2009-09-15
Pls can someone teach me a step by step how to install Bandluxe C100 in ubuntu 9... Thank you very much!!!

---

### Post by joelazz on 2010-01-14
Hi, I managed to set up a Bandluxe C100s Mobile Broadband card on ubuntu and kubuntu 9.10.

This is what I did:


1) attach the express card to your PC

2) check if it has been mounted as a USB storage device:
    - df -h
    - find the device path (e.g. /dev/sr0)
    - eject that device:
        - sudo eject /dev/sr0
    - note that you may have the device listed as /dev/sr1 instead of /dev/sr0

3) check that it is located in your devices:
    - ls -l /dev/tty*
    - you should have 2 entries as: /dev/ttyUSB0 and /dev/ttyUSB1
    - if this is not the case, you need to:
        - download the driver -> [http://www.bandrich.com/Download%5CAcer%20Aspire%20One.zip](http://www.bandrich.com/Download%5CAcer%20Aspire%20One.zip)
        - unzip
        - run (as root) bandrich.sh -> sudo ./bandrich.sh
        - let your computer reboot once this is done.
        - when it is up and running, disconnect and reconnect the usb connection
        - check that you now have the entries /dev/ttyUSB0 and /dev/ttyUSB1, or /dev/sr0 (or /dev/sr1)

4) install wvdial
    - sudo apt-get install wvdial

5) configure wvdial
    - edit /etc/wvdial.conf
    - change its contents to the following:
    [Dialer Defaults]
    Init 1 = ATZ
    Init 2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
    Modem Type = Analog Modem
    ISDN = 0
    Phone = *99#
    APN = <your apn> (goeverywhere)
    New PPPD = yes
    Modem = /dev/ttyUSB1
    Username = user
    Password = password
    Baud = 9600
    Stupid Mode = 1

6) Stop HAL
    - sudo /etc/init.d/hal stop

7) Connect
    - sudo wvdial

8) You should now be connect, use the ifconfig command to check that you have an entry ppp0 with an IP address assigned


Hope this works. It took a bit to get it done! :)

---

### Post by ddreamer on 2010-08-19
Hi, you can try this method: [http://swiss.ubuntuforums.org/showthread.php?t=886942&page=2](http://swiss.ubuntuforums.org/showthread.php?t=886942&page=2)
The method is successful for C120 in Ubuntu 10.04

---

