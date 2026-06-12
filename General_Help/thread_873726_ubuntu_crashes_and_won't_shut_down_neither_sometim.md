---
title: "ubuntu crashes and won't shut down neither sometimes"
date: 2008-07-29
forum: General Help
---

### Post by markling on 2008-07-29
had ubuntu lock up on me completely twice within the last 24 hours.

the day yesterday was hot, today it is not.

never happened before - had it installed three months or so.

also often won't shut down: powers down, but the lights are still on and the drive still going. have to pull the plug and battery to get it to switch off. (IBM X40 laptop)

didn't used to do that for the first six weeks or so of use. but have been having to do a brute-force power down so often that its beginning to make me wonder about the integrity of my clean install.

please help

markling.

---

### Post by cronholio on 2008-07-29
Have you installed any new software recently that might have caused it? Or changed hardware components?

---

### Post by markling on 2008-07-29
hello mr cronholio. thanks for your reply. i installed firestarter last night after firefox and open office both went down at the same time. after that crash i had another where the whole machine locked up but i can't remember if that was before i installed firestarter or afterwards.

i had running:
firefox 3.01
open office 2.4 - multiple windows
thunderbird 2.0.0.16
Skype 2.0.0.68
(firestarter 1.0.3)

cheers

markling.

---

### Post by cronholio on 2008-07-29
Can you check the log files in /var/log for the time of the crash? The interesting ones should be messages, kern.log and syslog.

---

### Post by markling on 2008-07-29
i wouldn't know what i'm looking for - should i post it here?

how far back in time from the moment of crash do you want me to go?

cheers

markling

---

### Post by markling on 2008-07-29
will this do?

messages:

Jul 29 13:58:31 mark-laptop kernel: [10835.944412] Inbound IN=ath0 OUT= MAC=00:05:4e:4d:bc:b4:00:14:7f:56:f2:cf:08:00:45:00:00:77:ec:3a:00:00:6e:11:7a:87:4e:92:d5:38:c0:a8:01:41:8d:12:c5:de:00:63:44:e6:fd:bb:02:79:1f:c1:97:18:40:e2:df:7f:82:81:34:91:59:02:e7:47:a5:e6:86:41:bb:c0:c7:53:b8:d0:2c:68:19:96:71:e0:b5:e5:71:3b:d2:3c:38:30:3a:64 SRC=78.146.213.56 DST=192.168.1.65 LEN=119 TOS=0x00 PREC=0x00 TTL=110 ID=60474 PROTO=UDP SPT=36114 DPT=50654 LEN=99 

syslog:

Jul 29 13:58:31 mark-laptop kernel: [10835.944412] Inbound IN=ath0 OUT= MAC=00:05:4e:4d:bc:b4:00:14:7f:56:f2:cf:08:00:45:00:00:77:ec:3a:00:00:6e:11:7a:87:4e:92:d5:38:c0:a8:01:41:8d:12:c5:de:00:63:44:e6:fd:bb:02:79:1f:c1:97:18:40:e2:df:7f:82:81:34:91:59:02:e7:47:a5:e6:86:41:bb:c0:c7:53:b8:d0:2c:68:19:96:71:e0:b5:e5:71:3b:d2:3c:38:30:3a:64 SRC=78.146.213.56 DST=192.168.1.65 LEN=119 TOS=0x00 PREC=0x00 TTL=110 ID=60474 PROTO=UDP SPT=36114 DPT=50654 LEN=99 

kern.log:

Jul 29 13:58:31 mark-laptop kernel: [10835.944412] Inbound IN=ath0 OUT= MAC=00:05:4e:4d:bc:b4:00:14:7f:56:f2:cf:08:00:45:00:00:77:ec:3a:00:00:6e:11:7a:87:4e:92:d5:38:c0:a8:01:41:8d:12:c5:de:00:63:44:e6:fd:bb:02:79:1f:c1:97:18:40:e2:df:7f:82:81:34:91:59:02:e7:47:a5:e6:86:41:bb:c0:c7:53:b8:d0:2c:68:19:96:71:e0:b5:e5:71:3b:d2:3c:38:30:3a:64 SRC=78.146.213.56 DST=192.168.1.65 LEN=119 TOS=0x00 PREC=0x00 TTL=110 ID=60474 PROTO=UDP SPT=36114 DPT=50654 LEN=99 

cheers

markling

---

### Post by cronholio on 2008-07-30
You need to post the last message before the crash. You will probably find it easily due to the time difference to the next one that should be related to booting the system. The info in the messages you posted looks unsuspicious and is not related to a crash.

---

### Post by markling on 2008-08-02
i presume then there must be some other reason for the crashes. those messages are last recorded in the moment before the last crash. there were two such crashes within the space of 24 hours. they have not been repeated since.

indeed, all appears to be running well. if as you say there's nothing unusual in the messages i've posted here then i'll just put it down to a brief gremlin infection.

there is, however, still this matter of the machine often not shutting down properly. its an IBM X40 laptop and the problem has occured regularly for at least a month. it starts shutting down and then hangs. battery and plug have to be removed to regain control of the machine. problem occured after an update probably in june.

cheers

m.

---

### Post by cronholio on 2008-08-03
Are there any suspicious looking messages in the logs at the moment when it hangs during shutdown?

---

### Post by markling on 2008-08-05
the log entries i posted above were the last recorded before the system hung last time.

it happened again this morning at 11.28. i had only firefox running, with 10 open tabs.

these are the last listed entries in messages up to the point of the crash - something about message handler not being found an hour before the system hung:-

messages:

Aug  5 10:30:24 mark-laptop kernel: [  121.852798] NET: Registered protocol family 10
Aug  5 10:30:24 mark-laptop kernel: [  121.854166] lo: Disabled Privacy Extensions
Aug  5 10:30:24 mark-laptop kernel: [  121.856510] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  5 10:30:37 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Aug  5 10:30:41 mark-laptop kernel: [  141.651233] NET: Registered protocol family 17
Aug  5 10:30:58 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Aug  5 10:30:58 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Aug  5 10:30:58 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Aug  5 10:30:58 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
Aug  5 10:47:24 mark-laptop -- MARK --
Aug  5 11:07:24 mark-laptop -- MARK --
Aug  5 11:27:24 mark-laptop -- MARK --

--
the last entry was recorded in kern.log an hour before the crash:-

kern.log

Aug  5 10:30:24 mark-laptop kernel: [  121.852798] NET: Registered protocol family 10
Aug  5 10:30:24 mark-laptop kernel: [  121.854166] lo: Disabled Privacy Extensions
Aug  5 10:30:24 mark-laptop kernel: [  121.856510] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  5 10:30:34 mark-laptop kernel: [  133.876794] ath0: no IPv6 routers present
Aug  5 10:30:41 mark-laptop kernel: [  141.651233] NET: Registered protocol family 17
Aug  5 10:31:06 mark-laptop kernel: [  173.621208] ath0: no IPv6 routers present

--
syslog has an interesting run of awkward looking entries:-

syslog:

Aug  5 10:30:41 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Aug  5 10:30:52 mark-laptop NetworkManager: <info>  Supplicant state changed: 1 
Aug  5 10:30:52 mark-laptop NetworkManager: <info>  Activation (ath0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'BTHomeHub-2ED4'. 
Aug  5 10:30:52 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) scheduled. 
Aug  5 10:30:52 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) started... 
Aug  5 10:30:53 mark-laptop NetworkManager: <info>  Activation (ath0) Beginning DHCP transaction. 
Aug  5 10:30:53 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 3 of 5 (IP Configure Start) complete. 
Aug  5 10:30:53 mark-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface ath0 
Aug  5 10:30:53 mark-laptop dhclient: wifi0: unknown hardware address type 801
Aug  5 10:30:55 mark-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface ath0 
Aug  5 10:30:55 mark-laptop dhclient: wifi0: unknown hardware address type 801
Aug  5 10:30:57 mark-laptop NetworkManager: <info>  Old device 'ath0' activating, won't change. 
Aug  5 10:30:58 mark-laptop dhclient: DHCPREQUEST of 192.168.1.65 on ath0 to 255.255.255.255 port 67
Aug  5 10:30:58 mark-laptop dhclient: DHCPACK of 192.168.1.65 from 192.168.1.254
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.65.
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: New relevant interface ath0.IPv4 for mDNS.
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: Registering new address record for 192.168.1.65 on ath0.IPv4.
Aug  5 10:30:58 mark-laptop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface ath0 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) scheduled... 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) started... 
Aug  5 10:30:58 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Aug  5 10:30:58 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Aug  5 10:30:58 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Aug  5 10:30:58 mark-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>    address 192.168.1.65 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>    netmask 255.255.255.0 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>    broadcast 192.168.1.255 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>    gateway 192.168.1.254 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>    nameserver 192.168.1.254 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>    domain name 'home' 
Aug  5 10:30:58 mark-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
Aug  5 10:30:58 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 4 of 5 (IP Configure Get) complete. 
Aug  5 10:30:58 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) started... 
Aug  5 10:30:58 mark-laptop dhclient: bound to 192.168.1.65 -- renewal in 40931 seconds.
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: Withdrawing address record for 192.168.1.65 on ath0.
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.1.65.
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: Interface ath0.IPv4 no longer relevant for mDNS.
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: Withdrawing address record for fe80::205:4eff:fe4d:bcb4 on ath0.
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.1.65.
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: New relevant interface ath0.IPv4 for mDNS.
Aug  5 10:30:58 mark-laptop avahi-daemon[4794]: Registering new address record for 192.168.1.65 on ath0.IPv4.
Aug  5 10:30:59 mark-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Aug  5 10:30:59 mark-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Aug  5 10:30:59 mark-laptop NetworkManager: <info>  Activation (ath0) Finish handler scheduled. 
Aug  5 10:30:59 mark-laptop NetworkManager: <info>  Activation (ath0) Stage 5 of 5 (IP Configure Commit) complete. 
Aug  5 10:30:59 mark-laptop NetworkManager: <info>  Activation (ath0) successful, device activated. 
Aug  5 10:31:00 mark-laptop avahi-daemon[4794]: Registering new address record for fe80::205:4eff:fe4d:bcb4 on ath0.*.
Aug  5 10:31:04 mark-laptop ntpdate[6022]: step time server 91.189.94.4 offset -3.366744 sec
Aug  5 10:31:06 mark-laptop kernel: [  173.621208] ath0: no IPv6 routers present
Aug  5 10:47:24 mark-laptop -- MARK --
Aug  5 11:07:24 mark-laptop -- MARK --
Aug  5 11:08:37 mark-laptop anacron[6244]: Anacron 2.3 started on 2008-08-05
Aug  5 11:08:37 mark-laptop anacron[6244]: Will run job `cron.daily' in 5 min.
Aug  5 11:08:37 mark-laptop anacron[6244]: Will run job `cron.weekly' in 10 min.
Aug  5 11:08:37 mark-laptop anacron[6244]: Jobs will be executed sequentially
Aug  5 11:13:37 mark-laptop anacron[6244]: Job `cron.daily' started
Aug  5 11:13:37 mark-laptop anacron[6276]: Updated timestamp for job `cron.daily' to 2008-08-05
Aug  5 11:17:01 mark-laptop /USR/SBIN/CRON[6315]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug  5 11:27:24 mark-laptop -- MARK --
Aug  5 11:28:03 mark-laptop NetworkManager: <info>  Supplicant state changed: 0

---

