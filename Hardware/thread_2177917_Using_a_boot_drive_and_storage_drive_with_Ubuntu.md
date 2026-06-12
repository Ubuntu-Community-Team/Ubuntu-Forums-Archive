---
title: "Using a boot drive and storage drive with Ubuntu"
date: 2013-09-30
forum: Hardware
---

### Post by nathan173ab on 2013-09-30
Alright, so I'm seriously considering throwing off the shackles that Micro$oft calls Windows, but I have a unique hardware setup. Right now, I have Windows and all my background software like Steam installed on my 120GB SSD, with all the larger stuff like games, music, and photos on my 750GB HDD. I'd like to do the same with Ubuntu. Install Ubuntu and background software on my SSD and everything else on my HDD. Does Ubuntu have a streamlined way of doing that? That is, a way to install software where you want them to be installed using the Software Center or some other mechanism? Or, will I need to get my hands dirty with the Terminal. I'm not turned off from using Terminal, but it's not my ideal way of doing things. I like Ubuntu because of how close it's approaching its straightforward use, but if I have to use Terminal for this I suppose I will.

Any friendly guidance is appreciated.

---

### Post by TheFu on 2013-10-01
a) yes, you can do this.
b) only large games and java development take up lots of space (so I hear), a normal install will use less than 20G of non-HOME storage.

When you install, create 4 partitions to start.
1) / (20G)
2) swap (1-2x RAM, unless you have more than 4G of RAM, then make swap match IFF you hibernatem less is fine if you don't.)
3) /home (as much as you like, but I've never needed/wanted more than 20G)
4) /data (the place for media, huge games, things to be shared)

Install most programs ... as usual. These go into / and it is unlikely to be filled. Most programs that YOU install will go into /usr/bin/ with global system settings in /etc and parts that change in /var ... Differential backups rock for this area.  Personal settings are place in .... 
Your "HOME" - will hold personal files and settings, but nothing big. Do not put music, videos there. A few photos are fine, but really I treat this as a place for things I want to backup easily and also change.  Differential backups rock for this area.
/data  is where media and large data sit.  These do not change much, so I like to use a different backup technique for these files.

You didn't mention anything about backup storage.  Spend the $70 and buy another HDD that is used **only** for backups. All HDDs will fail and not having backups is asking for trouble. OTOH, having a backup means you get to sleep better every night since it is highly unlikely that both HDDs will fail on the same day.  It is best if the backups are 100% automatic - linux makes that easy.

If you want to install software to different places, you'll want to read the manual pages CAREFULLY.  There are trade-offs in doing this.  Stuff that gets installed using software center, synaptic should be installed where they default.  Linux package managers are amazing and they work wonderfully.  Avoid installing software outside the package manage. DO NOT download .deb files and install them - your life will suck in a few months when things start to break. Loading software with "setup.sh" or "install.sh" usually means you are NOT making use of the fabulous package manager - you have been warned.

Also, read my signature about LTS. This is really important for noobs - who should run 12.04 now.  Next May, 14.04 will be fine. Avoid odd year and non-April releases. Simple?

I've never used Steam - don't game - but I'd be surprised is there wasn't a setting for where games should be installed.  /data/games would be my 1st idea, if it were my system(s).

Finally, you can do anything you like.  The system has documentation on it for almost every command - **man dpkg** will get you started, but using dpkg directly isn't usually a good idea. Software Center is an extremely simplified interface - I don't use it, mainly because it hides things that I want to know.  Grandma likes it better, because things are simpler.  Synaptic might be a happy medium ... just know that APT is the package system and these are the tools to interface with it from lowest level to grandma ready.  dpkg, apt-get, aptitude, synaptic and software center are all GUIs over the APT system. You can mix and match which you use, they all modify the APT data and each is powerful for different uses.

BTW, you can move files around between disks as needed or add more partitions and move things there easily too. Suppose that /var get huge and you need to move it.  Easy (just not drag-n-drop easy).

Enjoy.  Don't forget to backup! ;)

---

### Post by oldfred on 2013-10-01
Good info from TheFu.

i have 4 drives. Two original old 160GB, one XP and one my original Ubuntu. Newer 640GB for Data and many test installs or old installs and a newish 64GB SSD with current 12.04 in one 27GB and another 27GB / (root) for next or test install. My working root uses 9GB with lots of stuff installed  but no games. I also keep my /home in my / on SSD but it really is just the user settings as all data including some hidden folders like Firefox & Thunderbird profiles are on my data drive. My /home is 2GB of the 9GB but 1.5GB of that is Picasa in .wine.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

   Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by TheFu on 2013-10-01
Good info from Oldfred above. 

Lots of different viewpoints are good. We've each had different experiences to bring us to our specific recommendations.  You will weigh each and make the best decision with your current understanding. 

BTW, the **only** time that I've had massive data loss was when using LVM - lost 3 drives worth of data because 1 of them failed.  I didn't have backup-religion back then, like I do now.  Sadly, it usually takes a failure like that for a human to learn it.

I use symlinks to bridge access across different partitions and mount new partitions under /data ... as in /data/m1, m2, m3, and t1 ... /data/t3. You get the idea. With about 10TB of storage here, there really isn't any other method that I trust.  Backups for non-/data areas are 100% automatic and capture system and personal files that are likely to change daily.  Things in /data are not nearly as important, so backups of those area are monthly, only if they have changed.  Usually, only the most recent mounted partition changes. Older /data/* partitions really just have static media files.  rsync rocks, BTW.

Morbius1 is really smart too so if those words reflect your situation, pay attention. Lots of smart folks here trying to help. ;)

I'd also point out that storage, backups, disaster recovery can be entire career choices each, so there are many different levels of "need" for each. Only you can decide what your level of need is.

---

