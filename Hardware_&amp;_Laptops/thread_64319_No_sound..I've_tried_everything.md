---
title: "No sound..I've tried everything"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by shadowchaos on 2005-09-10
Hey guys, I can't get my sound to work at all, and Ive tried everything I can think of..

0000:00:00.0 Host bridge: Intel Corp. 82875P Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82875P Processor to AGP Controller (rev 02)0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
0000:02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
0000:02:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 02)


I've tried eveyrhting, and the stuff on the sticky, but nothing. :\

---

### Post by mlomker on 2005-09-10
[QUOTE=shadowchaos]I've tried eveyrhting, and the stuff on the sticky, but nothing. :\[/QUOTE]

I'm not sure what sticky you went through.  [Seen this?](http://linux.iuplog.com/default.asp?item=94639) It's worked for others.

Has sound never worked or did it stop?  Have you tried booting Knoppix or another LiveCD?

---

### Post by shadowchaos on 2005-09-10
[QUOTE=mlomker]I'm not sure what sticky you went through.  [Seen this?](http://linux.iuplog.com/default.asp?item=94639) It's worked for others.

Has sound never worked or did it stop?  Have you tried booting Knoppix or another LiveCD?[/QUOTE]

Well, it worked when I had Ubuntu a few months ago..and when I had windows..

Thanks for the link, but it doesnt seem to change anything.. :s

It detects everything it seems, and it even shows stuff playing on XMMS..but bleh, can't get any sounds to work at all.

---

### Post by mwboyd on 2005-09-10
[QUOTE=mlomker]I'm not sure what sticky you went through.  [Seen this?](http://linux.iuplog.com/default.asp?item=94639) It's worked for others.
LiveCD?[/QUOTE]

Thanks for that - I'm trying to get my sound to work and followed the link ("Sound Problem Hoary Fix"). Problem is, when I try to alter the /etc/esound/esd.conf entry as suggested, I can't as it's a read only file and it won't let me. I have no idea how to alter this - can you help? Is it to do with not being logged in as "root"? I'm a Windozer Ubuntu newbie who finds this all very confusing!

---

### Post by installer on 2005-09-11
To edit your esd.conf file enter 'sudo gedit' in a terminal and then  edit esd.conf and save the changes.




Edit>

    After entering 'sudo gedit' you will be prompted for your logon password, and the Gedit text editor will open.

---

### Post by mlomker on 2005-09-12
[QUOTE=shadowchaos]It detects everything it seems, and it even shows stuff playing on XMMS..but bleh, can't get any sounds to work at all.[/QUOTE]

Driver is loaded?  Have you looked through these for errors?

[b]
dmesg | more
cat /var/log/syslog | more
cat /var/log/messages | more
lsmod | more
[/b]

Unfortunately every machine is a little different, so generic advice is hard to provide.  Some distros try to load multiple sound drivers on my machine and they conflict with each other...didn't have that problem with Ubuntu.

---

