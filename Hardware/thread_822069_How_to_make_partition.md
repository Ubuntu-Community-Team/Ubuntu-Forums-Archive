---
title: "How to make partition ?"
date: 2008-06-07
forum: Hardware
---

### Post by secsud on 2008-06-07
Hi,

I have installed UBUNTU on a new 160 GB HD. Now I want to make partition into that, how can i do that ?

Early help will be appreciated.

Thanks in advance.
secsud

---

### Post by avtolle on 2008-06-07
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) is an excellent tutorial about creating a separate home partition after installation. The same techniques may be used to created other partitions, as the author indicates. Hope this is helpful.

---

### Post by Yuki_Nagato on 2008-06-07
The first thing you need is a way to partition the hard drive without actually using it.  We use GParted for this.

[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

Make yourself up a CD and then boot to it.  If you cannot get that to work, then get a Live CD of Ubuntu and boot to that instead.  If you are using the Live CD, go to System>Administration>Partition Disk.  The GParted tool is self-explanatory - if you can get it to run.

Once you have your partition editing program running, you must think before hand, how you want to butcher up your drive.  Since you already installed Ubuntu, there is no easy way for you to do neat /home and /usr mounting tricks, but for future installation, have a look at this.

[http://tldp.org/HOWTO/Partition/requirements.html#AEN493]("http://tldp.org/HOWTO/Partition/requirements.html#AEN493")

In fact, that whole website is an excellent resource for partition knowledge.

Whether or not you read that stuff now, you will need to sit down with pen and paper.  Map out what you need, and how much space to put things in.  If for example, you want to tack Windows on after the Linux, you might write this:

80g for Ubuntu
80g for Windows

Great.  Fire up your partitioning software, and you will see there is a bit more.  There is probably some amount of "swap" space that has been allotted (1g maybe) after your Ubuntu partition.  You will want to shrink the Ubuntu partition, but do not touch the swap space.  You should have Ubuntu (ext) space, Unallocated (?) space, and then the swap (swap) partition.  You will then turn (format) the unallocated (?) space into Windows (NTFS) space, filling your hard drive back up.

But that is an example.

---

