---
title: "3G Modem works, but is not detected"
date: 2009-05-16
forum: Hardware
---

### Post by filipe_aguiar on 2009-05-16
Yesterday i bought a *onda msa405hs* 3G modem for use with my laptop.

I have some trouble getting it to work, but after some further reading i can  get to work using usb_modeswitch.

The problem is that when i plug the modem, the network-manager doesn't detect it. So i'm forced to start the connection manualy, in the terminal.

I've created 3 files:

*/sbin/tim-web*
```

#!/bin/bash
sleep 5;
/usr/sbin/usb_modeswitch -v 0x19d2 -p 0x2000 -V 0x19d2 -P 0x0037 -m 0x01 -M 55534243123456782000000080000c85010101180101010101000000000001;

```
This is the script that changes de mode of the modem from "storage device only" to "modem".

/etc/udev/rules.d/45-onda-msa405hs.rules
```

ACTION!="add", GOTO="ONDA_End"
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", RUN+="/sbin/tim-web"
LABEL="ONDA_End"

```
This files grants that the tim-web script runs every time i plug the modem. 

*/usr/share/hal/fdi/preprobe/20thirdparty/10-onda-msa405hs.fdi*
```

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
    <match key="usb.vendor_id" int="0x19d2"> <!-- ONDA -->
      <match key="usb.product_id" int="0x0037"> <!-- MSA405HS -->
        <merge key="info.ignore" type="bool">true</merge>
      </match>
    </match>
    <match key="serial.device" string="/dev/ttyUSB3">
        <append key="info.capabilities" type="strlist">modem</append>
        <append key="modem.command_sets" type="strlist">GSM-07.07</append>
        <append key="modem.command_sets" type="strlist">GSM-07.05</append>
    </match>
  </device>
</deviceinfo>

```
This is the fdi for the modem.

What i'm doing wrong? What is missing?

This modem is very popular here in Brazil, and a lot of users are stucked with this same problem. I want help for me and for other users.

Thanks in advance.

---

### Post by dj-toonz on 2009-05-16
Hi there is a way to get the 3.5g modem working under Jaunty ubuntu. by going to


[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12) & download the 2 files (dont know if you have the usb-modeswitch installed or not) if you have you just need the second one then, if it complains about the missing usb-modeswitch, just download the first one & install it before installed the second file

usb-modeswitch_0.9.4-1_i386.deb
vodafone-mobile-connect_2.00.00-1_all.deb

Install the Usb-modewswitch first, then install the Vodafone-mobile-connect second, it will also download python files aswell, then goto applications, internet, then open the vodafone connect (you will need the APN details for your connection when it opens) and follow the walkthough, then you just click on connect & touch wood it should work

the software works with any 3.5g connections as I'm on three in the uk & it works no problem over here. Hope that helps, If you get stuck let me know & I'll help

---

### Post by filipe_aguiar on 2009-05-16
I already have the usb_modeswitch and its working fine.

I'll test the software that you've posted.

But the fact that my modem isn't detected realy bothers me. If i can make the modem to be detected, i can conect and manage the conection using the system default network-manager.

---

### Post by dj-toonz on 2009-05-16
The only modem I think what work's out of the box in Network Manager is the Huawei range of modems, I did try another brand & had the same propblem as your having, where the modem was being dectected, sort of, but network manager wouldn't pick it up, that's why I resorted to using the vodafone connect software instead & it worked like a charm, without having to keep using the terminal to connect every time & having to use ppon & ppoff & editing user scripts to enter the apn details & password, Lives to short to get stuff working, also the vodafone connect software lets you send/recieve txt messages & check you data allownece , network manager doesn't

---

### Post by filipe_aguiar on 2009-05-16
I think that the main question here is:

I have a working hardware, how can i get it detected? How can i can get my hardware detected by hal?

The sources about doing this are rare. I can't even figures in what is wrong with my configurations.

---

### Post by filipe_aguiar on 2009-05-17
I'm using the gnome-ppp for the conection now. Works fine. But i still wanna know how to make the gnome see my modem.

---

