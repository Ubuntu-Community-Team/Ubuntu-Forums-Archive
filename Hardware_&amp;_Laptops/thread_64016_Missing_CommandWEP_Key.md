---
title: "Missing Command/WEP Key"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by WayTooLate on 2005-09-09
I have just installed Ubuntu on my Compaq Presario 1200 with a Netgear WGT54 'G' card.  

Everything installed correctly, but every time it reboots, the same thing happens:
1) Laptop boots up OK
2) User login.  
3) Icons show for peripherals, Desktop, etc.  Right after the 'Panel' icon displays, a pop-up occurs.  
4) The pop-up window is not labeled, it just has the message, "Missing command to run".  No other details exist.  
5) The Network Settings window then appears.  

If the window is closed ('X') or accepted ('OK'), everything appears to work normally except for DNS - no internet names are resolved for Web, e-mail or even ping.  

If the WEP Key is re-entered, then names are properly resolved.  

Note: I have a Netgrear router as the DHCP server.  Other machines wired to the router have no problems, so it seems to be just the wireless link...  

As a Linux newbie, I am not sure how to proceed.    Looking at /var/log/messages, nothing is evident to me.  I don't know if I am using madwifi or ndiswrappers.  

As a recent Win-doze convert, I can search and download but unpacking tar-balls and loading new apps and drivers is quite intimidating!  

Thanks for your help!
Jim Scott

---

### Post by mlomker on 2005-09-09
[QUOTE=WayTooLate]I don't know if I am using madwifi or ndiswrappers.[/QUOTE]

Open a command prompt and type **dmesg | less**.  That'll output a bunch of kernel messages form bootup and tell you a lot of interesting things about what drivers are being used.  The **lsmod**, **lspci**, and **lsusb** commands are also informational.

I don't know the answer to your problem, but you might want to take a look at [GTK Wifi](http://ubuntuforums.org/forumdisplay.php?f=74).  It is a neat applet for managing your wifi settings.

---

### Post by WayTooLate on 2005-09-09
Thanks for the info!
dmesg shows me a lot of stuff, but I can't see where it is having any problems...

I'll keep looking.
thanks.
Jim

---

