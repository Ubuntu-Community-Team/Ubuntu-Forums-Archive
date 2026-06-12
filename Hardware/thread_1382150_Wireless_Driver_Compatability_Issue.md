---
title: "Wireless Driver Compatability Issue?"
date: 2010-01-15
forum: Hardware
---

### Post by andrewisinsane on 2010-01-15
I have an HP Mini 110 and I just finished installing the netbook remix on it. I removed Mint 7 to install it, and somewhere during the installation, the drivers for my wireless card have been lost. Is there anything I can do to get my wireless back?

---

### Post by DOSn3rd on 2010-01-15
What wireless card is it?
Run the command "lspci", it should be something wifi-related in the output ;)

---

### Post by andrewisinsane on 2010-01-15
The Network controller is Broadcom Coporation BCM4312 802.11/g (rev 01)
The Ethernet controller is Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (Rev c0).
Are those the only ones that you needed? I'm learning about this as I go.

---

### Post by onegallon on 2010-01-15
Check out my thread of one week ago "Broadcom 802.11 STA driver" click on "2" for complete description of fix. Don't pay attention to some of the older fixes, as a lot of them relate to when
UBUNTU wasn't supplying the driver, and they may be misleading. When I ran a search
the Broadcom drivers popped up. Think they were resident on the burned installation disk.

---

### Post by Greenwidth on 2010-01-15
Yes, the drivers are on the LiveCD. See:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by andrewisinsane on 2010-01-16
Thanks for helping me get the drivers! Next issue though... Now the STA Driver is showing up in the Hardware Drivers list, but it will not activate. I went through the steps on the Broadcom solution guid, but nothing is working. I click activate, it asks for my password, it thinks for a few seconds and then it still says that the driver is not active. Any suggestions?

---

### Post by onegallon on 2010-01-16
you have to install driver to activate it

---

### Post by onegallon on 2010-01-16
Did you go through the procedure of installing the ndiswrapper files? Check the 
synaptic pkg manager to see if ndisgtk, ndiswrapper-utils-11.9, and ndiswrapper-common are installed. I found the files in the synaptic pkg manager by clicking on search and entering ndis. The three files then came up, but were not installed in my system as downloaded. Marking one will auto mark all three necessary files. Then click install. After that when I went to hardware drivers  window popped up overlaying
the hardware drivers window, recognizing my broadcom card and showing two broadcom drivers. This pop-up window was were I selected and installed the STA driver. Once that is done you will get a screen with the description of the installed driver when you go system>administration>hardware drivers; and,also, your wireless light should come on. Then reboot and configure your network. Hope this helps.

---

