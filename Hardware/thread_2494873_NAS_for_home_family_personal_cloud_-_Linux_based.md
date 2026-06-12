---
title: "NAS for home family personal cloud - Linux based"
date: 2024-01-29
forum: Hardware
---

### Post by makem2 on 2024-01-29
I have been using a Pi 4 with a couple of 1TB HDs and need more power.

Can anyone suggest where to start looking as I have no knowledge of NAS. Perhaps a couple of recommended NAS which I can compare to get an idea of what is involved?

I had a desktop computer built recently to my spec and I am wondering if anyone has come across a NAS builder?

Just general pointers, things to look for and things to avoid would be of great help.

TIA

---

### Post by TheFu on 2024-01-30
I don't understand.  NAS isn't anything special, just a Linux system with the number of disks you want (DAS - _d_irectly _a_ttached _s_torage), then run an NFS server on it for other systems to access.

And though NFS is the native way for Unix-like OSes, some people, I hear, still have that *other OS* on their network. If it, you can setup a samba server too, though it should be used only for the *other OS* which will remain nameless. ;)

Or did you want some specialized software that takes over the entire system so using it for other stuff isn't trivial? Something like TrueNAS?  Meh.  Any recently modern CPU in the last decade to easily handle 20 major services/tasks. Why limit them to just being a "NAS"?

Any Linux Desktop/Server distro can be a NAS.

My "NAS" is also a VM host, Linux Container host, jellyfin server, music server, transcoder, TV recorder, Calibre Server ... and that doesn't could what the VMs and Containers do.

In general, a NAS shouldn't use USB connected storage. The protocols used by USB storage aren't the same as SATA/SAS protocols. The connections aren't as solid either.  USB storage is fine for backups, but not for a NAS.

And it should go without saying, if you do need USB storage, always buy USB storage with external power, not just powered over the USB port.  This should be obvious, but perhaps it isn't?

If your system is a mid-tower or larger, you can buy a hot-swap cage for $30-$50 that will use 3 of the 5.25 storage bays in the case and provide (4) 3.5in HDDs with cooling, power, and data connections.  Most motherboards have 4 or 6 SATA ports internally, but adding a $40 4-port SATA PCIe card will make those accessible without touching the internal SATA ports.
Here's an example, cheap, internal drive cage: [https://www.amazon.com/fairdog-Upgraded-Mounting-Dedicated-Enclosure/dp/B0BK8Q8SJX/](https://www.amazon.com/fairdog-Upgraded-Mounting-Dedicated-Enclosure/dp/B0BK8Q8SJX/)  I use different models, but they are out of stock currently.  That link is for a 5-drive cage.
If you add a SATA PCIe card, be certain it supports linux in the kernel. You don't want any drivers. Also, verify that all ports are enabled, not some stupid rule that only 2 can be used, and verify that it is SATA3, not SATA1 or 2.   Or you can add a SAS controller with 2 ports and use a 4-to-1 SATA-to-SAS cable to connect 8 HDDs to it.  Look for an LSI controller. No need for RAID, since you don't need RAID ... or if you do want it, you'll use Linux software RAID (extremely flexible).

Any specific questions?

---

### Post by makem2 on 2024-01-30
> **TheFu said:**
> I don't understand.  NAS isn't anything special, just a Linux system with the number of disks you want (DAS - _d_irectly _a_ttached _s_torage), then run an NFS server on it for other systems to access.

And though NFS is the native way for Unix-like OSes, some people, I hear, still have that *other OS* on their network. If it, you can setup a samba server too, though it should be used only for the *other OS* which will remain nameless. ;)

Or did you want some specialized software that takes over the entire system so using it for other stuff isn't trivial? Something like TrueNAS?  Meh.  Any recently modern CPU in the last decade to easily handle 20 major services/tasks. Why limit them to just being a "NAS"?

Any Linux Desktop/Server distro can be a NAS.

My "NAS" is also a VM host, Linux Container host, jellyfin server, music server, transcoder, TV recorder, Calibre Server ... and that doesn't could what the VMs and Containers do.

In general, a NAS shouldn't use USB connected storage. The protocols used by USB storage aren't the same as SATA/SAS protocols. The connections aren't as solid either.  USB storage is fine for backups, but not for a NAS.

And it should go without saying, if you do need USB storage, always buy USB storage with external power, not just powered over the USB port.  This should be obvious, but perhaps it isn't?

If your system is a mid-tower or larger, you can buy a hot-swap cage for $30-$50 that will use 3 of the 5.25 storage bays in the case and provide (4) 3.5in HDDs with cooling, power, and data connections.  Most motherboards have 4 or 6 SATA ports internally, but adding a $40 4-port SATA PCIe card will make those accessible without touching the internal SATA ports.
Here's an example, cheap, internal drive cage: [https://www.amazon.com/fairdog-Upgraded-Mounting-Dedicated-Enclosure/dp/B0BK8Q8SJX/](https://www.amazon.com/fairdog-Upgraded-Mounting-Dedicated-Enclosure/dp/B0BK8Q8SJX/)  I use different models, but they are out of stock currently.  That link is for a 5-drive cage.
If you add a SATA PCIe card, be certain it supports linux in the kernel. You don't want any drivers. Also, verify that all ports are enabled, not some stupid rule that only 2 can be used, and verify that it is SATA3, not SATA1 or 2.   Or you can add a SAS controller with 2 ports and use a 4-to-1 SATA-to-SAS cable to connect 8 HDDs to it.  Look for an LSI controller. No need for RAID, since you don't need RAID ... or if you do want it, you'll use Linux software RAID (extremely flexible).

Any specific questions?

Brilliant man! Just the sort of information I look for :)

In view of your input I should state the use the 'NAS' will be put to. It is very minor.

I and my wife have three mobile phones, Samsung and 2 x iPhone. We both have identical Samsung travel laptops, both dual boot Ubuntu and that 'other OS'. I have a desktop dual boot desktop PC, Ubuntu and the other. We have visitors with a variety mobile phones. I only use the 'other OS' if I have to, for infrequent gaming with children and grandchildren.

My aim is to have something which uses as little power as possible whilst running 24/7, that can be shut down and not interfere with other hardware in use when in-active. Something which will allow easy file sharing across the LAN when active but not WAN enabled. I also backup my PC and both laptops to the 'NAS' using rsync on a regular basis. The Pi used headless worked for this but lacks speed. It has two powered 1TB HDs but they are becoming a little small and I intend to use SSD. My backups are duplicated across the two drives after each successful backup.

I was considering a 'ready' built unit or a box to build my own. I would prefer to build my own having built PCs over the years. I suppose a suitable mobo could enable that.

EDIT: NFS server (New term to me - users of the other OS will need access. How to deal with mobile phone clients*)*

[https://bluexp.netapp.com/blog/azure-anf-blg-linux-nfs-server-how-to-set-up-server-and-client](https://bluexp.netapp.com/blog/azure-anf-blg-linux-nfs-server-how-to-set-up-server-and-client)

[https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)

---

### Post by TheFu on 2024-01-30
Android phones shouldn't be on any trusted network directly. Neither should any IoT devices like door cameras, garage door openers, streaming sticks, TVs, or game consoles.  This is an FBI security recommendation.  Don't trust any purpose-built devices on your real network - that's the easy way to know what shouldn't be allowed to sit there.

rsync isn't a good backup tool.  rdiff-backup is almost the same options, but provides versioning for free. For simple needs, rdiff-backup is trivial to use pushing over the network.
Never allow backup storage to be accessed using file sharing protocols like CIFS/samba/NFS/p9.  Like rsync, rdiff-backup will use ssh credentials for client/server authentication, so you probably already have that working.   If the clients can directly access the backup storage, malware and crypto-ware can destroy those backups. Beware.

For Android to have access, didn't we go over all the options in another thread last week?  Nextcloud, sftp, rsync, all come to mind.  Wormhole, or a 1-line http server for really small, quick, transfers too.

Further, sftp is secure enough for use over the internet, provided you use ssh-keys or ssh-certs, never passwords.  Passwords are a total security failure.  Heck, did you see that MSFT executives had their emails hacked last week due to passwords being cracked?  If those "experts" can't do it well, what chance do the rest of us have?  DON'T USE PASSWORDS without 2FA. That's the answer.

Don't think about "more" storage for the Pi as meaning more disks.  Think larger disk.  You can get an 8TB USB disk for $150-$200 and that should hold more stuff than you should have.  You'll still need another drive for backups, however.  Drives still fail due to physical problems.

SSDs are just too expensive for backup storage, unless you like to waste money.  If a backup runs when you shutdown the system for the day, then then it shutsdown or goes into standby mode over night, what do you care if it takes 30 seconds or 30 minutes?

BTW, rdiff-backup is faster than rsync after the initial run.  I already reviewed and deleted my backup logs from last night, but they take between 20 seconds and 3 minutes for all but 2 systems. Those 2 system have millions of tiny files, so the time required is more about finding and opening each file to decide that it hasn't changed more than anything else.

I assume that netapp link is for something you aren't planning to buy?  Who has $200K lying around?  I remember when NetApp was a new company. Our lab got one on loan from them and it was relatively cheap compared to other options of that period.  I also assume you aren't looking at enterprise storage solutions like EMC frames or Hitachi frames for home that hold hundreds of disks. ;)

Lastly, my data is worth more than anything else I have - computer-wise.  If the house is burning, I'll grab my backup storage and leave the computers.

Low power use shouldn't override all cost considerations.  R-Pi systems become more expensive than many low-cost, smallish, x86-64 computers that use 35W.  Look for ITX motherboards that have 1-3 PCIe slots of you want a low power solution for a NAS.  My NAS isn't really just a NAS nor is it even the main use for that system.  It was a media server long before I decided to share the storage on it via NFS.  My piv4 is a media player connected to a projector. It doesn't hold any data.  All media to be played is from jellyfin using either DLNA or jellyfin's protocol.  The fact that it might be able to access the NFS storage too isn't part of the media playback.  We have 2 other Pis for playback devices in other parts of the house, all wired ethernet.  

The only wifi devices are tablets, smaller tablets (some people call them phones) and a cheap security cam in the attic watching for critters.  All of these are kept outside the normal LAN subnet. Only using a VPN, yes, even at home, are they allowed to access any secure subnets.  I don't trust wifi security. Not at all. The world has been burned too many times with wifi security failures.  In short, don't trust wifi or bluetooth - ever.

---

### Post by makem2 on 2024-01-30
I was thinking [COLOR=#000000]Nextcloud on Ubuntu and SSD came to mind as power saving. nvme or external in £100 region would be fine I think. I need to find a suitable [/COLOR][COLOR=#000000]x86-64 [/COLOR][COLOR=#000000]mini PC probably on amazon. I will look into [/COLOR][COLOR=#000000]rdiff-backup.

Many thanks for your input and time.[/COLOR]

---

