---
title: "Number, types and sizes of partitions"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by neymac on 2005-12-12
I have 1Gb of RAM. 
Do I need a /swap partition?  If yes does it need be 3 times the RAM size?

 I've read that it's more safe to put /,  /home and /usr in different partitions, it's easyer to upgrade to newer versions keepping yours files in /home and /usr untouched when you format the / partition.

Questions:1) The above is true?
               2)Which is the minimum and recomended size for the /, /usr, /swap partitions for Ubuntu Breezy and Daper?
               3)Is there any problem in mix file system kinds (reiser, ext2, ext3,...)?
               4)In upgrades formatting the / , do I keep my /usr files after installation?

Base HD partition for Ubuntu 10Gb.

[PHP]Partition      Size     Type
/                 ?        ext3?
/swap             ?        swap
/usr              ?       reiserfs or ext3?
/home     (the remain)    reiserfs or ext3?  [/PHP]

[PHP][/PHP]

---

### Post by earobinson on 2005-12-12
[http://www.ubuntuforums.org/showthread.php?t=101252&highlight=swap](http://www.ubuntuforums.org/showthread.php?t=101252&highlight=swap)

---

### Post by SickTwist on 2005-12-13
Do not make swap larger than 2 GB. I do not think the kernel is configured to use more than that. Although, if you have 1 GB of RAM, swap will probably not be used much.

It is a good idea to put / and /home on separate partitions. Do not worry about a separate partition for /usr. The reason /home should be separate is because that is where each user's data and preferences will be stored. Later on, you can format / if you need to while preserving /home.

You can use a different filesystem on each partition with no problems. Ext3 and ReiserFS are both good choices. Ext2 is outdated and does not support journaling.

Ubuntu can be safely upgraded from one version to the next without having to reformat anything. However, if something broke or if you wanted to use a different Linux distribution, you should format the / partition but *not* the /home partition. The Ubuntu installer allows all of this to be accomplished with the partitioning utility.

Here is my recommendation if you have a 10 GB HDD and 1 GB RAM:
```
Size                    Type                     Mount Point
4 GB                    ReiserFS                 /
1 GB                    swap
5 GB                    ReiserFS                 /home
```

---

### Post by earobinson on 2005-12-13
The swap is vertual memmory it all depends on what your going to be doing.

---

### Post by NotJustANewbie on 2005-12-13
@ earobinson, swap shouldn't be too big. Roughly double your RAM.

@ SickTwist, I would make a 10Gb install with a bigger partition for the / than /home.

---

### Post by SickTwist on 2005-12-13
I suggested 4 GB for / because Ubuntu only uses about 2 GB after a default install. I figured the limited HDD space would be better spent in /home where users will save documents, video, music, pictures, etc. Those things tend to outgrow the size of /, at least on my machine.

None of these configuration options are written in stone, though--that's the great thing about Linux. ;)

---

### Post by NotJustANewbie on 2005-12-13
Its a thing of habit then really. I keep all my music on /music (in root partition)

---

### Post by azteech on 2005-12-14
[quote=neymac]I have 1Gb of RAM. 
 Do I need a /swap partition?  If yes does it need be 3 times the RAM size?
 
I've read that it's more safe to put /, /home and /usr in different partitions, it's easyer to upgrade to newer versions keepping yours files in /home and /usr untouched when you format the / partition.
 
 Questions:1) The above is true?
                2)Which is the minimum and recomended size for the /, /usr, /swap partitions for Ubuntu Breezy and Daper?
                3)Is there any problem in mix file system kinds (reiser, ext2, ext3,...)?
                4)In upgrades formatting the / , do I keep my /usr files after installation?
 
 Base HD partition for Ubuntu 10Gb.
 
 [php]Partition      Size     Type
 /                 ?        ext3?
 /swap             ?        swap
 /usr              ?       reiserfs or ext3?
 /home     (the remain)    reiserfs or ext3?  [/php] 
 [/quote] 
With the limited HD space you have, I would recommend the following partition set up:

/boot - 100MB (to 250MB)
/ - 4GB
/swap - No more than 2GB
/home - individual program settings and personal documents
/music - all your music files

Note each of these are separate partitions.
Because you do have 1GB of ram, you may not need to set up the /swap partition. But I would still recommend setting one up; it may not be used often, but still good to have it there, just incase. 
I recommend setting up this way as it allows you to have separate partitions for OS and data. The latter two partitions allow you just back them up, (and restore just them should something happen). 

To the best of my limited Linux knowledge, there is no rule about mixing fs types (e.g. reiser, ext3, etc.) But, as SickTwist stated above, none of this is really set in stone - everyone reviews the basic guidelines for partitions and then establishes their own particular way of setting them up. Once you get comfortable with using ubuntu, and Linux, I am sure you too will settle on a particular partition scheme that works best for your situation.

If you plan on upgrading down the road, there should be no problems. But, as with any upgrade for ANY OS, you should always back up 1st, as a precaution. Once you back up the /home and /music partitions, if you do an upgrade, or if you have to re-install Ubuntu, for any reason, you will not (rather should not) have to reformat the latter two. All you should have to do with the /home and /music partitions is to set the labels for them, but not format them. That way the data on the latter two partitions should remain intact.

---

### Post by neymac on 2005-12-14
[QUOTE=azteech]With the limited HD space you have, I would recommend the following partition set up:

/boot - 100MB (to 250MB)
/ - 4GB
/swap - No more than 2GB
/home - individual program settings and personal documents
/music - all your music files

Note each of these are separate partitions.
Because you do have 1GB of ram, you may not need to set up the /swap partition. But I would still recommend setting one up; it may not be used often, but still good to have it there, just incase. 
I recommend setting up this way as it allows you to have separate partitions for OS and data. The latter two partitions allow you just back them up, (and restore just them should something happen). 

To the best of my limited Linux knowledge, there is no rule about mixing fs types (e.g. reiser, ext3, etc.) But, as SickTwist stated above, none of this is really set in stone - everyone reviews the basic guidelines for partitions and then establishes their own particular way of setting them up. Once you get comfortable with using ubuntu, and Linux, I am sure you too will settle on a particular partition scheme that works best for your situation.

If you plan on upgrading down the road, there should be no problems. But, as with any upgrade for ANY OS, you should always back up 1st, as a precaution. Once you back up the /home and /music partitions, if you do an upgrade, or if you have to re-install Ubuntu, for any reason, you will not (rather should not) have to reformat the latter two. All you should have to do with the /home and /music partitions is to set the labels for them, but not format them. That way the data on the latter two partitions should remain intact.[/QUOTE]

Thanks for the advice.
I liked the proposal of have /music in a partition to put your musics, photos and movies, it is really a good idea because if  things go wrong you can reinstall Ubuntu again without lost these files.

About set labels for /home and /music at the begginning of a new reinstallation, is it only set these mount points when installation program asks for (without formatting them) or is there any other means after the installation?

---

### Post by linbetwin on 2005-12-14
With 1 GB of RAM, I doubt you even need a swap partition. Anyway, just to be safe, you can make it 500 MB, or even less.

---

### Post by azteech on 2005-12-14
[quote=neymac]Thanks for the advice.
I liked the proposal of have /music in a partition to put your musics, photos and movies, it is really a good idea because if things go wrong you can reinstall Ubuntu again without lost these files.

About set labels for /home and /music at the begginning of a new reinstallation, is it only set these mount points when installation program asks for (without formatting them) or is there any other means after the installation?[/quote] 
With regards to setting labels, when installing (or reinstalling) Ubuntu, it will ask you how you wish to setup the partitions. You will want to select the manual partitioning option. It is from there you can set up the partition names/lables, and, you can also chose to format, or not format a particular partition. 

I would highly recommend keeping notes as you install Ubuntu (or any linux version) about which partition is set up for what. That way you don't become confused, down the road, as to the purpose of a particular partition.

---

### Post by neymac on 2005-12-17
Thanks, azteech.

---

