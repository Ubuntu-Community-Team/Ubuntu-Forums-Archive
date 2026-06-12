---
title: "Motherboard took a dump ..... hmmm"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by redweb on 2006-02-16
Ok .. so my webserver has been working fine for the better part of 3 years now and I continually upgrade this box ... it's on breezy now

I love it

It's fantastic

It's stable as all hell

Hardware failure ... DAMMIT MAN

So the old KT400A chipset (DFI LAN Party MB) decides to take a dump on me and leaves me and about 60 or so of my friends hanging (I've given people email addresses now for all that time) I have about 12 domains on the box and use the VHCS2 hosting panel .. works great yadda yadda yadda ... 

I'm looking for the easiest way to migrate everything to a new box and keep all accounts intact 

I'm looking at 

[http://www.ubuntuforums.org/showthread.php?t=35087&page=14&highlight=migrate+hard+drive](http://www.ubuntuforums.org/showthread.php?t=35087&page=14&highlight=migrate+hard+drive)

and also this ..

[http://www.billboardhosting.com/vhcs2_migrate.txt](http://www.billboardhosting.com/vhcs2_migrate.txt)

and both seem plausible and in fact I was going to do a backup of the drive as posted in the first link I posted but it will not boot all the way before the MB freezes either to the HDD or to a CDRom.

I guess I'm going to have to mount it on another box to back it up and then try both of the above but it really got me thinking.

I can take a windows XP drive out of one computer and put it in another and after a little bit of work fixing any driver issues from the board chipset differrences it'll work just fine.

What is going to happen if I slap this drive in another box and fire it up ?

Curios in Orlando .....


Thanks :)

---

### Post by Stormbringer on 2006-02-17
Backing up up your old system before proceeding any futher is the best idea - this will leave you the option to revert back in case anything goes wrong.

Hook the harddrive onto another system and do a total backup. You can do this either by using the tarball method as explained in the thread you've mentioned above, or you can do it by using the Ubuntu Live-CD and/or any other Linux Live system (Knoppix, Damn Small Linux,...).

If you are done with the backup simply assemble the new system and connect the hard drive.

To my understanding Ubuntu doesn't rely on a static hardware config file (as in Fedora) --- all hardware is probed upon bootup.

If your new setup is different from your old one (speaking about partitions on the hard drive) it's best to edit /etc/fstab aforehand - otherwise you will run into problems during bootup.

Just give it a try and report back if you have any problems.

Cheers,
Storm.

---

