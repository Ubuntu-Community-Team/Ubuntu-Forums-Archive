---
title: "Getting a UPS working in Ubuntu (Kubuntu) 9.10"
date: 2010-04-03
forum: Hardware
---

### Post by steve* on 2010-04-03
For anyone struggling to get their UPS working if not automatically detected by the gnome power manager. These are the steps I used after some researching various forums & software documentation.  

OS: Ubuntu 9.10

1. INSTALL NUT
------------------
From Synaptic package manager or type in terminal..

~$ sudo apt-get install nut

2. SETTING UP THE NUT DRIVER
-------------------------------------

Create / modify the following file in /etc/nut:

**ups.conf**

and add: 

(My two UPS devices look like this)
(Powerware 3105 USB)       

[powerware]                            
  driver = bcmxcp_usb       
  port = auto                 

 (Powerware 5119 Serial)

 [powerware] 
  driver = upscode2
  port = /dev/ttyS0


(NOTE: refer to URL below for availible UPS drivers. Set UPS name and port for your device)

[http://www.networkupstools.org/compat/stable.html](http://www.networkupstools.org/compat/stable.html)

I couldn't get my serial UPS to connect with the genericups driver specified in the list
so I attempted connection with the alternative ones until successful. 

***************************************
If UPS is serial connected then set permissions:

Create the following file in /etc/udev/

rules.d/99_nut-serialups.rules

and add:

KERNEL=="ttyS0", GROUP="nut"

(NOTE: ttyS0 = port1, ttyS0 = port2, etc.)

update udev, type in terminal..
~$ sudo udevadm control --reload-rules
~$ sudo udevadm trigger
**************************************

See if driver will connect UPS:

sudo upsdrvctl start

Should return something like:

Network UPS Tools - UPS driver controller 2.4.1
Network UPS Tools - BCMXCP UPS driver 0.21 (2.4.1)
USB communication subdriver 0.17

3. CONFIGURING NUT
-------------------------

Create / modify the following files in /etc/nut:

**upsd.conf**

and add:

LISTEN 127.0.0.1 3493

**upsd.users**

and add:

[admin]
  password = MY_PASSWORD
  actions = SET
  instcmds = ALL

[monuser]
  password = MY_PASSWORD
  upsmon master

(NOTE: choose passwords)

**upsmon.conf**

and add:

MONITOR powerware@localhost 1 monuser MY_PASSWORD master
POWERDOWNFLAG /etc/killpower
SHUTDOWNCMD "/sbin/shutdown -h now"

(NOTE: UPS name, user & password should reflect previous selections)

**nut.conf**

and change:

MODE=

to:

MODE=standalone

4. GETTING NUT TO START AT BOOT
------------------------------------------

Create the following file in /etc/default/

**nut**

and add:

START_UPSD=yes
START_UPSMON=yes

5. STARTING UP NUT
------------------------

Type command in terminal..

~$ sudo /etc/init.d/nut start

Assuming NUT starts with no errors,
type the following command to display
UPS parmeters..

~$ upsc powerware

(NOTE: change UPS name to your device)

This is what my two UPS devices returned:

(3105)

driver.name: bcmxcp_usb
driver.parameter.pollinterval: 2
driver.parameter.port: auto
driver.version: 2.4.1
driver.version.internal: 0.21
input.frequency.high: 55
input.frequency.low: 45
input.frequency.nominal: 50
input.voltage.nominal: 240
output.phases: 1
output.voltage.nominal: 240
ups.beeper.status: disabled
ups.firmware: Cont:00.80 Inve:00.60
ups.model: POWERWARE UPS    350VA
ups.power.nominal: 350
ups.serial: &#65533;&#65533;
ups.status: OL

(5119)

battery.capacity.nominal: 17.00
battery.charge: 73.2
battery.runtime: 1620
battery.voltage: 26.00
battery.voltage.maximum: 28.20
battery.voltage.minimum: 20.00
battery.voltage.nominal: 24.00
driver.name: upscode2
driver.parameter.pollinterval: 2
driver.parameter.port: /dev/ttyS0
driver.version: 2.4.1
driver.version.internal: 0.87
input.phases: 1
input.voltage: 232.40
input.voltage.maximum: 276.00
input.voltage.minimum: 162.00
input.voltage.nominal: 230.00
output.current: 1.24
output.current.maximum: 4.90
output.current.nominal: 4.40
output.frequency: 50.00
output.frequency.maximum: 53.00
output.frequency.minimum: 47.00
output.phases: 1
output.power: 0.29
output.realpower: 190.00
output.realpower.nominal: 670.00
output.voltage: 232.40
output.voltage.maximum: 244.00
output.voltage.minimum: 207.00
output.voltage.nominal: 230.00
ups.delay.reboot: 000
ups.delay.shutdown: 000
ups.load: 28.2
ups.mfr: unknown
ups.model: UPS 1000 VA FW -0026
ups.power.nominal: 1000.00
ups.serial: LQ164A689           
ups.status: OL

If all went well then proceed to some post actions..

6. SECURE NUT FOLDER TO PROTECT PASSWORDS
----------------------------------------------------------
To set root privileges,
type commands in terminal..

~$ sudo chown root:nut /etc/nut/*
~$ sudo chmod 640 /etc/nut/*

7. INSTALLING AN IDEAL UPS MONITORING GUI
-------------------------------------------------------

A KDE monitoring app. exists for graphical display of
a network UPS device that can be installed in Ubuntu.

From Synaptic package manager or type in terminal..

~$ sudo apt-get install knutclient

This app is easy to configure and will even display your UPS
I/O status with analog meters (provided the UPS has such features to display).

Just create a new UPS entry and set the address, port and name as configured in NUT.
(e.g. - UPS name: powerware
        UPS address: 127.0.0.1
        Port: 3493)

Add a knutclient launcher to the autostart folder (Home/.config.autostart) to
have it start on login.

Good Luck !

---

