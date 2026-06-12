---
title: "Harddrive space being mysteriously eaten away fast"
date: 2008-09-28
forum: General Help
---

### Post by Nexusx6 on 2008-09-28
Hello,

I got a really weird problem on my hands and its starting to get critical. I have a a Fakeraid setup so that I have a total of 500gigs. The setup has worked for a long time now and I haven't had any problems. I have 4 partitions: /root, Swap, /home, NTFS. My /home partion is by far the biggest at something like 350gigs.

Recently I've started getting odd messages from Kubuntu about my drive becoming full, but when I check the amount of space all seems well so I dismissed it. When the message came up again today and started poping up more frequently I noticed something -- I was check the space of /root not /home. It turned out that this morning my /home partion had only 8gigs of free space and as off now its down to just 800 megabytes!! 

Something has filled up a 350gig partition, but I have no idea what nor how to stop it. In one afternoon I lost almost 8gigs of space. The only suspect I have is a seemingly misplaced "lost+found" folder that's parked under /home for some reason. I can't access it or check how big it is, even if I use sudo. 

I was greatly appreciate any help. I would like to have my 350 gigabytes of space back :(

---

### Post by taladan on 2008-09-28
I had this happen to me a while back, one way you can check it is to do a:

```
sudo du -h|grep G|grep -v K 
```

This will at least give you an idea of any files/directories that have grown to 1Gb+ in size.  In my case it was .xsession-errors that had grown to a disproportionate size.

Hope this helps out,

Tal

---

### Post by nowshining on 2008-09-28
> **taladan said:**
> I had this happen to me a while back, one way you can check it is to do a:

```
sudo du -h|grep G|grep -v K 
```

This will at least give you an idea of any files/directories that have grown to 1Gb+ in size.  In my case it was .xsession-errors that had grown to a disproportionate size.

Hope this helps out,

Tal


i had the same problem - please note that anything with a dot in front of it is hidden...

---

### Post by Nexusx6 on 2008-09-29
Hola, thanks for the responses. I found the the destructive processes causing the whole mess. It was Strigi - Ubuntu's indexing and searching program. For some reason it keep a massive index that keep growing and growing. Over the days it grew to 180gigs. As soon as I deleted the index I got back all that space.

I don't know what causes the recursive index in the first place but I'm thinking about filing a bug report.

---

### Post by nowshining on 2008-09-29
> **Nexusx6 said:**
> Hola, thanks for the responses. I found the the destructive processes causing the whole mess. It was Strigi - Ubuntu's indexing and searching program. For some reason it keep a massive index that keep growing and growing. Over the days it grew to 180gigs. As soon as I deleted the index I got back all that space.

I don't know what causes the recursive index in the first place but I'm thinking about filing a bug report.


if u don't plan on using it - u should be able to remove it...via synaptic or apt-get, etc...

---

### Post by Iwannakillyou on 2008-09-29
I have been waiting for about 5 days now but the shipping times are 10-19 days. As soon as I get them I will let you know. I have not seen you on that forum for a long time now and I was wondering where you are? How did it go with the collection that you got? Here is the link to the beads again [http://www.liangdianup.com/beadscrafts_1.htm](http://www.liangdianup.com/beadscrafts_1.htm) and here is the link to the Swarovski beads [http://www.liangdianup.com/inventory/900020.htm](http://www.liangdianup.com/inventory/900020.htm) if those links don't work then you can goto [www.lducompany.com](www.lducompany.com) and click on the beads picture, that should take you right there. I hope you see this message and get back to me cause I miss talking to you :)

---

