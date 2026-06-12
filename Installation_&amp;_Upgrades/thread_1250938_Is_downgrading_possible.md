---
title: "Is downgrading possible?"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by theregoesmyeye on 2009-08-27
I currently have ubuntu 8.04. If I upgrade to ubuntu 9.04 and I don't like it, is there any way I can downgrade and keep everything?

On that note can I even upgrade to 9.04 and keep everything? Similar to upgrading from windows XP to Vista, if you see what I mean.

---

### Post by oboedad55 on 2009-08-27
> **theregoesmyeye said:**
> I currently have ubuntu 8.04. If I upgrade to ubuntu 9.04 and I don't like it, is there any way I can downgrade and keep everything?

On that note can I even upgrade to 9.04 and keep everything? Similar to upgrading from windows XP to Vista, if you see what I mean.

Try the Live CD of 9.04 before you do anything. I always prefer a fresh install to attempting an upgrade. If you search these forums you will see lots of posts detailing upgrade disasters, or time-consuming fudges and fixes. Just backup your /home directory and have at it. Having said that, there is nothing wrong with 8.04. It is the most recent LTS release and if everything is working for you it's often best to let sleeping dogs lie. To answer your other question, no, it's not possible to go back to an earlier version of Ubuntu. I'd be shocked if it was.

Jon

---

### Post by wojox on 2009-08-27
Yes you can upgrade to 9.04, but you have to upgrade to 8.10 first. As far as not liking it and goind backwards I don't think it's possible.

---

### Post by dk06 on 2009-08-27
> I always prefer a fresh install to attempting an upgrade.

I'll second that!

Upgrades/Downgrades often don't turn out the way you hope them to (or the way I hope them to...lol)

I suggest backing-up before doing anything.

Just my opinion

---

### Post by theozzlives on 2009-08-27
If you have a seperate /home partition, choose manual partitioning while doing a fresh install. Choose not to format /home.

If you don't have a seperate /home, then I suggest you make one, here's how: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

As far as downgrading, you can do yet another install. Just DON'T FORMAT /home.

---

### Post by theregoesmyeye on 2009-08-27
> **theozzlives said:**
> If you have a seperate /home partition, choose manual partitioning while doing a fresh install. Choose not to format /home.

If you don't have a seperate /home, then I suggest you make one, here's how: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

As far as downgrading, you can do yet another install. Just DON'T FORMAT /home.


The article you shared with me was very in-depth. I didn't know that if I created my own separate home partition I could change distros when I pleased without losing my stuff. Good thing it was wrote for people like me who didn't think about it when installing:P

And a big thanks to everyone else who wrote in. I figure if I stick around here long enough maybe i'll be as proficient with Linux as I am with Windows. (this coming from a PC repair business owner.)

> **oboedad55 said:**
> Try the Live CD of 9.04 before you do anything. I always prefer a fresh install to attempting an upgrade. If you search these forums you will see lots of posts detailing upgrade disasters, or time-consuming fudges and fixes. Just backup your /home directory and have at it. Having said that, there is nothing wrong with 8.04. It is the most recent LTS release and if everything is working for you it's often best to let sleeping dogs lie. To answer your other question, no, it's not possible to go back to an earlier version of Ubuntu. I'd be shocked if it was.

Jon
 
I had jaunty installed and it just seems so much more responsive and faster.. It's just I was forced to downgrade due to problems with my ATI Radeon X1650 card not having support with any of the FGLRX, ati, or radeonhd drivers. Not to mention absolutely poor tvout support. When  I filed a bug, someone gave me a link to upgraded ati drivers that worked for the X1650, and I was going to try it. Maybe I should try the livecd first then.

---

### Post by oboedad55 on 2009-08-27
> **theozzlives said:**
> If you have a seperate /home partition, choose manual partitioning while doing a fresh install. Choose not to format /home.

If you don't have a seperate /home, then I suggest you make one, here's how: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")

As far as downgrading, you can do yet another install. Just DON'T FORMAT /home.

Correct me if I'm wrong, but is it not true that if you switch versions 8.10 to 9.04, or what have you, that you can run into problems with the old config files in /home/user not being suitable for the new system? That's the main reason I backup the partition but do not create a separate home partition. I'm curious to see whether or not my knowledge is correct.

---

### Post by Giampiz on 2009-08-27
Hi
There is no direct way to downgrade, but you could clone your disk or partitions by means of a specific live distro; I use Clonezilla for this, but you can find some more on the web;
I have a separate home partition, backup home partition and clone the whole disk on an external usb disk;
if I have troubles I go back to a previous "snapshot" of my pc by copying the last saved clone to my disk

---

### Post by Mark Phelps on 2009-08-27
> **theregoesmyeye said:**
> I currently have ubuntu 8.04. If I upgrade to ubuntu 9.04 and I don't like it, is there any way I can downgrade and keep everything?
Using the separate /home partition allows you to downgrade without losing the stuff under /home, but as to "everything" (e.g., changes to files under other directories), I can't attest to that.  If there's a way to reinstall without overwriting those files, then yes, you would keep "everything".
> On that note can I even upgrade to 9.04 and keep everything? 
Once again, "everything" is a LOT.  If you do an in-place upgrade using Upgrade Manager, you will retain nearly everything.  But, for example, if you've installed restricted hardware drivers from source, the upgrade won't be able to handle that and you'll have to rebuild from source against the newer kernel.  However, if you installed the same restricted drivers from a package, the upgrade will find the newer package and should take care of that for you.
> Similar to upgrading from windows XP to Vista, if you see what I mean.
If you're talking about the MS feature of automatically copying your current install into a "windows.old" directory which you can then mount (post-upgrade) and selective copy things back, then, no.

---

### Post by theregoesmyeye on 2009-08-28
After successfully biting my fingernails down to the cuticle, i've managed an upgrade to Ubuntu 8.10 (intrepid Ibex I believe?) I'm thinking that i'll just stop there since everything is working fine. All of my data is fine, applications, etc. Even tvout thank goodness. I did have to reinstall FGLRX though. With whatever drivers came with 8.10, in glx gears I was getting (maximum) 500 fps with my Radeon X1650. Now i'm getting around 4,000-5,000 fps, which is normal.

A big thank you goes to all who wrote in though!!!:KS

EDIT: I forgot to mention for some odd reason it seems as though the difference between 8.04 and 8.10 is tremendous. Bootup time seems slower but thats no worries to me. Firefox locked up around every 30-60 seconds on 8.04, but not on 8.10. Flash based items seem to run smoother also.

Is it my brain doing this or is 8.10 a bit more of a RAM hog than 8.04 though?

---

### Post by Mark Phelps on 2009-08-28
> **theregoesmyeye said:**
> ...  I did have to reinstall FGLRX though. 

Restricted drivers are tied to a version of the kernel.  If you upgrade the kernel (as you would do in upgrading to a newer version of Ubuntu), you will have to install a newer version of the restricted drivers.

However, be aware that ATI has discontinued support for lots of legacy cards.  So, if you're using an ATI card, and it's not one of the newer HD 3x or HD 4x series, upgrading beyond 8.10 to 9.04 will cause you to lose restricted drivers, as with 9.04, there are only open source drivers for the legacy cards.

---

### Post by theregoesmyeye on 2009-08-28
> **Mark Phelps said:**
> Restricted drivers are tied to a version of the kernel.  If you upgrade the kernel (as you would do in upgrading to a newer version of Ubuntu), you will have to install a newer version of the restricted drivers.

However, be aware that ATI has discontinued support for lots of legacy cards.  So, if you're using an ATI card, and it's not one of the newer HD 3x or HD 4x series, upgrading beyond 8.10 to 9.04 will cause you to lose restricted drivers, as with 9.04, there are only open source drivers for the legacy cards.

Unfortunately, I had learned that the hard way. I ripped open my new 9.04 Cd with excitement when I received it in the mail, only to find nothing but heartache with my now "legacy" card. How dare ATI call my card old :P

Mr. Phelps, moving on from my heartaches, would you consider Intrepid to use more RAM on idle than Jaunty? Or am I just hallucinating.

---

