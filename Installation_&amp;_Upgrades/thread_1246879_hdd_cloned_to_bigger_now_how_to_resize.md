---
title: "hdd cloned to bigger now how to resize???"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by stinger30au on 2009-08-22
g'day,

i have got an 80 gig ide hdd i have setup with a dual boot of windows and ubuntu

it works fine

i have cloned to it a new 300 gig hdd

i used g4l - ghost for linux boot cd and cloned one hdd to the other

[http://sourceforge.net/projects/g4l/](http://sourceforge.net/projects/g4l/)

i have removed the 80 gig hdd and put in the 300 gig and its working fine, infact i have booted up windows and shutdown and booted up ubuntu and its working like a champ, typing this using ubuntu now

so far , so good

i have attached a screen shot of gparted i installed to the ubuntu 9.04 install.

as you can see there is 223 meg of free space kicking round.
id like to split this up a bit between windows and ubuntu

ideally id like to give about 100 gig each to each o/s, but how the heck do it do it???

any ideas???

---

### Post by Mark Phelps on 2009-08-22
You would basically have to do the following:
1) Move the extended partition 100GB to the right to make room to the left to expand the NTFS partition
2) Inside the extended partition, do the following:
2a) move swap to the right
2b) resize the Ext3 partition to take up the unallocated space

I'm assuming you're running Window 7 (since you have a 100MB NTFS boot partition), or if not, Windows Vista.  Either way, use the Windows Disk Management tool to then resize the NTFS partition to take up the unallocated space next to the extended partition.

That should take care of it.

---

### Post by stinger30au on 2009-08-22
windows 7 rc im using

experimenting with dual boot and partition resizeing

i will try your suggestion in morning.

i have done some googling on the topic as well

i have read i can use a knoppix live cd to do ti with as well

it has a program in it called 

qtparted

supposed to be similar in nature to partition magic and it will do the same thing

its still d/l knoppix

i will worry about it in morning when i wake up, off for some shut eye

thanks for the tip

---

### Post by Mark Phelps on 2009-08-22
> **stinger30au said:**
> windows 7 rc im using
That's what I thought.
> i have read i can use a knoppix live cd to do ti with as well it has a program in it called qtparted supposed to be similar in nature to partition magic and it will do the same thing
Don't use that to resize the Windows 7 partition; use the Disk Management tool inside Win7 instead.

---

### Post by louieb on 2009-08-22
Just a thought. I'm big on keeping my data in a different partition from my OS.  40GB for Win and 30GB for Ubuntu is more that enough. 
To create a large data partition resize extended partition sda3  to take up all the unallocated space.  (the space will still show to be unallocated) Then create a new logical partition, its fine to format it with the NTFS file-system. Put your music, documents, whatever there. Now you have one place to backup and if you need to reinstall one of your OS - the data is out of the way.


BTW: Qtparted or Gparted - use the program **parted** just different front ends. And will work fine for adding a new data partition.

---

### Post by stinger30au on 2009-08-22
louieb thanks for the tip. good idea. i might even try that too

---

### Post by stinger30au on 2009-08-23
> **Mark Phelps said:**
> You would basically have to do the following:
1) Move the extended partition 100GB to the right to make room to the left to expand the NTFS partition
2) Inside the extended partition, do the following:
2a) move swap to the right
2b) resize the Ext3 partition to take up the unallocated space

I'm assuming you're running Window 7 (since you have a 100MB NTFS boot partition), or if not, Windows Vista.  Either way, use the Windows Disk Management tool to then resize the NTFS partition to take up the unallocated space next to the extended partition.

That should take care of it.


Try as i might i could not get this to happen.
so i ended up cutting the spare space in half. have half to ntfs the other half to ext3 and its all good now

thanks guys for the feedback

in the long run i think it will work out better like this. make life easier come upgrade or s/w reinstall time

---

