---
title: "Bluetooth SAMSUNG SGH-D900"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by useResa on 2006-12-03
I am trying to get file transfer working between my laptop (Dell Latitude D620) with Ubuntu Edgy installed and my mobile phone SAMSUNG SGH-D900.

When I issue the command```
hcitool scan
```The result is:> 
Scanning ...
        00:17:D5:A6:6A:E4       SGH-D900And when I issue  ```
sdptool browse 00:17:D5:A6:6A:E4
```I get > 
Browsing 00:17:D5:A6:6A:E4 ...
Service Name: WBTEXT
Service RecHandle: 0x10000
Service Class ID List:
  UUID 128: db1d8f12-95f3-402c-9b97-bc504c9a55c4
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x1cdb1d8f-1295-f340-2c9b-97bc504c9a55)
    Version: 0x0100

Service Name: Serial Port
Service RecHandle: 0x10001
Service Class ID List:
  "Serial Port" (0x1101)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Profile Descriptor List:
  "Serial Port" (0x1101)
    Version: 0x0100

Service Name: Dial-up Networking
Service RecHandle: 0x10002
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

Service Name: Voice GW
Service RecHandle: 0x10003
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: Voice GW
Service RecHandle: 0x10004
Service Class ID List:
  "Handfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 5
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0101

Service Name: Advanced audio source
Service RecHandle: 0x10005
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service RecHandle: 0x10006
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: OBEX File Transfer
Service RecHandle: 0x10007
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 6
  "OBEX" (0x0008)
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Object Push
Service RecHandle: 0x10008
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 7
  "OBEX" (0x0008)
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100Furthermore please find below the content of /etc/bluetooth/rfcomm.conf
> #
# RFCOMM configuration file.
#
rfcomm0 {
    # Automatically bind the device at startup
    bind yes;
    # Bluetooth address of the device
    device 00:17:D5:A6:6A:E4;
    # RFCOMM channel for the connection
    channel    1;
    # Description of the connection
    comment "SGH-D900";
}

rfcomm3{
       # Automatically bind the device at startup
       bind yes;
       # Bluetooth address of the device
       device 00:17:D5:A6:6A:E4;
       # RFCOMM channel for the connection
       channel 6;
       # Description of the connection
       comment "OBEX File Transfer"
}
Can someone help me please?

---

### Post by useResa on 2006-12-03
OK, I have come a bit further.

If I tried to connect from my phone to my PC, a pin was requested.
This seemed to go wrong all the time.
However, for me the same problem was the case as described in this [post]("http://www.ubuntuforums.org/showpost.php?p=1815447&postcount=4")

If I start the application *Applications --> Accessories --> Bluetooth File Sharing*, I am capable of sending files from my phone to the laptop.

If I like to get the files from my laptop ("pull" them from my phone), I understood I can uses obexftp. Basically this works, see below the result of ```
obexftp -b -l 
```> Scanning ...
Using   00:17:D5:A6:6A:E4       SGH-D900
Browsing 00:17:D5:A6:6A:E4 ...
Channel: 6
Connecting...done
Receiving "(null)"... <?xml version="1.0"?>
<!DOCTYPE folder-listing SYSTEM "obex-folder-listing.dtd">
<folder-listing version="1.0">
 <folder name="Afbeeldingen"/>
 <folder name="Muziek"/>
 <folder name="Andere bestanden"/>
 <folder name="Geluiden"/>
 <folder name="Video's"/>
</folder-listing>done
Disconnecting...doneWhat I like to know is, can the same be done using a GUI?

---

### Post by bmhm on 2007-01-01
[FONT="Verdana"]I got an SGH D500

I did this:
```
sudo aptitude install bluez-utils gnome-bluetooth
```

Edit "/etc/bluetooth/hcid.conf"
```
autoinit yes;
security auto;
passkey "5555"; # or any other
```

then restart your bluetooth service:
```
sudo /etc/init.d/bluetooth restart
```

start gnome-bluetooth
pair your phone to your PC
send files from your phone as usual
send files to your phones by right-click and send to

you may also wish to have a look at KDE's tools, they do have a gui for transferring multiple files.[/FONT]

---

