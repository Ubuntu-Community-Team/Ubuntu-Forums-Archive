---
title: "IrDA: trying to transfer photos from Nokia 6070 to notebook"
date: 2016-05-25
forum: Hardware
---

### Post by leozinho29_eu on 2016-05-25
Hello

I am trying to transfer photos from a Nokia 6070 using the infrared to my notebook Asus M2400N. However, I am having no success in making one identify the other. Initially, the IrDA made the notebook system freeze (it made me to reinstall the system, because it froze in the middle of the upgrade, I was doing nothing).
After a lot of search, I have found some guides about IrDA. Basically, I was able to make it turn on following this guide... [http://blogs.fsfe.org/stefan.a/2011/05/24/irda_infrared_data_transfer_on_ubuntu/](http://blogs.fsfe.org/stefan.a/2011/05/24/irda_infrared_data_transfer_on_ubuntu/)
...and making a script with that commands.

```
#!/bin/sh -e

/etc/init.d/irda-utils stop
/etc/init.d/irda-utils start
sleep 3
irattach irda0 -s
/etc/init.d/irda-utils stop
/etc/init.d/irda-utils start

exit 0


```

It asks for password four times, but once used, the infrared port starts to work. I can see with a digital camera and irdadump shows the packets. When I open Ircp-Tray, the irdadump messages change.

Irdadump with Ircp-Tray closed:
```
14:45:09.365011 xid:cmd d42a083f > ffffffff S=6 s=2 (14)
14:45:09.453128 xid:cmd d42a083f > ffffffff S=6 s=3 (14)
14:45:09.541128 xid:cmd d42a083f > ffffffff S=6 s=4 (14)
14:45:09.629125 xid:cmd d42a083f > ffffffff S=6 s=5 (14)
14:45:09.717132 xid:cmd d42a083f > ffffffff S=6 s=* administrador-M2Ne hint=0400 [ Computer ] (34)
14:45:12.197138 xid:cmd d42a083f > ffffffff S=6 s=0 (14)
14:45:12.285132 xid:cmd d42a083f > ffffffff S=6 s=1 (14)
14:45:12.373126 xid:cmd d42a083f > ffffffff S=6 s=2 (14)
14:45:12.461127 xid:cmd d42a083f > ffffffff S=6 s=3 (14)
14:45:12.549125 xid:cmd d42a083f > ffffffff S=6 s=4 (14)
14:45:12.637125 xid:cmd d42a083f > ffffffff S=6 s=5 (14)
14:45:12.725122 xid:cmd d42a083f > ffffffff S=6 s=* administrador-M2Ne hint=0400 [ Computer ] (34) 
```

Irdadump with Ircp-Tray opened:
```
14:46:06.341156 xid:cmd d42a083f > ffffffff S=6 s=0 (14)
14:46:06.429126 xid:cmd d42a083f > ffffffff S=6 s=1 (14)
14:46:06.517121 xid:cmd d42a083f > ffffffff S=6 s=2 (14)
14:46:06.605033 xid:cmd d42a083f > ffffffff S=6 s=3 (14)
14:46:06.693022 xid:cmd d42a083f > ffffffff S=6 s=4 (14)
14:46:06.781118 xid:cmd d42a083f > ffffffff S=6 s=5 (14)
14:46:06.869137 xid:cmd d42a083f > ffffffff S=6 s=* administrador-M2Ne hint=8420 [ Computer IrOBEX ] (35)
14:46:09.349035 xid:cmd d42a083f > ffffffff S=6 s=0 (14)
14:46:09.437124 xid:cmd d42a083f > ffffffff S=6 s=1 (14)
14:46:09.525016 xid:cmd d42a083f > ffffffff S=6 s=2 (14)
14:46:09.613017 xid:cmd d42a083f > ffffffff S=6 s=3 (14)
14:46:09.701127 xid:cmd d42a083f > ffffffff S=6 s=4 (14)
14:46:09.789135 xid:cmd d42a083f > ffffffff S=6 s=5 (14)
14:46:09.877125 xid:cmd d42a083f > ffffffff S=6 s=* administrador-M2Ne hint=8420 [ Computer IrOBEX ] (35) 
```

I was able to start the infrared port of the notebook. I can too start the infrared transference of photos using the Nokia 6070. I know the Nokia 6070 is working because I tested it with a Nokia 6585n. The notebook was unable to find both 6070 and 6585n. 

This guide [https://help.ubuntu.com/community/IrdaHowto](https://help.ubuntu.com/community/IrdaHowto) in the help was pretty problematic on my computer: while the guide I used told too to do the steps from 1 to 5 and I had no problems, the step 6 to 13 makes the computer to freeze (only keeping the power button pressed to turn it off), maybe because of the  differences of the versions. 

At the bottom of the page, there is "Testing operation". The dmesg option appears this: 

```
[   32.695816] nsc-ircc, Found chip at base=0x02e
[   32.695839] nsc-ircc, driver loaded (Dag Brattli)
[   32.698105] IrDA: Registered device irda0
[   32.698111] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
```

The only message lacking is the one about irlap_change_speed(). However, it is unable to detect any device. 

Here is the irda-utils file from /etc/default

```
# Set your startup settings for irattach, the IrDA-daemon, here.

# Set this to 'false' if you do not need to start irattach. Otherwise set it
# to 'true'.
ENABLE="false"

# Set this to 'false' if you do not want automatic discovery of irda devices.
# If 'true', it will automatically start irattach if devices are found.
AUTOMATIC="true"

# Set discovery mode which usually is a good idea for finding other devices.
# If set 'true' or 'false' irattach and sysctl are used to enable and disable
# discovery mode. By default discover mode is disabled.
DISCOVERY="true"

# Set IRDA device to access (e.g. /dev/ttyS1 or irda0).
# In case of irda0, the proper module for FIR-mode has to be set in
# /etc/modprobe.d/irda-utils.conf
DEVICE="irda0"

# Set dongle type, e.g. none, tekram, esi, actisys, actisys+, ep7211, girbil,
# litelink, airport, old_belkin, mcp2120, act200l, ma600). You do not need
# a dongle for FIR mode.
DONGLE="none"

# Set the serial device to quiet with setserial. This is only useful on some
# machines in FIR-mode, so most people should leave it blank. See 
# README.Debian for more information.
SETSERIAL="/dev/ttyS1"

# Some laptops (Toshiba Satellites and others with SMCS LPC47N227) require
# running smcinit to initialize the irda device prior to use.
# If you device is one of them, set this option to "yes"
USE_SMCINIT="no"

# Set the max baud rate for IrDA device
# Values: 2400, 3600, 9600, 14400, 19200, 28800, 38400, 57600, 115200
MAX_BAUD_RATE="9600"
```

/etc/modules and /etc/modprobe.d/irda-utils.conf are unchanged.

dmesg | grep tty results in:
```

user@administrador-M2Ne:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    1.445760] serial8250: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 921600) is a NS16550A
```

Thank you

---

