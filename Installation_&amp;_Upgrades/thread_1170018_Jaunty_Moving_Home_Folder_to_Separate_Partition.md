---
title: "Jaunty: Moving Home Folder to Separate Partition?"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by Format C on 2009-05-25
Hey everyone, I am trying to move my home folder to a new partition, so I have the ability to reinstall as needed without losing data.  In addition, I have formatted it as ntfs so my Windows install can use it too (for work/school - I need to use powerpoint and a few other programs).  However, I have tried to move the folder based on [this guide](http://www.psychocats.net/ubuntu/separatehome), and I cannot get it to work.  My problem is, it will not let me mount the ubuntu partition (sda1) as /old, as it will not create a new directory called old.  I got many more errors after trying to continue, I presume because it cannot find the /old I need.

Sorry in advance for my limited terminal knowledge.

Thanks,
Greg

---

### Post by whoop on 2009-05-25
What error do you get when you enter: sudo mkdir /old

---

### Post by merlinus on 2009-05-25
Linux does not run on ntfs.  You can use this tool to read and write from windows to linux partitions:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Format C on 2009-05-25
mkdir: cannot create directory `/old': File exists

I went to /old in Nautilus and it shows no files inside.  Should I try to delete it?

Also, I am not trying to run ubuntu on ntfs, just the home folder.  This is possible, right?  Because I can go mount my windows volume right now and see all its contents from within ubuntu.

Thanks,
Greg

---

### Post by presence1960 on 2009-05-25
> **Format C said:**
> mkdir: cannot create directory `/old': File exists

I went to /old in Nautilus and it shows no files inside.  Should I try to delete it?

Also, I am not trying to run ubuntu on ntfs, just the home folder.  This is possible, right?  Because I can go mount my windows volume right now and see all its contents from within ubuntu.

Thanks,
Greg

As far as I know /home can not be NTFS as it is a linux partition. If I am incorrect let me know.

P.S. You said you followed the guide on pychocats. It explicitly says to make the /home partition ext 3 (or ext3 or ext4 in Jaunty is understood)

---

### Post by merlinus on 2009-05-25
your linux /home needs to be on a linux filesystem, not ntfs.  it will not work properly otherwise.

perhaps it would be better to leave /home as is, and set up your ntfs partition for data that can be used by both linux and windows.  then if you want to install a new version of ubuntu, you can back up /home and reinstall it.

---

### Post by Format C on 2009-05-25
I see, I guess I should have payed more attention.  Thanks for all the assistance, and straightening me out.

---

### Post by presence1960 on 2009-05-25
> **Format C said:**
> I see, I guess I should have payed more attention.  Thanks for all the assistance, and straightening me out.

not so much straightening you out as lending a hand. Two or more sets of eyes are always better than one set.

---

### Post by Format C on 2009-05-25
Great, thank you.  It's nice to see a community that is so welcoming to new users.

Thanks again!

---

### Post by victor.cighir on 2009-05-27
Hi Format C.

I don't consider myself a linux expert. I've been using Ubuntu for 1.5 year or maybe 2. I don't remember. The community is indeed fantastic.

Here's a mix of ideas I found on the Internet : create a home partition. Install the home folder there for multiple OS (Ubuntu , Fedora and other share the same home folder - this is good to keep them in sync) and the configuration folders for different programs can be kept on yet another partition which can be ntfs. 

let's assume
/dev/sda1 - swap
/dev/sda2 - extended partition
/dev/sda3 - /home - it can be any other as well
/dev/sda4 - Ubuntu 32 bit install
/dev/sda5 - Ubuntu 64 bit install
/dev/sda6 - Fedora or other linux OS
/dev/sda7 - ntfs partition

Setup each OS, so that the home folder from each will be pointing to /dev/sda3
      Note: keep in mind that user name must be the same. I think the creation order of users also must be the same between OS's


Now, create .mozilla .thunderbird .skype .tomboy .xine and any other application folder on the NTFS partition    AND create symbolic links from the NTFS partition to the /home/user partition you want


Ubuntu 32 bit Firefox----------------Home folder and config---------Actual location
installed on /dev/sda4------------------>  /home/user1001  <-----link---- from NTFS partition .mozilla folder
Linux mint on /dev/sda5---------------> /home/user1001

One more thing you need to do. Add the ntfs partition in the /etc/fstab of each OS so that it will be mounted at boot. You can [see here how ]("http://ubuntuforums.org/showpost.php?p=6482350&postcount=7")to do that.

Please, anybody correct me if I'm wrong....

Have a great day everyone!

---

### Post by Format C on 2009-05-28
Hi Victor, That indeed looks like a good setup.  I will definitely give that a shot.

Thanks,
Greg

---

