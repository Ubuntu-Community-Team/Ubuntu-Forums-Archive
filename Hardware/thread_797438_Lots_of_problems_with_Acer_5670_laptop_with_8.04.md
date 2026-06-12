---
title: "Lots of problems with Acer 5670 laptop with 8.04"
date: 2008-05-17
forum: Hardware
---

### Post by pierrefar on 2008-05-17
Hi,

After a long search, I settled on Ubuntu 8.04 as the best Linux distro for my needs. It works superbly most of the time, but I have a few issues that I need help with.

The laptop is 3+ years old, so the battery doesn't hold that much charge.

1. The camera. It's an integrated webcam. I'm sure it's a Logitech one because it was not working under Mandriva. Asking on the Mandriva forums, they said I should post the output of lsusb. Under Ubuntu, the outuput of lsusb is - well - nothing:
> Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
I tried Cheese and it's not working either. 

2. Power management. There are multiple issues here that may or may not be related:
a. I can rarely get the computer to suspend or hibernate. Most of time, it just fails to suspend or hibernate giving me a login screen (with an unlock button, a leave a message button, etc). If it does succeed (very very rare!), on restart I get a message saying it failed to hibernate. 

b. On a routine, yet random, basis, the power management applet in the taskbar says it cannot determine the state or cannot get information. When that happens, the System->Quit window loses the hibernate and suspend buttons but keeps the shutdown button. I cannot find any correlation between losing the suspend/hibernate and any action or event to trigger it. It's random as far as I can tell.

c. The CPU runs very very hot even though in my power management applet I selected "maximum power saving". It gets so hot that using it as a *lap*top is very likely to reduce my chances of reproducing. The fan kicks in at full blast (well, it's very loud) regularly but that doesn't help much.

So please help. I'm half tempted to just re-format and go back to Windows XP. I've tried Vista and it's crap and decided to move to Linux after seeing how rubbish Vista is (worst money I've ever spent). Please don't let me go back to Windows. I like my Compiz!

Cheers,
Pierre

---

### Post by suriro on 2008-05-18
[http://global.acer.com/products/notebook/as5670.htm](http://global.acer.com/products/notebook/as5670.htm) says you have acer orbicam. It's known to work with linux, but it should appear in lsusb output at least. Could it be dead?
BIOS upgrade mostly helps to resolve ACPI problems (0.32xx is supposed to be latest for your model, visit acer support site for details).
There's a long thread here about overheating acer laptops, have a look at it.

---

### Post by b2d on 2008-08-20
I have the same Notebook - under Windows camera works perfetly. 7.10 Ubuntu said it some bug with camera time ti time and didn't start.
I have tried the famoust 
[http://paper0k.wordpress.com/2006/12/18/orbicam-finalmente-supportata/](http://paper0k.wordpress.com/2006/12/18/orbicam-finalmente-supportata/)

but still no luck, have you figured out guys how to make it working?

---

### Post by 4walters on 2008-09-12
I have the same laptop. Suspend and hibernate have never worked quite right but hasn't been something important enough to me to worry about. I guess I'll get a round to it one day. Have been running various versions of Linux on this lappy for 3 years and haven't had any overheating problems. Your webcam should work. the output of lsusb;

xxxxxxxxx@Takasago:~$ lsusb
Bus 005 Device 004: ID 046d:0892 Logitech, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
xxxxxxxxx@Takasago:~$

I'm wondering, as Suriro pointed out, is the camera dead or is there a problem with the usb bus? Not sure but I think you have some hardware issues going on with the total number of issues you have going on here.

If it is a bios issue how about posting the bios you're running and the bios you upgrade to, then let us know if it fixed your problems. Best of luck and and remember friends don't let friends do windows.

---

### Post by IntuitiveNipple on 2008-09-12
> **pierrefar said:**
> Hi,
So please help. I'm half tempted to just re-format and go back to Windows XP. I've tried Vista and it's crap and decided to move to Linux after seeing how rubbish Vista is (worst money I've ever spent). Please don't let me go back to Windows. I like my Compiz!

Cheers,
Pierre
If you provide some specific information as to what Linux reports it would be easier for people to provide specific useful suggestions.

As a starting-point, attach a compressed copy of the log /var/log/dmesg so we know what Linux discovers during start-up.
```

cat /var/log/dmesg | gzip > ./dmesg.log.gz

```
The lack of any devices being reported by lsusb is suspicious. I've seen that recently in another issue. I'm not sure the reason was ever completely resolved since it seemed to correct itself. I suspect the USB devices are found and will be logged in dmesg.

You can try, however, to ensure the USB device IDs are up-to-date (this shouldn't make much difference but...!):
```

sudo update-usbids
sudo update-pciids

```

---

