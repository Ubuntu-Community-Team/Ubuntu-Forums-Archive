---
title: "Windows/Ubuntu dual boot partition setup, please check!"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by ChrisUK on 2009-10-29
Hi all.

I'm wanting to dual boot Windows Vista with Ubuntu. I've read various guides on how to partition the drive in different ways but all the options are kind of confusing me a little.

I'll probably be booting between the OS's quite regularly because there are some programs on Vista that will not work on Ubuntu.

Here is the partition setup that I am considering;

Windows Vista (NTFS) - Not sure how large this has to be but will probably leave 60GB as I will be installing quite a few applications.

Shared Data (NTFS) - I read that FAT32 has limitations, specifically not being able to store files over 4GB in size? This will be no good for me because I will have files over 4GB.
Apparently Ubuntu can read and write NTFS without any problems?

Ubuntu (EXT4) - I'm not sure whether to use ETX3 or ETX4? Size will probably be 20GB as I doubt I'll be installing loads of apps in Ubuntu.

/Home - (ETX4) - No idea what size this should be?

Swap - 6GB in size (I have 4GB RAM).


I'd like to be able to share my files between OS's, so does the above setup sound OK for my needs?

Any help would be appreciated.

---

### Post by MrSnowmiss on 2009-10-29
> **ChrisUK said:**
> Swap - 6GB in size (I have 4GB RAM).

From what I have heard, set the swap to double your RAM or to 2GB, whichever is the most. So 6GB could be too much. But some other people might get you more info on that.
For the rest it seems a good setup (from what I recall, haven't been using windows since a year now ;))

---

### Post by NTHQ on 2009-10-29
I am thinking of doing the same but with Windows 7 instead of Vista. After asking for help here, this is the answer I got.

> **bulldog said:**
> 
How would I do it.
Create a primary for windows 100GB
Create a primary for data 100GB
Create a primary for /home 100GB
Create an extended partition as big as the rest of the hdd
Create in the extended a logical 10GB
Create in the extended a logical 10GB
Create in the extended a logical for swap 2GB

Some explanation ,you can do it with other size partitions of course,but it's the idea what counts.
Windows is clear I presume.
The reason I made several primary is that if your windows is running out of space,you can easily give space from the data partition to your windows [max 100GB extra]
Then I go to the logical partitions.
I create two 10GB partitions,one you will use for your current ubuntu install,which only will have your /  [system files] which would be more than sufficient and your personal data will be located on the primary which I created as /home.
If in the near future you want to install a newer version of ubuntu,but you don't want the risk of loosing your current install,you just use the second 10GB partition,the same swap and the same /home folder.
Only use for the new install another login and password,it will create his own folder on your /home,and you can copy/paste all your data between the two ubuntu's.
If the second ubuntu is up and running well,you will use in most cases this one,and no more the 'old' one.
So when the next version comes out,you can install it on the 'old' 10GB partition.using the same swap and /home.

Filesystem.
Windows NTFS
Ubuntu system / ext3
/home ext3
Data NTFS
swap swap

Personally, I think 100GB for /home is a bit of an overkill so I might only make it 50GB. I also only plan on only making one 10GB logical partition in the extended partition.

---

### Post by ChrisUK on 2009-10-29
> **MrSnowmiss said:**
> From what I have heard, set the swap to double your RAM or to 2GB, whichever is the most. So 6GB could be too much. But some other people might get you more info on that.
For the rest it seems a good setup (from what I recall, haven't been using windows since a year now ;))

Thanks. 
Do you know how big the /home partition should be just to store all of my settings?

---

### Post by ChrisUK on 2009-10-29
Ok, I'm trying to sort the partitions out now and I'm stuck.

I'm in Ubuntu using the live CD and trying to use GParted to create these partitions.
The problem I have is that I can only have 3 primary partitions and I'm not sure which ones should be primary and how the extended partitions work.

Can someone explain exactly how to create the above setup using GParted?
I know how to resize, etc. and I have already resized my Windows NTFS partition to 60GB but I don't know what order they need to go in and which ones need to be primary, etc.

---

### Post by ChrisUK on 2009-10-29
Nevermind, I think I've sorted it out now.

It currently looks like this;

1. Logical - NTFS (Windows, 60GB)
2. Logical - NTFS (/Shared data, 500GB)
3. Logical - EXT4 (/, 20GB)
4. Extended.
5. Logical - EXT4 (/Home, 6GB)
6. Logical - linux-swap (4GB)

---

### Post by NTHQ on 2009-10-30
How is it working for you? Do you have enough space for all your applications in both Windows and Ubuntu?
I haven't tried it myself yet. Didn't have time. Probably will get on it tonight or over the weekend. :)

---

### Post by ST3ALTHPSYCH0 on 2009-10-30
The only problem I might see with that setup is that I have nearly 90 GB full in my Win7 partition due to the programs I have installed. You could direct your programs to install in your shared space if storage become a problem, but I'd recommend just starting with a 100 Gb Windows partition. Also, I have an Ubuntu install with multiple users and some extras installed that only takes up a little over 5 Gb (and it's a 9.04 that's been upgraded to 9.10, I think that takes p a touch more space).
You might consider storing all save files into the NTFS shared space that way if you're in Windows and need to access an Ubuntu file (for instance an OO document) you have that ability. That will also allow you to minimize your dedicated Ubuntu storage, and puts your stored files on another partition which is a big help when it comes time for new version of OSes.
Just my $.02, I'm new to Ubuntu and still use Windows as my primary, so I may not have the best advice here.

---

### Post by zalberico on 2009-10-30
Windows Vista (NTFS) - 60GB

Shared Data - Don't need a partition, ubuntu can read and write to your NTFS windows partition

Ubuntu (EXT3) root partition: 10GB - 15GB

Swap (EXT3) 4.5GB

/Home - (EXT3) Everything else.

Reasoning...
15GB for root is generous and you won't have to worry about using all the space for a personal system.


EXT3 because it's rock solid and EXT4 can have some minor issues/bugs you're not going to want to worry about.

4.5GB for swap will allow your computer to hibernate if you so choose.  (You need the amount you have in RAM in swap in order to hibernate).  If you don't care about hibernating I'd go with 2GB Swap since your amount of RAM means you'll rarely use it otherwise.

Everything else for home because this is where all of your personal data is stored.

---

### Post by ChrisUK on 2009-10-30
> **NTHQ said:**
> How is it working for you? Do you have enough space for all your applications in both Windows and Ubuntu?
I haven't tried it myself yet. Didn't have time. Probably will get on it tonight or over the weekend. :)

It's working really well thanks. I did it all last night (I was up until 2am! :popcorn:) 

I saved roughly 60GB for Windows and 20GB for Ubuntu which I think will be more than enough. Windows so far has used only 13GB and I have installed quite a few of the applications that I will be using already.
Ubuntu has only used 3GB! which is far less than I expected. I might resize it to 15GB because 20GB is a bit overkill. 
I've left around 500GB for the Shared Data which is where all my music, movies, pics and documents are stored. It's good because both Windows and Ubuntu immediately mounted the Shared Data and I simply transferred all of my backed up data from my external hard drive over to the partition. Now I can easily access it from both OS's.

All in all it's worked out really well so far and I'm loving Ubuntu so much that I haven't even booted into Windows all day.
I think I will use Ubuntu as my main OS and only use Windows for photo editing with Adobe Lightroom, etc.

> **ST3ALTHPSYCH0 said:**
> The only problem I might see with that setup is that I have nearly 90 GB full in my Win7 partition due to the programs I have installed. You could direct your programs to install in your shared space if storage become a problem, but I'd recommend just starting with a 100 Gb Windows partition. Also, I have an Ubuntu install with multiple users and some extras installed that only takes up a little over 5 Gb (and it's a 9.04 that's been upgraded to 9.10, I think that takes p a touch more space).
You might consider storing all save files into the NTFS shared space that way if you're in Windows and need to access an Ubuntu file (for instance an OO document) you have that ability. That will also allow you to minimize your dedicated Ubuntu storage, and puts your stored files on another partition which is a big help when it comes time for new version of OSes.
Just my $.02, I'm new to Ubuntu and still use Windows as my primary, so I may not have the best advice here.

Thanks. I think 60GB will be enough for me because I've already installed most of my programs and I think it's only used around 15GB. I'll probably be using Ubuntu as my main OS now too.
I think my Ubuntu space is a bit overkill at 20GB as I've only used 3GB so far. I might resize it later but I don't want to wreck anything.


> **zman14321 said:**
> Windows Vista (NTFS) - 60GB

Shared Data - Don't need a partition, ubuntu can read and write to your NTFS windows partition

Ubuntu (EXT3) root partition: 10GB - 15GB

Swap (EXT3) 4.5GB

/Home - (EXT3) Everything else.

Reasoning...
15GB for root is generous and you won't have to worry about using all the space for a personal system.


EXT3 because it's rock solid and EXT4 can have some minor issues/bugs you're not going to want to worry about.

4.5GB for swap will allow your computer to hibernate if you so choose.  (You need the amount you have in RAM in swap in order to hibernate).  If you don't care about hibernating I'd go with 2GB Swap since your amount of RAM means you'll rarely use it otherwise.

Everything else for home because this is where all of your personal data is stored.

I'd prefer to keep my important data on a separate partition which is why I made the separate shared data partition. This is also good when I want to reinstall/upgrade Windows because I won't lose all of my data.
I've already gone with ETX4 so it's a bit late now! :( What are the bugs with ETX4? It's been running OK so far.

So what is /home exactly? Is it just where my documents, pictures, etc. are meant to be stored? Since I store all of my documents on the Shared Data partition it's not really using anything.
I left 6GB space for my /home partition and so far it's used just 270MB but I haven't put anything in there yet... Is that settings or something?

---

### Post by ST3ALTHPSYCH0 on 2009-10-30
I've run ext4 since day of my jaunty experience with no ill effects. Also, karmic is ext4 native. I think that worst bugs were worked out long ago, but I could be incorrect.

---

