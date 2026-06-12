---
title: "[SOLVED] Linux or Windows (?)"
date: 2008-08-09
forum: General Help
---

### Post by Thora3967 on 2008-08-09
Greets all

     I just finished assembling my new computer and am contemplating throwing away my windows disks away and using one of the linux builds (Ubuntu, Mandriva, etc - whatever).

   Before I take that step, I need to confirm a couple points:

1. One of the programs I use is 3d studio max, which "only" runs on windows platforms w/ hardware-accelerated OpenGL & Direct3D.  So I need to run windows "inside" linux (through vmware etc) or is there another option?

2. The same question as above also applies to online/offline gaming.

3. Do the linux builds have an equivalent to openGL & direct3D, or is there a completely (to my limited knowledge) hidden software industry solely geared to linux?

4. I've been told that only using the GUI in the linux builds instead of the command-line essentially "robs" the user of a majority of the computer's capabilities etc.  Is this true?  I've no inclination to learn another language at the moment but I want an alternative to using Vista.  I currently use XP Pro but if I keep on using it eventually I'll have to use vista, which I will not use.

So, fill me in guys, gimme the straight scoop :)

Just in case, here is parts list for my computer:

Motherboard: ASUS Maximus II Formula - Intel P45 Chipset
CPU:         Intel Core 2 Quad q6600 2.4 Ghz 
RAM:         Connair 4 Gig DDR2
HDD:         1 Seagate 500 Gig SATA
             2 Western Digital 80 Gig SATA
Video:       ATI Sapphire HD 3850 w/ 512 M
Audio:       Creative Labs Sound FX X-FI
Monitor:     Samsung 245G 22" Flatscreen
Printer:     Samsung ML-2510
             Brother MFC-465CN
Optical:     2 LG DVD Combo drives
Input:       Logitech wireless keyboard & mouse

---

### Post by dominiquec on 2008-08-09
For the situation you describe, dual-boot between Windows and Linux might be better for you.  This is particularly true of your requirement for 3D Studio Max and games.

Another alternative: you could use VirtualBox or VMWare to run a virtual operating system.  For your purposes, you could use a Windows host and a Linux guest, not vice versa.  This is because you want to take full advantage of your graphics capabilities for the Windows apps you mention.

OpenGL is supported under Linux.

As to point 4, I wouldn't exactly say GUI "robs" anything from the experience.  It's just that there are certain things you can do faster and more efficiently with the command line.  It's also a good skill to learn.

---

### Post by huxterby on 2008-08-09
I second the dual-boot option as well. In my office a few of the guys use Studio Max and Photoshop but use Linux for everything else. We tried installing Photoshop with Wine Doors but it kept throwing up problems with the plugins, Studio Max was a no go from the start.

Remember that as of yet, there is no 3D acceleration in Virtual Environments, so running Windows in a VM is not an option, nor vice versa with Linux on a Windows VMachine.

With the large harddrives that are available nowadays, having 2 OS's running side by side isn't a hindrance either.

Just remember to install Windows first and then Linux.

Huxterby

---

### Post by Elfy on 2008-08-09
Hi - I would agree with both suggestions of a dual boot.

I would also swap the drives - so the 80Gb is the first drive and install both os to that and leave the 500Gb for data storage.

I would set the 80Gb to have the majoprity as space for the win install and keep 20Gb for the linux install, you can then access the 500Gb drive for data storage through both.

and welcome to the forum.

---

### Post by Thora3967 on 2008-08-09
Thanks for the replies, and the welcome :)

Those have all been informative recommendations which was exactly what I needed.

This does bring out a second round of questions tho:

1. I've browsed across several websites "comparing" the various Linux variants and have not found anything to suggest that there is any large advantage to any one build over the rest. A majority of them use the same GUI (KDE), they all use approximately the same kernel (2.6.xx.xx) and C compiler (4.x.x).  They all have variants for the x86 architectures and most support x86-64 (I think I would need to get an x86-64 version, to take advantage of both 32 and 64 bit architectures.  So how do I select the build that's "right" for me?  Is there such a creature? Or do I need to go with trial & error?

2. I'm curious as to the sizing of the partitions you are recommending.  I'm almost certain 60g would leave sufficient room to grow for the registry file in windows; which makes me rather skeptical that 20g is sufficient for linux, which would be holding considerably more installed programs.  I knew linux was more efficient (and intelligent) in its use of space but 3x better seems a bit much.

3. How much (speed & efficiency) would my system suffer if I went with the following make-up:

C: drive(0) - 80 Gig SATA - 1 full-size partition - Windows & Compatible Software Installs

D: drive(1) - 80 Gig SATA - 1 full-size partition - Linux & Compatible Software Installs

E: drive(2) - 500 Gig SATA - 1 full-size partition - User Data

Thanks again in advance :)

---

### Post by dominiquec on 2008-08-09
> So how do I select the build that's "right" for me? Is there such a creature? Or do I need to go with trial & error?

I'd say go with the distribution that you know that your friends are using.  Friends are usually your first level of support, especially if you're new to Linux.

Other than that, it's really up to you.  I'd suggest you try the more popular ones and see which suits you.  Ubuntu (of course), or Fedora, or SuSE.

As for me, I've been with Ubuntu for the past three years.  I've customized it to the way I want to work with it.

> I'm almost certain 60g would leave sufficient room to grow for the registry file in windows; which makes me rather skeptical that 20g is sufficient for linux, which would be holding considerably more installed programs. I knew linux was more efficient (and intelligent) in its use of space but 3x better seems a bit much.

You're in for a surprise.  The root (system files etc.) partitions for my Ubuntu installations rarely go beyond 7GB.  On this laptop I'm using, since I've stripped everything down, it's only 2GB.

To be safe, I'd recommend at least 10GB.

You'll want to keep your /home directory separate.  This is where most of your user files will be.

---

### Post by Elfy on 2008-08-09
> You'll want to keep your /home directory separate. This is where most of your user files will be.Though it's not necessary to have any more than your config and hodden files in there; with 500Gb available for storage I would use that for the majority of my data which should in turn reduce the size of any /home considerably.

I misunderstood your hdds - I thought you were numbering them :)

1 Seagate 500 Gig SATA
2 Western Digital 80 Gig SATA

if you actually have 2 80Gb and 1 500Gb

Go with your plan - let windows do it's stuff on the 1st drive, use thepartition editor on the livecd to deal with the 2nd drive - make 3 partition on it

1 - ext3 10Gb
2 - swap - as much as you decide, unless you need hibernate or are likely to be doing memory intensive work then 500Mb would be sufficient I think
3 - ext3 - whatever is left

Partition the 500Gb as ntfs, although you could use ext3 and get the driver to read them from windows.

When you install ubuntu - you can use the manual method and sepcifiy partitions then.

---

### Post by mikjp on 2008-08-09
> **dominiquec said:**
> 
Other than that, it's really up to you.  I'd suggest you try the more popular ones and see which suits you.  Ubuntu (of course), or Fedora, or SuSE.

Install Ubuntu or openSUSE. Fedora might be a bit rough on the edges. 

But if you are purist with questions regarding freedom of software and media formats, install Fedora.

mikko

---

### Post by Thora3967 on 2008-08-09
> **forestpixie said:**
> Go with your plan - let windows do it's stuff on the 1st drive, use thepartition editor on the livecd to deal with the 2nd drive - make 3 partition on it

1 - ext3 10Gb
2 - swap - as much as you decide, unless you need hibernate or are likely to be doing memory intensive work then 500Mb would be sufficient I think
3 - ext3 - whatever is left

Partition the 500Gb as ntfs, although you could use ext3 and get the driver to read them from windows.

Clarification plz.

80 Gig disk 0
 - Windows - ntfs - full-size partition
80 Gig disk 1
 - Ubuntu - 10 Gig ext3 - swap (? gig) - ext3 (? Gig)
500 Gig disk 2
 - Data - does linux read NTFS file format? or shall I make 2 partitions her.. half for windows ntfs & half for linux etx3?

---

### Post by Elfy on 2008-08-09
ubuntu will read as default a little work to write, if you are likely to want to share. If you are sure you wont share between then split the drive.

> 80 Gig disk 1
- Ubuntu - 10 Gig ext3 - swap (? gig) - ext3 (? Gig)Before you can tell how much to have for your home ( the bigger amount) you need to decide on swap.

Swap will depend on whether you need to hibernate in which case swap=RAM , if not then a small amount would probably suffice, although as you have 64bit it will at least all be recognised. Maybe, as long as you wont be hibernating,  just make it 512MB - you can resize later easily.

Whatever is left on the hdd drive after allocating the first 10Gb of ext3 and the swap, which should be formatted as linux swap, can be formatted to ext3 as well.

Edit - as an example with 1Gb swap

10Gb - ext3
1Gb - linux-swap
69Gb - ext3

---

### Post by RB2610 on 2008-08-09
As for games, check out [WineAppDB]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true") Basically, if it is rated Platinum, Gold or Silver, it should work mostly fine, Platinum being the same as running on Windows, G/S will either require a little fiddling to get to work or some features may not work or occasionally there may be some glitches (in Oblivion you can end up with pink water and having the screen invert for a moment occasionally when outdoors for a long time :S )
Bronze is unplayable and garbage won't work at all.
For specific info on what does/doesn't work in a particular game just check out the games entry in the AppDB, some games like Oblivion have more detailed help on their forums and wikis.

From personal experience I can tell you that Trackmania Nations Forever from the Steam client works fine but requires some tweaking and runs a little worse than in Windows. (Therefore Steam also works)
Oblivion works including mods, it needs quite a bit of fiddling to get the right balance between best graphics and bugged or glitched gameplay, I got most settings to high, except HDR/Bloom and some of the water effects which caused crashes when you got in the water. On Windows however for me it played really badly for some reason, crashing every 10 minutes, so the inferior graphics in Ubuntu were acceptable, at least it seldom crashes :) )
Halo Combat Evolved works, originally a no-cd crack was needed, but Microsoft released a patch yesterday for some reason that removes the CD check :? (strange of the evil Microsoft to remove all security for one of their best selling games :confused: )
Finally Dawn of War, Dark Crusade and Soulstorm, the first 2 work perfectly, as long as you start the install properly (otherwise disk switching during installation doesn't work) After that everything is just like in Windows :)
Soulstorm however has one complication, there is no patch that removes the disk security check and due to a problem in the software it doesn't recognise your disk as a legitimate one so you will need a No-CD crack which can be found on it's entry in the Wine AppDB.
I just remembered that in Halo and DoW the patches caused a couple of problems to install, it might have been me being stupid though, but again any problems are likely to be mentioned with solutions in the AppDB.

Good luck with gaming in Ubuntu :)

---

### Post by mb_webguy on 2008-08-09
Just for another perspective...  I have a dual-boot system, with Ubuntu as my primary OS and Windows for those few necessary Windows applications that won't run under Wine.

I have two hard drives, partitioned like this:
[LIST]
[*]hd0 (160GB)
[LIST]
[*](hd0,0)  30GB NTFS partition for Windows
[*]   (hd0,1)  20GB ext3 partition for Linux root
[*]   (hd0,2)  2GB swap partition for Linux
[*]   (hd0,3)  20GB ext3 partition of Linux /home
[*]   (hd0,4)  90GB NTFS partition for shared data
[/LIST][*]hd1 (160GB)
 [LIST]
[*](hd1,0)  160GB NTFS partition for shared data
[/LIST][/LIST]
Since I'm dual-booting with Vista, I'm using most of the 30GB Windows partition.  On the other hand, even though Ubuntu is my primary OS and I have quite a bit of software installed, I'm using about 5GB of the 20GB Linux root partition.  

While I have a 20GB home partition for Linux, most of my data is located on the 160GB NTFS partition which is my user folder under Windows.  I have symlinks in my Ubuntu user directory to that 160GB NTFS partition.  In fact, I've been thinking about reinstalling everything and changing my partition scheme slightly, since I'm only using a fraction of my 20GB /home partition, since the only thing in it is configuration files and symlinks to other partitions.  I'm also thinking of cutting my 20GB Linux root partition in half, since I'm only using a quarter of it.

Soooo...  For your setup, I'd recommend the following partitioning schemes for one of the 80GB drives:
[LIST]
[*]A 25GB or 30GB NTFS partition for Windows, depending on whether you're installing XP or Vista, and how much software you're planning on installing.  
[*]A 10GB or 15GB ext3 partition for the Linux root partition.  15GB is a bit of overkill, but it will give you all the room to install software you'd ever want, and more.
[*]A swap partition roughly equal to the amount of memory on your system.
[*]A small (1GB to 5GB) ext3 partition for your Linux /home directory.
[*]An NTFS or ext3 partition taking up the rest of the drive, accessible by both Windows and Linux.
[/LIST]
The other drives should also be formatted as either NTFS or ext3 and shared between Windows and Linux.  I'd set the large drive as my user folder in Windows, and put symlinks in your Linux user directory to that drive.  

I disagree (respectfully) with forestpixie that you should devote the entirety of one of your smaller drives for Windows, since either you would expose your Windows installation to Linux (which is a bad idea) or else not be able to access data on that drive from Linux (which isn't ideal).  It's a much better idea to separate your OSes but consolidate your data.

---

### Post by SuperSonic4 on 2008-08-09
Well I have linux mint on one of my 500gb HDD (excessive I know)
Windows is on a 640gb hdd (also excessive)
Storage is on a second 500gb hdd which is NTFS so windows and linux can read it. I formatted it before getting ext3 recognised in windows though

---

### Post by Elfy on 2008-08-09
tbh - there as many ways of skinning this cat as you could possibly want, (I'd even be inclined to not completely partition drives and leave room for future possibilities) - the only thing I would be at all worried about is accessing linux data through windows as the driver doesn't deal with permissions properly apparently.

---

### Post by bpowell2005 on 2008-08-09
> **Thora3967 said:**
> Thanks for the replies, and the welcome :)



1. I've browsed across several websites "comparing" the various Linux variants and have not found anything to suggest that there is any large advantage to any one build over the rest. A majority of them use the same GUI (KDE), they all use approximately the same kernel (2.6.xx.xx) and C compiler (4.x.x).  They all have variants for the x86 architectures and most support x86-64 (I think I would need to get an x86-64 version, to take advantage of both 32 and 64 bit architectures.  So how do I select the build that's "right" for me?  Is there such a creature? Or do I need to go with trial & error?

Thanks again in advance :)


For my money, Ubuntu has been the most stable, and most "plug and play" distribution I've used so far. I was running PCLINUXOS for quite a while, but I had frequently wireless failures, lockups, and could not hibernate or suspend to RAM...I finally dorked the PCLOS installation trying to install an unsupported Kernel...I loaded Ubuntu, and have loved it ever since. I've also installed it for family members, and they're happy!

---

### Post by knutschr on 2008-08-09
I have installed both Ubuntu and Kubuntu (KDE 4.x) in my /root partition and have installed a lot.This now uses 16 GB, so I think you should use 20 MG for that partition.

For windows games, I have Cedega which is payware.

---

### Post by RB2610 on 2008-08-09
> **knutschr said:**
> I have installed both Ubuntu and Kubuntu (KDE 4.x) in my /root partition and have installed a lot.This now uses 16 GB, so I think you should use 20 MG for that partition.

For windows games, I have Cedega which is payware.

How much larger is Cedega's library of working games? I was considering it earlier but if it's just for the sake of 1 or 2 games I won't bother.

---

### Post by knutschr on 2008-08-09
Look at the homepages of Wine and Cedega, and you will know.
Another thing is that Cedega is making it possible to have games running in small windows while you do other things asw.

Do you have ktorrent installed ;-)

---

### Post by vjkeito on 2008-08-09
have you tried using *Blender* instead of *3DS Max*?

I used to use 3DS Max too but have switched to Blender now.  It has a steep learning curve but is well worth the effort.  I wish I had been taught this at university (multimedia tech) instead!

[**Elephants Dream**]("http://orange.blender.org/") & [**Big Buck Bunny**]("http://www.bigbuckbunny.org/") were both "open source" movies modeled/animated/rendered with Blender.

Dual Booting is a good idea if you require the use of 3DS Max as virtualisation is a waste of resources when you need the extra grunt for 3D work.

---

