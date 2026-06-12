---
title: "Ubuntu on a USB drive?"
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by shubox357 on 2005-10-03
Is there any way ubuntu can be run live from a USB drive?

---

### Post by shubox357 on 2005-10-09
anyone??

---

### Post by costoa on 2005-10-09
[QUOTE=shubox357]Is there any way ubuntu can be run live from a USB drive?[/QUOTE]

Yes but IFAIK there's no automated setup for Ubuntu yet. This means it will install but requires some advanced configuration work. Other distros like [dsl]("http://www.damnsmalllinux.org") and [slax]("http://slax.linux-live.org") have tools you can use while running their distros from a cd-rom to easily setup a flash boot drive.

I wish there was a better answer. I'm sure there will be an unoffical Ubuntu / USB boot version in the next six months but not today.

I've been playing about with a minimal Ubuntu boot / network installer disk image based on Debian's excellent single floppy installer. The idea is that one could download the disk image, write it to an USB drive, reboot and network install needed apps. Right now it's very alpha but might be ready someday.

---

### Post by shubox357 on 2005-10-09
sounds cool, i cant wait until i can jsut haev it on a USB pen drive adn take it to any computer i come in conatact with. i jsut dont like using Microsoft that much

---

### Post by costoa on 2005-10-09
My goal is to build a custom iso/installer for USB drives and then the iPod nano. With the nano there would be custom tools to access non DRM'd music and save notes, pictures, contacts, to dos and calender entries accessible from the iPod's interface. 

The problem right now is thinning out the standard distro down to less than 100m and still have feel like Ubuntu.

---

### Post by andrewsawyer on 2005-10-09
Beaten to it...

I was just about to start a thread like this, and came across this one.  After reading a Slashdot article today, I was thinking about making to move to USB.  I've tried before with DSL and a couple of other variants, but I would love a USB version of Ubuntu.

I might have to give it a try myself, but I have a couple of questions that you guys might be able to answer for me before I go out and buy a USB stick:

1. How big should it be?  Obviously in this case, bigger is better.  I have a 1Gb USB drive, but would that be big enough?  I know you can get 2Gb USB drives.  Can you get them any bigger than that?  You can get 8Gb SD cards (I think), but what about USB?  How big is a standard install of Ubuntu, with networking tools, FireFox, Thunderbird and OO.org?

2. Should the drive be partitioned with a swap partition?  As it could be assumed that it would be used on more than one PC, and more than likely the default OS on these would be MS, should you be having say a 512Mb swap partition on the drive or would that be a waste of space?

3. Security would be a BIG issue with something like this, as loosing your disk, or forgetting to unplug from someones computer would leave not just your files, but your entire OS and possibly all your emails open to anyone who had the disk.  What options would be most suitable for getting around this problem?  A USB with built in fingerprint reader, or software encryption, or both?  If software, what would be a good choice?

4. Some computers don't allow booting from USB.  I've seen two options for OS's on USB drives.  One allowing the user to boot, and another allowing them to run the OS from within Windows (from an exe file).  Obviously the second is much slower.  I have tried to get a USB disk to allow both options - booting as a preference, however allowing the user to run out of Windows if necessary, but I've not had much luck.  Is this even possible?

5. If you were to use this as stated in the Slashdot article, it would be your main OS.  What would the speed of such a device be like?  Is it something that you could just plug into your home PC and use, unaware (speed wise) that it was anything other than a partition on a EIDE drive, or would the speed be terrible?  I'm obviously talking about booting from USB rather than running from within Windows.

If someone could help answer any of these questions, it would be much appreciate!

Many thanks,

Andy

---

### Post by casper_2095 on 2005-10-10
Seems people are selling preloaded usb drives - all the work is done and dusted...
[http://www.geekzone.co.nz/content.asp?ContentId=4879](http://www.geekzone.co.nz/content.asp?ContentId=4879)
[http://www.pertec.com](http://www.pertec.com) (parlez-vous?)

Or do it yourself, and guard against misadventure...
[http://www.debian-administration.org/articles/179](http://www.debian-administration.org/articles/179)

And as mentioned above...
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://slax.linux-live.org/](http://slax.linux-live.org/)

For my 2c, this is a bleeding edge niche and I wouldn't like to see Ubuntu resources consumed on it just yet.

---

### Post by andrewsawyer on 2005-10-10
I would have to agree that at the current time, this is something that is still in its infancy.  Unfortunately, as I didn't start the thread, I can't add a poll to question whether this is something that more people might like, or whether it is just the small minority that would like a system like this.

Personally, the idea of having my Ubuntu desktop available to me everywhere I go, on any computer that I choose sounds very appealing.  I like the idea o having my icons, themes, programs and background available to me where ever I am in the world without the need for a laptop.

I have had a look at the links posted above by casper_2095, although unfortunatley they aren't Ubuntu.  The DIY link is for Debian Sid (and may be of help to someone trying to make an Ubuntu LiveUSB), however the only info that I can gain from the other is that it is a Gnome based distro.

I don't think that a downloadable iso all ready to go would be something that the Ubuntu team should be occupied with, however a nice how-to would get the ball rolling for those of us who would like to give it a go, but are lacking the skills to do it themselves.

Going by a search at [Dabs.com]("http://www.dabs.com/productview.aspx?Quicklinx=3PP3&CategorySelectedId=11152&NavigationKey=11152,40096") , you can get USB drives upto 4Gb (solid state), and as I see it you would need maybe four partitions:

1. Bootable
2. Root - encrypted (ext2)
3. Home - encrypted (ext2)
4. FileShare - not encrypted (fat32)

You could keep all your private info, email, contacts etc in the Home partition, while still keeping info that you might like to share on the FileShare partition, which would be viewable from Windows as well as Linux.

Note: Possibly make the FileShare partition a standard size - 128Mb, 256Mb etc.  Purely from a security perspective, if the drive was ever lost, Regular Joe might look at the drive he just 'picked up off the desk' in his Windows machine and assume it to be only a 256Mb drive with some invaluable data on it, as the ext2 partitions wouldn't be visible.  An extra layer of 'security'?

As you can probably see, I'm just playing around with some ideas in my head at the moment, and as I'm still not sure on the speed of such a device it might not even be worth having, however the idea is now up here on the forums, so it'd be good to get some other peoples insite on the topic.

After reading through the link in the above post, I can now answer some of my own questions: yes, you can get a USB solid state drive big enough for Ubuntu; no, you won't need a swap partition; software encryption seems to be a route that is available, however using a mixture of both software and hardware would be good too.

Anyway, I've drivelled on a little too long now!  I'll keep an eye on this post though and see what people think of the idea.

---

### Post by shubox357 on 2005-10-14
i think itd be cool to have it on an iPod shuffle too

---

### Post by 11hjpphty76lkjj on 2005-10-14
Not sure if this will help:
[http://www.ubuntuforums.org/showthread.php?t=75439](http://www.ubuntuforums.org/showthread.php?t=75439)

I'm thinking it should be the same for a usb flash drive--of course you'd need a large capacity one.  But I have done these steps with a usb hard drive it and works great.

Aaron

---

### Post by shubox357 on 2005-10-16
yeah thats cool but I'm maibnly interested in running it off a USB drive without installing anything, just walking up ot a PC and running Ubuntu on it without installing anything. has anyone tried that yet?

---

### Post by 11hjpphty76lkjj on 2005-10-16
I haven't tried it on a USB flash drive per se, but I am currently using Ubuntu Breezy on a USB hard drive.  The setup should be the same, so it should work.  A hard drive may be a better choice because it may have a longer life span.  I can boot from Ubuntu USB hard drive from any computer that is USB boot enabled.  and it works great.

Aaron

---

### Post by DaBruGo on 2005-10-27
kalosaurusrex,

There has to be a way to load a scaled down version of Ubuntu on a USB flashdrive (the small keychain type) with just the OS and a browser/email program loaded in. That would really make an awesome and very portable OS "on a stick". If we leave OpenOffice out (as well as some other programs) it should free up enough space to install.

After reading some of your posts (and posts from others) I was able to get Ubuntu Breezy loaded to a 40GB external usb drive. Here is how I accomplished it ... [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

Now, if I am a complete Ubuntu newbie and I could get the thing loaded on an external USB hard drive within a week ... surely a number of us can figure out how to get Ubuntu onto a 1GB USB memory stick? I mean, if they can get the whole Live CD into roughly 630 megs, surely we can figure something out with 1GB to play with.


So, here is what I'm thinking on this idea ...

(1) Can we get a very scaled down version of Breezy loaded on a USB flashstick (lets say, a 1GB size unit)?

(2) Which version could we use to accomplish this ... the Live CD or the Install CD?

(3) What partition formats should, or can, we use on the USB flashstick to accomplish this?

(4) How would we setup the Xserver stuff so video cards/monitors function properly ... like the Live CD accomplishes on so many different PCs?

Thats just a few of my thoughts on this. I am sure this is somehow possible. With enough people scratching their heads on this, we should be able to get a very minimal install of Ubuntu on a keychain-sized USB device.

How should we approach this?


DAVE

---

### Post by 11hjpphty76lkjj on 2005-10-27
> (1) Can we get a very scaled down version of Breezy loaded on a USB flashstick (lets say, a 1GB size unit)?

(2) Which version could we use to accomplish this ... the Live CD or the Install CD?

(3) What partition formats should, or can, we use on the USB flashstick to accomplish this?

(4) How would we setup the Xserver stuff so video cards/monitors function properly ... like the Live CD accomplishes on so many different PCs?

1/2:  I'm sure a base install would fit on a 1 gig flash drive, but I'm not 100% sure.  I'll need to do some experiements to see how big the base install is, but I think it will fit.  Which would work nice because the install will install the GRUB boot loader on the boot sector of the flash drive.  Either that or perhaps somehow copying the boot sector from the cd and making an img and then copying the boot img to the flash disk, and then copying over the live cd and then modifying GRUB and the initrd file for the correct /sda instead of hdb.  That might work as well.

3:  I'm assuming that the standard / partition should be fine.  Although the problem is creating a swap partition that would be 1.5-2x the size of a standard machine ram.  assuming everyone has at least 128mb ram that's a 256mb swap that leaves only 744mb of disk space. hmmm..perhaps using a live cd image, even though it will be more complicated would be the best route.

4: assuming we can get the live cd to install on the flash disk the live cd configures the x server on boot I believe. (i could be wrong however.) if not having a boot task that runs the dpkg-reconfigure xserver-xorg to setup xserver might work..

I don't have a 1 gig flash drive, I wish I did and I'd try to help more.  Not sure if this helps atall..but it's some thoughts..

Aaron

---

### Post by DaBruGo on 2005-10-27
[QUOTE=kalosaurusrex]1/2:  I'm sure a base install would fit on a 1 gig flash drive, but I'm not 100% sure.  I'll need to do some experiements to see how big the base install is, but I think it will fit.  Which would work nice because the install will install the GRUB boot loader on the boot sector of the flash drive.  Either that or perhaps somehow copying the boot sector from the cd and making an img and then copying the boot img to the flash disk, and then copying over the live cd and then modifying GRUB and the initrd file for the correct /sda instead of hdb.  That might work as well.

3:  I'm assuming that the standard / partition should be fine.  Although the problem is creating a swap partition that would be 1.5-2x the size of a standard machine ram.  assuming everyone has at least 128mb ram that's a 256mb swap that leaves only 744mb of disk space. hmmm..perhaps using a live cd image, even though it will be more complicated would be the best route.

4: assuming we can get the live cd to install on the flash disk the live cd configures the x server on boot I believe. (i could be wrong however.) if not having a boot task that runs the dpkg-reconfigure xserver-xorg to setup xserver might work..

I don't have a 1 gig flash drive, I wish I did and I'd try to help more.  Not sure if this helps atall..but it's some thoughts..

Aaron[/QUOTE]

I have a 1GB flash stick (that I purchased from Best Buy). So, if we can figure out how to get the basic installation to work, I am more than willing to try it out. 

REGARDING 1 and 2 ...

I'm wondering if the "expert" install method gives you the flexibility to load whatever apps you want. If it does, we could load a very basic install (with a few core apps ... browser/email etc.) to the flash stick. If we can get it working from a simple, minimal install method then we can enter tweak heaven from there (grin). Then maybe we could figure out how they squish down everything on the Live CD and squish ours down as well!

I also read in another post that there is a way to dump the grub bootsector info from an external USB drive into a .bin file (example: dd if=/dev/hda of=/boot/ubuntu_boot_sector.bin) and then copy this file to a windows directory on another drive. 

Then, by adding a line (c:\ubuntu_boot_sector.bin="Start Ubuntu Linux") to the bottom of the Windows XP boot.ini file, they were able to boot Ubuntu from the windows XP bootup manager screen ... without even having grub on the bootsector of the XP drive!

I wonder if we can do this with the bootsector info from the Live CD?

REGARDING 3 ...

Can we hard code how big the swap file can be? Does the swap file HAVE to be 1 1/2 times bigger? Can we create a ramdisk and put the swap file in it?

Also, I wonder what format the partitions on the flash stick should be?

REGARDING 4 ...

If we could get the Live CD to pull over ... it would have all the openoffice apps on it ... that would be sweet!

Does the 'dpkg-reconfigure xserver-xorg' command really configure the video every time you bootup? That would be awesome if it does. My external USB hard drive at home would then work on my work PC. Last time I brought it in to work, I got the dreaded error message that the xserver couldn't start. 

Is that how the Live CD works on almost any video?

Anyway, great chat! Maybe we can pull some other scratching heads in here to work on this idea with us. I just know we can do this somehow! If you can think of something you want me to try on my flash stick, post it here and I'll be looking for it.


DAVE

---

### Post by andrewsawyer on 2005-10-27
Hi guys,

A few of thoughts - 

1. Don't use a swap file.  USB disks only have a limited numbe of write times (1 million or something), so adding a swap file will greatly reduce the life of your disk. - If you're worried about the speed, see below - it is possible to load the system in to RAM. Also consider that the LiveCD doesn't have a swap partition.

2. If it's on a USB drive, it might as well be a Live disk.  For the extra trouble (and there might not even be any extra hassle) you would be able to use it on any pc - not just your own.

3. For the same reason as 1. you should get the system configured, and then mark the boot and root partitions as read only.  If you want to change it later, it'd just mean a reboot first.

4. Make the home partition fat32.  It's a usb drive, that you will carry with you where ever you go right?  Might as well be able to get access to your files from the school/uni/work pc, or from a mates windows machine that doesn't allow boot from USB.  Or, if its a big enough drive, have two partitions - a home, ext2 partition that is encrypted, and then a smaller fat32 to do data transfer on.

5. I mention ext2 above because the rest are journalling.  Again, this will limit the life of the disk - correct me if I'm wrong.

Having had a look at the standard kernel, its configured as standard to load pretty much every module on offer.  Also the fact that the liveCD will fit on 630Mb or whatever, while a standard install is about 1Gb (which I assume is due to compression - again feel free to correct me) would make it more sensible to make a liveCD rather than a standard install on a usb drive

Oh - I was reading a thread - I don't remember where - either on Ubuntu Forums or Gentoo Forums about getting your system to load into ram.  This might be worth considering as it would solve the speed issue associated with running from a USB disk.  I didn't read it too carefully, so I'll have to look it up again and link to the thread.

Well, I hope that info sould help someone.  I'm currently waiting for my 8Gb LaCie Carte Orange USB disk to drop through the post, but unfortunately they won't start shipping until mid-November!

Anyway, catch ya all later

---

### Post by DaBruGo on 2005-10-28
Hey Guys,

If we were to try and get the Live CD contents onto a USB flash stick, where would we begin the process from?

Should we just copy the entire Live CD directory structure over to the USB flash stick, or is there another way we should go about this? Should we copy it over from within a fully installed version of Ubuntu or would Windows XP work for us?

On the Install CD, in expert mode, I saw an option in one menu somewhere involving the making of a live cd on read-only media. But, I don't know if we could point it to a flash drive and have it install correctly.

We would also have to figure out how to get the stick to be bootable. Which bootloader should we use for this? There is grub and loadlin and lilo and another app called syslinux. Which one would work the best?

Theoretically, if we get all the Live CD files onto the flash stick, we just need to figure out how to make it bootable.

Maybe we could copy the grub bootsector info off of another drive and try to duplicate it on the flash stick (using the dd option that I have previously mentioned in this thread). Or, maybe we could use one of the other bootloaders for this?


Lets try to get a basic outline together on how we could do this and then smack this beast down step by step.

(I'm sure this isn't rocket science ... but it sure feels like it right now.)


DAVE

---

### Post by 11hjpphty76lkjj on 2005-10-28
Would you have to format the usb drive to ext2 and then copy over the files?  I don't believe a straight copy would work correctly.  Perhaps boot from an install cd with the usb drive connected do expert, format the drive using the parition wizard skip all the rest of the steps and install the grub boot loader then copy the live cd over to the drive from within ubuntu and then edit the grub per the instructions in the install to usb hard drive thread.

hmm damn I wish I had a 1 gig flash drive..this sounds like a lot of fun.

Aaron

---

### Post by DaBruGo on 2005-10-28
Maybe , we could even add another partition (fat or fat32) to the flash stick to store our documents (so we could access them from almost any OS), since the Live CD is only about 670 MB in size.

hmm...

Aaron, you're starting to want that 1GB flash stick, arent ya?

(he he)



DAVE

---

### Post by DaBruGo on 2005-10-28
Here is a little additional reading material to help with our brain overload in here ...

[https://wiki.ubuntu.com/LiveCDCustomizationHowTo](https://wiki.ubuntu.com/LiveCDCustomizationHowTo)



DAVE

---

### Post by DaBruGo on 2005-11-01
Hi Folks,

I did a google search on some words (make live cd usb) and found some info on a Gentoo Linux site that may work for us, but I need your help to fill in this outline. Here are the basic steps given (which I believe were run from within linux) to get a Live CD onto a USB Flash Stick ...


(1) write an MBR to the USB memory stick (using a dd command)

(2) format the stick with vfat (which i think is good ole FAT, or FAT16)

(3) mount the stick (using a mkdir command and a mount command)

(4) copy the live cd contents to the usb stick (using the cp command)

(5) unmount the stick (with the umount command)

(6) run syslinux on the stick to make it bootable


Supposedly that's all we need to do. Can some of you guys fill this outline in with the meaty details. I can test it out on my USB flash stick (1GB in size) to see if it really works.

I think we're getting closer ... 



DAVE

---

### Post by andrewsawyer on 2005-11-01
Sounds like a plan.

Can I just confirm that no-one has yet tried just mounting the iso and copying the entire lot over to a USB, or writing to the USB instead of CD, and then changing the boot drive details to point to a USB mount rather than a CD mount?

As far as the MBR bit, you'd just use Grub wouldn't you, with the kernel in a directory called /boot?  I installed Gentoo a while ago, and I can't remember for sure, but I'm pretty sure thats all I did.  All the details on how to install Grub (and LILO I think) are in the Gentoo docs secton of the site.

If you are using Breezy, you can format the USB disk with the System >> Administration >> Disks utility (although I would do this before the MBR bit).  Not sure whether you would specify a partition for the boot sector (32Mb) or something, or just do it the Ubuntu way and have it as part of the /root partition.

Again, mounting can be done with the Disk utility in Breezy - keeping it simple and GUI based.

I've never used syslinux before, so wouldn't have a clue what to do with this, although you could just use fdisk to create the partitions in the first place and mark the /boot as bootable.

In fact (and I'm just writing this as I'm thinking about it - sorry if my mind skips about too much), stick the USB disk in.  Use fdisk to format it into whatever filesystem and partition structure you like (I'd suggest at least one fat16 for windows access, and don't use a journalling file system).

In fdisk, mark the one partition as bootable (I'm not sure what it is in terms of the three letters, and I know this is wrong, but for the sake of example, I'll stick with hda as thats what people are familiar with).  So make hda1 bootable and mount it as /boot, make hda2 mount as / and then have hda3 as /home and just have them with whatever file system you like.

When all is mounted, stick in a LiveCD, and just drag it all over.  You would then have to go into /boot/grub/menu.lst and alter the paths - swap hda for whatever USB sticks mount as.

That would be it wouldn't it?  You'd probably want to make the lot (with the exception of /home) read only.  It's designed that way anyway and it will increase the life span of the USB disk.

Many that will help, maybe I have forgotten about something major - I guess without doing it you just won't know!  I wish you luck though, and I'll definately be trying when my new USB stick comes through the post.

Final thought - would it be worth trying to get a USB drive (normal hard drive running off USB) to work as a live disk first, and then just move it over to a stick?  You have more space to play with then.

---

### Post by DaBruGo on 2005-11-01
[QUOTE=DaBruGo]

(1) write an MBR to the USB memory stick (using a dd command)

(2) format the stick with vfat (which i think is good ole FAT, or FAT16)

(3) mount the stick (using a mkdir command and a mount command)

(4) copy the live cd contents to the usb stick (using the cp command)

(5) unmount the stick (with the umount command)

(6) run syslinux on the stick to make it bootable

[/QUOTE]

Assuming that my USB flash stick shows up as /dev/sda at startup ...

In step #1 :
How would I use the dd command to get a MBR onto the USB device? 

In step #2 :
What is the correct Ubuntu terminal command to format the stick as vfat? 

In step #3 :
What should my mkdir and mount commands be?

In step #4 :
If I have a full install already on a hard drive and pop in the Live CD, what is the correct terminal command to copy the Live CD to the USB flash stick. 

In step #5 :
What should my unmount command be?

In step #6 :
I believe this is a simple command involving the typing of syslinux with a few parameters into a terminal window.


STATUS OF MY TESTING ...

Last night I did a format of my USB flash stick in windows xp (as FAT) using the 'HP USB Disk Storage Format Tool'. Then I copied over the Live CD contents (using windows xp) to my USB flash stick. After that, I tried to follow the syslinux setup instructions to get the flash stick bootable.

Well ... I did see some light at the end of the tunnel. It did come up with a screen with the Ubuntu logo on it. But, I got an error message that said 'Could not find kernel image: /install./vm'. And below the error line was a 'boot:' prompt. When I checked the syslinux.cfg file, everything looked OK?

What I'm thinking is this ... if we can get this whole process accomplished from within a linux session (running from a full install with the Live CD in the drive and the USB flash stick connected), then I think it will work.

If we can get the correct ubuntu linux commands for our steps above, I think we can do this with minimal effort!


We need a Jimmy Neutron brain blast here,
DAVE

---

### Post by DaBruGo on 2005-11-01
ANOTHER STATUS UPDATE

I made some changes to the syslinux.cfg file and that seemed to fix the initial kernel error message I was getting.

When I rebooted the PC with the USB flash stick connected ... I saw the Ubuntu logo and after hitting enter it loaded vmlinuz and initrd.gz successfully (yipee)

I then got to the "Ubuntu Live" blue-colored screen and I successfully chose my language and keyboard settings.

And then it hacked up a furball (sigh) ... at the "detect and mount CD-rom" step. It wants to read the CD-ROM to get whatever files it needs, instead of getting the files from the USB flash stick.

There must be a file somewhere that is pointing the startup procedures to the CD-ROM.

Anyone got any ideas?


DAVE

---

### Post by andrewsawyer on 2005-11-01
> n step #1 :
How would I use the dd command to get a MBR onto the USB device?

I have had a look at dd, however it doesn't mention MBR at all.  It looks like it is designed to convert the contrents of a file when copying?!?!

```
andrew@sam:~$ dd --help
Usage: dd [OPTION]...
Copy a file, converting and formatting according to the options.

  bs=BYTES        force ibs=BYTES and obs=BYTES
  cbs=BYTES       convert BYTES bytes at a time
  conv=KEYWORDS   convert the file as per the comma separated keyword list
  count=BLOCKS    copy only BLOCKS input blocks
  ibs=BYTES       read BYTES bytes at a time
  if=FILE         read from FILE instead of stdin
  obs=BYTES       write BYTES bytes at a time
  of=FILE         write to FILE instead of stdout
  seek=BLOCKS     skip BLOCKS obs-sized blocks at start of output
  skip=BLOCKS     skip BLOCKS ibs-sized blocks at start of input
      --help     display this help and exit
      --version  output version information and exit

BLOCKS and BYTES may be followed by the following multiplicative suffixes:
xM M, c 1, w 2, b 512, kB 1000, K 1024, MB 1000*1000, M 1024*1024,
GB 1000*1000*1000, G 1024*1024*1024, and so on for T, P, E, Z, Y.
Each KEYWORD may be:

  ascii     from EBCDIC to ASCII
  ebcdic    from ASCII to EBCDIC
  ibm       from ASCII to alternated EBCDIC
  block     pad newline-terminated records with spaces to cbs-size
  unblock   replace trailing spaces in cbs-size records with newline
  lcase     change upper case to lower case
  notrunc   do not truncate the output file
  ucase     change lower case to upper case
  swab      swap every pair of input bytes
  noerror   continue after read errors
  sync      pad every input block with NULs to ibs-size; when used
              with block or unblock, pad with spaces rather than NULs

Note that sending a SIGUSR1 signal to a running `dd' process makes it
print to standard error the number of records read and written so far,
then to resume copying.

  $ dd if=/dev/zero of=/dev/null& pid=$!
  $ kill -USR1 $pid; sleep 1; kill $pid
  10899206+0 records in
  10899206+0 records out

Report bugs to <bug-coreutils@gnu.org>.
```

Can I suggest using fdisk from within a terminal (in Ubuntu):

```

sudo fdisk /dev/sda (or whatever your device is set up as - mine is /dev/sdb)
```

Please note: If there is a --- followed by text, this is comment.  Don't write this into the terminal

```
andrew@sam:~$ sudo fdisk /dev/sdb

Command (m for help): d
Partition number (1-4): 1

Command (m for help): d
Partition number (1-4): 2

Command (m for help): d
Selected partition 3

--- The above deletes any existing partitions that are on the disk.  There will be a maximum of 4, so just 'd' then '1', then 'd' then '2' until there are none left.

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

--- If you want to view the commands at any time, just hit 'm'

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1024, default 1):
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-1024, default 1024): +50M

--- This creates your first partition (where all the liveCD files will be copied to.  I have made it 50Mb (+50M), however this is because I only have a 130Mb USB disk.  You should make it 600Mb (type +600M) to be sure you will fit everything in.  You need to type 'n <enter> p <enter> 1 <enter> +600M <enter>'.

Edit: The CD-ROM is a post formatted size of 628Mb.

Command (m for help): a
Partition number (1-4): 1

--- The 'a' command sets the partition as bootable.  This would mean that you don't have to use syslinux.  You need to type 'a <enter> 1 <enter>'.

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 3
First cylinder (393-1024, default 393):
Using default value 393
Last cylinder or +size or +sizeM or +sizeK (393-1024, default 1024):
Using default value 1024

--- Here, I have created another partition to fill the rest of the drive.  This will be the /home partition. You need to type 'n <enter> p <enter> 3 <enter> <enter> <enter>'.

Command (m for help): p

Disk /dev/sdb: 131 MB, 131072000 bytes
5 heads, 50 sectors/track, 1024 cylinders
Units = cylinders of 250 * 512 = 128000 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         392       48975   83  Linux
/dev/sdb3             393        1024       79000   83  Linux

--- The 'p' command will show you what the partition allocation on the disk looks like.  The * next to /dev/sdb1 means that the partition is bootable.  The block numbers on yours will be different to mine - remember this is only a 130Mb stick.

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 0: Success.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
andrew@sam:~$

--- Finally, use 'w' to write the changes to the disk.


```

> 
In step #2 :
What is the correct Ubuntu terminal command to format the stick as vfat?

As I said before, I would suggest ext2 for the root partition, and then vfat for the home partition.  There is no reason why you should need to access any of the root info from within Windows, so you might as well hide it from it.

```

andrew@sam:~$ sudo mke2fs /dev/sdb1
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
7840 inodes, 31348 blocks
1567 blocks (5.00%) reserved for the super user
First data block=1
4 block groups
8192 blocks per group, 8192 fragments per group
1960 inodes per group
Superblock backups stored on blocks:
        8193, 24577

Writing inode tables: done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 21 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
andrew@sam:~$


```

And then you need to make the dos/fat16 file system for hda3 (or hdb3 in my case) which is going to be your home partiton:

```

andrew@sam:~$ sudo mkdosfs /dev/sdb3
mkdosfs 2.11 (12 Mar 2005)
andrew@sam:~$

```

> In step #3 :
What should my mkdir and mount commands be?

To mount the 600Mb partition, use the following commands:

```

sudo mkdir /mnt/liveusb

```
That will create a directory for you. Then you need to mount it:
```

sudo mount /dev/sdb1 /mnt/liveusb

``` 

You can then copy the contents of the CD-ROM over to the USB stick.  I'd do it in filemanager - I am not sure of the cp code - sudo cp /mnt/cdrom/* /mnt/liveusb/ maybe?

I hope this help!

Don't forget though, you will need to change the grub file to point to the USB stick partitions rather than the CDROM partitions.

---

### Post by andrewsawyer on 2005-11-01
[QUOTE=DaBruGo]There must be a file somewhere that is pointing the startup procedures to the CD-ROM.

Anyone got any ideas?
[/QUOTE]

Sorry - you've got me on that one!  I assumed it might be a little harder than just copying over.  I'll have a search about the net though and see if I can come up with anything.

---

### Post by andrewsawyer on 2005-11-01
Actually, having had a look at the CD, have you changed the isolinux.cfg file in the isolinux directory to point to the casper directory on the USB stick rather than the CD?

I've printed the contents of the file below:

```
DEFAULT /install/vmlinuz
APPEND  casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop vga=normal initrd=/install/initrd.gz ramdisk_size=1048576 root=/dev/rd/0 rw --
LABEL live
  kernel /install/vmlinuz
  append  casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop vga=normal initrd=/install/initrd.gz ramdisk_size=1048576 root=/dev/rd/0 rw --
LABEL live-expert
  kernel /install/vmlinuz
  append  DEBCONF_PRIORITY=low casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop vga=normal initrd=/install/initrd.gz ramdisk_size=1048576 root=/dev/rd/0 rw --
LABEL rescue
  kernel /install/vmlinuz
  append  rescue/enable=true vga=normal initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
LABEL memtest
  kernel /install/mt86plus
  append -
DISPLAY isolinux.txt
TIMEOUT 0
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

Fingers crossed!

---

### Post by DaBruGo on 2005-11-01
hi andrew,

I had made some changes to the isolinux.cfg file (which I renamed to syslinux.cfg) to get rid of the error I mentioned in post #23.

Here is what my syslinux.cfg file (on the USB flash stick) currently looks like ...

====================
DEFAULT vmlinuz
APPEND  casper/enable=true casper-udeb/snapshot/backing-file=casper/filesystem.cloop vga=normal initrd=initrd.gz ramdisk_size=1048576 root=/dev/rd/0 rw --
LABEL live
kernel vmlinuz
append  casper/enable=true casper-udeb/snapshot/backing-file=casper/filesystem.cloop vga=normal initrd=initrd.gz ramdisk_size=1048576 root=/dev/rd/0 rw --
LABEL live-expert
kernel vmlinuz
append  DEBCONF_PRIORITY=low casper/enable=true casper-udeb/snapshot/backing-file=casper/filesystem.cloop vga=normal initrd=initrd.gz ramdisk_size=1048576 root=/dev/rd/0 rw --
LABEL rescue
kernel vmlinuz
append  rescue/enable=true vga=normal initrd=initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
LABEL memtest
kernel mt86plus
append -
DISPLAY isolinux.txt
TIMEOUT 0
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt
====================

First, I copied all the files from the Live CD over to the USB flash stick. 

Then, I copied all the files from the (/install) and (/isolinux) directories on the USB flash stick into it's root directory (/).

Then, I changed the isolinux.cfg filename to syslinux.cfg after reading a post somewhere about it.

Then, I edited the syslinux.cfg file to remove the line pointers to the cdrom (/cdrom). And I took out the leading (/) on the vmlinuz lines. That is when it let me into the setup screens until the furball happened on mounting and detecting the CD-ROM.

If we can figure a way to have the setup program look on the USB flash stick, instead of the cdrom, I believe this will work!


DAVE

---

### Post by dspp on 2005-11-02
Is there a future official version of Ubuntu that will run off a USB drive? I run Damn Small Linux <http://www.damnsmalllinux.org/> successfully off of a USB drive, but I am still getting used to fluxbox.

---

### Post by DaBruGo on 2005-11-02
[QUOTE=dspp]Is there a future official version of Ubuntu that will run off a USB drive? I run Damn Small Linux <http://www.damnsmalllinux.org/> successfully off of a USB drive, but I am still getting used to fluxbox.[/QUOTE]


dspp,

Rumor has it (at least after reading some posts) that there will be some type of USB support coming for the USB flash sticks.

I too have tinkered with DSL some (have it on a 256MB Lexar jumpdrive), but Ubuntu on a USB stick would be awesome.

If you're looking to install Ubuntu on an external USB hard drive (not a memory stick), I have an outline to do that in thread 80811 (SUCCESS - Breezy loaded on external USB drive)


DAVE

---

### Post by andrewsawyer on 2005-11-02
DaBruGo,

I guess this is going to be a teadious process of going through the files and trying to find a pointer to the CD-Rom drive.  I don't suppose the person who wrote the setup section of the LiveCD is following this thread!?!?

Just a thought - could we use the setup (as far as determining which drivers to load etc) off another distro, or maybe mash them together?  I'm pretty sure I read somewhere that the Ubuntu LiveCD is based on Knoppix.  Unfortunately I wouldn't know where to start with this, other than perhaps trial and error.

Would anyone else know anything about this?

Andy

---

### Post by HokeyFry on 2005-11-04
wouldnt it be fairly simple to put ubuntu on a flash drive? wouldnt it be as simple as copying the files from the live cd to an empty flash drive and making sure wat ever computer that you are trying to load it on can boot from the usb drive? or is it more comlicated than that?

---

### Post by andrewsawyer on 2005-11-04
Hi HokeyFry,

Unfortunately it is a little more complicated than that.  If you have a read through this thread, you will see that the files on the LiveCD expect that they are being run off a CD, so when they call other files, they look for them on the CD - not on a USB disk.

I'm not sure if this is the case for 1 file, 2, 10 or 100 files, however in order to get Ubuntu to run as a LiveUSB, we need to edit each file that points to a CD, and point it to a USB device instead.

I hope this answers your question, and also quickly tells everyone else where we are upto with this project.  If anyone knows of any files that need to be changed - eg. isolinux.cfg, can they please post here so that we can quickly track them all down?

Many thanks,

Andy

---

### Post by DaBruGo on 2005-11-08
Hi folks,

I am wondering if we can adapt a HOWTO article I found to get our LIVE CD running completely from an USB flash stick.

It is an article on running knoppix from a USB memory stick...
 
[http/rz-obrian.rz.uni-karlsruhe.de/knoppix-usb/](http/rz-obrian.rz.uni-karlsruhe.de/knoppix-usb/)

In this article there is a line that I noticed while skimming through it. Just maybe it would work for us if we can figure out where to place it in the scheme of things.

Here is the line ...

mount -t vfat /dev/sda1 /cdrom

I wonder if I can add some sort of mount command to the syslinux.cfg file ( in message #28 ) to direct the setup to look at the USB stick for files and not the CDROM  ( in message #24 )?

Anyone familiar with mount commands? I really believe if we can get over this hurdle that we can get the LIVE CD contents loaded and running from a USB stick.



Any suggestions,
DAVE

---

### Post by andrewsawyer on 2005-11-08
> mount -t vfat /dev/sda1 /cdrom

Cunning.  I like it.

This is of course assuming that you have formatted the USB drive as Fat16.  Would it be mounted at /cdrom or /mnt/cdrom?

This is also probably a realy dumb question.  I can't seem to format a USB stick partially ext2 and partially vfat.  Well, I can but Windows won't recognise the vfat partition as formatted, and then when I format it, Linux won't mount it anymore.  Would this have something to do with the order in which the partitions are created?  Does Microsoft need the vfat to be the first partition on the disk?

I know this might seem to be off topic, however I would like to get a LiveUSB working with an ext2 partition for /root and /home with just a small spare vfat partition for swapping between the device and Windows.

I don't suppose the LiveCD has an /etc/fstab we could use to mount from does it?  Then we could just map the sda1 partition to the cdrom mount point, and everything in the syslinux.cfg file could remain pointed at the CD.

I don't have the CD on me at the mo, so if someone could post to advise if there is a fstab file we could just change, that would be great.

---

### Post by DaBruGo on 2005-11-08
STATUS UPDATE ...

The mount command seems to partially work! (At least there is some progress to this insanity ... he he ) 

When the setup coughed at the "detect and mount cdrom" step, I went to the "execute a shell" option and typed in the mount command in question ( mount -t vfat /dev/sda1 /cdrom ).

Then, I exited from the shell and chose the "detect and mount cdrom" option again and ... it pulled some files from the USB stick!

It then did the "detect network hardware" and "configure the network" steps without a hitch.

But, then it trys to detect hardware again and coughs up a furball at the "enter pre-installed session" step. And, I noticed in another window there was a "preparing for live session" installation bar that was froze at 8%.

So ... it seems that when it detects the hardware again, it somehow loses the mount setting that we create in the shell window.

I also noticed something else during these tests. If you go straight to the "execute a shell" option at the very beginning ( before the cdrom detection phase ) and then do a directory listing command ... there is no /cdrom directory there.

But after the setup runs the "detect and mount cdrom" step (for the first time) and hacks up a furball, it creates the /cdrom directory.

I noticed this when I got curious and pulled up a directory listing before typing the mount command from the shell.



DAVE

---

### Post by andrewsawyer on 2005-11-08
Hey Dave,

The /cdrom isn't actually a directory.  It is just a link.  You might find that it has created the /mnt/cdrom or /media/cdrom instead?

Likewise, if there is an fstab file in the /etc directory, you could enter the details in here and it would save you exiting to the shell to type it in manually.

Just a thought anyway.

---

### Post by DaBruGo on 2005-11-11
[QUOTE=andrewsawyer]Hey Dave,

The /cdrom isn't actually a directory.  It is just a link.  You might find that it has created the /mnt/cdrom or /media/cdrom instead?

Likewise, if there is an fstab file in the /etc directory, you could enter the details in here and it would save you exiting to the shell to type it in manually.

Just a thought anyway.[/QUOTE]

Andrew,


I will see if I can find where the LIVE CD places the /etc/fstab file. I know where it is located after a full install, but couldn't find it when trying the mount command from a shell prompt with the LIVE CD.


DAVE

---

### Post by DaBruGo on 2005-11-11
[QUOTE=andrewsawyer]Hey Dave,

The /cdrom isn't actually a directory.  It is just a link.  You might find that it has created the /mnt/cdrom or /media/cdrom instead?

Likewise, if there is an fstab file in the /etc directory, you could enter the details in here and it would save you exiting to the shell to type it in manually.

Just a thought anyway.[/QUOTE]

Andrew,

I had another quick thought. Maybe what we need is some kind of link command instead of messing with the /etc/fstab file ... something kind of like an environment variable that redirects everything properly to the usb stick.

or

I wonder if there is a parameter we can enter at the boot menu of the LIVE CD to redirect any CD access requests to the USB stick?

or

Is there a parameter we can add to the syslinux.cfg file to redirect any CD access requests to the USB stick?

---

### Post by andrewsawyer on 2005-11-14
Ok,

It is possible: [http://www.tomshardware.com/howto/20051110/index.html](http://www.tomshardware.com/howto/20051110/index.html)

By the look of it, the Ubuntu H2 is sold as a miniCD and a 3Gb micro-drive.

You install from the miniCD onto the micro-drive and then boot from the micro-drive via USB from then on.

Now, I have just this morning received my 8Gb LaCie Carte Orange USB disk, so at last I can help out with getting us all up and running.  I have partitioned as below:

```
andrew@sam:~$ sudo fdisk /dev/sda
Password:

Command (m for help): p

Disk /dev/sda: 8000 MB, 8000004096 bytes
247 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         132     1010693   83  Linux
/dev/sda2   *         133         235      788671   83  Linux
/dev/sda3             236        1020     6010745   83  Linux

Command (m for help):
```

The sda1 is formatted as vfat (although I will need to stick it into a Windows machine and reformat it to get access from within Windows).

The sda2 is my bootable partition - 800Mb formatted as ext2 (same as on my laptop)

The sda3 takes up the rest of the disk.  I want to use it as the /home partition for the LiveUSB when it is all up and running.  I am already using it as my /home for my laptop/desktop - it should save me having to keep syncing them.

Now, unfortunately when I copied the contents of the LiveCD over to ext2 and rebooted, I got a message:

```
No Operating System
```

Does anyone know why this might be?  It is set as the bootable partition.

Also, I was having a look at the file system on the CD.  It uses a cloop file which it mounts as the file structure.  I assume the details of where to look for things (the problem we have been having with is seeking the cdrom) is in here.  Would it just be a matter of opening up the cloop file (there is a program in Synaptic) and editing it before saving it back down again?

DAVE - if you know why I'm having the problem getting the OS to load, can you please let me know?  Then once I am at the same stage as you I can start messing around with the cloop file.

Cheers,

Andy

---

### Post by DaBruGo on 2005-11-14
andy,

I remembered that I saw something like this startup message below when playing around with our little project.

"root file system" is a ram disk
"hard disk file system" is mounted on /target

I am wondering how to access either of these to see what files are being used for the cdrom detection ... and if there is a way to edit them.



DAVE

---

### Post by DaBruGo on 2005-11-14
andy,

What is the name of the cloop editor you mentioned was available in synaptic? 



DAVE

---

### Post by andrewsawyer on 2005-11-15
Hey Dave,

The cloop editor can be downloaded by 'sudo apt-get install cloop-utils'.  It basically comprises of a cloop extractor and a cloop compressor - you use the first to extract the filesystem.cloop file out to a 2Gb file called extracted_fs.  You can then mount this with the loop command.  You then obviously do it the other way around to compress back to the filesystem.cloop.

For more info, there is a whole section on it in the Wiki link you provided about halfway through this thread.

When you mount the extracted_fs file, you will see that it is essentially an entire system file structure.  From what I can gather (and I don't claim to be an expert) the syslinux section is just used to mount the filesystem.cloop file.  There is then a /boot/grub, /etc/{fstab,mtab} and whatnot inside the cloop file.

Now unfortunately I can't tell whether the problem you are experiencing when booting is something pre or post mounting of the cloop, as I can't get mine to do a damn thing!

I have a nice new cloop file (with thunderbird, w32codecs, gftp etc etc and apt-get updated as of 14th Nov), however I can't do a thing with it.

I gave up on the ext2 partition, as I was having no luck, and decided you try your route with the vfat partition.

So, 
```
sudo su
fdisk /dev/sda
d #delete all partitions
n #create new partition
p #primary
1 #primary 1
<enter> #enter through until partition is created
a #set bootable
1 #choose boot partition
p #check everything looks ok
w #write file structure

#then

mkfs.vfat /dev/sda1

syslinux /dev/sda1

mount /dev/sda1 /mnt/usbdisk
```

All is well so far.  And yes - I've done it that many times I know what to type by heart!

So now, in theory I have one vfat partition which is set as bootable in fdisk and also has syslinux installed on it.

Now come the problems.  The cd filesystem has three symlinks on it.  The first called 'ubuntu' in the root directory, and two others - stable and unstable in the dist directory.  Try as I might, I can't get them to copy over to the vfat partition on the usb disk.  When the disk was formatted as ext2 it was no problem, however vfat doesn't seem to like them.

Did you have this problem?

So I copy over everything else.  I move the contents of /isolinux and /install into the root directory, and rename isolinux.cfg to syslinux.cfg.  I also remove any reference to the cdrom from it, and also make sure it points to the correct files that are now in the root partition.

But when I try to reboot, I get nothing.  No error - nothing.  Just a little flashing line in the very top right of the screen.

Dave, please - tell me what I've done wrong!

Patiently waiting...

Andy

---

### Post by andrewsawyer on 2005-11-15
With reference to Post 41

> "root file system" is a ram disk
"hard disk file system" is mounted on /target

By the look of that message, your system is getting mounted.  All good!  This means that (for you anyway) syslinux is doing its job.  It is mounting the file filesystem.cloop, which is kinda like how you mount an iso without burning it.

It will however be read-only.  Any changes you make will be wiped out as soon as you umount the cloop file.  To make permanent changes you have to uncompress the filesystem.cloop file, chroot into it (assuming you're not just going to be text-editing), and do whatever you want.  You then need to recompress the filesystem and stick it back in the correct directory on the USB, or if making a LiveCD, you have to then make the iso, and then write it back out onto another disk.

This is a bit of a shame really, as I originally thought that once you had your liveUSB up and running, you could apt-get update ever now and again and just keep is as a normal system - what with a USB disk being writable and all.  Unfortunately that's not the case.  At least not if you want to use the cloop system.

---

### Post by DaBruGo on 2005-11-15
andy,

Here is a summary of what I have been doing ...

FIRST, I formatted my USB flash stick in Windows XP (as FAT) using the &#8220;HP USB Disk Storage Format Tool&#8221; that I downloaded.

SECOND, I copied over the Live CD contents (using Windows XP) to my USB flash stick.

THIRD, I copied (using Windows XP) all the files from the (/install) and (/isolinux) directories on the USB flash stick into it's root directory (/).

* note: Make sure these directories are copied over before you try to install syslinux (in FIFTH step)

* note: Delete the /install and /isolinux directories once you copy their contents to the root directory.

FOURTH, I changed the isolinux.cfg filename to syslinux.cfg after reading a post somewhere about it.

FIFTH, (From within Windows XP) I installed syslinux to the USB stick. I believe my command was something like syslinux &#8211;s e:  ( or whatever my drive letter was for the USB stick).

* note: If this is done correctly, syslinux places a file called ldlinux.sys in the root folder of the USB stick.

Here&#8217;s an excerpt from where I got the syslinux install info ...
[syslinux.zytor.com/faq.php](syslinux.zytor.com/faq.php)
> 
In order to create a bootable Linux floppy using SYSLINUX, prepare a normal MS-DOS formatted floppy. Copy one or more Linux kernel files to it, then execute the DOS command: 
syslinux [-s] a: 
(or whichever drive letter is appropriate; the [] meaning -s is optional) 

If you're running in a Win95/98/ME DOS box, you should execute the command lock a: first. If you're running in a WinNT/2K DOS box, you will probably get a dialog box about not getting exclusive access and with Abort/Retry/Ignore buttons; people have reported that selecting "Ignore" makes the command complete correctly. 

Under Linux, execute the command: 
syslinux [-s] [-o offset] /dev/fd0 
(or, again, whichever device is the correct one.) 

This will alter the boot sector on the disk and copy a file named LDLINUX.SYS into its root directory. 

The -s option, if given, will install a "safe, slow and stupid" version of SYSLINUX. This version may work on some very buggy BIOSes on which SYSLINUX would otherwise fail. If you find a machine on which the -soption is required to make it boot reliably, please send as much info about your machine as you can, and include the failure mode. 

The -o option is used with a disk image file and specifies the byte offset of the filesystem image in the file. 

On boot time, by default, the kernel will be loaded from the image named LINUX on the boot floppy. This default can be changed, see the section on the SYSLINUX config file. 

If the Shift or Alt keys are held down during boot, or the Caps or Scroll locks are set, SYSLINUX will display a LILO-style "boot:" prompt. The user can then type a kernel file name followed by any kernel parameters. The SYSLINUX loader does not need to know about the kernel file in advance; all that is required is that it is a file located in the root directory on the disk.


SIXTH, I edited the syslinux.cfg file to remove the line pointers to the cdrom (/cdrom). And I took out the leading (/) on the vmlinuz lines. That is when it let me into the setup screens.

=== syslinux.cfg file ===
DEFAULT vmlinuz
APPEND casper/enable=true casper-udeb/snapshot/backing-file=casper/filesystem.cloop vga=normal initrd=initrd.gz ramdisk_size=1048576 root=/dev/rd/0 rw --
LABEL live
kernel vmlinuz
append casper/enable=true casper-udeb/snapshot/backing-file=casper/filesystem.cloop vga=normal initrd=initrd.gz ramdisk_size=1048576 root=/dev/rd/0 rw --
LABEL live-expert
kernel vmlinuz
append DEBCONF_PRIORITY=low casper/enable=true casper-udeb/snapshot/backing-file=casper/filesystem.cloop vga=normal initrd=initrd.gz ramdisk_size=1048576 root=/dev/rd/0 rw --
LABEL rescue
kernel vmlinuz
append rescue/enable=true vga=normal initrd=initrd.gz ramdisk_size=16384 root=/dev/rd/0 rw --
LABEL memtest
kernel mt86plus
append -
DISPLAY isolinux.txt
TIMEOUT 0
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt
=== end ===

SEVENTH, When the setup coughed at the "detect and mount cdrom" step, I went to the "execute a shell" option and typed in the mount command in question ( mount -t vfat /dev/sda1 /cdrom ). Then, I exited from the shell and chose the "detect and mount cdrom" option again and it pulled some files from the USB stick. It then did the "detect network hardware" and "configure the network" steps without a hitch ... before furballing again at the "preinstalled system" step
 
Thats my steps thus far ...


I have been doing all my edits and modifications exclusively in Windows XP. I never tried any of these steps in my full install of Ubuntu Breezy.

 As far as the problems you are having ... I am wondering if there is some issue on the maximum disk size when using just FAT. Or, if there is some similar size issue when using syslinux. (I think that FAT has a 1GB limitation?)

Just for giggles, you might try making just a 900 meg FAT partition on your usb unit (preferably using Windows XP or an MSDOS boot disk) and leave the rest free space. Then see if the steps above actually give you a setup screen. That might tell us if this is a disk size issue.

I am just guessing here, but I would definitely like to get you up and running with me on this insanity!



DAVE

---

### Post by DaBruGo on 2005-11-15
andy,

Here is something else I found out about syslinux ...

> 
{ Can I Use SYSLINUX on a Hard Drive? } 
SYSLINUX can boot from a FAT12 or FAT16 filesystem partition on a hard disk (FAT32, introduced in Windows 95 OSR-2, is not supported, however.) The installation procedure is identical to the procedure for installing it on a floppy, and should work under either DOS or Linux. To boot from a partition, SYSLINUX needs to be launched from a Master Boot Record or another boot loader, just like DOS itself would. 

Under DOS, you can install a standard simple MBR on the primary hard disk by running the command: 
FDISK /MBR 
Then use the FDISK command to mark the appropriate partition active. 

A simple MBR, roughly on par with the one installed by DOS (but unencumbered), is included in the SYSLINUX distribution 
{ What Bugs are Still in SYSLINUX? } 
SYSLINUX is unsafe to use on any filesystem that extends past cylinder 1024. This is a fundamental limitation of the standard BIOS API. 

SYSLINUX will not work (and will refuse to install) on filesystems with a cluster size of more than 16K (typically means a filesystem of more than 1 GB.)


The website I mentioned in the previous post also offers extlinux which works like syslinux but on an ext2 or ext3 file system.



DAVE

---

### Post by andrewsawyer on 2005-11-16
Thanks for that!

I had a brainwave last night!  Unfortunately my idea didn't work, however it might help someone think up something similar...

I downloaded DSL Linux, and burnt the iso onto a cd.  I then booted it, and used its own program to create a LiveUSB of DSL.

Note: You have to use the HDD-USB rather than the ZIP-USB due to partition issues.

Now I have a bootable USB stick with all the software etc needed to mount a .cloop file (which both Ubuntu and DSL use).

I then copied the filesystem.cloop file over to the USB into the KNOPPIX directory, and renamed it to KNOPPIX (no extension) to replace the one that was currently there.

I also edited the syslinux.cfg file on the USB stick so that the ramdisk size was the same as that in the Ubuntu LiveCD's isolinux.cfg file (ramdisk_size=1048576).

I figured that I could use everything else off the already working DSL USB disk, but just run the Ubuntu filesystem rather than the DSL one.

Well needless to say, it didn't work.  I booted, and it all started up ok.  I hit enter and the USB stick light was flashing away like mad.  It showed the following screen:

```
Scanning for USB devices... Done.
 Accessing DSL image at /dev/sda1...
/linuxrc: /usr/bin/gawk: not found
/linuxrc: /usr/bin/gawk: not found
 Copying DSL image to ramdisk... Please be patient.
```

As I say, it was doing whatever it was doing for about 10-15 minutes, and then it just stopped.  No error or anything.  I just sat there.  It wasn't frozen, but there were no lights on either the hard disk or USB disk flashing.  It was almost as if it had extracted the cloop file, and it had the whole lot sitting in memory, but it just didn't know what to do with it.

It's unfortunate, however I hope this might make someone think 'ah, but what if you did it *this* way...'.  I figure that the whole ubuntu system is stored within the cloop file.  It doesn't matter what you use to get the cloop file mounted - so long as you do!

It also tells me that if we do ever get it to work, it will take about 10-15 minutes to mount the cloop file, plus then booting time everytime you turn on the pc.  Ouch!

Now, it has occurred to me that DSL runs on a 2.4 kernel (which I think Warty did so - and therefore the Ubuntu H2 device as well).  Maybe this has something to do with it?

There may also be some extra settings within the KNOPPIX (DSL cloop) file that help it to mount.  I will have a look into this at the weekend.

Anyway, although this test was a failure, I hope it might help us to think outside the box and get this all sorted!

Cheers,

Andy

---

### Post by andrewsawyer on 2005-11-16
Update:

I removed the 'toram' option and tried again.

This time I get a whole lot more scrolling - too much to try and copy into gedit by hand while watching on the other computer!

It didn't take half as long either.

Problems I can recall...

1. version 2.86 booting, but then..
udev requires a kernel >= 2.6.8, not started

2. Mounting file system - fail

3. Syncing with ubuntu server for clock update - fail (although I'm running it wifi and none of the settings will be in)

After this, the screen then goes blank, and the computer freezes - probably due to the fact that the kernel didn't load!

I am considering this a great success!  Ok, it didn't work, but...

We know that we need to sort out udev.  Is it just me reading the version numbers wrong, or is 2.86 already greater than 2.6.8?  If we can fix this, then onto the next step.

Possibly the filesystem didn't mount because of this?  And I would say that the sync to the Ubuntu time server failed just due to the wifi.

Could be that we are almost there!

I don't like to think too far ahead, but how hard would it be to edit the orginal DSL bootup process to replace the DSL logo, and all references with something more in line with Ubuntu?

Andy

UPDATE:

```
andrew@sam:~$ sudo mount extracted_fs /mnt -o loop
andrew@sam:~$ cd /mnt
andrew@sam:/mnt$ ls
bin   dev  home    initrd.img  media  opt   root  srv  tmp  var
boot  etc  initrd  lib         mnt    proc  sbin  sys  usr  vmlinuz
andrew@sam:/mnt$ cd /
andrew@sam:/$ sudo mount -t proc proc mnt/proc
andrew@sam:/$ sudo mount -t sysfs sysfs mnt/sys
andrew@sam:/$ sudo chroot mnt/ /bin/sh
sh-3.00# echo "Kernel version is" $(dpkg-query -W --showformat '${Version}' linux-image-$(uname -r))
No packages found matching linux-image-2.6.12-9-686.
Kernel version is
sh-3.00# ls
bin   dev  home    initrd.img  media  opt   root  srv  tmp  var
boot  etc  initrd  lib         mnt    proc  sbin  sys  usr  vmlinuz
sh-3.00# uname -r
2.6.12-9-686
sh-3.00#

```

The above is me mounting the extracted filesystem out of the cloop compressed file, and chrooting into it.  I have tried to display the kernel version, however it didn't seem to like it.  Can someone tell me why?  

If I just do a basic 'uname -r' command, then it comes back with the kernel that I'm running - not the one that is on the LiveCD that I've just chrooted into.

FYI - the file sitting in /boot in the extracted filesystem is vmlinuz-2.6.12-9-386.  2.6.13 is available (I think), but this is the latest stable version.  I am therefore going on the basis that it is the kernel sitting on the USB stick (the DSL one) that is causing the problems, as it is quite old and the udev from Ubuntu doesn't like it.

I'll keep working, and let you all know how it goes!

---

### Post by andrewsawyer on 2005-11-16
Sorry to keep posting!

Right, been at this for hours, and still no further on.

However, I have had time to think about the possible options.

This is the contents of my USB stick:

```
andrew@sam:/media/usbdisk$ ls
backup.tar.gz  boot.msg~  f3          initrd.gz    linux24       syslinux.cfg~
boot.cat       f2         f3~         KNOPPIX      logo.16
boot.msg       f2~        german.kbd  ldlinux.sys  syslinux.cfg
andrew@sam:/media/usbdisk$
```

backup.tar.gz - this is the 'home' directory etc that DSL would write to to save your data
boot.cat - this is a boot file
boot.msg - this loads the splash image plus a couple of lines of info
f2 - more info on boot options
f3 - as above
initrd.gz - this has something to do with the kernel I think?
KNOPPIX - a directory containing the cloop file
german.kbd - not 100% on this one, but I don't really want to delete it!
linux24 - the kernel.  This is a 2.4 kernel, which udev doesn't like
logo.16 - this is splash.rle from the LiveCD just renamed
ldlinux.sys - boot file made by syslinux
syslinux.cfg - a file to pass data to syslinux to tell it what to do
files ending ~ are just backups I think.


Now, I figure (assuming we want to try this way!) 3 main options:

1. Delete out linux24, which is the kernel that DSL uses to boot and mount the cloop, and replace it with a new file - linux26, which contains a kernel newer than 2.6.8.  If we do this, we will also have to add the USB modules to the new kernel so that it can boot.  I'm figuring we could probably use the kernel off the CD, but it would have to have the modules added.  We would also need to replace the initrd.gz file, as the two seem to be linked.  Another possibility would be to find another distro with a LiveUSB option and a 2.6 kernel and use this as the base rather than DSL.  Gentoo maybe?

2. Downgrade the udev file in the cloop file.  I'm not sure how easy this would be, as it could cause issues with all sorts of stuff.  We might even end up having to knock back Breezy to a 2.4 kernel which I'm sure would cause endless problems.

3. Use Warty for the LiveUSB.  It works for Ubuntu H2, and given that it is running on a 2.4 kernel is should fix all the problems I'm having.

I would be tempted to go with either number 1 or maybe 3, however I get the feeling that the first one will end up with us compiling a kernel, which is a pain, and the other option (3) will leave us with an out of data distro.  I don't really like the idea of option 2, but I've posted it anyway as it is an option.

As far as the boot up stuff goes, when I got sick of the system crashing out, I decided to have a play with the cosmetics of the start up.  I've replaced the DSL image with the Ubuntu one that you get while it is booting, and I've also changed some of the wording from DSL over to Ubuntu LiveUSB.  There are some things that I haven't changed yet, coz I just can't find them, however I think these are based in the initrd.gz, and so when we change that the wording can be altered anyway.

Well, just gone midnight here now, and I've been up since 5am.  Let me know what you think of this idea anyway.  Do you feel it is worth going down this line, or would the majority of people prefer to try and stick with the 'full ubuntu' thing, just using the LiveCD to source files from?

Cheers,

Andy

---

### Post by DaBruGo on 2005-11-16
Andy,


I just noticed something on the LIVE CD, when I was browsing through it in Windows XP.

There is a file in the /install directory called ...

**initrd.list**

I believe this file seems to list all the stuff that the initial ramdisk tries to run at startup. Some of the files that it lists, I have seen in other directories on the LIVE CD that may be related to our current startup issues.

They are all inside of directory ...

**/pool/main/c**

The files are ...

[B]cdrom-checker
cdrom-detect
cdrom-retriever
load-cdrom (inside the cdrom-retriever directory)[/B]

A description of what these are is located in the file ...

**/dists/breezy/main/debian-installer/binary-i386/Packages**


I am wondering if we can edit the initrd.list file to get a little further along in our quest.



DAVE

---

### Post by andrewsawyer on 2005-11-17
Yes - I was looking for this - I thought it was inside a .gz file - shows what I know!

This is the file that is used to load the modules into the kernel on boot - we need to add the USB modules, and make sure that the system pauses long enough to load them before it tries to access any more data.

I will have a look at this tonight and let you know what I find.

Andy

edit: Sorry - I got it wrong.  I *think* the file you are talking about is literally just a list of what goes on inside the initrd.gz (the .gz file I mentioned).  If you extract this file, and mount it you will find a kind of mini file structure, and a load of files.  But (and again I only *think*) if you want to change something in this, it is quite a bit more complicated than just changing the list order in that file.  I think it needs the kernel recompiling and all that.  I've downloaded a 2.6.8 vanilla kernel (the minimum for udev), and I will have a go at compiling that with the usb stuff in it later on this evening (or maybe tomorrow)

---

### Post by DaBruGo on 2005-11-17
[QUOTE=andrewsawyer]Yes - I was looking for this - I thought it was inside a .gz file - shows what I know!

This is the file that is used to load the modules into the kernel on boot - we need to add the USB modules, and make sure that the system pauses long enough to load them before it tries to access any more data.

I will have a look at this tonight and let you know what I find.

Andy

edit: Sorry - I got it wrong.  I *think* the file you are talking about is literally just a list of what goes on inside the initrd.gz (the .gz file I mentioned).  If you extract this file, and mount it you will find a kind of mini file structure, and a load of files.  But (and again I only *think*) if you want to change something in this, it is quite a bit more complicated than just changing the list order in that file.  I think it needs the kernel recompiling and all that.  I've downloaded a 2.6.8 vanilla kernel (the minimum for udev), and I will have a go at compiling that with the usb stuff in it later on this evening (or maybe tomorrow)[/QUOTE]

Andy,

There is also a Packages.gz file in there ...

/dists/breezy/main/debian-installer/binary-i386/Packages.gz :D 



DAVE

---

### Post by henk.1955 on 2005-11-18
Hi.
i have a DELL Latitude D800 and a Kingstone DataTraveler 1G

I copied files outoff the livecd 5.10 iso to the fat32 formated USBmemorystick.
installed grub bootloader.

Then when i boot every thing goes well, untill the "cdrom not found".

I select the shell and type:

mount /dev/sda1 /cdrom -t vfat.

exit the shell and select the scan for cdrom.
then the hardware configuration continues. and in the end i get the GNOME desktop.
everything works a it should. it runs faster then from a cdrw.

so the drivers you need to boot and run the livecd from a usbmemorystick are allready in the initrd.

No how do we change the cdrom scan script to include scans for /dev/hda? and /dev/sda?

---

### Post by DaBruGo on 2005-11-18
[QUOTE=henk.1955]Hi.
i have a DELL Latitude D800 and a Kingstone DataTraveler 1G

I copied files outoff the livecd 5.10 iso to the fat32 formated USBmemorystick.
installed grub bootloader.

Then when i boot every thing goes well, untill the "cdrom not found".

I select the shell and type:

mount /dev/sda1 /cdrom -t vfat.

exit the shell and select the scan for cdrom.
then the hardware configuration continues. and in the end i get the GNOME desktop.
everything works a it should. it runs faster then from a cdrw.

so the drivers you need to boot and run the livecd from a usbmemorystick are allready in the initrd.

No how do we change the cdrom scan script to include scans for /dev/hda? and /dev/sda?[/QUOTE]

henk.1955,


If what you are telling us works ...you are our HERO !!! =D> [-o<


Could you elaborate some on this ... 

Did you copy the .iso file itself to the stick or did you copy the file/directory structure to the stick?

What was your install method for GRUB?

Were there any special edits you had to do for any files?


(I almost jumped over my desk when I saw your post! \\:D/ )



DAVE

---

### Post by henk.1955 on 2005-11-18
content of usbmemorystick

drwxr-xr-x  13 root root   4096 1970-01-01 00:00 .
drwxr-xr-x  21 root root   1024 2005-11-18 20:47 ..
drwxr-xr-x   3 root root   4096 2005-11-09 12:36 boot
dr-xr-xr-x   2 root root   4096 2005-11-17 13:50 casper
dr-xr-xr-x   5 root root   4096 2005-11-17 13:50 disctree
dr-xr-xr-x   2 root root   4096 2005-11-17 13:47 .disk
dr-xr-xr-x   3 root root   4096 2005-11-17 13:50 dists
dr-xr-xr-x   3 root root   4096 2005-11-17 13:50 doc
dr-xr-xr-x   2 root root   4096 2005-11-18 16:57 install
dr-xr-xr-x   2 root root   4096 2005-11-17 13:50 isolinux
-rwxr-xr-x   1 root root  41611 2005-11-17 13:52 md5sum.txt
dr-xr-xr-x   2 root root   4096 2005-11-17 13:50 pics
dr-xr-xr-x   4 root root   4096 2005-11-17 13:50 pool
dr-xr-xr-x   2 root root   4096 2005-11-17 13:50 preseed
-rwxr-xr-x   1 root root    223 2005-11-17 13:52 README.diskdefines
-rwxr-xr-x   1 root root 303056 2005-11-17 13:52 start.bmp

i think some more folders and files can be deleted (but that for later)

content of /boot/grub/menu.lst

# Default to first menu entry
default 0

# Allow 30 seconds before booting default
timeout=30

# Use prettier colors
color green/black light-green/black

title UBUNTU Live
root (hd0,0)
kernel /install/vmlinuz casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop vga=792  ramdisk_size=1048576 root=/dev/rd/0 rw debian-installer/locale=nl_NL kbd-chooser/method=us --
initrd /install/initrd.gz

i am now playing with /var/lib/dpkg/info/cdrom-detect.postinst
lines 66-77
```


    if [ "$mounted" = "1" ]; then
        break
    fi

# added henk.1955 begin
mount /dev/sda1 /cdrom -t vfat
mounted = "1"
break
# added henk.1955 end

    # If a device was detected but the mount failed, ask for the CD.

```

hope this fools the cdrom detecting at startup

---

### Post by andrewsawyer on 2005-11-18
Hey Henk.1955 - Congrats!

I will have to try it out asap!

I've noticed you don't have the Ubuntu link 'directory' on the CD.  Did you copy the iso over from within Windows or from Ubuntu?

Cheers,

Andy

---

### Post by DaBruGo on 2005-11-18
Henk.1955,

Help me figure this out please. I am having problems getting the grub bootloader loaded on my USB stick (1GB). I keep getting this GRUB install error while running the LIVE CD.

The error is "/dev/mapper/casper-snapshot does not have any corresponding BIOS drive" ... although I can browse the stick and everything.

What steps did you use to get your stick going. What operating system were you using to accomplish all of this (Windows XP or Ubuntu?) Did you do everything in Ubuntu (formatting, copying, GRUB installation etc)?

Any help would be greatly appreciated

---

### Post by henk.1955 on 2005-11-18
i used winxp to format the memorystick fat32
i used slackware ( a diy livecd ) to mount the iso to a tmp mountpoint, copy the the files and folders to the stick, and the grub-install.

the Ubuntu link is NOT on the fat32 formated stick.

---

### Post by DaBruGo on 2005-11-18
[QUOTE=henk.1955]i used winxp to format the memorystick fat32
i used slackware ( a diy livecd ) to mount the iso to a tmp mountpoint, copy the the files and folders to the stick, and the grub-install.

the Ubuntu link is NOT on the fat32 formated stick.[/QUOTE]

henk,

I have a slax live (5.0.6) CD. Will that work for what I need to do?

Also, could you share with me what the mount command was that you used as well as what the grub-install command was?

Much thanks :D



DAVE

---

### Post by andrewsawyer on 2005-11-18
Hiya,

correct me if I'm wrong, but don't you have to be chroot'd into the USB to be able to install Grub?  If so, how did you do this?

I know how to do it as standard, but with none of the file structure in place, how did you so it?

Did you temporarily create /proc and /sys on the USB stick?

I tried this, however when I then tried to chroot into the environment, I got this:
```
sudo chroot mnt/ /bin/sh
chroot: cannot run command '/bin/sh': No such file or directory
```

I checked, and there is no sh (or bash) file in the /bin directory on the cd.  I renamed the /mnt/bin to /mnt/bin-1 and copied over the /bin from my own system.  I still got the same error when trying to chroot into the USB disk though.

Can you please run through how you got Grub installed on the USB stick, coz as I said, I'm not aware of any way to do it unless you are actually already in the system (chroot'd for example).

Cheers,

Andy

---

### Post by DaBruGo on 2005-11-19
Andy,

I have got everything done but the grub install.
Here are the steps I have taken ...

(1 ) Boot into the full version of Ubuntu on my external USB drive

(2 ) Connected my usb stick (after the desktop was up and running)
NOTE: I formatted it as FAT32 from within Windows XP but it shows up as vfat in Ubuntu (system menu /administration/disks)

(3 ) Inserted my iso CD into the cdrom drive
NOTE: this is just a CD that I copied the ISO file onto from within Windows XP. There's just one file on the CD called ubuntu-5.10-live-i386.iso

(4 ) When the file browser window opened, I right clicked on the iso filename and chose ... 

"Open with Archive Manager" ... 
"Edit /Select All" ...  
"Edit /Extract" ... 
"Extract in folder" (I  picked the mount point where my USB stick was located,  /media/GS-MEDIA) ... 
* All files ... 
* Re-create folders ... 
* Overwrite existing files ... 
"Extract"

It successfully copied the contents of the iso file (the files and directories) onto my USB stick.

Now if we can get GRUB loaded, we can test this puppy out.



DAVE

---

### Post by andrewsawyer on 2005-11-19
Hey Dave,

I'm at the same stage as you.  I just need to get Grub installed.  However, as you will have read from my previous posts, I have no idea how to do this.  I had a look at the Gentoo site, however even doing it the Gentoo way (as in from scratch) you still have to chroot into the new system before emerging grub.

Unfortunately, I've yet to find a way to chroot into an environment that essentially only contains a couple of files.

I guess there is the option of sticking something like DSL or Knoppix onto the USB disk, and then chrooting into that to install Grub, and then deleting out all the other files and copying the Ubuntu ones over in their place, but I would like to hear how henk.1955 did it first!

---

### Post by DaBruGo on 2005-11-19
Andy,

henk.1955 is our hero !!!!!!!!!!!!!!!!

I got it to work!
It works !!
It really works !!!

Here are my steps ...

** (1 )** Format the stick in Windows XP as FAT32.

**  (2 )** Boot into the FULL VERSION of Ubuntu on my external USB drive
 
**  (3 )** Connect my usb stick (after the Ubuntu desktop is up and running)

* NOTE*: I formatted it as FAT32 from within Windows XP but it shows up as vfat in Ubuntu (system/ administration/ disks)
 
**  (4 )** Insert my iso CD into the cdrom drive

* NOTE*: this is just a CD that I copied the ISO file onto from within Windows XP. There's just one file on the CD called ubuntu-5.10-live-i386.iso
 
**  (5 )** When the file browser window opens, I right click on the iso filename and choose ... 
 
 "Open with Archive Manager" ... 
 "Edit /Select All" ...  
 "Edit /Extract" ... 
 "Extract in folder" (I  picked the mount point where my USB stick was located, which was   /media/GS-MEDIA) ... 
 * All files ... 
 * Re-create folders ... 
 * Overwrite existing files ... 
 "Extract"
 
 It successfully copies the contents of the iso file (directories and files) onto my USB stick.

** (6 )** Open up a terminal window (Applications/ Accessories/ Terminal)

sudo su --  (this puts my terminal in temporary sudo mode)
mount /dev/sdb1 /mnt     (be sure to use your correct /dev setting for the USB stick)
grub-install --root-directory=/mnt /dev/sdb
umount /mnt
exit      (this exits sudo su mode)
exit      (this closes terminal window)

** (7 )** The grub install command creates a device.map file under /boot/grub on the USB stick.

Here is my device map file ...
> 
(fd0)    /dev/fd0
(hd0)    /dev/hda
(hd1)    /dev/sda
(hd2)    /dev/sdb
 
** (8 )** I create a menu.lst file under /boot/grub on the USB stick ...
> 
# Default to first menu entry
default saved

# Allow 30 seconds before booting default
timeout=30

# Use prettier colors
color cyan/blue white/blue

title UBUNTU Live USB (henk.1955 version)
root (hd0,0)
kernel /install/vmlinuz casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop vga=792 ramdisk_size=1048576 root=/dev/rd/0 rw debian-installer/locale=en_US kbd-chooser/method=us --
initrd /install/initrd.gz
savedefault
 
** (9 )** When I restart the PC and boot from the USB stick ( setting it to boot first in BIOS ), I enter the "mount /dev/sda1 /cdrom -t vfat" command in a shell window when the "detect cdrom" step fails. I then go back and rerun the "detect cdrom" step again and it keeps on loading everything and comes to the Ubuntu desktop!

It was such a beautiful thing (sniffle).  

And, it all just works beautifully for me ... and noticeably faster than the LIVE CD just like henk.1955 said. \\:D/



DAVE

---

### Post by henk.1955 on 2005-11-19
If you change the first lines in /var/lib/dpkg/info/cdrom-detect.postinst file in initrd to:
```
. /usr/share/debconf/confmodule
#set -x

log() {
    logger -t cdrom-detect "$@"
}

fail () {
    log "CDROM-detect failed."
    exit 1
}

# Is a cdrom already mounted?  If so, assume it's the right one..
mount | grep -q ^/dev/cdroms/ && exit 0

sleep 10
mkdir /cdrom 2>/dev/null || true
mount /dev/sda1 /cdrom -t vfat

if [ -e /cdrom/.disk/info ] ; then
   CDNAME=`cat /cdrom/.disk/info`
   log "Detected CD '$CDNAME'"
   exit 0
fi

```
it mounts the usbstick;
then you dont have to go into the shell at boottime
it will go from boot up into the gnome desktop withhout having to type anything.

next step:
try to find a way to get presitent home and a way save settings.

---

### Post by DaBruGo on 2005-11-19
[quote=henk.1955]If you change the first lines in /var/lib/dpkg/info/cdrom-detect.postinst file in initrd to:
```
. /usr/share/debconf/confmodule
#set -x

log() {
    logger -t cdrom-detect "$@"
}

fail () {
    log "CDROM-detect failed."
    exit 1
}

# Is a cdrom already mounted?  If so, assume it's the right one..
mount | grep -q ^/dev/cdroms/ && exit 0

sleep 10
mkdir /cdrom 2>/dev/null || true
mount /dev/sda1 /cdrom -t vfat

if [ -e /cdrom/.disk/info ] ; then
   CDNAME=`cat /cdrom/.disk/info`
   log "Detected CD '$CDNAME'"
   exit 0
fi

``` it mounts the usbstick;
then you dont have to go into the shell at boottime
it will go from boot up into the gnome desktop withhout having to type anything.

next step:
try to find a way to get presitent home and a way save settings.[/quote] 
henk.1955,

How did you get the file extracted out and then put back in again after edits? I don't know enough about editing those type of files yet to perform that task with any level of confidence.

As far as saving settings, can we partition part of the USB stick and edit some config files to point the home/save settings to that partition?



DAVE

---

### Post by andrewsawyer on 2005-11-20
Hey guys,

I'm having real issues with this.

I have done as said, and all works.  I get to the point that the cdrom isn't recognised, and drop out to the ash shell.  I type:
```
mount /dev/sda1 /cdrom -t vfat
```
and then chek inside the /cdrom directory.  Everything is mounted.  I then type exit and get back to the menu where I try and check the cdrom again.  However I then get the same message.  I go back to the ash shell and the system has unmounted /cdrom.

I've tried in both vfat and ext2, on both sda1 and sda2 partitions (installing on each in both ways.  I've also tried mounting, exiting back to the menu, and then going back into the shell.  The system is still mounted correctly.  It seems that when it checks for the cdrom, it is unmounting the partition I just mounted.

Any idea why this might be?

---

### Post by DaBruGo on 2005-11-22
Henk,

I got it going!

I did a google search for "edit initrd.gz" and found a forum with instructions on how to edit the initrd file within a gz archive. Here is what I found ...

> 
 I give you only the commands written in a terminal ... 
 
cd /tmp 
mkdir work 
cd work 
cp /.../.../initrd.gz . # Here you have to add the correct path 
gunzip initrd.gz 
mkdir initrd.dir/ 
mount -o loop,rw initrd initrd.dir 
cd initrd.dir 
# Now you can remove or add stuff, change scripts or something else 
cd /tmp/work 
umount initrd.dir 
rm -R initrd.dir 
gzip -n9 initrd 
cp initrd.gz /.../.../... # Here you have to add the correct path 
cd .. 
rm -R /tmp/work 
 
That was my way and it worked fine for me. 
 
I did the edits by booting up my full version of ubuntu and popping in the usb stick when the desktop came up. I then did the above commands in the terminal window ... and it worked!

I will post a more complete guide for our Live USB setup soon ... for everyone's benefit.

Thanks for all your help!



DAVE

---

### Post by andrewsawyer on 2005-11-22
Hey guys,

Still no luck I'm afraid :(

I have altered the initrd.gz file (and then remounted and gone in and checked to be sure).  It's all correct.  However for some reason, my computer is still not liking it.  It gets to the detecting CD-Rom section, loads the floppy driver stuff and all that, and then fails saying it can't find the CD-Rom.

Going into the command prompt and checking what is in /cdrom reveals it is empty.  I can then mount sda1 as /cdrom, and check - it mounts correctly.  However then when I go back to the system to get it to check for the cdrom again, it fails.

It seems that the system is unmounting whatever is on /cdrom and then trying to mount the normal cdrom.  When it can't find it, it dies.

I'm using a laptop, so I will try it at work tomorrow - you never know, I might have more luck then!

I'll post to let you know.

Andy

Edit: I've just tried on another laptop.  The above was on a Compaq Presario R3000.  My other laptop is an Acer Travelmate C110.  The reason I hadn't tried it before was that it doesn't like booting from USB - I can't even get Knoppix to run on it - although I now thing that may be down to syslinux rather than booting from USB.

The Acer booted to the same point as the Compaq.  It then gave an error saying that it couldn't find the driver for the Cdrom, and asked me if I wanted to get the driver from the floppy (which I don't have).  Looking in the command prompt though showed me that the USB cloop system was indeed mounted inside the /cdrom directory - the Acer doesn't unmount it like the Compaq seems to.  I still can't get it to work on either, but it does tell us that different computers are working through the same files in a different way - strange.

Anyway, I'll leave that thought with you.  I'll check it out on the work desktop tomorrow.

---

### Post by joshpelkey on 2005-11-22
Here is a wiki for installing ubuntu from a USB drive.  I did this myself and I have Ubuntu on my IBM X40 :)

[http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive]("http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive")

---

### Post by DaBruGo on 2005-11-22
[QUOTE=joshpelkey]Here is a wiki for installing ubuntu from a USB drive.  I did this myself and I have Ubuntu on my IBM X40 :)

[http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive]("http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive")[/QUOTE]

joshpelkey,

Good job! Thanks for sharing the info.

I don't know if you noticed from our previous posts, but we've got the LIVE CD ( and NOT the full version ) actually running on a ( 1GB ) USB memory stick by following the installation steps previously mentioned. And, believe it or not, the Ubuntu desktop loads fairly quickly from a memory stick (at least I think it does). 8)

We are working at duplicating the way they have setup Ubuntu on a flash drive currently available that has Ubuntu pre-installed ... the Ubuntu H2. 

I bet your wiki would also work if you put the install CD on a USB memory stick? I have a thread on doing a full install to an external USB hard drive ... [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

Let me know what you think?


Glad you could drop in on us!



DAVE

---

### Post by DaBruGo on 2005-11-22
Andy,

In your bios, where is the CDROM located in the scheme of things.

My bios is setup to ...

boot floppy, then
boot cdrom, then
boot memory stick

... in that order.

Do you think something funny might be going on in your bios during bootup? I can't think of anything else, at the moment, that might be happening.

I'd really like to see you get this thing going too!

---

### Post by joshpelkey on 2005-11-22
:o I should have read the thread before posting!  My wiki was just for installing Ubuntu **from** USB **to** your computer [that way you don't need a CD...good for people w/o an optical drive].  I didnt realize you guys were talking about the LIVE version.  I've never tried that one with Ubuntu, but I have done it with knoppix.  Though now that I've thought about it, I might try to do it :)

---

### Post by DaBruGo on 2005-11-22
[QUOTE=joshpelkey]:o I should have read the thread before posting!  My wiki was just for installing Ubuntu **from** USB **to** your computer [that way you don't need a CD...good for people w/o an optical drive].  I didnt realize you guys were talking about the LIVE version.  I've never tried that one with Ubuntu, but I have done it with knoppix.  Though now that I've thought about it, I might try to do it :)[/QUOTE]

joshpelkey,

Dude, that's quite alright.
Sharing knowledge is always a good thing.

I bet if you glance at message #63 in here and use the full version iso file for step 4 ... you just might be able to install the full version from a USB memory stick (probably with some tweaking here and there).

Let us know how it works.

By the way, do you have a good link for doing the Live Knoppix thing.
I just might try that out too! (Isn't Knoppix sorta from Debian?)



DAVE

---

### Post by joshpelkey on 2005-11-22
It took me a while to find it again, but this is the site I got my info from for running Knoppix on USB.  I found this to be the simplest yet well-explained article on the subject.  

[http://www.pcworld.idg.com.au/index.php/id;1104862437;fp;512;fpid;1783981662]("http://www.pcworld.idg.com.au/index.php/id;1104862437;fp;512;fpid;1783981662")

I had one problem running it on an IBM X40; when trying to boot it would fail or hang up after attempting to detect scsi devices.  For whatever reason this was bypassed by typing expert in the console before booting.

And yes, Knoppix is based on debian.  It runs KDE though...bleeehh :)

Oh and this assumes you have the knoppix files already [on a cd to copy over to your usb drive...not just the iso]  and also the utility syslinux [this is in the ubuntu repositories].

---

### Post by andrewsawyer on 2005-11-22
[QUOTE=DaBruGo]Andy,

In your bios, where is the CDROM located in the scheme of things.

My bios is setup to ...

boot floppy, then
boot cdrom, then
boot memory stick

... in that order.

Do you think something funny might be going on in your bios during bootup? I can't think of anything else, at the moment, that might be happening.

I'd really like to see you get this thing going too![/QUOTE]


Heya,

I have the boot order set as follows:

ATAPI CD-ROM Drive
-Hard Drive
---         USB Seagate 8Gb (my USB 'stick')
---         My main HDD
Floppy Diskette Drive (not that I actually have one anyway)
Network adaptor


As you can see, the bios picks up the USB as a hard drive.  It does this on both laptops.

Anyway, I'll see how I do at work today - fingers crossed it's just a laptop thing!

---

### Post by DaBruGo on 2005-11-22
[QUOTE=andrewsawyer]Heya,

I have the boot order set as follows:

ATAPI CD-ROM Drive
-Hard Drive
---         USB Seagate 8Gb (my USB 'stick')
---         My main HDD
Floppy Diskette Drive (not that I actually have one anyway)
Network adaptor


As you can see, the bios picks up the USB as a hard drive.  It does this on both laptops.

Anyway, I'll see how I do at work today - fingers crossed it's just a laptop thing![/QUOTE]

Andy,

Have you tried putting your 8GB stick just below the CD but above the other drives and then trying it out?



DAVE

---

### Post by DaBruGo on 2005-11-22
> **joshpelkey]It took me a while to find it again, but this is the site I got my info from for running Knoppix on USB.  I found this to be the simplest yet well-explained article on the subject.  

[URL="http://www.pcworld.idg.com.au/index.php/id said:**
> http://www.pcworld.idg.com.au/index.php/id;1104862437;fp;512;fpid;1783981662[/URL]

I had one problem running it on an IBM X40; when trying to boot it would fail or hang up after attempting to detect scsi devices.  For whatever reason this was bypassed by typing expert in the console before booting.

And yes, Knoppix is based on debian.  It runs KDE though...bleeehh :)

Oh and this assumes you have the knoppix files already [on a cd to copy over to your usb drive...not just the iso]  and also the utility syslinux [this is in the ubuntu repositories].

joshpelkey,

Thanks for digging that up for me.

I wonder if you can load Knoppix as a server install and then setup gnome from the repositories ( instead of using kde )?



DAVE

---

### Post by DaBruGo on 2005-11-22
Andy,

Are there some kind of temp files that you can flush in Ubuntu, just in case something is saving a setting that it shouldn't?



DAVE

---

### Post by andrewsawyer on 2005-11-23
Update:

Still no luck.

I set the system at work to boot from USB-HDD and got the following error (in about the same place as normal):

[CENTER]Detect and Mount CD-Rom
Non-Ubuntu CD-Rom detected[/CENTER]
The CD-Rom drive contains a non-Ubuntu CD.
Please insert the Ubuntu CD to continue with installation

I checked the system, and the cloop file was mounted correctly in /cdrom.

Can I just check - when you are changing the initrd file, are you just doing it to the one in the /install directory, or are you editing the one in the cloop file as well?

Cheers,

Andy

---

### Post by andrewsawyer on 2005-11-23
> Andy,

Have you tried putting your 8GB stick just below the CD but above the other drives and then trying it out?



DAVE

It is. It's just the way I have written it I think.  The USB drive appears as a hard disk, and so is in the hard disk sub section along with my standard hard disk.

> Andy,

Are there some kind of temp files that you can flush in Ubuntu, just in case something is saving a setting that it shouldn't?



DAVE

Not that I'm aware of.  It's just a copy of the CD-Rom with the initrd.gz file in the /install directory altered.  I'm trying it with a standard (read unaltered) filesystem.cloop file, so there should be no strange settings in this.

It's all very strange.  It could have something to do with the bios, but I don't know much about all that - plus it's not like you can go altering peoples bios' just to boot you system temporarily on them!

Do you guys have any other pc's you could try your disks on?  Make sure they work on a number of different systems?

Andy

---

### Post by DaBruGo on 2005-11-23
[QUOTE=andrewsawyer]Update:

Can I just check - when you are changing the initrd file, are you just doing it to the one in the /install directory, or are you editing the one in the cloop file as well?

Cheers,

Andy[/QUOTE]

Andy,

What I did was copy the files to the USB stick and then I went in and edited the initrd file ( the one inside initrd.gz ) in the /install directory. I didn't mess with the cloop file at all.



DAVE

---

### Post by teuteuguy on 2005-12-07
Hi there,

i've tried your great solution for installing the live cd on an external drive.

Problem is it doesnt work.
when booting, I get the grub word displaying continuesly on the screen .... for ever

However there a just a few changes I made in the install process.
I burned the Live CD iso on a cd. (burned the iso, rather than burn the actual file on a cd)

Put the cd in the drive and from windows, copied all the files accross to the root of my usb2 20gb external hard drive.

Restarted the computer and booted up from the live cd.
And did the install procedure you describe .... mount usb drive, install grub, and create a menu.lst file.

Any ideas on how I can fix this up ?

Thanks

Tim

---

### Post by pomalin on 2005-12-11
Many thanks for this solution, I use it to build a live usb and it work very well. I made my own howto with your, and the henk.155 modification, I also add the use of mybuntu script by michael moore, and to finish burn a 6M cdr to enable usb boot on computers that cannot boot from usb.

All work. Perhaps someday my howto will be in the "customization tips and tricks" thread.
;)  

Again, and again, thank you.:D

---

### Post by DaBruGo on 2005-12-15
[QUOTE=pomalin]Many thanks for this solution, I use it to build a live usb and it work very well. I made my own howto with your, and the henk.155 modification, I also add the use of mybuntu script by michael moore, and to finish burn a 6M cdr to enable usb boot on computers that cannot boot from usb.

All work. Perhaps someday my howto will be in the "customization tips and tricks" thread.
;)  

Again, and again, thank you.:D[/QUOTE]

pomalin,

Thanks for your comments.
Could you post what your howto steps are for us to look at.
I would be very interested in looking at them.


Thanks again for the kind words,
DAVE

---

### Post by pomalin on 2005-12-17
Here. > [http://ubuntuforums.org/showpost.php?p=561550&postcount=1](http://ubuntuforums.org/showpost.php?p=561550&postcount=1)

Like I say in the end of the post, I've made a iso of the original live cd with just an upgrade, and the initrd modified, but to upload it, I have to have time, because my transfert rate is slow. But I will to that. Sure.

---

### Post by andrewsawyer on 2006-01-29
Heya,

It's been a while since I've posted, however (and I don't know what I was doing wrong before), I have now got my LiveUSB working.

I've been looking into ways to get a persistent home drive, and I found this:

[https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence)

I assume this works with the live CD (although I've not tried myself), however I did notice that it directs to the Dapper download.  Can anyone confirm this works with a standard liveCD?

The way the LiveUSB is made however you don't get the chance to pass details to the kernel on boot as it uses GRUB rather than syslinux.  I've tried editing the menu.lst, however this doesn't seem to work.

Had anyone else come across this wiki and managed to get it working in this manner?  If you could post to let me know, it would be much appreciated.

Andy

Edit: Looks like this might be a new function in Dapper only.  Hitting F4 on boot in Breezy doesn't give the same menu, and typing 'persistent' as a 'switch' on boot doesn't seem to work either :-(

On the plus side, we might be able to get a LiveUSB with persistent /home when Dapper gets here (unless someone want's to download the iso for Dapper Alpha and give it a go in advance).

---

### Post by andrewsawyer on 2006-01-29
I've been looking into this in some more detail. It looks like when they went from Breezy to Dapper, they also changed the LiveCD quite considerably - e.g. they will be using SquashFS rather than cloop.  I don't know much about the differences, however it looks as though SquashFS has something to do with OnionFS, which is what Knoppix uses.  Knoppix allows a persistent /home, and it is the OnionFS that allows this to be possible.  It seems that it just isn't possible to do this with a cloop file.

So, I've downloaded the iso for the Dapper LiveCD.  I'm running Dapper (fully dist-updated as of half an hour ago) on my test machine anyway.  What I am going to see if I can do tonight is to get this all sorted, start to finish on Dapper, fully updated as of tonight.

Hopefully I'll be able to open up the filesystem in a similar way to the cloop file (but I've not checked yet), and I'll update it all to current.  I'm also figuring on scrapping Evolution and replacing it with Thunderbird. I'll also download all the free sound/movie codecs, skype, enigmail and whatever else I can think of.  If it's easy and it's not too late by the time I work out how to do it, I might have a play with some of the logos etc and change them to Usbuntu.

I'll (fingers crossed) get the persistent /home partition working too.  I'll do all of this on a standard 1Gb USB stick, and then dd it into an iso.  I'll stick that up on a server (assuming I'm allowed to make edits like that and make them available - can someone please confirm???), and you should be able to just grab it and install the iso to USB.

Looking at that it might take longer than tonight, but I'll keep you all posted.  If I get it done, I'll also write up a full how-to for it, so you can copy rather than download my iso.

Andy

---

### Post by andrewsawyer on 2006-01-29
Hmmm... it's changed quite a bit.

2:15am and I'm gonna call it a night.  It's currently giving me a: 

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)

This is due to me messing around withthe initrd.gz file and trying to sort out the mount to it thinks that sda1 is cdrom.  More about that in a mo.  This is what I have done so far:

Format the 1Gb USB disk
```

#go Super User for the following
andrew@samantha:~$ sudo bash 
Password:

#fdisk your USB stick (you may need to change the device location - sdb/sdc etc)
root@samantha:~# fdisk /dev/sda 

#delete all partitions on the drive
Command (m for help): d
Partition number (1-4): 1

Command (m for help): d
Selected partition 2

#create a new primary, 700Mb partition, and set it as bootable and vfat
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-1024, default 1):
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-1024, default 1024): +700M

Command (m for help): a
Partition number (1-4): 1

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): b
Changed system type of partition 1 to b (W95 FAT32)

#create another new partition - this one is for the /home directory. I have made it ext2
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (691-1024, default 691):
Using default value 691
Last cylinder or +size or +sizeM or +sizeK (691-1024, default 1024):
Using default value 1024

#check it all looks good and save the partition info
Command (m for help): p

Disk /dev/sda: 1040 MB, 1040187392 bytes
32 heads, 62 sectors/track, 1024 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         690      684449    b  W95 FAT32
/dev/sda2             691        1024      331328   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.

WARNING: If you have created or modified any DOS 6.x
partitions, please see the fdisk manual page for additional
information.
Syncing disks.
root@samantha:~#
```

I then rebooted my machine so the kernel was using the new tables.

Then format the to new partitions.
```

#again use Super User
andrew@samantha:~$ sudo bash
Password:

#unmount the drives (they may not be mounted, but worth checking)
root@samantha:~# umount /dev/sda1
root@samantha:~# umount /dev/sda2
umount: /dev/sda2: not mounted

#format the /home partition, and give it a label of 'casper-cow'. This is what Dapper looks for when setting persistence
root@samantha:~# mkfs.ext2 -b 4096 -L casper-cow /dev/sda2
mke2fs 1.38 (30-Jun-2005)
Filesystem label=casper-cow
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
82848 inodes, 82832 blocks
4141 blocks (5.00%) reserved for the super user
First data block=0
3 block groups
32768 blocks per group, 32768 fragments per group
27616 inodes per group
Superblock backups stored on blocks:
        32768

Writing inode tables: done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 39 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

#I did the same for the first partition, but did it as vfat and called it 'usbuntu'.
root@samantha:~# mkfs.vfat -n usbuntu /dev/sda1
mkfs.vfat 2.11 (12 Mar 2005)
root@samantha:~#
```

Next, I downloaded the iso from the net to my desktop.  The location is: [http://cdimage.ubuntu.com/releases/dapper/flight-3/](http://cdimage.ubuntu.com/releases/dapper/flight-3/)

Then mount the main USB partition as /mnt.
```

#mount the main partition on the USB disk as /mnt
root@samantha:~# mount /dev/sda1 /mnt
```

Open the iso in Archive Manager, and extract the directories .disk - preseed to /mnt - don't include the programs directory or any files below that.  These all relate to Windows, and so just take up space.

Then install grub
```

#next, install grub
root@samantha:~# grub-install --root-directory=/mnt /dev/sdb
Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/sdb
root@samantha:~#
```

Now that was simple enough. No difference from what you guys were doing in Breezy with the exception of the second partition.  I then made the menu.lst in /mnt/boot/grub.  Because the LiveCD is now using SquashFS rather than cloop, I got a bit stuck.  Would someone be able to give me a hand with this?

The isolinux.cfg is below:

```
DEFAULT /install/vmlinuz
GFXBOOT bootlogo
APPEND  boot=casper initrd=/install/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL live
  menu label Run preinstalled ^live system
  kernel /install/vmlinuz
  append  boot=casper initrd=/install/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL check
  menu label Check CD for defects
  kernel /install/vmlinuz
  append  boot=casper integrity-check initrd=/install/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL rescue
  menu label ^Rescue a broken system
  kernel /install/vmlinuz
  append  rescue/enable=true initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

And my attempt at a menu.lst is here:

```
# Default to first menu entry
default saved

# Allow 3 seconds before booting default
timeout=3

# Use prettier colors
color cyan/blue white/blue

title USBUNTU
root (hd0,0)

kernel /install/vmlinuz boot=casper ramdisk_size=1048576 looptype=squashfs loop=/casper/filesystem.squashfs cdroot=/dev/sda1 root=/dev/ram rw quiet splash persistent
initrd=/install/initrd.gz
savedefault
```

I also had a go at editing the initrd.gz file, however it now uses cpio, so you can't just mount it with the loop command:

```

#copy your initrd.gz file to the /tmp directory and unzip it
cd /tmp
mkdir work
cd work
cp /media/usbuntu/install/initrd.gz .
gunzip initrd.gz

```

This command will extract out the file structure of the initrd file:
```
cpio -i --make-directories --verbose < initrd

```

In this, the things I changed are listed below:

/scripts/casper-bottom/15autologin
change username from ubuntu to one more personal

/scripts/casper-bottom/25configure_init
change username to same as above

/lib/casper/shutdown
change end echo to read more USB like rather than cd
Question: might have to remove the eject line, as we are using USB not CD.  Can someone please confirm?

/scripts/casper
replace everything above mountpoint=/cdrom with:
```

	#!/bin/sh

	# set -e
	sleep 10
	mkdir /cdrom 2>/dev/null || true
	mount /dev/sda1 /cdrom -t vfat

```

I think the above code is where I have gone wrong and caused the kernel panic.  If someone could have a look at this and see what it ACTUALLY should be like, it'd be appreciated!

Edit: For anyone that wants to help, but hasn't the time to download the isoand go through all this, I have attached a copy of the casper shell script file (the one that I assume should have the line setting /dev/sda as /cdrom in it).  If you could tell me where you think it should go, or post a copy of an edited version, I'll be happy to try it and let you know how it goes!  I've given it a .txt extension to allow upload.

Then use cpio to remake the initrd file:
```

find /tmp/work -print | cpio -o > initrd
```

And finally compress it, and move it back to it's correct location:
```
gzip -n9 initrd
cp initrd.gz /media/usbuntu/install/initrd.gz
cd ..
rm -R /tmp/work 

```

Well, After that it all kinda died on me.  I will load Grub, and before I messed with the initrd it would do the splash screen too.  Problem is that it has changed so much you can't just exit out to the shell anymore to mount the usb as the cdrom.

I'll keep going at it tomorrow night, but if anyone else can offer some advice to save me some time, it'd be much appreciated.

Andy

---

### Post by andrewsawyer on 2006-01-30
Ok, it's not my editing of the file that's wrong - I don't think it even gets that far.  It is my menu.lst file that is messing it up.

At the moment, I have the following in it:

```

kernel /install/vmlinuz
boot /casper
initrd /install/initrd.gz
root=/dev/ram
savedefault
```

This looks to load the kernel and the initial ram disk, however when it comes to setting the root I am getting the kernel panic.  I have tried a number of root= combinations:

```
root=(hd0,0)
root=/dev/sda1
root=/dev/ram0
root=/dev/rd/0
```

However nothing seems to work.  I have noted that if you stick 'root=(hd0,0)' up above the kernel line it does get recognised as ext2, so it's not like it's corrupted or anything.

The exact detail of the error is:

```

VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
```

At which point the machine locks up and I have to physically turn it off and on again to have another go.  It's getting quite frustrating as I'm sure you can imagine!

Any help would be much appreciated.

Andy

---

### Post by DaBruGo on 2006-02-22
I found a few articles by doing a google search on "portable ubuntu" that I wanted to share with everyone.

[http://www.desktoplinux.com/news/NS7418276314.html]("http://www.desktoplinux.com/news/NS7418276314.html")

[http://www.zinside.com/index.php?main_page=product_info&products_id=76&language=en]("http://www.zinside.com/index.php?main_page=product_info&products_id=76&language=en")


DAVE

---

### Post by brucetan on 2006-02-24
Hi Aaron,

Do you have a step by step installation guide for ubuntu on the USB Hard Drive?  I am keen to do it with my 40GB USB disk while retaining my built-in HD for WinXP.

Apprecaite your help.

---

### Post by DaBruGo on 2006-02-26
[QUOTE=brucetan]Hi Aaron,

Do you have a step by step installation guide for ubuntu on the USB Hard Drive?  I am keen to do it with my 40GB USB disk while retaining my built-in HD for WinXP.

Apprecaite your help.[/QUOTE]

brucetan,

I have an install guide you may be interested in. See the link in my signature lines below.


DAVE

---

### Post by DaBruGo on 2006-02-27
[QUOTE=andrewsawyer]Ok, it's not my editing of the file that's wrong - I don't think it even gets that far.  It is my menu.lst file that is messing it up.

At the moment, I have the following in it:

```

kernel /install/vmlinuz
boot /casper
initrd /install/initrd.gz
root=/dev/ram
savedefault
```

This looks to load the kernel and the initial ram disk, however when it comes to setting the root I am getting the kernel panic.  I have tried a number of root= combinations:

```
root=(hd0,0)
root=/dev/sda1
root=/dev/ram0
root=/dev/rd/0
```

[/QUOTE]

andy,

Have you tried this yet ...

root=/dev/rd/0 rw 


Still here,
DAVE

---

### Post by andrewsawyer on 2006-02-27
I haven't yet, however I'll have to give it a go soon.  I must say, I've put it on a bit of a back burner for the mo, as I've been side tracked with Xgl.

---

### Post by Brocco on 2006-03-31
I couldn't get grub to work so I found an easier method using syslinux.  You still need to do the "mount flash drive as cdrom" trick after booting, but you don't need to partition the disk nor create a menu.lst file.

The USB flash disk shows up on my desktop as /dev/sda.

```
# be root for a while
sudo bash

# install mkdosfs & syslinux tools
aptitude install dosfstools syslinux

# mount the live CD ISO
mkdir /mnt/loop
mount -o loop ubuntu-5.10-live-i386.iso /mnt/loop

# format the USB flash disk
mkdosfs -I /dev/sda

# install the syslinux bootloader on the disk
syslinux /dev/sda

# mount the newly formatted disk
mount /dev/sda /media/usbdisk
cd /media/usbdisk

# copy the contents of the live CD
cp -r /mnt/loop/. .

# unlike isolinux, syslinux likes to operate in the root directory
mv isolinux/* .
mv install/* .

# remove '/install/' from pathnames while generating syslinux.cfg
sed 's/\/install\///' < isolinux.cfg > syslinux.cfg

# unmount the flash disk
umount /media/usbdisk

# unmount the live CD ISO
umount /mnt/loop

# stop being root
exit
```

Cheers,
Brocco

---

### Post by DaBruGo on 2006-04-02
[quote=Brocco]I couldn't get grub to work so I found an easier method using syslinux. You still need to do the "mount flash drive as cdrom" trick after booting, but you don't need to partition the disk nor create a menu.lst file.

The USB flash disk shows up on my desktop as /dev/sda.

```
# be root for a while
sudo bash

# install mkdosfs & syslinux tools
aptitude install dosfstools syslinux

# mount the live CD ISO
mkdir /mnt/loop
mount -o loop ubuntu-5.10-live-i386.iso /mnt/loop

# format the USB flash disk
mkdosfs -I /dev/sda

# install the syslinux bootloader on the disk
syslinux /dev/sda

# mount the newly formatted disk
mount /dev/sda /media/usbdisk
cd /media/usbdisk

# copy the contents of the live CD
cp -r /mnt/loop/. .

# unlike isolinux, syslinux likes to operate in the root directory
mv isolinux/* .
mv install/* .

# remove '/install/' from pathnames while generating syslinux.cfg
sed 's/\/install\///' < isolinux.cfg > syslinux.cfg

# unmount the flash disk
umount /media/usbdisk

# unmount the live CD ISO
umount /mnt/loop

# stop being root
exit
``` 
Cheers,
Brocco[/quote] 
Brocco,

Thanks for posting this info.

I'm wondering if we could use your technique after we create 2 partitions on the usb stick (700 MB for the iso file, and then use the remaining space for a future /home area).

If we can figure out how to point the /home to the second partition on the usb stick, then we would have a live breezy CD on a stick that would remember user settings (persistence)

Any ideas on how we might be able to do this, if it is possible?


DAVE

---

### Post by e-sabbath on 2006-04-04
[QUOTE=henk.1955]Hi.

Then when i boot every thing goes well, untill the "cdrom not found".
I select the shell and type:
mount /dev/sda1 /cdrom -t vfat.

[/QUOTE]

I've got a 1 gig SanDisk Cruzer Mini, and I've followed henk's steps.  Actually, I followed the usbutnu.com steps, but they seem the same. Grub boots... but /dev/sda1 is not visible. Heck, /dev/sda isn't visible, either. Any thoughts?

Booting on a Gateway, where the Cruzer shows up as a hard drive in the BIOS.

---

### Post by sportsfan986 on 2006-05-20
Using the live cd persistence of Dapper:[https://wiki.ubuntu.com/LiveCDPersistence](https://wiki.ubuntu.com/LiveCDPersistence) would we be able to make an equivalent home partition.  I do not know if anyone has got Dapper to work on a USB drive though, and currently do no have a USB thumbdrive to try installing it.  If anyone can get this to work let me know.

---

### Post by andrewsawyer on 2006-05-21
Hiya,

I've been trying to get Dapper to work as a LiveUSB for a while now, with the same thought that we could use the persistence to get a home directory.  Unfortunately as it so different to Breezy I've not been able to get it working yet.  I'll keep trying though!

---

### Post by K0LO on 2006-05-28
**Holy cow! I got it working!**

I now have a 1 GB USB pen drive with the Live Desktop version of Kubuntu Dapper installed and running (version 6.06.rc) ** Including the LiveCDPersistence feature**. I spent so many hours reading up on how to do this that my eyes were starting to bug out. This thread contained the most useful information so I decided to append my solution here. Thank you AndrewSawyer and DaBruGo and everyone else who pointed me in the right direction.

I did this with Kubuntu but suspect that the same procedure will work for Ubuntu; I just haven't tried.

In the end it turned out to be relatively simple. Most of the more detailed articles (Gentoo, Knoppix, etc) give instructions for working on a Linux box. I tried these at first and then in a late night blunder of monumental proportions, I issued the wrong command and almost wrote over the bootsectors in my hard drive when I intended to write to the USB pen drive (sda1 = my hard drive; sdc1 = my pen drive). Thank God that I wasn't root and the command was denied permission! :oops:  At that point I stopped for the night.

The next day I decided that it would be a whole lot easier to do this on a Windows XP box, so I decided to give that a go. My procedure assumes that you're able to run Windows. Modify appropriately if you are more comfortable working in Linux at a command shell.

______________________________________________
Preparation:

A) Download the iso for the latest version of Kubuntu and burn it to a CD. Test the CD to be sure that it will work with your hardware. My IBM laptop worked perfectly, and so did my Dell desktop. Both are very modern machines with SATA drives; the Dell even has SATA RAID and there were no problems at all!

B) Next download a copy of the HP format utility for USB drives from the following web location: [http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html](http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html)
The utility makes it as easy to format USB pen drives as it is to format floppies.

C) Next go to [http://syslinux.zytor.com/iso.php](http://syslinux.zytor.com/iso.php) and download a copy of syslinux-3.11.zip for Windows. Extract the zip file contents and move the extracted folder to your favorite location on your hard drive.
________________________________________________

Procedure:

1. Plug in your USB pen drive and use the HP format utility to format it with a FAT32 filesystem.

2. Using a partitioning tool, create two partitions. The first is formatted with a FAT32 filesystem and needs to be about 650 MB. The second should occupy the remaining free space and should be formatted with the ext2 filesystem and is given the name "casper-rw". Note! Most DOS partitioning tools will create the partition name in uppercase (CASPER-RW). Since Linux is case-sensitive you need to do the formatting of the second partition in Linux. The persistent feature will not work if the partition name is in uppercase. See the Wiki for details. [https://wiki.ubuntu.com/LiveCDPersistence#head-463b3dc931fcb7dc6aa3eedccd8d4f459868bb82](https://wiki.ubuntu.com/LiveCDPersistence#head-463b3dc931fcb7dc6aa3eedccd8d4f459868bb82)

3. Put the Live Desktop CD in your drive and copy over all of the files to the USB pen drive. Make sure that you have Windows set up to show hidden files and to show Protected Operating System files so that you are sure to copy every file.

An alternate way to do this is to mount the iso image file and copy the files that way. I did this with NERO. You might want to do it this way if you don't want to burn a CD.

Open a window to display the contents of the USB drive and do the following steps.

4. Delete the following files from the root directory:
	start.exe
	start.bmp
	start.ini
	autorun.inf


5. Delete the following folders:
	bin
	programs

These files and folders contain Windows software that is not necessary to run Linux. You'll save about 64 MB that way.

6. Move the following files into the root directory of the USB stick:
	isolinux --> all 66 files in this folder, then delete the isolinux folder

7. Copy the following files into the root directory of the USB stick:
	casper/vmlinuz
	casper/initrd.gz
	install/mt86plus

8. Rename the following file:
	isolinux.cfg
	--> change the name to syslinux.cfg

9. Delete the following file:
	isolinux.bin


At this point you should have 8 folders and 71 files on the USB stick.

10. Open **WordPad** and edit the file syslinux.cfg as follows. You need to do two things; first, delete any references to a CD-ROM device and second, make sure that the file references are correct since we moved some files around. In addition, I added another menu choice called "Custom" and made it the default so that when booting up you can just hit Enter to start your customized session. Here is a copy of my edited syslinux.cfg file for the Kubuntu Dapper 6.06.rc Live Desktop disc:

> 
    DEFAULT custom
GFXBOOT bootlogo
APPEND  preseed/file=preseed/kubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --

LABEL custom
  menu label ^Start Kubuntu in persistent mode
  kernel vmlinuz
  append  preseed/file=preseed/kubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL live
  menu label ^Start or install Kubuntu
  kernel vmlinuz
  append  preseed/file=preseed/kubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL xforcevesa
  menu label Start Kubuntu in safe ^graphics mode
  kernel vmlinuz
  append  preseed/file=preseed/kubuntu.seed boot=casper xforcevesa initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt


11. Open a command prompt and change directory to the location of the syslinux folder. For example, if you placed the folder on your desktop then: cd C:\Documents and Settings\(your user name)\Desktop\syslinux-3.11\win32 (by the way you DO know that command prompt has command completion just like in Linux (start entering characters and then press the TAB key to complete the entry). I've been running Windows for 17 years and just discovered that by accident. doh!

12. Next write the bootsectors to the flash drive by entering the following command:
	syslinux -f X:
	--> where X: is replaced by the drive letter of your USB key. Be careful to pick the correct drive letter!

That's it. Now you should have a bootable USB key with the latest version of Kubuntu Dapper on it. My end result is a USB key with 230 files, 43 folders and occupying 608 MB (637,798,407 bytes) on the 1 GB USB key. There's about 367 MB of free space in the second partition for storing custom settings using the LiveCDPersistence feature.

LiveCDPersistence is a really neat feature; give it a try!

---

### Post by sportsfan986 on 2006-05-29
If you don't mind the switch to Xubuntu it would be a simple way to customize your system without having to change the live cd.  it comes with a very minimal amount of applications so you can add whatever apps and games you want easily using the live cd persistence in dapper.  Just a suggestion since the Xubuntu live cd is only 380 megs.

---

### Post by andrewsawyer on 2006-05-29
Hey K0LO

Congratulations!  I've not tried it yet, but when I do I'll go with Ubuntu and also do it fully through Linux.  I'll post the linux procedures on my website, and also a copy here.  Not sure when I'll get around to it though as I am pretty hectic at work at the mo.

Were you aware that if you formatted the USB stick into two partitions and named one of them (you used to name it casper-cow but I think it has changed in more recent versions), then you can have a persistent home directory on the USB disk?  This was my one reason for wanting a Dapper USB stick over a Breezy one.

I have tried to edit the squashfs file, however from memory it is slightly different from the cloop file in Breezy.  It shouldn't be too much trouble to make some amendments if you wanted to say wipe out Evolution and put Thunderbird on, although be aware that if you do any updates, they won't last the reboot - not sure if that wuld apply with a persistent home or not.  Anyone?

Anyway, well done, and thank you for posting!

---

### Post by K0LO on 2006-05-29
Andrew:

I had a chance to try the LiveCDPersistence feature with the USB stick. I reformatted the drive with two partitions and enabled the feature. Wow! It is a really neat feature. I've tweaked settings, installed programs, added files and they are all there upon reboot.

I edited my post #100 to include instructions on how to do this.

I'm really impressed with how well this works.

Mark

---

### Post by Kelley_Jernigan on 2006-06-01
[QUOTE=kalosaurusrex]I haven't tried it on a USB flash drive per se, but I am currently using Ubuntu Breezy on a USB hard drive.  The setup should be the same, so it should work.  A hard drive may be a better choice because it may have a longer life span.  I can boot from Ubuntu USB hard drive from any computer that is USB boot enabled.  and it works great.

Aaron[/QUOTE]

kalosaurusrex,

I am brand new to this and I have an 80 gig USB hard drive and I'd like to do exactly what you are doing (But perhaps with Dapper since it has now been released).

Just how did you do it?

Thanks,

Kelley

---

### Post by leetcharmer on 2006-06-02
I think I read somewhere on the Ubuntu Release Info page from [www.ubuntu.com](www.ubuntu.com) that the ability to install Ubuntu to a USB flash disk has been added to the Ubuntu Alternate Install disk -- can anyone verify this?

---

### Post by leetcharmer on 2006-06-02
> **K0LO]**Holy cow! I got it working!**

I now have a 1 GB USB pen drive with the Live Desktop version of Kubuntu Dapper installed and running (version 6.06.rc) ** Including the LiveCDPersistence feature**. I spent so many hours reading up on how to do this that my eyes were starting to bug out. This thread contained the most useful information so I decided to append my solution here. Thank you AndrewSawyer and DaBruGo and everyone else who pointed me in the right direction.

I did this with Kubuntu but suspect that the same procedure will work for Ubuntu said:**
> http://h18000.www1.hp.com/support/files/serveroptions/us/download/23839.html[/url]
The utility makes it as easy to format USB pen drives as it is to format floppies.

C) Next go to [http://syslinux.zytor.com/iso.php](http://syslinux.zytor.com/iso.php) and download a copy of syslinux-3.11.zip for Windows. Extract the zip file contents and move the extracted folder to your favorite location on your hard drive.
________________________________________________

Procedure:

1. Plug in your USB pen drive and use the HP format utility to format it with a FAT32 filesystem.

2. Using a partitioning tool, create two partitions. The first is formatted with a FAT32 filesystem and needs to be about 650 MB. The second should occupy the remaining free space and should be formatted with the ext2 filesystem and is given the name "casper-rw". Note! Most DOS partitioning tools will create the partition name in uppercase (CASPER-RW). Since Linux is case-sensitive you need to do the formatting of the second partition in Linux. The persistent feature will not work if the partition name is in uppercase. See the Wiki for details. [https://wiki.ubuntu.com/LiveCDPersistence#head-463b3dc931fcb7dc6aa3eedccd8d4f459868bb82](https://wiki.ubuntu.com/LiveCDPersistence#head-463b3dc931fcb7dc6aa3eedccd8d4f459868bb82)

3. Put the Live Desktop CD in your drive and copy over all of the files to the USB pen drive. Make sure that you have Windows set up to show hidden files and to show Protected Operating System files so that you are sure to copy every file.

An alternate way to do this is to mount the iso image file and copy the files that way. I did this with NERO. You might want to do it this way if you don't want to burn a CD.

Open a window to display the contents of the USB drive and do the following steps.

4. Delete the following files from the root directory:
	start.exe
	start.bmp
	start.ini
	autorun.inf


5. Delete the following folders:
	bin
	programs

These files and folders contain Windows software that is not necessary to run Linux. You'll save about 64 MB that way.

6. Move the following files into the root directory of the USB stick:
	isolinux --> all 66 files in this folder, then delete the isolinux folder

7. Copy the following files into the root directory of the USB stick:
	casper/vmlinuz
	casper/initrd.gz
	install/mt86plus

8. Rename the following file:
	isolinux.cfg
	--> change the name to syslinux.cfg

9. Delete the following file:
	isolinux.bin


At this point you should have 8 folders and 71 files on the USB stick.

10. Open **WordPad** and edit the file syslinux.cfg as follows. You need to do two things; first, delete any references to a CD-ROM device and second, make sure that the file references are correct since we moved some files around. In addition, I added another menu choice called "Custom" and made it the default so that when booting up you can just hit Enter to start your customized session. Here is a copy of my edited syslinux.cfg file for the Kubuntu Dapper 6.06.rc Live Desktop disc:



11. Open a command prompt and change directory to the location of the syslinux folder. For example, if you placed the folder on your desktop then: cd C:\Documents and Settings\(your user name)\Desktop\syslinux-3.11\win32 (by the way you DO know that command prompt has command completion just like in Linux (start entering characters and then press the TAB key to complete the entry). I've been running Windows for 17 years and just discovered that by accident. doh!

12. Next write the bootsectors to the flash drive by entering the following command:
	syslinux -f X:
	--> where X: is replaced by the drive letter of your USB key. Be careful to pick the correct drive letter!

That's it. Now you should have a bootable USB key with the latest version of Kubuntu Dapper on it. My end result is a USB key with 230 files, 43 folders and occupying 608 MB (637,798,407 bytes) on the 1 GB USB key. There's about 367 MB of free space in the second partition for storing custom settings using the LiveCDPersistence feature.

LiveCDPersistence is a really neat feature; give it a try!

I may have missed it -- but, when I need to place files -- does that go to root of the FAT32 partition, or of the ext2 partition?

---

### Post by K0LO on 2006-06-02
> I may have missed it -- but, when I need to place files -- does that go to root of the FAT32 partition, or of the ext2 partition?
When you get the FAT32 partition finished you don't write anything else in there; it's just a substitute for the CD. The files in this partition are read, but not written to.

When you run Kubuntu from the USB stick you just save files as you would normally do -- to your /home directory, or anywhere else in the filesystem. They will all be written to the ext2 partition. As you install programs the system will write any changes to the original filesystem to the ext2 partition. This happens automatically; you don't need to do anything special.

I've run the LiveUSB stick for a couple of days and have installed several programs on it, have updated some programs, and have added some files and I've filled one-third of the ext2 partition, so there seems to be adequate room for normal operation. If you really want to get carried away and install tons of programs then you may want to consider a 2 GB stick.

Mark

---

### Post by djago on 2006-06-03
Hi K0LO!

> **K0LO]
1. Plug in your USB pen drive and use the HP format utility to format it with a FAT32 filesystem.

2. Using a partitioning tool, create two partitions. The first is formatted with a FAT32 filesystem and needs to be about 650 MB. The second should occupy the remaining free space and should be formatted with the ext2 filesystem and is given the name "casper-rw". Note! Most DOS partitioning tools will create the partition name in uppercase (CASPER-RW). Since Linux is case-sensitive you need to do the formatting of the second partition in Linux. The persistent feature will not work if the partition name is in uppercase. See the Wiki for details. [https://wiki.ubuntu.com/LiveCDPersistence#head-463b3dc931fcb7dc6aa3eedccd8d4f459868bb82](https://wiki.ubuntu.com/LiveCDPersistence#head-463b3dc931fcb7dc6aa3eedccd8d4f459868bb82)
[/QUOTE]

Why format it 2 times?
I've tried to format with Dapper Alternative x64 disk and 650Mb is not enough. I've to put 685Mb.

[QUOTE=K0LO]

3. Put the Live Desktop CD in your drive and copy over all of the files to the USB pen drive. Make sure that you have Windows set up to show hidden files and to show Protected Operating System files so that you are sure to copy every file.

An alternate way to do this is to mount the iso image file and copy the files that way. I did this with NERO. You might want to do it this way if you don't want to burn a CD.

Open a window to display the contents of the USB drive and do the following steps.

4. Delete the following files from the root directory:
	start.exe
	start.bmp
	start.ini
	autorun.inf


5. Delete the following folders:
	bin
	programs

These files and folders contain Windows software that is not necessary to run Linux. You'll save about 64 MB that way.

[/QUOTE]

You'd better copy everything except those files  said:**
> 
6. Move the following files into the root directory of the USB stick:
	isolinux --> all 66 files in this folder, then delete the isolinux folder

7. Copy the following files into the root directory of the USB stick:
	casper/vmlinuz
	casper/initrd.gz
	install/mt86plus

8. Rename the following file:
	isolinux.cfg
	--> change the name to syslinux.cfg

9. Delete the following file:
	isolinux.bin


At this point you should have 8 folders and 71 files on the USB stick.


70 files in x64 or I've lost a file? :-k 

> **K0LO]

10. Open WordPad and edit the file syslinux.cfg as follows. You need to do two things said:**
> 

What references do you mean? The "Check CD for defects" label?

[QUOTE=K0LO]
11. Open a command prompt and change directory to the location of the syslinux folder. For example, if you placed the folder on your desktop then: cd C:\Documents and Settings\(your user name)\Desktop\syslinux-3.11\win32 (by the way you DO know that command prompt has command completion just like in Linux (start entering characters and then press the TAB key to complete the entry). I've been running Windows for 17 years and just discovered that by accident. doh!

12. Next write the bootsectors to the flash drive by entering the following command:
	syslinux -f X:
	--> where X: is replaced by the drive letter of your USB key. Be careful to pick the correct drive letter!

That's it. Now you should have a bootable USB key with the latest version of Kubuntu Dapper on it. My end result is a USB key with 230 files, 43 folders and occupying 608 MB (637,798,407 bytes) on the 1 GB USB key. There's about 367 MB of free space in the second partition for storing custom settings using the LiveCDPersistence feature.

LiveCDPersistence is a really neat feature; give it a try!

698,159,104 bytes 
231 files and 58 folders for my x64 version... :-k  I hope I didn't drop any file...

Anyway, I've tried to boot and I get:

> 
GRUB Loading stage1.5.


GRUB Loading, please wait...
Error22
_

And that's all. ](*,) 

[QUOTE=GRUB Manual]
22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.
[/QUOTE]

Any clues?

---

### Post by K0LO on 2006-06-03
djago:

Where did GRUB come from? The live CD versions have their own bootloader (isolinux on the CD or syslinux if you've using a USB pen drive). That error message sounds like it's coming from a GRUB installation on your hard drive.

You need to get your PC to boot from the USB pen drive. Be sure that the pen drive is plugged in and then go into the PC's BIOS setup menu and move the USB drive to the top of the boot list. On some PCs you can press F12 when the PC starts up to get to a boot list without entering setup.

Once you've done that you should be good to go.

I don't know how many files are on the x64 version. The numbers in my original post were ONLY for Kubuntu version 6.06 for i386 machines. Your numbers may vary...

Mark

---

### Post by djago on 2006-06-03
[QUOTE=K0LO]djago:

Where did GRUB come from? The live CD versions have their own bootloader (isolinux on the CD or syslinux if you've using a USB pen drive). That error message sounds like it's coming from a GRUB installation on your hard drive.
[/QUOTE]
I don't know... I have Windows XP only in my HD (in fact it's a nvidia SATA RAID and I couln't make it work with fakeraid :( )

[QUOTE=K0LO]You need to get your PC to boot from the USB pen drive. Be sure that the pen drive is plugged in and then go into the PC's BIOS setup menu and move the USB drive to the top of the boot list. On some PCs you can press F12 when the PC starts up to get to a boot list without entering setup.[/QUOTE]

Yes, my mobo has this option with F11.

[QUOTE=K0LO]Once you've done that you should be good to go.[/QUOTE]
Not in this case :confused: 
I even did a shred with the pendrive! I don't know where the hell is GRUB coming from, and I don't know how to get rid of it :???: 
Seems that win32 syslinux.exe isn't working...

[QUOTE=K0LO]I don't know how many files are on the x64 version. The numbers in my original post were ONLY for Kubuntu version 6.06 for i386 machines. Your numbers may vary...[/QUOTE]

I know, i know... I'm only saying that because somebody using x64 version might find it usefull :cool: 

Cleaning a ghost GRUB someone?

---

### Post by K0LO on 2006-06-03
One more thing to check -- make sure that the FAT32 partition is set as "Active" on your USB pen drive. You can do this with Partition Magic or other DOS tools, or you can do it on a Linux box with fdisk.

---

### Post by leetcharmer on 2006-06-04
I haven't been able to copy over the file "casper/filesystem.squashfs" (622MB) to my 1GB flash drive when it's formatted in FAT32 -- I've been able to do it *once* when it was FAT16; but, haven't been able to get it since.  :/ weird.

---

### Post by K0LO on 2006-06-04
You can format your flash drive's first partition with FAT16 or FAT32. Both will work.

If you can't get the file to copy, check the CD for errors and be sure that the partition on the flash drive is large enough to hold the file.

---

### Post by djago on 2006-06-04
[QUOTE=K0LO]One more thing to check -- make sure that the FAT32 partition is set as "Active" on your USB pen drive. You can do this with Partition Magic or other DOS tools, or you can do it on a Linux box with fdisk.[/QUOTE]

It was active :(
Anyway the problem seems to be using the ubuntu format utility from the installation. I'll try with PQMagic

---

### Post by Flashstar on 2006-06-05
I got SLAX to run on a small 512 mb usb stick so that's great, but I have a large 120gb external usb drive as well and I was wondering if there is a relatively easy way to install Ubuntu 6.06 lTS using something like syslinux? I can make a partition of about 40gb on it to run Ubuntu and I read the guide for a 1gb flash drive but will it still apply to my 120gb drive with a 40gb ext2 or FAT32 partition? I've tried this over and over with no success. ](*,)

---

### Post by K0LO on 2006-06-05
Flashstar:

With that much space available you should be able to do a regular install of Ubuntu/Kubuntu to the external USB hard drive and forget about syslinux. This thread was started by people who were trying to do just that. Have you tried their installation procedure?

[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

Although written for Breezy, you should be able to install Dapper in a similar manner.

---

### Post by Flashstar on 2006-06-05
I looked at that installation procedure and tried it but it just seemed too complicated. I'll give it a whirl again but if there is a conflict with Dapper, I wouldn't know what to do.

---

### Post by cotcot on 2006-06-06
Is it possible to get a customized Dapper on the USB pen ? (with numlock on, azerty keyboard, application added, others deleted) ?

---

### Post by K0LO on 2006-06-06
cotcot:

Absolutely! That's the really great thing about the LiveCD version of Ubuntu. If you use the feature it will save all of your customizations, files, and any programs that you add on the "casper-rw" partition of the USB pen drive.

I'm currently traveling and brought my USB pen drive along. At my mom's house I can just plug the drive into any PC that can boot from USB and my whole customized Kubuntu installation is right here with me.

I just used it to fix the partitioning on her hard drive with Qtparted. Very slick!

---

### Post by cotcot on 2006-06-06
Kole : 
If I understand you well I have to follow your procedure from page 11 ; then boot on the USB pen drive and then make all modifications I want ?

---

### Post by K0LO on 2006-06-06
cotcot:

That's correct. The first time that you boot from the USB drive you will see a default K/Ubuntu installation. You need to be passing the "persistent" kernel argument when you boot, so if you follow my post #100, I modified the syslinux configuration file so that if you just press "Enter" to start K/Ubuntu, then the "persistent" setting will be passed to the kernel.

To test, start K/Ubuntu and then make a change. For example, change the desktop background. Then restart the PC and when you get back to the desktop the background should return to the way you left it. The same goes for other changes.

Besides remembering settings, the Persistence feature remembers other changes. For example, you can install Firefox, add themes and extensions, save a bunch of bookmarks and they'll all be there the next time you return.

Mark

---

### Post by cotcot on 2006-06-10
[QUOTE=K0LO]**10. Open [B]WordPad** and edit the file syslinux.cfg as follows. You need to do two things; first, delete any references to a CD-ROM device and second, make sure that the file references are correct since we moved some files around. In addition, I added another menu choice called "Custom" and made it the default so that when booting up you can just hit Enter to start your customized session. Here is a copy of my edited syslinux.cfg file for the Kubuntu Dapper 6.06.rc Live Desktop disc:
[/QUOTE]

I followed your instructions but the booting of my pen drive failed.
I followed your instructions using a desktop PC (PC1 in my signature) hesitating at 2 points :

1. By copying files from the install CD to the pen I could not copy the folder "ubuntu"; i guess because it is linked. Should this be copied to the pen drive ? It is the empty folder tree of the install CD.

2. In the syslinux.cfg you have added " preseed/file=preseed/kubuntu.seed". As I am loading ubuntu i changed it in " preseed/file=preseed/ubuntu.seed". But there is no filename "ubuntu.seed" on the pen drive. There is "lt.sp.seed" and "server.seed". Do i have to use " preseed/file=preseed/lt.sp.seed" instead ?

On the "casper-rw" partition i have only a lost+found file. Is that ok ?

Finally i went in the bios of the laptop where i would like to use ubuntu on the pen drive and changed the boot order with "USB Storage Device" as first and indicated as bootable. But I got XP from the HDD. Select the USD Storage Device from a boot setup menu (F12) did not work either.

Is there a way to check on the pendrive if it is bootable ? 


Thanks

---

### Post by K0LO on 2006-06-10
cotcot:

On the Kubuntu Live CD the item "ubuntu" is a simlink that points to the root of the CD. Windows copied it over as a zero-byte file named "ubuntu". If you were unable to copy it then I wouldn't worry about it.

If you want to create the simlink manually then mount your pen drive on a Linux machine and create a simlink named "ubuntu" that points to "." (the root of the pen drive). I didn't do this and the pen drive seems to work fine.

It appears that the preseed files are named differently in Kubuntu. I have two files in the Preseed folder; kubuntu.seed and server.seed while it appears that Ubuntu names the files lt.sp.seed and server.seed. So you are correct; you would change the reference to "preseed/file=preseed/lt.sp.seed for Ubuntu.

When you create the casper-rw partition and format it with ext2, the file "lost+found" will be created. When you get the persistence feature to work then there will be a lot of other files added to the partition, but at first there is only the "lost+found" file.

Finally, the last step of the procedure is what makes the USB pen drive bootable. When you run the DOS command "syslinux -f X:" (replacing X: with the drive letter of your USB pen drive), then the syslinux program writes the bootsectors to the pen drive and also adds the file "ldlinux.sys" to the drive. The "ldlinux.sys" file is the one that is booted. It is a hidden, protected operating system file so if you want to see it in Windows you will have to set folder options to display hidden files and also to display protected operating system files.

If your drive won't boot then try running the DOS syslinux command again.

Mark

---

### Post by cotcot on 2006-06-10
Does not get ldlinux.sys working. I also tried with linux (installed syslinux and mtools ; then "syslinux /dev/sde1 after having umounted it).  I have now all files on the USB root protected (padlock icon).
The laptop still goes to XP. May USB Storage Device is not for a USB pen drive.

---

### Post by K0LO on 2006-06-10
cotcot:

Sorry to hear that you can't get the USB pen drive to boot.

I've heard that booting from USB pen drives is still a work in progress. It works on some models of pen drives but not on others, so maybe your drive is one of the brands that won't boot. Maybe google for bootable USB drives and perhaps you can find a list that someone has posted.

The drive that I got to work successfully is a Corsair CMFUSB2.0-1GB.

Can you try to boot from your drive with a different PC?

One final thought -- is the primary partition on the USB drive set as active? Check with qtparted or Partition Magic or fdisk -l to see.

---

### Post by cotcot on 2006-06-11
Thanks Kolo to keep on checking this thread. 
I made a stupid error. I forgot to write out with fdisk. Although fdisk does not see it as active; gparted sees it as 'boot' and the USB drive is now trying to boot, still with some errors but that is because i experimented to much. So i am going to redo the procedure..

---

### Post by K0LO on 2006-06-11
Sounds like you're on the right track.

---

### Post by cotcot on 2006-06-12
Success !!!
I got it working. Persistent mode works too. The speed is good, much better than from LiveCD.  

Kolo : I followed your steps with following exceptions (because i used only ubuntu) :

Step 2 : i used fdisk under linux ; the casper-rw partition was made using ```
sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sda1/CODE] 
Gparted did not function well. I think that coldplug tried to mount the thumb drive during formatting of the partition so that the formatting was interrupted. 

root partition was set active with fdisk ('a' and then '1'  and then 'w') 

Step 3 : copying the hidden folder '.ubuntu' with a link on was not possible, obviously also not necessary.

Step 10 : I used 'gedit' as text editor for syslinux.cfg. I have attached it (at least i tried because it is the first time i attach something in this forum). Different from yours is the preseed name because yours is kubuntu and mine is ubuntu.

Step 11 : i installed syslinux (with apt-get) and used the command [CODE]syslinux /dev/sda1
``` to install ldlinux.sys on the thumb drive.

At the end it is a fairly easy procedure. It is worth to make a wiki of this. With a good wiki also new linux users could make this.

Once again thanks for following me in this thread.

---

### Post by K0LO on 2006-06-12
Excellent! I'm glad that you were successful.

I really like being able to carry my custom version of Linux with me on a small pen drive. It's almost like having your PC with you while you travel, but much much smaller.

Perhaps you could add to the existing Wiki article at:
[https://wiki.ubuntu.com/LiveCDPersistence#head-463b3dc931fcb7dc6aa3eedccd8d4f459868bb82](https://wiki.ubuntu.com/LiveCDPersistence#head-463b3dc931fcb7dc6aa3eedccd8d4f459868bb82)

The only change to your procedure that I would suggest is to format the second partition with ext2 instead of ext3, although either filesystem will work. I say that because I read somewhere that ext2 is a better choice for a flash memory device with limited storage space. Ext3 will use more overhead in storing files.

Mark

---

### Post by cotcot on 2006-06-13
During the formatting of my thumb drive I took the instruction to format casper-rw from the wiki you mentioned and changed ext3 to ext2 according to your 11-step instrcution, but forgot to change the 3 in 2 in the text of my previous post. Sorry.

I made a separate wiki page :  [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

---

### Post by enfield on 2006-06-23
I've got the live CD running from my Sandisk 1Gb micro USB stick!  Thanks for all the tips.  After getting it running I had to dive into ndiswrapper to get the wireless card working on my Dell laptop.

However, I edited the syslinux.cfg file per post #100 but I don't get a menu at boot.

Anyone else have this problem?

---

### Post by K0LO on 2006-06-23
Don:

You don't really get a menu like you do when running the CD version. The pretty menus on the LiveCD are generated by isolinux, whereas the pen drive boots into syslinux where you only get text prompts on the screen.

BTW, cotcot has written a very nice Wiki page describing the procedure for making a bootable USB pen drive version of K/Ubuntu LiveCD:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by enfield on 2006-06-23
Lack of a menu hasn't been a problem, it's just that a lot of the editing of syslinux.cfg seems pointless.

On another note, is it possible to upgrade the programs on the USB stick, assuming there's sufficient storage space on the Linux partition?

---

### Post by K0LO on 2006-06-23
Don:

If all you do is start in the default mode then you might be right. The editing is to allow the other function keys to work; start in Live mode, start MemTest, etc. You can delete all of those options if you don't want/need them.

On the other note, yes! That's the main point of the persistence feature. ANY changes that you make to the installation are saved. You can install new programs, update programs, change settings, tweak, etc. All of your changes are saved as differential files in the casper-rw partition. The original Linux partition is never changed.

This is all assuming that there's enough free space on the casper-rw partition to store your changes. Just be aware that it won't take long to fill up a 300 MB partition. If you really want more space, a 2 GB pen drive would be better.

---

### Post by andrewsawyer on 2006-06-23
Can I ask, has anyone tried/managed to get this working with GRUB?  The reason I ask is that in theory if you can get it working with GRUB, you could make it encrypted.  If I'm walking around with what is essentially the contents of my hard disk in a bootable and fully usable format, it'd be nice to have a password prompt on boot up.

---

### Post by kabanta on 2006-06-24
This thread has been very helpful! And also, the two guides:  [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")  and 
[Holy Cow, I got it working!]("http://ubuntuforums.org/showpost.php?p=1062799&postcount=100")

Here are some comments and suggestions about the LiveUsbPendrivePersistent guide that might be helpful for others:

[LIST]
[*] Check to see how the usb-drive is mounted:   sudo fdisk -l

  It would help to have an example of what the author saw as result of
  running the **fdisk** command.

  Note also: the documentation for **fdisk** claims that is unreliable and
  suggests using **cfdisk** instead.


[*] Unmount usb-drive: sudo umount /dev/sda

  There is an interaction between /dev/sda (which is presumably the
  flash DRIVE) and /dev/sda1 (which is one of the PARTITIONS on the
  drive). It's probably important not to mix these. (This is one reason it would help to have example output from the author's **sudo fdisk -l** before creating partitions.)


[*] Create partitions: sudo fdisk /dev/sda1

  Note that upon completing this step you may get a message to the
  effect, "[I]unable to update tables ... kernel still using the old
  tables. Will update upon reboot[/I]." I've seen information that you
  should reboot before proceeding with the next steps.


[*] Copy the following folders and files to the 1st partition of your
  USB pendrive.

  There is a typo. For dapper, the name of the folder to copy should
  by 'disctree' rather than 'disktree'

  There may be a couple of errors when copying attempts to follow
  symlinks in the 'dists' folder. These are links to stable and unstable distributions. (Probably ok to just click 'skip' if these errors occur. Does anyone know of a reason to try and include the symlinked directories?)

  The [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") guide and the [Holy Cow, I got it working!]("http://ubuntuforums.org/showpost.php?p=1062799&postcount=100")  guide are pretty much the same. The only difference is that the Holy Cow guide gives advice that will result in a slightly smaller installation. It does this by indicating some additional files that can be deleted  from the usb-install (or need not be added to it) because they have to do with Windows. Following the LiveUsbPendrivePersistent guide will mean that these files will be left on the usb-drive (but they won't ever be used). 
  
  The files that are not needed: the entire **'programs'** folder (the files are all .exe files for windows) -- and the **isolinux.bin** file that now appears in the usb / directory as a result of copying all files in LiveCD's 'isolinux' directory.


[*] Downloading and running syslinux.

  When you run syslinux, there may be an error to the effect: "*mcopy needed but unavailable.*"
  To fix this, install 'mtools' via synaptic or apt-get -- then run the syslinux command again.

[/LIST]

HTH, k.

---

### Post by K0LO on 2006-06-24
kabanta:

The only reason that I suggest not copying the Windows programs and isolinux.bin is to save space, which is at a premium on the USB pen drive.

Mark

---

### Post by kabanta on 2006-06-24
[QUOTE=K0LO]The only reason that I suggest not copying the Windows programs and isolinux.bin is to save space, which is at a premium on the USB pen drive.[/QUOTE]
Ah, ok. I edited my comments above to reflect this.

---

### Post by kabanta on 2006-06-24
[QUOTE=andrewsawyer]Can I ask, has anyone tried/managed to get this working with GRUB?[/QUOTE]
I have a couple of related questions.

[LIST]
[*]What is the motivation for using syslinux? Other than, "because it works" :)  

I mean: by using syslinux (and formatting boot partition as FAT), feels like it is "less" of a Linux install. 


[*]Has anyone here tried to create a LiveUSB install with Xubuntu? 
[/LIST]

---

### Post by K0LO on 2006-06-24
kabanta and andrewsawyer:

In principle, it would seem that you could also do this by formatting the main partition as ext2 and then installing GRUB, configured to start up any of the choices (live, persistent, memtest, etc). You could then delete all of the syslinux related files.

I don't see why this wouldn't work. Anybody care to give it a go?

---

### Post by kabanta on 2006-06-26
[QUOTE=K0LO]In principle, it would seem that you could also do this by formatting the main partition as ext2 and then installing GRUB, configured to start up any of the choices (live, persistent, memtest, etc). You could then delete all of the syslinux related files.

I don't see why this wouldn't work. Anybody care to give it a go?[/QUOTE]
I would certain be willing to experiment on my drives. However, there are a couple of things I don't know/understand and would need some help:

[LIST=1]
[*]I don't really understand the relationship between **Syslinux** and **Grub**. Some descriptions I have seen suggest that these are simply alternative bootloaders. But I have also seen descriptions that imply that Syslinux can/does *rely on* Grub. 

[*]How to install **Grub**. The process you all described for creating syslinux-based LiveUSB involves copying some files, making a couple of edits, and running syslinux. Presumably, installing Grub instead would still involve the first two parts of this process, but how to do the "grub part"? 
[/LIST]

I'm looking around for some tutorials etc., but if anyone here can already suggest a way to modify the existing LiveUSB install-process to include Grub rather than Syslinux, let me know.

---

### Post by K0LO on 2006-06-26
kabanta:

I'd try also if I had the time, but right now I can't.

Syslinux does not rely on GRUB. When you boot your pen drive using syslinux, there is no copy of GRUB on the drive. As far as I know they are independent bootloaders.

I think the process of making a USB pen drive to use GRUB instead of syslinux would go as follows:

1. In my post #100, don't do steps 6 and 7 (don't copy the syslinux files and no need to duplicate the kernel, initrd, and memtest files at the root level; leave them where they are).

2. Size the main partition accordingly so that the caper-rw partition can be as large as possible.

3. Install GRUB to the MBR of the pen drive. You can find instructions for doing this in the GRUB manual, section 3.2. The manual is at [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

4. Try booting the system by manually entering GRUB commands as described in the GRUB manual, section 4. If this works, then you can go on to the next step.

5. Create the menu.lst file for GRUB (see manual section 5). Copy the general syntax by looking at your /boot/grub/menu.lst file on your current Linux box. Under the menu choices you could set up GRUB to boot the same variants as syslinux was doing -- Live, Persistent, memtest, etc. just by adding the appropriate lines to the menu.lst file. The syntax would be kind of similar to the lines in the syslinux.cfg file, but you'd have to check the GRUB manual to be sure of the exact required syntax. Setting up the ramdisk is the one area that I'm the least sure of how to do. This would require further research.

Mark

---

### Post by kabanta on 2006-06-27
[QUOTE=K0LO]I think the process of making a USB pen drive to use GRUB instead of syslinux would go as follows ... Setting up the ramdisk is the one area that I'm the least sure of how to do. This would require further research.[/QUOTE]
Ok, thanks for the tips. I'll experiment with this over the next couple of days.

---

### Post by sunset_studies on 2006-06-27
Hi, thanks to all of this information, I finally got Dapper running on my USB key. One thing bothers me though: the 'dapper' disk (as opposed to the 'casper' one) seems to be writable. Should it not be loaded read only so as to save writes to the flash memory?

---

### Post by K0LO on 2006-06-27
That sounds reasonable. Remember though that the system runs from ramdisk, and the ramdisk must be mounted as read/write.

---

### Post by kabanta on 2006-06-28
[QUOTE=K0LO]I think the process of making a USB pen drive to use GRUB instead of syslinux would go as follows[/QUOTE]
Unfortunately, at the moment I am in the process of moving and only
have access to a 4gb flash-drive -- and it requires some tricks to get
my computer to recognize it as bootable with such a large drive. So, I
have not succeeded yet to get this working -- and I'm not sure how
soon I can get back to this. However, here are some instructions that
may help someone else to finish in the meantime.

Based on your (Kolo) steps:

[LIST=1]
[*]Follow the steps for the [HolyCow]("http://ubuntuforums.org/showpost.php?p=1062799&postcount=100") install

   BUT: 
[LIST]
[*]Partition USB-drive with both partitions as ext2

[*]Don't do step 6 or 7 (This is based on what you wrote, Kolo.)
[/LIST]


[*]Create a /boot directory in primary partition (not the "casper-rw" partition) 


[*]Install GRUB as follows:


[LIST=1]
[*]Make sure your USB drive is mounted


[*]Type "sudo grub" which makes a GRUB prompt appear.


[*]Type "find /boot/grub/stage1". You'll get a response like this:

```

   (hd0,3)
   (hd1,0)
```
   This means: 

   (hd0,3) a grub bootloader for the computer's built-in disk (hd0) is on partition 4 (probably /dev/hda4)

   (hd1,0) a grub bootloader for mounted usb disk (hd1) is on partition 1 (probably /dev/sda1)

   (Note that you could get many more items if you have several boot-up partitions and/or additional usb drives mounted when you do this. To keep things reasonably simple and clear, you should probably *not* have any other USB devices attached to your computer when you do this entire procedure.)

So, for the listing above, we would want to do the next steps on (hd1,0) -- but when you do this, *make sure to select YOUR equivalent of the USB drive's primary partition*


[*]Type "**root (hd1,0)**" (without quotes)


[*]Do "setup" with one of two options:

   - To have Grub for the entire disk, type "setup (hd1)"

   - To have Grub for the partition, type "setup (hd1,0)"

   (For a small thumb-drive with only the two partitions described in this procedure, it shouldn't make a difference which one you choose.)


[*]Type "quit". 


[/LIST]

[*]Check to see that you have a /boot/grub/ directory on the usb-drive -- the contents should be similar to the contents of your computer's /boot/grub directory.


[*]Create the /boot/grub/menu.lst file (or, if it already exists, open it). 

   AS A SIMPLE WAY TO TEST YOUR SYSTEM, paste the following into menu.lst file:
```


# default startup item
default		0

## timeout in seconds
timeout		10

# Pretty colours
color cyan/blue white/blue

## default grub root device
# groot=(hd0,0)

title		Ubuntu 6.06 LiveUSB
root		(hd0,0)
kernel		/casper/vmlinuz root=/dev/sda1 ro quiet splash
initrd		/casper/initrd.gz
savedefault
boot

```
(Note: I *believe* the information above will work, but again, haven't been able to test it.)


[*]Save the menu.lst file and reboot off the usb-drive.


[*]If this works, someone else may be able to provide follow up for more complex Grub menu at startup -- and persistent memory.

[/LIST]
HTH, k.

---

### Post by Cruzer on 2006-06-28
Hi people!:D 
I was just wondering, since you people know about tech stuff, which is the fastest flash drive out there?
I succesfully got LiveUbuntu on an old usb drive and it's cool but kinda slow :( , so i'm thinking on getting one thats really fast that way boot time will be less.
Thanks

---

### Post by K0LO on 2006-06-28
[http://www.tomshardware.com/2005/08/10/two_fast_and_functional_usb_flash_drives/index.html]("http://www.tomshardware.com/2005/08/10/two_fast_and_functional_usb_flash_drives/index.html")

The article is a little old, so perhaps there's something faster now.

Here's a more recent article:
[http://chris.pirillo.com/2006/06/02/the-fastest-flash-drive/]("http://chris.pirillo.com/2006/06/02/the-fastest-flash-drive/")

---

### Post by sunset_studies on 2006-06-29
[QUOTE=K0LO]That sounds reasonable. Remember though that the system runs from ramdisk, and the ramdisk must be mounted as read/write.[/QUOTE]

Hi,

I won't pretend to know exactly what that means, but 'fair enough'. Next on the agenda: how to encrypt the Casper partition and therefore protect against loss/theft... any clues?

---

### Post by andrewsawyer on 2006-06-29
[QUOTE=sunset_studies]Hi,

I won't pretend to know exactly what that means, but 'fair enough'. Next on the agenda: how to encrypt the Casper partition and therefore protect against loss/theft... any clues?[/QUOTE]

For an encrypted Ubuntu (the actual distro, you would need a third partition.  One partition for GRUB etc, one for the main filesystem files - squashfs etc, and then a third as a casper-rw.

I would suggest that you would do it in a similar fashion to [http://ubuntuforums.org/showthread.php?t=120091](http://ubuntuforums.org/showthread.php?t=120091) only making some changes.  It would also require (to my knowledge) that we can get the LiveUSB working with GRUB as the bootloader.

To encrypt the casper-rw would be more difficult as I would think that you would have to play around inside the squashfs file (I may be mistaken).  You may be able to link the encryption into the GRUB section to it would un encrypt both partitions off the one command however I'm only guessing whether this is possible.

Just my 2c.

---

### Post by sunset_studies on 2006-07-04
thanks Andrew.... looks like a bit too much work for me :|  so I'll take the lazy option and wait for somebody else to do it.

One final thing: could you tell me how to disable/expedite the raid devices bit in the boot process? it takes sooo long and I don't think it's required for this machine of mine.

---

### Post by hubick on 2006-07-05
[QUOTE=kabanta]
Install GRUB as follows:

Type "find /boot/grub/stage1". You'll get a response like this:

```

   (hd0,3)
   (hd1,0)
```

[/QUOTE]

I am configuring this directly from the LiveCD, and that gives me a file not found error.

The flash drive I am attempting to boot from is formatted ext2 with the volume label "CHBoot", and has been auto-mounted as /media/CHBoot.  I was able to install grub with a command like:

sudo grub-install --root-directory=/media/CHBoot --no-floppy '(hd1)'

I ran "grub" previously to create a device.map file (google grub device.map), and used that to decipher the grub device name for my flash drive to install to (hd1).

[QUOTE=kabanta]
Create the /boot/grub/menu.lst file (or, if it already exists, open it). 

AS A SIMPLE WAY TO TEST YOUR SYSTEM, paste the following into menu.lst file:
```


# default startup item
default		0

## timeout in seconds
timeout		10

# Pretty colours
color cyan/blue white/blue

## default grub root device
# groot=(hd0,0)

title		Ubuntu 6.06 LiveUSB
root		(hd0,0)
kernel		/casper/vmlinuz root=/dev/sda1 ro quiet splash
initrd		/casper/initrd.gz
savedefault
boot

```
(Note: I *believe* the information above will work, but again, haven't been able to test it.)
[/QUOTE]

I don't think the "root=/dev/sda1 ro" argument to the kernel is correct - at least, it didn't work for me.  I changed my kernel line to:

kernel /casper/vmlinuz preseed/file=preseed/ltsp.seed boot=casper ramdisk_size=1048576 root=/dev/ram rw --

If I boot with that, I get a bunch of errors trying to open/read from the cdrom during boot and it dumps to a shell.  If I boot to grub on the usb flash drive, then put the cdrom in, then continue to boot the flash disk... it apparently works, and everything starts up - but apparently mostly from the cdrom.

Does this mean something still references the cdrom?  In initrd.gz?

Suggestions?

---

### Post by hubick on 2006-07-06
**Holy Emu! I got it working!**

I have an ext2 formatted USB flash drive booting the Dapper LiveCD! :)

In the Dapper Desktop CD /casper/initrd.gz image is a /scripts/casper script which has a find_cd() function. This function searches through system block devices to locate the filesystem.squashfs for casper. During this examination of block devices, it behaves differently for cdrom's and usb devices. The usb device code will only examine vfat, iso9660, and udf filesystems.  I had to modify this to also examine ext2/3 filesystems.  I filed a bug with the details of my change to the script at:
[https://launchpad.net/distros/ubuntu/+source/casper/+bug/52124](https://launchpad.net/distros/ubuntu/+source/casper/+bug/52124)

Obviously, I had to modify the initrd.gz image copied from the live CD to my flash drive to make this work.  The steps were roughly:
```
cp /media/CHBoot/casper/initrd.gz /tmp/
cd /tmp
gunzip initrd.gz
mv initrd initrd.img.old
mkdir initrd.img.dir
cd initrd.img.dir/
cpio -cid -I ../initrd.img.old
# modify scripts/casper here
find . | cpio --create --format='newc' > /tmp/initrd.img.new
cd ..
gzip -9 initrd.img.new
mv initrd.img.new.gz /media/CHBoot/casper/initrd.gz
```

As a recap, I installed grub on my flash drive with a command like:

sudo grub-install --root-directory=/media/CHBoot --no-floppy '(hd1)'

(That root dir being where I had the LiveCD flash drive mounted)

And my grub menu.lst contains the following:
```
title		CHBoot (Ubuntu)
root		(hd0,0)
kernel /casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw --
initrd		/casper/initrd.gz
boot
```

---

### Post by K0LO on 2006-07-06
Chris:

That's terrific. I gotta try this too!

I think I'll set GRUB up to have these menu options:

0) Persistent (the default choice)
1) Live -- Start or Install Kubuntu
2) Live -- Safe Graphics Mode, Verbose Startup
3) Memory Test 

And like Andrew Sawyer has said, you could also password-protect the startup process by adding a GRUB password.

Is the kernel argument "preseed=..." necessary any more? I don't see it in your GRUB menu.lst file. Any idea what it does?

Mark

---

### Post by hubick on 2006-07-06
[QUOTE=K0LO]Is the kernel argument "preseed=..." necessary any more? I don't see it in your GRUB menu.lst file. Any idea what it does?[/QUOTE]

It is my understanding from poking around that it loads extra configuration options to for the "Linux Terminal Server Project"  server software as part of the boot/install process.

---

### Post by andrewsawyer on 2006-07-06
[QUOTE=K0LO]
And like Andrew Sawyer has said, you could also password-protect the startup process by adding a GRUB password.[/QUOTE]

Heya,

My actual thought has been to get an encrypted bootable USB disk and also an encrypted laptop.  Then to use the GRUB bootloader on the USB disk to access both versions - so you couldn't boot the laptop without the USB key plugged in, and when you didn't have the laptop, you could still boot into Ubuntu on someone elses computer using your password to unencrypt the usb.

I'll hav a play around though and see what I can get going.  I've not had a chance to do anything on it recently other than follow the forum - work is kinda busy.

---

### Post by K0LO on 2006-07-07
Chris:

I too was successful in getting GRUB installed as the USB pen drive's bootloader and configuring it per my previous post.

Since I noted the objection to your bug report, I did not modify the initrd file and just left the main partition as vfat to avoid the issue of filesystem corruption, if it is true.

I will now try to figure out which files can be deleted and how much space it will free up for the casper-rw partition, which i'd like to make as large as possible. I'll post again with specifics.

Mark

---

### Post by K0LO on 2006-07-08
Kubuntu Live Desktop on a USB pen drive -- GRUB version

In my post #100 there are instructions for making a bootable USB pen drive version of the Kubuntu/Ubuntu LiveDesktop CD. If you want a more compact version, you can save some space by using GRUB as the bootloader instead of syslinux. 

Also, since my original post I've found other files on the CD that are only used by Windows and can be deleted.

Here is a summary of the space requirements for the different installations:

LiveDesktop CD ---------- 695 MB -- 97 folders -- 502 files
Syslinux USB pen drive -- 638 MB -- 58 folders -- 249 files
GRUB USB pen drive ----- 627 MB -- 51 folders -- 70 files

Why bother? If you're partitioning your pen drive so that you can use the persistent feature you will want to leave as much space available as possible for the "casper-rw" partition that holds the filesystem changes. I was able to create two partions on a 1 GB USB pen drive; 643.2 MB for a filesystem partition formatted as FAT32 and 329.5 MB for the casper-rw partition formatted as ext2. If you have a larger pen drive then this is not as much of an issue.

Here's a condensed description of the process.

1. Follow the article "LiveUsbPendrivePersistent" in the Ubuntu wiki:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

2. In the section "Making Partitions" you can use smaller sizes for the two partitons. Make the first partition at least 643 MB and allocate the remaining space to the second partition.

3. In the section "Installing Dapper on the USB pendrive" modify as follows:

Copy the following folders from the CD to the 1st partition on the pendrive:
'casper', 'dists', 'install', 'pics', 'pool', 'preseed', '.disk'

Copy the following files from the CD to the 1st partition on the pendrive:
'md5sum.txt'

Do **not** copy any of the isolinux files and do **not** duplicate 'vmlinuz', 'initrd', or 'mt86plus'. GRUB can find these files in their current folders so there is no need to duplicate them in the root directory.

Do not rename isolinux.cfg since it was not copied and is not needed.

4. In the section "Making the pen drive bootable, substitute the following steps to install GRUB:

Create a /boot directory
```
 sudo mkdir /boot 
```

Find your device name for the USB pen drive and the mount name. My device name was /dev/sdc with two partitions; /dev/sdc1 is the primary partition and /dev/sdc2 was the casper-rw partition. My mount name was /media/sdc1 for the primary partition. These names will vary depending on the drive configuration of your PC. **Be sure that you know the correct name!** You do not want GRUB to install itself to one of your hard disks during this step. I suggest writing the command down on paper with the correct device and mount names substituted to be very certain that you will type the command correctly.

```
 sudo grub-install --root-directory=/media/sdc1 --no-floppy /dev/sdc 
```

This command will install GRUB to the Master Boot Record of the USB pen drive and place its files in the /boot/grub folder of the first partition. Again, be sure to substitute the correct device names!

Check the contents of the /boot/grub folder:
```
cd /media/sdc1/boot/grub
ls 
```

Now you can delete some of the files from this folder if you want to save a little more space. Leave the following files:
'stage1', 'stage2', 'e2fs_stage1.5', 'fat_stage1_5'
and delete the others.

Create a menu.lst file and place it in this folder. Here is the file that I used:
```

# menu.lst - Customized for Kubuntu Live Desktop 6.06
#		MJW 8 Jul 2006

default		0
timeout		3
color white/blue yellow/blue

title		Kubuntu Live Desktop (Persistent)
root		(hd0,0)
kernel		/casper/vmlinuz boot=casper persistent ramdisk_size=1048576 root=/dev/ram rw quiet splash--
initrd		/casper/initrd.gz
boot

title		Kubuntu Live Desktop
root		(hd0,0)
kernel		/casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash--
initrd		/casper/initrd.gz
boot

title		Kubuntu Live Desktop (Safe Graphics Mode, Verbose Startup)
root		(hd0,0)
kernel		/casper/vmlinuz boot=casper xforcevesa ramdisk_size=1048576 root=/dev/ram rw --
initrd		/casper/initrd.gz
boot

title		Memory Test
root		(hd0,0)
kernel		/install/mt86plus
boot

```

Now when you boot the USB pen drive you should see the GRUB bootloader screen and you can select which version of LiveDesktop that you want to boot. The menu.lst file above can be customized with your own preferences. For example, change the colors to "white/brown yellow/brown" for Ubuntu users, change the default timeout in seconds, etc.

---

### Post by sportsfan986 on 2006-07-12
> **andrewsawyer said:**
> 
My actual thought has been to get an encrypted bootable USB disk and also an encrypted laptop.  Then to use the GRUB bootloader on the USB disk to access both versions - so you couldn't boot the laptop without the USB key plugged in, and when you didn't have the laptop, you could still boot into Ubuntu on someone elses computer using your password to unencrypt the usb.


I tried to get this to work, but I can't seem to get it to recognize the harddrive as bootable.  Let me know if you make any progress.

---

### Post by fra1027 on 2006-07-17
Sorry if isn't much in topic, but I don't see any thread that speeks about this...
I think, if works fine for a usb drive, why doesn't work for a partition on my hard disk?
I copy the contenent of livecd on hdd how I red on this forum (I have created the two partitions and modify the syslinux.cfg and run syslinux).
I have Win xp and I modify boot.ini to boot with grub Ubuntu, I used instlux tool.
The Ubuntu live"hdd" seems to boot but I receive error to load filesystem and stops.
Changing my menu.lst the boot pass filesystem but don't find /dev/ram on root and stops.
I presume that my menu.lst isn't correct. Which is the rigth string to boot my livehdd?
Or maybe I change initrd.gz... 
I'm waiting good news. :)

---

### Post by K0LO on 2006-07-17
fra1027:

If you are already using GRUB as a bootloader on your hard disk, perhaps you could try starting the Live CD from GRUB instead of from syslinux.

See my post #158 above. Add one or more of the entries shown to your menu.lst file for GRUB. Then reboot your PC and select the added entry when the GRUB screen appears and see what happens.

---

### Post by fra1027 on 2006-07-17
I try but nothing...
In verbose mode boot, but then stops with "cdrom: open failed"
Before of this I receive:
"hdc: packet command error: error=0x50{LastFailedSense=0x05}"
"ide: failed opcode was: unknown"

In other mode boot and stops at "Mountig root file system".

---

### Post by K0LO on 2006-07-17
fra1027:

Perhaps this is related to the problem that user *hubick *found in posts 152 and 153.

Which type of filesystem are you using for your partition that holds the LiveCD files; ext2 or vfat?

If ext2, then the scripts in initrd.gz will always look for a CD drive and you will get the "cdrom: open failed" error.

If you convert the filesystem to vfat (FAT32), then it should work.

Or, you could modify initrd.gz as hubick suggests and continue to use ext2 filesystem. However, you should read the bug report that he filed (see post 153) that recommends against doing this because of the risk of potential file corruption.

---

### Post by fra1027 on 2006-07-17
Yes I red this post... but I have vfat (Fat32)!
What's wrong???

---

### Post by K0LO on 2006-07-17
Is your hard disk a USB hard disk or an IDE hard disk?

I think that the scripts in initrd.gz are set up for booting from IDE optical drives or USB devices. I'm not sure what they'll do on IDE hard drives.

---

### Post by fra1027 on 2006-07-17
It's an IDE hard disk. Where find an initrd.gz that works for me?

P.S: There's another one on livecd? (I think to install procedure..)

---

### Post by K0LO on 2006-07-17
fra1027:

I'm sorry; that's beyond my abilities. Perhaps someone else here can figure out how to modify the initrd.gz script.

---

### Post by fra1027 on 2006-07-18
Please help me to configure my initrd.gz to boot from my IDE hard disk as livecd.

---

### Post by K0LO on 2006-07-18
fra1027:

I was just wondering why you would want to do this? If you have a hard disk available, why not just install Ubuntu on it? Why the LiveCD approach?

I realize that a LiveCD installation would only occupy 1 GB and a full install might need 8 or 10 GB. On the other hand, if it's just an experiment then that's a good enough reason.

---

### Post by fra1027 on 2006-07-19
It's an experiment and not an experiment... ;)
In livecd modal (boot by cd) I can use(at very slow speed) this good OS but when I try to install, the interface don't load.
I wrote to forum but I receive as answer "Download alternate cd" but I have a 56k...
Now I want to do this expirement. I try to modify my initrd.gz but nothing... same error. Maybe I modify a wrong script?

---

### Post by CameronCalver on 2006-07-26
you can get 300gb portable sb hard drives

---

### Post by leetcharmer on 2006-08-20
I have a laptop (Compaq Presario 2100) with a broken hard drive.  I have a 1GB Flash drive USB.  Can you let me know if I can boot from the USB drive to have a working system?  Thank you!

---

### Post by Stretch 4x4 on 2006-08-29
This ubuntu on a usb drive seems like exactly what i want and a great idea unfortunately incomptetent me can't get it to work. I am trying to install to a 10gb external usb hard drive I can format it okay and copy the files over but whenever I try to install syslinux or grub, it only takes a second and nothing seems to happe yet it still says it completes. When i try and boot it, it either doesn't seem to do anything and I get xp or 200 depending on where I am or one time i managed to get i think it was an L then lots of 99's kinda like L 99 99 99 99 99 99 for half the screen am i doing something wrong or is it maybe my drive

---

### Post by bernstein on 2006-09-06
> **fra1027 said:**
> It's an experiment and not an experiment... ;)
In livecd modal (boot by cd) I can use(at very slow speed) this good OS but when I try to install, the interface don't load.
I wrote to forum but I receive as answer "Download alternate cd" but I have a 56k...
Now I want to do this expirement. I try to modify my initrd.gz but nothing... same error. Maybe I modify a wrong script?

actually its very easy !!!

you'll have to do as K0LO [did]("http://ubuntuforums.org/showpost.php?p=1062799&postcount=100") and modify your initrd.gz ! (thanks hubrick) 

First you need to copy and extract your initrd.gz (assuming you copied the stuff onto your harddisk, partition hda2 - change this as apropriate):
```
cp /hda2/casper/initrd.gz /tmp/
gunzip /tmp/initrd.gz
mv /tmp/initrd /tmp/initrd.img.old
mkdir /tmp/initrd.img.dir
cd /tmp/initrd.img.dir/
cpio -id -I ../initrd.img.old
```
now edit /tmp/initrd.img.dir/scripts/casper :
```
gedit /tmp/initrd.img.dir/scripts/casper
```
finde the following and comment it out (put a # in front of every line) :
```
for i in 0 1 2 3 4 5 6 7 8 9 a b c d e f 10 11 12 13; do
    live_image=$(find_cd)
    if [ "${live_image}" ]; then
        break
    fi
    sleep 1
done
```
and add two small lines just below :
```
    mount -t vfat -o ro /dev/hda2 $mountpoint
   live_image=/cdrom/casper/filesystem.squashfs
```
now you just need to make the initrd.gz again and copy it back :
```
find . | cpio --create --format='newc' > /tmp/initrd
cd .. 
gzip -9 initrd
cp /tmp/initrd.gz /hda2/casper/
cp /tmp/initrd.gz /hda2/
```

i did this on a Compact Flash Card (CF) put it in an IDE adapter and since then running a completely noiseless notebook, which runs for about 45mins longer :-)

**I am assuming that you formatted your partition (hda2) with vfat (FAT32) and made it active! so this won't work in a multiboot scenario! however if you install GRUB instead of SYSLINUX it should work without a hick!! How to do this for kubuntu has actually been posted by K0LO [here]("http://ubuntuforums.org/showpost.php?p=1229101&postcount=158") (thanks!)**

in case anyone tries setting this up on a CF and runs into slow booting/booting errors: add *ide=nodma* to the boot options (hit F6 to see them in the menu)

*so now i have a question : Has anyone been able to modify this to boot from a PCMCIA Flash Drive ???? i succeded in setting initrd up to include the pcmcia kernel modules and initialize them. but i couldn't figure out how to initilize the PCMCIA Card (actually its a CF->PCMCIA Adapter with a CF Card in it :-))*

---

### Post by thom83 on 2006-09-08
To bernstein :
When modifying script casper you say :
and add two small lines just below :
```
    mount -t vfat -o ro /dev/hda2 $mountpoint
   live_image=/cdrom/casper/filesystem.squashfs
```

I want also make a liveusb whith Dapper in order to use it on computers of my friends everywhere. I think that it would be '/dev/sda1' for me instead of '/dev/hda2'.
I did it but have error message telling :
     Running /scipts/local-premount...
     Done
     mount: Mounting /dev/sda1 on /root failed: no such device
     Begin: Running /scipts/local-bottom...
     Done
     Done
     Begin: Running /script/init-bottom...
     mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
     Done        and so on

What is to do? Thanks.

---

### Post by bernstein on 2006-09-11
> **thom83 said:**
> 
I want also make a liveusb whith Dapper in order to use it on computers of my friends everywhere.

If you want to make a live USB-Pendrive/USB-Stick/USB-HDD you have to follow the [LiveUSBPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") wiki (SYSLINUX) or [this]("http://ubuntuforums.org/showpost.php?p=1229101&postcount=158") Post (GRUB)!

> **thom83 said:**
> I think that it would be '/dev/sda1' for me instead of '/dev/hda2'.
If you want to install a LiveUbuntu to a fixed disk in your computer, follow my post and it should be /dev/hda? (when disk is IDE/ATA) or /dev/sda? (disk is SATA). You'll have to install/run gparted and figure out the correct device (hda1,hda2,...sda1,sda2,...). (I won't not answer questions about gparted - there's plenty of info about installing/using it around!)

**two more things :**
- if you add/remove disks from your computer the devicenumber might change!
- following my post will bypass LiveUbuntu's routines of figuring  out the device on its own! its a simple and probably "ugly" hack.

---

### Post by NZ-Wanderer on 2006-10-02
Just finished reading all 18 pages of this thread, and would like to say a big WELL DONE to everyone concerned..

I think I may just have to try this out myself...:) 

I do have one little query tho if I may...

I have a rather interesting situation that isn't mentioned in amy message in the thread, in that my main computer has Ubuntu (Dapper) and XP Pro, and my little computer just has XP Pro..

Is there a way to make the pen drive so it will work on BOTH computers (and anyone elses I plug it into) ?
As I don't really want to get rid of Ubuntu from the hard drive on my main computer just yet.. :)

---

### Post by dante00001 on 2006-10-02
Im not sure if this was mentiond before (im not going to read all 18 pages) but i have had a lot of sucess with the program QEMU. It allows you to run ubuntu as a virtual machine form just about any    usb device. It is slower than booting directly into ubuntu but you might want to check it out.

---

### Post by bernstein on 2006-10-02
> **NZ-Wanderer said:**
> Is there a way to make the pen drive so it will work on BOTH computers (and anyone elses I plug it into) ?

The "LiveCD on a USB Pendrive" will work on most computers ubuntu runs! I being a liveCD it tries to detect your hardware on each boot...

besides of being small this is another benefit from a "liveCD"!!!

---

### Post by NZ-Wanderer on 2006-10-02
Thanks for that, spent most of the evening trying to figure out why the commands weren't working properly.. - discovered in the end the only way to make things work was to turn OFF the auto mount, once I did that things went more smoothly until I tried to copy the contents of the CD, it copied most, but refused to copy 2 files/folders (in the end I just did the copying over on my other machine (xp)
it 1:30am here, so am calling it a night annd will play further after I wake up..

I really wanted to actually "install" ubuntu itself onto my 2gb pen drive. but there is no way I can figure out how to get past the "min 2gb" that it seems is required to install ubuntu and from searching the forums it seems there is no manual way to install ubuntu with just the stuff you want.. - A little annoying really...

Anyway, thanks for the reply, much appreciated. :) 

> **bernstein said:**
> The "LiveCD on a USB Pendrive" will work on most computers ubuntu runs! I being a liveCD it tries to detect your hardware on each boot...
besides of being small this is another benefit from a 'liveCD"!!!

---

### Post by K0LO on 2006-10-02
4 GB pen drives are becoming a little more affordable now.....

However, the LiveCD version isn't that bad. It does take a little longer to boot than a "real" installation of K/Ubuntu but runs OK once it has started up. It's great for fixing PCs if you install your favorite tools to the pen drive installation. I add GParted, QtParted for graphical partitioning tools, Firefox and Thunderbird for web browsing and email, etc. Everything fits comfortably on a 1 GB pen drive.

---

### Post by bernstein on 2006-10-02
> **NZ-Wanderer said:**
> 
I really wanted to actually "install" ubuntu itself onto my 2gb pen drive. but there is no way I can figure out how to get past the "min 2gb" that it seems is required to install ubuntu and from searching the forums it seems there is no manual way to install ubuntu with just the stuff you want.

Actually there is a way over [here]("http://www.ubuntuforums.org/archive/index.php/t-186298.html"): 
basically install the server version of ubuntu - take the server cd and select "install to harddisk" (NOT LAMP server)

on the first bootup you login and enter :
sudo apt-get install x-window-system-core xserver-xorg gnome-desktop-environment 

now it should only take about 1.5gb of space!

haven't tried it but should work....

---

### Post by NZ-Wanderer on 2006-10-02
Ohh thanks for that, will have to give that a go and see what happens.. :)

---

### Post by TiredBird on 2006-10-02
Kolo and Berstein,

Comments first and then a few questions -

There has been some real yeoman work done by you guys on this subject. I've read all of it and I'm impressed. However, the size of non-live installations may be less than you think. 

I have one machine running what Ubuntu refers to as a 'minimum' system. It is only taking a total of 316 MB and I installed it in a 512 MB partition. (I used the 6.06.1 alternate installation CD.) Of course there's no GUI.

I have another machine running a full LAMP server. It totals 745 MB without any user space. I installed it on a 1 GB partition with the 6.06 server CD. (Again, no GUI).

Yes, I do have one with a GUI. It is about 3.5 GB, was installed from the 6.06 live/install CD, but includes a lot a personal stuff. I don't know how much of that total is actually OS but I suspect it's a lot less than 2.0 GB.

And now to my dilemma. I have gone through thread after thread, and pages of documentation, both here and elsewhere, on putting Linux on a thumbdrive. I  want something thats in the mainstream, has a Gnome desktop like I use every day, and has solid and easily useable update capabilities. I've looked at a lot of things and the only thing I find that meets my criteria is Ubuntu.

I have several questions: 

(1) Can the Ubuntu installation be modified, and I don't mean through the use of the second partition. I've read the documentation for remastering Knoppix and I want to know if something similar can be done with Ubuntu.
 
(2) Even though I think I have followed the directions religiously, I can't seem to get it to work on a USB stick. I used the Grub boot loader as one of you described but it still boots from the hard-disk.

When I ran the grub-install, (now several days ago so I'm going from memory), there were some messages about bios mapping which you didn't mention. It even created a map file on my USB stick but you said to wipe out all the files other than certain ones you named so I wiped out the map file. Could it be that some computers need that and others don't?

(3) Is it really as simple as you say to 'install' a small system on a USB. I realize that an install rather than a live type is only going to work on one machine but considering that one of the USB thumbdrives I bought the other day, (at Staples), was 1/2 GB for only $15.00, I'm tempted to put a bare-bones system on a thumbdrive just for the hell of it.

P.S. Do you have any idea why I keep getting logged off of the forum? If I'm writing a post when it happens I lose what I've written. I've sent two messages to the administrators regarding this but get no answer.

---

### Post by K0LO on 2006-10-02
TiredBird:

1. Probably, but I'm not that exprienced to know how to do it. The beauty of the LiveCD method with the differential second partition is that you accomplish the same thing with the only penalty being a larger footprint than the 600 MB CD. I've gotten all that I want on a 1 GB stick and still have 200+ MB of free space. With the price of USB sticks continually decreasing, it's not out of the question to solve any space problems by using a 2 GB stick (approx US$40 now).

2. Your BIOS must support USB boot, and you might have to change the boot priority to make sure that the USB device boots first before the hard disk.  I'm lucky that my PC's BIOS has a feature where you press F12 during POST to bring up a boot menu where you can select the boot device on the fly.

If the PC boots from the USB device, the BIOS *should* identify it as (hd0) in GRUB terminology. If not, you might have to figure out the correct identifier and change the GRUB menu.lst file to match.

3. You could probably put a small system on a USB stick like you describe, if that's what you want. I'm spoiled. I like having the full Kubuntu GUI with all of the apps that I'm used to.

Not to get too far off-topic, but these little USB thumb drives are really great for PC work. I too picked up a couple of 256 MB units on sale for US$7 each, so I have a set of DOS tools on one,  BartPE on another, and Acronis Disk tools on a third, and Kubuntu live on my 1 GB. A friend of mine picked up a 4 GB unit on sale and has a full install of Windows XP Pro on it.

---

### Post by TiredBird on 2006-10-03
Kolo, I posted to this last night but I guess it didn't take.

1. How's the speed of the Live CD on a USB stick? By remastering, I was mostly trying to avoid having a union type file system which I have heard can be slow. Also, I wanted to get rid of a bunch of apps I don't use, put on some that I want and still have plenty of open space for personal data, (jpg's take up a lot of space). (I bought a 2GB stick for this ($45.00).

2. I think the boot started on the thumb drive, (I do have the proper choices in my boot sequence), but as a recall (hd0) was mapped to my hard drive so it would have looked for stage 1.5 on the hard drive and found it as I use Grub and Ubuntu 6.06 as my regular stuff on that machine. What do I need to change to make this work right?

3. Whether its the 2 GB with GUI or the .5 GB with CLI, I don't really care. What I'm going to use it for mostly is emergencies. I've got three other Ubuntu systems so I'm not likely to use it for regular stuff at home. I'll use it for emergencies or when I find myself in need of a computer when I'm away from home and don't have my laptop with me. It'll have mostly rescue type programs on it, partitioning stuff, file stuff, network, etc. - the fundamental stuff you need to get a system working, like the rescue disks only with everything I need in one place instead of part here and part there as it is now.

I also have a 1 GB stick but I've been using that regularly now for several months. I'ts mostly encrypted and has a bunch of portable Windows programs that I use on XP type machines. I could move that stuff to another thumbdrive if I really needed a 1 GB for something. You're right though. They're so cheep these days that if I don't have the size I need for something I'll go buy it. Right now though I have two unused one, a .5 GB and a 2 GB. Any ideas?

---

### Post by thom83 on 2006-10-03
To TiredBird

For remastering, you can use Ubuntu Customization Kit :
[http://uck.sourceforge.net/](http://uck.sourceforge.net/)
It works well if you have the same system than the liveCD you want to modify : gnome for Ubuntu, or KDE for Kubuntu and so on.

---

### Post by K0LO on 2006-10-03
TiredBird:

1. It looks like thom83 has provided the answer that you were looking for! After reading the documentation of the Ubuntu Customization Kit, it appears that you can do it the way that you wanted.

2. If your BIOS does not map the USB thumb drive as (hd0) then you need to figure out the correct mapping. I would start GRUB and then press "c" when the initial GRUB screen appears. This gets you to a GRUB command prompt. Try the following command:```
find /boot/grub/stage1
```GRUB should then print out a list of every disk and partition that contains the file /boot/grub/stage1. If both your hard disk and USB thumb drive have the GRUB files located at /boot/grub, then you'll see an entry for each drive. Since you said that your hard disk is identified as (hd0) then the other one will be your USB drive. Then change the menu.lst file to reference the correct drive in the statement:```
root (hd0,0)
```change it to ```
root (hdx,0)
```where x is the drive number.

Curiously, I tried my USB thumb drive with Kubuntu Live Linux in as many PCs as I could find and in all cases it booted up right away, therefore the BIOS must have identified the drive correctly as (hd0). However, the GRUB manual warns that some BIOSes may not always map the boot device to (0x80) [or (hd0)]. See [this](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall).

I would be very interested in knowing if the remastering works out OK; it sounds like a good way to customize your installation.

---

### Post by TiredBird on 2006-10-03
KOLO and thom83:

Thanks to both of you for the help. I've downloaded the latest Grub documentation. That should help me understand the boot problem. I've also downloaded the remastering platform from SourceForge. 

Unfortunately, I've got to shelve this project for a few days. When I get back to it I'll let you know what happened.

Again thanks for your help.

---

### Post by wislon on 2006-10-06
I must say kudos to all of you for the work you've put in! :KS 

I've followed the last 18 pages or so with interest, because this is exactly what I want to try. I was having a look at pendrivelinux.com, and tho I quite like knoppix, I'd rather have an ubuntu dapper USB boot solution.

One question, which I haven't seen asked (or answered) here: What happens if you do an apt-get update/apt-get (dist-)upgrade? Will it be able to update (for instance) kernel images, or installed packages that are on the primary partition? If it does, obviously this may be a problem for the pen drive solution in terms of space. Any thoughts?

---

### Post by K0LO on 2006-10-06
Wislon:

I have updated a few of the packages on my USB pen drive Kubuntu installation, but never the entire distribution.

What happens is that the primary partition (the one with the CD image) is never modified, so it never grows. The second partition with the differential filesystem (UnionFS) gets written to with the updates, and it grows larger.

I suspect that a distribution update would work but would require quite a bit of space. If you want to upgrade the whole distribution, for example from Dapper to Edgy, you would be better off rebuilding the pen drive with Edgy CD image. You could probably make a copy of your /home directory first, save it somewhere else, upgrade, and then re-copy your home directory back if you're worried about recreating all of your previous settings and preferences, however.

---

### Post by amedias on 2006-10-06
thanks for all your work guys, ahve been reading and following all of this since the beginning, have previously only used slax but getting live ubuntu running of USB and IDE flash has been a pain, now finally working!

however, once tiny issue....

have edited intrd.gz as per previous posts to get a live install running off CF in IDE adpater, but the persistent feature doesnt seem to be working...

no changes held after reboot, have trid deleting and recreating the casper-rw partition etc but still no luck...

is there anything i have missed do you think?

thanks for any advice!

---

### Post by wislon on 2006-10-07
> **K0LO said:**
> 

I suspect that a distribution update would work but would require quite a bit of space. If you want to upgrade the whole distribution, for example from Dapper to Edgy, you would be better off rebuilding the pen drive with Edgy CD image. You could probably make a copy of your /home directory first, save it somewhere else, upgrade, and then re-copy your home directory back if you're worried about recreating all of your previous settings and preferences, however.

K0L0: thanks for your input. I think you might be right. I actually wanted to try this this weekend to see what would happen, but left my @$##$ USB disk at the office. Better luck next week maybe :)

---

### Post by K0LO on 2006-10-07
Amedias:

I never tried creating the LiveCD version on a CF card because my laptop cannot see the CF card as a boot device, but if your PC can boot from a CF card then I don't see why it wouldn't work.

The only things that I can think of to double-check are:

1. Be sure that the second partition is primary and formatted with the ext2 or ext3 filesystem (ext2 recommended because it's slightly smaller in size).
2. Be sure that the partition is named "casper-rw" using all lower-case letters.

---

### Post by amedias on 2006-10-08
thanks K0L0, it is formatted ext2 and definately lower case casper-rw, I'll try again later to create and reformat the partition just in case its having a naughty moment...(or im was having a blonde moment...)

It all boots fine from CF card in IDE adapter, just doesnt have any persistance which was the whole point!

i'll keep you posted.

thanks!

---

### Post by TiredBird on 2006-10-12
I finally got back on this project and I'm having all sorts of difficulties.

I have followed Kolo's directions that modify the wiki posted howto on putting Ubuntu on a USB drive. I have also tried it as originally written in the wiki. No joy on either one. (I have a Toshiba M45-S165 Satellite laptop, about one year old, has boot provision for removable storage. I'm using Memorex Travel Drives. I also have another machine that has several options, (4 or 5) for USB booting. I can't make it work there either.

I have also tried putting a working system on a thumb drive and letting grub boot it from the hard drive. (A Grub 'find' showed the pendrive files at (hd1,0) so I added it to the menu that way. Again - no joy.

I thought that in the meantime I could at least remaster a CD but 'uck' caused me problems as well. I tried first to remaster the latest Xubuntu disk but there is break in its packages, which I had encountered and bypassed but Uck is not going to let it go. I shifted to the latest Ubuntu. It has broken down several times so far, each time getting a little further as I read the log and fix what caused the problem. 

I am now nearly at the end but am stuck again. I don't have 'mksquashfs' so a script that needs that fails. I can't download a binary because it only comes in source and I've never done a 'make' so I don't know how to do that or if I have the right stuff on my system.

If anyone has any help or suggestions related to any of the above I would appreciate it. I'll check this thread regularly for the next week or so and see if anyone has any ideas.

---

### Post by ntm on 2006-10-14
I've been looking through this thread and various websites, and have run into a problem which a few other people seem to have encountered, but for which I can't find a solution.

In short, the Ubuntu and Kubuntu Live CDs work fine as CDs - but once the relevant files have been copied on to my USB stick (as per the instructions in this thread) and the device has been made bootable (using Syslinux or GRUB), I can boot up to the point where I'm asked to log in.

At this stage, both Ubuntu and Kubuntu give a repeated error message ("User not known to the underlying authentication module") on all the terminal screens, while the Kubuntu X screen brings up the message "Authenticating ubuntu... A critical error occurred. Please look at KDM's logfile(s) for more information or contact your system administrator."

There seems to be no means of logging on to the system (be it as user 'root' or as user 'ubuntu' or as no user) or of accessing a terminal.

Is there any known solution to this issue? I should mention that it happens on both my main PC and my laptop. Any help would be greatly appreciated.

---

### Post by bernstein on 2006-10-14
> **amedias said:**
> It all boots fine from CF card in IDE adapter, just doesnt have any persistance which was the whole point!

Well actually, when i tried the stuff about booting from CF-Card i haven't tried the persistence feature... and now i - sadly - haven't any cf lying around... sorry :(

> **ntm said:**
> There seems to be no means of logging on to the system (be it as user 'root' or as user 'ubuntu' or as no user) or of accessing a terminal.

Well normally, that shouldn't happen...:-k When one copies the content of the liveCD, basically one copies a squashfs image file and the kernel/initrd to load that image. So basically if you didn't mess with this file and the booting proceeds without errors until the graphical login screen... you should be able to login the same way as with the liveCD! Try booting from the liveCD you created the liveUSBStick with and if that works i - sadly - have not the knowledge/time to help you :(

> **TiredBird said:**
> I can't make it work there either.

I've never done a 'make' so I don't know how to do that or if I have the right stuff on my system.

1. when you try to boot from the usb-pendrive: does grub(the one on the pendrive) show up? if yes, what error messages do you get? (like: does it find the partition? does it find the kernel files?)
2. same question but when you try to boot the usb-drive from grub on hdd...
3. i have never tried uck but compiling on linux is easy(well as easy as possible),: try downloading the following stuff```
sudo apt-get install build-essential checkinstall
```
now download the source and extract it. (for ex. to /tmp) go into the directory of the sourcecode.(in a shell) basically it should be ```
sudo ./configure
``` which will give you errors if a package is needed and tells you which one (well enough info to find the ones) if you have all the sources it quits without errors. now you're ready to compile the package. type:```
sudo make
```now you have to wait.... all should go well... ;) now to make/install a .deb package which you can easily uninstall afterwards type:```
sudo checkinstall
```:cool: 
Remember:
a) be prepared that the packages you need might to compile stuff might take  a huge amount of space on your drive...
b) note the packages you install for later uninstallment
c) i'am in no way an expert in this - actually i'm new to this too -, but i've succeded in compiling gparted 0.31, grsync 0.5 and glade 3.0.2 for ubuntu dapper with this method. 
d) based on c) i really can't offer you much help beyond what i've just written, i've never come across real errors

now on a personal note: i am following this thread and will give advice, if what little knowledge i have is enough to help, but don't expect me to post more than once a week nor when i have no idea's to help out. i am in no way an expert and for me linux/ubuntu is just a means to run my home edv smoothly (well on windows it's impossible)

---

### Post by TiredBird on 2006-10-14
Bernstein,

Thanks for the response.
> 1. when you try to boot from the usb-pendrive: does grub(the one on the pendrive) show up? if yes, what error messages do you get? (like: does it find the partition? does it find the kernel files?)No matter how I set the boot sequence, the first thing to show up is the grub menu from the hard-drive. I never see the one from the USB stick. I'm not sure though whether it is trying to boot first from the USB stick and then falling back to the hard drive or whether it's skipping the USB entirely. I have considered that my Memorex sticks (I have three of them) just can't be booted from.
> 2. same question but when you try to boot the usb-drive from grub on hdd...I have multiple partitions on the hard-drive and I'm using Grub to boot from a choice of three operating systems. On the grub install I did a 'find' and found stage1 on (hd1,0) whereas all other OS's showed up as (hd0,x). I then quit without doing a setup. Instead, I put the appropriate entries into my normal Grub menu so I could choose the USB installation as one of the OS's. However, when I chose the USB from the menu, Grub gave me an error about not being able to find the file. 

[It has just occurred to me that I probably copied the menu entry from one that was set up for another partition and the kernel version from the live cd I mastered from was probably not the same as the menu entry I copied. I'll go back and try that again.]

> 3. i have never tried uck but compiling on linux is easy(well as easy as possible),: try downloading the following stuffI appreciate your suggestion but it's not a matter of ease. I can compile if I want to but I don't want to. I have spent a lifetime doing that and at this point I refuse to do any more. (My first programming was an IBM 705 and it it didn't even have an assembler. I wrote in octal, no hex then. And I've written about 30,000 lines of c++ code, but for me personally, if it doesn't work out of the box, I won't use it. I'd rather wait until they fix the problems. Personally, I think Synaptic is the best part of Ubuntu. I even have it on my menu bar.)

Thanks again for your help!

---

### Post by TiredBird on 2006-10-14
Bernstein,

I got it working - at least on one machine. My main machine is a Toshiba M45 S165 Satellite laptop. On that machine I still haven't gotten it working. But, on the box I use for a home server, one the computer store built for me several years ago, I got it to boot. That machine has a Phoenix Award BIOS chip in it with 4 USB boot options. Of course it was the fourth one that worked, that was called "USB HDD". 

I've still got some experimentation to do on getting it to boot on machines without a USB boot by booting into it from a minimal CD. I'll keep you posted on what happens.

Thanks again for your help. You at least made me rethink what I was doing and do it over again. Maybe I did it right this time and didn't before. Who knows? Anyway, its working.

---

### Post by TiredBird on 2006-10-14
Now I'm frustrated again.

I just tried the same USB stick on my laptop, numerous different ways, (see below), and was unable to get it to boot or be recognized. The BIOS gives me a way to boot from removable media without going into the whole BIOS setup thing. You'ld think it would work.

There is an interupt in the boot sequence that allows you to select your boot method. (F12 at a certain point). I have three USB ports so I tried each of them. I tried different combinations of root, different sockets and even tried to boot it from the hard disk boot menu but couldn't get anything to work. This is a one year year old machine. It should work. The machine that did work is three to four years old!

---

### Post by K0LO on 2006-10-27
Hi, guys. Now it is I who needs some expert assistance.

I have tried to create a LiveCD version of Kubuntu Edgy on a USB flash drive following my own advice in post #158 of this thread. This time it fails to complete the boot process. GRUB successfully locates both partitions on the flash drive (FAT32 partition for the files and ext2 partition for the casper-rw portion). The kernel loads and detects hardware including the flash drive and identifies the two partitions as sdb1 and sdb2. When the init scripts start to run the process fails. The error messages are:```
cp: unable to open '/root/var/log/': No such file or directory
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
...
```and then drops to a busybox shell.

If I repeat the boot from USB flash drive but this time I keep the LiveCD loaded in a CD drive the boot proceeds normally from the USB flash drive and when the INIT stage begins the system finds the filesystem on the CD-ROM and finishes successfully. So it would appear that the initrd.gz file furnished with Edgy will need to be modified to boot from USB flash drives whereas the one from Dapper worked without modification.

I've uncompressed initrd.gz and attached the init script from /scripts/casper as a text file. Could someone take a look at this script and suggest a modification that will allow the system to find the squashfs on the USB flash drive instead of wanting to find it on a CD?

Mark

---

### Post by K0LO on 2006-10-31
Another update on getting Edgy to work on a USB Flash drive -- I'm embarassed:oops: I had formatted the first partition on the USB flash drive as FAT32. After reformatting as FAT16 it started working.

However, I'm now having a problem with the persistent feature. If I start up into the LiveUSB version using the "persistent" kernel argument, the UnionFS does get created on the second partition because I can then plug the USB flash drive into a PC running linux and browse the contents and see the files. However, the next time that I start up in persistent mode I get all kinds of read-only and permissions errors that prevent KDE from starting. I'm still troubleshooting this.

The second partition is formatted as ext2 and is named "casper-rw". So far I can't see what I've done wrong. Any ideas?

---

### Post by zakhooi on 2006-11-04
So, can someone summarize all steps in a proper howto how to set up an Edgy live USB stick?

The requirements I'm looking for are:
- Boot Edgy from USB
- Ability to install packages permanently on the USB stick while booted
 
Currently I'm using SLAX/backtrack wich is able to do this, but I guess ubuntu should be able too and I rather use ubuntu on a stick (maybe called 'USBuntu' ???)

Thanks in advance

---

### Post by K0LO on 2006-11-04
zakhooi:

I'm pretty close now to getting this to work but I'm still working the bugs out. I will post here when I get everything to work correctly.

My latest discovery is that I can make the persistent feature work if the second partition (casper-rw) is formatted with ext3. It's supposed to work with ext2 but it didn't seem to for me. The first partition was also supposed to work with FAT32 but I had to make it FAT16 to get it to work at all. So either something has changed since Dapper or else I'm doing something stupid.

While it's now working, I'm currently chasing down a problem. The casper-rw partition is just littered with hundreds of zero byte files with names like .wh_dir_opaque and variations (.wh.*). Every time that I restart in persistent mode, more of these are added. Over on the Knoppix forums they were discussing problems like that with their distribution, so I'm trying to track down their solution.

If you want to try this out, follow the wiki article [here](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) but instead choose FAT16 for the first partition and ext3 for the second, and use the Edgy LiveCD instead of the Dapper LiveCD.

---

### Post by zakhooi on 2006-11-04
> **K0LO said:**
> zakhooi:

I'm pretty close now to getting this to work but I'm still working the bugs out. I will post here when I get everything to work correctly.

My latest discovery is that I can make the persistent feature work if the second partition (casper-rw) is formatted with ext3. It's supposed to work with ext2 but it didn't seem to for me. The first partition was also supposed to work with FAT32 but I had to make it FAT16 to get it to work at all. So either something has changed since Dapper or else I'm doing something stupid.

While it's now working, I'm currently chasing down a problem. The casper-rw partition is just littered with hundreds of zero byte files with names like .wh_dir_opaque and variations (.wh.*). Every time that I restart in persistent mode, more of these are added. Over on the Knoppix forums they were discussing problems like that with their distribution, so I'm trying to track down their solution.

If you want to try this out, follow the wiki article [here](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) but instead choose FAT16 for the first partition and ext3 for the second, and use the Edgy LiveCD instead of the Dapper LiveCD.

That's exactly what I did, the weird thing is that FAT32 on the first partition did work for me.
The only problem I face is that I want to have a set of tools installed by default but that doesn't fit so until now I end up with a '/' of 100%.

Can't wait for your HOWTO... thanks for al the effort

---

### Post by K0LO on 2006-11-04
Are you starting the system with the "persistent" kernel argument? If so, you can install any tools that you want and do your customizations and they will be saved to the second (casper-rw) partition.

I believe that there's a reference in the Wiki article about customizing the contents of the LiveCD, but that's over my head. Or maybe it was referenced in one of the earlier posts in this thread.

I don't know why I had trouble with the filesystem types. I'm going to have to zero the USB flash drive and try again. Maybe the problem is that I used a mixture of DOS and Linux tools to partition and create filesystems. I'll repeat but this time with all Linux tools.

---

### Post by unclechewgum on 2006-11-06
> **K0LO said:**
> **Holy cow! I got it working!**

I now have a 1 GB USB pen drive with the Live Desktop version of Kubuntu Dapper installed and running (version 6.06.rc) ** Including the LiveCDPersistence feature**......

10. Open **WordPad** and edit the file syslinux.cfg as follows. You need to do two things; first, delete any references to a CD-ROM device and second, make sure that the file references are correct since we moved some files around. In addition, I added another menu choice called "Custom" and made it the default so that when booting up you can just hit Enter to start your customized session. Here is a copy of my edited syslinux.cfg file for the Kubuntu Dapper 6.06.rc Live Desktop disc:


I got this to work with Ubuntu Dapper 6.06 LTS, but editing a custom section in the syslinux.cfg didnt work for me. Only got a single bootprompt (with the Ubuntulogo in background), no menu either. But passing the parameter :

live persistent

to the prompt got the persistente funktion worked and i could save data and reconfigure desktop etc...all intact at next use.

There where no ubuntu "seed" in the seed-directory, so i skipped that out of syslinux.cfg

BTW: FAT32 didnt work, i had to use FAT16 on /dev/sda1 (and i used ext2 for /dev/sda2)


Uncle

---

### Post by TiredBird on 2006-11-06
It would appear that live USB's are not yet ready for prime time. They work sometimes, some sticks, some pc's, but no one seems to be able to make them work all of the time.

It looks like it may be a year or two before we get enough standards to make USB booting as reliable as CD booting. I'm tired of fooling with it. I'm going to wait.

---

### Post by xemet on 2006-11-07
Hi to all,
I'm Manfredi from Italy, 

great work here! After reading a lot of posts, now I've my usb pen with my customized Ubuntu Live with persistent feature working (I need it customized because I need a software called EMC2 to drive numeric control machines, and this software not only is preinstalled, but the kernel of the live CD was modified, not by me, because this software requires Real Time Linux). 

However, now everything works fine with the USB pen thanks to all people here. I had to change few things: I've read that most of people say to format the fisrt partition as Fat32, but I had to format it as Fat16 because syslinux didn't work with Fat32...
I had problems using fdisk to make partitions because I didn't know how to make Fat16 partitions, so I used gparted and after I used fdisk only to format and give name to the partitions, I had to deactivate the automatic mount feature in ubuntu (the one that mounts your usb pen when you plug it) because this was causing problems during formatting process. I had to copy the file vesamenu.c32 in order to get a decent syslinux boot menu.

Now, my next aim is to make the same ubuntu live system booting from a IDE Compact Flash. Why? 

Because at University we have to use it on a embedded small computer that has not Hard drive but only a compact flash.

I've read here (page 18 ) that Bernstein had done it, modifying the initrd casper script, I'm going to try it and see what will happen. 

If I have problems I will ask ;)   

Many thanks to all

---

### Post by K0LO on 2006-11-08
Manfredi:

How did you disable the automount feature for usb pen drives? I've tried "sudo pumount /dev/sdxx", which unmounts the drives, but they automatically remount when a new partition is created.

The automount feature creates problems when using gparted, so I'd like to be able to figure out how to disable it.

---

### Post by xemet on 2006-11-09
Hi, 

not by terminal, simply go in the menu system -> preferences -> removable drives and media and uncheck the box "mount removable drives when hot-plugged".

Of course there will be a way to do it by terminal, but I don't know it. If anyone knows it please share because I'm interested too...

Let me know if it worked,

byeee

Manfredi

---

### Post by K0LO on 2006-11-09
You must be running Ubuntu. I can't find any similar setting in Kubuntu (kde).

---

### Post by xemet on 2006-11-10
Sorry, I never used kubuntu so I did not know this particular...
But I'm sure that there will be a way to do that, I will search on the web, if I find something usefull I will let you know.

byee

---

### Post by beefcurry on 2006-11-27
Great, ive now finished reading all the pages. wheef. Surely the popularity should have suggested to the developers that people want a portable ubuntu :P. If someone could create a script like MySlax Creator for SLAX that would make life alot easier.

The bootable CF card is very impressive, as a photographer i have LOADS of CF cards lying around, i have a spare 8GB EXTREME 3 CF card and am DYING to rip the guts (harddrive) out of my Laptop and replace it with a CF Card. Flash degrades with multiple rewrites but reading is fine, which makes a bootable drive so cool :D.

We should add this into the wiki if no one has already done so.

---

### Post by chettedeboeuf on 2006-12-09
Hi !
Sorry for my poor english, I'm french !
I'm using this page : [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
for create my USB Libe
All is ok, but I've those messages :
/bin/sh : can't accept tty, job control turned off
[xxxxxxx] usb 3-5 : device not accepting adresse 4 Error -110
[xxxxxxx] usb 3-5 : device not accpeting adress 5 Error -110
...
....
.....

Can anybody explain me or help me ??

Thank you for your help

Cheers

ChEtTeDeBoEuF

---

### Post by K0LO on 2006-12-09
ChEtTeDeBoEuF:

Bonjour and welcome to the forum.

If you are using Ubuntu Edgy version 6.10, then try this. When you go to format your drive:```
Formatting the partitions

We will now format the partitions by putting a filesystem on and giving them the name 'dapper'
(or any other name you want) and 'casper-rw' (this name is MANDATORY, do not change other names
and do not use capital letters) :

sudo mkfs.vfat -F 32 -n dapper /dev/sda1
sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sda2
```
Instead of FAT32 and ext2, try FAT16 and ext3:```
sudo mkfs.vfat  -n edgy /dev/sda1
sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sda2
```

I had the same problem and error message as you did when using FAT32 with one brand of USB flash drive, but FAT32 worked fine on another.

However, I have been unable to make persistence work with ext2. Using ext3 it always works.

---

### Post by chettedeboeuf on 2006-12-09
Thank you very much KOLO,
I'm trying to install Ubuntu 6.10 on my USB Stick and have an AMD with XP Pro SP2 installed
USB Stick INTUIX S600

but do you have a trick under Windows ?

If not, I'll try under Ubuntu

Cheers

ChEtTeDeBoEuf

---

### Post by K0LO on 2006-12-09
ChEtTeDeBoEuf:

Here is a link to an article that I wrote for a different forum that is targeted to Windows users:
[http://www.gottabemobile.com/forum/forum_posts.asp?TID=917](http://www.gottabemobile.com/forum/forum_posts.asp?TID=917)
Perhaps it will help?

---

### Post by chettedeboeuf on 2006-12-09
I'm lost,
so I will use your method page 10 with kubuntu

Cheers

ChEtTeDeBoEuF

---

### Post by sportsfan986 on 2006-12-11
Is there any way to hide the Ubuntu partition form Windows Computers.  I have an extra 256 MB FAT 32 partition on my drive, and I want it to appear as just a normal Flash Drive when plugged in.  Thanks in advance.

---

### Post by K0LO on 2006-12-11
As far as I've been able to tell, Windows will only see the first partition on a removable USB flash drive.

I tried an experiment by putting 4 FAT partitions on a USB drive but Windows could only see the first one. It will, of course, ignore any Linux partitions on the drive.

---

### Post by chettedeboeuf on 2006-12-11
Hi all !
If I've understand, I need 2 USB Keys ?

PS : sorry for my poor english

Cdlt

ChEtTeDeBoEuF

---

### Post by K0LO on 2006-12-11
No, you only need 1 USB key if you have a CD drive.

If you are looking at my article on the GottaBeMobile forum, do the  following steps:

Part 2
Part 3
Part 5

Bonjour!

---

### Post by bobl on 2006-12-11
I've started to play around with "casper-rw" with my Ubuntu LiveCD and an EXT3 thumb drive and like it very much.  Nevertheless, some more hardware-savvy associates have pointed out that a block of flash memory is not something one normally wants to write to repeatedly, as, for instance, in the case of blocks containing journal entries (i.e. EXT3).  They suggested a better choice is something like JFFS2.

On the other hand, some random Web pages suggest that modern USB drives do something called "write balancing" that does what JFFS2 does, but in hardware, and that using JFFS2 together with such hardware would be counterproductive and that EXT3 is just fine.

On yet another hand, if there's sufficient RAM, perhaps the thumb drive shouldn't get hit very often in the first place -- mainly during boot and shutdown -- but if so, why am I seeing the LED flash a lot during normal operation?  Also, how much is "sufficient" to avoid reliability problems?

So can someone direct me to some definitive comments from a developer or evaluator (not just a response to an email) about the reliability of "casper-rw" compared to a conventional hard drive:
[LIST]
[*]Is EXT3 really the best choice?
[*]What is the usage pattern of the thumb drive?
[*]Has anyone using "casper-rw" damaged their thumb drive?
[*]Does write balancing make a difference, and if so, which thumb drive models have it?
[/LIST]
Thanks.

---

### Post by K0LO on 2006-12-11
bobl:

I can't direct you to the articles that you want, but can make the following comment.

Ext2 would be a better choice for the casper-rw partition for two reasons. First, there is no journaling. Second, the size required on disk is less. However, ext2 does not seem to function with the latest version of Ubuntu Edgy. Ext2 worked fine with Ubuntu Dapper. Maybe the developers will fix whatever bug is preventing Edgy from working with ext2 and we can go back to using it on the next release.

---

### Post by chettedeboeuf on 2006-12-13
Hi Kolo
It's ok for me. All is ok but I've a question :
- When I install softwares, wheres are they installed (on fat on or ext 3)

Cheers

ChEtTeDeBoEuF

---

### Post by K0LO on 2006-12-13
On the ext3 partition.

The FAT partition can even be made read-only if you want. Think of it as taking the place of a CD, which is read-only.

---

### Post by chettedeboeuf on 2006-12-14
Thank you for your answer Kolo
If I pur the FAT partition in 'only read' mode, it's to avoid mistake and making the LIVEUSB unreadable ?
How can I make this partition 'only readable'
Do you have a 'kubuntu for dummy'  guide ??

Cheers

ChEtTeDeBoEuF

---

### Post by K0LO on 2006-12-14
You really don't need to make the FAT partition read-only. If you accidentally delete some files you can always copy them over from the CD again.

If you really want to make the files read-only you can do it on your Windows PC as follows:

1. Select all files on the USB flash drive (Ctrl-A)
2. Right-click on a file and choose "Properties"
3. Under "Attributes" check the box for "Read-only"

There is some introductory information about Kubuntu on the desktop when you start the LiveCD version. That might be a place to start. It will probably be most helpful if you can find information about Kubuntu in your native language. Linux can be hard enough to learn at first even without a language barrier.

---

### Post by chettedeboeuf on 2006-12-15
Thank you Kolo
I will test this this week-end
I've found the french kubuntu forum 
But french people on this forum seems to be less strong as you

Cheers

ChEtTeDeBoEuF

---

### Post by amichair on 2006-12-17
Hi guys,

I've been trying to get a bootable USB stick working with grub using the info on this thread (namely post #158 ), but can't get it to work. I'm on Kubuntu Edgy, with a single hard disk (dual boot winxp/kubuntu) and a 2GB usb stick, which normally shows up as /dev/sdb.

First off, it looks like there has been some great work done by y'all in this thread, and I'd like to suggest that u open an Ubuntu Wiki page with the latest and greatest step-by-step howto you've come up with, and different variations where applicable. It sure beats having to read over 20 pages of forum posts... something like post #158 is a good start, but then there are later posts with updates (like the Edgy ex3 tip, fat16 instead of fat32, etc.), and also some missing data that needs to be taken from the LiveUsbPendrivePersistent wiki page, which adds some additional confusion to the game... in short, I think it would be great if u guys can get an official(?) howto with all this great info you've come up with.

As for my problem, after I set up the USB stick according to ur guidelines, when I bootup from the USB stick (via BIOS boot device menu), it says that the drive is not bootable. I've found that if I change the /dev/sdb parameter of grub-install to /dev/sdb1, and reboot, it seems to boot from the usb stick, but all I see is a blank screen with the four capital letters 'GRUB' in the top left corner, at which point the system hangs. So I think this is progress, since it's now finding grub, but still far from where I want to be :-)
What's the difference between those two different parameters to grub-install?

Another hint I found is that if I boot from my hard disk, with grub as well, then press 'c' for the grub console and then find /boot/grub/stage1, it shows up in (hd0) and (fd1) - it looks like the usb stick is being mapped to fd1 when it's selected in the bios as the boot device, even though it's being mapped to /dev/sdb (hd1) when I boot normally from the hard disk. I've tried changing menu.lst and devices.map in various ways to try and add fd1, but nothing works.

As for the Edgy ext3/ext2 bug, I've tried that too - no difference. btw has a bug been reported on this? any chance it'll be fixed in Feisty?

One final question - the wiki page says to partition the stick with a FAT32 partition, but in the detailed steps it says, in fdisk, to select 't' then '1' then '6', which according to the types list (when pressing 'L') is FAT16, and not FAT32. Is this a bug in the wiki page? should a different type be selected instead (0x0B perhaps? that's listed as W95 FAT32)? and how should the formatting commands be modified appropriately?

Well I hope this is enough info to start the troubleshooting... I've been trying to do this for 3 days now, and I would really appreciate some help from the gurus...

Thanks :-)

---

### Post by K0LO on 2006-12-17
amichair:

Has your PC been able to successfully boot from a USB device; any USB device at all?

What is the output of ```
fdisk -l
``` if you plug your USB flash drive into your PC running Linux? Please post the entire output including the header that describes the disk geometry.

---

### Post by amichair on 2006-12-17
Hi K0LO,

Thanks for the quick response :-)

I don't have any other bootable USB device around, so this is the first time I'm trying to boot from a USB device. Since it appears as an option in the BIOS menu, I'm assuming the BIOS supports this. Is there anything else I can check on the USB stick to prove bootability? are some sticks inherently bootable while others are not, or is it just a matter of proper partitioning/formatting/MBRing and should work on any USB stick?

Here's the output:


$sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7844    63005246+   7  HPFS/NTFS
/dev/sda2            7845        9652    14522760   83  Linux
/dev/sda3            9653        9733      650632+   5  Extended
/dev/sda5            9653        9733      650601   82  Linux swap / Solaris

Disk /dev/sdb: 2048 MB, 2048901120 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         340      685408+   6  FAT16
/dev/sdb2             341         992     1314432   83  Linux

---

### Post by K0LO on 2006-12-17
[FONT=Verdana][SIZE=2]amichair:

Booting from a USB flash drive is one of life's unsolved mysteries to me. A lot depends on the PC BIOS. I don't pretend to understand all of the nuances of this topic but from what I've read this is still a work in progress. There have been some efforts to standardize but at the present time it can be hit or miss.

The first thing I would do is to explore your BIOS setup menu and see if there are any settings that affect USB booting. Some devices identify themselves as USB-zip and others as USB mass storage. Sometimes this is called "Legacy USB Support". If you can find any settings, try them out. Also, if you have access to another PC at work or at a friend's house, try your drive in their PC.

[/SIZE][/FONT][FONT=Verdana][SIZE=2]Each PC BIOS can also report the drive geometry differently. For example, your 2 GB drive is reported as having[/SIZE][/FONT][FONT=Verdana][SIZE=2] 64 heads, 63 sectors/track, 992 cylinders. My 2 GB SanDisk Cruzer Micro drive is reported as having [/SIZE][/FONT][FONT=Verdana][SIZE=2]255 heads, 63 sectors/track, 249 cylinders by fdisk. Does this matter? I don't know.

I think I would try formatting the first partition as FAT32 (0x0c). This may have something to do with the limitations of large disks and certain BIOSes with FAT16.

Also, when you install GRUB it is easiest if you install it to the MBR (Master Boot Record, /dev/sdb). If you install it to the partition boot record (/dev/sdb1), then you must have a standard MBR on your drive. At this point you don't because it was written over by GRUB on the first install.
[/SIZE][/FONT]

---

### Post by amichair on 2006-12-17
Funny, mine is also a SanDisk Cruzer Micro...

I'll try the legacy USB bios settings, and a different pc (when I get a chance). So the wiki page's tutorial is wrong in saying to use fat16? the text says fat32, but the instructions lead to fat16, which is one of the things that got me confused. I hope the formatting command is correct for fat32 as well.

btw what's a standard MBR? how would I get one there if I wanted to try this alternate configuration? and do u maybe have some clue as to why I got that hanging "GRUB" screen when I grub-installed on /dev/sdb1?

Thanks again!

---

### Post by K0LO on 2006-12-17
I'm not sure why GRUB got hung up. Maybe has to do with disk geometry?

A "standard" MBR is the one used by Microsoft since the early days of DOS. It is small, extremely simple, and dumb. Upon boot it searches the partition table looking for a partition with the "boot" flag set. Upon finding one it chainloads to the partition where a bootloader is supposed to reside.

To get one you would format the drive with DOS tools (fdisk). There is also a tool from HP that will format a USB flash drive. Partition Magic will also work. But for what you are trying to do, installing GRUB to the MBR is the simplest solution.

---

### Post by xyz on 2006-12-19
> **shubox357 said:**
> Is there any way ubuntu can be run live from a USB drive?
[How to install Ubuntu Edgy to USB, to boot from any USB bootable machine]("http://www.ubuntuforums.org/showthread.php?t=308027&highlight=install+external+drive")
You'll need to set your BIOS to boot from external HD.
Check it out. You may want to install.

---

### Post by zakhooi on 2007-01-10
Hi,

I've got a nice customized ubuntu config on my USB stick and I was wondering whether it's possible to make an image of both partitions as a backup.
Of course the images should be in a format so that they can be dumped on a stick again.

Any recommendations for the right procedure? (I was thinking about dd but am not sure what the correct options are).

Thanks in advance

---

### Post by K0LO on 2007-01-10
zakhooi:
 
Yes, you can use DD to make a backup and to restore the backup later. If you want to just copy the entire USB drive including both partitions to a single file, do the following:```
dd if=/dev/sdb of=/home/username/image.bin
```
In the above instruction, substitute the device name for your mounted USB flash drive if it is different from **sdb** and use whatever filename you want for the output file.
 
To restore the backup image do this:```
dd if=/home/username/image.bin of=/dev/sdb
```
The above will copy every byte on the USB flash drive to the specified file so it will take a while. Eventually you will see an error message when there are no more bytes to copy. A 1 GB flash drive will create a 1 GB image file since there is no file compression going on here; just a byte-for-byte copy.

---

### Post by zakhooi on 2007-01-10
Thanks for the reply.
The plan I had was to do the same but then for each partition seperatly.

Now the question is which method is the best?

When making a single dump into one file of the entire stick you don't need to configure partitions before restoring to a stick.
In case you make separate dumps of each partition you need to configure partitions on the stick you want to dump to.
I guess that's the only difference between the two methods.......

At the other hand, restoring for instance just the 'casper-rw' or 'edgy/dapper' partition might become handy in some cases ......

---

### Post by K0LO on 2007-01-10
Yes, you can do that also. Just substitute the name of the partition in the dd command. For example, if your drive is /dev/sdb then the first partition is /dev/sdb1 and the second is /dev/sdb2.

---

### Post by zakhooi on 2007-01-10
> **K0LO said:**
> Yes, you can do that also. Just substitute the name of the partition in the dd command. For example, if your drive is /dev/sdb then the first partition is /dev/sdb1 and the second is /dev/sdb2.

I know that procedure, but I was wondering what method is wise to choose.....
I think I'll just make a backup using both methods...

---

### Post by manatlan on 2007-01-15
I followed the wiki : [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
and I had installed a livecd edgy on a HDD USB ! And it works like a charm !
(i'd just a trouble, it started to boot by prompting "MBR FA:" and nothing more ... so i made the partition bootable, and it goes well !)

I can configure it, and make it up-to-date ! All is persistant !

When feisty will go out ... do you think it will be dist-upgradable ? or should we just reinstall the feisty livecd on the 750mo fat32 partition ?

---

### Post by jonnnny on 2007-01-24
Hey all, thanks for the great tutorial!

Just wondering - why do we need to use the HP Drive Key utility to format the USB key?
Could we just use right-click->format in Windows Explorer since it still offers FAT16/FAT32 format?

Does the HP software add boot functionality to the drive or something? Just curious.

Jon

---

### Post by sikandarinux on 2007-01-24
Hi guys.

It seems to me there's an easy way to install onto a usb drive a linux distro, and, of course, ubuntu. Just take care of the GRUB final step using the ubuntu alternate install CD. Instead of directly installing GRUB, you should avoid that step, execute a shell in the installing menu, and understand what /dev/sd? is your usb drive. Then install the GRUB, finish the main setup of ubuntu and restart. Then the GRUB will boot at the wrong drive, but reading the GRUB manual is very easy to fix it up at the main boot of your pc.

I would like to ask if anybody knows about the casper package, so we can go further and make a live usb disk which can be plugged in any pc and work fine.

Well what I wrote is very synthetic I'll drop a better explaination if you guys are interested.

Have fun..

---

### Post by tenjin1 on 2007-01-25
Thanks Kolo and Andrew and the many others for this How to.

I have been plugging away at this since last night and tonight I have finally got this to boot from my 1gig PNY USB flash drive with Ubuntu Dapper! I used [http://ubuntuforums.org/showpost.php?p=1229101&postcount=158]("http://ubuntuforums.org/showpost.php?p=1229101&postcount=158")and [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"). Used the GRUB install method...for some reason the syslinux method would not work for me, trying many times on Ubuntu and XP. At first I was getting GRUB Errors 17 and 15. Seems when all is done (or maybe after partitioning and formatting) you have to reboot first with your USB drive out of computer! and also make sure your (hx,y) in menu.lst matches that of your (hx,y) device.map. The reboot after the grub install w/ usb drive out of machine, is what resolved the GRUB Errors for me. (for now)

Upon boot into Ubuntu Live Desktop (Persistent) mode (the top of menu.lst)...my X server crashes (I'm sure this will depend on different computers hardware I'm using it on) and doesn't seem to drop to a shell afterwards. So I use the 'Safe Graphics Mode' option (3rd one down on menu.lst) and it works great! 

...My question is...Is the Ubuntu Live Desktop (Safe Graphics Mode) option Persistant???:-k 

Also...someone could actually make a .zip of all the contents on the 1st partition (/dev/sdb1) and post it to help beginners in the install and then they can do all the configuring from there.

---

### Post by Nummymuffin on 2007-01-25
I read this entire thread several days ago and have since encountered a problem that I'm not sure was ever addressed here.  Maybe I missed it though.

I have a 2GB PNY Attache, formatted it using that HP utility, got rid of the awful included U3 software and still get a blinking lower case J whenever I try to load various distros of Linux.  I haven't yet tried to load Ubuntu on it, but I figured if these ready-made, downloadable  pen drive OSes won't work I probably won't have much of a chance of Ubuntu working either after all the work I'd do to get it on the drive!   

I really don't know where else I can ask, but has anyone else had this flashing J problem?  What causes this and does anyone know how I can fix it?  I run Windows XP and my BIOS tells me I have the ability to boot from USB and removable drives and I had it set as such.  I don't quite have enough experience using Linux on a daily basis to be able to fix a lot of things myself but I do catch on quickly... just to give you an idea.  I'm not a Linux power user but I do follow directions well.  :D   

I'd like to be able to run Ubuntu on my 2GB PNY Attache because it's such an elegant OS... if only I could get past that flashing j!  I hope I won't be stuck running it on a CD.  I'm wary of installing it on an actual hard drive because I've had issues in the past decade with Debian, Red Hat and OpenLinux all dying on me within two weeks of install, having some awful, unrecoverable hard drive error I couldn't figure out by reading the manual.  That is an other issue entirely but I felt it was worth mentioning as it's my main reason for wanting to run an OS off a flash drive... it seems less messy somehow and I won't have to worry about lost data on my real hard drive.

Anyway, maybe I missed a simple step somewhere?  I did not partition the USB drive but I really don't think that would cause the flashing j problem, would it?  I would figure that formatting it for Linux (Fat32) would be enough because the partition was meant for the persistence feature, no?

Any help or advice would be much appreciated!

---

### Post by tenjin1 on 2007-01-27
> **Nummymuffin said:**
> I have a 2GB PNY Attache, formatted it using that HP utility, got rid of the awful included U3 software

I had the dreaded U3 Launch pad sofware on my USB pendrive too! It is very annoying. [HERE]("http://www.jwjkp.com/U3_Uninstaller.exe") is the uninstaller for it. Which I'm sure alot of people can google it, but it's here if anyone needs it. :D

Also...here is instructions to install [XUbuntu USB]("http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610") on a USB pendrive, that has all the files in a .zip as I mentioned in my last post someone should do.

---

### Post by Nummymuffin on 2007-01-27
Ooh, thank you so much for this link!  I'll try it out and hopefully the dreaded flashing J won't happen again.  :D

---

### Post by laidback on 2007-01-28
Have a look here, it wont be the complete answer but may point the way.

[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

---

### Post by uboltun on 2007-01-29
> **bernstein said:**
> If you want to make a live USB-Pendrive/USB-Stick/USB-HDD you have to follow the [LiveUSBPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") wiki (SYSLINUX) or [this]("http://ubuntuforums.org/showpost.php?p=1229101&postcount=158") Post (GRUB)!


If you want to install a LiveUbuntu to a fixed disk in your computer, follow my post and it should be /dev/hda? (when disk is IDE/ATA) or /dev/sda? (disk is SATA). You'll have to install/run gparted and figure out the correct device (hda1,hda2,...sda1,sda2,...). (I won't not answer questions about gparted - there's plenty of info about installing/using it around!)

**two more things :**
- if you add/remove disks from your computer the devicenumber might change!
- following my post will bypass LiveUbuntu's routines of figuring  out the device on its own! its a simple and probably "ugly" hack.

> **bernstein said:**
> The "LiveCD on a USB Pendrive" will work on most computers ubuntu runs! I being a liveCD it tries to detect your hardware on each boot...

besides of being small this is another benefit from a "liveCD"!!!


I was looking for a solution like this for my problem , and I think it might actually work (trying it right now). 
On my PC I do not have USB boot , so I created a bootable CD that loads the kernel and mounts the USB drive. 
I followed this tutorial [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB). With casper things are getting a bit more complicated and I am not happy about changing the script at all. 
If you guys found a good solution - let me know! I have invested a whole weekend on this, and my wife is looking angry at me.

---

### Post by Nummymuffin on 2007-01-30
Well!

I followed all the instructions from a few posts earlier and everything went smoothly when I partitioned my USB drive while running Xubuntu.  I extracted the files as required and rebooted... and the same exact thing happened.

What happens is it accesses the USB drive -- I see the light come on -- and a lower case j appears with a blinking cursor to its right, on a black screen.  This is all that happens and I rebooted several times with the same results, even disconnecting and reconnecting the pen drive to see if that would help matters.  I switched USB ports and even disabled another USB hard drive I have just to be certain none of those are affecting the pen drive.

I'd sure love to know why this is happening.   :cry:

---

### Post by hrp2171 on 2007-02-06
This is so cool. I followed the post on page 20 of this thread, and was able to get Kubuntu 6.06LTS on both my 20gb USB HD and my 1gb USB stick.  :guitar: 

Now I'm looking to further strip files from the first partition.  For example, all the *.deb files used for installation to HD can go.  It'll make more space available on partition 1 and I won't have to get rid of OpenOffice.

Also, I would like to secure the USB key with password for login in.  As it is, anyone who finds/takes the key from me, can just plug it in and get to all my bookmarks, browsing history and personal files, etc.

---

### Post by mysticmarks on 2007-02-18
[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")  This has a great ubuntu usb drive setup instruction set. there is one important error in the instructions. once you are doing the mk.vfat and mk.ext2 instructions it does not tell you to umount your "sda2" before the mk.ext2 option. I have added that information to this copy of the install instructions, so do so. This install works wonderfully, i was able to save back all changes and files without anything special. It works just like a standard installed setup. This install is Xubuntu. it is done so that it will fit a smaller drive. It is also setup to not autosearch for updates. this is because the updates will put you way over the 1GB stick requirement. I was able to setup the not free codecs etc to play CSS dvds and such. i also was able to set up a few other smaller goodies. if you do use the 1 gig instructions just add updates that are small. also run apt-get clean at intervals during updates. If you use a larger pen drive, say a 2 or 4 GIG then you should be able to do all the updates and install most other wanted add ons. You also should be able to switch to other formates such as Gnome or KDE if you have the room. Make sure to uninstall the Xfce in these cases. extra room counts! This tutorial only extends a 2 partition setup because it will fit the 1GIG pen drive. I would suggest a third fat 32 partition for use as a standard pen storage drive on other OS's. The pen drive linux website is wonderful! be sure to stop by and pass on your thanks in what ever way you choose. They have other distros there as well. They also have instructions for windows users to setup a linux pendrive without a linux box to work from. MAKE SURE YOU NOTE WHAT YOUR PENDRIVE IS LISTED AS!!
(mine was sdf not sda) my hdd was actually sda instead of hda.

The tutorial:

Insert a 1GB or larger USB flash drive 

Open a terminal window and type sudo su 

Now type fdisk -l to list available drives/partitions (note which device is your flash drive typically /dev/sda) 

type umount /dev/sda1 (replacing sda1 with your flash drive partition) 

type fdisk /dev/sda (again replacing sda with your device)
 
type p to show the existing partition and d to delete it 

type p again to show any remaining partitions (if partitions exist, repeat step 3) 

type n to make a new partition 

type p for primary partition 

type 1 to make this the first partition 

hit enter to use the default 1st cylinder 

type +700M to set the partition size 

type a to make this partition active 

type 1 to select partition 1 

type t to change the partition filesystem 

type 6 to select the fat16 file system 

type n to make another new partition 

type p for primary partition 

type 2 to make this the second partition
 
hit enter to use the default cylinder
 
hit enter again to use the default last cylinder
 
type w to write the new partition table 

Type umount /dev/sda1 (replacing with your partition) to ensure the partition is unmounted. 

Type mkfs.vfat -F 16 -n USB /dev/sda1 to format the first partition (replace sda1 with your partiton) 
“Alternately you can try mkfs.vfat -F 32 -n USB/dev/sda1 if your system doesn’t boot the drive”. 

Type umount /dev/sda2 (replacing with your partition) to ensure the partition is unmounted. 

Type mkfs.ext2 -b 4096 -L casper-rw /dev/sda2 to format the second partition (replace sda2 if necessary) 

Remove and Re-insert your flash drive 

Download the USBEdgy.zip and select the option to open with Archive Manager 
Once the download has finished, use the Archive Manager to “extract” the contents of the zip your USB partition. 

Back at the terminal, type sudo apt-get install syslinux 

Type sudo apt-get install mtools 

Type syslinux -sf /dev/sda1 (replace sda1 if necessary) 

Reboot your computer and set your system BIOS to boot from USB-HDD or USB-ZIP. Also set the boot priority if necessary. 

Article Source: [http://pendrivelinux.com/](http://pendrivelinux.com/)

---

### Post by Finnerty01 on 2007-02-21
I've been able to boot Ubuntu Edgy from a 2GB USB. The USB drive has two partions, the first is 1.6 GB and FAT16 and the second is named casper-rw and EXT2. 

The problem is that booting off my USB doesn't seem have persistent mode, and I can not add new programs (at least they do not stay the next time I boot). I'm drawing a blank at what I could keep changes to settings. Any help would be greatly appreciated.

---

### Post by K0LO on 2007-02-21
Finnerty01:
 
When starting, don't forget to type the kernel argument "persistent".
 
There seems also to be a bug with Edgy that prevents this from working with ext2 partitions. Try reformatting your second partition with ext3 instead of ext2. That worked for me.

---

### Post by Finnerty01 on 2007-02-21
when typing persistent at boot screen, the message returned is "no persist.ent command found in kernal"

The same happened after converting to EXT3. I appreciated the quick response.

---

### Post by K0LO on 2007-02-21
Finnerty01:

Take a look at my post #100 in this thread and replace your syslinux.cfg file with the version that I posted. It's attached as a text file to the end of the post. It will let you start up into the persistent mode without typing the word on the command line. Perhaps that will do it for you.

---

### Post by maraja on 2007-02-23
Hallo from Italy!

first of all let me thank you so much everyone for your effort and patience. I have followed the #100 post instructions but, when trying to boot the usb pen, I am facing a new problem.

First of all two links were not copied during the installation:
dists/edgy/stable
dists/edgy/unstable

Anyways a note on the wiki stating there is not problem in missing these.

The first time I booted the system it went trough after the bouncing orange indicator screen (with the ubuntu logo in the middle) presenting a black screen (text mode) with only the flashing cursor on the top left position. I waited about 5 minutes and then rebooted using ctrl-alt-del.

Since then the USB is loaded and the usual selection menu is presented. I press Enter and the black screen with the bouncing progress indicator is shown but, after a while the indicator suddenly stops and I am not even able to reset the system (ctrl-alt-del). 
All I can do is to turn it off using the main switch... :( 

I have also tried to install syslinux 3.20 and 3.36 with no better results.

Booting from the same CD I used to copy the files works with no problems.

System
Ubuntu 6.10 live
Toshiba Satellite SM30
768Mb RAM
SanDisk USB 1Gb

Is there anything I can set in the boot sequence to get a clue about where the procedure hangs?
Do you have any clues to help me?

thank you so much again!

---

### Post by maraja on 2007-02-24
*Update*

I tried this morning to reinstall using GRUB this time. Unfortunately the problem is still there, after I select the first grub menu item I am presented with the black screen showing the ubuntu logo and the bouncing progress bar. 
It looks like the system is loading but, after few minutes, all I get is a black text screen with the cursor flashing.

Hope to be able to run an USBbuntu soon...

---

### Post by maraja on 2007-02-24
Update v2

After getting the black text screen I left the system untouched for about half an hour, just curious to see if it could take that long.
Nothing happened and I pressed CTRL-ALT-DEL to reboot: before the reboot process started I was able to spot some lines on top of the screen stating something like:
usb ..... device description....

hope this can give you a clue on the issue.

thank you.

---

### Post by MrDetermination on 2007-02-24
I'm new to Linux/Ubuntu and trying to learn on a work machine (which I can't mess with the HD on... ergo need to boot to CD/USB).  I have read [this]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") many times, the pendrivelinux.com tutorial many times, tried it from Windows and from booting to a Xubuntu CD then trying the pendrivelinux tutorial commands.  I've tried various versions on syslinux, etc.  No luck.  I can run in the live environment but no matter what when I try to go persistent I end up with the useless blinking cursor after the splash screen.

This is the case with my company thinkpad T42 and my girlfriend's Vaio.

Guess I'll try w/Dapper tomorrow.

---

### Post by wislon on 2007-02-25
Hi maraja,

I had a similar problem with my ubuntu loading from my USB hard disk, it basically froze where you are. It would say something like "waiting for file system..." or similar and just hang there.

I made two changes, which helped me figure out what was going on. When the grub boot menu came up, I went down to the line that shows all the boot parameters (2nd one), and hit 'e' to edit it. I removed the 'splash' parameter (which you will have if you are seeing the progress bar). I also removed the 'quiet' parameter. 

Press 'Enter' to get back to the menu, and then press 'b' to boot.

This basically boots up the PC with all the stuff and details you don't usually see, in text mode, where you can see what's being loaded (or not) and where it's gotten stuck. Mine was getting stuck on some or other kernel panic about something not synching, and after searching this forum for that error, it turned out to be something to do with my power management. The solution was to add a parameter called 'acpi=force' where I'd taken out splash and quiet. This acpi problem has only been an issue for me on Edgy.

Hopefully that will point you in the right direction! :)

(note that this edit of the grub parameters is NOT persistent, it'll be reset the next time you boot). If you want to make it persistent, I suggest you physically got and edit the /boot/grub/menu.lst (when you finally get up and running).

wislon

---

### Post by maraja on 2007-02-25
Hallo,

meanwhile I tried all the other boot entries (livecd without persistent, memtest and the xforcevesa) and all of them work. So I now guess the problem is with the casper-rw partition. Also tried to make it ext3 but with no success.


@MrDetermination: 

I do not think its a Dapper/Edgy problem. At the beginning I had to play with all different file systems to be able to see, at least, the initial menu.
My Toshiba+SanDisk liked the boot partition to be FAT32 and the writable one to be EXT2.

Have you tried to boot the other options? do they work? 

Also: do you see the boot menu? 
I lost two days trying to do this installation on 2 other USB sticks (8Gb LaCie and 2Gb KData myflash) just out find out that the Toshiba does not like to boot from them at all! (Now I know where to shop for USB sticks in the future).

@wislon:

While waiting to get some comments on this forum I started doing some trials and edited my menu.lst to remove both the quiet and splash parameters ;)
Now I can see the following messages issued right before freezing:

> 
usb 3-2: new high speed usb device using ehci_hcd and address 7
usb 3-2: device not accepting address 7, error -71
0.0.0.0: rejecting I/O to dead device
FAT: unable to read inode block for updating (i_pos 21439723)


Note that there are other lines just before these ones showing some temptatives to use the usb device on different addresses (6, 5, 4, etc). Unfortunately there is no way to scroll the list up.

Curiously after the boot Ubuntu was able to write the following files on the casper-rw disk:

_{directories}_
lost+found (*1)
rofs
var
var/cache
var/cache/debonf (*2)
var/lib (*2)
var/log
*1: this is created by mkfs.ext2
*2: I am unable to open this dir

_{files}_
/cdrom
/etc
/home
/tmp
var/log/faillog (24Kb)
var/log/lastlog (294Kb)

I was able to send me an email with the last two files as it was not possible to open them in Linux. Checked for contents but they both only includes returns (newline, "\n").

So somehow Ubuntu was able to access the casper-rw disk... making me even more crazy.

I am out of clues at the moment and full of hope to read the right clue on this great forum :)

---

### Post by tormod on 2007-02-25
Hi,
I am trying to make a Ubuntu 6.10 Desktop USB stick. So, exactly like the Desktop CD, except on a bootable USB stick. Since isolinux won't work on fat16, I use syslinux. I have converted isolinux.cfg into a syslinux.cfg (with everything flat on the top directory). The USB stick boots fine, but there's one issue (making me spend many a desperate hour):

The menu text specified with "menu label" does not show up. I only get the LABEL itself, so the list I can choose from is: live, xforcevesa, check, memtest, hd. It works, but is not very newbie-friendly.

If I take away GFXBOOT bootlogo, I get the full menu texts, but then I don't get the Language and Keyboard menus, of course...

Is there a known conflict between the Edgy  gfxboot/bootlogo and the menu/label command?
Please help!
Tormod

edit: Another thing that is missing is the Ubuntu colours, I only get blue, black and white colours. Not so dramatic though.

ps. my project (incl docs&src): [https://wiki.ubuntu.com/SwissTeam/OpenExpo2007/USBStick](https://wiki.ubuntu.com/SwissTeam/OpenExpo2007/USBStick)

---

### Post by mellevyys on 2007-02-28
Hi

I have Xubuntu installed on my USB pen drive. I did it with pendrivelinux.com manual. Now Xubuntu works fine in ext2-partition and other (fat16 and 700MB) partition have some files and directories. Is it possible to delete files from fat16-partition or does Xubuntu need those files. And if it uses, witch files? Like casper directory is over 500MB...

I want to use pen drive also with XP.

Thanks!!

---

### Post by mellevyys on 2007-02-28
Hi

I have Xubuntu installed on my USB pen drive. I did it with pendrivelinux.com manual. Now Xubuntu works fine in ext2-partition and other (fat16 and 700MB) partition have some files and directories. Is it possible to delete files from fat16-partition or does Xubuntu need those files. And if it uses, witch files? Like casper directory is over 500MB...

I want to use pen drive also with XP.

Thanks!!

---

### Post by tormod on 2007-02-28
> **mellevyys said:**
> Now Xubuntu works fine in ext2-partition and other (fat16 and 700MB) partition have some files and directories. Is it possible to delete files from fat16-partition or does Xubuntu need those files. And if it uses, which files? Like casper directory is over 500MB...

You definitely need a casper directory and some other stuff to be able to boot Xubuntu. If all the clutter is a problem, you can mark all files "hidden" in Windows.

---

### Post by trance_monkey on 2007-03-02
hi, I'm completely new to Ubuntu and any Linux OS for that matter. So far, I love it - I have it on my desktop and laptop now. I wanted to see if I could get a bootable USB Flash drive for it though for kicks, showing it off and/or troubleshooting (desktop's having a little problem).

Doing this from my laptop, I plug my 2GB flash drive in, and I follow along with this guide:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

and I keep getting:

WARNING: Re-reading the partition table failed with error22: Invalid argument.
The kernel still uses old table.
The new table will be available at the next reboot. (You can reboot flash drives?)

The steps I took:

sudo fdisk -l
sudo fdisk /dev/sda1 (that's mine)

Following the guide, I created two partitions: One with FAT16 and one with W95 FAT32 (that's what the guide seems to say to do...). 
I end up with /dev/sda1p1 and /dev/sda1p2

I activate both, and hit w to save, that's when I get that WARNING error.

I do another *sudo fdisk -l*

And I do not see the two partitions, I only see the /dev/sda1 that I saw in the beginning!

Attempting to continue on with the guide anyway, I try

sudo mkfs.vfat -F 32 -n edgy /dev/sda1p1 

and, as I figured, it couldn't be found. 

I've re-done all those steps a few times, re-inserting the USB card since it says it needs to 'reboot', and even rebooted my own laptop. But, alas, nothing.

Help?

EDIT:

I got it working =)

In kind of a fubar'd way though.

In Ubuntu I went and set the partitions up, like stated above, and ignored the fact that **sudo fdisk -l** didn't recognize it.

I put the USB card into my WinXP machine, it saw one volume, so I formated it with FAT32.

I put the USB flash card back into my Ubuntu machine, and it suddenly saw it as two partitions!

It was a 'wtf' moment for me, but I'm happy it worked.

Anyone have an idea why? I'd be curious to know why that fixed it.

---

### Post by K0LO on 2007-03-02
Hi trance_monkey:
 
The warning message is generated by the Linux kernel because it has detected that you have modified the partition table on a mounted drive.
 
Next time you see the warning message, try unplugging your USB flash drive and then reinsert it. I think that upon reinsertion, the drive will be automounted, a new filesystem table (fstab) will be generated and then you should be able to see it with fdisk -l. If so, continue on with the steps in the Wiki procedure.

---

### Post by K0LO on 2007-03-05
> **trance_monkey said:**
> In Ubuntu I went and set the partitions up, like stated above, and ignored the fact that **sudo fdisk -l** didn't recognize it.
I put the USB card into my WinXP machine, it saw one volume, so I formated it with FAT32.
I put the USB flash card back into my Ubuntu machine, and it suddenly saw it as two partitions!
It was a 'wtf' moment for me, but I'm happy it worked.
Anyone have an idea why? I'd be curious to know why that fixed it.
trance_monkey:

See my previous reply. It was the removal and reinsertion of the flash card that enabled Linux to recognize the drive and let you list the contents. After a change to the drive (like creating a new partition), the fstab is invalid until refreshed. This will happen when you re-insert the card.

---

### Post by stevet1 on 2007-03-09
I think I'm having the same issue as Maraja. 

I've created my 2 partitions fine. The boot partition is good, I'm able to boot into Ubuntu no problem, at least on the first boot.  The problem is with the casper-rw partition. The first time the casper-rw partition is formatted, I get absolutely no errors on bootup. I've used both ext2 and ext3 filesystems for the casper-rw. However, once I shut down, get these types of errors, right after

"Unmounting temporary filesystems" these occur:

Buffer I/O errors for sdb2
ext2-fs error sdb2 (unable to read inode block)

and I get a ton of these errors in regards to sdb2 (or the casper-rw partition)

If you then examine the casper-rw partition from by booting from liveCD, there has been some files that were written to the partition.

Now when I reboot into the USB drive, on startup I get unverified filesystem error, recommend using e2fsck. I now have to reformat casper-rw in order to boot up without errors.

Obviously there is someting wrong with my casper-rw partition. Any ideas how I can get Ubuntu to access/use it correctly? Thanks.

---

### Post by linuxbuddhist on 2007-03-12
Hello Everyone,

I've read through a lot of these posts and just wanted to first say hello as a new user, secondly that I just installed Edgy on a 4gig Sandisk Micro Cruzer flash drive directly from the cd without having to deal with casper.

I manually partiioned into boot, root, and swap and installed from the live cd (alternative) and everything went fine.  I did make the mistake of telling GRUB to look in the wrong partion for the  startup files but a simple change in the /boot/grub/menu.lst file to the correct one and rebooting did the trick and it was quite simple.

The only thing it doesn't want to do is load Windows XP (well, who does really) but thats not a big issue.  If I want Ubuntu running I'll startup with the flash drive plugged in and if not, I won't.

Best of luck to everyone and it will be nice to participate in these forums.

BTW: Anyone looking to hire a network, system admin or tech support manager? :)

---

### Post by mojo on 2007-04-01
I succeed making my USB bootable but ambiguity remains, why do we need to create 2nd partition and lable it casper-rw? What is the use of it?

Another question is why don't we use ext2/3 for 1st partition and boot up directly from it. This will add more protection for the USB, since people can't mis-delete some important file on the drive since Windows can't read ext fs. I've done some research and known that syslinux only on vfat fs. However there is extlinux that can be boot from ext2/3 fs. Does any know have success with extlinux?

---

### Post by larytet on 2007-04-15
> **TiredBird said:**
> Now I'm frustrated again.

I just tried the same USB stick on my laptop, numerous different ways, (see below), and was unable to get it to boot or be recognized. The BIOS gives me a way to boot from removable media without going into the whole BIOS setup thing. You'ld think it would work.

There is an interupt in the boot sequence that allows you to select your boot method. (F12 at a certain point). I have three USB ports so I tried each of them. I tried different combinations of root, different sockets and even tried to boot it from the hard disk boot menu but couldn't get anything to work. This is a one year year old machine. It should work. The machine that did work is three to four years old!

install gparted
apt-get gparted
unmount USB using command 
umount /media/usbdisk
run gparted 
sudo gparted
choose USB drive (likely /dev/sdb1)
make sure that flags boot and lba are ON

---

### Post by larytet on 2007-04-15
> **K0LO said:**
> zakhooi:

I'm pretty close now to getting this to work but I'm still working the bugs out. I will post here when I get everything to work correctly.

My latest discovery is that I can make the persistent feature work if the second partition (casper-rw) is formatted with ext3. It's supposed to work with ext2 but it didn't seem to for me. The first partition was also supposed to work with FAT32 but I had to make it FAT16 to get it to work at all. So either something has changed since Dapper or else I'm doing something stupid.

While it's now working, I'm currently chasing down a problem. The casper-rw partition is just littered with hundreds of zero byte files with names like .wh_dir_opaque and variations (.wh.*). Every time that I restart in persistent mode, more of these are added. Over on the Knoppix forums they were discussing problems like that with their distribution, so I'm trying to track down their solution.

If you want to try this out, follow the wiki article [here](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) but instead choose FAT16 for the first partition and ext3 for the second, and use the Edgy LiveCD instead of the Dapper LiveCD.

if you use syslinux only version 3.2 and higher will work with FAT32
and it should be ext3 indeed

---

### Post by TiredBird on 2007-04-15
Larytet:

Thanks for taking the time to write your suggestions. As you will note from [ this post of mine]("http://ubuntuforums.org/showpost.php?p=1724671&postcount=209"), I gave up on this project several months ago. 

However, as I have not previously tried your suggestions, I may try again. I will have to start from scratch as I have overwritten all the stuff I had on the USB sticks previously so it is going to be a couple of days before I get to it.

I have the gparted live cd (0.3.3-0). I presume that will work as well. 

I am now using Kubuntu (6.06) instead of Ubuntu but I guess that shouldn't make any difference either. In fact it should now be possible to follow 'Kolo's directions exactly.

Thanks again. I will make a post to this thread telling how it works out.

---

### Post by K0LO on 2007-04-23
> **larytet said:**
> if you use syslinux only version 3.2 and higher will work with FAT32
and it should be ext3 indeedlarytet:

I didn't use syslinux at all when doing this; I used GRUB as the bootloader to start up directly into the kernel.

Do you know why the casper-rw partition needs to be ext3?

---

### Post by K0LO on 2007-04-24
I just got a chance to try this with the new release of Feisty (7.04). FAT32 works fine for the main partition however persistence is broken with this release. A bug report has been filed by several people reporting this problem, and the developers acknowledged that they couldn't fix it in time for the release. See launchpad bug 84591:

 [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591)

I have to give credit to the developers for the LiveCD release of 7.04, however. Upon first boot my laptop came up with everything working properly; video, sound, power management, and networking including wireless. A quick click on the knetworkmanager tray icon brought up a dialog box to enter my wireless network's WPA-AES key and it connected immediately. Very impressive.

I hope the persistence feature can be fixed before the next release in October.

---

### Post by allforcarrie on 2007-04-25
[http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610 ]("http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610")
i didnt read all of this but i did find this.

---

### Post by hazzaboy69 on 2007-05-06
I am having problems with this, I have tried several turorials and it still doesnt work. I get the message Missing Operating System when I turn on my laptop. It is a fujitsu seimens and I am using a pny attache pro 1gb memory stick. Any ideas guys?

Does anyone know if there is somewhere I can download all the files as they should be on the usb stick which have allready been tested?

Thanks Harry

---

### Post by Carl Foxmarten on 2007-05-17
Hi, all, I've read practically this entire thread, and I must say that there are lots of good suggestions here.
I've been using Linux for about a year and a half to two years now, and Ubuntu/XUbuntu for most of that, so I do know a fair bit about using it.

Myself, I've installed the XUbuntu 7.04 LiveCD onto my 2GB flashdrive and have encountered only two problems:
1: Persistence (already covered here)
2: All PS/2 input devices don't respond.

It's as if the kernel or something at that level is just ignoring the PS/2 subsystem entirely.
If I plug in a USB mouse, it works just fine, but as I don't have a working USB keyboard I can't do enough fiddling around with it to see if I can find the problem.

The partitions are FAT16 and EXT2 (and I tried EXT3), copied the files over via Linux (admittedly from Dapper), but had to use the Windows version of Syslinux to get it working properly (otherwise it booted my first hard-drive's MBR, which started my main system, but stilll disabled my PS/2 ports :( ).

The PS/2 ports seem to stop working right after Syslinux hands things over to whatever it boots up, making debugging almost impossible... :(

---

### Post by fasaxc on 2007-05-28
Running with quiet and splash kernel options  turned off, my usb boot gets as fas as "squashfs: version 3.2-r2 2007/01/15 Phillip Lougher" but then just stops (no error message I can see). I've left it for ten minutes with no progress. I know it hasn't simply hung because removing a usb device adds a disconnect mesage for example.

Anyone have any ideas?

-Shaun

---

### Post by C.S.Cameron on 2007-06-08
I've installed Ubuntu on a 4G USB Traveler.
Works great. A portable O/S on a stick. Everything on the desktop as you left it on the last box you plugged it into.
Set Up:
Plugged in the dongle to my living room computer.
Ran bios and set dongle as primary hard drive, second to boot after CD.
Rebooted into CD. 
Did install, ejected CD and rebooted to see if it worked.
It did.
Took it to my office computer, It worked.
But no duel monitor.
Tried the Nvidia drivers, went thru several hours of hell, eventually reformatted and reinstalled.
I have learned to back up my xorg.conf file and am getting braver trying to get drivers working for the 8800gts.
Also wondering how to multi boot depending on the graphics card in the box, Nvidia, ATI or generic.
Cork

---

### Post by hsuominen on 2007-06-10
I have tried everything and looked everywhere and i still cannot seem to get my new 2GB SanDisk Cruzer Micro drive to boot Ubutu 6.10 Edgy. 

My bios is usb bootable and i have a fully working usb drive with pclinxos that works without problems.

I have bascially followed the tutorial at ([https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)) word for word and still nothing works. I have also searched google for answers but havent come up with anything useful.

I have tried rewriting the MBR using both install-mbr and lilo

I have tried both FAT16 and FAT32

The problem is that the usb drive is simply not detected at startup and my computer boots right into windows...

My biggest wonder is that my pclinux os usb drive works while my ubutu one does not. Effectively i have used the same version of syslinux on each so it cannot be due to that.

Ultimately this leaves us the drives themselves, the partions and filesystems (the one running pclinux os was never formatted in anyway, the files were simply copied over and syslinux took care of the rest), and the mbr... or smn else?

I would be very thankful for anyone able to point me in the right direction... 

Henri

---

### Post by K0LO on 2007-06-10
Henri:
 
It sounds like the drive is not bootable. Did you check the boot flag on the main partition? Please plug your USB flash drive into a machine running Ubuntu (or any other Linux distribution) and look at the output of ```
fdisk -l
```If you run that command as a non-root user it should only list the partition structure of removable drives. Check the output and make sure that the boot flag is set on the main partition. If it isn't you can just run cfdisk to set it.
 
If that's not it then you might want to resort to something a little more drastic. Some USB flash drives are formatted strangely or contain hidden "Secure Vault" partitions and special software. You could first zero the entire drive to get rid of any of these and then start over.```
sudo dd if=/dev/zero of=/dev/sdx
```Substitute the appropriate device number in place of "sdx" in the previous command, but do be careful. You don't want to accidentally zero the wrong drive (for example, your hard disk). Let the command run until it completes. It may take 10 - 15 minutes to zero a 2 GB drive. When it reaches the end of the drive it will produce an error message. Before doing anything with the drive, be sure that all writes have finished by issuing a sync command.```
sync
```When that completes your drive is freshly zeroed and you may be able to get it to work if you try again.

---

### Post by hsuominen on 2007-06-11
yea the boot flag is set i checked that multiple times aswell...

I shall give the zeroing a go this afternoon

Thx for the help

---

### Post by iqag1060 on 2007-06-12
> **hsuominen said:**
> I have tried everything and looked everywhere and i still cannot seem to get my new 2GB SanDisk Cruzer Micro drive to boot Ubutu 6.10 Edgy. 

Is it at all possible that [U3]("http://en.wikipedia.org/wiki/U3") is causing your problems? Reformatting/partitioning usually will not get rid of this. Both [SanDisk]("http://www.sandisk.com/Retail/Default.aspx?CatID=1415") and [U3]("http://www.u3.com/uninstall/final.aspx") have removal apps. (Windows only)

---

### Post by hsuominen on 2007-06-12
ahh i never thought of this... i went on right to reformat my drive when i bought it and have never even seen a trace of U3. Doing a small search though i figured U3 should have been on my drive, and if it is i have no idea how to now remove it (spsedly it is somehow built into the firmware, and not on the flash memory itself)... The U3 uninstaller anyway does not recognize the device

---

### Post by hsuominen on 2007-06-12
I found the packaging of the Usb actually as it is relatively new... no mention anywhere of U3, did i get lucky?

---

### Post by K0LO on 2007-06-12
Zeroing the drive (per my previous post) will remove it.

---

### Post by hsuominen on 2007-06-13
Successfully zeroed the drive, partitions gone and left with a blank disk =) will have a go at reformatting tm evening as i have a physics exam to study for tonight...

Thanks

---

### Post by hsuominen on 2007-06-14
despite my efforts in zeroing and such.. no progress at all, usb is completely ignored at start up as before

---

### Post by K0LO on 2007-06-14
hsuominem:
 
Sorry to hear that. I am now suspicious that your PC may have problems booting from USB devices that are formatted as USB-HDD. Do you have access to another PC to try your USB key in? If it works in other computers then you are creating it properly and the problem is your PC BIOS not being able to boot from the USB-HDD format, which is the format that is created if you follow the steps in the Wiki article.
 
Your other USB key with PCLinux OS must have been created in the USB-ZIP format, which is an older format that may be bootable by your PC.
 
You could try looking in the BIOS setup screens on your PC to see if there are any options to select between USB-HDD and USB-ZIP formats when booting USB devices. Also try turning on and off "USB Legacy Support" to see if that matters.
 
Here are a couple of articles from DSL and Knoppix about the differences between USB-HDD and USB-ZIP:
 
[http://www.damnsmalllinux.org/wiki/index.php/USB_Booting](http://www.damnsmalllinux.org/wiki/index.php/USB_Booting)
[http://www.knoppix.net/wiki/Bootable_USB_Key](http://www.knoppix.net/wiki/Bootable_USB_Key)
 
A condensed summary is that USB-HDD is newer, uses the same partition structures as hard disk drives, and is needed for drives larger than about 1 GB. USB-ZIP uses partition 4 as the bootable partition, a different cylinder/head/sector (CHS) layout, and is only suitable for smaller drives. But only newer PC BIOSes can boot from USB-HDD.

---

### Post by C.S.Cameron on 2007-06-15
[QUOTE=hsuominen;2819531]I have tried everything and looked everywhere and i still cannot seem to get my new 2GB SanDisk Cruzer Micro drive to boot Ubutu 6.10 Edgy. 

I tried most everything I could read also.
I then unplugged the hard drives, got bios to set the thumb drive to boot second after CD.
Booted the Ubuntu CD, did an install and everything worked perfect, Two weeks of hard labor later I got the Nvidia drivers working.

2GB is probably ok to run the base system, but my 4GB filled up fast. today I am getting an 8GB.
Cork

---

### Post by hsuominen on 2007-06-17
Finally my computer is able to detect the drive after performing a full bios update (the problem seemed to be the USB-ZIP and USB-HDD)

However now my system hangs whenever I boot the "custom" option as described on 

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

However funnily enough the "live" option works... 

Once again im lost for ideas

Thanks for all the help so far!

---

### Post by hsuominen on 2007-06-17
this is wat i get when going through the boot in text-mode

"cp: unable to stat '/root/var/log/' : Not a directory"

---

### Post by K0LO on 2007-06-17
> **hsuominen said:**
> this is wat i get when going through the boot in text-mode
 
"cp: unable to stat '/root/var/log/' : Not a directory"
Sounds like you're making progress!
 
Check the "syslinux.cfg" file contents carefully. You might want to copy/paste from the wiki article.

---

### Post by hsuominen on 2007-06-17
problem is... thats exactly wat i did

---

### Post by hsuominen on 2007-06-17
stupid me... i did a copy paste without realizing that the tutorial was for dapper, and im using Edgy.. just had to replace ltsp.seed with ubuntu.seed...

---

### Post by hsuominen on 2007-06-17
Ahh same problem still... and i realized that the live option also had the link to inexistent ltsp.seed but it still worked so i cant be that... could it possibly be something to do with the persistent command? I mean thats the only difference between the two boots no?

---

### Post by hsuominen on 2007-06-19
Still the same problem.. and nothing seems to change it, any ideas? Anyone? I really am getting a little desperate here...

---

### Post by EagleRock on 2007-06-19
I'm not sure if you're trying to use Feisty for LiveUSB...

Did you check out this thread?

[http://ubuntuforums.org/showthread.php?t=427312](http://ubuntuforums.org/showthread.php?t=427312)

---

### Post by n_suess on 2007-06-19
Couldn't you just mount a virtual CD drive on a 1GB memory stick then "burn" the CD image to the virtual drive? Then you could just use it the same way you use the live CD.?

---

### Post by hsuominen on 2007-06-20
My problem is no longer the booting of the live CD from the USB.. that works fine... my problem is the booting of the live CD using the PERSISTENT mode, in which i am able to save settings, programs etc...

---

### Post by EagleRock on 2007-06-20
Which version of Ubuntu are you using?

If it's Feisty, Persistent mode will NOT work unless you do the proper steps.  Visit the link I showed you above.

---

### Post by hsuominen on 2007-06-21
I am using Edgy, though I tried Dapper aswell and that didnt work either

---

### Post by n_suess on 2007-06-21
My problem is no longer the booting of the live CD from the USB.. that works fine... my problem is the booting of the live CD using the PERSISTENT mode, in which i am able to save settings, programs etc...


Couldn't you just use a 1GB usb drive, and then use the left over space for your filesystem?

---

### Post by hsuominen on 2007-06-21
Well yes that is essentially exactly wat I am doing... look a page back or so for clarification, sorry for all the confusion...

---

### Post by pds on 2007-07-04
> **stevet1 said:**
> I think I'm having the same issue as Maraja. 

I've created my 2 partitions fine. The boot partition is good, I'm able to boot into Ubuntu no problem, at least on the first boot.  The problem is with the casper-rw partition. The first time the casper-rw partition is formatted, I get absolutely no errors on bootup. I've used both ext2 and ext3 filesystems for the casper-rw. However, once I shut down, get these types of errors, right after

"Unmounting temporary filesystems" these occur:

Buffer I/O errors for sdb2
ext2-fs error sdb2 (unable to read inode block)

and I get a ton of these errors in regards to sdb2 (or the casper-rw partition)

If you then examine the casper-rw partition from by booting from liveCD, there has been some files that were written to the partition.

Now when I reboot into the USB drive, on startup I get unverified filesystem error, recommend using e2fsck. I now have to reformat casper-rw in order to boot up without errors.

Obviously there is someting wrong with my casper-rw partition. Any ideas how I can get Ubuntu to access/use it correctly? Thanks.

Hi!

I have exactly the same problem as you. On the first boot it's everithing ok, but then, when I make a reboot, the ext2 partition gets corrupted.

Has anyone solved this problem?

Thanks

---

### Post by LuisC-SM on 2007-08-21
Hi.

Thanks a lot.

I got it working using your method. None of the wikkies worked for me except this method.
I used it with a 2 GB USB Flash Memory Stck and installed "Comfussion" (Ubuntu 7.04 based distro that works right out of the box with Compiz-Fussion effects).

I suggest you to update this howto as far as some softwre has been upgraded and there is no need to delete some files you are specifing. 

However, I must say that I used 2 computers to get this howto working, one with ubuntu and the other one with WinXP.

I must do it again when Ubuntu 7.10 comes out, so probabily 'll gve u details on what to change when I finished.

Regards

Luis

---

### Post by schaumkeks on 2007-09-21
> **pds said:**
> 
I have exactly the same problem as you. On the first boot it's everithing ok, but then, when I make a reboot, the ext2 partition gets corrupted.

Has anyone solved this problem?

This has been a problem for me, too. I'm using [Gutsy Tribe 5]("http://www.ubuntu.com/testing/tribe5"). I simply formatted the second partition with ext3 (replace X with the letter of your USB pen device!)
```
sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sdX2
```
and all went fine.

Bye, Sven

---

### Post by n00bWillingToLearn on 2007-10-05
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by LuisC-SM on 2007-10-05
> **n00bWillingToLearn said:**
> [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Easy but... how many have succeeded? (noobs)

the howto shown above is not really for newbies, in fact, I had a hard time to succeed with just half of the howto (Feisty), we need (noobs like me) something easier to understand, with apples and oranges :)

however, thanks for showing me a different way (tho it did not work for me :$)

Regards
Luis

---

### Post by rulixx on 2007-12-01
Did all the necc. actions and had success. Dapper persitent is running from a SD card 1GB

But following remarks:
1 I don't see the bootlogo, the file is in / of the card
  I tryed several settings in the syslinux.cfg but I get only the isolinux.txt 
Also I did'nt found any explanation of the line: GFXBOOT bootlogo
Is there some insight available.

2. IP and routing address is not stored on casper-rw
All other settings like mouse, country etc are set permanently.

KOLO did a good job, but has anyone the problem with the bootlogo?

rgds Rudi

---

### Post by mordy on 2007-12-25
Hi,
Since I'm also new I had this problem for a week
and then I figured:
I wrote
fdisk /dev/sdf1
I should have write 
fdisk /dev/sdf

The partitions name (before the w command issued) were as you describe /dev/sdf1p1 and /dev/sdf1p2

So this might be your problem also.

---

### Post by mamanmapillai on 2008-02-11
Hi,
 
  I am using ubuntu 6.06LTS .While I boot my system I am getting this error.

Begin: Runnung /scripts/local-premount...
Done
Kjournald starting. commit interval 5 seconds
EXT3-fs:mounted filesystem with ordered data mode.
Begin: Running /scripts/local-bottom.....
done
done
Begin: Running /scripts/init-bottom ...
Done


Like this I am getting error. 

Please help me to solve this problem

---

### Post by d3adp00l on 2008-04-01
I have an 8b corsair usb drive, That installs xubuntu 7.10 just fine, the only hitch is boot up, which it normally tries to install grub to hd0 which is my 400g sata drive, which I dont want it to do. I used fdisk to make the first partition on the usb drive active, (3g) and the second is a primary part. for /home. 

If this doesn't work, does anyone know how to move grub from the sata drive to the usb drive, or how to delete it from the sata drive and install it on the usb? either of those is guaranteed to make the usb bootable. thanks for any ideas.

---

