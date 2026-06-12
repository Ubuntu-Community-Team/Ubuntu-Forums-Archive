---
title: "Hard Drive Space"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by Adam_TechSupport on 2009-09-23
Hi All.

When I installed ubuntu on my laptop to duel boot I made the partition to small, so I can't install anything due to lack of space.

So, am I able to increase the partition size? Or do I have to delete the Ubuntu partition and re-install Ubuntu?

Thanks

Adam

---

### Post by presence1960 on 2009-09-23
well that depends on your setup. Why don't you go System > Administration > Partition Editor and post a screenshot of the disk with Ubuntu on it.

If you don't have Partition Editor installed open a terminal and run this command ```
sudo apt-get install gparted
```

After installation is complete you will find partition Editor where I said above.

---

### Post by Adam_TechSupport on 2009-09-24
It won't install, I get this message:

adam@adam-laptop:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate


Thanks

---

### Post by presence1960 on 2009-09-24
> **Adam_TechSupport said:**
> It won't install, I get this message:

adam@adam-laptop:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate


Thanks
then boot the Live CD and go System > Administration > Partition Editor.

---

### Post by Lars Noodén on 2009-09-24
The tool to resize is called parted.  It's situations like this that the GUI can be a liability.  It's also not so good to work on a live file system so you should boot to your install CD and use the partitioning tool there to resize so that you are not using the hard disk at the same time you are working on it. 

Alternately, you may wish to look at a self-contained, live CD for system administration.  [Finnix](http://www.finnix.org/) is one example
[http://www.finnix.org/](http://www.finnix.org/)

Or you can make your own live CD if that one is missing the one or two tools you can't live without.

---

### Post by Lars Noodén on 2009-09-24
[QUOTE=presence1960;7995128
If you don't have Partition Editor installed open a terminal and run this command [/QUOTE]

These two programs will give you output which can be cut and paste:

```
sudo parted  -l
df -h
```

Those will give you a list of all partitions and their sizes and how much space is free in the mounted partitions.  However, see my comment about the [live cd](http://ubuntuforums.org/showpost.php?p=8000997&postcount=5)

---

### Post by drs305 on 2009-09-24
> **Adam_TechSupport said:**
> Hi All.

When I installed ubuntu on my laptop to duel boot I made the partition to small, so I can't install anything due to lack of space.

So, am I able to increase the partition size? Or do I have to delete the Ubuntu partition and re-install Ubuntu?

Thanks

Adam

If you chose a "side by side" install and ended up with a partition of less than 3GB, the following guides will help you create a usable system. Even if that isn't the exact problem, the first link may prove useful.

You have a choice of expanding your Ubuntu system partition by taking space from another partition or reinstalling and taking an extra action in Step 4 (Partitioning) to create a larger Ubuntu partition.


EXPAND  /
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

2.5GB  INSTALL
[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271")

---

### Post by Adam_TechSupport on 2009-10-02
Ok attached is the screen shot of the disk partitioner. If need be can I just delete the partition Ubuntu is installed on and re-install it? There is nothing to loose.

---

### Post by dwinks on 2009-10-02
Boot to Windows and see if you can shrink the Windows partition there, as it's safer and faster.  If not, boot up with the live CD, delete the Ubuntu partition, and the swap partition, shrink the Windows partition by another GB or two, then reinstall as you did before.  Also, it's perfectly fine to use your windows partition as /home.

What will happen if you do that is this:  Your C drive will have another folder added to it so you will have C:\Windows C:\Documents and Settings C:\"Your Name" (from /home/your name), and all of your home data will be available in both OS.

---

### Post by urugTON on 2009-10-02
I see that you have a Windows installation of some sort. Either XP or Vista will resize the NTFS partition.  You currently have about 20 GB free. Were I in your situation, I'd go back to XP/Vista, defrag the C: drive (maybe twice?) and then ask Windows to resize its partition to say, 25 GB.  That will leave you with 10 GB for Ubuntu.  That's not a lot, but it will get you going as long as you're not planning to load up 10 years of photos.  :P

FWIW, there are a variety of open source tools that can be used to resize your partitions.  I have read reports that Vista can get unhappy about the resized partition - to the point of needing to use the Vista Recovery disk to correct the situation.  That means you'll need to reinstall Grub.  I have consistently used Vista to resize its partitions because of those reports.

Once you have the NTFS partition down to 25 GB, my advice would be to just reinstall Ubuntu from scratch rather than fool with resizing what you have.

---

### Post by Adam_TechSupport on 2009-10-04
Right, managed to get the partition sorted so I can atleast download and install stuff now, however, when i try to install Flash Player or Virtual Box I get the error attached, does this mean I'm downloading the incorrect version?

---

### Post by drs305 on 2009-10-04
What version of Ubuntu are you running and have you done an update since installing (sudo update-grub). Do you have libcurl3 installed? If not:
```

sudo apt-get update && sudo apt-get install libcurl3

```

The version of libcurl3 you have also may be too old. I'm using Karmic, and the version I have is 7.19.5. You need at least 7.16.2-1.  You can check the version you have installed by checking the version in Synaptic or running the following command:
```
sudo apt-cache show libcurl3
```

While in Synaptic you can check libcurl3 and see what the latest version available to your system is. Just find libcurl3 in the right pane and the installed and latest versions will be displayed.

---

### Post by Adam_TechSupport on 2009-10-04
Thanks for that, managed to get flash and virtual box installed after doing the updates you suggested and then realizing I had another 250 updates to do ](*,)

Next question, this may sound stupid but now I've installed virtual box, how do I access it. When installing apps are they supposed to appear in the Applications menu?

---

### Post by drs305 on 2009-10-04
Check the Applications, System Tools menu, or you can start it with:
```

VirtualBox

```


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

