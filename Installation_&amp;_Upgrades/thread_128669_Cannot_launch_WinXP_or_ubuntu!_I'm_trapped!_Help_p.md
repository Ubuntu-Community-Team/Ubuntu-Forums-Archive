---
title: "Cannot launch WinXP or ubuntu! I'm trapped! Help please!"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by executex on 2006-02-12
Yes i'm sort of panicking, because today i decided i should stop chickening out and just go for it, and install ubuntu and make a partition on my WinXP comp! Guess that was a bad idea. It did the partitions successfully, so i thought everything was cool, then the computer restarted and it said installing the last of the packages. Then suddenly at like 70% it says "some packages have failed to install, you must install them manually or else things will not work". And then i said "ok", and then the command line comes up, the terminal thing, but in DOS. 

It asks me for my password and username, and i log in. and get $ sign.
Now i look around with ls and dir, which is practically the only commands i know for linux.

I have read all the tutorials and articles before i started this installation. And the posts about Dual install. So i thought everything would work out fine. Since most people who had the slightest problem just used ubuntu to get winXP to work again, my problem is , i can't get either to work.
I can't launch ubuntu, only some sort of DOS terminal version of ubuntu, which i dont know how to use.

When the GRUB launcher comes it says Should i launch win xp or ubuntu, and when i pick Win XP, it just stays at a black screen, and doesn't launch.

Now i'm stuck using the live CD, at annoying 640x400 resolution, and cannot do anything. 

I can't use linux and i can't use windows, all those articles didn't help. None of them have my problem.

Please help me!! I am looking at GParted now thru the live cd, and see all my partitions are there, and looks like nothing is broken, but i can't GET to my other drives, only "desktop" and thats it. Why can't i access my WinXP harddrive with linux???? How do i fix my ubuntu problem? How do i fix my WinXP problem??

Thanks in advance. :cry:

---

### Post by Mustard on 2006-02-12
Using your liveCD can you look at your linux partition and find the menu.lst in the /boot/grub/ directory.  This is your grub menu.  Copy and paste your menu.lst file in here so we can try to analyse what the system is currently doing.

When you choose linux from grub menu what happens?  Do you get dropped to a login prompt?  Can you login?  If so it might be possible to continue the installation from there.  I'm not sure yet.

---

### Post by executex on 2006-02-12
From the live CD, my /boot/ folder has a couple text files and a gzip in it. No other folders or files named menu.lst

I tried using: mount /dev/hda5/ /mnt/hda5/
but it says i dont have root.

When i click linux with the Grub boot. It goes to a login. I log in using my username and pass, and it gives me the $ sign, and just a DOS version of the terminal.

I believe im suppose to be able to continue installation but , i dont know how. and there is no good help thing for newbies in linux. Like when i type help nothing really happens except a list of commands, half of which you can't even see. I would like to see if i can reinstall those things that failed.... or something.

---

### Post by Herman on 2006-02-12
I would just try the install again, it only takes half an hour or a little longer, maybe it will work a little better the second time around.

If not, [check the md5sum]("http://ubuntuforums.org/showthread.php?t=100657&highlight=md5+check+iso") for your .iso if it is a CD-ROM you downloaded from the internet and burned yourself. if so did you burn it at a nice slow speed like 4x? Maybe try burning another CD and see if that one works better.
If it is a 'shipit CD', try using a different one.

If the ,iso is good, and the CD is okay, and Ubuntu still won't install, and you get tired of it and want to leave it for a while, you can always use GAG on a [System Rescue CD ]("http://www.sysresccd.org/")to boot WIndows, or [download your own GAG bootloader]("http://gag.sourceforge.net/") and [make a floppy disk or your own GAG CD]("http://users.bigpond.net.au/hermanzone/p12.htm") out of it just to boot Windows until you are in hte mood and/or have the time to resume trying to get Ubuntu installed.
Either that, or restore your Boot Sector for now by one of the methods [here.]("http://users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by rainstreet on 2006-02-12
Hi executex, i had the same problem loading ubuntu on my older machine, got to the same place as yours did . not knowing what to do with it i just put the install cd back in and tried again, and it worked the third time.
i got six cds sent to me and out of them only one would complete a full install !

---

### Post by executex on 2006-02-12
It gets stuck at 76% everytime, something called libopena or something.
And it just launches this thing called Breezy and ubuntu 5.10. I log in, and i just get a $ sign and can't do anything 

How do i open ubuntu. I mean is the last 25% of the packages that important?? Why won't it launch ubuntu so i can install the rest of the packages like the error message says...

I will download another ISO... and then cry some more.

Edit: I found out how to get root. I mounted my old hda5. It said something like NTFS error or something but then it displayed all my files on my winXP. So i'm guessing its fine, unless there is something wrong.

---

### Post by executex on 2006-02-12
I tried another mirror and redownloaded ibuntu, reburned with a different computer. And still got an error at 77%. Called libgnome something. IT was configuring this file and now got stuck. 
AGAIN!

What the hell is going on Why is it so hard to install ubuntu, i mean i'm experienced in programming and web design, and yet i can't install it, now imagine if some average joe tried to install it. No wonder windows XP is still the majority. 

The GAG thing is useless it doesnt do anything I already have GRUB. When i launch WinXP it just stays at a black screen. 
When i launch ubuntu now some wierd stuff come up, then says "define apt source" and insert CD, so i do and then says "this is not an ubuntu CD" wtf!!!
I insert my older ubuntu cd, and says same thing.
Then it says error on line 30 no space left, bla bla bla. Then says configuring base system like 10 times, then says "id "1" respawning to fast, disabled for 5 minutes".... now what do i do.

The more i try to fix the problem the worse it gets. I need help pleasE!!
I made a 2 GB partition ext3 for ubuntu using the installer and "automatically configurefree partition" option. And it gives me an evil smiley sometimes, and then installs and gets stuck at 76% AFTER it restarts and starts configuring. 

I seriously need some help... Also when i get root and mount my old HD, my winxp hard drive, it does, and then i type "ls" or "dir" and it says 3 times "NTFS error bla bla bla" and then lists all my files on my winxp root. So my files are there but something went wrong.
Can someone guide me on how to escape this? Perhaps tell me to go buy another hard drive and somehow use ubuntu's Terminal to copy all files from 1 hard drive to another so i can atleast save my files?????? I need help pls :(

---

### Post by executex on 2006-02-12
Ok just an update. I was able to install Linux now. I checked MD5sums and it was fine, but the problem was that when i partitioned the pieces i partitioned were causing problems. Then i had another piece of 2 GB free space, which i made into a partition and installed ubuntu. Now i'm stuck in 640x400 for some reason, and cannot change it. And i still cannot access windows.

---

### Post by klett on 2006-02-12
Hi,
I'm not an expert in GRUB, but I had some problems with it a few days ago. I was trying to do a different thing, but I think that some commands I used may help you to find out what is going on with GRUB. You can run grub in console mode with a  live cd and try to boot anything from here  and also you can analyze you menu.lst to find out what is happening.

[http://ubuntuforums.org/showthread.php?t=127925](http://ubuntuforums.org/showthread.php?t=127925)

Good luck!!

---

### Post by racecat on 2006-02-12
[QUOTE=executex]Ok just an update. I was able to install Linux now. I checked MD5sums and it was fine, but the problem was that when i partitioned the pieces i partitioned were causing problems. Then i had another piece of 2 GB free space, which i made into a partition and installed ubuntu. Now i'm stuck in 640x400 for some reason, and cannot change it. And i still cannot access windows.[/QUOTE]

There are things that other folks have been very good at troubleshooting for the screen res problem, but one simple gottcha that I ran into is if you use a KVM switch and are switched to a computer other than the Ubuntu box at boot up, you will only have 640X480 available.

Hope it helps.
Bill

---

### Post by executex on 2006-02-12
Ok i fixed the 640x400 issue by adding refresh rate lines under "Monitor" section in the xorg.conf file. (/etc/X11/xorg.conf)

But my problem is i cannot get windows to run still. Something during partitioning or with grub has happened and i can't run it. Just a black screen comes up. I studied menu.lst but it seems like everything is normal. 

Just wondering if playing with the numbers here might make a difference:
hda0,1
there is a line that looks like that in the menu.lst file. Perhaps changing the second number from 0-5 might make a difference.

---

### Post by klett on 2006-02-12
hda0,1 is the second partition in your first hard drive. You can learn more about this numbers here:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
click on  
2. Naming convention.

it's also interesting the topic
12.1 The flexible command line interface

with the command line interface you can run the commands containde in your menu.lst file and see the error messages.

---

### Post by executex on 2006-02-12
i tried hda0,0 all the way to hda0,5... none of them work, only 0,0 is the one that gives me a black screen, the rest give me errors.

---

### Post by klett on 2006-02-13
What is your partitioning scheme?
Do you have a live cd? If so, can you post your menu.lst file along with the result of  fdisk -l?

---

### Post by executex on 2006-02-13
ok i did some researching. 
I tried editting the boot command for windows XP under GRUB (before launching any OS). And i did hd0, and then pressed TAB. And then it gave me a list of partitions in my hard disk.

hd0,0 is my FAT system, my old C drive. It has nothing but a bunch of files left over from my first Win XP install. Which i then had deleted, and which i had installed Win XP to my D drive.
So C has "NTDETECT.com" and a bunch of sys files, and all those necessary files in order to launch win xp in it.

So when i try to launch that it gives me a black screen, because there is no OS there.

I found out my OS isn't corrupt, or maybe it is, but GRUB thinks my partitions hd0,4 and hd0,5 are "unknown filesystem" ... But they are both NTFS. One is like logical NTFS containing my WinXP partition. The other is called "extended" but i do believe 4, and 5 are the same partition. 

And GRUB doesn't recognize them so it doesn't launch them!!!

---

### Post by executex on 2006-02-14
So anyway, GRUB won't recognize my Win XP NTFS partition. It says "Unknown file system 0x7"

So what do i do?

---

### Post by Pavel Kraynov on 2006-02-15
[QUOTE=executex]So anyway, GRUB won't recognize my Win XP NTFS partition. It says "Unknown file system 0x7"

So what do i do?[/QUOTE]

I have this problem too.
GRUB can't  recognize ntfs partition while booting.
and this error code 0x7  - what is mean?

Thanks angels, i install ubuntu on autonomous hard disk drive! so i could booy XP and Ubuntu by switching boot order in BIOS Setup. So, I use BIOS as boot manager :)

---

### Post by mr_ed on 2006-02-15
[QUOTE=executex]... and which i had installed Win XP to my D drive.[/QUOTE]

Can you tell us your drive and partition layout?  I am assuming you only have one drive.

For the record, an IDE drive can only have 4 primary partitions... partition 4 is the partition that contains all the logical partitions... so if you created 3 logical partitions, they would be numbered 5, 6, and 7.
That's the difference between partitions 4 and 5.  Partition 4 is only a container, but 5 is your actual NTFS partition.  It's strange that GRUB doesn't recognise 
it...

I assume that you tried this in your /boot/grub/menu.lst

root (hd0,4)
chainloader +1


And try
rootnoverify (hd0,4)
chainloader +1

---

### Post by executex on 2006-02-16
yes i have tried that. 
I figured out that windows numbers partitions differently  than linux. In linux my windows is 5, and in windows its 3.... so boot.ini was the problem  not grub.

---

### Post by mr_ed on 2006-02-17
Was the problem?  So you can boot into Windows now?

---

### Post by executex on 2006-02-17
Yes, i can... i just dont want to anymore :X

---

