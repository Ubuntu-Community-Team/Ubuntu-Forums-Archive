---
title: "Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller"
date: 2005-05-08
forum: Hardware &amp; Laptops
---

### Post by Me_Titus on 2005-05-08
Hi there.

I have just installed UBUNTU, and i realised that my network card is not detected
"Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller" i did a google find and i found out that this kernel version doens't have support for this card. I need to get the latest kernel or install the driver from [www.syskonnect.com](www.syskonnect.com). The problem here is that as a newbie i dont know where to start.

Could anyone help me.

Many thanks Marco

---

### Post by djgardyn on 2005-05-09
Hello:
Have you got an Asus motherboard?, try this: [http://www.asus.com.tw/support/download/item.aspx?ModelName=A8N-SLI%20Deluxe&Type=Latest](http://www.asus.com.tw/support/download/item.aspx?ModelName=A8N-SLI%20Deluxe&Type=Latest)

---

### Post by Me_Titus on 2005-05-09
[QUOTE=djgardyn]Hello:
Have you got an Asus motherboard?, try this: [http://www.asus.com.tw/support/download/item.aspx?ModelName=A8N-SLI%20Deluxe&Type=Latest](http://www.asus.com.tw/support/download/item.aspx?ModelName=A8N-SLI%20Deluxe&Type=Latest)[/QUOTE]

No its a toshiba laptop.
Toshiba Equium A80

---

### Post by mitropank on 2005-05-22
[QUOTE=Me_Titus]No its a toshiba laptop.
Toshiba Equium A80[/QUOTE]

can you say me how did you installed ubuntu on the toshiba a80?
I've tryied Ubuntu Live cd with acpi=off and pcmcia=off options, but when start X,  i've the cursor blocked at the center of the screen and i can do nothing....

tnx.

---

### Post by kleeman on 2005-05-22
I have had this problem for quite some time (the gigabit card and the sk98lin driver which doesn't work). Here is my bug report:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=6142](https://bugzilla.ubuntu.com/show_bug.cgi?id=6142)

You have to download the driver from sysconnect and then put 
sk98lin.tar.bz2 into its own subdirectory. then from there issue
tar jxvf sk98lin.tar.bz2
Then install the linux-source and linux headers packages for your kernel
then go to /usr/src and issue
sudo tar jxvf linux-source-2.6.10.tar.bz2 
ln -s linux-source-2.6.10 linux
ln -s /usr/src/linux-headers-2.6.10-5-*-* (where the stars correspond with your kernel version)

Then go back to the subdirectory where you put sk98lin.tar.bz2 and issue
sudo sh  install.sh

and choose option 1)

If everything was installed properly as per instructions above the network should work. To bring it up type
sudo ifup eth0

These instructions are a bit complex so feel free to ask questions  :smile:  :smile:  :smile:

---

### Post by Me_Titus on 2005-05-23
Thanks for the reply but as a newbie, i dont know where to start from.
I had other other laptop, running Fedora, but that distro is too slow. A couple of weeks ago i bought this brand new laptop, and since then, i tried fedora core 4, ubuntu 5.04 and 5.10 not to mention mepis 3.3.1 as well. I really enjoy ubuntu, and that is way, i came back. The reason for trying do many distro is because i just started using linux 1 month ago or so. The problem is that the all those distro dont bring the support for pci-e. There is also a patch for my ethe, but i dont now how to install it on the kernel. I then tried to compile the latest version of the kernel, but then, when doing "make" i got a all of error, like : gt+ librarie not installed.. So i dont really know how to finish this. I installed all the libraries from the Ubuntu 5.10 cd. but still when i do make it says that there are libraries missing. My friend who as just moved from Slackware to gentoo, says that he can't solve the problem.

Thanks for the help,
Marco 
](*,)  ](*,)  ](*,)  ](*,)

---

### Post by kleeman on 2005-05-24
Well if you need any help following the above directions let me know.
By the way the kernel developers say that this problem should be fixed in breezy. One of them has the same problem...

---

### Post by Octane on 2005-06-19
[QUOTE=kleeman]Well if you need any help following the above directions let me know.
By the way the kernel developers say that this problem should be fixed in breezy. One of them has the same problem...[/QUOTE]
The drivers provided by SkyKonnect ([www.skykonnect.de](www.skykonnect.de)) work great. Check them out.

---

### Post by kleeman on 2005-06-20
If anybody wants them I can send them the sk98lin.ko modules for the standard 386 and 686-smp hoary kernels. Just whack them here:
/lib/modules/2.6.10-5-386/kernel/drivers/net/sk98lin/sk98lin.ko

---

### Post by faarbruno on 2005-08-20
I have the same problems with Ubuntu 5.04 and Toshiba M40-145 with Marvell/yukon card.
I've installed the driver with the same procedure but the card didn't work.
I've tried  to write  /lib/modules/2.6.10-5-386/kernel/drivers/net/sk98lin/sk98lin.ko
but the system says I haven't Permission even if I've logged as Root. :mad: 

Ifconfig see the ethernet card but dhclient say: NO DHCPOFFERS recived, NO WORKING LEASES in persistent database-sleeping   ](*,)  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by kleeman on 2005-08-20
Well if ifconfig shows eth0 then your driver is usually working and your problem is likely a networking or dhcp issue. If you want help you should post the output of some commands:

dmesg | tail -30

dmesg | grep eth0

ifconfig

sudo dhclient eth0

more /etc/network/interfaces



You don't have a wireless card as well do you?

---

### Post by jopsen on 2005-08-21
[QUOTE=kleeman]
You have to download the driver from sysconnect and then put 
sk98lin.tar.bz2 into its own subdirectory. then from there issue
tar jxvf sk98lin.tar.bz2
Then install the linux-source and linux headers packages for your kernel
then go to /usr/src and issue
sudo tar jxvf linux-source-2.6.10.tar.bz2 
ln -s linux-source-2.6.10 linux
ln -s /usr/src/linux-headers-2.6.10-5-*-* (where the stars correspond with your kernel version)

Then go back to the subdirectory where you put sk98lin.tar.bz2 and issue
sudo sh  install.sh
[/QUOTE]

I have the same card in my toshiba tecra A3, Yes I'm a Newbie when it comes to linux...
I have some problems findeing out how to do what it says above:
1. where can I download: sk98lin.tar.bz2, I'v looked at Syskonnect.com but I can't find it... can I use install-8_23.tar.bz2 it contains a file named: sk98lin.tar.bz2
2. linux-source and linx headers packages, how do I do that with out internet connection... (I have internet connnection on my win partion, so is it possible to download it under windows and save on my /windows (FAt32) partion?? and how??)

the rest is just about writing commands and I hope that doesn't give me any problems...
hope someone can help me with my 2 problems...

---

### Post by jopsen on 2005-08-21
okay after a look in synaptic or what ever it called, I can see that I have something of version 2.6.10-7 and 2.6.10-34 
Note: MY install is not updated in any way, so there is the same version as there is in the ubuntu install cd version 5.04.
I found the linux header package on my install cd... and installed them by use of synaptic...
and while I wait for a reply I think I'm going to try downloading header and source from kernel.org
if I'm allwrong, I'll just reinstall ubuntu :)

---

### Post by kleeman on 2005-08-21
Follow along the five steps in my howto

[http://www.ubuntuforums.org/showthread.php?t=47615](http://www.ubuntuforums.org/showthread.php?t=47615)

and if you don't understand anything ask!
The driver package you downloaded (install-8_23.tar.bz2) sounds correct to me.
Again check the howto carefully it is more accurate than my comments in this thread which are outdated....

---

### Post by Mr. Electric Wizard on 2005-08-30
[QUOTE=faarbruno]I have the same problems with Ubuntu 5.04 and Toshiba M40-145 with Marvell/yukon card.
I've installed the driver with the same procedure but the card didn't work.
I've tried  to write  /lib/modules/2.6.10-5-386/kernel/drivers/net/sk98lin/sk98lin.ko
but the system says I haven't Permission even if I've logged as Root. :mad: 

Ifconfig see the ethernet card but dhclient say: NO DHCPOFFERS recived, NO WORKING LEASES in persistent database-sleeping   ](*,)  ](*,)  ](*,)  ](*,)  ](*,)[/QUOTE]

This is EXACTLY what happened when I went through this whole tutorial.
Is there anything I can do to possibly get my card working?
I am typing this reply using my older 100mb card.
BTW, I am using the default Hoary Kernel (2.6.10-5-386)
and the card is a SMC9452TX (the driver is supposedly the same as the one above.)

---

### Post by kleeman on 2005-08-30
What happened after step 5 of the tutorial? Did everything give a green OK?
If it did try

sudo modprobe sk98lin

then

sudo ifup eth0

I assume your network settings are set with dhcp....

---

### Post by Mr. Electric Wizard on 2005-08-30
Yup, did that and everything was go...
However when I do sudo modprobe sk98lin the card does not light up (and no network access)?

You know what is really strange about this is that when I had this card hooked up to a 100mb router it worked like a champ, just not running GB.
As soon as I hooked up my Gigabit switch it stopped working all together?

When I do a -->  sudo ipup eth1 it activates fine, but won't light up or engage the network.
It is on eth1 because I have another card installed that is a 100mb card and I know works.

Yes, I have a DHCP server.

---

### Post by kleeman on 2005-08-30
What does

ifconfig 

show?

Also what does 

dmesg | tail -20

give?

What was your output from
sudo ifup eth1

---

### Post by Mr. Electric Wizard on 2005-08-30
[QUOTE=kleeman]What does

ifconfig 

show?[/QUOTE]

```
eth0      Link encap:Ethernet  HWaddr 00:A0:C9:1A:D8:66
          inet addr:192.168.1.40  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:c9ff:fe1a:d866/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:733 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1071227 (1.0 MiB)  TX bytes:69088 (67.4 KiB)

eth1      Link encap:Ethernet  HWaddr 00:04:E2:EC:BA:2A
          inet6 addr: fe80::204:e2ff:feec:ba2a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Memory:dfdfc000-0

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:438069 (427.8 KiB)  TX bytes:438069 (427.8 KiB)
```


[QUOTE=kleeman]
Also what does 

dmesg | tail -20

give?[/QUOTE]
```

PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 5 (level, low) -> IRQ 5
sk98lin: Network Device Driver v8.23.1.3
(C)Copyright 1999-2005 Marvell(R).
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 5 (level, low) -> IRQ 5
[B]eth1: SMC EZ Card 1000 (SMC9452TX V.2)
      PrefPort:A  RlmtMode:Check Link State[/B]
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
NET: Registered protocol family 17
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 11 (level, low) -> IRQ 11
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present
eth1: no IPv6 routers present
```

**I put in bold the SMC 9452 above because this is the actual card.  It just uses the same drivers as the Yukon.** 

[QUOTE=kleeman]
What was your output from
sudo ifup eth1
[/QUOTE]

and finally:

```

Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:04:e2:ec:ba:2a
Sending on   LPF/eth1/00:04:e2:ec:ba:2a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

All signs point to me being close to solving this debacle, but I just can't seem to get there.  Do you see anything that looks strange?
I know my DHCP server is working because I am typing this reply on the same computer using a 100mb card.  And yes, I switched the cable before I ran the sudo ifup eth1 command.

 :???:

---

### Post by kleeman on 2005-08-30
So the driver looks like its working. Maybe there is a clash between interfaces. What happens if you try:

sudo ifdown eth0
sudo ifup eth1

(you can get eth0 back by sudo ifup eth0)

---

### Post by kleeman on 2005-08-30
One other check. What does 

cat /proc/net/sk98lin/eth1

give?

---

### Post by Mr. Electric Wizard on 2005-08-31
[QUOTE=kleeman]So the driver looks like its working. Maybe there is a clash between interfaces. What happens if you try:

sudo ifdown eth0
sudo ifup eth1

(you can get eth0 back by sudo ifup eth0)[/QUOTE]

Nope, nothing.

---

### Post by Mr. Electric Wizard on 2005-08-31
[QUOTE=kleeman]One other check. What does 

cat /proc/net/sk98lin/eth1

give?[/QUOTE]

```
Detailed statistic for device eth1
=======================================

Board statistics

Card name                      SMC EZ Card 1000 (SMC9452TX V.2)
Vendor/Device ID               11ab/4320
Card type (Bit)                32
Active Port                    A
Preferred Port                 A
Interrupt Moderation           disabled
Bus type                       PCI
Bus speed (MHz)                33
Bus width (Bit)                32
Driver version                 8.23.1.3 (01)
Driver release date            Jun-20-2005
Hardware revision              v1.2

Receive statistics

Received bytes                 0
Received packets               0
Receive errors                 0
Receive dropped                0
Received multicast             0

Transmit statistics

Transmitted bytes              0
Transmitted packets            0
Transmit errors                0
Transmit dropped               10174109472
Transmit collisions            0

```

---

### Post by kleeman on 2005-08-31
It appears that the driver is not working properly judging from the transmit dropped statistics:
Transmit dropped               10174109472

Why do you think sk98lin is the correct driver?

This page shows another vendor driver:

[http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_USA&knowsPartNumber=false&productCategory=9&userPartNumber=&modelNumber=1216&partNumber=2932&downloadType=1&os=12](http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_USA&knowsPartNumber=false&productCategory=9&userPartNumber=&modelNumber=1216&partNumber=2932&downloadType=1&os=12)

---

### Post by Mr. Electric Wizard on 2005-08-31
As a "last resort", do you know of a LiveCD that uses the new kernel, 2.5.13?
I have tried Knoppix 3.9, and the card won't work with this distro either.
I am going to try Kanotix tonight and see what happens.

Is there anything that looks funky with any of the settings I posted?
Possible wrong driver perhaps?

---

### Post by Mr. Electric Wizard on 2005-08-31
That is an XP driver.
I tried to ndiswrapper the xp driver to no avail either.
The only linux drivers supplied on the driver cd were for 2.2, and 2.4 kernel.

---

### Post by Mr. Electric Wizard on 2005-08-31
BTW, Kleeman I really really appreciate you helping me with this! :) 
Thanks!

---

### Post by Mr. Electric Wizard on 2005-08-31
[QUOTE=kleeman]It appears that the driver is not working properly judging from the transmit dropped statistics:
Transmit dropped               10174109472

Why do you think sk98lin is the correct driver?

This page shows another vendor driver:

[http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_USA&knowsPartNumber=false&productCategory=9&userPartNumber=&modelNumber=1216&partNumber=2932&downloadType=1&os=12](http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_USA&knowsPartNumber=false&productCategory=9&userPartNumber=&modelNumber=1216&partNumber=2932&downloadType=1&os=12)[/QUOTE]

I concur about the wrong driver part.
There was a hyperlink in the linux directory on the CD provided by SMC, that mentioned sysconnect.  On the sysconnect site, I followed the links until I found the sk98xx link.  This is the same prefix that the drivers on the CD had.
I assumed these were the ones I needed.
Supposedly, these drivers are "Certified Linux" for Suse and are "SuSE certified drivers are included in SuSE packages"

 ](*,)

---

### Post by kleeman on 2005-08-31
Interesting that the cd only had drivers for the 2.4 kernel. Maybe something has broken since. Couple of suggestions:

1) Contact the vendor (smc) and ask which driver should be used for the 2.6 kernel. Such a kernel is standard now so the vendor should give you some advice

2) In breezy there is a new driver (skge) which might work if you are lucky ;-) It did not work for my Yukon 2 chipset but might for you.

---

### Post by semsem good on 2007-11-08
[email]greatsemsem@yahoo.com[/email] GOOD:popcorn:

---

### Post by semsem good on 2007-11-08
Re: Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller IWANT THIS DRIVER:lolflag:

---

