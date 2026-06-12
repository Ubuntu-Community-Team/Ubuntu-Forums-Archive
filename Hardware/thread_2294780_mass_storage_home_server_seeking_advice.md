---
title: "mass storage home server seeking advice"
date: 2015-09-13
forum: Hardware
---

### Post by Drenriza on 2015-09-13
Hi all

I am in the middle of lining up the different parts i need for a home build mass storage server with up to 60TB of storage.

Unfortunately though i am not a hardware expert and are a bit stuck on a server motherboard since they don't come with 15 Sata ports :)
When you don't want hardware raid, what is a good / best way to expand the Sata ports beyond the motherboard?
I have looked after a few Sata expanders (don't know the official tech word), but have not found anything that i could use.

From what i have been told Supermicro makes EXECELENT server motherboards, but they are a bit cryptic in their site where i don't understand how they categorize their products.
And trying to get a official Supermicro agent to explain their categorizing system (Storage focus, I/O focus and a third unknown option) have left me with many outgoing mails and no incoming ones :/

The system i am planning to build is a storage server for my own home family picture and videos along with work related files and Git repos that i have for different projects.
I plan to use ZFS as the filesystem, where i haven't researched yet if Ubuntu / Debian fully supports this yet or if i should use FreeBSD.

I don't know any good dedicated mass storage server cases without it costing 2.000 - 2.500$, so at the moment i plan on using Corsair Obsedian 900D, which can hold fifteen 3.5" HDD's along with four 2.5" HDD's / SSD's.

I plan on running Samba with CIFS and Git on the server, no streaming from it. So it does not need to handle super intensive I/O work.

All and any advice are most welcome, since i have not build a mass storage system before.

Thanks on advance
Kind regards

---

### Post by TheFu on 2015-09-13
Find a FreeNAS build guide and follow that for hardware choices.  Supermicro boards seem expensive until you see the elements they have built in, which saves buying addon cards for commonly needed things-like a 2nd NIC. The key to ZFS is to use ECC RAM.  Most desktops do not support that.

For storage controllers, Supermicro AOC-SAS2LP-MV8 Add-on Card, 8-Channel SAS/SATA Adapter with 600MB/s per Channel has been recommended for ZFS use and the drivers are reported to be part of the Linux kernel.

I am wondering what you will do wht 60TB of storage. Do'nt forget that you **must** backup all that data too. So if you use ZFS with RAIDz2, you'll need well over 150TB of raw storage.

Lastly, I can recommend the disk enclosures from addonics.  Have one here that has been working non-stop since 2007.

---

### Post by Drenriza on 2015-09-13
> Find a FreeNAS build
No thanks.

> The key to ZFS is to **_use ECC RAM_**.  Most _**desktops**_ do not  support that.
What??

My 2 cent on ZFS key features. Their are probably more but these are the ones i know.

[LIST]
[*]Resolve data corruption without shutting the system down. 
[*]Live snapshots of data. 
[*]ZFS pools. 
[*]ZFS checksum data before writing it to disk. 
[*]ZFS burst write data to disks. 
[/LIST]

> I am wondering what you will do wht 60TB of storage
Family picture and videos along with work related files and Git repos

> Do'nt forget that  you **must** backup all that data too. So if you use ZFS with RAIDz2,  you'll need well over 150TB of raw storage.
I know their is a data consumption in raidZ as their is with any raid system unless for example raid 0, where their is a increase in speed for the cost of redundancy.

The end setup is going to be a mix or mirrors for speed and raidZ as needed for redundancy.

> For storage controllers, Supermicro AOC-SAS2LP-MV8 Add-on Card,  8-Channel SAS/SATA Adapter with 600MB/s per Channel has been recommended  for ZFS use and the drivers are reported to be part of the Linux  kernel.
Awesome thanks, i will look into that :)

---

### Post by TheFu on 2015-09-13
You asked for "advice" ...  > 
All and any advice are most welcome, since i have not build a mass storage system before.

The FreeNAS build was for hardware, not software.

ECC RAM is highly suggested by ZFS builders. Ignore that at the peril of your data. THERE IS A GOOD REASON. If you want to avoid data corruption, use ECC RAM. [http://hardforum.com/showthread.php?t=1689724](http://hardforum.com/showthread.php?t=1689724) is a discussion of pros/cons.

---

### Post by tgalati4 on 2015-09-13
I agree with TheFu's advice.  60TB is not a home server and thus requires business-grade hardware:  [http://www.freenas.org/hardware-requirements/#bizchw](http://www.freenas.org/hardware-requirements/#bizchw)

A home-built server with a bunch of SATA cards is like building your own fireworks.  An interesting exercise with the possibility of extreme damage.

---

### Post by Drenriza on 2015-09-14
> **TheFu said:**
> You asked for "advice" ...  

The FreeNAS build was for hardware, not software.

ECC RAM is highly suggested by ZFS builders. Ignore that at the peril of your data. THERE IS A GOOD REASON. If you want to avoid data corruption, use ECC RAM. [http://hardforum.com/showthread.php?t=1689724](http://hardforum.com/showthread.php?t=1689724) is a discussion of pros/cons.

We are probably talking past each other.

I am very grateful for all advice i can get and i take everything i am told, hear, read and so on into consideration.

A desktop / server is based (in my world) what you put in the case. In my initial post i write i am looking at Supermicro motherboards so the desktop was out of context with the rest of the thread
and their for confusion rise about what you are trying to communicate to me. Which lead me to the "what??" along with trying to state the few reasons to why i have chosen ZFS.

Note. I am a person who is being told (from time to time) that i come off as arrogant, which of course is all on me.
I am not trying to be so at all, and if that is the case i apologize for that. When i write out a list of reasons for why i have chosen ZFS its not because i am being
"look buddy", its my way of trying to communicate over a text media that i to some degree have thought about what i am considering.

> A home-built server with a bunch of SATA cards is like building your own  fireworks.  An interesting exercise with the possibility of extreme  damage.

True, also i am not saying that the case i have chosen is the right one or that i am in the right direction.
I am saying this is my initial thoughts which are very subtitle to change.

> An interesting exercise with the possibility of extreme damage
But i would ask what the problem would be with a good quality host bus adapter?

I have also looked at a 4U case, 24 3.5" from Supermicro with SAS backplates, but again Supermicro is very cryptic about how they categorize their products (performance I/O, storage + a unknown option).
Where i am having issues with the DK supplier that they wont deliver a standalone case, without me ordering the entire case + all hardware at the same time.

Which increase overall price and (i am guessing) if i than change the hardware configuration within the three years of warranty i forfeit it.
This would also imply adding more storage over time, since i don't need to max out the 24, 2.5" trays from day 1.

Moving and structuring the data i got now would take a great deal of time.

> Anything pre-build
Also if i go out and order everything pre-built, assembled and so on (trusting the good sales person) i will learn nothing.
Why is it exactly this motherboard over that one, is it the chipset, the construction, something else?
I will probably have a system that works but i will have NO idea as to why.

I like to know why my systems work so when they eventually break i have an idea of as to why, what is the issue and how do i fix it?
Can i do it myself or who do i need to contact.

It is not the most straight way, but for me its the way i learn.
And i work in that aspect with everything, instead of 3'rd party backup solution that i have no idea of how works or fit for me i learn the different aspects and build something myself.
Which give me the experience to be better prepared to problems that arise further down the road in my own or a 3'rd party solution.

Of course their are topics i don't touch because that would take a life time as when we are speaking of encryption, i pretty much trust the guys that know their stuff.

---

### Post by tgalati4 on 2015-09-14
The reason for going with a business-class, prebuilt box is testing.  Yes, you won't learn how to do it, but then you won't risk your data.  Having a file server blow up in your face is not pretty.  Losing your data is not fun.  

The reason vendors don't publish complete specifications is because 1.  They don't really know--hasn't been tested thoroughly, 2.  Competitive reasons--they don't want to expose weakness in their hardware.  That is something for you to discover. 3.  Some other reason I haven't thought of.

Perhaps ask the question in a different way:  "I want to purchase a SuperMacro Motherboard with a 16-port SuperSATA backplane to host my 60TB data pool.  Will it work?"

---

### Post by TheFu on 2015-09-14
> **Drenriza said:**
> Also if i go out and order everything pre-built, assembled and so on (trusting the good sales person) i will learn nothing.

Server builds aren't like desktop builds.  There are many more "compatibility issues" which is why people buy prebuilt configurations which have been tested together.  

It is like mixing network gear used to be - Cisco mixed with Bay-networks and Nortel often didn't "just work" - there would be odd failures - certain network features didn't work at all. If you didn't live through that, you haven't learned this lesson.

There is little incentive for HP, IBM, Dell, etc. to test their hardware compatibility with any hw from the competition except the leading network and storage vendors, so they don't.

In a prior job, they had a huge lab and tested all Intel server configurations to ensure compatibility. Certain model lines from highly reputable vendors would fail those compatibility checks, while others "just worked."  We needed Windows Server and Linux compatibility and didn't want to worry about which OS worked 3 yrs later when the server was repurposed and a different OS was loaded. 

If you want a largely used design - check out the BackBlaze built sheet. [https://www.backblaze.com/blog/user-builds-extreme-media-server-based-on-a-backblaze-storage-pod/](https://www.backblaze.com/blog/user-builds-extreme-media-server-based-on-a-backblaze-storage-pod/) - don't know about ZFS compatibility.

---

### Post by lukeiamyourfather on 2015-09-14
I think you're on the right track with ZFS for this purpose. I just built a file server for work with one of these and ST4000VN000 drives. In the past I've used ST4000DM000 and they work fine too. Using ZFS of course, note the IT mode controller it comes with instead of hardware RAID.

[http://www.supermicro.com/products/system/4U/6048/SSG-6048R-E1CR24L.cfm](http://www.supermicro.com/products/system/4U/6048/SSG-6048R-E1CR24L.cfm)

I've built several storage systems with Supermicro hardware running ZFS on Linux and I'm never disappointed. An older build is on my website.

[http://whenpicsfly.com/getting-to-know-zfs/](http://whenpicsfly.com/getting-to-know-zfs/)

As already pointed out ECC memory is mandatory for ZFS. Unlike other file system ZFS will store critical data in memory for extended periods of time, can be months or years if the system is up that long. This sounds like a design flaw but it's for various reasons including performance. The question people should be asking is why any modern computing device doesn't have ECC memory as pointed out by James Hamilton.

[http://perspectives.mvdirona.com/2009/10/you-really-do-need-ecc-memory/](http://perspectives.mvdirona.com/2009/10/you-really-do-need-ecc-memory/)

---

### Post by Drenriza on 2015-09-15
> Perhaps ask the question in a different way:  "I want to purchase a  SuperMacro Motherboard with a 16-port SuperSATA backplane to host my  60TB data pool.  Will it work?"

I 100% agree, but you need to know what you want to ask before you can ask it. I don't know 100% want i want to ask from my initial post and their for i can only ask what i know in that point in time.
Down the road i than get more and more experience and would at a later point in time be able to ask the question as you netly type above.

Thanks for your reply @lukeiamyourfather
Awesome with the links and your experience.

How did you connect the drives from your Dallas Makerspace build? Directly to the MB or?

Courious. Anyone who has experience with a Sata / SAS HBA?
Link purely for example
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816118142](http://www.newegg.com/Product/Product.aspx?Item=N82E16816118142)

---

### Post by mastablasta on 2015-09-15
> **TheFu said:**
> Server builds aren't like desktop builds.  There are many more "compatibility issues" which is why people buy prebuilt configurations which have been tested together.  

There is little incentive for HP, IBM, Dell, etc. to test their hardware compatibility with any hw from the competition except the leading network and storage vendors, so they don't.



+++++++++

You would want data to be as safe as possible on backup server.

and on a side note - what about BTRFS? still too immature compared to ZFS?

---

### Post by lukeiamyourfather on 2015-09-15
> **Drenriza said:**
> How did you connect the drives from your Dallas Makerspace build? Directly to the MB or?

The specific motherboard used for the build at the Dallas Makerspace has 12 SATA ports on the motherboard so those were used. The board is perfect for a low power and low cost ZFS file server but I don't know that I'd throw more than that at it.

> **Drenriza said:**
> Courious. Anyone who has experience with a Sata / SAS HBA?

I use a Supermicro AOC-SAS2LP-MV8 at home. It's a SAS HBA for around $120 with a Marvell chip. I like it because it's supported by Ubuntu 14.04 LTS and CentOS 7 out of the box and it's relatively inexpensive. I connect drives directly to it with these cables but it could connect to a backplane instead of directly to drives if needed.

[http://www.amazon.com/gp/product/B001L9DU88](http://www.amazon.com/gp/product/B001L9DU88)

---

### Post by TheFu on 2015-09-15
> **mastablasta said:**
>  what about BTRFS? still too immature compared to ZFS?

I do not consider BTRFS to be production ready. Nothing is more important to me than data.  Hardware like disks, computers, and network stuff can all be replaced. Data cannot. Many others have a different opinion.

Plus - btrfs has known performance impacts to virtual machine storage: [http://www.linux-kvm.org/page/Tuning_KVM](http://www.linux-kvm.org/page/Tuning_KVM)  I/O freeze has been reported.

---

### Post by lukeiamyourfather on 2015-09-15
> **mastablasta said:**
> and on a side note - what about BTRFS? still too immature compared to ZFS?

There are some similarities and feature overlaps but the design goals are fundamentally different. ZFS is more focused on data integrity and scalability than Btrfs. For example 32-bit versus 256-bit checksums, up to two parity stripes with no higher level geometry versus up to triple parity stripes with dynamic striping across multiple VDEV, 16EB volume limit versus 256ZB volume limit (ZB>EB>PB>TB), and performance features like the ARC and L2ARC. I think Btrfs is a great thing happening and it will make a great successor to ext4 and that's a huge achievement and very important for Linux so don't get me wrong, I'm not not dogging Btrfs. Since we're talking a project that will require dozens of drives I think it's beyond what Btrfs was designed for though it'd probably work just as good as other options like hardware RAID or Linux software RAID. In my opinion ZFS is a better option though.

> **TheFu said:**
> I do not consider BTRFS to be production ready. Nothing is more important to me than data.  Hardware like disks, computers, and network stuff can all be replaced. Data cannot. Many others have a different opinion.

The on disk format for Btrfs is stable but the other aspects are still in development. I think there's relatively low risk of losing data but somewhat of a risk of operations being halted or slow by other problems in the software stack. ZFS on Linux is in a similar place where the on disk format is stable but it still has some bugs that can cause deadlocks and other problems. I haven't personally experienced any problems like that but I know they are out there since the release notes for each new version of ZFS on Linux mention them. The benefit with ZFS at least for now is the feature set is much larger and if uptime is critical the entire ZFS software stack is very stable on other platforms (illumos and FreeBSD).

---

### Post by Drenriza on 2015-09-17
> **mastablasta said:**
> +++++++++

You would want data to be as safe as possible on backup server.

and on a side note - what about BTRFS? still too immature compared to ZFS?

Thanks for the input @mastablasta.
I am not aware of BTRFS, what is the advantages over ZFS?

Edit, added information to above question.
> There are some similarities and feature overlaps but the design goals  are fundamentally different. ZFS is more focused on data integrity and  scalability than Btrfs. For example 32-bit versus 256-bit checksums, up  to two parity stripes with no higher level geometry versus up to triple  parity stripes with dynamic striping across multiple VDEV, 16EB volume  limit versus 256ZB volume limit (ZB>EB>PB>TB), and performance  features like the ARC and L2ARC. I think Btrfs is a great thing  happening and it will make a great successor to ext4 and that's a huge  achievement and very important for Linux so don't get me wrong, I'm not  not dogging Btrfs. Since we're talking a project that will require  dozens of drives I think it's beyond what Btrfs was designed for though  it'd probably work just as good as other options like hardware RAID or  Linux software RAID. In my opinion ZFS is a better option though.

Edit, added information to above question.
> 
[QUOTE]
btrfs has known performance impacts to virtual machine storage: [http://www.linux-kvm.org/page/Tuning_KVM](http://www.linux-kvm.org/page/Tuning_KVM)  I/O freeze has been reported.

The on disk format for Btrfs is stable but the other aspects are still  in development. I think there's relatively low risk of losing data but  somewhat of a risk of operations being halted or slow by other problems  in the software stack. ZFS on Linux is in a similar place where the on  disk format is stable but it still has some bugs that can cause  deadlocks and other problems. I haven't personally experienced any  problems like that but I know they are out there since the release notes  for each new version of ZFS on Linux mention them. The benefit with ZFS  at least for now is the feature set is much larger and if uptime is  critical the entire ZFS software stack is very stable on other platforms  (illumos and FreeBSD).
[/QUOTE]

@[**[COLOR=#000000]lukeiamyourfather[/COLOR]**]("http://ubuntuforums.org/member.php?u=774656") (awesome name btw) thanks for the reply and the link!

---

### Post by Drenriza on 2015-09-21
Hi all

So far, thanks for all the suggestions, sharing of experience and suggestions it is all highly appreciated!

I have given the ZFS setup some more thought and hoping to hear your thoughts on the subject.
More specifically its how to best handle the second level cache, which in my understanding is ZIL (write cache) and L2ARC (read cache).

Apparently a lot of systems are using SSD disks with mirror because of the blazing fast speeds in read and write, unfortunately though SSD's degrade over time in the loss of transistors
as they are written to.

The ZIL and L2ARC (as i understand) is a intermediate device / devices for slower spindle disks where it act as a buffer zone (meta data) for temporarily storing data until they
can be written to the permanent storage disks and get an acknowledgement back that the data has ACTUALLY been written or sent to the client / clients that requested the data (network bottle-neck?).

As everything that is written and read to / from the storage area goes through this intermediate device i am wondering if SSD disks is the right way to go unless i frequently want to swoop them
out (thats how it works in my head).

So the question is, to SSD or not to SSD?

If to SSD what is your experience with how fast you're killing them off? Environment for the slaughter and disk quality?

If not to SSD i am thinking _**one could**_ hardware raid (entire out around of ZFS) with a battery pack and use spindle disks in the 10.000 RPM area, in a raid 10 solution with a spare disks or two at hand for the "Oowww F(#!" moment.
But what do you think about that solution?

I know that if you don't specify a separate device for the second level cache, one is created in the zpool / zpools. But this would severely slow down the entire pool as its filled.

Thanks to all who takes the time to read / reply.
Kind regards

---

### Post by lukeiamyourfather on 2015-09-21
Using a SLOG for the ZIL is optional. The SLOG is a dedicated device or devices for the ZIL. Without a SLOG in the system ZFS will use a small section of the pool for the ZIL. The ZIL is used only for synchronous writes which most software doesn't ask for. In a home setting with mostly multimedia I wouldn't worry about a SLOG because nothing would ever ask for synchronous writes in that scenario. It's typically used in environments where knowing that a write operation failed is critical (like financial transaction information).

The L2ARC is an extension of the ARC (which is in system memory) which stores metadata, frequently accessed blocks, and recently written blocks. This speeds up some reads because the system doesn't have to hit the spinning disks. The L2ARC matters more when there are many clients or a workload with high IOPS requirements. In a home setting this is unlikely to make a noticeable difference given there's enough memory in the system for a reasonable ARC. In your case that'd be something like 16GB to 64GB of memory.

For what it's worth at home I don't have a L2ARC or SLOG setup but I do have them in systems built for work where there are multiple clients accessing them. If you want a SLOG and L2ARC for whatever reason then SSD is definitely the way to go. A Samsung 850 Pro 512GB model has a 10 year warranty or 300 TBW warranty which is more than plenty unless you plan to push a petabyte of data through the system. Using two SSD is common where there's a small partition for the SLOG on each SSD and they are mirrored and then a large partition for the L2ARC which is a stripe. The mirror is in case power is lost before a write and one of the SSD dies. The L2ARC is not mirrored because it's just a duplicate of data already in the pool. The number of SSD can grow from there depending on the performance needs of the system, there are also just straight up pools made with SSD.

---

### Post by tomkk on 2015-09-25
I'll drop my 2p here as well.

So:

There is a plenty of advice on using a supermicro motherboards, and for your setup of 60TB this actually sound as a very good advice - there is plenty of workstation mobo that give you a bunch of sata but to my own avail I've found that for example my setup with z9pe-d8 ws has a marvel controller which creates more problem than a gunshot whole in the mobo :( Seriously this can (and very often will) corrupt your kernel mid-flight not mentioning the data. But reson I'm using it is I need performance as well as storage capacity (a workstation performance and ample of storage at the same time).

In terms of ECC ram - it's an absolute must, trust me, when you care about your data - single most prone to f*** up place is your ram. I've had corruptions with non ecc ram and learned my lesson (more about that soon).

BTRFS - I seriously don't understand the phobia in society about this file system ... ofcourse they state that it's not production ready, but this to my mind is mostly because they don't want to eligible for loss of data and make ORACLE a bad name. Bare in mind, it's oracle that pays for the whole gig. BUT just ask your self, if it's not production ready why oracle is using it as default file system ??? I've been running BTRFS since it had a label given by Chris "it may kill your dog and shag your wife" and upgraded my storage several times to currently 20TB raid 10. Still have my data ... right ? Of course you will encounter issues, but this is true with any file system, anybody remembers "zero bug" on etx4 ? that was a masterpiece of f*** ups, even ZFS has it's issues. 

But seriously, zfs is ok ... but btrfs is in my mind a lot better. It's less resources hungry, it got active community - even Chris Mason, a blody henchman of this file system helped me diagnose that I've got a huge (2MB) hole in my non ecc ram that was inverting bits ONLY under heavy load that was not discovered on memtest with his "helpfull friend fs_stress.sh". Also (yes this will upset a lot of people) last time I checked it:
- zfs is sloooooooow on linux :/ in my tests on stock ubuntu it was not keeping up with (broken in terms of performance at the time) xfs
- zfs needs so much ram, you might as well setup another partition in ram running btrfs and booting from that :)
- zfs is not native on linux (main reason for slowlnes) 
- zfs is not really open source, this and previous point main cause that if you update to new kernel you may find your self with inaccessible array

ZFS IS DEAD ! (yeah, this will start a biggest flame war in decade :) maybe even bigger than systemD. Don't get me wrong, solaris is maybe steaming away with their own platform but since you want to use linux - consider it dead, support is bad, openZFS more or less stinks, if you plan to keep your data for longer than few years, you might wake up with the fact that nobody else is using in: so don't jump on a sinking ship, sail by on btrfs ship with big smile.
If you want you can read some comments of developers of ZFS here:
[https://www.flamingspork.com/blog/2012/05/28/zfs-could-have-been-the-future-of-unix-filesystems/](https://www.flamingspork.com/blog/2012/05/28/zfs-could-have-been-the-future-of-unix-filesystems/)


Also, don't believe a word about this "slowness in WM" - it's rubbish! I'm using my storage / WS box as a ios dev box, and coincidently I run OSX Yosemite in WMware ... when I plug a pendrive (sandisk that can do 220 MB/s raw write performance) I get ~160 MB/s from inside of virtual machine to this pendrive formatted as HSF+ ... and this is not some buffers tainting results, this is shifting 25GB of bunch of medium size files. And no, my WM disk has no "nocow" flag set etc ... it's runnind as normal. 
(BTW it's vertex 3 BUT sitting on sata 2 controller)

[flame off] :)

Also nobody seems to state anything about how power hungry your machine will be, consider that ... it's going to be your main heater at home with toys that you plan to include. If you don't play your cards right, your setup (if left on 24/7) will cost you double in power usage.

---

### Post by lukeiamyourfather on 2015-09-26
> **tomkk said:**
> - zfs is sloooooooow on linux :/ in my tests on stock ubuntu it was not keeping up with (broken in terms of performance at the time) xfs

The FUSE implementation is very slow. ZFS on Linux is a kernel module and is very fast. Which are you referring to?

> **tomkk said:**
> - zfs needs so much ram, you might as well setup another partition in ram running btrfs and booting from that :)

There's a trade off which is performance. Well worth it in my opinion but YMMV.

> **tomkk said:**
> - zfs is not native on linux (main reason for slowlnes) 

It's not native to Linux due to licensing (GPL doesn't allow CDDL). In other words a completely non-technical reason. Again, ZFS on Linux isn't slow.

> **tomkk said:**
> - zfs is not really open source, this and previous point main cause that if you update to new kernel you may find your self with inaccessible array

ZFS on Linux is open source as are most other implementations of ZFS with a few exceptions (like Oracle). Other former Sun projects that become closed source were forked in a similar way (like Grid Engine).

> **tomkk said:**
> 
ZFS IS DEAD ! (yeah, this will start a biggest flame war in decade :) maybe even bigger than systemD. Don't get me wrong, solaris is maybe steaming away with their own platform but since you want to use linux - consider it dead, support is bad, openZFS more or less stinks, if you plan to keep your data for longer than few years, you might wake up with the fact that nobody else is using in: so don't jump on a sinking ship, sail by on btrfs ship with big smile.
If you want you can read some comments of developers of ZFS here:
[https://www.flamingspork.com/blog/2012/05/28/zfs-could-have-been-the-future-of-unix-filesystems/](https://www.flamingspork.com/blog/2012/05/28/zfs-could-have-been-the-future-of-unix-filesystems/)


That link is over three years old. ZFS on Linux is hardly dead. The last stable release was six days ago, yes, literally six days ago.

[http://zfsonlinux.org/](http://zfsonlinux.org/)

The greater OpenZFS community is alive and well and very active. Saying it's dead is misinformed to say the least.

---

