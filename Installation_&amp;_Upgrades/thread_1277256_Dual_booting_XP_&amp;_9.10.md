---
title: "Dual booting XP &amp; 9.10"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by Scunnered on 2009-09-28
I am extremely frustrated as I have been totally unable to find suitable Linux software which will run iTunes using the audio book set up.

Consequently I am giving very serious consideration to going totally against my best intentions and loading a copy of Windows XP on to my system.  If I do this it will be once version 9.10 is final as I intend to install it when available.  I have experimented with 9.04 so much and not at all times with too much success that I feel that a totally fresh install will be for the best.

My laptop was purchased as a Ubuntu system and although I was able to load XP onto a Virtualbox I wonder if loading XP as a stand alone OS would cause problems.
  
What I would like to know is the best way forward when dual booting.  As far as XP is concerned other than being forced to register it on line that will be the total extent of any external connection. I propose to use XP only to sync audio books to my iPod 2GB and as such space requirements will be minimal.  

It would be appreciated if you could offer guidance on the best approach to dual booting and if it is possible to have Ubuntu automatically load on start up as XP will only be a side show.  From what I can see ext4 looks to be the best option for 9.10 so unless I am advised to the contrary I would like to use it.  I also wish to keep Ubuntu and XP totally apart and not piggy back Ubuntu on Windows.

Thanking you for your kind assistance in this matter.

---

### Post by mikewhatever on 2009-09-28
I think using XP in virtualbox to run itunes is the easiest solution, no problems expected. I'd also advise to stop buying Apple's hardware, as there are better and cheaper gadgets out there.

---

### Post by Scunnered on 2009-09-28
**mikewhatever**

Thanks for your post.  The only reason I am prepared to load XP on to my system is that I can't get the expletive deleted iTunes to work on VirtualBox. I had bought an iPod years ago to let me listen to audio books as I had cateracts.  As I had the iPod I saw no good reason for it to sit in a box doing nothing therefore the attempt to have it work properly.

No Linux software will do what is needed and so far nor will Virtualbox.  Am hoping from another post where someone advised that they had it working that assistance might be given.

Meanwhile I am preparing for the worst.

Thanks again

---

### Post by Bartender on 2009-09-28
I'm using a Sansa Fuze for audiobooks.  It's working out pretty well.  I realize that doesn't help you out with your situation, just thought I'd pass that on.
The iPods are awful expensive for what you get.  Maybe you could sell the iPod and that would almost be enough to buy a Fuze?  I bought a 2GB Fuze on Amazon for about $45.  A few days later Amazon emailed me an ad.  $12 for an 8GB micro-SD card.  So it's now a Fuze with 10GB storage for quite a bit less money than if I'd bought an 8GB Fuze.

---

### Post by Scunnered on 2009-09-28
**Bartender**

Many thanks for your post.  Keeping up the image of miserable Scot I am determined not to add to hoard of useless IT equipment.  As I have the iPod and paid dearly for it at the time of purchase am determined to get my moneys worth.

If the worst comes to the worst and I am forced to consider a dual boot then I will do so reluctantly.

I see that you dual boot and would ask for your guidance in the matter.  Will I be able to achieve my aim easily?  Other than using XP for the iPod I intend Ubuntu to be the OS of choice.

Thanking you in anticipation

---

### Post by jward3010 on 2009-09-28
In terms of support for iPods, the likes of Rhythmbox can only read and play the files on Apple devices which is a pity - but at the same time a testament to the frustration that people feel when they use highly proprietary devices.

Anyway, a dual boot of XP and Ubuntu is easy enough to acheive and not a bad idea at all. What size disk do you have?

---

### Post by intrader on 2009-09-28
> **Scunnered said:**
> **Bartender**

Many thanks for your post.  Keeping up the image of miserable Scot I am determined not to add to hoard of useless IT equipment.  As I have the iPod and paid dearly for it at the time of purchase am determined to get my moneys worth.

If the worst comes to the worst and I am forced to consider a dual boot then I will do so reluctantly.

I see that you dual boot and would ask for your guidance in the matter.  Will I be able to achieve my aim easily?  Other than using XP for the iPod I intend Ubuntu to be the OS of choice.

Thanking you in anticipation
Maybe try converting mp4 to mp3. There are converters available. I have found the AVS Audio Converter useful. However, there are also other available.

---

### Post by wilee-nilee on 2009-09-28
The dual boot is fairly straight forward, except that it will take over the master boot. leaving your 9.10 still there but needing to have grub take over again with the xp included. There are links on how to do this all over the Forums just ask for help.

Now if you don't mind reinstalling both OS's start with xp write it to the size needed if this is allowed with the installation, if it needs to write to the whole HD you can shrink it with a ubuntu live CD partition manager. The 9.10 install will then ask you if you want to write side by side to the empty space, but there is a slider at the bottom of the GUI that allows you to set the OS size's. Personally on dual boots I use that slider to write it exactly to the open free space so it basically doesn't disturb windows. I have found Xp to not be as easy going with messing around then Linux generally is. Also make sure you defrag the xp after you install and after resizing the xp OS if needed before installing 9.10, Good Luck. ;)

---

### Post by cariboo on 2009-09-28
Before you waste time installing xp again, what version of virtualbox are you using? The version in the repositories doesn't support usb. This [version]("http:///www.virtualbox.org/wiki/Linux_Downloads") supports usb with the guest additions, available in the Devices menu. I am able to program my Logitech Harmony remote using xp in a vm as there is no way to do it running Linux.

---

### Post by Scunnered on 2009-09-29
**cariboo907**

I have Virtualbox 3.0.6r52128 loaded but my iTunes problem is that it will not load any CD. I have never had XP on this laptop and I had hoped that I never would. However as loading XP seems to be the only option to get things to work properly I will have to load it.

**Wilee-nilee**

What I am proposing to do is to once I have a 9.10 CD and having checked it out in a live situation is to remove 9.04 from the system.  I then intended to load 9.10 and XP.  As my system was bought as a Linux one I wondered if this would be a problem with XP (as if there were not enough of them).

From what you say I should start with XP and then follow on with 9.10.  That looks reasonable enough. What worried me was that I saw somewhere that Ubuntu could be loaded on to Windows and it is this that I want to avoid at all costs.  

I also note your remark about grub and Windows wanting to take over and it is this that worries me the most.  I only want XP to run iTunes and nothing else so what I would prefer is that it sit in the background.  When I boot up the laptop I would much prefer to have 9.10 start automatically and it was guidance on how this could be achieved that I was seeking.  

Is defraging required if I allocate say 10% of my HD to XP?  

I am feeling my way with this as I dont want to have everything clash and cause  major problems. 
I would rather look foolish now that have to start screaming that nothing works at all.

===

My thanks to everyone for their comments.  My problem is that as I want to listen to audio books and iTunes offer the best possible option I am forced to stick with Apple. Until such time as someone will offer something close or better than iTunes then I will have to live with things as they currently are.

---

### Post by coller_girl on 2009-09-29
I Used Sound Converter to convert my OGG files to MP3 as i had the same kind of issue -my Girlfriend had a few million OGG files i was allowed to have... i needed them as MP3 it took a few months to convert them all... for less i'm sure that it will take less time...

if you have many then its going to take a while but there are other solutions depending on how you want to use the audio books, 

[http://tuxmobil.org/ebook.html](http://tuxmobil.org/ebook.html) this has lots of pages that give a good base for where to replace your books from. or convert to different formats for devices.


:cool:

---

### Post by wilee-nilee on 2009-09-29
I would check 1st to see if your computer will run xp, you might start with just posting what your computer is, if it is a standard model then the hardware info should be available. I don't know the command line to find this out. 

If you install both OS's separately they will be in different partitions, which allows you to see windows from Ubuntu, but not Ubuntu from windows. Now being that the default extension for 9.10 is ext4 things maybe different in being able to see and mount the windows partition if you wanted to transfer something or delete something in the windows side unfettered.

If you install xp first then 9.10 Linux grub should be controlling the boot. 

Installing Ubuntu inside of Windows is done with wubi and generally is used for people wanting to try out Ubuntu, a dual boot which is what we are talking about is generally considered the best way to set up your computer beyond a virtual setup.

I am a new windows user and I saw some advice about defraging when you resize the windows partition before the dual install, another person on the forums suggested a pre-defrag but this is a new install. Personally I think the defrag is a good Idea in that I am finding that my net-book xp is rather temperamental, so I say better safe then sorry. 

As far as windows running in the background the only way I know to do this is a virtual set up, so whether you install 9.10 in XP with wubi or dual-boot they run separately. The only thing I have seen about a wubi setup is that if Ubuntu picks up a virus----etc it may not effect Ubuntu but can be passed to the windows portion they are in the same partition and Ubuntu is running in a Pseudo virtual environment.

Last of all hopefully others will chime in on this so that you feel more comfortable in this endeavor. The dual boot is fairly straight forward, and if anything goes wrong you can use a Ubuntu Live CD to delete the partitions or adjust them. You might consider downloading Gparted to a separate disc or have a copy of a Jaunty live CD so if you need the partition manager you have one. 

Worse case scenario since you have a computer that runs linux you can always just install that in the end if the XP install doesn't work, but it probably will go okay.

---

### Post by Bartender on 2009-09-29
Scunnered -
I'm a little confused.  Do you want to do virtualization, or do you want to do a standard dual-boot?
A lot of folks have gone with virtualization.  I've never tried it. 

If you have a fairly powerful machine with lots of RAM and processing cycles, it appears virtual can be a great way to go.  If not, my 2 cents would be stick with a standard dual-boot.

If you're willing to start from scratch, that would be great.  Download a copy of the latest stable GParted LiveCD .iso from sourceforge (link below my sig) and create a bootable disc from the download.  This is the same process as burning an Ubuntu install disc.  You have to turn the .iso into a bootable CD, not just copy the data.  When you're done you have a stand-alone partitioner that works better than the one that's available from the Ubuntu LiveCD desktop, although it looks the same.

Boot up from GParted LiveCD (GPLCD).  Remove all partitions.  Pick the amount of space you want for XP.  Let's say 25GB for argument's sake.  Using the GPLCD, create a primary partition at the "front" (left) of the disc.  Format it as NTFS.  Apply the changes.  It's important to apply each change as you go or GPLCD will stack up tasks and try to do them all at once.
Create an extended partition out of the rest of the space.  Apply the change.  Windows has to boot from a primary partition.  Linux does not.  IMO there's no good reason not to make the rest of the drive extended.

At this point I'd suggest continuing with the GPLCD, but if you go this way you'll have to use the "manual partitioning" option when you get to the Ubuntu LiveCD.  Manual isn't hard, and you can watch a few YouTube videos to get the idea.

If you continue with GPLCD, you need to fill the extended partition with logical partitions.  You'll want to stop and think about how much space you want to give to each of the following components.  The minimum would be:

#1: an Ubuntu / partition, 
#2: swap partition,
#3: a shared data partition, which used to be FAT but I don't think there's any reason not to make it NTFS anymore

I'd suggest a /home partition too, but that's up to you. 

With the GPLCD, you're just building the partitions and installing a file system, not filling them with data.  So I'll say "create a partition for /" but what I mean is you're creating a partition now that the Ubuntu installer will use as / later.  Understand?

Create a logical partition for /, formatted as ext3 or ext4.  I've been using ext4 but I see many people are sticking with ext3.  I doubt a person would ever need more than 15GB for / if you make a separate /home partition.

Create a logical partition for swap, formatted as swap.  As long as you have 2GB or more of RAM, I think the general rule of thumb is make swap a little bit bigger than your RAM if you want to suspend.

Create a logical ext3 or ext4 partition for /home.  I can't tell you how big to make /home.  Depends on how much room you have left, and how much data you think will be shared between Ubuntu and XP.  XP will not be able to access home because it'll be ext.

Create a logical NTFS partition for data that XP and Ubuntu can both access.  This would be for your iPod stuff.  Make sure to format it as NTFS. 

Apply all these changes, make note of the names that were given to the partitions (sda6, sda7, etc.) get out of GPLCD, pop in the XP disc, restart the PC.  The XP disc will only recognize that primary NTFS partition and will ignore the rest of the HDD.  This avoids all the hassles of installing XP to the entire disc, then trying to squish it back into its corner.

When you install Ubuntu, go to the manually partition option at step 5.  Mount swap and / and /home to the appropriate partitions, the ones you set up earlier.  Don't let the installer try to format anything else, just those three.  Let GRUB install in the default method.

Once it's all up and running, Ubuntu will be the default OS.  It'll only boot to Windows if you choose Windows.  That's how you want it, right?

Here's a [post]("http://ubuntuforums.org/showthread.php?t=1249374") showing some pictures of dual-boots and single-boots.  Notice how I made 25GB / partitions.  Those were a little too big.  I'll probably never get close to filling them.  Screenshots at the bottom.

---

### Post by Scunnered on 2009-09-29
**coller_girl**

Thanks for your reply.  What I have been doing up till now is to borrow audio books from my library and download them in iTunes.  Having done that I then sync them to the iPod. There is a specific set up for audio books and it is this function that I hope some day will be provided as Linux software.

**wilee-nilee**

Once again thanks for your advice.  From  what you say I will go down the road of loading XP followed by 9.10.  If I have to choose from a menu at start up then I will just have to live with that.

As I am only loading XP because I am forced to I will not bother about a defrag unless it is essential. I have Jaunty on a CD so if the worst comes to the worst I sould be adequately covered.

I will now impatiently wait until the end of next month and see how things go.

Again my thanks to everyone for their assistance

---

### Post by Scunnered on 2009-09-29
**Bartender**

Your post has crossed with my composing the reply to coller-girl & wilee-nilee.

You have given me a lot to work with and with it reassurance that I can keep Ubuntu in the ascendancy and have XP for what little I need it for.  

From what has been provided I feel confident that I will be able to use my iPod properly yet still have Ubuntu as my working OS.

Again my sincere thanks for your guidance.

---

### Post by Bartender on 2009-09-29
> **Scunnered said:**
> As I am only loading XP because I am forced to I will not bother about a defrag unless it is essential.

See, that's the thing.  XP will install to the entire disk, and it often leaves little bits of data way out there in the second half of the disk space that don't want to move.

That's why I suggest partitioning with a GPLCD first and setting up a primary NTFS partition for XP.  That way you control XP, rather than XP controlling you.

EDIT:  Now I'm cross-posting with you!  Yeah, I know I threw a lot of info at you, but that's how I do it and none of what I described is very technical.  Just a matter of doing it once or twice and taking some notes if your memory is as crappy as mine.  It seems confusing the first time or two, but if you're starting out from scratch it's all good.  The worst that might happen is you have to start over again.  Do you have access to another PC so you can post a question if you get stuck mid-stream?

I'm doing the same thing with library audiobooks as you.  Basically the same thing.  I'm using a Sansa Fuze, RubyRipper in Ubuntu to rip the CD's, then storing the audiobooks on an external 1TB Seagate plugged into a Vantec NexStar dock.  The Seagate is formatted as NTFS.  I didn't want to format it as NTFS, but needed to access the drive from Windows and Linux.  My wife owns the Fuze.  She's listening to the second book from Stephen King's "Dark Tower" series right now.

---

### Post by Scunnered on 2009-09-29
**Bartender**

We will have to stop cross posting like this, people are begining to talk.

I am still digesting all the information provided but from the initial read through I propose to follow your suggestion of firstly partitioning the HD. If I give XP 15 GB that should be more than enough to play with as I will only be loading up to 1.8GB to the iPod. 

Looking at my current set up I have /dev/sda1 an ext3, sda2 an extended and sda5 a Linux swap partition. Both the extended and swap are 2.84 GiB. 

Am I required when partitioning having allocated 15GB NTFS for XP to then allocate an ext4, extended and Linux swap or will this be done automatically when loading 9.10 into the remaining space on the HD?

Mostly things look straight forward and as I have plenty of time between now and 9.10 going live I can take a close look and prepare for myself an idiots guide. I may even resurect an old desktop and fiddle with it in preparation.

Could you please clarify if I need a shared partition. I see my way of working as first and foremost Ubuntu. When I need audio books loaded I would boot into XP directly as I wish to keep Windows and Ubuntu completely apart. XP would be totally limited to audio books and nothing else and for this reason I dont feel the need of a shared partition. Am I right in my thinking on this?

I really appreciate you taking the time to walk me through this. There are times that I find the forum offers up a better instruction than the Begining Ubuntu book.

Once again my thanks

---

### Post by Bartender on 2009-09-30
*Looking at my current set up I have /dev/sda1 an ext3, sda2 an extended and sda5 a Linux swap partition. Both the extended and swap are 2.84 GiB.*

OK, you must have let Ubuntu install automatically.  The Ubiquity installer changes with every release - in this latest release they decided to set the installer default so that it installs to an absolute minimum size.  The user is supposed to understand that he/she needs to drag the slider so that the installer will carve out a larger portion for Ubuntu.  Don't feel bad - lots of people missed it.  

*Am I required when partitioning having allocated 15GB NTFS for XP to then allocate an ext4, extended and Linux swap or will this be done automatically when loading 9.10 into the remaining space on the HD?*

The simplest answer is "depends".  Let's stick with what I described in the earlier post:  you're going to set things up first with a bootable GParted LiveCD.  Let me think here - 
the simplest thing to do would be to create the primary NTFS partition for Windows first, then create an extended partition out of all the rest of the drive.  Apply your changes, and get out of GPLCD.  Boot into the Windows CD, install Windows, make sure it's working.  Then you boot into your Ubuntu install CD and let it install automagically (I believe this is the "Guided" option?) to the extended partition.  Ubuntu would handle the file systems and formatting.

*I may even resurect an old desktop and fiddle with it in preparation.*

That's an _outstanding_ idea.  Use the test box to get comfortable with GPLCD, set up partitions, then install Ubuntu and see how it comes out.  GPLCD is not hard.  It's only confusing the first couple of times because you're not familiar with it.  Once you get the idea, it's very simple to mount / and swap and /home if you choose.

*XP would be totally limited to audio books and nothing else and for this reason I dont feel the need of a shared partition. Am I right in my thinking on this? *

Yeah, I think you are right.  I got off onto a tangent, thinking you wanted to be able to share data.  
- Use GPLCD to (1) build a primary NTFS partition for Windows, and (2) an extended partition out of the rest of the drive.  The extended partition is just a "box" for logical partitions.
- Install Windows.  It should only see the primary NTFS partition.  Make sure it's working.
- Install Ubuntu and if you don't care about a separate /home partition or a data partition just make sure it auto-installs to the extended partition.  Make note of the little slider - we don't want it to install to 2.3GB again!

Feel free to PM me if you have specific questions that you feel would not benefit others.

---

### Post by robbieo11 on 2009-09-30
how out flash the ipod to work with linux

---

### Post by vonlexden on 2009-09-30
I am completely confused. I have been successfully rununning UBuntu using the WIBU one click download. Today I added 2 gigs of RAM to my system and Ubuntu would not boot up - no matter aht i tried. I reinstalled Ubuntu with WIBU, it installed OK. When I get the boot choice between Ubuntu and Windoes I select Ubuntu - only to be met with a blank screen except for the cursor sitting blinking in the screen to left.
 
Can anyone help?

---

### Post by Bartender on 2009-09-30
von -
You need to start a new thread with a good descriptive title.  Posting your question to an unrelated thread is not likely to get you any good answers and it takes away from the OP's quest for direction.

---

### Post by Scunnered on 2009-10-09
**Bartender**

As I indicated earlier I dug out an old system and tried your suggestion.

Using Gparted Live worked a treat.  I previously had an old version of Ubuntu and using Gparted split the HD into 2.  I gave the Windows 20GB and left the rest as unallocated.  I loaded XP and then followed on with Jaunty loading it on a side by side basis.

When I booted up XP initially it advised that One of your disks needed to be checked but letting disk check work the following re-boot did not display the disk checker again. 

I am pleased to report that I feel confident that once 9.10 has settled down that I might just dual boot XP to solve my problem.

Again my sincere thanks for your kind assistance.

---

### Post by Bartender on 2009-10-09
I'm very glad to hear it's working out so far.  

There's great value in practicing on an old test PC.  Unfamiliarity and fear are a deadly combination when someone new to Linux is performing brain surgery on their main PC.  If you make a mistake with an old test box, it's a learning experience.  Make a mistake with your main PC and you could be scarred for life.  

I've read some horror stories on this forum:  "XP disappeared after I installed Ubuntu, and my wife had all the baby pictures on that computer!"

I'd suggest wiping the drive clean and doing it again.  Great confidence builder.

---

