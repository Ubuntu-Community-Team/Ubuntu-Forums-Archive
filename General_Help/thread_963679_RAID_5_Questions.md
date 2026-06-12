---
title: "RAID 5 Questions"
date: 2008-10-30
forum: General Help
---

### Post by Blazef on 2008-10-30
Hello,

I had setup a RAID 5 in my Ubuntu setup (8.04) but had not gone through all the optimization options when setting it up. I setup the RAID without the -m option when using 'mke2fs'( mke2fs man page: [http://linux.die.net/man/8/mke2fs](http://linux.die.net/man/8/mke2fs) ), so I believe I lost about 150 GB to the Super-user reserve, which I don't need as this isn't a startup drive (mainly media on this drive). 

I also didn't set the 'stride' value when using mke2fs, and now I see my write speed has seriously detoriated from 30-40 Mb/s when the drive were not RAID'd, to about 8Mb/s ( I know there is a penalty for parity writing, but would it be in the 20-30 Mb/s range?).

So my questions are:

1. Can I use 'mke2fs' with the -m and stride options without affecting the data already on the RAID 5 ( I know I should back up the data, but I don't have the capacity at the moment, so keeping the data on the RAID is the key)?

2. Based on what I've read, the stride is calculated by 'size of stripe/blocksize' per single drive. So my stride based on stripe of 512k and blocksize of 4k would be 128k (512k/4k=128k ), right?

Thanks in advance

---

### Post by fjgaude on 2008-10-30
The -m sets the reserved block percentage. The default is 5%. You mean your raid5 array is 3TB?

If you change the filesystem I believe you will lose all your data, but I've never tried to change the things you wish to see.

A 64K or 128K stride is what most of us use. If memory serves the default is 64K.

How are you measuring drive thru-put, write speed? Try **hdparm -tT /dev/md[nn]** for cached read speed.

all this points to always having backups of important data. I have three, one online, another near-line, and finally, one off-line. It's that important.

---

### Post by Blazef on 2008-10-30
Thanks for the reply.

Yep, my raid5 is 3 TB, that's why I want to recover the lost space,and why I don't have another backup (for now anyway). I may just experiment with mke2fs on an empty partition to see what happens with existing data.

And using the hdparm command, it appears the source drive I was copying from may be the problem. The raid5 output was as follows:

 > Timing cached reads:   732 MB in  2.00 seconds = 365.27 MB/sec
 Timing buffered disk reads:  462 MB in  3.00 seconds = 153.93 MB/sec

but the source, a raid1 using 2 IDE drives has the following output:

>  Timing cached reads:   790 MB in  2.00 seconds = 394.25 MB/sec
 Timing buffered disk reads:   90 MB in  3.02 seconds =  29.76 MB/sec


The timed cache is faster than the raid 5, but the buffered read is incredibly slow. The cache on the IDE drives must be a lot smaller than I realized (don't remember off the top of my head).

Thanks for your help.

---

### Post by fjgaude on 2008-10-31
Wonderful, but please let us know what your testing ends up showing.

---

### Post by Blazef on 2008-10-31
It appears mke2fs does nuke all the data no matter what switches I tried. Fortunately the 'grow' command in mdadm has a stride option as well, so I'll wait until when I add a drive to adjust the stride option.

Thanks for your help, saved me from a lot of frustration and heartbreak.

---

### Post by fjgaude on 2008-10-31
Well, we all learn something new everyday, if we keep our hearts and minds open.

I thought what you found out was true, now if I can only remember. <smile>

---

### Post by psusi on 2008-10-31
The root reserve option can be changed with tune2fs without loosing data ( though you have to unmount the filesystem to do this ).  The stride can not be changed without a reformat, though it really shouldn't make hardly any difference.  The stripe width option to mdadm sets the width of the raid stripe, which the stride option to mkfs attempts to align important filesystem structures with to make them _slightly_ faster to access.

---

