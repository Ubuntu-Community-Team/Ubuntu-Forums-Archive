---
title: "Ubuntu impossible to install!"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by compusolver on 2009-09-15
I started with a Red Hat Linux version several months ago, never could get it to install.  Gave up and bought a big manual with Ubuntu 8.04.  Tried two days straight on two different computers, never got it installed.

Bought 9.04 and another book.  Today I have switched everything on this computer, motherboard, ram, video card, tried three different harddrives (ide & sata) and three different dvd drives and gave up on the cd with the book and downloaded 9.04 from the Ubuntu site but Nero said there was a problem with the iso file, and the burn doesn't work.

Back to the 9.04 with the book..  It gives a bunch (497+) of dos-like error messages against a black screen as it boots up, then has me set language, computer name, etc.  Although I am going to let it partition and format the drive, it insists on "scanning" the drive before I get to the partition option and it gets errors there or at "detecting file systems" and just loops through all this over again and again.

I see now how Windows has stayed on top for so long!

Is there only some special computer brand that Ubuntu will install on?  Is there some magic incantation you have to do?  What is the secret to installing Ubuntu?

By the way, I am a database programmer and web developer with nearly thirty years experience in coding.  I build my own computers and run a six-pc network, which I setup and maintain myself.  If I can't install Linux, it'll never get popular with the masses!!

---

### Post by running_rabbit07 on 2009-09-15
Bad CD burn maybe? That is what it sounds like. What speed are you burning at? Did you do the check disk function when the LiveCD first boots?

---

### Post by running_rabbit07 on 2009-09-15
> **compusolver said:**
> I see now how Windows has stayed on top for so long!

Is there only some special computer brand that Ubuntu will install on?  Is there some magic incantation you have to do?  What is the secret to installing Ubuntu?

Patience. Being able to start at the beginning. Playing nice with others. We are all volunteers here.

---

### Post by staf0048 on 2009-09-15
I've not had any "major" problems installing on 4 different machines.  2 laptops and 2 desktops.  Additionally, the only "issues" I've had were related to video cards and getting compiz to work.

1st was a generic computer built in 2001 that came shipped with XP(I do not remember the brand at all), 2nd was a Toshiba Satellite that came with XP, 3rd was another Toshiba Satellite that came with Vista, and the 4th is an HP Pavillion that also came with Vista.  Was able to get Ubuntu up and running within 1 hour and each and every machine - not special chants, seances, or lucky charms needed.  

I know it doesn't help your situation at the moment, but I assure you your experience is the exception rather than the rule.

---

### Post by David-IT on 2009-09-15
well personally you can try to go and get Gparted Live cd then whype your HDD'S totally clean. and format them to EXT3 that might help but it does sound like a bad disk try burning it at 2x-4x speed's if possible GL man!

---

### Post by Flying caveman on 2009-09-15
:-({|=

---

### Post by sgosnell on 2009-09-15
Did you check the md5sum to make sure you had a good file download?  Did you check the CD to make sure you got a good burn?  These two account for most of the problems I've ever seen.  If those are definitely good, there is a possibility of a defective HDD, and a defective CD drive. I've seen both of those cause problems.  None of these are caused by the OS, whether it's Windows, Mac, or any Linux variant.

---

### Post by QIII on 2009-09-15
I'm sorry you are having difficulties.  That is exceptionally rare.  Installing Ubuntu is far easier than installing Windows.  Installation should take maybe 8 mouseclicks and a few keystrokes to set up your computer name, account name and password.

You "bought" an Ubuntu CD?  What book did it come with?  Was the disk from Canonical?

You should not be having this sort of trouble with your installation unless the is a problem with the disk.

Did you check the md5 hash?  The following tells you how to do it with 8.10, just change references to 9.04.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Have your tried to run LiveCD?  

There is an option to check the disk for integrity.  Do that.  If it passes both the md5sum check and the integrity test, move on.

Select the option to run without making changes to your machine.  If it doesn't run, you may need a new copy.  (Remember that it will probably run painfully slowly from the CD, so keep in mind that this is NOT how Ubuntu will respond when actually installed.)

If the md5sum and integrity tests fail, use a torrent client to download the ISO.  Check the md5sum.

Burn the image as slowly as you can stand or as slowly as your burner will allow.

Run the integrity check.  Attempt to run the LiveCD.

35 years doing the computer gig here.  I haven't had problems installing Ubuntu since 2004 ...  Didn't have much trouble back in the days when we had to compile our own kernels for years before that.

---

### Post by running_rabbit07 on 2009-09-15
> **QIII said:**
> You "bought" an Ubuntu CD?  What book did it come with?  Was the disk from Canonical?.

He bought the book on Ubuntu 9.04, I think.

---

### Post by running_rabbit07 on 2009-09-15
> **sgosnell said:**
> Did you check the md5sum to make sure you had a good file download?  Did you check the CD to make sure you got a good burn?  These two account for most of the problems I've ever seen.  If those are definitely good, there is a possibility of a defective HDD, and a defective CD drive. I've seen both of those cause problems.  None of these are caused by the OS, whether it's Windows, Mac, or any Linux variant.

I agree. I burnt Window 7 to disk and it turned out to be a bad burn. Same thing with my XP Pro.

---

### Post by steveneddy on 2009-09-15
> **compusolver said:**
> 

Is there only some special computer brand that Ubuntu will install on?  Is there some magic incantation you have to do?  What is the secret to installing Ubuntu?



First of all we aren't going to hold the programmer stuff against you. It's OK,  really.

Hardware compatibility is your main issue I believe.

Much like Windows, one must use compatible hardware.

Either check the hot sheets or buy a product from vendors like System76.

It is entirely possible that the hardware you are using is just too new.

Try one year old hardware or buy a preinstalled product.

Links:

[http://webapps.ubuntu.com/certification/list/?category=Laptop](http://webapps.ubuntu.com/certification/list/?category=Laptop)

[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

[http://tldp.org/HOWTO/Hardware-HOWTO/motherboards.html](http://tldp.org/HOWTO/Hardware-HOWTO/motherboards.html)

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

Pretty much Intel processors and Nvidia graphics work the best, but use the links to pick/choose hardware.

Or just post on the forums and ask if anyone else has issues with your hardware.

I wish you luck. don't be frustrated. It's just a learning experience that will pay off in droves once you get it figured out.

---

### Post by oboedad55 on 2009-09-15
> **compusolver said:**
> I started with a Red Hat Linux version several months ago, never could get it to install.  Gave up and bought a big manual with Ubuntu 8.04.  Tried two days straight on two different computers, never got it installed.

Bought 9.04 and another book.  Today I have switched everything on this computer, motherboard, ram, video card, tried three different harddrives (ide & sata) and three different dvd drives and gave up on the cd with the book and downloaded 9.04 from the Ubuntu site but Nero said there was a problem with the iso file, and the burn doesn't work.

Back to the 9.04 with the book..  It gives a bunch (497+) of dos-like error messages against a black screen as it boots up, then has me set language, computer name, etc.  Although I am going to let it partition and format the drive, it insists on "scanning" the drive before I get to the partition option and it gets errors there or at "detecting file systems" and just loops through all this over again and again.

I see now how Windows has stayed on top for so long!

Is there only some special computer brand that Ubuntu will install on?  Is there some magic incantation you have to do?  What is the secret to installing Ubuntu?

By the way, I am a database programmer and web developer with nearly thirty years experience in coding.  I build my own computers and run a six-pc network, which I setup and maintain myself.  If I can't install Linux, it'll never get popular with the masses!!

There's no magic to it, even I can do it. Why don't you let us know what kind of hardware you've got, esp. video card and we can try to help.

---

### Post by compusolver on 2009-09-15
Thanks for everyone's replies (hopefully that violin is playing Mozart!).  One book is "A Practical Guide to Ubuntu Linux, 2nd ed by Prentice Hall and the latest is "The Official Ubuntu Book" by the same publisher.  The first book was a Red Hat book, it's in another room.  All books came with dvd or cd.  All were brand new and purchased at B&N.

I'll try all these suggestions in the morning.  Thanks again, and sorry if I sounded grouchy, but I started this process at 10 this morning, now it is midnight.  Ubuntu, from my experience, is much, much more difficult than installing Windows, not in terms of user input but in terms of just working or not.

---

### Post by QIII on 2009-09-15
Your experience, as I said, is highly unusual.

I don't know that hardware being "too new" as suggested, is the culprit.  It may be.

---

### Post by steveneddy on 2009-09-15
> **compusolver said:**
> T  Ubuntu, from my experience, is much, much more difficult than installing Windows, not in terms of user input but in terms of just working or not.

It is actually easier than Windows.

You may be doing something wrong because most of us here can get a machine from nothing to working desktop in 30-45 minutes.

Make sure the machine is set to boot from CD.

Check CD for errors (on the list when booting live CD)

---

### Post by RemmyNumber7 on 2009-09-15
I to am having problems installing Ubuntu. I got a cd that i bought from online. I checked the disk for errors it said there was none. Question during the partition setup. Why dose it say scsi  even though i have an 80gb ide drive. Isn't scsi  a drive so don't i need a scsi drive to be able to install it. Anyway my main problem when installing is guided it goes through the motions goes to install the file system with the cd-rom lite on, loading everything it goes to a certain percent then stops. An error mesage show out saying bad disk can't go on hdd. then just stops. Iv'e changed the ribbin and the Cd-Rom and still won't load all the way to 100 % to install os. Any solution need help

---

### Post by Flying caveman on 2009-09-15
Well, you didn't actually ask a question.  


I could try to guess you have some weird BIOS settings possible causing problems though.

Pretty sure its still possible to install.  Ive had my problems installing before too, but have never failed to install Ubuntu.

---

### Post by Khakilang on 2009-09-15
I have install Ubuntu 8.10 and now 9.04. First on my old PC which is Pentium 4 with only 384MB RAM and 20GB hard disk and an old notebook Pentium M processor with 512MB RAM and 20GB hard disk without any problem. I just insert the CD and let it boot up. Key in the necessary info and let Ubuntu do the rest. Did you plug in any USB device by any chance? If yes unplug those and try again.

---

### Post by running_rabbit07 on 2009-09-15
> **RemmyNumber7 said:**
> I to am having problems installing Ubuntu. I got a cd that i bought from online. I checked the disk for errors it said there was none. Question during the partition setup. Why dose it say scsi  even though i have an 80gb ide drive. Isn't scsi  a drive so don't i need a scsi drive to be able to install it. Anyway my main problem when installing is guided it goes through the motions goes to install the file system with the cd-rom lite on, loading everything it goes to a certain percent then stops. An error mesage show out saying bad disk can't go on hdd. then just stops. Iv'e changed the ribbin and the Cd-Rom and still won't load all the way to 100 % to install os. Any solution need help

Welcome to Ubuntu Forums. Please start your own help thread and include your system specs.

Thanks

---

### Post by compusolver on 2009-09-16
I guess Ubuntu is just picky about hardware.  I downloaded the Ubuntu iso from the Ubuntu website and it seemed a bit better than the cds in the books, but it didn't like my SATA harddrive, even though it let me install from a SATA dvd drive.  It choked on two different ide harddrives before finally accepting the third one.  All these drives came out of running systems and now have been put back into other running (Windows) systems - but Ubuntu didn't like them.

Thanks to all for your replies!

---

### Post by PhilippeK on 2009-09-23
Same problem: all my attempts blocked at the partition (automatic freezes at 5 %), manual at 33 %, mini at 76 %. Gparted boot as well.
All clean install with Cds downloaded 4X from Ubuntu websites:
First successes were with 8.10 and 9.04 32 bits as well as 9.04 64 bits.
I upgraded the 9.04 32 bits with the Karmic Alpha 2: success
Failed with Karmic Alpha 2 64 bits, Alpha 6 32 or 64 bits
Now on my two computers only 9.10 Alpha 2 32 bits installed. even both 9.04 nor 9.04 mini installs anymore.
I finally reloaded windows XP and tried installing 9.04 as succeded before: impossible. anymore.

Do not understand how CDs which installed do not do anymore on same computers. All Cds have been tested as well as compatibility.
I can only install Karmic Alpha 2 but be careful with updates to not be obliged to reinstall. 

Dell laptop Latitude D810, Dell Optiplex 755 (that I can not run anymore in 64 bits).

I love Uuntu, but what a nightmare to install and what a fear when rebooting after updating.

I read a lot of pages, found a lot of advices, but nothing work really.

thank you for helping our "unusual cases"



I really love Ubuntu but am afraid

---

### Post by RemmyNumber7 on 2010-08-02
Maybe your BIOS in your motherboard is not Linux compatible

---

### Post by wizarddrummer on 2010-08-02
> **compusolver said:**
> I started with a Red Hat Linux version several months ago, never could get it to install.  Gave up and bought a big manual with Ubuntu 8.04.  Tried two days straight on two different computers, never got it installed.

Bought 9.04 and another book.  Today I have switched everything on this computer, motherboard, ram, video card, tried three different hard drives (ide & sata) and three different dvd drives and gave up on the cd with the book and downloaded 9.04 from the Ubuntu site but Nero said there was a problem with the iso file, and the burn doesn't work.

Back to the 9.04 with the book..  It gives a bunch (497+) of dos-like error messages against a black screen as it boots up, then has me set language, computer name, etc.  Although I am going to let it partition and format the drive, it insists on "scanning" the drive before I get to the partition option and it gets errors there or at "detecting file systems" and just loops through all this over again and again.

I see now how Windows has stayed on top for so long!

Is there only some special computer brand that Ubuntu will install on?  Is there some magic incantation you have to do?  What is the secret to installing Ubuntu?

By the way, I am a database programmer and web developer with nearly thirty years experience in coding.  I build my own computers and run a six-pc network, which I setup and maintain myself.  If I can't install Linux, it'll never get popular with the masses!!

Hmmm. 30 years experience? Then I have to assume that in 30 years you only participated in computer world created by Bill Gates. Which means you never experienced PDP 11's or VAX /VMS or UNIX System III or any of the myriad programming languages other than Microsoft Windows and it's development environment.

I started with computers in the early 70's. I too am a database (Unify, Oracle, DBIII, SyBase, ACCESS) programmer (PHP, ASSEMBLER (PC, VAX, Motorola), VBA, C, Objective C, Lisp, Pascal, ADA, and others) with network experience. I had a total of 250 machines and work stations (ethernet, FDDI, ATM, Token Ring / wired and fiber) with Sun Solaris, OS2, Windows, HP UX, NEXTSTEP and a DEC Alpha computer all connected together.

Your problem is your experience is working against you.

Operating systems that are Linux / UNIX derivatives are NOT Windows.

Ubuntu, if you take your time and study the differences, is a very easy installation. You must make sure that the CD is clean without errors. For a Windows only person, the concept of partitioning is a little difficult to grasp, but not beyond someone with your experience.

You should try to install SCO UNIX, or early versions of BSD (they have a hideous installation program)

That being said, if you can have the patience and you do get the new version of Ubuntu installed you will be pleasantly surprised at how much nicer this OS is compared to the clunky Windows.

The only reason I ever go into XP is that I have some databases that have extensive coding; more then 60,000 lines of VBA code that do intensive financial calculations and also upload and download information from the web that i can't easily migrate into the Linux world.

A few programs like Maya, Swishmax, Swishvideo, texture maker that i like to use, but other than that, Linux is my OS of choice.

Yes, you have to "work" a little, you have to, at times, go into the terminal and issue a few commands. Think DOS commands on steroids. 

Back in the day, the "terminal" was the ONLY thing we had. I used to write 10 to 15 shell scripts a day to automate things that I did.

You never mentioned what kind of machine you're running on, but that should not be an issue. A few things outside the realm of linux are the proprietary stuff from NVIDIA and other vendors that has to be added after the install. 

Unlike Windows, you don't have to install sound, networking and a host of other things after the installation.

Keep trying, you will be rewarded.

---

