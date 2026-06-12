---
title: "Supermicro IPMI installation on server 7.04"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by pibdoc on 2007-09-18
I have just installed a Supermicro server with Ubuntu Server 7.04.
It has a IPMI card, so I can manage the server remotely. (reboot, shutdown, bios setup, etc.)
To take over the shell you have to do a couple of things. I'll quote the installationmanual:

a) BIOS POST:
	(i) Enable "Console Redirection" in BIOS Setup.
		For example, COM2 / 19.2Kbps / 8N1
	(ii) Disable "Enable Console Redirection after POST" in BIOS setup.
b) BOOT LOADER:
	(i) For GRUB, add the following TWO lines into /boot/grub/grub.conf, but
		comment out "splashimage=(hd0,0)/grub/splash.xpm.gz"
		serial --unit=1 --speed=19200 --word=8 --parity=no --stop=1
		terminal --timeout=10 serial console
		#splashimage=(hd0,0)/grub/splash.xpm.gz
	(ii) Then add "serial console=ttyS1,19200n8" to the end of kernel /vmlinuz in
		/boot/grub/grub.conf.
		For example:
		kernel /vmlinuz-2.6.5-1.358smp ro root=LABEL=/ rhgb quiet serial console=ttyS1,19200n8
		This will result all boot message to be output to console ttyS1, and you will not see
		all these boot messages in local console until login message promt up.
c) LINUX OS:
	(i) Add the following line into /etc/inittab.
		s0:2345:respawn:/sbin/agetty ttyS1 19200
	(ii) Edit /etc/securetty and add ttyS1 
(i) Add the following line into /etc/inittab.
s0:2345:respawn:/sbin/agetty ttyS1 19200
(ii) Edit /etc/securetty and add ttyS1 

Step A and B are working, so I can see the booting off the server, but when the logon screen (text based of course...) appears I won't see that. I think this is because of the absence of /etc/inittab.Just placing a new file with the above content won't work. Any ideas on how to resolve this issue?

---

### Post by stevenwagner on 2007-09-23
Yah, inittab is gone. It has something to do with  /etc/event.d  which is part of the new upstart system. I don't have it completely figured out yet. 

I've started this page here:
[https://help.ubuntu.com/community/IPMI](https://help.ubuntu.com/community/IPMI)

---

### Post by hessml on 2008-06-30
I followed the instructions on the aforementioned page and it mostly works: 

1) all the boot messages show up
2) the login prompt shows up
3) after you log in the console locks up

I'm on 8.0.4. Any ideas?

---

