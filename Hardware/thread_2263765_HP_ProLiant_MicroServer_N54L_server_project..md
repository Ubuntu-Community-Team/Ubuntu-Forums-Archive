---
title: "HP ProLiant MicroServer N54L server project."
date: 2015-02-03
forum: Hardware
---

### Post by globetrotterdk on 2015-02-03
Recomendations needed for optical drive and choice of graphics card.

I have just purchased an HP ProLiant MicroServer N54L as an Ubuntu server project. This is the first time that I have tried a server project, although I have played around with Ubuntu cli versions in the past. Here is where I am at:

I have most of the hardware -
Drives: 3x3TB Western Digital drives (planning to install Ubuntu server edition on the 250GB enterprise standard drive that comes with the N54L). Two of the drives to be used as RAID1 and tha last as backup (RAID0)
Graphics card: Asus Radeon HD 5450 2GB or Zotac GeForce GT 210 1GB
Optical (DVD) drive: *unsure what would work*

Ubuntu 14.04 server edition
Since I am a newbie at this, and know nothing about the security issues of running a server connected to the Internet, I thought I would just try running the server in my rehearsal room with no Internet connection. I want to be able to rip CDs and play my collection of .flac files using alsa and moc.

Ideas, comments would be appreciated.

---

### Post by lukeiamyourfather on 2015-02-03
The HP ProLiant MicroServer N54L is designed to be a file server. That's it. The CPU is incredibly slow compared to any other modern processor and it has a 150 watt power supply, not enough for any discrete graphics card (AMD recommends 400 watt or higher for the Radeon HD 5450). It sounds more like you want to setup an audio workstation rather than a file server in which case the HP ProLiant MicroServer N54L is a poor choice.

---

### Post by globetrotterdk on 2015-02-04
> **lukeiamyourfather said:**
> The HP ProLiant MicroServer N54L is designed to be a file server. That's it. The CPU is incredibly slow compared to any other modern processor and it has a 150 watt power supply, not enough for any discrete graphics card (AMD recommends 400 watt or higher for the Radeon HD 5450). It sounds more like you want to setup an audio workstation rather than a file server in which case the HP ProLiant MicroServer N54L is a poor choice.

Thanks for your reply. Interesting. I have seen a number of [postings]("http://www.theoutpost.org/6-techy/hp-microserver-n54l-nas-build/") where people use the HP ProLiant MicroServer N54L as a NAS. Having never used a NAS, i can't say for sure, however my impression was that many NAS can both serve web sites, files and do some media streaming. In my case, I would eventually like to use the HP ProLiant MicroServer N54L as a OwnCloud server, which also supports some streaming (experimental at this stage). Until I get a handle on Internet security, I thought that using moc to play audio files was so low resource, that using audio files woudn't be an issue.

With regards to the discrete graphics card, there are a number of [postings]("http://www.tekforums.net/guides-projects/hp-proliant-microserver-purchase-upgrade-setup-guide/") that only mention the issue of availability of AMD graphics drivers, and that the Zotac  card worked succesfully.

I would be interested to hear more, as I am sure that you know more about this than me.

---

### Post by mastablasta on 2015-02-04
> **globetrotterdk said:**
> Thanks for your reply. Interesting. I have seen a number of [postings]("http://www.theoutpost.org/6-techy/hp-microserver-n54l-nas-build/") where people use the HP ProLiant MicroServer N54L as a NAS. Having never used a NAS, i can't say for sure, however my impression was that many NAS can both serve web sites, files and do some media streaming. In my case, I would eventually like to use the HP ProLiant MicroServer N54L as a OwnCloud server, which also supports some streaming (experimental at this stage). Until I get a handle on Internet security, I thought that using moc to play audio files was so low resource, that using audio files woudn't be an issue.

NAS - Network Attached Storage. what you do with that computer besides storing files is up to you. this CPU has it's limits.
> 
With regards to the discrete graphics card, there are a number of [postings]("http://www.tekforums.net/guides-projects/hp-proliant-microserver-purchase-upgrade-setup-guide/") that only mention the issue of availability of AMD graphics drivers, and that the Zotac  card worked succesfully.

Server already has built in radeon hd 4200. you do not need another graphics card. I am assuming you plan to run the server headless anyway... then the card is needed only during setup & install so you can see what you type etc. after that it gets no use. drivers for this chip are included in kernel (open source ones). there is no issue with availability of them.

how do you plan to administer the server? via CLI or will you use some WebGUI or desktop interface?

you mention raid 0 - raid 0 is not a backup it's putting two hard disks together and then both are showing up as one. in your case this is not such a good idea. it might be better to indeed use the disk as backup copy. RAID 1 is not backup it's a disc redundancy.  if one disk goes the other one can copy data to it. however if you have corrupt files on one disk or if you delete them on one they get deleted on the other as well. which is why this isn't a backup solution. backup solution is something like fsarchiver, rdiff, rsync and similar. or backurserverup or what was it.

anyway I would say install the OS, start setting it up and see where it get's you and what other questions you might find. at the moment you question is pretty general and I am not quite sure what the issue is. 

her eis a nice guide on hardening: [http://hardenubuntu.com](http://hardenubuntu.com)
I use fail2ban to block attempts as well.

another one here: [http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/](http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/)

---

### Post by globetrotterdk on 2015-02-04
new info> **mastablasta said:**
> NAS - Network Attached Storage. what you do with that computer besides storing files is up to you. this CPU has it's limits.

Am what I am suggesting within those limits?

> **mastablasta said:**
> Server already has built in radeon hd 4200. you do not need another graphics card. I am assuming you plan to run the server headless anyway... then the card is needed only during setup & install so you can see what you type etc. after that it gets no use. drivers for this chip are included in kernel (open source ones). there is no issue with availability of them.

how do you plan to administer the server? via CLI or will you use some WebGUI or desktop interface?

Cool! At the outset I was thinkin CLI, but I am unsure if OwnCloud can be administered from the CLI.

> **mastablasta said:**
> you mention raid 0 - raid 0 is not a backup it's putting two hard disks together and then both are showing up as one. in your case this is not such a good idea. it might be better to indeed use the disk as backup copy. RAID 1 is not backup it's a disc redundancy.  if one disk goes the other one can copy data to it. however if you have corrupt files on one disk or if you delete them on one they get deleted on the other as well. which is why this isn't a backup solution. backup solution is something like fsarchiver, rdiff, rsync and similar. or backurserverup or what was it.

So all three disks should be RAID 0?

> **mastablasta said:**
> anyway I would say install the OS, start setting it up and see where it get's you and what other questions you might find. at the moment you question is pretty general and I am not quite sure what the issue is.

First time, proof of concept, hardware confirmation. Would like a DVD, but not sure what will work.

> **mastablasta said:**
> her eis a nice guide on hardening: [http://hardenubuntu.com](http://hardenubuntu.com)
I use fail2ban to block attempts as well.

another one here: [http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/](http://blog.mattbrock.co.uk/hardening-the-security-on-ubuntu-server-14-04/)

Very cool info. Thanks.

***
I have been looking at the ownCloud Architecture Overview white paper. It looks like OwnCloaud is a PHP application that runs on IIS or Apache servers.
***

---

### Post by lukeiamyourfather on 2015-02-04
> **globetrotterdk said:**
> Am what I am suggesting within those limits?

Sort of. Simply running a desktop interface on the machine will take up a fair amount of the available memory and processor resources. It's possible to do but it's not what the machine was designed to do. In my opinion you'd be better off building a desktop machine with a faster processor and more memory if you plan to use it like a desktop computer and not just a file server.

> **globetrotterdk said:**
> Cool! At the outset I was thinkin CLI, but I am unsure if OwnCloud can be administered from the CLI.

ownCloud can be setup and administered without a desktop interface but if you're asking these kinds of questions maybe you should not be hosting this yourself. While it provides a lot of convenience it also exposes you to a lot of threats you otherwise wouldn't have to worry about.

> **globetrotterdk said:**
> So all three disks should be RAID 0?

RAID 0 simply stripes data across all of the drives in the array. If a single drive fails then all of the data on all of the drives is completely lost. There are RAID modes like 1 and 5/6 which can continue to function after a drive failure but they are not backup. If you're concerned about not losing important data you should create and adhere to a strict backup routine. The backup should be on another machine or on a drive at least not stored at the same place. Also check out ZFS on Linux as an alternative to traditional RAID. It offers RAID like features but many benefits over traditional RAID. Some reading material...

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://en.wikipedia.org/wiki/Standard_RAID_levels](http://en.wikipedia.org/wiki/Standard_RAID_levels)
[http://en.wikipedia.org/wiki/ZFS](http://en.wikipedia.org/wiki/ZFS)
[http://en.wikipedia.org/wiki/OpenZFS](http://en.wikipedia.org/wiki/OpenZFS)
[http://zfsonlinux.org/](http://zfsonlinux.org/)

[http://whenpicsfly.com/getting-to-know-zfs/](http://whenpicsfly.com/getting-to-know-zfs/)
[http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf](http://whenpicsfly.com/wp-content/uploads/2014/09/Intro-to-ZFS-on-Linux.pdf)

> **globetrotterdk said:**
> First time, proof of concept, hardware confirmation. Would like a DVD, but not sure what will work.

Optical media is no longer needed to install Ubuntu or most other Linux distributions. They can be installed from a USB flash drive as long as the machine can boot from USB (almost all computers made in the last decade can do this).

> **globetrotterdk said:**
> I have been looking at the ownCloud Architecture Overview white paper. It looks like OwnCloaud is a PHP application that runs on IIS or Apache servers.

Yes. It can be setup from the Ubuntu repositories and it will take care of everything for you but it will be an out of date version. Or you can setup Apache, a database, and install ownCloud manually using the latest version.

---

### Post by mastablasta on 2015-02-05
> **globetrotterdk said:**
> new info

Am what I am suggesting within those limits?


I guess so. the CPU is not that bad, but it's not something great either. 

> 
Cool! At the outset I was thinkin CLI, but I am unsure if OwnCloud can be administered from the CLI.
***
 I have been looking at the ownCloud Architecture Overview white paper. It looks like OwnCloaud is a PHP application that runs on IIS or Apache servers.
***


yup. you install apache and the own cloud. not that by default owncloud is made for one user and uses SQLite as database. if you add more users it might become slow. you can use MySQL, mariadb or postresql as database. probably it also works on another web server such as ngnix and similar.

owncloud is your own cloud. it's like ogogle drive or dropbox only you have it. you do not administer server via owncloud GUI. you only administer owncloud. you still need a way to check logs, do updates etc. etc.

> 
So all three disks should be RAID 0?

again I am not sure why you would need raid0. it's up to you, but in your case it might make more sense to setup 2 drives as software raid 1 and then use the third one to backup the files to from RAID array. with raid one you loose 25-30% disk space on those disks. 

> 
First time, proof of concept, hardware confirmation. Would like a DVD, but not sure what will work.

you can try it out using USB. in fact the box has internal USB where I added a USB stick with OS on it :-). sure it is slower than disk but it works well. I took the more ram, no hard disk option. you can install the OS by booting from USB and then installing to hard disk. hard disk is better for OS especially this one.


like I said try it.

to administer server via webGUI I suggest you look at Zentyal - use expert mode and install without desktop interface, so you will end up with webgui (you connect to server via web browser). 

A few other newbie friendly options:
OpenMediaVault - debian based, very nice and clean webGUI
Ajenti - uses python, very light
ClearOS - CentOS based
Nethserver - CentOS based
...
etc ., etc.

---

