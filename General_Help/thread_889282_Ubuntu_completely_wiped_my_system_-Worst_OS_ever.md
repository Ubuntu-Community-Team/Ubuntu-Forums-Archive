---
title: "Ubuntu completely wiped my system -Worst OS ever?"
date: 2008-08-13
forum: General Help
---

### Post by Biggerbean on 2008-08-13
About 3 days ago I posted that I need help with recovering information from my hard drive.  (After 2 days, one person finally responded...but unfortunately it wasn't that useful.)

Far worse, I'd originally posted that I'd entered the following into the Terminal:
sudo dd_rescue /dev/sdb3 /dev/sda1. 

WELL, that's the absolutely worst thing I could have entered. For 3 days it chugged at 'recovering' my damaged drive...only to WIPE OUT MY MAIN HDD and utterly destroy Ubunto, making the whole system worthless by replacing it with a replica of the information from the damaged drive. 

But I can't even open any of the files I 'see' on that drive (I can see the structure and file names, but nothing opens. 

Did Ubunto give a warning that I'd be wiping out my operating system and all my personal and work files??? No.  No? No. Why? Because Ubuntu blows. Worst, least user friendly program, ever. I mean, why issue a warning about that? It's super obvious from the code above that is what would happen, right? Just like all the parameters are so incredibly obvious that there's no need to define them when you access the help page. 

Sudo dd_rescue -[edit by OldSoldier: removed expletive] -u -p -ur -OS

What can I say? I can't even salvage the files it did copy for days. (If anyone wants to help with that...I'm running off a DVD that ISN'T RW so unless Linux has a tendency to burn over a finished DVD, I can't get any worse off.) 

The worst part of this is: I still think Ubunto is better than Vista.

---

### Post by tamoneya on 2008-08-13
first of all you should realize that by entering "sudo" you are telling the OS: "I have root privileges, I know what Im doing" and then the OS will just let you go ahead.  

Now for fixing your system here some guidelines that you should try to follow.
1.  On the harddrive that had your data on it DO NOT write any thing to it.  Do not download programs to it, do not run an OS from it.  Do nothing on it.  From now on you can only read from it.
2.  Go find a secondary or external drive that you can transfer recovered data to during the recovery process.
3.  Now to recover the data I recommend using a program called TestDisk.  It is in the ubuntu repositories.  The way that you should run this program is by putting in the liveCD/Install CD (remember we arent running the OS from the disk anymore).  Then open up a terminal and run:```
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk
```

Then tell test disk to search your drive for lost partitions or files.  When/If it finds files tell it to save them to your external drive.

---

### Post by Mgiacchetti on 2008-08-13
lol as long as you still like it, thats all that counts :)

---

### Post by cardinals_fan on 2008-08-13
None of your "no"s apply to me.  I'm not a genius; I just never give anything root permissions unless I know exactly what it will do.

---

### Post by Biggerbean on 2008-08-13
> **tamoneya said:**
> first of all you should realize that by entering **"sudo"** you are telling the OS: "I have root privileges, I know what Im doing" and then the OS will just let you go ahead.  

  Then open up a terminal and run:```
**sudo** apt-get update
**sudo** apt-get install testdisk
**sudo** testdisk
```


Exactly. I've just proven, beyond a shadow of a doubt that *I have no idea what I'm doing.*  lol.  :)  

And just go and *find another hard drive*, like I have tons of them just lying around. What kind of computer dork do you think I am???  

OK, fine, I found *several*. On with the mission:

Results?
```
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release        
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [53.8kB]       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages             
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [12.3kB]          
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [298kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [6636B]     
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources [86.4kB]           
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [908B]       
Fetched 583kB in 8s (72.9kB/s)                                                 
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found 
```

It's almost Mac like in it's simplicity. ](*,)

Is the intention of this to recover the info I can see on the Hard drive (the data from a damaged USB device that now is written all over my previously functioning OS), or files from the vanished OS HDD, or both?  (Honestly, both would be ideal.)

---

### Post by troutbum13 on 2008-08-13
sorry you were running commands you didn't understand as root and things got hinky.

I will say I think it is hilarious that you base your judgment of ubuntu on the fact that it let you screw up...if you are looking for an OS that will baby-sit you linux might not be the right choice.

sudo= I know what I am doing, you didn't.

---

### Post by Sef on 2008-08-13
[Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") Wiki and Download page.

---

### Post by tuxxy on 2008-08-13
Ubuntu is the best OS ever, it wont go wrong on its own and certainly wont wipe itself, it cant protect itself from user error but it does a good job at everything else.

---

### Post by tamoneya on 2008-08-13
> **Biggerbean said:**
> Exactly. I've just proven, beyond a shadow of a doubt that *I have no idea what I'm doing.*  lol.

Results?
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release        
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [53.8kB]       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages             
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [12.3kB]          
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [298kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [6636B]     
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources [86.4kB]           
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [908B]       
Fetched 583kB in 8s (72.9kB/s)                                                 
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found

It's almost Mac like in it's simplicity. ](*,)

actually I think that is my fault.  I think you dont have the correct repos enabled.  Please go into system -> administration -> software sources.

When prompted enter in your password and then make sure that all the boxes are checked on the left most tab(ubuntu software).  You do not need the CD-ROM to be checked.  Then hit close and work through the prompts.  Then try running the commands again.

---

### Post by emarkay on 2008-08-14
Be cool - don't panic, [edited by OldSoldier: read the man pages], and when in doubt, DON'T!

But of course, you did back up all your data, didn't you?  

RULE NUMBER ONE:  MAGNETIC AND ELECTRONIC MEDIA IS NOT PERMANENT.  EVEN IF YOU ARE AN EXPERT, IT WILL DEGRADE.

Rule Number 1.5: Therefore make copies of it, preferably on different media, and store in different locations.

Rule number 1.x: Nothing lasts forever.

No Rule:  Input without 100% validation only makes forever happen sooner.

---

### Post by pansz on 2008-08-14
Personally, I think it is way too hard for a computer program to determine what is right and wrong, and what is dangerous.

So, I think I myself should know exactly what I am doing, before I type command to the computer.

---

### Post by Biggerbean on 2008-08-14
And it looks like I'm on my way to being sorted out...got testdisk up and running, reformatted an old drive (intentionally this time! And only used Google threetimes in order to figure out HOW! I used gparted and then g2fsprongs for the formerly OSX 10.1 --so I'm crossing my fingers that I can get some work of my main drive. 

Then BAM!:

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63

The harddisk (320 GB / 298 GiB) seems too small! (< 640 GB / 596 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
D HFS+                     0   1  1 48624 254 45  781160544
D HFS+                     1 131 23 48626 130  4  781160544
D HFS+                     1 133 34 48626 132 15  781160544
D HFS+                     1 135 29 48626 134 10  781160544
D HFS+                     1 138  9 48626 136 53  781160544
D HFS+                     1 148 44 48626 147 25  781160544
D HFS+                     1 150 15 48626 148 59  781160544
D HFS+                     1 152 18 48626 150 62  781160544
D HFS+                     1 155 62 48626 154 43  781160544
D HFS+                     1 158 26 48626 157  7  781160544

Continue

```


Ok, the only chice here is continue. That can't hurt, right? 

The next screen gives 3 'choices'
```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors
P HFS                     19 120 26    19 120 27          2
P ext3                    25   6  5 38653  30 56  620560384
P Linux SWAP 2         38653  30 59 38906  11 26    4063216










Structure: Ok.


Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock Backup superblock, 317 GB / 295 GiB

```

Gotta be honest here...this is where *some info* would come in handy...it looks like I can choose between 3 drives...but WHAT am I choosing??? The drive to write to? The drive to recover?

SDA1 is the 320GB main drive that I want information OFF OF.

SDC3 (formated in EXT3) is the drive I want to put that info (yes, I know it's too small...I have more drives...or perhaps I can do a partial recovery, burn a DVD and recover again? Or select key files? Regardless, most of the 320GB was blank...till I put 120GB of an old drive on it.)

So...what's the next move?

---

### Post by Biggerbean on 2008-08-14
> **pansz said:**
> Personally, I think it is way too hard for a computer program to determine what is right and wrong, and what is dangerous.

So, I think I myself should know exactly what I am doing, before I type command to the computer.

Really? I'd prefer that too. Wouldn't it be nice if we could all understand the commands? A wee bit of clarity in naming, a wee bit more information in when you type --help (like instead of *just* listing parameters...listing what the parameters *mean*? I know, I know, it might take up an extra 50kb on your new Terabyte drive...totally inefficient. But I'd take that over the inefficiency of Googling every step. 

I certainly don't think a program *could* determine right & wrong...but it could give you a hint that it's about to do something like write over your active system files. Even just interpreting in English what it's about to do, it would be nice as the command labels *aren't particularly clear.*  

Are you telling me you've never typed in something without knowing 100% in advance what it would do? No trial & error, ever?

---

### Post by zxscooby on 2008-08-14
DD is very dangerous in the wrong hands.
 If you read up on it you will find that it is also 
known by the alias Destroy Data, because a very simple mistake
when issuing commands can spell disaster.

---

### Post by lisati on 2008-08-14
> **Biggerbean said:**
> Are you telling me you've never typed in something without knowing 100% in advance what it would do? No trial & error, ever?

+1: when I first installed Ubuntu on my laptop, I had some minor annoyances to deal with. Research on the forums yielded solutions which I didn't fully understand at the time. I'm still not sure I fully understand them more than a year later!

---

### Post by kostkon on 2008-08-14
DD is powerful tool and you did not do the necessary research before using it.

I don't think that if you put a highly specialised system command in the windows command prompt you'll get a warning or some type of helpful hint either.

The way I see it is that it was your mistake and now you are blaming the OS.

It's like shooting yourself in the foot and then blaming the gun...

---

### Post by mb_webguy on 2008-08-14
I'm with cardinals_fan.  None of your poll options apply to me.  I'm no genius (well, technically, depending on which test you use...), but I know enough that you never type "sudo" unless you really know what you're doing.  It's no different than messing with your Windows installation with Administrator privileges.  If you edit/move/delete a file in your C:\Windows\System32 folder, you're just asking to hose your installation.

Linux gives you more power over your system than Windows, but, to paraphrase the guy in the spider suit, "With great power comes great responsibility not to shoot yourself in the foot".  

I have nothing but sympathy for your plight, but never point a gun at someone unless you're prepared to shoot them, and never, *ever* type "sudo", "gksu", or "gksudo" before a command unless you know *exactly* what you're doing.

---

### Post by jharadie on 2008-08-14
In the poll you don''t have
Yes:  Because I was following a workaround I found in the forums for when the install hung on installing locales.

I've had nothing but horrors trying to install 8.04LTS, and so has everybody I've talked to.  Many of the horror stories rival what we've heard from our unfortunate friends using Vista.

I can't prove that it was the 8.04 OS, but at the same time that my system hung, my drives wiped and/or corrupted, one of my 1G RAM sticks died.  Two seconds into memtest and the segfaults just kept going and going and going...

I give up.  I'm going back to 7.10, and it's going to take a lot of convincing me to upgrade even after 7.10 ends life.

Don't get me wrong - I'm not leaving Ubuntu.  Ubuntu is arguably setting a great standard for Linux in general, and has (notice I said "has" not "had") the best opportunity to give Bill Gates some seriously severely major heartburn.  But I'm TERRIBLY disappointed with 8.04, as one friend told me, it's the Vista version of Ubuntu.  Ever since I started using Linux in the mid-90's (RH7.x), it wasn't until Ubuntu 7.04 that I finally broke away from being a "Micro$oft of Borg."  I've used Freespire, Linspire, Fedora, and experimented with others, but Ubuntu is by far the leader.  I just hope it hasn't shot itself in the foot with 8.04.

The Linux community has always been smarter, more innovative, more collegiate (despite a significant abundance of arrogant types), and most importantly, forward-looking.  The biggest fault I've seen (in Linux in general, not just Ubuntu) is that in looking forward, it's too easy to forget to look around.

Looking foward to significant improvements in 8.10 (though again, it will take a lot of convincing), and maybe it will be made an LTS, too, given what I personally see as too many failures in 8.04, and the fact that I've never understood an 18-month life cycle.

Then again, I'm just one person...  :)

---

### Post by mcduck on 2008-08-14
[QUOTE=Biggerbean;5585313]a wee bit more information in when you type --help (like instead of *just* listing parameters...listing what the parameters *mean*?QUOTE]
That's what the manual pages are for. reun "man COMMAND" and you'll get the manual for that command. And sometimes yothere might even be info pages available, which would give even more detailed information: "info COMMAND".

The purpose of "--?" _is_ to just give a quick reference to most commonly used parameters, for those situations when you don't need the more detailed instructions. ;)

Really, I feel sorry for you, but you can only blame yourself. I'd say that the two most important rules in computing are to 1: _Always_ have a backup. and 2: Find out what you are doing _before_ you do it. 

..and I didn't find any suitable option in the poll. Something along the lines of "No, because I always read the manual if I don't know what I'm doing".. :)

---

### Post by deep64blue on 2008-08-14
Using dd in a terminal window with sudo privileges is hardly Ubuntu's fault is it ...

---

### Post by Biggerbean on 2008-08-14
Ok, I get it. Don't type sudo because I'm a newbie. Would someone please enlighten me: what *should I have typed?*  Perhaps there's a non-sudo solution that I'm overlooking? And I'd also love to know exactly what it was about the command I typed that was so off?

Oh, and thanks for that wiki link on testdisk...very useful. As was the comment about typing "man" for the manual on the command.  It might be helpful to add that option to the 'help' list so newbies can get a clue. (I've been digging around Ubuntu forums for about a week and this is the first time I've encountered that tidbit.)

---

### Post by tamoneya on 2008-08-14
that screen where test disk lists the three disks it is showing you all the possible partitions that it found (deleted or still existing).  What you need to do now is look at them and determine which of them is the one with your data.  Now I am assuming your data was one a windows partition since you just migrated to linux.  In that case it means that you probably want the HFS partition.  Tell testdisk to list all the files ("P" key).  The only potential problem I see with that partition is its detected size.  It is very small and I dont think it will have much in it.  Could you possibly tell us a little bit about how your partitions were setup before this whole mess was created.

---

### Post by deep64blue on 2008-08-14
> **Biggerbean said:**
> Ok, I get it. Don't type sudo because I'm a newbie. Would someone please enlighten me: what *should I have typed?*  

You should have typed nothing at all until you had thoroughly researched the problem and knew exactly what you were doing.

> **Biggerbean said:**
> And I'd also love to know exactly what it was about the command I typed that was so off?


2) You told the system to take the contents from one partition and write them onto another then complained when you couldn't read the partition you just wrote all over.

---

### Post by decoherence on 2008-08-14
In situations like this i compare the command line to the windows registry. Are there some things in Windows that can only be configured through the registry? Absolutely. Would you hack around in the registry or blindly follow random advice without being familiar with the part of the registry you're editing? Absolutely not.

If you aren't comfortable editing the registry or using the command line, it is better to find a trustworthy GUI program to do it for you.

That is all.

---

### Post by lukjad on 2008-08-14
I hosed my system once, but I had to use two operating systems to do it. I had somehow installed a system on only one of my two hard drives and the other one was considered to be only a folder. So, instead of doing the smart thing and backing up in Ubuntu, I thought that I would do a backup in another OS that I was not familiar with. I tried to create a disk image on an external hard drive, which then wiped the disk. I lost a lot of data. It wasn't Ubuntu's fault, really, but it was involved. It was more of an i dee ten tee error.

---

### Post by Biggerbean on 2008-08-14
> **deep64blue said:**
> You should have typed nothing at all until you had thoroughly researched the problem and knew exactly what you were doing.



2) You told the system to take the contents from one partition and write them onto another then complained when you couldn't read the partition you just wrote all over.


In response to (1)...we covered that already. I'm asking, is there a way to do this without typing sudo and putting the system at risk? Or are users forced to thoroughly research (more so than the 25 web pages I opened before I made my move ... the more common instructions yielded errors and simply didn't work)...making the system, how to say this politely, user-unfriendly. 

What I asked was, *what should I have typed.*


(2) No kidding. Is that what happened?? (*Sarcastic*) I knew that already, thanks. From reading the line, I already deduced that was exactly what it did and ALSO *exactly* what I asked it to do.  Could someone break the correct format of this command. It seems that writing it to a specific file name & location (eg. /dev/sda1/badimage.iso writes it to a file *on* the drive but omit "badimage.iso" and it writes *over* your entire drive. Is this a correct understanding?

---

### Post by tamoneya on 2008-08-14
> **Biggerbean said:**
> In response to (1)...we covered that already. I'm asking, is there a way to do this without typing sudo and putting the system at risk? Or are users forced to thoroughly research (more so than the 25 web pages I opened before I made my move ... the more common instructions yielded errors and simply didn't work)...making the system, how to say this politely, user-unfriendly.


(2) No kidding. Is that what happened?? (*Sarcastic*) I knew that already, thanks. What I asked was, *what should I have typed.*

You should have used testdisk as i am trying to guide you through.  dd_rescue is not meant to deal with filesystem level recovery.  It does things at the bit and block levels.  Even using dd_rescue correctly wouldnt have done any good in your situation.

---

### Post by Biggerbean on 2008-08-16
> **tamoneya said:**
> You should have used testdisk as i am trying to guide you through.  dd_rescue is not meant to deal with filesystem level recovery.  It does things at the bit and block levels.  Even using dd_rescue correctly wouldnt have done any good in your situation.

Ok, test disk doesn't seem to find anything of value. Not a single buried file. (The drive was overwritten with more data than was originally on it --so that's not too surprising. But I don't seem to see any data from the overwritten information either. 

To make matters WAY worse, a young guy is 'helping' me out --and just informed me that he has just formatted a couple of Harddrives with Ubuntu for me.  

ME: "Where'd you get the drives?"

Him: "From your old computer."

Me: "Of %&^* -- those drives weren't empty. They had everything else on them."

I'm going to go find somebody to give me a smoke.

And...I'm really going to need some help now. All my work, my backups, everything was on these THREE newly formatted drives. 

How's that for 'user error'?

Rock on.

---

### Post by cybrsaylr on 2008-08-16
> **Biggerbean said:**
> 

Are you telling me you've never typed in something without knowing 100% in advance what it would do? No trial & error, ever?

Been using Ubuntu for a little over a year and it is a great OS. When is comes to sudo I would never type something in unless I knew exactly what it will do. This is NOT the place for trial and error. You can't blame the OS for operator error.

---

