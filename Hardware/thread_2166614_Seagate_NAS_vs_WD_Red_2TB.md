---
title: "Seagate NAS vs WD Red 2TB"
date: 2013-08-10
forum: Hardware
---

### Post by ocdkv on 2013-08-10
Hi There.

I decided to re purpose my old desktop to a media server and learn a new OS while I was at it. It was an HP media center m8430f with a Core2Quad Core Q6600 and an IPIBL-LB motherboard running Windows Vista and the latest BIOS Update (v 5.43). I Purchased 3 x 3TB Seagate NAS HDD (ST3000VN000-1H4167) for storage and 1 x 128Gb Kingston SSD for OS. I installed Ubuntu 12.04 LTS. I checked BIOS and found the NAS HDD's were only being recognized as 801Gb.  I believe the problem is that my MoBo, being 5 years old, simply will not support Hard Drives over 2TB (at least the BIOS will not).  Ubuntu does recognize them for what they are, 3TB, but cannot use them as such and need to be partitioned to 2Tb or less. 

Now it appears that [COLOR=#000000]2 out of the three Seagates were DOA, (BIOS seen them but SeaTools confirmed they're not working right), lots of grinding noises beeping and chatter.  I am therefore replacing them with 2TB drives and crossing my fingers that this will fix this issue.[/COLOR]

[COLOR=#000000]Now to my question.  I am a little leery of purchasing Seagate NAS Drives again from this experience, however reviews (at least on Newegg) have not been very favorable towards the WD Reds.  I'm willing to bet that the good people on this forum could assist me and point me in the right direction.  Give me the good, the bad and the ugly.  And if you have experience using both then i definitely want to hear from you.

Please limit your responses to the actual drives I'm referring to and not the companies making them.  Both companies have their +/-'s and I have had excellent experiences with other drives by these two very good companies.

Seagate: [/COLOR][http://www.newegg.ca/Product/Product.aspx?Item=N82E16822178391](http://www.newegg.ca/Product/Product.aspx?Item=N82E16822178391)

WD: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16822236343](http://www.newegg.ca/Product/Product.aspx?Item=N82E16822236343)

Thank you for your time and experiences.

Kevin

---

### Post by gordintoronto on 2013-08-10
You might get more responses on a site which is mostly about hardware, such as pcmech.com

---

### Post by 1clue on 2013-08-10
First, space:

I just went through this.

What kind of partition table are you using on your big drives?  If you have an MSDOS partition table, then at most it will handle 2T.  The whole partition table in the free space at the end of the MSDOS boot loader was a dirty hack to cope with HDD bigger than 32Mb (yes MB).  Ever since the hard disk has been bigger than 32 mb, the dos partition table has been obsolete.

You need to make sure you're using a GPT partition table.

Now, regarding drives:

You need to decide what sort of use you're going to use these drives for, and then search on reliability for that purpose.  Or better yet, search on best drives to use for that purpose.  For example, you mentioned NAS drives.  Are you using them for NAS?  For home use or small office use, this probably doesn't matter so much.  However if you're using a WD green drive you might have big trouble with Linux, they're set up to sleep after 8 seconds of inactivity, which is outrageous.  You have to either run the WD utility or hdparm, which is dangerous.  Also some WD green drives have hardcoded values that cause them to melt with Linux.

I did some research for a NAS and I got mixed reviews on WD red.  I think there was a bad batch out there or something, but mostly people have good luck.  Sorry I don't have the links anymore though.

---

### Post by ocdkv on 2013-08-11
Thanks for the assistance, much appreciated. No WD Greens here, too many bad reviews in a NAS/Server enviroment. 
I'm so new to this that I just spent the last hour reading about GPT partitions so again, thank you, i love learning new tricks (old dog here!).
I'll get back to you when I finish playing around with this 'new info'

Kevin

---

### Post by 1clue on 2013-08-11
I'm definitely not new at this, been in computing since the mid '80s.  Been using ms-dos partition tables in spite of all the warnings since then too, it's been working all this time right?  Then extremely recently I spent way too long trying to figure out why my RAID array only had 2t drives instead of 3t drives.

---

