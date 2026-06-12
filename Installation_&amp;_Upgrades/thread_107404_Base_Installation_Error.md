---
title: "Base Installation Error"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by greywell on 2005-12-22
Hello all,

     I am currently trying to install Ubuntu 5.10 onto my somewhat aged (about 4 years old) computer. The installation process goes fine, until it starts to retrieve the base packages that it installs from the web. It will do great until it hits 6%. Once it hits that, it seems frozen, but it's just moving very slowly. I had to leave it overnight (and this may help: I have a 633MHz processor with 256MB of RAM and a perfectly operational network connection) and when I came back, there was an error of some type; sorry, but I was so frustrated that I didn't take note of it. I didn't check the md5sums yet, so I'll have to do that this weekend sometime, as I do not currently have ANY access to it, while it IS running a Ubuntu 5.10 LiveCD. I am also ordering a CD to make sure that the md5sums are correct. Could someone help me by telling me what might've went wrong? If you need more information, I'll provide it. Thanks!

---

### Post by randy on 2005-12-24
Have you run a bad block check on your hard drive?  I have experienced several different problems similiar to that due to bad blocks/sectors on a hard drive.

---

### Post by sisco on 2005-12-24
Install error; my son was give a cd with ubuntu 5.1 install and a live cd and both do the same thing: all that shows is a dead screen with a cursor in the left hand corner that won't move so since this is the first experience with ubuntu I don't know what is wrong.  The system is old.  Any suggestions?

---

### Post by cker on 2005-12-24
Hi - I have the same problem

I am trying to install Ubunto 5.10 on my computer and am having some trouble.

the installation seems to go well but after I remove the CD and reboot and while the installation is installing the packages the computer shuts down (about 65% into the installation of the packages).

the message I have been getting is that there is a problem - either not enough space (I do not think this is the problem) a bug in the disc (again I do not think so because I tryed 2 different discs) or something else.

when I boot after this stage I am prompted to login with my user name and password and after I do that I receive something that looks like this:

[usr][host]:~>

I tried doing a startx and this is what I got:

giving up.
xinit: Connection refused (errno 111): unable to connect to x server
xinit: No such process (errno 3): server error.

Any ideas?

---

### Post by greywell on 2005-12-24
My reply to:

randy:

I dont think its a disk problem, because I had a perfectly good SuSE Linux 10.0 install on it.

sisco:

That might be a graphics card problem. How old is it? Did it come with the computer? It might also be a bad install on your disk/bad ISO you downloaded. You might want to reinstall it or download a new CD.

cker:

Ive never experienced that. It might've been a bad CD. Try checking the md5sums of the ISO you downloaded and get back to me!

-greywell

---

### Post by Luke771 on 2005-12-24
I am a newbie myself, I'll only talk about how I did it.
A long post that doesn't say much, other than "check your time zone" -  that's it
How I got that? Well my First (and second and third) Ubuntu installation went exacly like yours: it freezed at 6% retrieved packages.
My computer is somewhat less old but no factory-new either (1600MhZ, 512RAM, 40GBhdd)
It was the first time I tried to install Linux, I had been thinking about doing "The Switch" long enough, but never tried it.
It kept "freezing" 6% retrieved packages, and after several hours said that it was not possible to continue installation. Frustrating.
I had Windows already installed and I wanted to set up a dual-boot system, so my partitioning included a Windows NTFS partition and a file storing FAT23 partition
As you know, you should have two Linux partitions on your hard disk: one ext3 and one linux swap.
After every failed installation I deleted and re-created the partitions using Partition Magic boot-cd (easily available on BitTorrent),
The fourth or fith time I started to think, what can I have done wrong?
I ran the installation in English though I dont live in an English speaking country because it is easier to follow eventual instrucions and tips without having to translate (90% of the Internet is still in English, even if some people dont want to get used to it)
When the installation program asked me about my location I just hit "next" without really checking that the location was set to my country (a western european country, not France, thanks God) (just kidding)
Well, the third or fourth time the installation failed, I checked every step.
boot from Partition Magic
delete partitions (linux ext3 and linux swap)
recreate partitions (ext3, swap)
format them
boot from Ubuntu-cd
set  language to English (or whatever)
...and ladies and gentlemen...here comes...
     ---IT!!!----
(er, actually, it may be it or  it may be not it)
set the location to your REAL location (or one in the same time zone)
I'm not sure about that, but that was actually the only thing I changed: it did not work before I did that,  and it DID work after, so it could be "it" after all...
then, when it comes to partitions,
manually edit the partition table
mount the linx partition as / (the root directory), format it and MAKE IT ACTIVE
   --if dual boot---mount the eventual fat32 partition as /media/somename (the important part is that it is in the /media directory)
                          -mount the windows partition as /windows
                           (don't format these two)
OK; at this point it should go straigt down to the end, it worked for me.
As I said, the only thing I changed was the location, unaccurate when it freezed and accurate when it worked; I still refuse to beilive that it was the reason why it didnt work the first 2-3 times, but I dont see any other explanation: Maybe it was the different time settings it was getting from the hardware clock and the internet (I have a 24/7 cable connection), i don't know, and I dont have any reason to presume that you did not set the your real location on install, I'm only telling you how it went for me.
And one more thing, I dont really know if it does make some difference or not, but I delete and re-create the partition when I reinstall an OS. Maybe just formatting does as good, maybe not.
       --------(If you are dual booting, DONT install GRUB (boot loader) in the main boot record, but it in your Ubuntu partition, assuming that you have Windows on the first partition, you should choose the second partition of the first hard disk; the count begins from zero both for disks and partition, so you have to enter hd0,1)
yeah, ok, that was really all, not bad for a first post huh?

---

### Post by cker on 2005-12-25
Thanks Luke,

I will try doing that - I have a bit of a problem because my computer is rather old and not connected to the internet so there is a good possibility that the time zone is f!!@#!@# - usually it starts up as 1.1.1999

since it is not online it fails to read accurate time each time I boot so it might be the problem - not that I know how to overcome this issue. 

It is certainly something to look at - I will keep you posted if that works

Thanks again and happy holiday
Eyal

---

### Post by greywell on 2005-12-25
Hmm.. that might work... I'll have to try that again tonight.... But what I don't get is that during every other Linux installation, I choose USA/Chicago (It was the only thing that I was SURE was in my time zone, which is Central) and it worked fine. I don't know how it affects this, but who knows? Oh, an if you know ANY city near or within Louisiana in the Central Time Zone that I can use, PLEASE tell me!

-greywell

---

### Post by ed_d on 2005-12-26
Greywell, dont worry about the timezone USA/Chicago. Its just a general reference to the timezone area. I live in MN, and that is just what I have always used in the past. As far as installing on "old" pcs, I had installed ubuntu on an armad 700 laptop (700mhz, 128mb mem) and it went fine.

---

