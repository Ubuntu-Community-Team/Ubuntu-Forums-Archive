---
title: "Windows XP does not recognize my partitions made in GParted"
date: 2008-09-14
forum: General Help
---

### Post by Pontus9 on 2008-09-14
I am currently running Ubuntu 8.04 but I have decided to dual-boot with a version of windows XP also.

I have my sda formated to ext-3 and have recently turned my sdb into a FAT32 using GParted. However when I try to install windows XP on that partition it says it is not a file system supported by windows. So I then split my sdb into two partitions sdb1 as NTFS and sdb2 as FAT32. However my windows installer still tells it can not install on either of the partitions because they are not supported by windows.

Ideally, I would like to have my whole sdb as FAT32 and run windows from there. Any ideas what might be wrong?

---

### Post by benerivo on 2008-09-14
Don't know why this is happening. It should work the way you have done it. Are there no partitioning options in the xp installer? My xp disk used to be able to create, delete and format partitions at the start of the process.

---

### Post by alzie on 2008-09-14
This sounds a bit like my wife's (windows only) computer.  XP just didn't want to go on, and it didn't want to format.  I think it was an issue with the boot sector.

I ended up using the ultimate boot cd ( [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) ) to wipe the disk before formatting.

I hope this helps you.

---

### Post by Pontus9 on 2008-09-14
Thank you for your replies. I will try to experiment some with the windows CD and see if that's where the problem is.

---

### Post by Sycron on 2008-09-14
You should format the drive from ubuntu, but as far as i've understnd you have windows on it...

---

### Post by DOSIX on 2008-09-14
dude, windows isn't designed to read ext3 partitions. it is normal for it not to recognize. i don't even think that vista recognizes it either.

---

### Post by bigbear2350 on 2008-09-14
you need this to read ext2 in windows

[http://www.fs-driver.org/](http://www.fs-driver.org/)

When ext3 is cleany unmounted than it can be mounted as ext2. Ext3 is ext2 but ext3 has a journal where ext2 dosent.

---

### Post by lewisskinner on 2008-09-14
> **DOSIX said:**
> dude, windows isn't designed to read ext3 partitions. it is normal for it not to recognize. i don't even think that vista recognizes it either.

> **bigbear2350 said:**
> you need this to read ext2 in windows

[http://www.fs-driver.org/](http://www.fs-driver.org/)

When ext3 is cleany unmounted than it can be mounted as ext2. Ext3 is ext2 but ext3 has a journal where ext2 dosent.

He never even mentioned ext2 or ext3!  He's trying to install XP or a FAT32 drive!

Please be aware that Windows cannot be installed on logical partitions (although it does recognise them), so, if you have formatted the FAT32 drive as a logical partition (within an extended partition) this will likely be your problem.

If however, you are trying to install onto a primary partition, then I'm stumped.  I have heard people who say that Windows likes to be in the first partition on the drive.  Could it be that?

---

### Post by Sycron on 2008-09-15
> **lewisskinner said:**
> He never even mentioned ext2 or ext3!  He's trying to install XP or a FAT32 drive!

Please be aware that Windows cannot be installed on logical partitions (although it does recognise them), so, if you have formatted the FAT32 drive as a logical partition (within an extended partition) this will likely be your problem.

If however, you are trying to install onto a primary partition, then I'm stumped.  I have heard people who say that Windows likes to be in the first partition on the drive.  Could it be that?

You say it right. That's it!

---

### Post by Pontus9 on 2008-09-15
Currently I have my sdb formated as a primary partition with fat32. This is where I am trying to install windows. Since there is only (currently) one partition on this drive it is also the first partition of this drive.

On my other drive (where I have ubuntu installed) I currently have one ext3 partition and one extended partition with a linux-swap inside of it (standard?).

I have tried with multiple copies of Windows XP now and keep getting the same error. It says "This is not a windows compatible partition" after I press enter to setup windows (having selected my fat32 partition). If I try to partition using the bootable CD I get the same error.

I mustn't install Windows on the same drive that I have installed Ubuntu on, do I?

---

### Post by Pontus9 on 2008-09-15
I have come so far now that I no longer think my problem lays in GParted (I bladed it since I was new to it, hehe). Now I am convinced there must be something wrong with the setup of my drive. I have tried to leave the whole drive unpartitioned and let my boot CD (two different boot CDs even) partition it and I keep getting the same error. The drive does not contain a windows supported partition.

The thing is that I had a OS on this drive only like 6 months ago, and then all were fine.

Any help is appreciated.

---

### Post by Jonie on 2008-09-15
As far as I can see from the posts above, the boot drive in BIOS is sda, which has no recognizable filesystem for Windows to put ntldr and boot.ini. Since you cannot change the order in which BIOS sees drives when you boot from CD you may try to unplug temporarily sda, install Windows and then add it to GRUB menu.lst or use BIOS boot menu to boot Windows. Install XP either solo or make a little bit of fat32/ntfs on sda, just to put those 2 small files.

---

### Post by mkrahmeh on 2008-09-15
this may not make a difference though, but usually i'd prefer installing windows before ubuntu (or any other linux dist.)

---

### Post by Pontus9 on 2008-09-15
I unplugged my sda and managed to successfully install windows on my sdb (I think)! Thanks Jonie.

However, when I then tried to reboot my computer with only sdb connected it gave me "disk error" and only allowed my to boot from the bootCD.

I then plugged my sda back in and it still gave me "disk error" so I had to unplug sdb to even get my computer running again.

Now I am downloading Ubuntu Live to try to start my computer with both drives plugged in and "update the boot sector on GRUB". That part I was told to do by a friend. I will see what I can do. Is 'updating the bootsector on GRUB' what I must do to make this work? And how do I do that if so?

(And yes, it seems easier to install windows first and then Ubuntu, but that was not an option to me at first.)

---

### Post by Jonie on 2008-09-15
I see no reason why should that disk error occur. Is your BIOS set up to do the HDD autodetection each time the computer starts? Remember also to set up jumpers on the disks accordingly.

To add Windows to the Grub menu just add those lines to /boot/grub/menu.lst


title		Windows XP
rootnoverify	(hd1,0)
makeactive
chainloader	+1

However, if your Windows disk was running solo during install you may try to swap BIOS drives.

title		Windows XP remapped
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify		(hd0,0)
makeactive
chainloader	+1

Add both entries and see which one boots.

BTW, in case you have deleted the first partition from XP, left the second and then recreated the first, wtithout having a few megabytes free at the end of disk, XP will leave some space at the front of the disk making the partition table inconsistent and unbootable. This is a rare error, but I've already seen it . This might be the cause of "disk error".

---

### Post by Pontus9 on 2008-09-15
Thank you for your new reply.

First of all I must point out I am very new to Ubuntu and I do not know how or where (at the end of the file?) to add those lines. When I tried opening the file in a text editor (yes, I tried the GUI way...) I was not able to save since I did not have authorization. What is the command for editing the file?

And yes, my windows disk was running solo when I installed windows since I had unplugged my sda drive. Will this make windows run the boot and take over the job of GRUB? How do I solve that?

By the way, I now managed to start both my drives at the same time. I did not get any option to choose OS, it just started Ubuntu right away even though I have both my drives plugged in (and can access both from Ubuntu).

EDIT: I found out how to edit the file. I have done so now and am currently rebooting.

---

### Post by Pontus9 on 2008-09-15
I added the lines Jonie wrote to the very end of /boot/grub/menu.lst.

After playing around with the timeout (setting it to 10 instead of 3) I managed to find the menu where I am to select OS (duh...). In the list I see both 'Windows XP' and 'Windows XP remapped'. However none of them is working. 'Windows XP' gives the "disk error" and the only option is to reboot the computer and 'Windows XP remapped' says something about not being executable.

---

### Post by Jonie on 2008-09-15
Have you read the addendum to my last post? It seems that the error comes from Windows Master Boot Record:

Disk error.
Press ctrl+alt+del to restart.

Right?

This usually means that the partition table is inconsistent. Can you post the output of sudo fdisk -l /dev/sdb from Ubuntu? If you can, show me also your Windows boot.ini file.

Correction: of course I made a mistake - there should be rootnoverify for Windows instead of root.

---

### Post by Pontus9 on 2008-09-16
I think it says "Disk error - Press any key to restart", but yes.

I wrote: fdisk -l /media/disk (that seems to be the name of the drive)
[I]
last_lba(): I don't know how to handle files with mode 40700[/I]

If I write: fdisk -l /dev/sdb

[I]Cannot open /dev/sdb
[/I]

The boot.ini says:
[I]
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\ = "Det gr inte att identifiera ett operativsystem p enhet C." [/I]

Where the last line means "It's not possible to identify a OS on drive C".

---

### Post by Jonie on 2008-09-16
A little omission: ```
_sudo_ fdisk -l /dev/sdb
``` - you need root i.e. administrator rights to gain direct access to the drive. Then you'll be able to post the output.

I assume (correct me if I'm wrong) that you boot from /dev/sda and you can get into grub menu.

Since you plugged back the sda (disk from which you boot) you also need to update ARC path in your boot.ini, i.e. replace rdisk(0) parameter with rdisk(1) or use "remapped" entry. I didn't get it, what does it say about not being executable? Remember also to change root to rootnoverify in your Windows entries in GRUB.

C:\ = "Det går inte att identifiera ett operativsystem på enhet C." could mean that Windows tried to add an operating system to the boot menu located on the partition marked as active which was not the one on which you installed Windows. Now the Windows partition is active, previously the other active one was empty, hence the message. Nothing to worry, except your Windows will be on D: and that empty volume will be mapped as C:.

---

### Post by Pontus9 on 2008-09-16
Silly me, I should of course have tried to sudo when it did not work. Here is sudo fdisk -l /dev/sdb:

[I]Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007e2a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    b  W95 FAT32[/I]

"I assume (correct me if I'm wrong) that you boot from /dev/sda and you can get into grub menu." 

That is correct.

I now edited my boot.ini so it says *rdisk(1)* instead of *rdisk(0)*. I will attempt to boot now.

Okay, I am back from my reboot. Nothing seems to have changed by altering the rdisk value. If I try to boot Windows XP I still get *"disk error"* and if I try to boot Windows XP remapped I get *"Error 13: Invalid or unsupported executable format"*.

---

### Post by Jonie on 2008-09-16
Try changing to this:


title Windows XP remapped
rootnoverify       (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

Remember, those map lines snd changing "rdisk" value are mutually exclusive. So if you changed this, and windows boots with "remapped" but says something about not finding hal.dll change it back.

Can you boot XP when you choose the second disk as boot device through BIOS boot menu (usually accessible by pressing F9, F11 or F12 during POST)?

If not, and the error repeats and you're stuck at "disk error" I'm affraid you are hit by "partial last cylinder problem". You made your FAT32 parttion to end on last cylinder, what makes booting from FAT32 impossible. Try shrinking /dev/sdb1 by a few megabytes with GNOME Parted and make sure "round to cylinders" option is checked.

---

### Post by Jonie on 2008-09-16
I added exactly the same entry Windows XP remapped 

title Windows XP remapped
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

to my menu.lst, plugged an additional harddisk with XP through USB and it starts to boot! 

It must work, otherwise you have /dev/sdb incorrectly partitioned or its boot sector is invalid.

P.S. Oops. In the post from yesterday I've written rootnoverify (hd0,0) instead of rootnoverify (hd1,0), of course it was wrong. Report back if you can boot.

---

### Post by Pontus9 on 2008-09-17
Okey, here I go again. In a desperate attemp for progress I decided to start over. I deleted all partitions on sdb and then made a fat32 from 5000 MB to the end (leaving 5000 mb unpartitioned in the front). I then unplugged sda which allowed me to reinstall windows on the unpartitioned space on sdb.

After instal it looks like this:
[I]Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007e2a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2         637     5108670    5  Extended
/dev/sdb2   *         638       30401   239079330    b  W95 FAT32
/dev/sdb5               2         637     5108638+   7  HPFS/NTFS
[/I]

Windows have partitioned sdb1 and inside of it sdb5. I have myself partitoned sdb2. Why windows decided to leave 1 unpartitioned cylinder in front I do not know and I hope it doesn't have any affect (besides me losing 8 mb of disk space).

When I look at my sdb in GParted I can still see that sdb2 is the partition with the boot flag. How is that changed and does it matter?

I will try to edit my GRUB menu.lst a bit now from what you have learned me and see what happens. I hope I do not do anything bad.

Who should I put in my menu.lst?

After adding:
[I]title Windows XP remapped
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1[/I]
to the menu.lst I get "Invalid device request" when trying to boot with Windows XP remapped.

I have also noticed that my boot.ini is located in sdb2 (the fat32 partition) since that is flagged as boot. I guess I have to fix that somehow...

---

### Post by Jonie on 2008-09-17
> I get "Invalid device request" when trying to boot with Windows XP remapped.
 
Your Windows installation is on /dev/sdb2 (hd1,1) from now on, so the device has changed indeed. "1" in GRUB stands for 2nd, GRUB counts from 0. Map command fools guest OS to think it starts from the first device configured in BIOS as long as it uses Int 13h.

Let's not complicate things. Windows partitioner doesn't play well with other tools. I see that you're desperate to bypass Windows imposed limit of 32 GB for FAT32. Although that's not recommended, it's ok.

> Why windows decided to leave 1 unpartitioned cylinder in front I do not know and I hope it doesn't have any affect (besides me losing 8 mb of disk space).

It's known to screw things like that.

Repartition /dev/sdb again with GParted. Delete everything on it, commit the changes, create and format one big fat32 parttion (don't have to mark it bootable, XP will mark it itself) leaving the last cylinder in the end free (make sure "align or round to cylinders" is checked) - it's usually about 7.84 MB. Windows XP's got to have some untouched space in the end.

You can also use command line parted, it's even easier but be careful. Make sure that /dev/sdb is really what's meant to be.

```
sudo parted /dev/sdb
```

```
mklabel msdos
```

This will overwrite the MBR, removing all partitions.

```
mkpartfs primary fat32 63s -1cyl
```

This will create a partition as you were told by Bill G.

```
toggle 1 boot
```

This will make it bootable

```
quit
```


Install Windows on the disk running solo.

Add this entry exactly as given:

```
title Windows XP remapped
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

There's no way it wouldn't boot if you follow the instrucions precisely.

I'm just a little bit affraid one of moderators would move us to "Windows XP" forum. Ah, there is no such one ;)))

P.S, Other OS Talk - Windows? From Ubuntu point of view the thread is over, so if anyone decides  - please move.

---

### Post by Pontus9 on 2008-09-17
<sigh>

No, I still get disk error when trying to boot with Windows XP remapped. 

The strange thing is that the first time I try to boot with windows XP remapped it says "disk error". If I try again I get "Invalid or unsupported executable file" (or something like that). And from then on I can't even boot Ubuntu any more, it says "invalid or unsupported..." there as well. Then I have to turn of the power to the computer and start it up again to even get Ubuntu running (it works fine if I do not try to boot windows XP remapped first).

---

### Post by Jonie on 2008-09-17
You tried your partitioning scheme (Windows on sdb2) now without reformatting?

title Windows XP remapped
rootnoverify (hd1,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

In (hd1,1) first number translates to 2nd disk, second to 2nd partition. 

But now your disk layout is nothing but a big mess, so I suggested reformatting.

The symptoms make me think of broken BIOS in some way.

Can you change the boot order in BIOS and boot directly from sdb?

P.S. If you follow all the instructions from post #25 and still cannot boot, there's nothing more that can be done software-wise.

---

### Post by Pontus9 on 2008-09-17
I reformatted with GParted before I reinstalled windows. I think my disk layout is rather simple (but again I am new to this):

[I]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b4bd3b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007e2a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+   b  W95 FAT32[/I]

I will try to boot changing the boot order for harddrives in the BIOS (is that what you mean?), but I do not think it will work. I couldn't even get my secondary hard drive to start alone when the primary was unplugged.

My boot.ini (on sdb) currently looks like this:
[I][boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\ = "Det g†r inte att identifiera ett operativsystem p† enhet C."[/I]

And my menu.lst like this:

[I]
[...]

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a2f65323-abe8-4046-ab60-efbae85d182d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a2f65323-abe8-4046-ab60-efbae85d182d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

## Egna ändringar
title Windows XP remapped
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1[/I]

---

### Post by Jonie on 2008-09-17
Everything looks ok now. Just to make sure: you installed Windows with sda unplugged and your BIOS is configured for HDD auto-detection, i.e. disks in Standard CMOS Setup in BIOS are set up as Auto and not User?

---

### Post by Jonie on 2008-09-17
We can check what does your GRUB and this way BIOS see when the computer starts.

At the GRUB screen hit c for commandline.

type root (hd

after typing it directly press tab

it should answer you with something like that:

Possible disks are: hd0, hd1

if you type root(hd0, and hit tab directly after comma, GRUB will list partitions on hd0, subsequently do it for hd1

Report back what did it output.

---

### Post by Pontus9 on 2008-09-17
Okay, first of all. I went into my BIOS looking for HDD Auto-detection STANDARD CMOS Setup but didn't find anything like it. The closes one I could find was 'HDD Smart monitoring' which was enabled.

Then I went into my GRUB and pressed c like you told me to. I got in there and just as you said it first told me "Possible disks are: hd0, hd1" and I typed exactly what you told me. It took a few tries (to me it seemed like tab did different things every time I pressed it) but eventually I got it to tell me (for hd0):
[I]Partition num: 0, Filesystem type is ext2fs, partition type 0x83
Partition num: 4, Filesystem type unknown, partition type 0x82[/I]

I tried to make it work for hd1 (which I guess is the interesting part) but it did not work. When I typed "root (hd1," and pressed tab it just filled in "0)" making it "root (hd1,0)" and neither tab nor enter made any sense to it.

The GRUB using a english keyboard layout made it a bit tricky for me (using Swedish keyboard), but tab should still be tab, right?

---

### Post by Jonie on 2008-09-17
> I tried to make it work for hd1 (which I guess is the interesting part) but it did not work. When I typed "root (hd1," and pressed tab it just filled in "0)" making it "root (hd1,0)" and neither tab nor enter made any sense to it.

That's the way it should be. There is only one partition, so it fills a "0".

So. Everything is alright with GRUB and BIOS, you've got proper partition layout and you... still can't boot. I think something fails during the process of installing XP on the single second disk. Did you rejumper it accordingly to be single master disk for the time of installation if it is an ATA (not SATA) disk. I think here lies the rub (some may say the dog ;)

---

### Post by Pontus9 on 2008-09-17
It filled a 0, yes. But then I could not make it reply to the command, so I had nothing to report back for hd1. What I wrote was only for hd0.

I think my disks are SATA. When I installed windows with Primary Master unplugged it still considered my other (and at that time only one) hard drive as Secondary Master.

---

### Post by Jonie on 2008-09-17
> It filled a 0, yes. But then I could not make it reply to the command, so I had nothing to report back for hd1. What I wrote was only for hd0.

That's the expected reply.

The only thing that makes me worry is that Windows did look for something on C:\ while it shouldn't do so if you have only one partition.

Does it reboot to XP to finish the installation with the single disk?

---

### Post by Pontus9 on 2008-09-17
"Does it reboot to XP to finish the installation with the single disk?"

I am not sure since I didn't pay much attention at that part but it is possible it didn't. I think it fails when trying to reboot with XP after the installation giving me a "disk error".

---

### Post by Jonie on 2008-09-17
You can check what does this C:\ "unit" mean. Start recovery console from XP CD (having sdb connected as the single disk) and while at its prompt type map. This should give a hint how Windows does assign the letters. I'll drop back tommorow.

One more thing before I can sleep well ;)

There are motherboards that can't boot from secondary SATA  at all - yours might be one of them. Swap the data cable to install Windows on the second disk. Check if it finishes.

---

### Post by Jonie on 2008-09-18
Last thing that comes to my mind is that XP installer failed somehow to install bootstrap code to FAT32 boot sector (which is normally installed by formatting and since you used Parted and/or GParted it wasn't there) and the last line of boot.ini shows that XP was bewildered by Parted bootstrap code.

Boot Windows from the CD into Recovery Console (by pressing R when prompted). If your XP (check with map) is shown as located on C: you may try to fix the error by typing fixboot c:. It will tell you that you have non-standard bootsector and ask whether you're really sure, type y. Don't use fixmbr command since this could overwrite GRUB.

Report back if this helped.

---

### Post by Malac on 2008-09-18
If you are installing XP don't use gparted to format the partitions. Use the XP format/partition tool during install of XP.
Every Linux distro I have used to format either FAT32 or NTFS for installing Windows on has failed due to not setting the ID bytes how Windows expects/wants them, this includes Ubuntu.

Hope this helps.

---

### Post by Jonie on 2008-09-18
I SOLVED the problem!!!

Having a moment to test it, I grabbed an additional hard disk lying around and recreated your scenario. Indeed, XP gave "disk error" on reboot. And appended an entry to boot.ini C:\="Unidentified operating system on drive C.".

I tried recovery console, still disk error.

What gives?

I found that GParted or Parted (pretty the same but command line) installs legacy dos FAT boot sector (first sector of the partition) that confuses XP installer. It succeeds to install appropriate IPL (bootstrap code) but the part that's contains information about disk geometry becomes invalid.

What to do?

Install testdisk.

```
sudo apt-get install testdisk
```

```
sudo testdisk
```

You will need to make your terminal window one line taller

Select No Log

Select your hard disk and press enter

Select Intel

Select Advanced - filesystem utils

Select Boot

Select Rebuild BS

Wait a minute as it scans FAT table. Answer yes to all questions.

Select Write


Now XP will boot. I think it's not too soon to say "Skal" with my carafe of Ubuntu :)

---

### Post by Pontus9 on 2008-09-18
Skål indeed! It worked!

I can enter windows and to me it seems to be running perfectly (I have not had much time to test it yet though). I only have one problem left.

When I choose Windoes XP remapped in the GRUB another screen appears. There I must again choose an OS and the two options I am given is:

Windows XP Profesional
Can not identify an OS on c:

The first options starts perfectly while the second one obviously doesn't. Does this screen appear because of the remapped code in my menu.lst or is it a problem with the windows booter? Would be nice to skip this screen.

Thank you so much! The best thing with installing Ubuntu is all the great support you get :popcorn:.

---

### Post by Malac on 2008-09-18
> **Pontus9 said:**
> Skål indeed! It worked!

I can enter windows and to me it seems to be running perfectly (I have not had much time to test it yet though). I only have one problem left.

When I choose Windoes XP remapped in the GRUB another screen appears. There I must again choose an OS and the two options I am given is:

Windows XP Profesional
Can not identify an OS on c:

The first options starts perfectly while the second one obviously doesn't. Does this screen appear because of the remapped code in my menu.lst or is it a problem with the windows booter? Would be nice to skip this screen.

Thank you so much! The best thing with installing Ubuntu is all the great support you get :popcorn:.

From inside Windows
Edit C:\boot.ini in notepad (you made need to unset Read Only to save changes)
Change "timeout=" value to 0
Make a note of the folder and/or boot file that the second entry is pointing to and delete it if it is not needed.
And delete the "Can not identify an OS on c:" entry.

Hope this helps.

---

### Post by TeXtonyx on 2008-09-18
Disconnect the power cable to sda. Set the jumpers on sdb to master. You are better off with NTFS because the driver to read that kind of partition works well from Ubuntu. XP wants to be on the 1st drive, though you can likely switch them after the install. I also use LinuxReader and a small fat32; also boot.ini since I installed grub to the first sector of the Ubuntu boot partition; also used BootPart.

---

### Post by Jonie on 2008-09-18
That's great :)

:guitar:

Yay, delete the last line from boot.ini as Malac wrote. A drawback of having FAT32 is that you can't have a file bigger than 4 GB on it (32 bit file size). On the other hand NTFS support in Linux is great in fact, but just as long as NTFS is healthy. And Windows won't tell you much about its filesystem state. Unless you run chkdsk from time to time manually. Your choice.

Cheers:D

---

### Post by TeXtonyx on 2008-09-18
I've been dual booting since Redhat 6.0 and I just set this up again with Ubuntu.
The best way is to have Windows as your first primary master drive and Linux on your second drive as slave (with correct jumper settings on the back of the drive) My boot.ini
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu.bin="Ubuntu"
c:\bootsect.lnx="Linux"
------------------------------------
"Ubuntu" was installed on sda, the first sector of the boot partition.
"Linux" was installed on sdb, the first sector of the boot partition.
I'm a computer purist which means I usually like Linux, but is it subjective to say this boot.ini record of how one boots is cleaner and more understandable than Grub? Also sdb is a logical partition which can matter. This is for future reference because you have already have grub installed. So, Windows should be on the first drive and I think grub should be reinstalled to the MBR of the first drive configured so that you can boot XP or, Ubuntu on your second/slave drive.  That seems like less work from where you are now.  I have small fat32 partitions on both drives; XP should be installed NTFS. To answer my own question, there is a factual best way to do this, dual boot.

---

### Post by Pontus9 on 2008-09-18
Yeah, I guess I have to trust everyone who says that having windows on the first hard drive is better to be right so maybe that I what I SHOULD have done.

But I think I am kind of okay with this setup. I mostly plan to have windows for running my scanner (CanoScan LiDE 70, which is not supported in Ubuntu) so 4 GB limit on files seems acceptable.

Then again maybe I did plan to run some games from windows and then 4 GB limit could be a problem for handling DVD images, but I am not to worried as of now.

Big thanks to everyone who helped me and especially Jonie for all the hard work!

---

