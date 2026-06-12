---
title: "Need help setting up HP PSC 1210 on network"
date: 2008-11-09
forum: General Help
---

### Post by 5oviet on 2008-11-09
I'm running Ubuntu 8.10 64 bit.

I have an HP PSC 1210 printer connected to a Windows XP machine on the network and I'm trying to set it up. I've tried going to system>administration>printing and setting it up that way. It sees the printer and can connect to it, but when I get to the part where I have to choose the driver, there is no PSC 1210 option. The closest thing, PSC 1200, doesn't work. It sends the job but the printer doesn't do anything I've tried doing "sudo hp-setup" but that couldn't detect the printer at all. Any ideas?

---

### Post by 73ckn797 on 2008-11-09
> **5oviet said:**
> I'm running Ubuntu 8.10 64 bit.

I have an HP PSC 1210 printer connected to a Windows XP machine on the network and I'm trying to set it up. I've tried going to system>administration>printing and setting it up that way. It sees the printer and can connect to it, but when I get to the part where I have to choose the driver, there is no PSC 1210 option. The closest thing, PSC 1200, doesn't work. It sends the job but the printer doesn't do anything I've tried doing "sudo hp-setup" but that couldn't detect the printer at all. Any ideas?


Go to: Applications/Add/Remove and install "hplip" and see if that will help you. 

You can go here: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) but it will only offer the same as can be found in my suggestion. This link was the result of going to HP with your printer model and looking for Linux drivers.

Google, Search, Ubuntu Help and Ubuntu Community Documentation are your friends. Use them.

---

### Post by 5oviet on 2008-11-09
HPLIP is that "sudo hp-install" command I mentioned, and I've already tried it. It doesn't detect the printer at all.

---

### Post by 73ckn797 on 2008-11-10
> **5oviet said:**
> HPLIP is that "sudo hp-install" command I mentioned, and I've already tried it. It doesn't detect the printer at all.


This one involves no command line input. It is self installing via the Add/Remove or even through Synaptic.

---

### Post by 5oviet on 2008-11-10
I installed it through add/remove and when I go to system>preferences>HPLIP Toolbox nothing happens... Oh and by the way, it DOES send the print job because the printer makes the noises it always does, moving the cartridges, but then gets stuck right before actually sucking the paper in and printing.

---

### Post by 5oviet on 2008-11-12
Actually, it seems to me that the 1200 driver it's using is the right one because it's the 1200 SERIES, which would include 1210. Also, Vista uses a 1200 series driver as well, but that works.

---

### Post by 5oviet on 2008-11-17
Anybody?

---

### Post by m00nshine on 2010-04-19
BUMP

I'm having this same exact problem. Does anyone know where I can find the PPD file for a 1210 or how I can get hplip to see the printer?

---

### Post by m00nshine on 2010-05-21
Bump bomp

---

### Post by spcwingo on 2010-05-21
I have that same EXACT setup here...here's what you can do to get it going:

First, go to the XP box and go to start>control panel>printers and faxes>hp psc 1200 series (right click)>properties>ports>enable bidirectional support (untick).  Let me know how it goes.  :)

---

### Post by m00nshine on 2010-05-21
Thanks for the help. I'm rebooting the win box now but so far I got an unable to find CIFS host error. I have already restarted cups. I think it's definitely communicating with it now, might be share permissions?

---

### Post by spcwingo on 2010-05-21
> **m00nshine said:**
> Thanks for the help. I'm rebooting the win box now but so far I got an unable to find CIFS host error. I have already restarted cups. I think it's definitely communicating with it now, might be share permissions?

Have you tried connecting through samba as opposed to CIFS?

EDIT: You might also want to add the print server info to your /etc/hosts file.  Like so,

```
127.0.0.1	localhost
127.0.1.1	jonathan-desktop
[COLOR="Red"]192.168.0.100	jnjwingo[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

EDIT 2:  I also forgot to add that I have the XP box setup with a static IP address.

---

### Post by m00nshine on 2010-05-22
I reinstalled 9.10 and it's working now, thanks so much. Unticking that field was the fix.

---

### Post by spcwingo on 2010-05-22
I'm glad you got it going.  Have fun with Ubuntu.  ;)

---

### Post by m00nshine on 2010-05-22
Yeah I'm so glad I got it working because it was really irking me - it made me think bad things about linux :( hplip wouldn't see it at all! But, all is well now. Thanks again, buddy.

---

### Post by [__nik__] on 2011-05-26
Had the same problem . same fix worked unchecked the bidirectional option in XP 
Thanks

---

### Post by spcwingo on 2011-05-26
No prob, by the way, what version of Ubuntu are you using?  I'm just curious as to which versions of Ubuntu this is working on.  I'm just wondering as I have now retired the PSC1210.  :(

---

