---
title: "HP Proliant DL380 G5 support &amp; avoiding RAID?"
date: 2017-05-13
forum: Hardware
---

### Post by courtney2 on 2017-05-13
I'm looking at getting an old HP Proliant DL380 G5 for my own family/friend server to run things like Nextcloud and local network backups. Perhaps even as a media server too. The one I'm looking at has 2 Xeon E5410 processors. I'm wondering if anyone knows how well supported this is with Ubuntu 16.04? I primarily want to entirely avoid the RAID card in here and do MDADM RAID with my OS disks and then a mirrored ZFS pool with some HDDs. Has anyone had experience with these old 2U servers and have any suggestions? I'm mostly interested in these old servers because the cost is so low

---

### Post by TheFu on 2017-05-14
Old servers aren't usually a good choice unless you specifically want to have server hardware.  Why not?
* they are loud.
* they use a bunch of power
* they generate HEAT
* upgrades/replacement parts often can only come from the vendor

For the stuff you've mentioned, a $100 MB+CPU is all that is needed.  I know.  I have a G3258 ($50) plus a $50 MB from 3 yrs ago that is my Plex Server, NAS, Calibre Server, and does 20 other things just fine.  Plus it uses about 35W of power, so it is relatively low power, quiet, and cheap to run.  I don't have any "servers" in the house (too noisy), but do run 5 systems as servers 24/7. Just got an electric bill yesterday - it was $65 for a 3 bdr house with all those computers, multiple networks, 20+TB of storage.  I don't spin-down any disks either.

BTW, I run nextcloud inside a VM - public internet stuff needs to be separate from storage and really should be on a different LAN.  Our nextcloud server is only available via a VPN, ssh-socks proxy or on the LAN.

For nextcloud, a $35 r-pi v3 will easily handle it, but if you need to transcode video for different playback devices, then you'll want that $50 Intel CPU.

IMHO.

---

### Post by courtney2 on 2017-05-15
Hey TheFu, I understand your points, and my only deterrents in your list are #2 and #4 because my server would be "tucked away" in a year-round cold garage. 

That energy cost is not a bad cost for 5 servers. I'd just need the 1 and 2TB of storage (I'm seeing some decent looking single core xeon towers that are old) and I assume $10/mo is what I'd spend max on that (energy where I'm at is cheap). I know network security, but I'm a person on a budget who just has some simple needs, and my raspberry pi server isn't enough. Plus I'm not running a business environment so my security rules aren't as strict for accessibility

I want something beefier to handle the applications I want to run, get my feet wet in some "out of school" learning and ultimately my needs are both cheap, something with 6 SATA plugs & bays and I'd really like ECC (I highly value data integrity). I like these older servers bc they have all that and sit within my budget. So really, I just want to know if there's a good SATA card or something I can get for these older 2U/tower servers so I can 100% ignore RAID

---

### Post by TheFu on 2017-05-15
If you care about data integrity, then you need ECC and ZFS. You know this already.

I wouldn't touch an old server for the reasons outlined above. We are clearly different folks.
My energy bill isn't just for those computers, it is for an entire 2700sqft house located near Squidbillyland. We've had the A/C on for a few months already.

For out of school learning, I prefer a 16G RAM Core i5 box.  Plenty of CPU and RAM to load up 10+ VMs easily.  Heck, I ran 10 VMs on 8GB of RAM for years.  If you don't do much Windows, that is easy.  I've paired down my VMs from 20+ to ... let me see ... 
```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 2     zcs43                          running
 3     lubuntu                        running
 4     Win7Ult                        running
 5     xen41                          running
 6     spam2                          running
 7     blog                           running
 8     nextcloud                      running
```

To 7 on that 1 machine.  Running some infrastructure VMs on another, smaller box to handle VPNs and internal routing.  External routing is always on a dedicated machine.  All my systems support VT-x, except the r-pis.
I don't run storage/NAS inside a VM.

Anyway, sounds like I cannot help with your needs.

---

