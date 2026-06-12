---
title: "[SOLVED] Help! Windows/Ubuntu partitioning. Dual-Booting."
date: 2008-08-28
forum: General Help
---

### Post by winbutu on 2008-08-28
**Hello,**

My name is Evan and i am _new_ to linux, my mom just got a EEpc from asus for her 10th anniversary from my step-dad and i was extremely impressed with the mobility and efficieny of the linux version installed. 
My idea is to have vista for gaming and applications, as there are more, and easily found. and linux for quick web browsing, quick boot times, and coding.

After some research i have a few questions in regard to dual booting, partitioning, and compatability.

My first question lies within partitioning.

I have used windows vista for a year now on my computer (and it sucks) and would like an alternative for faster browsing and simplicity.
Since i have Vista installed(im not sure how to put this)After my research i think that it is a good idea to backup my photos, and videos, and then wipe my hard drive.

The reason being, i would like to partition my hard drive like this;
[IMG]http://www.psychocats.net/ubuntu/images/partitioning3.png[/IMG] Except Vista.

Now my second question, haha.
I think, that i understand that if i install vista first and make three partitions(my hard drive is 300GB) of 
75GB **vista** - 180GB **shared** - 45 **Ubuntu**
with the vista partitioning software, i will not be able to install ubuntu onto a "vista made partition" Is this correct?
First off, will that be enough space for windows vista, and drivers, and games? Or can i put games into the shared folder?

Or should i use this;
[IMG]http://www.psychocats.net/ubuntu/images/partitioning4.png[/IMG]

On another note, i have my recovery disks so if anything goes awry, its not life threatening, i have no problem with a reinstall.

Please keep in mind that im only 16 so any complex computation may be beyond what i can do, thanks!

-Winbutu!

---

### Post by Bakon Jarser on 2008-08-28
First off, DO NOT use fat32 for your shared partition.  Ubuntu will read ntfs partitions just fine.  Second, that should be more than enough space for Vista and if you use ntfs for your shared partition then yes, you can install games onto that partition.  And by the way, backing up your personal files is always a good thing to do.  I use a backup program to keep a copy of the important ones on a flash drive.  You never know when your hard drive is going to die.

---

### Post by winbutu on 2008-08-28
Thanks!

Okay, so should i make the shared portion NTFS then?

What about creating partitions with vista and installing ubuntu onto it, will that work?

I have gone through the startup of ubuntu up to the stage where you select a destination for the OS, and im wondering if you can just choose a partition, is there an option that i did not see.
There is the "largest free space" but since i will be installing linux on the smallest free space how do i go about doing this?

To be very honest with you, i do not have any important documents! ;D haha
I have maybe 200mb of photos, and 20 GB of videos(that i feel i should keep). and i have dvd's so i can slap them onto a few of those, that isnt a problem.
I have a samsung hard drive which i have read up on, apparently they are more reliable then maxtor, or western digital. But i understand what your saying.

-thanks in advance
winbutu

---

### Post by mssever on 2008-08-28
You'll want to choose the manual partition option in the installer. EDIT: Do the partitioning from Linux, not Windows.


Something to note: My /home partition uses a whole lot more space than my / partition. That's where I keep my data. Granted, you can keep stuff on an NTFS shared partition, but you lose Linux permissions. My preference would be to omit the shared partition altogether and use that space for /home. Then, install the Windows ext3 driver, and you'll be able to access it from Windows, as well.

---

### Post by winbutu on 2008-08-28
Okay there are a few things here that i dont understand all to well.

-What exactly do you mean by /home? Is this your storage? /partition? and this is your OS?
-ext3 driver?
-Linux permissions?

Is there some way in which i can access the same information on both OS, such as photos, videos?
Thats the main reason for the shared partition.

Should i possibly make it a four part partition?
30GB Vista OS - 150gb Vista - 100GB Ubuntu - 20GB Ubuntu OS?

I may be sounding a little annoying about now, and im very sorry, but how exactly would i do this, in a brief step-by-step?

Thanks
-Winbutu

---

### Post by Bakon Jarser on 2008-08-28
/  is the root folder where all the system files go.
/home is the folder where all your personal stuff will go.
Putting them on seperate partitions makes things easier if you ever need to reinstall the OS.  You will also need a swap partition.  I think you said you're using a laptop so the swap partition should be sized RAMx2.  No matter what file systems you end up using, there is a way to read them from both windows and ubuntu.  I'm sure there is a guide that covers all this somewhere, I'll see if I can find it.

---

### Post by Bakon Jarser on 2008-08-28
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by mssever on 2008-08-28
> **winbutu said:**
> -What exactly do you mean by /home? Is this your storage? /partition? and this is your OS?Linux filesystems are rooted at a directory called /. It's vaguely like the C: drive in windows, except that there are no drive letters. Instead, you mount partitions on a directory or your choice, and then the partition becomes a seamless part of your filesystem. Your home directory (where your files live) is normally /home/yourusername. It's common practice to make a separate partition to hold /home (the installer will set that up for you if you just tell it that you want that particular partition to be /home. You have to have a partition called / whch will hold your system files. You can divide it up further if you want, but newbies shouldn't. Because your files normally go in your home directory (also known as $HOME or ~), /home is a logical choice for a storage partition, as well.
> -ext3 driver?The default Ubuntu filesystem is called ext3. It's backwards compatible eith its predecessor, ext2. Google can find a Windows driver that will enable Windows to access ext2/3 partitions.
> -Linux permissions?This is how Linux determines how a file is allowed to be used. It also determines whether a file is executable or not. Google "unix permissions" for all the details you could hope to want. FAT32 has no permissions, and NTFS permissions are completely different and incompatible. Windows filesystems also don't support some UNIX-specific file types such as symlinks (think Windows shortcuts on steroids, then Google "symlink" for the details). Note that, because Windows and Linux permissions are fundamentally incompatible, if you use the Windows ext3 driver, then the permissions will be ignored while you're in Windows.

> Is there some way in which i can access the same information on both OS, such as photos, videos?
Thats the main reason for the shared partition.See above.

> Should i possibly make it a four part partition?
30GB Vista OS - 150gb Vista - 100GB Ubuntu - 20GB Ubuntu OS?I'm a little confused by this. I think there are basically two reasonable options (others might disagree with me, and the specifics are subject to debate):

[LIST]
[*]/dev/sda1 (first partition) Vista. Drive C: in Windows and /windows (or whatever you want to call it) in Linux--Don't let Linux format that partition.30 GB or whatever is reasonable for Vista.
[*]/dev/sda2 (second partition) Shared data, ext3 format, /home in Linux. All available space left over.
[*]/dev/sda3 (third partition) swap. Should be the larger of 512 MB or the amount of RAM in your machine if you want to be able to hibernate. If you have lots of RAM and don't care about hibernation, you can omit swap.
[*]/dev/sda4 extended partition
[*]/dev/sda5 Your main Linux system and application files. Mounted on / and should be 15 to 20 GB.
[/LIST]
The other reasonable variation is to shrink /home smaller (it's difficult to estimate how much smaller) and add another NTFS partition for shared data. You could mount it wherever you want. If it were my machine, I'd choose either /media/shared_data or /home/myusername/shared_data (assuming a single user).

---

### Post by mssever on 2008-08-28
> **Bakon Jarser said:**
> I think you said you're using a laptop so the swap partition should be sized RAMx2.
That advice is quickly becoming outdated. If you have 1 GB or more of RAM, that rule really doesn't apply (though it can't hurt). If you want to hibernate, then you need at least as much swap as you have RAM. If your combined RAM + swap is at least 2 GB, you should be fine for most purposes. I've got 3 GB RAM, and I can run 4 virtual machines simultaneously, plus Firefox with a whole slew of tabs, and not touch swap.

---

### Post by winbutu on 2008-08-28
Okay, wow thats alot of information.

@Bakon Jarser;
Hello, thanks for the assistance, im using a desktop pc, that is a year old tomorrow!
I would do this but since i have 60 GB left only... plus it would speed up my computer to do a wipe, and get rid of random junk, and bloatware which i might have missed when i bought this thing.

@msserver

Yes, single user.

For the sake of it im going to call my windows drive, (Z) or (E) ;D

The information you provided me with is pretty compressed, and i only understand half of it;
-Extended partition?
-All of the things you listed to do can be done from a linux, and vista boot disks?

So let me get this kinda straight, 
1. Make a 30gb partition, after wiping hard drive, with the vista software, and install it there, and then make a second partition that would be, program files and such? Or my documents and such?
2. After that im a little lost.
3. I have 3GB of ram, so basically i should google, "how to create SWAP partition"
4. Extended partition? size?
5.linux OS 20GB.

Im sorry that i dont unserstand so much, being 16... wisdom comes with age! ^.^

-Winbutu

---

### Post by Surkow on 2008-08-28
@winbutu
I would recommend to create a partition for vista (NTFS), a shared data partition (NTFS) and leave enough empty space for Ubuntu. If you boot the live cd you will notice that there is an option to let Ubuntu use all the free space. This way a swap partition and a system partition will be created automatically for Ubuntu.

---

### Post by Bakon Jarser on 2008-08-28
Let's make this a lot simpler for you.  I've never had any problem with file permissions on my ntfs drive.  You're using it for data storage so you shouldn't have any problems.  To start out with you should go with a simple setup that is easy.  You can always change things later.

Step 1.  Decide how much space to use for Vista and install it.
Step 2.  Create your shared partition using NTFS.  I don't think you'll run into any problems using this.  Leave 34gb free for Ubuntu.
Step 3.  Install Ubuntu.  When you get to the partitioning step choose manual.  Create a 30gb partition to install ubuntu on.  You have plenty of hard drive space so make a swap partition the size of your ram in case you ever want to use hibernate.  

This will get you an installation that should meet all your needs.  All that other stuff is probably getting too complex for a beginner.  Later when you learn more about linux you may decide on a different setup but start small.  You'll have read/write access to your shared partition from both windows and ubuntu and it sounds like that is your main concern.

---

### Post by Bakon Jarser on 2008-08-28
Just saw surkow's answer.  Sounds like the simple solution you are looking for.

---

### Post by winbutu on 2008-08-28
Thanks guys, you are very supportive!

I think that what you two have just said lays it out failry simple, im just going to clarify below what im going to do.
To wipe my hard drive right now, do i just select everything in Drive c: and delete all? sounds kinda barbaric!

1. after hard drive wipe. Put in the windows vista dvd, and make two partitions with the vista software, one 30gb for the OS, and one 240gb for storage that will be NTFS.
2. Pop in the ubuntu disc, selecting the option to use all available space, which will be 30GB.

There are two things that are unclear to me, and after this im pretty sure i can handle this.
In the shared partition i will just have music and videos, so it will be like one large (my docments) folder that can be vewied by both OS, but if i am to install games to vista, should i install them to the vista OS partition and make it slightly larger to accomodate that, or can i write it to the shared NTFS partition, but create three folders.
(Vista games) (Shared) (linux downloads)

Im so close to getting this thanks for everyones trouble!

-Winbutu

---

### Post by Surkow on 2008-08-28
Can't you delete the C partition and create the NTFS partitions with the Vista installation DVD (after backing up your data)? Ubuntu and Vista do not interfere with each other. So you don't have to worry about installing Vista games on your data partition. Also remember that a small amount of the partition space for Ubuntu will be used for a swap partition (comparable to the pagefile from windows).

---

### Post by winbutu on 2008-08-28
Yea but the swap files are made when you install arent they?

---

### Post by Bakon Jarser on 2008-08-28
> **winbutu said:**
> Thanks guys, you are very supportive!

I think that what you two have just said lays it out failry simple, im just going to clarify below what im going to do.
To wipe my hard drive right now, do i just select everything in Drive c: and delete all? sounds kinda barbaric!

1. after hard drive wipe. Put in the windows vista dvd, and make two partitions with the vista software, one 30gb for the OS, and one 240gb for storage that will be NTFS.
2. Pop in the ubuntu disc, selecting the option to use all available space, which will be 30GB.

There are two things that are unclear to me, and after this im pretty sure i can handle this.
In the shared partition i will just have music and videos, so it will be like one large (my docments) folder that can be vewied by both OS, but if i am to install games to vista, should i install them to the vista OS partition and make it slightly larger to accomodate that, or can i write it to the shared NTFS partition, but create three folders.
(Vista games) (Shared) (linux downloads)

Im so close to getting this thanks for everyones trouble!

-Winbutu

When you do the windows install you will be deleting the existing partition(s).  No need to do anything special until then.  Like he said, you can install games to the shared partition.

---

### Post by Bakon Jarser on 2008-08-28
> **winbutu said:**
> Yea but the swap files are made when you install arent they?

The way you'll be installing your swap partition should be created automatically.  I think his concern was that maybe 30gb wasn't enough space since it will include a 4gb swap partition, but I think it should be plenty.

---

### Post by winbutu on 2008-08-28
> **Bakon Jarser said:**
> The way you'll be installing your swap partition should be created automatically.  I think his concern was that maybe 30gb wasn't enough space since it will include a 4gb swap partition, but I think it should be plenty.

Oh, space isnt a problem i can make it 40GB without a sweat.

Another quick thing, when i install, program files will be installed to the OS partition for vista right? I have 60GB of videos that i want to back up, and i dont want to waste 15 DVD's and two hours burning them, what would be your solution to keeping those?

thanks in advance

-Winbutu

---

### Post by winbutu on 2008-08-28
> **Bakon Jarser said:**
> When you do the windows install you will be deleting the existing partition(s).  No need to do anything special until then.  Like he said, you can install games to the shared partition.

My computer is a Hp pavilion A6109n with an extra 1GB of RAM slapped in there, and a 256mb nvidia graphics card, will ubuntu recognize, and be able to use these drivers for it?

So i can install linux, and windows applications into the same directory and they will not conflict?

thanks

-Winbutu

---

### Post by Surkow on 2008-08-28
> **winbutu said:**
> Oh, space isnt a problem i can make it 40GB without a sweat.

Another quick thing, when i install, program files will be installed to the OS partition for vista right? I have 60GB of videos that i want to back up, and i dont want to waste 15 DVD's and two hours burning them, what would be your solution to keeping those?

thanks in advance

-Winbutu

You could resize your existing partition, create a new partition and then move the videos to that new partition (perhaps your data partition?). But I don't have good experiences with resizing partitions (with possible data loss). Perhaps an external HDD would solve your problem.

> **winbutu said:**
> My computer is a Hp pavilion A6109n with an extra 1GB of RAM slapped in there, and a 256mb nvidia graphics card, will ubuntu recognize, and be able to use these drivers for it?

So i can install linux, and windows applications into the same directory and they will not conflict?

thanks

-Winbutu

Ubuntu will be able to use drivers for your graphics card. This is something you will have to enable after you have installed Ubuntu. You normally don't install Linux programs by hand. A large number of programs is handled by the package manager (which lets you install programs by just selecting them).

---

### Post by mssever on 2008-08-28
The others' advice probably suits your needs better than mine does. I'll only say that with 3GB of RAM, the only reason you need swap at all is if you want to be able to hibernate, in which case you'll need 3 GB of swap. You can also create a swap file (instead of a swap partition) later and not worry about swap now.

---

### Post by winbutu on 2008-08-28
> **mssever said:**
> The others' advice probably suits your needs better than mine does. I'll only say that with 3GB of RAM, the only reason you need swap at all is if you want to be able to hibernate, in which case you'll need 3 GB of swap. You can also create a swap file (instead of a swap partition) later and not worry about swap now.

Yea, sorry but i have to agree with them, their advice is a little more beginner, your too advanced for me. haha.
After doing some research i do understand a little more about what you have posted, and i will try to use the best of everyones advice.

-thanks for everything
-Winbutu

---

### Post by winbutu on 2008-08-28
> Ubuntu will be able to use drivers for your graphics card. This is something you will have to enable after you have installed Ubuntu. You normally don't install Linux programs by hand. A large number of programs is handled by the package manager (which lets you install programs by just selecting them).

I guess when i install it ill figure it out, with the power of GOOGLE!

Yea, my step-dad is a manager at a local college and i asked him if he could maybe borrow a external hd for the day!
He said he'll see what he can do, otherwise i might just have to do it the hard way. DVD's.

---

### Post by mytchmatch on 2008-08-28
Hi! I am really new with  ubuntu. i used to used windows xp. however out of curiosity, I tried to install ubuntu. Im supposed to make dual OS in my  pc  but unfortunately I erased my xp...

I wanted to reformat  my  computer  and  install xp and ubuntu so that i could  have both. I tried to install xp but i found out that the setup.exe is not working in ubuntu and  gnome...
anyway  what  should  i do?
what are the steps i need to do?
how  can i clear/reformat my harddisk using ubuntu so that i could have dual OS?
hope  you can help me...[http://ubuntuforums.org/images/icons/icon8.gif](http://ubuntuforums.org/images/icons/icon8.gif)
[http://ubuntuforums.org/images/icons/icon4.gif](http://ubuntuforums.org/images/icons/icon4.gif)

---

### Post by mssever on 2008-08-28
> **mytchmatch said:**
> Hi! I am really new with  ubuntu. i used to used windows xp. however out of curiosity, I tried to install ubuntu. Im supposed to make dual OS in my  pc  but unfortunately I erased my xp...

I wanted to reformat  my  computer  and  install xp and ubuntu so that i could  have both. I tried to install xp but i found out that the setup.exe is not working in ubuntu and  gnome...
anyway  what  should  i do?
what are the steps i need to do?
how  can i clear/reformat my harddisk using ubuntu so that i could have dual OS?
hope  you can help me...[http://ubuntuforums.org/images/icons/icon8.gif](http://ubuntuforums.org/images/icons/icon8.gif)
[http://ubuntuforums.org/images/icons/icon4.gif](http://ubuntuforums.org/images/icons/icon4.gif)
Please start a new thread instead of hijacking another user's thread. Also, if you're an absolute beginner, then the Absolute Beginner forum is the most appropriate place to post.

---

### Post by winbutu on 2008-08-28
> **mssever said:**
> Please start a new thread instead of hijacking another user's thread. Also, if you're an absolute beginner, then the Absolute Beginner forum is the most appropriate place to post.

Well, he did sorta hijack, but i told him in his own thread, that he should come look at my thread, because its pretty similar and is just vista instead of XP. Plus you guys have given really good awnsers.

---

### Post by winbutu on 2008-08-28
I was just reading a few other posts and it brought another question to mind, after this ill rename the thread [SOLVED]

Can i reinstall vista with a recovery disk?
It's made with the HP software that ships with the computer, not a microsoft made one.
Will i be able to use it for my endeavour?

-Winbutu

---

### Post by Surkow on 2008-08-28
> **winbutu said:**
> I was just reading a few other posts and it brought another question to mind, after this ill rename the thread [SOLVED]

Can i reinstall vista with a recovery disk?
It's made with the HP software that ships with the computer, not a microsoft made one.
Will i be able to use it for my endeavour?

-Winbutu

Yes you can reinstall Vista with a recovery disk. But if you install Windows after Ubuntu, Ubuntu won't be able to boot anymore. This has to do with the fact that Windows overwrites the boot grub loader.

---

### Post by damispyderbyte on 2008-08-28
Hi. 
Hmm... I jsut got a vista laptop and only needed 3 partitions. I dont understand why u need so many. 

My system is {[-----Vista 30GD-----][--------Ubuntu 130GB-----][swap]}

Just Edit Partitions Inside vista they are locked to ubuntu.

Then install the ext3 driver on Windows Visa.

Boom...... Both OS's can see each other. When u install Ubuntu make SURE that you install on the new partition and swap u made!!

That is a simple and easy way to install.  Ps: i'm 15 too lol

Hope This Helps
Yeah the recovery Disks will wipe ubuntu though

---

### Post by damispyderbyte on 2008-08-28
Well if u need more help you can send me a message i g2g

---

### Post by winbutu on 2008-08-28
@ Surkow

I will be installing Vista first, and i will use three partitions.
The SWAP partitions will be made upon installation.
With the vista partitioner i will make two partitions, and then i will install ubuntu 8.04, the only thing that i cannot decide is what format to make the shared partition?

@damispyderbyte

lol, i dont want so many, i want 4. ;D 
Thats only one more than you.
But i have decided that i want three.

@all

How should i format the shared partition?
Should i use ex2, or ex3?

---

### Post by mssever on 2008-08-28
> **winbutu said:**
> How should i format the shared partition?
Should i use ex2, or ex3?
Ext3 is better than ext2. It's newer, and because it uses journaling it's safer. If you lose power an ext2 filesystem could become corrupted, resulting in data loss. An ext3 filesystem is less prone to those kinds of problems due to journaling. There's a similar comparison between FAT32 (non-journaling) and NTFS (journaling).

---

### Post by winbutu on 2008-08-28
> **mssever said:**
> Ext3 is better than ext2. It's newer, and because it uses journaling it's safer. If you lose power an ext2 filesystem could become corrupted, resulting in data loss. An ext3 filesystem is less prone to those kinds of problems due to journaling. There's a similar comparison between FAT32 (non-journaling) and NTFS (journaling).

Allright so ill install vista on an NTFS partition, /home to a ex3, and then linux too?

thanks

-winbutu

---

### Post by Surkow on 2008-08-28
> **winbutu said:**
> @ Surkow

I will be installing Vista first, and i will use three partitions.
The SWAP partitions will be made upon installation.
With the vista partitioner i will make two partitions, and then i will install ubuntu 8.04, the only thing that i cannot decide is what format to make the shared partition?

@damispyderbyte

lol, i dont want so many, i want 4. ;D 
Thats only one more than you.
But i have decided that i want three.

@all

How should i format the shared partition?
Should i use ex2, or ex3?

The shared partition should be NTFS, for your own convenience.

Edit: There are Vista/XP drivers for Ext3 but they do not support journaling (so it will behave like an Ext2 driver). So I would not recommend to use Ext3 for your shared partition.

Edit2: Your /home directory will be on the Linx partition (which is normally Ext3).

---

### Post by mssever on 2008-08-28
> **winbutu said:**
> ex3
It's ex***t***3, not ex3.
> **Surkow said:**
> Edit: There are Vista/XP drivers for Ext3 but they do not support journaling (so it will behave like an Ext2 driver). So I would not recommend to use Ext3 for your shared partition.
I didn't realize that the Windows ext drivers don't support journaling. That certainly changes the equation. Any idea why ext3 isn't supported yet? (For other people's benefit, when I say ext3 isn't supported, I don't mean that you can't use it; I mean that ext3 is treated like ext2.)

---

### Post by winbutu on 2008-08-28
**@*** Surkow*
Are you sure they dont support it?

When i make the partition with the linux OS software it will automatically make it ext3?

So what do i use for the shared one? LOL

**@** *Msserver*

Sorry about the spelling error.
ext3.
What format should i use for my shared then?

---

### Post by mssever on 2008-08-28
> **winbutu said:**
>  What format should i use for my shared then?
If you'll be using Linux considerably more than Windows, I recommend ext3. Otherwise, I recommend NTFS.

Note on the relationship between ext2 and ext3. You shouldn't create ext2 filesystems. However, if the driver for whatever reason supports ext2 but not ext3, then it will treat the ext3 partition as ext2 and use it without the journal. When you boot back into Linux, Linux will continue using it as ext3.

---

### Post by winbutu on 2008-08-28
ahh, i see.
Well i do game alot, so i may be using vista more.
I have never had linux so i really dont know, and i dont want to use WINE because it lowers FPS compared to XP, so it will likely be the same with Vista.

So NTFS may be the case, im going to google "vista ext3" see what i can dig up.

thanks

-Winbutu

---

### Post by Surkow on 2008-08-28
@winbutu
Don't be confused. Just stick to the suggestions I (or others) gave you earlier.
- Backup your files;
- Remove your previous Windows partition;
- Create two partitions (Vista and shared) with the Vista install DVD (both NTFS) and leave free space for Ubuntu;
- Boot the Ubuntu live CD and let Ubuntu use all the free space to automatically create two partitions (Ubuntu and swap);

Btw, did you try the live cd to see how Ubuntu performs on your pc? And while I do not recommend it, Vista will be able to read ext3 file systems (as ext2).

---

### Post by winbutu on 2008-08-28
I did but all i did was look at the desktop.... ;D
Then i turned it off and went to bed, why should i?

Yea, all im confused about now is which format for the shared to use. I was told NTFS will have issues with secutiry because linux has issues with permissions on NTFS?

Check this out?
[http://ubuntuforums.org/showthread.php?t=358241](http://ubuntuforums.org/showthread.php?t=358241)
[http://www.go2linux.org/accessing-linux-drive-ext-with-vista](http://www.go2linux.org/accessing-linux-drive-ext-with-vista)

---

### Post by Surkow on 2008-08-28
> **winbutu said:**
> I did but all i did was look at the desktop.... ;D
Then i turned it off and went to bed, why should i?


To see if sound works, internet works and so on.

> **winbutu said:**
> 
Yea, all im confused about now is which format for the shared to use. I was told NTFS will have issues with secutiry because linux has issues with permissions on NTFS?

Check this out?
[http://ubuntuforums.org/showthread.php?t=358241](http://ubuntuforums.org/showthread.php?t=358241)
[http://www.go2linux.org/accessing-linux-drive-ext-with-vista](http://www.go2linux.org/accessing-linux-drive-ext-with-vista)

It seems the Vista drivers for the ext file systems are likely to corrupt the partition. Don't worry about the opposite, writing to NTFS from Ubuntu will work fine (without risk of losing your data).

---

### Post by winbutu on 2008-08-28
Oh okay, so ill just do NTFS then.

Shouldnt those things work anyways?

Can you post a link of a "how-to" virtual ubuntu, because i did it by accident.. i put in the install disk and went all the way to finding a directory to save too... then i clicked quit... and the ubuntu desktop.. i think "GNOME" was displayed.

---

### Post by Predator106 on 2008-08-28
Yeah, writing and reading any NTFS partitions in linux is now seemless and I haven't had any errors or problems. But you do, however, have to watch out for creating directories in Ubuntu, on the NTFS drive, naming them as something Windows would see as "illegal". For instance a dir named "Documents: Programming" would be illegal because of the ":". Windows will see that directory, but when you browse in it, it will throw a fit(but even if you do, you can just fix it through Ubuntu).

I actually see no real "point" to making 3 partitions, all-in-all. It may just be easier to do the Vista one(ntfs), then the Ubuntu partition(ext3). Unless you are a neat freak, and would prefer to have it all nice. But I mean you could install more games, if you ever go over the one partition's limit, instead of having to resize it. And from Ubuntu, you could just browse in the drive going to... I believe it would be NTFSVOL:/Users/MyName/Documents. Etc.

Yes, it is Gnome that Ubuntu uses by default, just to confirm you.

Oh, and as for the seeing if the internet works, sound works. It's just as with every OS, you have to make sure everything works, some hardware is incompatible with Linux, as is some with Window$

---

### Post by winbutu on 2008-08-28
> **Predator106 said:**
> Yeah, writing and reading any NTFS partitions in linux is now seemless and I haven't had any errors or problems. But you do, however, have to watch out for creating directories in Ubuntu, on the NTFS drive, naming them as something Windows would see as "illegal". For instance a dir named "Documents: Programming" would be illegal because of the ":". Windows will see that directory, but when you browse in it, it will throw a fit(but even if you do, you can just fix it through Ubuntu).

I actually see no real "point" to making 3 partitions, all-in-all. It may just be easier to do the Vista one(ntfs), then the Ubuntu partition(ext3). Unless you are a neat freak, and would prefer to have it all nice. But I mean you could install more games, if you ever go over the one partition's limit, instead of having to resize it. And from Ubuntu, you could just browse in the drive going to... I believe it would be NTFSVOL:/Users/MyName/Documents. Etc.

Yes, it is Gnome that Ubuntu uses by default, just to confirm you.

Oh, and as for the seeing if the internet works, sound works. It's just as with every OS, you have to make sure everything works, some hardware is incompatible with Linux, as is some with Window$

Now im being honest here, i am a neat freak i have a picture of my desk if you want to see it, ill put the link on the bottom.

Okay, if i go with two partitions, will i be able to view the same photos, in jpg. format, from both vista and ubuntu without problems, as well as videos?

I kinda want it really neat as in, let me post a picture after the neat freak desk.

thank
-Winbutu

[http://i118.photobucket.com/albums/o112/unix4owns/DSCN6971.jpg](http://i118.photobucket.com/albums/o112/unix4owns/DSCN6971.jpg)
That would be my desk, and i paid for everything you see with my own money, and im 16! ;D

[http://i118.photobucket.com/albums/o112/unix4owns/abc.jpg](http://i118.photobucket.com/albums/o112/unix4owns/abc.jpg)
This is what i had in mind if i was to make partitions.
Except imagine the icon as little drives instead, with a size bar beneath them.

---

### Post by Predator106 on 2008-08-28
LOL, wish mine looked like that, you don't even want to see my bedroom. Uhm, yeah, file transferring and reading/writing is seamless with 2 or 3 partitions, it doesn't really matter. the only thing is that most of your data will have to be on the Vista partition. Say, music, pictures, movies. In which case, to access them from Ubuntu, you would have to mount the partition (open it), and browse to what windows would see as C:\myfolder\my movies\movie.avi. The only reason you would have to have your shared info on the Vista partition, is because Vista can't read ext3 (or any Windows for that matter) natively.

---

### Post by winbutu on 2008-08-28
> **Predator106 said:**
> LOL, wish mine looked like that, you don't even want to see my bedroom. Uhm, yeah, file transferring and reading/writing is seamless with 2 or 3 partitions, it doesn't really matter. the only thing is that most of your data will have to be on the Vista partition. Say, music, pictures, movies. In which case, to access them from Ubuntu, you would have to mount the partition (open it), and browse to what windows would see as C:\myfolder\my movies\movie.avi. The only reason you would have to have your shared info on the Vista partition, is because Vista can't read ext3 (or any Windows for that matter) natively.

I try to keep it that clean lol, i spilt a beer on the floor when my friend was over... i was pissed... but it was my fault... i think? lol.

How about this, i have a 300GB drive so...
Ill give Vista 180GB on NTFS
Ill make a drive for storage, and backup, on NTFS about 80GB
Ill then fill up the remaining space (40GB) with Ubuntu? 

Vista and ubuntu can read and save onto NTFS, if im not mistaken, and they can both access it to play movies, listen to music, or look at photos.
All the games and such will be saved onto the vista partition. Will i still have to mount it? and if i do mount it wont i need an antivirus on ubuntu, or no?


thanks

-Winbutu

---

### Post by Predator106 on 2008-08-28
> All the games and such will be saved onto the vista partition. Will i still have to mount it? and if i do mount it wont i need an antivirus on ubuntu, or no?



No, you don't need antivirus on Ubuntu. You only do if you download stuff from Ubuntu and transfer it to a window$ pc and open it there. In which case, I don't even think you would need one, the windows antivirus should pick it up.

Will you still have to mount it? I don't get it. Think of mounting as just... turning on that disk (or logical disk). Normally it is turned off(unused), this saves boot, shutdown times, and avoids unnecessary writes. Unmounting is done when you don't want to write to it anymore and stuff. This is similar to Windows Removable Disk thingy, except not as annoying and stupid. Say you have a flash drive, you copy data to it, and right click to go to unmount. Ubuntu will say that it is still writing to it (if it is), then it will unmount it. This essentially "ejects" it. So you can take it out without corrupting anything.

Drives (or partitions) that Ubuntu is not residing on, are typically left unmounted, this will prevent programs from being able to access them, and will speed things up, especially something like a partition manager, where it reads drives. The less drives you have there, it should be faster.

Hope I'm explaining this correctly to you.

---

### Post by winbutu on 2008-08-28
Yea, you are.
That was clear and i understood all of it.

The second partition that would be used would only be 80GB, that shouldnt slow it down that much? so ubuntu would be running on a total of 120GB.
I dont want to access the vista folders, just the NTFS shared.
Or /home.

---

### Post by mssever on 2008-08-28
> **winbutu said:**
> [http://i118.photobucket.com/albums/o112/unix4owns/DSCN6971.jpg](http://i118.photobucket.com/albums/o112/unix4owns/DSCN6971.jpg)
That would be my desk, and i paid for everything you see with my own money, and im 16! ;DWow. You bought your own house? I see a wall. ;)

> **winbutu said:**
> How about this, i have a 300GB drive so...
Ill give Vista 180GB on NTFS
Ill make a drive for storage, and backup, on NTFS about 80GB
Ill then fill up the remaining space (40GB) with Ubuntu?
As long as you're using NTFS for shared data, you don't need a separate partition (unless you want one). You can just use your Windows partition as your shared partition.

Also, in Linux, you can exploit the wonders of symlinks to make file access simple. For example, your Windows partition will by default mounted on either /windows or /media/sda1. Inconvenient. But say you want easy access to your Documents folder: ```
ln -s /windows/Users/Evan/Documents ~/"Vista Documents"
# These paths are only examples, the specifics might vary
```Now, Vista's Documents folder is conveniently accessible from your Linux home directory.

---

### Post by mssever on 2008-08-28
> **Predator106 said:**
> Drives (or partitions) that Ubuntu is not residing on, are typically left unmounted, this will prevent programs from being able to access them, and will speed things up, especially something like a partition manager, where it reads drives. The less drives you have there, it should be faster.
All partitions on your internal hard drive(s) are by default mounted at boot. There really isn't any good reason to change that. If they aren't mounted, then you'll have to remember to mount them before using them. If they're already mounted, there's no problem. And there will be no speed difference (at least, not enough to notice) either way.

For removable media, such as CDs, DVDs, flash drives, etc., it's another story. But trying to keep internal hard disk partitions unmounted when you're not using them is a waste of time and effort.

---

### Post by winbutu on 2008-08-28
okay, that makes sense.
If you give the okay on the plan below, then this is solved.

_1_. Backup all data to external HDD - working on it.
_2_. reboot with windows recovery disk and (obliterate, lol ) hard drive, recreating three partitions.
_3_. **First** partition, made by vista, will be 180 GB. 
   **Second** partition, made by vista will be NTFS at 80GB
   **Third** and final partition, made by ubuntu 40GB ext3.
_4_.Install all updates for vista, drivers, software, games,  make sure they all work. Install Sophos, my antivirus.
_5_.Boot into ubuntu and make sure internet, sound, applications work. Install any required updates.
_6_.boot into vista, plug in external drive and copy all videos, music and photos to the second partition made for sharing.
_7_. Copy all other files to Vista directories.
_8_. I gotta figure out what applications are installed when i first boot up vista. ex. windows media player, windows office (trial with minimum features) then if some of those things are not installed i will install them.

This is a rough outline of what id be doing.
Verify that its pretty decent?

---

### Post by mssever on 2008-08-28
> **winbutu said:**
> _5_.Boot into ubuntu and make sure internet, sound, applications work. Install any required updates.
You mean INSTALL Ubuntu, right? Installing Windows after Linux makes life more complicated.

---

### Post by winbutu on 2008-08-28
yea, boot, install, i got em mixed up.
Yea vista first, for sure. There is no reason to install ubuntu first that i can think of. So you verify that procedure then?

---

### Post by Predator106 on 2008-08-28
> **mssever said:**
> All partitions on your internal hard drive(s) are by default mounted at boot. There really isn't any good reason to change that. If they aren't mounted, then you'll have to remember to mount them before using them. If they're already mounted, there's no problem. And there will be no speed difference (at least, not enough to notice) either way.

For removable media, such as CDs, DVDs, flash drives, etc., it's another story. But trying to keep internal hard disk partitions unmounted when you're not using them is a waste of time and effort.


No, every internal, non-ext3(ubuntu doesn't reside on these) drives, are not mounted. Ubuntu did this on install, they are NTFS, and besides, I don't want them spinning up for no reason either. Or are they spun up the whole time? I hope not, I thought I set it to spin down the disks somewhere anyways....

I was actually referring mostly to seperate drives, I can see why mounting/unmounting partitions doesn't really hold any value, I kind of accidentally swapped the terms.

---

### Post by mssever on 2008-08-28
Sounds reasonable. I question the need for a separate share partition (as I said above), but either way will work.

---

### Post by mssever on 2008-08-28
> **Predator106 said:**
> No, every internal, non-ext3(ubuntu doesn't reside on these) drives, are not mounted. Ubuntu did this on install, they are NTFSI can't remember if I manually configured my NTFS partition. I thought I did, but I might be wrong. I do know that it's automounted now. At least in the past, FAT32 partitions were automounted. I don't know about the present since I no longer use FAT32.

---

### Post by Predator106 on 2008-08-28
> 2. reboot with windows recovery disk and (obliterate, lol ) hard drive, recreating three partitions.

Oh uhm, make sure (I know you probably just said it wrong, as you stated it correctly later on) that you are actually creating only 2 partitions on that hard drive in windows, leaving enough space for the third partition. Make sure you do this, otherwise I believe windows will take up all that space, and Ubuntu, I don't think that it will be able to create a partition in that already partitioned space without wrecking anything(not positive though). So you should be making 1 partition of x gigs, 1 partition of y gigs(both NTFS, from windows installer), and x + y < z - TOTAL DISK SPACE.
Z being the third, Ubuntu partition. So, as a rough example, out of a 100 gig drive, 40 for the 1st, 50 for the 2nd, and 10 gigs remaining (unallocated) for ubuntu.

Hope I explained this clearly (and correctly), once again. As I am getting sleepy(not related to you :) ).

---

### Post by winbutu on 2008-08-28
@ msserver

Well the only reason i wanted to make it was that i could easily access media files, but if i can do that by just putting them on vistas partition i might just do two, three feels more comfortable though in case any of the OS go (SUICIDE) Thats little bit is slightly protected

@ predator

I want all partitions to be mounted, i dont really care about 5ms difference.

Yes, i know.
Ill make the two windows partitions, and use ubuntu "fill largest remaining space" and that will cover the last 40GB.

Thanks for all your help guys i think im going to do this tomorrow, once i have everything backed up, and im all rested up!

---

### Post by Predator106 on 2008-08-28
Your very welcome, don't forget to hit the thank buttons on the repliers.

---

### Post by winbutu on 2008-08-28
yea, well i didnt buy the house lol, but i did buy the;
Logitech G11
Logitech G5
Qck steelseries gaming mousepad
logitech 5.1 x-540
cod4! ^.^
cd's.
hp pavilion a6109n
+1GB RAM
+ 256mb Nvidia 8600 GTS XXX PCI-E graphics card, which you cant see.
The acer 22" screen (deal at futureshop 199$, cant even get that today and its been a year)
You cant see it, but theres a 500GB external hdd to the right of my tower.

I wish i had more money so i could create a computer from scratch. With a NZXT tempest case, and quad q6600, dual RADEON! OMG...gotta stop.

(ps. sorry if i bragged a little, it feels gooood!)

I want to create the middle partition because isnt it less at risk if one of the OS, quits?

---

### Post by Bakon Jarser on 2008-08-28
Jeez, you leave for a couple of hours expecting to miss a couple of posts and suddenly the thread blows up :)

> **mssever said:**
> Sounds reasonable. I question the need for a separate share partition (as I said above), but either way will work.

Well allow me to answer that question with an example.  Let's say you have all your music and movies in your windows partition.  A nice windows exploit is discovered and someone turns your machine into a zombie.  The only fix for these is a clean install of Windows.  Now you don't just have a windows install to do, you also have to reload all your music and movies which in my case would take hours.  If you have them on a seperate partition then an OS install goes much, much quicker.  So even in the days when I didn't dual boot, I always had a seperate partition for data.

---

### Post by winbutu on 2008-08-28
Are you talking to me about the "leaving" part.

My step-dad needed some help getting the floor ready in my sisters room, (washing floor, laying down underlay, moving some boxes, moving some furniture)

I have a feeling that im gonna like a dual-boot!

It will be more efficient, stable, fun!

---

### Post by Bakon Jarser on 2008-08-28
> **winbutu said:**
> Are you talking to me about the "leaving" part.

My step-dad needed some help getting the floor ready in my sisters room, (washing floor, laying down underlay, moving some boxes, moving some furniture)

I have a feeling that im gonna like a dual-boot!

It will be more efficient, stable, fun!

No.  I left for a few hours and there were about 25 new posts when I got back!  

Dual booting is the only way to go if you're a gamer.  Personally I haven't booted to windows in a long, long time but I'm not a gamer.  The only program I need windows for works fine in virtualbox.

---

### Post by winbutu on 2008-08-28
oh haha, ya i got a truckload of questions.

Why is it the only way to go if your a gamer?, do you use WINE?
Could i use it for cod4?
I think WoW released a linux version didnt they?

---

### Post by Bakon Jarser on 2008-08-28
> **winbutu said:**
> oh haha, ya i got a truckload of questions.

Why is it the only way to go if your a gamer?, do you use WINE?
Could i use it for cod4?
I think WoW released a linux version didnt they?

Wine doesn't fully implement d3d yet.  WOW works fine from what I've heard.  You can go to [www.winehq.com](www.winehq.com) and search the appdb for programs to see how well they work.  I've heard some games actually get more fps using wine then windows.

---

### Post by winbutu on 2008-08-28
Whats virtual box?

---

### Post by Bakon Jarser on 2008-08-28
> **winbutu said:**
> Whats virtual box?
Virtualbox is a virtual machine.  You can run another 'guest' OS inside of linux.  You take a performance hit since you share resources between linux and the guest os but it's a good way to avoid having to boot to windows.  You can also have a snapshot of the OS so you can screw around with it all you want and if you mess it up just go back to the snapshot.  That makes it handy for testing things or playing with viruses.

---

### Post by winbutu on 2008-08-28
lol, i cant believe you just said
"play with virusus"
that made me lol so hard!

---

### Post by mssever on 2008-08-29
I've just started messing with VirtualBox. It's awesome to be able to have a different OS on each virtual desktop and be able to switch between them without rebooting. I'm finally giving KDE 4 a try, after ignoring KDE for years. And when I get brave enough, I'll try a tutorial I found that's supposed to let me boot my XP partition in VirtualBox for those rare occasions where I actually need Windows. Then I won't ever have to completely leave Linux.

(I doubt that gaming will be ideal under VirtualBox, but I'm not a gamer, so that doesn't matter.)

---

### Post by winbutu on 2008-08-29
Ha, we all learn something new, i love that about computers.
You can never fully be 100% learned.
You learn C
then c++
then java
then you make websites. 
It goes on forever.
Your a programmer correct?

---

### Post by mssever on 2008-08-29
> **winbutu said:**
> Your a programmer correct?
An amateur programmer, yes. I mostly use Ruby, with some Python, Bash, and Javascript thrown in, and PHP when I'm forced to use it. I need to learn C one of these days, and I'm looking forward to learning Lisp, but I plan to ignore C++ and Java for as long as possible.

---

### Post by winbutu on 2008-08-29
And why would you want to ignore them?
I told a friend i wanted to get into some programming, he recommended C, and then C++, and if im ambitous, java.

---

### Post by mssever on 2008-08-29
> **winbutu said:**
> And why would you want to ignore them?
I told a friend i wanted to get into some programming, he recommended C, and then C++, and if im ambitous, java.
Because high-level, dynamically-typed languages are much more productive (at the expense of some speed, but raw speed isn't an issue most of the time--you're waiting on the user, or on the network, or on the disk, or whatever). C is an important language to know in the Unix world, and it can be used for time-critical parts of your code, but it's so low-level that I keep putting it off because of the drudgery. Why would I want to mess with C++ and Java when I have Ruby and Python and--eventually--Lisp?

Granted, C++ and Java have their legitimate uses, and there are a number of jobs for C++ and Java programmers. But I don't program for a living, and the programming I do doesn't require C++ or Java.

There are many flamewars^H^H^H^H^H^H^H^H^Hdiscussions about languages over in the programming talk subforum. In particular, check out the sticky there.

EDIT: If you learn Python, you'll likely experience enlightenment. It's so much more productive than C or C++.

---

### Post by Bakon Jarser on 2008-08-29
> **winbutu said:**
> And why would you want to ignore them?
I told a friend i wanted to get into some programming, he recommended C, and then C++, and if im ambitous, java.

I learned Java then C++ and when I felt ambitious c.  Java is easy and it's the beginner language at quite a few universities now.

---

### Post by mssever on 2008-08-29
> **Bakon Jarser said:**
> I learned Java then C++ and when I felt ambitious c.  Java is easy and it's the beginner language at quite a few universities now.
Python is the beginner language at MIT, I hear. And it's easier than Java. Plus, it's used extensively in Linux--particularly Ubuntu.

---

### Post by Bakon Jarser on 2008-08-29
> **mssever said:**
> Python is the beginner language at MIT, I hear. And it's easier than Java. Plus, it's used extensively in Linux--particularly Ubuntu.

I haven't learned python yet.  It's my next project.  One of the programs I use extensively is lacking a couple of features I want so I gotta learn python so I can add them.  I hope it's easier than java, because java is easy and I'm not looking for a challenge.

---

### Post by Predator106 on 2008-08-29
Isn't Java really really close to C#. You know, except Microshaft doesn't make it. But the syntax is virtually the same from what I have seen. Lots of similarities from what I've seen.

---

### Post by winbutu on 2008-08-29
Well maybe after C, ill check out my local library for books on python.

What sort of applications can be made on python, and not on C, and vice versa?

I dont really want to learn java.

---

### Post by mssever on 2008-08-29
> **Predator106 said:**
> Isn't Java really really close to C#. You know, except Microshaft doesn't make it. But the syntax is virtually the same from what I have seen. Lots of similarities from what I've seen.
From what I understand, Microsoft invented C# because Sun wouldn't allow them to change Java in such a way that they could lock Java users to Windows.
> **winbutu said:**
> Well maybe after C, ill check out my local library for books on python.

What sort of applications can be made on python, and not on C, and vice versa?

I dont really want to learn java.
Python is really popular in Ubuntu. A ton of Ubuntu software is written in Python. If you head over to the [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") subforum, there's a [sticky]("http://ubuntuforums.org/showthread.php?t=832449") there with a bunch of Python links. Plus, [LaRoza]("http://ubuntuforums.org/member.php?u=266234") and [pmasiar]("http://ubuntuforums.org/member.php?u=130379") maintain more Python links in their signatures.

---

### Post by winbutu on 2008-08-29
Yes, but what sorts of programs can you write with python that you cant with C?

---

### Post by mssever on 2008-08-29
> **winbutu said:**
> Yes, but what sorts of programs can you write with python that you cant with C?
That's really the wrong question. You can write anything in any language, but you'd be foolish to try it.

C is good for the kernel, libraries used by multiple languages, and situations where raw execution speed is important.

Python is good where flexibility and programmer time are important, and when bugs are undesirable (OK, all bugs are undesirable, but Python's less bug-prone). Since it's easy to extend Python with C, you don't have to use C just because one part of the program needs fast execution speed.

A lot of desktop apps are in Python. A lot of system utilities are in Python. Python is commonly used for web development. And that's just scratching the surface. Basically, Python is a general-purpose language.

You can, of course, do all of those things with C, but you'll spend a huge amount more time, and you'll have more bugs.

---

### Post by winbutu on 2008-08-29
Is it foolish of me to learn C then?
I like raw speed. ;D

I think im dual booting today, i have everything backed up to a E-hdd, and i have my boot discs, my cd's for mouse, keyboard software, i have a bunch of installers saved to the hdd (ec. mozilla firefox, xfire, etc.)

And all im waiting for is confidence i can do this, things running through the back of my mind are;

1. Will it be stable?
2.What if i mess up, will i waste hours of time?
4.Do i just wipe my hard drive clean when i use the vista recovery disk?
3.What do i do if i get it right and everything works? lol

---

### Post by mssever on 2008-08-29
> **winbutu said:**
> Is it foolish of me to learn C then?
I like raw speed. ;DRaw speed actually isn't as important as you might think, for two reasons:

[LIST=1]
[*]When you're optimizing your code, you obviously need to find the bottleneck and speed that up--otherwise you're wasting your time. Much of the time, your bottleneck will be something beyond your control, such as the user, or the database, or the network, or the disk.
[*]When the bottleneck is something you *can* control, the first thing you should try is improving your algorithm; that will usually buy you a greater speed improvement than writing your old algorithm in C. And often, once you've improved your algorithm, your back at case 1, so there's no benefit to writing it in C. It's *much* easer and quicker to try different algorithms in Python than in C. Of course, there are situations where it *does* pay to write in C. But you'll come out ahead if you try it first in a language like Python and only switch to a lower-level language like C when you've proven that that's the only acceptable solution. Translating from Python to C isn't hard.
[/LIST]
EDIT: By the way, one of the big mistakes programmers make sometimes is premature optimization. You can't know what to optimize until you test and profile your code. Optimizing before then is wasting your time, because you're probably optimizing the wrong thing.

By the way, all I've said about Python also applies to other similar languages, such as my personal favorite, Ruby.

> I think im dual booting today, i have everything backed up to a E-hdd, and i have my boot discs, my cd's for mouse, keyboard software, i have a bunch of installers saved to the hdd (ec. mozilla firefox, xfire, etc.)

And all im waiting for is confidence i can do this, things running through the back of my mind are;

1. Will it be stable?
2.What if i mess up, will i waste hours of time?
3.What do i do if i get it right and everything works? lolTake the plunge, man! :) You won't know until you've tried.

---

### Post by winbutu on 2008-08-29
wow im on the edge of SPAZZING ON VISTA F!^#!!!!!
The recovery disk, IS BS, all it does is reinstall vista to its factory settings... that basically means...
i cant repartition the hard drive... or if i do itll F@^# itself in the A@^
Im gonna partition with ubuntu and see if it screws vista over. If it does, im just installing ubuntu, i dont care about games so much that ill sacrifice myself to the microsoft chopping block.
Im frosted, i AM THIS CLOSE TO THE EDGE -

---

### Post by mssever on 2008-08-29
> **winbutu said:**
> wow im on the edge of SPAZZING ON VISTA F!^#!!!!!
The recovery disk, IS BS, all it does is reinstall vista to its factory settings... that basically means...
i cant repartition the hard drive... or if i do itll F@^# itself in the A@^
Im gonna partition with ubuntu and see if it screws vista over. If it does, im just installing ubuntu, i dont care about games so much that ill sacrifice myself to the microsoft chopping block.
Im frosted, i AM THIS CLOSE TO THE EDGE -
Ubuntu to the rescue! The Ubuntu installer can resize your Vista partition--with Vista installed.

---

### Post by winbutu on 2008-08-29
Thank god, i almost punched out my sister when she asked for help with her coloring. -.-
Its gonna take so long to "RE UNINSTALL ALL THIS BLOATWARE GARBAGE" thank god ubuntu doesnt have that.

---

### Post by winbutu on 2008-08-29
Guess whos on ubuntu right now?

! ;D !:popcorn:

---

### Post by mssever on 2008-08-29
> **winbutu said:**
> Guess whos on ubuntu right now?

! ;D !:popcorn:
Good for you!

---

### Post by Grez on 2008-08-29
> **winbutu said:**
> Guess whos on ubuntu right now?

! ;D !:popcorn:

Nice one!

Worth the heartache, wasn't it?

Have you been spooked by the quieteness and inactivity of the HDD yet?

:KS

---

### Post by Bakon Jarser on 2008-08-29
Good to hear.  One of the biggest complaints you'll hear about linux is that flash crashes firefox a lot.  But not if you do this:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by winbutu on 2008-08-29
Thanks guys, im actually on vista atm... trying to install the 53 updates that it requires.. except my only problem is it wont start downloading them...

Ubuntu installed perfectly no hitches, it updated super fast, its way faster then vista in, copying, and pasting data, opening applications, saving, downloading...anything else? lol

My only problems with ubuntu are, my sound is really quiet??
and i dunno how to install adobe flash player for youtube, which version Tar. YUM?


@Msserver

Thanks for all the help, couldnt have been possible without you! 
;D

@Grez
you know what, i just noticed that... ;D
But my graphics card fan is really loud so its hard to notice, but it is different! The heartache? Vista is the heartache.

@Bakon Jarser
Are you searious?

---

### Post by Bakon Jarser on 2008-08-29
> **winbutu said:**
> Thanks guys, im actually on vista atm... trying to install the 53 updates that it requires.. except my only problem is it wont start downloading them...

Ubuntu installed perfectly no hitches, it updated super fast, its way faster then vista in, copying, and pasting data, opening applications, saving, downloading...anything else? lol

My only problems with ubuntu are, my sound is really quiet??
and i dunno how to install adobe flash player for youtube, which version Tar. YUM?


@Msserver

Thanks for all the help, couldnt have been possible without you! 
;D

@Grez
you know what, i just noticed that... ;D
But my graphics card fan is really loud so its hard to notice, but it is different! The heartache? Vista is the heartache.

@Bakon Jarser
Are you searious?

Very serious, and that link will get flash installed for you.  YUM is for a different distribution of linux.  the tar file would make you compile it from source, which you could do but don't have to.  Ubuntu's installation packages are .deb

As for the sound, you probably already found the volume control in the upper right corner.  Try double clicking it and make sure PCM is turned up all the way.

---

### Post by winbutu on 2008-08-29
Uhh, well thats a pretty complicated first time with the terminal!

My vista updates fnally started downloading, took half an hour for them to start. -.-

---

### Post by Bakon Jarser on 2008-08-29
> **winbutu said:**
> Uhh, well thats a pretty complicated first time with the terminal!

My vista updates fnally started downloading, took half an hour for them to start. -.-

Terminal isn't so hard.  For that guide it's all just copying and pasting.  Don't copy the $ though.  They shouldn't be there.

---

### Post by winbutu on 2008-08-29
I installed it all, and didnt copy $, i much prefer seeing everything as its happening, opposed to a little green bar that flashes... ;D

---

### Post by mssever on 2008-08-29
> **Bakon Jarser said:**
> Good to hear.  One of the biggest complaints you'll hear about linux is that flash crashes firefox a lot.  But not if you do this:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)
Uh, that might not be necessary, depending on your hardware. For me, installing flash is a matter of:

[LIST=1]
[*]Enable the Medibuntu repository (I actually don't remember whether this step is necessary)
[*]Install flashplugin-nonfree ```
sudo aptitude install flashplugin-nonfree
```
[*]Restart Firefox.
[/LIST]

---

### Post by Bakon Jarser on 2008-08-29
> **mssever said:**
> Uh, that might not be necessary, depending on your hardware. For me, installing flash is a matter of:

[LIST=1]
[*]Enable the Medibuntu repository (I actually don't remember whether this step is necessary)
[*]Install flashplugin-nonfree ```
sudo aptitude install flashplugin-nonfree
```
[*]Restart Firefox.
[/LIST]

Yes but that doesn't take care of the fact that firefox will crash about every fourth youtube video.  That thread addresses some bugs in pulseaudio and flash.

---

### Post by Bakon Jarser on 2008-08-29
> **winbutu said:**
> I installed it all, and didnt copy $, i much prefer seeing everything as its happening, opposed to a little green bar that flashes... ;D

It's nice to see what happens behind the scenes isn't it?  Is flash working for you now?

---

### Post by mssever on 2008-08-29
> **Bakon Jarser said:**
> Yes but that doesn't take care of the fact that firefox will crash about every fourth youtube video.  That thread addresses some bugs in pulseaudio and flash.
I can watch all the YouTube videos I want without Firefox crashing. That's why I said it depends on your hardware.

My experience has been that the more complex the software setup, the more maintainability problems occur down the road. I never reinstall, so I'm careful what I install; the consequences of a complex setup could take years to fully manifest themselves. And if I don't have a specific need for something outside the official repos and Medibuntu, I don't install it. (Of course, if I had trouble with that bug, then I'd use that solution.)

---

### Post by winbutu on 2008-08-29
> **Bakon Jarser said:**
> It's nice to see what happens behind the scenes isn't it?  Is flash working for you now?

Didnt test it, i will test it after the vista updates are finished downloading, and installing

"its been three hours"
Jeez microsoft blows.

Free stuff FTW!
:lolflag:

---

### Post by Predator106 on 2008-08-30
Shyeah, tell me about it. I love the quietness of my HDD and network. Heck, everything resource-wise is quiet, it certainly isn't like Windows where you are browsing the web and it starts thrashing the hard drive like mad for 20 minutes. Not to mention, everytime I boot up Windows, my brother on his PS3 would get lag, everytime I boot up Ubuntu, nothing. Windows was probably calling back to Microsoft to make sure my copy was legal(it is, wink, wink). More and more I find out that, after moving to Ubuntu, Window$ actually is way more intrusive, and annoying, I find it counter-productive, actually. The only time I boot into XP (yes I did have vista, but that was just an even worse egg from a bad tree, so to speak :) ), is to do my gaming, but since I have a PS3 now, I ha ven't booted into it for a month, at least.

---

### Post by winbutu on 2008-08-30
you have a verified version of vista? (wink wink) i dont blame you.

Im slowly learning how the terminal works, and i installed compiz fusion which looks better then vistas preinstalled graphical effects but is less resource consuming. CUBE ftw! :KS
I just need to figure out how to get all of the things working that i need.
Can you reccommend some desktop applications?

I gotta be honest... xbox360 ftw. I hate supporting microsoft but it is pretty slick. I would choose the wii but the graphics are pretty shoddy.

One thing i notice is that vista boots slower now that i have ubuntu installed.
plus vista doesnt even recognize ubuntu partition.

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Predator106 on 2008-08-30
I have a PS3, alot more freedom with it IMO, as opposed to the others, and Sony has been really getting "on the ball" lately, not too mention their upcoming updates that will be really, really awesome, something never seen before with consoles.

Yeah, compiz-fusion works nicely on my computer too. You should install the Emerald engine for it. It looks just like Vista window borders, except you get waaay more customization as opposed to Vista.

Desktop applications? Like what?

Yeah, the only thing is, I wish Ubuntu would boot faster than XP, I still have some optimizations that I have not gotten to yet, and it's been a few months (sigh, procrastination). Maybe I will do those now, they are waay back in my bookmarks, lol.

---

### Post by winbutu on 2008-08-30
how do you optimize?
I'm sorry, im not gonna install emerald, to make it look like vista... ;D
Upgrades to a gaming system?

---

### Post by Bakon Jarser on 2008-08-30
Sony is just as evil as Microsoft.  Anybody remember them selling cd's with rootkits?

If you want to get into some more pretty stuff that compiz can do you'll need the compiz configuration manager.

```
sudo apt-get install compizconfig-settings-manager
```

I think it shows up under System > Appearance > Advanced Desktop Settings.  Animations is a fun one to play with.  When my windows close they go up in flames.  Scale is another one I use all the time.  When I move my mouse to the bottom lef corner of the screen it shows all open windows on the screen.  Makes switching between windows easier for me.

What kind of programs are you looking for?  Tell us what you use in windows and I'll try and tell you what matches it in Ubuntu.

I've been meaning to get around to speeding up Ubuntu's boot process for a while now too.  I guess it just isn't important enough for me to actually get around to it, but here is the thread I have bookmarked for some day when I'm not feeling so lazy :).

Edit:  Oops, that link was really old!!

---

### Post by mssever on 2008-08-31
> **winbutu said:**
> I'm sorry, im not gonna install emerald, to make it look like vista... ;DBy default, Compiz uses metacity themes (at least in Gnome-based systems). There are a whole lot more metacity themes than there are emerald themes--at least, last I knew. See art.gnome.org and gnome-look.org for themes galore. Metacity themes control the title bar. GTK themes control the window itself (colors, buttons, menus, etc.) for GTK-based apps. (My favorite GTK theme is Gilouche2 and my favorite metacity theme is ClearLooksWithACherryOnTop.)

---

### Post by Predator106 on 2008-08-31
> Sony is just as evil as Microsoft.

Not from my point of view. Considering you can install Linux on it, you can upgrade the HDD, all of which are supported even by their manual, saying that you can do it without voiding the warranty. You also don't have to pay for their internet services-especially when Home comes out, which Microsoft wasn't planning to do anything that great, although they will probably end up "trying" to copy it, and probably charge for it...

Not to mention Sony actually makes quality products, a built in BD player, they actually thought ahead, and new that the other discs weren't going to work (was it HD-discs or something, forget the name).

Do you ever see a PS3 with 3 rings of death, heh, of course not, you can have your PS3 folding at home everyday in a little cupboard and the thing won't overheat. Less than 1% failure rate, compared to an estimated 15% failure rate (at least).

Besides, the rootkits on the cd's was just one instance, one division of the corp....have you even looked into how much Microsoft actually does. They probably even have a section in their budget for lawsuits that constantly grows.

---

### Post by winbutu on 2008-08-31
okay, i think ill check out some of those tools for compiz fusion, and, all of those gnome effects.

One of the main features i was looking for on my desktop was stardock, but msserver gave me a similar program for linux.

Wow, this really changed my mind about the ps3, and i agree with the failure rate, my cousins who are 18 and 16 both have a xbx360...and they both failed... hahaha, and microsoft took them for two months and sent them back still broken.

What about games? I know that ps3 came out with not too many games.

P.S - halo sucks.\
P.S.S - is there anything you guys can reccomend for me to get more acquainted with ubuntu?

-winbutu

---

### Post by Predator106 on 2008-08-31
Yeah, it didn't come out with many games, but now it's starting to get more PS3-only games, not just ports. Which is good, because that means that they don't have to "tone" down all the versions, just because they are porting to the X360, so in essence the Xbox is dragging them down graphically.

Well what I play is Battlefield:Bad company, GTAIV, Metal Gear Solid 4, Resistance:Fall of man, and Call of duty 4.

Resistance 2 is coming out, along with Killzone 2(the first one was for PS2, which was really pushing the limits of that console), Socom:Confrontation, Prototype, and Little big planet. For the last one, please search youtube for gameplay videos. I like to think of it as a 2D-type view (except it's actually 3D, of course) version of garrys mod. You can create your own objects, and then levels, and then play on them with you or your friends, it sounds kind of iffy at first, since other games have said the same to some degree. But this game looks awesome, it's coming out Oct. 21, You can place a wooden square board, cut holes out of it where ever you want, put some other objects on the end, and motorize it. You can make all kinds of traps and stuff (puzzles, basically) and it is supposed to have a huge array of user-created content (since any person can make a level).

Have you heard of Folding @ Home, the PS3 lets you do this, basically, it uses your PS3's 6/7 cores (one is locked for OS use only) and it simulates protein folding and misfolding, and submits the simulation results back to stanford university, and in turn helps cure diseases, etc. This is the first console to have something like this, before it was only for PC, but computer's don't have this much CPU power at the moment.

Life with playstation is also coming out very shortly. It is supposed to be a place to watch real-time weather, a globe with the weather effects on it(really really awesome IMO), get real-time news, listen to music, and I heard you can do folding while doing this(not sure if this is true or not yet).

Home, is also something you should look up on wiki for, basically if you heard of Second Life, this is for the PS3, except good graphics. You can go around to clubs for individual games, say, a GTAIV club, talk to people about it, invite them to your apartment, or play that game with them right from there.

You can also modify your apartment to your liking, trophies you will earn can be placed in your apartment, you can buy new furniture, lamps, and the apartments look really, really awesome.

And of course, with Playstation, it's all free, now this is what I call post-purchase return value, not just buy it and that's the way it is.

The PS3 is really coming a long way, I love how quiet the fan is, and it only kicks up a little bit when hot. The PS3 now has in-game messaging, and in-game music (with future, and updated games since July).

Did you know that you can also download any theme you want for the playstation XMB (main menu), you can set your wallpaper, and make your own theme, with sounds and icons however you want it to be. There are hundreds of themes out there now for it. I believe Micro$oft makes you pay for themes, heh, what a joke. Not to mention, I can check my email, or even go to this forum and be posting this right now, from my PS3, and that's even without using linux, or goto youtube and watch a music video, list is endless. It has flash player (it's an older version though, but they should update it soon) built in.

Oh, did I mention full Blue tooth support, I think that the Xbox 360 uses Infrared, is that a joke or what? I remember a friend saying that his leg would block the controller's infrared port, which is just pathetic. The remote on your TV uses infrared, and I know that you can block it with your leg also... I can turn my PS3 on, and play it from outside the house, when my PS3 is downstairs(I'm serious, I actually tried this, no lag either).

"The controller remains connected to the Xbox console even when you turn off the Xbox console." I got that from microsoft's support site, it is for the Xbox 360 by the way. Is it just me or is that a really inefficient design. That's like leaving my laptop on when I'm not using it, or leaving my TV on when DirectTV is off. Talk about wasting the batteries. The batteries in the PS3 controller are built in, and they are Lithium Ion, which is so far-probably-the best rechargeable battery on the market. Also, I have heard of a lot of people snapping their disc tray, not to mention having something on their disc tray. The PS3 doesn't have a disc tray, it has the little slot with the fuzzies(I'm sure you know what I'm talking about) to prevent the dirt. From experience, these work a lot better than trays.

Welp, those are my opinions, and this is why I have stuck with the Playstation forever, and especially with the PS3, I will be laughing when my PS3 outlives the Xbox in both performance, lifespan, and replaying longevity.

Believe it or not, I actually like Halo, it gets old pretty quickly though, but I really like the story, it seems like many people don't like it, I find it similar to Half-Life in a way.

And did you know that Microsoft actually planned to only have a 30-day warranty on it's release, talk about screwing you, the only reason they upped it is because of the mass break-downs and bad press they were getting. Sony offered a 1 year warranty before it even hit the shelves, and stuck with it. Sony is actually confident that their machine won't break down, and it rarely does. I've seen the inside of this, and it is really a heat-dissipating masterpiece.

Not to mention, the PS3 is truly the best bang-for-the-buck, try getting a Blu-Ray player for as much or cheaper than this console, that is a feat, especially since this has Blu-tooth, and a 7 core processor. The list goes on and on :) .

Not to mention, I stereotype, but it certainly seems to be true, PS3 owners tend to be more intelligent, actually KNOWING what the hardware is capable of, and what is in it. Not just buying something off of the shelf that has bill gates logo on it. I realized that I could do so much more with it, it's not just a gaming platform, it's a media center too. Most X360 owners tend to have the "I could kick your ***, and my cock is bigger than your cock" attitude, in other words, their consumer base is full of immature "children". If microsoft even tried to make a browser for it's crappy box, I'm sure it would end up being like internet explorer...and we all know where that ends up..

EDIT: Man, I wrote a huge article, yay.

---

### Post by Bakon Jarser on 2008-08-31
> **Predator106 said:**
> 
Not to mention Sony actually makes quality products, a built in BD player, they actually thought ahead, and new that the other discs weren't going to work (was it HD-discs or something, forget the name).

Of course they put in the blue-ray player.  They were the major financial backer for blu-ray.  They were trying to win a format war and that's how they did it.  And the other one was HD-DVD

> **Predator106 said:**
> Besides, the rootkits on the cd's was just one instance, one division of the corp....have you even looked into how much Microsoft actually does. **They probably even have a section in their budget for lawsuits that constantly grows.**

You don't think sony has a section in their budget for lawsuits?  Are you not aware that they are one of the big four behind the RIAA, probably the most litigious organization on the planet?  That alone makes them just as evil as Microsoft in my book.  

The PS3 may be a good product, I won't argue with you about it because I don't own one.  I never will because I personally don't want to support Sony in any way.

---

### Post by Bakon Jarser on 2008-08-31
> **winbutu said:**
> okay, i think ill check out some of those tools for compiz fusion, and, all of those gnome effects.

One of the main features i was looking for on my desktop was stardock, but msserver gave me a similar program for linux.

Wow, this really changed my mind about the ps3, and i agree with the failure rate, my cousins who are 18 and 16 both have a xbx360...and they both failed... hahaha, and microsoft took them for two months and sent them back still broken.

What about games? I know that ps3 came out with not too many games.

P.S - halo sucks.\
P.S.S - is there anything you guys can reccomend for me to get more acquainted with ubuntu?

-winbutu

Yeah, Microsoft finally acknowledged they shipped a bunch of bad 360's and shelled out $1 billion to fix the problem.  I'm sure they weren't to happy about it and I'm sure the problem is fixed now.  They've had quite a few problems with the 360.  I think some of the early ones would also ruin the game discs.

I think I read in a previous post that you had lots of music so you probably need a good music player.  I personally hate rythmbox.  I use Amarok.  You might want to give it a try.  The only thing I don't like about it is that it takes too long to start but it's a minor gripe.  I think it starts faster in KDE.  I'm actually going to give KDE a try when 4.2 comes out.

---

### Post by Predator106 on 2008-08-31
Actually, as for the 360 problems, I believe they still occur, they're _*still*_ trying to fix it.

Yeah, but the lesser of two evils in my opinion, especially considering one is directly opposing OSS.

Well at the moment I use Banshee, it seems decent, nothing exceptional, it's waaay too long to add/remove music though, especially when you have like over 50 gigs of music, but a bug is that it actually crashes when you try to delete over 800 songs at a time, so I have to basically select 800 and goto remove, and continue until they're all gone.

Man, that would be so great if a company (or companies) made a free, OSS console. But then again, it would probably end up like a PC heh, except I suppose game support would be better than in Linux. Until that time however, I shall stick with a non-microsoft console that isn't terrible (thinking of Wii :) ).

I want a media player that was like WMP(I hate to say it, but this part was good) WMP 11 had like a cover art display, and you had all kinds of categories, and the search was kind of good, if only banshee could adopt those features. I do like that banshee has a similar artist bar at the bottom, and shows you the top-liked songs and stuff from this artist, and who is like them, and a percentage of similarity.

Yeah, I didn't like rythym box either. The only thing about amarok, I may have tried it before, but if it uses the KDE engine.... then I really don't like it, I don't know, is there a way I can change the look(I'm using Gnome). Because to me, it seems too, Mac-y-like.

---

### Post by winbutu on 2008-08-31
predator wow that was a long post, hehe

>  
yay!


If i had money.. lol, id go and buy a ps3 right now, i am searious.
Even the outside of it looks pretty narley!

---

### Post by Predator106 on 2008-08-31
Yeah, got a lil' carried away. But hey, it's good practice at typing :lolflag:

---

### Post by winbutu on 2008-09-01
> **mssever said:**
> By default, Compiz uses metacity themes (at least in Gnome-based systems). There are a whole lot more metacity themes than there are emerald themes--at least, last I knew. See art.gnome.org and gnome-look.org for themes galore. Metacity themes control the title bar. GTK themes control the window itself (colors, buttons, menus, etc.) for GTK-based apps. (My favorite GTK theme is Gilouche2 and my favorite metacity theme is ClearLooksWithACherryOnTop.)

How do i install GTK+ ?
I downloaded it and it says that the archive manager does not recognize it. Im still a noobuntu

---

### Post by Bakon Jarser on 2008-09-01
> **winbutu said:**
> How do i install GTK+ ?
I downloaded it and it says that the archive manager does not recognize it. Im still a noobuntu

First of all, get out of the habit of googling for your programs.  Always search synaptic first.  System > Administration > Synaptic Package Manager.  You now have a whole world of free software to search through.  Every once in a while you'll need a program that isn't there but that should rarely happen.

Second, I believe gtk is the default theme manager in Ubuntu.

---

### Post by Bakon Jarser on 2008-09-01
> **Predator106 said:**
> Actually, as for the 360 problems, I believe they still occur, they're _*still*_ trying to fix it.

Yeah, but the lesser of two evils in my opinion, especially considering one is directly opposing OSS.

Man, that would be so great if a company (or companies) made a free, OSS console. But then again, it would probably end up like a PC heh, except I suppose game support would be better than in Linux. Until that time however, I shall stick with a non-microsoft console that isn't terrible (thinking of Wii :) ).



Didn't know they were still having the same problem.  Knowing them it could be a new problem.  They might start 'patch teusday' for the xbox:)  I'v got nothing against the wii.  It's not really targeted at hardcore gamers and the games are fun.  An OSS console could happen someday.  We are getting an OSS phone soon:)

[QUOTE=Predator1]
I want a media player that was like WMP(I hate to say it, but this part was good) WMP 11 had like a cover art display, and you had all kinds of categories, and the search was kind of good, if only banshee could adopt those features. I do like that banshee has a similar artist bar at the bottom, and shows you the top-liked songs and stuff from this artist, and who is like them, and a percentage of similarity.

Yeah, I didn't like rythym box either. The only thing about amarok, I may have tried it before, but if it uses the KDE engine.... then I really don't like it, I don't know, is there a way I can change the look(I'm using Gnome). Because to me, it seems too, Mac-y-like.[/QUOTE]

I was a winamp user and don't know much about wmp11.  If you liked amarok but are a gnome purist try exaille.  Also amarok does let you choose colors for it if that makes a difference for you.

---

### Post by winbutu on 2008-09-01
hey thanks, yea i guess i gotta get out of the habit of "google it" 
cuz vista aint got SHT!
I want to get rid of vista so bad its not even funny.
Stupid hardcore gaming obsession, i rape in cod4 pubs.

---

### Post by mssever on 2008-09-01
> **winbutu said:**
> How do i install GTK+ ?
I downloaded it and it says that the archive manager does not recognize it. Im still a noobuntuGTK is the default GUI toolkit in Gnome (the default desktop environment in Ubuntu) Because it's default, you already have it. Besides, as a library, you never interact with it directly. Basically, GTK is responsible for drawing window contents, buttons, menus, etc.

> **Bakon Jarser said:**
> First of all, get out of the habit of googling for your programs.  Always search synaptic first.  System > Administration > Synaptic Package Manager.  You now have a whole world of free software to search through.  Every once in a while you'll need a program that isn't there but that should rarely happen.And in the *very rare* event that you need to install something that isn't available through the repos, see [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) .

> Second, I believe gtk is the default theme manager in Ubuntu.GTK is themeable, but it isn't a theme manager.

By the way, to install GTK or Metacity themes, simply drag and drop them onto the theme tab of the Appearance dialog.

---

### Post by winbutu on 2008-09-01
Yea, i already have a new firefox theme, and mac os X window borders and button, except black, border blue buttons.

;D

Its really awesome!

I find myself booting into ubuntu then vista already, its already a habit.
Sometimes it just boots up by itself because ubuntu is the default, vista you have to manually click before ubuntu starts up automatically in 9 seconds unless you do.

Kinda funny actually.

---

### Post by Bakon Jarser on 2008-09-01
> **mssever said:**
> GTK is the default GUI toolkit in Gnome (the default desktop environment in Ubuntu) Because it's default, you already have it. Besides, as a library, you never interact with it directly. Basically, GTK is responsible for drawing window contents, buttons, menus, etc.

And in the *very rare* event that you need to install something that isn't available through the repos, see [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) .

GTK is themeable, but it isn't a theme manager.

By the way, to install GTK or Metacity themes, simply drag and drop them onto the theme tab of the Appearance dialog.

good to know.  I get all that gtk, metacity, emerald stuff mll mixed up.  psychocats is a good web site, I was surprised to see that's where those images in post #1 came from recommending fat32.  I guess it shows you why you should never trust just one source.

---

### Post by winbutu on 2008-09-01
yup, this forum is awesome!

;D

---

