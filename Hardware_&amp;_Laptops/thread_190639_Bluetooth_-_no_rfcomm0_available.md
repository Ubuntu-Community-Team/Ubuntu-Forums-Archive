---
title: "Bluetooth - no rfcomm0 available"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by fdimmling on 2006-06-06
Hi,

in Breezy I was able to make a GPRS connection from my Aver Travelmate 4652LMi to my Motorola RAZR V3i via Bluetooth using /dev/rfcomm0 and wvdial

In Dapper I can establish the bluetooth connection between laptop and mobile phone to exchange data, but I cannot access /dev/rfcomm0 - permission denied.
/dev/rfcomm0 is owned by root, group is dialout.  I'm member of dialout.

Any ideas?

Friedrich

---

### Post by nekr0z on 2006-06-13
Have the same phone, but never tried to make GPRS-connection. Now I'm quite busy making all the bells and whistles of my AMILO M7400 laptop work, so I have no time, but it would be nice to have this thing work, too.

If you ever finally solve the problems, could you please give a link to a HOWTO or write one so that other happy RAZR owners can follow?

---

### Post by fdimmling on 2006-06-17
It works now after deleting the connection on the RAZR and make it pairing again. To switch between file transfer and use of rfcomm0 I have to restart bluez-utils and eventually delete the connection in the bluetooth setup of the RAZR.

Friedrich

---

### Post by nekr0z on 2006-06-17
I tried this today. My problem is I'm using Kubuntu and cannot follow your way completely.

I'm using KPPP to dial, and it all goes OK until the moment ATD*99***1# command is passed to the phone. From this point, KPPP starts "waiting for CONNECT", and waits forever... :(

---

### Post by fdimmling on 2006-06-17
Have you tried wvdial?

You need a file /etc/wvdial.conf, mine is

[Dialer GPRS]
Modem = /dev/rfcomm0
Baud = 115200
Dial Command = ATDT
Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","internet.eplus.de";
FlowControl = None
Username = eplus
Password = gprs
Phone = *99***1#

for dialing via mobile phone. 

To connect, I enter:

sudo wvdial GPRS

in a console. wvdial cares for all the ppp stuff itself. As soon as you see the name server address displayed in the terminal you have internet access.

Wvdial is installed by default and is ready to be run as soon as you have a wvdial.conf. Since I use Gnome Ubuntu I never tried kppp.

Friedrich

---

### Post by nekr0z on 2006-06-17
Still the same thing... It looks like the problem is not in dialer, but somewhere deeper.
> nekr0z@xxxxxxxx:~$ sudo wvdial GPRS
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT+CGDCONT=1,"IP","internet.nw"
AT+CGDCONT=1,"IP","internet.nw"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#


---

### Post by fdimmling on 2006-06-17
Do you have installed the package setserial?

Friedrich

---

### Post by nekr0z on 2006-06-17
*Now* I do! :)

Looks like I have to set it up somehow?

---

### Post by nzgreen on 2006-06-17
[QUOTE=fdimmling]It works now after deleting the connection on the RAZR and make it pairing again. To switch between file transfer and use of rfcomm0 I have to restart bluez-utils and eventually delete the connection in the bluetooth setup of the RAZR.

Friedrich[/QUOTE]
You should edit your rfcomm.conf file such that rfcomm0 is used for dial-up networking and rfcomm1 (for example) is used for file transfer.  Here's what my rfcomm.conf looks like - you can get the channel number by doing sdptool browse bdaddr:
```
rfcomm0 {
        # Automatically bind the device at startup
        bind yes;
        # Bluetooth address of the device
        device 00:0A:D9:C9:D4:8D;
        # RFCOMM channel for the connection
        channel 1;
        # Description of the connection
        comment "Z600 Dial-up Networking";
}

rfcomm1 {
        # Automatically bind the device at startup
        bind yes;
        # Bluetooth address of the device
        device 00:0A:D9:C9:D4:8D;
        # RFCOMM channel for the connection
        channel 4;
        # Description of the connection
        comment "Z600 Serial Port 1";
}

rfcomm2 {
        # Automatically bind the device at startup
        bind yes;
        # Bluetooth address of the device
        device 08:00:28:89:95:BD;
        # RFCOMM channel for the connection
        channel 1;
        # Description of the connection
        comment "iPAQ H4350 Serial Port";
}

rfcomm3 {
        # Automatically bind the device at startup
        bind yes;
        # Bluetooth address of the device
        device 00:0C:A5:0F:55:1C;
        # RFCOMM channel for the connection
        channel 1;
        # Description of the connection
        comment "NAVMAN GPS ONE Serial Port";
}

rfcomm4 {
        # Automatically bind the device at startup
        bind yes;
        # Bluetooth address of the device
        device 00:0A:D9:C9:D4:8D;
        # RFCOMM channel for the connection
        channel 11;
        # Description of the connection
        comment "Z600 IrMC Synchronization";
}


```

---

### Post by nekr0z on 2006-06-19
Now I get the problem: pppd claims, that "The remote system is required to authentificafe itself, but I couldn't find any suitable secret (password) for it to use to do so."

---

