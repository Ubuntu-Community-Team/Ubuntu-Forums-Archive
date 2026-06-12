---
title: "Ubuntu Reinstall Help"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by pyromanic123boom on 2009-03-18
Hey guys,

I'd like to clean up my system because of programs, files, etc. I used to do this with windows occasionally and it really helps.

Problem is, I've got about 105 GB in my /home folder. I only have one harddrive, so moving data isn't exactly an option. My harddrive is about 170 GB in space. I'm looking into buying a external hdd but that's not an option now because I don't have the money.

My question: how can I reinstall either hardy or intrepid without losing my /home folder? And how can I make easier to do this in the future? I've read about creating a seperate partition for /home specifically for this issue.

Any feedback would be great. I'm not really pressed for time here, just a laid back "clean up the computer" sort of deal. Thanks!

---

### Post by Partyboi2 on 2009-03-18
Moving your /home folder to its own partition would be the way to go.

---

### Post by pyromanic123boom on 2009-03-18
So you mean to say that I should resize my partition using a live cd, then transfer, then reinstall?

---

### Post by upchucky on 2009-03-18
yes to the partition solution of the home partition, and there is no real benefit to re-installing ubuntu. unless the original install was severely messed up, it is not like flaky windows that slowly self destructs.

---

### Post by Partyboi2 on 2009-03-18
In short yes. [[COLOR=Blue]Here[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") is a guide to moving your /home folder to its own partition.

---

### Post by pyromanic123boom on 2009-03-18
All right, sounds good. I'm sort of familiar with doing like operations, i.e., dual booting on the same hdd.

I'm just curious- how much space would you recommend for the /home partition? Since it won't be expanding, I want create it as *large* as possible.

---

### Post by upchucky on 2009-03-18
mine home is 120 gig, but i have tons of real estate, and other storage drives.

ubuntu core only needs about 10gig, i have given mine 25 gig, and i have 2 gig ram so i set my swap to 1gig, upon checking my swap, ubuntu does not use the swap at all, but it is nice to have it available especially if you have lots of room.

i also have a 120g usb drive to use to experiment with other flavors of linux.

so the answer is if you have lots of room use it, if not go for the minimums.

---

### Post by pyromanic123boom on 2009-03-18
Well here is my /dev/sda

-----------------------------------------------
partition_____filesystem____space_(total/used)
------------------------------------------------
/dev/sda1_____fat16_________47mb/9mb                             

/dev/sda2_____fat32_________3gb/2gb

/dev/sda3_____ext3__________226gb/123gb

/dev/sda4_____extended______3gb/0 

/dev/sda5_____swap__________3gb/0
-----------------------------------------------

I know #2 is the OS, but what is #1 used for?
Exactly what is #3? It's not just the home folder, is it?
I plan on keeping everything basically intact, just creating a /home partition that's as large as possible.

---

### Post by upchucky on 2009-03-18
download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh

```


it will tell u everything that is on the drive and how it is booted.

fat 16 looks like a maintenance partition created by the pc manufacturer, not sure about fat32, and ext3 is linux. extended looks like available storage, swap is linux swap.

dont need 3g for swap, usually half of system ramsize is good enough. 

only need 25g for linux core, and the rest of drive for home
download gparted live cd for redoing the partitions.

---

### Post by pyromanic123boom on 2009-03-19
Sweet, thanks. Yeah, I was looking into new computers, and at the same time wanted to make a switch to ubuntu. So I got a dell tower with ubuntu pre-installed. It looks like I'm just going to leave everything untouched except the linux-core, and resize it to about 20 gb, leaving about 200 gb for my home folder. Then I won't have to change anything with grub and whatever is located in sda1 and 2 will just remain alone. 

Thanks for the help! If I've got any more questions I'll ask them

---

