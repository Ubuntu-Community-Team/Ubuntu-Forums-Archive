---
title: "Internet connectivity lost after upgrade from 9.04 to 9.10"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by wysesid on 2009-11-04
Hi All,
I recently upgraded from 9.04 to 9.10. After the upgrade, my internet connectivity has been lost. I looked around in the forums and saw threads like these:

[http://ubuntuforums.org/showthread.php?t=1307560](http://ubuntuforums.org/showthread.php?t=1307560)
[http://ubuntuforums.org/showthread.php?t=1307107](http://ubuntuforums.org/showthread.php?t=1307107)

But none of the fixes worked for me.

When I run

#sudo pppoeconf

(the most commonly recommended fix), it detects all of my interfaces but then gives me the message "Sorry, I scanned 4 interfaces, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem."

I have tested the cable on other machines and internet connectivity is OK.

Other symptoms: I can't ping anything. When I ping by IP address, I get the message "connect: Network is unreachable"

Please let me know if there's anything else I should do to get more information. Any help will be greatly appreciated!! Thanks,
-Sid

---

### Post by wysesid on 2009-11-06
Help, anyone? :(

I tried another solution I found: "sudo dhclient -r" followed by "sudo dhclient" -- no success. I went to Network connections, and when I select my wired connection (listed as "Ifupdown (eth0)" it doesn't allow me to "Edit" the connection.

I really need to get this back online.. do reply if anything occurs to you. thx

---

### Post by wysesid on 2009-11-12
::bump::
help! :)

---

### Post by bgc on 2009-11-14
That could be solved by disabling ipv6. Try it out on Firefox first:

type "about:config" in the url bar
then search for "network.dns.disableIPv6" and double-lick it so that it says "true", and see if that works.

---

### Post by efflandt on 2009-11-14
It is not clear what type of network connection method you need to use (is it through ethernet or USB).  It sounds like you have DSL, since you are trying to use pppoeconf, but the Network Connections manager may have that locked.

I know that when I tried to use an alternate wireless program to connect wireless, that did not work because Network Connections had it locked.

You would only use pppoe if you have an older bridge modem or one specifically configured as a bridge (pppoe itself does not use dhcp).  Most DSL would now use a combination modem/router, in which case the modem handles the pppoe connection, and your computer ethernet would simply get a private dhcp IP from the modem/router.

If another computer is able to connect, what is the output in that computer for **ifconfig -a** in Linux, or **ipconfig /all** in Windows command window?

If you need to use pppoe, just delete the Wired "Ifupdown (eth0)" connection (you do not need it for pppoe) and concentrate on DSL settings.

If your modem handles pppoe, delete anything from DSL settings and concentrate on getting your Wired device working (delete it, then add new).

---

### Post by tigermath on 2010-03-15
Me too have the same problem. I have netgear adsl modem.The delete button beside ifupdown eth 0 is not working.
What to do?

---

