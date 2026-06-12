---
title: "install problems, partition issues"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by the_artz19 on 2009-08-23
i downloaded and ran the ubuntu 9.04 cd recently, but i haven't successfully installed yet. i have two main partitions, one for vista, and another that i made for ubuntu. i cannot seem to select just that partition during the install. most the roads i take, ubuntu tells me that something is in progress at that momment and wont be able to take effect untill it restarts. yet even when i ignore, it still says that there is an error and goes back to the partition manager. the partition manager also seems to show less free space than i thought i had overall(since my main has 20gb free and the ubuntu partition is at least 26gb), and it in some views shows that the free space is in small bits.
i am not sure if any of this makes sense, but it is problems like this that makes me consider using wubi again. since that was a lot more clear the last time i attemtped a ubuntu install. however i was told it wasnt that pollished when i last tried(8.10), and possibly for that reason... it didnt work then either. im not sure if that has changed, but it seems that my luck with computers, combined with me thinking making a seperate partition myself was a good idea....has but me into some anti ubuntu rutt.

any help would be apreciated.

---

### Post by VMC on 2009-08-23
Have you tried to do a custom or manual install from Ubuntu livecd install?

Also from livecd output from a terminal: ```
sudo fdisk -l
```

---

### Post by the_artz19 on 2009-08-23
i cant say that i have, nor that i have any clue how really. i have only gone as far as using firefox, and the several failed attempts at installing ubuntu.
i am amusing that i would need to open some terminal or something in ubuntu to do what you recommend. but like i said i am now tempted to try a install through windows again.

---

### Post by the_artz19 on 2009-08-26
can anyone help me/give me a step by step on how to preform this alternate install?
i guess it might have been wrong for me to try and make that separate partition for ubuntu first, perhaps if i could get rid of it it would make it easier. yet all that i looked into seemed to point to deleting a partition to be bad.

can anyone comment on wubi installer? is it better since 8.10?
dont want to spam in another post just to give myself a bump, but i am eager to use ubuntu.

---

### Post by Bartender on 2009-08-26
artz -

You don't give much information, but you want a specific guide to something that's been discussed on these forums about a million times.

How about posting the output of fdisk -l as was requested?

Maybe post a screenshot of what the partitioner is reporting.

By "free space" do you mean what Windows reports?  Ubuntu needs a stretch of space without any Windows data.  If the drive is horribly fragmented and has Windows data scattered all about, Windows will still report the spaces in between as "free space".  That kind of free space doesn't get you any closer to installing Linux.

From everything I've read, wubi is great for trying out Ubuntu, but it should not be considered a permanent solution.

---

### Post by the_artz19 on 2009-08-26
sry about the lack of information, i will try to write down what messages i get next time i am trying it.
as far as the f disk command, i cant say that i know how to access the terminal to put that in.
also, i am not sure if formatting something in windows as a separate partition for ubuntu, makes it harder to actually be used for ubuntu. but that is exactly what i tried initialy, and i am not sure if there is any way to reset that to just free space.
with that said, i think my drive is fairly fragmented, since when i run auslogics defreag it shows up with more red than anything. i have run that serveral times, but i am not sure if that will get me anywere.
unfortunately, the only solution might be to reinstall vista,but i only have an upgrade disk. so that would be my last idea for right now.

not sure if that helps at all, but i will try again to write down any messages i get when im in ubuntu.

---

### Post by marpiacas on 2009-08-26
hi, i'm having probs too. so i installed all good and now i want to update, but it says i have no space! the window says:

The upgrade needs a total of 399M free space on disk '/'. Please free at least an additional 398M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'

but when i was doing the partitioning thing, it looked like there was space. furthermore, when i opened the terminal and typed that in it was like, no nonexisting command or something. 
so i'm a total newb and i'm pretty sure i accidentally erased windows. hating my actions right now. 
any help would be much appreciated.
i hope i didn't do one of those badly worded questions that so irrates ubuntu wizzes.

---

### Post by raymondh on 2009-08-26
> **the_artz19 said:**
> sry about the lack of information, i will try to write down what messages i get next time i am trying it.
as far as the f disk command, i cant say that i know how to access the terminal to put that in.
also, i am not sure if formatting something in windows as a separate partition for ubuntu, makes it harder to actually be used for ubuntu. but that is exactly what i tried initialy, and i am not sure if there is any way to reset that to just free space.
with that said, i think my drive is fairly fragmented, since when i run auslogics defreag it shows up with more red than anything. i have run that serveral times, but i am not sure if that will get me anywere.
unfortunately, the only solution might be to reinstall vista,but i only have an upgrade disk. so that would be my last idea for right now.

not sure if that helps at all, but i will try again to write down any messages i get when im in ubuntu.

Artz,

Boot into the liveCD and TRY UBUNTU WITHOUT CHANGES (known as a live session).

In a live session, access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

Copy/paste what the terminal outputs in your next post.  If you could, let's also have a visual of what your HD looks like.  Same live session, quit/close the terminal and access gparted (system > administration > partition editor).  It will produce a visual.  Press ALT + Printscreen and save it to your desktop.  When you post back, click attach (beside the smiley on top) > browse to your desktop > upload and wait for it to be done.

With the fdisk and gparted output, we can visualize a plan for you.

Try to complete the defrag and do back-up your files.

---

### Post by raymondh on 2009-08-26
> **marpiacas said:**
> hi, i'm having probs too. so i installed all good and now i want to update, but it says i have no space! the window says:

The upgrade needs a total of 399M free space on disk '/'. Please free at least an additional 398M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'

but when i was doing the partitioning thing, it looked like there was space. furthermore, when i opened the terminal and typed that in it was like, no nonexisting command or something. 
so i'm a total newb and i'm pretty sure i accidentally erased windows. hating my actions right now. 
any help would be much appreciated.
i hope i didn't do one of those badly worded questions that so irrates ubuntu wizzes.

Hello Marpiacas,

Welcome.  

Access a terminal and type

```
df -h
```

That will show you allocations and usage.  I have a hunch you have the 2.5GB install but want to be sure.

Also, 

```
sudo fdisk -l
```

which will show what your disk has (windows or not).

Lastly, kindly post those results in a new thread so as not to confuse this issue with that of the original posters' (and the forum as well).  I will try to follow/look for your username and a new thread.

---

### Post by marpiacas on 2009-08-26
yess!! thanks! i haven't finished, but just telling me what to type has already made me so happy!:KS

here's what happened first:
marpiacas@marpiacas-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G  152K 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  108K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  148K  497M   1% /dev
tmpfs                 497M   76K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             7.6G  6.7G  855M  89% /media/Recovery

the second thing:
marpiacas@marpiacas-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G  152K 100% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  108K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  148K  497M   1% /dev
tmpfs                 497M   76K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             7.6G  6.7G  855M  89% /media/Recovery

lastly, the third thing
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cdc7628

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         981     7873536   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         981       14268   106726872    7  HPFS/NTFS
/dev/sda3           14269       14593     2610562+   5  Extended
/dev/sda5           14269       14571     2433816   83  Linux
/dev/sda6           14572       14593      176683+  82  Linux swap / Solaris
marpiacas@marpiacas-laptop:~$ 


this all means nothing to me. 
thanks a bunch!!

---

### Post by raymondh on 2009-08-26
> **marpiacas said:**
> yess!! thanks! i haven't finished, but just telling me what to type has already made me so happy!

Am glad .... kindly create a new thread and repost the outputs so as not to complicate artz' thread and issue.

I will follow you there (on your new thread)

---

### Post by the_artz19 on 2009-08-30
thank you for you response and further details. after accessing the terminal and entering what you asked i recieved this back.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           8       26164   210102380    7  HPFS/NTFS
/dev/sda2           26164       29662    28098578+   f  W95 Ext'd (LBA)
/dev/sda3           29989       30393     3253162+  db  CP/M / CTOS / ...
/dev/sda5           26164       29662    28098578    7  HPFS/NTFS

also attaching picture of partition edditor. i am not sure if it is too bad off to fix really, but like i said. all partitions were done in windows, hd is around 200+ and i had made that one 20gb partition for ubuntu.

thanks again for your help.

---

### Post by drs305 on 2009-08-30
> **marpiacas said:**
> yess!! thanks! i haven't finished, but just telling me what to type has already made me so happy!:KS

here's what happened first:
marpiacas@marpiacas-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="DarkRed"]**/dev/sda5             2.3G  2.2G  152K 100% /**[/COLOR]
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  108K  497M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  148K  497M   1% /dev
tmpfs                 497M   76K  497M   1% /dev/shm
lrm                   497M  2.4M  495M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda1             7.6G  6.7G  855M  89% /media/Recovery



It appears you are a victim of the Ubuntu "side by side" installation procedure. During Step 4, you must resize the Ubuntu partition or it will create one only 2.3-2.5 GB. I consider it a bug, it's been reported, but not fixed as far as I know.

I wrote two guides. One tells you how to repeat the installation and avoid the same mistake. The second tells you how to take existing space from Windows and transfer it to the Ubuntu partition. One takes about as long as the other.

[HOWTO: 2.5 GB System Partition - What Went Wrong?]("http://ubuntuforums.org/showthread.php?p=7658271#post7658271")

[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by the_artz19 on 2009-09-04
could some one take a look at the info and pic included im my last post please. just wanted to make sure that it didnt get lost in whatever other help was being provided on my post.

---

### Post by Bartender on 2009-09-04
Hi, artz -
Reread your post from the start.  Good job posting a screenshot.  You tried to make a partition for Ubuntu from inside Windows, correct?  That might work, but there are more reliable methods.

Such as GParted LiveCD, the handiest tool AFAIC.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
  

Have you read the Community Docs?  This one is actually pretty good
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
and it links to other good articles.  Notice the Dell link, which helps explain recovery discs.

Speaking of which, have you made your recovery discs?  If not, please do so immediately.

That unallocated area in front of Windows bugs me, but I'm hesitant to suggest that you instruct Windows to move into that space because I don't know for sure that Windows would do it successfully.

How do you feel about deleting the Dell recovery partition?  Some people get rid of the recovery partition after making their recovery discs, but some people don't.  I helped some friends set up a new laptop from HP last year.  HP stated right in their paperwork that the recovery partition becomes unusable after burning the recovery discs, so the user can delete it if they want!  But every manufacturer does things differently and I don't know for sure how Dell handles things.

I'm assuming that sda5 is the partition that you made from within Windows?

I'll tell you what I'd do, but take this with a grain of salt because I don't know what you want to do about the Dell Restore partition (sda3, a primary NTFS partition) and I'm not sure that sda5 (a logical NTFS partition within the sda2 extended partition) is the one you created.

I'd create a GParted LiveCD, then boot from that CD.  I'd delete sda2 and sda5.  Then I'd combine all those unallocated bits and pieces into one extended partition.

If you have access to broadband, watch a couple of GParted YouTube videos to see how it's done.

After you have one extended partition, you then need to think about what you want to do next.  The simplest thing to do would probly be boot into your Ubuntu LiveCD and install Ubuntu to the extended partition automatically.

BTW, Windows looks like it's getting crowded.  You should start to see it slow down as you run out of free space.

---

### Post by presence1960 on 2009-09-04
> **Bartender said:**
> Hi, artz -
Reread your post from the start.  Good job posting a screenshot.  You tried to make a partition for Ubuntu from inside Windows, correct?  That might work, but there are more reliable methods.

Such as GParted LiveCD, the handiest tool AFAIC.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
  

Have you read the Community Docs?  This one is actually pretty good
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
and it links to other good articles.  Notice the Dell link, which helps explain recovery discs.

Speaking of which, have you made your recovery discs?  If not, please do so immediately.

That unallocated area in front of Windows bugs me, but I'm hesitant to suggest that you instruct Windows to move into that space because I don't know for sure that Windows would do it successfully.

How do you feel about deleting the Dell recovery partition?  Some people get rid of the recovery partition after making their recovery discs, but some people don't.  I helped some friends set up a new laptop from HP last year.  HP stated right in their paperwork that the recovery partition becomes unusable after burning the recovery discs, so the user can delete it if they want!  But every manufacturer does things differently and I don't know for sure how Dell handles things.

I'm assuming that sda5 is the partition that you made from within Windows?

I'll tell you what I'd do, but take this with a grain of salt because I don't know what you want to do about the Dell Restore partition (sda3, a primary NTFS partition) and I'm not sure that sda5 (a logical NTFS partition within the sda2 extended partition) is the one you created.

I'd create a GParted LiveCD, then boot from that CD.  I'd delete sda2 and sda5.  Then I'd combine all those unallocated bits and pieces into one extended partition.

If you have access to broadband, watch a couple of GParted YouTube videos to see how it's done.

After you have one extended partition, you then need to think about what you want to do next.  The simplest thing to do would probly be boot into your Ubuntu LiveCD and install Ubuntu to the extended partition automatically.

BTW, Windows looks like it's getting crowded.  You should start to see it slow down as you run out of free space.

+1
You aren't going to get better advice than that!

---

