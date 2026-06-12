---
title: "enterprise-class VS consumer hard disk for backup NAS?"
date: 2011-12-19
forum: Hardware
---

### Post by ijason on 2011-12-19
greetings.

i am making plans for a 2 year contract overseas, and these include setting up a NAS to let me manage remote backup of files i have with me. 

while not specifically an Ubuntu question, this is the only computer forum i'm on, and i usually find some pretty sound advice, so i thought i would ask here :)

i am trying to decide whether an "enterprise-class" hard drive is worth the extra cost, over a "consumer" model disk. i have read that the enterprise models undergo extensive burn-in testing at the factory, and that their error rate is generally a magnitude lower than consumer disks (1:10^14 vs 1:10^15)... of course, they cost 3x as much too!

the end result will be a NAS that is generally powered down, but can be powered up through the network, and then used as the target for rsynch file dumps. so it will only be powered up occasionally, but as i will be several thousand miles away reliability is key. although it is more a question of reliably powering up and writing a bunch of data, and then powering down... and less a question of 365/24/7 operation. also, write speed is not a concern as everything will be done through VPN anyways. 

any advice is greatly appreciated.

---

### Post by tgalati4 on 2011-12-19
You could set up 3 consumer drives and perform the rsync then have the other two rsync offline at a later time.  More likely is a failure of the controller due to power fluctuations.

So whatever you do, get an UPS that will power the NAS for as long as it takes to perform your rsyncs.  Enterprise drives generally work well for 24/7 use in servers.  For your wakeup-and-rsync use case, consumer drives may work as well.  I like the WD Blue and Black series of drives, but read the reviews on the specific drive model that you are considering.  Avoid "green" drives, they seem to be problematic in RAIDs and NAS configurations.

Also realize that massive writes can cause consumer drives to fail.  The heads heat up (due to higher write current needed) and delaminate making the drive unreadable.  Enterprise drives have more robust heads and are designed for continuous writes.

For a NAS, I am running freenas ([http://freenas.org](http://freenas.org)) and it's bulletproof.  My uptime is 189 days and counting since I set it up 6 months ago.

---

