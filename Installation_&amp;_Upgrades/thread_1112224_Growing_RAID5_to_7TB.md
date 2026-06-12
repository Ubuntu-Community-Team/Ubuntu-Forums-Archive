---
title: "Growing RAID5 to 7TB?"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by zac_haryy on 2009-03-31
I am having this problem with my RAID 5 setup and really need some help here. I setup my RAID 5 server using this guide: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188). All went well with that about 1 year ago. I installed 4 - 1TB hdd's in my server. Then I wanted to add double the amount after the price of the 1TB hdd's went down. I have 8 - 1TB hdd's in my server right now and they are all in the array but I can only use 4.13TB of that 8TB (which if I could get it going right I would be able to use 7TB with RAID5). So To grow the array I used this guide:  [http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/](http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/) This is where I ran into problems. When I went to run this command "resize2fs /dev/md0" I would get an error after about an hour of resize2fs running. This is the error: 
```
resize2fs: Memory allocation failed while trying to resize /dev/md0
```

So trying to find people with this same issue was pretty hard to do. I found a person on this forum with the same problem here: [http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-09/msg01430.html](http://linux.derkeiler.com/Mailing-Lists/SuSE/2008-09/msg01430.html) Basically what I learnt from this site was this quote from there
```
However, there is one last issue. The resize2fs tool does not want
to grow the file system beyond 4.3TB. I was able to run:

# resize2fs /dev/array2/rd2 4300G
```

So then I ran the command "resize2fs /dev/md0 4300G" and I able to get the array to  4.13TB but the problem is I want it bigger so that I can actually use all the 7TB of data that I should be able to store data on. I have been stuck on this for about 5 months now and have gotten nowhere at all with it. I had thought about just making two different RAID 5 arrays with the size varying between the two but then I would have to sets of RAID 5 arrays with two spare disks instead of one. I would rather just have it be one big array so that I can add multiple spares for more protection. If anybody can point me in any direction that would be great I would really like to get this up and running! Thanks!

-haryy

---

### Post by zac_haryy on 2009-04-01
Any thing at all to help me out here would be great! Maybe even other forums to post something along these lines or anything at all? I cannot figure this one out very easily :(

---

### Post by Vico Vicario on 2009-04-02
Are you using ext3 over raid? If so, what is the block size? Find it out with:

/sbin/dumpe2fs /dev/md0 | grep 'Block size'

You need a block size of 4096 to use close to 8TB, and a block size of 8192 to use close to 16TB ([http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)).

I dont know if you can resize a block size...

V.

---

### Post by zac_haryy on 2009-06-09
I checked the block size and It says that it is 4096 yet I still haven't had any success in expanding it past that 4.13TB that it is currently at. Here is what it said in terminal:

```
root@server:~$ sudo /sbin/dumpe2fs /dev/md0 | grep 'Block size'
dumpe2fs 1.40.2 (12-Jul-2007)
Block size:               4096

```

Any other ideas...I am about ready to transfer all data to other hard drives and then create an array using JFS file system. I don t really wanna do this but if I have to I will. Please let me know if anybody has any ideas. Thanks!

-haryy

---

### Post by zac_haryy on 2009-06-09
But with a 4096 I should be able to go up to the 7TB of useable data. So I dont really understand why resizef2s is giving me this error? Is there something that I am doing wrong with trying to resize this?

---

### Post by zac_haryy on 2009-06-09
So I am trying "ext2online" to resize this while it is mounted (although I am not accessing it at all) and so far within 10 min all seems well and has grown from 4.13TB so 4.41TB so far. I just saw that some random person used this app so I decided to give it a shot. Anyways will post back when done for people that would ever run into a problem like this again. Still have no idea why I couldn't get it to go with resize2fs??

-haryy

-ps very happy right now, have had lots of frustration, patience, and time wrapped up into this one problem!

---

### Post by jw_one on 2009-06-10
I am having the same problem growing an ext3 partition from 4TB to 6TB; I get the same error from resize2fs.  I'm very interested to read whether ext2online was successful for you.

If it was successful, where did you find that program?  The versions I could find are over 5 years old and require a kernel patch.

Regarding the 'Memory allocation failed' error message; my machine has only 512 MB of RAM and about the same amount of swap.  Watching 'top' during the 45 minutes resize2fs ran, it was using nearly all the RAM in the system.  The program died suddenly, and 'top' didn't refresh fast enough to track its memory usage.

Does your system more have more memory than that?  I'm just wondering if adding more memory might help.

Thanks,
-JW

---

### Post by zosky on 2010-03-25
hey. my setup seems identical to jw_one, ubuntu karmic w/ 512 ram. growing from 4x1TB to 5x1TB was fine... growing from 5TB to 6TB gave me the memory error :( 

the resize2fs error also said 'try running "e2fsck -fy"'
so i did... then tried resize2fs again (just for kicks)

it worked :biggrin:

before
```
$ df -h /home/
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              3.6T  2.0T  1.7T  56% /home

```
after
```
$ df -h /home/
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              4.5T  2.0T  2.6T  45% /home

```

and ... 
```
$ sudo mdadm -D /dev/md0
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)

```

why does mdadm reports 1TB used, when the df & du report 2TB ?
```
 du -h --max-depth\=1 /home/
2.0T    /home/zosky

```

:confused:

---

