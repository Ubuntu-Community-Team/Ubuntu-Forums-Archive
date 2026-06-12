---
title: "No connection (eth0) with PCMCIA nic"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by iminj on 2005-09-21
I have an old IBM Thinkpad with a Belkin FD5020 nic (PCMCIA). 

The laptop connected with 'warty', but I am struggling now with 'hoary', and can not connect to my LAN. ifconfig shows me a "lo" (localhost), but no eth0.

Here's what I've done so far:

(1) The nic wasn't recognized during the installation, so I added the driver "pcnet_cs" to /etc/modules. Now lsmod lists pcnet_cs .. (although it shows as being used by 0 modules .. if that's important.)

(2) I also noticed at the boot, that PCMCIA wasn't being loaded, so I added "i82365" to /etc/modules. Now the little LED lights on my nic's dongle glow, so I assume that PCMCIA is loading properly.

What next ? ... anyone ?

Thanks
-iminj

---

### Post by az on 2005-09-21
The bug is being worked on!

[http://bugzilla.ubuntu.com/show_bug.cgi?id=8575](http://bugzilla.ubuntu.com/show_bug.cgi?id=8575)

---

### Post by iminj on 2005-09-21
azz:

Thanks for the quick response !

I'm not 100% certain .. but I don't think that the bugzilla report you point to is the obstacle I currently face. The reported bug was a failure of pcmcia to load properly. I already found the fix >> put i82365 into /etc/modules.

I believe I now have pcmcia working. (If there is a way to test this, please let me know.)

My problem is no network connection ... no eth0.

---

### Post by az on 2005-09-21
I see.   Now that the module is loaded (you load it yourself or you put it in /etc/modules) you get pcmcia.  It is just that since the installer did not detect your card, the interface is not configured.  You need to go to the networking tool in your system menu.  Configure your wireless connection.

---

### Post by iminj on 2005-09-21
Thanks azz:

Yes, you're correct. I added the modules to /etc/modules - and now pcmcia and the nic's drivers are loaded after I boot the system. 

The **problem is** when I go the networking tool in the system menu, I don't see any option for configuration of an ethernet connection (eth0). It's simply not there. 

There's an option to configure a modem ( I have a pcmcia modem card in the laptop) .. but nothing for the pcmcia nic.

Just be sure it's not a hardware failure, I just popped a liveCD into the laptop (slax - the only one handy), and it connects.

-iminj

---

### Post by iminj on 2005-09-22
azz:

Your 1st reply (a bug) was the correct answer after all.

Although I am using ubuntu 'hoary', I downgraded pcmcia-cs to the version found on the 'warty' install CD ... and  I now have an eth0 connection. 


Thanks. 
-iminj

---

