---
title: "Modem Busy or Unable to Open"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by jodef on 2005-04-26
I use a 3COM US Robotics PCI modem (a confirmed hardware modem) in most distros it uses COM5(ttyS4) in Kubuntu when I set it to ttyS4 I get a **modem busy** error message. I am unsure as to how to proceed in resolving this issue. I am posting the output of **lspci -v** below some urgent assistance would be appreciated.

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
	Flags: bus master, medium devsel, latency 32
	Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: [c0] AGP version 2.0

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: cde00000-cfefffff
	Prefetchable memory behind bridge: c9c00000-cdcfffff

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
	Flags: bus master, medium devsel, latency 0

0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
	Flags: medium devsel
	I/O ports at 0c00 [size=32]

0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
	Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]

0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
	Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at cffff000 (32-bit, non-prefetchable) [size=4K]

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
	Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
	Flags: bus master, fast devsel, latency 128
	I/O ports at ff00 [size=16]

0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
	Subsystem: C-Media Electronics Inc: Unknown device 0300
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at dc00 [size=256]
	I/O ports at d800 [size=64]
	Capabilities: [48] Power Management version 2

0000:00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
	Subsystem: Silicon Integrated Systems [SiS] SiS900 10/100 Ethernet Adapter
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at d400 [size=256]
	Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at cffc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2

[B]0000:00:11.0 Serial controller: 5610 56K FaxModem 56K FaxModem Model 5610 (rev 01) (prog-if 02 [16550])
	Subsystem: 5610 56K FaxModem: Unknown device baba
	Flags: medium devsel, IRQ 11
	I/O ports at d000 [size=8]
	Capabilities: [dc] Power Management version 2[/B]

0000:00:13.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at c800 [size=32]
	Capabilities: [80] Power Management version 2

0000:00:13.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at cc00 [size=32]
	Capabilities: [80] Power Management version 2

0000:00:13.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) (prog-if 20 [EHCI])
	Subsystem: VIA Technologies, Inc. (Wrong ID): Unknown device 1234
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at cfffcf00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15) (prog-if 00 [VGA])
	Subsystem: nVidia Corporation Compaq NVIDIA TNT2 Pro
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at ca000000 (32-bit, prefetchable) [size=32M]
	Expansion ROM at cfef0000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 1
	Capabilities: [44] AGP version 2.0

---

### Post by az on 2005-04-26
"0000:00:11.0 Serial controller: 5610 56K FaxModem 56K FaxModem Model 5610 (rev 01) (prog-if 02 [16550])
Subsystem: 5610 56K FaxModem: Unknown device baba
Flags: medium devsel, IRQ 11
I/O ports at d000 [size=8]
Capabilities: [dc] Power Management version 2"

Try installing setserial from universe (you will need to transfer it from a floppy if you cannot get onto the net from ubuntu)

Open a terminal and change directories to where you put the deb
sudo dpkg -i setserial*.deb


then do
sudo setserial /dev/ttyS3 port 0x0d00 irq 11 uart 16550A

(Unless you have four serial ports on your computer, you do not need to create another device (/dev/ttyS4))

If that works, let me know.  I will file a bug report for my Topic Semicunductor modem.  Others with the USR5610 have had the same issue.  Either this needs to be autoset, or setserial needs to be included in the ship seed (on the cd)

[http://packages.ubuntu.com/hoary/base/setserial](http://packages.ubuntu.com/hoary/base/setserial)
setserial for i386:
[http://ftp.cs.umn.edu/pub/ubuntu/pool/main/s/setserial/setserial_2.17-39_i386.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/main/s/setserial/setserial_2.17-39_i386.deb)

---

### Post by jodef on 2005-04-26
Hi azz thanks for the quick response unfortunately that did't work. When I set the modem device to either /dev/modem or /dev/ttyS3 error is **unable to open modem**. When I set to /dev/ttyS4 I get **modem busy**.

In windows the modem is detected on COM5(ttyS4) and it most distros that works fine. Thinking back I believe in earlier version of Ubuntu it was detected on ttyS14 I seem to have this problem on debian based systems.

Any other ideas ](*,)

---

### Post by jodef on 2005-04-26
OK I just installed Xandros it's debian based and it detected the modem on COM4 is there any info I could get from this install that would help with the problem in Kubuntu?

---

### Post by az on 2005-04-26
lspci -vv

---

### Post by jodef on 2005-04-26
Ok azz I have been trying to solve this issue first note:

sudo setserial /dev/ttyS3 port **0x0d00** irq 11 uart 16550A seems like it should be:
sudo setserial /dev/ttyS3 port **0xd000** irq 11 uart 16550A.
Is that correct I noticed the syntax while kubuntu was booting? 

When I changed it and tried ttyS3 I get a modem ready message. But alas joy shortlived on dialing kppp terminates on connection with error 1 ie fatal error on connection. Below is the PPP log username and password correct so something else at work:
> 
Apr 26 13:19:35 localhost pppd[7674]: The remote system is required to authenticate itself
Apr 26 13:19:35 localhost pppd[7674]: but I couldn't find any suitable secret (password) for it to use to do so.
Apr 26 13:19:35 localhost pppd[7674]: (None of the available passwords would let it use an IP address.)


One additional note on boot up I notice Kubuntu setting up ttyS0 ttyS1 and ttyS14. 

I will boot into Xandros and post the lspci as well.

---

### Post by az on 2005-04-26
[QUOTE=jodef]Ok azz I have been trying to solve this issue first note:

sudo setserial /dev/ttyS3 port **0x0d00** irq 11 uart 16550A seems like it should be:
sudo setserial /dev/ttyS3 port **0xd000** irq 11 uart 16550A.
Is that correct I noticed the syntax while kubuntu was booting? 

When I changed it and tried ttyS3 I get a modem ready message. But alas joy shortlived on dialing kppp terminates on connection with error 1 ie fatal error on connection. Below is the PPP log username and password correct so something else at work:


One additional note on boot up I notice Kubuntu setting up ttyS0 ttyS1 and ttyS14. 

I will boot into Xandros and post the lspci as well.[/QUOTE]

A-ha!  I knew I was right.

Yes, it was a typo on my part.  The values you enter in setserial must match those of your lspci -vv.  If you change your pci hardware, those values may change (plug and play) and you will need to setserial again.

Make sure that your setserial values are autosaved.

Isofar as kpp not authenticating, this is a permission problem.  You should pass the noauth argument to pppd.

Try dialing with the command like:
sudo pppconfig
enter and then save your info.  Name the connection provider, for now.
sudo pon
sudo plog

Let me know if this works!

Also, com1, com2 com3 and com4 are for real serial ports.  If you have a pci device, it can either use the port addresses mapped to one of the real serial ports or use another location.  If that is the case, you must tell the kernel what that port address (and irq) is.
If you use ttyS4 and the device is not there in /dev, you have to create it

cd /dev
/.MAKEDEV ttyS4

I do not know if you have to still do this with udev, but it is just less of a hassle to use /dev/ttyS3 since it is propbably present and probably unused.

---

### Post by jodef on 2005-04-26
> Make sure that your setserial values are autosaved.

Isofar as kpp not authenticating, this is a permission problem. You should pass the noauth argument to pppd.

How do I autosave setserial values?
How do I pass noauto argument to pppd?
Not new to linux but this is new ground for me so sorry if questions a bit simplistic.

> Try dialing with the command like:
sudo pppconfig
enter and then save your info. Name the connection provider, for now.
sudo pon
sudo plog

Let me know if this works!
Going to try this now.

> Also, com1, com2 com3 and com4 are for real serial ports. If you have a pci device, it can either use the port addresses mapped to one of the real serial ports or use another location. If that is the case, you must tell the kernel what that port address (and irq) is.
If you use ttyS4 and the device is not there in /dev, you have to create it

cd /dev
/.MAKEDEV ttyS4

I do not know if you have to still do this with udev, but it is just less of a hassle to use /dev/ttyS3 since it is probably present and probably unused.
Understood except it seems the debian based distros are the ones that have this particular issue have tried dozens of other distros literally and the modem is correctly detected. So this is a learning experience for me. I was quite surprised when Xandros detected modem.

I tried MAKDEV earlier something about not devfs but udev came up can't remember exactly what.

---

### Post by jodef on 2005-04-26
> Try dialing with the command like:
 sudo pppconfig
 enter and then save your info. Name the connection provider, for now.
 sudo pon
 sudo plog
 
 Let me know if this works! 
YES!! posting from Ubuntu now. :) But again pppconfig detected modem on /dev/ttyS14 how do I get kppp to see /dev/ttyS14? I have other users on this machine while this might work for me I need kppp to work.

But we are making progress so don't abandon me yet. Here is the output of plog

> Apr 26 14:31:14 localhost pppd[7686]: sent [IPCP ConfReq id=0x2 <compress VJ 0f                  01> <addr > <ms-dns1 > <ms-dns3 >]
Apr 26 14:31:14 localhost pppd[7686]: rcvd [IPCP ConfAck id=0x2 <compress VJ 0f                  01> <addr > <ms-dns1 > <ms-dns3 >]
Apr 26 14:31:14 localhost pppd[7686]: Cannot determine ethernet address for prox                 y ARP
Apr 26 14:31:14 localhost pppd[7686]: local  IP address x.x.x.x
Apr 26 14:31:14 localhost pppd[7686]: remote IP address x.x.x.x
Apr 26 14:31:14 localhost pppd[7686]: primary   DNS address x.x.x.x
Apr 26 14:31:14 localhost pppd[7686]: secondary DNS address x.x.x.x
Apr 26 14:31:14 localhost pppd[7686]: Script /etc/ppp/ip-up started (pid 7698)
Apr 26 14:31:15 localhost pppd[7686]: Script /etc/ppp/ip-up finished (pid 7698),                  status = 0x0

---

### Post by jodef on 2005-04-26
Tried something else symlinked ttyS14 modem and changed the permissions on 
symlink to root dialout the same as on ttyS14. Now I can dial using kppp with /dev/modem but again this error reoccurs :
> Apr 26 13:19:35 localhost pppd[7674]: The remote system is required to authenticate itself
 Apr 26 13:19:35 localhost pppd[7674]: but I couldn't find any suitable secret (password) for it to use to do so.
 Apr 26 13:19:35 localhost pppd[7674]: (None of the available passwords would let it use an IP address.) 
So close ](*,) yet so far ](*,)

---

### Post by az on 2005-04-26
"YES!! posting from Ubuntu now.  But again pppconfig detected modem on /dev/ttyS14 how do I get kppp to see /dev/ttyS14? I have other users on this machine while this might work for me I need kppp to work."

I suppose that /dev/ttyS14 was there all the time and that you did not have to make it with setserial or makedev?

I do not use kppp.  It is not my choice for a modem dialer.  You should be able to use any device, for example.

To make kppp see your modem device, do 
cd /dev
sudo ln -s ttyS14 modem

Now you have /dev/modem.

It probably will be erased on boot.

Try:
create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:
#modem
KERNEL="ttyS14", SYMLINK="modem"

---

### Post by jodef on 2005-04-26
> To make kppp see your modem device, do
cd /dev
sudo ln -s ttyS14 modem

Now you have /dev/modem. 
The problem is the kppp dialer is not actually working even when I symlink ttyS14 to modem it keeps terminating with an error code 1.  ](*,) Along with the following output:
>  Apr 26 13:19:35 localhost pppd[7674]: The remote system is required to authenticate itself
Apr 26 13:19:35 localhost pppd[7674]: but I couldn't find any suitable secret (password) for it to use to do so.
Apr 26 13:19:35 localhost pppd[7674]: (None of the available passwords would let it use an IP address.) 

---

### Post by az on 2005-04-26
This is why I never used kppp.

If you run kppp as root, does it work?

Gnome-ppp?  Other dialers?

---

### Post by jodef on 2005-04-27
Thanks azz for all the assistance you really taught me a lot,it's much appreciated. 

The final piece of the puzzle came today when I was browsing the forums:
[Kppp Error](http://www.ubuntuforums.org/showthread.php?t=27782)
This excerpt straight from kppp manual: > 10.1.2.
  pppd died - The remote system is required to authenticate itself ...
  Typical error message in system log:
pppd[699]: The remote system is required to authenticate itself
pppd[699]: but I couldn't find any suitable secret (password) for it to use to do so.
pppd[699]: (None of the available passwords would let it use an IP address.)

As far as I can tell there are two causes for this problem: 
/etc/ppp/options contains the auth option. Simply put a # comment in front and try again. 
 
Simply editing the file worked am now posting via connection established via kppp.

Again many thanks \\:D/

---

### Post by Paki on 2005-04-27
BRILLIANT work guys - not getting my US Robotics 5610B to work with Ubuntu has been holding me up for MONTHS!

Just one last issue: I have to use the command line to establish the symbolic link between where Ubuntu sets up my modem (i.e., /dev/ttyS14) and /dev/modem EVERY TIME I reboot the system.

What can I do to make the symbolic link permanent?

Thanks so much, and again - great job!

p.s. - For others working through this issue, here's a note from my experience: Because it turns out Ubuntu was detecting my modem and assigning it to /dev/ttyS14, I did not have to use setserial to get the modem on-line.

---

### Post by az on 2005-04-28
Excellent!

Try:
create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:
#modem
KERNEL="ttyS14", SYMLINK="modem"

---

### Post by Paki on 2005-05-23
Worked like a charm. Thanks!

---

### Post by matchew on 2006-01-03
I just made my P2/450/320mb system triple boot. The 5610 installed under Winders, so it works there, but not under Knoppix or Breezy (S14).
 I did the verbose troubleshooting install (read all the FN key pages) then started locating and reading init scripts. Seems the low level inits descriminate against dial-up. The network port is the preferred communications channel.

---

