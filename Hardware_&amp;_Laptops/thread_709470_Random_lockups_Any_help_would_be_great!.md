---
title: "Random lockups?? Any help would be great!"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by tdpeek3 on 2008-02-27
For whatever reason, my laptop, a Gateway ML3109, likes to randomly lockup while using Ubuntu.  I am dual booting Ubuntu 7,10 GG with XP and have no problems with XP.

Upon installing 7.10, The GUI would only work for a few minutes and then lock up, After a get-apt update, I no longer experienced the immediate lockups, they tend to happen after about 10 minutes of use while running Wifi, firefox, and openoffice simultaneously. I am using NDISWRAPPER for my wireless with a windows driver.

I am not sure what log file i should check to help diagnose this problem.

Any help would be appreciated.


-Trey

---

### Post by Sam Lars on 2008-02-27
Try /var/log/syslog.

---

### Post by tdpeek3 on 2008-02-29
This is the last thing that it did before it froze.  The update time server always seems to be one of the last things the PC does before it freezes.

I just dont know what to check or where to go from here.



```
Feb 28 19:40:40 Judas avahi-daemon[4740]: New relevant interface wlan0.IPv4 for mDNS.
Feb 28 19:40:40 Judas avahi-daemon[4740]: Registering new address record for 192.168.0.182 on wlan0.IPv4.
Feb 28 19:40:40 Judas NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Feb 28 19:40:40 Judas NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb 28 19:40:40 Judas NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Feb 28 19:40:40 Judas dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Feb 28 19:40:40 Judas dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.domain_name
Feb 28 19:40:40 Judas dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Feb 28 19:40:40 Judas dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Feb 28 19:40:40 Judas NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Feb 28 19:40:40 Judas NetworkManager: <info>    address 192.168.0.182 
Feb 28 19:40:40 Judas NetworkManager: <info>    netmask 255.255.255.0 
Feb 28 19:40:40 Judas NetworkManager: <info>    broadcast 192.168.0.255 
Feb 28 19:40:40 Judas NetworkManager: <info>    gateway 192.168.0.1 
Feb 28 19:40:40 Judas NetworkManager: <info>    nameserver 192.168.0.1 
Feb 28 19:40:40 Judas NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb 28 19:40:40 Judas NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Feb 28 19:40:40 Judas NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Feb 28 19:40:40 Judas avahi-daemon[4740]: Withdrawing address record for 192.168.0.182 on wlan0.
Feb 28 19:40:40 Judas avahi-daemon[4740]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.182.
Feb 28 19:40:40 Judas avahi-daemon[4740]: Interface wlan0.IPv4 no longer relevant for mDNS.
Feb 28 19:40:40 Judas avahi-daemon[4740]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.182.
Feb 28 19:40:40 Judas avahi-daemon[4740]: New relevant interface wlan0.IPv4 for mDNS.
Feb 28 19:40:40 Judas avahi-daemon[4740]: Registering new address record for 192.168.0.182 on wlan0.IPv4.
Feb 28 19:40:40 Judas dhclient: bound to 192.168.0.182 -- renewal in 34106 seconds.
Feb 28 19:40:41 Judas NetworkManager: <info>  Clearing nscd hosts cache. 
Feb 28 19:40:41 Judas NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Feb 28 19:40:41 Judas NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Feb 28 19:40:41 Judas NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Feb 28 19:40:41 Judas NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb 28 19:40:41 Judas NetworkManager: <debug> [1204245641.548138] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'Chernobyl' 
Feb 28 19:40:42 Judas ntpdate[5415]: adjust time server 91.189.94.4 offset 0.451031 sec
```

---

### Post by Sam Lars on 2008-02-29
It seems to be locking up consistently after ntpdate?  Can you disable that and see if it still crashes?

---

### Post by tdpeek3 on 2008-03-06
i disabled ntpdate, and am now lockup free! 

What is ntpdate, and is it bad that it is gone?  Also, why is it that ntpdate would have caused my PC to freeze?

thanks.

---

### Post by Sam Lars on 2008-03-08
ntpdate is responsible for synchronizing your computer's time with Internet servers.  You might want to post a bug about this.

---

