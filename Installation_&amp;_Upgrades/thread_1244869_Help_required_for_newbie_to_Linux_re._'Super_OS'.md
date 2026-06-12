---
title: "Help required for newbie to Linux re. 'Super OS'"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by paul48 on 2009-08-19
:) I am interested to trial use of Ubuntu on my sole Laptop that has WinXP-MCE, SP2, 2GHz Core2Duo, 1G RAM.
I initially booted a straight Ubuntu 9.04 CD for 30min, to discover it drove the WXDA screen and my ADSL internet ok, but the included Music and Video Players would not play MP3's, DVDs, .AVIs, .RMVBs or any other music or film, due to lack of codecs.  Somewhere suggested 'Super Ubuntu' (now the vaguely named 'Super OS' acc to Search engines) was a 'more complete, ready to run out of box' port of Ubuntu.  After many tries, I managed to dl the 0.96GB Super_OS_9.04.iso from goukihq.hackolive.  I tried to 'mount' that into my Windows 'Virtual CloneDrive (F:) but got errmsg "to run. you need .NET V2.0.5...  Nevertheless, it WAS Mounted so able to browse files, and see a file called wubi.exe in root dated 25/4/09, also 'CD2USB.bat' that may be relevant to what I want to do:

**I want to SAFELY trial use of 'Super OS' for some weeks or months, WITHOUT ALTERING OR DAMAGING MY EXISTING WinXP installation in any way**, as travelling far from home, I am absolutely dependant on my Laptop for Skype, email, bank access back home.  I thought for a Trial Installation, my most efficient install method to balance performance against minimal intrusion onto my WinXP system, was to be able to ideally RUN it from my Virtual Clone Drive, OR Boot from a USB Pendrive (I assume running a 0.96GB DVD disk would be v. slow - and see from browsing the .ISO, it is organised as 2 CDs !. so possible issues there).

**My question is**, **can I RUN it, or a derived version of it, from my Virtual DVD (prefered, as it should be faster than PenDrive), or from a Pendrive ?**

**In either case, grateful for newbie instructions on 'how to**', and in either case, how much spare HD space do I need, and **what reasonable minimum size of Pendrive**. - I think safer to buy a new Pendrive reserved for Super OS, as not clr if it reformats Pendrive... much important portable data on my existing pendrive, where I don't take Laptop.

Although it would be nice to acces my Broadband ISP when in 'Super OS', and play my .mp3 and .wma collection, and films in DVD, .AVI and .rmvb (already use VLC 0.99), main reason for Trialling a LINUX, is to explore simple Application programming in C and possibly Java, for embedded CPU's, where I heard the target API envrironment is more UNIXlike than Windows, so was thinking to go directly to LINUX, rather than Sun Beans IDE 6.7 for Windows.  Grateful for thoughts if my idea to go directly to LINUX OS is more time-consuming than the later.  If the above is successful, then once confident, I may go to what seems to be the preferred install onto a sep partition on my HD, currently C:60GB, D:90GB, not much spare as I use much multimedia, so like to know how much Windows space lost if installing into sep partition. I hear an alternative to that is to install into a '**VirtualBox**' - see a file of that name on the goukihk mirror. **Is that better than the tradition of separate partition ?**   Thanks in advance for help

---

### Post by 3rdalbum on 2009-08-19
Okay, that's a lot of questions there so forgive me if I miss out a few.

It's very easy to install codecs and DVD playback support onto Ubuntu. Ubuntu actually does most of it for you - you start to play an MP3 file and it will download the codec for you (with your permission). DVD playback can be installed by visiting [www.medibuntu.com](www.medibuntu.com) and following the instructions there, and then installing VLC Media Player from the Synaptic Package Manager program.

The main advantage with using Ubuntu is stability - it's better tested than those derivatives. You'll also find that the derivative distributions like Linux Mint and this "Super OS" cannot be upgraded to new versions. You will save yourself a LOT of time in the long run by installing real Ubuntu and adding the codecs.

The best way of installing Ubuntu is to boot it up and run the Install program on the desktop. When you are asked whether you want to erase a disk, resize a partition etc, you choose "Resize partition" and move the slider in the bottom bar graph, toward the left to allocate space for Ubuntu.

This is 99% safe for your data, but you should back up your Windows data just in case. It is the best way to install Ubuntu because it becomes independent of Windows, e.g. you can still run Ubuntu even if your Windows gets viruses and crashes.

The second option is to insert the Ubuntu CD while Windows is running, and choose the "Install in Windows" option from the menu. (This method is known as a "Wubi" installation). This will install Ubuntu within a file on your Windows partition, and when you boot up your computer it will ask you if you want to run Windows or Ubuntu. This is virtually 100% safe and allows you to trial Ubuntu, with a limit of 30 gigabytes of disk space.

If Windows crashes for any reason, you will temporarily lose access to Ubuntu until you boot up Windows successfully TWICE. This is why I don't recommend the Wubi method.

Your third option is to install some virtualisation software such as Virtualbox, which will emulate a full PC. Install Ubuntu in there and there is 0% risk to Windows, and you can even store the virtual machine's data on a pen drive or any other Windows-mountable disk if you want. The downside is the lower performance, and you don't get the ability to directly use your computer's hardware within Ubuntu.

You cannot run a real or a Wubi installation of Ubuntu from a pendrive or this "virtual clone drive" you speak of. Frankly, the "virtual clone drive" sounds like an unneccessary complication to your computing setup.

For a full Ubuntu experience, you really need about 20 gigabytes of disk space. If worst comes to worst, 5 gigabytes will do, without a lot of room for applications.

So, in summary:

1. Use real Ubuntu and install the codecs onto it. Ubuntu will do most of this automatically for you when you try to play an MP3. Use the Medibuntu website to install DVD playback and all the other codecs. Ubuntu can be 100% set up in the GUI.

2. For best results, install Ubuntu as the traditional dual-boot method, onto your internal hard disk. Don't forget to specify that you want to "resize partition", and ESPECIALLLY don't forget to move the slider to the left in order to give Ubuntu some space to play with.

3. Other possible methods are "Wubi" (installing into a file on Windows) and "virtualisation" (installing Ubuntu into an emulated PC) but these have particular drawbacks that you will probably not like.

4. If in doubt, do not install ANY new operating system on any computer that you depend on for your work. Wait until you get home and have access to another computer.

---

### Post by SoftwareExplorer on 2009-08-19
First, welcome to the ubuntu forums.  :)
Ubuntu can play mp3s, DVDs and AVIs. I have never even heard of rmvbs but after a quick google search, it sounds like mplayer, which runs on ubuntu can  play them. You just have to install mplayer, the ubuntu-restricted-extras, and a dvdplayer program (all of these tasks are easy with ubuntu package management) and you're good to go. So basically I'm recommending plain ubuntu, but of course it is your computer, not mine, so it is your decision. If you use the wubi program when you have an ubuntu image in Virtual DVD, you should be able to install it that way. When you install with wubi, there's basically zilch chance of messing up windows. If you need more help, just ask away.  :)

---

### Post by SoftwareExplorer on 2009-08-19
Looks like it took to long to write my reply. The rebooting windows twice thing is true with the wubi, but if you are depending on your computer and want to be 99% safe, then I would use wubi.

---

### Post by raymondh on 2009-08-20
If your BIOS allows booting from a USB, I suggest making a persistent USB of Jaunty.  Whenever you have the need to 'try' ubuntu, you can boot into the USB and have fun learning this distro/OS.

If you want to review the process ... [here's the guid]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/")e.

I suggest you use a 4 - 8GB thumb drive.

---

### Post by paul48 on 2009-08-20
Many thanks for your helpful reply.
Taking your points in turn, during the 30min session with the physical Ubuntu 9.04 CD I do remember when trying to play the various multimedia types I use MP3. RMVB etc, it did Prompt to search for the codecs to install, I thought I clicked yes to do the Search but it came up with not found (it was able to use my ADSL connection to access the net).  

However, I was concerned NOT to actually proceed/store new software on my HD, so if it had found codecs, I would have stopped at that point.  As mentioned, am ABOSLUTELY DEPENDANT ON MY LAPTOP for my daily work, can't risk corrupting any of my Windows installation at all, hence my saying I want to TRIAL Ubuntu for a few weeks or months, preferably as a 'LIVE DVD' - but without the speed penalty of a physical DVD, hence my mentioning running on my Virtual Clone Drive, failing that, a 'LIVE USB'.  I'll probably only trial Ubuntu a day a week until I know it enough to write C or Java on it using Sun NetBeans 6.7.  So it seems too invasive to start repartioning my HD or otherwise making a permanent installation of LINUX.  As I regularly reboot Windows on my laptop, I would prefer not to slow further the already too-long boot time by introducing a Boot Prompt (or... seem to remember from my DOS 5 days, playing with boot managers that default to preferred choice quickly in absence of KB input).

Re. your comment on not being able to upgrade 'Super OS' (which the website says its based on Ubuntu 9.04).  As a newcomer, I hope not want to upgrade often (not upgraded my Office 97 in Windows as it does what I want).  I see  Netbeans.org 'recommend' older Ubuntu 8 rather than 9.  So hopefully, won't need next Ubuntu until well after my evaluation.  Think I got recommendation to goto 'Super Ubuntu' as a **'works out-of-the-box' experience** [for Trialers] from Wikipedia and a few blogs, and as it said 'all codecs included on DVD', I thought Great -**don't have to actually 'Install' anything onto my HD** and risk screwing my Windows work.  Or is this wishfull thinking ?

Are you saying more likely to have crashes with 'Super OS' compared to straight Ubuntu ? 

Re. 99% safe and 'if Windows crashes', also your Summary #4 **wait till I have a 2nd PC :  Not an option**, I am nomadic, away from base 3 yrs, no space for paper computer books, much less 2 laptops  For me 99% not reliable enough. Had my Dell Inspiron laptop near 3 yrs and I don't remember my WinXP SP2 EVER crashing.  I often feared it would, as the hardware has had probs from Day#1, and Dell Guarantee U/S.  Only disaster was a HD Headcrash/new HD/installing Windows- other than that, never lost data.  Want to keep it that way. I note your point about traditional sep partition for LINUX 'best' as independant from Windows - prefer to wait for post-trial, more permanent instal.

By the way: can I choose to shrink only D: not C: ?... seem to remember Linux needed a sep small Paging Partition, another drive letter - is that still so ?

Re. your option#2 WUBI.  This sounds more attractive than your #1 for trialing, but from your text it again interferes with the boot process, when for most reboots I will choose Windows.  You say it "will install Ubuntu within a file on your Windows partition" - is this an equivalent answer to my Q about being able to run it as a 'LIVE DVD' inside my Virtual DVD ?

Re. your option#3  'Virtual Box'. I first came across this with Sun's product, then saw a ref to a 'VirtualBox' in the 'Super OS' dl mirror site - does that mean VB is a popular install for 'Super OS' ?  Also with this #3, am not worried about speed during a trial, but are you also saying Super OS cannot access my ADSL internet connection & other peripherals when running in VB ? - that would be a downer.

Re. my Q on how much HD space lost from Windows, you mention 5GB min, 20GB full
I was only thinking to play my Windows hosted multimedia collection to see a little of LINUX capabilities driving PC hardware in general, not essential.  As Windows is my main platform, only purpose of the Trial is for dedicated programming using the Netbeans IDE.  The Netbeans site says 650MB of HD space taken by the IDE in Ubuntu 9.04. 
I am guessing say 300MB max to develop a C or Java 'Project' (when done will archive externally to free space)
Again, roughly guessing the 0.96GB Super OS may 'unpack' into say 3GB max ?  Maybe another 1GB for cache ? That seems to indicate a total HD space of 5GB if I add no more applications.

Am I being too simplistic on HD space ?

As the Super OS ISO file has a 'CD2USB.bat' in the root, is not that an Option#4 ?   My Laptop BIOS can boot from USB. USB faster than DVD but slower than HD, **so my 2nd choice  on speed, but has advantage my Windows boot not interfered with unless 'Super OS' Pendrive is inserted.**  If this is correct, re. my simplistic estimate of a 5GB total memory requirement to run it, surely that is the max Pendrive I need to buy ? Pendrives very expensive in Brazil, so is it ok to store Linux Projects on a HD, (NTFS). Further Q on 'CD2USB.bat' - does it create a 'LIVE USB' or a 'full' boot install ?

Sorry about my dumb misconceptions/questions on this, but not obvious from the little intro articles seen.    Thanks again for your help.

---

### Post by PhilGil on 2009-08-20
I don't believe booting to a USB drive will alter your Windows install at all.  Others may correct me on this, but Ubuntu should not write anything to your hard drive unless you tell it to.  All software installs and changes to the Linux system will write back to the pen drive.

I also think Wubi is a fine option.  The entire Ubuntu system is contained within a single file on your hard drive, so there is very little chance that your Windows install will become corrupted.  The only Windows XP file that Wubi writes to is the boot.ini file - it adds a line so you can choose to boot to Ubuntu or Windows.  I believe Windows remains the default boot option.  When I deleted my Wubi install I did have to manually edit my boot.ini file to remove the option to choose Ubuntu, but I was still able to boot into Windows regardless.

---

### Post by paul48 on 2009-08-21
Many thanks for all your helpful inputs, from which am getting the idea the WUBI intallation may be my preferred Trial installation, and so would like to focus Q&A on a WUBI install.

Am still thinking to go for the 'Super OS' version for reasons given in prev. post, and again, it would be nice to 'play' my existing multimedia collection if only to confirm it will drive my hardware ok. (VLC supports .RMVB in Windows)

1)    With WUBI, does it use existing Windows drivers to run my Internet connection, (be it ADSL, WiFi), other Dell peripherals eg. screen modes, energy saving modes, hard-button multimedia controls on front of laptop ?

2)    During WUBI install, is a 10GB 'size' sufficient, given my main use will be writing C and Java small apps using Sun's Netbeans, using my simple calculation in last post of a 5GB total (3GB for Super Ubuntu, 1GB for PagingFile ? 1GB for Netbeans + Application) ?

3)    My internal HD is c:60GB, D:90 GB.  Is it ok to create the WUBI 'file' on D: ?  ...does it make any diff C or D ?

4)    Any other prompts in WUBI install that need aforethought ?

5)  Once basic install done and desktop tools available, will I be able to access the internet and use all my laptop facilities like during my initial 30 min try of the straight Ubuntu LIVE CD ?

6)    Can I read/write my other files stored in rest of the computer, and use all my existing data files as if from Windows ?

7)    Am I right in thinking Ubuntu used sytem RAM for all its paging needs, no longer creates a paging file on disk ?
Thanks again.

---

### Post by PhilGil on 2009-08-21
> **paul48 said:**
> Am still thinking to go for the 'Super OS' version for reasons given in prev. post, and again, it would be nice to 'play' my existing multimedia collection if only to confirm it will drive my hardware ok. (VLC supports .RMVB in Windows)

Or install from the regular Ubuntu CD then install the ubuntu-restricted-extras package from the Synaptic Package Manager.

> **paul48 said:**
> 1)    With WUBI, does it use existing Windows drivers to run my Internet connection, (be it ADSL, WiFi), other Dell peripherals eg. screen modes, energy saving modes, hard-button multimedia controls on front of laptop ?

No, Ubuntu manages all that using Linux drivers.

> **paul48 said:**
> 2)    During WUBI install, is a 10GB 'size' sufficient, given my main use will be writing C and Java small apps using Sun's Netbeans, using my simple calculation in last post of a 5GB total (3GB for Super Ubuntu, 1GB for PagingFile ? 1GB for Netbeans + Application) ?

Probably - depends on how big the Netbeans Package is.

> **paul48 said:**
> 3)    My internal HD is c:60GB, D:90 GB.  Is it ok to create the WUBI 'file' on D: ?  ...does it make any diff C or D ?

As I recall (it's been a while since I've done a WUBI install) , the WUBI file can be on any drive in your system.

> **paul48 said:**
> 4)    Any other prompts in WUBI install that need aforethought ?

Not that I can recall - install is very straightforward.

> **paul48 said:**
> 5)  Once basic install done and desktop tools available, will I be able to access the internet and use all my laptop facilities like during my initial 30 min try of the straight Ubuntu LIVE CD ?

If everything worked out of the box using the Live CD, it will work the same way after the WUBI install.

> **paul48 said:**
> 6)    Can I read/write my other files stored in rest of the computer, and use all my existing data files as if from Windows ?

Yes

> **paul48 said:**
> 7)    Am I right in thinking Ubuntu used sytem RAM for all its paging needs, no longer creates a paging file on disk ?
Thanks again.

Not sure

**WUBI FAQ here: [URL="http://wubi-installer.org/faq.php"]http://wubi-installer.org/faq.php
[/URL]

---

### Post by presence1960 on 2009-08-21
I went to the wiki for super os. Don't take this the wrong way, but in my opinion using the super os is going to deprive you of learning more about linux and computing in general. One of the greatest things I have experienced in linux is the ability to learn new things no matter how much I think I have already learned. I don't ever want to go back to my Windows days of just doing things because "that is how you do it", but never really learning how & why things work. Yes point & click can be convenient, but even those who think they aren't smart enough to use anything else are selling their ability to learn & themselves so, so short. They are choosing to remain in the dark, when there is so much out there for them. And with Ubuntu you have the greatest community to help you along. Even when you botch something , if you pay attention to the help you get you will not only learn what the fix is, but why you broke it in the first place and why the fix works. There is a point in my opinion of making things to easy for people. Humans need to expand their horizons and challenge themselves.

---

### Post by paul48 on 2009-08-29
Away last week, not online.   Interested in your input "*in my opinion using the super os is going to deprive you of learning more about linux and computing in general*".      Bearing in mind the fairly limited objectives I said I was considering Linux for (exploring use of Sun-Netbeans IDE to write some C/Java apps, grateful if you can list the main disadvantages of using 'Super OS' compared to the basic Ubuntu, and/or articles throwing light on that.    A further query, again apologies for my ignorance, but can one use the 'repositories' fn in both distros to install/update Apps - without having to compile/build, i.e binary install like in Windows ?

---

