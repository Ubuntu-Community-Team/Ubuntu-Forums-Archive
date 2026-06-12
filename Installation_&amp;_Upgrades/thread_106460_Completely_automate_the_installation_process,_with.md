---
title: "Completely automate the installation process, with no user intervention whatsoever"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by harisund on 2005-12-20
Hello

I am trying to deply Linux on a lot of workstations in a lab, and I observe that I have to repeatedly intervene for each machine. After installing on 3 machines, I got really tired of it .. here is a listing of what I do: 

-> Choose default keyboard layout, location and the initial yadda yadda. 
-> Choose the host name
-> after a while, partitioner comes up. Choose the partition. Not much work here. just some swap.
-> time zones. 
-> User name / password. 
-> Once that is done, I change the apt sources.list (I do a server install) and then run apt-get update && apt-get -y install xubuntu-desktop openssh-server. In the middle it asks me for the screen resolution. Oh with sudo of course, in which case it asks for the password.

So how do I automate this? All the machines are identical, and all I need to change is the hostname (that too, each machine differs only by two digits.)

Also the user name in each case will initially be the same, and after the initial housekeeping tasks, the user names will be present in a networked database on the domain (central file server with user's home folders on them). So that needs to be set up too. 

I would gladly search on the web, but I do not even what seearch string to type. 

I am sure it can be done, since after all isn't that what the power of the command line is? I mean, I use the command line for so many series of procedures that I want automated (prime example - backup using rsync, scp so on at periodic times using cron.) There should be a way where I can save the settings, and then just ask the installer to pull the settings off during installation. 

I just want to press "Enter" key, and after a while  leaving the computer unattended, I should have a running Xubuntu desktop with the ability to remote SSH login. 

Thanks !!!

---

### Post by aysiu on 2005-12-20
If they all use the same hardware, consider using PartImage and then creating a back-up .gz that you can unzip onto all the computers.

Once you had that, all you would need is a live CD and an external hard drive (with the backed-up partition image).

---

### Post by harisund on 2005-12-20
Wow ! That was even faster than instantaneous. Yes. The exact same hardware, straight from the vendor, Dell in this case. Same monitor, keyboard, memory, hard disk space, same network card (different MAC id though !!!). Identical. In all respects. 

Now that sounds new. I will try searching for PartImage. 

A million thanks !

---

### Post by aysiu on 2005-12-20
PartImage is in the repositories.
You can also go to the project's [home page](http://www.partimage.org/), which has screenshots showing you how to use it.

You have to run the program from the terminal using root privileges: ```
sudo partimage
```

Once you have a machine set up exactly the way you want it, save the entire partition (using a live CD and PartImage) as a compressed file onto an external hard drive. Then, just take around the live CD and the external hard drive to each new computer and unpack the compressed partition.

You may have to ```
sudo apt-get install partimage
``` each time you use the live CD, though.

---

### Post by harisund on 2005-12-20
From the documentation on the webpage
> The network support is very useful in several cases: 

It you have the same image file for several computers, which have the same partitions and the same software installed

Great ! Thanks so much ... You have just saved a hell lot of time and taught me something terrific too...

---

### Post by harisund on 2005-12-20
Hmm.. I am not able to use partimage on a mounted disk. But I want to create an image of my / root partition and it will be mounted right? So do you suggest I use a live cd?

---

### Post by aysiu on 2005-12-20
[QUOTE=harisund]So do you suggest I use a live cd?[/QUOTE] Yes. Here are the steps:

1. Configure one computer exactly the way you want it.
2. Boot up a live Ubuntu CD on that computer.
3. *sudo apt-get install partimage*
4. Plug in an external hard drive
5. *sudo partimage*
6. Save the partition you want to the external hard drive
7. Reboot without the live CD

8. Pop the live CD into the next computer
9. *sudo apt-get install partimage*
10. Plug the external hard drive in
11. *sudo partimage*
12. Restore the partition from the external hard drive.

Repeat steps #8-12 for each computer.

---

### Post by BatsotO on 2005-12-25
Another suggestion : Use G4L for mass instalation. You just need one fully set system on one HD for source, another HD (same type will be better) as target. and a g4l cd. plug the hard drives, I usualy set the source as hda and target hdb, boot from g4l cd, then do click and clone.  It takes about 45 to 1 hour minute on 40 gigs hd, but you can just leave it there and doing something else.

---

