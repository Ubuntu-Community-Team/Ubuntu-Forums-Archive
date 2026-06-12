---
title: "Wireless USB instability"
date: 2008-11-04
forum: General Help
---

### Post by Onay on 2008-11-04
This has been an ongoing problem, and is the only thing preventing Ubuntu from being the only OS I need... I am sorry if this is a long post but it something that I really want an explanation for


I am currently using a D-Link wireless USB adapter (DWL-G132). It is working with the help of the ndiswrapper module. There are only 2 main problems with it:

1. The internet cuts out whenever trying to load certain websites or while downloading files (especially from torrents). The only thing I can find related to all of those is that it is a bandwidth problem. My windows installation on the same computer works perfectly fine and I have never had this problem once, so I know its not the adapter or the router.

2. I understand that ndiswrapper relies on the usb-core module, which I believe is the cause of this problem. Whenever plugged in usb devices are ejected and then unplugged, I lose all internet usage. The adapter is still blinking indicating it is working, and NetworkManager shows signal strength. But the internet is completely cut out.


I have tried to do temporary fixes to the problem, such as removing the ndiswrapper module and then modprobing it, though the success rate of that is only about 10%.


All I want to know is why is this happening? Is this something that I can possibly fix, or do I have to live with it? On days where I use the computer for internet intensive activity, I end up restarting 3 or 4 times to regain internet connectivity. Is this an ndiswrapper issue? Can it be fixed?

Thanks in advance

---

### Post by Onay on 2008-11-04
bump

---

### Post by Onay on 2008-11-04
bump

---

### Post by Mark224 on 2008-11-05
Sorry I can't really help but it looks similar to the problem I am having described in this thread: [http://ubuntuforums.org/showthread.php?p=6109573]("http://ubuntuforums.org/showthread.php?p=6109573").

What problems are you referring to with usb-core?  I'll update you if I find anything relevant.  Please can you do the same for me?

---

### Post by Onay on 2008-11-05
> **Mark224 said:**
> Sorry I can't really help but it looks similar to the problem I am having described in this thread: [http://ubuntuforums.org/showthread.php?p=6109573]("http://ubuntuforums.org/showthread.php?p=6109573").

What problems are you referring to with usb-core?  I'll update you if I find anything relevant.  Please can you do the same for me?

My problem is similar... although my other apps do work when usb devices are plugged and unplugged, and the issue dealing with bandwidth is still an issue. Actually the bandwidth issue I described above is more annoying because that's the primary internet dropper.

Anyway I know it deals with usb-core because the ndiswrapper relies on it, and if I'm correct usb devices being plugged and unplugged also rely on it. This dependency I believe is the reason for the internet cutting out, since the wireless usb and usb devices are connected through that usb-core module.

---

### Post by Onay on 2008-11-07
bump

---

### Post by Onay on 2008-11-09
Arg still can't find anything else about this and I'm still searching...

---

### Post by CLomax on 2008-11-09
It seems likely that your ISP is throttling your traffic or blocking certain websites especially if you're, like me, in the UK.

I've been having terrible trouble with Pipex lately and they don't seem to want to know.

How long has this been happening? Has it ever worked perfectly before?

My DWL-G122 works out of the box, I don't see why the DWL-G132 shouldn't.

---

### Post by Onay on 2008-11-10
> **CLomax said:**
> It seems likely that your ISP is throttling your traffic or blocking certain websites especially if you're, like me, in the UK.

I've been having terrible trouble with Pipex lately and they don't seem to want to know.

How long has this been happening? Has it ever worked perfectly before?

My DWL-G122 works out of the box, I don't see why the DWL-G132 shouldn't.

Here's all I know: the usb adapter worked perfectly only in windows, and I'm using the exact same windows drivers through the ndiswrapper module. This has been a problem since I first installed feisty a while back.

I also found some useful information regarding my card. Apparently it works with the atheros driver AR5005UG. I'm not exactly sure what this means, because the adapter didn't work at all "out of the box", is there a way I can stop using ndiswrapper and try this atheros driver?

---

### Post by CLomax on 2008-11-10
> **Onay said:**
> Here's all I know: the usb adapter worked perfectly only in windows, and I'm using the exact same windows drivers through the ndiswrapper module. This has been a problem since I first installed feisty a while back.

I also found some useful information regarding my card. Apparently it works with the atheros driver AR5005UG. I'm not exactly sure what this means, because the adapter didn't work at all "out of the box", is there a way I can stop using ndiswrapper and try this atheros driver?

I think it means you can use a Madwifi driver with it. It's worth a shot if it has been troubling you that long. Apparently the very page the driver was on closed down none too recently and I couldn't find any more information and googling the problem only churns out people who are having problems installing the driver.

---

### Post by Mark224 on 2008-11-10
What's the output from running the following command?
```

lsusb

```

---

### Post by Onay on 2008-11-10
```
$ lsusb
Bus 005 Device 003: ID 2001:3a03 D-Link Corp. [hex] 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04b3:310b IBM Corp. Red Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04b3:300a IBM Corp. 
Bus 001 Device 001: ID 0000:0000  

```

The D-Link DWL-G132 is at ID 2001:3a03.

---

### Post by Mark224 on 2008-11-11
If you haven't already then search for the ID string "2001:3a03" and you may find some better way of setting up your network adaptor.

When the problem next occurs try running the following commands and post the last 20 or so lines of each output.
```

sudo dmesg
tail /var/log/messages

```

BTW: Are you using Network Manager to configure the wireless network?  I have found this very flaky and found that manual configuration was necessary.

---

### Post by Onay on 2008-11-11
> **Mark224 said:**
> If you haven't already then search for the ID string "2001:3a03" and you may find some better way of setting up your network adaptor.

When the problem next occurs try running the following commands and post the last 20 or so lines of each output.
```

sudo dmesg
tail /var/log/messages

```

BTW: Are you using Network Manager to configure the wireless network?  I have found this very flaky and found that manual configuration was necessary.

I already have searched google for it but it just came up with the AR5005UG atheros madwifi driver which has not been updated and I can't figure out how to get it to work.

I'll post the message next time it happens

And yes I am using NetworkManager auto configuration by identifying the network and putting in the wep code

---

### Post by Onay on 2008-11-12
[http://www.linuxant.com/driverloader/wlan/install.php](http://www.linuxant.com/driverloader/wlan/install.php)

By the way if anyone knows anything about this it says on their site that they tested out my exact usb wireless card and it works, but I'm not sure what it is or how to use it

---

### Post by Mark224 on 2008-11-13
AFAIK DriverLoader does much the same thing as NDISWrapper.  DriverLoader is not free, though.

---

