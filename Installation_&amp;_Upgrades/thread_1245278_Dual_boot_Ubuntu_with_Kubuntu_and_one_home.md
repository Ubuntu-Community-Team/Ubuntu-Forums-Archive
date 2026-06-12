---
title: "Dual boot Ubuntu with Kubuntu and one /home"
date: 2009-08-20
forum: Installation &amp; Upgrades
---

### Post by timmynana on 2009-08-20
As someone who wants their cake to be able to eat it i would like to install Ubuntu alongside Kubuntu.

My laptop is frail and i've already had some installation issues (i think the cd drive is on the way out) so would like to leave Ubuntu on there just in case something does go wrong. I currently have;

1x1GB swap partition
1x12GB / (root)
1x7GB /home
2 x 50 GB NTFS doc partitions

I was thinking of resizing the 12GB down to 8 gb with a 4gb kubuntu parition.

Can;
1) I have 6 partitions
2) Can kubuntu use Ubuntu's home folder

Many thanks

---

### Post by presence1960 on 2009-08-20
> **timmynana said:**
> As someone who wants their cake to be able to eat it i would like to install Ubuntu alongside Kubuntu.

My laptop is frail and i've already had some installation issues (i think the cd drive is on the way out) so would like to leave Ubuntu on there just in case something does go wrong. I currently have;

1x1GB swap partition
1x12GB / (root)
1x7GB /home
2 x 50 GB NTFS doc partitions

I was thinking of resizing the 12GB down to 8 gb with a 4gb kubuntu parition.

Can;
1) I have 6 partitions
2) Can kubuntu use Ubuntu's home folder

Many thanks

You can only have 4 primary partitions per disk, but there is a way around the 4 partition limit. You can make one partition extended. Then you can create as many logical partitions inside the extended partition as the size you allotted for the extended partition will allow. You can only have one extended partition per disk.

Linux will boot from a logical partition, but windows has great difficulties booting from a logical partition, unless it is a windows created logical partition as in what happens when you have XP and install Vista to have 2 windows OSs. It is best to keep windows in a primary partition for dual boot with another OS.

For much more detailed info on partitioning see [here]("https://help.ubuntu.com/community/HowtoPartition")

**_It is not a wise idea to share /home between distros or versions of Linux_** Most of your config files are in /home. Ubuntu uses gnome and Kubuntu uses KDE. Both sets of config files will be in a shared /home and this will cause problems when running one or the other OS.

---

### Post by timmynana on 2009-08-20
Many thanks for the treply presence1960.
Do you think this set up is a possiblity?

1x1gb swap
1x6gb ubuntu /
1x 4gb ubuntu /home
1x10gb logical drive (split in to 1x6gb kubuntu /, 1x4gb kubuntu /home)
1x 99 gb ntfs (or can i keep these split?)

thanks again for the help

---

### Post by snowpine on 2009-08-20
Hi Timmynana, there is an easier way:

```
sudo apt-get install kubuntu-dekstop
```

Then, each time you log in, you can choose Sessions->KDE (for Kubuntu) or Sessions->Gnome (for Ubuntu).

The drawback of this method is that your menus might get a little crowded, as you'll have all the Ubuntu and Kubuntu apps in there. But it will save you a lot of hard drive space.

The other option of course is to install them separately and share a /home partition. This will work just fine as long as you use a different username for your Kubuntu account.

---

### Post by presence1960 on 2009-08-20
> 1x1gb swap
1x6gb ubuntu /
1x 4gb ubuntu /home
1x10gb logical drive (split in to 1x6gb kubuntu /, 1x4gb kubuntu /home)
1x 99 gb ntfs (or can i keep these split?)

You can't do it that way you have 5 partitions included the extended partition: swap, ubuntu /, ubuntu /home, extended & ntfs.

I would recommend this :

Extended partition with these logicals inside it:
swap
ubuntu /
ubuntu /home 
kubuntu /
kubuntu /home

and your NTFS as a primary partition. This will leave you room for 2 more primary partitions should the need arise. You can always grow your extended partition by freeing up space adjacent to it and then resizing. You can then add more logical partition(s) to the extended.

---

### Post by presence1960 on 2009-08-20
> **snowpine said:**
> Hi Timmynana, there is an easier way:

```
sudo apt-get install kubuntu-dekstop
```

Then, each time you log in, you can choose Sessions->KDE (for Kubuntu) or Sessions->Gnome (for Ubuntu).

The drawback of this method is that your menus might get a little crowded, as you'll have all the Ubuntu and Kubuntu apps in there. But it will save you a lot of hard drive space.

The other option of course is to install them separately and share a /home partition. This will work just fine as long as you use a different username for your Kubuntu account.

Funny i started typing that suggestion then reconsidered because I remember a friend who did that and you are right the menus were crowded.

But that is the beauty of Linux- there is usually more than one way to accomplish the same task. I guess the OP can choose which best suits his fancy. A far cry from another OS which shall remain nameless!

---

### Post by timmynana on 2009-08-21
Many thanks,
now have

Logical: (1x 1gb swap, 2x8gb root, 2x 6gb home)
2x 50gb ntfs.

Have to say while Kubuntu looks nice, alot of the programs and are easily accessible in ubuntu appear hidden - i guess thats the fun of linux, looking around and modifying till you get the system you want. The add/remove section in particular seems alot worse in kubuntu - why is there no simple list like in ubuntu - firefox, wine and VLC had to be installed via the terminal as add/remove didn't have them.

Anyway - thanks again for all the advice - solved.

---

### Post by presence1960 on 2009-08-21
> **timmynana said:**
> Many thanks,
now have

Logical: (1x 1gb swap, 2x8gb root, 2x 6gb home)
2x 50gb ntfs.

Have to say while Kubuntu looks nice, alot of the programs and are easily accessible in ubuntu appear hidden - i guess thats the fun of linux, looking around and modifying till you get the system you want. The add/remove section in particular seems alot worse in kubuntu - why is there no simple list like in ubuntu - firefox, wine and VLC had to be installed via the terminal as add/remove didn't have them.

Anyway - thanks again for all the advice - solved.

Great! Enjoy Ubuntu.

---

