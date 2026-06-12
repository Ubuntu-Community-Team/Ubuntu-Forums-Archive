---
title: "modem huawei E1752 on ubuntu 9.04"
date: 2009-11-16
forum: Hardware
---

### Post by harvejs on 2009-11-16
hi everybody, can somebody advice me, how to configure huawei E1752 modem on ubuntu 9.04? 

many thanks

---

### Post by dalfish on 2009-11-16
It is simple Just plug in your modem if it is USB modem. go to the network manager click the mobile broadband tag if it is taken by ubuntu. it would be as a "auto cdma connection" edit the connection by clicking the edit button give the no to dial for the connection and the username and password dont forget to check the automatically connect options  and also to check the box which makes it available for all users then click ok then close the program


next time you plug in the modem before booting on to ubuntu. then boot the system it will be available 



Note user name and password and no to dial will be provided by the ISP So check it and do the procedure  

ALL THE BEST Happy browsing 



dalfish

---

### Post by harvejs on 2009-11-23
hi, thanks for answer, but I tried it and it didn't work :(

finally I found great and easy article:
[URL="http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6"]
http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6[/URL]

---

### Post by birkopf on 2010-05-16
> **harvejs said:**
> hi, thanks for answer, but I tried it and it didn't work :(

finally I found great and easy article:
[URL="http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6"]
http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6[/URL]

That's what I found most helpful as well. I have tried (London, England) T-Mobile dongle and it gets recognized immediately and works. Orange E1752 doesn't. 

To sum up:
1. Activate new dongle
2. Install usb_modeswitch (preferably through Synaptic)
3. Alt+F2 and write gksu gedit /etc/usb_modeswitch.conf
4. Add this at the bottom of opened file:

```

########################################################
# Huawei E1752
#
# Contributor: 

DefaultVendor=  0x12d1
DefaultProduct= 0x1446

TargetVendor=	0x12d1
TargetProdct=	0x1001

MessageEndpoint=	0x01

MessageContent=	"55534243000000000000000000000011060000000000000000000000000000"

```

5. Create the file: /etc/udev/rules.d/10-huawei-e1551.rules or 10-huawei-e1752.rules
6. Paste that into it:

```

ATTRS{idVendor}==”12d1&#8243;, ATTRS{idProduct}==”1446&#8243;, 
RUN+=”/usr/sbin/usb_modeswitch”

```

7. Reboot
8. Plug in dongle after system loads
9. Go to Places -> Computer -> Unmount Dongle (error will pop up if you don't have memory card in it. Ignore error)
10. Terminal and: sudo usb_modeswitch
11. All should go fine. If not - dig the net :guitar: 
12. Right click on Network Manager
13. When adding New Mobile Connection on first screen is HUAWEI device you have succeed.
14. Follow steps. For Orange UK use:
number *99#
user
pass
apn: consumerbroadband

(user and pass leave blank)



At this stage I need to unmount and start it from terminal every time. 

-Question to those who know programming well - is there any way to automate it ?

---

### Post by hanmetzen on 2010-06-06
[B]hello, please if anyone could help a mostly noob at ubuntu
I wouldn't ask if I wasn't desperate but I've been trying to ru.n huawei e1752 on my Lucid Lynx and it gives me no chance. 

in lsusb it says:[/B]

*Bus 002 Device 014: ID 12d1:1417 Huawei Technologies Co., Ltd. *

**in /etc/usb-modeswitch.conf i wrote:**

[I]########################################################
# Huawei E1752
#
# Contributor:

DefaultVendor=  0x12d1
DefaultProduct= 0x1417

TargetVendor=   0x12d1
TargetProdct=   0x1001

MessageEndpoint=        0x01

MessageContent= "55534243000000000000000000000011060000000000000000000000000000"[/I]
[B]
and when i run usb_modeswitch it appears the next and doesn't let me connect:[/B]

[FONT=monospace]Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 013 on bus 002 ...
Using endpoints 0x01 (out) and 0x82 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI Technology
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Looking for active driver ...
 OK, driver found ("option")
 OK, driver "option" detached
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x01 ...
 OK, message successfully sent
-> Run lsusb to note any changes. Bye.
[/FONT][B]
and if in [/B][B] /etc/usb-modeswitch.conf i write 1446 instead of 1417 (as the code i've been fouding around) it just doesn't find any device.

what could I be doing wrong?

thx a lot


[/B]

---

### Post by gtriderxc on 2010-06-29
OK NOW A BIT EASIER. We in Poland do it that way:
1.Open Synaptic
2. Instal [B]usb-modeswitch
3. Connect the modem into an USB.
The modem should already work. The one last thing You may be expected to do is configuration of the connection.

Have a nice day.
[/B]

---

### Post by birkopf on 2010-06-30
That re-connection if it is not discovered properly is quite important as not always usb-modem which detect modem correctly...


> **gtriderxc said:**
> We in Poland do it that way:
[/B]

Pozdrawiam Polske.... :)

---

### Post by ugm6hr on 2010-09-11
> **gtriderxc said:**
> OK NOW A BIT EASIER. We in Poland do it that way:
1.Open Synaptic
2. Instal [B]usb-modeswitch
3. Connect the modem into an USB.
The modem should already work. The one last thing You may be expected to do is configuration of the connection.

Have a nice day.
[/B]

Indeed - for Orange UK (contract) customers - I am on the special £5 / month deal, this works too (Ubuntu 10.04).

The Connection Manager gets the correct username etc - just select Britain (UK) as country, and Orange as network, and then "Contract"

---

