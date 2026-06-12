---
title: "Recommendations for back up drive"
date: 2013-08-03
forum: Hardware
---

### Post by BmrfxKG on 2013-08-03
Hey all,

I am looking for a back up solution for my Ubuntu laptop.  I took a look at deja-dup and it seems that the remote options will let me do wireless backups over my home network. The only missing piece is to get the back up hard drive. 

Which external wireless enable hard drives with integrated SSH, FTP or WebDav do you recommend?

---

### Post by TheFu on 2013-08-03
Chances are that wifi is a very slow way to backup an entire PC. It just doesn't have enough bandwidth. Wired GigE ethernet or directly attached USB3/eSATA would be preferred. Even USB2, which is 4x faster than 100baseT seems extremely slow in comparison.  You might want to do the first backup directly connected, the do incrementals over wifi where much less data gets transferred.

Just wanted to say that, so you know what to expect if you decide to go with wifi.

I use wired GigE and rdiff-backup for backups here. These are written to a Linux server with Linux file systems, but I know that writing Linux backups to non-Linux file systems can turn out bad. Be certain that the backup storage has whatever file system you need to make your system backups workable.  Perhaps dejadup doesn't care, but most backup solutions based on librsync DO care about the backup storage file system so owner/group and other permissions are not lost in the backup process.  What all this means is that if your backup solution needs a Linux file system, then it is unlikely that cheap NAS storage will support that. Buyer beware.

If dejadup doesn't care about the target file system, then don't worry and be happy.

Anyway, I hope this helps.

UPDATED:
Realized later that I didn't really provide any guidance about NAS device features. If you need/want Linux file systems, then the NAS device will need to support ... 
* NFS
* iSCSI
* AoE
If you look for cheap network-based storage, you won't see those until around $700+ prices.  That's why many Linux people just find a low powered box and put a few huge HDDs inside for backups.  An Atom or AMD E-series system uses 15+W and can be built for $120. It makes a good NAS for Linux needs.  My E350 has a built-in GigE LAN port too - perfect for backups even if the clients do not have GigE. This way the backup server can handle multiple clients concurrently.

Samba is NOT a Linux file system.
CIFS is NOT a Linux file system.
NTFS/FAT32 is NOT a Linux file system.
"Windows Sharing" is NOT a Linux file system.
I have a WD HD TV Live device that supports USB storage and makes it available on the network. It runs Linux, but only supports FAT32 or NTFS file systems. Since it is a 100baseT device, the fastest transfers it accepts are about 11MB/sec.  Compare 11MB/s vs 80MB/s for GigE. There isn't any real comparison.

Devices that support FTP really aren't desirable for LAN-based storage.  Actually, almost nobody should be using FTP for anything anymore. Google the reasons, if you care.

My systems never transfer data faster than 80MB/sec. Guess my GigE switches and NICs are too cheap?  This limit even applies to 100% pure network transfers - no disk IO at all.  Before I upgraded all my NICs to Intel PRO/1000s, I had cheaper GigE cards and usually didn't get over 200Mbps (25MB/s).

---

### Post by CharlesA on 2013-08-03
I think The Fu pretty much covered it.

I wouldn't do backups over wifi unless it was a tiny amount of data - the transfer speeds are ridiculous compared to Gigabit ethernet. Even going over ethernet, it will still take time if you have a lot of data because Gigabit ethernet tops out of around 125MB/sec.

I do full backups from my main server to my backup server via GigE and it still takes around half an hour to sync the 4TB of data using rsync, but that's mostly due to the maxing out bandwidth available to me.

---

### Post by BmrfxKG on 2013-08-03
Hey, thanks for the response.

Wifi is definitely to slow for the initial back up.  But I am thinking of a back up solution for a home computer where I just add a few MB a week so wifi will work for regular diff backups.

I do not want to have to plug a wire every time I need to do a back up, this is my current set up and I just don't do it, I rather doing it in a cron job.

Also, I do not want to set up an additional server just for back up, so having a hard drive that I can access wirelessly is my desired solution.

---

### Post by TheFu on 2013-08-04
Charles and I completely understand the convenience of wifi, hence the suggestion that your first backup be wired or directly connected, then you can switch to wifi.  With the backup systems I use, based on librsync, it isn&#8217;t just the changed data that gets transferred, but the checksums for every block of every file in the backup list which needs to be compared.  That is the magic and curse of librsync. If the remote storage machine doesn't run a compatible server, then all that data will be transferred to the client machine for comparison or worse, the files will just be copied over again if the system thinks the storage is local (if it is mounted).

Does your WiFi router support USB storage?  Many models do, so switching the router and getting a cheap external USB disk might be the most cost effective.  I suppose there are pogoplugs and similar solutions [http://www.tonidoplug.com/](http://www.tonidoplug.com/) too - most of these require we trust a 3rd party even just for local file access.  Unless we swap out the OS on them and void the warranty.

A few years ago, Seagate made a small HDD dock that ran an imbedded Linux and had a GigE port.  Dockstar ... was the name, I think.  They were on ebay for $20-$25 for about a year after that.  [http://techcrunch.com/2010/05/06/how-to-use-the-seagate-dockstar-on-a-lan-without-pogoplug/](http://techcrunch.com/2010/05/06/how-to-use-the-seagate-dockstar-on-a-lan-without-pogoplug/) seems relevant. So does [http://archlinuxarm.org/platforms/armv5/seagate-goflex-home](http://archlinuxarm.org/platforms/armv5/seagate-goflex-home)  I would have gotten one, but my backup storage requirements were larger than a single disk could support.  Some friends got these dockstars, but installed bittorrent clients on them and left the torrents running 24/7/365 ... er ... until their ISP sent cease and desist letters out.

You probably already looked at these: Seagate Home/SmBiz NAS [http://origin-www.seagate.com/external-hard-drives/network-storage/](http://origin-www.seagate.com/external-hard-drives/network-storage/)
SmallNetBuilder does product comparisons of lots of products - especially NAS boxes: [http://www.smallnetbuilder.com/nas](http://www.smallnetbuilder.com/nas) Probably more complexity than you'd like.

I built my external array with stuff from these guys: [http://www.addonics.com/](http://www.addonics.com/)  Probably overkill for your needs. They do make a tiny USB-to-NAS devices, however. [http://www.addonics.com/products/nas40esu.php](http://www.addonics.com/products/nas40esu.php) and $90 to support 16 storage devices seems like a bargain. This is the first, cheap device they make that actually claims support for EXT2/3/4, XFS and FAT32/NTFS file systems.  Hummmm. Too bad it is only USB2 or eSATA. If it supported USB3 - I'd have already clicked "buy!" today. Of course, they sell [http://www.addonics.com/products/adu3esa.php](http://www.addonics.com/products/adu3esa.php)  $30 to solve that (hope it goes from eSATA-to-USB3 and not just USB3-to-eSATA).  Sorry - I got lost there for a second. ;) I love storage.

Anyway, please report back on what you select ... or after you select a specific device, it might be worth posting a new thread and asking for comments and known issues around the exact backup method on the exact device you plan to use.

Good luck.

---

### Post by CharlesA on 2013-08-04
> **TheFu said:**
> Charles and I completely understand the convenience of wifi, hence the suggestion that your first backup be wired or directly connected, then you can switch to wifi.  With the backup systems I use, based on librsync, it isn&#8217;t just the changed data that gets transferred, but the checksums for every block of every file in the backup list which needs to be compared.  That is the magic and curse of librsync. If the remote storage machine doesn't run a compatible server, then all that data will be transferred to the client machine for comparison or worse, the files will just be copied over again if the system thinks the storage is local (if it is mounted).

Indeed. When I first set up my old server as an extra backup location I wondered why it it took so long when backups via USB3 were quick. I think the part that took the most time was the transferring and checking of checksums  because I ended up looking at iotop and noticing the read speed of the drives topped out at around 125MB/sec.

I spent some googling around and found suggestions to lower to encryption, but decided against it because I would rather wait 30 minutes than mess with something that is already working as intended.

As far as USB storage on the router goes, I've had friends who praise it, but most of them run Windows, and if I remember right, you would need to look for one that supported *nix file systems instead of just NTFS if you want to keep your permissions intact.

---

### Post by calltheninja on 2013-08-04
You might want to take a look at DiskStations by Synology, they are extremely reliable network storage devices which support SSH etc.

---

### Post by BmrfxKG on 2013-08-04
Thanks for the advise.

I am playing with the idea of use a raspberry pi and attach a driver to it.  That seems to be the more flexible solution at a reasonable price.  Any thoughts?

---

### Post by CharlesA on 2013-08-04
> **BmrfxKG said:**
> Thanks for the advise.

I am playing with the idea of use a raspberry pi and attach a driver to it.  That seems to be the more flexible solution at a reasonable price.  Any thoughts?

How would the Pi be connected, wifi?  It might work, but you'd be limited to USB2 speeds if the wifi connection didn't kill the transfer speed.

---

### Post by BmrfxKG on 2013-08-04
Not sure how the pi and the drive are going to connect.  I am leaning for that solution since I do not have a lot of space.  Some of the drives recommended here look very promising.  I have to research them before going forward.

---

### Post by CharlesA on 2013-08-04
> **BmrfxKG said:**
> Not sure how the pi and the drive are going to connect.  I am leaning for that solution since I do not have a lot of space.  Some of the drives recommended here look very promising.  I have to research them before going forward.

Well, if you are going the Pi route, your only option to connect the drives is going to be USB2.

As far as network connectivity goes, it has a 10/100 port, but that would max out at around 11MBps, so you wouldn't have to worry about the bottleneck being the USB HDD.

---

### Post by BmrfxKG on 2013-08-04
Yea, it might be slow.  My current plan is go the pi route (I already have an external drive that supports USB/eSATA) and it is to slow get one of the NAT adapters that TheFu pint to...

---

### Post by TheFu on 2013-08-04
> **BmrfxKG said:**
> Yea, it might be slow.  My current plan is go the pi route (I already have an external drive that supports USB/eSATA) and it is to slow get one of the NAT adapters that TheFu pint to...

I've seen the rPi at work. Don't expect much from it as a NAS device. It doesn't have enough CPU.  Much better off getting a Marvell-based plug computer-dock thingy, IMHO, if you can't afford that mini-NAS device with EXT2/3/4 support and a GigE port.

---

### Post by TheFu on 2013-08-05
> **BmrfxKG said:**
> Yea, it might be slow.  My current plan is go the pi route (I already have an external drive that supports USB/eSATA) and it is to slow get one of the NAT adapters that TheFu pint to...

Just saw this today - $70 for a Seagate GoFlex ... could be what you want.
[http://bensbargains.net/bargain/seagate-goflex-500gb-usb-3-0-mobile-wireless-storage-70-at-newegg-67889/](http://bensbargains.net/bargain/seagate-goflex-500gb-usb-3-0-mobile-wireless-storage-70-at-newegg-67889/)
I've never used it and didn't look too closely at the specs.

---

### Post by CharlesA on 2013-08-05
> **TheFu said:**
> Just saw this today - $70 for a Seagate GoFlex ... could be what you want.
[http://bensbargains.net/bargain/seagate-goflex-500gb-usb-3-0-mobile-wireless-storage-70-at-newegg-67889/](http://bensbargains.net/bargain/seagate-goflex-500gb-usb-3-0-mobile-wireless-storage-70-at-newegg-67889/)
I've never used it and didn't look too closely at the specs.

That looks like a newer model than the ones I have, but I've been using quite a few of those for external backups. So far they seem to be decent.

---

