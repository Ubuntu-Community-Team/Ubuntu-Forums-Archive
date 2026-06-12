---
title: "Synaptic asks for Ubuntu CD but doesn't recognize the disc so can't update anything"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by Elliander on 2009-08-29
I am trying to install Eclipse from Synaptic Package Manager. However, every time I go to apply the changes I get this message:

Please insert the disk labeled:
Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)
in drive /cdrom/

(This is the CD I installed from, but it updated a number of times since install)

When I would put this in the drive, and click OK, the box just comes up again and again. It's as if it just doesn't see it. But I know there is no problem with the disc, because when I put it in, it opens the CD displaying the contents.

I am left clicking to skip it, which means nothing gets installed.

I am not at all familiar with Linux based operating systems. I just want to be able to study C and C++, and compile. I tried downloading a file directly from Eclipse but I don't know how to "install" anything without using a .deb or synaptic package manager.

---

### Post by str8outtacpt on 2009-08-29
i know i am not suppose to do this but i am sorry i am so paranoid and nervous. i think i did something very bad. i put linux on my computer and i accident went to partition editer and made my hard allocated instead of ntfs but i never commited the change but i cant back to windows and i do not have anything to back it up with so is there anyway i can get windows back without losing all my data?

please someone help...i need a solution. idk what to do.

---

### Post by Elliander on 2009-08-29
> **str8outtacpt said:**
> i know i am not suppose to do this but i am sorry i am so paranoid and nervous. i think i did something very bad. i put linux on my computer and i accident went to partition editer and made my hard allocated instead of ntfs but i never commited the change but i cant back to windows and i do not have anything to back it up with so is there anyway i can get windows back without losing all my data?

please someone help...i need a solution. idk what to do.

um... that really doesn't have anything to do with this topic. :confused: It's also kind of rude to detract topics like that... but to answer your question - really, I've never used partition editor. But you can have windows and ubuntu on the same machine. I do. If you install windows first, then install Ubuntu, ubuntu can change the partition size so you can have both. If you have files on your hard drive you need to backup first, you can boot from the ubuntu CD to run ubuntu from the CD and have access to all your files that way. then just copy them onto your flash drives before reinstalling everything. That's the simplest solution I can think of. If you can't access the files because a partition is corrupt or was damaged I don't think there is anything you can do about it.

---

### Post by str8outtacpt on 2009-08-29
> **Elliander said:**
> um... that really doesn't have anything to do with this topic. :confused: It's also kind of rude to detract topics like that... but to answer your question - really, I've never used partition editor. But you can have windows and ubuntu on the same machine. I do. If you install windows first, then install Ubuntu, ubuntu can change the partition size so you can have both. If you have files on your hard drive you need to backup first, you can boot from the ubuntu CD to run ubuntu from the CD and have access to all your files that way. then just copy them onto your flash drives before reinstalling everything. That's the simplest solution I can think of. If you can't access the files because a partition is corrupt or was damaged I don't think there is anything you can do about it.

i apologize...thank you...ima send u a DM

---

### Post by Elliander on 2009-08-29
Anyway, I still need help either getting Eclipse installed without needing the CD, or getting Synaptic Package Manager to recognize the CD

---

### Post by Elliander on 2009-08-30
This problem is now causing additional problems. When I go to update, when updates are available, it gives me a message saying it can only do a partial update.

So... I don't know what to do. I just need to use *SOMETHING* to study with. KDevelop doesn't have a build or debug option. Code::Blocks IDE won't even run. And most other programs I can't even install now... you'd think an open source operating system would have a bit more stability than this. Or even someone able to give some kind of useful information.

Since day one installing Ubuntu, the only programs I could ever get to work right are windows programs running under WINE.

---

### Post by Elliander on 2009-08-30
As if it couldn't get any worse...

Now I get this error, even though other updates would download, and clearly I am online right now.


Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.140 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by hansdown on 2009-08-30
Hi Elliander.

Support for 7.10 is no longer available.

You may wish to install a newer version.

You can choose 8.04 or 9.04.

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

