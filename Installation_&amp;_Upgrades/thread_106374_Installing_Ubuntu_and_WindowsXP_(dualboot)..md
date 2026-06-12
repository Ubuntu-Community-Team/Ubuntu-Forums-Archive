---
title: "Installing Ubuntu and WindowsXP (dualboot)."
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by godvict on 2005-12-20
I want to DualBoot my computer. I have 2 types of questions. 
What i need to know... 
-What O/S should I install first? What is a good size partition for Linux and Windows? (Will be using a new 120gig Seagate)

-My old HD (the 1 in my computer now) Has many mp3's and Video's witch i would like to share between O/S, Is that possible? For example if i was to RIP a CD using linux, then i was to load up windows would i be able to see the file and play it?   

Thx You Very Much.

---

### Post by harisund on 2005-12-20
You will need to install Windows first, since if you don't, and when you do install Windows first, it will erase the Master Boot Record, and you will not be able to get into your Linux installation again. 

Regarding your old hard disk, do you know what kind of file system it has on it? I am guessing you have NTFS. In case you do, writing into it with Linux won't be easy. 

Typically, irrespective of which platform you write a CD on you should be able to read it anywhere. How do you plan to do your writing and what do you plan to write? 

Ideally, 5GB for each operating system is great enough, but if you are planning on installing a lot of programs, you need to budget for that. But I would suggest trying to find out how much data you have and decide how much of the 120gig  you want for data.

---

### Post by godvict on 2005-12-21
I have a New 120gig HD out of the Box. I will install WindowsXP 1st, with FAT32 (using 30gigs, becuz my g/f will be using windows not me!). Then i will install Ubuntu on 10gigs, and have another partition about 20-30gigs to install linux software on it. 

My mp3's and Vidoes are on NTFS format. What im planning is coping the music/vids to the rest of my available 120gig partition(FAT32) then reformating my other HD to FAT32. After doing all that and having my music/vids on a FAT32 format, would both O/S be able to play the music/vids (prob after installing some other software). 

My goal is to be able to d/l music on windows (say to folder ( F: )Music ) and then be able to listen/see the mp3 on linux when i open ( F: )Music.

---

### Post by veloct on 2005-12-21
From linux you can read the NTFS drive, you just won't be able to write to it.  There's a way to do it but it's still very buggy and not suggested. If you are going to download the music in windows then you can keep the NTFS drive but if you do like you mentioned and reformat it to FAT32 you'll be able to read and write to it from linux. I would suggest you create a /home partition with about 15 gig and put / in 25 gig (going from your 40 gig amount you are planning on using).  For your /swap partition, set it to double your ram (if you have 1 gig then set your /swap to 2 gig).  HTH

---

### Post by godvict on 2005-12-21
(sorry kinda forgot about linux all together) ..

Out of 120gigs... This is what i plan
Windows = 30gigs (for the O/S and other progs)
Linux= 42gigs (/home 10gigs, /programs 30gigs, /swap 2gigs)
Music/Vids = Rest of HD 60gigs

My Only Questions are. 
/home is where linux will be installed?
&
/swap 2gigs, becuz i have 1gig of RAM?

Thx For You Help :)

---

