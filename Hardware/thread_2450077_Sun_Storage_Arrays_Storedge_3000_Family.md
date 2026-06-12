---
title: "Sun Storage Arrays Storedge 3000 Family"
date: 2020-09-07
forum: Hardware
---

### Post by arpeggi5150 on 2020-09-07
Hey guys, long time dabbler in linux in general (installed linux on my ps3 back in the day) and have dual booted windows and linux for most of my career in computers. recently been trying to build my first server, and of course i had to go with Ubuntu!
(Please let me know if i didn't post this in the correct place!)

I got a Sun Oracle Storage 7410 Server with 
2 - 6-Core Processors (I believe they're amd's equivalent of xeons but i may be wrong?)
-64gb of ram and 
-2 500gb SSDs in raid 1

I have lubuntu installed on it and running seemingly well and i can even remote into the system easily using TeamViewer and noodle around.
ended up going with Lubuntu for multiple reasons (the main being that it was the most convenient way for me to install linux in raid without having too much resources to the desktop envoronment [If anybody has any knowledge about that please let me know lol! still very much a noob])

My main function for the server is to have a file database for my long term storage archive needs, and to experiment. maybe a media server, or perhaps an email server, perhaps VMs. 


However I also Bought 3 Storedge 3000 Family Units (I'm honestly not sure exactly which ones they are,) and i'm having a tough time figuring out how they work. I have two 14 tb drives ready to go in them JBOD Style until I can buy enough drives to do proper Raid style. (Also open to doing that a better way if anyone has any ideas.) wanting to buy 14tb drives as i can afford them and slowly expand my storage needs until i've filled all 3 units (which would total over half a petabyte) Kinda thought it would be plug and play but clearly i was mistaken. Looked into the CLI for Sun (Command Line Interface) and INstalled that on my server (I think?) But haven't been able to get that working. 

I have the Storedge single unit (the master unit i believe) plugged into the Server via SFB (I believe) But all it does is beep. I was thinking i need to connect it and edit some settings before i put the drives in but is that not the case? is it not working because It has no drives in it? (this is probably my last thing to try at this point) 

My question basically is does ANYONE have ANY idea how the ---- These things work? I've been googling for days and all i can seem to find that helps me is a page detailing the meaning of the beeps the things absolutely will not stop making. Am I supposed to connect through ethernet and then send commands to it? Am i Missing Some Software?

Really anything at this point would be massively helpful. Thank you

---

### Post by TheFu on 2020-09-08
I would first check to see if there are hardware/controller limitations on the size of storage supported.  One of my external arrays won't support HDDs over 4TB in size. These appear to be SCSI, which makes me think they are pretty old. Try using smaller disks first, if you can't find the manual with the size limitations spelled out.

For your needs, that's a huge amount of power use.  If power isn't free where you are, a $350 recent generation desktop is probably much faster, uses much less power, will be quieter and easier to handle. 

You'll likely need some SUN HW expertise to get this stuff working.

---

### Post by arpeggi5150 on 2020-09-08
Thank you very much for your response. See i was certainly wondering about that, however I was assuming (probably my first problem) that these would be something I can expand capabilities with over time by using linux (Meaning that linux would be able to fix that limit or upgrade that limit if that's the case). Meaning that the 14 Tb drives would be accessible from linux due to linux being awesome. The idea was that in the future I can add more and more drives until i hit the max capacity using 14 tb drives (over half a pedobyte considering I have 3 units with 12 bays each)

However I haven't even put the drives in yet. Should I try that first? I really don't know if there are settings i need to alter first to setup the raid so i was trying to simply access the settings for the devices before i installed the drives, in some way hoping that might give me more info. 

As i mentioned in the post i have a sun server that is the base of the whole system and it's playing great with linux, so Im just hoping this is sometype of config issue.

I am very serious about needing 36 drives in the long run (and ideally expandable to more) with raid redundancy. My business does a lot of video / audio storage and it's important to us. I'm happy to sell these and find a better way to do it but I'm trying to find a plug and play rack solution to do so.(Ideally with as many 3.5 inch hard drive slots as possible for the price) I thought this was going to be it. perhaps I was mistaken. 

I don't mind building a desktop for this purpose but I was hoping to find something rack mountable and redundant which is why i thought these would be awesome. Plus they match my sun server and i got a great deal on them. I should've known better to assume anything important would be plug n play. But again, hoping there is something relatively simple i just don't know about.

thanks again for your time and input

---

### Post by arpeggi5150 on 2020-09-08
I believe i did read something about a 4gb limit in the manual, but is that really true? Is this hard-coded? or simply a limit of the sun operating system? I'm using Lubuntu so I IMAGINE (Probably my mistake again) that in theory it could just be used as a hardware connection tot the drives and Linux would handle the software side of things or is that totally wrong and stupid? Again thanks for taking the time to help me. i Really thought large-scale storage would be simple as plugging in multiple big drives and calling it a day.

---

### Post by TheFu on 2020-09-08
> **arpeggi5150 said:**
> I believe i did read something about a 4gb limit in the manual, but is that really true? Is this hard-coded? or simply a limit of the sun operating system? I'm using Lubuntu so I IMAGINE (Probably my mistake again) that in theory it could just be used as a hardware connection tot the drives and Linux would handle the software side of things or is that totally wrong and stupid? Again thanks for taking the time to help me. i Really thought large-scale storage would be simple as plugging in multiple big drives and calling it a day.

Hardware from 15 yrs ago didn't know anything about 14TB HDDs.  I doubt it had a 4GB limit, but 4TB would definitely be reasonable as a hardware address limitation.  No way around it, if that is true.  I think Sun included ZFS support around 2006-ish, so exactly now old is this hardware?  There can be all sorts of failures that aren't related to size limitations.  Don't confuse ZFS huge file system support with actual hardware limits for disk sizes. There may have been firmware updates for those storage arrays, but without a Sun contract, you won't be getting those. Oracle wants to be paid for everything, especially support.

Enterprise storage is very picky about all sorts of things.  They would only test enterprise storage, not consumer storage. They would only test storage that Sun sold with the arrays, not random storage provided by any other vendors.  With disk arrays, it is common to have approved disk models that can be used. Sometimes this is just to ensure the best compatibility and sometimes it is because the firmware in the controller takes advantage of specific instructions that only those disks support.  If you've ever been involved in purchasing hardware in large enterprises, you know that they don't really shop around between vendors for new equipment. You buy a complete system exactly as you need it configured.

You are learning valuable lessons. Hopefully, it isn't costing you more than $200 and $20/month in added power costs.

BTW, Linux has limitations for storage sizes too. These are mainly limitations due to file system size limits, but if you stay with commonly used, supported, file systems, those limitations are so huge as to be unlikely an issue for any playing around at home. Look up the limits on wikipedia.

---

### Post by arpeggi5150 on 2020-09-10
Sorry that was a typo, i meant 4 TB. Lots of late nights lately. I really don't know that much about it i came upon it second hand and don't have a ton of details about it. I believe youre right it was ZFS. What I'm trying to understand tho is there any type of OS or firmware that's controlling the formatting and disks inside the arrays themselves or does this happen through Linux? I haven't installed the drives yet i mentioned that But I 'm not sure if that was clear. I was expecting to just use the arrays as essentially a big case with slots for a ton of drives. But am i understanding that they need a dedicated specific software? I'm just a little confused because they're actually all matching sun sytsems and linux actually runs great on the sun server itself. So why is the array itself such a problem? I mean on the Server side of things does it see each individual drive? If so config should be easy I'm just wondering if it's supposed to be plug in play or if there is supposed to be some etherenet method of accessing the system. I'm actually pretty decent at troubleshooting and have gotten MANY systems to do things they weren't supported to do. I just really don't even know where to start as far as accessing any settings with these devices. 

Yea i'm not really worried too much about the power costs or about the linux file size limitations i'm more just trying to understand how disk arrays in general, and sun arrays specifically are operated at all. Thank you for your time and input into my situation

---

