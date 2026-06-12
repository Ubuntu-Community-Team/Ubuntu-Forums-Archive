---
title: "Partition confusion"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by Annigma on 2009-11-10
Hello ):P

I've just done something daft! After burning an iso I ran it (wubi) and pressed enter to 'install side by side'... (I wanted to look up and check what to do but other computer was in use so.. impatience got the better of me! ](*,) )

Anyway, I assume I can't undo this, since it warned me that I wouldn't be able to, so I guess I'll have to wipe everything and start over.. I only installed Win7 yesterday so it's not a big deal. Just annoying (annoyed at myself!)

So... I'd like advice on the correct/best way to go about it. 
I want to dual boot Win7 and Karmic, and I'd like a third partition for data. I've got 250Gb and thought something like 80/80/90 would be best..?
I've got an idea in my head that I don't want Windows on C: as that's the most vulnerable place for it to be, from a security/virus point of view. Is this founded?

This is how I think it should be:
Small boot partition: Windoze/Grub..? don't know
Win7 (Primary) partition: preferably not C: ..? (NTFS)
Karmic (Primary?) partition (& a couple of logical/extended? partitions for /home and /swap..?) (linux filesystem..)
Data partition: Doesn't need to be FAT32 anymore - Can read/write NTFS from Win and Ubuntu..? (Get Ubuntu installer/partitoner do this or do it later?)

Install Win7 first, then Ubuntu, choosing to partition myself this time.. 

I know there are guides, but it gets confusing when you want to do something slightly different (and you don't know what you're doing! :lolflag: )

I await your advice patiently.

:)

---

### Post by darkod on 2009-11-10
First of all, you might not have to reinstall Win7. Wubi installs Ubuntu sort of like a virtual box, it shouldn't make any changes to your partitions even if you selected side-by-side.

You can check this easy by going into Win7 control panel, then admin tools, then computer management, then disk management from the side menu.

Or just windows button + R open a small window, type "diskmgmt.msc" with no quotes hit enter and it will open disk management. Your partitions should be the same as before.

Wubi should have "installed" Ubuntu just as a software. Go into control panel, programs and remove/uninstall it. And that should settle it.

Then start thinking about organizing the partitions for the proper install of Ubuntu, come back with ideas and someone will help.

---

### Post by darkod on 2009-11-10
First of all, you are probably aware, your 250GB does not have 250 real GB. It has around 250 bln bytes which is not the same. 1GB is 1024*1024*1024 and not 1bln.

For that drive I believe the real size is around 233GB. Take that into account so you will have no surprises later.

My setup is:
C: ntfs primary
D: ntfs primary
/ ext4 primary
swap 2GB (double the RAM but no need to be than 2GB from what I've read) logical part
/home ext4 logical

Depending how much windows programs you use and their size, 80GB is a waste. I too had the same size and on the latest install lowered it to 65GB. That is still plenti for software. Mind you I don't play games and have no idea how much space they consume.

The above is true for Ubuntu partitions too. 15GB for / sounds more than plenty, 2GB for swap, 10GB or similar for /home.

Remember you will still have D: as data partition available to both OS. Work around the numbers depending your needs.

---

### Post by Annigma on 2009-11-10
Thanks for the quick reply darkod :)

I realise now I wasn't clear. When I downloaded the iso.torrent I thought I'd done the wrong one, since it said 'wubi', and I'd read this was for installing Ubuntu inside Windows, which I don't want. However, after more reading I decided that it should be able to do a full install, so booted from it and chose to install.

I could see from the installer that the Win7 partition had 'grown', and realised I'd messed up. I've taken out the DVD now and booted back into 'Windoze'. It appears to be about 30Gb bigger than before :shock: so.. it's probably easier to start over..

Re. partitions, other than what I've put in my first post, I'm really not sure. I was hoping someone would help me out there..:D I'll go off now though and do some more research and try to put a better partition plan together.

:)

---

### Post by darkod on 2009-11-10
If it helps, here is mine partitioning also on 250GB drive:

C: 65GB ntfs primary
D: 141GB ntfs primary
/   15GB ext4 primary
swap 2GB logical
/home 10GB ext4 logical

---

### Post by Annigma on 2009-11-10
That's extremely helpful. Thank you :)

I take it from looking at your setup that Ubuntu is fine with NTFS now i.e. can read and write to/from it? :cool:

I'm just trying to find out whether my idea that Windows shouldn't be on C: has any rhyme or reason; and looking into whether I can put it elsewhere. I believe that as long as it's on the first Primary partition it's okay, but research ongoing.. :P

---

### Post by darkod on 2009-11-10
Actually I installed Ubuntu yesterday, so I haven't tested it too much with ntfs.

But yes, when you click on ntfs partition to open it, it will just ask you again for your ubuntu account password and it will mount it. I have even created a bootable USB stick with the ubuntu usb startup disk creator tool and the ISO was on my D: ntfs partition. Ubuntu created the USB stick successfully even like that.

I haven't tried writing to ntfs yet though.

---

### Post by Annigma on 2009-11-10
Thanks again darkod :)

Haven't found much confirmation that I'm right about C: being vulnerable. A couple of bits [here]("http://www.wisegeek.com/what-is-a-c-drive.htm") and [here]("http://partition.radified.com/partitioning_4.htm"), but one is at least three years old..

Anyhoo, here are my latest thoughts:
C: Primary FAT32 'DOS' partition 2-5Gb
D: Primary NTFS 'Win7' partition 70Gb
Extended: 
Logical 1: /ext4 (is that the same as /root?) 20GB?
Logical 2: /swap 2GB
Logical 3: /home 10GB..?
Logical 4: /boot 1GB...?
E: Primary NTFS 'Data' partition ~100GB (Karmic apparently can read and write to NTFS, so both OS' can share this partition)

Will I be able to use the unallocated space to make any of the others bigger later if needed, or will the 'architecture' I(will ha)'ve created prevent that..?

Any thoughts on vulnerabilities of C: ?
Will Karmic be 'happy' in one extended partition?
Do I need /boot?, or just the other 3, or something else..?

Thanks

(Off to watch 'Collision' now :D )

---

### Post by Annigma on 2009-11-11
Okay, after much digging around, reading, researching, etc. I've come to the conclusion that whilst C: may have been vulnerable once, it is unlikely today. A virus that is only able to target C: is likely to be eaten alive by the even most basic AntiVirus program :P

So.. I can go with a much more 'normal' setup like yours darkod =D>

Just before I attempt to use Gparted (on Wubi disc?), let me check... Am I able to undo whatever it did before when I chose 'side by side' and it increased the Win7 partition by about 30 Gigs..? (Can I just shrink it, or did it 'put stuff' on there..?)

If so, I'll try and setup the Karmic partitions manually (from wubi). If not, I'll start over and create partitions for everything (wubi), making C: and /ext4/root/'whatever it's called' Primary, and /home and /swap Logical. That'll mean I'll have to make the data partition primary too.. better to have all Ubuntu stuff in one extended partition..(Linux doesn't care does it?)?

Lastly (for now :P), am I right in thinking that I don't need to format as such i.e. specifically. I can run Wubu (Gparted?) to create partitions, then install Win7, then install Karmic?

Thanks for the help so far. [COLOR="White"]I do hope someone replies...[/COLOR]

---

### Post by darkod on 2009-11-11
You don't need /boot specifically as partition. A folder boot will be created in / (root).

You can use available free space to expand and sometimes also shrink, but that is a process that takes very long and it puts your data at risk.

My suggestion: If you have all your data backed up both from windows and ubuntu, do a clean install of windows, then of ubuntu.

Make a good plan for the partitions because any shrink/expand later is a pain. I waited 1hr for 80GB partition to be moved by Gparted so I could add 15GB to it. Using shrink/expand fron within windows is even more limited (to free space made by shrink is always to the right of the shrinked partition and you can expand partitions only to the right).

I would suggest something similar to my setup, of course you can change the sizes of the partitions.

Why do you need the DOS C:? Something specific?

In case you really need it:
C:
D: windows 7
E: ntfs for data for both OS, largest partition
These three can be primary. Install win7. Then install ubuntu selecting manual partitioning and create logical:
/ ext4
swap 2GB
/home ext4

Cheers.

PS. You say you will create partitions manually from wubi. Do not confuse wubi now, wubi is to run ubuntu as a software program from within windows. You will install Win7 first with its DVD and then boot with the Ubuntu CD and select the Install option and go from there. Wubi is not involved.

---

### Post by raymondh on 2009-11-11
> **Annigma said:**
> Thanks again darkod :)

Haven't found much confirmation that I'm right about C: being vulnerable. A couple of bits [here]("http://www.wisegeek.com/what-is-a-c-drive.htm") and [here]("http://partition.radified.com/partitioning_4.htm"), but one is at least three years old..

Anyhoo, here are my latest thoughts:
C: Primary FAT32 'DOS' partition 2-5Gb
D: Primary NTFS 'Win7' partition 70Gb
Extended: 
Logical 1: /ext4 (is that the same as /root?) 20GB?
Logical 2: /swap 2GB
Logical 3: /home 10GB..?
Logical 4: /boot 1GB...?
E: Primary NTFS 'Data' partition ~100GB (Karmic apparently can read and write to NTFS, so both OS' can share this partition)

Will I be able to use the unallocated space to make any of the others bigger later if needed, or will the 'architecture' I(will ha)'ve created prevent that..?

Any thoughts on vulnerabilities of C: ?
Will Karmic be 'happy' in one extended partition?
Do I need /boot?, or just the other 3, or something else..?

Thanks

(Off to watch 'Collision' now :D )


Some random thoughts :

-  Ubunt does not care if it resided inside and extended partition as a logical.  Ubuntu will not care about having the boot flag neither.  That said, I think it's a good idea to create ubuntu root (/), ubuntu /home and swap as logicals inside an extended.  Of course, creating those partitions would require a MANUAL install (step 4 of the installer) where sizing, file formats and mounting are required.  Lastly, out of preference, I always put my swap at the end believing that if I need space, I can delete SWAP and just create a swap file.

root - 15GB
/home- as much as I can give
swap - 2GB

-  We all abide by the 4-rule.  4 PRIMARY or ... 3 PRIMARY + 1 EXTENDED.  My win7 created (default install) 2 primary partitions.  I am assuming that the smaller sized partition is the boot partition whereas the bigger sized is win7 system. Sorry I cannot check because I have already deleted win7 preferring to go back to XP. I also don't think there is no need for a /boot unless you have a older system/bios and are trying to avoid an error 18.  I would just let ubiquity install GRUB automatically.

-  Best use a live CD (or liveUSB ... or a standalone live gparted CD) to access gparted and partition. That'll automatically unmount the partitions for you.  For swap, use swapoff.  From Vista experiences, I preferred to use Vista disk management tool to resize a vista partition.  You might want to use win7's.  If you decide to use gparted, remember to uncheck the "round to cylinder" box (again, a Vista experience).

-  Before taking space from a windows install, remember to defrag.  2x is you have the time.  Even a new windows  install will/can be fragmented.

happy ubntu-ing.

---

### Post by oldfred on 2009-11-11
I do not think it matters what primary partition you put windows in, it will think it is c:, the second NTFS partition will be d: etc and it will not see the ext3 or ext4 partitions at all.

If you do a clean install of Win7 it also creates a small boot partition.

I read & write NTFS currently, but I had set up my shared partition 3 years ago and used FAT at that time. FAT has issues, like no files over 4GB and not as stable. I plan on converting my FAT32 partition to NTFS next week.

---

### Post by Bartender on 2009-11-11
Annigma -
We don't refer to partitions as C:/.  That's Windows terminology.

You do want to install 7 first, and this has nothing to do with security as you alluded in post #1.  Windows is Windows, and it's vulnerable no matter where you physically install it.

I try to keep primary partitions to a minimum.  I don't like getting anywhere near that 4 partition limitation in BIOS.

*If it were me*, I'd use a stand-alone partitioner such as GParted LiveCD (link below my sig) to create all the partitions beforehand.  Download the latest stable .iso, burn like you would an Ubuntu CD, then boot from the CD.

I'd wipe all partitions (since you're starting from scratch, you have the luxury of playing around a little and starting over again if you don't like the results) off the HDD.  Keep removing partitions until you have one huge unallocated space.

Then I'd create one primary NTFS partition at the "front" (left hand side) of the partition map for Win 7.  About 50GB should be enough since you're planning on a data partition.

Then I'd create an extended partition out of the rest of the drive.  Inside that extended partition, starting from the left-hand edge, I'd create a logical ext4 partition.  About 15 - 20 GB should be more than enough for the Ubuntu OS, identified as /.
  
I'd then create a logical swap partition.  Back in the day, with 256 MB of RAM, swap size was important because it determined how much virtual memory you were going to allow the OS to use.  These days, with 2GB of RAM being the lower end, swap is not used much for its traditional function.  However, it is important to make swap a little bit bigger than your physical RAM if you want to use suspend.  In other words, if you have 2GB of RAM, make swap 2.5 GB and move on.  Swap partition is formatted as "swap".

With whatever is left, I'd create one huge logical partition formatted as NTFS.  I'd rather format it in ext, but Windows doesn't play nice with Linux file systems.

Then I'd get out of the partitioning tool and install Win 7.  It *should* only see the primary NTFS partition and install to that.  I haven't seen this with my own eyes so don't know if anything's changed but that's how it used to work.

Then I'd fire up the Ubuntu install CD, choose manual partitioning, and click on that ext4 partition.  I'd tell Ubuntu to use the partition, format it, and mount it as /.

Ubuntu installer will recognize the swap partition, so you don't ahve to do anything with it.  After you've moved past the partitioning step, you might notice the summary will say that Ubuntu will format the swap partition.  Don't worry about that.  It always says that even if you don't tell it to format swap.

I left out making a separate /home partition, because this was already getting complicated and you're making a separate data partition.  If you don't want to screw around with making a separate /home partition but you think you'll use /home pretty regularly, you might want to bump out the ext / partition to 30 or 40 GB.

---

### Post by Annigma on 2009-11-11
[COLOR="Blue"]Wow, thank you. First nothing, now lots to think about. You're like buses :P
[/COLOR]
> **darkod said:**
> You don't need /boot specifically as partition. A folder boot will be created in / (root).
[COLOR="Blue"]I'd kinda decided this, but thanks for the confirmation :)[/COLOR]
You can use available free space to expand and sometimes also shrink, but that is a process that takes very long and it puts your data at risk.
[COLOR="Blue"]May as well allocate all the space now then.[/COLOR]
My suggestion: If you have all your data backed up both from windows and ubuntu, do a clean install of windows, then of ubuntu.
[COLOR="Blue"]Ok[/COLOR]
Why do you need the DOS C:? Something specific?
[COLOR="Blue"]Paranoia. Research has allayed my fears ;)[/COLOR]

PS. You say you will create partitions manually from wubi. Do not confuse wubi now, wubi is to run ubuntu as a software program from within windows. You will install Win7 first with its DVD and then boot with the Ubuntu CD and select the Install option and go from there. Wubi is not involved.

[COLOR="Blue"]Well, I was worried about this before (posted [here]("http://ubuntuforums.org/showthread.php?t=1320546")), but did a bit of reading and decided that Wubi would do both.. The setup looked like what I've seen.. Is that why it increased my Win7 partition - because it was going to install itself in there..? I'm pretty sure I downloaded the right iso..[/COLOR] :confused:

> **raymondhenson said:**
> Some random thoughts :

-  Ubunt does not care if it resided inside and extended partition as a logical.  Ubuntu will not care about having the boot flag neither.  That said, I think it's a good idea to create ubuntu root (/), ubuntu /home and swap as logicals inside an extended.  Of course, creating those partitions would require a MANUAL install (step 4 of the installer) where sizing, file formats and mounting are required.  Lastly, out of preference, I always put my swap at the end believing that if I need space, I can delete SWAP and just create a swap file.

root - 15GB
/home- as much as I can give
swap - 2GB

-  We all abide by the 4-rule.  4 PRIMARY or ... 3 PRIMARY + 1 EXTENDED.  My win7 created (default install) 2 primary partitions.  I am assuming that the smaller sized partition is the boot partition whereas the bigger sized is win7 system. 
[COLOR="Blue"]Yes, I think you're right. Although, I didn't think the 'little partition' (~100MB) was a 'partition' as such, since windows didn't assign it a letter.. I just assumed it had somehow 'tacked' it's system files onto the MBR or something.. (no I don't know what I'm talking about: a little reading is dangerous lol)[/COLOR]
-  Best use a live CD (or liveUSB ... or a standalone live gparted CD) to access gparted and partition. That'll automatically unmount the partitions for you.  For swap, use swapoff.  From Vista experiences, I preferred to use Vista disk management tool to resize a vista partition.  You might want to use win7's.  If you decide to use gparted, remember to uncheck the "round to cylinder" box (again, a Vista experience).
[COLOR="Blue"]Now you've lost me.. I thought Gparted was included with Ubuntu? Can I burn it onto the **DVD** I've burned Karmic/Wubi? onto..? (I'm guessing no..)[/COLOR]
-  Before taking space from a windows install, remember to defrag.  2x is you have the time.  Even a new windows  install will/can be fragmented.
[COLOR="Blue"]Looks like I'll be trashing it and starting over, so Gparted should sort that out, shouldn't it?[/COLOR]
happy ubntu-ing.
[COLOR="Blue"]Thank you [/COLOR] :D


> **oldfred said:**
> I do not think it matters what primary partition you put windows in, it will think it is c:, the second NTFS partition will be d: etc and it will not see the ext3 or ext4 partitions at all.

If you do a clean install of Win7 it also creates a small boot partition.
[COLOR="Blue"]Yes I noticed this. Around 100MB. If it had called it C: I may have been typing this from 'the Koala'[/COLOR] :icon_frown:


> **Bartender said:**
> Annigma -
We don't refer to partitions as C:/.  That's Windows terminology.
[COLOR="Blue"]I know. I called it C: because that's where my Windows is. Don't worry, I'm trying to move from the dark side :D[/COLOR]

You do want to install 7 first, and this has nothing to do with security as you alluded in post #1.  Windows is Windows, and it's vulnerable no matter where you physically install it.
[COLOR="Blue"]Otherwise it'll overwrite the bootup and mess up dual install?[/COLOR]
I try to keep primary partitions to a minimum.  I don't like getting anywhere near that 4 partition limitation in BIOS.

*If it were me*, I'd use a stand-alone partitioner such as GParted LiveCD (link below my sig) to create all the partitions beforehand.  Download the latest stable .iso, burn like you would an Ubuntu CD, then boot from the CD.
[COLOR="Blue"]Is DVD ok? (only DVD burner up and running atm). Can I put it on same disc as Ubuntu (though I have Wubi.. awaiting advice on that)?[/COLOR]
I'd wipe all partitions (since you're starting from scratch, you have the luxury of playing around a little and starting over again if you don't like the results) off the HDD.  Keep removing partitions until you have one huge unallocated space.

Then I'd create one primary NTFS partition at the "front" (left hand side) of the partition map for Win 7.  About 50GB should be enough since you're planning on a data partition.

Then I'd create an extended partition out of the rest of the drive.  Inside that extended partition, starting from the left-hand edge, I'd create a logical ext4 partition.  About 15 - 20 GB should be more than enough for the Ubuntu OS, identified as /.
  
...if you have 2GB of RAM, make swap 2.5 GB and move on.  Swap partition is formatted as "swap".

With whatever is left, I'd create one huge logical partition formatted as NTFS.  I'd rather format it in ext, but Windows doesn't play nice with Linux file systems.

[COLOR="Blue"]Sounds good. One Primary, One Extended (4 Logical (including /home). Seems less messy somehow.[/COLOR]


So questions I still have:
Have I got the wrong iso? 
Can I burn Gparted onto same DVD as Ubuntu?

Current Partition Plan:
Primary C: (sorry Bartender) NTFS Win7 60GB
Extended: Logical: 
hda2 /ext4 15GB
hda3 /home 40GB
hda4 /swap 2.5GB
D: NTFS Data partition ~120GB/whatever's left

How's that lookin'?

Thanks so much for your help

---

### Post by darkod on 2009-11-11
About the 100MB partition win7 creates. First of all, yes, it is primary partition even if win7 does not assign letter. It will be counted as one of the 4 available primary partitions (or 3 + 1 extended).

What I have noticed is I think win7 only creates it if you make the partitioning with it. For example you start with blank drive, and you use the installation process of win7 to create the partition for it (you need to click on Advanced Options on the screen where it asks you where to install windows). In that case there will be a message that it will create a small 100MB partition. It happened when I was installing 7 on my netbook.

But my desktop has a D: partition for data that I had nowhere to move, so when installing win7 there I just selected the first partition, where Vista was installed, as a target for win7. In this case no 100MB partition was created.

About whether you have the correct ISO. Why do you think you don't?

Just put the CD into your dvd drive, select in BIOS to boot from cd first and the ubuntu menu should come up. In fact, you can go and select the first option, Try Ubuntu With No Change and that should load Karmic and allow you to see how it works and whether all hardware is recognized.

For Gparted, it is part of the Ubuntu CD but I'm not sure you can do partitioning from there and whether it is good to do it that way. You could start Ubuntu in live environment (not installed, like I explained just now), and probably it should allow you to run Gparted and create/delete partitions because Ubuntu at that moment is actually working from the CD. If you actually create your partitions this way win7 most probably won't create the 100MB as explained before. You will not ask win7 install process to create you any partitions, just select the one where you want it installed (if your partitions are created in advance with Gparted).

Otherwise you can not just add Gparted live ISO to Ubuntu CD because they both have boot sector. You might want to have bootable Gparted on separate CD or you can just run Gparted from Ubuntu live CD under condition what I wrote just now works. Sorry, I'm new to Ubuntu also and can't guarantee it.

PS. About wubi. As far as I know you use it just to install ubuntu as application under windows. To see how it runs and play with it. You can do the same by booting in live CD (live environment). It will not partition your disk. All in wubi is ""virtual". I has it installed under windows too, and it creates Ubuntu entry in your windows bootloader (does not install grub at all), and an entry in your Add/Remove programs in windows. Then I just clicked on it in Add/Remove programs and removed it just as any windows application. Your partitions stay the same. You do not want wubi. Anyone can correct me if I am wrong.

---

### Post by raymondh on 2009-11-11
Gparted is the partition editor of Ubuntu.  If you boot into the liveCD (or liveDVD) and go live session (aka TRY UBUNTU WITHOUT ANY CHANGES) ..... you can access gparted from system > administration > partition editor.  The reason it is suggested to go LIVE is because a live session will unmount the partitions.  Gparted will not work on any partition that is mounted (you'll know when you see the key beside the partition label ... or you have a greyed out option to resize/create/etc.)

The suggestion to use a standalone live gparted CD is because it is a great tool to have in your bag.  You can download gparted and burn it to a CD.  That makes it a "standalone" and not part of Ubuntu.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You're partitioning looks great :)  Nice to have space 'eh ;)  Like previously suggested .... it's OK to install win7 first, update win 7, and then use it's disk management tool (administrative tools) to resize/shrink it down to your desired allocation (60GB).  From my previous Vista experience, windows has a habit of putting "immovable" files (like MFT's, etc.) all around the disc (or HD).  If you run into that, the usual result is you will not be allowed to resize past an immovable file.  Vista had a workaround but I do not know if it will work with win7.  Here's the link. 

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)


If you decide not to try to resize further, you'll just have to adjust your partitions accordingly.  Ubuntu is fine with 15GB.  Swap is ok at 2GB.  The rest is for /home and your DATA partition.  If you decide to incorporate /home with root (i.e. no more separate /home ... which I think is NOT a good idea), Ubuntu root will be ok with about 25GB (giving you the space for config files) as you will have a DATA partition anyways to store your personal data/media files.

Post back if you need assistance in manual partitioning and manual installation.

Have fun.  Have your coffee/favorite drink ready.  Be patient and happy ubuntu-ing.

---

### Post by darkod on 2009-11-11
Raymond just gave excellent reason to use Gparted from the live CD and create your partitions that way. In fact, for a start just create the first 60GB ntfs partition.

Then boot with win7 dvd and install it on that partition. That way it will not create the 100MB primary partition and it will be limited to those 60GB you gave it. If you give it larger partition that you already plan to shrink, and it places unmovable files there, you are just creating way too much work than needed.

You will create the rest of the partitions during the Ubuntu installation process with selecting manual partitioning.

---

### Post by Bartender on 2009-11-11
So questions I still have:
Have I got the wrong iso?
Can I burn Gparted onto same DVD as Ubuntu?

Current Partition Plan:
Primary C: (sorry Bartender) NTFS Win7 60GB
Extended: Logical:
hda2 /ext4 15GB
hda3 /home 40GB
hda4 /swap 2.5GB
D: NTFS Data partition ~120GB/whatever's left


I don't know if you have the wrong .iso.  I would forget about wubi.  Do a real true dual-boot.  wubi runs inside Windows.  It's for newbs who aren't ready to partition.  Unless you want 64 bit, you're looking for the standard Ubuntu download.  I attached a screenshot that might help.

No, use separate discs for Ubuntu LiveCD (or Ubuntu alt-install CD) and GParted LiveCD.  You could do all the partitioning from an Ubuntu LiveCD but once I tried out a stand-alone GParted LiveCD I was hooked.  Even though you're using a DVD burner you can use CD-R's and probably should.

Looking at your partition plan, I want to point out something about the numbering scheme.  As soon as you create an extended partition, Linux will skip to sda5.  Even if you only create one primary, which will be identified as sda1, the extended will still be sda5.  sda2 thru 4 will not be assigned.  So your partitioning would go sda5 for the extended partition, sda6 for the first ext4 partition (which you would mount as /), sda7 for the /home partition, sda8 for swap, and sda9 for the NTFS data partition.

Here's a thread with some pictures that might help you get an idea of a few different partitioning schemes.
[http://ubuntuforums.org/showthread.php?t=1249374](http://ubuntuforums.org/showthread.php?t=1249374)

---

### Post by Annigma on 2009-11-11
Ok, I really need to find out if I've got the right iso burned onto DVD.
I followed the instructions on [this page]("http://www.psychocats.net/ubuntu/iso"), and downloaded ubuntu-9.10-desktop-amd64.iso.torrent from the file list towards the bottom of [this page]("http://releases.ubuntu.com/karmic/"). I did the hash compare thing and that was fine.
(I've just put together an M4A78T-E and a Phenom II x3 720 so thought I'd go for the 64-bit option.)

The instructions I followed said the download should look like this:

[IMG]http://www.psychocats.net/ubuntu/images/iso18.png[/IMG] 

but mine has the Wubi logo instead of the Ubuntu logo, and it doesn't 'say' Ubuntu 9.10 64 or whatever, it just says 'Install Ubuntu' (I'm sure it said 'Wubi' last time I loaded it..)..
(It also reports '4.37GB free of 4.37GB', but if I open it, all the programs are there and it runs, works, etc.. so I put that down to Windoze being dozey :D )

I have run it in live mode, and all was well. Well, I say 'all' - I just had a little browse on FF.

It does seem like I have the wrong one doesn't it? And that would explain why it increased the size of my Win7 partition by ~30GB wouldn't it..? It's like I clicked the right download, but it gave me something else.. :confused:

I'll work through the other helpful posts, once I'm happy I've got the right iso on the disc in my grubby mit. Not sure about Gparted yet. Seems I can use Ubuntu's one, but since it would appear that Gparted may do a better job, I might download that (onto a different DVD) too..

EDIT: I've just checked the Ubuntu download page (like your thumbnail Bartender) and changed download option to 64-bit and clicked as if to download (but didn't) and the file name is the same as the one I downloaded, which ended up as 'Wubi'? (apart from the .torrent bit obviously)... has BitTorrent got it mixed up? :confused: May as well start downloading it whilst I wait.. I'll give BT a miss this time..

---

### Post by Bartender on 2009-11-11
Oops, sorry, didn't know you were installing to AMD 64-bit.  
I don't understand the "Wubi" part that you keep mentioning.  I have never done a wubi install, and I've never seen a reference to wubi come up like you describe.
It does kinda sound like you have the wrong download, but if a link is sending you the wrong download there would be others saying the same thing.  I would think so, anyway.  Maybe try downloading from a different mirror?  Yeah, if you can use bitorrent, try that too.
I thought wubi wasn't a separate download, but an available option from the Ubuntu LiveCD?  I'm probably wrong...

OK, even though I'm on dial-up I did a little checking.
Here's the wubi download site
[http://www.ubuntu.com/getubuntu/download-wubi](http://www.ubuntu.com/getubuntu/download-wubi)

Here's the standard Ubuntu LiveCD website
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I got to the wubi site by clicking the "Alternate install options..." link just underneath the bright green "Download Ubuntu" box.  See where it says "Ubuntu Installer for Windows"?  That's wubi.

I really don't know what's going on with your situation.  From what I can see, wubi is wubi.  There is no amd-64 version.  If that's correct, and you got the amd-64 bit download, then it's not wubi and I don't know why you're getting wubi references unless it's because you already installed it on your PC.

---

### Post by Annigma on 2009-11-11
> **Bartender said:**
> Oops, sorry, didn't know you were installing to AMD 64-bit.  


That's okay. I didn't say :)

Just downloaded the 'proper' one (from ubuntu, which you linked to) and... it's the same as the one I've already burned.. 

Hmm...

---

### Post by raymondh on 2009-11-11
If I remember right,  the WUBI logo appears if you load (or insert) the CD/DVD while windows is running ..... as that segues into a wubi installation.

If the above is true, reboot into the livecd/Dvd by altering the BIOS to boot into the CD/DVD drive first before the internal HD.

---

### Post by Annigma on 2009-11-12
Did that before. It'll boot ok, I'll get install instructions, and it won't be till partitioning stage (or thereabouts) that I discover something's wrong..

How about this. Does anyone know of a definite, obvious difference between the two: i.e. Wubi and Karmic 'proper' install?
Gonna look through some walkthroughs for both and see if the bootup screens are different or something..

I appreciate your help and patience :)

I'm watching this and there would appear to be no 'side by side' option for Karmic.. When I got to that bit, I chose 'side by side', then entered username, password, etc.. I didn't click advanced to install the boot loader, then I cancelled it somewhere around there as I felt something wasn't right..

Perhaps the iso I've got does it all..? i.e. run live CD (no changes), install Ubuntu inside Windows, OR do a 'proper' dual boot install..? That's the only thing that makes sense.. 

If I don't hear back, I'm going to run it again, try partitioning with it (though I'm confused as heck about what Bartender was saying about it skipping hda2-5 (sda2-5?).. guess that's not too important, though I know it'll annoy me) and see what happens..

---

### Post by MrSnowmiss on 2009-11-12
> **Annigma said:**
> If I don't hear back, I'm going to run it again, try partitioning with it (though I'm confused as heck about what Bartender was saying about it skipping hda2-5 (sda2-5?).. guess that's not too important, though I know it'll annoy me) and see what happens..

Just to expain (and it's not too important ;))
When you would create 4 primary partitions they would be called hda1-4 (or sda1-4 if it's sata devices).
Now when you instal 1 primary it would be hda1 and the next, which would be a logical partition, could be named hda2 but isn't. Inside that logical partition the name of the first partition will be hda5 and so on)

---

### Post by Annigma on 2009-11-12
> **MrSnowmiss said:**
> Just to expain (and it's not too important ;))
When you would create 4 primary partitions they would be called hda1-4 (or sda1-4 if it's sata devices).
Now when you instal 1 primary it would be hda1 and the next, which would be a logical partition, could be named hda2 but isn't. Inside that logical partition the name of the first partition will be hda5 and so on)

Ahh, I see. So it kinda reserves sda1-4 for the Primaries 8-)
Thanks for that, and also for the h/sda thing. I fired up this machine after putting it together, then kept getting S.M.A.R.T. complaints about the HDD (that's probably what was wrong with my machine before lol! - although it never reported it like that.. :confused: It was time for an upgrade anyway: built the last one about 5 years ago :shock:), so I went and got a SATA one. So I'll forget about hda. sda is the way to go :D

---

### Post by Annigma on 2009-11-12
If I run my disc 'live' I can choose Gparted from System-->Admin.
Since wubi is designed to run inside windows and to avoid the hassle of partitioning, surely this is an indication that I have got a 'proper' Ubuntu installation iso....? (i.e. one that will allow me to install Karmic on a separate partition and dual boot)

Box of popcorn to speedy responses.. :D

---

### Post by audiomick on 2009-11-12
My Advice:
hold your nose and jump :-)

I think we have certain character similarities: I always want to know everything before I start.

If I've understood you correctly, you're doing everything from scratch.
The advice to make a partition for windows, fill it, then go ahead with the Ubuntu bit seems good to me.
The Ubuntu installer will always see the windows install, and offer the choice of installing beside it, or freeing the world of its' existence

From your descriptions, I reckon you've got the "right" Ubuntu cd

So, go ahead and run it. If, at the end, you realize something is strange, do it again.
I know that costs a lot of time, but for me, that was an extremely valuable experience: to whit, I got a new box a year or so ago, and for various reasons, none of which had to do with the operating system or the installer, ended up installing about 6 times. Result: a much more relaxed Michael ;)

A bit more info:
Ive just done a 9.10 install for someone
the root partition, i.e. / , which I allocated 8GB, has got about 2.4 GB in it.
The reason for re-installing was that / was full ( had 5 GB, and had been on the box about 3 years. )
My Ubuntu Studio, after a couple of Updates ( 8.10 .9.04, 9.10 ) and random addition of programs for the last 18 months, has nearly 6 GB in /

In the process of re-installing the aforementioned computer, I used gparted from the Ubuntu live cd to resize an existing /home partition. All the stuff is still in it, but, in the subsequent fresh install, for which I used the pre-existing /home, there is some weird stuff happening with nautilus.
( thread here [http://ubuntuforums.org/showthread.php?t=1322931](http://ubuntuforums.org/showthread.php?t=1322931) )

Anyway, hope this helps.
go for it!
Michael

---

### Post by Annigma on 2009-11-12
> **audiomick said:**
> My Advice:
hold your nose and jump :-)
[COLOR="Blue"]Take the bull by the horns. Yep, I feel you're right :D[/COLOR]

I think we have certain character similarities: I always want to know everything before I start.
[COLOR="Blue"]Lol, yeah it's a pain isn't it.. Stop dithering and just get on with it (me I mean) :lolflag:[/COLOR]

If I've understood you correctly, you're doing everything from scratch.
[COLOR="Blue"]Kind of. I installed Win7, but due to aforementioned problems, I'm gonna start over, so.. yep [/COLOR]

The advice to make a partition for windows, fill it, then go ahead with the Ubuntu bit seems good to me.
The Ubuntu installer will always see the windows install, and offer the choice of installing beside it, or freeing the world of its' existence
[COLOR="Blue"]Well I'm going to do all the partitions first with Gparted, then install Win7, then Karmic.. I assume that's just a slightly different way (i.e. order) to go about the same thing. Also, it will save me a step when installing Ubuntu.. that's the idea anyway.. :idea:[/COLOR]

From your descriptions, I reckon you've got the "right" Ubuntu cd

So, go ahead and run it. If, at the end, you realize something is strange, do it again.
I know that costs a lot of time, but for me, that was an extremely valuable experience...
[COLOR="Blue"]Yeah, not the end of the world is it.. I'll give it a go.[/COLOR]

Anyway, hope this helps.
go for it!
Michael
[COLOR="Blue"]It does. Thank you :)[/COLOR]


<holds her nose and jumps>

---

### Post by audiomick on 2009-11-12
Hallo again
One more thing:
You are palnning to have a data partition aren't you? and someone advised you to make it nfts ( or whatever... the windows one :)) because Windows doesn't like Linux file systems.

As far as I now, the Linux file systems are a bit safer/ more stable/ better
There are tools like this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
which allows you to look at an Ext2 filesystem in windows.
I used this on my old Laptop for 2 years or so, till the machine died of old age. Haven't got a dual boot at the moment, so I don't know what the state of the art is.

Appropos 64 bit:
I use the 64 bit version, and am very happy with it. There are however still occasional minor irritations, e.g. some Firefox plugins that don't work and suchlike. I just ignore things like that, same as websites that don't run because they have too much flash crap on them.
Michael

---

### Post by Annigma on 2009-11-12
Thanks Michael, but I think I'll stick to NTFS as I'm pretty sure both OS' will be able to access/read/write to/from it.. (hopefully)

I just set up my partitions carefully, then Gparted 'got stuck' when it came to create my Win7 partition.. 

I don't need to create a New Partition Table do I.., or format, or.. uhm.. :confused:

---

### Post by darkod on 2009-11-12
You will need to format the newly created partitions with the corresponding file system. For the win7 partition, ntfs of course. For ubuntu, ext4. For the data partition, ntfs.

---

### Post by Annigma on 2009-11-12
So click partition and select format:
Win7 and storage --> NTFS
/ and /home --> ext4
/swap --> linux-swap

Yes..?

..and unticking/unchecking 'Round to cylinders' on all?

---

### Post by audiomick on 2009-11-12
Sounds right. I let mine round off when I was messing around with it. Makes sense to me. The machine can only deal with blocks of a particular size. No point trying to force it to accept a size that it cant deal with. If you let it round off, I think that just means that it goes to the division it can deal with closest to the size you want
Michael

---

### Post by Bartender on 2009-11-12
Annigma -
Did you decide to start over?  The last couple of posts sound like it.  Are you using the stand-alone GParted LiveCD or the gparted partitioner inside an Ubuntu LiveCD?

I prefer the stand-alone partitioner, but as long as you make sure to right-click on the swap partition (if you have one) and click "swapoff"  you should be able to wipe all partitions.  Get it back to one big unallocated section.

Oh, I forgot - only do one task at a time.  Any time you create or destroy or resize, apply the change and let GParted finish that task before starting another one.

Then create the primary NTFS partition, shoved up against the left side of the partition map.  You said you were having problems making the Win 7 partition.  With all partitions wiped off the drive you *shouldn't* have any problem doing this.

Technically, it's not a Win 7 partition at this point.  It's just a primary partition, with NTFS laid in as the file system.  I always think of the file system as the foundation for the house.  Once you've got the foundation put in, you don't really have to think about it too much, but it is important to have a good foundation!

If you can't create a primary NTFS partition, something is definitely not right.  Probably the CD.

---

### Post by Annigma on 2009-11-12
Hi guys

Not sure I've done what you said Bt but I've just installed Win7 so hopefully I don't need to back again.. :eek:
Here's what I did:

Ran Gparted (from my 'wubibuntu' disc - lazy). Deleted all partitions. Made Primary NTFS, Extended, then 4 logicals: /, /home, /swap, data (NTFS). Chose ext4 for 2 of the ubuntu partitions and 'linux-swap' for the /swap partition. Didn't see a 'swapoff' option.. Gave all labels (even extended lol), didn't specifically format, as came to conclusion that choosing file system does that.. Did choose 'format' when installing Win7 (knew it would be quick), and so far so good... (she says hopefully)

Just installed Windoze on the primary, and was just about to run my 'wubibuntu' disc again to install Karmic.. (I'm wondering where Ubuntu will put it's 'grub bit'.. but fairly confident that it'll do a good job, or I'll be able to fix it, as long as I've done nothing wrong so far..)

I'll have a little break from it now whilst I try and find a nice guide I found earlier on dual booting, and await any responses saying OH NO WHAT HAVE YOU DONE.. :lolflag: :P

---

### Post by audiomick on 2009-11-12
Hi. 
Sounds good to me. Interested to hear what Darkod has to say. I've bumped into him on another thread today, and he seems to have a really good grasp of things.

Pushing the "GO" button is a good feeling, isn't it?

Do let us know how things turn out in the end, wont you. I wont be able to sleep if I don't know how the story ends...;)

Michael

---

### Post by Annigma on 2009-11-12
Hehe thanks Michael :D

I'm just at the Advanced Options for the boot loader.. it's on (hd0), but I believe I need to change it to sda5 (where / is).. hopefully this is right... looking at [herman's link]("http://members.iinet.net.au/~herman546/p23.html") I think it is.. 
.. uhm.. no actually.. I should leave it on (hd0).. crikey. Decisions decisions!

To quote herman:
> 
If you're dual booting, you should just go along with the default here, and install GRUB to MBR in their first hard disk.  
That will also install GRUB's stage1_5 in the first track of the first hard disk.
GRUB's stage2 files and menu.lst are always installed in Ubuntu's /boot/grub/
That's the recommended option for dual booters.


I want it at the start of my HDD, before/in front of Windows.. not at the start of Ubuntu.. after windows..

Hmm.. ready to click ok for (hda0).. waiting patiently for the go ahead.. :P

---

### Post by audiomick on 2009-11-12
Hi.
getting almost out of my depth.
I have always, for want of sound knowledge, let the installer continue with its' default settings in this regard. This would also seem to be Herman's advice.
I also have feeling that where such things need to go has more to do with arcane reasons only known to a select circle of hardware engineers in the early seventies than any sensible kind of tidy orderliness that might occur to normal people;)

In short, let the thing do what it wants to do.

---

### Post by Annigma on 2009-11-12
Well, things are looking good so far..
Got the option of which OS I wanted to use. Chose Karmic

Just done a package update and it wants to know what I want to do with GRUB.. lots of options in a drop down, and something about the current version has been locally modified.. A new version of  configuration file /etc/default/grub is available apparently..

..what to do... :confused:

---

### Post by audiomick on 2009-11-12
Rings a bell. Is there a thing called merge? I think I was choosing that a while back, although I don't remember exactly why, I'd have to see it happening. As I recall, it is supposed to combine the differences.

---

### Post by Bartender on 2009-11-12
Yeah, all things being equal, if you just skip right past that "Advanced" button on the final page of the installer, GRUB Stage 1 will be installed to the Windows MBR.
For your typical "one hard drive/Windows-Linux dual boot" this is probably the best way to go.
I'm not familiar with this GRUB choice that you refer to, but it must have something to do with the new GRUB 2.

Is there an option that appears to leave GRUB where it is, but update to the latest version?

---

### Post by Annigma on 2009-11-12
Thanks guys.

There are 7 options, like so:

Install the package maintainer's version
keep the local version currently installed
show the differences between the versions
show a side-by-side difference between the versions
show a 3-way difference between the available versions
do a 3-way merge between available versions (experimental)
start a new shell to examine the situation

Presumably whatever I do, I can change later..?

---

### Post by Annigma on 2009-11-12
<drums her fingers on the desk>

Well, I'll finish off that popcorn no-one 'earned' earlier, and I'll use my 'beans' to make a cuppa coffee... :P

---

### Post by Annigma on 2009-11-12
I'm leaning towards the 'experimental' merge...

---

### Post by MrSnowmiss on 2009-11-12
I remember dubbing between those (when I was upgrading my 9.04):

Install the package maintainer's version
keep the local version currently installed

Since you're doing a fresh install I guess you could go for the first.

---

### Post by Bartender on 2009-11-12
Keep the local version seems safest to me but I haven't delved into GRUB 2 in any way.
Install package manager's version would, I assume, attempt to erase any vestiges of GRUB and install GRUB 2.
Since there are no worries about losing personal data, maybe installing package manager's version would be best...get it over with and move on with GRUB 2.

I'm just guessing at this point!

---

### Post by audiomick on 2009-11-12
Hallo.
Been out for the evening:P
I think the other two are right; for a fresh install, the packet managers version is probably ok.
you could try having a look with the various "show" options. Maybe you'll learn something. I've done that, and it shows you a list of stuff, then brings you back to the point of choosing, i.e. not dangerous.
I have also definitely used the 3 way merge. There was a reason for this, had something to do with the multiple installs that were on the machine at the time, but I'm afraid I don't remember details. That was at least 6 months ago...;) Anyway, the merge wont kill you. Apart from that, as I've already mentioned; it's a new install, so you wont lose anything but time.
Trust Ubuntu that the options all have a reason for being, and suck it and see.
Michael

---

### Post by Herman on 2009-11-12
> Install the package maintainer's version
keep the local version currently installed
show the differences between the versions
show a side-by-side difference between the versions
show a 3-way difference between the available versions
do a 3-way merge between available versions (experimental)
start a new shell to examine the situation:D **I always choose to 'Install the package maintainer's version', unless I have a special reason not to.**
The package maintainer's version will be the more advanced version of a file, usually some kind of a configuration file, such as /boot/grub/grub.cfg in this instance. 
A configuration file is a file for storing a list of commands along with your favorite settings which belong with whatever program the configuration file belongs to.
The same question could be referring to configuration file for some other program in other circumstances.

Your update has just given you the most advanced software. Developers have been hard at work programming and scripting to bring us some new features that weren't available before.  That means there's probably some new commands which have been freshly enabled that weren't included in your older configuration file, (the  'local version currently installed' copy).

If you don't update to the 'package maintainer's version' of the file, you can still use the program, but you probably won't be making use of the latest improvements to the program.
On the other hand, a few people might have a special customized configuration file which they might want preserved, so the default suggestion is to keep that one, just to be on the safe side. It's mainly only a few advanced users who may be doing something special who would want this option.

Unless you have a special reason, (and you would know about it if you did), it's generally best to select the top option, 'Install the Package Maintainer's Version'.

Regards, Herman :)

---

### Post by Herman on 2009-11-12
Your settings will be preserved, (at least mine always have been), but there might be new settings added that you can then go and play with if you're interested, or maybe they'll be enabled automatically.

---

### Post by Bartender on 2009-11-12
Herman!!

Annigma, herman knows way more about this stuff than most of us.

---

### Post by Herman on 2009-11-12
:D Hi there Bartender, long time no see! I remember you helped me with my website way back in the Breezy Badger days and we were working on how to help Windows users with MD5 summing their Ubuntu .iso dowloads. [Checking the integrity of your .iso in Windows]("http://members.iinet.net.au/%7Eherman546/p17.html#Checking_the_integrity_of_your_.iso_in_Windows"), you'll still see your name there, and thanks again for your help! 

annigma,
Just re-reading a few of the latest posts, I see it's your /etc/default/grub you're getting an updated version of, That file is one of the files that helps make your new grub.cfg when your operating system makes one, so the end result is the same. I made a mistake in the details, (sorry), but essentially my earlier post is not incorrect. :D

---

### Post by Annigma on 2009-11-13
Thanks again for your help guys, and thanks for coming in Herman :D

I basically cancelled out of the package updater at that point, as I wasn't sure which one to go for. I fired up Windoze as I wanted to see how GW worked with my onboard graphics. Chuffed to bits with that, and flicking between game and FF was so quick it kept making me smile hehe. I guess that's the tri-core doing it's thing.. or could be because of more RAM or simply a quicker processor than I had.. dunno, but it's very nice :cool:

I'm back in Karmic now, to finish the update.. but it doesn't want to know. Says I'm up-to-date.. Hmmm... bootup seemed the same, so I guess it's kept whatever I had (then why didn't it offer me an update and the chance to choose again?). If I can somehow choose the 'install package maintainer's version' I will. Otherwise I guess it's not important..

Next big challenge will be getting GW working on Wine (assume you still need Wine..?), but plenty of other stuff to fiddle about with for the time being: plugging in my old HDD and seeing if anything is retrievable, getting files from external HD, getting security progs. back on windoze (only got Avast so far), exploring Karmic, etc.. etc...

Thanks again for all your help. It's made the whole thing enjoyable, rather than tedious and frustrating.

:popcorn:

:D

---

### Post by audiomick on 2009-11-13
Hallo
Glad to see it all worked out!
Michael

---

### Post by Annigma on 2009-11-13
Thanks Michael :)

I've just set up firefox so that it's sync'd between Karmic and Win7, having replaced the profile with mine. Nice :cool:

I'm currently researching how to make best use of my shared data partition and the /home partition (occurs to me I might not really need both, but I'll try and find a way to make use of both ;) ). I kinda dragged and dropped stuff over before, but I'm seeing if I can point to it from both OS', and be more organised. Will look into better backing up too, since I find it rather a drag, and it needn't be.

:)

---

### Post by audiomick on 2009-11-13
Hi.
The stuff you need in both systems is likely to be mostly Open Office files, at a guess, isn't it? If you tell OO, and whatever other programs generate files you want to access from both worlds, to save to a folder on the Data partition instead of the default, the whole thing will be almost automatic.
In OO extras - options, in the Open Office.org section under "paths"

You do really need both partitions because Ubuntu needs /home to work, and it has to be a Linux filesystem of one sort or another, which Windows refuses to be able to read. Your linux will, of course, be able to get into the Windows partition. My problem, however, was always that I only remebered that I wanted file "X" in Windows after I had already booted windows, and of course had not thought to put it where I could get to it whilst using it in Linux...

If you find anything the does your backups for you overnight whilst the computer is turned off, never loses anything, feeds the cat and has the coffee ready in the morning, let us know...

---

### Post by oldfred on 2009-11-13
If you boot both windows and Ubuntu often you can have the same firefox and thunderbird data in the common partition.
I created a FAT32 partition (before NTFS linux driver wrote reliably) 2-3 years ago and moved both firefox and thunderbird to the shared partition. I then edited the profiles in windows and linux to look the the common partition rather than the local one. It still worked even when I converted from Thunderbird version 2 to 3 on both windows & ubuntu. 
More info:

[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by Herman on 2009-11-13
+1 for oldfred, I didn't know that before! Cool! :D

One other reason for wanting an extra partition to allow for files to be shared between Linux and Windows is to allow for a staging area where files can be deposited temporarily while on their way into Windows so they can be scanned for viruses first.
Ubuntu doesn't seem to collect viruses from the internet in the first place, and it's much safer to keep Windows off the internet and use Ubuntu to get files to put in Windows if that's needed for any reason. Windows seems to remain perfectly clean that way. However, it is still possible for a bad file to be passed through Linux since viruses remain dormant in Linux and can be stored without harm and inadvertently passed on, possibly. There are antivirus programs for Linux to prevent that from happening, clamav I think and AVG for Linux, ... but I digress, that's another subject. 
A shared data partition allows files to be scanned by your antivirus program you should have installed in Windows.

There's a fear in some workplaces that introducing Linux with Windows PCs might cause some information to become unavailable to Windows users because they lack the ability to be able to open files made by Linux machines, while Linux can open any files. I'm referring to OpenOffice.org files in particular.
In fact, it's quite simple to 'save as' the file in Open Office .org in Ubuntu and select from a whole range of Windows compatible file extensions. It's surprising how many people don't think of that. 
It's also easy to install Open Office.org in Windows.

---

### Post by Herman on 2009-11-13
It's also easy to install Ubuntu in all machines (LOL!) :D

---

### Post by audiomick on 2009-11-13
Nice windmill, Herman. Makes me homesick...

---

### Post by Herman on 2009-11-13
> Nice windmill, Herman. Makes me homesick...     Are you an Aussie? Or from the Netherlands?

:D Off topic, but it's a 35 foot Comet brand windmill.
In Australia it's customary to specify the size of a windmill by the diameter of the wheel, and not by the height of the tower, which is not considered so important. Windmills like this one are an 'icon' of the Australian 'Outback'.
The 35 foot Comet was the largest windmill manufactured in Australia of its type to be durable. There was an unsuccessful attempt made by a rival firm to make a larger one but their prototype was blown over and wrecked in the first storm. This 35 foot Comet windmill is around 100 years old. It was used  at Wirrilla station near Winton for pumping water up from underground for livestock to drink. It has recently been moved to our town and now stands on the banks of the Flinders River as a tourist curio.  I can see it from my back doorstep. Link, [Wirrila Windmill]("http://picasaweb.google.com/herman543/WirrillaWindmill#slideshow/5272484951028195426").
Windmills and their mechanical details can be extremely interesting to those who take the time to look at them closely.

---

### Post by audiomick on 2009-11-13
Never heard of Comet. I thought they were all made by Southern Cross.
I grew up at Cobram, on the Murray. Came to Germany in '96.
Let's not hijack the thread, though.

---

### Post by Annigma on 2009-11-16
> **audiomick said:**
> Hi.
The stuff you need in both systems is likely to be mostly Open Office files, at a guess, isn't it? If you tell OO, and whatever other programs generate files you want to access from both worlds, to save to a folder on the Data partition instead of the default, the whole thing will be almost automatic.
In OO extras - options, in the Open Office.org section under "paths"

[COLOR="Blue"]Documents, pictures and music. My Word is '97, and I've been using OO for a bit, so just downloaded that. Just wondering whether I need to install it on Ubuntu and Windows, or whether I can install it on the data partition and use it from there.. Either way, I'll be saving docs. to the folders I've made on the data partition. Spent some time earlier creating folders, renaming folders on external without s p a c e s and moving stuff over[/COLOR]

You do really need both partitions because Ubuntu needs /home to work, and it has to be a Linux filesystem of one sort or another, which Windows refuses to be able to read. Your linux will, of course, be able to get into the Windows partition. My problem, however, was always that I only remebered that I wanted file "X" in Windows after I had already booted windows, and of course had not thought to put it where I could get to it whilst using it in Linux...

[COLOR="Blue"]That's reassuring :)
Yes, I usually remember the stable door after the horse has bolted :D[/COLOR]

If you find anything the does your backups for you overnight whilst the computer is turned off, never loses anything, feeds the cat and has the coffee ready in the morning, let us know...

[COLOR="Blue"]Ok, will do :lolflag:[/COLOR]


> **oldfred said:**
> If you boot both windows and Ubuntu often you can have the same firefox and thunderbird data in the common partition.
I created a FAT32 partition (before NTFS linux driver wrote reliably) 2-3 years ago and moved both firefox and thunderbird to the shared partition. I then edited the profiles in windows and linux to look the the common partition rather than the local one. It still worked even when I converted from Thunderbird version 2 to 3 on both windows & ubuntu. 
More info:

[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

[COLOR="Blue"]That's handy. I've synced FF between both OS' by following [this tutorial]("http://cybernetnews.com/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+CyberNet+%28CyberNet+News%29"), so happy with that for now. Might try your way if I don't like the way it works. So far so good though. Haven't bothered to get Thunderbird back yet, but will bear it in mind :)
[/COLOR]

> **Herman said:**
> +1 for oldfred, I didn't know that before! Cool! :D

One other reason for wanting an extra partition to allow for files to be shared between Linux and Windows is to allow for a staging area where files can be deposited temporarily while on their way into Windows so they can be scanned for viruses first.
Ubuntu doesn't seem to collect viruses from the internet in the first place, and it's much safer to keep Windows off the internet and use Ubuntu to get files to put in Windows if that's needed for any reason. Windows seems to remain perfectly clean that way. However, it is still possible for a bad file to be passed through Linux since viruses remain dormant in Linux and can be stored without harm and inadvertently passed on, possibly. There are antivirus programs for Linux to prevent that from happening, clamav I think and AVG for Linux, ... but I digress, that's another subject. 
A shared data partition allows files to be scanned by your antivirus program you should have installed in Windows.

[COLOR="Blue"]More confirmation that having /home and a separate data partition is a good idea :cool: 
I'm using Ubuntu for surfing, and I intend to stay on it as much as possible. There are at least a couple of programs that I need Windows for though (GW, old Paint Shop Pro - easier for me than the Gimp, though I'll keep trying to pick that up), which is a good thing: otherwise I would've wasted my money on Win7!
I've got Avast on my Win installation and always scan stuff before opening, but I'll take care to bear in mind what you said about dormant malware.[/COLOR]


> **audiomick said:**
> 
Let's not hijack the thread, though.
[COLOR="Blue"]I don't mind :)[/COLOR]


---

### Post by audiomick on 2009-11-16
Hallo.
You seem to be coming along really well. Good to see! 
If I understood you right, you were wondering if you could install open office once and use it from both OSes? No you can't. Do install it on both systems. My experience was that I only managed to really make the change to Linux through a concious decision to do everything possible in Linux, i.e. stop hedging my bets and trying to keep windows options open. That included, for me, always working in Open Office no matter what, even when I was using Windowa. It has got to the point now, after about 3 years, that if I have to use MS Office for some reason, maybe on someone elses' computer, if "feels" really clumsy and alien.

Keep at it with the Gimp. I am still trying to get my head around it, but it is indeed a really good thing. If you read German, I can recommend a really good book...:)

---

### Post by Annigma on 2009-11-17
Hiya :)

Yes, you understood what I was asking. I installed OO on Win7 then spent a while trying to add it in Karmic from the package manager. Nearly installed one, but wasn't certain it was the right one.. It then occurred to me that I may already have it.. sure enough..  :oops:  :lolflag:

Thought I was happy with what I'd done with FF, but Ubuntu wouldn't let me use it.. kept 'saying' it was open when it wasn't. Eventually occurred to me that it may not like what I'd done, so created a new profile and pointed it to my old FF profile on the data partition. I think this is the same as what oldfred spoke of above.. Seems to be working.. will try the same thing in Windows next time I'm on there (quite like it here atm :D ) 

Been playing with the Gimp (see avatar :) ). It's better/easier than I remember, so I'll play with it more. Avatar looked okay till I shrank it down. Now the koala's practically disappeared, and it all looks a bit too 'squished' and busy. Preferred my Heron one, so I'll see if I can imrove it. I don't read German I'm afraid Michael :( so will make do with the online help.

I suppose I should stop posting on this thread now, since I'm quite happy with my partitioning... it's been lovely having my own thread to ask and get help on. Thanks again to everyone who has helped me :)

---

### Post by audiomick on 2009-11-17
Hi. It was fun helping. Put a solved tag on the thread, wont you.
Look after yourself:)

---

### Post by Herman on 2009-11-18
> Been playing with the Gimp (see avatar :smile: ). It's better/easier than I remember, so I'll play with it more. Avatar looked okay till I shrank it down. Now the koala's practically disappeared, and it all looks a bit too 'squished' and busy. Preferred my Heron one, so I'll see if I can imrove it. I don't read German I'm afraid Michael :sad: so will make do with the online help.I think you're being way too modest when you claim you don't know much yet about GIMP if you can make a nice avatar like that with it! :D

I can recommend a different book on the GIMP, it's called 'Grokking the GIMP', by Carey Bunks, and you can download your own digital copy of it for free from: [http://gimp-savvy.com/BOOK/index.html](http://gimp-savvy.com/BOOK/index.html)

When you have downloaded it, you can extract it by right-clicking on it and choosing 'extract here'.
It will produce a folder ('directory'), called 'Grokking-the-GIMP-v1.0', and in it somewhere you'll find a file called 'index.html', drag and drop that into an open Firefox window, or right-click on it and click 'open with Firefox Web Browser, (or whatever web browser you like). Once you have it open, add it to your bookmarks menu so you'll be able to bring it up instantly with Firefox from now on instead of having to navigate to it.
'Grokking the GIMP is really great, I wish it was around when I started learning the basics of using GIMP, it would have saved me a lot of time. I'm still slowly learning more too, and 'Grokking the GIMP' is still my favorite reference manual, it's full of tricks and tips I haven't tried yet, there's always more to learn. The GIMP is great fun!  :D

---

### Post by Annigma on 2009-11-19
> **Herman said:**
> I think you're being way too modest when you claim you don't know much yet about GIMP if you can make a nice avatar like that with it! :D


Well I don't know whether you're referring to the one I have now, or my first 'effort', which is the one I was talking about. This one:

[IMG]http://www.pix8.net/pro/pic.php?u=192330YvJo&i=1147390[/IMG]

The first took me much longer to make, as it's more detailed. This doesn't work of course, when the image size is reduced. The new one is much simpler, but I quite like it :)

I've played with PSP a fair bit, and I know the latest version of The Gimp will be more sophistocated than my old PSP 7, so it's just a matter of finding the function I'm after, if you see what I mean :)

I've got 'Grokking the Gimp' bookmarked. It looks very useful. Thank you :D 
I'm a bit confused about the download part.. I followed your instructions and ended up with a folder in my downloads folder, containing lots of things.. did what you said, and seemed to end up with exactly what I'd started with.. the web page you linked to..  I started by downloading the 'tarball' of the book. Anyway, I'll definitely be referring to that next time I do something with Gimp.

:)

---

### Post by Herman on 2009-11-19
> did what you said, and seemed to end up with exactly what I'd started with.. the web page you linked to.. I started by downloading the 'tarball' of the book.Yes, but now it's inside your computer instead of on the internet..:D

---

### Post by audiomick on 2009-11-19
g'day Herman.
thank's for the book tip from me too.
Michael

---

### Post by Annigma on 2009-11-19
> **Herman said:**
> Yes, but now it's inside your computer instead of on the internet..:D

Ahh I see :idea:

---

### Post by Herman on 2009-11-19
:D Since 'Grokking the GIMP' contains a few of image files, and image files are relatively large to transfer over the internet every time we revisit the web site, it will save a wee bit of bandwidth and take some load off the internet to just download the files once rather than every time we revisit the same website. 
It will also mean they'll be much quicker to appear as soon as you open the page in your browser, because they'll already be on your hard drive.

An interesting and sometimes useful thing to know is that our Mozilla Firefox  web browsers do download images and videos and other files from the internet and store them temporarily on our hard drives. That makes it faster to re-play a youtube video or to view the same image in a web page the second or third time in a day. 
 
You may already know that, but just in case it's interesting or useful to anyone else, I'll elaborate a little more.
If you go 'Places'-->Home Folder', and click 'View'-->'Show Hidden Files', you'll see a directory called '.mozilla'. 
Inside your .mozilla directory there should be one called 'firefox', and inside that there should be one with a name that looks like some meaningless random numbers and letters and ends in '.default' file extension.
Inside that  there'll be one called 'Cache', which is where you'll find temporarily stored images and youtubes. These remain for a while and then get deleted. That's why we have a lot of pauses when we're trying to watch a youtube on a slow internet connection, but when we replay it it plays properly, because it has already been downloaded and it's actually sitting in our file system.
Completely off topic, (sorry), but nevertheless possibly interesting to some. :D

---

### Post by Annigma on 2009-11-20
I keep trying to leave this thread, but feel compelled to respond when someone offers good and helpful advice, so don't blame me :P :D

I did know most of that, but didn't know exactly where FF stored them, and never thought much about how long they're stored. I suppose there is a cache size limit and older/less used files are removed to make room for newer ones.. and of course they'll be purged when we run tools like 'CCleaner', etc.. 
I also never realised why online video clips stutter, so that's interesting to know. I had noticed that if you pause, for instance, a youtube clip until the bar fills up, then it plays much better: just hadn't thought it through/made the connection.

So again Herman, thank you :)

I'm still fiddling about with FF profiles, but I'll resist the urge to ask questions, and try and find a suitable thread to find an answer/post in.

:D

---

### Post by audiomick on 2009-11-20
Hallo.
Firefox?
Look at this:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Found it the other day

Michael

---

### Post by Annigma on 2009-11-21
Ooh thanks Michael. That looks very useful. I've read a bit, and have bookmarked for later.

=D>

---

### Post by audiomick on 2009-11-22
Hallo.
This might interest you  too.
[http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)
Michael

---

### Post by Annigma on 2009-11-23
Lots of stuff there. Nice one :)

---

### Post by Scooter_X on 2009-11-24
I'd like to ask a question if I may. I've been reading this thread for the past 2 days trying to wrap my brain around partitions. I think I just need a little clarification.

> **Annigma said:**
> [COLOR="Blue"]
Current Partition Plan:
Primary C: (sorry Bartender) NTFS Win7 60GB
Extended: Logical: 
hda2 /ext4 15GB
hda3 /home 40GB
hda4 /swap 2.5GB
D: NTFS Data partition ~120GB/whatever's left


> **Annigma said:**
> 
Here's what I did:

Ran Gparted (from my 'wubibuntu' disc - lazy). Deleted all partitions. Made Primary NTFS, Extended, then 4 logicals: /, /home, /swap, data (NTFS)....

This is what I understand that she came up with:

 Primary: NTFS, [60GB] (for windows 7)

 extended/logical: ext4, [15GB] (for /)
 extended/logical: ext4, [40GB] (for /home)
 extended/logical: linux-swap, [2.5GB] (for swap)
 extended/logical: NTFS, [leftover space] (for file storage)


Am I getting warm? I think so. Thing is, is now that i am trying to install ubuntu, it says: "ready to install" and says it's going to format partition 5 and partition 7. Partition 5 is my (15gb for /), partition 7 is my (swap) one, but it doesn't ask anything about my (/home) one. I had an option of clicking on "Advanced..." whic popped up a window asking about the boot loader, and where to install it. Now, do I want my boot loader on my / or my /home?

---

### Post by audiomick on 2009-11-25
Hallo Scooter.
You're very warm.
The installer should want to format your /home as well, unless you are re-using an existing one. If it doesn't, you most likely forgot to check the box. Unfortunately, when you go back to the partitioner, I think you have to do it all again...

As far as the boot loader goes, let the installer put it where it wants to. You only need to change that when you are doing something other than what the installer expects, i.e. multi boot with more than what you have, re-installing one of many Linuxes, or something like that. I am not sure enough of my facts to go into details; you're better off looking into that yourself in the course of time. For now, as I said, don't bother with "advanced" on that point, just let it go ahead.
Michael

---

### Post by Scooter_X on 2009-11-25
Oh good. I actually went ahead with my suspicion that the advanced button didn't need any attention and now I'm running Karmic. Which is good. But I have a new issue now. You could go to [this link]("http://ubuntuforums.org/showthread.php?t=1337285") if you want to read my new thread on it. Probably best to post there, too. I basically can't install anything.

I don't have a /home directory. Is that screwing me up? I was just going to install things on my data partition. ....:confused:

EDIT: Nevermind. I figured out my issue. Remember, people. The Update Manager is your FRIEND. :D

Thanks anyhow. Take care.

---

