---
title: "Trying yet again to dual-boot"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by Veteropinguis on 2009-06-02
[b]I decided to just go with Ubuntu and cross the XP bridge when I come to it. If I need a program that can't be run under WINE or Virtualbox -as I suspect I will- I will figure something out. For now, there's no reason to deal with Windows.

Credit goes to (in alphabetical order):
[COLOR="Blue"]coffeecat[/COLOR]
[COLOR="Blue"]merlinus[/COLOR]
[COLOR="Blue"]raymondhenson[/COLOR]
[COLOR="Blue"]Shazaam[/COLOR]

Honorable mention for showing up: [COLOR="Blue"]Brayden13[/COLOR]

I learned a lot from this and hopefully, this 9-page saga will help a newbie in the future.[/b]

Original post below:

I've been trying to dual-boot since Hardy and I still haven't been able to successfully pull it off. Windows and Ubuntu run flawlessly by themselves, but neither will boot when I try to run both OSs. Windows loses ntoskrnl.exe and I can't copy it back over from the (legit) installation disc, while Ubuntu gets to a black screen with a blinking white cursor and stays there for eternity.

So in about 10 hours (tomorrow morning for me) I will be trying yet again. I have made a complete backup of all my data, I have all my discs assembled (XP installation, drivers discs, Jaunty disc, GParted disc) and I have no obligations until the evening. I plan on using GParted to completely wipe my hard drive and set up the appropriate partitions, then installing XP, then installing Ubuntu.

One consistent problem I have had with Ubuntu is that my whole system will hang during the installation and I will occasionally have to hard-reboot. I know this isn't good but when things haven't worked themselves out after 30 minutes, I don't see what choice I have. This doesn't happen when installing Windows. It also happened when I installed Mint a while ago. Is it overheating my CPU or something? Nothing else brings my computer to a complete halt like installing Linux does, so I'm not sure what's up. If it's a problem with my CD drive, I have another optical drive I can install.


I'd like to set it up so I can have my data accessible from either OS, if that's possible possible. Meaning, I'd like to have my Rhythmbox library be identical to my iTunes library, without having to dig around for the files. Same for my pictures, documents, and even game files I'd like to try and run under Wine. I'd like to have files I download in Ubuntu be accessible in Windows. I have about 55 GB of files and I expect that to get bigger. _How many partitions should I make, what format should they be, and what goes where?_ I have a 250 GB hard drive. If I've forgotten any precautions please let me know.

I've read all the dual-booting guides but so far I have not tried to dual-boot while in a clear state of mind, while cataloguing what goes wrong. I will have my laptop -which runs Ubuntu beautifully- and will be updating this thread when I hit the snags that have always stopped me before.

If anyone has had problems with ntoskrnl.exe before please let me know what your problem was, and how you fixed it. I did a forum search but I didn't find anything that was relevant. Unfortunately I don't really remember all the specifics from my last dual-boot attempts, since it's been several months since I last tried this.

---

### Post by Shazaam on 2009-06-03
My suggestions..
Windows gets at minimum a 50-60 gig partition.
Ubuntu/linux will work with a 10gig or larger partition (mine are 40gig minimum for breathing room).
Shared Multi-Media partition(s)- some suggest formating it as Fat32 (or Fat16) for compatibility.
Have you seen this?...
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by Veteropinguis on 2009-06-03
Thanks Shazaam. I just want to make sure I understand your post.

Why does Windows need 60 GB of space? Wouldn't I just need to make a partition with basically enough space to hold the OS, plus a bit more?

Also, to any other wonderfully helpful readers out there...uh, how exactly would I go about setting everything up so that both OSs read and write to the big partition?

I will be offline for approximately 9 hours from this post so I will not be able to give any further info.

---

### Post by Shazaam on 2009-06-03
Partition size-
Windows likes a LOT of free space so it's swap (page) file can stretch out (and fragment your files :) ) Thats why I like it to be that big (even with 2 to 3 gigs of ram).
FAT32 (or FAT16) shared partition-
Windows does not natively read/write to ext3 partitions without added drivers. I don't like Windows running roughshod all over my linux partitions so I don't use them. I have had Windows put it's "Recycle Bin" and page file on 6 linux partitions before. It got a bit tiresome deleting them all after running Windows. Ubuntu can read/write to almost ALL partition types so that is not a problem.

---

### Post by Veteropinguis on 2009-06-03
Doesn't FAT32 have a file size limit of 4 GB, and a partition size limit of 32 GB? I have some game files that are much bigger than that and can't be trimmed down.

---

### Post by coffeecat on 2009-06-03
> **Veteropinguis said:**
> Doesn't FAT32 have a file size limit of 4 GB

Yes

> **Veteropinguis said:**
> and a partition size limit of 32 GB?

No. That was a limitation of Windows 98, and a limitation of the formatting utility in Windows 2000/XP which can only create FAT32 filesystems up to 32GB in size. Windows 2000/XP can read FAT32 partitions of very large size, but they have to be created with 3rd party tools. Or with Linux. :p

Why not use NTFS? NTFS read-write support in Ubuntu is very reliable. You have the advantage of a journalled filesystem without the FAT32 filesize limit, and which you can share between Windows and Ubuntu.

---

### Post by Veteropinguis on 2009-06-03
I had read about using NTFS in Ubuntu, but all the articles said that it was still a work in progress. On further inspection, all those articles are from 2006. Should have looked closer :oops:

Could I do this:

1. XP (NTFS)(probably about 40 GB)
2. Shared (NTFS) (about 160 GB)
3. Ubuntu (probably also about 40 GB)
4. Swap (4 GB, 2x my RAM)

---

### Post by Veteropinguis on 2009-06-03
I'm going to go ahead and give that a shot. I may have to pay for my hubris, but that's a risk I'm willing to take. I'll be checking back here in a few minutes when I have all my CDs assembled; if any of you Good Samaritans see a reason to step in and offer some of your charitable advice, this is your last chance. Many thanks to coffeecat and Shazaam for their help so far.

---

### Post by coffeecat on 2009-06-03
> **Veteropinguis said:**
> Could I do this:

1. XP (NTFS)(probably about 40 GB)
2. Shared (NTFS) (about 160 GB)
3. Ubuntu (probably also about 40 GB)
4. Swap (4 GB, 2x my RAM)

That looks pretty fair to me. 40GB for Windows XP should be OK, so long as you don't have an enormous amount of apps installed. Vista would need more - A Vasta amount more. :wink: On my old laptop, XP lived and worked quite happily in only 20GB - and with only 512MB RAM. And 40GB for Ubuntu would be very generous for my sort of use. I rarely go above about 5GB in my root partition because I keep all my personal data on a shared partition, as you are going to do. But I don't run games in WINE, which I believe can use a lot of disc space. You'll need to check that for yourself.

The 2x RAM for swap is a fairly old rule-of-thumb for when people were using much less RAM. If you've got 2 GB, then I would say 2GB would be fine. If you are going to use suspend to RAM you must have a swap partition at least as large as your RAM, otherwise suspend may fail, but much more than 2GB is unlikely to be used. I have Jaunty NBR running in 512MB with **no** swap partition on my Asus EeePC, and I haven't had a system crash yet. Of course, I don't do any video encoding with it (life's too short :p ) and the 7" screen is a real disincentive to having too many apps open at once, so I've been lucky.

**Edit:** by the way, when you partition, it might be a good plan to make the Ubuntu root and swap partitions logical ones in an extended partition. That way, you don't use up your allowance of four primary partitions. Linux is happy to boot from a logical - unlike Windows. If it was me that was setting up, I'd go for:

sda1 - primary - XP
sda2 - primary - shared
sda3 - extended
      :     sda5 - swap
      :     sda6 - Ubuntu root

(You won't have to designate sda5 and 6 with those numbers. Anything >=5 is a logical partition and logicals will be given those partition numbers automatically.)

---

### Post by raymondh on 2009-06-03
> **Veteropinguis said:**
> I had read about using NTFS in Ubuntu, but all the articles said that it was still a work in progress. On further inspection, all those articles are from 2006. Should have looked closer :oops:

Could I do this:

1. XP (NTFS)(probably about 40 GB)
2. Shared (NTFS) (about 160 GB)
3. Ubuntu (probably also about 40 GB)
4. Swap (4 GB, 2x my RAM)

Looks good.  

If I may suggest, make your ubuntu partition an EXTENDED partition with root (/) and /home as logical partitions inside the extended.   This also refers to making a separate /home partition.  That way, when you decide to upgrade to another distro version, all you have to do is reformat/upgrade the root whilst keeping your /home (and all the tweaks, settings,etc you have done so far) intact.

Swap ... do you plan to suspend/hibernate a lot.  If so, it's a good idea.... specially if you have multiple apps running prior to suspend.  Nevertheless, with a big HD, 4GB is OK to spare.

You may have decided to install windows first.  General consensus is that's preferable.  Once installed and prior to installing/partitioning for shared and ubuntu, remember to defrag first.

Just out of curiosity ... what is the vintage of your system and BIOS?  Pre 2001 (I think) BIOS may have acpi difficulties which may cause boot up or shut down problems.

Lastly, as you know from your hardy experiences, try the Ubuntu version in LiveCD/live session mode first to get an idea re: compatibility with your specs.

Good Luck and regards,

---

### Post by Veteropinguis on 2009-06-03
I came in to check from the Jaunty LiveCD and everything's working perfectly out of the box. Good to see I'm starting to become less of a newbie and more of a novice.

I updated my BIOS some months ago and I bought my motherboard in 07, so that should be fine, right?

---

### Post by raymondh on 2009-06-03
A forum member, Didius Falco, while helping/responding to a thread, wrote a very good and understandable installation guide for the OP.  You might want to take a look....it may help you.  It starts at post # 7 and it involves making a partition prior and later on making a manual install.

[http://ubuntuforums.org/showthread.php?t=1175277](http://ubuntuforums.org/showthread.php?t=1175277)

Regards,

---

### Post by raymondh on 2009-06-03
> **Veteropinguis said:**
> I came in to check from the Jaunty LiveCD and everything's working perfectly out of the box. Good to see I'm starting to become less of a newbie and more of a novice.

I updated my BIOS some months ago and I bought my motherboard in 07, so that should be fine, right?

as the movie says .... "Houston, we are go for lift-off" :)

---

### Post by Veteropinguis on 2009-06-03
Hello from the Jaunty LiveCD.

If I want to make a /home folder -seems like a good idea- what partition should that be?

---

### Post by merlinus on 2009-06-03
Perhaps you are talking about a /home partition?  A /home folder is made automatically during installation, but it will be in the same partition as /.

At the partitioning screen, you can set this up with separate partition for / and /home, as well as /swap.

---

### Post by Veteropinguis on 2009-06-03
Merlinus, you're right, I meant to say partition. More specifically, what I'm asking is what number it should be, if that makes sense. (e.g sda1, sda2, sda3, etc)

---

### Post by merlinus on 2009-06-03
The number of the partition is irrelevant.  Just be sure that you leave enough space. I have /home right after /, and /swap is at the very end of the hdd.

---

### Post by Veteropinguis on 2009-06-03
Thanks very much, Merlinus. :)

---

### Post by raymondh on 2009-06-03
> **Veteropinguis said:**
> Merlinus, you're right, I meant to say partition. More specifically, what I'm asking is what number it should be, if that makes sense. (e.g sda1, sda2, sda3, etc)

That will depend on how many partitions you have set up already.

As you may know, you have a 4  partition limit, whether primary or extended.  The advantage of an extended partition is that you can have so many partitions inside it called LOGICAL.  Each logical partition is assigned a number depending on how many partitions are already in place.

have you already started partitioning?  Using liveCD, access the partition editor (system > administration) and take a screenshot of what gparted outputs.  Kindly post it.  Let's take a look visually on how you have it set up.

EDIT : Did not see Merlin's post.  You may consider this post as another way of saying 'it's irrelevant'.  If you wish, before installing, you may post gparted so the forum may comment on it.

---

### Post by Veteropinguis on 2009-06-03
So, running the GParted Live CD I got three logical block errors: 25088, 50176, and 50177. The screen also said something about an L - EC uncorrectable error and something like Medium Sense errors. I had to leave the room for a moment while GParted was booting so I frantically scribbled down what I could see. However, GParted booted and is running with no problems. I just deleted my main partition with no problems.

I got logical block errors last time I tried to install Ubuntu as well, even though I know that I have no problems burning LiveCDs that work.

Also, how big should my root and home partitions be?

---

### Post by merlinus on 2009-06-03
Trying to install from a defective cd drive is a recipe for disaster!

Also, as Raymond so astutely pointed out, you may wish to have but one primary partition -- the first on the disk -- and then create an extended partition for all the rest of the space.

Then you can create logical partitions within the extended for /, /home, and /swap.  It will make any future changes easier to perform.

---

### Post by Veteropinguis on 2009-06-03
So the logical blocks mean that I have a defective CD drive? :confused: I've installed Windows many times and have had no problems- why would it be different for Ubuntu? And when I installed Ubuntu on its own, it worked. Unfortunately at this point I don't remember if I got logical block problems back then.

On the partitions note: I've set up the extended partition, but how big should the / and /home partitions be? I have 30 GB of space left, so should I just split that up between the two drives?

---

### Post by merlinus on 2009-06-03
10G is plenty for /.  Give the rest to /home, but reserve about 1.5G for /swap.

As for the bad blocks, perhaps they exist on your hdd.

---

### Post by Veteropinguis on 2009-06-03
So I'm going to do what's in here...[http://ubuntuforums.org/showthread.php?t=707029](http://ubuntuforums.org/showthread.php?t=707029)

This is how I set up my partitions: [http://s582.photobucket.com/albums/ss268/Veteropinguis/?action=view&current=partitions.png](http://s582.photobucket.com/albums/ss268/Veteropinguis/?action=view&current=partitions.png) Did I get that right?

---

### Post by merlinus on 2009-06-03
4G for /swap is overkill.  1.5 is enough, if you have more than 1.5G RAM.  Also, I would place that partition at the end of your hdd.

Otherwise everything else looks fine.  Just remember not to format your ntfs partitions!

---

### Post by raymondh on 2009-06-03
Merlin has a point re swap.  Also, pls, pls, do not re-format your NTSF partitions.


Good luck.

---

### Post by Veteropinguis on 2009-06-03
I backed up all my data already- those are supposed to be blank. Is there another reason I should leave partitions those alone?

---

### Post by raymondh on 2009-06-03
> **Veteropinguis said:**
> I backed up all my data already- those are supposed to be blank. Is there another reason I should leave partitions those alone?

Am glad you have backed-up.  That advise was to make sure you don't erase those partitions (hence erasing any data you may have had there) as well as reformatting them to another format not intended.

How goes the install?

---

### Post by Veteropinguis on 2009-06-03
I decided to ditch the partitions and run badblocks on my whole hard drive. I used ```
sudo badblocks -swv /dev/sda
``` after I'd deleted all the partitions. I'm about 85% through so hopefully that wasn't a stupid move. So far there's no output or anything. I've also tried burning a Jaunty CD from a computer running 8.10, at 4.7x speed, to see if that will fix anything. My disk check should be done in about 60 minutes, after which I will repartition, install Windows, then install Ubuntu.

I've done more waiting then I expected, but I guess it's given me a chance to catch up on homework.:p

**edit** My optical drive and hard drive are both SATA. Does that matter?

---

### Post by Veteropinguis on 2009-06-03
badblocks has been running for about 2 hours now and the waiting is starting to drive me crazy. It tested, read, and compared with pattern 0xaa, whatever that means. It's now 1/3 done testing with pattern 0x55. It's not telling me if it's found any bad blocks or sectors or anything yet, just a few lines telling me what checks it's running and the timer.

If I stop it, will anything bad happen? Can I just make it stop and get my results? Or do I have to wait another two hours...

---

### Post by raymondh on 2009-06-03
> **Veteropinguis said:**
> I decided to ditch the partitions and run badblocks on my whole hard drive. I used ```
sudo badblocks -swv /dev/sda
``` after I'd deleted all the partitions. I'm about 85% through so hopefully that wasn't a stupid move. So far there's no output or anything. I've also tried burning a Jaunty CD from a computer running 8.10, at 4.7x speed, to see if that will fix anything. My disk check should be done in about 60 minutes, after which I will repartition, install Windows, then install Ubuntu.

I've done more waiting then I expected, but I guess it's given me a chance to catch up on homework.:p

**edit** My optical drive and hard drive are both SATA. Does that matter?

well done Veteropinguis ... having bad blocks may cause further problems down the road ... not to mention, "more hair loss" from frustrations.

Just a quick note as you seem to have partitioning down pat.

1.  Install windows first. Most consensus states it is easier that way.  After checking that the windows install boots and works, proceed with the ubuntu install.
2.  Remember to use manual install and be sure to which partition /, /home and swap goes into.  See the link I provided earlier (re; didius falco's guide). 
3.  Check to see if GRUB boots to both OS'.  If not, we can find solutions from there.
3.  Then mount the shared NTSF partition.

Good luck, will be back in about 3 hrs to check on your thread.

Regards,

---

### Post by Veteropinguis on 2009-06-03
Thanks for spending all this time helping me out, Raymond.

---

### Post by Veteropinguis on 2009-06-03
I've gone for an 'install now, check overnight' approach. Possibly stupid, but I need to see some progress.

Windows is recognizing a single 130 GB partition on my hard drive. I have a 40 GB partition I wanted to put XP in, and the 160 GB partition that's going to be shared space, so I have no idea what this is.

My XP disk is SP1, don't know if that matters. What can I do about this?

---

### Post by merlinus on 2009-06-03
Can you post a screenshot of gparted, whether from the live gparted disk or from within ubuntu (partition editor)?

---

### Post by Veteropinguis on 2009-06-03
[http://s582.photobucket.com/albums/ss268/Veteropinguis/?action=view&current=Screenshot.png](http://s582.photobucket.com/albums/ss268/Veteropinguis/?action=view&current=Screenshot.png)

I had deleted all my partitions to run badblocks, so this is the repartitioned drive. All the partitions are basically the same size, only difference really is that my swap space is smaller and on the end of the drive.

---

### Post by brayden13 on 2009-06-03
So how much have you dedicated to ubuntu? Do note that whatever you dedicate to ubuntu windows can't read as windows doesn't like anything that isn't fat or NTFS. And ubuntu uses EXT2 and upwards, as well as some other creepy file systems.

sorry i posted a little late, anyway i guess windows is having a crap out, looks like more than 130GB there

---

### Post by merlinus on 2009-06-03
From what I see in your screenshot, windows may be trying to use both of the ntfs partitions!  

Unless you can change that from the install screen, and have no valuable data on sda2, then let it do so.  Afterwards you can use gparted to shrink what will be sda1, and recreate sda2.  It will not try to install into an ext3 partition unless you tell it to use the entire disk.  In fact, it probably does not even see these partitions!

Not the best scenario, but indeed possible.

---

### Post by Veteropinguis on 2009-06-03
Okay, Merlinus, I'll give that a shot. I have no data on this HDD- everything has been backed up on to my iPod. I'll report back in probably about 30 minutes.

---

### Post by Veteropinguis on 2009-06-03
Well...I installed XP on that partition, but then when it rebooted it just went straight back to the text-based installer. It recognizes one 130 GB NTFS partition. It also recognizes that there is "another operating system" on the drive. I'm going to try a repair install. If that doesn't work, should I delete the partition XP is seeing?

---

### Post by merlinus on 2009-06-03
Did you remove the install CD before restarting?

---

### Post by Veteropinguis on 2009-06-03
Yes, I did. However all that happened was that now when I try to boot from the hard drive I get a disk read error and told to restart. Booting in from the Windows CD I get back to the graphical installer. :confused:

**edit** You know, at this point, I think I'm just going to ditch my partitions (yet again), do a clean install of XP, then go back and do all the partitioning again...just resizing XP instead of trying to wrestle it in to the right partition.

---

### Post by merlinus on 2009-06-03
Sounds like a good idea.  I still wonder, though, if you have bad blocks on your hdd.

---

### Post by Veteropinguis on 2009-06-03
If I do, that would seriously suck...I've been saving up to try to help fund part of a trip abroad this summer, I really don't want to have to dip in to that to buy a new HD. If I can get this damn thing going, I'll run badblocks tonight.

What's odd is that I have had 0 problems installing XP until now and it hasn't crashed on me except one mysterious time last year. (That time is what got me in to Linux.)

Yeah, I just booted in to GParted, and my whole drive has been turned in to NTFS, but GParted says that the device doesn't exist...yeah, I think it's better to just install XP and work around it. Oh well :(

**edit** ARGH. I went and deleted all my partitions in GParted, XP still only sees 130 GB. I guess I'll see if there are any spare optical drives lying around in my dad's office, that could be the problem. I don't see how I could have a failing optical drive if I can do everything but install Ubuntu, but I guess that could be what's happening. **update** I made my entire drive NTFS and XP recognized it. I chose to leave the filesystem from GParted intact and am now installing.

---

### Post by Veteropinguis on 2009-06-03
Installed XP with no problems. Haven't bothered activating or installing drivers. It's just there. Boot in to Jaunty, shrink sda1 (windows) no problem. I go about the rest of my partitioning with no issues.

I go to install. I set up sda5 as /, sda6 as /home, as planned. I have to add this from the install menu; I'm not sure if I added that in GParted this time around. Whatever. I tell Jaunty to format the partitions too, just in case there's some special Jaunty way of doing it. Jaunty recognizes my XP install, as it wants to import my XP settings. All goes well until 70% through the installation.

I got an [Errno 5] Input/Output error. So it looks like something is wrong with either my optical drive, my hard drive, or both. Thanks anyway for all the help, guys.

---

### Post by merlinus on 2009-06-03
Sorry to hear that....  If you could borrow an external CD drive, that would help to at least isolate the problem, and might even lead to a successful install.

---

### Post by Veteropinguis on 2009-06-03
I might be able to do that in a few days. I'll admit, at this moment I'm trying the installation again. I tried it in the LiveCD environment before, so this time I just selected 'Install Ubuntu'. If this works I'm expecting problems with a corrupt XP install and GRUB not being happy. **edit** Installation stopped in the same place. Someone somewhere reported that bad RAM had caused a problem, so I'll try swapping sticks out. **edit2** Same thing happened, same place. 69%. I'm going to try switching sticks.

---

### Post by Veteropinguis on 2009-06-03
So, I switched out RAM sticks again. My computer told me I had an unmountable boot volume a few times, then when I went in to the BIOS and set it so that I can only boot from CD, it started saying DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.

I don't really know what's going on, but I know this isn't good.

**edit** So far, I have reseated my RAM (don't know if I switched sticks), changed the SATA cable I was using for my optical drive, made sure that everything is plugged in properly, and gone in to the BIOS to enable a few tests on boot up- most notably a memory test. According to that, my RAM is all okay. I then sprayed a bit of compressed air inside my optical drive, didn't get too close too avoid damaging anything inside. I poked at the laser very gently with a q-tip that was lightly moistened with rubbing alcohol, then dried it with another q-tip. So, if none of this worked, then something is wrong with both my optical drive and my hard drive. Not sure what else I could do.

---

### Post by merlinus on 2009-06-04
Just to make sure -- you did run the cd check from the opening menu?  It may have worked previously, but gotten damaged in the process of so may attempts at installing.

---

### Post by Veteropinguis on 2009-06-04
Everything is completely secured. Jaunty and GParted didn't work, for some reason XP was no issue. Rather, XP is not shutting my drive down, it's just only recognizing 130 GB of my 250 GB hdd. Whatever. At this point I just want something to work.

---

### Post by Veteropinguis on 2009-06-04
To rehash what happened yesterday:

I was trying to dual-boot but kept running in to problems. The errors I got showed it was probably my CD drive. I had a full backup so I simply deleted all my partitions and made new ones. The problems I kept running in to were these:

- I could only get 69% through the Jaunty installation, then it would complain at me about an error5- meaning that I either have a hard drive on its way out, or an optical drive that's either dying or needs some love. I'm inclined to think it's the optical drive as I got sr0 errors every time I went in to Jaunty or GParted, though they always loaded. I got a cheap drive OEM with the confidence-inspiring name of SuperWriteMaster, so I can see why that would happen.

-When I only completed part of a Windows install, my CD drive died. Now, this all happened around midnight when I was sick and tired of dealing with computers, so I might have the sequence of events out of order. Essentially, what happened is that my CD drive just stopped recognizing disks, and I couldn't boot in to an OS because all I had was either part of a Windows install or a corrupted install.

-My dad, ever resourceful, has kept a spare CD drive and spare HDD around from an old computer. They are IDE and my drives are SATA, but I have IDE ports so I cannibalize some IDE cables from his Dell. I can now install XP, though it only recognizes 130 GB of my hard drive.

So now, here are the mysteries:

-If I try to do anything from the Jaunty LiveCD, my computer just shuts down. Doesn't give me an error message or anything, and it gets to the menu with no problems. However, if I try to do anything- it just powers off before doing a thing. I know it's firmly plugged in and I doubt it's a problem with my PSU, so what else could it be?

-Once I get to trying to do anything in GParted, the same thing happens.

-XP only recognizes part of my HDD, whereas Jaunty recognizes everything. I'm thinking of just creating a 40 GB NTFS partition for it and making the rest ext3 or something it won't recognize, then going from there. I know this is an Ubuntu board, but if anyone has some ideas as to why XP is acting like this, I'd like to try and be able to fix it. I remember encountering this problem before and getting past it, but I don't remember how.

So, why is my computer telling me it hates me and slamming the door to its room every time I try to boot a CD that isn't Windows? If it's a hard drive problem, I can try and hook up a 20 GB IDE drive, but I don't want to do too much on that. If I have to get a new HDD I don't want t invest too much work in a drive I'm just going to have to wipe.

What makes no sense to me is that my computer spits out anything Linux, but has no problems with opensource. I didn't have this problem at all on my laptop. In fact, Ubuntu was insanely easy to install and has been rock solid, even though I had no idea what I was doing when I installed it.

I just ran an md5sum on the iso I used, and an error check on the disk. Both are okay. The fact that I could run the error check makes me more optimistic.

Okay, I'm in Ubuntu and am going in to the partition editor. (Sorry if I'm spamming up the board with this; I'm trying to record what I'm doing so that future users who run in to similar problems can have something to follow.)

Partition editor worked, so I'm installing XP on the 40 GB partition. It recognized that my ext3 partition exists, and it recognized my whole hard drive this time. Go figure.

---

### Post by raymondh on 2009-06-04
> **Veteropinguis said:**
> To rehash what happened yesterday:

I was trying to dual-boot but kept running in to problems. The errors I got showed it was probably my CD drive. I had a full backup so I simply deleted all my partitions and made new ones. The problems I kept running in to were these:

- I could only get 69% through the Jaunty installation, then it would complain at me about an error5- meaning that I either have a hard drive on its way out, or an optical drive that's either dying or needs some love. I'm inclined to think it's the optical drive as I got sr0 errors every time I went in to Jaunty or GParted, though they always loaded. I got a cheap drive OEM with the confidence-inspiring name of SuperWriteMaster, so I can see why that would happen.

-When I only completed part of a Windows install, my CD drive died. Now, this all happened around midnight when I was sick and tired of dealing with computers, so I might have the sequence of events out of order. Essentially, what happened is that my CD drive just stopped recognizing disks, and I couldn't boot in to an OS because all I had was either part of a Windows install or a corrupted install.

-My dad, ever resourceful, has kept a spare CD drive and spare HDD around from an old computer. They are IDE and my drives are SATA, but I have IDE ports so I cannibalize some IDE cables from his Dell. I can now install XP, though it only recognizes 130 GB of my hard drive.

So now, here are the mysteries:

-If I try to do anything from the Jaunty LiveCD, my computer just shuts down. Doesn't give me an error message or anything, and it gets to the menu with no problems. However, if I try to do anything- it just powers off before doing a thing. I know it's firmly plugged in and I doubt it's a problem with my PSU, so what else could it be?

-Once I get to trying to do anything in GParted, the same thing happens.

-XP only recognizes part of my HDD, whereas Jaunty recognizes everything. I'm thinking of just creating a 40 GB NTFS partition for it and making the rest ext3 or something it won't recognize, then going from there. I know this is an Ubuntu board, but if anyone has some ideas as to why XP is acting like this, I'd like to try and be able to fix it. I remember encountering this problem before and getting past it, but I don't remember how.

So, why is my computer telling me it hates me and slamming the door to its room every time I try to boot a CD that isn't Windows? If it's a hard drive problem, I can try and hook up a 20 GB IDE drive, but I don't want to do too much on that. If I have to get a new HDD I don't want t invest too much work in a drive I'm just going to have to wipe.

What makes no sense to me is that my computer spits out anything Linux, but has no problems with opensource. I didn't have this problem at all on my laptop. In fact, Ubuntu was insanely easy to install and has been rock solid, even though I had no idea what I was doing when I installed it.


Hi,

Am sorry to hear this.

Try a different approach.  You have a working OS right?  Since you're thinking your computer won't have anything to do with a ubuntu/linux live CD .... why not make a liveUSB and try.

Another alternative is to pull the HD, mount it in a different computer and use that computer to set-up the dual boot.  Once done, put it back into the original, hard-headed computer and see how goes?

I'm trying to google right now the relationship of Linux and sata drives.  Will let you know results of interest.

Good luck,

---

### Post by Veteropinguis on 2009-06-04
I've been updating my previous post, which I guess was kind of stupid.

It seems to be working now. I set up a 40 GB NTFS partition just for Windows, so I think my Ubuntu installation should go fine. Once I've got everything installed, I'm going to run badblocks for the rest of the day, and then memtest86+ overnight. So far I am very optimistic. If this doesn't work, my problem is that my only USB drive is 32 mb -got it free from Google many a year ago- and I'm not sure what can be done with something that little.

---

### Post by Veteropinguis on 2009-06-04
Going for the installation again. I'm assuming Ubuntu will recognize that I created the separate partitions -I labeled them appropriately- so I just have to choose to install on /, and it will recognize /home?

---

### Post by Veteropinguis on 2009-06-04
XP installed without a hitch, as did Jaunty. As has happened in the past, Windows is missing ntoskrnl.exe.

Trying to boot to Jaunty gets me this:

Boot from (hd0,4) ext3   5459b40b-e8ef-4596-b288-638405d01943

What's up with the hd0,4 thing? Did something go wrong with the partitions?

---

### Post by merlinus on 2009-06-04
First of all, good on you for not giving in to computer malfeasance!

You will have to select the partitions and mountpoints at the partitioning screen.  Select manual, click on each partition, one at a time, and use the edit function to select mountpoint.  If they are already formatted to ext3, no need to do this again.

Good luck!

---

### Post by Veteropinguis on 2009-06-04
How specifically do I go about setting up a mount point? Is that the same as /, /home, etc? When it comes to Ubuntu I know that some things work, but I don't really know why or what the real names are.

---

### Post by merlinus on 2009-06-04
I missed your last post, as I was still writing mine.

If you look at the output of

```

sudo fdisk -l

```you will see where / is located. From what you wrote, it is probably sda5.

And yes, mountpoints would be /, /home, and swap.  These will be set up automatically, once selected.

---

### Post by Veteropinguis on 2009-06-04
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5229    42001911    7  HPFS/NTFS
/dev/sda2            5230       25971   166610115    7  HPFS/NTFS
/dev/sda3           25972       30401    35583975    5  Extended
/dev/sda5           25972       27442    11815776   83  Linux
/dev/sda6           27443       30218    22298188+  83  Linux
/dev/sda7           30219       30401     1469916   82  Linux swap / Solaris

That's mostly gibberish to me...

---

### Post by merlinus on 2009-06-04
sda1 = xp
sda2 = ntfs partition
sda3 = extended partition, using all the rest of hdd space
sda5 = /
sda6 = /home
sda7 = /swap

What can be confusing is that for the various config files, numbering starts at 0 (zero) for both hdd and partitions.  So hd0,4 = hdd1, partition sda5.

---

### Post by Veteropinguis on 2009-06-04
I don't understand why this isn't working, then...do I need to change where the boot flag is or something?

---

### Post by merlinus on 2009-06-04
Linux does not need a boot flag, but windows usually does.

Exactly what is not working?

---

### Post by Veteropinguis on 2009-06-04
GRUB loads, but then Jaunty stays at the startup for at least 10 minutes. I can try booting again though.

I don't even get to a progress bar or anything. Just a black screen with white letters that say, 'starting up'.

And this time, it's not even saying 'starting up.' Just 'boot from (hd0,4) and that same string of numbers and letters I posted before.

I've got 2 GB of RAM and a 3.2 GHz CPU so I'd be very surprised if I'm underpowered. Windows never took this long to load.

---

### Post by merlinus on 2009-06-04
Sad to say, it looks like a problem with your ubuntu installation.  If grub could not find the / partition, you would get an error message to that effect.

---

### Post by Veteropinguis on 2009-06-04
Is there anything I can do? Also, how could this have messed up my Windows install if I didn't touch my Windows partition?

I guess I'll just boot back in to the LiveCD and run badblocks for the rest of the day.

I went in to the BIOS to see if I could see anything weird. All I see is that my SATA HDD is set as IDE Third Master. Does that matter?

---

### Post by merlinus on 2009-06-04
When the grub menu appears, press the letter e on the keyboard.  You should see the entire booting command line.  Remove "quiet" if it is at the end of the line by using the backspace key -- you may have to press e again.

Then boot up again, I believe by pressing b.

This should give you info about what is happening during the booting process, and you can see where it is hanging.

---

### Post by Veteropinguis on 2009-06-04
Awesome! That worked!

Now I just have to try to fix my XP, but I have Ubuntu!

Thanks so much, Merlinus! Here, have some popcorn: :popcorn:

---

### Post by merlinus on 2009-06-04
Great news!  To make the change permanent, however, you will have to edit a file.

```

gksudo gedit /boot/grub/menu.lst

```

Scroll down until you see the section marked ## ## End Default Options ##

Just below that is the entry that boots ubuntu.  It should look something like this:

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        8268d051-ae3a-4d8b-9c21-ddf82d782734
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8268d051-ae3a-4d8b-9c21-ddf82d782734 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

Remove splash and quiet from all lines.  Save the file, and exit.  No need to restart.

---

### Post by dE_logics on 2009-06-04
Well...nothing happened with me...I'm still on ubuntu + XP dual boot...working very stable.

---

### Post by Veteropinguis on 2009-06-04
Agh, stupid Windows. It looks like my XP installation just...disappeared or something. I tried to follow the instructions here: [http://www.computerhope.com/issues/ch000646.htm](http://www.computerhope.com/issues/ch000646.htm) to put the nt kernel back, but I couldn't pick an installation. I figured I'd just try to reinstall XP on the partition I left for it, but Windows is only seeing that 130 GB partition.

I suppose I can try booting in to my GParted CD, reformatting XP's partition, making the shared partition ext3 for now, installing Windows, then formatting the shared partition back to NTFS. What I don't understand is how my Windows install got screwed up when I never touched those partitions.

---

### Post by merlinus on 2009-06-04
You are trying to make logical sense out of windows????

:p

---

### Post by Veteropinguis on 2009-06-04
Yeah, I think Windows doesn't like the thought of us parting ways :(

I'd ditch it completely, but I use some software that can't be run in WINE and has no good open alternatives.

---

### Post by Veteropinguis on 2009-06-04
Um, I think I messed up GRUB...I deleted where it said 'quiet' and 'splash' but now I'm stuck at where it says 'starting up' on the black screen. All I did was run Compiz-check, enable my nvidia driver, and reboot. So, I'm rather confused about what's going on.

I've been letting this screen stay for a few minutes, but nothing's happening. Tried booting in recovery mode, nothing happened. :confused: What could I have done wrong?

---

### Post by merlinus on 2009-06-04
The driver may be the problem.  Also, you can try to run win apps in a vm under linux, if you have enough system resources.

Go through the steps I outlined previously whilst grub is onscreen to make sure that quiet is deleted.  Then you should see each step of the booting process.

---

### Post by Veteropinguis on 2009-06-04
Quiet is deleted. I want to make sure I'm not misunderstanding your instructions...

I get to the GRUB menu. I have three Ubuntu options: Ubuntu 9.04, kernel 2.6.28-11-generic, Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode), Ubuntu 9.04, memtest 86+, and the option for my XP install. I'm choosing the first option. When I hit b, I just boot like normal. Sometimes I get the Starting up line, sometimes I don't.

Still, nothing's happening.

I guess it might be time to hook up that other hard drive.

---

### Post by merlinus on 2009-06-05
Did you try recovery mode?  If that works, then you might try going back to your old video driver.  If that is the only thing you changed, then it may be the culprit.

BTW, how did you go about installing it?

You also might post /etc/X11/xorg.conf, which has the video settings in it.

---

### Post by Veteropinguis on 2009-06-05
I ran Compiz-check and got the driver that way. I couldn't boot in in recovery mode either.

Currently I'm installing XP and Ubuntu on an old 20 GB IDE drive I rustled up...never thought my dad's Dell could be so useful. I haven't set up a shared partition on this- could that somehow be part of the problem? I'm figuring that if everything works on this new hard drive, the problem has to be with my old hard drive.

I have yet another CD drive I could try using if it's a problem with my replacement CD drive. But since I had no problems under XP -Windows wasn't a headache, I just want to try something new- I'm not sure what to think about potential hardware issues. On the other hand, maybe this is sort of a heads-up about hardware problems that would have hit me later.

**edit** Aha! On my replacement drive, I can boot in to Ubuntu perfectly, but I cannot boot in to XP. This time around Jaunty told me it was using proprietary drivers, and it didn't do that before. So I installed the driver, rebooted, no problems whatsoever. XP says ntoskrnl.exe is missing. Jaunty booted in about 45 seconds. I'm not sure if this is +1 for Linux or not. Also, I told Jaunty to split the drive between XP and Ubuntu. Somehow, on this 20 GB drive, I have 98 mb of free space for Ubuntu and 17.3 GB for XP. Not sure what happened there.

Now, on closer inspection, my XP CD has some scratches. This is probably because it was stored in a paper sleeve with no top -nothing to keep the disk from falling out- in a tiny closet that serves quadruple duty as office storage, storing my sister's shoes, holding my clothes, and some of my sister's stuff. So it probably had a few bad experiences with the floor. If I can find a skip doctor or something, would that help my woes? I'm inclined now to think that my woes were because of a basically dead CD drive, a hard drive going out -odd because it hasn't been in use long, but whatever, they wear out- and because of a scratched CD. I have no tech background so I can't be sure, but that's my gut instinct.

---

### Post by merlinus on 2009-06-05
Hi.  Sounds like some progress has been made, especially in terms of beginning to localize the problems.

Again, good on you for hanging in there!  I am sure the experience and knowledge gained in this process will serve you well in future.

Keep me posted!

And remember the age-old adage:  To err is human, but to really screw things up, you need a computer!

---

### Post by Veteropinguis on 2009-06-05
Update: I was experimenting on this other IDE drive. Jaunty installed like a charm, took about 20 minutes plus another 5ish to enable some fancy effects and install a driver.

I went in to the XP recovery console and on this disk, my XP install was seen. I went in and followed step #5 here [http://www.computerhope.com/issues/ch000646.htm](http://www.computerhope.com/issues/ch000646.htm) and XP said it successfully expanded the file. But, I tried to boot in to XP again, and got the same message. 

So, I'm back on the SATA drive and I have a new plan. I have deleted all my partitions. I am repartitioning and will then install XP. Once I have installed XP, I will boot in to the Jaunty LiveCD and copy ntoskrnl.exe on to my flash drive. I will then install Jaunty, plug in my flash drive, navigate over to my Windows partition, delete that ntoskrnl.exe and replace it with the one off my flash drive. My reasoning is that if ntoskrnl.exe is somehow being corrupted every time I install Ubuntu, the ntoskrnl.exe from before Ubuntu ever touched the system should be safe.

If this doesn't work, then tomorrow I'll take the XP CD around to Gamestop or Blockbuster to see if they'll take care of the scratches.

---

### Post by Veteropinguis on 2009-06-05
Well, I don't know why, but that flash drive plan didn't work. Once again I have two unbootable operating systems. I've got to figure out why Ubuntu and XP can't play nicely on my hard drive. It's either my hard drive itself (merely a year old and fortunately still under warranty) or my XP disk, at this point. The strange thing is that this happened even when I tried installing using Wubi, which is +1 suspicion about my HDD. However I've had solid XP installations before, which for me is mysterious problem +1.

The big mystery is why installing Ubuntu on a totally separate partition makes XP unbootable. That happened every other time I installed, plus it happened with a completely different CD drive and hard drive plugged in. So the only common factor, so far as I can see, is the XP disk. **edit** I suppose this time around it might also be that video driver. Or I guess even the video card itself. Should have thought of that before I went and deleted all my partitions again. When I try this again I'll see what happens if I unplug my video card.

I'll finally be able to run badblocks, which should be rather revealing. Anyone got an idea of how long that would take to run on a blank 250 GB HDD?

**edit2** I'm posting some system specs for anyone who's reading this.

Motherboard: MSI 975X Platinum PowerUp Edition
CPU: 3.00 GHz P4
HDD: 250 GB Seagate Barracuda
RAM: 2 GB Kingston ValueRam
Graphics: nVidia 8600 GT

---

### Post by merlinus on 2009-06-05
I do not understand the xp dual-boot situation either.  I have never had problems dual-booting with various versions of ubuntu (since 6.x) and win 2000, even installing win after ubuntu and restoring grub.

I run nvidia cards on both of my systems with no problems, either.  The new machine has a geforce 9400 gt.

So your xp disk may be faulty, and bad blocks that are unmarked on the hdd will be deadly.  If they are marked in advance by a troubleshooting program (even using win chkdsk), then no disks will write to them.

---

### Post by Veteropinguis on 2009-06-05
Fortunately, my hard drive has another two years under warranty. So, if badblocks reveals any problems, I can probably ship my drive out on Monday. I'll be able to survive with the 20 GB IDE drive for a while. The only thing I won't be able to do is use iTunes...I don't mind seeing if Amarok will work on my iPod Classic, but I should probably wait until my files are restored to my PC and backed up on another drive. 

Anyone know how many tests badblocks runs? The command I used was ```
sudo badblocks -swv /dev/sda
```, don't know if that matters. It's been going for about three hours now and is halfway through the 'Reading and comparing' stage of the second test, pattern 0x55. I know these things take time. I'm mainly curious because I have a few errands to run, but I really want to fit a memory test in because I have to leave my hours for the rest of the day in two hours, and I'd like to have a memory test running during that time. Each test takes 45 minutes, and each 'Reading and comparing' stage takes 45 minutes. So, I'd just like to have some idea of how long this could take, if that's possible.

---

### Post by Shazaam on 2009-06-05
If you get to where you are totally disgusted and you have the room in your pc can I make a suggestion?
1. Put both the 20gig drive and the 250gig drive in the pc.
2. Attach the 20gig as the PRIMARY Master (first) drive by plugging it into the FIRST IDE port on the motherboard, then attatch the 250 as the SECONDARY MASTER (or however your SATA drive hooks up). (2 seperate cables/ports). Attatch your cd/dvd drive(s) as either a primary SLAVE or a secondary SLAVE.
3. Install Windows to the 20gig. Update/configure it and make sure it works fine.
4. Boot the Ubuntu livecd to the desktop and run gparted (Partition Editor), run each of the rest of the operations ONE at a time.
5. On the 250 make an EXTENDED partition to take up the whole drive.
6. Inside that EXTENDED partition make  a 1gig /swap LOGICAL partition.
7. Again inside the EXTENDED partition make 2(or more) LOGICAL partitions- one for Ubuntu (plus another if you want a separate /home partition) and make the other your SHARED partition (Fat, NTFS, ext3, whatever).
8. Install Ubuntu to the LOGICAL partition(s). The default grub install should be fine.
That is similar to how I have my pc set up except that since I use linux more often I have that drive set up as the first in the bios boot order. Here is my fdisk...
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00047d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   625137344   312568641    5  Extended
/dev/sda5             126     4369679     2184777   82  Linux swap / Solaris
/dev/sda6         4369743    53817749    24724003   83  Linux
/dev/sda7        53817813   136086614    41134401   83  Linux
/dev/sda8       136086678   458398709   161156016   83  Linux
/dev/sda9       458398773   625137344    83369286   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000096f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156296384    78148161    7  HPFS/NTFS
```
SDA- SATA
sda6-PuppyLinux
sda7-Mepis
sda8-Ubuntu Hardy
sda9-Ubuntu Intrepid

SDB- IDE (PATA)
sdb1-WinXP
As an aside, go here...
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
and download/burn a stand-alone cd of gparted (partition editor- same as the Ubuntu one). That way you won't wear out your Ubuntu cd :)
Another great tool is the SuperGrubDisk...
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Veteropinguis on 2009-06-05
Edited for me being stupid. You wouldn't have mentioned a shared partition if it wouldn't still be shared.

After badblocks is done running (I finally found what I was searching for in the manual- badblocks runs 4 tests, at 90 minutes per test that means I have about an hour of testing left) I will check my results and decide what to do from there. If my hard drive doesn't need replacing, I'll probably just do the two-drive installation.

---

### Post by Shazaam on 2009-06-05
I like the 2 drive setup because if one dies you don't lose everything. And there isn't really a limit to how many logical partitions you can have. At one time I had 9 different versions of linux on the SATA drive. :)

---

### Post by Veteropinguis on 2009-06-05
There are no bad blocks on the hard drive! Since I have no real reason to think my RAM is faulty, and since I can hold on to this IDE drive, I'll be taking the two-hard drive approach. This ended up being a really big thread for something as simple as hardware failure, but I learned a lot and have a great story about the Ubuntu Forums to tell others who might want to use Ubuntu.

**edit** Heh, awesome, I've started installing Ubuntu at 9:04 PM. **edit2** Figured I'd mention that I'm following Shazaam's instructions, and will be very happily setting my boot order to Linux first.

---

### Post by Veteropinguis on 2009-06-06
Well, somehow I ended up on an infinite loop of the first part of XP's installation, but I figured out what to do:

1. From XP setup screen, delete all partitions. Quit setup, eject XP disk.
2. Insert Jaunty CD, reboot.
3. Answer 7 questions, spend 5 minutes setting up partitions.
4. Apply updates, install ubuntu-restricted-extras, enable proprietary drivers.
5. Reboot. Done. Celebrate.

Ubuntu performed flawlessly throughout this whole ordeal; every last problem I had was with Windows.

Installing Ubuntu, while wandering around my house chatting on the phone with a friend -and thereby letting several prompts wait -> adding to my time- took 35 minutes according to my stopwatch.

Trying to make Windows play nice took three days. Not worth it.

---

### Post by Shazaam on 2009-06-08
Congratulations! I'm glad you got it working.

---

### Post by raymondh on 2009-06-08
> **Veteropinguis said:**
> Well, somehow I ended up on an infinite loop of the first part of XP's installation, but I figured out what to do:



Well done =D>

---

