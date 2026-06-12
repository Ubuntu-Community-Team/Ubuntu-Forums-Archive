---
title: "How to install Ubuntu over Windows without a CD."
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by magnoliasouth on 2009-10-11
I have a brother-in-law who has a laptop that was loaded with viruses. Long story there, but probably junk porn. In any case, I was asked to fix it and after trying everything known to mankind, Windows is toast, which is probably not a bad thing for him.

The problem is that his CD drive doesn't work and I don't have a thumb drive big enough (and I'm not going to buy one just to use for only his laptop).

Now I managed to install Jackalope alongside Windows (major pain due to the stupid virus), and while the install did fine, it's not going to work because when I tried to run the update manager, there were only a small number of updates and there wasn't enough memory.

So....

I need to go back and wipe Windows off, and install Ubuntu over it without a CD.

I have minimal experience with Ubuntu. I have Hardy Heron on mine, but I'm not a moderate user. I'm learning, but am so out there I've no idea what most Ubuntu language means.

Any help or direction at all would be appreciated. I need to fix this today, if at all possible. He's in the dining room waiting on me.

---

### Post by oldos2er on 2009-10-11
If you have a high speed Internet connection, you could use unetbootin. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by bulldog on 2009-10-11
How did you install ubuntu this time?
Just do that again and when you come to the partition part of the installer,delete all partitions,after done,create a 10GB partiton for / ,a small 1-2 GB partition for swap and the remaining disk space for /home.
When done select the 10GB partition and set it to mount at / and set it to format ext3.
Select the small partition and mount it as swap and set it to format as swap.
At last select the remaining partition and set it to mount as /home,format as ext3,and go with the install.

Good luck!

---

### Post by p2bc on 2009-10-11
Ok I know this in Ubuntu forums, but I am trying to help the guy out so he can install Ubuntu.

With that said, you said you don't have a large enough thumb drive, did you try using [DSL Linux](http://www.damnsmalllinux.org/)(Damn Small Linux) small enough to fit on a 64mg thumb drive. It is not fancy, very basic, but with that and ClamAV(Backend Anti-Virus) and ClamTK (GUI or frontend) you should be able to get some results.

I would also, and this is me, would buy a 2gig thumb drive, can get them as cheap a $5 and charge you Brother-In-Law. It is truly the least he can do for all the work you are doing to help him out. With 2 gig you would have more than enough room to get Ubuntu on it and just install it one time with little headache, but again that is me. You can also keep that thumb drive are a rescue system on your utility belt pulling it out the next time someone is in distress, you wil be well prepared.  Just saying  ;-)

---

### Post by norm7446 on 2009-10-11
If the Hard drive is a sata one can you not connect it to and other computer that has a working CD rom..... and install UBUNTU that way.

---

### Post by magnoliasouth on 2009-10-11
Wow! I love Ubuntu users. They're the most helpful people I've ever met. :)

Thanks so much for all the helpful advice. Following various methods posted here, I did manage to get it installed. However Jackalope just will not work on it for whatever reason I cannot identify. I ended up going with Hardy Heron and that seems to be working okay. I've not yet tested it fully, but so far so good.

Just to answer a few questions that were asked, I did originally download use unetbootin via Windows, which is like a dream it's so simple! I just couldn't figure out how to overwrite Windows.

@p2bc: Thanks for your suggestions but I did want to clarify one thing. I'm a woman, and a very sexy one at that. ;) 

Again, thanks to all because if you hadn't helped, I wouldn't have managed getting it done. Phew! Glad it's nearly over.

---

