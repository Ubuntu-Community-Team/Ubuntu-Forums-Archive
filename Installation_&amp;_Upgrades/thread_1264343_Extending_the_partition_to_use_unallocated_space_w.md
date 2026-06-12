---
title: "Extending the partition to use unallocated space while installation"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by kumarprabhatn on 2009-09-12
Hi there. I m new to ubuntu. I m dual booting my system with windows 7 and ubuntu 9.04. I have already installed windows 7 and now I want to install ubuntu. I have created a seperate partition of about 6GB for ubuntu. But I also have about 8GB unallocated space which I want to allocate it to ubuntu. Any idea how I can do that ? I wanted to know if there is anyway to extend the 6GB to 14GB using 8GB unallocated space, during installation. I tried everything. There are ways to shrink the volume but not extend it. Please help.

---

### Post by orionas on 2009-09-12
Hi,
 I haven't used the graphical installer to mess with partition sizes, so I can't help there. But why not just allocate another new partition at the 8GB empty space?
I would suggest to put your / partition at the 8GB and your /home at the 6GB space. Creating a separate /home partition is common practice.

---

### Post by oboedad55 on 2009-09-12
> **kumarprabhatn said:**
> Hi there. I m new to ubuntu. I m dual booting my system with windows 7 and ubuntu 9.04. I have already installed windows 7 and now I want to install ubuntu. I have created a seperate partition of about 6GB for ubuntu. But I also have about 8GB unallocated space which I want to allocate it to ubuntu. Any idea how I can do that ? I wanted to know if there is anyway to extend the 6GB to 14GB using 8GB unallocated space, during installation. I tried everything. There are ways to shrink the volume but not extend it. Please help.

Use the partition editor from the LiveCD or use PartedMagic, [http://partedmagic.com/](http://partedmagic.com/) which is a bootable CD with a partitioner on it. Then assuming the unallocated space is next to your Linux partition size away. It's pretty easy.

---

### Post by rob-ward on 2009-09-12
If the partitions are next to each other then you can merge them together to be a single partition, if not then it is a lot more difficult and I would say that you are better using both partitions but mounting the 6GB one as /home as already suggested.

---

### Post by hal10000 on 2009-09-12
If you post the output of [COLOR="Red"]sudo fdisk -l[/COLOR] it may be possible to tell you wether you can expand the partition.

---

### Post by kumarprabhatn on 2009-09-12
Ok.. thanks.. I guess I will try assign the 6GB to /home directory. I wanted to expand the volume because I will be installing heavy applications like VMware, Netbeans which require a lot of space. Assigning /home will be of help? By the way, by default which location do the packages from synaptic or by installing using a tar or using a deb get installed to ??

---

### Post by hal10000 on 2009-09-12
> By the way, by default which location do the packages from synaptic or by installing using a tar or using a deb get installed to ?
Packages installed by synaptic are always .deb files, but not every .deb file is made for ubuntu, it could also be for debian, knoppix or another debian-based distribution.

In linux you don't have separated "Program" directories for a given package

Software-packages usually consists of many kinds of different files (e.g. executable commands, libraries, configuration files etc.).

Executable commands usually reside in /bin, /usr/bin or /usr/local/bin

Libraries can be found in /lib, /usr/lib or /usr/local/lib

Configuration files are in /etc or /usr/local/etc if they configure things for your whole system or in your home-directory /home/yourname if they are user-specific

Variable parts of program packages can be found in the /var directory-tree (e.g. if you have installed a database-system like mysql, then the databases you create can be found in /var/lib/mysql/mysql/)

In synaptic you can see where the files reside, if you right-click on a package and choose properties--->installed files

For a beginner i would recomment not to install tar.gz or tar.bz2 zipped packages, in almost any case you can find an ubuntu package of the program. But if you have to, it's usually a good idea to separate them from the other ubuntu-packages by installing them under the /usr/local/ directory-tree.

If you want to know where a given command is installed, you can use 
[COLOR="Red"]which commandname[/COLOR] ,e.g. which nautilus and it will show you the path to the executable file

---

### Post by orionas on 2009-09-13
Hi,
 /home will help if you save the vmware virtual disks you create under /home/user/VMware or something like that. All your application files will be installed under /, (mostly /usr and /etc as already said) by the debian package management system.
For a thorower explanation, [take a look here.]("http://www.debianadmin.com/linux-directory-structure-overview.html")
Also, note that by default you will only have permissions to save files under your /home/user folder anyway.
If you manage to install so many apps that your / will become full, you can free space by removing the automaticly downloaded packages with the following command:
```
$ sudo apt-get clean
```

---

