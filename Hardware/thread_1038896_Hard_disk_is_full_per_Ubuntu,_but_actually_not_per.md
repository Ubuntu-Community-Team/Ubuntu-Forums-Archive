---
title: "Hard disk is full per Ubuntu, but actually not per Windows"
date: 2009-01-14
forum: Hardware
---

### Post by shanmugamt on 2009-01-14
Hi, I am new to Ubuntu. I have a question on Memory Mgmt on Ubuntu.
I have three partition on my hard drive (Winodws 150 GB,Personal 150 GB,Ubuntu 10GB). Installed Ubuntu on the thrid partition.

When i check the memory usage from Windows Vista, it says 4.5GB is free. But on Ubuntu it says available disk space is 0 bytes and used disk space is 12.5GB. I dont understand how this is possible? When the hard disk parition total memory is 10GB, Ubuntu says it has occupied 12.5 GB. 

Per Ubuntu there is no disk space, I am seeing some weird things on my laptop.  I am unable to do Google search (from the default Google search next to the address bar). Unable to run any online vedios, as there is no space for download.. sometimes the system is unable to perform some simple operation like, opening multiple applications.

Can someone suggest me a solution for this? 
(for your information, while installing Ubuntu, i selected 6 GB space for Ubuntu installation)

---

### Post by melojo on 2009-01-14
memory usage and disk space are 2 different things.

To check hard disk space
open a terminal under the accessories menu and type the command below and post the output.

```

df -k

```

for memory

```

free

```

---

### Post by shanmugamt on 2009-01-14
Hi Melojo,
Here is the output: (I couldnt save in table format.. The first output is attached with this post. Please refer the attachement)
Me@ubuntu:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk

                       4421560   4110852     86100  98% /
tmpfs                  2022912         0   2022912   0% /lib/init/rw
varrun                 2022912       108   2022804   1% /var/run
varlock                2022912         0   2022912   0% /var/lock
udev                   2022912      2840   2020072   1% /dev
tmpfs                  2022912       104   2022808   1% /dev/shm
/dev/sda2             10484732   5702104   4782628  55% /host
lrm                    2022912      2380   2020532   1% /lib/modules/2.6.27-9-generic/volatile
Me@ubuntu:~$ 


Me@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       4045828    1479336    2566492          0     382568     595124
-/+ buffers/cache:     501644    3544184
Swap:       390616          0     390616

Does this help you to figure out the problem?
Thanks,
Shan

---

### Post by scott_g on 2009-01-14
I believe the first command should have been 
```
d**f** -k
```

likely a typo...

---

### Post by shanmugamt on 2009-01-14
Thanks for the quick reply.. sorry about that. :) i found that typo.. pls refer the attachment..

---

### Post by scott_g on 2009-01-14
I'm likely not the best at reading that, but I think it shows you have filled your Ubuntu partition 98% of the way.  It also looks like you only have 4.5GB or so for your root partition; could be part of the reason.  Some suggestions are below; you may not be able to run all of them, if not, there's always the live-cd...

1. run: ```
sudo apt-get autoclean
```
2. run ```
sudo apt-get clean
```
3. run Applications>Accessories>Disk Usage Analyzer and look for large files you don't need
4. check to see if there are any files in /tmp

If the command line codes won't run, you could always start into the recovery mode (from grub).

The best long term solution in my opinion is to increase the size of your Ubuntu partition...  

Also, to see the usage of all the hard drives, go to System>Administration>System Monitor, and look for the 'File Systems' tab; it will list all your drives, and how much space is available.  For a graphical view, use the:

```
sudo apt-get install gparted
```

and then go to System>Administration>Partition editor and have some fun...

Note: all the above instructions assume you are using a gnome interface...

Also, how can Windows see your root partition?  Did you install the ext2 drivers?

Anyone else have ideas?

Scott

---

### Post by shanmugamt on 2009-01-14
Thanks for the quick response Scott.

With sudo apt-get autoclean and sudo apt-get clean, i have cleaned 10% of the root disk. Now the root disk is 88% occupied. Looks better now.
In your post you mentioned that, "It also looks like you only have 4.5GB or so for your root partition;" 
Is there any way i can increase the root partition? I have 10GB space on my Ubuntu partition.

Please refer the attachment. The system monitor explains the problem. Root, Boot and Host are all one and the same partition per Windows. But Ubuntu calculates differently. Does this explains?

Thanks again,
Shan

---

### Post by scott_g on 2009-01-15
Hmm; thats an odd partition setup... well at least different than mine...  Did you install Ubuntu using Wubi?  I've never used that so I may not be the best person to answer this question...  hopefully someone else can offer some advice.  I'd try installing gparted ```
sudo apt-get install gparted
``` and trying to re-size your partitions to give you more space.  Can you post a screenshot of what gparted looks like?  It does look like you gave Ubuntu 10gb, yet your root partition is only showing 4.2gb; very odd...  

May also want to take a look at: [http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234) it deals with Wubi...  perhaps this thread should be moved there?

Sorry I can't be of much help...
Scott

---

### Post by shanmugamt on 2009-01-16
Yep! I installed with Wubi.
Please refer attached GParted screenshot. I am seeing 1 MB free space in between my three partitions. Is this normal? when i select any partition, I m not getting the resize/move option enabled. Any idea??

Thanks,
Shan

---

### Post by scott_g on 2009-01-17
Hmm; t'is a tricky one....

I don't have very much experience with Wubi (none at all actually...); hopefully someone else can add some information.  I believe the 1MB free space is fairly normal; nothing to worry about at any rate.  You are likely not getting the re-size options as the drives are mounted; they must first be unmounted before you can perform any operations on them.  Unfortunately, it shows you have a 10GB partition, but your / partition is only 4.2GB.  I'm not sure how to increase that size, but: [http://ubuntuforums.org/archive/index.php/t-505628.html](http://ubuntuforums.org/archive/index.php/t-505628.html) looked promising.  Sorry I can't be much more help.

Perhaps someone else knows?
Scott

---

