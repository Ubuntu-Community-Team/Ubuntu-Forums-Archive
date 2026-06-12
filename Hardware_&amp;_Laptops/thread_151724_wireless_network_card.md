---
title: "wireless network card"
date: 2006-03-28
forum: Hardware &amp; Laptops
---

### Post by iAlta on 2006-03-28
I installd a wireles network card, what now? Do I need to install a driver? If so how?
Now, I dualboot Ed- and Ubuntu. I perfer Edubuntu, it's faster. This may be because of erorrs in the installations of Ubuntu, so I'm considdering reinstalling, but I'll post about that on an apropriet forum. Edubuntu, on the other hand, has some limitations, I can't even access SPM.
Nevermind, can any one help me with the first part?

---

### Post by BlaineM on 2006-03-28
have you looked in the network config to set up the info that it needs to connect to your wireless network?

---

### Post by iAlta on 2006-03-28
[QUOTE=BlaineM]have you looked in the network config to set up the info that it needs to connect to your wireless network?[/QUOTE]
 no, where is that, and what info I need?

---

### Post by BlaineM on 2006-03-28
its under system>administration>networking.  This will then open up the network settings box that will display your available interfaces.  Next you can double click your Wireless connection and enter the appropriate information. ie... network id name, dhcp or static network address, and the rest of the info that you have set up for the wireless access point that you will be gaining access to the internet through.  When you get done entering the info, click to activate the interface.  Start there first, and you should be able to access the internet, if everything is supported.

---

### Post by iAlta on 2006-03-29
It only displays a modem connection, and I don't even havd a modem.
[[img=http://img96.imageshack.us//img96/2647/screenshotnetworksettings8ot.th.png]](http://img96.imagdshack.us/my.php?image=screenshotnetworksettings8ot.png)

---

### Post by BlaineM on 2006-03-29
did you install the wireless card into a laptop or tower?  Also what brand did you install?

---

### Post by iAlta on 2006-03-29
[QUOTE=BlaineM]did you install the wireless card into a laptop or tower?  Also what brand did you install?[/QUOTE]
The Space Needle, just kidding, a tower. 
NETGEAR 54 Mbps Wireless PCI Adaptor WG311 v3

---

### Post by BlaineM on 2006-03-29
what do you get when you run iwconfig from the terminal?

---

### Post by iAlta on 2006-03-30
lo       no wireless extention
sit0    no  wireless exetention.

but it defenetly detects it, I once wrote a command (don't remember which) it sayd something like: Subsystem: Netgear: Unknown device 6b00
But this was in Edubuntu. I'll try in Ubuntu and come back to you.

---

### Post by iAlta on 2006-03-30
hmmm... same respons with Ubuntu. Not that it supprises me. And the command I wroth was "lspci -v | less" and at the bottom it saied <available only to root> and I have tried before and I just can't logg on as root.

---

### Post by BlaineM on 2006-03-30
entering sudo before the command that needs the root account is the safe way to do things in the command line.  although the lspci -v | less should work without sudo.

iwconfig will also show you the available wireless extensions.

the root account is disabled in ubuntu.  but the sudo command gives you rights to do any of the modifications and commands that you need.

---

### Post by The_Tankengine on 2006-03-30
You can download the driver you need for this card here:
[http://network.free-driver-download.com/NETGEAR/28325/NETGEAR-WG311v3-Wireless-PCI-Adapter-Driver-v3.10.html]("http://network.free-driver-download.com/NETGEAR/28325/NETGEAR-WG311v3-Wireless-PCI-Adapter-Driver-v3.10.html")

You will need to use ndiswrapper to install these drivers.  For that, go here:
[http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper")

Good luck and let me know how it goes!

---

### Post by iAlta on 2006-03-31
[QUOTE=The_Tankengine]You can download the driver you need for this card here:
[http://network.free-driver-download.com/NETGEAR/28325/NETGEAR-WG311v3-Wireless-PCI-Adapter-Driver-v3.10.html]("http://network.free-driver-download.com/NETGEAR/28325/NETGEAR-WG311v3-Wireless-PCI-Adapter-Driver-v3.10.html")

You will need to use ndiswrapper to install these drivers.  For that, go here:
[http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper")

Good luck and let me know how it goes![/QUOTE]
thanks, but the driver won't download! I'll try IE...](*,)

Nope, probably not the browser(Opera) it's wrong with...

---

