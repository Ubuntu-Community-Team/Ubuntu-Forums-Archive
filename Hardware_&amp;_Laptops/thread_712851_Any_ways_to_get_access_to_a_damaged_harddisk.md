---
title: "Any ways to get access to a damaged harddisk?"
date: 2008-03-02
forum: Hardware &amp; Laptops
---

### Post by circle on 2008-03-02
My friend has a quite seriously damaged harddisk. It was dropped onto the floor and my friend took it to a data recovery shop, unfortunately a non-trustworthy one. The staff there disassemble the harddisk and tried to recover from scratch, and failed. The disk can hardly spin up after that, the success rate is about one-tenth. It is noisy sometimes.

I tried to plug the harddisk into my PC using an external USB connector. I can see the device in Windows but when I tried to access it using those foresenics/data recovery software, access was denied. I then moved to Linux where I expect that I can perform more low level task or at least I can see more detailed log. When I plug the harddisk into my Ubuntu, there is no new device created in /dev. I found from dmesg that the kernel tried to create /dev/sdb but encountered some error, and said the device is offline and rejects I/O. It mentioned sg1 and I tried /dev/sg1 but no hope. Attached part of my dmesg for your information.

Are there any ways to create the device file (/dev/sdb) manually that map to the harddisk? Can I access the harddisk directing using the address sd 14:0:0:0:? Are there any other ways to by-pass those errors and recover as much data as possible? Or do you have any other suggestions?

The disk contains the graduation photo of my friend, and he has no backup of that. Now I am his final hope to recovery his valuable memory... Please help, any help is highly appreciated

---

### Post by wieman01 on 2008-03-02
If I were you, I would get professional help. It is certainly costly, but if this HD contains personal photos and a lot of memories, it will be worth the money. Don't mess around with it yourself, but get a professional company help you. One that costs more than 500 HKD, mate. :-) 

Greetings to HK.

---

### Post by circle on 2008-03-02
Thanks wieman, I do agree with you, really... I always believe that we should leave the specialized tasks to the professionals.

Actually my friend did too. He has tried to seek help from so called professionals, unfortunately not real ones. They quoted him for HKD 7000 (if I remember correctly... my only reply when he told me the price is WOW~), but the situation is even worse afterwards. The harddisk cannot even spin up all the time after their "professional" service. I'm afraid that he won't trust those "professional" shops any more...

So, he just want me to try what ever I can to recover as much data as possible...:|

---

### Post by wieman01 on 2008-03-02
If this relates to a mechanical problem, there is little software can do I guess. That's very unfortunate.

Aren't there any other data recovery firms in Hong Kong? Let me ask a friend of mine, he might know.

---

### Post by circle on 2008-03-03
There are some in those famous shopping arcade selling computer accessories in Hong Kong, but I'm not sure whether they are trustworthy. And you may have heard of the recent scandal of a HK pop star who leaks out *** photos after having his computer serviced at a repair shop. With this incident and my friend's past experience, I am afraid he will not try those company again.

But for his own good, I think you are right. He should really seek help from professionals. Let me try to persuade him to do so.

Thanks so much for your sincere help!

---

### Post by BillDozer on 2008-03-03
You can try to take a look at this: [http://wiki.linuxquestions.org/wiki/Dd_rescue]("http://wiki.linuxquestions.org/wiki/Dd_rescue"). I haven't tried it myself though.

---

### Post by wieman01 on 2008-03-03
No problem.

My friend had his repaired in Sham Shui Po. But I guess that's exactly the place you don't want to go... He said he had 2 HDs repaired, 1 was a success, the other one a big failure and he lost all his data. So that does not sound reasonable either. 

So we'll have to do some more research concerning this. 

Yeah, I heard about the scandal... pretty shocking to be frank. But this kind of stuff happens all over the world, there are similar examples in Europe. Pretty naive to trust anybody if you are a celebrity. ;-)

---

### Post by PreviousN on 2008-03-03
What exactally did those professionals do? If they actually opened up the hard drive and replaced things like the motor within or moved the platters to a new hard drive, then I'm afraid that theres' not much he/you can do.

IF you can somehow get it to be recognized by linux, you should try ddrescue. This reads bit by bit and copies it to a new location on a different drive (which you specify) and tries hard to recover bad blocks. 

If you get a /dev entry, then this will work since even if the partition table is bad the data will still be copied. 

Sounds like you're in a bad situation.

---

### Post by circle on 2008-03-04
> **wieman01 said:**
> No problem.

My friend had his repaired in Sham Shui Po. But I guess that's exactly the place you don't want to go... He said he had 2 HDs repaired, 1 was a success, the other one a big failure and he lost all his data. So that does not sound reasonable either. 

So we'll have to do some more research concerning this. 

Yeah, I heard about the scandal... pretty shocking to be frank. But this kind of stuff happens all over the world, there are similar examples in Europe. Pretty naive to trust anybody if you are a celebrity. ;-)
Yes. I think my friend gave his hard disk to a shop in Sham Shui Po.

Actually I am quite interested in knowing more about the low-level OS stuff relating to this issue, that's actually one of the reasons why I am seeking some expert advice here :)

About the scandal, it's not good to talk much here, but I really think the real victims are those poor girls involved.:(

> **PreviousN said:**
> What exactally did those professionals do? If they actually opened up the hard drive and replaced things like the motor within or moved the platters to a new hard drive, then I'm afraid that theres' not much he/you can do.

IF you can somehow get it to be recognized by linux, you should try ddrescue. This reads bit by bit and copies it to a new location on a different drive (which you specify) and tries hard to recover bad blocks. 

If you get a /dev entry, then this will work since even if the partition table is bad the data will still be copied. 

Sounds like you're in a bad situation.
According to my friend, those professionals did open up the hard drive but I doubt whether it was necessary. The hard disk used to work fine physically. Not sure whether they had replaced anythings inside.

Thanks for the suggestion of the tools, I will give it a try if I can get it recognized. But before that I may really need someone who are familiar with the low level operations to kindly offer me some help.

---

