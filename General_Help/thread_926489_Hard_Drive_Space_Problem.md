---
title: "Hard Drive Space Problem"
date: 2008-09-22
forum: General Help
---

### Post by jman24 on 2008-09-22
Hi, I just switched from vista to ubuntu on my laptop and I didn't want vista on my computer anymore so when I ran the livecd I chose the option of Installing Ubuntu on my 250gb harddrive and not partioning it or anything.

I've had some problems with Ubuntu, so I reinstalled about 2-3 times. And everytime I chose to have Ubuntu installed on my hard drive without any partions. Now it works fine, but there is a problem with my hard drive now.

My hard drive is 250gb, Ubuntu shows that the total space I've used up in my contents is 7.4gb and that the free space that I have is 208gb.

 My question is, What Happened to the Other 30 Gb of MEMORY!!! 

Please, any help would truly be appreciated.

Thanks again

---

### Post by Tag_yer_dead on 2008-09-22
probably not the problem (in fact im sure its not) but is it possible that the manufacturer put some sort of recovery partition hidden on the hard drive?

---

### Post by wolterh on 2008-09-22
If you have re-installing ubuntu as an option, I would recommend you to run a live session, and--before starting the installation process--run the partition editor (System > Administration > Partition editor) and select your hard-drive, and format as ext3. Afterwards, you should install on that partition. Anyway, as I can infere, you do not like to partition, but I'll tell you this: it is not difficult nor hard to understand at all.. Is like making bounds in your hard drive, even though, sometimes it may be mysterious how much space to assign to each partition.

I strongly recommend to make a /home partition so that everytime you reinstall ubunu or something you do not loose your information.

If you need any further help, do not bother to ask.

---

### Post by jman24 on 2008-09-22
Thanks for all your replies. 

I was just wondering where the 30gb went, I mean I never partitioned it, it can just dissapear, can it?

---

### Post by jman24 on 2008-09-22
screenshot using gparted

---

### Post by jman24 on 2008-09-22
Oops, here is the screen shot without the window blocking it, sorry 

By the way here is a screenshot of the hard drive information using gparted, does this mean I have 232gb? If so, where is the other 20gb?

---

### Post by wolterh on 2008-09-22
Well, I would really appreciate if you did not put a window over the partition data, because I could not read well what lied behind the screenshot taking window...

---

### Post by Ryadt on 2008-09-22
Have a look here: [http://www.computing.net/answers/hardware/lost-hd-space/13838.html](http://www.computing.net/answers/hardware/lost-hd-space/13838.html)

---

### Post by wolterh on 2008-09-22
Well, first of all, you are using some of the space (9.5GB) for swap. That would make your harddisk 2.40 MB. If you substract the 4GB used, you can see that you have 2.36GB. Now, I do not know what is contained by that 'Used' space. It happend to me also. Maybe is just what Tag_yer_dead said, maybe the disk kept some backup. 

Now, you are getting that you have a disk with 2.32GB free.. Gues what? The sizes of the disks are never exact. I really do not know why, but I think that it is required to much precision to achieve correct numbers in hardware, but that is just a guess...

---

### Post by prshah on 2008-09-22
> **jman24 said:**
> 
My hard drive is 250gb, 

First of all, manufacturers treat GB as 10^10, instead of 2^30 (which is what it should be, and is correctly calculated so in Linux.) To differentiate between the two, linux uses the terminology GB for 10^10 and GiB for 2^30.

That brings your 250GB down to 232-odd GiB.

Of this, your swap takes (approx) 9.5 GiB. That brings it down to 222 GiB.

Of this, about 5% is reserved for root operations (to allow the computer to continue operating in case of disk drive getting full) That brings it down to 210GiB.

You've used up about 7.5 GiB, so that should leave you with 203GiB. 

So there is no diskspace "lost".

QED.

btw, 10Gb for swap is not required for day-to-day use. You can have swap ranging from 512MiB to 1.1*RAM, whichever is higher. More than that is required only if you are using memory heavy operations, such as large scale printing (for hoardings).

---

### Post by jman24 on 2008-09-22
Thanks, I thought there was something wrong with my hard drive for a second.

---

### Post by TeXtonyx on 2008-09-22
disk
             description: ATA Disk
             product: WDC WD2500BEVS-6
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WXE308CU2827
             size: 232GiB (250GB)

1) 1GiB equals 1, 073, 741, 824 bytes -- over a billion

2) 1GB equals 1,000,000,000 bytes -- exactly a billion

So if you multiply the number after 1) by
232 it comes out to just about 250 billion bytes.

Computer manufacturers use the number after 2)
while computer OS use the number after 1)
and it has been that way for some time. If you
look at your snapshot, it says size: 232.88 GiB

---

### Post by Greyed on 2008-09-22
Remember to edit your message and mark it as [Solved] so people know at a glance you've gotten the answer you seek.

---

### Post by wolterh on 2008-09-22
Well, it seems like the HDD Experts have given out the word now, so you may now completely discard my non-sense-ness

---

