---
title: "networking problems since upgrade"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by rbrcurtis on 2009-05-02
When I did the 9.04 upgrade my wireless networking got all messed up.  I was using a WUSB300N usb adapter with ndiswrapper, but since the upgrade it has been unable to connect to the wireless network; the icon just spins and spins.  I plugged in my old WUSB54G usb adapter instead and it connects fine.  However, I can't pass any network traffic at all for several hours after reboot.  I can't even ping 127.0.0.1 or anything else.  It shows that its connected, and I can stop and restart networking via etc/init.d without trouble but no change; no packets will pass, they just time out, for many hours (around 6 hours I think).   This makes rebooting kind of troublesome.  

I'm honestly a bit clueless on how to troubleshoot such a problem. Anyone have any suggestions?  I can't easily plug in my compter via a wired connection, so thats out...

Thanks.

---

### Post by rbrcurtis on 2009-05-04
Any thoughts?  Is networking part of the kernel or is it a package that can be un/reinstalled?

---

### Post by WarrenKarl on 2009-05-05
I have a similar problem.  Jaunty does not recognize my wireless card.
Everything worked well with Intrepid.  I can't figure out what to do.
Any help would be greatly appreciated.

---

### Post by Old_Grey_Wolf on 2009-05-10
I got my WUSB300N to work by going to Applications > Add/Remove... menu and installing the Windows Wireless Drivers application. I inserted the CD that came with the Adapter, and copied the drivers mrvw243.inf through mrvw246.inf along with Mrvw243.sys through Mrvw246.sys to the /opt directory using gksudo nautilus. I then opened Windows Wireless Drivers from the System > Administration menu. Clicked Install New Driver, and browsed to the location of the mrvw24*.inf file and installed it. I chose to try the mrvw246.inf first and it worked. I've done this with 8.10 and 9.04.

---

### Post by charliko on 2009-05-10
My Belkin USB wireless adaptor RTL 1187 doesnt work with 9.04 either.  I have read of some folks with this adaptor not getting ndswrapper to work with the windows drivers either.  Another message I read said someone was working on the driver.  **My problem is that every thing says its connected, but it is not getting on internet.**  Would be nice not to have to use this 50 feet of cat 5 to use the internet.  

Hope someone can point me in right direction.  I wish I had the savvy of the previous poster and could try that approach with the Belkin USB.

---

### Post by panosgr on 2009-05-10
My card was working well till yesterday, after installing the last recommended updates.
The strange thing is that my ethernet card seems to be connected (gets an ip) but I don;t have access neither to the web nor my router ip! The same thing happens if I use my linksys usb wifi adapter. It connects to my router (asks about the WPA2 password) but firefox cannot connect. I have tried other programs like Ekiga, Pidgin, Add/remove programs. Updates manager but there is no connection with the web.
If I type dhclient eth0 I get the following text:
 
wmaster0:unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: permission denied
SIOCSIFADDR: permission denied
SIOCSIFFLAGS: permission denied
wmaster0:unknown hardware address type 801
open a socket for LPF: Operation not permitted
 
I am a new user to ubuntu and I don't know what to do...
Please help.
 
My system is a Compaq Presario 1510EA laptop with 512MB Ram and only Ubuntu 9.04 installed (no dual boot).

---

### Post by panosgr on 2009-05-12
I looked at [http://ubuntuforums.org/forumdisplay.php?f=336&order=desc&page=2](http://ubuntuforums.org/forumdisplay.php?f=336&order=desc&page=2)
&#954;&#945;&#953; followed the advise to remove network manager and install wicd manager. After this my laptop keeps to connect (ethernet and wireless) to my router but no internet.
I checked /etc/resolv.conf and it shows the correct nameservers that also use my second pc connected to the same router and running winxp. This pc has internet access so the router is OK.
I used livecd 8.1 on my laptop and internet is OK. The problem is only with jaunty.
Do I have to go back to 8?

---

