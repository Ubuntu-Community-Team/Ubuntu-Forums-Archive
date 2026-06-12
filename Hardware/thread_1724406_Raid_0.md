---
title: "Raid 0"
date: 2011-04-08
forum: Hardware
---

### Post by KG4UJD on 2011-04-08
I am getting mixed info on installing ubuntu 10.10 on raid 0 what is the proper way of doing this?

---

### Post by ronparent on 2011-04-08
Are you speaking of a software raid or fakeraid? If you don't know you probably shouldn't be trying to use a raid. 

If you are using raid with Windows it is a fakeraid. Your 10.10 release probably needs a work around. You have to load the live cd and install kpartx. Once kpartx is installed to the session you can continue the session to install to a raid0 nornally.

---

### Post by KG4UJD on 2011-04-08
I am building my first system so no I don't know alot, but I learn a little more everyday.

I am using Gigabyte ga-880ga-ud3h MB it supports raid 0, 0+1,1,5

---

### Post by ronparent on 2011-04-08
A raid based on a MB chip set is generally known in linux (Ubuntu) circles as 'FakeRAID' 9I hate that term). I have found it reliable for my partitcular use but implementation in Ubuntu has been flaky. Although easier to set up than linux software raid both flavors of raid need some study to be able to use them successfully. Windows user particularly are drawn to the fakeraid because of its relative ease of use in the windows environment and have very little understanding of what their risks are.

Fakeraid is your only choice if you intend to share data partitions between side-by-side installs of Windows and Ubuntu. If you will have Ubuntu only the software raid is probably preferable if you know what you are doing. You need some understanding of what raid entails to properly setup and use either variety.

Some references for you:
Software raid - [http://ubuntuforums.org/showthread.php?t=408461&highlight=raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=raid)
More - [http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)
Partitioning in general - [https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

I haven't listed any fakeraid references because the ones I know of are out of date. But if you use fakeraid you need to be familiar on how to use dmraid. The syntaxes are a bit murky if you are not used to linux command lines but you do need 'man dmraid' (terminal command) to tell how to use it. Otherwise post your questions here. Good luck.

---

### Post by psusi on 2011-04-08
> **ronparent said:**
> Your 10.10 release probably needs a work around. You have to load the live cd and install kpartx. Once kpartx is installed to the session you can continue the session to install to a raid0 nornally.

You do not need to install kpartx to install Ubuntu.  Installing kpartx was a workaround in 10.04 to get gparted to see the fakeraid; the installer had no problem with it.

You should read [http://wiki.ubuntu.com/FakeRaidHowto](http://wiki.ubuntu.com/FakeRaidHowto) for more info on fakeraid.

---

### Post by ronparent on 2011-04-08
psusi - The problem wasn't fixed with the initial release of 10.10. I frankly don't know where it stands now. You are right that the problem wasn't with the installer seeing the fakeraid but with 10.04 in particular the installer could not format a fakeraid partition to install to it!

---

### Post by psusi on 2011-04-08
> **ronparent said:**
> psusi - The problem wasn't fixed with the initial release of 10.10. I frankly don't know where it stands now. You are right that the problem wasn't with the installer seeing the fakeraid but with 10.04 in particular the installer could not format a fakeraid partition to install to it!

There was a problem around alpha 2 or 3, but 10.10 final works just fine.  IIRC, 10.04 original had a problem but it was fixed in 10.04.1, and installing kpartx didn't help with it.

---

### Post by ronparent on 2011-04-08
We have differing experiences, but, that is not surprising. I tend to describe fakeraid support in Ubuntu as flaky.):P

---

### Post by psusi on 2011-04-08
> **ronparent said:**
> We have differing experiences, but, that is not surprising. I tend to describe fakeraid support in Ubuntu as flaky.):P

I'd agree, especially if you are talking about the redundant raid levels, but I've been trying to keep raid0 at least working since 2005 ;)

---

