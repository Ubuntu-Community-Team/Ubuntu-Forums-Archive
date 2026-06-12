---
title: "bioinformatics machine questions"
date: 2012-08-02
forum: Hardware
---

### Post by Quatermain on 2012-08-02
Hello,
I'm planning to build a machine to do some bioinformatics and I had a few questions about Ubuntu.  
We need a lot of RAM, I'm thinking of starting with 32-64 GB.  It looks like when going above 32GB, non-server motherboards tend to be flaky and RDIMM memory should be used.  As a result, I'm looking at a server board and CPU like the Supermicro X9SRA and an LGA 2011 E5-26xx xeon of some sort, with RDIMMs. 

My questions are if 'regular flavor' Ubuntu 64 will work successfully with this board and CPU, and if 'regular flavor' Ubuntu 64 will support more than 32GB of RAM.  (I've seen 1TB and 32GB as the limit for what it will support). (The alternative probably being Ubuntu server version, which I haven't used before)

Any other advice would be welcome as well.

Planning on using this to assemble ~120million reads, which is essentially taking 120million or so 100 character strings (90gb of data when stored in chars? roughly) and trying to find somewhat random overlap places between them all. It will be used for a few tasks of this nature; the best data I've seen is that 32GB is more or less a requirement and anything above really makes a difference.  

Thanks

---

### Post by gordintoronto on 2012-08-02
As far as I can determine, 64-bit Linux will support whatever memory your motherboard supports. That includes Ubuntu, of course. When I searched on Newegg, I found five current motherboards which support 128 GB of memory, and several which support 64 GB.

Avoid the server version unless you will run a high-volume web site.

Will you be running a custom application?

---

### Post by drmrgd on 2012-08-03
Yes, this will work fine.  An Ion Torrent Server is setup similarly to what you describe (I think only 48 GB of RAM, IIRC).  I would also recommend getting a higher end Video card with plenty of CUDA cores so that you can use the GPU to help process it.  

I hadn't heard anything about non-server boards being flaky with too much RAM.  Interesting if it's true.  Along those lines, though, I have this board, and a lot of people generally seem happy with it running 64GB of RAM from what I can tell:

[http://www.asus.com/Motherboards/Intel_Socket_2011/SABERTOOTH_X79/](http://www.asus.com/Motherboards/Intel_Socket_2011/SABERTOOTH_X79/)

That being said, I'm guessing you'd still probably prefer to go with a server board with dual-processor capabilities.  The Torrent Server is 2 x 6-core CPUs.

EDIT: Just to clarify since I didn't actually say it(!), but the server is running 64-bit Ubuntu 10.04 LTS server edition.

---

### Post by Quatermain on 2012-08-03
> **gordintoronto said:**
> When I searched on Newegg, I found five  current motherboards which support 128 GB of memory, and several which  support 64 GB.
Will you be running a custom application?
I saw the MB's  which support 128 GB on newegg, but it looked like they all had a high  failure rate.  That and some posts about boards being picky about memory  are why I was looking at server boards.  
I'm not sure what you mean  by custom, but the programs used to assemble aren't available in the  Ubuntu package system, unless something has changed in the last 6 months  or so.  I've run them before on Ubuntu on smaller projects  successfully.  They are a mix of C/C++ and perl, I believe.  We run some  perl scripts to pre and post-process the data.  

[quote=drmrgd]
Yes, this will work fine.  An Ion Torrent Server is setup similarly to  what you describe (I think only 48 GB of RAM, IIRC).  I would also  recommend getting a higher end Video card with plenty of CUDA cores so  that you can use the GPU to help process it.  [/quote]
I think our  memory req's will be a lot higher than for an assembly of an ion torrent  chip, but that is encouraging.  I don't have any experience using GPU  cores that way, but price is a big consideration for us.  
> 
I hadn't heard anything about non-server boards being flaky with too  much RAM.  Interesting if it's true.  Along those lines, though, I have  this board, and a lot of people generally seem happy with it running  64GB of RAM from what I can tell:
That being said, I'm guessing you'd still probably prefer to go with a  server board with dual-processor capabilities.  The Torrent Server is 2 x  6-core CPUs.

The work is a lot less CPU bound and more RAM bound from the  performance tests I've seen, I was thinking of going with a server  board partly because it could be upgraded to 256GB, supposedly.  I'm  more hoping 64GB will be enough, if it isn't I'd have to put some more  in. 
I'm considering an SSD drive to store the data as well, but I'm  not sure what the cost/performance would be over another 16 gigs of ram.

> 
EDIT: Just to clarify since I didn't actually say it(!), but the server is running 64-bit Ubuntu 10.04 LTS server edition. 	
Hm, was hoping to stay away from that just because I don't  have much experience and we don't really need it to do anything  server-like, just a lot of graph generation and string compares.

Thanks for the info

---

### Post by drmrgd on 2012-08-03
Is this HiSeq data we're talking about?  I can find out the specs of the cruncher have working on that data if it's helpful to you.  I don't work with that as much, and so I'm not sure how the system is handling that data (although I wouldn't imagine it being all that different, depending on your pipeline).  What I will say, though, is that the RAM doesn't seem to take nearly as much of a hit as the CPU cores do on my system.  Also, in looking at other people rigs (there's a few threads over at SeqAnswers about this), it always seems like they go for more processor cores than RAM.  I could be way off on this, though.  I would personally think you'd be fine with 64 GB of RAM (at least to start) and at least 12 CPU cores.  

I don't know of any tools that use GPU computing at the moment, with the exception of the Ion Torrent stuff.  So, figuring in a good GPU might not be worthwhile anyway.  Good to think of in the future, though, as I'm sure we're going to see a lot more of that to come!

I personally would be afraid to use and SSD for this.  One of the caveats of SSDs are the limited read /write cycles they can endure.  I would imagine you're going to be doing a TON of that!  So, even though the speed is nice, I think you'd be better off staying away.  I could also be wrong here too, tough.

I only mention the OS just to give you a clearer picture.  Since the Ion Torrent uses a web interface for setting runs up and accessing the data, they built in around that server.  However, you wouldn't need to go server for this.

---

