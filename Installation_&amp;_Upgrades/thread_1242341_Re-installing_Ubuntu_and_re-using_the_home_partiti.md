---
title: "Re-installing Ubuntu and re-using the /home partition"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by Inferiority Complex on 2009-08-17
Having been playing around with Linux for about 15 years, I finally 'upgraded' my PC from Windows to Ubuntu.  I'd been running a dual-boot scenario for a while and I've put a small Windows install onto the disk again but only to run games what I can't get working under Wine.

Anyway, I created /, swap and a /home partition but couldn't help wondering how this will work for a re-install...

If thing ever go wrong, I can easily deal with a re-install but my question was about the files in the /home partition.

When I installed, I created my username e.g. "user1".  When I re-install, if I create the same user "user1", will all my files be sitting in place ready to be used again or do I have to perform some other ritual or incantation?

(I get the feeling that the command line will be mentioned...  Looking forward to any answers the clever folks here can provide.)

---

### Post by donato roque on 2009-08-17
The answer is a simple yes.  
I also have a separate partition for /home and i re-install using my live cd of ubuntu 9.04.  Anyway amidst the installation you're going to be presented with your partitions.  Just mount your /home partition (remember which one ok?) before you finish the installation process.
The real job is updating your system to current usable state.  Takes hours due to my slow connection.

Good luck!

---

### Post by stlsaint on 2009-08-17
donato is right..you can easily re-use home...just dont format during isntall and mount again...also as for user integration yes that too should change over...as you will have you videos in videos folder as well as music etc...like you said your keeping home which has all that and you will be presented with an option during install to import external user profiles ie user1...

---

### Post by Inferiority Complex on 2009-08-17
> **stlsaint said:**
> ...you will be presented with an option during install to import external user profiles ie user1...

Thanks for the replies, guys.

When I re-install, am I able to specify the same username?
i.e. currently, the files might reside at **/home/user1** so can I specify "user1" as the default user in the installation "Who Are You" page?

---

### Post by presence1960 on 2009-08-17
when you get to the partitioner screen with all your disks & partitions highlight the /home partition, click edit. Set the parameters and set mount point to /home, **_But leave the format box unticked!!_** If you fail to do this you will be able to mount the partition after the install but it wont be as home. it will just be a data partition. You need to configure that partition during the install and tell it to be mounted as /home. This will then be a seamless integration for you. When you go to your user directory the "home partition" will be there.

---

