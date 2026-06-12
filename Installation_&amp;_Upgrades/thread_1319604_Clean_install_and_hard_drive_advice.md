---
title: "Clean install and hard drive advice"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by redjedi on 2009-11-08
Hi

I'm soon going to be installing the Ubuntu 9.10 and was looking for a little advice before going ahead.

I've decided to do a clean install instead of up-grading ffrom 9.04 because
1) as a newbie to Linux in Jan I messed around quite a lot, getting things working (esp graphics), and probably changed things I shouldn't have, so want to start fresh.

2) I went for the safer option of the 32 bit OS, and as I have an AMD64 processor I want to install the 64bit version this time.

My main question is about keeping all my data. I'm going to install a second hard drive and move all of my data across to it before my main HD gets formatted, but do I need to do anything special with the second hard drive to stop it getting formatted at the same time?
I was planning on being overly cautious and actually removing the HD while I installed and set up 9.10, but I'm sure this wouldn't be necessary, am I right, or should I play it safe?

---

### Post by lidex on 2009-11-08
If you're paranoid, go ahead and remove it. It really shouldn't be an issue though. I would recommend formatting drive with a separate /home partition when you do install.

---

### Post by hal10000 on 2009-11-08
If you have a separate /home partition, then you should leave the harddrive in your system during the installation process. You can then easily take over your old user(s) existing home directories to be used with the new system, you just have to create the same usernames as you did in your old installation.

But if you do this, you have to do a manual partitioning during the installation, so you can tell the system where to find the /home partition.

Of course you have to take care to choose the correct harddrive and partitions for your / and swap.

If you decide to plug off your harddisk, then you will have additional work to get the existing /home and/or data partitions running again (but it's not too much work).

---

### Post by redjedi on 2009-11-24
Right, I'm finaly getting my act together on this.

I've ordered a new hard drive. A Western Digital Black caviar 640GB.

I want this to be my main HD, as it's a lot better than the one I currently have.

I'm thinking of doing my clean install like this.

Remove old HD
Install new HD
Boot up and install 9.10 64 bit.
Re-install old HD, and copy data across.
format old hard drive

I'm just going to use my old HD as a secondary/back-up one.

Does this process sound like a good way to do it, or is there an easier way?

Thanks

---

### Post by dddanmar on 2009-11-24
That's how I'd do it.

I agree though, its easy to tell in the installer what drive is what, but while you've got the case open, don't tempt the gods with the extra drive in. Once your machine works with the os, reboot with the drive in and start poking around fdisk -l if it doesn't automount for you to copy the files in nautilus.

---

### Post by darkod on 2009-11-24
I would recommend:
1. Leave old drive in.
2. Install new drive (if you have space).
3. Set in BIOS the new drive to be first choice HDD for boot.
4. Install Ubuntu 9.10 and continue as planned.

I have seen people reporting problems when they play with drives moving them around and it seems to make a difference how many drives were present when ubuntu was installed and what was their boot order in BIOS.
Grub2 uses UUID so moving drives shouldn't be a problem but it seems it gets stuck at the root(hd0,0) command. BIOS seems to assing hd0, hd1, etc according to the boot order in BIOS so you have to b careful when adding/removing drives. I would just leave the old one in, it can't do any damage.
You will set BIOS to boot from the CD-ROM anyway so the boot process will not even reach your old drive. And don't forget setting the new drive as first choice HDD, that's usually separate setting from the 1st choice CD-ROM, 2nd choice HDD, etc.
It sounds easier having only one drive in during install but you are risking confusing grub2. Unneeded risk IMHO.

---

### Post by redjedi on 2009-11-24
Not being the most technically experienced, I'm worried about losing all my data.

If I leave the old HD installed, and set the New HD to boot first and do a fresh install, will any Ubuntu info be copied across?

I want to start completely fresh with the new install, as I'm sure I've made quite a few mistakes with this one.

How easy is it to remove all Ubuntu only data from the old HD, once the new one is up and running?

---

### Post by darkod on 2009-11-24
No data will be copied over automatically. You will choose what you want copied and copy it yourself once you have ubuntu up and running.
No problem about copying, you will mount the old hdd and just copy whatever you want to. But it depends what you want copied, are we talking about music, videos, etc or program settings from your old ubuntu install?
For personal data, docs, music, videos etc you literary just mount the old drive and copy what ever you want.
But if you want to move software settings etc you will have to read around for migration scenarios or ask someone with more experience about it. I haven't migrated myself, new to ubuntu also.

And just because you are unexperienced I suggested not to remove the drives one by one because you leave more room for mistakes that way. And then you will not know why your new ubuntu is not working. If I understood correctly you plan to use the old drive as secondary too. My first rule is always to put all the hardware together that you plan to use, and only then to start installing any OS. It's better for the OS to know what hardware is there right away.
After all, you plan to use the computer with both drives inside then why put them one by one?

---

### Post by redjedi on 2009-11-25
Cheers Darkod

It will be just data, i.e.  movies, music, documents.

So I should set the boot sequence as 

CD > New HD > Old HD (maybe disable boot from old HD to start with)

Install new OS

Copy data over to new HD 

format old HD.

Should be easy :P

---

### Post by redjedi on 2009-11-27
Almost success.

I've installed new HD, then installed 9.10 onto it, leaving my old HD along with 9.04 alone.

Set the boot sequence to boot my new HD first, but it won't boot (doesn't start/initialise GRUB)

Try booting old HD first and 9.10 start-ups.

OK???

Now I'm copying data from old HD new new one.

But I want to remove 9.04 from old HD, but I don't want to just format it because I guess that's where the GRUB(?) is being stored.

How can I move the GRUB to my new HD, so I can format old HD??

---

### Post by darkod on 2009-11-27
Item number 12:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Since you have two hdds be careful to specify the one where 9.10 is, whether it's sda or sdb, and the correct partition where root of 9.10 is, for example /dev/sdb1. The rest is easy.

---

### Post by redjedi on 2009-11-27
Ok I think I know what to do.

Should I do it AFTER I have formatted my old HD with 9.04?

---

