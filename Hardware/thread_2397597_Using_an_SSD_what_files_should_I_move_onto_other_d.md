---
title: "Using an SSD what files should I move onto other drives?"
date: 2018-07-31
forum: Hardware
---

### Post by Fsirett on 2018-07-31
First of all, there is no real urgency to this, I suspect I will not be getting an SSD for a few weeks yet.

I am interested in using an SSD exclusively as a home for my OS. I know that should not be a problem, that part is perfectly straight forward. The drive will be somewhat small (120Gb) and I do understand that multiple rewrites on the disk will substantially shorten the drive lifespan.

My problem comes with advice I am getting or finding that is conflictive. 

I already keep my /home folder on another partition and, of course, I shall continue to do that. It is the suggestions for other files following suit that I am wondering about. I have been told - both to do and not to do - to do the same with the /usr, /var, and /etc files as well. I have no problem doing so, in principle but I am wondering if they are all good ideas.

My object is to lengthen the life of the drive (SSD) and I have plenty of HDD space to use. Obviously I want the machine to boot much faster, not that it is very slow now, but I am getting more impatient with time. 

My question is this: Is it a good idea to move some or all of these files off the disk and/or should I move other files as well? 

I am finding that I need to do some work on the computer because of the heat (climate) and as long as I am installing a new cpu fan, case fans and filters, I might as well go ahead and add the SSD that I lust after.

Many thanks for taking your time to help.

---

### Post by oldfred on 2018-07-31
If a standard desktop install, just have / (root) & /home.
New versions now use swap file, so swap partition not even required. 
And if a newer UEFI system you will need an ESP - efi system partition as first partition.

Who is suggesting separating the / folders into partitions. Years ago that was common. And some with servers want separation to manage users or various types of server software.
Ubuntu's default install is now just /. And an ESP if UEFI. I prefer to separate system from data, but that is not a requirement.

---

### Post by Fsirett on 2018-08-01
Cheers for that! This makes everything much easier. 

I know, from personal experience, that Flash memory has come ahead in reliability and durability by leaps ad bounds, but I do remember memory sticks that crashed within a year and MP3 players that would die in six months. On top of that, I speak to people who sell SSDs and do not use Linux, therefore having lots of opinion to share, I can become obsessed and scour the internet for information that is ages old and even then, probably wrong. I come here for current information from people who know what they are actually talking about.

If I understand correctly, the only really overly active file that will seriously deteriorate the drive is the /home folder. So much easier! 

I know in the not too distant future I will be going for a decent sized SSD, but only when the reliability has really improved a good bit more. A small one is now really throw away money, so I can play. 

I also thank you for the advice on the UEFI boot. I have always had problems with UEFI, mostly because I do not really understand what it is, how to use it, or what the advantages are. I understand it gives great advantages to Windows but far less to Linux. Maybe I shall try it again in the future.

In any case thanks again for clearing up this problem and, with any luck, it will clear problems with others. I am surprised it does not seem to have been asked before

---

### Post by kurt18947 on 2018-08-01
Some who know more than I say that concern about short lifespan of modern SSDs is overblown. I'm in the same situation looking at an SSD upgrade for a desktop machine. Either MLC or 3D TLC should give service length equal to or exceeding spinning drives in desktop service. I think planar TLC based drives might have shorter lifespans. Some drives will specify a rated lifespan in either terabytes written or drive writes - number of times the entire drive capacity can be written. Flash 'wear' only occurs on write not on read so if a system writes to swap quite a lot it'd be wise to put swap on a spinning drive.

---

### Post by Fsirett on 2018-08-01
Thanks for that. That is what I understood to be the problem, the writing and I was told, by people who came with unsubstantiated(?) knowledge that I should break up Ubuntu because the rewrites would kill the drive in record time. I have to come to those who know when I hear so many conflicting stories. As it is, small drives are now cheap enough for me to try out and as prices fall and reliability increases I can go to a larger drive if things work out well. 

To be honest, Nobody mentioned MLC or TLC technology in the shops, nor do many of the tests mention the technology used. That is an eye opener that I am much obliged for learning! That will make evaluation of tests much easier to fathom in the future. So often they talk about the cost per Gb of memory but that ignores the lifetime costs, which strikes me as a much more valuable number. Now I can look at the technology and then go back and look at the performance of that tech over time. that will certainly make a future difference!

Cheers!

---

### Post by wyliecoyoteuk on 2018-08-01
The only files that I worry about are in /var
For example log files and mythtv or video surveilance recordings, because applications like mythtv or zoneminder etc are constantly writing to disk, 24/7.
That said, it is not because of drive life, but the fact that spinning rust usually gives some warning before it expires, during which time it is often possible to recover data, whereas SSDs tend to die quite suddenly.
And of course we all backup regularly don't we?
My media and surveillance server runs on a 16GB SLCmode SSD for /, which cost £5 off ebay, and I have a spare. No need for swap if you have enough RAM.

---

### Post by oldfred on 2018-08-01
Some info on life:
       [http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash](http://hothardware.com/news/google-data-center-ssd-research-report-offers-surprising-results-slc-not-more-reliable-than-mlc-flash)
SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb) 
    
And hard drives also do fail, or why backups are important.
       hard drive life 
[https://www.backblaze.com/blog/hard-drive-stats-for-q1-2018/](https://www.backblaze.com/blog/hard-drive-stats-for-q1-2018/)
[https://www.backblaze.com/blog/hard-drive-stats-for-2017/](https://www.backblaze.com/blog/hard-drive-stats-for-2017/)

---

### Post by QIII on 2018-08-01
My primary machine runs on nothing but M.2 NVMe devices.  Solid state technology is far, far more mature these days and their reliability is on par with spinning iron oxide.

That said, I back up to rust -- but you should do regular backups no matter the technology.  Any device can fail suddenly and catastrophically.

For my web servers, I use spinners.  For my home servers I use a combination -- with things like movies and photos on solid state.  I run a home web server for movies and media so my family can browse to a web page behind my router and watch the movies stored on SSD.  Several can watch movies at the same time without the physical conflicts that might arise from spinners.

For home use, SSDs are fast and reliable.  But do regular backups anyway - just as you should with mechanical drives.

---

### Post by Fsirett on 2018-08-01
I have no doubt that the SSD is better than the worst stories, but I seem to have luddite genes (they are a Levis knock off) but I am still going to start small and try it. Besides, the small ones are cheap enough to throw away! If I do it right, it just means a simple reinstall if the worst happens.

That helps a lot. I have plenty of Ram and I do not use it for anything like surveilance or MythTV. That sounds like I do not need to even think about moving /var.

Cheers for that! This gives me much more information and makes a selection much easier! This seems like a better and better idea. I can roughly do the same as I do now, just separate /home and away I go. Now I have to go back and look at the brands and their specs. Fortunately, I have weeks to go before I need to commit.

---

