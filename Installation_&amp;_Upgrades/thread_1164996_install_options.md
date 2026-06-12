---
title: "install options"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by maflynn on 2009-05-20
I'm a fairly new user of ubuntu, I installed kubuntu on my MBP a couple of weeks ago and things are going very nicely. I have one question about files systems and installation options. (yeah a little late now that I have it installed). 

Anyways I noticed in another thread that a poster installed Ubuntu with a separate partition for the root and a separate one for home

What's the advantage of separating the OS from the home directories and would it be worthwhile to redo my installation this way?

If so how much space should I provide the root file system.  I have a 500 gig drive and I gave OSX 250gig (I'm on a MacBook Pro), 220 (or there abouts of) to ubuntu with a 3.75gig swap partition. because its a new 500gig drive, I have plenty of free space which translates into flexibility in setting up Ubuntu the best way.

Any thoughts, recommendations would be appreciated

~Mike

---

### Post by langsweirdt on 2009-05-20
Hi,

Using different partitions for /home and / (root) has an advantage if you want to reinstall ubuntu. You can then choose to format / and just leave /home as it is. You will have a fresh install, without the need to backup your personal files first. Furthermore, all personal settings of the applications are usually stored in /home. So you don't loose these as well. If you are new to ubuntu and linux in general, chances are you mess up your system several times while experimenting. If you do, a 10 min reinstall is sometimes way easier then three hours of problem solving.

An even more advanced setting is using a seperate partition for /boot, /home and / . If you are using different kernels (versions/configurations - these are stored in /boot), you can preserve these as well.

Taking this even further, you can make a partition of every directory, but I don't see the use of it (unless you're running a server, sometimes people make a separate partition for /var then for security reasons).

Cheers.

---

### Post by maflynn on 2009-05-20
Cool thanks for the quick response and even explaining the differences between /boot and/root :)

Any suggestions on setting the size for /root and /boot. I don't want to make them too big and waste the space if I can help it.

---

### Post by growled on 2009-05-20
I just don't see the need of a separate home directory. Some do. The main purpose is so when you upgrade all your "stuff" is still there waiting for you when you upgrade. I just keep all my "stuff" on another disk. 

If you wanted to do a separate /home directory, I would probably give Kubuntu 30-50 GB and the rest to /home, since that is where all your files will be stored and it will take much more space than the system files and programs.

---

### Post by langsweirdt on 2009-05-20
I think assigning 30% of the space you can spare for your ubuntu installation to / and 70% to your /home is a good idea, especially if you want to store a lot of documents and media in your home.

Remember that you can only have four primary partitions on your harddisk at most. If you already have a OSX partition on your hard-disk, you cannot have a /boot, /, /home and swap partition as well. You need to put these in a logical partition then.

---

### Post by Bölvaður on 2009-05-20
> **langsweirdt said:**
> Hi,

Using different partitions for /home and / (root) has an advantage if you want to reinstall ubuntu. You can then choose to format / and just leave /home as it is.

Unless if you do not want to keep your hidden config files from the first install.
If you only want to keep data but discard config files then making a /data partition is the way to go.
Either linked to /home or just use bookmarks in nautilus.

Links:
we have /data/Documents
and /home/maflynn/ (with no Documents directory)

We right click Documents in /data and click "make link" and drag it into /home/maflynn/
Now your computer will think it is placing everything into /home/maflynn/Documents but it really is placed onto the /data partition.
So when you reinstall ubuntu over the old one and choose to mount /data, then all you need to do is make those links again.

That way you always keep your data and discard your old config files.

---

### Post by maflynn on 2009-05-20
30% sounds like a good benchmark and that puts a little over 60 gig, so my guestimate of 50 gig sounds pretty good.

coming from apple/osx where they really really don't want to to create separate disks, I need to get a new mindset.  We do this for our window servers as well. The OS is on the C drive and the data/apps are on E. For what ever reason I had not considered that when installing ubuntu.

I'll back up what I do have in my home folder and go through repartitioning/reinstalling.

Thanks for your help.

---

### Post by Bölvaður on 2009-05-20
you'll need about 12 to 30 GiB for your / partition depending on how you will use it and for how long.
Im currently using 32 GiB as I have many games and programs installed from add/remove

---

### Post by maflynn on 2009-05-20
Thanks for the recommendation, if 12-30 gig.  I've backed up my home folder and I'm getting ready now to get the ball rolling in reinstall kubuntu.

---

### Post by OzOle on 2009-05-20
Hi guys,

This is a very interesting thread. I'm a great believer in separating DATA from PROGRAMS (software, applications, system) to the extend possible. For one thing it makes backing up your data so much easier.

I have a slightly different setup from the one described in the posts above. I have:
HP 2133 Mini-Note netbook computer with 2 GB RAM, 120 GB hard disk drive (HDD). There is a built-in SD memory card drive and I have installed Ubuntu 9.04 on an 8 GB SD card (simply used the SD card as a hard disk during installation, required manual partitioning). I have a swap file on the HDD. It works very well. I have all the standard programs that come with Ubuntu installed incl. Firefox and OpenOffice (+ OO Base) and some other programs. It only takes up about 5 GB out of the 8 GB on the SD card (that should give you an indication of how much an every day normal installation requires, I cannot imagine using 30 GB for the systems). I keep careful notes about programs I install, so that when I want to install the next version of Ubuntu, I simply make a clean install on the SD card and then spend a bit of time re-installing the programs from my notes. It takes a couple of hours, but the advantage is that I have a clean, fresh install. I have tried doing a system upgrade from one version of Ubuntu to the next but not with any great success, I therefore favour doing the clean install.

I would like to use a setup like the ones described in your posts, but the difference is that I use 2 devices (hence 2 partitions) :
SD card for Ubuntu
HDD for data.

How do I mount the HDD automatically during boot up?

How exactly do I point ~SD-card/home/ole to ~HDD/home/ole ? What commands do I have to use?

Question for Bölvaður: Why would I want to keep my "hidden config files from the first install"? What would be the advantage of that after the next clean install of Ubuntu? I'm only asking because I don't understand how it works, so I don't understand the benefits. I hope you don't mind explaining it to me, I would like to learn.

Thanks for your excellent posts.

Cheers,

Ole down-under

---

### Post by Bölvaður on 2009-05-20
> **OzOle said:**
> 
Question for Bölvaður: Why would I want to keep my "hidden config files from the first install"? What would be the advantage of that after the next clean install of Ubuntu?


For an instance there is a very big thumb collection of all your photos and videos there (well it is small if you dont have your family photos and videos on the computer) and that will save you some time not having to recreate it.

You might want to keep your existing themes that are on there.

There are many config files you would want to keep, like if I had set gnome-terminal to look some strange way and geany (program I use to code c++ in).

It can also be beneficial to share /home between many distros, so you have many  /  but only one /home. So you can share configs on every distro you got.


Right click a directory and click "make link" can be useful :P you can even have it on a usb stick and just copy it into your /home on every install

---

### Post by maflynn on 2009-05-21
Well partitioning went well last night I created the following setup.  The numbers are slightly rounded but you get the idea.

/dev/sda1 - 0.2	- EFI boot partition  	
/dev/sda2 - 250	- HFS+ (OS/X) 	
/dev/sda3 - 51	- EXT3 root partition 	
/dev/sda4 - 155	- EXT3 home partition 
/dev/sda5 - 8	- SWAP partition
/dev/sda6 - 0.5	- boot partition

As I work on Ubuntu, I may adjust / and /home thanks to gparted ability to alter partition sizes non-destructively.  I plan on having a couple of VMs under VMware server and they'll of course go in the /root partition and that will eat up a lot of my space. I do plan to have my music, docs and everything else in the home.  As I continue to work with ubuntu I'll alter the configuration to allow me to work the way I want it too.

---

### Post by Bölvaður on 2009-05-21
> **maflynn said:**
> I plan on having a couple of VMs under VMware server and they'll of course go in the /root partition and that will eat up a lot of my space.
it's actually going to be in your home folder in a hidden directory.

---

### Post by maflynn on 2009-05-21
Mine wasn't when I installed vmware server (prior to rebuilding my os).
It put it in /var/lib/vmware

---

### Post by Bölvaður on 2009-05-21
you can link the directory to one in your /home and move it into that directory

---

