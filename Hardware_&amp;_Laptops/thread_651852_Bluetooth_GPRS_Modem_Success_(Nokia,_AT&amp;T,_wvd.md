---
title: "Bluetooth GPRS Modem Success (Nokia, AT&amp;T, wvdial)"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by togume on 2007-12-28
I was able to connect my laptop running 7.10 to the internet using my Nokia E70 using bluetooth through AT&T's network after putting together information found on various websites and posts. As always, I hope this will be useful for others as well.

First, make sure you have bluetooth utilities:

```
sudo apt-get install bluez-gnome bluez-utils
```
(I installed these a long time ago, please correct me if I'm missing something)

First, find the MAC address of your device:
```
togume@togulaptop:~/Desktop$ hcitool scan
Scanning ...
        00:12:D2:0A:XX:YY       Togucell
```

Then, find the channel used for dial up networking using the MAC you just found:
```
sdptool browse 00:12:D2:0A:XX:YY
...
Service Name: Dial-Up Networking
Service RecHandle: 0x1002e
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    **Channel: 2**
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100
```

In this case (and for Nokias) it's channel 2. This will be used to configure the bluetooth connection. To do so, open up /etc/bluetooth/rfcomm.conf with your favorite editor.

rfcomm.conf:
```
rfcomm0 {
bind yes;
device 00:12:D2:0A:XX:YY;
channel 2;
comment "Dial-up networking";
}
```

Next, restart bluetooth services:
```
sudo /etc/init.d/bluetooth restart
```

Now the final part is to configure wvdial. Again, open up /etc/wvdial.conf with favorite editor. The following is the configuration I used for AT&T. The name of the dialer is what will be used with the wvdial command later on.

wvdial.conf:
```
[Dialer E70BT]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=, ,"wap.cingular"
Modem = /dev/rfcomm0
Phone = *99***1#
Username = WAP@CINGULARGPRS.COM
Password = CINGULAR1
New PPPD = yes
BAUD = 460800
Stupid Mode = 1
```

Now, try out wvdial:

```
sudo wvdial E70BT
```

The first time I did this, the phone asked for a passcode, I entered anything into the phone, and then the laptop asked for the same. After this I did not need it again.

That's it. You should see something along the following:

```
togume@togulaptop:/etc/bluetooth$ sudo wvdial E70BT
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Sending: AT+CGDCONT=, ,"wap.cingular"
WvDial Modem<*1>: AT+CGDCONT=, ,"wap.cingular"
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99***1#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99***1#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Starting PPP immediately.
WvDial<Notice>: Starting pppd at Fri Dec 28 00:15:40 2007
WvDial<Notice>: Pid of pppd: 7751
WvDial<*1>: Using interface ppp0
WvDial<*1>: pppd: h&#65533;[06][08][18]&#65533;[06][08](&#65533;[06][08]
WvDial<*1>: pppd: h&#65533;[06][08][18]&#65533;[06][08](&#65533;[06][08]
WvDial<*1>: pppd: h&#65533;[06][08][18]&#65533;[06][08](&#65533;[06][08]
WvDial<*1>: pppd: h&#65533;[06][08][18]&#65533;[06][08](&#65533;[06][08]
WvDial<*1>: pppd: h&#65533;[06][08][18]&#65533;[06][08](&#65533;[06][08]
WvDial<*1>: local  IP address 10.54.129.81
WvDial<*1>: pppd: h&#65533;[06][08][18]&#65533;[06][08](&#65533;[06][08]
WvDial<*1>: remote IP address 10.6.6.6
WvDial<*1>: pppd: h&#65533;[06][08][18]&#65533;[06][08](&#65533;[06][08]
WvDial<*1>: primary   DNS address 172.16.8.224
WvDial<*1>: pppd: h&#65533;[06][08][18]&#65533;[06][08](&#65533;[06][08]
WvDial<*1>: secondary DNS address 172.16.8.223
WvDial<*1>: pppd: h&#65533;[06][08][18]&#65533;[06][08](&#65533;[06][08]
```

To exit, ctrl+c.

A couple notes:

1. I set my laptop as a trusted device on my phone, that way it does not ask for permission when the connection is initiated.

2. When testing this out, make sure other connections are disabled. The first time I tried it the packets went nowhere because I had my wireless turned on and disabled it after making the bluetooth modem connection.

3. This should also work with [email]ISP@CINGULARGPRS.COM[/email], however, I don't believe I have that plan. Make sure you have unlimited data, though, or the bill might be something worth fighting about. I pay $20 for unlimited data.

Best,

Tomás

---

### Post by BlairKatu on 2008-04-29
It works very well and excelent tutorial, Worked on Fluxbuntu 7.10 using a standard bluetooth adaptor and a samsung a737 on the new AT&T network

Thanks Thomás!!

~Blair

---

### Post by jajabinx on 2008-05-09
this was really helpful. thanks thanks.

---

### Post by saro on 2008-05-19
I tried this and I was able to connect to the phone etc. But when I start wvdial, I get " No Carrier!  Trying again." for ever.

```

sudo wvdial E70BT
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=, ,"wap.cingular"
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
NO CARRIER
--> No Carrier!  Trying again.

```

I am trying to dial to ATT using a samsung A737. Any idea why I am getting this ?

cheers
Saro

---

### Post by charlier1977 on 2008-06-30
I get the exact same error. I make to the point of dialing the number ATDT*99***1#  it pauses for a few minutes then I get the msg about no carrier. 
I am using a Moto Krzr with the unlimted Data package

---

