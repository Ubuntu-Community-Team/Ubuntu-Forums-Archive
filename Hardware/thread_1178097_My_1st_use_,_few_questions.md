---
title: "My 1st use , few questions"
date: 2009-06-04
forum: Hardware
---

### Post by mohd on 2009-06-04
Hey there , thats my 1st time using ubuntu so i donno much so i need some help

- 1st when i was installing it i got my hdd formated like that 
1 - swap
2 - a partition '/'
3 - a partition '/usr'
now i can only see the 2nd which is used for the system yet i can't see the other partition 

- 2nd do i need to find drivers for my hardware like gfx or main board etc ? or the ubuntu does it on its own ?

- 3rd i have external storages a flash and a usb hdd , so my question is if i connect them and they are in ntfs and fat32 format , will they work fine or the ubuntu will format them or sth ? cause i can't lose the data on that hdd

*note* am using ubuntu 7.1 , on a fujitsu siemens amilo pi 1505

thanks in advance

---

### Post by ad_267 on 2009-06-04
Welcome to Ubuntu!

1. You shouldn't be able to see them anywhere, they should be invisible and just work. Post the output of "sudo fdisk -l" and "mount" from a terminal if you're worried (Under applications - accessories - terminal). It's most likely that everything is fine though so probably no need to.

2. No, Ubuntu should find most stuff automatically. You can check under System - Administration - Hardware Drivers if there are any graphics drivers available to install.

3. They will work fine on Ubuntu, just plug them in and they should work. (7.10 is quite old though so not 100% sure)

Is there any reason why you're using 7.10 and not a later version? 9.04 is the latest stable release, and each new release supports a lot more hardware and has many improvements and bug fixes.

Some more tips, read these pages:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

### Post by AndyCee on 2009-06-04
1) Where are you looking for the /usr partition? Right-click on the /bin directory, and the /usr directory. If the third partition has been mounted on the /usr directory, the free space will be different.

2) Ubuntu will find many drivers on its own. The newer the version of Ubuntu/linux kernel, the easier it is to install. Some drivers are installed via the

System -> Administration -> Hardware

menu (or something like that. 3 new versions have been released since 7.10, so it might be slightly different). If you are missing a driver, ask on these forums for help.

3) FAT32 is currently included in the linux kernel. You may need to install a driver for ntfs by typing:

sudo apt-get install ntfs-3g

in a terminal window

I'd advise (if appropriate) to try a more recent version of Ubuntu.

EDIT: ad_267 beat me to it. Scary how similar our replies are.

---

### Post by mohd on 2009-06-04
@ad_267
- i used the command and it showed me the partitions info , still if i go to computer i find only a partiton called file system which is the small partition i used for the system and the other isn't there , when i go to any of the folders like music or documents and i check for the space it shows the same space used by the system partition , how will i use it if i can't see it ?

- is there any way to upgrade to 9 or i need to start over ? the thing is i had the cd from a friend and it was 7 


@Andy i donno where the /bin or /usr directory is

---

### Post by ad_267 on 2009-06-04
Yeah don't worry about your /usr and swap partitions, they'll be working fine. Mounting partitions doesn't work in Ubuntu like it does in Windows. They're mounted at directories rather than having a C, D, E drive like in Windows.

If you go to System - Administration - System Monitor it should show your different partitions, although maybe not the swap partition.

If you browse the file system you can go to / and then see /usr within the root directory as if it was a normal directory, but it is actually where your partition is mounted.

What did you want to use your /usr partition for? This partition is used by the system for installing applications in. If you want a partition to store your data in you should mount it at /data or something else which isn't already used by the file system. I usually have just a root partition at /, a swap partition and a home partition at /home.

You can upgrade to to the latest version but that's quite a few versions to skip, and I doubt the upgrade would go smoothly. I haven't tried that kind of thing myself though so it might go ok. It's probably better to do a clean install if you haven't gone too far though and you don't mind downloading 700MB and burning the image to a CD.

---

### Post by mohd on 2009-06-04
ok i'll make a clean copy , so i do a partition '/' and a '/home' ? if i want to have one as a system and application  and the other as a storage for media and data

my hard is 160gb , can you recommend me how much i should leave for the system and swap ? 

sorry for inconvenience and thanks for you help

---

### Post by ad_267 on 2009-06-04
Your /home directory contains all the stuff you see when you open up the file browser like the Documents, Music and Pictures directories. There are also hidden directories that contain configuration files for different applications.

I find having a separate /home suits me, as I can do a clean install and keep all my configurations, but if you want to keep that configuration stuff separate you could create a separate /data and make links from your home directory to directories in /data.

With a 160gb drive I'd say about 2gb for swap, 30gb for the root partition and the rest for your /home or /data. A general rule of thumb I've heard is about twice your ram for swap, but I think now days with the increase in ram size, this isn't needed. I've heard you need at least as much swap as you have ram if you want to hibernate your computer, but with normal use my swap hardly goes over 2%.

---

### Post by mohd on 2009-06-04
i don't get it , the / partition will be having the operating system
what is the difference between /data , /usr and /home 
which is the closet to the windows system , like having a separate partition where i can store data and have as much folders as i want , and having the software and applications installed in the os partition

---

### Post by bol0 on 2009-06-04
Comparing to Windows let say / is C: so /home and /usr will be the same as C:\home and C:\usr in tree hierarchy. It's a bit different than in Windows so you may get confused as u can have /home as a separate partition but still see it as a 'folder'. Again comparing to Windows /home is 'documents and settings' like and /usr is 'program files' like ;)

---

### Post by mcduck on 2009-06-04
> **mohd said:**
> i don't get it , the / partition will be having the operating system
what is the difference between /data , /usr and /home 
which is the closet to the windows system , like having a separate partition where i can store data and have as much folders as i want , and having the software and applications installed in the os partition

/usr is a system directory where most of the user-level programs and stuff is installed. /home is where user's home directories (and thus all personal files) are located.

/data isn't part of the standard file system hierarchy. So it could contain anything you want.

In general all personal files are stored in each users home directory, located inside /home. The rest of the file system isn't supposed to be writable for any normal user (apart from stuff inside /media, which is where all your removable drives and medias are mounted).

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/")

Any directory inside the file system can be on separate partition, or even mounted through network. From user's point of view this makes no difference and users don't really even notice anything, apart from perhaps having a different amount of available space in different directories.

---

