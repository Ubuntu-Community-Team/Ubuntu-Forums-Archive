---
title: "Need help with buying linux hardware"
date: 2009-12-25
forum: Hardware
---

### Post by chadhenry on 2009-12-25
Hi all,

I'm fairly new to linux and I'm looking for some help in buying linux compatible hardware. I would appreciate any input from the community since I haven't been able to find definitive and detailed info from google searches. I'm looking to either buy a prebuilt system or build my own

Here are my needs and plans:

I'm looking to run UBUNTU SERVER on a desktop setup with several virtual environments (vmware server) including ubuntu desktop, windows xp and 7 and possibly centos, fedora and mandriva for testing and possible adoption - 64bit versions will be ideal. All my computers are currently windows based but I'm looking to switch to linux for many reasons.    

This setup will be mainly used as a testing platform for website and web application development, as well as a storage system for my home network that will eventually allow remote access. 

I've looked at Dell under their linux systems but I can't seem to find linux desktops - just expensive servers.

I would love to spend less than $1,000 for a system, with $500-$750 being the sweet spot, however, I need the system to be able to handle all the virtual environment loads as well as being cross compatible with all the environments. 

Can the community please offer me some advise into prebuilt systems, or hardware I should buy to built my own system? I need the system to be reliable for at least the next 3 years, so up-to-date hardware is a must. I also need a minimum of 6GB RAM and I'm looking into buying an SSD for the bootup and application system. I've been looking into core i7's but they seem to significantly increase the cost of the overall system due to their special hardware needs.

Any help would be greatly appreciated! Thank you!

---

### Post by sliketymo on 2009-12-25
System76,TuxMachines are two off the top of my head.

---

### Post by Bucky Ball on 2009-12-25
Try the Ubuntu-friendly computer build link in my signature for some ideas.

---

### Post by chadhenry on 2009-12-25
@sliketymo - thanks for the info, I'll be looking more closely at system76

@Bucky - Thanks for your lengthy post I'll be looking into some of the hardware you suggested. Unfortunately, and AMD processor isn't going to work for me as some of the software I need to run will only work with Intel hardware. I like that fact that you suggested low energy hardware - especially useful for me since this box will be running nearly 24x7.

I agree with your statement: "[FONT=Comic Sans MS][SIZE=2]Why don't manufacturers label their products as compatible with Linux[/SIZE][/FONT]" - it's really a shame and I hope more manufacturers start adopting the linux system.

Any other suggestions from the community?

---

### Post by cascade9 on 2009-12-26
There are Dells that fit your pricing, and not expnives servers. I've never been fond of dell, so I only point that out cause it would be dishonest not to ;) 

For the $500-750 mark, i7s are probably a bit hard to get. The cheapest i7 CPU is over $275, thats a lot of your budget gone on just a CPU. 

For that price range, AMD is a better choice, but you've said this- 

> **chadhenry said:**
> @Bucky - Thanks for your lengthy post I'll be looking into some of the hardware you suggested. Unfortunately, and AMD processor isn't going to work for me as some of the software I need to run will only work with Intel hardware. I like that fact that you suggested low energy hardware - especially useful for me since this box will be running nearly 24x7.

Its been a very long wsince I've heard that. What software are you planning on running that is Intel only? 

BTW, do you want windows with the system? I would assume that since your looking at system76 you dont want windows...or at least don't want windows preinstalled. Do you want a monitor as well? 

Also, would you prefer a pre-built system, or are you happy enough to build your own?

---

### Post by chadhenry on 2009-12-26
@cascade9 I have no problem building my own system, the only problem is I'm fairly new to linux systems so I don't know what hardware is compatible without jumping through a lot of hoops to get drivers working correctly.

The only reason I have asked about pre-built system is, I would have thought some of the bigger manufacturers could have built a good system for cheaper than I could since they have the buying power to purchase hardware cheaper than the end consumer can. However, that doesn't seem to be the case - at least from what I've seen so far.   

I could care less if the system comes with or without a copy of windows installed. I plan to run ubuntu server as the core operating system and then have my copy of windows xp and 7 installed as virtual environments for testing platforms of my development applications. I don't plan to use windows as my day-to-day OS - unless ubuntu desktop doesn't live up to my expectations and needs.

My main concern is to have a system powerful enough to run a minimum of 4 virtual environments at the same time. A monitor is not factored into my price range since I have plenty to spare for this box.

---

### Post by cascade9 on 2009-12-26
I thought that you might like the system to come with windows as its a lot cheaper to get it that way. 

To cut a long story short- you shouldnt have problems with any of the current AMD/Ati or Intel chipsets. As far as I know, none of them have any major issues with linux. For video, your either looking at intel intergrated (slow, but should work without drivers on linux systems), ATI or nVidia. nVidia has slightly better linux support, but ATI support is getting better, and should contunire to do so. HDDs, DVD drives, SSDs, etc should have 0 issues. 

About the only things you might run across that will give issues are wireless (some have good support, some of them 0 support) and hardware RAID (same thing). 

For your needs, I would be looking at some quad core CPU. If it was me, I would be getting either- 

Intel Core 2 Quad Q9550. (2.83Ghz, 12MB) 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115041](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115041)

Yeah, its not cheap ($250) but tis got 12MB cache, that is really going to help. There are cheaper Intel quads around but they have less cache (e.g. Q9505- 2.83Ghz, 6MB, $230)(Q9400- 2.66Ghz, 6MB, $190)(Q8300- 2.66, 4MB, $180). 12MB cache is more than the i7s! 

You could also check the Phenom IIs unless your sure your stuff in Intel only.   

Phenom II 965 (3.4Ghz, 8MB)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103692](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103692)

I can see what you were trying to do by checking Dell, etc, but in my experience you can biuld your own cheaper than dell. that can depend however. If you were looking for somethign with a quadcore (non-i5 or i7) and no monitor look a the studio desktop-

[http://www.dell.com/us/en/home/desktops/desktop-studio-mini/pd.aspx?refid=desktop-studio-mini&s=dhs&cs=19&ref=dthp](http://www.dell.com/us/en/home/desktops/desktop-studio-mini/pd.aspx?refid=desktop-studio-mini&s=dhs&cs=19&ref=dthp)

With a Q9550, 6GB, Intel intergrated graphics, windows 7 home premium (cant remove), no monitor, 500GB SATA drive, keyboard and mouse (cant remove) = $784

I'm 99% sure that can be beaten buy buying from newegg (or possibly somewhere else, I'm not up on the US stores) and building it yourself.

---

### Post by chadhenry on 2009-12-26
@cascade9 - the intel core 2 quad that you mention is exactly the one I've been looking at instead of going with the core i7, I'm also looking at the Geforce 9500GT 1GB since I'm planning to use dual monitors and also need decent graphics for Adobe CS4 within wine.

My only question is this: I'm planning to use an SSD for the OS and other applications - including a LAMP stack. The only problem is the SSD size will only be 80 GB (Intel) or 128GB (corsair P series). Is it possible to RAID an SSD to a Western Digital Caviar 1 Terabyte to increase the storage size?    

Thanks for the help!

---

### Post by cascade9 on 2009-12-26
> **chadhenry said:**
> @cascade9 - the intel core 2 quad that you mention is exactly the one I've been looking at instead of going with the core i7, I'm also looking at the Geforce 9500GT 1GB since I'm planning to use dual monitors and also need decent graphics for Adobe CS4 within wine.

My only question is this: I'm planning to use an SSD for the OS and other applications - including a LAMP stack. The only problem is the SSD size will only be 80 GB (Intel) or 128GB (corsair P series). Is it possible to RAID an SSD to a Western Digital Caviar 1 Terabyte to increase the storage size?    

Heh, 'great minds think alike'. Hopefully we both have great mind then, eh? :lolflag:

You can RAID an SSD to a HDD, but you wont get what you want. RAID size is the size of the smallest disc (so in this case you would 160 or 256GB). I'd run /root and /home on the SSD, swap and data partitions on the HDD (which is what you were basically saying, just stated a different way). 

To be honest, I have no idea how much extra core speed and memory will help with CS4, especially under WINE. 

> **chadhenry said:**
> Thanks for the help!

No problem, any excuse to look at more 'hardware porn' LOL 

BTW, for your info (and anybody else reading this thread) I said go with the Q9550 over an i5/i7 in part because of teh extra cache, but also because i7 (LGA 1366) needs more expensive triple channel RAM, and more expensive motherboards. i7 and i5 on LGA 1166 only needs dual channel RAM, so its the same cost as for LGA 775, but the boards are more expensive than the LGA 775 (cheapest LGA 1166 is $90 at newegg, cheapest  LGA 775 $40)

---

### Post by chadhenry on 2009-12-26
> You can RAID an SSD to a HDD, but you wont get what you want. RAID size is the size of the smallest disc (so in this case you would 160 or 256GB). I'd run /root and /home on the SSD, swap and data partitions on the HDD (which is what you were basically saying, just stated a different way).You lost me here... I'm not the best at partitioning and running applications across multiple drives. Can you explain how to do this this in a bit more detail? Figuring out how to get an AMP stack and ubuntu desktop to work across two different drives is giving me a bit of a headache. Thanks again for your help!

---

### Post by cascade9 on 2009-12-26
Its pretty easy. When you start to install ubuntu, you will just follow the 1st few screens (select language, install ubuntu, select location, select keyboard layout,). Then you will get to the 'partitioning' selection screen. 

Choose 'select partitions manually'.

/dev/sda is the 1st hdd (normally channel 0) and /dev/sdb is the 2nd hdd (normally channel 1). It wont matter which drive is sda and sdb. Lets just say that the SDD is /dev/sda and the HDD is /dev/sdb. 

Since you will be installing totally fresh, they both will be empty. You should be able to tell what hdd is which just from the amount of free space on the drives. Thye both should appear as just 'free space'

Select /dev/sda 'free space' and then click the 'add' button. Make it 'primary', give it a size (say, 15GB, thats a good size for /root), make it the 'beginning' of the drive, filesystem 'EXT4', make the mount point '/'. Thats the 'root' file system (similar to C: on windows, its where you system files are stored). You have just made the '/root' partition. 

Now, you should have soem free space left on the SSD. Click on 'free space' again, and 'create partition' again. Again, 'primary', use all the remaining space, make it the 'beginning' of the drive, EXT4, make the mount point '/home' (this is where ubuntu keeps some program data, and the linux of 'documents and settings' and 'desktop' in windows) 

You now have / and /home defined. 

Move on to sdb. 

Same thing again, but make it a 'swap' partition. If you have 6GB RAM, and for heavy, sever use, I would go for somewhere around 8-12GB.

For the rest of the space on sdb, you can cut it up into several partitons, or have just 1. Its up to you and what you prefer. Also, since its not a 'core' filesystem, you can use any one of several mount points for the extra partitions. I use /mnt/data, /mnt/archive, /mnt/media myself. I'm sure that other people will have different ideas, but thats just how I do it. these extra partitions are linux versions of D:, E:, etc. 

If you setup the rest of the drive as /mnt/data, this is how it should look

/dev/sda1 EXT4 /  
/dev/sda2 EXT4 /home  
/dev/sdb1 swap
/dev/sdb2 /mnt/data. 

BTW, it wont matter if you stuff it up....I know I did the 1st few times I did this. I was 'flying blind', so to speak, so hopefully you will get it right the 1st time..but if not, just reboot the CD and reinstall it. You will probably have to delete the partitions you already have (its a similar process, just for example click on /dev/sda1 and hit 'delete', etc). 

Hopefully that helps. Its just a rough idea, and no doubt I've got soem detail wrong, but honestly..if your smart enough to setup virtual enviroments then you should be able to muddle through it.

BTW, here is afew screenshots of the process. It doesnt screenshot the actual 'manual partitioning' bit, but it gives you an idea of how things look,etc.

---

### Post by chadhenry on 2009-12-26
@cascade9 - awesome! Thanks for your clear instructions. It seems to be pretty easy, I just have to get used to ubuntu's file structure and play around with it a bit. I'll be ordering my hardware and installing over the next week. Thanks for all your help!

---

### Post by RyanA804 on 2009-12-26
hi. i just randomly came across this post looking for hardware compatibility in the forums, and wanted to put in my 2 cents.

i've been shopping for components for about the last 12 hours for 2 pc's that i'm building (1 media box, 1 for a friend), and although i'm building lower-end budget pc's, i've notices a couple trends.

1. DDR2 is on its way out. prices have been on the rise for DDR2 lately, and it's because companies are making the switch to DDR3. both are about the same price now, but DDR3 will continue to get cheaper as it takes over, and DDR2 will continue to get more expensive. so if you, like me, plan on upgrading in the future, make sure you go with DDR3 now. or you might not be able to upgrade in the future.

2. intel is in a time of transition. the LGA775 was there predominate socket for a few years, but now with the i7's, etc, coming out, there are multiple socket choices. i haven't been following this that closely, but again, if you're looking to upgrade in the future, you might be stuck with a cpu socket that didn't catch on. so you might not be able to upgrade with buying a new mobo. also, during that time of transition you're not getting the optimal price. so it's just bad timing to buy intel. at the same time, amd seems to have settled into their AM3 socket nicely. there are affordable options (i'll be getting the athlon II x2 250 regor 3.0GHz dual-core) and high-end options that offer tested and stable over-clocking.

it seems to be a good time for DDR3 and amd's am3 series both for price vs. performance and for future-proofing. it's all cyclical, and this will probably all be wrong next year, but those are definite trends that jumped out at me when shopping on newegg and reading hardware review sites.

---

### Post by chadhenry on 2009-12-26
@Ryan - Thanks for your input. I agree with you about the RAM. It's something I've been weighting heavily. I'm a bit hesitant to buy AMD only because I haven't seen many multi-visualized systems using anything other than Intel hardware. To me AMD hasn't proven their power for visualized environments - but then again, i could be wrong.  

If you can, would you mind posting your component specs for both systems when you buy?

Thanks!

---

### Post by cascade9 on 2009-12-27
> **RyanA804 said:**
> hi. i just randomly came across this post looking for hardware compatibility in the forums, and wanted to put in my 2 cents.

i've been shopping for components for about the last 12 hours for 2 pc's that i'm building (1 media box, 1 for a friend), and although i'm building lower-end budget pc's, i've notices a couple trends.

1. DDR2 is on its way out. prices have been on the rise for DDR2 lately, and it's because companies are making the switch to DDR3. both are about the same price now, but DDR3 will continue to get cheaper as it takes over, and DDR2 will continue to get more expensive. so if you, like me, plan on upgrading in the future, make sure you go with DDR3 now. or you might not be able to upgrade in the future.

I dont think its so much DDR2 is getting more expensive as DDR3 has dropped to similar prices to DDR2. If I was after a new machine, for sure I would be looking at DDR3. But DDR2 should be avaible for a long time yet. You can still buy SD-RAM and DDR1 new these days. But you will be paying more the older the RAM type is. 

> **RyanA804 said:**
> 2. intel is in a time of transition. the LGA775 was there predominate socket for a few years, but now with the i7's, etc, coming out, there are multiple socket choices. i haven't been following this that closely, but again, if you're looking to upgrade in the future, you might be stuck with a cpu socket that didn't catch on. so you might not be able to upgrade with buying a new mobo. also, during that time of transition you're not getting the optimal price. so it's just bad timing to buy intel. 

I wont go into detail on the whole LGA 1166/1366 'market split' (which is something totally new IMO). Neither type should disappear that soon, but if you go for LGA 1366 you pay a LOT for it (triple channel RAM is not cheap, the motherboards are not cheap either). Its typical Intel, getting as much money as possible for its 'top of the line' gear. Fair enough, Intels in this to make money not solve world hunger LOL. LGA 1166 is cheaper, but you might well be stuck with getting 'lower end' stuff for the life of the socket. Like locking people into buying celerons (yeah, I know i5 and LGA 1166 i7s are not celerons, its not a perfect analogy) 

However, in the interest of fairness, thats for the future upgrade market. LGA 775 is very mature, and with the new stuff coming out prices for LGA 775 (on CPUs and motherboards) are dropping. If you get a top-end CPU and a large amount of RAM, (which is what chadhenry is looking at in LGA 775) upgrading isn't really that much of an option. 

> **RyanA804 said:**
> at the same time, amd seems to have settled into their AM3 socket nicely. there are affordable options (i'll be getting the athlon II x2 250 regor 3.0GHz dual-core) and high-end options that offer tested and stable over-clocking.

it seems to be a good time for DDR3 and amd's am3 series both for price vs. performance and for future-proofing. it's all cyclical, and this will probably all be wrong next year, but those are definite trends that jumped out at me when shopping on newegg and reading hardware review sites.

AMD has always had very good price/performance, and currently its as good, if not better than its ever been. Pity that the fastest AMD (non-opteron servers anyway) is the Phenom II 965. Still, the 965 is very fast, and at $200 US or less, its a bargin compared to the i5s and i7s. 

IMO, AMD has always had a better upgrade path. AM3 CPUs will actually work in (at least some) AM2 boards, and will work fine in almost all AM2+ boards. I actually have a AM2+ board myself, and I'm planning on getting a Phenom II 9xx sooner rather than later (still got a AM2 4800+ in here so thats going to be a  major speed increase). 

BTW, as far as I know, AMD is planning on releasing 'thuban' (6 cores, 45 NM porcess) and 'zambezi' (4/8c cores, 32 NM process) on AM3. (as well as 'lower end CPUs'). So AM3 should remain around for at least another 2 years, minimum. 

[http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3673&p=2](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3673&p=2)

> **chadhenry said:**
> @Ryan - Thanks for your input. I agree with you about the RAM. It's something I've been weighting heavily. I'm a bit hesitant to buy AMD only because I haven't seen many multi-visualized systems using anything other than Intel hardware. To me AMD hasn't proven their power for visualized environments - but then again, i could be wrong.  

If you can, would you mind posting your component specs for both systems when you buy?

Thanks!

Its a really pity that VMwares 'VMmark' benchmarks are not more common. Its something I would like to see more hardware reviews using. But in case you are interested, there is a list of setups benchmarked on the VMware site. Its not user friendly, its very server oriented (the main page only has down to 2 CPU systems, and goes right up to 16 CPU/64 core serveres!). They dont even have the CPU type listed on individual scores, its really just a list. AMD has quite a few CPUs in the list though- 

[http://www.vmware.com/products/vmmark/results.html](http://www.vmware.com/products/vmmark/results.html)

BTW, the "HP ProLiant" systems are AMD opterons. Everything that isnt opterons (which is pretty much everything) are Intel Xeons.

---

### Post by Bucky Ball on 2009-12-28
> **chadhenry said:**
> @Ryan - Thanks for your input. I agree with you about the RAM. It's something I've been weighting heavily. I'm a bit hesitant to buy AMD only because I haven't seen many multi-visualized systems using anything other than Intel hardware. To me AMD hasn't proven their power for visualized environments - but then again, i could be wrong.  



I think you mean virtualisation and AMD CPUs have been built with virtualisation since just about the start. Streets ahead of Intel at the time.

---

### Post by chadhenry on 2009-12-28
@Bucky - yes I did mean virtualisation - dumb spell checker plugin for firefox messed that up!

I'm aware that AMD has had that feature for a long time. I just don't see many higher-end servers using AMD. My concern was how many virtualized environments an AMD processor could handle. I'm going to have 6-10 most likely and from people I've talked to, only Intel hardware could handle that many environments at one time. 

I don't want to go with dual xeon processors like many 'real' servers have, due to the added expense, so I'm looking for the best alternative using a single processor.

I don't know much about hardware capabilities so I could be wrong about this.

---

### Post by steveneddy on 2009-12-28
Just some observations from the thread so far:

You need the server edition just to run some other OS's in a VM? Are you serving them to tiny clients? Or using them locally on that machine only? Just curious.

You're going to run a server but don't understand partitioning? You understand that the Ubuntu Server edition doesn't come with a GUI? It is possible to install the GUI on the server edition.

Why would you blame the spell checker in Firefox for spelling a word wrong? Didn't you choose the word for it to use? Just an observation. 

Remember:

> GIGO

It just seems like there is some basic missing knowledge here, but I suppose that if you get this project up and running you will gain this needed knowledge during the course of the build.

I recommend System76 hardware. I've used many of their laptops over the years and will order another next year for myself. I'm sure that their server hardware would be of the same build quality. Customer service at System76 rocks.

To the OP, please post back here or start a new thread for each obstacle that you encounter and don't forget to search the forums for your question first because it probably have been asked before. What you are about to attempt has been done before and it you search the forums, especially the Server Platforms section of UF you may find useful info to help you in your quest to set up a server and keep it running. You may find that if you aren't going to serve the VM's to other machines on the network that you may not need the server edition.

I'm not judging you, just some simple things to point out to you. 

* Understand where you are going.

* Don't blame the software for your mistake.

* Research the next step before taking the next step. 

This is just my .02

---

### Post by cascade9 on 2009-12-28
@ steveneddy- LOL, yes, good points. 

I wouldnt go to system 76 myself. They make good systems, and for people that really want ubuntu preinstalled, dont want to build the system themselves, and dont want to worry about checking hardware for linux compatibility they are very good. You do pay for it though....a 'wild dog' system with Q9550, 8GB, 9400GT and 160GB  HDD is over $1000 US. Cheaper to build it yourself. Mind you, I would rather go there then dell, or any of the other major manufacturers. Probably much better quality parts and your dealing with a nicer company. 

Edit- I'm pretty sur that servers are out of the OPs prices range. Pity that they dont build AMD based servers, but thats the way things go.... 

> **chadhenry said:**
> @Bucky - yes I did mean virtualisation - dumb spell checker plugin for firefox messed that up!

I'm aware that AMD has had that feature for a long time. I just don't see many higher-end servers using AMD. My concern was how many virtualized environments an AMD processor could handle. I'm going to have 6-10 most likely and from people I've talked to, only Intel hardware could handle that many environments at one time. 

Pfft to that. AMD can handle virtualisation just as well, if not better, than Intel. 

You dont see many AMD server systems because almost all the computer companys deal with Intel exclusively (and I wont go into why that happnes unless anyone cares LOL). Its a catch 22, 'chicken and egg' situation. There is nothing wrong with the AMD based servers. 

If your planning on running 6-10 virautalised OSes at once on a single CPU, get ready for some heavy CPU and RAM use. If it handles it at all.

---

