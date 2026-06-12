---
title: "wireless on my pavillion zv5000"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by mbgb14 on 2006-07-07
Hi guys!
I've just moved my dads lappy to Ubuntu Dapper :D Woopy!
Everything (including the battery-o-meter) works, except the wireless!

I've installed ndiswrapper-utils and done

sudo ndiswrapper -i /path/to/my/inf/file.inf
sudo ndiswrapper -m
sudo ndiswrapper -l


```
mbrown@LAPTOP:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
bcmwl5a         driver present, hardware present
mbrown@LAPTOP:~$




```

However, when I goto System > Admin > Networking > my wireless, and try to connect to a network, and hit activate - it doesn't work. It just sits there forever :( 

What am I doing wrong?

---

### Post by evilghost on 2006-07-07
You need to add 'blacklist bcm43xx' to /etc/modprobe.d/blacklist and reboot.  Also add 'ndiswrapper' to /etc/modules ;)

---

### Post by mbgb14 on 2006-07-07
bcm43xx?
Wouldn't it be

bcmw15
bcmw15a

---

### Post by evilghost on 2006-07-07
> **mbgb14 said:**
> bcm43xx?
Wouldn't it be

bcmw15
bcmw15a

No, bcm43xx is the kernel module that's loaded with Dapper, it doesn't function correctly without the fwcutter firmware.  Since you are using ndiswrapper (like me) you must blacklist this kernel module from loading else ndiswrapper will not function.  I am using a BCM4306 NIC.

luser@zd7000:~$ lspci|grep -i bcm
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by mbgb14 on 2006-07-07
Okay it half works now. I can now go into the networking list, click the dropdown and see my network. I click it, click Ok, and activate the connection. It doesn't time out anymore - it says ACTIVE. So it work (aparently). BUT, when I try to get to any websites, or ping anything, it doesn't work. 

Whats wrong?

---

### Post by evilghost on 2006-07-07
> **mbgb14 said:**
> Okay it half works now. I can now go into the networking list, click the dropdown and see my network. I click it, click Ok, and activate the connection. It doesn't time out anymore - it says ACTIVE. So it work (aparently). BUT, when I try to get to any websites, or ping anything, it doesn't work. 

Whats wrong?

Post the output of:

iwconfig
ifconfig
cat /etc/resolv.conf

---

### Post by CedricMordrin on 2006-07-07
> **evilghost said:**
> No, bcm43xx is the kernel module that's loaded with Dapper, it doesn't function correctly without the fwcutter firmware.  Since you are using ndiswrapper (like me) you must blacklist this kernel module from loading else ndiswrapper will not function.  I am using a BCM4306 NIC.

luser@zd7000:~$ lspci|grep -i bcm
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

I'm using the native driver and the firmware cutter on my ZV5240...

Everything seems to work but WEP/WPA, so I can't use my encrypted network at home.
Hadn't come across any other users of this laptop yet, to see if they have the same problem.

---

