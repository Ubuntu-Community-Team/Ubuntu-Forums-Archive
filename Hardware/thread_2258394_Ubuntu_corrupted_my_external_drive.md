---
title: "Ubuntu corrupted my external drive"
date: 2014-12-27
forum: Hardware
---

### Post by rjhanson on 2014-12-27
Hello,
Not a happy camper.  Since the last updates Ubuntu 14.10 is corrupting my external drives, causing me to lose 2TB of data.  I have never had this issue before so I need a solution or I am going back to windows, just can not afford to lose data.

The first one was an exfat drive and now a flash drive with NTFS.  Here is the message.  Just so you know the drive shows up in windows with no formating so I can not use fdisk in windows to fix it.

Error mounting /dev/sdh1 at /media/rjhanson/64gb-mini: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdh1" "/media/rjhanson/64gb-mini"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdh1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Thanks in advance for any help as I am new to Ubuntu with few skills :(

---

### Post by barkerson on 2014-12-27
What caused the corruption? Was it mounting the drive or was it just connecting it to your pc that caused the problem?

Before you do anything drastical wait for someone to confirm what I am abot to say is true as I don't know if it is myself.

Look if exfat is actually installed in ubuntu, if it isn't this could cause errors(it at least did this for me with a reiser disc when reiser wasn't installed, only no corruption). If you're lucky it will fix itself if you haven't formatted anything yet.
You could as a last resort use GParted in ubuntu to format the drive (or look for disc errors), but use this only as a last resort.

---

### Post by rjhanson on 2014-12-27
I made the mistake of creating the exfat structure with a script I found on the web.  It looked good.  Started to move files and after about 1.5 TB it says it had a pointer error (can not remember the exact statement).  I put it on a windows box and it wanted to format the drive, never good.  I have been using exfat for over a year with no issues until today.

The next issue, I used DISK to format a 64 GB flash drive and as I started to copy things over (got smarter and only copied, not cut and pasted, which I was smarter sooner) and in the middle of copying it comes up with this error in my first entry.

Tried GParted to find the partition but is says it does not have one

---

### Post by weatherman2 on 2014-12-27
Unfortunately, no one here can say exactly what happened to you in those two isolated cases.  Sometimes you have to learn the lessons (use copy not move; always have a backup) the hard way.

For what it's worth, I've been using NTFS in Ubuntu for many years with never a corruption issue or major problem, having copied many TB of data.  (The only "minor problem" is that copying large NTFS files can take a lot of CPU time and be slower than using Windows.)  I haven't used Ubuntu 14.10 yet though - I prefer to stick to the LTS versions that are supported for many years instead of versions that are supported for only nine months.

I use exFat occasionally to copy files from my camera's memory card (exFat) to my Ubuntu laptop.  Never an issue there either, but I wouldn't call that extensive use.  I'd stick to NTFS if Windows compatibility is required.  In the last few years, as I've transitioned from part-time Ubuntu use to full-time Ubuntu use and mostly abandoned Windows, I've moved all of my data to ext4 partitions anyway, so Windows compatibility isn't an issue for me anymore.

---

### Post by barkerson on 2014-12-27
If you wanted to format the drive you SHOULD have used GParted to do the job for you(easier, less prone to errors). These cases seem more like me in my first years of ubuntu not knowing what was more logical(windows=download programs from random places while ubuntu=use software center/synaptic). You could try to insert the disc after opening GParted then in the tab "gparted" press refresh devices, this should make it appear.

Try to install exfat-util from synaptic (which you find in software center if synaptic isn't installed). then gparted will let you format and shows you errors in a more "human" way.

---

### Post by rjhanson on 2014-12-27
Thanks guys for the feedback.  I don't know what caused the issues either.  I have all my other drives in ext4 with no problems.  I was moving the files to exfat because I was going to keep it on a windows 7 computer at our church.  I should have left it as ext4 and added the windows driver to use it, but hindsight is wonderfully painful :(

Thanks again

---

### Post by Sef on 2014-12-27
Did you [install]("http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04") these packages:

> [FONT=Ubuntu Mono]sudo apt-get install exfat-fuse exfat-utils[/FONT][COLOR=#333333][FONT=UbuntuRegular]Or try to mount it manually after installing the above packages,[/FONT][/COLOR]
sudo mkdir /media/exfat
sudo mount -t exfat /dev/sdxx /media/exfat
[COLOR=#333333][FONT=UbuntuRegular]/dev/sdxx - your exfat partition.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In Ubuntu 14.04, exfat-fuse and exfat-utils packages are available in Universe repository. So enable this repository inorder to install these two packages on Ubuntu 14.04.[/FONT][/COLOR]
sudo add-apt-repository universe
[COLOR=#333333][FONT=UbuntuRegular]And don't forget to update all repositories,[/FONT][/COLOR]
[FONT=Ubuntu Mono]sudo apt-get update[/FONT]

---

