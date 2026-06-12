---
title: "Need help picking hardware for 24/7 server use."
date: 2019-08-29
forum: Hardware
---

### Post by Tadaen_Sylvermane on 2019-08-29
I am at a loss here. I can't find any stats on low power usage. I'm looking to build a dedicated server for my home and switch my current server / htpc to a pxe booted media center. As such I need a new main file  / network server. 99% of my use is light network stuff. Dhcp, dns, print server (2 printers, they get used once or twice a month at most), transmission server, apt caching proxy, mariadb (total of 5-6 devices being served at a time), a single minecraft server (2 users tops at any given time), mythtv backend for a max of 2 users at a given time, and a pxe installer server which would get used very rarely (more for my own convenience). The only strenuous thing it will need to do is build a single LTSP image monthly roughly as that is how often I update. The rest is just file serving. NFS mainly, a little bit of samba. Never more than 5-6 devices at a time.

My storage plan is 4x 2tb drives, 3 pooled with Mergerfs. One functioning as Snapraid parity. The majority of my stuff is media so no need for a full raid set up imho. OS will be on an SSD. I plan on running my services above in LXD containers except for LTSP, unsure how to do that as it needs to be privileged.

My current htpc / server is idling right now at 5% cpu usage, AMD quad core AM1 socket Kabini. I know I don't need much to do what I need. Even when both logged into Minecraft we max at 30-40% cpu.

What is a good low power chip / mobo combo that will keep my power bill down yet still easily do what I need? Would prefer Intel although I am open to AMD. Plan is Ubuntu LTS, and nothing else.

*EDIT* Another option I have is to use my current hTPC hardware and just add a Sata card for more ports, but then I would need to come up with a cheap pxe bootable hdmi output capable machine for my living room media center. Either one would be helpful.

---

### Post by SeijiSensei on 2019-08-29
I run a Dell Poweredge T30 on my home network with three additional drives.  It's connected to an APC UPS that reports its load average is 0.0%.

A quick search online turned up this review:

> The primary advantage this server offers over more powerful and redundant alternatives is really frugal power usage.  Two of the three servers I&#8217;ll be running are shown in this photo, and the total draw for everything (firewall, Ethernet switches, two servers, WiFi access point powered by PoE) is ninety watts.  The servers are at idle, but the UPS in the photo thinks it can run everything shown here for 120 minutes, which gives me plenty of time to pull out the generator and power it up if power fails.  If my UPS runs these servers for half that amount of time I&#8217;ll be thrilled.

Another way to phrase this: electricity where I live is pretty inexpensive, but my Kill A Watt meter tells me the Dell T30 will only cost me $24 per year in power annually.  That&#8217;s impressive, even when the numbers represent the machine running at idle.

[https://www.derekzeanah.com/2018/03/16/dell-t30-overview-review/](https://www.derekzeanah.com/2018/03/16/dell-t30-overview-review/)

I bought mine for $300, or about half the list price, when a third-party distributor had a bunch to sell at NewEgg.  However Dell currently offers this for $299 with a coupon code: [https://www.dell.com/en-us/work/shop/cty/pdp/spd/poweredge-t30/pe_t30_12084](https://www.dell.com/en-us/work/shop/cty/pdp/spd/poweredge-t30/pe_t30_12084). I think it's a great deal at that price.  It's incredibly quiet as well, a welcome relief after replacing a decade-old server that made a lot of noise.

My APC [Back-UPS XS 1300]("https://www.amazon.com/APC-Battery-Protector-BackUPS-BX1350M/dp/B06WD82BM8/") estimates it can run this with a monitor and a couple of routers attached for 130 minutes.  top reports load averages for the server of less than 0.10.  It's mostly used for data storage though I do run a mail server, a BIND name server, and a PostgreSQL server on it as well.  It's also the local endpoint for an OpenVPN network of virtual machines in the cloud at Linode.

---

### Post by TheFu on 2019-08-29
What do you mean by "low power"?  Is 10W low power?  40W?  70W?  200W?
Do you have a UPS?
By saying "server" and implying that is a HW requirement, do you want dual or triple power supplies?

I wouldn't use Mergerfs.  LVM can merge PVs on different disks into a single VG and you can setup LVs as needed without regard.  Enterprise storage techniques.  If you do merge multiple disks into a single LV, be certain your backups can deal with that size.  I think all media servers will easily merge multiple disk storage into a single DB view, so there's no need to merge storage into a single file system.  I know plex and kodi do that. It is trivial.

If you are in the 65W range, it is amazing what a Ryzen 5 CPU can do.  11K passmarks for $80 and 65W peak is pretty amazing.

There are also higher-end ARM systems that can almost handle everything you seek for about $100 all-in.  Check out the Odroid-N2 or Pine64Pro - both have real GigE, USB3 and perhaps SATA3 ports ( I don't remember ).  They address most of the issues with the Raspberry Pi-type SBCs.  [https://ameridroid.com/collections/single-board-computer](https://ameridroid.com/collections/single-board-computer) shows some options an pricing.

---

### Post by Tadaen_Sylvermane on 2019-08-30
Meant low power as in usage. I'm worried about my environmental impact, while still wanting my services available without messing about. Yes I have a UPS. I call it a server, but it's just a home server and that may be the wrong word for it. Consumer hardware is where I'm heading as I have nowhere to put a loud enterprise grade machine, although that would be the case if possible. This will sit in my kitchen above the refrigerator in a ventilated cabinet. I'm not looking for maximum performance. Just enough to run the few services I have without wrecking my electric bill.

I've eliminated MergerFS as I'm currently only running a single 2tb drive for media storage. MergerFS was more of a test that I just left in place. I originally planned on expanding my storage with MergerFS as 99.9% of my stuff is media, so the higher IO of raid wasn't necessary. I had semi backups of my media with Snapraid. I know that isn't a true backup, but for my purposes worst case I can just re-rip everything. Snapraid would save that process. However for storage on the new machine I'm thinking 3 4tb drives in Raidz1. It's taken us 4 years to fill 80% of this 2tb drive, and it's slowing as we are finding that we now already own so many movies we rarely find them anymore to add to the collection save for new releases.

The machine currently running all of my services + living room htpc / kodi is a 25w tdp AMD chip AM1 socket. I've been flirting with just upgrading the case / psu / storage for this hardware. Seems to be the most economical way right now. And this machine barely costs us 2-3 US a month under our usual load according to my KillAWatt.

---

### Post by CatKiller on 2019-08-30
Unless you terribly enjoy managing servers (which TheFu totally does, and more power to him) your storage needs would probably be handled fine by a Synology box somewhere, and your playback needs by something really tiny. There are a bunch of options for low-power ARM things with hardware accelerated video playback, and some of the Synology machines can do transcoding as necessary. 

I ran a Minecraft server on a Raspberry Pi 3 for a while, and it was just about adequate for a handful of players; a Pi 4 would probably handle it fine, or one of the beefier tiny computers that TheFu has already mentioned. In my case I upgraded to a NUC so that I could combine HTPC, Minecraft servers, SteamLink and light gaming into one small machine.

---

### Post by TheFu on 2019-08-31
I have a combined storage/nfs/plex/calibre "server" with a Pentium G3258 CPU.  It has about 32TB of storage connected now, 16TB useable, since 50% is an rsync copy for backups.  The "server" was built reusing old stuff. Only 3 things were new, before I started adding disks over time.
Total cost new was $126. That was about 5 yrs ago.  A similar system can be built today with about 3x the CPU capability for the same price, I'd guess.
[LIST]
[*]G3258 CPU (65W max) w/ iGPU
[*]miniATX MB
[*]8G DDR3 RAM
[/LIST]
Reused an ATX case, bronse-PSU, initial 4TB HDD.  Hooked it up to my KVM for video, keyboard, mouse and all the different playback devices in the house can use it.

There are times when I could use a little faster CPU to do on-the-fly transcoding for cheap playback devices that only support h.264 video.

Over the years, 2 HDDs in that machine have failed, so I don't ever expect not to backup the files.  Re-ripping the disks is worth the cost of the extra storage to me after I calculated the time involved.  It is on, 24/7/365.  

The plex server is never accessed locally, only from DLNA clients or through the plex web app. I don't have a plex account and never used the plex clients for ARM or PCs or tablets. I find them ugly and slow.

Anyway, if size is the primary concern, expect to pay $100 for similar initial capabilities, but be stuck when/if more storage is desired.  While a fast CPU isn't necessary to handle transcoding for limited playback devices, if you go too slow, you might wish a different choice had been made later.

My playback devices are $50 tablets, a roku and $40 RaspberryPis - have a  v2 and a v3 connected to the network.  The way I see it, I can have a slightly beefier "server" that can handle transcoding and cheap playback devices, or I can have dumb storage and playback devices that cost 3x more each.

Plex estimates 3,000 passmarks for every stream to be transcoded as a rough guess. That doesn't handle UHD content, however.

---

### Post by Tadaen_Sylvermane on 2019-08-31
In my case Kodi is my only access, which is on every device in the house. So no transcoding, just nfs file shares.

---

### Post by Tadaen_Sylvermane on 2019-09-01
I have decided after reading this thread that as my primary goal is more storage as well as my current hardware already doing what I need and then some that a NAS is likely the best idea for me. I've figured that to upgrade my current case / psu would cost roughly as much as a Synology box just to get more space for 2 hard drive spaces. Just add a few drives and away I go. I still need to find if it can share over NFS. As I've already got a local DNS server it is trivial at best for me to change the NAS to my storage ip for Kodi, while changing my current HTPC / Server IP to something else without losing my Kodi DB's as kodi mounts shares via ip rather than fqdn. I can dedicate the existing 2tb drive in the server to mythtv, everything else will get rolled over to the nas. This will allow me to eliminate mergerfs completely from my future, as well as snapraid. Marginal work for major benefits.

---

### Post by CatKiller on 2019-09-01
> **Tadaen_Sylvermane said:**
> I've figured that to upgrade my current case / psu would cost roughly as much as a Synology box just to get more space for 2 hard drive spaces. Just add a few drives and away I go. I still need to find if it can share over NFS.

Yeah, that's why I suggested it: you can't really find a case that's as small/nice/effective as the Synology box for the price, and it is really easy to use. You can share over NFS; that's how I use it from my static computers. Plus there's SMB/AFP/FTP if you want those. It shares media by DLNA for my mobile computers, and has a torrent client. There's packages available for a bunch of stuff that I don't personally use: mail servers, or PXE servers, or wikis; all sorts. There's a list of them [here](https://www.synology.com/en-uk/dsm/packages), if you're interested. I did spot MariaDB on there, which isn't something I'm interested in but was something that you said you were. I also saw that there are some [community packages](https://github.com/colin1497/Synology-Install-Package-for-Minecraft-and-Craftbukkit) for installing a Minecraft server on a Synology, but I've never tried them.

If you want to DIY you can go bigger for cheaper or the same size for more expensive, but if you just want an appliance that sits there quietly doing its thing it's the best option I'm aware of.

---

