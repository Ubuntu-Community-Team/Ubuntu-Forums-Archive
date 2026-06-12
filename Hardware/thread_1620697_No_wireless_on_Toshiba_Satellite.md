---
title: "No wireless on Toshiba Satellite"
date: 2010-11-13
forum: Hardware
---

### Post by Special D on 2010-11-13
Hello all,

My Toshiba Satellite L645D-S4056 is currently running 10.04 LTS.  I've been following the **[Wired ethernet not getting detected]("http://ubuntuforums.org/showthread.php?t=1505697")  ** thread, but I have been unable to get my wireless working. I did manage to get my wired ethernet running using pytheas22's instructions to another user.

I'm still new to using Ubuntu.

Some commands I think you guys will need;

> 

**sudo ifconfig -a**
...
Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
...

**lspci**
...
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
08:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
...

**lshw -C Network**
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:7000(size=256) memory:f3100000-f3103fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c1
       serial: 60:eb:69:0c:b4:4f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A ip=192.168.1.3 latency=0 multicast=yes
       resources: irq:27 memory:f3000000-f303ffff ioport:6000(size=128)Any help would be greatly appreciated! I've read that the driver can't support both the wired and wireless internet in Ubuntu; if that's true, I would rather have the wireless than the wired.

Thanks,

Aaron

---

### Post by Special D on 2010-11-14
Anyone else having this problem?

---

### Post by Yellow Pasque on 2010-11-14
Uses a Realtek 8192 chip. Driver is still in the staging area of the kernel and definitely isn;t in Ubuntu 10.04. [http://linuxwireless.org/en/users/Drivers/rtl819x](http://linuxwireless.org/en/users/Drivers/rtl819x)

---

### Post by Special D on 2010-11-14
Ah, I see. Sooo... are these chips interchangeable as long as the bit count is the same? Could I, in theory, downgrade my laptop's network card to something Ubuntu 10.04 will recognize?

Or am I better off buying a USB-device from D-link until the programming catches up?

Thanks for the help Temüjin,

Aaron

---

### Post by bkauger on 2010-11-16
I am having this same problem.  It's a really nice laptop, especially given that I won it at a Bill & Melinda Gates Foundation sponsored conference!  I couldn't get Ubuntu on it fast enough, what with tall the nagware shovelled in with Windows 7.  But I do miss having a wireless connection...

Anyone have any other work around suggestions?

---

### Post by physicist47 on 2010-12-06
I have recently purchased this model of Toshiba laptop and encountered the same wireless issues. I have found that there is a workaround. Someone has written a DKMS driver for the RTL8192CE wireless chipset and set up a [PPA]("https://launchpad.net/~lexical/+archive/hwe-wireless"). To install it, run the following commands:
 
[FONT=Fixedsys]sudo add-apt-repository ppa:lexical/hwe-wireless[/FONT]
[FONT=Fixedsys]apt-get update[/FONT]
[FONT=Fixedsys]apt-get install rtl8192ce-dkms[/FONT]
[FONT=Arial][/FONT] 
Now restart the machine and upon reboot you should be able to click on the wireless icon in the top panel and set up a wireless connection.  Hope this helps.

---

### Post by Special D on 2010-12-28
That worked for me! It would not let me carry out your second and third commands, to get and install the chipset, but I commanded "sudo su" and was able to do it as root.

Problem solved. I now have functioning wireless internet.

Thank you for the help!

Aaron

---

### Post by bkauger on 2011-01-18
Thanks so much for the fix, Aaron!  I hadn't checked back in a bit, and was pleasantly surprised with your post.  Works perfectly!

---

