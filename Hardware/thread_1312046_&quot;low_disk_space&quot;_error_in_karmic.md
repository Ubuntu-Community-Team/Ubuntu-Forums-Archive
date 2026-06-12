---
title: "&quot;low disk space&quot; error in karmic?"
date: 2009-11-02
forum: Hardware
---

### Post by kabanta on 2009-11-02
i have an ext3 partition called "Extra" mounted with many files on it. since upgrade to 9.10, i keep getting the following error window appearing on login:

   "Low Disk Space"
   Volume Extra has only 451 MB of free space!

The amount of free space available matches the results of "df -h":

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             158G  150G  449M 100% /Extra

but the math above seems VERY odd -- if i have used 150gb out of 158gb, there should be 8gb of free space available, not 450mb!

similarly, if i browse via the gui and select "properties" for the Extra partition, i get:

  Contents: 142.8 GB (some contents unreadable)
  Free space: 448.6 MB

suggesting there is about 6gb of free space

Gparted gives:

  Size: 160.14gb
  Used: 151.69gb
  Free: 8.44gb

Finally, if i use the "disk usage analyzer", the results are:

  Total filesystem capacity: 167.2gb
  Total filesystem usage: 153.7gb

which suggests that there is on the order of 13gb of free space.

i realize that calculating actual free space is difficult, and i am not quibblind about most of the differences above. however, i am concerned about the results that suggest i only have 450Mb of free space -- the difference between 450mb and, say, 10gb seems absurd.

is this a bug -- or are there "hidden files" that are somehow not included when calculating disk usage (but *are* included when calculating free space available)?

EDIT: i noticed that the "missing space" was roughly 5% of the total available -- and that reminded me that ext3 sets aside space that is only usable by root. some googling confirms that linux sets aside 5% of available space. *it is a total mystery to me why NONE of the various gui interfaces that show available disk space actually indicate this.*

This percentage can by modified with **tune2fs**. There is a clear summary of the space allocation and the use of **tune2fs** [here]("http://www.unixtutorial.org/commands/tune2fs/")

---

