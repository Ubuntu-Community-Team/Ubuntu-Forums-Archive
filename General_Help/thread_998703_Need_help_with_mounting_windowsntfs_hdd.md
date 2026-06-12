---
title: "Need help with mounting windows/ntfs hdd"
date: 2008-12-01
forum: General Help
---

### Post by iAndrew on 2008-12-01
So just recently my windows has been giving me errors. I can't boot; I get bsod neither can I boot into safemode, I get the same errors.

Now all I want to do is to be able to mount it, save a few files onto my ubuntu (8.04) partition then reformat my windows.

I read up on how to mount it, I've installed ntfs-3g/ntfs-config and I've tried doing sudo fdisk -l

this is what I get out:

```
drew@x86:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e635b74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         373     2996091   82  Linux swap / Solaris
/dev/sda2   *         374       10707    83007855   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd16dd16

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS
drew@x86:~$ 


```

the sdb1 is what I'm trying to mount.

```
drew@x86:~$ sudo mount /dev/sdb1
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```

I use the installation cd and I can't even use /f as a parameter.

It's the second one, I do have a SoftRaid/FakeRaid (it's on a floppy used it when I installed Windows) but I'm not sure on how I can activate it.

---

### Post by tjandracom on 2008-12-01
because your SoftRAID/FakeRAID will not run under Linux (you said that you use the floppy when u install Windows, so it must be a Windows Service Application), and the data is so important, it is better to open it from Windows rather than from any Linux. have a clean install of windows (and install the same SoftRAID/FakeRAID) in another hardisk, then attach the previous disk to save the data.

after that, you could play with linux to see if it could be mounted. ntfs-3g is an awesome project, and could used safely to mount "read and write" an ntfs disk, and i myself used it for partition that should be mount from WinXP and Ubuntu Hardy.

---

### Post by zotkop on 2008-12-01
Have you tried to use forcemount the partition?

---

### Post by iAndrew on 2008-12-01
Thanks so far to both replies.

I would need more clarification on how I would do that (new installation of windows, etc)

and what is the force mount? (no)

---

### Post by taurus on 2008-12-01
You can try something like this to see if it works or not.

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```

---

### Post by iAndrew on 2008-12-01
> **taurus said:**
> You can try something like this to see if it works or not.

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
df -h
```

For the first command, the directory already exists.

For the second, I get the same error, previously mentioned above, and the 3rd it mentions which are mounted.

(I must've changed boot pattern while I plugged/unplugged the hdds because the windows hdd turned into sda1 and the ubuntu hdd turned into 320gb hdd)

---

### Post by TeXtonyx on 2008-12-01
Manually, the process goes like this,

sudo mkdir /mnt/Windows
sudo mount -t ntfs /dev/sdb1 /mnt/Windows

If the Windows partition was not shut down cleanly, the times
when you boot up and see a screen with different boot options
in black and white, one of which says, start Windows normally,
then Ubuntu will not mount Windows in this case. Windows needs
to have been shut down cleanly for the mount to work. Or maybe
you already have a Windows folder from running ntfs-config and
that is under /media/Windows or whatever you named windows.

sudo mount nfts-3g -o force,rw /dev/sdb1 /mnt/Windows
or
sudo mount -t ntfs -o force,rw /dev/sdb1 /mnt/Windows/ 

force is not a recommended practice. Also it might not work
depending upon what's wrong with Windows. But if you can mount
it, then you'd better do your backing up of key docs and images.
Because repairing or installing XP puts more stress on the drive.

I'm better at Windows than Ubuntu. How old is your hard drive on
sdb? You will need your XP install disk not an OEM recovery disk.

[http://support.microsoft.com/kb/315341](http://support.microsoft.com/kb/315341)
This has tons of instuctions, read only if you are a geek.

[http://www.michaelstevenstech.com/XPrepairinstall.htm#RI](http://www.michaelstevenstech.com/XPrepairinstall.htm#RI) Use this!
Now in your case you can actually do the first repair install
he mentions which just lets fixmbr, fixboot, bootcfg /rebuild
in that order. I don't think it will work but it is fast and
less (possibly) destructive.

If it doesn't work try the 2nd repair install presented in stevens article.
There is also a way to do a non-destructive reinstall of windows.
It makes a C:\Window.000 directory. It's not supposed to damage
any data except My Documents. But most of your applications won't
work and will need to be reinstalled. 

These Repair steps will probably fail if you have a bad hard drive.
Your system memory is ok, because you can still boot Ubuntu.
To do this stuff it is easier to change your boot order in bios
from hd0 = Ubuntu =sda to hd1 = sdb and also set your boot order
to boot from the cdrom first. cdrom, hd1, hd0 in that order.

Afterwards of the Windows reparir install, change the boot order
back to cdrom hd0 hd1. Mabye you will have to reinstall grub to
recognize the Windows drive again. Try it first. 

sudo grub
grub> find /boot/grub/stage1
grub> root (hd0,0) (use what 'find' reports)
grub> setup (hd0)
quit

This recovery should proceed with no problems, like clockwork. :lolflag:

---

### Post by iAndrew on 2008-12-01
Alright, I'm not really a computer newbie (I should just put this out there) but I guess I'm sort of a novice compared to how much there is too know about computers / different os(s). The disks are pretty recent (6-8 months).

I'm sure that they weren't shut down correctly and I won't be able to shut them down correctly due to bsod on load (even when I try to safemode it).

Without reading either guides most of the documents I need are in "my documents", however I'll read more indepth about this.

I'll post another reply once I've tried/read up on the methods. Thanks.

---

### Post by iAndrew on 2008-12-01
Both instances required Repair to be there, it wasn't an option for me.

Any other ideas? I appreciate the effort.

---

### Post by TeXtonyx on 2008-12-01
> **iAndrew said:**
> Both instances required Repair to be there, it wasn't an option for me.

Any other ideas? I appreciate the effort.

I guess that your Windows OS is XP. Here is a screenshot for Vista,
[http://www.winsupersite.com/win7/win7_m3_install.asp](http://www.winsupersite.com/win7/win7_m3_install.asp)
I think fixing startup problems comes under Startup Repair with Vista.

[http://www.labtestproject.com/screenshot/windows_xp/pages/001_xp_setup.html](http://www.labtestproject.com/screenshot/windows_xp/pages/001_xp_setup.html)
This is for XP and I will attach the relevant screenshot below.
At the bottom but not shown in the screenshot attached, it says,
Enter=Continue R=Repair  F3=Quit (just for information)

This then, is the screen if you have a Windows XP install cd. If 
you don't have that option (Repair) then you don't have an XP 
install cd, but a manufacture recovery cd which installs XP and 
drivers but does not preserve any data. It's like you just got it.

So you can try forcing the mount of Windows and navigate to 
My Documents and copy that folder over to your Ubuntu drive.
If that doesn't work, try a rescue cd, like UBCD. You can try
to borrow a genuine XP cd and try Repair with that cd. These
approaches assumes the drive is sound, Repair or reinstalling. 

You can decide to run a hard drive disk diagnostic, one or two
come with the UBCD rescue cd. [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
If the drive is bad no use going to a lot of trouble trying to 
reinstall. Maybe your recovery cd will work on a replacement drive.

Recovering data after the fact of a problem, is a pita, so now
you know why people repeat, backup, backup, like a mantra. You
could have already backed up My Documents on the Ubuntu drive
before this happened, or to a cd or usb stick. I had to learn 
this the hard way, actually, like most people do. That old
saying, a word to the wise is sufficient, doesn't work very often.

---

### Post by iAndrew on 2008-12-01
I'll try a recovery disk, and the disk is genuine. It says in the guide not to use the recovery console, so I'm confused there.

---

### Post by TeXtonyx on 2008-12-01
> **iAndrew said:**
> I'll try a recovery disk, and the disk is genuine. It says in the guide not to use the recovery console, so I'm confused there.

There is a genuine recovery disk provided for some computers by 
the manufacturers. There is also a genuine Windows installation cd
which is often acquired separately. They are not the same thing.
The Windows installation cd comes with a Recovery Console, that
lets one run fixmbr, fixboot, and bootcfg /rebuild in that order.
That is not what the OEM recovery disk does, that restores the
computer back to a fresh install level, OS/drivers, not a repair.

What guide are you using and what OS do you have?
I showed you a picture of what a genuine Windows XP install cd 
looks like when at an early screen; and a link to what a Vista 
install cd looks like at an early screen. 

If your disk doesn't show you either the XP or Vista install screen,
that matches the one in the picture I sent you, then you have a
manufacturer recovery cd, which does not have the Repair option,
for XP/Vista, either the first repair option which does fixmbr etc. or the 
next Repair option... Did you mean the stevens guide? The fixmbr etc.
method is quicker if it works. Or you can do the second Repair option
if the fixmbr method doesn't work. Or you can skip the fixmbr method
and do the second Repair option immediately. A recovery disk isn't the 
same thing as an installation disk that has some recovery functions.
And both kinds of disks are common. That's why I don't know what you
mean by "a recovery disk". You can't use a recovery cd just an install cd
to do either kind of Repair install.

---

### Post by iAndrew on 2008-12-01
I guess I should've clarified more.

I have windows xp pro sp2 installed, and the same disk (windows xp pro sp2) installer cd.

---

### Post by TeXtonyx on 2008-12-01
> **iAndrew said:**
> I guess I should've clarified more.

I have windows xp pro sp2 installed, and the same disk (windows xp pro sp2) installer cd.

Earlier you wrote,
"Both instances required Repair to be there, it wasn't an option 
for me. Any other ideas? I appreciate the effort."  

So if you have the xp installer cd, why wasn't Repair there,
why isn't it an option for you?

---

### Post by iAndrew on 2008-12-01
Must've been a wording mistake.

I get the "Recovery Console" I've tried deleting a few sys files, and I get access denied.

---

### Post by TeXtonyx on 2008-12-01
> **iAndrew said:**
> Must've been a wording mistake.

I get the "Recovery Console" I've tried deleting a few sys files, and I get access denied.

I mentioned using Recovery Console for fixmbr, fixboot, and
bootcfg /rebuild in that order. I wouldn't call that deleting files
so you must be doing something else I guess, nothing I mentioned.

---

### Post by iAndrew on 2008-12-02
Well, after checking that route a few more times I found that I could not login

Normally, you'd have a prompt like this: [http://www.intelliadmin.com/images/Windows%202003%20Recovery%20Console.jpg](http://www.intelliadmin.com/images/Windows%202003%20Recovery%20Console.jpg)

I tried re-installing it (to see if I got the repair option (not system recovery)) on a different partition (which messed up my booting(I fixed it with sgrub))

So I login to the "bad/partial" Windows, and from there it seems that I'm not able to ( I don't know if can't is right ) fixmbr/fixboot/bootcfg /rebuild for the correct locked up drive.

/e - I'll try this in a few minutes and post if I can or not.

However, I tried

copy x:\i386\ntldr C:\
copy x:\i386\ntdetect.com C:\

and when I tried executing the first command I got bsod (like I normally do) but this time I was able to capture the entire message (it was instantenous when I tried to boot / safe mode boot)

The message is:

A problem has been detected and Windows has been shut down to prevent damage to your computer.

BAD_POOL_HEADER

If this is the first time you've seen this stop error screen, restart your computer. If this screen appears again, follow these steps:

Check to make sure any new hardware of software is properly installed.
If this is a new installation, ask your hardware of software manufacturer for any windows updates you might need.

If problems continue, disable or remove any newly installed hardware of software. Disable BIOS memory options such as caching or shadowing. If you need to use safe mode to remove or disable components, restart your computer, press F8 to select advanced start up options, and then select safe mode.

Technical Information:

*** STOP: 0x00000019 (0x00000020, 0xE10DB3C0, 0xE10DB418, 0x0C0B0802)

If there are any spelling errors, my apologies. I double checked the tech info so no possible mess ups.

---

### Post by iAndrew on 2008-12-02
Alright well I executed those commands. I also added the correct drive.

All seem to have went well except for the 3rd.

Error: Failed to succesfully scan disks for Windows installations. This error my be caused by a corrupt file system, which would prevent bootcfg from successfully scanning. use chkdsk..

so I'm running chkdsk on the drive, it's awfully slow and keeps hoping from like 70 to 50.

I'll keep you posted, thanks for the help

---

### Post by TeXtonyx on 2008-12-02
[http://www.intelliadmin.com/images/W...%20Console.jpg](http://www.intelliadmin.com/images/W...%20Console.jpg)

You need to enter the password that was created during the original
installation. Or, no password was created and you can use <enter>
for the password, just tap the Enter key. I've seen a utility on
the internet that removes or resets the Admin password also (UBCD?).

I think you should do the second option Repair available, the one
at [http://www.michaelstevenstech.com/XPrepairinstall.htm#RI](http://www.michaelstevenstech.com/XPrepairinstall.htm#RI) 

This time, since you don't want to use Recovery Console, which is
what his warning is about, many people get confused and use the
first option of Repair when they need to use the second option,
his warning is to prevent the confusion only. You probably should
read the Warnings that he issues before taking this step.

This repair will often fix problems, but it not infallible. 
For one thing it replaces ntldr and related files. If it does
not work, then you will have to do a fresh install. I think
there will be an option to create a C:\Windows.000 instead
of deleting the old system. If you haven't been able to force
a mount from Ubuntu and backup your important data, then one
should consider the C:\Windows.000 approach since it saves quite
a bit of data, but as I said I'm not sure about My Documents. 
You can try the rescue cd, UBCD, which might let you mount the
drive and copy some of the important documents. 

Because you get an error message about ntldr missing, doesn't
mean that ntldr isn't there, it can already be on the drive.
That message can be a symptom not the actual problem. At this
point one doesn't know what the actual problem is. If the Repair
installation doesn't go through, or you can't cleanly reinstall,
the drive may have too many damaged sectors.

[http://www.techspot.com/vb/topic16669.html](http://www.techspot.com/vb/topic16669.html)
I used Google to find a post close to yours "I usually get BSOD 
with message "bad_pool_header" with info: " STOP 0x00000019 
(0x00000020, 0x86301D68, 0xA210004)"

Seems to me that if you had a hardware problem other than the
hard drive, that it would show up when you used Ubuntu also.
Did you install any new hardware recently, like a video card?
Your hard drive is specific hardware for your XP system which
is why I mention that. Often the computer will come with a cd
disk which has the drivers for the motherboard. That has to be
installed after a fresh install of XP or you will see yellow
exclamation points for devices in Device Manager. 

I think you should try the (second) Repair option. If that doesn't
work, rather than a clean install next, you could see if your
hard drive is well either from a UBCD utility or the manufacturer
of your drive very likely has a diagnostic utility at the website.

[http://forum.parallels.com/showthread.php?t=12387](http://forum.parallels.com/showthread.php?t=12387)
This offered a solution that required safe mode which you might
not have available, so here is an untested registry fixer from
Ubuntu: [http://www.arsgeek.com/2008/02/27/use-your-ubuntu-partition-to-fix-a-corrupt-registry-on-a-windows-xp-partition/](http://www.arsgeek.com/2008/02/27/use-your-ubuntu-partition-to-fix-a-corrupt-registry-on-a-windows-xp-partition/)

Those error message might have 15 to 20 different causes. Another
is a bad driver for a wireless card. Starting with a second 
option Repair install seems like the best place to start. I do
a clean install next if there are many time consuming ways to try
to fix a problem, but I have a backup. There is no guarantee that
any of several possible fixes will actually fix the problem.

---

### Post by iAndrew on 2008-12-02
Okay I'm not sure what it was.

But I left on chkdsk, then I tried logging (logon cmd) and I found that this time they let me login to it.

I tried the 3 commands, but bootcfg /rebuild still didn't work.

I hopped on ubuntu and now I can mount it which was I wanted.

Thanks a bunch.

---

### Post by tjandracom on 2008-12-03
the easier and safer way if u don't know how to install windows is to attach the hardisk as slave or secondary disk in another computer running Windows to see whether the disk is functioning or could be mounted.

---

### Post by TeXtonyx on 2008-12-03
> **tjandracom said:**
> the easier and safer way if u don't know how to install windows is to attach the hardisk as slave or secondary disk in another computer running Windows to see whether the disk is functioning or could be mounted.

That's a good idea. I have a friend Paul who visits a town named
Bandung in Thailand, I don't know how common that name is.

---

### Post by tjandracom on 2008-12-05
[QUOTE="TeXtonyx"]I have a friend Paul who visits a town named
Bandung in Thailand, I don't know how common that name is. [/QUOTE]

i just know that there's a town named Bandung in Thailand too... ):P

---

