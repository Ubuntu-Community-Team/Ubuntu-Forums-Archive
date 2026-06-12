---
title: "Extremelly weird network problem"
date: 2024-06-26
forum: Hardware
---

### Post by laserburn2 on 2024-06-26
This problem started on Ubuntu 22.04 about a year ago and is also present on Ubuntu 24.04 which was cleanly installed on the same PC. Computer is connected by ethernet cable to a home router, some Zyxel given to me by the ISP.

Most times, everything works without any problems. But sometimes on boot Ubuntu won't connect. And here is the strange part: in order to make it work, you have to wait for notification to show that the network connection is not available, close that notification, then unplug the network cable from the router and plug it in another ethernet port on the router. If you change the port before the notification is shown or do not close the notification first, changing the port does not fix the issue. Rebooting the computer or the router often doesn't fix the issue either, only the mentioned workaround is reliable.

I've checked journal messages when this happens and I can't seem to find the problem. My guess is that lower and higher level network tools and systems are possibly quarreling among themselves. Any ideas what could be the problem or what I could check?

---

### Post by #&amp;thj^% on 2024-06-26
If you have IPV6 enabled, try to disabled it first to see if that helps steady your connection.
Do it for both WiFi and Ethernet. 

Any better?

If not give this a try: (Now wait for it to disconnect)
```
journalctl -ef > journal_output.txt
```
To quit it  use>>{Ctrl+Alt+ c}

Might give us a clue

---

### Post by laserburn2 on 2024-06-26
> **1fallen said:**
> If you have IPV6 enabled, try to disabled it first to see if that helps steady your connection.
Do it for both WiFi and Ethernet. 

Any better?

I did that now, but I won't know if it had any affect for a long time. It can sometimes take weeks before the issue reappears. The bad thing is that it usually happens when I'm in a rush or I'm eating or something else is happening that I don't have time to deal with the stupid issue. So strange that it started out of a blue and persisted through two LTS editions.

If it helps any, here is the journal from the last boot that it happened.

---

### Post by #&amp;thj^% on 2024-06-26
> **laserburn2 said:**
>  The bad thing is that it usually happens when I'm in a rush or I'm eating or something else is happening that I don't have time to deal with the stupid issue. So strange that it started out of a blue and persisted through two LTS editions.

Isn't that the way things always turn out, when your most pressed for time. :)

Your not alone on this matter.

Don't forget the logs, it will show something when or if it happens next .

---

### Post by laserburn2 on 2024-07-07
It happened again and this time I believe I might have found the culprit in the journal:

Jul 07 21:57:44 Kassad systemd[1]: NetworkManager-wait-online.service: Main process exited, code=exited, status=1/FAILURE
Jul 07 21:57:44 Kassad systemd[1]: NetworkManager-wait-online.service: Failed with result 'exit-code'.
Jul 07 21:57:44 Kassad systemd[1]: Failed to start NetworkManager-wait-online.service - Network Manager Wait Online.

From what I've been Googling on this, seems I was originally on the right track thinking it's a tools conflict, NetworkManager and systemd-networkd might have a problem running together. Before I start messing about, I'd like an opinion of someone more familiar with Ubuntu networking.

---

### Post by currentshaft on 2024-07-07
> **laserburn2 said:**
> My guess is that lower and higher level network tools and systems are possibly quarreling among themselves.

Millions of people use Ubuntu daily and do not experience the issue you describe, so unless you've set up the tools to do that on purpose, that is not the cause.

Next step: figure out what "won't connect" means: do you have an IP address, can you resolve DNS, etc?

---

### Post by Doug S on 2024-07-08
Discalimer: I am not a networking expert. I am a server person and do not use NetworkManager.

> **laserburn2 said:**
> From what I've been Googling on this, seems I was originally on the right track thinking it's a tools conflict, NetworkManager and systemd-networkd might have a problem running together. Before I start messing about, I'd like an opinion of someone more familiar with Ubuntu networking.

I thought that it was either one or the other, but not both. The related line from the file posted earlier:

```
doug@s19:~/tmp/tmp/bla$ grep -i networkd output.txt
Jun 26 01:24:34 Kassad systemd[1]: networkd-dispatcher.service - Dispatcher daemon for systemd-networkd was skipped because no trigger condition checks were met.
```

showing that networkd was not started. But don't take my word for it, check (of course, in my case it is running):

```
doug@s19:~/tmp/tmp/bla$ systemctl status systemd-networkd
&#9679; systemd-networkd.service - Network Configuration
     Loaded: loaded (/usr/lib/systemd/system/systemd-networkd.service; enabled; preset: enabled)
     Active: active (running) since Sat 2024-06-29 07:58:56 PDT; 1 week 1 day ago
TriggeredBy: &#9679; systemd-networkd.socket
       Docs: man:systemd-networkd.service(8)
             man:org.freedesktop.network1(5)
   Main PID: 809 (systemd-network)
     Status: "Processing requests..."
      Tasks: 1 (limit: 38229)
   FD Store: 0 (limit: 512)
     Memory: 3.5M (peak: 4.0M)
        CPU: 410ms
     CGroup: /system.slice/systemd-networkd.service
             &#9492;&#9472;809 /usr/lib/systemd/systemd-networkd

Jun 29 07:58:56 s19 systemd-networkd[809]: Enumeration completed
Jun 29 07:58:56 s19 systemd[1]: Started systemd-networkd.service - Network Configuration.
Jun 29 07:58:56 s19 systemd-networkd[809]: enp3s0: Configuring with /run/systemd/network/10-netplan-enp3s0.network.
Jun 29 07:58:56 s19 systemd-networkd[809]: br0: Configuring with /run/systemd/network/10-netplan-br0.network.
Jun 29 07:58:56 s19 systemd-networkd[809]: br0: Link UP
Jun 29 07:58:56 s19 systemd-networkd[809]: enp3s0: Link UP
Jun 29 07:58:59 s19 systemd-networkd[809]: enp3s0: Gained carrier
Jun 29 07:58:59 s19 systemd-networkd[809]: br0: Gained carrier
Jun 29 07:58:59 s19 systemd-networkd[809]: br0: DHCPv4 address 192.168.111.136/24, gateway 192.168.111.1 acquired from 192.168.111.1
Jun 29 07:58:59 s19 systemd-networkd[809]: virbr0: Link UP
```

---

### Post by laserburn2 on 2024-07-08
Seems Doug S was correct in his thoughts. Still don't know how to fix the problem. 

nikola@Kassad:~$ systemctl status systemd-networkd
&#9675; systemd-networkd.service - Network Configuration
     Loaded: loaded (/usr/lib/systemd/system/systemd-networkd.service; disabled; preset: enabled)
     Active: inactive (dead)
TriggeredBy: &#9675; systemd-networkd.socket
       Docs: man:systemd-networkd.service(8)
             man:org.freedesktop.network1(5)
   FD Store: 0 (limit: 512)


nikola@Kassad:~$ journalctl -u systemd-networkd
-- No entries --

---

### Post by #&amp;thj^% on 2024-07-08
Which do you want to use???
```
 systemctl status systemd-networkd
&#9675; systemd-networkd.service - Network Configuration
     Loaded: loaded (/usr/lib/systemd/system/systemd-networkd.service; disabled>
     Active: inactive (dead)
TriggeredBy: &#9675; systemd-networkd.socket
       Docs: man:systemd-networkd.service(8)
             man:org.freedesktop.network1(5)
   FD Store: 0 (limit: 512)

```
Or
```
 systemctl status NetworkManager
&#9679; NetworkManager.service - Network Manager
     Loaded: loaded (/usr/lib/systemd/system/NetworkManager.service; enabled; p>
     Active: active (running) since Mon 2024-07-08 10:12:54 MDT; 17min ago
       Docs: man:NetworkManager(8)
   Main PID: 1871 (NetworkManager)
      Tasks: 4 (limit: 16308)
     Memory: 7.9M (peak: 26.3M)
        CPU: 1.150s
     CGroup: /system.slice/NetworkManager.service
             &#9492;&#9472;1871 /usr/sbin/NetworkManager --no-daemon

Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <info>  [1720455201.1030]>
Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <info>  [1720455201.1036]>
Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <info>  [1720455201.1045]>
Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <info>  [1720455201.1046]>
Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <info>  [1720455201.1371]>
Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <warn>  [1720455201.1392]>
Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <info>  [1720455201.1419]>
Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <info>  [1720455201.1428]>
Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <info>  [1720455201.1429]>
Jul 08 10:13:21 me-Legion-5-zfs NetworkManager[1871]: <info>  [1720455201.1432]>
lines 1-21/21 (END)

```
```
journalctl -u NetworkManager

```

---

### Post by laserburn2 on 2024-07-08
NetworkManager service is up and running. If I'm thinking right, NetworkManager on some occasions for whatever reason decides to wait on systemd-networkd and can't connect? I don't really understand how this works.

I've uploaded the journalctl messages of NetworkManager service from the last problematic boot, maybe someone will understand more why it wouldn't connect. I see that it complains that it can't load the connection profile, but it's not clear why.

---

### Post by #&amp;thj^% on 2024-07-08
Post this back please:
```
systemctl --type=service --state=failed

```

---

### Post by laserburn2 on 2024-07-08
nikola@Kassad:~$ systemctl --type=service --state=failed
  UNIT                      LOAD   ACTIVE SUB    DESCRIPTION                                              
&#9679; apport-autoreport.service loaded failed failed Process error reports when automatic reporting is enabled

Legend: LOAD   &#8594; Reflects whether the unit definition was properly loaded.
        ACTIVE &#8594; The high-level unit activation state, i.e. generalization of SUB.
        SUB    &#8594; The low-level unit activation state, values depend on unit type.

1 loaded units listed.

---

### Post by #&amp;thj^% on 2024-07-08
Lets have a look then at
```
 systemctl status  systemd-networkd-wait-online.service
```

I'm testing your theory with "networkd-wait-online.service"

This really is looking like a bug in NetworkManager though.

---

### Post by laserburn2 on 2024-07-08
In the meantime, I have edited /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf to look like this:

[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma,except:type:ethernet

This should not be necessary, as NetworkManager should always manage ethernet devices without it being mentioned here, but I have ran into this advice in several places, so let's give it a shot in case it is indeed a service conflict.

---

### Post by laserburn2 on 2024-07-08
> **1fallen said:**
> Lets have a look then at
```
 systemctl status  systemd-networkd-wait-online.service
```

I'm testing your theory with "networkd-wait-online.service"

This really is looking like a bug in NetworkManager though.

nikola@Kassad:~$ systemctl status  systemd-networkd-wait-online.service
&#9675; systemd-networkd-wait-online.service - Wait for Network to be Configured
     Loaded: loaded (/usr/lib/systemd/system/systemd-networkd-wait-online.service; disabled; preset: enabled)
     Active: inactive (dead)
       Docs: man:systemd-networkd-wait-online.service(8)

---

### Post by #&amp;thj^% on 2024-07-08
Looks good as far as "networkd-wait-online.service"
I had to edit mine a year back so mine reports (dead) as yours dose, but will show my edit:
```
Loaded: loaded (/usr/lib/systemd/system/systemd-networkd-wait-online.servi>
    Drop-In: /etc/systemd/system/systemd-networkd-wait-online.service.d
            [COLOR="#FF0000"] &#9492;&#9472;override.conf[/COLOR]
     Active: inactive (dead)
       Docs: man:systemd-networkd-wait-online.service(8)
```

This one is a mystery so far.

---

### Post by Doug S on 2024-07-08
As far as I can tell, and from the first posted output.txt file, the failure point is lack of getting an IPV4 IP address from DHCP. The network interface itself comes up just fine. I think, but am not sure, the problem is in the router.

The relevant extractions from the file are:

```
Jun 26 01:24:40 Kassad NetworkManager[1901]: <info>  [1719354280.6877] device (enp4s0): carrier: link connected
Jun 26 01:24:40 Kassad kernel: r8169 0000:04:00.0 enp4s0: Link is Up - 1Gbps/Full - flow control rx/tx
Jun 26 01:24:40 Kassad NetworkManager[1901]: <info>  [1719354280.6885] device (enp4s0): state change: unavailable -> disconnected (reason 'carrier-changed', sys-iface-state: 'managed')
Jun 26 01:24:40 Kassad NetworkManager[1901]: <info>  [1719354280.6899] device (enp4s0): Activation: starting connection 'Profile 1' (2eed1083-9009-4c77-8201-9929bcf1c67b)
Jun 26 01:24:40 Kassad NetworkManager[1901]: <info>  [1719354280.6900] device (enp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jun 26 01:24:40 Kassad NetworkManager[1901]: <info>  [1719354280.6904] device (enp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jun 26 01:24:40 Kassad NetworkManager[1901]: <info>  [1719354280.6926] device (enp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jun 26 01:24:40 Kassad NetworkManager[1901]: <info>  [1719354280.6953] dhcp4 (enp4s0): activation: beginning transaction (timeout in [COLOR="#FF0000"]45[/COLOR] seconds)
Jun 26 01:24:40 Kassad avahi-daemon[1778]: Joining mDNS multicast group on interface enp4s0.IPv6 with address fe80::7d3e:26d9:ee45:89e8.
Jun 26 01:24:40 Kassad avahi-daemon[1778]: New relevant interface enp4s0.IPv6 for mDNS.
Jun 26 [COLOR="#FF0000"]01:24:40[/COLOR] Kassad avahi-daemon[1778]: Registering new address record for fe80::7d3e:26d9:ee45:89e8 on enp4s0.*.
Jun 26 [COLOR="#FF0000"]01:25:26[/COLOR] Kassad NetworkManager[1901]: <info>  [1719354326.0995] device (enp4s0): state change: ip-config -> failed (reason 'ip-config-unavailable', sys-iface-state: 'managed')
Jun 26 01:25:26 Kassad NetworkManager[1901]: <warn>  [1719354326.1001] device (enp4s0): [COLOR="#FF0000"]Activation: failed for connection 'Profile 1'[/COLOR]
Jun 26 01:25:26 Kassad NetworkManager[1901]: <info>  [1719354326.1005] device (enp4s0): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
```

and, where I am assuming the cable was moved in between:

```
Jun 26 01:25:45 Kassad kernel: r8169 0000:04:00.0 enp4s0: Link is Up - 1Gbps/Full - flow control rx/tx
Jun 26 01:25:45 Kassad NetworkManager[1901]: <info>  [1719354345.8783] device (enp4s0): carrier: link connected
Jun 26 01:25:45 Kassad NetworkManager[1901]: <info>  [1719354345.8785] device (enp4s0): state change: unavailable -> disconnected (reason 'carrier-changed', sys-iface-state: 'managed')
Jun 26 01:25:45 Kassad NetworkManager[1901]: <info>  [1719354345.8801] device (enp4s0): Activation: starting connection 'Profile 1' (2eed1083-9009-4c77-8201-9929bcf1c67b)
Jun 26 01:25:45 Kassad NetworkManager[1901]: <info>  [1719354345.8802] device (enp4s0): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
Jun 26 01:25:45 Kassad NetworkManager[1901]: <info>  [1719354345.8807] device (enp4s0): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
Jun 26 01:25:45 Kassad NetworkManager[1901]: <info>  [1719354345.8812] device (enp4s0): state change: config -> ip-config (reason 'none', sys-iface-state: 'managed')
Jun 26 01:25:45 Kassad NetworkManager[1901]: <info>  [1719354345.8819] dhcp4 (enp4s0): activation: beginning transaction (timeout in 45 seconds)
Jun 26 01:25:45 Kassad avahi-daemon[1778]: Joining mDNS multicast group on interface enp4s0.IPv6 with address fe80::7d3e:26d9:ee45:89e8.
Jun 26 01:25:45 Kassad avahi-daemon[1778]: New relevant interface enp4s0.IPv6 for mDNS.
Jun 26 [COLOR="#FF0000"]01:25:45[/COLOR] Kassad avahi-daemon[1778]: Registering new address record for fe80::7d3e:26d9:ee45:89e8 on enp4s0.*.
Jun 26 [COLOR="#FF0000"]01:25:51[/COLOR] Kassad NetworkManager[1901]: <info>  [1719354351.5347] dhcp4 (enp4s0): state changed new lease, address=192.168.1.116, acd pending
Jun 26 01:25:51 Kassad NetworkManager[1901]: <info>  [1719354351.7274] dhcp4 (enp4s0): state changed new lease, address=192.168.1.116
Jun 26 01:25:51 Kassad NetworkManager[1901]: <info>  [1719354351.7281] policy: set 'Profile 1' (enp4s0) as default for IPv4 routing and DNS
Jun 26 01:25:51 Kassad avahi-daemon[1778]: Joining mDNS multicast group on interface enp4s0.IPv4 with address 192.168.1.116.
Jun 26 01:25:51 Kassad avahi-daemon[1778]: New relevant interface enp4s0.IPv4 for mDNS.
Jun 26 01:25:51 Kassad avahi-daemon[1778]: Registering new address record for 192.168.1.116 on enp4s0.IPv4.
Jun 26 01:25:51 Kassad systemd-resolved[1722]: enp4s0: Bus client set search domain list to: router.wind
Jun 26 01:25:51 Kassad systemd-resolved[1722]: enp4s0: Bus client set default route setting: yes
Jun 26 01:25:51 Kassad systemd-resolved[1722]: enp4s0: Bus client set DNS server list to: 192.168.1.254
Jun 26 01:25:51 Kassad NetworkManager[1901]: <info>  [1719354351.7405] device (enp4s0): state change: ip-config -> ip-check (reason 'none', sys-iface-state: 'managed')
Jun 26 01:25:51 Kassad NetworkManager[1901]: <info>  [1719354351.7733] device (enp4s0): state change: ip-check -> secondaries (reason 'none', sys-iface-state: 'managed')
Jun 26 01:25:51 Kassad NetworkManager[1901]: <info>  [1719354351.7735] device (enp4s0): state change: secondaries -> activated (reason 'none', sys-iface-state: 'managed')
Jun 26 01:25:51 Kassad NetworkManager[1901]: <info>  [1719354351.7741] device (enp4s0): [COLOR="#FF0000"]Activation: successful, device activated.[/COLOR]
```

---

### Post by laserburn2 on 2024-07-09
That's a very good eye for details you have, Doug S. The reason why I  suspected that the issue is on Ubuntu side is a strict procedure that  must be followed to restore connection, reboot of router would sometimes  not resolve the problem. But it could indeed be a DHCP problem. 

Sadly,  this meh router does not have many options when it comes to DHCP, I can  only change the lease time or try assigning static IP to my MAC. I  tried the latter and set for my rig the IP that it currently has. If  that doesn't help, I'll put the static IP on the NIC. If that doesn't  help either, it's not DHCP.

---

### Post by laserburn2 on 2024-07-27
Incredible. I've turned off DHCP and set a static IP. I've even reset the router to the factory settings. The problem is still there, with the only difference that now network indicator shows that the network is actually established, when in fact it's not, I can't even ping the router. The only remedy remains as before, unplug the cable and plug it into another port.

The only thing that comes to me to try is when the next time this happens, I will try plugging the Windows laptop in the same port and see if it's the same thing again.

---

### Post by laserburn2 on 2024-08-30
This is definitely a Linux-hating router. It was shut down during the vacation, then when I came back, network wouldn't work on any eth port. In the end, I had to connect Windows laptop to it, unplug and then connect Ubuntu machine to the same port, only after that the Ubuntu could connect normally. I don't even know how that is possible.

---

### Post by laserburn2 on 2024-10-28
What seems to have solved it was updating the PC motherboard firmware. :-s No problems for two whole months.

---

### Post by Doug S on 2024-10-28
> **laserburn2 said:**
> What seems to have solved it was updating the PC motherboard firmware. :-s No problems for two whole months.Thanks for the update post. It is nice to know how it played out in the end.

---

