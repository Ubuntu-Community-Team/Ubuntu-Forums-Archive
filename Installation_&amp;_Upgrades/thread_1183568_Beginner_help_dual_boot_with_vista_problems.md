---
title: "Beginner help: dual boot with vista problems"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by skawars on 2009-06-10
I decided to finally take the plunge and get Ubuntu on my new laptop aling with vista. I made a fairly hasty installation and booted from the Ubuntu disk and installed it "alongside my existing operating system" as a dual boot.

This has left me with a fair few problems.

When the installation attempted to Migrate my documents and settings, only my actual "documents" folder can be seen, there is nothing in music pictures or videos.

I attempted to download partition magic in uBuntu to sort out my partitions, but was unsuccessful as it said there was not enough disk space (presumably on the Ubuntu system partition). I changed the download location to my main partition which worked, but I was then unable to access this from the package installer.

I can access some of my main windows documents in Ubuntu, it shows my C drive, but if I go any further, for example into "Documents and Settings" in attempted to access my music etc, nothing is displayed.

It seems like i've just done everything wrong? I couldn't even play my Last.fm music in Rhythmbox because I didn't have an mp3 codec, which i attempted to download and fix and got a similar problem as when downloading partition magic.

Any help gladly received, thanks in advance.

---

### Post by sudeepk on 2009-06-10
try to use Gparted in ubuntu.
what is the problem u r getting when your download the packages.? are you downloading from synaptic or from the any online repository?

---

### Post by murray92 on 2009-06-10
Can you access other folders on your C: drive? If you are going to Documents and Settings to access your 'My Documents' folder, then it should display nothing because Vista is organised differently to other versions of Windows. Try going to 'Users' on your C: drive instead, thats where your 'My Documents' should be

---

### Post by skawars on 2009-06-10
it just seems like everything is set up wrong. in this "places" bit it has documents, music, pictures etc
the documents contains everything that is in my windows "documents", but all the others are empty.

this is the same when i go in from "dan".

i can't download anything to my desktop as it says drive is full.

i basically want to be able to use my windows documents as i do in vista from Ubuntu, and i thought this was reasonably easy to do.

i downloaded the .zip of gparted to a folder in c: called linux that i created, but when i went into the package manager i could access the files in C: but they were greyed out?

i typed parted into the package manager search and it said that a package called "parted" was already installed in System Administration but i couldn't find it.

even when i get a partitioning program up and running im not 100% how this will solve my problem. should i extend my existing Ubuntu system partition so there's room for stuff on the desktop, temporary download folders etc? but then i'll still be left with the problems accessing the main c: drive properly.

---

### Post by Bucky Ball on 2009-06-10
What you should do is take your personal data off your C: partitiond, download Gparted LIVE iso and burn a CD of it, then boot from that. It is never a good idea having personal data and OS on the same partition as if the OS irretrievably crashes, you have lost your data. Once you have backed up you data, boot from the Gparted CD you just made and resize your partitions, and create a ***shared*** data partition for your data, accessible from Ubuntu and Windows. Put your data back onto that partition.

This is a basic course of action which could be tweaked to suit your purposes. Just remember, you cannot resize or manipulate partitions that are mounted. That is why you must do this by booting from CD (doesn't mount drives/partitions).

Linux is not Windows. Be prepared to encounter some new concepts and slightly different ways of computing. Good luck with it. :)

---

### Post by skawars on 2009-06-10
Thanks, this sounds like it could work. I'm not an absolute beginner with linux/unix, i had a dual boot years ago but gave up because of USB DSL modems in the UK making things IMPOSSIBLE, and now i've got a new laptop feel its time to dive in.

Will update, thanks again.

---

### Post by presence1960 on 2009-06-10
The key words "fairly hasty installation" tell the story! Installing a new OS is not a minor undertaking and if unfamiliar with the process it is suggested that one do reading and studying to insure that one is familiar with the process and knows what they are going to attempt to do when they actually begin installing the OS. here are a few links that will get you up to speed:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Go here to download a free pdf Ubuntu Pocket Guide which BTW has a section with explicit instructions on the install process from the CD: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

I would suggest reading these prior to trying to install again. You used your computer for how long without Ubuntu? another few hours or days won't kill you.

P.S. Don't feel bad about your messed up install, a lot of us have learned the hard way- myself included. On my first attempt I read nothing and wound up wiping all my data from my hard drive. Luckily I had a backup. Which brings up another important point : **Always make back ups prior to installing any OS or partitioning! Even though they usually work flawlessly  anything can happen at any time. Don't get caught with your pants down. back up always, even when your computer is working fine. ALWAYS, ALWAYS have a back up.**

---

### Post by Zimmer on 2009-06-10
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Might be a bit late for the stable door now the horse has gone, but...
if you read here you will learn what you should have done and maybe work out what has gone wrong... and maybe even be able to go back and start again, provided Vista is still ok.
Basically the important bits are:

Vista is best partitioned/resized with its own partitioning tool.

Make sure you DO NOT INSTALL GRUB  to the MBR  but to the partition you are installing Ubuntu on.

Install EasyBCD to Vista and create an entry for Ubuntu....

---

### Post by dE_logics on 2009-06-10
I think you will need to reinstall everything...that's the best option, cause, yeah you can resize NTFS (from windows) but if you've formatted any drive with JFS (or a few file systems in general) it wont get resized.

What I did was backed up all my data...the main reason was cause gparted (a partition editor) could not detect the previous partitions...so I was left with no options.

Then I used the following partition schemes - 

The first partition will be obviously the boot partition...but I made it for windows also...this was a primary partition.

Then the rest I made extended, in that - 

5 GB for root, 4.1 GB for usr and 3GB swap (though 2 GB is much more than enough, but if you're insane, you will use that much too...like me).

Rest you can divide as you like...as per your needs.

One more thing, its recommended that you format the partitions 'wisely' with the right file systems so as to suit the type of files in there.

---

### Post by dE_logics on 2009-06-10
Actually you need to learn a bit about linux before using any Linux distribution...that solves most of the problems..........if you don't have technical support around (like I help around people with ubuntu).

If you want technical support, you can try Red Hat (Fedora)...they will come to you and fix the issue.

---

### Post by grand_tale on 2009-06-13
i know how it is to be a beginner and then just jump in. i had done that and had the same problems. not exactly but i f*ed up my mbr and i just didnt know what to do. so this time i read a bunch of stuff and understand a bit more about linux. if you want a complete newbie guide of linux and a good beginners language tutorial, go to [www.linuxnewbieguide.org](www.linuxnewbieguide.org). 

:popcorn:

---

### Post by Bucky Ball on 2009-06-13
Nice link, I am passing it on to my mother-in-law who has dived in after years of Windows, and good on her! That guide is perfect.

Thanks for posting. :)

---

