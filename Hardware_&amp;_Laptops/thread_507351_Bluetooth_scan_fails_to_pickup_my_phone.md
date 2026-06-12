---
title: "Bluetooth scan fails to pickup my phone"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by sarath_it on 2007-07-22
After a lot of research, a lot of TS I am vexed to get my BT working.

System Inspiron 6k, internal bt

 i stop-stop the service

```

root@sarath-laptop:/home/sarath# /etc/init.d/bluetooth stop
 * Stopping Bluetooth services                                           [ OK ] 
root@sarath-laptop:/home/sarath# /etc/init.d/bluetooth start
 * Starting Bluetooth services                                           [ OK ] 
root@sarath-laptop:/home/sarath# 

```

When i do this, i get a message in the tray. 
[IMG]http://farm2.static.flickr.com/1015/872842635_2be29f4bf2.jpg[/IMG]

and then this is what happens

```

root@sarath-laptop:/home/sarath# hcitool dev
Devices:
        hci0    00:10:C6:C3:23:25
root@sarath-laptop:/home/sarath# hciconfig -a
hci0:   Type: USB
        BD Address: 00:10:C6:C3:23:25 ACL MTU: 384:8 SCO MTU: 64:8
        UP RUNNING 
        RX bytes:1008 acl:0 sco:0 events:30 errors:0
        TX bytes:613 acl:0 sco:0 commands:29 errors:0
        Features: 0xff 0xff 0x9f 0xfe 0x9b 0xf9 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
        Link policy: RSWITCH HOLD SNIFF PARK 
        Link mode: SLAVE ACCEPT 
        Name: 'sarath-laptop-0'
        Class: 0x3e010c
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Laptop
        HCI Ver: 1.2 (0x2) HCI Rev: 0x679 LMP Ver: 1.2 (0x2) LMP Subver: 0x679
        Manufacturer: Cambridge Silicon Radio (10)

root@sarath-laptop:/home/sarath# hcitool scan
Scanning ...
root@sarath-laptop:/home/sarath# 
```

1. the hci0 doesnot show any pscan or iscan
2. my XDA cinglr 8125 which is sitting right next to the dell cannot be seen :(
3. the bluetooth-manager applet options are disabled
[IMG]http://farm2.static.flickr.com/1266/873745312_ded815a3f9_o.png[/IMG]

SOME ONE PLEASE CALL 911!!!

apart from this now.. my ***Ubuntu Rocks!!!***

---

### Post by scxtt on 2007-07-22
i have a cingular 2125 (windows smartphone) - just plain ol' doesn't work all that well w/ BT in linux ... even when i get my phone and computer dongle to communicate, i can't really send/receive files consistently -- i think @ best i can send files from the phone to the computer, but it's a 1-way street - and it doesn't show up as a drive ... same goes for USB ...

---

### Post by sarath_it on 2007-07-22
well, i am just trying to connect via BT.. let me try with another phone...

update.. i tried with my friends Motorola razr.. this dell doesnot show that either. i can find the razr on my 8125 (i can even pair..)

any ideas?

---

### Post by scxtt on 2007-07-22
no ideas, i have a belkin dongle - it works to some degree (as mentioned above) ... i used to have an older moto flip phone, it worked much better (at least in terms of OBEX support) - the 2125 doesn't seem to support OBEX (if that's even a possibility) ... i've more or less given up on getting them to work ideally ...

---

### Post by sarath_it on 2007-07-23
Can anyone help me here!!

---

