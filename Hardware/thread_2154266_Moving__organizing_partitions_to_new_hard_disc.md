---
title: "Moving / organizing partitions to new hard disc"
date: 2013-06-14
forum: Hardware
---

### Post by scottmay on 2013-06-14
Hi there.  I currently have a disc in my machine with Windows and Ubuntu on it.  I want to migrate to a new disc, and I only want to bring Ubuntu along.  So what's the "best" way to organize my new space.  New space being 1TB.

I'm leaning towards the following:
boot partition  (500MB)
swap partition (12GB = equal to RAM)
/         (450 GB or so)
/home (450GB or so)

I intend do "dd" stuff across, but currently my "/" and "/home" partitions are one and the same...

Any advise?  Splitting "/home" from "/"?  Getting grub onto boot?

I'm pretty conforable with linux generally but I want to do this safely.

Thanks!

---

### Post by Cheesemill on 2013-06-14
Unless you have a good reason for a seperate /boot partition then there is no need to have one, it can just cause issues later on.

450GB is massive for a root partition, I always have lots of software installed on my Ubuntu installations and I've never had a root partition use more than 30GB.

With 12GB of RAM you don't need any swap at all unless you're planning to hibernate your machine, in which case you will need 12GB of swap. But the time it would take to copy 12GB of data to and from your HD to hibernate would probably be longer than the time it would take to boot your machine normally so I wouldn't bother.

I'd probably suggest just having 50GB for / and the rest for /home.

Instead of using dd I'd suggest to a freash installation onto your new drive then just copying over the contents of your old /home directory.

---

### Post by oldfred on 2013-06-14
+1 on Cheesemill's suggestions.

dd is size for size copy, so you would then have to do major resizing later. You also then have the issues of duplicate UUIDs which you have to reconfigure.

If dual booting with Windows you may want a shared NTFS data partition for much of your data?

I used a shared NTFS data partition with my XP install and had Firefox & Thunderbird profiles in it and all photos. So I could use Picasa from both installs. I still have NTFS partition as I have yet to reconfigure as I do not boot XP any more, but now have most data and all new data goes into Linux formatted data partition.

I also like to have space for a couple more 25GB / (root) partitions to be able to test another install or next version.

If you partition in advance and copy /home in advance then do the install including the new /home everything will be set up. You will have to reinstall all your apps but can easily export a list with dpkg and reimport list to download them.

You only have to do the copy function:
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

