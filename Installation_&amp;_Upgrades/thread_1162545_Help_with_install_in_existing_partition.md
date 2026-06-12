---
title: "Help with install in existing partition"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by babllano on 2009-05-17
I am trying to install Ubuntu 9.04 in an existing partition and need some help. I searched the forums and thought I was ready but during the install I found questions. I want to try Ubunto while also running windows. I set up my computer with 3 partitions, one with Windows Vista, one with nothing installed and the other I use for my documents. All are formatted with NTFS. I have now downloaded Ubuntu and want to install it on the empty partition, it's size is 15GB. When I run the CD it asks how to choose the partition and I choose manual. Then it asks to prepare partitions and this is where I am confused. It shows a list; /dev/sda, /dev/sda1/, /dev/sda2, and /dev/sda3. Sda1 is where Windows is installed, sda2 is the unused, and sda3 is the documents partition. I need step by step info on how to prepare the sda2 and /dev/sda partition. Thanks in advance.

---

### Post by zvacet on 2009-05-17
I hope you will find what you need [here.]("http://mywebsite.bigpond.net.au/dfelderh/p23.html")

---

### Post by presence1960 on 2009-05-17
The simplest way is to choose manual option when you get to the partitioner screen. Highlight sda2 and click Edit button. Set filesystem to ext 4 or ext 3. Ext 4 is new but is way fast compared to ext 3. Choose partition type: primary or extended. Set mountpoint to "/". Then you are ready to go.
Follow the rest of the screens and you will soon be using Ubuntu.

---

### Post by shaloken on 2009-05-17
I don't know the installer of 9.04 but with my 7.10, 
there is an option : assisted, it takes the entire partition, 
you just need to tell him what the partition to use and he say what kind of os there is on each partition. 
Seriously, I didn't read all the site web you posted babllano, but I saw the image and I saw that there is an option almost like mine in 7.10 (with the name of the os)
like that you can see which partition there is nothing on it.

---

### Post by babllano on 2009-05-17
presence1960 -- your response looks like the help I need. What is;  Choose partition type: primary or extended

---

### Post by presence1960 on 2009-05-17
> **babllano said:**
> presence1960 -- your response looks like the help I need. What is;  Choose partition type: primary or extended

it is on the screen after you click edit. as long as you don't have 4 primary partitions on your hard disk you can choose primary. The other option I believe is logical, not extended. You would use this option if the partition would put you over 4 partitions on that disk. Which I believe it wont from what you said. You should wind up with 4 : windows, ubuntu, data and swap once Ubuntu completes the install.

P.S. I would create a swap partition, unless you have a lot of ram and don't intend on using suspend or hibernate. If you want to utilize them your swap should be at least equal to your RAM.

---

### Post by babllano on 2009-05-18
I will give the install another try tonight. One other question, when I am editing the partition, how do I set up a swap file? The existing partition I want to use for Ubuntu is 15 GB and my RAM is 4 GB. Will it be OK to use 4 GB of this partition for a swap file? Thanks, again.

---

### Post by presence1960 on 2009-05-18
> **babllano said:**
> I will give the install another try tonight. One other question, when I am editing the partition, how do I set up a swap file? The existing partition I want to use for Ubuntu is 15 GB and my RAM is 4 GB. Will it be OK to use 4 GB of this partition for a swap file? Thanks, again.

You can go two ways with this. 1) Boot the Ubuntu Live CD and use partition editor or boot the gparted Live CD. Delete the 15Gb partition and create 2 partitions from the resulting space. 4096 MB for use as swap and the remaining 11264 MB for use as / for Ubuntu. Now your partitions are set up prior to install. Install from Ubuntu live CD and choose manual at the partitioner. Same instructions for the root (Ubuntu) partition as given in above post (highlight partition and click Edit). When you get to the swap partition highlight it and click Edit partition. Set it as swap. then you'll be good to go for the install..

2) Install from Live CD, at partitioner screen choose manual, highlight the 15 GB partition and click delete. Highlight the resulting free space and click New partition. Set the size to 4096 MB and set the partition as swap. When that is complete highlight the remaining free space (should be 11264 MB) and Click new partition, set that up as "/", set the file type as ext 3 or ext 4 and mountpoint to "/". Proceed with the install. 

Either method will produce the same results.

---

