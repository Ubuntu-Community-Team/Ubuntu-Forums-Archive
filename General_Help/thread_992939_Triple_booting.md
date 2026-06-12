---
title: "Triple booting"
date: 2008-11-25
forum: General Help
---

### Post by stalkingwolf on 2008-11-25
I have a 120gb HDD. what I would like to do is partition it with 3 OS
partitions, 1 for 8.04 as primary OS, 1 for 8.10 so I can get it set to the 
flukes of my system, and 1 for test installs.  I would also like to use
a single swap partition and a single /home for the other 3.

Is this possible and if so what is the best method?

---

### Post by stalkingwolf on 2008-11-26
any advice?

---

### Post by ibutho on 2008-11-26
Personally I wouldn't use the same /home for all distros unless you are using different usernames. Sometimes sharing /home can result in settings and file permissions being messed up.

---

### Post by gTinker on 2008-11-26
I agree with ibutho that it would be wise to use a separate home for your "production" system, it's the one you want to keep working during your tests.

A different version may have a different version of some of the applications that you use and thus a possible different config file in your home. In that case it's possible for the config of the newer version to not work with the older version of the application. 

With a different distro on your test partition you might even have more and different config issues, for example if the distro expects different defaults.

I would not expect any permission issues.

As to what is the best way to accomplish the task of partitioning, it depends on what tools you have available, what tools you are comfortable using, and your level of knowledge. Best is a relative term and is more likely to start a flame war or argument among people trying to help than get you helpful information. 

You might also consider leaving some of the drive unpartitioned for things you haven't thought of when you start or if you decide to test with more than one other distro.

They can all happily use the same swap.

---

### Post by stalkingwolf on 2008-11-27
Ok so I have one partition (20gb) with 8.04 on it. standard install with 
/home inside, one partition with 8.10 same as above.  the rest at this point is unallocated.

I will use 2 gb of this as a swap partition.  The balance i guess I need to make an extended partition so that I can create a 20gb partition and a /media
partition.  Or is /media not a primary partition?  what I am getting at is
with the swap and a 3rd 20gb partition that is 4 primary partitions, the max allowed.  If /media is not considered a primary then there is no problem.
if it is a primary then I will need to make an extended pertition with the 20gb and the /media inside it.  Not sure how to do this if needed.  This is the first time I have tried a triple setup.


stepping further from the dark side.:D

---

### Post by gTinker on 2008-11-28
Sorry I took so long to get back to you, I wasn't here yesterday.

The directories (folders) like /media that you mention become part of the filesystem once you have mounted the partition they are on, it doesn't matter whether they are on a primary partition or if they are on a logical partition contained in an extended partition. Swap can exist on either a primary or a logical partition too. So, you have freedom to organise the system any way you choose for partitioning.

---

### Post by stalkingwolf on 2008-12-02
Next question,
when I install a third os  where should i put grub?  Or do I
not need to install it at all?  Will the current installed version
just find the new os?

Sorry never tried a triple before.

---

### Post by Graham1 on 2008-12-02
> **stalkingwolf said:**
> Next question,
when I install a third os  where should i put grub?  Or do I
not need to install it at all?  Will the current installed version
just find the new os?

Sorry never tried a triple before.

Hi

I'm triple booting also. My setup is as follows:-

10GB = Fedora 10 (ext3)
10GB = openSUSE 11.0 (ext3)
10GB = Ubuntu 8.10 (ext3)
100MB = Boot (fat32, XOSL)
2GB = Linux Swap
28GB = Data (ext3, shared)

I'm using XOSL as my boot loader (installed on fat32 partition) which then selects the required distro. I installed GRUB onto each distro's partition. 

I've never installed GRUB to the MBR but I would imagine each distro would include the distro before in it's menu.

:)

---

### Post by Herman on 2008-12-02
> I've never installed GRUB to the MBR but I would imagine each distro would include the distro before in it's menu. :) I agree with Graham1, and I can confirm that if you just install GRUB to MBR each time, each distro will probably include a list all the preceding distros in it's GRUB menu automatically for you. That's the simplest thing to do, so almost anyone can multi-boot. However, it's possible to improve from that type of set-up.
> I'm using XOSL as my boot loader (installed on fat32 partition) which then selects the required distro. I installed GRUB onto each distro's partition. 
 :) I agree once again, I don't know about other distros, but with the Ubuntu installer, it's easy to install the boot loader to the boot sector of Ubuntu's partition by selecting 'advanced' in step 7 of 7 during the installation, and selecting the partition you are installing Ubuntu in rather than the first hard disk's MBR.
When you do it that way though, you'll find it won't boot up automatically for you and you'll need to edit whatever boot manager you have in MBR to add the new OS to the boot list. 
In the long run that's the best way, and it's worth the little bit of extra effort if you're going to be keeping the extra distros for a while.

I use a 'dedicated GRUB partition', for multi-booting 
Ubuntu Intrepid Ibex, 
Hardy Heron, 
Gutsy Gibbon, 
Feisty Fawn,
Debian 
and OpenSuse.
[How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").

You might also find the following link helpful, [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems").

Whatever you do, have fun and enjoy your multibooting experience.
Regards, Herman :)

---

### Post by stalkingwolf on 2008-12-02
I will give this a go.  But first i have to take care of a few of those
real life intrusions on playing.

Actually the turn around time to start with will probably be about 2 months
oe less.  What ever it takes to familiarize myself with them enough to
beable to answer general questions or suggest them as an alternative if
necessary.

---

### Post by Graham1 on 2008-12-02
If you decide to install GRUB to it's own partition in Ubuntu, make sure you enter the correct settings. By default, GRUB will install to hd0 (MBR), if you want to install GRUB to the first partition, choose hd0,0. Second partition, hd0,1 and so on. I've found other distro's (i.e Fedora and openSUSE) slightly easier when selecting the partition to install to.

:)

---

### Post by Graham1 on 2008-12-02
> **Herman said:**
> I use a 'dedicated GRUB partition', for multi-booting 
Ubuntu Intrepid Ibex, 
Hardy Heron, 
Gutsy Gibbon, 
Feisty Fawn,
Debian 
and OpenSuse.
[How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").

Hi Herman

Installing GRUB to a seperate partition has got me thinking :). Could GRUB be installed to it's own partition AND still point to each GRUB on it's own partition? If so, I may use this method instead of XOSL.

Also, you have 5 distro's listed above. Am I right in saying that you may have installed some distro's to logical partitions rather than primary? I've always thought that 3 primarys (i.e Fedora, openSUSE and Ubuntu in my case) were the limit.

:)

---

### Post by Herman on 2008-12-03
> Could GRUB be installed to it's own partition AND still point to each GRUB on it's own partition?Yes, you could do that, but you would still need a boot manager to boot GRUB with if it's installed with it's IPL in a boot sector, since the BIOS will only look at a MBR.

I don't know much about  XOSL, but I googled it and it looks interesting. I think I might give  XOSL a try and see what it's like. :)

> Also, you have 5 distro's listed above. Am I right in saying that you may have installed some distro's to logical partitions rather than primary? I've always thought that 3 primarys (i.e Fedora, openSUSE and Ubuntu in my case) were the limit.It doesn't make any difference at all to Ubuntu or most other Linux distros I've tried whether they're in a primary or a logical partition, so we can install quite a number of operating systems per hard disk, up to 16 I think. And then of course, if we have more hard disks we can have a very great number of operating systems. I don't know why anyone would want to do that, except just to prove it can be done.
Here's a link by one fellow who installed as many operating systems as he could  on four hard disks,  [How to install and boot 145 operating systems in a PC]("http://www.justlinux.com/forum/showthread.php?p=861282#post861282"). - JustLinux Web Forums.

Even Windows can be booted in a logical partition.
Some time ago after we had a few people posting in to the forums here with problems booting Windows in a logical partition I tried some experiments with one of my own computers and found out how to do it. Basically, I found I just needed to set the boot flag on the logical partition, (although I have since been told that isn't necessary for all BIOSes, but for mine it did seem to be necessary. 
GRUB normally uses it's 'makeactive' command for setting the boot flag on whichever Windows installation is to be booted, but GRUB could not set a boot flag in a logical partition last time I checked, and would give an error and quit. The bootable flag can be added to a logical partition using a partition editor though, and GRUB's 'makeactive' command can be diabled by 'commenting it out'. As long as the boot loader files NTLDR, NTdetect.com and boot.ini are presesnt, it's possible to boot Windows XP in a logical partition using GRUB. I haven't tried Windows 98 or Vista, but those should probably be bootable that way too.

Regards, Herman :)

---

### Post by TeXtonyx on 2008-12-03
Hello Herman,

"Even Windows can be booted in a logical partition."

That's usually not what what "they" say. To be bootable Windows
has to have boot files and probably the Registry, a C:\Windows
so it's much different than just formatting a drive fat32 or ntfs
which could be used as a logical data partition. Is that true?

So my question is how did you install a bootable Windows to a
logical partition rather than a primary? I remember that there was 
once a make bootable command A:\sys C: Is that all it takes for XP?
Can you do a full install of XP on a logical partition and it remains
a logical partition and isn't changed into a primary partition?

But you are saying that with a partition editor that once XP is
installed the partition can be changed to logical and it will
still boot directly (boot.ini, ntldr etc)? Or, only with grub?

Your comment was certainly interesting, and an idea that never
occurred to me to experiment with to test. I remember format /s
and it seems to me that the first step, fdisk, required a primary. 
But that with a partition editor, that partition could be changed
to logical and still boot directly; or, it will boot only with grub?

As you can see, I'm struggling to wrap my head around the concept. :-)
If Windows would boot directly as a logical partition, what is the
downside? I recall that Bootit NG allowed exceeding the limit of
4 primary partitions per drive.

---

### Post by Herman on 2008-12-03
:0 Hello TeXtonyx,
> That's usually not what what "they" say. To be bootable Windows
has to have boot files and probably the Registry, a C:\Windows
so it's much different than just formatting a drive fat32 or ntfs
which could be used as a logical data partition. Is that true?

So my question is how did you install a bootable Windows to a
logical partition rather than a primary? :) I don't think that people install Windows that way on purpose or because they want to, it's just something that happens to people.
 A few years ago, if someone had Windows 98 in their computer already and they went and bought a Windows XP installation CD and installed Windows XP after Windows 98, Windows XP would be automatically set up in a logical partition and it would have no boot loader files. Instead, the boot loader files from XP would be moved into the primary partition, (Windows 98 ).
The same thing happens when a Windows user adds another installation of Windows XP too.
The user wasn't informed of this at all, and many Windows users might have found it confusing anyway. The end result was, when the unfortunate Windows user deleted the first (Primary) Windows partition to install Ubuntu, they didn't realize it at the time, but they were deleting their 'boot partition'. So, of course, then soon after we get a post here in Ubuntu Web Forums about Ubuntu or GRUB allegedly destroying the boot files in Windows.
The smarter way to set up a Windows-Windows dual boot is to use a third party boot manager that can 'hide' the older Windows installation until the new one is installed, and then it will install itself into a primary partition and retain it's boot loader files. That was before Windows Vista came along, I haven't noticed this type of problem so much lately, but I do know that Vista can donate it's boot files to XP even if XP is on another hard disk and even regardless of whether it's 'hidden' or not, so that trick won't help anymore.
To better understand what I'm talking about, you should read  [Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") - by Dan Goodell.
 > I remember that there was once a make bootable command A:\sys C:In Windows 95, 98 and ME, the boot sector must point to the boot loader file called IO.SYS. The command 'sys C:' runs SYS.COM which will write a new boot sector and also refresh the important files in the root of drive C: that are needed for booting, which are: IO.SYS, MSDOS.SYS and COMMAND.COM
When you are finished, press 'Ctrl'+'Alt'+'Del' to reboot, and remember to eject and remove the floppy disk so your computer will boot from the hard drive.
> But you are saying that with a partition editor that once XP is installed the partition can be changed to logical and it will still boot directly (boot.ini, ntldr etc)? Or, only with grub?I didn't quite mean that. I don't think you can change a partition from primary to logical, but you could create a logical partition and use a 'dd' command or Partimage or something like that to copy an operating system to another partition. Technically that would be easy to do, but I'm not sure how Windows would react to that. I would worry that kind of treatment might trigger some kind of anti-piracy booby-traps possibly. Maybe it would be okay, someone might hypothetically be able to do that. It should boot.
All I really meant was to help people get their Windows in a logical partition bootable again when someone ends up in that situation by accident. That is possible with GRUB I am sure, and likely also with some other boot managers like XOSL or GAG Boot Manager and some others probably.
> If Windows would boot directly as a logical partition, what is the downside? I recall that Bootit NG allowed exceeding the limit of 4 primary partitions per drive.     
I don't know of any downside. I'm only guessing, but it seems to me that it's not Microsoft's policy to encourage people to dual boot or multi boot so they don't go out of their way to make that easy for people. I'm not sure.

---

### Post by stalkingwolf on 2008-12-04
It never ceases to amaze, me the amount of information available on this site.

Please continue.  I will be coming back as time allows.  I enjoy these
kinds of "side issues".  The information already here should be worth 
at least 6 units at any university.

145 OS's on one machine. WOW. what an asset for a tech. I can see it now
" Wait just a minute while I bring your system up on my computer".  "Ok
now what is the problem you are haveing?"

Talk about choices and possibilities.

---

### Post by stalkingwolf on 2008-12-19
once again life intrudes. Vehicle breakdowns ( how I wish there was a
"fix broken ...command for automobiles) power outages,inet outages etc.

Would it not be great if we had "fix broken" commands for this stuff?

If I dont get back , I wish you all a great Holiday season and a great New Year.

---

