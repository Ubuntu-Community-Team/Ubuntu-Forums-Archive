---
title: "does the Dell XPS 13 9350 usb type-c dell dock wd15 with ubuntu 16.04 work ?"
date: 2016-03-15
forum: Hardware
---

### Post by ashleymail4u on 2016-03-15
Can anybody confirm if the usb type-c dock WD15 works with the ubuntu 16.04 with either ubuntu kernel or the 4.5 kernel.

I thought usb type-c Alternate Mode is already in the 4 series kernel.

Anybody have connected 2 1080p screens using this dock

---

### Post by svast on 2016-03-17
Hello, I am proud owner of this brilliant laptop XPS13 9350, and want as well to connect 2 screens on it.
Still don't get it to work with HDMI on the small USB-C adapter (DA200), but VGA/Eth/Usb all work as expected. And seems to allow only 1 screen :-(
I wish I could try also the very promising tb15 dock (thunderbolt), but it is not yet available in France.

Still I am interested by any feedback on any docking stuff plugged into that XPS13, including D3100 or wd15

best regards

---

### Post by matt082606 on 2016-05-11
Has anyone tested these ports yet?

If it is working correctly please provide any and all information about what dock, and what devices you have tested. Also please post your distro and kernel.

Thanks.

---

### Post by lumpysaurus on 2016-06-15
> **matt082606 said:**
> Has anyone tested these ports yet?

If it is working correctly please provide any and all information about what dock, and what devices you have tested. Also please post your distro and kernel.

Thanks.

With the Dell XPS 13 9350 and the WD15 everything works with 16.04 if you upgrade the kernel to 4.6 or higher. HOWEVER, if you suspend the computer then the dock has problems afterwards. I'm not sure why yet.

---

### Post by svast on 2016-06-27
> **matt082606 said:**
> Has anyone tested these ports yet?

If it is working correctly please provide any and all information about what dock, and what devices you have tested. Also please post your distro and kernel.

Thanks.
I have two USB-C TB configs (work / home):
- the DA200 dongle: works as expected (VGA output, USB, Ethernet). I still did not test the HDMI
- USB-C to Display-Port (got it from Google store) and connected two external displays (DELL UH2515) through MST (daisy chain). No problem as long as it does not go to sleep mode

---

### Post by AION2009 on 2016-11-15
No it does not work. Not as expected at least.

I have read a couple of comment saying that it works but my results are these:

DisplayPort works like a charm.
Nothing else is recognized. lsusb / kernlog, syslog dmesg what ever do not indicate anything else happening. 

But the displayport works like a charm. Bit expensive DisplayPort adapter I would say :D


I'm running 16.10 and kernel 4.8 so that should be fine. 

Also the DA200 sleep problem persists here, I posted extensive post about it here [https://ubuntuforums.org/showthread.php?t=2317843&page=13](https://ubuntuforums.org/showthread.php?t=2317843&page=13)

Edit:

charging work also but I guess that is kind of hard wired. 

And I'm rocking brand new Precision 5510 which came from the factory two weeks ago (with the WD15) and pre-installed Ubuntu.

---

