---
title: "Basic questions about RAID setups"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by helix_r on 2007-06-20
Hi,

I have a motherboard that allows me to have SATA RAID (its an [ASUS A8N-SLI premium]("http://www.asus.com/products4.aspx?l1=3&l2=15&l3=0&model=539&modelmenu=1") that can be set up with raid 5). I've never done this before, but I think it might be useful. I do have a few questions:

1) For install of the OS, can I just plug in the 4 sata drives, config the bios and start installing? In other words, can the OS itself reside on the raid array?

2) When something goes wrong with a disk how will the computer tell me? How will I know which disk is bad?

3) If I do raid 5, do I just get one big "partition"? How does partitioning work? 

4) Has anyone done this recently? Any other things I need to know?

---

### Post by vmikalinis on 2007-06-20
1) For install of the OS, can I just plug in the 4 sata drives, config the bios and start installing? In other words, can the OS itself reside on the raid array?

  **It depends, I didn't look at the manual, but if the hardware supports it, you can just open some sort of raid manager at bootup and configure the raid.**

2) When something goes wrong with a disk how will the computer tell me? How will I know which disk is bad?

**someone else will have to field this, i'm not familiar with Linux raid monitoring.  I doubt very much that the board came with linux software.  But I know there are a few things out there to do this.**

3) If I do raid 5, do I just get one big "partition"? How does partitioning work? 

 **Yes you can make one big partition, if you use 4 drives you will lose the capacity of 1 drive to restoration info.  If there are 4 100 gig drives, you will have about 300gig usable.  **


Check out [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by vmikalinis on 2007-06-20
Ok I went back and looked , this board has both nvidia and Silicon Image raid controllers.  They are both configurable in the bios.  You can pretty much do whatever you want with the config and it won't affect the OS.     The OS will just see it as one drive, or however many you configure. 

If you just want to do a raid 5, go into the bios and turn on the Silicon image controller and configure it for raid 5.  Leave the nvidia raid disabled.  You will be installing your OS and data on this.  

You could also install the OS on the nvidia mirror and the data on the raid 5 , but you need 6 drives for that.  You can do alot with this motherboard.  I would take a look at the manual.

---

### Post by helix_r on 2007-06-21
Thanks, I will do some more reading and give raid5 a try.

Has anyone on these boards ever set up raid 5 (or raid 0,1,0+1) on an a8n SLI running ubuntu?

---

### Post by Midahed on 2007-06-21
I've been looking into installing a raid.  From what I've read I thought the general recommendation was NOT to use the 'hardware' raid controllers that are built into many motherboards.  My understanding is that they're what are known as FakeRAIDs (software raids, albeit with the software loaded as firmware in the on-board controller) and are difficult if not impossible to set-up under Linux.  Typically Linux will see the drives on such a controller as separate devices - not as a raid.

Unless you know otherwise, it may be worth searching the Ubuntu forums for Fake RAID....  There are quite a few threads covering the subject.

Mike

---

### Post by helix_r on 2007-06-22
Yes, it is looking like a RAID 5 mobo with ubuntu is going to be a pain to set up. My ultimate goal is simply to have a robust file server with some apps like svn, mysql, etc.

I am thinking now that the way to go would be to purchase a RAID 5 NAS (like [this]("http://www.buffalotech.com/products/network-storage/terastation/terastation-live/"), for example), and then put together a very simple and minimal server that mounts the NAS. I could then back up the server regularly so that if it malfunctions, it is quick and easy to get it up and running again.

---

