---
title: "Linksys WPC54gs woes"
date: 2010-03-12
forum: Hardware
---

### Post by arolfsen on 2010-03-12
I used the search and went through probably 2 dozen threads trying to get this card to work. 

I have the linksys WPC54GS v2 pcmcia card. 

I have installed all the utilities revolving around ndiswrapper. Wireless Network driver utility is showing up under system | administration and is functioning.

I could not get fwcutter to properly install off the cd.

I have used ndiswrapper and successfully installed the driver. However when i start the wireless network drivers utility it says:
> 
     unable to see if hardware is present


When i click OK it lists the correct driver and says:
> 
      hardware present: YES


When i click Configure Network it says:
> 
     Could not find a network configuration tool


I have done a lspci -v in terminal with the following results:
> 
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
         Subsystem: Linksys Device 0049
         Flags: bus master, fast devsel, latency 64, irq 11
         Memory at 20000000 (32 bit, non-prefetchable) [size=8k]
         Kernel driver in use: b43-pci-bridge
         Kernel modules: ssb


under SYSTEM | PREFERENCES | NETWORK CONNECTIONS no wireless network is shown.

under SYSTEM | ADMINISTRATION | NETWORK TOOLS i show:
> 
protocol     ip address    netmask     scope
IPv6         ::1           128         host
IPv4         127.0.0.1     255.0.0.0


what am i doing wrong? and why can't i get it to connect to the interweb?

---

### Post by arolfsen on 2010-03-15
bump for help

---

### Post by gordintoronto on 2010-03-15
"under SYSTEM | PREFERENCES | NETWORK CONNECTIONS no wireless network is shown."

Concentrate your efforts here. Click on the Wireless tab.  Click on the "add" button.

You will need to know your router's SSID, encryption type and password. On the wireless tab, enter the SSID, it should say "mode -- infrastructure" and "mtu -- automatic". The wireless security tab is where you enter the other info. IPv4 settings, normally "automatic (DHCP)."

By the way, it is better to use Google search than the forum search. That way it can point you to writeups in the Community docs. Sometimes they are old/obsolete, but they are generally better than message threads.

---

### Post by arolfsen on 2010-03-16
after setting up the wireless network like described above:

In the NETWORK CONNECTIONS utility the wireless connection is still showing LAST USED: NEVER. Tried to open google.com and got a connection failure.

Under NETWORK TOOLS utility the only two network devices that are showing up are LOOPBACK INTERFACE (LO) and ETHERNET INTERFACE (eth0), the wireless card is not showing up here.

i'm new to linux, and am NOT a any type of programmer. so i'm a little lost in all this.

I used google search and that's where i found all the other threads. That's how i got ndiswrapper installed.

like i said in the OP ndiswrapper is showing the driver for the wireless card installed.

---

### Post by gordintoronto on 2010-03-16
Did you reboot at any time?  A lot of Linux people will tell you that you don't have to reboot, don't believe them.

If you have followed 2 dozen threads you have probably installed stuff which makes it not work. A better strategy is to follow one thread and work it as if you were a terrier. Here's an example: in this thread:
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/)
It seems to have a complete solution to your problem. If you tried it and it didn't work, you could ask why. 

BTW, to "edit as root" use the command: gksudo gedit [file]

Your card is a BCM4318 (rev 02), which is what you should put into Google.

---

