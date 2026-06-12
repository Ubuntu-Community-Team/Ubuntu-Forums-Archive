---
title: "Externel HDD Problem HELP"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by mraza08 on 2009-06-29
hi please i am new to ubuntu. i installed it from windows xp as dual boot on my 2nd hard drive. i have 3 hard drives, 2 internal and one external. in first hard drive i installed XP and in 2nd i installed ubuntu and in my external HDD i store my all Data for backup. now i am not sure what i did but my external hard drive has a lot of problems. first it only shows 10 mb with FAT file system in explorer in XP windows and in disk management it shows the correct size about 47.GB as actual size is 500GB and in ubuntu there are very wierd named files like "â=+FrÅ&#9508;
.C"  and "&#960;&#8729;^u&#9600;?a .&#9608;x" and many more.. please help me this drive has all of my data about 350+GB ...i really appericiate of your help.

 oh GOD i will have big loss with this  :(

Edit: when i see in drive properties i see File System as vfat(F12) of this drive...please help me ...thanks

---

### Post by starcraft.man on 2009-06-29
Did you ever touch it at all with any partitioning tools like the Ubuntu partitioner or gparted? If you had 3 drives, there'd have been multiple options to install to, your certain you installed to the correct internal drive? Any power outages during recent write operations to the external drive? Did you do anything in particular immediately before the drive failure started happening? Did you ever have any trouble before reading it in windows explorer or with nautilus?

Ok, that's all the questions that immediately popped into my head. From what you said, I'm thinking it's a drive failure (data corruption of some sort or physical failure). Happens to everyone eventually. To get data off might take some work, do you know what connector the drive uses? Is it a SATA (if it's new) if it's more than a few years it's an old IDE drive. Do you have a free slot in your current PC to support the connector it's using? As well as a free power cable to go to it? 

A lot of questions, answer please. I'm writing a recovery guide now as well, I'll post it once i've more info. I don't promise I can save anything, but we will try! :)

---

### Post by mraza08 on 2009-06-29
thanks for your reply !

first thing i install windows on first drive and i remove my external drive from computer and untill i installed ubuntu on my second hard drive i never connected it to computer. once i connect it to computer and booted to ubuntu and i was able to see the external drive in ubuntu. but suddenly when i went to xp i never see it again...only 10 mb with unknown files. and there was no problem of power here. and i don't think i did some sort of partation. i did install some software though via ubuntu package installer . and i did mount and unmount that drive. i am using USB connector with its own power cable connector..this hard disk is about 5-6months older.

please in this hard disk are some very important files...thanks for any help

and please don't forget i don't know much about ubuntu...this was just my second day :(

---

### Post by muglikar on 2009-06-29
Hello brother,
                    I have turned to Linux hoping it will solve my problem that my hard drive which is receiving a msg regarding my USB Hard Disk in xp "This device cannot start. (Code 10)"

I have chosen Ubuntu due to recoomendation by a frnd and his advocacy that Ubuntu has huge support and that he has not faced any prob whatsoever whne he used Ubuntu.

I think the problem is because I reinstallled XP sp2, which in turn I did because the HD was running well on my Dell Laptop but its not working on my Desktop...

Another prob is that scrolling on my desktop CRT monitor has suddenly become discrete after I reinstalled XP sp2...

I cant change my Monitor's refresh rate...Earlier I could change it from 60 Hz to 85Hz...

DO U THINK UBUNTU WILL SOLVE THESE PROBLEMS FOR ME?

---

### Post by starcraft.man on 2009-06-29
Edit: Mug, these comments aren't directed at you, please make a separate help thread in another topic. Your error is different.

Ok, good to know. If it's only a few months old I'm gonna assume it's a SATA connector, I don't think many companies made 500GB IDE drives. Also happy you knew to mount and unmount properly, and no power outage. So ya, I'm pretty sure it's some sort of drive failure. With external drives, sometimes it's the interface itself (i.e. the controller between the drive and the USB controller that fails. In order to rule this out, and expose the low level data to recover, we are going to put it into the main computer.

These are the steps I propose, please read them over slowly and carefully and prepare everything you need before you start step 1. If you have any questions, ask BEFORE you start.

1. Get the drive out of enclosure. If it's aftermarket (i.e. an enclosure you bought and put a drive in), you can easily remove it. If it isn't, and you bought it as a retail external drive you'll have to find a way to pry it open. They got it in somehow, so it does come apart. Be careful, no hammers or dropping, I recommend a flat head screw driver in the largest seem on it. Once the case is exposed, you need to usually unscrew the interface from the case and remove the drive from the interface.

2. Now you got your drive you want to save. Hook it up to your machine. Regardless of whether it's IDE or SATA you should be able to support it. If your unsure, list your motherboard/OEM Make and model and I'll tell you. IDE is the big fat wide connector, SATA is the cheap tiny one the size of the thumb. You should be able to look inside and see what you have, once opened you'll be able to tell what the drive is too.

3. Once installed properly, you need to download and run a disk rescuing software. I recommend [spinrite]("http://www.grc.com/spinrite.htm") personally cuz it's what I use on failing drives, but a lot of people don't like paying the price (google if your curious more). Linux has an alternative though called TestDisk, it comes on great utils like [System Rescue disk]("http://www.sysresccd.org/Download"). Download and burn the disk please. It comes with gparted btw as well, so you can see if your partition displays correctly one more time with that.

3b - Note: I just thought, you can at this point use GParted if it detects and recognizes the drive and partitions to mount them graphically and then use one of any means to get data off. That would be DVD burner, USB (another drive), Mount a partition on your other drives internal (the two you started) and copy over, some sort of online storage if you have access to.

4. Now that we got our tools, we get started. Put the sys rescue CD in and boot it. Push enter at first screen to initiate boot and wait for it to stop, it auto configures almost everything. Then when it stops, type in wizard and push enter. Then accept the first option on the main screen, and push enter to select it. This will get the GUI loaded.

5. GParted is in the menu at the bottom (looks like a hard drive), I suggest having a look with it at your partitions and seeing how things are now before proceeding. I assume they won't work right.

6. Now we are going to start up test disk, it's a terminal program so unfortunately no GUI or text-graphics. Push the CD in the bottom right, System > Test Disk. That opens a terminal with the program installed.a The first screen explains it needs to create a log file, just push enter and it will.

Quick tips: Up down left right are the keys to move. Enter selects an option. Tab moves you between menus and or buttons at the bottom (proceed, quit, etc...). That's all needed.

Next, you'll be presented with a list of drives/partitions. Scroll down to the one your trying to save (you should be able to tell). Select the partition (I assume it's one big storage NTFS one) then push enter.

Next screen asks how the partition table was made. I assume your on a standard Windows box, the first option that says intel is the one for you. The others are for specialty, like Macs, Xbox, etc...

Now, new screen, this is the meat of the program. Lots of options, the first one anylyse is what we want. Select it. Next, it will list your partitions. Push right arrow to select backup, this will back up current partition table. Next it will do a quick search, it asks if you want to check under vista, say yes even though I don't think you need it.

Next screen is the results. If they display green, they are ok (will also say so in the bottom part of terminal). If not, it should tell you right now that something is bad. Next step, we will do a deeper search, select the partition we're saving and push enter. Then you can do a deeper search, do so (one of the options at bottom). Takes some time, especially on a large drive.

Once this is done, we will be ready to do get this going. After all this, you'll be back at the main colored screen that says bad/good on structure etc, one after quick search. Highlight the partition we are working on, notice at the bottom there are choices, let's go over them. 

First notice after the explanation on how to navigate (see screenshot), it describes the different states. A * to the left of partition name indicates primary boot (this would be an OS), P means simply a primary drive, L a logical one, E an extended space and D means deleted. On my example, I have to partitions, the first is a bootable linux partition, the second a standard swap. Your case will be different, but it should detect what the partitions are and select the right labels accordingly.

You can actually modify the partition's characteristics by highlighting the drive in question and pushing left right, please remember what you started at. This is more if you know for instance the partition on your external drive is primary but detected improperly, then you'd change it. 

Now, assuming everything's alright, you can actually peak at the files on the drive by highlighting the partition and pushing p, the left right arrows will navigate you up and down directories letting you browse to make sure it's the right one. Once all set, your going to push enter on the partition with the data. 

This is last step, since deeper search has been done, only option is to write the partition structure to the table and hope it works. Once done, quit the program and reboot. This should be it, if not I think your in worse trouble.

If that doesn't restore proper access to the files, I'm gonna have to send you to spinrite. You can get a, uh, "free" version by the same means other people get free software. I'm not trying to encourage piracy, but the author I've listened to speak and really does want people to fix their drives. In fact, a lot of his customers that pay freely admit they took the software freely as skeptics, and paid once it fixed their drives and saved their life.

Note: If this process seems a bit too involved or complex, I STRONGLY recommend you call a friend who is a computer geek, he should be able to help. I've written my instructions best of my ability. Also, two heads are better than one. Please reply with any questions BEFORE doing anything (except download and burn the CD, that you can do anyway).

Note 2: There's no guarantee of data recovery. Neither test disk not spinrite offer a perfect solution. I hope one or then the other will do it, but I can't give a guarantee. If neither program can, you'd have to resort to a professional service and that costs a fortune. This is the best I can offer for free/90 bucks (cost of spinrite, if test disk doesn't work).

Note 3: Added step 3b, also wanted to note that this live environment gives you the option to log onto the internet with a browser and come ask for help on these forums. You can paste any terminal output and ask what to do at a given step. Please do so before committing any changes to drive.

Note 4: Just realized how FREAKING LONG this post is, maybe longest ever to a single case? I should get like 10 or 20 beans for that monumental effort of text. Hope it helps dude. Disk recovery isn't easy, if test drive doesn't do it I'll give you quick instructions on how to use spinrite (it's more straight forward, got a bit of a text-gui to it).

starcraft.man out for now...

---

### Post by mraza08 on 2009-06-29
i really appreciate your help [starcraft.man]("http://ubuntuforums.org/member.php?u=250927") ! and i will not let you down.. these were very clear guide lines, and i know i can follow them . unfortunately i don't have any friends near to me who can help me in these things. well i am not familiar with linux world at all but i participate in windowsmuch. i know some about web development. now it's very late here about 4,O clock midnight...gonna sleep will try in the morning...and will post here the results....thanks again for your immediate help

God bless you

---

### Post by starcraft.man on 2009-06-29
> **mraza08 said:**
> i really appreciate your help [starcraft.man]("http://ubuntuforums.org/member.php?u=250927") ! and i will not let you down.. these were very clear guide lines, and i know i can follow them . unfortunately i don't have any friends near to me who can help me in these things. well i am not familiar with linux world at all but i participate in windowsmuch. i know some about web development. now it's very late here about 4,O clock midnight...gonna sleep will try in the morning...and will post here the results....thanks again for your immediate help

God bless you

Your welcome. Man, I'm tired after that. I think I'm gonna take a bit of a rest. My fingers tired.

---

### Post by mraza08 on 2009-06-30
[starcraft.man]("http://ubuntuforums.org/member.php?u=250927")
i told you i will not let you down ;)

i really thankful for your quick help. and its really a nice community here. i like to congrats to ubuntuforums.org for having such a great team member like [starcraft.man]("http://ubuntuforums.org/member.php?u=250927") . i will never forget what you did for me. i was able to not only recover my external hard disk but also all data inside th disk with the software System Rescue Cd... and after recovering i enclose again to its box and connected via USB to my computer and everything is normal with this drive.

Now i have one strange problem....the first disk i have XP install when i boot xp the second hard drive (on which ubuntu is installed) will disappear after short time while running windows. but when i am running ubuntu no drive is making such a problem. and ubuntu never makes a problem while running. i  read some where that ubuntu can make damage to hard drive can you confirm that please? i hope you know any tool to recover this problem :) 

Thanks again for everything

---

### Post by starcraft.man on 2009-06-30
Glad your fixed up, ensure you back that up to somewhere safe. As to your problem, it is strange. I think you might be best served by making a new thread in beginner or general help section on that. The first thing I thought of was you formatted the drive with EXT3 or 4, Windows does not natively write to this file system. You can install a separate driver (search forums for windows EXT2 driver) but I just use NTFS on drives I want to share between Windows and Linux.

As to your last note, no, Ubuntu does not cause any damage to hard drives to my knowledge. 

Anyway, if it's not EXT3/4 then make a new thread in either sections noted and I'm sure someone more knowledgeable with HDDs can help.

---

