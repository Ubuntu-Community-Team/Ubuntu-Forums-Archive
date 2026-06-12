---
title: "SSD Lifespan increasing tricks?"
date: 2012-04-21
forum: Hardware
---

### Post by jcllings on 2012-04-21
So I ordered a new laptop with an SSD in it but I hear they crap out a lot.  I also spotted this article which details measures for extending the life of your SSD on Windows: 

[http://lifehacker.com/5802838/how-to-maximize-the-life-of-your-ssd](http://lifehacker.com/5802838/how-to-maximize-the-life-of-your-ssd)

Does anyone know of a similar guide for Linux? I have many questions. For example, my new machine has like 16 GiB of memory so I doubt I'be be doing a lot of paging. I suppose I could get a small non-SSD hard drive for the swap partition and put some of the caches there. I don't care much for this idea though, because one of the big advantages of SSD's is power savings. Add a hard drive and you loose that. I do keep almost everything in the Google cloud. So much so that it just doesn't seem like I need backups much any more. What I intend for this machine is JEE software development using an IDE that does a lot of indexing. This seems more read intensive than write intensive though. 

What about getting another drive and making a RAID array or a mirror or something? 

Thoughts? Ideas? Links or resources? 


Jim C.

---

### Post by BertN45 on 2012-04-21
With that amount of memory you could work without the swap partition. I did so for half a year with Ubuntu 10.10 with only 2GB of memory.

---

### Post by ahallubuntu on 2012-04-21
I wouldn't do without a swap file.  I have seen many cases where the operating system uses a swap file anyway even when it wouldn't seem to be necessary.  In some cases it may improve performance.  Plus, FYI, if you ever want to use hibernation (which would be super fast with an SSD since the image is written to the drive), you will have to have a swap file in Ubuntu.  You might worry that hibernation puts extra wear on the SSD over time, but it also saves wear on your battery since you wouldn't need to use suspend; hibernation would probably be fast enough not to need suspend.

I wouldn't worry about wearing out your SSD.  Just use it and make regular backups as you would for any other hard drive, assuming it might fail at any time.  FYI, your SSD firmware contains load-balancing algorithms to avoid constantly re-writing the same blocks over and over again.  That's one important way an SSD is different from simply a USB flash drive you can treat as a hard drive: no load balancing there so much easier to wear it out.

If your SSD wears out in 4-5 years (highly doubt it), by then a replacement of the same size will either be super cheap or too small to be available - and the smallest SSD you could buy to replace it is likely going to be a lot cheaper than what you paid for this one anyway.

---

### Post by jcllings on 2012-04-22
Here is an idea... 

Do kernels still have the "swapiness" setting? Perhaps I could create a small swap partition and simply arrange for it to only be used in emergencies via this setting?

---

### Post by jcllings on 2012-04-22
Here is another idea. If I create a RAM drive, could I use that for the swap partition? This seems reasonable since swap partitions are often wiped on restart anyway.

---

### Post by ahallubuntu on 2012-04-22
So you are not planning to use Hibernation at all?  If you do, you need a swap partition at least as large as your RAM.  That is, if you have 8GB of RAM, you need an 8GB swap partition minimum.

---

### Post by jcllings on 2012-04-22
> **ahallubuntu said:**
> So you are not planning to use Hibernation at all?  If you do, you need a swap partition at least as large as your RAM.  That is, if you have 8GB of RAM, you need an 8GB swap partition minimum.

I've gotten kind of used to not having it as this machine is ACPI 5.0 which isn't supported yet in the kernel. Supposed to be in the next kernel though. If I let it sleep or hibernate it will not wake up.  System76 will have already checked to see if it works on the new machine. Says it does right on the specs for it, anyway. I suppose I should bug them for MTBF on the drive model in question.

---

### Post by ahallubuntu on 2012-04-22
Wow - a laptop without standby or hibernation support?  Not something I'd be able to use.  I never shut my laptop down or restart it unless I have to.

---

### Post by jcllings on 2012-04-22
Yet another idea: Put the swap partition on an SD card? :-)

---

### Post by ahallubuntu on 2012-04-22
Yes, you could totally put the swap partition on an SD card.  That would be slower than using the SSD itself most likely; it may slightly reduce the wear-and-tear on your SSD, but again, in my opinion, it's not worth the trouble.

---

### Post by jcllings on 2012-04-22
> **ahallubuntu said:**
> Wow - a laptop without standby or hibernation support?  Not something I'd be able to use.  I never shut my laptop down or restart it unless I have to.

Ya. The machine to be replaced is quite the lemon and not just for that reason. The GPU fan screams at top velocity at all times using the Linux graphics drivers and if you use the proprietary ones, it locks frequently. It's actually a GSOD but you don't see it because of the locking. 

That's on the Linux side. On the Windows side, you have the same problem with the proprietary graphics drivers unless you use the ASUS drivers and not the ATI drivers. In other words don't update. There's also a known BSOD when the machine goes into certain low power states as the USB 2.0 drivers don't work right. Found a work around for the BSOD eventually but it took quite a while before somebody else figured it out. About 8 months. It involves using ThrottleStop to keep the machine from sleeping quite so deeply. I was even able to keep the work-around completely transparent to the user. Point is that I shouldn't have to do all this crap.  

I seriously recommend not buying department store machines. They have been nothing but trouble for me. System76 is my new dealer unless they tick me off. I doubt they will though.

---

### Post by jcllings on 2012-04-22
> **ahallubuntu said:**
> Yes, you could totally put the swap partition on an SD card.  That would be slower than using the SSD itself most likely; it may slightly reduce the wear-and-tear on your SSD, but again, in my opinion, it's not worth the trouble.

Hmmm... Another idea: I could couple an extended warranty with prodigious backups. It's unlikely I would loose any significant data anyway, since the only loosable data on my machines is code that hasn't been checked in yet and I use subversion branches and check in frequently so there isn't much of that either. The rest of my stuff is in the Google cloud or already on an SD card somewhere.  

I'm liking this one.

---

### Post by 23senick on 2012-04-22
I found this a really useful guide:

                       [LEFT][COLOR=#0000ff]***[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/) ***[/COLOR][/LEFT]
   
    
Problem I had was slow write speed on the SSD in my Acer Aspire One.  Not sure that's so much of an issue with recent SSDs.  The guide at this link helps by showing how to reduce journal writes to the SSD, setting up a tmp file in RAM and getting Firefox to save its cache there instead of SSD, and using an in/out scheduler that is better suited to SSDs.  

Hope that helps

---

### Post by jcllings on 2012-04-22
> **23senick said:**
> I found this a really useful guide:
...
scheduler that is better suited to SSDs.  
Hope that helps

Hmmm... This article would seen to indicate that the write-endurance issue is mythological anyways, despite what appears to be significant anecdotal evidence to the contrary:

[http://www.storagesearch.com/ssdmyths-endurance.html](http://www.storagesearch.com/ssdmyths-endurance.html)

---

### Post by ITPhoenix on 2012-04-22
[FONT=Arial][SIZE=2]The main question is increasing the lifespan.  This is primarily accomplished with fstrim.  It could be scheduled with cron for any partition you wish and/or by [COLOR=#000000]editing the /etc/fstab file, with "discard" where fstrim will execute upon start or reboot.  [/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#000000][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=#000000]I read somewhere fstrim should not be used on the swap partition while the system is running, but I never found out why.  I do not even know what kind of file format the swap uses (hopefully someone can help with this).[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#000000][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=#000000]As far as putting paritions on different physical drives, I heard that root and home increases speed.  As far as the swap, the low price of memory and the slow speed of the swap partition, especially with a mechanical drive, seems to make no sense, unless the partition is necessary for your uses or applications.[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]This is good [/SIZE][/FONT][[FONT=Arial][SIZE=2]http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux[/SIZE][/FONT]]("http://techgage.com/print/enabling_and_testing_ssd_trim_support_under_linux")[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]FSTRIM manpage [/SIZE][/FONT][[FONT=Arial][SIZE=2]http://www.vdmeulen.net/cgi-bin/man/man2html?fstrim+8#index[/SIZE][/FONT]]("http://www.vdmeulen.net/cgi-bin/man/man2html?fstrim+8#index")

---

### Post by jcllings on 2012-04-22
> **ITPhoenix said:**
> [FONT=Arial][SIZE=2]The main question is increasing the lifespan.  This is primarily accomplished with 

What I am hearing and reading is that SSD tech is evolving quite rapidly and consequently wear leveling is increasingly likely to be automated in firmware. I just read in an article that recent tests run by a storage pro were showing 90% of newly released SSD hardware can last for 51 years if all anyone ever did was write to em all day long using real time recording apps. So maybe it's just a bad rap from old hardware. On the other hand I am hearing quite a bit of anecdotal reports to the contrary, so maybe it's not.  I think it's best that I ignore neither of these for now. The knowledge of what situations are possible is certainly useful but I suppose I must take both of these with a grain of salt until I have the actual make/model/vendor of the hardware in hand. The warranty is good for a year so I'll just configure it as best I can and keep good backups.

---

### Post by ITPhoenix on 2012-04-22
I agree. The technology is changing by the day, and we need to know what the hardware is capable of.  I have a bad habit of not reading all the specs of a particular piece, and as a consequence, there is a big box of stuff collecting dust.
 
I made my comments with the presumption we were talking about drives that were released within the past few years.  If the drive has self-leveling, it would be a good idea to read the docs so we do not do anything to decrease its life. Perhaps fstrim would actually hurt that drive.
 
I have a W7 on a WD with Diskeeper--a mindless solution.  They claim their system adds to the W7 trim support to increase life as well as performance--no problems yet.   I also have run Linux on an OCZ Vertex 2 with just "discard" surmising that my reboots were so frequent I must be trimming it often enough.  I experimented with fstrim first using a bash one liner that does all the partitions in verbose mode. A terminal window pops up with the results, and stays there until you close it.  No problems with that setup yet.
 
There is also the question of frequency.  It appears from the literature if many files are written and then deleted continually, the need to trim more frequently is beneficial. Admitedly, I have only cursory knowledge of this subject.  I need to go research again to see if anything has changed or if I missed something. I do know that heat is a big enemy of any ss device, so I would want to make sure my SSD always runs cool even if a fan has to be added.   It is possible to mount it in what I call a hot spot.  One could use an aluminum 2.5 to 3.5 adapter but I feel a fan is better.  These drive get very hot when writing (and reading?) huge amounts of data.  I noticed this during clean installs of the OS and backup restorations. Otherwise it is cold as ice.
 
Part of your original question was if one document could put this all together and answer all of out questions to our satisfaction.  I did not find one.  I found several--many in the forums.  I would read all of them and compile the info you need into a file for future reference.  I am lazy and just copied them to a folder.  The bottom line I gathered is that a) trim should be performed and b) its frequency is proportional to the write-erase operations.
 
No one has automatic software to do this for Linux AFAIK, as is the case for live automated backup like Acronis or the W7 Image Backup.  I use Image for Linux--it has to be booted every time, but it works good.

---

### Post by oldfred on 2012-04-22
I did not put discard in right away in my fstab. So it ran this:

Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox ssd
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

