---
title: "partitioning on new PC"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by Sasquatch2000 on 2009-01-07
Hello.

I just purchased a new motherboard/drive/memory (basically a new PC).

Before I start with it, I am wondering what the best approach is to using Ubuntu along with Windows XP Pro. 

Should I format the entire drive in NTFS using Windows' installer, and then just run Ubuntu on top of it? Or are there other, better or faster ways to run the Ubuntu OS?

How much of a partition does Ubuntu need for basic install, plus maybe some extras? Again, or should I just run on top of Windows?

I am at an opportune time right now to do this, but don't know where to begin. 

System specs:
[LIST]
[*]3.0 Gb/sec SATA drive
[*]ASUS M3A78-EM AM2+/AM2 AMD 780G HDMI Micro ATX AMD Motherboard
[*]AMD Athlon 64 X2 5050e Brisbane 2.6GHz Socket AM2 45W Dual-Core Processor
[*]G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model F2-6400CL5D-2GBNQ
[/LIST]

[COLOR="DarkRed"]Let me add that this motherboard has a built-in OS (ASUS Express Gate V1.3.13.2 for Windows XP) on the BIOS to let you get into the Internet in 5 seconds from hitting the power button, but before it hits the regular OS. Don't know if that affects anything here.[/COLOR]

Thank you!

---

### Post by Sasquatch2000 on 2009-01-07
Let me put this another way:

Should I format from Windows installer (DOS), or Ubuntu installer (linux), and what options should I take? What format should I use, and how big for Ubuntu?

What are the advantages and disadvantages to each install method, and do either affect performance, reliability, or usability?

---

### Post by Zeroberry on 2009-01-07
This should give you all the info you need.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I can add that Ubuntu can use ntfs formatted partitions just fine, especially for movies and so on, I run alot of my games off an ntfs partition as well. So the Ubuntu partition doesn't need to be very big. Good luck!

---

### Post by albinootje on 2009-01-07
> **Sasquatch2000 said:**
> Let me put this another way:

Should I format from Windows installer (DOS), or Ubuntu installer (linux), and what options should I take? What format should I use, and how big for Ubuntu?


The best thing to do is to install Windows first, give it a primary partition at the beginning of the disk, and leave space for the Ubuntu partition(s).
Then install Ubuntu.

NTFS is better for your Windows installation for several reasons.

How big is the hard disk ?
I suggest to give Ubuntu at least 10 Gb for the installation and your home directory.

---

### Post by Sasquatch2000 on 2009-01-07
It is a WD Caviar 500 (black) disk.

I was planning on doing an NTFS partition for Windows. OK, so two NTFS partitions it is then.
[LIST=1]
[*]How about 20 Gb for Ubuntu?
[*]Can Ubuntu and Windows share partitions?
[*]How could I share data between OS's?
[*]Could I, for example, use the same Firefox profile or at least bookmarks?
[*]By "just fine", does that mean that NTFS is the best way to format for Ubuntu?
[*]Can I use the Windows formatter to set it up since I'm in there anyhow, or is it better to do all the Windows stuff first, and then do the Ubuntu stuff from the Ubuntu CD?
[*]Any naming conventions to avoid or steer towards?
[*]Nobody has mentioned running Ubuntu inside Windows. Is this to be avoided for some reason? It sure seems like the web site is steering everyone in that direction.
[/LIST]

---

### Post by albinootje on 2009-01-07
> **Sasquatch2000 said:**
> It is a WD Caviar 500 (black) disk.

I was planning on doing an NTFS partition for Windows. OK, so two NTFS partitions it is then. How about 20 Gb for Ubuntu?

Good. But it depends how much data you will store.
In general it's a little easier to access NTFS partitions from Ubuntu then the other way around.
> 
Can Ubuntu and Windows share partitions? How could I share data between OS's? 

Yes. Ubuntu can read FAT and NTFS by default.
For Windows there is software to access ext2 and ext3 Ubuntu partitions.

See here : [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

> 
Could I, for example, use the same Firefox profile or at least bookmarks?

Not sure about sharing profiles right away, but it should be possible with a little work-around.
> 
By "just fine", does that mean that NTFS is the best way to format for Ubuntu? Can I use the Windows formatter to set it up since I'm in there anyhow? Any naming conventions to avoid or steer towards?

For Ubuntu you need at least a / (slash) partition, and a swap partition.
The / partition should be ext3.
There's also xfs,jfs and others, but using ext3 is recommended for a Linux beginner on a desktop.

---

### Post by albinootje on 2009-01-07
> **Zeroberry said:**
>  I can add that Ubuntu can use ntfs formatted partitions just fine, especially for movies and so on, I run alot of my games off an ntfs partition as well. So the Ubuntu partition doesn't need to be very big.

Well, in the past I tried using a VMware virtual disk from a NTFS partition, that gave problems (I think it was OK with using VirtualBox virtual disks from that NTFS partition in Ubuntu), for the rest I agree.

---

### Post by Sasquatch2000 on 2009-01-07
So an NTFS partition for Ubuntu is not good, and I need an ext3 for the / partition? Seems contradicting to what I just read.

Why would I want to use this if NTFS works just fine? 

What size do I need to make the swap partition? (I thought Ubuntu was supposed to be EASY!)

Are you saying I now need 2 partitions for Ubuntu and not just 1, for a total of 3 new NTFS partitions on my new drive (1-WinXP, 1-/, 1-swap)?

Finally, would it be easier to just do this all on an old IDE drive, since it is a practice/experimental area anyhow, or does that overly complicate things? I've got plenty of spare IDE drives sitting around which could be used.

---

### Post by albinootje on 2009-01-07
> **Sasquatch2000 said:**
> So an NTFS partition for Ubuntu is not good, and I need an ext3 for the / partition? Seems contradicting to what I just read.

Why would I want to use this if NTFS works just fine? 

You can perhaps install Ubuntu on a NTFS partition, but you will run into trouble soon.
Linux is flexible, MS-Windows usually not, or not all.
Imagine the option in the Windows to be able to choose Linux ext3 file system to format a partition.

The comments were about Linux accessing the NTFS partition of your Windows installation.
> 
What size do I need to make the swap partition? 

2 x RAM size is a rule of thumb.
> 
(I thought Ubuntu was supposed to be EASY!)

Imho there's only one "easy well-known" OS, and that's MacOSX ;)
> 
Are you saying I now need 2 partitions for Ubuntu and not just 1, for a total of 3 new NTFS partitions on my new drive (1-WinXP, 1-/, 1-swap)?

I would even recommend to make a separate /home partition for Ubuntu, that would make a total of 4 partitions.
> 
Finally, would it be easier to just do this all on an old IDE drive, since it is a practice/experimental area anyhow, or does that overly complicate things? I've got plenty of spare IDE drives sitting around which could be used.
It makes more sense to use only your new disk.

---

### Post by Sasquatch2000 on 2009-01-07
OK, here goes:
Using Windows installer, make a 476Gb NTFS partition.
Install Windows and do all associated setup.

After Windows is all OK on that partition:
Do or don't install Ubuntu within Windows?
Using Ubuntu installer, set up:
15Gb ext3 / partition
4Gb ext3 swap partition
5Gb ext3 home partition

Sound right? Finally down to just a few questions.

---

### Post by albinootje on 2009-01-07
> **Sasquatch2000 said:**
> 
Do or don't install Ubuntu within Windows?
Using Ubuntu installer, set up:
15Gb ext3 / partition
4Gb ext3 swap partition
5Gb ext3 home partition

Looks good.

And I'm probably not the only non-native english speaker here :| :)
What do you mean with "Do or don't install Ubuntu within Windows?" ?

---

### Post by Sasquatch2000 on 2009-01-07
> **albinootje said:**
> Looks good.

And I'm probably not the only non-native english speaker here :| :)
What do you mean with "Do or don't install Ubuntu within Windows?" ?

You know, the Installer where you can just run Ubuntu like it is an application. There is some acronym for it which escapes me right now.

---

### Post by albinootje on 2009-01-07
> **Sasquatch2000 said:**
> You know, the Installer where you can just run Ubuntu like it is an application. There is some acronym for it which escapes me right now.

Ah, you mean Wubi.

But.. please get a normal Ubuntu installation cdrom if you're already creating partitions for Ubuntu.

Wubi is only meant as a "safe" way to play with Ubuntu *located* inside MS-Windows without need for any partitions for Ubuntu.

I recommend you the 32 bit desktop version of Hardy :
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
Or if you are a little more adventurous Intrepid :
[http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)

---

### Post by NEUR0M4NCER on 2009-01-07
[noparse][disclaimer][/noparse]
I'm in the middle of sorting out my own borked system right now, so this advice may not be the best, but...
[noparse][/disclaimer][/noparse]

I would really, *really* recommend just installing Windows onto a 400GB partition, then booting the LiveCD and installing, using all of the defaults, on the remaining 100GB. With any luck, Ubuntu will detect your Windows install and import any settings you may or may not have there, and pretty much sort itself out. When you start to tinker is when things start to go wrong... Trust me, I know.

Regards

---

### Post by albinootje on 2009-01-07
> **NEUR0M4NCER said:**
>  I would really, *really* recommend just installing Windows onto a 400GB partition, then booting the LiveCD and installing, using all of the defaults, on the remaining 100GB.

Why would you recommend to let Ubuntu do the resizing during the Ubuntu installation when resizing is not needed at all in this setup because the OP will do a fresh MS-Windows installation anyway ?
Can you at least give arguments with possible sources ?

---

### Post by NEUR0M4NCER on 2009-01-07
*Whoa*...



No, I can't offer 'sources'. I was just trying to help out a fellow user with my (limited) experience.

For the desired outcome, it just seems more appropriate to go the default route, as the OP appears not to have much experience with Linux and all of its quirks. I'm sure you (with your mighty post count) can give much better advice...


Regards



**edit**
But if you're suggesting the more complex route, why on earth would you recommend 32bit when the OP is running AMD64? Arguments and possible sources please.

---

### Post by albinootje on 2009-01-07
> **NEUR0M4NCER said:**
>  No, I can't offer 'sources'. I was just trying to help out a fellow user with my (limited) experience.

For the desired outcome, it just seems more appropriate to go the default route, as the OP appears not to have much experience with Linux and all of its quirks. 

I didn't mean to offend you in any way.
The only reason that I'm asking is because of your "really,really recommend" remark.
That made me curious why you recommended this so persistently.

Many years ago I saw problems when a friend tried a dual Linux/Windows, he claimed that he got problems with his Windows (95) because of the dual boot, but that was around 1999 or so.
> 
But if you're suggesting the more complex route, why on earth would you recommend 32bit when the OP is running AMD64? Arguments and possible sources please.

Because for a beginner it's not easy to install the 64 bit flash player and Java for example.
And I noticed that the OP didn't have a machine with 4 Gb or more.

---

### Post by NEUR0M4NCER on 2009-01-07
> **albinootje said:**
> I didn't mean to offend you in any way.

Sorry - i'm having a bad day.

> **albinootje said:**
> The only reason that I'm asking is because of your "really,really recommend" remark.

Basically, i've re-installed both XP, and Ubuntu (7.04, 7.10, 8.04 and now 8.10) so many times, that I find the simplest, quickest way to do things is to let the installer go about its business. Sure, it might technically be a more roundabout way of doing things, but as a simple user, it saves a lot of time and effort.

> **albinootje said:**
> Many years ago I saw problems when a friend tried a dual Linux/Windows, he claimed that he got problems with his Windows (95) because of the dual boot, but that was around 1999 or so.

It works now. Honestly, it's probably the only thing i've never had to muck about with... unless i've already done something daft (which I have at the moment).

> **albinootje said:**
> Because for a beginner it's not easy to install the 64 bit flash player and Java for example.

Hooooooo boy, you would get hounded out of the 64bit sub-forum!! It's actually not too complex now. The stickies over in that area are *very* simple, and a lot of the time, aren't even needed now.

> **albinootje said:**
> And I noticed that the OP didn't have a machine with 4 Gb or more.

Meh. I always see it like this: Why sell your hardware short? Or, to put it another way: I paid a big chunk of money for my 64bit processor, and now it deserves to pay me back.



No offence taken, please accept my apologies for my caustic remarks. As I said, it's a bad day (Christmas visits to the parents, anyone?).




Regards

---

### Post by albinootje on 2009-01-07
> **NEUR0M4NCER said:**
> 
Hooooooo boy, you would get hounded out of the 64bit sub-forum!! It's actually not too complex now. The stickies over in that area are *very* simple, and a lot of the time, aren't even needed now.

Good to hear this. Thanks.
Perhaps I should try it too on my oldish beloved AMD Athlon 64 bit.

I also read that 64 bit is better for emulation and virtualisation ?
> 
No offence taken, please accept my apologies for my caustic remarks. As I said, it's a bad day (Christmas visits to the parents, anyone?).

OK, no problem. :)

I'm actually looking very much forward to springtime.
Quite some people I know are suffering from the cold and the lack of sunshine.

---

### Post by Kingpong on 2009-01-07
I am in the same boat with new hardware arriving this week.

Should I install Ubuntu and Vista on an old 80GB IDE drive and use my new 750GB drive for data only?

Will the sata drive provide a large enough performance jump that I should partition that drive for the OS?

Thanks

---

### Post by Sasquatch2000 on 2009-01-08
> **albinootje said:**
> Ah, you mean Wubi.

But.. please get a normal Ubuntu installation cdrom if you're already creating partitions for Ubuntu.

Wubi is only meant as a "safe" way to play with Ubuntu *located* inside MS-Windows without need for any partitions for Ubuntu.

I recommend you the 32 bit desktop version of Hardy :
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)
Or if you are a little more adventurous Intrepid :
[http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/)


> **NEUR0M4NCER said:**
> [noparse][disclaimer][/noparse]
I'm in the middle of sorting out my own borked system right now, so this advice may not be the best, but...
[noparse][/disclaimer][/noparse]

I would really, *really* recommend just installing Windows onto a 400GB partition, then booting the LiveCD and installing, using all of the defaults, on the remaining 100GB. With any luck, Ubuntu will detect your Windows install and import any settings you may or may not have there, and pretty much sort itself out. When you start to tinker is when things start to go wrong... Trust me, I know.

Regards


And what is wrong with "SAFE"?
When you say booting the live CD and installing, do you mean to use the Ubuntu formatter, or to use Windows formatter before doing this?
What exactly, does it "import" from Windows?
My worries with taking defaults is that it would overwrite my hard work on a new Windows install.

I would most likely download the latest decent "nightly" or "beta" version with niceties and warts all included.








> **NEUR0M4NCER said:**
> *Whoa*...



No, I can't offer 'sources'. I was just trying to help out a fellow user with my (limited) experience.

For the desired outcome, it just seems more appropriate to go the default route, as the OP appears not to have much experience with Linux and all of its quirks. I'm sure you (with your mighty post count) can give much better advice...


Regards



**edit**
But if you're suggesting the more complex route, why on earth would you recommend 32bit when the OP is running AMD64? Arguments and possible sources please.



I wonder if the 32 or 64 makes any difference. 






> **albinootje said:**
> I didn't mean to offend you in any way.
The only reason that I'm asking is because of your "really,really recommend" remark.
That made me curious why you recommended this so persistently.

Many years ago I saw problems when a friend tried a dual Linux/Windows, he claimed that he got problems with his Windows (95) because of the dual boot, but that was around 1999 or so.


Because for a beginner it's not easy to install the 64 bit flash player and Java for example.
And I noticed that the OP didn't have a machine with 4 Gb or more.



Then again, wouldn't it make sense to do this once, in the eventuality I increase to 4Gb or more RAM?








> **NEUR0M4NCER said:**
> Sorry - i'm having a bad day.



Basically, i've re-installed both XP, and Ubuntu (7.04, 7.10, 8.04 and now 8.10) so many times, that I find the simplest, quickest way to do things is to let the installer go about its business. Sure, it might technically be a more roundabout way of doing things, but as a simple user, it saves a lot of time and effort.



It works now. Honestly, it's probably the only thing i've never had to muck about with... unless i've already done something daft (which I have at the moment).



Hooooooo boy, you would get hounded out of the 64bit sub-forum!! It's actually not too complex now. The stickies over in that area are *very* simple, and a lot of the time, aren't even needed now.



Meh. I always see it like this: Why sell your hardware short? Or, to put it another way: I paid a big chunk of money for my 64bit processor, and now it deserves to pay me back.



No offence taken, please accept my apologies for my caustic remarks. As I said, it's a bad day (Christmas visits to the parents, anyone?).




Regards



It sets up the "swap", "home", and "/" partitions automatically? Why 100Gb? Because it is easy to type? I'd prefer more of my drive be available to Windows, especially if Ubuntu can see it anyhow.




Gee, I thought I was all ready to go after yesterday, but am now all confused again.:confused:

---

### Post by Sasquatch2000 on 2009-01-08
.

---

### Post by Sasquatch2000 on 2009-01-08
.

---

### Post by Sasquatch2000 on 2009-01-08
.

---

### Post by Sasquatch2000 on 2009-01-08
Test (having trouble replying)

---

### Post by Sasquatch2000 on 2009-01-08
test (having problems sending to the forum)

---

### Post by Sasquatch2000 on 2009-01-08
checking on the forum, having trouble posting

---

### Post by Sasquatch2000 on 2009-01-09
.

---

### Post by NEUR0M4NCER on 2009-01-09
> **Sasquatch2000 said:**
> checking on the forum, having trouble posting

Rather than give possible bad advice regarding your dual-boot install, allow me to point you to a How-To that I used to use - it pretty much covers every way you might want to do things: Windows first, Ubuntu first, whatever...

[The definitive dual-booting guide: Linux, Vista and XP step-by-step](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

64bit does make a difference, you should see a slight improvement with some apps, and a very marked improvement with others, depending on what you use you PC for. All I would say is it is the same situation as this:
> Then again, wouldn't it make sense to do this once, in the eventuality I increase to 4Gb or more RAM?
Your processor is 64bit. There's no real reason left to *not* use a 64bit OS (Windows is just fine on 32bit to retain compatibility, but most Linux apps have a 64bit version).
> It sets up the "swap", "home", and "/" partitions automatically? Why 100Gb? Because it is easy to type? I'd prefer more of my drive be available to Windows, especially if Ubuntu can see it anyhow.

Gee, I thought I was all ready to go after yesterday, but am now all confused again.
Yes, the Ubuntu installer will set up swap, /home and / automatically. There's no need to look into this too much, it's way more fun to just go ahead and get the OSs installed, then worry about the rest. And it's much easier to get Ubuntu working the way you want from *inside* Ubuntu. At the moment, you're pretty much driving blind.

Follow the How-To and just get the two OSs on there. You'll be surprised how easy it really is.



Regards

---

### Post by Sasquatch2000 on 2009-01-09
Thanks. My biggest fear is installing Windows and setting it all up and then blowing it away with an errant Ubuntu, or not having the right settings and needing to blow either Windows or Ubuntu away to fix something. You know, the old "haste makes waste" thing.

---

### Post by albinootje on 2009-01-09
> **Sasquatch2000 said:**
> My biggest fear is installing Windows and setting it all up and then blowing it away with an errant Ubuntu, or not having the right settings and needing to blow either Windows or Ubuntu away to fix something. You know, the old "haste makes waste" thing.

After installing Windows you can use software like CloneZilla or something like that, to clone your installation.
Putting it back exactly like it was can be a matter of 5 till 10 minutes.

I've used CloneZilla for cloning Linux installations, and booting and using CloneZilla itself was sometimes taking more time than the restoring of the hard disk itself ;-)

[http://clonezilla.sf.net](http://clonezilla.sf.net)

---

### Post by Sasquatch2000 on 2009-01-09
> **albinootje said:**
> After installing Windows you can use software like CloneZilla or something like that, to clone your installation.
Putting it back exactly like it was can be a matter of 5 till 10 minutes.

I've used CloneZilla for cloning Linux installations, and booting and using CloneZilla itself was sometimes taking more time than the restoring of the hard disk itself ;-)

[http://clonezilla.sf.net](http://clonezilla.sf.net)

Does this work to even recreate errant partitions? If so, it sounds better than Acronis, and I want in.

---

### Post by albinootje on 2009-01-09
> **Sasquatch2000 said:**
> Does this work to even recreate errant partitions? If so, it sounds better than Acronis, and I want in.

Not sure what you mean with "errant partitions".

But the 5 - 10 minutes is from a 15 Gb disk where Ubuntu had almost 2 Gb of data in use.
Restoring a 250 Gb disk with more data in use, from a disk image made with CloneZilla will surely need quite some more time.

Furthermore, CloneZilla's interface is a little bit primitive, but that's easy to get used to imho.

---

### Post by Sasquatch2000 on 2009-01-10
> **albinootje said:**
> Not sure what you mean with "errant partitions".

But the 5 - 10 minutes is from a 15 Gb disk where Ubuntu had almost 2 Gb of data in use.
Restoring a 250 Gb disk with more data in use, from a disk image made with CloneZilla will surely need quite some more time.

Furthermore, CloneZilla's interface is a little bit primitive, but that's easy to get used to imho.
What I mean is for when things don't work as expected. This could either be a computer problem or a problem with my expectations or understanding of it. What I mean is can you restore the entire partition, or just its contents.

---

### Post by albinootje on 2009-01-10
> **Sasquatch2000 said:**
> What I mean is for when things don't work as expected. This could either be a computer problem or a problem with my expectations or understanding of it. What I mean is can you restore the entire partition, or just its contents.

Clonezilla will, on your request, either restore the whole disk, or the partition(s) you'd like to restore.

If you have a partition with file system errors, then those will be gone because Clonezilla will overwrite, at your request, either the whole disk (plus bootloader) or the partition(s).

A word of warning, I like CloneZilla's whole disk backup + restore.
The moment you want to restore partitions, on a different disk or when you've been resizing or moving around partitions, or with a disk which has no partitions, then you *have* to create those partitions.
CloneZilla will not do this for you.

If you're gonna be using CloneZilla only for your own machine, then I don't see much of a problem.

---

