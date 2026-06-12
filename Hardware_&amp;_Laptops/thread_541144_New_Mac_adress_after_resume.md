---
title: "New Mac adress after resume"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by bmhm on 2007-09-02
[FONT="Verdana"]Hi, 

I don't think it belongs directly to this: [http://ubuntuforums.org/showthread.php?t=45266&page=2](http://ubuntuforums.org/showthread.php?t=45266&page=2)

Ok, the matter: I can shut down my PC and start it - everything's fine. Mac Adress stays the same all the time.

Now, when I hibernate or suspend, I got another Mac adress after resuming. Also, the card's name is now eth1, not eth0. eth0 is *dead* from then on.

It's really ugly, because my port forwardings won't work anymore since I get a new IP adress from my router (AVM Fritz!Box 70xx).

Also, my fritz!box never displays the computer's name, only when the connected client is a windows client.

Any ideas? Some module to forcefully unload/reload?

lspci says:
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3) 
it's an nforce4 ultra chipset with onboard gigabit ethernet.

Thanks in advance![/FONT]

---

### Post by eggdeng on 2007-09-02
Sorry if I'm asking a stupid question but are you sure you mean Mac address (the one ifconfig reports as HWaddr) and not IP address?

---

### Post by bmhm on 2007-09-03
> **eggdeng said:**
> Sorry if I'm asking a stupid question but are you sure you mean Mac address (the one ifconfig reports as HWaddr) and not IP address?

[FONT="Verdana"]Yes, and I AM serious.
ifconfig shows me, eth0 is still there, but all the connection now is managed by eth1 (which didn't exist before).
Also, eth0 and eth1 have different MAC adresses - but yes, I only have one networking card.

And my router (Fritz!Box) shows a new network card with exactly this new adress - and that's why it gets a new IP.

Yes, same card, new MAC and therefore new IP.[/FONT]

---

### Post by dgowilliams on 2007-09-12
Same problem here!  Check this out.  I typed ifconfig before suspend.  I typed ifconfig after suspend:

> davidf@williams:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:**:**:6D:30  
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fef1:6d30/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150735 (147.2 KiB)  TX bytes:18145 (17.7 KiB)
          Interrupt:17 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

davidf@williams:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 30:6D:**:**:19:00  
          inet addr:192.168.1.144  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::326d:f1ff:fe21:1900/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1764 (1.7 KiB)  TX bytes:4159 (4.0 KiB)
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

davidf@williams:~$ 



The MAC problem looks like a some sort of front to back translation issue...

I too have an nVidia onboard controller:

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)

with nForce chipset.


Anyone have any ideas?  Thanks in advance :o)

David Williams

Ubuntu 7.10  2.6.20-16-generic

---

### Post by ThrashJazzAssassin on 2007-10-21
anyone managed to figure this out yet?

---

### Post by tylerious on 2007-10-22
I have the same problem and am also using an onboard nvidia ethernet device with nvidia chipset.

If I suspend/wake up several times, I keep getting new MAC/IP addresses. Since my school network is set up to only allow internet access to certain MAC addresses, I would need to re-register my new MAC address after every suspend!

I've tried to set up my card manually with static IP and DHCP - neither works, but I get "eth0:avah" when I do "ifconfig".

Is this a bug in Gutsy?

---

### Post by junkdan on 2007-10-22
Hi. I see an old forcedeth bug about the MAC address being reversed for certain nvidia controllers. This is _exactly_ what I see here -- my MAC is reversed after resume. Maybe we need to reload a network module or something after suspend?

[http://mandrivausers.org/lofiversion/index.php/t39208.html](http://mandrivausers.org/lofiversion/index.php/t39208.html)

> Actually some nforce based mb's seem to give the mac address in reverse order, and forcedeth.c sputters, and udev allocates a bogus mac address.

This is all fixed in latest forcedeth.c (0.60 at time of writing, fix went first to 0.57). Installing for instance one of the later kernel-tmb's fixes this problem.
It would be nice to have it backported though, like they did for Ubuntu: see [https://bugs.launchpad.net/ubuntu/+source/l...6.15/+bug/76346](https://bugs.launchpad.net/ubuntu/+source/l...6.15/+bug/76346)

---

### Post by tylerious on 2007-10-22
Not sure if this is the forcedeth bug. I have version 0.60 and instead of getting a backwards MAC address, I got numerous random MAC addresses.

Anyways, I think I may have it working! What I did:

First of all, I got rid of the network-manager package. That "roaming mode" thing is most of the problem, I think.
*sudo apt-get autoremove network-manager*

My /etc/network/interfaces reads:
[I]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp[/I]

My /etc/default/acpi-support does NOT contain the line:
*STOP_SERVICES="networking"*
instead, it reads the default:
*STOP_SERVICES=""*

I hope it keeps working; otherwise I'll post with more information. I hope this helps anybody else getting this problem.

---

### Post by junkdan on 2007-10-22
> **tylerious said:**
> Not sure if this is the forcedeth bug. I have version 0.60 and instead of getting a backwards MAC address, I got numerous random MAC addresses.

Yes. In dmesg, you'll see a log like this:
> 
[    8.345351] 0000:00:14.0: Invalid Mac address detected: ff:ff:ff:d3:16:00
[    8.345410] Please complain to your hardware vendor. Switching to a random
MAC.
[    8.706062] eth0: forcedeth.c: subsystem: 0103c:30b5 bound to 0000:00:14.0


The first line is my Mac address backwards. And, I also have forcedeth 0.60 installed.

---

