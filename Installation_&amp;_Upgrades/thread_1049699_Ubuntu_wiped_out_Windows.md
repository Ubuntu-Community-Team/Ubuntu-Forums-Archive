---
title: "Ubuntu wiped out Windows ?"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by ilushkin on 2009-01-24
Hello,

I installed Ubuntu 8.10 tonight on the Windows XP machine with 250Gb hard drive.

i choose to manually edit the partitions in Ubuntu installer.

I left sda1 (with Windows XP ) as it is.
Added 5Gb for swap 
and created 150Gb partition for /. (i assume its for Ubuntu)

After all I dont have windows in the grub menu.

Fdisk produces this output.

sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3733d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  82  Linux swap / Solaris
/dev/sda2   *         785       18244   140247450   83  Linux

Did I loose windows xp completely? What can I do now to return it back?

---

### Post by Will4 on 2009-01-24
start from your live Cd of Ubuntu, then once it starts go to a terminal (press Alt+F2 and after being prompted you type, gnome-terminal and Enter) 

once at the terminal you...

> ~# sudo grub
grub> find /boot/grub/stage1

after you get a result, let´s say (hd0,2) 

> grub> root (hd0,2)
grub> setup (hd0)

after it says Done...

hit ESC key to save and exit.
then 

> gedit /boot/grub/menu.lst

when it prompts you go to the end to when it says
> ## ## End Default Options ##

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /vmlinuz-2.6.24-16-generic root=UUID=fd4b1619-59ad-4341-ab35-d8a332bac727 ro quiet splash
initrd        /initrd.img-2.6.24-16-generic
quiet 

and edit the 
> root        (hd0,0) 

take your live CD from the tray and reboot.
if you have any other problem when rebooting just edit your menu from the start screen you get by pressing 'e' to edit and after editing 'b' to boot.

once you enter Ubuntu from the normal boot be sure to 
> gedit /boot/grub/menu.lst
again and do all the process one more time. you won't have to do it again.

---

### Post by ilushkin on 2009-01-24
what this will give me? do i still have windows or not ? im so confused....

---

### Post by x33a on 2009-01-24
use gparted to see all of the partitions of your system. if windows shows up, then its a matter of configuring grub as will4 instructed.

---

### Post by caljohnsmith on 2009-01-24
You don't have any NTFS/FAT partitions, so it does look like you lost Windows. How about posting:
```
sudo fdisk -lu
```
That will give a little clearer picture of your partition setup, because it looks like there might be a large chunk of unused space on your HDD.

---

### Post by ilushkin on 2009-01-24
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3733d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    12594959     6297448+  82  Linux swap / Solaris
/dev/sda2   *    12594960   293089859   140247450   83  Linux
ubuntu@ubuntu:~$

---

### Post by ilushkin on 2009-01-24
grub> find /boot/grub/stage1 

produces 

 (hd0,1)

then after following your instructions i hit ESC to quit Grub and get this:

Error 12: Invalid device requested

Press any key to continue...

---

### Post by Buffalo Soldier on 2009-01-24
> **ilushkin said:**
> I left sda1 (with Windows XP ) as it is.

But according to your fdisk -l output, it seems you have set your **sda1** to be used as s**wap partition**
> /dev/sda1               1         784     6297448+  82  Linux swap / Solaris


---

### Post by caljohnsmith on 2009-01-24
You do have a large chunk of unused space on your HDD after your Ubuntu partition, but if your Windows was previously sda1, it looks like it was overwritten when you installed Ubuntu. I suppose there is a small hope that the Windows partition could be hiding in that unused space, so it won't hurt to at least check. How about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on whether your Windows was Vista or not, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

### Post by ilushkin on 2009-01-24
> **Buffalo Soldier said:**
> But according to your fdisk -l output, it seems you have set your **sda1** to be used as s**wap partition**

can i restore sda1?

---

### Post by vandorjw on 2009-01-24
yes you can.

All you need is some software that will restore your partition tables to a previous state.

I don't really know how hard-drives work, but if you haven't done much yet, other than install ubuntu, you might be lucky.

on second thought, maybe not so lucky.

You see, one day I formated my external hard-drive, and I thought I had copied everything to another place. However, I had forgotten all the family photo's that were on there. I found some software that restored a partition tables, except that it was windows software.

So, if windows is overwriten, I hope that you did this to a desktop computer, and that you have another desktop in which you can put the hard-drive on which windows is lost.

Best of Luck - CC7

---

### Post by ilushkin on 2009-01-24
> **caljohnsmith said:**
> You do have a large chunk of unused space on your HDD after your Ubuntu partition, but if your Windows was previously sda1, it looks like it was overwritten when you installed Ubuntu. I suppose there is a small hope that the Windows partition could be hiding in that unused space, so it won't hurt to at least check. How about first making sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on whether your Windows was Vista or not, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

[IMG]http://img440.imageshack.us/img440/9416/screendm7.png[/IMG]

HPFS-NTFS gives me directory listing. What do i Do next? Im in a such trouble.....

---

### Post by caljohnsmith on 2009-01-24
Please follow the directions carefully from my previous post; what you show in that screen looks like the "quick search", so you should press enter to get the next screen, and then select "Deeper Search".

---

### Post by ilushkin on 2009-01-24
> **caljohnsmith said:**
> Please follow the directions carefully from my previous post; what you show in that screen looks like the "quick search", so you should press enter to get the next screen, and then select "Deeper Search".
I did deep search and
HPFS-NTFS gives me directory listing.
Linux gives me directory listing as well.

---

### Post by caljohnsmith on 2009-01-24
OK, how about selecting the swap partition, and using the right/left arrow keys, mark it as "P". Next select the Linux partition and also mark it as "P". Then the NTFS partition, mark it with "*". Once you have them marked exactly like that, press enter to proceed, and in the next screen choose "write" to write the new partition table. Then reboot your Live CD, and please post the new output of:
```
sudo fdisk -lu
sudo mount /dev/sda3 /mnt && ls -l /mnt
```
And we can go from there.

---

### Post by ugm6hr on 2009-01-24
I hope that you are able to recover Windows, but I highly doubt that you will.

sda1 is written from the start of the HD, and it would be very unusual for Windows not to have been there originally.

I hope you backed up important files before embarking on this installation.  It is a bit late for you (sorry), but repartitioning a hard drive is generally not to be recommended unless you know what you are doing.

---

### Post by ilushkin on 2009-01-24
> **caljohnsmith said:**
> OK, how about selecting the swap partition, and using the right/left arrow keys, mark it as "P". Next select the Linux partition and also mark it as "P". Then the NTFS partition, mark it with "*". Once you have them marked exactly like that, press enter to proceed, and in the next screen choose "write" to write the new partition table. Then reboot your Live CD, and please post the new output of:
```
sudo fdisk -lu
sudo mount /dev/sda3 /mnt && ls -l /mnt
```
And we can go from there.

Is this ALL supposed to be done while Im loaded from Live CD or Linux? presently, the desktop loaded from the hard drive.

---

### Post by caljohnsmith on 2009-01-24
> **ilushkin said:**
> Is this ALL supposed to be done while Im loaded from Live CD or Linux? presently, the desktop loaded from the hard drive.
Either is OK, but after you write the new partition table, there's a possibility you might not be able to boot into Ubuntu after you reboot until we reinstall Grub. If that is the case, you can use your Live CD.

---

### Post by ilushkin on 2009-01-24
> **caljohnsmith said:**
> Either is OK, but after you write the new partition table, there's a possibility you might not be able to boot into Ubuntu after you reboot until we reinstall Grub. If that is the case, you can use your Live CD.

Ok, i will follow your instructions in a minute, then. thank you.

It said something like "Invalid Partition Structure" and quit to the main  menu.

---

### Post by ilushkin on 2009-01-24
It said something like "Invalid Partition Structure" and quit to the main menu.

---

### Post by caljohnsmith on 2009-01-24
Sorry about that, that was my mistake--you won't be able to recover both your NTFS and Linux partitions because they overlap. So to recover just your Windows partition for now, how about doing the deep search again, and then mark the NTFS partition with "*" again, but mark all the other partitions with "D". Then write the partition table, reboot the Live CD, and please post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda1 /mnt && ls -l /mnt
```

---

### Post by ilushkin on 2009-01-24
> **caljohnsmith said:**
> Sorry about that, that was my mistake--you won't be able to recover both your NTFS and Linux partitions because they overlap. So to recover just your Windows partition for now, how about doing the deep search again, and then mark the NTFS partition with "*" again, but mark all the other partitions with "D". Then write the partition table, reboot the Live CD, and please post the output of:
```
sudo fdisk -lu
sudo mount /dev/sda1 /mnt && ls -l /mnt
```

I did "write" it and BEFORE restarting with Live CD I would like to show you the output:

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS            914   0  1 30400 254 63  473708655

Boot sector
Status: Bad

Backup boot sector
Status: OK

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

---

### Post by ilushkin on 2009-01-24
here is the output while being loaded with Live CD.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc3733d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *    14683410   488392064   236854327+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && ls -l /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2009-01-24
OK, next try using testdisk to fix the NTFS boot sector, so again run testdisk:
```

sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, try mounting the partition again with:
```
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt && ls -l /mnt
```

---

### Post by ilushkin on 2009-01-24
> **caljohnsmith said:**
> OK, next try using testdisk to fix the NTFS boot sector, so again run testdisk:
```

sudo testdisk
```
After starting testdisk, choose "No log", choose the correct HDD and "Proceed", choose "Intel", choose "Advanced", select the Windows partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". After you are done doing the "Rebuild BS" in testdisk, try mounting the partition again with:
```
sudo mount -t ntfs-3g -o force /dev/sda1 /mnt && ls -l /mnt
```

ubuntu@ubuntu:~$ sudo mount -t ntfs-3g -o force /dev/sda1 /mnt && ls -l /mnt
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

---

### Post by caljohnsmith on 2009-01-24
OK, how about running testdisk yet again, but this time choose "Repair MFT" instead of "Rebuild BS" for the Windows partition. Then try mounting the partition again. If that doesn't work, I would boot your Windows Install CD, go to the "recovery console", and do:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then try mounting the partition again, and let me know if that works or not. Also, just to let you know, I have to get going now and won't be around until tomorrow morning sometime (about 10 hrs from now probably), so we can pick up then if you want.

---

### Post by ilushkin on 2009-01-24
> **ilushkin said:**
> ubuntu@ubuntu:~$ sudo mount -t ntfs-3g -o force /dev/sda1 /mnt && ls -l /mnt
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

This the output from testdisk

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS            914   0  1 30400 254 63  473708655

Boot sector
Status: OK

Backup boot sector
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

---

### Post by ilushkin on 2009-01-24
> **caljohnsmith said:**
> OK, how about running testdisk yet again, but this time choose "Repair MFT" instead of "Rebuild BS" for the Windows partition. Then try mounting the partition again. If that doesn't work, I would boot your Windows Install CD, go to the "recovery console", and do:
```
chkdsk /r
```
And run it as many times as it takes until it reports no errors. Then try mounting the partition again, and let me know if that works or not. Also, just to let you know, I have to get going now and won't be around until tomorrow morning sometime (about 10 hrs from now probably), so we can pick up then if you want.

MFT mirror fixed.

---

### Post by ilushkin on 2009-01-24
> **ilushkin said:**
> MFT mirror fixed.

ubuntu@ubuntu:~$ sudo mount -t ntfs-3g -o force /dev/sda1 /mnt && ls -l /mnt
ls: cannot access /mnt/CMPNENTS: No such file or directory
ls: cannot access /mnt/Config.Msi: No such file or directory
ls: cannot access /mnt/CONFIG.SYS: No such file or directory
ls: cannot access /mnt/Documents and Settings: No such file or directory
ls: cannot access /mnt/hiberfil.sys: No such file or directory
ls: cannot access /mnt/IO.SYS: No such file or directory
ls: cannot access /mnt/MP_ROOT: No such file or directory
ls: cannot access /mnt/MSDOS.SYS: No such file or directory
ls: cannot access /mnt/MSOffice: No such file or directory
ls: cannot access /mnt/NTDETECT.COM: No such file or directory
ls: cannot access /mnt/ntldr: No such file or directory
ls: cannot access /mnt/pagefile.sys: No such file or directory
ls: cannot access /mnt/Program Files: No such file or directory
ls: cannot access /mnt/QIP: No such file or directory
ls: cannot access /mnt/RECYCLER: No such file or directory
ls: cannot access /mnt/System Volume Information: No such file or directory
ls: cannot access /mnt/T4Metrics.log: No such file or directory
ls: cannot access /mnt/TEMP: No such file or directory
ls: cannot access /mnt/tmp.bat: No such file or directory
ls: cannot access /mnt/WINDOWS: No such file or directory
ls: cannot access /mnt/wizard.txt: No such file or directory
ls: cannot access /mnt/AUTOEXEC.BAT: No such file or directory
ls: cannot access /mnt/boot.ini: No such file or directory
ls: cannot access /mnt/Click to DVD 2: No such file or directory
total 492
-????????? ? ?    ?         ?                ? AUTOEXEC.BAT
?????????? ? ?    ?         ?                ? boot.ini
d????????? ? ?    ?         ?                ? Click to DVD 2
d????????? ? ?    ?         ?                ? CMPNENTS
d????????? ? ?    ?         ?                ? Config.Msi
-????????? ? ?    ?         ?                ? CONFIG.SYS
d????????? ? ?    ?         ?                ? Documents and Settings
-rwxrwxrwx 1 root root 502784 2006-06-09 18:42 ehthumbs.db
?????????? ? ?    ?         ?                ? hiberfil.sys
?????????? ? ?    ?         ?                ? IO.SYS
d????????? ? ?    ?         ?                ? MP_ROOT
?????????? ? ?    ?         ?                ? MSDOS.SYS
d????????? ? ?    ?         ?                ? MSOffice
?????????? ? ?    ?         ?                ? NTDETECT.COM
?????????? ? ?    ?         ?                ? ntldr
?????????? ? ?    ?         ?                ? pagefile.sys
d????????? ? ?    ?         ?                ? Program Files
d????????? ? ?    ?         ?                ? QIP
d????????? ? ?    ?         ?                ? RECYCLER
d????????? ? ?    ?         ?                ? System Volume Information
-????????? ? ?    ?         ?                ? T4Metrics.log
d????????? ? ?    ?         ?                ? TEMP
-????????? ? ?    ?         ?                ? tmp.bat
d????????? ? ?    ?         ?                ? WINDOWS
-????????? ? ?    ?         ?                ? wizard.txt
ubuntu@ubuntu:~$

---

### Post by ilushkin on 2009-01-24
I will get back to you tomorrow with the results. thank you!

---

### Post by ilushkin on 2009-01-25
> **ilushkin said:**
> I will get back to you tomorrow with the results. thank you!

chkdsk /r produces nothing but "The volume appears to contain one or more unrecoverable problems."

At this point can I just reinstall Ubuntu and still be able to use both Windows and Ubuntu?

---

### Post by ilushkin on 2009-01-25
need your help. my friendship is at stake. i took my friends pc and wiped his windows out with all his personal files, accidentally. What a fluke. I have 2 years experience in IT, but always felt uncomfortable in Linux partitioning. Trouble! Trouble!

---

### Post by golusweet on 2009-01-25
I never had any problem while installing ubuntu.Looks like you did something wrong.

Well!Just search for some recovery applications that could recover the data from partition.:p

---

### Post by ilushkin on 2009-01-25
> **golusweet said:**
> I never had any problem while installing ubuntu.Looks like you did something wrong.

Well!Just search for some recovery applications that could recover the data from partition.:p

Nothing can help me, but the pray. i did sometthing wrong. Now, I lost my friend's files.

---

### Post by caljohnsmith on 2009-01-25
OK, how about running testdisk again, but this time do it in a "recovery directory" so you can save files there:
```
cd; mkdir Windows_recovery
cd Windows_recovery; sudo testdisk
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "N" for Vista partitions, and if it lists your Windows partition after the quick search, use "p" to get a directory listing. If that gives you a directory listing OK, use your right/left arrow keys to go through all the Windows folders, and when you find your friend's personal documents (probably stored under "Documents and Settings" and then his user name), try copying them with "c". If you can't get a directory listing, do the deeper search again and try doing "p" to get a directory listing once the deep search is done and shows your NTFS partition. Let me know if that works or not.

---

### Post by ilushkin on 2009-01-25
> **caljohnsmith said:**
> OK, how about running testdisk again, but this time do it in a "recovery directory" so you can save files there:
```
cd; mkdir Windows_recovery
cd Windows_recovery; sudo testdisk
```
After starting testdisk with the above command, choose "No Log", select HDD and "Proceed", "Intel", "Analyze", "Quick search", "N" for Vista partitions, and if it lists your Windows partition after the quick search, use "p" to get a directory listing. If that gives you a directory listing OK, use your right/left arrow keys to go through all the Windows folders, and when you find your friend's personal documents (probably stored under "Documents and Settings" and then his user name), try copying them with "c". If you can't get a directory listing, do the deeper search again and try doing "p" to get a directory listing once the deep search is done and shows your NTFS partition. Let me know if that works or not.

I had enough. I'm an idiot. All I had to do was to choose automatic partitioning in Ubuntu installer, instead of it I screwed up all hard drive and took your time. Fortunately, I have these recovery cds. I will use them and reinstall Ubuntu properly. Thank you for your support and help.

---

