---
title: "A ubuntu media server"
date: 2006-09-03
forum: Hardware &amp; Laptops
---

### Post by neptune39 on 2006-09-03
Ive just started using ubuntu, my first real use of linux, and i'm trying to create a media server. So far its been great and im now ready to take my plans and actually invest some cash.

What im trying to do at first is have the media server run as an itunes server (mt-daapd) and as a movie server. It needs to work with macs and PCs. I've managed to get this set up with just a 20gb drive and now i'm looking to get 2x250gb seagate drives.

I did look into SATA as I only have ide but I have decided not to go this route, is this a mistake? As I see it; doing this allows me to add it later with even more drives.

I would like to set up a software raid, raid 0 or 5 with at least the 250gb drives and if possible with the 20gb as well, i've downloaded the alternative install disk, how do I set this up and what would be the best way to do it, e.g the 20gb not in raid with ubuntu on it or everything together. I've read about it elsewhere but a bit confused about the partitions of the raid drive. With the raid im just looking to have the one big drive, i'm not worried about mirroring.

How should I physically hook up the drives for best performance, I have 3 and obviously 2 are going to be on the same cable.

Cheers for any help.

---

### Post by neptune39 on 2006-09-03
Ok some questions about raid, im doing it raid 0 and the software recomends a swap file. How big should the swap file be and is it ok on one drive? I think im close to getting this to work, the first try stalled on 50% during the grub install and im trying again.

---

### Post by neptune39 on 2006-09-04
Ok so I found out that a boot partion is required for a raid 0 array and I got it working, its quite simple once you understand whats going on. I've order two seagate 320gb drives and ive gone the sata route by buying a pci sata raid card from dabs, total cost was £145 for that. Went the sata route because it cost so little to implement, about £8 for the pci card, and the drives are the same price.

The pci cards are not true raid so im hoping i can just use them as sata controllers and then set up the software raid.

Im also adding another sata drive i have wich is 200gb, giving me 840gb total space. Once I have it all installed the first thing im going to do is add mt-dappd support i.e run it as an itunes server and then use samba for the other media - videos etc. My front end is probally going to be a mac mini running Front Row and various laptops.

Any tips or ideas are welcome.

---

### Post by neptune39 on 2006-09-05
So the Raid SATA cards work perfectly as I wanted with no use of the onboard RAID. It has allowed me to add four SATA ports to my old PC for a mere £12.

I now have a software raid with 720GB of space.

I installed mt - daapd, it worked, I added my 33gb of songs and it stopped, any ideas on that one? Also when I move the files they take their permision setting with them meaning they are locked on the ubuntu side, how can I get around this?

I'm going to play around with this a little...

Anyone interested in adding SATA; I used the dabs value 2 port pci RAID card, about £7.

---

