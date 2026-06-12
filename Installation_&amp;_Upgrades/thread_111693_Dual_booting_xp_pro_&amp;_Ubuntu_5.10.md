---
title: "Dual booting xp pro &amp; Ubuntu 5.10"
date: 2006-01-02
forum: Installation &amp; Upgrades
---

### Post by bigguy on 2006-01-02
Hello all, very nice place you have here. I have a question. If I want to install ubuntu on my xp pro box is it as simple as putting the install cd in and following the onscreen instructions ? It will create a partition and install ? I dont want to lose or screw up myxp pro. I`m VERY new to ubunto but I really want to give it a shot.

---

### Post by DoorGunner on 2006-01-02
Yes, Pretty much so.

However, I decided that i wanted to have a partition that i could use to share between both xp and ubuntu. (Ubuntu and xp can both have read write access to both). That way you can put mp3s, pictures and other files that you may want to use in both. 

In order to do that i used a windows program called Partition Magic to create a 25Gb fat32 file for the share and reclaim some unused space for Ubuntu.

If you are interested there are some screen shots in this link that will show you what the Installation process is like.
[http://shots.osdir.com/slideshows/slideshow.php?release=475&slide=2](http://shots.osdir.com/slideshows/slideshow.php?release=475&slide=2)

---

### Post by bigguy on 2006-01-02
Ok I`ll check that out, thanks. Plus I have just read that there are readwrite issues with the ntfs file system, This is what my harddrive is is ntfs. Am I going to have any problems with this ?

---

### Post by DoorGunner on 2006-01-02
If you creat fat32 partition there is no problems or worries. It will show up in your windows mycomputer as another drive. In Ubuntu you will need to mount it in. You can worry more about that later.:)

If you are going this route dont forget to defrag your computer first then do your partitioning.

---

### Post by bigguy on 2006-01-02
So I should: Use Partition magic to create another partition on my drive and make it fat32 and install ubuntu 5.10 into that partition ? Is this right.

here is a screenshot from Partition magic, does this look right ?

[IMG]http://img.photobucket.com/albums/v704/bigguy982/screenshot.jpg[/IMG]

---

### Post by DoorGunner on 2006-01-02
What i did was in this order

1 Defrag your computer
2 resize your current partition (partition Magic) taking into account both space sizes for your   share and your Ubuntu
3 make a fat32 partition (partition Magic) in the unused space for your share drive
Install Ubuntu using Ubuntus partition option of Using the remaining empty space.

If you dont have partition magic there are other partitioning tools there. I just found it easy to use and handy.

sound simple?

---

### Post by bigguy on 2006-01-02
Check the above screen shot it wouldnt allow me to make a fat 32 on an ntfs so it made a Ext2 partition and a swap file. Does that look right ?

---

### Post by mach on 2006-01-02
I'm currently dual booting.. xp and ubuntu.

The way I have it set up, I have divided my hd into 3 (well 4 with swap) parts.

20GB for linux (ext 3 journaling file system)
1 GB for linux swap
20GB for windows (ntfs - read-only)
113GB for a mutual partition (must be fat32 to get write access)
---------
~154GB hd

I posted because I think bigguy wants to install ubuntu onto the fat32 or ntfs partition, which you can't do.

If you have a program like Partition Manager, you can downsize your current NTFS windows xp partition to a smaller size w/o losing any data. This will free up space so the installer can create ext 3 and swap partitions to install ubuntu.

People merely suggested a seperate fat32 partition because both Windows and Linux can read and write to it.

Godspeed,
mach.

---

### Post by mach on 2006-01-02
In response to the screenie uploaded while I was in the middle of my previous post, I'm fairly sure the ext2 (or 3 - doesn't matter) partition has to be a primary partition, not a logical one. But other than that, it looks good.

From personal experience, I had trouble getting GRUB to install on the same hd (worked fine when GRUB/ubuntu was installed on a seperate HD), so have your windows XP cd handy in case GRUB doesn't install. (fix MBR info [here]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp")).

---

### Post by bigguy on 2006-01-02
Does the above screenshot look right ? Have have not applied these changes yet but am waiting to do so. I asked Partition magic to create a linux partition and this is what it did. Screenshot is a couple posts up.

---

### Post by bigguy on 2006-01-02
It said it should be logical so I let it do it all. So then this should be fine ?

---

### Post by DoorGunner on 2006-01-02
actually what i would have done is add the linux to the other end......

your xp will reside first. (warning if you try to put it there you will loose your xp)

In order it should look like this in this order

c://drive>> Freespace                  (freespace will appear by resizing, you can grab the right side of pink box area and move it like resizing a window)

apply it and let partition magic do its thing (it may take a few minutes)
-------------------------------------------------

Then add Fat32 so it looks like this

c://drivre >> fat32>> Freespace

just leave the free space and Ubuntu will do the rest.

-----------------------------------------------

---

### Post by bigguy on 2006-01-02
Question: Does it matter which comes first? and is the only reason I need fat 32 so I can share between the 2 partitions ?

---

### Post by DoorGunner on 2006-01-02
Yes "Windows will be first" thats just the way it was installed on your computer.
If you put it in as it is you will erase windows

As far as Fat32 I found it easier to install it after you have enough freespace.

with partition magic if you try and put it in after it will give you greif

---

### Post by mach on 2006-01-02
It doesn't matter. I personally have Ubuntu's partition first. And yes to the fat32 question.

Your best bet is to let Ubuntu's installer handle the partitioning of the free space (21885.4MB in your case), rather than PartitionMagic.

Just delete the two partitions (edit: swap and ext2.. don't delete ntfs or you'll lose windows ;)) you made with PartitionMagic (it should be designated as Unallocated or Free space or something similar). And let the installer handle it with its automatic allocate free space feature.

---

### Post by DoorGunner on 2006-01-02
I concure with Mach

---

### Post by bigguy on 2006-01-02
@Mach: So your saying just use the install disk to make the partitions and such ? what bout this.

> Issues with Windows XP and NTFS

Note: most current Linux distributions, including Ubuntu, do not support write-access to NTFS partitions; only read access is supported. Write-access is available through commercial packages or in some experimental open-source packages which may be risky to use. See NTFSReadWrite for more info.

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by mach on 2006-01-02
Yes. Partition w/ install disk. Keep windows xp cd handy incase GRUB fails to install. (you pop the cd in, go to recovery console and type fixmbr).

AFAIK, any sort of ntfs program that lets your write to ntfs drives from linux is very experimental, and not recommended. Reading is fully supported, however. So if you have media (i.e. mp3s, avis, etc) on your 92GB partition, linux can access those files perfectly.

If you need linux to be able to write to a drive that can be accessed by both linux and windows, downsize the 92GB partition and form a fat32 one.

---

### Post by bigguy on 2006-01-02
Ok I guess I`ll give it a go and see how it goes then.

EDIT: Any last words of advice ?

---

### Post by mach on 2006-01-02
good luck ;)

If you get an 'error loading OS' message, that means GRUB didn't install correctly. fixmbr, and you will be back up.

Keep us updated.

---

### Post by bigguy on 2006-01-02
I`ll be back to tell you how it goes, It shouldnt take long (I hope) Going now thanks for the help.

---

### Post by socrazy143 on 2006-01-02
I think this got a little more complicated than it needed.

First forget about Partition Magic cause you gotta pay for it.  Instead use Bootit NG from [http://www.terabyteunlimited.com/bootitng.html](http://www.terabyteunlimited.com/bootitng.html).  It is pretty simple to use.

Defrag your hard drive first.
Then turn the ISO for BootIT NG into a real CD with Nero or whatever you use.  Pretty soon you will be using GnomeBaker and your life with get easier.

Next make sure your computer can boot to CD-ROM and boot using your frest BootIT NG CD.  Follow their instructions but for the most part you will be shrinking your Windows partition to make room for free space.

After the shrink, take out the BootIT NG CD and put in your Ubuntu CD.  Boot from the CD and follow the directions.  When you get to partitioning DON'T ERASE the entire drive.  Instead either manually partition or just use free space to install.  You should be good to go.

Quick and dirty just the way I like it.

---

### Post by bigguy on 2006-01-02
Ok well I just went through a bit of the install. I came to the part where it asks for how big the new partition should be, It said I should make it 75.5 gig well i put that down to 50 gig and pressed enter and it sat on a blue screen for about 5-10 minutes doing nothing.(No cd activity just harddrive ) I thought something was wrong so I took out the cd and restarted where apon scandisk started and recovered a whole bunch of orphaned files. I thought it was supposed to confirm the partitioning before it started to do it ? Was I doing something wrong or should I have waited.

---

### Post by mach on 2006-01-02
75GB? I thought you only had 22GB~ of free space. If you're erasing the entire partition table, then you'll lose Windows.

You only want to partition the **free space** you have left over.

So, select manually edit the partition table, and select "Guided Partitioning" near the top choosing the free space you have left over. It'll automatically create the two (ext3 and swap) partitions for you in the space provided and not overwrite Windows. I had a site that depicted these few steps in screenshots, but lost it. I hope my directions are clear enough, though.

---

### Post by Substance on 2006-01-02
I believe its the ultimate ubuntu guide..but thats more confusing than it is helpful.
[[Ultimate Ubuntu Guide](http://users.bigpond.net.au/hermanzone/)] *kinda confusing*

heres the debian guide...!! 
([color=red]**PLEASE READ THE WHOLE GUIDE BEFORE TRYING...(AND PRINT OUT A COPY)**[/color]

[[Debian Dualboot Guide](http://aboutdebian.com/dualboot.htm)]

---

### Post by bigguy on 2006-01-03
**@ mach:** No I never said that as a matter of fact I have 120 gig.

**@Substance:** Thanks for the guide I`ll read that. I`ll probably be back with more questions.

---

### Post by SighKick on 2006-01-03
I came across a great tutorial video to create a Windows XP / Ubuntu Linux dual boot computer.

This was made for the WVU ACM's Linuxfest / Installfest on October 26th, 2005.

[Video  Tutorial Windows / Ubuntu Dual Boot Setup]("http://video.google.com/videoplay?docid=-6104490811311898236&q=")

Tested the link and its ok.

---

### Post by Substance on 2006-01-03
My only problem with that video is that its poor quality. -_- and yea you cant print a copy of a video for later reference... lol

---

### Post by Substance on 2006-01-03
[QUOTE=bigguy]**@ mach:** No I never said that as a matter of fact I have 120 gig.

**@Substance:** Thanks for the guide I`ll read that. I`ll probably be back with more questions.[/QUOTE]

The debian guide ive found alot easier to understand. It provides you with two methods single hardrive method, and two-hardrive method...

---

### Post by bigguy on 2006-01-04
Thats very nice, thank you. I will watch this a couple times and get to it. Thanks for the find.

[QUOTE=SighKick]I came across a great tutorial video to create a Windows XP / Ubuntu Linux dual boot computer.

This was made for the WVU ACM's Linuxfest / Installfest on October 26th, 2005.

[Video  Tutorial Windows / Ubuntu Dual Boot Setup]("http://video.google.com/videoplay?docid=-6104490811311898236&q=")

Tested the link and its ok.[/QUOTE]

---

### Post by bigguy on 2006-01-04
Well...I got it. I finally installed ubuntu linux 5.10 on a windows xp pro system (Dual boot) As a matter of fact I am using it right now to be able to be on the net to type this. I had a small problem with the network, it didnt configure during install. Then I couldnt get the internet working on xp pro, so I disconnected the cable modem and reconnected it and it came on in xp pro and then all I had to do was enable it in the networks icon and here I am. Thanks for all the help dudes, this was worth it. I like it so far. Is there anything I should be updating so its all up to date ???

---

