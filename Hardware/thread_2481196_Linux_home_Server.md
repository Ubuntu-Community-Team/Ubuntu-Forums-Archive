---
title: "Linux home Server"
date: 2022-11-21
forum: Hardware
---

### Post by wp.rauchholz on 2022-11-21
Hello community,

I want to setup a home server with the following functionality; web server, email server, media server (emby) and file server (mainly to backup family stuff). The server will be modem/router of the home network (router from telecom company will be configured in bridge mode) and have the firewall.
What kind of hardware does the community recommend? I don't look necessarily for the cheapest possible hardware. I am looking for reliability, energy efficiency and robustness.



Thanks, Wolfgang

---

### Post by Tadaen_Sylvermane on 2022-11-21
It's difficult to measure that for many, myself included. What I can do however is give you this and tell you what I'm running with plenty of free muscle available.

```
[FONT=monospace][COLOR=#5454ff]**System:    Kernel:**[/COLOR][COLOR=#000000] 5.10.0-19-amd64 x86_64 [/COLOR][COLOR=#5454ff]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454ff]**Console:**[/COLOR][COLOR=#000000] tty 0 [/COLOR][COLOR=#5454ff]**Distro:**[/COLOR][COLOR=#000000] Debian GNU/Linux 11 (bullseye)  [/COLOR]
[COLOR=#5454ff]**Machine:   Type:**[/COLOR][COLOR=#000000] Server [/COLOR][COLOR=#5454ff]**System:**[/COLOR][COLOR=#000000] Intel [/COLOR][COLOR=#5454ff]**product:**[/COLOR][COLOR=#000000] S1200BTL [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] .................... [/COLOR][COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**Mobo:**[/COLOR][COLOR=#000000] Intel [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] S1200BTL [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] E98681-352 [/COLOR][COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#5454ff]**BIOS:**[/COLOR][COLOR=#000000] Intel [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] S1200BT.86B.02.01.0044.072520181346  [/COLOR]
           [COLOR=#5454ff]**date:**[/COLOR][COLOR=#000000] 07/25/2018  [/COLOR]
[COLOR=#5454ff]**CPU:       Info:**[/COLOR][COLOR=#000000] Quad Core [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] Intel Xeon E31225 [/COLOR][COLOR=#5454ff]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] MCP [/COLOR][COLOR=#5454ff]**L2 cache:**[/COLOR][COLOR=#000000] 6 MiB  [/COLOR]
           [COLOR=#5454ff]**Speed:**[/COLOR][COLOR=#000000] 1863 MHz [/COLOR][COLOR=#5454ff]**min/max:**[/COLOR][COLOR=#000000] 1600/3400 MHz [/COLOR][COLOR=#5454ff]**Core speeds (MHz):**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**1:**[/COLOR][COLOR=#000000] 1863 [/COLOR][COLOR=#5454ff]**2:**[/COLOR][COLOR=#000000] 1689 [/COLOR][COLOR=#5454ff]**3:**[/COLOR][COLOR=#000000] 2247 [/COLOR][COLOR=#5454ff]**4:**[/COLOR][COLOR=#000000] 2349  [/COLOR]
[COLOR=#5454ff]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] NVIDIA GT218 [GeForce 210] [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] nouveau [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#5454ff]**Display:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**server:**[/COLOR][COLOR=#000000] No display server data found. Headless machine? [/COLOR][COLOR=#5454ff]**tty:**[/COLOR][COLOR=#000000] 236x57  [/COLOR]
           [COLOR=#5454ff]**Message:**[/COLOR][COLOR=#000000] Advanced graphics data unavailable in console for root.  [/COLOR]
[COLOR=#5454ff]**Audio:     Device-1:**[/COLOR][COLOR=#000000] NVIDIA High Definition Audio [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] Creative Labs CA0106/CA0111 [SB Live!/Audigy/X-Fi Series] [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_ca0106  [/COLOR]
           [COLOR=#5454ff]**Sound Server:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] k5.10.0-19-amd64  [/COLOR]
[COLOR=#5454ff]**Network:   Device-1:**[/COLOR][COLOR=#000000] Intel 82579LM Gigabit Network [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] e1000e  [/COLOR]
           [COLOR=#5454ff]**IF:**[/COLOR][COLOR=#000000] eno1 [/COLOR][COLOR=#5454ff]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#5454ff]**speed:**[/COLOR][COLOR=#000000] 1000 Mbps [/COLOR][COLOR=#5454ff]**duplex:**[/COLOR][COLOR=#000000] full [/COLOR][COLOR=#5454ff]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] Intel 82574L Gigabit Network [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] e1000e  [/COLOR]
           [COLOR=#5454ff]**IF:**[/COLOR][COLOR=#000000] enp4s0 [/COLOR][COLOR=#5454ff]**state:**[/COLOR][COLOR=#000000] down [/COLOR][COLOR=#5454ff]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**IF-ID-1:**[/COLOR][COLOR=#000000] br0 [/COLOR][COLOR=#5454ff]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#5454ff]**speed:**[/COLOR][COLOR=#000000] 1000 Mbps [/COLOR][COLOR=#5454ff]**duplex:**[/COLOR][COLOR=#000000] unknown [/COLOR][COLOR=#5454ff]**mac:**[/COLOR][COLOR=#000000] <filter> 
```

Got the machine for 80 bucks with only a single 1tb hdd at the time. It's running 5 right now, 2 raid 1's with an lvm volume across them and then an os ssd.

I run daily with little to no hiccups...

Mythtv backend, 2 minecraft servers, dnsmasq, nfs, samba, minidlna, ampache, jellyfin, ltsp for a couple clients, squid for http proxy (apt packages mainly), mumble server for lan, print server via cups, and mariadb. The majority of these are running in docker.

It's a low end 2nd or 3rd gen Xeon with 16gb ecc. 

Very out of date but hums along just fine out in the workshop, and has for the past 4 years since I bought it.
[/COLOR]
[/FONT]

---

### Post by ian-weisser on 2022-11-21
> **wp.rauchholz said:**
> The server will be modem/router of the home network

Many of us have tried that.

Problem: If your server crashes, you lose your LAN and your network connection. It can be MUCH harder to fix a problem without convenient internet access to do a bit of googling.

---

### Post by mIk3_08 on 2022-11-22
> **ian-weisser said:**
> Many of us have been tried that.
Problem: If your server crashes, you lose your LAN and your network connection. It can be MUCH harder to fix a problem without convenient internet access to do a bit of googling. Yes, I agree with ian-weisser. You should have a secured home network configurations. Just to be safe. But if you are wise enough to do it. It can be so easy then. server configurations is easy but to be safe is NOT. Regards and cheers.

---

### Post by wp.rauchholz on 2022-11-24
Thanks for the advise. Will go shipping now.
And I promise I will give it a 2nd thought on modem/router config.

Thanks, Wolfgang

---

### Post by TheFu on 2022-11-24
> **wp.rauchholz said:**
> Hello community,

I want to setup a home server with the following functionality; web server, email server, media server (emby) and file server (mainly to backup family stuff). The server will be modem/router of the home network (router from telecom company will be configured in bridge mode) and have the firewall.
What kind of hardware does the community recommend? I don't look necessarily for the cheapest possible hardware. I am looking for reliability, energy efficiency and robustness.

It is your network and your responsibility.  A few thoughts from my 25+ yrs as a Unix/Linux admin, systems architect and security guy:
* Keep the WAN router as separate hardware.  I have a PCEngines APU2 running OPNSense for this.  Routers, especially, small business/home versions, have holes in them during reboot before all the software is up and running, but routing is still working.  So, for 10 seconds after any reboot, there's effectively no firewall at all. Beware.
* I have an email gateway system that is on a different subnet with a web reverse-proxy server. These are high-risk systems and shouldn't be anywhere near the real servers or desktops or any wifi network.
* Treat all IoS devices as enemy servers. Put them outside your WAN router, connected directly to the ISP's router.  Thermostats, cleaning machines, coffee makers, security cameras, streaming devices ... all need to be outside, untrusted.
* That goes for all wifi devices too.  Wifi is never to be trusted without running a full VPN.  I have very good reasons for this recommendation, beyond the FBI recommending it.
* Each service you want to run needs to be put into a Linux Container (perhaps lxd) or a full virtual machine.  There are security and management reasons for this. Software used in these different projects have specific software stacks that will quickly have conflicts. Best to keep them separate, even if their software stacks are compatible today. In a year, they won't be.
* If you aren't already running email professionally, I wouldn't suggest it for anyone at home.  I've been running email servers for work and myself since the mid-1990s. It isn't the same anymore.  Plus, all residential ISPs will block this, so it won't work.
* Keep internet email and websites in different VMs.  Keep desktops on different subnets than any internet facing servers.

So, with all that, I think you need these networks internal:
* Untrusted wifi (tablets/phones/IoS (all wifi is untrusted)
* IoS/IoT  wired - all untrusted / gaming systems, security cams.
* High risk internet-facing servers (vpn, email gateway and web reverse-proxy)
* Lower risk servers (DNS, DHCP, email, internal LAN, and limited internet read-only access)
* Trusted Desktops

So, each of those bullet points needs to be on separate subnets with a firewall controlling access into and between them all. You could put another OPNSense router into a VM to control the access between subnets inside.

All email in and out from the email server would traverse through the email gateway.  It is smart to place this gateway at a hosting provider setup for store and forward, so when you ISP connection is down, emails still are delivered and you'll get them eventually, but most of the time, no data would exist on that email gateway.  I run my email gateway inside an LXD container.  Initially, my filters were blocking about 95% of all messages. They kept coming from the same places, so I setup an ipset to block those networks and now less than 10% of messages are bounced by postfix according to pflogsumm   <--- gotta love than name! pf-log-summ 
```
Grand Totals
------------
messages

    142   received
    276   delivered
      0   forwarded
      1   deferred  (3  deferrals)
     12   bounced
     11   rejected (3%)
      0   reject warnings
      0   held
      0   discarded (0%)
```

Of course, if you want to host internal-only websites, like a nextcloud server, then the security doesn't matter too much. To access nextcloud when away from home, you'll need to run a VPN server at home ... which has to be either on separate hardware (don't put it in the router) or in a separate VM.  Running a VPN server inside a Linux container can't be done without drastically harming security for all containers on the same system and the host OS.  Just don't do it.  I'd suggest getting ssh and wireguard working from the outside to provide access internal when you are away.  Wireguard has clients for tablets and phones, so accessing your internal servers when traveling will be really easy, assuming you setup the DNS and subnets correctly.  Use 'odd' subnets for everything you can.  Avoid 192.168.1.x/24, 192.168.0.x/24, 10.1.10.x/24 and 172.16.x.x anything.  You'll thank me later.  Routing works by having different subnets between where you are and where you want to be. If those ever match, you'll not be able to get there.  So, if the cafe you are in has you on 192.168.1.240/24 and your home subnet is 192.168.1.x/24, those are the same and you can't get there.  They must be different to work.  I use 10.1.10.1/24 for IoT/IoS and wifi stuff outside my network and the internal subnets are in the 172.20.x.x-172.22.x.x areas. It has worked well. Hardly anyone uses 172.16.x.x - 172.32.x.x, so picking any LAN subnets in those ranges has never caused any collisions.  10.x.x.x can be used too, but be certain to use odd networks to avoid collisions.

BTW, you'll need an internal DNS server and want to use static IPs for any systems that run network services.  The DNS is necessary since some devices and browsers will ignore the /etc/hosts files and only use DNS answers for lookups - I'm looking at nearly all google products.  If you are running a DNS anyway, why not run some domain blocking too?  A pi-hole running in an LXD container easily handles both.

I'm all about self-hosting stuff, but within a secure architecture to provide layers of security so when we get 1 thing wrong, our entire network doesn't get pwn'd in 5 minutes.  

for backups, use real client/server backup tools and have the backup server "pull" the backups. No clients should have direct access to the storage, unless you want the malware on them to encrypt all the backup files too.  Shared storage and backups don't mix.  'rdiff-backup' over ssh supports "pulled" backups for Unix-like OSes. It is efficient for storage and maintains versions for not just the data, but for the ACLs, permissions, owners, and xattrs too.  All of these are necessary to restore correctly.  

For Windows backups, I don't keep any important files on them. They write to a small CIFS area just for their needs which gets backed up on the Linux side. We barely use MS-Windows anymore - just for financial stuff at this point. I have a Windows VM that gets cloned each month as a backup of the OS.  The financial files are immediately cloned to 2 storage locations when I finish with bi-weekly updates or during tax season. The Windows VM is seldom powered on.  If I had a house full of Windows computers, I'd look for something like [http://www.amanda.org/](http://www.amanda.org/) to pull the backups.  Amanda requires an agent installed on each client machine.  I think BackupPC is similar.  I tested rdiff-backup on Windows and was disappointed mainly due to Windows lacking ssh support at the time of the testing. Perhaps it is better now?

If you want energy efficiency, that's not server hardware.  The energy efficient servers aren't suitable for some media center needs like transcoding on the fly content for different client requirements.  OTOH, all desktop hardware can have problems from time to time and most home's don't have redundant power circuits to a single room, so there is little to be gained by having a server with redundant power anyway.  I have a couple 6-core Ryzen 5 systems. Either one could run all the VMs, except one doesn't have enough network ports to support all the PCI passthru needs for each NIC.  It is a security thing for any internet traffic.  Within the different LANs, I use physically separate networks. VLANs are a bit of a security risk, since client machines can see all the other VLAN traffic on the same wire.  VLANs are like sharing a multilane highway.  If everyone stays in their lane, everything is fine, but sometimes we can change lanes or be in multiple lanes at the same time.  VLANs are logical "suggestions", not real security.  If you use managed switches on each end of the wire runs, then much of that risk is mitigated, since the edge switch would only provide traffic meant for the specific device, but managed switched double (or more) the cost in network equipment.

I'm probably babbling at this point.

You might find [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign) interesting.
And [https://www.howtoforge.com/tutorial/perfect-server-ubuntu-20.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/](https://www.howtoforge.com/tutorial/perfect-server-ubuntu-20.04-with-apache-php-myqsl-pureftpd-bind-postfix-doveot-and-ispconfig/) ... though please don't run any plain FTP server in 2022!  Security nightmare and Bind should probably be left to the professionals.  In 2002, my Bind server was hacked. Since then, I've paid others to provide DNS for my internet stuff and use a light DNS for internal needs.

---

