---
title: "moving OS to new drive"
date: 2015-08-07
forum: Hardware
---

### Post by kurja on 2015-08-07
i'm installing a new hard drive soon, as the current SSD is starting to get full, and I'm wondering if there's any performance benefit to be gained from keeping the old one around? Storage space is not an issue, I now have a HDD as a second drive where I keep my data. A long time ago I remember configuring, I think it was win nt machines, to use multiple drives - one had the OS on it, second one was where the applications went, a third one was for storage, sometimes one just for swap; is there any sense in a scheme like this with today's Ubuntu installed on a SSD? I'd think that a drive for swap could be useful in some instances but I don't think running out of RAM is ever an issue in my case. Not worth the effort? Or is it?

And a second question about the procedure itself. I understand that booting to a live session (so hard drives can remain unmounted) I only need gparted to copy the current partitions to the new drive, gparted will even copy the files system labels and uuid. Then I can increase the partition size to utilize the larger drive and I'll need to do anything else only if I want to keep the old drive around as well (because there are now two drives with same uuid's). Is that about right?

---

### Post by monkeybrain20122 on 2015-08-07
For the second question, check out fasrachiver [http://ubuntuforums.org/showthread.php?t=2221842&page=4](http://ubuntuforums.org/showthread.php?t=2221842&page=4)

---

### Post by kurja on 2015-08-07
I don't see how using fs archiver would be the better choice over gparted?

---

### Post by oldfred on 2015-08-07
I prefer new installs.
If you have lots of settings in /home then you can copy that over. 
Or export a list of installed apps if you have added a lot, to make it easy to reinstall.
You should have those /home & apps as part of your regular backup anyway.

If you do copy, and want to keep old drive, you must change UUIDs and then old drive would not be bootable.

Depending on size of SSD and now much data you have, you may want some or all data on hard drive and just use SSD as boot drive. I now keep /home inside my / (root) on SSD, but have all data on rotating drive. But my new SSD is large enough for several /, so I have space to test another version.

---

### Post by sudodus on 2015-08-07
I use a **data** partition for most data files (documents, pictures, videos, music etc), and I back it up separately from the operating system. Some people prefer to have a separate home partition, but I don't. It is quite small, when it is not used for the data files.

-o-

There are several tools for copying a system from one drive to another drive. If you want a pure clone to a drive of at least the same size, it is often a good idea to use ***Clonezilla***. ***fsarchiver*** works in a different way, but both of them do not copy the unused space (only blocks which contain files). I don't know which copying method is used by gparted, so I can't tell how efficient it is, but it is probably not more efficient than the other two tools, but maybe easier to use. I use gparted a lot, but not for cloning.

It the block structure is different on the target drive, it may be better to use ***gparted*** and create a new structure with partitions and file systems and copy the files with ***rsync*** and install the bootloader with ***grub-install***. (If you have Windows, you probably need some cloning tool.)

---

### Post by weatherman2 on 2015-08-07
I prefer to keep the OS and "applications" (/usr) + swap on a fast drive (SSD) and put data on a hard drive if necessary.  I don't now the sizes involved, but for a typical Ubuntu installation, not much spare is really need for OS + applications.  30GB is usually more than enough for me these days, sometimes less will work.  Keeping that stuff on an SSD will give you the best performance, better boot times, etc.

Yes, Gparted works well to copy partitions - if you wish to clone manually, that's how I do it usually, but you also must install/update Grub again afterward.  I prefer the "chroot" method for this - do a web search for "ubuntu grub chroot" and follow the instructions.

Clonezilla also works great to clone drives, unless you are doing something more complicated like moving partitions around or splitting them up.  Sometimes you can start by doing a Clonezilla clone then doing "surgery" on it with Gparted later - maybe less manual work overall even though it could take more wall clock time.

---

### Post by kurja on 2015-08-07
> **oldfred said:**
> I prefer new installs.
If you have lots of settings in /home then you can copy that over. 
Or export a list of installed apps if you have added a lot, to make it easy to reinstall.
You should have those /home & apps as part of your regular backup anyway.

If you do copy, and want to keep old drive, you must change UUIDs and then old drive would not be bootable.

Depending on size of SSD and now much data you have, you may want some or all data on hard drive and just use SSD as boot drive. I now keep /home inside my / (root) on SSD, but have all data on rotating drive. But my new SSD is large enough for several /, so I have space to test another version.

The new SSD is going to be 240GB, my old one is 64 and my / is almost 50GB now. How do I export a list of installed applications? I do have many applications installed from various repositories, this sounds like a handy feature.

A HDD for data is a must for me, I handle large numbers of photographs which take a lot of disk space. I'm not removing or replacing the data HDD that I have now.

> **sudodus said:**
> I use a **data** partition for most data files (documents, pictures, videos, music etc), and I back it up separately from the operating system. Some people prefer to have a separate home partition, but I don't. It is quite small, when it is not used for the data files.

-o-

I'm not planning to make any extra partitions, what I'm wondering is if I could get any noticeable performance increase from including the old SSD in my setup. Doesn't seem likely really, but I thought I'd ask. Is it even possible to have Ubuntu install applications to a different drive? In (windows) times past I often had a d:\program files which seemed to work well.

> **sudodus said:**
> 
There are several tools for copying a system from one drive to another drive. If you want a pure clone to a drive of at least the same size, it is often a good idea to use ***Clonezilla***. ***fsarchiver*** works in a different way, but both of them do not copy the unused space (only blocks which contain files). I don't know which copying method is used by gparted, so I can't tell how efficient it is, but it is probably not more efficient than the other two tools, but maybe easier to use. I use gparted a lot, but not for cloning.

It the block structure is different on the target drive, it may be better to use ***gparted*** and create a new structure with partitions and file systems and copy the files with ***rsync*** and install the bootloader with ***grub-install***. (If you have Windows, you probably need some cloning tool.)

Hmm I don't know either if gparted does a low level copy like dd, or not... a quick search didn't yield anything useful on the subject.

---

### Post by sudodus on 2015-08-07
Clonezilla and fsarchiver are more efficient than dd. (dd copies every byte).

---

### Post by oldfred on 2015-08-07
My / is partitioned as 25GB and I am using about 15GB including /home of about 2GB. Included in /home is .wine where I have Picasa and that is the vast majority of my /home.

I manually copy any file I edit in /etc like grub into /home so my /home backup includes any /etc edited files.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

I include a new list of installed apps with every backup.

 From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

If reinstalling same version, ppas should be ok. But new version of Ubuntu may not work if ppa does not have new version. And then all sorts of issues as updates get blocked by bad ppa.

       But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)

---

### Post by gordintoronto on 2015-08-08
Your root is huge! Have you tried running: sudo apt-get clean

Then fire up Synaptic and "completely remove" all but two old kernels. I search for the numerics, such as "3.19.0" to make sure I get all the installed files.

---

### Post by kurja on 2015-08-09
> **gordintoronto said:**
> Your root is huge! Have you tried running: sudo apt-get clean

Then fire up Synaptic and "completely remove" all but two old kernels. I search for the numerics, such as "3.19.0" to make sure I get all the installed files.

apt-get clean didn't seem to do much if anything. It looks like I do have a couple kernels in there that I don't think I'm ever going to need for anything =D But they shouldn't take *that* much disk space.. Oh and / is not just the root "system files" but it includes /home and everything else on the partition for that matter, no? At least df -h tells me that sda1 is mounted on /.

```
:~$ sudo apt-get clean


:~$ uname -r
3.13.0-55-generic
:~$ dpkg -l | grep linux-image-
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic                               3.13.0-54.91                                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                               3.13.0-55.94                                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                         3.13.0-54.91                                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                         3.13.0-55.94                                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.55.62                                           amd64        Generic Linux kernel image
:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        55G   46G  6,4G  88% /



```

---

### Post by kurja on 2015-08-09
> **oldfred said:**
> My / is partitioned as 25GB and I am using about 15GB including /home of about 2GB. Included in /home is .wine where I have Picasa and that is the vast majority of my /home.

Oh and I have picasa installed as well, but since the libopencl conflict with nvidia drivers I haven't had wine so no picasa... I've been trying to get used to shotwell. Do you use nvidia & Picasa?

---

### Post by oldfred on 2015-08-09
I have used nVidia and Picasa on old system with 14.04 and 9600GT. 

My new system is UEFI and I was just going to use the Intel video, but did not pay attention to video ports on motherboard and had a mis-match with monitor. So I added a nVidia GT 620 that I had. It has worked well enough with open source driver that I have yet to install nVidia driver.

Many have posted that since Picasa changed something that uploading to Google does not work, but never used that anyway. But my wife liked that it would also connect to the vendor she uses to print some of the photos and that also stopped. I also wanted her to save edits anyway so not just in Picasa but in files that I backup, so she now uploads directly from file system. But she uses Picasa to edit, review & search for our photos.

---

### Post by kurja on 2015-08-09
> **oldfred said:**
> I have used nVidia and Picasa on old system with 14.04 and 9600GT. 

My new system is UEFI and I was just going to use the Intel video, but did not pay attention to video ports on motherboard and had a mis-match with monitor. So I added a nVidia GT 620 that I had. It has worked well enough with open source driver that I have yet to install nVidia driver.

Many have posted that since Picasa changed something that uploading to Google does not work, but never used that anyway. But my wife liked that it would also connect to the vendor she uses to print some of the photos and that also stopped. I also wanted her to save edits anyway so not just in Picasa but in files that I backup, so she now uploads directly from file system. But she uses Picasa to edit, review & search for our photos.

There was a thread here about the login problem, if you can login through windows then you can dig up ..something from registry (?) that you then put somewhere in wine's registry (?) and it should work. I never tried that since I don't have windows but in case you want to look into it ;)

Picasa has not worked on my machine at all in a long time, there's a conflict with nvidia drivers and wine - installing wine complains that nvidia drivers need to be removed, and vice versa. And I kinda need the opencl :/ Did you experience this issue?

---

### Post by kurja on 2015-08-12
I got the new drive, booted with livecd, copied sda1 to new drive with gparted, [installed]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") grub, and it boots from the new disk. Gparted copied the uuid as well. Now running the system from the new disk, back to gparted and created a swap partition at the end of the disk and stretched the main partition to fill the gap. Done, and done!

---

### Post by sudodus on 2015-08-12
Congratulations :KS

Thanks for sharing your result! It is good to know that gparted works well to clone a partition.

---

### Post by oldfred on 2015-08-12
Glad you got it working.
You will need to change UUID on old install or reformat it.

On Picasa.
I have  Nouveau and Picaca on my main working install 14.04. So I went into a install of 15.04. I thought I had installed nVidia, but did not. So I ended up installing wine, Picasa and then nVidia and it still seemed to be working. Did not do any real testing other then that nVidia was installed & Picasa opened & was busy updating all my photos.
Start a new thread on Picasa if you still have issues.

---

### Post by kurja on 2015-08-13
Oh yes, gparted worked wonderfully. UI is intuitive and very clear in what's being copied where, which helps to avoid the classical "I ghosted a blank disk over my OS" -problem. Recommended :)

For sake of completeness and to anyone looking to copy their OS, I should add that following above procedure, /etc/fstab needs to be edited to correctly mount the new swap space.

---

### Post by kurja on 2015-08-13
> **oldfred said:**
> Glad you got it working.
You will need to change UUID on old install or reformat it.

Oh, I removed the old drive from the system, it's uuid is a nonissue. Keeping it in there or not was a part of the original question, remember ;)

> **oldfred said:**
> 
On Picasa.
I have  Nouveau and Picaca on my main working install 14.04. So I went into a install of 15.04. I thought I had installed nVidia, but did not. So I ended up installing wine, Picasa and then nVidia and it still seemed to be working. Did not do any real testing other then that nVidia was installed & Picasa opened & was busy updating all my photos.
Start a new thread on Picasa if you still have issues.

Guess I'll do that. There are plenty of discussions about the issue around the net, with some possible work-arounds, but I've not seen a real solution yet, maybe there is one now.

---

