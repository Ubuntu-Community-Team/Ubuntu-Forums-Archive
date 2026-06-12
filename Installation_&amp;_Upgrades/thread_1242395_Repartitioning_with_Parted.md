---
title: "Repartitioning with Parted"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by Raff1 on 2009-08-17
Hello! I already have Ubuntu 9.04 and now I am trying to install Win XP again using my unallocated space. I got this output from Parted:

```

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  5996MB  5996MB  primary   ext3         boot 
 2      5996MB  320GB   314GB   extended               lba  
 6      5996MB  86.0GB  80.0GB  logical   ext3              
 7      86.0GB  87.0GB  1003MB  logical   linux-swap        
 5      178GB   320GB   142GB   logical   ntfs              

```1,6 and 7 is /, /home and swap. 5 is my secondary ntfs partition from my previous Win XP install. What I don't get is what partition 2 is. It is apparantly mounted (hence cannot be edited) and contains the entire disk  (320 Gb), save the boot partition (6 Gb).

What I want to know is how I can make unallocated space ready, or perhaps creating an ntfs partition, where I can install Win XP. As it is now, the Win installation dont find any unallocaded space and my only option is using sda5 (which is not an alternative). I only need about 50 Gb for it and should have had about 90 Gb unallocated. I had that at least when installing ubuntu, but I dont know what happened to it during the installation. Apparantly its in the sda2-thing :confused:.

What would happen if i deleted sda2? What is "lba"? What should I do? :P

Thanks for any help, I am pretty much stuck here...

And here is the help output from parted:
```

  check NUMBER                             do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition
  help [COMMAND]                           print general help, or help on
        COMMAND
  mklabel,mktable LABEL-TYPE               create a new disklabel (partition
        table)
  mkfs NUMBER FS-TYPE                      make a FS-TYPE file system on
        partititon NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system
  move NUMBER START END                    move partition NUMBER
  name NUMBER NAME                         name partition NUMBER as NAME
  print [devices|free|list,all|NUMBER]     display the partition table,
        available devices, free space, all found partitions, or a particular
        partition
  quit                                     exit program
  rescue START END                         rescue a lost partition near START
        and END
  resize NUMBER START END                  resize partition NUMBER and its file
        system
  rm NUMBER                                delete partition NUMBER
  select DEVICE                            choose the device to edit
  set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
  toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition
        NUMBER
  unit UNIT                                set the default unit to UNIT
  version                                  display the version number and
        copyright information of GNU Parted

```--
Regards,
Raff1

---

### Post by Mark Phelps on 2009-08-17
I believe that XP needs a Primary NTFS partition for installation and you only have a Logical partition.

Also, if you remove your Extended partition, you would remove all the partitions following the first one on your drive.  An extended partition is essentially a container for other partitions -- known as logical partitions.

So, basically, you would need to create a Primary NTFS partition outside of the Extended partition.  That means you will have to shrink the Extended partition to make room for the Primary following it.  However, before you can shrink the Extended partition, you would have to either remove sda5 or shrink it to make room.

---

### Post by Raff1 on 2009-08-18
Thanks for the reply Mark!

> **Mark Phelps said:**
> I believe that XP needs a Primary NTFS partition for installation and you only have a Logical partition.

Also, if you remove your Extended partition, you would remove all the partitions following the first one on your drive.  An extended partition is essentially a container for other partitions -- known as logical partitions.

So, basically, you would need to create a Primary NTFS partition outside of the Extended partition.  That means you will have to shrink the Extended partition to make room for the Primary following it.  


I see. It makes sense that the primary ntfs partition needs to be outside the extended partition.

> **Mark Phelps said:**
> 
However, before you can shrink the Extended partition, you would have to either remove sda5 or shrink it to make room.

Removing as in deleting it, right? I rather not do that because of the files I got there. Shrinking it is an option however. Still, when summing up the storage space in the extended partition:

Allocated Space = sda5 + sda7 + sda6 = 142 Gb + 1 Gb + 80 Gb = _223 Gb_.

However, the extended partition claims to have 314 Gb. The difference is 103 Gb.
*This difference is in agreement with the left-over space (unallocated) I did not share among my linux partitions when installing Ubuntu because I had in mind to use it for the Windows installation later.*

I don't understand how this space was feeded into the extended partition or why I have to shrink the existing ntfs partition in order to create a new primary ntfs partition, when I got apparently unallocated space (~100 Gb) in the extended partition.

Do I have to shrink the ntfs-partition because it is the only partition which is not mounted? Perhaps a boot-up partitioning program would be of better use?

Appreciate the help! :)
Regards, Raff1

---

### Post by Elfy on 2009-08-18
Boot with your buntu livecd or a partition editor like gparted or partedmagic.

If you use the buntu cd then swap will get used - you can right click and swapoff in the parted program.

---

### Post by Raff1 on 2009-08-18
> **forestpixie said:**
> Boot with your buntu livecd or a partition editor like gparted or partedmagic.

If you use the buntu cd then swap will get used - you can right click and swapoff in the parted program.

Ah, thanks! And then I will be able to access the ~100 Gb of unallocated space "eaten" by the extended partition?

--
Raff1

---

### Post by aarons6 on 2009-08-18
if you have free space from your extended partition you can move it to the right.
it takes a long time, but i see that is your only option

then your table will look like this

sda1 primary ext3 boot
sda2 free space (format ntfs)
sda3 extended (this houses sda5,6,7)
sda5 logical ext3
sda6 logical swap
sda7 logical ntfs

then you can format sda2 and install windows there..
it will have 2 ntfs drives tho (sda2 and sda7).. you might can move the files over and delete the sda7 drive and resize the extended again later.

---

### Post by Raff1 on 2009-08-18
> **aarons6 said:**
> if you have free space from your extended partition you can move it to the right.
it takes a long time, but i see that is your only option

Thats what I will do then. I will have to do it with GParted live CD then?
Is it strightforward to move storage space from extended partition "to the right" ( = making it a primary partition?)?

--
Raff1

---

### Post by aarons6 on 2009-08-18
no it stays extended.

basically you right click the extended partition and move it to the right.
making the free space in the front.

this will let you make a new primary partition with the free space

---

### Post by raymondh on 2009-08-18
Just in case of difficulties .... post back a screenshot of gparted to help the forum visualize.

---

### Post by Raff1 on 2009-08-20
> **raymondhenson said:**
> Just in case of difficulties .... post back a screenshot of gparted to help the forum visualize.

About that.. How am I supposed to fetch a screenshot when booting from GParted live CD?:P

Oh and I used following options:

GParted Live (default)
Don't touch keymap
British English
Default graphics option (the first. Don't remember the formulation)

This resulted in a message on my monitor "Input not supported". This message was generated by the monitor itself.

I tried again with following options:

GParted Live (Safe graphic settings, vga=normal)
Don't touch keymap
British English
Enter command line prompt

I then typed "help", but the first entries disappeared over the top of my screen. It is a flag I can put after help to make the output pause isn't it?

Anyways, after typing "exit" to get back to the menu I got the familiar error on my monitor: "Input not supported" and had to reboot manually again.

How could I make a primary ntfs partition out of the unallocated space contained in the extended partition atm using the command prompt on GParted live?

Thanks for the help!:)
Regards, Raff1

---

### Post by Raff1 on 2009-08-20
My swap partition is only 1 Gb btw.. Can this be causing some trouble in this regard?

---

### Post by Bartender on 2009-08-20
I wrote this up a few years ago - if it's outdated there should be newer instructions on the GParted website

[http://ubuntuforums.org/showthread.php?t=325775](http://ubuntuforums.org/showthread.php?t=325775)

It seems a bit convoluted but I did it and I'm not all that great with Linux.

Another option is to boot into an Ubuntu LiveCD and useGParted from there just to take a screenshot.  All youhave to do is boot into the LiveCD desktop, plug in a USB thumb drive, wait for it to be recognized and come up on the desktop, take a note of its name, then go to partitioner (System>Gnome Partitioner).  When you have the partititoner up, go to Applications>Accessories>Screenshot, then save the screenshot to your USB thumb drive.  Then get out of the LiveCD, start up any PC to get back to this forum, and post the screenshot from the thumb drive.

---

### Post by Raff1 on 2009-08-22
> **Bartender said:**
> 
Another option is to boot into an Ubuntu LiveCD and useGParted from there just to take a screenshot.  All youhave to do is boot into the LiveCD desktop, plug in a USB thumb drive, wait for it to be recognized and come up on the desktop, take a note of its name, then go to partitioner (System>Gnome Partitioner).  When you have the partititoner up, go to Applications>Accessories>Screenshot, then save the screenshot to your USB thumb drive.  Then get out of the LiveCD, start up any PC to get back to this forum, and post the screenshot from the thumb drive.

Ah, thank you! I booted up Ubuntu Live CD and GParted from there and I got this nice photo session =)

Enjoy!

[[IMG]http://img89.imageshack.us/img89/3812/pic1b.png[/IMG]]("http://img89.imageshack.us/img89/3812/pic1b.png/")
Picture 1: Overview over my HD's partitions

As we can see from picture 1 the swap-partition and hence the extended partition is in use/locked. I tried to un-swap the partition but that didn't do me any good, and screen-shots became disabled. I re-swapped it afterwards.

[[IMG]http://img90.imageshack.us/img90/3467/pic2q.th.png[/IMG]]("http://img90.imageshack.us/i/pic2q.png/")
Picture 2: Rightclick unallocated > Make New

As you can see in picture 2, I am unable to select primary partition. It was suggested earlier that I should move storage from extended "to the right". (Whatever that means, and how?)

[[IMG]http://img220.imageshack.us/img220/4605/screenshotresizemovedev.th.png[/IMG]]("http://img220.imageshack.us/i/screenshotresizemovedev.png/")
Picture 3: Edit screen for existing ntfs partition, sda5.

In picture 3 it becomes evident that using the "move" option on the ntfs partition sda5 only can extend/shrink it at the cost/benefit of the unallocated space on the extended partition.

So how can I move any unallocated space outside the extended partition or create a primary partition?

Thanks again everyone =)
Regards Raff1

---

### Post by Elfy on 2009-08-22
> So how can I move any unallocated space outside the extended partition or create a primary partition?To do that you have to move the partitions which are between the edge of the extended partition and the unallocated space - that is sda6 and the swap. 

It will possibly take a long time - if it's a laptop make sure it's not running on battery. Do not assume that it has hung.

---

### Post by Bartender on 2009-08-22
Hey, guys, I don't want to go off topic, but I've got a question regarding swap.  In just the last couple of days several folks have mentioned that the Ubuntu installer CD mounts the swap partition if it sees one, so you can't delete or move swap when you're in the partitioner.    

I don't remember ever having problems deleting swap partitions when using a GParted LiveCD (GPLCD).  Does a GPLCD run off just the physical memory?

Raff, that's a bummer that you can't get a picture with the GParted LiveCD.  If you don't mind burning another CD, I'd suggest going back to SourceForge and downloading a version of GParted LiveCD from a year back or more.  I've got a 2 year old copy of GPLCD that often works when the newer copy doesn't.

I have several questions -

#1: sda1; where did it come from?  Is it a vestige of a Windows installation?  A recovery partition, perhaps?  If we can get the extended shoved over, do you have a problem with deleting the data on that partition and starting over?
#2: You know that you need a primary partition for Windows, right?  Windows won't boot from within an extended partition.
#3: I'm not sure if anyone has yet mentioned that installing Windows after Ubuntu can be problematic?  This might get so unwieldy that you get to the point where you're better off deleting Ubuntu and starting over...

---

### Post by Raff1 on 2009-08-23
> **Bartender said:**
> 
#1: sda1; where did it come from?  Is it a vestige of a Windows installation?  A recovery partition, perhaps?  If we can get the extended shoved over, do you have a problem with deleting the data on that partition and starting over?

I'll take it from the beginning:
First off I had a primary C: partition, and secondary D: and E: partitions. I emptied the D: partition when installing Ubuntu and went for the install alternative with the slide you can move. Only I didn't get it was a slide *facepalm*:( so I next'ed with only 2,5 Gb between /root and /home! That was not even enough for the first synaptic update... And the rest of the space I was intending to use was catastrophically merged with the windows C: partition. I dont know how that happened but it was a puch in my face. I did rather not want to touch the C: partition but now I had to.

I managed to screw up something when partitioning C: so windows didn't boot as usual. [I]I intended to reinstall windows at some point anyways, since it was getting slow and buggy so I didn't bother to fix it but rather deleted the whole partition with Ubuntu live CD and used some of the space to install Ubuntu.
[/I]
Yet again *sigh* the unallocated space I had liberated was put somewhere akward, namely the middle of the extended partition.

> **Bartender said:**
> #2: You know that you need a primary partition for Windows, right?  Windows won't boot from within an extended partition.

I know that, thats why I posted the picture of only logical being enabled.. I frankly don't know how I can create a primary ntfs partition. As I will explain below, even  after moving unallocated space to the rightmost of the extended partition this isn't possible, seamingly...

> **Bartender said:**
> #3: I'm not sure if anyone has yet mentioned that installing Windows after Ubuntu can be problematic?  This might get so unwieldy that you get to the point where you're better off deleting Ubuntu and starting over...

Yes, I am aware, but things ended up like this and I wanted to take the challenge :). If everything failes I will mount the ntfs partition in Ubuntu and save everything I need and start from scratch, windows first. I don't mind since I like playing around a bit with my PC.

** More will come below as soon as I fetch those images I took **

---

### Post by Raff1 on 2009-08-23
I decided to shrink my sda6 /home partition and move the free space to the right in order to get free space to the right and save my self a lot of moving, as well as getting the general idea of moving partitions.

Now my HD looks like the display in picture 4 below:

*see attached file pic4.png, image hosting crashed.. will edit in later*
Picture 4: New partition layout with  35 Gb unallocated space to the right in the extended partition.

When I tried to create a new ntfs primari partition from the 35 Gb free space to the right it wasn't possible as can be seen in picture 5 below.

*see attached file pic5.png, image hosting crashed.. will edit in later*
Picture 5: Attempt to create new primary ntfs partition from the 35 Gb space to the right with "primary" option disabled.

Okey.. *Will I be able to create a primary ntfs partition using GParted from Ubuntu live CD? *If not there is hardly any point of me mocking about in there any further. :P

Appreciate all the help folks! :)
Regards Raff1

---

### Post by Elfy on 2009-08-23
Looks like you are almost there - all that is standing in the way is the extended being locked - turn off swap - right click sda7 - ther should be an option to  turn off swap. Refresh Ctrl+R and then both sda7 and sda2 should be unlocked and ready for editing.

Now you have to resize the extended partition from left to right and once it has finished the unallocated space will be outside the extended and you can make a primary partition with it.

---

### Post by Raff1 on 2009-08-23
> **forestpixie said:**
> 
Now you have to resize the extended partition from left to right and once it has finished the unallocated space will be outside the extended and you can make a primary partition with it.

Yes, about that I think you need to break this down a bit for me. I thought that once (some) unallocated space was all the way to the right it was moved outside the extended partition or at least somehow "usable" as primary partition (can be moved out). That didn't happen so now I don't know what you want me to do. Resize from right to left? Do I have to move all the unallocated space to the right before I can use it as intended? Do I have to sort the partitions in a particular way?

*I don't need the unallocated space in the middle yet, the space to the right is more than sufficient if I could just move it. So do I still have to resize and move my partitions?*

And how do the space move from all the way to the right and to the actual outside of the extended partition?

> **forestpixie said:**
> Looks like you are almost there - all that is standing in the way is the extended being locked - turn off swap - right click sda7 - ther should be an option to turn off swap. Refresh Ctrl+R and then both sda7 and sda2 should be unlocked and ready for editing.

Perhaps this is why it didn't work when I did this. I will boot up Ubuntu live CD again and make sure to disable swap this time. :) Thanks!

---

### Post by Raff1 on 2009-08-23
> **Raff1 said:**
> 
And how do the space move from all the way to the right and to the actual outside of the extended partition?


Ah, I finally figured it now.. You only have to move the extended partition itself! Then you can specify how much space will precede it.

Thanks for the patience! I will move my space outside the extended partition and make a primary ntfs partition for my windows and cope with the booting problems afterwards. I found a nice guide for just that somewhere.

Regards, Raff1

---

### Post by Raff1 on 2009-08-23
Then I finally managed to partition my HD according to the attached pic6.png.

I got sda3 as a primary ntfs partition and 38 Gb of unallocated space outside of sda2 (extended).

However, my win XP installation only seems to see the sda5 partition. it doesn't see the newly created sda3 or the 38 Gb of free space... :(  The sda5 partition is about the only place I'd rather not touch!

So how do I make it recognize it? (And why does it only see the sda5 from inside the extended partition? It seems pretty upside down... ):confused:

Do I have to delete sda3, move sda1 to the right and create the primary ntfs partition as the first (leftmost) partition? Is windows really *that* stupid? :P

---

### Post by Raff1 on 2009-08-24
> **Raff1 said:**
> 
Do I have to delete sda3, move sda1 to the right and create the primary ntfs partition as the first (leftmost) partition? Is windows really *that* stupid? :P

I did this, tried installing win again but it didn't recognize the newly made ntfs sda3. So I deleted sda3 again and my partition layout is displayed in the attached image picA.png.

Exactly the same thing happened again. The message that appears when I am to chose install location is this:

```

131070 MB Harddrive 0 on Id 1 on bus 0 on apti [MBR]
C: Partition1 [Unknown]             131072 MB (131071 MB free)

```This is the same message/choice I've had from the beginning of this tread. I have this far suspected it to be the ntfs partition sda5 (my treasure chest) (132.07 GiB/ 115.83 GiB used) but I am really not sure.

What detail am I missing? Why won't windows see the neatly prepared space?

---

### Post by Raff1 on 2009-08-25
Well.. I have at least taken backup of my data so I can precede with a full format and start all over if none can help me. But I really want to get this working after all the effort. I should be nearly there.

Thanks!
Raff1

---

### Post by Raff1 on 2009-08-25
Thought I might bump this before doing something drastic...

---

### Post by Bartender on 2009-08-25
Raff, I'd like to help but that ext3 sda1 partition is what's puzzling me.  Notice it's flagged as boot.  And there's data inside.  What does it do?  What's in there?  I'm guessing that this partition is what's messing you up.

If you've copied your personal data to external storage, maybe the best thing is to wipe the drive and start over.

I posted some GParted screenshots this morning.  Two of the pics are fairly typical dual-boots.  Maybe that'll help you visualize what you want the final product to look like.

[http://ubuntuforums.org/showthread.php?t=1249374](http://ubuntuforums.org/showthread.php?t=1249374)

If you want a data partition that's accessible from Windows and Linux you could use either one of the dual-boots as the basic model, but add another logical partition inside the extended box way out to the right, formatted as NTFS.

---

### Post by aarons6 on 2009-08-28
it looks like you about got it.. to make window see the new sda2 drive on install it has to be set active and boot.. 

only 1 partiton can be active and bootable, and you have sda1 ext3 partition set to that.

---

### Post by Raff1 on 2009-08-30
> **aarons6 said:**
> it looks like you about got it.. to make window see the new sda2 drive on install it has to be set active and boot.. 

only 1 partiton can be active and bootable, and you have sda1 ext3 partition set to that.

[quote=Bartender]
Raff, I'd like to help but that ext3 sda1 partition is what's puzzling me. Notice it's flagged as boot. And there's data inside. What does it do? What's in there? I'm guessing that this partition is what's messing you up.
[/quote]

Thanks! So that was what it was all about. That ext3 partition was my Ubuntu root partition actually.

However, I used GParted on UCD to format my entire disk and installed win xp (first) and Ubuntu from scratch. So now I am up and going again with a clean PC with dual boot. :)

All my problems are solved, even if I intended to try out install windows after ubuntu originally.

So how could I have moved the boot flag to the ntfs partition I created?

Thanks everyone!
Regards, Raff1

---

