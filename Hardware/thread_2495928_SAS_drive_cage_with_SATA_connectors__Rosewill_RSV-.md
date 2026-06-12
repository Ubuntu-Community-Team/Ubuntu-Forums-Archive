---
title: "SAS drive cage with SATA connectors?  Rosewill RSV-SATA-Cage-34"
date: 2024-03-08
forum: Hardware
---

### Post by papriak on 2024-03-08
I'm using a pair of Rosewill RSV-SATA-Cage-34 model drive cages in my server, and just noticed that they have SAS connectors inside.  However, the cages use plain 7-pin SATA data connectors on the back.

Does the latter fact mean that any SAS drives I install would lose their advantages over the SATA drives I'm currently using, or might the backplane fix that?


Manufacturer's product page:  [https://www.rosewill.com/rosewill-rsv-sata-cage-34-hard-disk-drive-cage/p/9SIA072GJ92556](https://www.rosewill.com/rosewill-rsv-sata-cage-34-hard-disk-drive-cage/p/9SIA072GJ92556)

Type of connector I saw inside:  [https://www.tape-drive-repair.com/wp-content/uploads/2012/10/Sff-8482-Connectors.jpg](https://www.tape-drive-repair.com/wp-content/uploads/2012/10/Sff-8482-Connectors.jpg)

---

### Post by MAFoElffen on 2024-03-09
The data plane for both SATA and SAS is 8-pin. My DELL Poweredge Servers had PERC RAID Controller that supported SAS Drives and SATA drives, and had SATA/SAS back planes out of the box, that supported both drives in their internal bays. SAS controllers will support both SATA & SAS drives, but it does not work the other way around. So if you have a SAS controller connected to SAS Drive bays, you can do both. But if you have only a SATA controller, you cannot use SAS drives with it...

Quote from: [https://www.seagate.com/support/kb/connecting-sata-drive-to-sas-controller-006170en/](https://www.seagate.com/support/kb/connecting-sata-drive-to-sas-controller-006170en/)
> 
The use of SATA hard drives on SAS controllers is made possible by the fact that both share the same infrastructure and have similar features. SATA drives may be plugged into SAS controllers. SAS drives cannot be plugged into SATA controllers.


RE: 
[https://www.sabrepc.com/blog/Computer-Hardware/difference-between-sata-and-sas](https://www.sabrepc.com/blog/Computer-Hardware/difference-between-sata-and-sas)

It's not the backplane that will give you the extra smarts needed to be able to use SAS Drives, it is the "Controller" connected to that backplane.

I can't remember offhand which brand and model controller you settled on, from when I was helping you. I do remember you had picked up another used controller to do HBA JBOD.

---

### Post by papriak on 2024-03-10
Thank you, MAFoElffen.

The backup server you helped me with is still going strong, but I've decided to upgrade it to an ECC motherboard.

Do you think I will benefit from upgrading my server's storage drives to SAS models, or should I stick with the SATA ones I'm currently using?  I ask because the server is powered off most of the week, and I hear spinning up is hard on SAS drives.

---

### Post by MAFoElffen on 2024-03-10
> **papriak said:**
> Thank you, MAFoElffen.

The backup server you helped me with is still going strong, but I've decided to upgrade it to an ECC motherboard.

Do you think I will benefit from upgrading my server's storage drives to SAS models, or should I stick with the SATA ones I'm currently using?  I ask because the server is powered off most of the week, and I hear spinning up is hard on SAS drives.
If you read that article I linked to, it relflects the current trends...

SAS drives are fast and dependable. But they are very spendy. Current trends seem to be shifting to replace SATA drives with SSD's.

SAS controllers and drives support up to 12 Gbps. Current SAT controllers now support 12 Gbps. NVMe are faster but the tech for storage sizes, and the drops in prices are just making them a viable options for more datacenters, business, and home NAS solutions. At the moment, I think SAS is loosing ground as not being as cost effective as it was once was for the benefits to be had. There are now other ways to do that.

Big business has been using a Datacenters full of server racks full of SSDs for over about a decade. They have to money to support that. My little brother worked for a major cable media network, had a large Datacenter fill of SSDs, with over 70 SSD's per 2u box... He sold me on using digital storage, and it's advantages.

That is what I am shifting to in what I do. My VMs storage pools are on ZRAID SSD and NVMe arrays. Gaming on that storage is wild.

There is still a use and place for HDDs. I use them for media server storage. It mostly is just reads. Then my background backups.

RE: [https://www.techtarget.com/searchstorage/feature/NVMe-SSD-speeds-explained](https://www.techtarget.com/searchstorage/feature/NVMe-SSD-speeds-explained)

---

### Post by papriak on 2024-03-10
You're not wrong about the article, but it didn't answer my biggest question either.

I want to know if accumulating power-ons and spin-ups will damage SAS drives over time.  I know their SMART keeps records of those, and don't want to be told they've gone bad because of it.

Also, I'd *love* to use SSDs for my storage pool, but 8 or so 4TB models aren't in my budget.  :P

---

### Post by MAFoElffen on 2024-03-10
So thinking about "recertified" SAS Enterprise drives? That might be a cost effective option if you could find a good used SAS Controller... You can find 20TB factory recertified Enterprize SAS drives for about $200 each. That comes out to $0.01 per GB.... Used for less.

SAS drives are more dependable and faster than SATA. Hands-down. No question about that. I had very few problems with SAS drives. Almost never. Note the almost. A few problems, but were very rare. Those rare instances were usually from something else that caused the error. (Connections. See Note at end...) With ZFS you have the added protection of COW.

You brought up SCSI... Years ago I used to have chained SCSI RAID tower arrays, that would help heat my house in the winter. LOL. They didnt make them very large so I had a lot of them. They were fast for the time, but took a while to spin up, were very noisy, and used lots of power. They sounded like an airplane starting up when they spun up. Things have progressed since then.

NOTE: That drive cage... is not robust and made for constant hot-swap use. It says it is hot-swap "capable", but the quality is not up there with more robust hot-swap cages... So the back-plane slot connectors are not as durable. You can see that in it's reviews. It is worth the cost they are charging. But in that area, you get what you pay for. It's still a good deal. Just a side-note on that.

---

### Post by papriak on 2024-03-10
The motherboard I want comes with an integrated 8-drive SAS-3 controller.

I actually have an old 4-bay SCSI tower, I gutted it and use it to house the power supply, DVD, floppy, and CF drives for my retro rig, which is in an old IBM 5160 shell.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293476&stc=1[/IMG]

---

### Post by MAFoElffen on 2024-03-10
LMFAO!!!

I think have those same old DELL SCSI Storage Towers in my storage! LOL. 

What do you put in them after gutting out their old SCSI back-plane? My curiosity is going on what might be possible for repurposing them...

---

### Post by papriak on 2024-03-10
> **MAFoElffen said:**
> LMFAO!!!

I think have those same old DELL SCSI Storage Towers in my storage! LOL. 

What do you put in them after gutting out their old SCSI back-plane? My curiosity is going on what might be possible for repurposing them...

In this case it was an ATX PSU, and DVD drive, dual floppy drive, CF to IDE adapter, and a storage drawer.

I imagine it would be easy to fit a pair of Raspberry Pi 5s with 4-port SATA hats into your Dell towers.

[https://radxa.com/products/accessories/penta-sata-hat/](https://radxa.com/products/accessories/penta-sata-hat/)

---

