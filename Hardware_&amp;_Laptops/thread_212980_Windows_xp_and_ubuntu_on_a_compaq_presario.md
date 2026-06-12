---
title: "Windows xp and ubuntu on a compaq presario"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by chuckn on 2006-07-10
I really appreciate all the good, helpful information on these forums. It certainly helps when you're new to linux. 

I have been running ubuntu from a live cd, and have installed it completely on my desktop. Now I would like to install in on my laptop, and keep my windows xp.

My question is, when i install ubuntu, should i set up a separate partition for data (both windows and ubuntu. This would certainy help if i ever lost the OS, and had to reinstall.

Also, do you know of a simple, step-by-step tutorial on how to do this?

Thanks, and blessings.

Chuck

---

### Post by the_maassk on 2006-07-10
Here is the paritioning scheme I am using on my Presario (it works for me):

10 GB for Windoze XP (NTFS)
6 GB Ubuntu / (root)
3 GB Ubuntu /home (keeps all my working data and config even if I have to reinstall my base Ubuntu)
1 GB Ubuntu Swap (don't need it any more coz' I upped my RAM to 1 GB recently)
20 GB FAT32 (all data), 'rw' from both Linux and Windoze

Steps:

1. Make sure you install Windoze first. Give it 10 Gigs and let it install. Leave all other space unformatted.

2. Install Ubuntu. Assign space to partitions as required. Let it install.

3. GRUB would detect your XP install and add it to the bootloader.

4. Boot into XP and format the remaining space as FAT32.

Churn out your own XP recovery CD (without apps installed). I don't care much about it any longer since I shifted full time to Ubuntu around 6 months ago.

Configure your Ubuntu install with all the apps you want and then back it up using Mondo onto recovery CDs (it saved my *** a few times!).

---

### Post by chuckn on 2006-07-11
Thanks for all the help Maask.

I successfully partitioned my harddrive as follows:

25 G - Windows
9 G - / (root)
1 G - swap
25 G - /home.

After changing the partitions, Unbuntu was a breeze to install.

A couple of more questions, if you don't mind. Can I use fs-drive to access my /home directory from windows? Also, does your Compag have a wireles card? If so, are you running wep or wpa? I need wpa to connect to my linksys wireless router.

Thanks, and have a great day

---

### Post by the_maassk on 2006-07-12
I love the questions; after all that is what Ubuntuforums is all about!

You can use fs-drive to access Linux partitions from Windows. However, my personal experience was not too good with them. I happened to install them and access data off my Linux partitions. A reboot later, Ubuntu refused to boot properly. I was 'forced' into a fsck (disk check) and it found lots of problems with my ext3 file system :mad:. Thankfully for me, it did repair most of it. Some of my config files got corrupt too. My XSession was corrupt and I had to manually edit it.

That said - fs-drive does seem to work for most people out there - maybe I was just plain unlucky! I'd read up more on it before trying it again.

On the wireless - My Presario has inbuilt Broadcomm Wi-Fi in it. I was using ndiswrapper with Breezy but I don't have to use it any more with Dapper. It native, once you use the appropriate microcode. I have not used WPA yet because the routers I connect to, didn't need it. However, I'm planning to buy a Netgear router/ AP and will try WPA with it. Will let you know how it goes. You can hunt the forums for info on WPA. I'm sure someone already uses it!

Best of luck! :p

---

### Post by gazza567 on 2006-07-12
I got a question

My Presario wont let me change the partition size. I cannot shrink my windows  XP partition size :(

I currently have 6GB for linux and want to change that. Ive tried PQMagic, qparted and other tools

---

### Post by blu.gecko on 2006-07-12
Dude, since when is broadcom on a compaq presairo native, Ide like to know how you did that, I had to se bcm43xx-fwcutter and a firmware drive to exstract to make it work.........
](*,)

---

### Post by chuckn on 2006-07-12
Thanks for all the help. I am up and running with a dual boot nicely now. I can access all of my files from windows from within linux, but not the other way around.

I am having major problems connecting to the iternet thru Ubuntu. Connection is great on the windows side, but nothing on the Ubuntu side. I can't even connect when I plug a network cable directly into my laptop.

Am i missing something? How do I go about getting conected. I would prefer to go the wireless route if I could.

Thanks, and have a great day!

Chuck

---

### Post by ShirishAg75 on 2006-07-19
> **the_maassk said:**
> I love the questions; after all that is what Ubuntuforums is all about!

You can use fs-drive to access Linux partitions from Windows. However, my personal experience was not too good with them. I happened to install them and access data off my Linux partitions. A reboot later, Ubuntu refused to boot properly. I was 'forced' into a fsck (disk check) and it found lots of problems with my ext3 file system :mad:. Thankfully for me, it did repair most of it. Some of my config files got corrupt too. My XSession was corrupt and I had to manually edit it.

That said - fs-drive does seem to work for most people out there - maybe I was just plain unlucky! I'd read up more on it before trying it again. 


   Hi massk, 
               Lemme share my fs-driver experience with you.  As everybody knows fs-driver is installed in control panel. So I toggle it to give something like Y or Z: to mount it for tht period in time & then unmount it again when I don't need it. I've been using for almost 3 weeks without any issues. Of course this is been on the desktop rather than the laptop, but who knows perhaps u'r irritance may be solved this way :)

---

### Post by the_maassk on 2006-07-19
Shirish - I might try, but I'm chicken right now :-D 

Here is another issue I'm facing:

[http://ubuntuforums.org/showthread.php?t=218140](http://ubuntuforums.org/showthread.php?t=218140)

Any ideas?

---

