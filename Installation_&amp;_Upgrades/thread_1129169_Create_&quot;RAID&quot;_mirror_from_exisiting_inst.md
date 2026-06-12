---
title: "Create &quot;RAID&quot; mirror from exisiting install?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by richardedwards on 2009-04-18
I have an Ubuntu 8.10 install onto one hard disk.

I have recently purchased another (matching) hard disk.

How do I "mirror" my existing hard disk with this new one?

I have tried reading the FakeRaid Howto - but it does not make any sense to me...?! 

Can someone point me in the right direction?

thx vm

Richard

---

### Post by richardedwards on 2009-04-19
bump

---

### Post by ronparent on 2009-04-19
The Fake Raid How To applies if you have provision in your bios to activate and configure your disks as raid and you need a driver to actually use it. In which case dmraid impements that capability. 

Software raid proceedures would apply if you had no raid capabilities built into your motherboard. The software raid alternatve not only allows you to set up a raid array between identical disks but also between identical partitions. The mdadm linux software solution implements this case. 

There are proponents for both approaches and both will work quite well. I personally use dmraid to run a raid0 pair of discs. That said, you may want to investigate this site:

[http://ubuntuforums.org/showthread.php?t=1027240&highlight=raid](http://ubuntuforums.org/showthread.php?t=1027240&highlight=raid)

In priciple, the process with a raid1 setup should be simple. It should be like if a disk broke and you replaced it with a new one. Having never had to do it myself I  would never try to guide you step by step.

---

### Post by mitanc on 2009-04-20
Great answer, but I have a slight update on the situation.

I have a server which has a "fakeraid" intel controller, I originally intended to install Ubuntu 8.10 using mdadm software raid so I disabled the hardware raid controller in the bios.  During the install it said it would setup raid (I assumed software raid) but it setup some kind of half working dmraid.  

Anyways, how is your experience with dmraid?  Stable?  Can you update via bios or would you recomend using software raid if I was to do it all over again.

---

### Post by ronparent on 2009-04-20
I have not yet had any problems with my dmraid setup. Initially I could see the array but couldnt' mount the partitions. This was fixed by editing fstab to automatically mount my windows partitions on reid with boot. The array was defined as a raid0 in the raid bios before I ever installed ubuntu. Once you have a stable array there should not be any need to fuss with the bios settings. The bios perfoms the functions of defining the array simular to assembling the array in mdadm.

In my case, it was simpler for me to install ubuntu on a separate drive, I had installed for the purpose, than to chance destroying 320 Gb of winXP installation and data files on a relatively fragile raid0 array! There were too many oppotunities for me to do something stupid. Knowing more now, I still would use the dmraid approach since it would be simpler to implement to meet my particular objective (keep the existing raid0 array intact). In your case you safely can take either approach. Implementing a software raid is spelled out in the reference I gave you. You would probably have to research the fakeraid approach. Like I said before, once the raid array is defined in bios (for the ports you disks are plugged into) it should recognize the new disk immediately and begin mirroring to it. I would be more comfortable with it if I could advise you on the particulars.

---

### Post by mitanc on 2009-04-21
Yeah, if your using Windows then DMRAID is the way to go.  My issue now is my Raid is totally corrupted because I disabled the raid cntroller in bios but Ubuntu still made a dmraid config using 4 different hard drives.

This weekend I plan on revamping my server and am totally stuck on which way to proceed. I have the following options and thoughts:

1.  Configure the system using dmraid, but this time enabling the raid config in bios.  My thoughts on this are how to reactivate partitions if it one becomes corrupted or broken?  I saw mdadm docs on how to do the same, but not sure about dmraid.

2.  Use mdadm, but I hope intrepid doesn't autodetect and install dmraid when I configure my machine.  I was planning on installing one HD, throw the system in, then activate a mdadm software raid on that partition with the new harddrive.  Anyone have thoughts?

For both systems I will back up my OS config the way I have it now and then reinstall intrepid onto the box and PRAY that everything works.  Setting up openLDAP and my printers were a PAIN and I hope I can have it all working properly!

Thanks for listning.

Mitan

---

