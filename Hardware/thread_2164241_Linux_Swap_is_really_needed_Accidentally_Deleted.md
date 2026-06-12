---
title: "Linux Swap is really needed? Accidentally Deleted"
date: 2013-07-30
forum: Hardware
---

### Post by nachinew on 2013-07-30
[TABLE]
[TR]
[TD="class: postcell"]               My DELL laptop having 500 GB hard-disk, I plan to install  dual OS in it, So I re-size the disk using Gparted and my primary OS is  Ubuntu 12.10. While resizing my disk, its displays an error only four  primary partition u can partition size. Please find the below for screen  shot of my partition details.

  
[IMG]http://s21.postimg.org/kmhoq44xz/Screenshot_from_2013_07_31_06_08_11.png[/IMG]


  In additionally one partition with 8GB of Linux swap is already i  deleted accidentally so the disk is now possibly to re-sized for  creating a sda4 for another OS. Now when i boot my primary OS UBUNTU i  am facing a small error that "Uaaa-ssdds-------" is missing wait for  mounting automatically or S for Skip or M for manually mounting.

  How to solve this problem I i need to recreate a Linux Swap.

      
       

[TABLE="class: fw"]
[TR]
[TD="class: vt"][/TD]
[TD="class: post-signature owner"][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by SweetAurora on 2013-07-30
How much ram does your computer have? If it's 4GB or more, swap is meaningless as there is enough ram to run Linux with no problems. If so, just push s to skip mounting swap. BUT... If you have less than 4GB, tell us here and we can try to remedy the situation.

---

### Post by VMC on 2013-07-30
Why didn't create an extended partition for Linux, Swap?

You could create an extended partition at the end (7.4gb),and put a swap partition inside there.

Here's a picture of mine as an example. I have Windows 7, an NTFS partition, several Ext4's and a Swap inside the Extended partition:

[IMG]http://i.imgur.com/Kz7tP4K.png?1[/IMG]

---

### Post by nachinew on 2013-07-31
> **kitsuneinari78 said:**
> How much ram does your computer have? If it's 4GB or more, swap is meaningless as there is enough ram to run Linux with no problems. If so, just push s to skip mounting swap. BUT... If you have less than 4GB, tell us here and we can try to remedy the situation.

I am using 4GB RAM, But I need the solution for this, my friend also having same ubuntu but differ in RAM, Please suggest so that I can help him.

---

### Post by frankblero on 2013-07-31
I think that you don't need more than 4 Gb RAM. Don't worry about your swap partition deleted. For your friend, the same thing. If he has less than 4GB you should create a partition swap.

PS: I'm french so my English is a little bit.... catastrophical ;)

---

### Post by Yellow Pasque on 2013-07-31
Create an extended partition with the free space at the end of your disk, and then you can make a swap partition.
Your friend can make an extended partition too..

---

### Post by nachinew on 2013-07-31
> **frankblero said:**
> I think that you don't need more than 4 Gb RAM. Don't worry about your swap partition deleted. For your friend, the same thing. If he has less than 4GB you should create a partition swap.

PS: I'm french so my English is a little bit.... catastrophical ;)

Thanks friend

---

### Post by nachinew on 2013-07-31
> **Temüjin said:**
> Create an extended partition with the free space at the end of your disk, and then you can make a swap partition.
Your friend can make an extended partition too..

As u said I recommend my friend to create extended partition.
Thanks for your help

---

