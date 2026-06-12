---
title: "Need advice on shrinking Vista"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by pooja on 2009-06-23
Hi everyone,
I'm totally intrigued by Ubuntu and can't wait to try it on my HP laptop.
My laptop has only 1 hard drive of about 150 GB. It has an HP Recovery partition (D:/ ) of approx. 5GB and another partition ( C:/ ) of 144 GB, entirely occupied by Vista. When I go to shrink C:/ it tells me:

Total size in MB, before shrinking: 147330
Available shrinking space, in MB: 31203
**Specify reduction size, in MB: 31203**
Total size in MB, after shrinking: 116127

1) What should I do? Reduce Vista by approx. 31 GB, i.e. all the available space? I know Ubuntu needs 10GB to work properly so in the end I will be using only 20GB. Is that enough to do some programming, surf the net, multimedia tweaking (customize the desktop, experiment with Gimp etc.)?

2) Suppose later on I decide to furthermore shrink Vista to make some more room for Ubuntu, can it be done?

3) I found a [[COLOR="Red"]guide[/COLOR]]("https://help.ubuntu.com/community/WindowsDualBoot") in the forum and clicked on the 3rd link at the bottom of that page - it's a [[COLOR="Red"]link[/COLOR]]("http://neosmart.net/wiki/display/EBCD/Ubuntu") to another guide on dual booting Vista and Ubuntu with EasyBCD. Is it still valid or there's some new step-by-step tutorial around?

---

### Post by madverb on 2009-06-23
20GB is tonnes.
You shouldn't need more space. Just access to your Windows partition from within Ubuntu.

---

### Post by Mark Phelps on 2009-06-23
You're taking the right approach by shrinking Vista OS partition using Vista's own Disk Management tool.  The link below provides to tips for when you can't get it to shrink as much as you want:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

As to the size, 30GB should be more than enough for Ubuntu.  It's not nearly the resource hog that Vista is.  I've been running different versions of Ubuntu on several dual-boot machines for years and am hard pressed to use up more than 5GB of space.

---

### Post by pooja on 2009-06-23
Ok, thank you for replying.
So I should take up all the space Vista is able to give me (~31GB), right?
And what about this [[COLOR="Red"]guide[/COLOR]]("http://neosmart.net/wiki/display/EBCD/Linux"), is it up to date? If I follow it may I incur into some bugs?

---

### Post by Mark Phelps on 2009-06-23
An alternative would be to only use 10GB or so for Ubuntu, and setup a shared NTFS partition for data in the remaining 20GB.  Ubuntu, using the ntfs-3g package, can readily read and write NTFS partitions without problems.

As to EasyBCD, the best source of advice is their forums.  Check the NeoSmart website. They deal with this stuff all the time and have How-to's you can download with specific directions/

---

### Post by irv on 2009-06-23
Before installing Ubuntu, I would did some house cleaning in Vista. I un-installed all the programs I wasn't using in Vista, and move old data files to a USB drive then ran the Disc utility in Vista and shrunk the partition size and left a nice size piece for the install before I installed Ubuntu. Here is what I ended up with.
My drive is 219.2Gb, I have 148.3 for Vista, and 70.9 for Ubuntu.
I know you don't have the same size drive but you can see from what I am saying that it will give you something you can live with for a long time to come.

---

### Post by presence1960 on 2009-06-23
We are leaving out some important advice : Back up your files & defrag Vista at least once or twice . Then try resizing the Vista partition from within Vista.

As for easy bcd, why use that? GRUB is way more versatile and easier to configure!

---

### Post by executorvs on 2009-06-23
second the defrag comment on vista before repartitioning, it does a better job of cleaning its self than xp out of the box but still not great.

DO NOT use Gparted to shrink Vista or the recovery partition, vista has these recorded and panics if they're different on it's next boot.

Stick with grub for your bootloader, it sets up on it's own during boot and is easy to repair later should something go wrong.

as for the space needed by vista, it says it needs it but it's actually mostly empty so you don't need to worry about space vista side.

as people say 20-30Gigs is huge in linux if you keep only what you need i.e. don't install the entire repo

---

### Post by pooja on 2009-06-24
I'll take up all the space Vista is giving me, ~31GB.
I already backed up documents and data and defraged Vista twice. I want to keep Vista's bootloader so I guess I'm going to follow NeoSmart Technologies's guide. 

That guide shows how to install **Grub in Ubuntu's partition**. 
I've read of people who after trying out Ubuntu for a while, wanted to remove it but since Grub had been installed in place of Win's MBR, when they removed Ubuntu's partition they were no longer able to boot into Vista. They had to reinstall Vista from a DVD. I however, don't have a Vista DVD. I only have an HP Recovery partition in the hard disk and don't know how to use it in case the MBR needs to be re-installed. So I better keep Grub and MBR apart and leave MBR in charge of the boot up process. 

For safety reasons, should I make Recovery Disks from within Vista? What are they used for anyway?

PS: I checked Computer, in Vista, and it states C:/ is 95.4GB free on total 143 GB. This means I am occupying 47 GB with programs and files. To save some more space I did as **irv** suggested, I cleaned up Vista by removing unnecessary applications. Things didn't change much though.

---

### Post by pooja on 2009-06-24
By the way, how much space does Compiz occupy in Ubuntu?
And what about Nvidia drivers, how much do they occupy?

---

### Post by executorvs on 2009-06-24
just a few Mb, not much at all.

---

### Post by wojox on 2009-06-24
Want to shrink windows ?
1. Scrub you disk, killdisk is a nice HD scrubber for free.
2. Install ubuntu.
3. Enjoy !!!!

Ubuntu: Anything you can do I can do better. I can do anything better than you. :D

Vista: No you can´t. :mad: 

Ubuntu: Yes I can. :D

Vista: No you can´t. :mad:

Ubuntu: Yes I can. :D

---

### Post by pooja on 2009-06-24
> **executorvs said:**
> just a few Mb, not much at all.

How much, 400 MB approx.?

And are the Nvidia drivers available for Ubuntu? Do they also occupy 400 MB?

---

### Post by executorvs on 2009-06-24
no no, less than 100Mb all together. it's been awhile but they take up very little space I don't think it's even 40Mb, but I could be a little off.

---

### Post by pooja on 2009-06-24
Apart from the applications that are installed from the ubuntu CD installation, what is the most heavy package/software you have downloaded on your computer? Cinelerra? That must be quite a huge bundle. 
For example, I'm very fond of LaTeX and am using MikTex repository under WinVista. It takes up some 140 MB, add TeXniCentre to that and that makes it 150 MB. But I've googled about the size of texlive-latex-basic and it around 2 MB, maybe it is larger once it's expanded, I don't. 

I finally starting to get what people earlier meant by "30 GB is a lot of space" and "Ubuntu is not a resource hog like Vista". So maybe I should take 25GB, considering that 10GB go for Ubuntu itself, I'm left with 15 GB of space for my needs. On the other hand Vista has 7GB more than what it would have had I taken all the available space.
I hope I may be able to expand Vista or Ubuntu if needed.

---

### Post by presence1960 on 2009-06-24
> **pooja said:**
> Apart from the applications that are installed from the ubuntu CD installation, what is the most heavy package/software you have downloaded on your computer? Cinelerra? That must be quite a huge bundle. 
For example, I'm very fond of LaTeX and am using MikTex repository under WinVista. It takes up some 140 MB, add TeXniCentre to that and that makes it 150 MB. But I've googled about the size of texlive-latex-basic and it around 2 MB, maybe it is larger once it's expanded, I don't. 

I finally starting to get what people earlier meant by "30 GB is a lot of space" and "Ubuntu is not a resource hog like Vista". So maybe I should take 25GB, considering that 10GB go for Ubuntu itself, I'm left with 15 GB of space for my needs. On the other hand Vista has 7GB more than what it would have had I taken all the available space.
I hope I may be able to expand Vista or Ubuntu if needed.

31 GB is plenty unless you are going to be storing a huge amount of data. AS far as software goes you have enough space for 2 or 3 Ubuntu's packed with software.

---

### Post by presence1960 on 2009-06-24
to restore windows bootloader to MBR without install disk see this : [http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

or download a Vista repair Disk here: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by santhust on 2009-06-25
hi.
if you wish to try ubuntu then two ways:

1.) you can install ubuntu-9.04 straight in vista (mind I said in vista) like any other software/application. few days back i installed ubuntu separately, leading to dual boot. however i got an option of installing ubuntu in vista, when i ran live cd of ubuntu-9.04 in vista.

2.) you can have dual boot option. what you need is to have a ubuntu live cd. then u don't have to create space for it via shrinking vista size through vista itself (which give way to limited space). just insert the ubunut live cd in your drive and restart. follow the options. you can have as much space as you wish not limited like in the case of shrinking from vista.

to obtain a live cd: order it or download it from internet.

best of luck.:P

---

### Post by pooja on 2009-06-25
**santhust** thank you for your advice. Indeed I have downloaded and burnt the Live CD but I prefer installing Ubuntu in a partition of my hard disk. 

Since I saw that most of the programs don't cost much in terms of space in MB, I think I probably go for something much less than 30 GB, maybe 22 GB in total (10GB for system + 12 GB for my necessities). 

What do you say? Is it a reasonable deal for my purposes (listening to music, occasionally downloading movies, surfing the net, writing documents with Latex and OpenOffice)?

---

### Post by executorvs on 2009-06-25
keep in mind that some software has functions that can be space intensive like video editing.

also have you looked at the pros/cons of the various formats for your linux partition?
I recommend EXT4 I've been using it since beta 4 of jaunty and have had only good things to say about it's performance.

---

### Post by irv on 2009-06-25
> **executorvs said:**
> keep in mind that some software has functions that can be space intensive like video editing.

also have you looked at the pros/cons of the various formats for your linux partition?
I recommend EXT4 I've been using it since beta 4 of jaunty and have had only good things to say about it's performance.

I believe that the EXT4 is mush faster at booting up. Only 20 seconds on my Dell Inspiron 1521 laptop.

---

### Post by lisati on 2009-06-25
> **executorvs said:**
> second the defrag comment on vista before repartitioning, it does a better job of cleaning its self than xp out of the box but still not great.

DO NOT use Gparted to shrink Vista or the recovery partition, vista has these recorded and panics if they're different on it's next boot.

Another "second" on the "back up your data"

And having not long used gparted to tinker with the partitions on a fresh Vista install to get the machine in a "fresh out of the box state" (the original installation was showing signs of things not being quite right), I can relate to Vista panicing - I had a black screen of death ("missing" file(s)!!1), easily fixed by using the "repair" option on the recovery disk.

(now to wait for Vista to finish doing its updates, so I can put Ubuntu back on the machine!!!)


Edit: BTW, I chose gparted over Vista's partitioning tools is that the last time I tried something similar on the same machine, Vista didn't let me change anything.

---

### Post by pooja on 2009-06-25
> **executorvs said:**
> 
also have you looked at the pros/cons of the various formats for your linux partition?
I recommend EXT4 I've been using it since beta 4 of jaunty and have had only good things to say about it's performance.
 
What pros/cons are you talking about? Would you name them explicitly?

> **executorvs said:**
> 
keep in mind that some software has functions that can be space intensive like video editing.

 
Yeah, that's why  in a previous post, I was asking how much space does Cinelerra occupy in MB (or GB). Does anybody know? 12GB is a lot of space after all, considering that of the real 22 GB, 10 will go for system files etc. 
At the moment, in Vista, I have some 84 programs/applications installed in C:, occupying 1.90 GB. Yet when I go to *Computer* I see Local Disk C: has **96 GB** upon 143 GB of **free space**. I have already backed up important files and/or documents.

---

### Post by executorvs on 2009-06-25
Cinelerra is not a big program nor is Kino or LIVES or 2manDVD (most listed are between 3 and 30Mb once installed). The video files however can be large, DVDs can hold movies in a state which takes 4Gb. In some cases you need to be able to fit both the file you are working on and the corresponding output file at the same time. as you can read and write to your NTFS partition this storage limitation may not be a big issue.

as for formatting pros and cons
in EXT2 and EXT3 you can, by means of third part software (ext2fsd), read and write from windows.

I don't believe the software will work with EXT4. however I have not tested to see if EXT4 will support EXT2 type non-journaled entries.

you could in theory use Fat32 for your ubuntu install, but I don't know what kind of issues might arise.

I use EXT4 because it's ability to handle Large files very well. as has been mentioned it can load very quickly.

there are more pros and cons that get technically difficult for me to argue. maybe someone else could expound from this?

---

### Post by irv on 2009-06-26
> **executorvs said:**
> Cinelerra is not a big program nor is Kino or LIVES or 2manDVD (most listed are between 3 and 30Mb once installed). The video files however can be large, DVDs can hold movies in a state which takes 4Gb. In some cases you need to be able to fit both the file you are working on and the corresponding output file at the same time. as you can read and write to your NTFS partition this storage limitation may not be a big issue.

as for formatting pros and cons
in EXT2 and EXT3 you can, by means of third part software (ext2fsd), read and write from windows.

I don't believe the software will work with EXT4. however I have not tested to see if EXT4 will support EXT2 type non-journaled entries.

you could in theory use Fat32 for your ubuntu install, but I don't know what kind of issues might arise.

I use EXT4 because it's ability to handle Large files very well. as has been mentioned it can load very quickly.

there are more pros and cons that get technically difficult for me to argue. maybe someone else could expound from this?
Because EXT4 is much better then EXT2 or 3, I do this:
A way around this is to setup a partition to move files from ext4 to a fat32 partition. This way when you are in either ntfs or ext4 you can get to the file in fat32. Here is a screen shot of my hard drive.
[ATTACH]119031[/ATTACH]

---

### Post by alfu on 2009-09-22
I just got a new H-P laptop (WAY too much bling) with a 320GB HDD, of which Vista claims it needs 190GB for ~40GB of actual bloat.  **No way it is going to get it.**

I removed a lot of drek and defragged with Vista (took forever). The external fancy-pants DVD drive provided with the computer reads a CD fine, but on attempting to burn a Recovery Disk, the Recovery Manager indicates: "This computer does not have a drive capable of creating CDs or DVDs".  It turns out ANY DVD except Memorex will work, according to H-P.

How this resolved is dealt more completely [here]("http://ubuntuforums.org/showthread.php?t=1175269").

---

### Post by Herman on 2009-09-22
:) Defragging Windows used to be necessary if the Ubuntu 'Alternate Installation' CD's partitioner wasn't able to resize Windows.
Defragging before partitioning might also be necessary if you're going to use Vista's own partitioner, I'm not sure about other partitioners.
I have  tried Vista's own partitioner once and it did the job very well and quickly too I might add. 

Readers might be pleased to know that since GParted has been around it's no longer necessary to spend hours defragging Windows before resizing a Windows partition. GParted uses programs that are smart enough to carefully relocate files in the Windows partition regardless of the state of fragmentation without data loss. 
It is always recommended to make a backup of all files and especially important files before using any partition editor if you don't already have a backup.
I recommend running CHKDSK C: /R if possible before resizing a Windows partition though, and again afterwards as recommended by GParted documentation. (GParted will program Windows to do a quick file system check on the next boot anyway if you don't run one manually).

A file system check is well worth doing, and defragging is good for Windows, but if you're planning on using GParted to resize Windows you can save yourself hours and hours of time by skipping the defragging. :)

---

### Post by Herman on 2009-09-22
Another popular myth about resizing Windows using GParted is that it will make Windows difficult or impossible to boot again.

The reason for that problem is because Windows decided suddenly to stop having their partitions start and finish on the first sector of a hard disk track, (usually sector number 63), but instead to make the start of the first partition begin in sector number 2048.

GParted defaults to lining partittions up on cylinder boundaries, and if you don't remove the checkmark from the 'align on cylinder boundaries' checkbox before resizing your Windows, GParted will take hours, painfully relocating every file in Windows to dutifully re-align Windows on a cylinder boundary. Then when you reboot, Windows will need to find all it's files again.

To avoid all that hassle and make resizing with GParted a lot quicker, just remove the check mark: 

[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]

If you remove the checkmark before resizing you will find resizing Windows a lot quicker, and Windows boot sector will be left in sector number 2048 and Windows Vista or Windows 7 will reboot just fine without any error messages and without the need to 'repair' itself. :)

This tip does not apply to the Ubuntu installer's built-in partititioner but only to GParted in the Ubuntu Live CD or GParted Live CD or Parted Magic. The Ubuntu installer's GParted does not move the start point of the Windows partition so it is not necessary to do anything special if you're using the Ubuntu installer's inbuilt partititoner.

It's simple to check what sector a Windows partition both before and after resizing by right-clicking on the partititon in GParted and clicking 'properties'.
Another way to check is to run 'sudo fdisk -lu'.
You will find that as long as Windows's boot sector is not moved, there will be no boot problems.

Regards, Herman  :)

---

