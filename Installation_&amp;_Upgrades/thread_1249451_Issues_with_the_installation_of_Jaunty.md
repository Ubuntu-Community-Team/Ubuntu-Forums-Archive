---
title: "Issues with the installation of Jaunty"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by heathramos on 2009-08-25
I have just built a new PC and I was trying to install Ubuntu on it but I have been having all kinds of issues with it. I have got past a few of them (the installer didn't like the dvd-rom connected to the sata card and the wireless usb keyboard stopped functioning during the installation) but after 3 days I still can't complete the install.

What I am trying to do is set up a software raid during the install (RAID1) and install the OS on it. Most of the issues I am having is either manually creating the partitions needed or formatting them. I boot from the cd and answer the prompts until I get to the partioning section. I choose to set up things manually. I have tqo 1tb drives that I am trying to mirror so I create 3 partitions on each (20gb on the first, 512mb for the 2nd and the remaining free space for the 3rd) and set them as raid partitions. I then set up the software raid (choose the matching partitions and set them as raid1). In the end I have the 3 RAID devices. I configure the 20gb device to use ext3 and mount to /, the 512mb device is swap space and the 967gb device is mounted to home and uses ext3 as well.

My issues are that it freezes as various points during this process. Sometimes when I create the raid device, the screen will just turn blue and sit there. I can't see any hard drive activity and eventually I have to hard boot it. I tried to start over at one point and it would not let me delete the raid devices (kept saying the devices were in use even though I booted off the cd and never got to the point of installing anything). I tried erasing the raid device I couldn't delete and the screen again turned blue and just sat there, which forced me to reboot it after awhile.

At this point I have created the 3 raid devices and it is trying to format. It has been on the 33% done screen for 9 hours now.

any help would be appreciated.

---

### Post by raymondh on 2009-08-26
Hope the [fakeraid how-to]("https://help.ubuntu.com/community/FakeRaidHowto") can give you clues.

Good luck.

---

### Post by heathramos on 2009-08-27
> **raymondhenson said:**
> Hope the [fakeraid how-to]("https://help.ubuntu.com/community/FakeRaidHowto") can give you clues.

Good luck.

thanks

it ended up being bad ram

I finally got the OS installed

now if I could only get the raid5 set up for data.

my computer froze while creating the raid device after a few hours (the last time I checked it was 27% done).

I'll have to delete and recreate the device and see if it works the second time.

I hope there aren't anymore hardware issues.

It will end up being pretty large (6 2tb drives) so it will take awhile.

---

### Post by eashwer on 2009-09-03
I have JAUNTY's ISO and I get 3 choices for the applicaiton to open it with
1. Archive manager
2. CD/DVD Burner
3. 

I dont know how to install from an ISO
I am on 8,04 now going to Jaunty 9.X

WHat is the very next thing that I have to do in order to get the installation/upgrade going?

> **heathramos said:**
> thanks

it ended up being bad ram

I finally got the OS installed

now if I could only get the raid5 set up for data.

my computer froze while creating the raid device after a few hours (the last time I checked it was 27% done).

I'll have to delete and recreate the device and see if it works the second time.

I hope there aren't anymore hardware issues.

It will end up being pretty large (6 2tb drives) so it will take awhile.

---

### Post by presence1960 on 2009-09-03
Eashwer you need to burn the iso as an image to CD-R or create a bootable USB from the iso with Unetbootin or USB Startup Disk creator.

In the future please don't hijack someone else's thread. It makes it harder for those helping & being helped when there are multiple problems being addressed. Start your own thread please.

---

