---
title: "installing opensuse on an existing ubuntu-winXP dual boot system"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by gourinath on 2009-10-26
Hi All,
Recently I switched to ubuntu/linux. It has been a transforming experience.:P
I have the following query:
__________________________________________________________________________________
Context of the query:
This question is about installing openSUSE 11.1 on a laptop, on which I already installed  ubuntu 9.04 and windowsXP. As of now, the dual boot works perfect. At the bootup, I can opt either of the five ubuntu versions and winXP.
---------------------------------------------------------------------------------------------------------------------------

Background information:
I installed ubuntu and winXP from scratch. First I installed ubuntu9.04 and then winXP. But before installing ubuntu, using the liveCD, I made five partitions on my 160 GB hard disk:
first partition- 20 GB with filesystem ext3 (on which I installed Ubuntu 9.04)
 second parition- 30 GB with filesystem NTFS (on which winXP is installed)
third - extended partition with two logical partitions: (1) 60 GB with filesystem ext3 (I installed this as home for ubuntu); (2)  5 GB (which I use as swap for ubuntu) 
forth partition- 30 GB (with filesystem ext3) (THIS partition is empty and I plan to install openSUSE 11.1 over it)
------------------------------------------------------------------------------------------------------------------------------
QUERIES:
I have liveCD of openSUSE 11.1 and would like to install it in the forth partition. Here are my questions:
Q1: Can I install openSUSE so that I can choose between ubuntu, winXP and openSUSE?
Q2: If I can, then can share the ubuntu home with the openSUSE linux?
Q3: If yes then please guide me how to do this?
_____________________________________________________________________________________

My previous experience:
1. I partition and installed ubuntu on a clean hard disk.
2. Then installed winXP
3. Edited the GRUB to get back my ubuntu
4. Edited menu.lst of ubuntu to add winXP.

I am a bit scared about installing another linux alongside the existing linux system.

Thanks
gourinath

---

### Post by zvacet on 2009-10-27
You can install Open suse on empty partition.If you want to use ubuntu grub then you will have to reinstall it following [this.]("http://ubuntuforums.org/showthread.php?t=224351")

Maybe same home for ubuntu and Open suse is not good idea because Ubuntu use deb and Open suse rpm so maybe you will have troubles with settings,but maybe someone else know better.

---

