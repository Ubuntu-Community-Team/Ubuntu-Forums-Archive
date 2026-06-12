---
title: "Partition for multiple distros"
date: 2008-08-22
forum: General Help
---

### Post by intense.ego on 2008-08-22
I am planning to install arch linux and, according to their installation guide, I will need: 

> ~12GB root (/) partition, ~6GB /var, 1GB swap, and a /home containing the remaining disk space

I have about 17gb free, plus i can take off a few GB from the ubuntu /root (I only use 3 out of 9GB). 

In the example they give on the guide ([http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)), the /home is 140gb, so they expect you to have a large /home and what I have available seems like the absolute minimum.

So, I need help.

First of all, any tips on taking off a few more gigs from my /home on ubuntu right now?

Second of all, what would be my best set up to be able to dual boot arch and ubuntu? is it possible for the two distros to share a swap? surely they could share a data partition (which would ease the load on both /home s)?

Current set up:

TOTAL AVAILABLE: +/- 54 GB (60 million bytes)
Windows - 6 GB/6 GB
Ubuntu /home:  19 GB /38 GB (only 18 free)
Ubuntu /: 3.3 GB/ 9 GB
Swap: 1.1GB

One more thing, please note I am using Gutsy Gibbon, and when I install Hardy or Intrepid, that root partition might get bigger (i am just assuming, no evidence).

Thank you in advance

---

### Post by Patb on 2008-08-22
There are quite a few questions here. To answer just two:

You can share one swap partition for different distros provided you don't want to use hibernation. 

You are best to have different home **directories** for each distro.  These may be different users on one /home partition.  There are too many settings and files which will create conflicts if you have one home partition with the same user name for different distros. 

Hope this helps.  Cheers, Pat.

---

### Post by mb_webguy on 2008-08-22
Ditto Patb.

Also, if you have multiple OSes or distros on one computer, it's really best to have separate small (no more than 2GB) /home partitions for each distro (or else one /home partition with a different username for each distro), and a separate partition for your files.  The most basic purpose of the /home directory is to store your local configuration files and settings.  Since those are basically all text files, you can get away with a very small /home directory as long as you store all of your files somewhere else.

Given your current setup, however, it may make more sense to use your current /home partition, but use a different username on the new distro.

Also, it's not really necessary to have a separate /var directory.  While it can be useful, particularly if you're running a webserver (since the default MySQL data directory and Apache web root are both in the /var directory), it's not necessary for a desktop system.

---

### Post by intense.ego on 2008-08-23
> **mb_webguy said:**
> Ditto Patb.

Also, if you have multiple OSes or distros on one computer, it's really best to have separate small (no more than 2GB) /home partitions for each distro (or else one /home partition with a different username for each distro), and a separate partition for your files.  The most basic purpose of the /home directory is to store your local configuration files and settings.  Since those are basically all text files, you can get away with a very small /home directory as long as you store all of your files somewhere else.

Given your current setup, however, it may make more sense to use your current /home partition, but use a different username on the new distro.

Also, it's not really necessary to have a separate /var directory.  While it can be useful, particularly if you're running a webserver (since the default MySQL data directory and Apache web root are both in the /var directory), it's not necessary for a desktop system.

So, a different username would avoid all conflicts even if they shared a partition. Even adding one letter would do it, right? (e.g. "ego" and "ego1")

I didn't even know what /var was for; its just what the guide recommended.

the best solution, then, would be to have it like this:

windows - 6GB
ubuntu /root - 5GB
Ubuntu /home 3GB
Arch /root - 12GB
swap - 1gb (i have 2.5 gb of ram so this is enough, i don't plan on hibernating)
data - 17gb

Would this work?

---

### Post by carolinason on 2008-08-23
my old test bed had a 40g drive partitioned into ~6 g ext3 parts with a swap. i sued smb to boot into each linux. smb can detect the new bootable partition.

install each distros grub into its on partitions.

---

### Post by sandysandy on 2008-08-23
i am booting multiple distros like ubuntu, freespire, mandriva, Open suse, window etc.

i am using 20 gb for each distro ( which includes /home)

using only one SWAP, which each linux distro uses.

for data, i am using /home folder of one of the distros, as from all linux versions u can access /home of the other distros. u can even have a separate big ext3 partition for storing data as it would be accessible from all distros.

earlier i was using separate NTFS partition to store data, to share with windows, but found it too prone to crashing.

hope this helps

regards

---

### Post by intense.ego on 2008-08-23
Yeah, I think I will do something similar. Store the bare minimum on the /home and keep all the data (especially media) on a seperate ext3 partition.

Before I try anything, I just want to confirm that it is fine to share a /home between two distros if they have different usernames. I remember reading a post on these forums, that warned against it.

Also, if I am to share the /home partition, but with different directories, how do I do it so that the second distro installed (arch) doesn't erase the existing data on the /home partition?

---

### Post by estyles on 2008-08-23
Do yourself a favor.  Find your user id (type "id"), and when you set up your arch user, use the same user id.  That way, you'll be owner of your files on either distro.

Personally, I don't see the use in a separate home partition if you have a separate data partition, but since you already have it, it shouldn't hurt anything.

Oh, and to answer your other question - when you set up drives in Arch, it asks you if you want to add a filesystem to the chosen drive.  Tell it no.

---

### Post by sandysandy on 2008-08-23
> **intense.ego said:**
> Yeah, I think I will do something similar. Store the bare minimum on the /home and keep all the data (especially media) on a seperate ext3 partition.

that would be OK

> **intense.ego said:**
> Before I try anything, I just want to confirm that it is fine to share a /home between two distros if they have different usernames. I remember reading a post on these forums, that warned against it.

different user names should be OK. to make it simple u can try username[COLOR="Red"]arch[/COLOR], username[COLOR="Red"]ubuntu[/COLOR]

regards

---

### Post by intense.ego on 2008-08-23
> **estyles said:**
> Do yourself a favor.  Find your user id (type "id"), and when you set up your arch user, use the same user id.  That way, you'll be owner of your files on either distro.

Personally, I don't see the use in a separate home partition if you have a separate data partition, but since you already have it, it shouldn't hurt anything.

Oh, and to answer your other question - when you set up drives in Arch, it asks you if you want to add a filesystem to the chosen drive.  Tell it no.

So, what you are saying goes against what the others are saying. You think I should use the same username because it will give me ownerships of all files. 

But wouldn't that cause conflicts (e.g. one of them might edit a configuration file that affects the other distro)? Also, wouldn't it be better if I didn't have ownership of my ubuntu files when using arch and vice versa, but only share ownership with regards to stuff on the data partition?

---

### Post by estyles on 2008-08-23
> **intense.ego said:**
> So, what you are saying goes against what the others are saying. You think I should use the same username because it will give me ownerships of all files. 

No, no, don't do that.  You want to use the same user id.  Which will be a number.  I think Ubuntu uses 1000 by default for the first user, but I could be wrong.

Personally, I do use the same username, because I keep my /home directories on the same partition with their distros, but if you want to have a /home partition for both distros' /home directories (which is a perfectly fine way of doing it), then make sure to have different usernames like others said.  Arch will ask you for a user id number in the process of setting up a new user, and using the same id will make things easier.

Technically, you really could have the same user name, but when arch asks you what the new user's home directory is, just change the name.  Would be simpler to just have a different user name.  On top of other reasons, I can imagine that there might be programs out there that are sloppily coded that look for "/home/username" instead of just looking for your $HOME directory.

As for whether or not you *want* ownership of your files cross-distro, that's a personal preference.  AFAIK, it's not simple to give ownership to multiple users, unless you create a group for those users, and since your Ubuntu user doesn't technically exist in arch (other than as a number), I'm not sure how easy that would be.  My solution, since I'm the only one that uses my computer and I don't mind if my wife has access to my Data directory, was originally to just chmod the Data partition as all r/w.  You may be able to set up a "data" group that has r/w access to that directory, or you can use the same user id, which means that all file permissions for both users will be the same across both distros.  Your choice.

---

### Post by intense.ego on 2008-08-23
Thank you so much, estyles. I checked and my user ID is 1000, so that's what I'll make my Arch user. 

As for the data partition, I'll make it all read and write, so there shouldn't be a problem.

One more thing, I would like to confirm that I do not need a /var partition. Is this true? Looking at the [wikipedia article]("http://en.wikipedia.org/wiki//var") concerning /var, it seems it could be important.

---

### Post by estyles on 2008-08-23
I've never made a /var partition, but I kinda wish I had, just because having many small files are supposedly handled better by reiserFS.  I don't know that there's really that much benefit, but I think it would be worth a try.  I just wonder whether it's best to have a /var for each distro, one var partition with two directories that are linked to /var, or one /var partition where distros just overwrite files that have the same name.  Overwriting seems like a big mess, so probably not a great idea.

All-in-all, I've been fine with /var on the same partition as whichever distro, but I haven't been using linux all that long.  It's probably a good idea to clear out old logs every once in a while, because they really can build up.

---

### Post by intense.ego on 2008-08-24
> **estyles said:**
> I've never made a /var partition, but I kinda wish I had, just because having many small files are supposedly handled better by reiserFS.  I don't know that there's really that much benefit, but I think it would be worth a try.  I just wonder whether it's best to have a /var for each distro, one var partition with two directories that are linked to /var, or one /var partition where distros just overwrite files that have the same name.  Overwriting seems like a big mess, so probably not a great idea.

All-in-all, I've been fine with /var on the same partition as whichever distro, but I haven't been using linux all that long.  It's probably a good idea to clear out old logs every once in a while, because they really can build up.

Perhaps taking what would have been made into a /var partition and instead include it with the root partition would be a better option?

i.e. instead of 12 gb for / and 6 gb for /var, make it 18 gb for / (var included, at least that's what i though)

---

### Post by intense.ego on 2008-08-25
*bump

---

