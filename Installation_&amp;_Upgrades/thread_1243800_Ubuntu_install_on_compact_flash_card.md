---
title: "Ubuntu install on compact flash card"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by vishnumrao on 2009-08-18
I am thinking of installing Jaunty on 8 GB CF card on the nettop with a dual core atom processor. 

These are the links to the CF card and the nettop: 

[http://www.frys.com/product/5669231?site=sr:SEARCH:MAIN_RSLT_PG](http://www.frys.com/product/5669231?site=sr:SEARCH:MAIN_RSLT_PG)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167037)

I am  installing to CF because this machine heats up fast(hdd sits right over the fanless heatsink) and moreover its primary use is going to be some light web browsing and skype! 

Question: 

Is it ok to use ext4 filesystem. Also I read about having to disable swap. I have only 1 Gb RAM on this system.

Even with swap disabled, is the CF card going to withstand the repeated read/write cycles of an OS, since ext3/ext4 are journaled file systemd? 

Has anyone tried installing to CF cards? Can you post your experience?

---

### Post by dlmarti on 2009-08-18
Installing on a CF card is the same as a HD, the OS doesn't know the difference.
If your just doing this for fun, go ahead and use any file system.  If this is for work, then ext*anything on a flash is not acceptable, unless you RO the filesystem.

I use YAFFS instead of ext*, on all my NAND chips. 
I use RO filesystem (ext) for my CF cards (although I don't recommened CF cards for a production environment).

---

### Post by stinger30au on 2009-08-18
i have used 16 gig flash card to install to
i used a flash to ide convertor and the pc thought it was a 16 gig hdd

just put it in the desktop pc and loader up with ubuntu and off u go

run what ever file system u like

---

### Post by vishnumrao on 2009-08-18
I understand the CF card will be detected just like a HDD.(cos it uses the same IDE connection pins, just smaller).

My question is: Will installing an OS kill the CF card! Do I have to take any other precautions besides disabling swap?


@dlmarti: What is "RO"? Is there YAFFS support for Jaunty? I mean can I choose it during the install?

@stinger30au: I don't need the convertor. My mobo detects the CF card as a hdd.

---

### Post by Mighty_Joe on 2009-08-19
> **vishnumrao said:**
> My question is: Will installing an OS kill the CF card! Do I have to take any other precautions besides disabling swap?


Probably not.  Flash memory will wear out, but it will take more wear [than some think]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html") (yes, I know that's a USB flash drive, but the principal is the same).
I posted some links in [this thread]("http://ubuntuforums.org/showthread.php?t=1193680") to some install and configuration instructions I used to put Ubuntu on a flash drive. They contain some optimizations for running on flash memory.

---

### Post by dlmarti on 2009-08-19
> **vishnumrao said:**
> I understand the CF card will be detected just like a HDD.(cos it uses the same IDE connection pins, just smaller).

My question is: Will installing an OS kill the CF card! Do I have to take any other precautions besides disabling swap?


@dlmarti: What is "RO"? Is there YAFFS support for Jaunty? I mean can I choose it during the install?


What I meant by RO is marking the partition on the CF card as read-only, meaning it can't be modified.  This is how I ship my Linux-CF-based products, or at least how I used to.  I've switched to NAND flash with a YAFFS based solution.

For a normal desktop switching to a read-only partition would be a horrible inconvenience.  The state of one of my products NEVER changes, meaning no one is installing software on them daily.

For my best guess: If you install Ubuntu on a CF card using a ext2/3 filesystem you will be happy at least for a year or so.  Eventually your read/write times will become excessive and after a while the card will just fail.  This assumes you are using the box as  a daily desktop machine.

If this is going to be a machine you only occasionally use, the CF card will probably outlast your interest in the box.

---

### Post by quietplease on 2010-02-11
> **vishnumrao said:**
> I understand the CF card will be detected just like a HDD.(cos it uses the same IDE connection pins, just smaller).

My question is: Will installing an OS kill the CF card! Do I have to take any other precautions besides disabling swap?


I have been using CF cards with Xubuntu for the past two years. 9.10 seems to kill the CF cards. With two cards I started getting I/O errors soon after upgrading to 9.10. 

9.04 seems fine. No swap installed. XFS filesystem.

---

