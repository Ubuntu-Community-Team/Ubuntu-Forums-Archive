---
title: "[SOLVED] Can't mount live CD"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by GrahamM on 2008-12-08
I need to access the Live CD so that I can re-install Network Manager. I have Ubuntu 8.10 installed on a dedicated HD and Live CD is on a dual CDROM/DVD drive.

When I attempt to mount the Live CD, I get a Can't mount error box. It says something about not reading Superblock.

If I insert another CD, it will mount and be accessible. 

The Live CD when used standalone boots fine and works as it should.

I burned the live CD using Nero v8. Could it have something to do with the file format?

Any help appreciated! I am new at this!

---

### Post by psusi on 2008-12-08
I'm not sure why it won't mount, but mounting it won't get you anything.  If you want to reinstall something just do so in synaptic.

---

### Post by GrahamM on 2008-12-08
> **psusi said:**
> I'm not sure why it won't mount, but mounting it won't get you anything.  If you want to reinstall something just do so in synaptic.

Without internet access, how will reinstalling work with Synaptic? It just gives me a string of error messages because it can't connect.

It is Network Manager (or WiCD) that I am trying to re-install so that I can gain wifi access. Where would I find NM other than from the CD?

I did download both Network Manager and WiCd using Windows and placed them on the desktop. But, I don't know how to tell Synaptic that that the desktop is the depository. I did try, but did not get it to work.

For this question, I am trying t find out why the Live CD will not mount, when others CDs do.

---

### Post by psusi on 2008-12-08
> **GrahamM said:**
> Without internet access, how will reinstalling work with Synaptic? It just gives me a string of error messages because it can't connect.

It won't, but you can't do that with the livecd either.

> **GrahamM said:**
> 
I did download both Network Manager and WiCd using Windows and placed them on the desktop. But, I don't know how to tell Synaptic that that the desktop is the depository. I did try, but did not get it to work.

For this question, I am trying t find out why the Live CD will not mount, when others CDs do.

If you downloaded the .debs then just browsing to them in the file manager and opening them should work, or from the command line run sudo dpkg -i foo.deb ( in the directory where it is located ).

---

### Post by murrayd77 on 2008-12-09
Try using below command if its NTFS. 

sudo umount /media/cdrive
sudo mount -t ntfs /dev/hda1 /media/cdrive

Or try here.. It may help you.. [http://ubuntuforums.org/showthread.php?t=911226](http://ubuntuforums.org/showthread.php?t=911226)

---

### Post by GrahamM on 2008-12-09
> **murrayd77 said:**
> Try using below command if its NTFS. 

sudo umount /media/cdrive
sudo mount -t ntfs /dev/hda1 /media/cdrive

Or try here.. It may help you.. [http://ubuntuforums.org/showthread.php?t=911226](http://ubuntuforums.org/showthread.php?t=911226)

Windows say format is CDFS. I guess I would need to first find what Ubuntu names the CD. hda1 would presumably be a hard drive?

I did check the link - mainly to do with mounting a HD though. But maybe principle will work.

No longer really need to resolve this because I did a complete re-install so as to get Network Manager back working. 

Problem still persists with mounting the Live CD disk, so still would like to find out how to access it for future reference.

---

### Post by jenkinbr on 2008-12-09
Simply inserting the disc doesn't do anything? On my system, simply inserting the LiveCD will bring up a message box that asks me if I want to start the package manager or not - If I don't click on 'Open Package Manager', I am unable to use the disc until I eject and re-insert it.  btw, I have ONLY ever gotten liveCD's and Apt-on-cd discs to work with synaptic using the procedure I just described - trying to use apt or aptitude doesn't work (for me).

Have you tried re-burning the CD, maybe at a slower speed?

Because of the nature of the LiveCD, it's size,and everything, one little slip in the laser's path could break the disc.

---

### Post by GrahamM on 2008-12-09
Thanks for reply. I don't think there is anything wrong with disk - I have used it twice for installation, booted from it many times and can access it without problem and look at files using Windows 2000.

If I insert it during a Ubuntu session, it does nothing except name does show up at Ubuntu 8.10 i386. If I try and open it, I get the Cannot Mount error message - It says something about a problem reading the superblock.

This leads me to believe that Ubuntu has a problem with the format Nero used. Windows says it is CDFS - I think this is same as 1so9660? Shouldn't that work with Ubuntu?

---

### Post by jenkinbr on 2008-12-09
It should...

I would try Burning the ISO file at a slower speed, using a different burner.  [InfraRecord ]("http://infrarecorder.org/")works good and is reccomended by most Ubuntuers for burning CD's in windows. (I even got it to run in wine, but never tried burning a disk...)

---

### Post by GrahamM on 2008-12-09
I tried burning a new CD from within Ubuntu - I actually burned the Kubuntu iso just so effort would not be totally wasted :)  I used the lowest speed available using the Ubuntu built in CD writer - I forget it's name.

Once I had the new CD burned, I attempted to access it from ubuntu - once again, I got the same cannot mount message as I get when trying to read from the ubuntu Live CD. Something about not being able to read the superblock.

I ran Kubuntu from the Cd and it worked fine. I do have to hit F6 and add the allgeneric_all_ide floppy=off irqpoll to get the live cd to work for both ubuntu and kubuntu. Is there a way to add this to the installed system boot and would it likely help?

Once in kubuntu, I was able to read the Live CD without problem. I have not tried reading from the ubuntu live CD, but suspect that too would work.

It would seem that there is something about my hard drive installation of ubuntu that prevents the kubuntu and ubuntu live CDs from mounting while other CDs load OK. 

This is a dual DVD/CD RW drive. 

Does anyone have any idea why  the Live CDs won't mount and how to fix it:confused:

---

### Post by psusi on 2008-12-10
Post the output of the following commands:

cat /etc/fstab
mount

---

### Post by GrahamM on 2008-12-10
> **psusi said:**
> Post the output of the following commands:

cat /etc/fstab
mount

Have no clue what this is doing, but this is what I get:

graham@graham-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=ef646dc3-ecca-4afa-9236-8646cbf6a986 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc5
UUID=b8597476-a07a-4a6b-b6f1-bf863ddb382b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
graham@graham-desktop:~$ mount
/dev/sdc1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/graham/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=graham)

---

### Post by psusi on 2008-12-10
Ok, now:

sudo mount /media/cdrom0
dmesg | tail --lines=15

---

### Post by GrahamM on 2008-12-10
> **psusi said:**
> Ok, now:

sudo mount /media/cdrom0
dmesg | tail --lines=15

Sorry for delay - Have to sleep sometimes :)

here are results:

graham@graham-desktop:~$ sudo mount /media/cdrom0
[sudo] password for graham: 
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

graham@graham-desktop:~$ dmesg |tail --lines=15
[  237.836004] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  237.836050] sr 0:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[  237.836061] sr 0:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  237.836075] end_request: I/O error, dev sr0, sector 72
[  237.836115] isofs_fill_super: bread failed, dev=sr0, iso_blknum=18, block=18
[  258.190889] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  258.190913] sr 0:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[  258.190923] sr 0:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  258.190937] end_request: I/O error, dev sr0, sector 72
[  258.190979] UDF-fs: No VRS found
[  258.232143] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  258.232164] sr 0:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[  258.232174] sr 0:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  258.232188] end_request: I/O error, dev sr0, sector 72
[  258.232221] isofs_fill_super: bread failed, dev=sr0, iso_blknum=18, block=18


I tied another CD - An old ASUS driver disk that came with computer - It would not mount.

I inserted a different CD - Actually a windows program - Photopaint that had been burned on another CD drive - This was mounted. I unmounted then issued the same terminal commands and received this:

graham@graham-desktop:~$ sudo mount /media/cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only
graham@graham-desktop:~$ dmesg | tail --lines=15
[ 1755.062329] sr 0:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1755.062339] sr 0:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1755.062352] end_request: I/O error, dev sr0, sector 398692
[ 1755.065145] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1755.065156] sr 0:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1755.065165] sr 0:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1755.065176] end_request: I/O error, dev sr0, sector 398696
[ 1755.091559] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1755.091579] sr 0:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1755.091590] sr 0:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1755.091604] end_request: I/O error, dev sr0, sector 398692
[ 1755.094367] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1755.094377] sr 0:0:1:0: [sr0] Sense Key : Hardware Error [current] 
[ 1755.094385] sr 0:0:1:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 1755.094396] end_request: I/O error, dev sr0, sector 398696

This CD mounted again after I unmounted it, but I get an error message when I try to unmount saying I do not have priveledges! Cannot even eject it. Seems like I would have to shut down to remove the disk! This is error message:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Obviously something amiss! More inf0 - I have ATA100 and IDE interfaces. Ubuntu boots off the primary IDE and CDROM is IDE slave. W2K is on Primary ATA100 and WinMe and data on ATA slave. Other that the CDROM problems, the boot loader seems to work well.

---

### Post by psusi on 2008-12-10
It looks like you have a communication problem with the cdrom, maybe caused by the driver negotiating a transfer mode the drive can't handle, or you may be using a bad cable to connect it.

---

### Post by GrahamM on 2008-12-10
> **psusi said:**
> It looks like you have a communication problem with the cdrom, maybe caused by the driver negotiating a transfer mode the drive can't handle, or you may be using a bad cable to connect it.

I don't think it can be the cable, because the drive works fine under Windows. Could be a jumper setting perhaps. But, it even works when I boot from the Live CD. 

Live CD will not even boot unless I put in  **all_generic_ide floppy=off irqpoll** - But these items are not there when I look at menu.lst in Grub. I tried to add them, but it says that I do not have permissions! 

How do I get permissions to edit the grub menu? 

Is there a grub editor or do I have to just edit the text?

Would adding those items likely help?

---

### Post by jenkinbr on 2008-12-10
you need to be root to edit menu.lst.

try ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
``` 

then add the bit you are trying.

Edited my code block to include a command to back up the file - wouldn't want to be totally stuck because you screwed up your menu.lst file

---

### Post by GrahamM on 2008-12-10
> **jenkinbr said:**
> you need to be root to edit menu.lst.

try ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
``` 

then add the bit you are trying.

Edited my code block to include a command to back up the file - wouldn't want to be totally stuck because you screwed up your menu.lst file

Too late with the edit ;)

Now that worked and I was able to save file - Why does it not work when I navigate to the file and then open it?

Anyway, I made the changes, rebooted and lo and behold, everything now works as it should!!!!:p

Can anyone explain just what those items do?

all_generic_ide --   I can guess that this installs generic ide drivers?
floppy=off -- Is that necessary and does it disable the floppy drive?
irqpoll - what does that do?

And, is there a grub editor in this distribution or can I download one?

PS: How do I become root?

---

### Post by jenkinbr on 2008-12-10
You cannot login as root in ubuntu (well you can, but that is not the Ubuntu way to do things, and violates the CoC).  However, the 'sudo' and 'gksudo' parts of the commands I had you run allow you to become root temporarily.

For the grub editor, you could try kgrubeditor. It's a KDE app, but it is the only one I can find.
```
sudo apt-get install kgrubeditor
```

about the parameters, I don't know.  I'm assuming that floppy=off does what it says and disables the floppy drive (who uses them anymore?).  As to which of those are nessesary, I don't know - I'm assumeing that all_generic_ide is all you really need, but only a bit of testing on your end will determine whether it works or not.

---

### Post by GrahamM on 2008-12-10
> **psusi said:**
> It looks like you have a communication problem with the cdrom, maybe caused by the driver negotiating a transfer mode the drive can't handle, or you may be using a bad cable to connect it.

Problem solved by editing menu.lst - see above. Thanks for help.

---

### Post by jenkinbr on 2008-12-10
Glad it works for you.

---

