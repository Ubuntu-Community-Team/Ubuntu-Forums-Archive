---
title: "How-To Install Express Gate / Splashtop on Asus Motherboards from Ubuntu / Linux"
date: 2009-01-24
forum: Hardware
---

### Post by SqRt7744 on 2009-01-24
Well I finally got Express Gate to install with Ubuntu! It was actually pretty easy, strange that nobody has posted a how-to yet. I'm using Ubuntu 8.10 x86-64 (though the method should work just as well for 32 Bit)

1. Install wine. I used version 1.1.13, which I got from winehq.org, installation instructions are on the wineHQ site.


2. run the installer from the CD. Accept defaults and click OK, etc. etc until it indicates that it has completed the install successfully.

3. It is now necessary to create an NTFS (or FAT32) partition for the Splashtop install. This must be done from a live CD or USB stick. I set up a usb stick with the 'Desktop' version of Ubuntu 8.10 using Unetbootin for the purpose. Boot into the live environment. 

4. start gparted from the live CD (System->Administration->Partition Editor). Create a new partition on your hard drive, type NTFS. I made mine 1.5GB, labeled it "WINDOWS", and gave it the boot flag to be on the safe side. I created mine at the beginning of the drive. This was probably a mistake since the drive is 500GB and the current partition had to be shrunk and moved, it took 20hrs or so. I suggest making it at the end of the drive where the computer has less work to do. When gparted is finished, reboot the computer (remove the live CD) and enter your normal install.

5. Open a terminal window (Applications->Accessories->Terminal) and mount the partition. The command will look something like this:
sudo mount.ntfs-3g /dev/sda3 /mnt
where sda3 is the name of the newly created ntfs partition on my computer. It may well have a different name on yours. It will now be mounted in the directory /mnt.

6. copy the 'fake' wine drive c to the newly created WINDOWS partition.
cp -pr ~/.wine/drive_c/* /mnt

7. if you now look in /mnt, you should now find a file called splash.idx. You have to edit this file.
Mine looks like this:

root=UUID=43FE94EC1C4A1BAA
/ASUS.SYS
/ASUS.000

the first line, containing the UUID has to be changed to the UUID of your new ntfs partition. You can find this by typing
ls -l /dev/disk/by-uuid/
if you have a number of partitions and aren't sure which is the correct one, note that an NTFS UUID should look similar to mine. The ext3 and swap partitions look something like this: d7a92374-231a-4b45-86db-abc930c5a89c (note the presence of dashes and overall length)
typing 'file 43FE94EC1C4A1BAA' tells me that the UUID points to /dev/sda3 which is what I am looking for.
Now enter the UUID of the appropriate partition into the splash.idx file.

Save everything, close, reboot. If it doesn't work, make sure that the Sata mode in BIOS is set to IDE emulation, otherwise splashtop won't work at all (see the mainboard manual)

8. YAY!

---

### Post by devolnx on 2009-02-10
Tks for this great instruction list. I have just got a ASUS P5Q SE & want to use the Express Gate. (just sucks that a Linux based prgm doesn't run naturally on Ubuntu 8.10)

Went through steps 1 - 6 (step 4 used bootable gParted & put at end as advised) BUT in step 7 I did not get a splash.idx in the /mnt folder. There are two folders, Program files & windows but the file isn't there either. Wine was version 1.01 through the Package Manager.

Searched all file system but no splash.idx. How else can this be created?

So close but so far.

TIA

---

### Post by devolnx on 2009-02-11
I finally got Express Gate to work, very happy now, but it needed a few more steps for this machine.

1) Found out how to make a new splash.idx at here [http://www.phoronix.com/forums/showthread.php?p=52657](http://www.phoronix.com/forums/showthread.php?p=52657) and did step 7.

2) Did steps 5 & 6 again then rebooted. BUT the /mnt folder became empty again.

3) So I did 5 & 6 again and copied the Express Gate folder from the MB CD into the /mnt folder.

4) Using Wine I ran the install program accepting OK all the way. I then noticed new files like ASUS.000 & ASUS.SYS & checking the splash.idx, it was different. So putting the correct UUID in place & rebooting, the thing works very well.

Perhaps all that is needed is to do all to step 6, then install the Express Gate using wine, do step 7 & reboot.

Since by chance this one is working now, I am not going to try & undo it to prove a theory, but hope others will try.

Cheers to all & once it is going it does look good.

---

### Post by SqRt7744 on 2009-02-12
I'm glad that you didn't have to create the partition at the beginning of the drive. I suspected this wouldn't be necessary, but it's good to know it isn't!

note: mounting the NTFS partition is only necessary to copy the Splashtop install over to the new partition. After a reboot it won't be mounted anymore, which is fine.

---

### Post by koshari on 2009-05-10
any reason the partitioning needs to be done in a live session?

---

### Post by SqRt7744 on 2009-05-11
> **koshari said:**
> any reason the partitioning needs to be done in a live session?

you can't modify a mounted partition.

---

### Post by StuartRothrock on 2009-05-20
Thanks for the informative post. I removed the windows and Program Files directories and it worked well. I think it was 307MB. It gzipped down to 158MB for safe keeping. Thanks again - You saved me hours!!
 
Stuart

---

### Post by Mahyar on 2009-05-31
Thanks everyone for your help so far.

I couldn't get Express Gate working with the methods above, so I tried a few different things and came up with this.  Note that this is on an Eee Box B202 with Ubuntu Jaunty installed.

1. Create a 1GB NTFS partition at the end of your HDD and give it a "boot" flag (the installation takes 865MB).  I called mine ExpressGate and it shows up in Nautilus, but I've set it as unmountable if not root.
2. Download and extract this file: "ftp://ftp.asus.com/pub/ASUS/misc/utils/ExpressGateSSD_ExpressGateV1231.zip".
3. Open ExpressGate(HDD)/ST_ASUSEG00_HD_v1.2.3.1_20080605.EXE with WINE.
4. Copy all the relevant files from /home/username/.wine/drive_c/ to your new NTFS partition.  These are directories called ASUS.000, ASUS.SYS and windows, and other files called 1033.MST, Express Gate.msi, splash.idx and version.
5. Open your splash.idx file and do as SqRt7744 suggests in number 7 above.  The only change is that there's no need to muck around with /mnt.  Do it all on the NTFS partition.  In fact, my /mnt is empty.
6. Save and reboot and you should have Express Gate.

The only (quite large) problems are that I can't link my photos directory to the NTFS partition, it won't detect USB drives and it won't pick up my router.  It picks up some other networks, so it must have to do with the N standard (which my router doesn't use).  I suppose I'll just plug it in.

I hope this helps someone.

Edit: LAN works fine in Express Gate, as do external drives.

---

### Post by SqRt7744 on 2009-06-02
has anyone figured out how to change the resolution to a widescreen format? 1440x900 in my case...

---

### Post by BobGod8 on 2009-06-19
How did you get past needing a bootloader?  All I get is "Bootmgr is missing".  I tried installing my own (install-mbr, syslinux, etc.), but just ended up with a screenful of noise.

How did you select the kernel?  Do I have to try pointing it to /ASYS.SYS/kernel.bin somehow?

---

### Post by SqRt7744 on 2009-06-22
> **BobGod8 said:**
> How did you get past needing a bootloader?  All I get is "Bootmgr is missing".  I tried installing my own (install-mbr, syslinux, etc.), but just ended up with a screenful of noise.

How did you select the kernel?  Do I have to try pointing it to /ASYS.SYS/kernel.bin somehow?

I didn't get that error - did you remember to set the UUID? I'd double check the value to make sure you don't have a type...

---

### Post by VladoSk on 2009-08-07
Hi,
I am trying to run Express Gate on my PC. I have first partition NTFS with installed WinXP, but after short message Installing Express gate, computer continue with booting up regular OS.
This is on my IDE harddrive.
When I make the same on SATA harddrive, Express Gate works properly.
Every time I change first boot device to correct disk. I try remove SATA disk, but nothing helped.
Is it possible that Express Gate works only with SATA drives?
But I think it is possible to run Express Gate from USB key, so why not from IDE?
:confused:

---

### Post by SqRt7744 on 2009-08-16
> **BobGod8 said:**
> How did you get past needing a bootloader?  All I get is "Bootmgr is missing".  I tried installing my own (install-mbr, syslinux, etc.), but just ended up with a screenful of noise.

How did you select the kernel?  Do I have to try pointing it to /ASYS.SYS/kernel.bin somehow?

The BIOS controls starting Splashtop BEFORE it gets as far as loading GRUB. Are you sure you have Splashtop enbled in the BIOS?

---

### Post by neojames on 2009-11-29
I just wanted to check that it would work on karmic, thanks for the tutorial I'm hopping that it will work on my new setup with a asus p5q/epu board! Thanks again.

---

### Post by techfreak on 2009-11-30
Interesting thread wish I was a bit more sophisticated with this but I have a similiar problem trying to reinstall splashtop onto my LG X120 netbook. I follow the steps listed in the  thread and installed ExpressGateHD-V1469 onto a Fat32 partition. Did the UUID edit to the splash.idx file and gave it a go. My netbook has a specific "power button" for the previous splashtop that was installed and low and behold it worked **partially**.

It booted however with a corrupt video display, you could make  out most of the icons etc. but my guess that this was a driver issue. This has me a little closer to finding a resolve on how to restore this splashtop. The splashtop.com website has the source files for the original version that was installed on the netbook. 

Next time I will image the drive before I blow away the partitons :oops:

Of course no recovery disk is available.

Any suggestions would be great!

---

### Post by buzz91 on 2010-02-03
i have the very same problem as techfreak has.

i blowed away the partitions.

does anyone know how to install this integrated SpalshTop again?

does it work to install SplashTop as explained here - is the SplashTop-Button then booting SplashTop as expected?

greets

p.s.: i wrote to support but until now i got no answer

---

### Post by buzz91 on 2010-02-03
I found a ExpressGate-folder on the CD delivered with my eee.

But when i try to install this ExpressGate (ExpressGate/AsusSetup.exe)with wine it says that the EFI-Partition wasn't found.

Also ExpressGate/EN_EXGATE_32H_1.2.17.13_EFI.exe says that the EFI-Partitoin wasn't found.

So I think this installation-routine differes from the one mentioned here for installing SplashTop on the hd "normally".

Does someone know how to get this EFI-Installation working under wine? An idea how this SplashTop can be recovered when accidently blowing up the partitions.

greets

---

### Post by buzz91 on 2010-02-04
I got a reply by the ASUS support. They say it wouldn't be possible to recover ExpressGate without recovering the whole system with help of the support dvd. This would be very sad because i would have to install ubuntu again and configure all the things - very sadly.

But i don't want to give up. I think there should be a way to just recover ExpressGate. Therefore i again asked the support more precicesly what the ExpresssGate partitiopn have to look like etc.

Another thing i would give a try is to copy the ExpressGat directories (ASUS-sys) onto a NTFS-partition and see what happens. Maybe someone can offer a copy of the relevant directories?
But I think there must also be something like flashing the ExpressGate mainboard flash to find the correct partition, but i don't know how to do this.

Can anyone help?
Does anyone know how to specify what is bootet when hitting the ExpressGate-button?

greets

---

### Post by buzz91 on 2010-02-05
so i run a test now on my eee pc 1001p where i accidently deleted the express gate partition:

a) i set up a primary fat32-partition with boot flag.
b) downloaded the newest expressgate installer from asus.com
c) executed this installer using wine
d) copied the directories belonging to express gate from .wine/device_c/ to the previous created fat32-partition
e) changed the uuid in the splash.idx file to the uuid of the fat32-partition
f) tried to boot express gate with help of the express gate button on my eee pc 1001p

FAILED

now i want to try wether it is possible in genereal to boot this splashboot installation via my grub.

i think when this test is positive the only thing to change would be the where the express gate button points at.

maybe someone has an idea...

---

### Post by buzz91 on 2010-02-10
So my tests and the asus support says:
no chance to get express gate running without resetting the whole system, which means, loosing all your datas/partitions on the hard drive and install win xp then express gate ...

i won't do that. firstly i don't want to loose all my things and secondly i'm not sure wether it will work afterwards, when then installing ubuntu again on this machine.

very sad!

is there someone who knows if there's a way to use the express gate button as button for starting a certain entry in grub?
there was a way on my dell, there i use the button for booting a minimal moblin which is also on my harddrive, when i hit the normal boot button there is my ubuntu preselected.

---

### Post by -jay- on 2010-04-11
ill give this a try see what happens i got a recovery dvd so no biggy if it fails ill just load up the recovery dvd

---

### Post by essexboyracer on 2010-04-25
buzz91: I too would like this feature on my Asus G71v Gaming Laptop.

The AMI Bios has no entries for modifying the button behaviour. From reading this post, does the button 'press' initiate a look for a splash.idx file, if it finds one it starts the loader?

Further info: [http://www.phoronix.com/image-viewer.php?id=870&image=devicevm_splashtop_4_lrg](http://www.phoronix.com/image-viewer.php?id=870&image=devicevm_splashtop_4_lrg)
referenced from: [http://www.phoronix.com/scan.php?page=article&item=870&num=1](http://www.phoronix.com/scan.php?page=article&item=870&num=1)

---

### Post by charlesopondo on 2010-06-23
Reading through this whole thread so far, this is what I was able to glean, which I did and worked at the first attempt:

1. Create an NTFS or FAT32 partition of at least 1.5GB and give it a boot flag. The easiest way to do this is by booting into Ubuntu Live CD then using a partition manager such as GParted which you may need to install first. Be very careful not to make a mess of your existing partitions.

2. Reboot into your Ubuntu installation and obtain the ExpressGate installer from Asus website which will usually have the latest update.

3. Run the installer with Wine. It will create a file named 'splash.idx' and two folders named 'ASUS.000' and 'ASUS.SYS' in the pseudo C:\ drive of your Wine installation.

4. Mount the NTFS or FAT32 partition that you created earlier if you need to (usually you don't - it should appear in your file manager by default). Copy (or, preferably, move) the file 'splash.idx' and the two folders 'ASUS.000' and 'ASUS.SYS' from the Wine C:\ drive to your newly created partition.

5. Finally, edit the 'root=UUID=...' line in 'splash.idx' to point to the UUID of the partition you created. You can list the UUIDs of your partitions using the command 'ls -l /dev/disk/by-uuid/'

6. If you are a control freak like me, remove all trace of ExpressGate from Wine (uninstall or delete the menu shortcuts) as you don't need any of that now.

7. Shutdown your computer and press the ExpressGate button to launch ExpressGate.

Mine worked perfectly with these steps; it connected to the wired and wireless networks, allowed me to use a USB device and configure various settings.

---

### Post by charlesopondo on 2010-06-24
See my reply #23; I succeeded in getting this done after blowing away the original partitions.

---

### Post by chimaera on 2010-07-16
Hi, probably not exactly on topic, but is anyone aware if it is possible to replace ExpressGate with another OS? I don't use it for its borked resolution and, well, general ugliness, but it would be nice to put the EG-button (Eeepc 1001p) to good use, i.e. start a full grown linux distribution with it. 

Any ideas on that?

Thanks.

---

### Post by UptownRedLine on 2010-07-23
Worked perfect on Asus M4A78T-E. Thanks!

---

### Post by fat yak on 2010-10-26
Thank you, I wouldn't have done this without help.

I couldn't work out where the splash.idx came from in the original instruction so I have included my step here in case it helps anyone else.
Started off with Asus N10 with Ubuntu Netbook remix 10.04 on a 160GB HDD.
Lost the XP and express gate partitions when I loaded Ubuntu from the live USB.
Had the Asus recovery DVD and instructions from forum.

Started out by using live USB from old ubuntu remix to use Gparted on drive and create 1.5GB NTFS partition. This was flagged as bootable.
When I looked it up , I found that only one partition can have a boot flag, and giving the NTFS partion the flag didn't affect the ubuntu boot. 
I then mounted the NTFS drive; went to Ubuntu software centre and installed wine.

Then in a desktop computer with a DVD drive I took the Asus N10 disk and extracted express gate files from the software folder.
These were zipped so I right clicked and extracted them to my 4GB USB disk.
Then I moved these files from the USB to my c drive on wine. I then right clicked on the .exe file and opened with wine windows program loader.
This started the express gate installer - which ran until I got to a screen which said select drive - but wouldn't let me select any drives.
This stumped me for a while until I saw the next button was selectable, so I ignored the drive question and clicked next and the installer
completed. This created the splash.idx, ASUS.SYS and ASUS.OOO files.

I transferred those files to my NTFS drive and amended splash.idx as described. I cut and pasted from ls -l  /dev/disk/by-uuid/ to make sure I 
didn't get the number wrong.Then I  shut down and restarted by pressing the express gate key on the N10 and it all worked :) just as it did before I stuffed it up.

---

### Post by Roman0 on 2010-11-18
Nice descriptions, I particularly liked and followed charlesopondo's description and am stuck at 3rd point. The installer won't run, it only shows me a message "No EF Partition! Installation is aborted!" and that's all.
Tried on both, stable and unstable Wine (1.2.1 and 1.3.7).
The only difference is that I didn't download the ExpressGate from asus.com, but got it on a DVD with my netbook (it seems to be a newer version anyway, 2.2.52 on DVD vs 2.2.44.163 on asus.com). Even if I'd try to download the file, the transfers on that site are horrendously low, like <10KiB/s, that would take me more than a day to download.

So, anyone cares to tell me what I'm doing wrong, and what should I do to bypass this problem?

---

### Post by 0x656b694d on 2010-11-19
Same issue here as Roman0's.
Tried NTFS and FAT32, with and without boot flag, mounted and unmounted, with and without 0xEF flag.

---

### Post by fat yak on 2010-12-09
For Roman0 and 0x656b694d;
Charlespondos instructions do not include step 6 in Sqrt7744's original post.
Don't know if it would make any difference, and don't think I did it but I know I got confused with the NTFS partition and the pseudo C drive and created an extra volume that I ended up deleting.

---

### Post by 0x656b694d on 2010-12-28
Thanks, yak. Unfortunately, copying the wine drive doesn't help.

What i have now:
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x184b8eb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           30272       30275       20480   ef  EFI (FAT-12/16/32)
/dev/sda2   *       30275       30402     1018880   ef  EFI (FAT-12/16/32)
/dev/sda3               1        2432    19530752   83  Linux
/dev/sda4            2432       30272   223627264    5  Extended
/dev/sda5            2432       29762   219530240   83  Linux
/dev/sda6           29763       30272     4095743+  82  Linux swap / Solaris

```

---

### Post by realizee on 2011-01-26
Couldn't you create an EFI partition using [this]("http://https://help.ubuntu.com/community/EeePC/Using") guide?

---

### Post by charlesopondo on 2011-04-21
For those experiencing the EFI partition error I think it is possible (in theory at least) to run the installation in a real or virtual Windows machine, then copy the required files/folders from there and proceed with the next steps as I have outlined above.

---

### Post by charlesopondo on 2011-04-21
> **Roman0 said:**
> Nice descriptions, I particularly liked and followed charlesopondo's description and am stuck at 3rd point. The installer won't run, it only shows me a message "No EF Partition! Installation is aborted!" and that's all.
Tried on both, stable and unstable Wine (1.2.1 and 1.3.7).
The only difference is that I didn't download the ExpressGate from asus.com, but got it on a DVD with my netbook (it seems to be a newer version anyway, 2.2.52 on DVD vs 2.2.44.163 on asus.com). Even if I'd try to download the file, the transfers on that site are horrendously low, like <10KiB/s, that would take me more than a day to download.

So, anyone cares to tell me what I'm doing wrong, and what should I do to bypass this problem?

For those experiencing the EFI partition error I think it is possible (in theory at least) to run the installation in a real or virtual Windows machine, then copy the required files/folders from there and proceed with the next steps as I have outlined above.

---

### Post by Xitium on 2011-04-21
If you try and run this on a windows machine that does not have an EFI partition created already it will give the same error. I have not attempted to create an EFI partition yet on a real windows box so I don't know if this will work or not. The only one that I have access to is on my work computer so I don't know if I will try this.

---

### Post by hearea on 2011-08-22
Help me out guys, i just cant get pass the 1st step, which is to install it with wine.  it keeps saying DiskTool.exe and wine have some problems.  How can i fix it?

---

