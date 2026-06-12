---
title: "SATA performance, does it suck?"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by ahaslam on 2007-06-28
I don't seem to be getting the most of my SATA drive, extracting a 36MB archive takes the best part of 9 minutes. I'm using XFS, which I've tested to be the fastest for me. My rig comprises of an overclocked C2D & a WD Caviar SE16: [http://www.westerndigital.com/en/products/Products.asp?DriveID=298](http://www.westerndigital.com/en/products/Products.asp?DriveID=298)

Preformance benchmark from *hdparm -tT /dev/sda*:
```
/dev/sda:
 Timing cached reads:   3288 MB in  2.00 seconds = 1644.74 MB/sec
 Timing buffered disk reads:  188 MB in  3.02 seconds =  62.31 MB/sec
```

Time for extracting 36MB tarball:
```
root[sda3]# time tar xjpf /mnt/usb/Gentoo/portage-latest.tar.bz2 -C /home/ahaslam/sda1/usr/

real    8m58.492s
user    0m12.326s
sys     0m10.076s
```

Is this just me or does this suck? If so how can it be improved (hdparm does very little for sata drives)?

---

### Post by sharke on 2007-06-28
I have the same drive and they have selectable transfer rates via jumper on the drive. Mine came wth jumper set to 1.5mb and i removed jumper and this gave 3.0mb transfer.
Regards
Sharke

---

### Post by ahaslam on 2007-06-28
Thanks for the reply.
Though mine has no pre set jumpers, bought OEM...

PS. What does *hdparm -tT* give you? I doubt the jumpers would have an effect: [http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=981&p_created=1052339456&p_sid=NgxPThFi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTA4JnBfcHJvZHM9JnBfY2F0cz0xMjMmcF9wdj0mcF9jdj0xLjEyMyZwX3NlYXJjaF90eXBlPXNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1qdW1wZXIgc2V0dGluZ3M*&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=981&p_created=1052339456&p_sid=NgxPThFi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTA4JnBfcHJvZHM9JnBfY2F0cz0xMjMmcF9wdj0mcF9jdj0xLjEyMyZwX3NlYXJjaF90eXBlPXNlYXJjaF9mbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD1qdW1wZXIgc2V0dGluZ3M*&p_li=&p_topview=1)

---

### Post by sharke on 2007-06-28
2.844 MB/sec
regards
Sharke

---

### Post by ahaslam on 2007-06-29
Anyone else? 

I was told by the Gentoo guys on IRC that this sucked & I can't help but agree...
Maybe I should just splash out for another & go raid0...

---

### Post by patrickfromspain on 2007-06-29
On the first version of sata, using a VIA chipset and a 2mb cache disk:

patrick@patrick-desktop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1280 MB in  2.01 seconds = 637.21 MB/sec
 Timing buffered disk reads:  162 MB in  3.03 seconds =  53.47 MB/sec
patrick@patrick-desktop:~$

---

### Post by sharke on 2007-06-29
take a look here for benchmarking test [http://techreport.com/reviews/2005q2/wd-caviarse16/index.x?pg=1](http://techreport.com/reviews/2005q2/wd-caviarse16/index.x?pg=1)

Regards
Sharke

---

### Post by ahaslam on 2007-06-30
Thanks sharke, that made for depressing reading ;)

So would you guys buy another & use raid0, or get a smaller Raptor for / ?

:popcorn:

---

### Post by sharke on 2007-06-30
J would not go with raid most probably by a sata that supports  sataii. Did you know hdparm is only for ide sdparm is for sata.
Regards
Sharke

---

### Post by God Of Atheism on 2007-06-30
> **sharke said:**
> J would not go with raid most probably by a sata that supports  sataii. Did you know hdparm is only for ide sdparm is for sata.
Regards
Sharke

So how does one get similar parameters for a sata drive? I checked the manual of sdparm, but didn't really get it.

---

### Post by ahaslam on 2007-06-30
> **sharke said:**
> J would not go with raid most probably by a sata that supports  sataii. Did you know hdparm is only for ide sdparm is for sata.
Regards
Sharke

The drive is sata ii & I have a ga-965p-ds3 mobo so there's no support problem there.
I know about hdparm & sdparm, both are practically useless for sata hdd's imho (in terms of performance gains at least)...

So why not raid? I'll probably take this route, but it's nice to hear others' opinions ;)

PS. God Of Atheism, nice oxymoron :)

---

### Post by logos34 on 2007-06-30
ahaslam, 

my fav:

'thank God I'm an atheist!' (Luis Bunuel)

It may disappointing but I wouldn't sweat those rates.  ~62 MB/s for sata is normal (forget the 3 Gb/s -- that's just the theoretical interface bandwidth...even the burst speeds are well below that).  Close all your apps and anything that's using swap, then do sdparm, the rates will go up a little.  You do have a big 16mb buffer so that makes up a little.  Personally I'd like a small 37GB raptor just for / -- fast boot and loading times for apps and programs.  But have you seen the price per gb?.  RAID1 might be a better deal--at least you get redundancy (mirror) with the faster read times.  But in terms of overall performance improvement in everyday use my impression is that Raid is just not that big a deal.  

Are you sure you didn't mean *creating* a 36mb archive was taking nine min?  I could slighly understand that.  Something must be really be wrong because jeez you have a c2d.  Zipping especially is a cpu-intensive task--the hard drive speed isnt a factor.  Maybe the kernel isn;t running smp and only one core is going!  dunno.  But just to give you idea: I just compressed (bzip2) a 4.3 gb backup using a 1.6 gig sempron and it took a little over an hour.

---

### Post by ahaslam on 2007-06-30
Thanks for your reply ;)

It was *extracting* an archive (gentoo protage snapshot), to make things worse my C2D is overclocked to 3.2G...

Try it yourself, it should be used for benchmarking, it's a killer ;)
[ftp://ftp.mirrorservice.org/sites/www.ibiblio.org/gentoo/snapshots/portage-latest.tar.bz2](ftp://ftp.mirrorservice.org/sites/www.ibiblio.org/gentoo/snapshots/portage-latest.tar.bz2)

---

### Post by logos34 on 2007-06-30
> **ahaslam said:**
> Thanks for your reply ;)

It was *extracting* an archive (gentoo protage snapshot), to make things worse my C2D is overclocked to 3.2G...

Try it yourself, it should be used for benchmarking, it's a killer ;)
[ftp://ftp.mirrorservice.org/sites/www.ibiblio.org/gentoo/snapshots/portage-latest.tar.bz2](ftp://ftp.mirrorservice.org/sites/www.ibiblio.org/gentoo/snapshots/portage-latest.tar.bz2)


Took me little over 3 min:

03:16.153

unzipped size:
148830 items, totalling 259.3 MB

super-duper ultra compression ratio!

---

### Post by ahaslam on 2007-06-30
That's a big difference. What drive do you have & have you tweaked it at all?

---

### Post by logos34 on 2007-06-30
> **ahaslam said:**
> That's a big difference. What drive do you have & have you tweaked it at all?

100 GB Maxtor 6L100P0 ata6/133 IDE drive (8mb cache).  standard settings, (oh, write-cache is enabled)

clocks in around ~55-63 MB/s hdparm test.

But you keep focusing on the hard drive and I tell you it's the processor you should be looking at when compressing/extracting, ripping/encoding. etc.  Just watch your sys monitor -- cpu usage should shoot way up (mine goes 100%), can hardly do anything else (single-core, alas).

---

### Post by ahaslam on 2007-06-30
tar uses only 0.7% cpu & 0.9%memory. Do you think this is a problem?

---

### Post by logos34 on 2007-06-30
> **ahaslam said:**
> tar uses only 0.7% cpu & 0.9%memory...
& I get similar results on other distro's...

wait, I know I have a wimpy chip and you have bleeding edge (OC'ed on top of it), but gotta be using more processor resources than that to tar and untar.  the cpu does most of the work.  maybe I've got it all wrong.  i don;t know...maybe it's hardly working at all because it's crippled (that would explain the nine min.).  beats me.

---

### Post by ahaslam on 2007-06-30
> maybe it's hardly working at all because it's crippled
The disk? Never thought of that (pretty new), I'll check it out tomorrow (too late/early now).

;)

---

### Post by logos34 on 2007-06-30
> The disk?

no, the processor.  Look, you obviosuly have a problem with such an abnormally long extract time...maybe somethign is all corrupted with that particlular bzip  file, dunno.

---

### Post by jcostom on 2007-06-30
> **ahaslam said:**
> 
Is this just me or does this suck? If so how can it be improved (hdparm does very little for sata drives)?

I just repeated this on 2 machines.  Both systems were using the AHCI driver for the SATA controllers.

1. C2D E6600 (2.4 Ghz), Feisty, kern 2.6.21, Asus P5B Deluxe, Seagate ST3160812AS on SATA-II Link, ext3 filesystem

```

# time tar xfpj portage-latest.tar.bz2 

real    0m29.593s
user    0m15.549s
sys     0m4.448s

# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   3778 MB in  2.00 seconds = 1889.45 MB/sec
 Timing buffered disk reads:  204 MB in  3.01 seconds =  67.72 MB/sec
```

2. P-4 2.53 Ghz, Dapper, kern 2.6.21, Shuttle SB-95Pv2, Seagate ST3160812AS on SATA-I Link, ext3 filesystem

```
# time tar xjpf portage-latest.tar.bz2 

real    1m4.300s
user    0m28.460s
sys     0m9.950s

# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   3344 MB in  2.00 seconds = 1671.91 MB/sec
 Timing buffered disk reads:  200 MB in  3.00 seconds =  66.65 MB/sec
```

So yes, I'd say you've got something up there.  What's your performance look like on doing a similar test with a tarball of similar size that doesn't consist of thousands of tiny files?  Writing all of those inodes is bound to take lots of time.

```
# tar -tjvf portage-latest.tar.bz2 | wc -l
148874
```

---

### Post by God Of Atheism on 2007-07-01
Of course one should use an unloaded system for benchmarking, nevertheless:

kernel 2.6.20 on athlon xp 2500+, 1GB ram (2-3-3-11), Gigabyte 7NNXP, sda= ST3120026AS, sdb= WDC WD2500JS-00M
```

time tar xjpf Desktop/Temp/portage-latest.tar.bz2 

real    1m38.324s
user    0m29.814s
sys     0m12.437s

```
Which seems to be okay, nevertheless, something seems to be wrong with my discs:
```

sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   794 MB in  2.00 seconds = 396.44 MB/sec
 Timing buffered disk reads:  156 MB in  3.02 seconds =  51.59 MB/sec

```
and:
```

sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   718 MB in  2.00 seconds = 359.04 MB/sec
 Timing buffered disk reads:  186 MB in  3.03 seconds =  61.39 MB/sec

```

So what should I do about my discs? run sdparm with what parameters? What helps and what doesn't?

---

### Post by david_2001 on 2007-07-01
> **ahaslam said:**
> 
Time for extracting 36MB tarball:
```
root[sda3]# time tar xjpf **/mnt/usb/**Gentoo/portage-latest.tar.bz2 -C /home/ahaslam/sda1/usr/

real    8m58.492s
user    0m12.326s
sys     0m10.076s
```

Is this just me or does this suck? If so how can it be improved (hdparm does very little for sata drives)?
What improvement do you get if you move portage-latest.tar.bz2 from that usb drive to a sata hard disk drive before extracting it?  In the meantime, I've got a system with a slower Pentium D 820 and slower hdds and still manage a respectable extract time:
> david@darkstar:~$ time tar xjpf Desktop/portage-latest.tar.bz2 -C /media/Extra/
real    1m3.048s
user    0m25.634s
sys     0m7.820s
david@darkstar:~$ sudo hdparm -tT /dev/sdb *[is where /media/Extra is]*

/dev/sdb:
 Timing cached reads:   1476 MB in  2.00 seconds = 737.79 MB/sec
 Timing buffered disk reads:  184 MB in  3.02 seconds =  60.95 MB/sec

---

### Post by Rui Pais on 2007-07-01
> **ahaslam said:**
> I don't seem to be getting the most of my SATA drive, extracting a 36MB archive takes the best part of 9 minutes. I'm using XFS, which I've tested to be the fastest for me. My rig comprises of an overclocked C2D & a WD Caviar SE16: [http://www.westerndigital.com/en/products/Products.asp?DriveID=298](http://www.westerndigital.com/en/products/Products.asp?DriveID=298)

Preformance benchmark from *hdparm -tT /dev/sda*:
```
/dev/sda:
 Timing cached reads:   3288 MB in  2.00 seconds = 1644.74 MB/sec
 Timing buffered disk reads:  188 MB in  3.02 seconds =  62.31 MB/sec
```

Time for extracting 36MB tarball:
```
root[sda3]# time tar xjpf /mnt/usb/Gentoo/portage-latest.tar.bz2 -C /home/ahaslam/sda1/usr/

real    8m58.492s
user    0m12.326s
sys     0m10.076s
```

Is this just me or does this suck? If so how can it be improved (hdparm does very little for sata drives)?

hi ahaslam,
i think your issues are all due to 2 wrong assumptions that you have made: 
1- "I'm using XFS, which I've tested to be the fastest for me."
2- For a benchmarck pick **a** big tar.bz2 extract and that should give me some real world results.

Let me try to explain what is wrong.
The 1st it's simply because there is nothing that is fastest in absolute. It's impossible to choose a filesystem that is the best in all aspect and for all tasks. :( 
XFS is fast... yes, to save and read big files. It's bad to delete files and terrible for I/O of small files.
The 2nd assumption is almost correct, but you have been unlucky with your choice. 
A portage tree is special problematic case. It's made of thousands of very small little files, that usually creates fragmentations problems on partitions, exhaustion of inodes of filesystems and slowness on uncompress (due to intense IO operations). 

Here my times for your specific portage file:
ext3
```
real    0m29.472s
user    0m16.895s
sys     0m6.365s

```

XFS```

real    7m1.201s
user    0m19.375s
sys     0m12.249s
```
see the difference... 

I use XFS for /var/cache/apt/archives of Ubuntus and ext**2** for portage trees.

may i suggest some absolute must threads on Gentoo Forum, 
[The filesystems choice  thread]("http://forums.gentoo.org/viewtopic-t-2189-postdays-0-postorder-asc-start-0.html")
[portage slowness]("http://forums.gentoo.org/viewtopic-t-384292-start-0-postdays-0-postorder-asc-highlight-.html")
and
[ext3 tips]("http://forums.gentoo.org/viewtopic-t-305871-postdays-0-postorder-asc-start-0.html") and [xfs tips]("http://forums.gentoo.org/viewtopic-t-488215-postdays-0-postorder-asc-start-0.html")
[more portage slowness filesystems specific]("http://forums.gentoo.org/viewtopic-t-422873-highlight-.html")

hth

---

### Post by ahaslam on 2007-07-01
A lot of replies ;)

jcostom, *tar -tjvf portage-latest.tar.bz2 | wc -l* gives:
```
root[sda3]# tar -tjvf portage-latest.tar.bz2 | wc -l
148833
```
david_2001, it's actually significantly quicker to read it off the external drive, than it is to read from & write to the same disk, see my ext3 results below.

Rui Pais, I know that no fs is the outright fastest in every situation. XFS has just been the most *consistent* in *my uses* for a long while. I'd tested several before making this thread with a 100MB file:
```
XFS

root[ahaslam]# time cp sda1/stage3-i686-2007.0.tar.bz2 sda3/

real    0m2.334s
user    0m0.007s
sys     0m0.110s
root[ahaslam]# time tar xjpf sda3/stage3-i686-2007.0.tar.bz2 

real    2m28.168s
user    0m18.215s
sys     0m2.267s


ReiserFS

root[ahaslam]# time cp sda1/stage3-i686-2007.0.tar.bz2 sda3/

real    0m0.179s
user    0m0.000s
sys     0m0.160s
root[ahaslam]# time tar xjpf sda3/stage3-i686-2007.0.tar.bz2 

real    5m18.520s
user    0m18.619s
sys     0m3.180s


EXT2

root[ahaslam]# time cp sda1/stage3-i686-2007.0.tar.bz2 sda3/

real    0m2.221s
user    0m0.007s
sys     0m0.120s
root[ahaslam]# time tar xjpf sda3/stage3-i686-2007.0.tar.bz2 

real    6m37.085s
user    0m18.615s
sys     0m3.283s


JFS

root[ahaslam]# time cp sda1/stage3-i686-2007.0.tar.bz2 sda3/

real    0m2.362s
user    0m0.010s
sys     0m0.127s
root[ahaslam]# time tar xjpf sda3/stage3-i686-2007.0.tar.bz2 

real    5m17.993s
user    0m17.726s
sys     0m2.163s

```

I hadn't tested ext3 (as I've never got on with it). As a lot of you are using it with good results I gave it a spin, using the portage snapshot:
```
root[sda3]# time tar xjf portage-latest.tar.bz2 
real    4m24.161s
user    0m10.756s
sys     0m3.490s

*From usb disk:*
root[sda3]# time tar xjf /mnt/usb/Gentoo/portage-latest.tar.bz2 -C /home/ahaslam/sda3/
real    3m18.882s
user    0m10.809s
sys     0m3.530s
```
So it's twice as quick as XFS for this particular task, though it's still significantly slower than your result. As a bonus the disk is silent while extracting, it makes a racket under other fs's. Strangely, my system becomes unresponsive for a few minutes afterwards, with one core fully used, but with no trace of system activity...

I've checked my bios, sata native mode is enabled, as is ahci. I've checked kernel configs of my various installed distro's & I have ahci built into them all...

The more replies I get, the more obvious it it that there's something wrong, but what & how to check?

Thanks guys, your continued support is appreciated ;)

---

### Post by Rui Pais on 2007-07-01
hi,
well i agree that XFS is one of the best filesystem around. But for a portage tree is exactly the opposite what its needed ;)...
Have you tried to make tests using the kernel source? is usually more conventional for that.
Btw, seems that in that series of tests XFS drop to 2mn. 

My times where taken from uncompress the bz2 on XFS to the same XFS, and then from the bz2 on ext3 to the same ext3. No cross partitions, to reduce extra variables on the "equation". 
I don't know if i read your post right, but seems that you always uncompressed to the same partition, making the output, the witting part of test, the same for all. If i'm not read it wrong here, do you mind to make another round of tests uncompressing for the same partition where the bz2 is?



Anyway, if your ext filesystem times are around 4mn for journalized and 5mn for non-journalized i would agree that something is in fact wrong. And if that are consistent across several distros, i think that would mean either an hardware failure or an incompatible drive with existent sata drivers (less probable).

---

### Post by ahaslam on 2007-07-01
The stage3 bz2 was decompressed in the same partition in the above tests, bar the last ext3 portage test (From usb disk, to illustrate the difference for david_2001).

---

### Post by Rui Pais on 2007-07-01
> **ahaslam said:**
> The stage3 bz2 was decompressed in the same partition in the above tests, bar the last ext3 portage test (From usb disk, to illustrate the difference for david_2001).

The stressing part of the test/uncompressing is writing (organizations of inodes and write data to media) of thousand of files with a few bytes only. 
If you always decompressed to the same partition, that part would be always the same and your times differences reflects only the read of the compressed file.

Here a new test. 
My home partition is an ext3, and i got a XFS partition mounted as Install_X:
- uncompressed bz2 on XFS to ext3: **~46 s**. (fast read of XFS + fast write on ext3) 
- uncompressed bz2 on XFS to XFS:  **~7 mn**. (fast read of XFS but slow,slow write on xfs)
- uncompressed same bz2 on ext3 to ext3: **~1.5 mn**. (no so fast read of ext3 but fast write on ext3)
```
rui@servidor 02:42 PM  ~ $ time tar xjpf Install_X/portage-latest.tar.bz2 

real    0m45.918s
user    0m17.966s
sys     0m7.027s
rui@servidor 02:43 PM  ~ $ cd Install_X
rui@servidor 02:44 PM  ~/Install_X $ time tar xjpf portage-latest.tar.bz2 

real    7m6.683s
user    0m21.443s
sys     0m13.398s
rui@servidor 02:51 PM  ~/Install_X $ cd ~
rui@servidor 02:52 PM  ~ $ time tar xjpf portage-latest.tar.bz2 

real    1m34.674s
user    0m19.328s
sys     0m11.438s
```

My point is that performance at your XFS partition is not bad. 
Is bad only if you try to use it for something that is opposite its purpose. It's good for storage or for root system (that only changes on updates). 
For something require losts of I/O or huge trees/small files, better pick something else.

---

### Post by ahaslam on 2007-07-01
What about my ext3 test:
> root[sda3]# time tar xjf portage-latest.tar.bz2 
real    4m24.161s
user    0m10.756s
sys     0m3.490s
?

I know different fs's have their own pro's & cons suited to certain tasks, but it doesn't seem to matter what fs I use or what creation/mount options are passed. It just seems to plain suck in comparison to everyone else's results. What makes it frustrating is that I can't see anything wrong & my rig oozes performance in many other ways, just not here...

---

### Post by Rui Pais on 2007-07-01
> **ahaslam said:**
> What about my ext3 test:

?

I know different fs's have their own pro's & cons suited to certain tasks, but it doesn't seem to matter what fs I use or what creation/mount options are passed. It just seems to plain suck in comparison to everyone else's results. What makes it frustrating is that I can't see anything wrong & my rig oozes performance in many other ways, just not here...

Thats a bad time for a generic file system like ext3, indeed. 
Maybe your drive has some problem, i don't see what else can make bad writing times. 

Check if you get times like that at your Gentoo and other distros. 
Try to tune ext3 and XFS (the threads i link on my previous posts have good/safe tips) and see if performance improves (i doubt, but who knows...)

Note that if you say your computer is generally fast, maybe that is not a great issue. One don't uncompress huge files at any minute (:)) and some times benchmark and tests can pinpoint some weak part of our system and give them a huge but unreal importance. Every day use is the ultimate test, imho.

And you can try another benchmarks with specialized software like bonnie++ or tiobench... 
 
Sorry i haven't much more ideas :(

---

### Post by Rui Pais on 2007-07-02
hi again ahaslam.

Have you checked the XFS on steroids on Gentoo forum later? Nothing could be more in time... 
[Here is a recent post]("http://forums.gentoo.org/viewtopic.php?p=4125176#4125176") about more or less (not so drastic) your question on slowness of performance (with uncompressing) on XFS.

Apparently mounting with the flag nobarrier improve times a lot.
I have tested on mine XFS. here my new results:
```
rui@servidor 02:24 PM  ~/Install_X $ time tar xjpf portage-latest.tar.bz2 

real    1m12.365s
user    0m21.918s
sys     0m13.178s
```

Here thats a huge reduction from 7mn to 1mn! With uncompressin of kernel source, times with nobarrier are more or less the same as ext3.

Of course that didn't explain your bad times with ext, but at you can try and see if that improves your XFS ones.
Good luck.

---

### Post by ahaslam on 2007-07-02
Thank you, it now beats ext3 at least ;)

```
root[/]# mkfs.xfs -l internal,size=128m -d agcount=4 -f /dev/sda3
meta-data=/dev/sda3              isize=256    agcount=4, agsize=6553516 blks
         =                       sectsz=512   attr=0
data     =                       bsize=4096   blocks=26214063, imaxpct=25
         =                       sunit=0      swidth=0 blks, unwritten=1
naming   =version 2              bsize=4096  
log      =internal log           bsize=4096   blocks=32768, version=1
         =                       sectsz=512   sunit=0 blks
realtime =none                   extsz=4096   blocks=0, rtextents=0
root[/]# mount /dev/sda3 -o noatime,logbufs=8,nobarrier /home/ahaslam/sda3
```
```
root[/]# time tar xjf /mnt/usb/Gentoo/portage-latest.tar.bz2 -C /home/ahaslam/sda3/

real    2m54.460s
user    0m12.309s
sys     0m7.200s
root[/]#
```

And not much worse with the source on the same partition:
```
root[sda3]# time tar xjf portage-latest.tar.bz2 

real    2m56.265s
user    0m11.859s
sys     0m6.363s
```

So it's a big improvement, but I'm still way off the rest of you...

I was thinking of another drive & using raid0, but with an average file size of 2.87K, there's no block size that would offer a benefit here...

Thanks for your support ;)

---

### Post by ahaslam on 2007-07-03
Can anyone recommend a tool to check for disk faults (like a memtest86 for disks)?

I'm going to splash out on a Seagate Barracuda soon & just want to know if this drive is still going to suitable as a backup...

---

### Post by logos34 on 2007-07-03
> **ahaslam said:**
> Can anyone recommend a tool to check for disk faults (like a memtest86 for disks)?

I'm going to splash out on a Seagate Barracuda soon & just want to know if this drive is still going to suitable as a backup...

run a S.M.A.R.T. diagnostic on it.

[B]sudo apt-get install smartmontools

sudo smartctl -a /dev/sda[/B]

---

### Post by ahaslam on 2007-07-04
Thanks for your suggestion. Unfortunatly my drive doesn't seem to support SMART: 
> Device: ATA      WDC WD2500KS-00M Version: 02.0
Serial number:      WD-WCANKD297713
Device type: disk
Local Time is: Wed Jul  4 19:10:36 2007 UTC
Device does not support SMART
I guess this is a safe option to dissable in my BIOS then ;)

Any others?

---

### Post by ahaslam on 2008-04-19
New motherboard seems to better utilize SMART & I got a warning during POST.
I'd not used this drive for anything important since my last post, but some of what's on there is so FUBAR it can't even be copied. 

smartctl output:

```
[root@voodoo ahaslam]# smartctl -a /dev/sdb
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar SE16 family
Device Model:     WDC WD2500KS-00MJB0
Serial Number:    WD-WCANKD297713
Firmware Version: 02.01C03
User Capacity:    250,058,268,160 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Apr 19 16:32:13 2008 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (7680) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  90) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   207   185   021    Pre-fail  Always       -       4616
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2178
  5 Reallocated_Sector_Ct   0x0033   104   104   140    Pre-fail  Always   FAILING_NOW 764
  7 Seek_Error_Rate         0x000f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4772
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2173
190 Temperature_Celsius     0x0022   066   048   045    Old_age   Always       -       34
194 Temperature_Celsius     0x0022   116   098   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       1496
197 Current_Pending_Sector  0x0012   200   185   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   182   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   144   144   051    Pre-fail  Offline      -       1886

SMART Error Log Version: 1
ATA Error Count: 1489 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 1489 occurred at disk power-on lifetime: 4762 hours (198 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 4e 3a 49 e0  Error: AMNF 8 sectors at LBA = 0x00493a4e = 4799054

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 4e 3a 49 17 00      00:32:33.442  READ DMA EXT
  27 00 00 00 00 00 00 00      00:32:33.442  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:32:33.435  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:32:33.435  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:32:33.435  READ NATIVE MAX ADDRESS EXT

Error 1488 occurred at disk power-on lifetime: 4762 hours (198 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 4e 3a 49 e0  Error: AMNF 8 sectors at LBA = 0x00493a4e = 4799054

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 4e 3a 49 17 00      00:32:31.440  READ DMA EXT
  27 00 00 00 00 00 00 00      00:32:31.440  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:32:31.434  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:32:31.434  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:32:31.434  READ NATIVE MAX ADDRESS EXT

Error 1487 occurred at disk power-on lifetime: 4762 hours (198 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 4e 3a 49 e0  Error: AMNF 8 sectors at LBA = 0x00493a4e = 4799054

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 4e 3a 49 17 00      00:32:29.409  READ DMA EXT
  27 00 00 00 00 00 00 00      00:32:29.409  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:32:29.403  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:32:29.402  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:32:29.402  READ NATIVE MAX ADDRESS EXT

Error 1486 occurred at disk power-on lifetime: 4762 hours (198 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 4e 3a 49 e0  Error: AMNF 8 sectors at LBA = 0x00493a4e = 4799054

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 4e 3a 49 17 00      00:32:27.404  READ DMA EXT
  27 00 00 00 00 00 00 00      00:32:27.404  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:32:27.399  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:32:27.399  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:32:27.399  READ NATIVE MAX ADDRESS EXT

Error 1485 occurred at disk power-on lifetime: 4762 hours (198 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 08 4e 3a 49 e0  Error: AMNF 8 sectors at LBA = 0x00493a4e = 4799054

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 4e 3a 49 17 00      00:32:25.383  READ DMA EXT
  27 00 00 00 00 00 00 00      00:32:25.383  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      00:32:25.376  IDENTIFY DEVICE
  ef 03 42 00 00 00 00 00      00:32:25.376  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      00:32:25.376  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: unknown failure    90%      4763         -
# 2  Short offline       Completed: unknown failure    90%      4762         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

Looks like I need a new drive for my media backup. Doubt I'll RMA, heard refurbs are issued...

---

