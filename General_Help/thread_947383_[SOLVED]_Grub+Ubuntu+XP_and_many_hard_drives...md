---
title: "[SOLVED] Grub+Ubuntu+XP and many hard drives.."
date: 2008-10-14
forum: General Help
---

### Post by Brandon81 on 2008-10-14
Running Ubuntu on my laptop has been fantastic. I am now ready to go to my desktop with Ubuntu. I absolutely need to have XP on there as well for a few reasons. One being the lack of MS Access support that I need for school. 

In any event, here's my situation, and why I am posting it here when there's tons of information available out there on dual booting Grub with Linux and XP. 

I have the following hard drives, and my mboard is an ABIT IC7:
Motherboard:
SATA A 160GB
SATA B 160GB
IDE 1 320GB
IDE 2 200GB
Then I have a SATA PCI card I bought, which has the following:
SATA C 500GB
IDE 3 80GB. 

The BIOS will not show the 2 drives off the PCI SATA card (obviously)

Here is the order that the drives show when I install Ubuntu:
sda 500GB
hdb 80GB
hdc 320GB
hdd 200GB
sde 160GB
sdf 160GB

I had had the 2 160GB drives on a RAID0, but raid is such a pain in the *** that I decided "I'll break down the RAID array and install XP on one 160GB drive and Ubuntu on the other! Easy!"

Not quite so easy. 

Installing XP is easy, obviously. XP installs to the drive, and boots, no problem. 

Here's what I've done so far:
Installed XP to SATA A
Installed Ubuntu 8.04 to SATA B using Guided, entire disk option. 

Rebooting brings me directly to XP with no option (obviously) for Ubuntu.

Following some guides, I have booted to the Live CD and then run that dd options to extract the first 512 bytes of the hard drive Linux is on and extracted it to a file and then got my windows Boot.ini to point to that file. This would be my preferred method, but it doesn't work. I get disk not found errors when I go to boot to Ubuntu. 

According to another guide, I then tried this:
I switched the XP and Ubuntu 160GB Drives so that the Ubuntu drive was now sde. I then reinstalled Ubuntu. This would not allow Ubuntu to boot. Would get file or disk not found errors just trying to straight boot to ubuntu.

I've booted to the LiveCD and then ran GRUB, find /boot/grub/stage1 (says hd4,0) and then run setup (hd4).

Then I can't find the /boot/grub/stage1 file anymore if I search and I get a different set of file not found/disk not found errors. I've also tried the same thing after mounting the linux drive to a folder within the live cd. I've definitely done all commands prefixing with sudo, just so no one thinks it's a permissions issue. 

Basically at this point, I am pretty sure this has to do with the order that Ubuntu is listing the drives as opposed to the BIOS listing the drives, but I have absolutely no idea how to figure out what's where aside from the live cd, which is where it's coming up wrong. 

I would prefer to keep all the drives connected and in the same boot order so as to avoid problems as I would assume that things would change if I disconnected everything but the Ubuntu drive, installed it, then reconnected everything. I could be wrong though. 

All of the guides for more then one disk and dual booting have like 2 disks, which seems to be considerably easier. I wish there was an easier way to do this. Basically all I want is for the PC to boot, and give me an option to boot to Ubuntu and XP and having Ubuntu be the default (and load after 30sec or whatever)

One other thing I've found that I haven't specifically tried yet is this: [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902) but this seems like it doesn't solve my problem of hard drives booting up in different orders. It doesn't seem like the 500gb and 80gb drives off the sata card should be the first two disks. 

Thanks so much in advance.

EDIT: Unfortunately I am at work and this is regarding my home computer, so I wouldn't be able to try anything until late tonight or tomorrow as I have school after work today. I am sorry about that but I really wanted to get the ball rolling here and see if anyone else has had any similar experiences or good ideas for resolving this issue.

---

### Post by justleen on 2008-10-14
Ubuntu will install grub on the second drive. XP install the windows bootloader on the first drive. YOur bios is set to boot from the first drive, thus never even seeing grub.
As far as i can tell, all you need to do is make the other disk primary boot, which should give you a grub menu with XP in it..

---

### Post by Brandon81 on 2008-10-14
Thanks for the quick reply! 

I kind of did that, but by physically switching the SATA ports for the Windows and Linux drives, but that probably screwed up the boot order of things. 

So basically, if I understand you correctly, I should set my boot order as such:

SATA A (Will be Windows Drive)
SATA B (Will be Ubuntu Drive)
200GB
320GB

Install Windows to SATA A.

Then change boot order to

SATA B
SATA A
200GB
320GB

Then install Ubuntu to SATA B

Is that right?

I don't know that that will work because I have installed Ubuntu to the 1st drive in the boot sequence, and then trying to straight boot into it without any other changes I've gotten errors, and I think it has to do with the SATA PCI card in there. I think that BIOS is considering when booting the order of drives I listed above, but then when installing it for some reason it's putting the PCI card drives first.

I will try your suggestion, and if that doesn't work I will try it with the 2 SATA PCI card drives disconnected. I have a feeling that's what I will have to do.

---

### Post by justleen on 2008-10-14
no, thats not right.

I was under the impression you already had both installed.

Normally, you should be able to
1) install xp to disk A
2) install ubuntu to disk B
3) Go!
(as in: the boot order should stay the same after installing an OS)
if, however, windowsbootloader is installed on driveA and grub is installed on driveB, then you have to switch the boot order.

If you have already changed the boot order after the installs, then you probbly have restore it to the orginal config, and reinstall grub.

edit: The number of drives really shouldnt matter, the only thing you should be concerned about are the two drive you're installing to.
All the other drives just get drive letters (xp) or mountpoint (linux assigned)

---

### Post by caljohnsmith on 2008-10-14
Usually what is most ideal in your situation is if you can change your BIOS to boot your Ubuntu drive, make sure Grub is installed to your Ubuntu drive, and then add entries in your Grub menu for booting Windows or any of your other drives. If you really don't want to change your boot order, you could install Grub to the MBR (Master Boot Record) of your Windows drive while leaving Grub's boot files on your Ubuntu drive; the big disadvantage of doing that though is if anything happens to your Ubuntu drive (like simply disconnecting it or file system problems in Ubuntu for example), then you won't be able to boot at all, not even Windows. If instead you install Grub to the MBR of your Ubuntu drive and set BIOS to boot it first on start up, you won't be touching your Windows drive, and thus you could easily boot your Windows drive should anything happen to the Ubuntu drive. 

Which do you prefer to do? I can give specific instructions of how to set up either scenario if you would like help. :)

---

### Post by Brandon81 on 2008-10-14
Thank you guys. 

I've tried it as you describe. Both basic ways of setting it up result in file not found errors when trying to boot up. 

I installed Ubuntu onto SATA B after installing windows on A and no go. 

When booting to the Ubuntu drive, I can't boot into Ubuntu. Never have on my desktop PC. Everytime I boot up to the linux drive getting these file not found and disk not found errors. 

I really believe that the BIOS loads the drives like this:

Disk 1: 320GB IDE1
Disk 2: 200GB IDE2
Disk 3: 160GB SATA1
Disk 4: 160GB SATA2

And then somehow after the boot, it then detects the drives off of the sata controller card, and somehow puts them into the disk 1 and 2 spots, so when linux is installed, grub looks to 4 when I think ** it should be looking for a different hard drive number on the initial boot. 

It's all very strange. 

preferably I'd like to use the windows boot loader from SATA1 and have it default to the linux option and then go into grub from there on the linux drive. 

I don't really care very much how it's set up. I just need to be able to dual boot effectively, and have linux be default (do a lot of remote desktoping and want to make sure if rebooting it'll go back into Ubuntu, which will be my main OS)


Oh... and theoretically I have windows and Ubuntu installed already to both drives. I have at this point switched the SATA drives, so Windows, which was on SATA1 (sde) is now on SATA2 (sdf) and Linux is now on SATA 1 (sde)

I think the last thing I did trashed grub, as I was getting the file not found when running "find /boot/grub/stage1" in the grub menu on the live cd. 

I know I'm not giving you guys a lot to work with, I'm sorry about that! I am going to try to install with the SATA controller disk drives disconnected, I think that's the answer. Then it will match the bios for the disks, I think.

---

### Post by ram130 on 2008-10-14
Your  bios should  just give u a option to select  a boot device temporarily after the boot screen(i think its f12). Use it and select the  drive  the ubuntu install is currently on. If that does not work, repeat the process until you see grub load. As soon as u find it, note  the hard drive  grub loaded from. Then reinstall grub from the live cd using the find option. Then select the drive  in the bios that grub had booted from. You should be good to go. 


If not....let me know

---

### Post by WWSmith36 on 2008-10-14
I recommend having grub handle all you booting.  So I would definitely set your ubuntu drive to be the primary boot drive.  If you get the grub boot menu you are doing good.

Typically when there are many mixed drives (IDE, SCSI, SATA) on a machine you will get errors when trying to boot this is caused by the bios, grub, and kernel specifying them differently.

Grub will not boot either OS properly if the specification is menu.lst is incorrect.  Fortunately if you can get to the boot screen, grub is your friend. 

 You instead of selecting one of the options in the menu, choose to ´e´ to edit the root parameter - you can experiment to find the right one.  Or select ´c´ and enter grub CLI where you can use the find command determine the correct unbuntu boot partition.  After you get into ubuntu you can fix you windows boot entry - specific the correct windows partition and using the map command as well.

Here a link to good Grub Page (it is long) so you may want to search the page for these reference: **Chainloading Windows on a non-first hard disk** and **How to use GRUB's Command Line to investigate a computer**
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_OS_entries](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_OS_entries)

Hope this helps

---

### Post by Brandon81 on 2008-10-14
Thank you guys again :)

Really excellent how quickly and easily people are helpful here. I don't know what took me so long to jump onboard the Linux train. 

I am looking into a Windows installable boot loader, Acronis... ever hear of it?

I will probably give Grub another shot too. I honestly think the best bet is to disconnect the 2 hard drives off of the SATA card, because I think that's what the problem is. It has to do with what order they load in and at what point in the process. Anyway, just wanted to give an update, I am sure I'll get it working. Appreciate the help.

---

### Post by TeXtonyx on 2008-10-14
Following some guides, I have booted to the Live CD and then run that dd options to extract the first 512 bytes of the hard drive Linux is on and extracted it to a file and then got my windows Boot.ini to point to that file. This would be my preferred method, but it doesn't work. I get disk not found errors when I go to boot to Ubuntu.

TeX: Maybe you neglected to mention a crucial step. During the live cd install to
the drive, at step 7 under "Advanced" did you choose *not* hd0, which is the MBR,
but to one of the partitions displayed in the dropdown menu? That is called installing
to the boot partition. Then you copy the first 512 bytes of that partition. I think it is
a mistake to use dd to do this because it is a lot easier to make a typo. Bootpart is
free, displays the partitions, and writes the boot entry to boot.ini. From C:\ , you
would type something like: bootpart 10 ubuntusdb.bin "UbuntuSdb" <enter>
Here is a useful but not exact url:
[http://forums.majorgeeks.com/showthread.php?t=108021](http://forums.majorgeeks.com/showthread.php?t=108021)

If you resize a partition then run Bootpart again. If you installed grub to the MBR,
then you will need to reinstall grub to the appropriate boot partition. Also I think
it is a good idea to have that grub menu.lst duplicate most of the boot options
provided by the boot.ini menu. (I didn't mean that dd wouldn't work.)

---

### Post by Brandon81 on 2008-10-15
> Maybe you neglected to mention a crucial step. During the live cd install to
the drive, at step 7 under "Advanced" did you choose *not* hd0, which is the MBR,
but to one of the partitions displayed in the dropdown menu? That is called installing
to the boot partition.

Please forgive me, but I'm not sure if I fully understand this.

When installing Ubuntu, say in my situation I get a drive list up like this when I choose manual:

sda (1) 500GB } Off of the SATA Controller card
hdb (2) 80GB } Off of the SATA Controller card
hdc (3) 320GB
hdd (4) 200GB
sde (5) 160GB (This drive should have either Ubuntu or Windows XP)
sdf (6) 160GB (This drive should have the other OS)

Whats the right procedure here?

Say I want to have Ubuntu on drive 5. (There is no OS on either 500GB drive or 320GB drive)
What do I do here? Guided and then Use Entire Disk?

When I do this, even if that drive is set to the first disk in the boot list in BIOS it will NOT boot. I get the grub screen, but then continually getting file not found errors or system or disk not found errors. I have *never* once booted to an off the hard drive copy of Ubuntu on my desktop PC. I have never been able to boot either OS with grub. 

So what do I do where? Should I after installing Ubuntu to sde then go into the Live CD and install the Grub loader on the 500gb or 320gb drive? That doesn't make sense to me.

> Typically when there are many mixed drives (IDE, SCSI, SATA) on a machine you will get errors when trying to boot this is caused by the bios, grub, and kernel specifying them differently.

Grub will not boot either OS properly if the specification is menu.lst is incorrect. Fortunately if you can get to the boot screen, grub is your friend.

You instead of selecting one of the options in the menu, choose to ´e´ to edit the root parameter - you can experiment to find the right one. Or select ´c´ and enter grub CLI where you can use the find command determine the correct unbuntu boot partition. After you get into ubuntu you can fix you windows boot entry - specific the correct windows partition and using the map command as well.

I have tried this as well. I can't remember if I actually did the find /boot/grub/stage1 command or if it was possible, but I definitely messed around with it a little bit, changing to a couple different #'s for the harddrive. Maybe I should just start at 0 and make my way up one at a time till it boots. I don't really know. This is a PITA.

---

### Post by caljohnsmith on 2008-10-15
Brandon81, unfortunately the exact method that TeXtonyx is suggesting will only work if you have Ubuntu and Windows installed to the same drive. If you instead install Ubuntu to another drive, and try to add the Grub boot sector to your Windows boot loader like his method suggests, the Grub boot sector won't point correctly to the Ubuntu drive when you move it to the Windows drive. It is possible to install Grub in a special way to the boot sector so that it will correctly point to an external drive, and then copy it over for the Windows drive for the Windows boot loader to use, but his method does not take that case into account. If you really want to use that method of adding the Grub boot sector to your Windows boot loader on the other drive, I can help you with installing Grub so that the method would work. But there are some definite disadvantages to using that method, and I encourage you to read this thread if you want some of the details:

[http://ubuntuforums.org/showthread.php?t=944483](http://ubuntuforums.org/showthread.php?t=944483)

Personally, I would recommend for your situation using Grub4DOS, because you can install it within minutes into your Windows drive and then use the menu.lst copied over from your Ubuntu on the other drive (of course you'll have to modify it just once to make it point to the correct Ubuntu drive for Ubuntu). One advantage of this method is you will only get one boot menu (if you set it up that way) on start up where you can choose either Windows or any of your Ubuntu entries. If you use TeXtonyx method, you will have to go through two boot menus on start up to get Ubuntu. If you automount your Windows partition in Ubuntu on start up, you can even use a symbolic link from Ubuntu to your menu.lst in Windows so that Ubuntu will automatically update your menu.lst when you get new kernels and such. 

There are other methods for your situation as well, including making a dedicated Grub partition on your Windows drive, but I think Grub4dos is easier since you don't have to create any new partitions. If you want help giving Grub4dos a try, I would be happy to help, just let me know. Or if you really want to add Grub to your Windows boot loader, I can help with that too. :) But regardless what you decide, it would help if you would please post:
```
sudo fdisk -lu
```

---

### Post by Brandon81 on 2008-10-15
Thanks. I am a pretty advanced Windows user, and I believe I have a very good handle on Ubuntu, but this booting stuff is really giving me a headache. Especially with the various hard drives I have. I have had Windows installed at one point or another on 1 160GB, Vista on the 200GB, and XP on the 320GB. 

Would that in any way affect what I'm trying to do here?

My boot order in BIOS is 
sde 160GB drive 
sdf 160GB drive
320GB Drive
200GB drive.

The OS remnants on the other drives shouldn't affect this right? The computer is going to go to sde drive for booting regardless, right? I'm getting to the point where my preferential way of setting it up is getting less and less important. I am at the point where I'll do just about anything to get this damn thing to work correctly. 

> Personally, I would recommend for your situation using Grub4DOS, because you can install it within minutes into your Windows drive and then use the menu.lst copied over from your Ubuntu on the other drive (of course you'll have to modify it just once to make it point to the correct Ubuntu drive for Ubuntu)

I remember trying Wingrub with no success. Grub4Dos huh? This installs grub to my windows partition (primary and # 1 HDD according to boot order sequence in BIOS) and then I can modify it to include the Linux drive? (whether or not GRUB is installed on the Linux drive) Is that correct?

Thanks so much for the help!!

EDIT: BTW I will post the command line you requested as soon as I get home! (Around 5PM EST)

---

### Post by caljohnsmith on 2008-10-15
> **Brandon81 said:**
> Thanks. I am a pretty advanced Windows user, and I believe I have a very good handle on Ubuntu, but this booting stuff is really giving me a headache. Especially with the various hard drives I have. I have had Windows installed at one point or another on 1 160GB, Vista on the 200GB, and XP on the 320GB. 

Would that in any way affect what I'm trying to do here?

You should be fine regardless of what OSes you have installed on which drives; the important thing at this point is that sde has Windows, and it successfully boots up on start up.
> **Brandon81 said:**
> 
My boot order in BIOS is 
sde 160GB drive 
sdf 160GB drive
320GB Drive
200GB drive.

The OS remnants on the other drives shouldn't affect this right? The computer is going to go to sde drive for booting regardless, right? I'm getting to the point where my preferential way of setting it up is getting less and less important. I am at the point where I'll do just about anything to get this ~dang~ thing to work correctly. 

Yes, any OS "remnants" should not make any difference to booting so long as you are currently able to boot sde successfully. :)
> **Brandon81 said:**
> 
I remember trying Wingrub with no success. Grub4Dos huh? This installs grub to my windows partition (primary and # 1 HDD according to boot order sequence in BIOS) and then I can modify it to include the Linux drive? (whether or not GRUB is installed on the Linux drive) Is that correct?

Thanks so much for the help!!

Yes, you can easily boot your Ubuntu drive from Grub4DOS, or you can simply add all the Ubuntu entries to your Grub4DOS menu.lst so that you will only have one boot menu on start up that will allow you to boot Ubuntu directly; then you can "symlink" the Grub4DOS menu.lst back to your Ubuntu install so that Ubuntu will automatically update the menu.lst when new kernels are installed. 

Anyway, here is the method:
[LIST=1]
[*]Download and unzip Grub4DOS from [here]("https://gna.org/projects/grub4dos/").
[*]Copy the "grldr" binary file to your sde Windows root directory C:\
[*]Copy your Ubuntu's /boot/grub/menu.lst to the sde Windows root directory C:\
[*]Next, from Ubuntu (use the Live CD if you have to), open a terminal and navigate to the Grub4DOS directory that you unzipped which should have a "grldr.mbr" file, and do the following:
```

sudo dd if=grldr.mbr of=/dev/[COLOR="Red"]sde[/COLOR] bs=440 count=1
sudo dd if=grldr.mbr of=/dev/[COLOR="Red"]sde[/COLOR] skip=1 seek=1
```
Make sure you get the correct drive above (sde). The above commands will install a grub4DOS MBR (Master Boot Record) to the sde HDD. And just for completeness, I should mention that if you download the "grubinst" package too, you can instead install the grub4DOS MBR using the "grubinst" command from DOS; I prefer to do it from linux is all.
[*]Modify the menu.lst by adding the following entry for Windows on your sde drive:
```
title        Windows
root (hd0,0)
chainloader +1
```
The above (hd0,0) assumes that Windows is on the first partition of sde.
[/LIST]
Next, reboot, and you should see the Grub4DOS menu on start up, and the Windows entry should work, but Ubuntu is a different matter; because you have so many other drives, probably the best way to figure out the correct (hdX,Y) drive that Ubuntu is on, just select a Ubuntu entry in the Grub4DOS menu, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd1,Y)", press return to save the change, then press "b" to boot. If that doesn't work, then try X = 2, 3, and 4; one of those values should work to boot Ubuntu. Note that the change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So that's about it except for making a symlink from the Grub4DOS menu.lst back into your Ubuntu's /boot/grub directory; if you need some help with that let me know. Otherwise let me know how it goes or if you run into problems. :)

---

### Post by Brandon81 on 2008-10-15
Thank you so much for the detailed tutorial. 

Let me just ask this. Does Windows use hd(0,0) regardless of where it actually shows up when I load the Ubuntu Live CD (In other words in there Windows is on hd(4,0), and in my Windows Disk Manager, it's Disk 3 I think, though I'd have to double check.

Specifically this I mean: 
```
title        Windows
root (hd0,0)
chainloader +1
```

---

### Post by caljohnsmith on 2008-10-15
> **Brandon81 said:**
> Thank you so much for the detailed tutorial. 

Let me just ask this. Does Windows use hd(0,0) regardless of where it actually shows up when I load the Ubuntu Live CD (In other words in there Windows is on hd(4,0), and in my Windows Disk Manager, it's Disk 3 I think, though I'd have to double check.

Specifically this I mean: 
```
title        Windows
root (hd0,0)
chainloader +1
```
That's an excellent question; it is something that I too was confused about for a long time when I first started learning about Grub and booting issues. Finally a few kind souls enlightened me :), and I found out it works like this: on start up, Grub sees the order of drives as the same as the BIOS boot order, because on start up Grub must use BIOS to access the drives. But the BIOS boot order has nothing to do with the device order in Linux's /dev directory, because Linux works through the kernel (not through BIOS) to access the drives; Linux's /dev directory is ordered by the type of device, so for HDDs they would be ordered by whether they are IDE, SATA, USB, and so on. 

Because you will be booting the sde drive first, that means Grub will see sde as (hd0) on start up; thus Windows will be on (hd0,0) if Windows is in the first partition. Does that now make sense? :)

---

### Post by Brandon81 on 2008-10-15
Wonderful, thank you. Finally, that part of it makes sense now. I will do what you say when I get home and I think I'll have some better luck now! :)

---

### Post by Brandon81 on 2008-10-15
I followed your directions, and thanks to your explanation of the boot order with hd0, hd1, etc, I am now officially in my copy of Ubuntu on my second drive! I am so relieved! I used the grubinst program from windows, booted into the Linux LiveCD and copied over the menu.lst and modified it from hd4 to hd1, which would be the second drive in my boot sequence, and then I added what you told me to for windows. 

Now I will see if I can get into Windows. Ah... it stopped saying partition is already active. 

Editing menu.lst to remove that command...

And I'm in Windows!

Wow. After all that, it really became quite easy once it was properly explained :) 

Thank you so much again! :D

---

### Post by caljohnsmith on 2008-10-15
That's great news, glad I could help out. Cheers and have fun Ubuntu-ing. :)

---

### Post by Brandon81 on 2008-10-15
One final question! :)

How do I mark this thread as solved?

EDIT: Found it! Everythings good here! Going to install the updates and hardware drivers now :)

---

### Post by TeXtonyx on 2008-10-15
[QUOTE=Brandon81;5969456]Please forgive me, but I'm not sure if I fully understand this.

When installing Ubuntu, say in my situation I get a drive list up like this when I choose manual:

sda (1) 500GB } Off of the SATA Controller card
hdb (2) 80GB } Off of the SATA Controller card
hdc (3) 320GB
hdd (4) 200GB
sde (5) 160GB (This drive should have either Ubuntu or Windows XP)
sdf (6) 160GB (This drive should have the other OS)

Whats the right procedure here?

------------------------------------------------------------------------

OK Brandon, this is what you wrote before:

Installing XP is easy, obviously. XP installs to the drive, and boots, no problem.

Here's what I've done so far:
Installed XP to SATA A
Installed Ubuntu 8.04 to SATA B using Guided, entire disk option.

Rebooting brings me directly to XP with no option (obviously) for Ubuntu.

Following some guides, I have booted to the Live CD and then run that dd options to extract the first 512 bytes of the hard drive Linux is on and extracted it to a file and then got my windows Boot.ini to point to that file. This would be my preferred method, but it doesn't work. I get disk not found errors when I go to boot to Ubuntu.

--------------------------------------------------------

When you reboot it brings you to XP. That 512 bytes has to be copied to
C:\  It should be named something like Ubuntu.bin and is in the C:\ directory.
That 512 byte file is not left on Ubuntu or on a floppy disk, but C:\ root

Your boot.ini file has an entry like C:\ubuntu.bin="Ubuntu" and that
puts Ubuntu on your boot.ini boot menu so that you can choose it. I told 
you about Bootpart because it writes ubuntu.bin (512) and to boot.ini 
automatically, to the C:\ root and edits your boot.ini after Ubuntu installs.
Again, boot.ini points to the 512 bytes on the XP C drive, not Ubuntu.

The other thing is that grub must be installed for this method to work.
And not in the MBR, but in boot partition of the Ubuntu drive. That is
how it works if you want to boot to Ubuntu from your XP boot.ini file.
That is how the 512 bytes method works which you stated you wanted to use.

Yes, you can use grub installed in the XP MBR to boot XP and other OS's.
I'm also going to correct a misimpression that caljohnsmith posted.

---

### Post by TeXtonyx on 2008-10-15
[QUOTE=caljohnsmith;5969652]Brandon81, unfortunately the exact method that TeXtonyx is suggesting will only work if you have Ubuntu and Windows installed to the same drive. If you instead install Ubuntu to another drive, and try to add the Grub boot sector to your Windows boot loader like his method suggests, the Grub boot sector won't point correctly to the Ubuntu drive when you move it to the Windows drive. 

------------------------------------------------------------

I haven't tested my post on sata drives but only ide drives. So it is possible
that the behavior is different. But on ide drives the method I provided
always works. I have one computer with two drives and Ubuntu installed on
both drives. XP + Ubuntu and Fat32 +Ubuntu. My boot.ini loaded from the
first drive has entries: C:\ubuntuA.bin="UbuntuA" and C:\ubuntuB.bin="UbuntuB"
I have used both the dd method and Bootpart and Bootpart is easier.

My other computer has XP + Ubuntu on the first drive and Vista + OpenSuse
on the second drive. I used Bootpart to create the *.bin files. boot.ini
on the XP first drive can boot Ubuntu or OpenSuse. I boot Vista which is
on the second drive by adding an entry to the grub menu.lst (Ubuntu).
I could also boot Vista from the OpenSuse grub menu.lst also on first drive. 
(the boot.ini generated menu entry I mean).

Besides my evidence, you can find websites which detail using two drives
Windows and Linux and using Bootpart or dd to write the *.bin file.
Also you can download Bootpart and run it from a Windows drive if you
still have one. For two drives it will list them as C and D. If Ubuntu
is on drive D(the second hard drive) it will show a number like 7 next
to the Linux ext3 file extension. So if you type a command like
C:\bootpart 7 ubuntu.bin Ubuntu
That copies the first 512 bytes of the Ubuntu boot partition, located on
the second drive, to the first drive XP, to its root partition C:\
It writes the correct entry to boot.ini.
This works if one has installed grub to the Ubuntu boot partition
If one messes with the partition size, then run Bootpart again. 

If you were making this claim from your personal experience, then it's
user error than made it not work (unless sata prevents it somehow).

---

### Post by unutbu on 2008-10-15
caljohnsmith, congrats on another boot well done :)
Would you please explain what is the reason for installing grldr.mbr in two parts
```

sudo dd if=grldr.mbr of=/dev/sde bs=440 count=1
sudo dd if=grldr.mbr of=/dev/sde skip=1 seek=1

```
Isn't this the same as 
```

sudo dd if=grldr.mbr of=/dev/sde

```
Many thanks,
unutbu

---

### Post by caljohnsmith on 2008-10-15
> **unutbu said:**
> caljohnsmith, congrats on another boot well done :)
Would you please explain what is the reason for installing grldr.mbr in two parts
```

sudo dd if=grldr.mbr of=/dev/sde bs=440 count=1
sudo dd if=grldr.mbr of=/dev/sde skip=1 seek=1

```
Isn't this the same as 
```

sudo dd if=grldr.mbr of=/dev/sde

```
Many thanks,
unutbu
Hi Unutbu, the reason for doing it in two parts is so that installing the grub4DOS MBR doesn't overwrite the HDD's partition table and disk signature in the MBR; from the references I've read, this is what the MBR looks like:
```

**Bytes:**
  1-440    MBR boot code
441-444    4 byte "disk signature" used by Windows OSes
445-446    nulls
447-510    partition table
511-512    MBR signature, always 0xAA55 (byte 511=55, byte 512=AA)

```
I should mention that most of the time changing the disk signature is not a big deal *unless* you use an OS like Vista, and I don't remember the details of how and why Vista uses the disk signature while other OSes really couldn't care less; I just read that changing the disk signature with a Vista system can break Vista. :)

So anyway, the reason for copying that glrdr.mbr boot loader in two steps is to avoid overwriting the disk signature and partition table: the first dd command copies the first 440 bytes of that file, and the second dd command copies the rest of the glrdr.mbr to the sectors right after the MBR (similar to the way the Grub stage1.5 file is written to the sectors right after the MBR). If you look at the glrdr.mbr file in a hex editor, you will see that bytes 441-512 are zeros where the disk signature and partition table need to be, and of course that is deliberate on the part of the Grub4dos developers. And actually the boot loader code happens to end before byte 440, so that's the number I arbitrarily used in the above command. If you use the method of copying all the glrdr.mbr file at once like you suggest, the disk signature and partition table would then be overwritten with zeros, which will unfortunately make the HDD look like it is unformatted. :)

---

