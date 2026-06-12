---
title: "[SOLVED] Dual boot partitioning?"
date: 2008-11-12
forum: General Help
---

### Post by Yezinki on 2008-11-12
Hi there,

1.Did a clean install of XP MCE & Ubuntu 8.10 on my machines 232 GB HD.

2. Firstly installed XP MCE using Sony's OEM DVD.

3. Changed Drive letters of all drives.

4. Using Acronis Disk Director divided the drive into C & D , both primary partitions.

5. Ran CHKDSK on C drive.

6. Installed Ubuntu as see in the attached screen shot.

7. Did not transfer XP MCE's Admin rights & users Document settings??

8. Don't know whether the MBR is is on sda0?

Hoping to hear your suggestions regarding partitioning & their sizes etc.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-12
Another screen shot......

---

### Post by oilchangeguy on 2008-11-12
since you've already partitioned the drive, and installed ubuntu. what exactly is it you're wanting to know?

---

### Post by logos34 on 2008-11-12
I would throw out that install and try again...root and swap are way to small (even with some of the partitions separated out you still should give / a little more wiggle room, if not consolidate it)...you really don't need separate partitions for /var, /usr, etc. if this is just for normal desktop usage.  If you must use xfs, ideally you should have made /boot ext2 (but ext3 will work, but you can convert it with tune2fs)...Grub will be on the MBR of that drive (i.e. 'hd0', or /dev/sda)

---

### Post by Yezinki on 2008-11-12
> **oilchangeguy said:**
> since you've already partitioned the drive, and installed ubuntu. what exactly is it you're wanting to know?

I am wanting to hear your positive criticism/ remarks to improve it.

Regards,

Yezinki.

---

### Post by oilchangeguy on 2008-11-12
> **Yezinki said:**
> I am wanting to hear your positive criticism/ remarks to improve it.

Regards,

Yezinki.

i don't see a problem with your set up. as long as everything works leave it alone. i do wonder, what do you mean by you changed all of the drive letters. also third party partioning software is not needed. you could have used the live cd's partition manager.

---

### Post by Yezinki on 2008-11-12
> **logos34 said:**
> I would throw out that install and try again...root and swap are way to small (even with some of the partitions separated out you still should give / a little more wiggle room, if not consolidate it)...you really don't need separate partitions for /var, /usr, etc. if this is just for normal desktop usage.  If you must use xfs, ideally you should have made /boot ext2 (but ext3 will work, but you can convert it with tune2fs)...Grub will be on the MBR of that drive (i.e. 'hd0', or /dev/sda)



1. Way to small.....whats that.......suggest sizes please?

2. What is the logic of ext2 & XFS & not ext3?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-12
Separating  /usr, /var is suggested by Ubuntu long time users not new bies like myself & you guys.

Regards,

Yezinki.

---

### Post by oilchangeguy on 2008-11-12
> **Yezinki said:**
> 1. Way to small.....whats that.......suggest sizes please?

2. What is the logic of ext2 & XFS & not ext3?

Regards,

Yezinki.

don't get caught up in the trap that many linux users do. you do not have to do any manual partitioning. when you install ubuntu it will set it's own partitions.

---

### Post by Yezinki on 2008-11-12
> **oilchangeguy said:**
> i don't see a problem with your set up. as long as everything works leave it alone. i do wonder, what do you mean by you changed all of the drive letters. also third party partioning software is not needed. you could have used the live cd's partition manager.

XP MCE has 5  drives,....HD, SSD/MMC, Memory stick Pro, DVDRW,DVD-RAM .......C D E F G H.

When a D active was created, had to change their drive letters one step ahead to accommodate D Active NTFS.

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-12
> **logos34 said:**
> I would throw out that install and try again...root and swap are way to small (even with some of the partitions separated out you still should give / a little more wiggle room, if not consolidate it)...you really don't need separate partitions for /var, /usr, etc. if this is just for normal desktop usage.  If you must use xfs, ideally you should have made /boot ext2 (but ext3 will work, but you can convert it with tune2fs)...Grub will be on the MBR of that drive (i.e. 'hd0', or /dev/sda)


Hi logos34

Yezinki's partitioning setup is fine as it is.  Every partition (size and file system type) has been carefully chosen to suit his needs.

I have a surprise for you about the root partition size.  It will never have any more than 250MB of used data no matter what he does (even if he was to have a 64bit and 32bit system installed).  That is a fact with his setup.


I loved the comment about the ext3 partition.  that was funny.  But it is safer to have the ext3 IMHO.  And it is always nice to have faster recovery if something goes wrong.

I agree that the boot loader is installed in his MBR sda (or sda0)

---

### Post by linux23dragon on 2008-11-12
> **Yezinki said:**
> Hi there,
2. Firstly installed XP MCE using Sony's OEM DVD.

3. Changed Drive letters of all drives.

4. Using Acronis Disk Director divided the drive into C & D , both primary partitions.

5. Ran CHKDSK on C drive.

6. Installed Ubuntu as see in the attached screen shot.


Well that turned out very well IMO.  I normally use CHKDSK before resizing and splitting the windows partition.  But it must of worked out ok fine.  



> **Yezinki said:**
> 
7. Did not transfer XP MCE's Admin rights & users Document settings??

I'm not sure if that is needed.  Can anyone comment about that?

> **Yezinki said:**
> 
8. Don't know whether the MBR is is on sda0?


The MBR is on sda (or sda0)

> **Yezinki said:**
> 
Hoping to hear your suggestions regarding partitioning & their sizes etc.

The partitioning and the sizes look fine to me.  

So you can boot into both Windows and Ubuntu?

Do you think you need to mod the /boot/grub/menu.lst file at all?

If you can boot both systems then it is not necessary to mod the menu.lst file IMO.

---

### Post by logos34 on 2008-11-12
> **linux23dragon said:**
> Yezinki's partitioning setup is fine as it is. Every partition (size and file system type) has been carefully chosen to suit his needs.

Oh really?  How do you know that based on the info the provided?  I agree with oilchangeguy--there is no need to have all those partitions (except a dedicated /boot because Grub can't boot off xfs).  Unless it's for a mail server of something (i.e. /var).  There's no indication it's for anything other than home desktop use.

What about swap size?  If he has the standard 512MB or greater RAM, then the swap is too small for hibernation.

Maybe / is big enough, but why cut it so close with gobs of disk space (250 GB)?  Mine's more than a gig excluding the partitions in question.

> 
I loved the comment about the ext3 partition. that was funny. But it is safer to have the ext3 IMHO. And it is always nice to have faster recovery if something goes wrong.

um, sorry, don't get the joke.  FYI, it's standard to format a separate /boot ext2, journaling is not needed but won't hurt.

> I agree that the boot loader is installed in his MBR sda (or sda0)

There's no such thing as 'sda0'.  You might want to read 'A Quick Guide to GRUB's Numbering System' [here]("http://users.bigpond.net.au/hermanzone/p15.htm").

regards,

logos32

---

### Post by linux23dragon on 2008-11-12
> **logos34 said:**
> Oh really?  How do you know that based on the info the provided?

Correct. 

But he has provided questions, from other posts.     

> **logos34 said:**
> 
I agree with oilchangeguy--there is no need to have all those partitions (except a dedicated /boot because Grub can't boot off xfs).  Unless it's for a mail server of something (i.e. /var).  There's no indication it's for anything other than home desktop use.

Correct, for the average user, this is not needed. But his current partitioning practice is practical for a more controlled system maintenance.  

> **logos34 said:**
> 
What about swap size?  If he has the standard 512MB or greater RAM, then the swap is too small for hibernation.

That is true. But his system is a Desktop, and hibernation is more useful with notebooks.   

> **logos34 said:**
> 
Maybe / is big enough, but why cut it so close with gobs of disk space (250 GB)?  Mine's more than a gig excluding the partitions in question.

Cool


> **logos34 said:**
> 
um, sorry, don't get the joke.  FYI, it's standard to format a separate /boot ext2, journaling is not needed but won't hurt.

Correct.  It was not worth commenting on, so I withdraw my comment about it.

> **logos34 said:**
> 
There's no such thing as 'sda0'.  You might want to read 'A Quick Guide to GRUB's Numbering System' [here]("http://users.bigpond.net.au/hermanzone/p15.htm").


correct.  It is just sda. My bad

---

### Post by Yezinki on 2008-11-12
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]**.......

1. Ain't you glad that I did it in one  go?

2. Why are members ridiculing my partition sizes, file systems unnecessary partitions......like ext2, swap small, /var,/ usr, not needed?

3. Why do they want me to use Guided method vs Manual?

4. I never use hibernation even on my Dell XPS laptop, NO standby, drives running ALL the time........only shut the screen after specific period

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-12
> **Yezinki said:**
> 
1. Ain't you glad that I did it in one  go?

Yea.  Excellent stuff

> **Yezinki said:**
> 
2. Why are members ridiculing my partition sizes, file systems unnecessary partitions......like ext2, swap small, /var,/ usr, not needed?

That is normal. When I come home from work I'll write up some details about it.  Unless someone beats me to it. 

However in short, it is the same reason you have your hard drive size of 250GB, but you are only allocated 232GB after formatting. 

> **Yezinki said:**
> 
3. Why do they want me to use Guided method vs Manual?


It's easier lol.  But you then you have no control on the partition size used.


> **Yezinki said:**
> 
4. I never use hibernation even on my Dell XPS laptop, NO standby, drives running ALL the time........only shut the screen after specific period


Not meany people do use it.  It's only handy for some.

---

### Post by Yezinki on 2008-11-12
Firstly renamed the removable drives , rebooted.........than using Disk Director 8.0 partitioned C into C & D both active......ran CHDSK on C........no issues.

I have C & D both NTFS & Primary...... used Ubuntu to boot &  create the rest of the partitions.

Regards & Thanks,

Yezinki.

---

### Post by Yezinki on 2008-11-12
[FONT="Arial"]# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=10bf3937-290b-40b3-a1fb-68a651d22c07 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d41b7e99-187b-4426-a166-c0b1d965f952

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		d41b7e99-187b-4426-a166-c0b1d965f952
kernel		/vmlinuz-2.6.27-7-generic root=UUID=10bf3937-290b-40b3-a1fb-68a651d22c07 ro quiet splash 
initrd		/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		d41b7e99-187b-4426-a166-c0b1d965f952
kernel		/vmlinuz-2.6.27-7-generic root=UUID=10bf3937-290b-40b3-a1fb-68a651d22c07 ro  single
initrd		/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		d41b7e99-187b-4426-a166-c0b1d965f952
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/FONT]

1. Boot menu list.

2. Yes I can boot both in XP MCE & Ubuntu........

3. Ubuntu being the first option.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-12
1. Ubuntu Generic.

2. Ubuntu Recovery.

3. Memtest.

4. XP MCE.

---

### Post by TeXtonyx on 2008-11-12
The forumula for swap is inexactly 1.5 x the physical ram. 
512mb ram = ~870mb swap. 1GB ram = ~1.5GB swap. 
But don't go over 2GB of swap if you had 3GB of ram, it isn't used.

For the other partitions, you can resize them later if you need too.
Use Vista to resize Vista and make unallocated space. Use a Linux
tool to resize if one of those partitions you made need to be resized. 
MS software engineers have access to proprietary code and
design a tool for Vista. Linux doesn't have access to proprietary
code and its tool aren't designed to deal with Vista quirks as 
their primary purpose. Only rarely does it make a practical difference.
Linux ports to Windows are not identical, but approximations. There
is a formal language theorem which says that unless two languages
have exactly the same, symbols and logical operators, there will
be at least one expression in language A which does not have a 
direct, exact translation into language B. So use the very best tool.
Computers are actually physical devices, even software basically
electro-magnetically physical structures on the hard drive.
And the same principle which applies to other physical devices
applies to computers, use the best tool. "Box or socket type 
wrenches are safer than open ended. Individual sized wrenches 
are stronger and safer than adjustable wrenches." Can you use
a crescent wrench or GParted for most situations? Yes, but the
situations which they are not interchangeable isn't predictable!
So always maximize the efficiency of your selections; that includes
not being too perfectionistic, so your setup is good except swap.
In life and computers the number one ingredient of success is 
persistence. Quote from Calvin Coolidge,
"Nothing in the world can take the place of Persistence. Talent 
will not; nothing is more common than unsuccessful men with 
talent. Genius will not; unrewarded genius is almost a proverb. 
Education will not; the world is full of educated derelicts. 
Persistence and determination alone are omnipotent. The slogan 
'Press On' has solved and always will solve the problems of the 
human race. [TeX: And fixes many computer problems also.]

TeX: So don't rely on being smart too much. It will lead to 
arrogance which makes one inefficient: overestimation of one's
ability to make sound predictions in speculations/inferences
which really don't have enough information to reach a conclusion.

The second most important thing is mostly for computers. Become
an expert on doing searches (Google). That is the most important
skill in troubleshooting computer problems. Third is realizing
the importance of backups without a lot of brutal lessons. Fourth
is nearly all the time it is quicker to read the instructions than
to rely on one's innate perspicuity or is it perspicacity? :-)

---

### Post by Yezinki on 2008-11-12
Nice.....did you type it or cut & paste?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-12
LINUX KING........

I'll try a single OS install i.e Ubuntu keeping the same partitions??

Regards,

Yezinki.

---

### Post by logos34 on 2008-11-12
> **Yezinki said:**
> 
Why are members ridiculing my partition sizes, file systems unnecessary partitions......like ext2, swap small, /var,/ usr, not needed?

3. Why do they want me to use Guided method vs Manual?

4. I never use hibernation even on my Dell XPS laptop, NO standby, drives running ALL the time........only shut the screen after specific period

no one's 'ridiculing' your setup--you asked for feedback and I tried to offer constructive advice and suggest a simpler approach.  If you only want people to agree with you, say so beforehand next time.

When I was new to linux I had the same mindset as you.  I had read a bunch of books and they all suggested neat ways to divide everything up.  Sounds great--certain directories securely mounted on their own partitions. But I soon found out there's not much point in doing that as long as you backup regularly--unless you're running a server with mission critical data.  You also end up with a lot of unused (wasted) space.   (look again at the amount of space you allocated for /usr and /tmp).  

Generally, / (ext3) and /swap (= ~ 2 x RAM up to 512 MB, and 1-1.5 x RAM beyond that), and maybe a separate /home is the simplest and best way to go for everyday use.  I've tried various other fs types (reiserfs, jfs and xfs) and frankly I haven't been very impressed with the performance differences.   I'm sticking with ext3.  
 
Ok, so you don't need hibernate.  Most people want that option available--more so on a notebook (which I now see you have) where power saving is an issue.

that's just the way I see it, anyway.  good luck

---

### Post by Yezinki on 2008-11-12
Thanks for your remarks/views.....well appreciated!

 I have 2 GB of physical RAM @ 667 MHZ......so my swap should be around 2 GB approx.

 Lastly how does one create a back up in Ubuntu...like I use Ghost or True Image for windows.......Remastersys for Ubuntu??

Regards,

Yezinki.

---

### Post by logos34 on 2008-11-12
Remastersys is neat in that you end up with a bootable live cd of your installation.

Personally I use Partimage to make an image of / partition once a week, and I just make a .tgz archive of most everything in /home (which i have on separate partition).  There's also Clonezilla, or G4L.  

There's also the Simple Home Backup...has a gui in Gnome

---

### Post by Yezinki on 2008-11-12
Thanks for sharing your experienced, tried & tested back up utilities.

Does Remastersys creates an image as good as True Image.......& does that image include all customizations made , if for some reason the  OS gets corrupted, one could reinstall using that burnt ISO?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-12
> **Yezinki said:**
> LINUX KING........

I'll try a single OS install i.e Ubuntu keeping the same partitions??

Regards,

Yezinki.


You will no longer have any use for the NTFS Windows partitions.

In return you can have more space for allocated for /home.

---

### Post by Yezinki on 2008-11-12
> **linux23dragon said:**
> You will no longer have any use for the NTFS Windows partitions.

In return you can have more space for allocated for /home.



How do I do that LINUX KING!

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-13
> **Yezinki said:**
> How do I do that LINUX KING!

Regards,

Yezinki.

Currently you have a dual boot setup like this:-

```

sda1    C:/      NTFS     60GB            |
sda2    D:/      NTFS     60GB            | <-- Primary partition
sda3    /boot    ext3     200MB           |
sda4    ->Extended Partition<-
sda5    /        XFS      1GB            ||
sda6    /usr     XFS      20GB           ||
sda7    /var     XFS      5GB            || <-- Logical drives
sda8    /tmp     XFS      13GB           ||
sda9    SWAP              512MB          ||
sda10   /home    XFS      72GB           ||

```


It is a very nice setup that is flexible and even serviceable.  In fact you also have hard drive integrity, maintenance and performance benefits with this setup as well.   




The following single boot system works well too.  This setup is similar  to the duel boot system (minus the two NTFS partitions) but has the same benefits. 

On a single boot system you could keep the file system as is, or you could just repartition your hard drive (Using the Ubuntu installation disk) like this:-

```

sda1  /boot  ext3  200MB          |
sda2  /usr   XFS   20GB           | <-- Primary Partitions 
sda3  /var   XFS   5GB            |
sda4  ->Extension Partition<-
sda5  /      XFS   1GB           ||      
sda6  /tmp   XFS   13GB          || <-- Logical drives
sda7  /SWAP  N/A   512MB         ||
sda8  /home  XFS   192GB         ||

```

EDIT:- If you play games or like to install third party software (compiled from source) then it is a good idea to have a partition for /usr/local as well ~20GB (or more) in size.

If you feel like trying out the hibernation features, then you only need to increase your swap size up to around 2GB.  But if you have never used it before then you won't miss it.

But you can only learn by playing.

---

### Post by Yezinki on 2008-11-13
**[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING!!![/COLOR][/SIZE][/FONT]**

1. Will I need to format & reinstall for a single boot/OS?

2. In Ubuntu where do power plans reside?

3. I always use High Performance Power plans in windows XP/Vista on my laptop.

4. Are their any techniques in Ubuntu, like in Vista to enhance drive performance like disk caching etc?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-13
> **Yezinki said:**
> 
1. Will I need to format & reinstall for a single boot/OS? 

No, you can keep what you already have.

If you don't want the NTFS partitions you could just reformat them using gparted.  

You can format both the NTFS partitions as (for example) XFS and turn them into extra storage drives.

Then if you like to run your system as a dual boot again, you only need to reinstall windows into the same partitions.

You would then (after you install Windows) need to get grub to write to the MBR.  I can do that with the Ubuntu start up disk via command line interface. 
 
> **Yezinki said:**
> 
2. In Ubuntu where do power plans reside?

System -> Preferences -> Power Management  

> **Yezinki said:**
> 
3. I always use High Performance Power plans in windows XP/Vista on my laptop.

In Gnome you can add applets to your panel like CPU Frequency scaling and Brightness.

Right click with your mouse on the top (or bottom) panel, and left click on Add to panel.

> **Yezinki said:**
> 
4. Are their any techniques in Ubuntu, like in Vista to enhance drive performance like disk caching etc?


Yes, system Library pre linking (prelink).  It is not exactly hard drive caching,  it modifies ELF shared libraries and ELF dynamically
linked binaries so that it takes less time to start up programs.   It  is a advanced subject to help setup.

However I'm not sure if you can use it with Ubuntu's modern tool chain (binutils,libc,kernel, gcc).  Linux is more optimised than Vista (in regards to performance) anyway.  As you could see for yourself.

The XFS file system already uses page cache. And caches  data to ram.  But might not be in relation to disk caching as you are asking about.

Anyone like to correct me on that? (or add any comments?)

---

### Post by Yezinki on 2008-11-13
You are a[FONT="Arial"][SIZE="4"][COLOR="Red"]**[SIZE="5"] GENIUS![/SIZE]**[/COLOR][/SIZE][/FONT]!!!!!!

Regards,

Yezinki.

---

### Post by TeXtonyx on 2008-11-13
"Then if you like to run your system as a dual boot again, you 
only need to reinstall windows into the same partitions again."

A small comment about this. Yezinki said that he did a fresh install
with Win Media Center. Then he used Acronis to split the partitions.
If he deletes the first (boot) partition I'm not sure he can reinstall
Windows back into it. It depends on his cd, some require a clean
drive. So maybe he should keep that, even if he shrinks it. OTOH,
that Media Center OS was not nearly as good as Win XP Pro, so OP
isn't losing all that much if the reinstall fails. I think he should
acquire Win XP Pro, which is worth dual booting. The second NTFS
partition, doesn't need an OS, I guess it could be data storage,
or deleted like you suggest. It's kind of hard to predict than
one will never need to boot XP, and it may not be easy to reinstall.

However, my objection is a small matter in the context of some
rather fine posts on your part. I'm sort of a perfectionist.

Are you able to burn movie dvds from *.avi as easily on Ubuntu
as XP? I don't really care about game performance. The Gimp would
probably meet my needs, but I have a few dvd video tutorials 
which show how to use Photoshop and digital camera photo editing.
The Gimp makes a lot more sense if you don't have an educational
investment already made in learning props. I've got a Howto on
manually partitioning with pictures which looks good to me and
my reading suggests that /home is the key separate partition. 
[http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222)
[http://www.mediafire.com/?b1zushbgmeo](http://www.mediafire.com/?b1zushbgmeo) [the pdf file]
[http://thinkdigit.com/forum/showthread.php?t=96132&page=2#57](http://thinkdigit.com/forum/showthread.php?t=96132&page=2#57) Ubuntu 8.10

---

### Post by linux23dragon on 2008-11-13
> **TeXtonyx said:**
> 
A small comment about this. Yezinki said that he did a fresh install
with Win Media Center. Then he used Acronis to split the partitions.
If he deletes the first (boot) partition I'm not sure he can reinstall
Windows back into it. It depends on his cd, some require a clean
drive. So maybe he should keep that, even if he shrinks it. 


That sounds like a good idea TeXtonyx.    



> **TeXtonyx said:**
> 
OTOH, that Media Center OS was not nearly as good as Win XP Pro, so OP
isn't losing all that much if the reinstall fails. I think he should
acquire Win XP Pro, which is worth dual booting. The second NTFS
partition, doesn't need an OS, I guess it could be data storage,
or deleted like you suggest. It's kind of hard to predict than
one will never need to boot XP, and it may not be easy to reinstall.


Yea, the Windows issues.  I myself have Windows XP Corporate Edition and SP2.  But I have never been using it since WINE was able to play HL2.

> **TeXtonyx said:**
> 
Are you able to burn movie dvds from *.avi as easily on Ubuntu
as XP? I don't really care about game performance. The Gimp would
probably meet my needs, but I have a few dvd video tutorials 
which show how to use Photoshop and digital camera photo editing.
The Gimp makes a lot more sense if you don't have an educational
investment already made in learning props.

I have never tried converting .avi files to DVD (TOC format)?
But you can check out Linux application alternatives from these links :- 

[[COLOR="Blue"]***_The Linux Alternative Project_***[/COLOR]]("http://www.linuxalt.com/")
[***_[COLOR="Blue"]Alternatives to Windows Software[/COLOR]_***]("http://www.linux.ie/newusers/alternatives.php")
[***_[COLOR="Blue"]Linux App Finder[/COLOR]_***]("http://linuxappfinder.com/alternatives?page=1")

EDIT: Don't forget that you can install the some windows software using WINE. It's worth a try.

> **TeXtonyx said:**
> 
I've got a Howto on
manually partitioning with pictures which looks good to me and
my reading suggests that /home is the key separate partition. 
[http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222)
[http://www.mediafire.com/?b1zushbgmeo](http://www.mediafire.com/?b1zushbgmeo) [the pdf file]
[http://thinkdigit.com/forum/showthread.php?t=96132&page=2#57](http://thinkdigit.com/forum/showthread.php?t=96132&page=2#57) Ubuntu 8.10

Nice.  All looks good to me :)

---

### Post by TeXtonyx on 2008-11-13
Thanks. I looked up HL2 and it looked like a good game. The last
game venture I tried was Myst/Uru! Wine has certainly improved.

---

### Post by logos34 on 2008-11-13
> **Yezinki said:**
> 
4. Are their any techniques in Ubuntu, like in Vista to enhance drive performance like disk caching etc?

well, there's the 'write-cache' feature--you enable it through /etc/hdparm.conf.  I have mine off (the default), since there are apparently some stability issues with ext3.  Not sure about xfs or the others.  Also bear in mind that hdparm was originally designed to configure IDE devices, and ubuntu has switched to the libata scsi driver for PATA/IDE and SATA drives...I've never managed to straighten out if the driver accepts the hdparm settings or not.

---

### Post by Yezinki on 2008-11-13
I find Acronis Disk Director suite ver.10 very reliable,lots of features, tried & tested plus it synchronises the partitions created/resized according to the OS.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-16
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]**

1. I cant find features like hibernation, Standby drives running etc in 8.10

2. Does one need to type commands in Terminal for them??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-16
When manually creating Logical partitions, one should check Beginning or Last/End??

---

### Post by Yezinki on 2008-11-16
Like in a dual boot if I need to reinstall any windows versions, I shall do it on sda1 Primary NTFS..yea??

What If I want to reinstall Ubuntu...shall install it over /usr??

What other partitions would I need to format too?

What about my desk top / browser settings will they be persevered??

Regards,

Yezinki.

---

### Post by logos34 on 2008-11-16
Hibernation and standby settings are in system>prefs>power mngt and system>prefs>screensaver.  If you want to adjust drive [spindown]("http://www.gentoo-wiki.info/Hdparm#Spindown_-S") time, then hdparm.conf (but not sure exactly how it works with sata disks)

Beginning or Last/end is for when you want to leave some unused space at front or end of logical partition.  If you're using the entire empty space then either will do.

Any partition # will work for windows reinstall, but it must be a PRIMARY, not logical partition.  You'll need to restore grub afterward.  (see link my sig)

If you reinstall ubuntu, follow the guide below.  Basically you're just doing #5 as well for /usr, /var/, /tmp and /boot.  That's the one thing I like about dedicated partitions--if you have /var separated then all your .debs are there, and you don't have to download everything again.  (But then there's AptOnCD, which does basically the same thing).  

Note the '*not* ticked'--that's critical to prevent the installer from formatting those separate partitions.

You're /home is where all your desktop settings/preferences are stored.

> 
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)
**Clean Install Upgrade (not recommended)**

 If your /home directory is contained on a separate hard-disk partition you should be able to upgrade by performing a clean install of the current release of Ubuntu and 'adopting' the old /home directory. 
**Back-up any important data before following this procedure as data loss is possible, and very well may be likely.** 

[LIST=1]
[*]Obtain an installation CD for the release of Ubuntu 7.04 you wish to install, and boot from it. 
[*]Start the installation process. When you reach the *Prepare disk space* stage of installation, choose the *Manual* option and press **Forward**. 
[*]Identify your current '/' (root) partition. Select '/' as the mount point and ensure that *Format* is ticked. **You will lose all data on this partition and the new version of Ubuntu will be installed there instead.** 
[*]Identify your swap partition and set its mount point as 'swap'. 
[*][COLOR=Red]Identify your /home partition. Set its mount point as '/home' and make sure that *Format* is **not** ticked.[/COLOR] 
[*]Continue installation as normal until you reach the *Who are you?* stage, enter a username and password which *exactly match* your current username and password. 
[*]Complete the installation as normal. 
[/LIST]
Once the installation has completed, you should be able to log in to Ubuntu and your /home partition with all of your documents and settings should be intact.

---

### Post by Yezinki on 2008-11-16
Hi there,

1. How is grub restored.....where exactly is it located.....if another windows version is installed over any of the primary sda1/2...?

2. Cant it be saved earlier before installation?

3. Is grub similart to startup manager?

4. Ubuntu if reinstalled means that /, /usr,/var,/tmp should be formatted..../home remains intact....correct?

5. How can one bring desktop/ browser customized settings on the new install....or its not possible?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-17
> **Yezinki said:**
> Hi there,

1. How is grub restored.....where exactly is it located.....if another windows version is installed over any of the primary sda1/2...?

logos34 has a link in his signature on doing that.

> **Yezinki said:**
> 
2. Cant it be saved earlier before installation?

Windows will always rewrite the MBR when you install Windows (or if for some reason windows thinks it has an issue).

> **Yezinki said:**
> 
3. Is grub similart to startup manager?

No, its a configuration tool for grub.

I'm not sure if it rewrites the MBR as I have never used it myself.  I use the command line via installation disk.

Again, have a go with logos34 grub link.

> **Yezinki said:**
> 
4. Ubuntu if reinstalled means that /, /usr,/var,/tmp should be formatted..../home remains intact....correct?

Correct.

> **Yezinki said:**
> 
5. How can one bring desktop/ browser customized settings on the new install....or its not possible?

You need to backup your user directory if your going to reuse the same user name.  Then you can copy the hidden files over to your new installation user account.

These are the main hidden directory's that will restore most desktop settings:-

```
.config
.gconf
.gconfd
.gnome2
.gnome2_private
.nautilus
.themes
.VirtualBox
.local
```



But it is best to use the backup/restore options for both email and web browser clients.   Copying the hidden directory's might not work as they are.

---

### Post by Yezinki on 2008-11-17
Thank **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING[/COLOR][/SIZE][/FONT]**...........you are one genius, smart man.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-17
**You need to backup your user directory if your going to reuse the same user name.** Then you can copy the hidden files over to your new installation user account.

These are the main hidden directory's that will restore most desktop settings:-


Code:
.config
.gconf
.gconfd
.gnome2
.gnome2_private
.nautilus
.themes
.VirtualBox
.local

**But it is best to use the backup/restore options for both email and web browser clients.** Copying the hidden directory's might not work as they are.


Hi LINUX KING!

In short you recommend to make a back up of /usr & than paste that on the newly formatted one?

How do I make a back up of /usr......using APTonCD??

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-18
> **Yezinki said:**
> 

Hi LINUX KING!

In short you recommend to make a back up of /usr & than paste that on the newly formatted one?

How do I make a back up of /usr......using APTonCD??

Regards,

Yezinki.

No, just your /home as you already stated. You can reformat /usr

---

### Post by Yezinki on 2008-11-18
Thanks **[FONT="Arial"][SIZE="5"][COLOR="Red"][/COLOR]LINUX KING[/SIZE][/FONT]**

Copy home using APTonCD & than paste it after a reinstall....Correct?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-19
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**

1. I can use XP corp ed or XP 64 bit......but than what utility shall I use to watch cable in windows?

2. Is there any benifit in using 64 bit Ubuntu 8.10 or XP 64 bit?

Hoping to hear from you,

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-19
Is this a plan with no hibernation, drives running continuously, no stand by, just display turns blank after 10 mins........which I prefer in windows??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-19
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**

1. What exactly do I do...step wise....if I plan installing XP over XP MCE?

2. Simply install it over sda1 NTFS Primary?

3. Ubuntu 64 bit over present?

4. What changes to made in the Grub & how?

Regards,

Yezinki.

---

### Post by linux23dragon on 2008-11-20
> **Yezinki said:**
> Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**

1. I can use XP corp ed or XP 64 bit......but than what utility shall I use to watch cable in windows?

2. Is there any benifit in using 64 bit Ubuntu 8.10 or XP 64 bit?

Hoping to hear from you,

Regards,

Yezinki.

If you have a 64bit CPU then you can use both.

In the past their was a lack of 64bit application support for Windows XP 64bit.  And I've never seen that version of windows it take off.

There is some performance benefits with Ubuntu-64 but the main benefit is that you can install over 3GB of RAM in your PC

---

### Post by Yezinki on 2008-11-20
My machine's CPU is Core Duo T2400, 1.8 GHZ??

---

### Post by linux23dragon on 2008-11-20
> **Yezinki said:**
> My machine's CPU is Core Duo T2400, 1.8 GHZ??

That will run 32bit software only

---

### Post by Yezinki on 2008-11-20
How do you feel about Ubuntu 32 bit vs 64 bit??

---

### Post by linux23dragon on 2008-11-20
> **Yezinki said:**
> How do you feel about Ubuntu 32 bit vs 64 bit??

Both do the same job.  32bit has been more stable in the past.

---

### Post by Yezinki on 2008-11-20
> **Yezinki said:**
> Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]LINUX KING![/COLOR][/SIZE][/FONT]**

1. What exactly do I do...step wise....if I plan installing XP over XP MCE?

2. Simply install it over sda1 NTFS Primary?

3. Ubuntu 64 bit over present?

4. What changes to made in the Grub & how?

Regards,

Yezinki.


LINUX KING your thoughts.............

---

### Post by linux23dragon on 2008-11-22
> **Yezinki said:**
> 
1. What exactly do I do...step wise....if I plan installing XP over XP MCE?

2. Simply install it over sda1 NTFS Primary?

Thats how you do it normally, yes?

> **Yezinki said:**
> 
3. Ubuntu 64 bit over present?

No need to reinstall with Ubuntu 64bit unless you don't want Ubuntu 32bit.
If you have the Intel core2 duo (not the Intel core duo), then yes you can install the 64bit distro (not the 32bit).

> **Yezinki said:**
> 
4. What changes to made in the Grub & how? 

No changes are made to the menu.lst file needed.  you only need to boot the installation disk and recover the MBR using grub. 

This post[***_[COLOR="Blue"]How to restore Grub from a live Ubuntu cd[/COLOR]_***]("http://ubuntuforums.org/showthread.php?t=224351") link from catlett does the trick ( I recommend it).

---

### Post by Yezinki on 2008-11-22
Hi **[FONT="Arial"][SIZE="5"][COLOR="Red"]Linux KING!![/COLOR][/SIZE][/FONT]**

[http://ubuntuforums.org/showthread.php?t=988119](http://ubuntuforums.org/showthread.php?t=988119)

Hope you are doing great.

My Best Regards,

Keep in touch & take care,

Yezinki.

---

