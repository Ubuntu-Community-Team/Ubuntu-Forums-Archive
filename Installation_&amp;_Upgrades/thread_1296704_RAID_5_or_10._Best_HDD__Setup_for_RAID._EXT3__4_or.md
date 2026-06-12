---
title: "RAID 5 or 10. Best HDD / Setup for RAID. EXT3 / 4 or NTFS?"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by 337Manni on 2009-10-21
I’m in the process of putting together a server for storing media which could be streamed over a LAN to several clients.
  The server has Ubuntu Alternate 9.04 installed over a RAID 1 (2x40GB Seagate IDE HDD).
  It also has 12 x 3.5inch Hot-swap HDD bays which I plan to use in a RAID array for media storage. I plan on starting off with 3 to 5 HDD (2-4TB array size.), depending on my budget at the time of purchasing, then growing the array when / if needed. I would be using the software raid in Ubuntu.
  I have a few questions before I continue with the build which I would appreciate help in getting to the bottom of.
   
   
  1, What would be best (and why) for this type of application, RAID 5 or RAID 10 or others?
  I’ve heard bad things about the write performance or RAID 5 and praise for the performance of RAID 10, but I have also heard that you can’t / couldn’t expand RAID 10. Is this all true with Ubuntu software RAID?
   
  2. Are there any advantages / disadvantages of one big storage array verses several small ones?
  If I need more space in the future should I grow the array or make a second one?
   
  3. What would be the best option, more small HDDs or fewer large HDD?
  e.g. In RAID 5 to get a 4TB array would 5x1TB or 3x2TB be best?). I’m thinking the more HDDs I have, the greater the chance of one failing, but the larger the HDD the longer it will take to rebuild an array = the greater the chance of an unrecoverable write error.
  I just can’t decide between 1, 1.5 or 2TB drives. There’s the initial cost (3x1TB is cheapest to get things going), there’s cost / GB (1.5GB drives are currently best for this) or there’s the biggest drives for maximum expanding in the future.
   
  4. Diversification or Uniformity?
  Would it be best to try and keep all drives the same to get the best performance out of the array or use different make / model / batches to reduce the potential of mass drive failure from a bad batch…?

  5. What would you recommend for the best type of HDD/s to use in this system?
  I understand that there is no perfect HDD for every application, but I’m     not sure as to what is critical when taking about using a HDD in a RAID array. What I mean is would the RAID hide or highlight certain aspects of the drives performance (throughput, access time, latency, noise, power to MB/s…)?
  Again I would be using this to store HD Movies, Music & pictures to stream over GB LAN. Also question 7 way help with the power Vs performance side of things.
   
  6. Which file system would you recommend, EXT3, EXT4, NTFS or others?
  I will have a mixture of XP / Ubuntu & Kubuntu clients which I’m concerned about reading the array (unless this will be done by the server???)
  Also what about fragmentation? Am I right in thinking this wouldn’t be a problem with EXT3 or 4?
   
  7. Is it possible to make the server with Ubuntu Alternate 9.04 to Shutdown / Hibernate / Sleep with a command from one of the clients, and then Wake On LAN (WOL) when needed? I’m thinking of saving power as it wouldn’t be in use 24/7. I’m sure this must be possible under Ubuntu / Kubuntu, but I’m concerned about XP being able to issue the command to the server. I’m fairly new to Linux so I’m still learning!
   

  Thanks for reading and sorry about all the questions (the more I typed, the more I questions had!:confused:). No doubt there will be more.
   
  Any feedback is welcome and thanks in advance!

---

### Post by 337Manni on 2009-10-21
Can anyone recommend a good performance, lowish powered HDD for a RAID application?

---

### Post by rabban on 2009-10-21
Im in a similar situation and would love to see a good answer to these questions. 

337Manni
Have you decided on motherboard / Raid board?

Sincerely

---

### Post by 337Manni on 2009-10-21
Hi Rabban, thanks for the reply.
   
  I already have a motherboard and RAID card, but I’m not at home at the minute and can’t remember the model. I will post the details of them when I can. I’m concerned over the max capacity that my RAID card can handle, so when I get to the bottom of that I may be on the look out for a replacement.
   
  I actually was looking for a NAS on ebay and stumbled upon a used server at a ridicules price. I had thought about building my own so I put a bid in and won!
   
  I’ve been looking at a few reviews / roundups of HDD and have a couple in mind, but just would like to know what part of the performance really matters for a RAID array before I make the decision and go to buy them.
   
  Rabban, can I ask what hardware you have, if any and what you’re trying to do?

---

### Post by 337Manni on 2009-10-22
My Server specs are currently:
  Case – Evesham 12Bay SATA (Don’t know the model number unfortunately)
  Motherboard – Intel S845WD1-E
  CPU – Intel P4 2.8GHz
  RAM – (1GB) 2 x 512MB PC2100, ECC, 266MHz, SDRAM
  PSU – R3G-6650P = 650W
  PCI1 – 3Ware Escalade 8506-12 12Port SATA RAID Controller Card
  PCI 2 – Intel PRO 1000 MT Server Adapter
  PCI 3 – SCSI Host Bus Adapters - LSI20160
  OS HDD – 2 x 40GB Seagate Barracuda 7200.7 in Software RAID 1
  OS – Ubuntu 9.04
   
  I got the above (minus the HDD / OS) off ebay as I said, but wasn’t aware that any PCI cards came with the server so they where a bonus really. The HDDs where lying around in my loft.
   
  More  questions! :)
  I’m 99% sure I’m going to setup a software RAID array for my data storage, mainly due to the fact that if my RAID card goes down I would have to replace it with virtually like for like to get my data back, where as with software RAID I could be more flexible.
  I believe that this RAID card can support a max of 250GB HDD x 12 with 2TB Max each Array.
  My question is could I just use my RAID Card as 12 x individual SATA drives and setup RAID via software?
  If so would I still be restricted to 12 x 250GB HDDs?
  If I am restricted then I am going to look into selling this card and into buying another one or a new MB with lots of SATA ports (probably the MB).
   
  Anyway, back to my first set of questions. Hears a summery of RAID 5 & 10 then my reasoning so fare as to best HDD for them (please correct me if I’m wrong, or even confirm my understanding):
   
  **_RAID 5_**
  **Hard Disk Requirements**: Minimum of three; maximum set by controller. Should be of identical size and type.
  **Array Capacity**: (Size of Smallest Drive) * (Number of Drives - 1).
  **Fault Tolerance**: Good. Can tolerate loss of one drive.
  **Degradation and Rebuilding**: Due to distributed parity, degradation can be substantial after a failure and during rebuilding.
  **Random Read Performance**: Very good to excellent; generally better for larger stripe sizes. Can be better than RAID 0 since the data is distributed over one additional drive, and the parity information is not required during normal reads.
  **Random Write Performance**: Only fair, due to parity overhead; this is improved over RAID 3 and RAID 4 due to eliminating the dedicated parity drive, but the overhead is still substantial.
  **Sequential Read Performance**: Good to very good; generally better for smaller stripe sizes.
  **Sequential Write Performance**: Fair to good.
  **Cost**: Moderate
  **Special Considerations**: Performance will depend to some extent upon the stripe size chosen.
  **Recommended Uses**: RAID 5 is seen by many as the ideal combination of good performance, good fault tolerance and high capacity and storage efficiency. It is best suited for transaction processing and is often used for "general purpose" service, as well as for relational database applications, enterprise resource planning and other business systems. 
   
   
  **_RAID 10_**
  **Hard Disk Requirements**: An even number of hard disks with a minimum of four; maximum dependent on controller. All drives should be identical.
  **Array Capacity**: (Size of Smallest Drive) * (Number of Drives ) / 2.
  **Fault Tolerance**: Excellent for RAID 10.
  **Degradation and Rebuilding**: Relatively little for RAID 10
  **Random Read Performance**: Very good to excellent.
  **Random Write Performance**: Good to very good.
  **Sequential Read Performance**: Very good to excellent.
  **Sequential Write Performance**: Good to very good.
  **Cost**: Relatively high due to large number of drives required and low storage efficiency (50%).
  **Special Considerations**: Low storage efficiency limits potential array capacity.
  **Recommended Uses**: Applications requiring both high performance and reliability and willing to sacrifice capacity to get them. This includes enterprise servers, moderate-sized database systems and the like at the high end, but also individuals using larger IDE/ATA hard disks on the low end. Often used in place of RAID 1 or RAID 5 by those requiring higher performance; may be used instead of RAID 1 for applications requiring more capacity.
   
   
   
  **_RAID 5 HDD_**
  A lower **Write Access Time** would help to lesson the impact of the **Random Write Performance**.
   
  A lower **Write Transfer Rate** would help to lesson the impact of the **Sequential Write Performance**.
   
  **_RAID 10 HDD_**
  Larger **Capacity** drives due to the efficiency of the array.
   
  I’m thinking that in both cases:
  **Random Access Time **would be roughly as quick as the slowest HDD.
  **Transfer Rates **would increase with the number of HDD until you reach other limits (eg external transfer speed of 3GB/s).
  **Power Consumption **more obviously, would increase with each additional HDD
  **Noise **would also increase with each additional HDD, but by what degree, or how to calculate I’m not sure.
   
  For Operating Systems with lots of small files spread over the disk the positioning speed of the heads on the HDD is important, therefore Access Time (Random Read / Write, Seek Time, Latency) is an important facture.
   
  For large files types (Videos…) I believe Transfer Rate (Sequential Read / Write, Sustained Transfer Rates) is important. This is assuming that the data isn’t heavily fragmented. If video editing, sequential write would be more critical than read.
   
  Would you all agree with this?

---

### Post by rabban on 2009-10-23
Im at work right now, so I'll give you a more detailed reply later on.

I'm running a Raid5 software raid setup. The disks are all connected to the motherboard itself, no Raid controller card. I used mdadm to set up the raid. It has worked great for almost 2 years now, but Im not happy with the monitoring capabilites of the setup. I had one disk break after 1-3months but it took me a while to figure that out.

Rabban

---

### Post by 337Manni on 2009-10-23
I thought that mdadm could be setup to email you of a disk failure?
I was planning on looking into this more when I setup my RAID.

---

### Post by 337Manni on 2009-10-23
Is your RAID just used on that local PC or do you access it over a LAN?
   
  I’m starting to lean towards setting up a RAID 10 with four HDD, either 1TB or 1.5TB each HDD (2 or 3TB array size).
  I would then add a second RAID 10 if the need ever arises in the future. By then I could take advantage of the larger HDD or quicker SSD which would then be around.
   
  I think I may take the chance and go for all the same HDD to get the best performance out of the array.
   
  I can’t decide on the file system though. I would probably be looking to max my sequential read / write speed (mainly read) and so would like to take advantage of the EXT4 performance gains in this, however don’t know if this would be a problem with XP viewing the files.
   
  I don’t know if XP would read the disk itself, or it Ubuntu would read the disk and pass the info to XP? Any info here would be great!
   
  I’m still trying to get the server to power off when not in use so that I can WOL and I have started a separate thread for this here if anyone is interested:
  [http://ubuntuforums.org/showthread.php?t=1298842](http://ubuntuforums.org/showthread.php?t=1298842)

---

