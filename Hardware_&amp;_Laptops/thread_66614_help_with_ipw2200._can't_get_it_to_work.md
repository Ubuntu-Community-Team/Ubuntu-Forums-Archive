---
title: "help with ipw2200. can't get it to work"
date: 2005-09-17
forum: Hardware &amp; Laptops
---

### Post by FishFoot on 2005-09-17
Hey guys,

I've been trying for 2 days now to get my ipw2200 based centrino laptop to work on Hoary and i've had various levels of success.  The truth is I'm pretty lost here and I'm going to lose my mind if I have to hunt through search results and forums for much longer.

here's my story:

The system picked up the ipw2200 during installation and gave me great hope.  I decided not to configure it right then and there.  By the time I got to configuration i figured I'd just plug into my existing network which was running wpa.  So I grabbed the wpasupplicant packages, followed some instructions I found and nothing worked.  

I shot an email to Jouni Malinen and ran through my debug output.  He was awesome but told me that I might be having a problem with the ipw2200 driver.  He pointed me in the right direction and I checked there.  Sure enough I had to upgrade the drivers.  Hoary ships with .19, Intel has released (at this point) a 1.0.0 as well as 6 development releases after that.  I grabbed the latest 1.0.6 and installed it. 

I followed all the instructions rebuilt the driver, installed it and now.... nothing works.  I shouldn't say nothing, I can't connect to ANY AP, WEP doesnt' work, unencrypted and forget WPA.  I can however get a list of networks from the drop down list in the Ubuntu Network Configuration GUI dialog.

I thought that the problem might be the 1.0.6 release so I cleaned up and installed 1.0.0.  No luck there either.  I now have that installed figuring it will be the most stable.

The problem is, I don't even know where to begin looking for the problem.  I see that the driver is correctly installed when I run 

```

    lsmod | grep ipw

```
and when I run
```

    dmesg | grep ipw

```

Can somebody point me in the right direction here.  I can't find a guide that helps and I don't really know where to begin looking inside my machine.  I'm not a total noob but I could use some guidance here.

Thanks my friends.
FishFoot

---

### Post by matthew on 2005-09-17
You are in luck, luca_linux wrote a very easy to follow HOWTO for ipw2200 and wpa. Here's the link: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
I have used this howto myself with great success. Also, luca still reads and responds to posts in that thread, so if you run into problems feel free to ask and as soon as he is online and sees it he will reply.

---

### Post by FishFoot on 2005-09-17
Yeah, I've seen it and used it.  I'll ask around there...

---

### Post by ubuntme on 2005-09-18
what is the output of lspci?

---

### Post by FishFoot on 2005-09-18
[QUOTE=ubuntme]what is the output of lspci?[/QUOTE]
```

0000:00:00.0 Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
0000:00:00.1 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Registers (rev 02)
0000:00:00.3 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process Registers (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corp. 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:02:07.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a9)
0000:02:07.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 01)
0000:02:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:09.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)


``` 

I guess this dumps the PCI bus?

---

### Post by mlomker on 2005-09-18
> I guess this dumps the PCI bus?

Yup.  I also wrote a  [how-to](http://www.ubuntuforums.org/showpost.php?p=338666&postcount=16) on the installation.

Let me know if you have any trouble with it.

---

