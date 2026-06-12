---
title: "fixing windows partition from ubuntu"
date: 2008-11-20
forum: General Help
---

### Post by rokyersoxoff on 2008-11-20
Hello all,

Let me first say that I'm still learning my way around linux, but I'm a UNIX sysadmin by profession ( ie. not a complete noob )

Anyway, my problem is this: I have a dual-boot laptop ( Ubuntu & XP ).  I just installed the Ubuntu partition a couple months ago...so I'm still learning my way around.  XP used to boot up and allow me to login, but I ran into the following error ( "domain <domain_name> is not available" ), after I tried restoring to a previous backup point.  To be honest, I would love to convert to Ubuntu entirely, but there are still some things I need XP for ( running the Ultimate Bet poker client, iTunes, etc...).  I realize that there are currently solutions out there that would alleviate my XP dependency ( wine, etc... ), but I haven't had much luck running the UB client using wine ( it's pretty slow and crashes every 10 minutes ).  This probably speaks more to my hardware config, but I digress.  Suffice it to say that XP is a necessary evil, for now.

Here are things I’ve tried and/or determined thus far: 
- I cannot boot to “Safe Mode” at this point.  I don’t remember the problem I ran into, but this doesn’t appear to be and option.
- When I try to boot from my “Emergency boot CD” I get the “...corrupt or missing hal.dll” error.  Not sure if this is maybe a result of installing GRUB ( and it somehow conflicts with boot.ini ) , but I can’t boot this way.  I pulled a good copy of ‘hal.dll’ from a microsoft website and placed it in the appropriate directory just in case.  Same problem.
- Some people in the windows community ( other forums ) have suggested a full re-install of XP.  That really seems like a “bull in a china shop” approach, and obviously a last resort.  This shouldn’t be necessary, as the XP partition actually boots up.  The real problem is “logging in”.
- Other forums advise editing the windows registry to resolve the “domain not avail” issue, but this error message suggests that “logon credential caching” is not enabled ( according to the research I’ve done ), so I don’t believe this will resolve anything ( though I could be wrong ).
- I also read, on another forum, that there might be a patch that addresses this issue, but I’m not entirely sure how to apply a patch to XP from Ubuntu ( since Ubuntu is the only partition I can currently access ).


So.....what I’m looking for are any suggestions on how I can repair/change my XP partition from within Ubuntu.  I have the XP partition mounted ( with “read” and “write” permissions ).  There must be a way to delete/change the current logon credentials, or take some other action, to enable me to logon.

I apologize that I can’t provide more specifics, as I don’t have access to my personal laptop currently.  I also apologize for the lengthy nature of my post.

Any suggestions will be much appreciated.

---

### Post by Yellow Pasque on 2008-11-20
I ran into this problem (hal.dll messages and admin login not working) on my sister's computer (which was a purely XP Home machine). I did a lot of research and tried loads of things including fixing the partition from Linux Live CD's and other utility CD's (e.g. Hiren's Boot Utilities CD).

I, like you, believed that there HAD to be a way to fix it without reinstalling, but you have to remember that this is Windows we're talking about. It doesn't always make sense and I've found the following saying to be true the more and more I do tech support: ("he who does not understand UNIX is doomed to reinvent it ... poorly"). In hindsight, I just wasted a lot of time "pissing in in the wind". A full reinstall was needed.

---

### Post by caljohnsmith on 2008-11-20
Is your "Emergency Boot CD" an OEM Windows CD? Or do you have a Windows Install CD? If you have a Windows Install CD, then one option might be to simply do a "Windows Repair", which basically reinstalls all of the Windows core system files without touching your installed programs or personal data. It worked well for me when I had to do it once. Anyway, good luck.

---

### Post by rokyersoxoff on 2008-11-21
The disk is actually an "Ultimate Boot disk" I found after doing some online research.  It's a download titled "UBCD4WINV3".  I received no OEM CD when I purchased the laptop.  I guess that's standard procedure nowdays...to not get any type of recovery/boot CD with your hardware.  Anywho, that was the case when I purchased my Dell.

---

### Post by rokyersoxoff on 2008-11-21
"he who does not understand UNIX is doomed to reinvent it ... poorly"



Very true....I'm going to use that one

---

### Post by caljohnsmith on 2008-11-21
Do you have a Dell recovery partition maybe? How about booting your Live CD, open a terminal (Applications > Accessories > Terminal), and please post the output of:
```
sudo fdisk -lu
```

---

### Post by rokyersoxoff on 2008-11-22
Here's my setup:

root@chicken-hawk:/home/mspen# sudo fdisk -lu

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders, total 192426570 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+   6  FAT16
/dev/sda2   *       96390   102494699    51199155    7  HPFS/NTFS
/dev/sda3       102494700   142914239    20209770    5  Extended
/dev/sda4       182675115   192410504     4867695   82  Linux swap / Solaris
/dev/sda5       102494763   102912389      208813+  83  Linux
/dev/sda6       102912453   142914239    20000893+  8e  Linux LVM

---

### Post by caljohnsmith on 2008-11-22
You do have a small 50 MB FAT16 partition at the beginning of your drive; if you don't happen to know what that is there for, it might have something to do with a recovery partition, although it seems quite small for that. How about posting:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Where "-l" is a lowercase L, not a one. Also, how about booting your Ultimate Boot CD, go to File System Tools > Boot Managers > Super Grub Disk, and then when you get the Super Grub Disk menu, press "c" to go to the command line. Then enter:
```
grub> chainloader (hd0,0)+1
grub> boot
```
And let me know if it boots sda1 successfully, or if it just gives you an error of some sort, let me know the error.

---

### Post by rokyersoxoff on 2008-11-24
Here's the output:

root@chicken-hawk:/home/mspen# sudo mount /dev/sda1 /mnt
root@chicken-hawk:/home/mspen# bdf
bash: bdf: command not found
root@chicken-hawk:/home/mspen# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             19686804   4408864  14277896  24% /
varrun                 1033208       116   1033092   1% /var/run
varlock                1033208         0   1033208   0% /var/lock
udev                   1033208        56   1033152   1% /dev
devshm                 1033208        12   1033196   1% /dev/shm
lrm                    1033208     39760    993448   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda5               195694     36086    149168  20% /boot
/dev/sda1                48052      7930     40122  17% /mnt
root@chicken-hawk:/home/mspen# cd /mnt
root@chicken-hawk:/mnt# ls -l
total 6936
-rwxr-xr-x 1 root root  316659 2007-07-30 13:45 adaptec2.mdm
-rwxr-xr-x 1 root root  325139 2007-07-30 13:45 adaptec.mdm
-rwxr-xr-x 1 root root   48155 2007-07-30 13:45 ami_raid.mdm
-rwxr-xr-x 1 root root     398 2006-04-03 15:19 autoexec.bat
-rwxr-xr-x 1 root root     398 2006-04-03 15:19 autoexec.up
-rwxr-xr-x 1 root root   18955 2007-07-30 13:45 biosmp.mdm
-rwxr-xr-x 1 root root  189138 2007-07-30 13:45 cables.mdm
-rwxr-xr-x 1 root root   48491 2007-07-30 13:45 cache.mdm
-r-xr-xr-x 1 root root   53569 2005-06-21 18:54 command.com
-rwxr-xr-x 1 root root      49 2000-01-05 13:32 config.bts
-rwxr-xr-x 1 root root      77 2006-04-03 15:19 config.sys
-rwxr-xr-x 1 root root      77 2006-04-03 15:19 config.up
-rwxr-xr-x 1 root root      85 2006-04-03 15:19 copyup.bat
-rwxr-xr-x 1 root root   33490 2007-07-30 13:45 cpu.mdm
-rwxr-xr-x 1 root root    4419 2007-07-30 13:45 ddinit.mim
-rwxr-xr-x 1 root root    1814 2007-07-30 13:45 ddinit.mlm
drwxr-xr-x 2 root root    2048 2003-10-20 00:07 dell
-r-xr-xr-x 1 root root   29690 2005-07-25 18:48 dellbio.bin
-rwxr-xr-x 1 root root    2635 2006-04-03 15:19 Dellboot.exe
-rwxr-xr-x 1 root root   10145 2007-07-30 13:45 delldiag.com
-rwxr-xr-x 1 root root 1201839 2007-07-30 13:45 delldiag.exe
-rwxr-xr-x 1 root root     319 2007-07-30 13:45 delldiag.ini
-r-xr-xr-x 1 root root   33352 2005-06-21 18:54 dellrmk.bin
-rwxr-xr-x 1 root root   83415 2007-07-30 13:45 dellsys.msm
-rwxr-xr-x 1 root root  863731 2007-07-30 13:45 delltbui.exe
-rwxr-xr-x 1 root root     799 2006-04-03 15:19 dir.lst
-rwxr-xr-x 1 root root   62772 2007-07-30 13:45 diskette.mdm
-rwxr-xr-x 1 root root  259463 2007-07-30 13:45 disk.mdm
-rwxr-xr-x 1 root root   18946 2007-07-30 13:45 dvd.mdm
-rwxr-xr-x 1 root root     247 2008-09-05 10:36 eeprom.dmp
-rwxr-xr-x 1 root root  186829 2007-07-30 13:45 genaudio.mdm
-rwxr-xr-x 1 root root   77995 2007-07-30 13:45 hdaudio.mdm
-rwxr-xr-x 1 root root  106367 2007-07-30 13:45 iaudio.mdm
-rwxr-xr-x 1 root root   28655 2007-07-30 13:45 ieee1394.mdm
-rwxr-xr-x 1 root root   38980 2007-07-30 13:45 imchecc.mdm
-rwxr-xr-x 1 root root     900 2007-07-30 13:45 int15_88.com
-rwxr-xr-x 1 root root   50830 2007-07-30 13:45 ioapic.mdm
-rwxr-xr-x 1 root root   62438 2007-07-30 13:45 ir.mdm
-rwxr-xr-x 1 root root  194683 2007-07-30 13:45 Keyboard.mdm
-rwxr-xr-x 1 root root   90675 2007-07-30 13:45 lsi.mdm
-rwxr-xr-x 1 root root  120877 2007-07-30 13:45 Memory.mdm
-rwxr-xr-x 1 root root   41523 2007-07-30 13:45 MiscPci.mdm
-rwxr-xr-x 1 root root   77101 2007-07-30 13:45 Mouse.mdm
-rwxr-xr-x 1 root root   57302 2007-07-30 13:45 MpCache.mdm
-rwxr-xr-x 1 root root   42936 2007-07-30 13:45 NbBatt.MDM
-rwxr-xr-x 1 root root   33316 2007-07-30 13:45 nbfan.mdm
-rwxr-xr-x 1 root root   70808 2007-07-30 13:45 nbsvc.mdm
-rwxr-xr-x 1 root root   48212 2007-07-30 13:45 Nbtherm.MDM
-rwxr-xr-x 1 root root   83515 2007-07-30 13:45 nic8254x.mdm
-rwxr-xr-x 1 root root  239232 2007-07-30 13:45 Nic.mdm
-rwxr-xr-x 1 root root     319 2007-07-30 13:45 oldver.ini
-rwxr-xr-x 1 root root   47741 2007-07-30 13:45 Parallel.mdm
-rwxr-xr-x 1 root root   14691 2007-07-30 13:45 Pci.mdm
-rwxr-xr-x 1 root root   33490 2007-07-30 13:45 Perc2Ada.mdm
-rwxr-xr-x 1 root root   13931 2007-07-30 13:45 pm.mdm
-rwxr-xr-x 1 root root   24211 2007-07-30 13:45 pnp.mdm
-rwxr-xr-x 1 root root   62222 2007-07-30 13:45 raid.mdm
-rwxr-xr-x 1 root root  274886 2007-07-30 13:45 scsi.mdm
-rwxr-xr-x 1 root root   50393 2005-12-12 23:05 seal.exe
-rwxr-xr-x 1 root root   48564 2007-07-30 13:45 serial.mdm
-rwxr-xr-x 1 root root  112763 2007-07-30 13:45 smbios.mdm
-rwxr-xr-x 1 root root   23572 2007-07-30 13:45 smbus.mdm
-rwxr-xr-x 1 root root   27750 2007-07-30 13:45 smi.mdm
-rwxr-xr-x 1 root root    1979 2007-07-30 13:45 symtree.ini
-rwxr-xr-x 1 root root   84397 2007-07-30 13:45 sysbdmon.mdm
-rwxr-xr-x 1 root root   76252 2007-07-30 13:45 System.mdm
-rwxr-xr-x 1 root root   48239 2007-07-30 13:45 usb2.mdm
-rwxr-xr-x 1 root root  119144 2007-07-30 13:45 usbdevid.mdm
-rwxr-xr-x 1 root root   52404 2007-07-30 13:45 usbehci.mdm
-rwxr-xr-x 1 root root  142410 2007-07-30 13:45 usbkbd.mdm
-rwxr-xr-x 1 root root   23801 2007-07-30 13:45 usbmass.mdm
-rwxr-xr-x 1 root root   72648 2007-07-30 13:45 usb.mdm
-rwxr-xr-x 1 root root   51298 2007-07-30 13:45 usbmouse.mdm
-rwxr-xr-x 1 root root   34027 2007-07-30 13:45 usbohci.mdm
-rwxr-xr-x 1 root root   52481 2007-07-30 13:45 usbtm.mdm
-rwxr-xr-x 1 root root   61981 2007-07-30 13:45 usbufi.mdm
-rwxr-xr-x 1 root root   38267 2007-07-30 13:45 usbuhci.mdm
-rwxr-xr-x 1 root root  157727 2007-07-30 13:45 Video.mdm


- I'll also try booting that partition and let you know

---

### Post by rokyersoxoff on 2008-12-05
Well, I finally tried this....the system just hangs when trying to boot sda1

I think part of my problem is that I might not have the correct "repair cd".  Does anyone have any suggestions on where I can find a downloadable & bootable XP repair cd?  I received no XP cds with my Dell laptop purchase ( install, recovery, or otherwise ), which I'm assuming is par for the course nowadays.

Again, any suggestions are welcome.

---

### Post by TeXtonyx on 2008-12-05
You had an existing XP partition and then installed Ubuntu from
the live cd and chose to resize to create room for the Ubuntu
partition, right?

You used the default install which puts grub in the MBR and then
you boot XP from Ubuntu's grub menu.lst, right?

Try to fix this with free Testdisk, rebuild boot sector. 
search for testdisk in the search box, caljohnsmith has given
explicit instructions in the past. I would, but I have to go,
will write more later.

---

### Post by redilyn on 2008-12-05
> **rokyersoxoff said:**
> Well, I finally tried this....the system just hangs when trying to boot sda1

I think part of my problem is that I might not have the correct "repair cd".  Does anyone have any suggestions on where I can find a downloadable & bootable XP repair cd?  I received no XP cds with my Dell laptop purchase ( install, recovery, or otherwise ), which I'm assuming is par for the course nowadays.

Again, any suggestions are welcome.

I suspect it is against forum policy to post links to illegal downloads....

but

Maybe you should try one of the more popular torrent sites to download a working windows xp cd.

---

### Post by TeXtonyx on 2008-12-05
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654) for reference mainly.

[http://aumha.net/viewtopic.php?t=31844](http://aumha.net/viewtopic.php?t=31844)
The XP install disk has something called Recovery Console (RC)
which enables running some basic boot recovery commands.
C:\fixmbr
C:\fixboot
C:\bootcfg /rebuild

It is much easier (if you can boot that far) to have RC as a boot option
-------------------------------------

WindowsXP-KB310994-SP2-Pro-BootDisk-ENU.exe
[boot loader]
timeout=2
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
------------------------------------------

The problem is that laptops are often shipped without an install
cd, just a recovery cd (OS + drivers) which deletes your XP
partition and freshly installs XP and drivers. Microsoft has 
made a rescue/recovery cd for people in this situation for Vista,
but not XP. I don't think there is a way to do a Repair install,
the next option after the repair with RC option on the install cd.

So you can try testdisk and probably manage the fixmbr, fixboot
and bootcfg /rebuild (in that order) commands but to do the 
second option of the XP install cd Repair, you'll need to borrow
an XP install disk. That may work to do a repair. 

XP may not be vital to you, but many dabblers come from Windows
which is still vital to them and try a dual boot with Ubuntu.

I think the XP partition should be resized to make room for Ubuntu
before the live cd Ubuntu install. Then you can still test XP
to see if it works since it remains dominant in the MBR.

Next, when you run the Ubuntu live cd, you can then choose 
'install to largest continuous free space (directed)' - don't 
preformat that unallocated space you just made by resizing -.

So this method doesn't bother the XP installation, it makes
sure you don't overwite the XP partition which you've already
tested to see that it works after the prior resizing of XP.

So next in the live cd install, at Step 7, Advanced, choose to 
install grub to the /boot partition of Ubuntu. 
Because again this leaves XP untouched and bootable. But Ubuntu 
doesn't boot yet, so you can use free Bootpart to make a ubuntu.bin file,
a 512 byte boot sector segment, and it writes to boot.ini automatically. 
Or you can use the dd command to make the 512 bytes, if you use 
it on the same drive. The point is that you and about 14 other
users per month on this forum, don't ever have the problem created
that afflicts many laptop users and some desktop users, no install cd. 
Because grub isn't installed to the MBR, there are
no page after page of experimenting with different menu.lst
entries to get XP to boot again. 60% of Ubuntu users are dual 
boot Windows/Ubuntu users. Meaning most of them look at a
menu.lst and think its a greeting from the Martians. Well, you
are a linux sysadmin and have a leg up on them, but do you think
this is an easy problem to solve? And the problem is so preventable.

---------------------------------------------------

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/NOEXECUTE=OPTIN /FASTDETECT
c:\UbuntuB.bin="Ubuntu"
c:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /CMDCONS
c:\linux.bin="Debian"

-----------------------------------------------

It took me less than a minute to create both *.bin entries and
write them to boot.ini. This isn't just a rant. You may have to
reinstall everything and you will know how to do it. Maybe not,
since you are more sophisticated than the average user with this
problem. I did have another reason for showing you my boot.ini.

"the following error ( "domain <domain_name> is not available")"

When I did the Debian install which is closely related to the
Ubuntu install, it did have a question about entering an IP
address and a domain. It was a Linux fixable question. Does your
laptop belong to a network which has a domain rather than a 
Workgroup. In XP (not Vista) you don't have to logon in a Workgroup.
[Is there any virtualization involved which might access a domain?]
 
With grub in the Ubuntu /boot partition both OS are
standalone and don't conflict with each other. Sometimes putting
grub in the MBR damages the Windows boot sector (testdisk fixes). 

There is a very handy tool called the Super Grub Disk that enables
booting one OS if the other OS is damaged and can't boot both. 
If you don't have an OEM recovery cd, you might have the files
in a hidden partition. Often tapping F11, HP, to boot into it
during setup. You'd better make a backup since it wipes the
XP partition. If you don't have it then you have to call the
manufacture and wheedle them out of one. Or, you can "borrow"
an XP cd which will be easier for RC fixmbr etc. and the next 
Repair option after that. 

Since this problem seriously impacts the user, I think there 
should be a Sticky advising people who dual boot of alternatives.

---

### Post by Herman on 2008-12-05
Originally posted by rokyersoxoff,
> Anyway, my problem is this: I have a dual-boot laptop ( Ubuntu & XP ). I just installed the Ubuntu partition a couple months ago...so I'm still learning my way around. 
XP used to boot up and allow me to login, but I ran into the following error ( "domain <domain_name> is not available" ), after I tried restoring to a previous backup point.Probably it's not a boot loader problem, but a problem with the operating system itself, since it booted fine for two months after Ubuntu was installed and them borked itself from running 'System Restore'.

I'm not familiar with the error message "( "domain <domain_name> is not available" )", that's a new one to me. 
> When I try to boot from my &#8220;Emergency boot CD&#8221; I get the &#8220;...corrupt or missing hal.dll&#8221; error. Not sure if this is maybe a result of installing GRUB ( and it somehow conflicts with boot.ini ) , but I can&#8217;t boot this way. I pulled a good copy of &#8216;hal.dll&#8217; from a microsoft website and placed it in the appropriate directory just in case. Same problem. I have never heard of any conflict between GRUB and boot.ini before.
GRUB simply chainloads the Windows boot loader NTLDR at the Windows boot sector, so I don't see how it could possibly conflict with boot.ini. 
'Chainload' means it boots the other boot loader, basically, so it is really NTLDR that is doing the booting.
I have seen a problem when there are un-needed or wrong 'map' commands in the booting stanza for windows in Ubuntu's /boot/grub/menu.lst file. That would have shown up right away though, not two months later, and usually only applies to computers with more than one hard disk.

Here's what I have for &#8220;...corrupt or missing hal.dll&#8221; error, if it's any help, [hal.dll is missing or corrupt.]("http://users.bigpond.net.au/hermanzone/p15.htm#hal.dll_is_missing_or_corrupt")

> Since this problem seriously impacts the user, I think there 
should be a Sticky advising people who dual boot of alternatives.Hmmm, I recommend GRUB, but I have howtos for a few alternatives already listed in my website, you can help yourself to those.
NTLDR is a bit rough and primitive, it's the last method I would recommend to anyone, I don't even list that one. although I know how to do it. It would be better to use EasyBCD instead, if you want to boot from Windows.
I think you can use EasyBCD in Windows XP, although it was developed mainly for Vista.
EasyBCD is way more advanced and much more convenient for the user than manually messing with NTLDR and boot sector images.  [EasyBCD]("http://ubuntuforums.org/EasyBCD").

However, like said earlier, I still feel that it's probably not a boot loader problem, (if I'm understanding the original post correctly).
> the XP partition actually boots up.  The real problem is &#8220;logging in&#8221;.

Regards, Herman :)

---

### Post by Herman on 2008-12-05
Originally posted by Temüjin,
> I, like you, believed that there HAD to be a way to fix it without reinstalling, but you have to remember that this is Windows we're talking about. It doesn't always make sense and I've found the following saying to be true the more and more I do tech support: ("he who does not understand UNIX is doomed to reinvent it ... poorly"). In hindsight, I just wasted a lot of time "pissing in in the wind". A full reinstall was needed.I think Temüjin will be correct.
> I think part of my problem is that I might not have the correct "repair cd". Does anyone have any suggestions on where I can find a downloadable & bootable XP repair cd? I received no XP cds with my Dell laptop purchase ( install, recovery, or otherwise ), which I'm assuming is par for the course nowadays.First, try contacting Dell for a Windows XP CD and see if they will help you. 
If that doesn't work then you might be able to do [THIS]("http://ubuntuforums.org/showpost.php?p=5901952&postcount=5").
Or do as redilyn said and go download one maybe.

---

### Post by TeXtonyx on 2008-12-05
OP: the following error ( "domain <domain_name> is not available") 
after I tried restoring to a previous backup point.
---------------------------------------
Herman wrote:
Probably it's not a boot loader problem, but a problem with the 
operating system itself, since it booted fine for two months after
Ubuntu was installed and them borked itself from running 'System Restore'.

TeX: I agree, though perhaps it was an F8, last known good configuration.
The problem is most likely the reason why he ran System Restore in
the first place, perhaps he could describe that.

Using testdisk was probably not very good advice even though OP
has very limited options. He has no XP install cd so has to
struggle just to run fixmbr, fixboot and bootcfg/rebuild. And,
those commands don't seem that likely to fix the problem. Maybe
the second option Repair, offered by the XP install cd would 
fix it since it does more, but he doesn't have that cd. I think
there is a better than 50% chance that he will have to reinstall
XP which means that grub will need to be reinstalled. I think
that it is better to reinstall grub in the /boot partition,
which is why I gave a lot of advice about that.

Another reason that I didn't mention is troubleshooting. I've
seen a few dozen threads that go on 3 to 5 pages, trying new
entries in menu.lst, which all fail and then the conclusion is
reached that the problem is probably Windows. This approach seems
as wasteful as tits on a boar hog. If Windows remains in place in
the MBR, you can either boot to Windows or not. If you can boot
to Windows directly but not from grub menu.lst then the problem
is with grubs menu.lst. A 3 minute determination rather than a
laborious trial and effort approach that lasts 3 days or so.
The time management for troubleshooting for the, let's see if it
is a grub error first method, is very inefficient and frustrating
for the new user.
--------------------------

Herman wrote: NTLDR is a bit rough and primitive, it's the last 
method I would recommend to anyone, I don't even list that one. 
although I know how to do it. It would be better to use EasyBCD 
instead, if you want to boot from Windows.

TeX: 
 meierfra, who imo, is fairly expert had this to say:
"This is different if you use bootpart, bootpart does not create
a copy of the boot sector. Instead it stores the location of the 
boot sector. So bootpart only needs to be updated if you resize 
a partiton, but not after reinstalling grub. EasyBCD actually 
uses bootpart, so the same is true for EasyBCD."

TeX: This is why Bootpart works for booting across two drives,
whereas the dd method, only works on the same drive. Before Easybcd
was invented, the manual way for adding a Linux OS to Vista used
dd for a 512 bytes and installed Linux in the /boot partition.
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)
"Step 1 &#8211; Install GRUB on the Linux partition (outside of MBR)
As Windows Vista will replace the Master Boot Record (MBR) with 
its own, we need to relocate GRUB elsewhere by running grub-install
with the Linux partition as a parameter.

Step 2 &#8211; Get a copy of Linux boot sector
We will need to instruct Windows Boot Manager how to boot correctly 
Linux using Linux boot sector, which we will extract using dd."

TeX: So Vista before Easybcd used the bcdedit commands to add
the Linux entry to the database with the dd produced 512 bytes.
But Easybcd can boot across two drives and dd can't. The point 
I'm making is that Easybcd uses the same engine as Bootpart,
the difference is a GUI.
C:\bootpart <enter>
Physical number of disk 0 : 56d9f43b
 0 : C:* type=7  (HPFS/NTFS), size= 64974861 KB, Lba Pos=63
 1 : C:  type=5  (Extended), size= 15028807 KB, Lba Pos=130769100
 2 : C:  type=83   (Linux native), size= 14354046 KB, Lba Pos=130769163
 3 : C:  type=5   (Extended), size= 674730 KB, Lba Pos=159477255
 4 : C:  type=82    (Linux swap), size= 674698 KB, Lba Pos=159477318

C:\bootpart 2 ubuntu.bin Ubuntu <enter>
writes ubuntu.bin to C:\ and adds an entry to boot Ubuntu in boot.ini

------------------------------

"I think you can use EasyBCD in Windows XP, although it was developed mainly for Vista.
EasyBCD is way more advanced and much more convenient for the user than manually 
messing with NTLDR and boot sector images. EasyBCD."

TeX: Yes, you can use Easybcd in XP. I just tested it. It takes me 
12 seconds (I have a dos icon on the desktop) to add ubuntu.bin 
to C:\ and write to boot.ini. It takes Easybcd about 12 seconds
just to load, and another 12 seconds to navigate the menu to
Linux and find the dropdown box and choose the right entry.
The instructions for Bootpart are easier and simpler to follow.

So Bootpart is both faster and more intuitive than Easybcd and
on XP they both use boot.ini and ntldr. There is no messing 
around manually with ntldr and boot sector images. The both do 
that automatically. It's true you have to type
C:\bootpart 2 ubuntu.bin Ubuntu <enter> which is faster than 
the time it takes Easybcd to open. They both use the bootpart
engine (according to meierfra) not the dd functionality although
both methods produce 512 bytes. 

Easybcd is more advanced, but who needs it? Maybe those who
don't know how to add a Windows second boot entry. Bootpart
is simpler for a new user. I don't believe you actually tested
both methods to compare them before you offered your opinion.
I agree with caljohnsmith that Dos4grub is smarter, but the
new user has to be smarter to use it. 

hal.dll and ntldr errors are common in Windows and cover a
multitude of possible causes, having nothing to do with those
two files. A somewhat clever user, thinks that he needs to copy
a "good" ntldr to replace the "bad" ntldr. Almost always, the
ntldr or hal.dll is already there. I never have any trouble with
ntldr and bootpart unless I resize a partition and then I have
to run bootpart again. When linux or gparted resizes the Windows
partition it can be tough to fix unless you know about testdisk.
When grub writes to the MBR it sometimes damages the Windows
boot sector. Those are definite downsides that never have to
occur. I asked what the advantages of grub in the mbr were and
I was told it could do searching (like grub4dos) and the claim
which was never substantiated that stage 1.5 grub provided some
error messages that were not available for stage2 because putting
grub in the /boot partition eliminated stage 1.5. I asked for
evidence and was shown some 1.5 error messages. That has nothing
to do with showing that the error messages are not available at
stage2, so is no evidence for an advantage for grub. Why use grub
when it obviously causes problems for so many new users, and when
more than 50% of Ubuntu new users are dual booting Windows users?

I've never seen a consensus of expert opinion which states that
ntldr is unstable or unreliable. ntldr and bootpart keep working
reliably unless one messes with the partition or the OS. Just
like Linux using grub and grub is not easy to for new users to fix.

---

### Post by TeXtonyx on 2008-12-05
Well, Herman, I see you've had this debate before with Juan Largo. 
[http://ubuntuforums.org/archive/index.php/t-342663.html](http://ubuntuforums.org/archive/index.php/t-342663.html)

Herman: "If someone is frightened by the prospect of something 
happening that they don't understand when their MBR is upgraded, 
they can back up their MBR from any Linux LiveCD with a simple 
'dd' command if they like." 

TeX: Yes, this is true. But, how many new users to Ubuntu coming 
from Windows would know how to take advantage of this advice, apriori.

Herman:"The 'dd' command used to do that is similar to the 'dd'
command they would need to use to copy Grub's stage1 from the 
Linux partition anyway, so it would not require any extra work 
or learning than the NTLDR method."

TeX: Again this is true, but with Bootpart you can avoid the
typing errors of dd in both instances; bootpart is simpler.
There is almost no extra effort involved in learning Bootpart,
certainly less than learning Easybcd. Learning dd isn't needed.

Herman:"Actually, it would be safer, as editing the boot.ini 
file in Windows imperfectly would also render Windows 
unbootable. In fact, it would put both operating systems out 
instead of only one."

TeX: Editing boot.ini is done automatically with Bootpart. About
the only error that matters is getting the partition number wrong
which temporarily prevents Ubuntu from booting, but not XP. And
if XP is out of service, then Super Grub Disk boots Ubuntu.

Herman:"Editing Grub's device map, which is very simple, should 
sort out your IDE/SATA problem. Editing Grub's device.map 
(http://users.bigpond.net.au/hermanzone/p15.htm#device.map)"

TeX: First of all the new user has to know that IDE/SATA is a
problem for Ubuntu but not Windows. Then the new user is supposed
to know that one can fix that by editing Grub's device.map and
that the information for how to do this is within his grasp. I
see nearly every new user not even use the Search function at
the forum which has contains the answers for their questions
most of the time. I think they are forced into the position where
they are forced to ask for help. I think it is a far superior
method to not create the problem that they ask for help about
in the first place which means keeping the OS booting independent.

I really don't get the impression that you worked as a computer
technician and learned the limitations of most Windows users,
and they represent most of the Ubuntu users, 60% dual boot.

The problem is not that my idea for a Sticky informing new dual
booters, Windows/Ubuntu - that they ought to install grub to the
/boot partition - isn't a good idea, but that most new users 
wouldn't read it. I think the best effort is to make the live cd
make that choice/option more obvious, like some other Linux OS's
do, rather than obscuring the choice under Step 7, Advanced.

It does not seem to me that the Powers are weighing what is best
for the majority of new users, but abiding by some Linuxcentric
notion that having grub in the mbr instead of windows is a 
measure of Ubuntu's manliness and virility, it's too philosophical
or idealistic or (male) chauvinistic) rather than practical.

---

### Post by thomas228 on 2008-12-05
> **TeXtonyx said:**
> OP: the following error ( "domain <domain_name> is not available") 
after I tried restoring to a previous backup point.
---------------------------------------
.
.
.
 I think the best effort is to make the live cd
make that choice/option more obvious, like some other Linux OS's
do, rather than obscuring the choice under Step 7, Advanced.

It does not seem to me that the Powers are weighing what is best
for the majority of new users, but abiding by some Linuxcentric
notion that having grub in the mbr instead of windows is a 
measure of Ubuntu's manliness and virility, it's too philosophical
or idealistic or (male) chauvinistic) rather than practical.

Instead of writing such confusing recommendations why not be a little more clear and (remembering the COC) keep the thread a little less inflammatory.

Tom

---

### Post by TeXtonyx on 2008-12-06
> **thomas228 said:**
> Instead of writing such confusing recommendations why not be a little more clear and (remembering the COC) keep the thread a little less inflammatory. Tom

 Originally Posted by TeXtonyx  View Post
OP: the following error ( "domain <domain_name> is not available")
after I tried restoring to a previous backup point.

-----------------

[http://support.microsoft.com/kb/244671](http://support.microsoft.com/kb/244671)
"When you attempt to log on to a computer, you may receive the 
following error message immediately after you type your user 
name and password 

System cannot log you on now because domain Computername is not 
available. where Computername is the name of the local computer 
you are trying to log on to."

------------------

If you read more of that webpage above you'll see that all three 
resolutions wants to edit the Registry. That requires a Recovery
Console which comes with an XP install cd. OP which stands for
Original Poster = rokyersoxoff said he doesn't have such a cd.
So my post to OP encouraged him to try to get a substitute for
the Recovery Console; Herman suggested another method. There is
more than one reason why I dont think the RC method will work:

----------------
Somebody with similar problem wrote:

"The MS solution didn't work... here is my update so far.. still
nothing. I have my install CD, and have been able to bring up 
the recovery console. I have even tried to reinstall Win XP on 
top of the existing OS so that I can start from new without 
losing any of my files, essentially "repairing" whatever is 
causing this. That did not work either. Every time I'd get to 
the license agreement, I could only scroll up and down the page,
but press F8 to accept (as it instructs) never works.

This has always been a home computer and has never been connected
to a network of any sort. I've never had this problem with the 
machine."

----------------------------------------
This example is pretty much exactly OP's error message.
[http://support.microsoft.com/kb/324141](http://support.microsoft.com/kb/324141) "Changing the password 
on a locked-out account generates a "domain not available" message"

"If a user tries to change their password on an account that is 
locked out and has the User must change password at next logon 
attribute set, the user receives the following error message: 
The system cannot change your password now because the domain 
domain_name is not available.

This error message is misleading because it does not distinguish 
between the actual situation (a locked-out account) and true 
connectivity problems."

TeX: It doesn't seem like it would be a true connectivity issue
because he can logon to Ubuntu. Anyway there is a suggested fix

"Windows XP
A supported hotfix is available from Microsoft. However, this 
hotfix is intended to correct only the problem that is described in this article." 

The problem with these solutions is that there are often a dozen
of them and you have to try them one at a time. Maybe you get
lucky and win at the sixth try. The reason that the OP tried
a System Restore might shed some light on why this error developed.
Did he get the same error before he tried System Restore?

[http://www.arsgeek.com/2008/02/27/use-your-ubuntu-partition-to-fix-a-corrupt-registry-on-a-windows-xp-partition/](http://www.arsgeek.com/2008/02/27/use-your-ubuntu-partition-to-fix-a-corrupt-registry-on-a-windows-xp-partition/)

This suggests doing a System Restore to fix a corrupt registry.
But OP reports the problem symptom manifested after a System Restore.

"Instead of writing such confusing recommendations why not be a little
more clear and (remembering the COC) keep the thread a little less 
inflammatory."

TeX: I don't think I wrote any confusing recommendations. Your
quotes were put together out of two different posts. Neither of
the posts were addressed to the OP or offered the OP recommendations.

Both posts were pointed at Herman. I quoted what the OP wrote
to support the conclusion that it was probably not a bootloader
problem, agreeing with Herman. I had previously recommended
Bootpart to the OP. Herman contested that idea. My response to
Herman was about why it was a good idea. Indirectly, it was
relevant to my prior recommendation to the OP, but there was no
recommendation addressed to the OP or instructions to the OP
in that post. That post justified to Herman, and to the OP, if
he read it, why I thought my recommendation was warranted.

The other post which you quoted from, starts with "Well, Herman"
and it was about how to avoid errors which were generally related
to OP's, but not actually specific to OP's situation. I don't
see how one can offer a criticism of an idea without it having
the implication that the idea is stupid or bad. Certainly that
can be taken as inflamatory. Is that reason to avoid criticism?
I don't think so, I think it is better to be honest. There are
a number of experts who think grub should go in the /boot partition
and the guy mentioned, Juan Largo, was agreeing with that view,
while Herman was disputing it. I agree with Juan Largo et al.
I didn't have to use intellectual words to criticize Herman's
position, I could have said what I meant. I am not here to live
up to other people's non-adult expectations, nor do I have any
reason to value such opinions or expectations. I have no idea what 
was unclear about my comments to Herman, or my others to the OP. My 
posts were not all exactly about the same thing, that's how threads work.

Just to be clear, I mean Herman is an adult and has a great deal of
knowledge about dual booting/computers, but, none of us are perfect. :-)

---

### Post by TeXtonyx on 2008-12-06
> **rokyersoxoff said:**
> Well, I finally tried this....the system just hangs when trying to boot sda1

I think part of my problem is that I might not have the correct "repair cd".  Does anyone have any suggestions on where I can find a downloadable & bootable XP repair cd?  I received no XP cds with my Dell laptop purchase ( install, recovery, or otherwise ), which I'm assuming is par for the course nowadays.

Again, any suggestions are welcome.

Since you have data you want from the XP partition, I think that
this MS KB fix offers your best chance that I've seen so far and
is worth trying. The KB fix is available without paying although
you have to register with your email in order to download it.
The download link is at the top of the page.

-------------------------------------

This example is pretty much exactly OP's error message.
[http://support.microsoft.com/kb/324141](http://support.microsoft.com/kb/324141) "Changing the password
on a locked-out account generates a "domain not available" message"

"If a user tries to change their password on an account that is
locked out and has the User must change password at next logon
attribute set, the user receives the following error message:
The system cannot change your password now because the domain
domain_name is not available.

This error message is misleading because it does not distinguish
between the actual situation (a locked-out account) and true
connectivity problems."

-----------------------------------------------

I did look at some of the files in the KB fix and saw one, kerberos
which I'm pretty sure deals with authentication. I wasn't able
to read how to apply the KB fix, so I hope the instructions are
included in the KB fix download. Or you could ask on an XP forum.

"NOTE: This update affects user interface behavior on the client
computer on which the user logs on. However, you must also apply
the hotfix on domain controllers." 

That NOTE does not seem like good news since you said you had
never belonged to a domain. What did you do that caused you to 
try System Restore that eventually led to the error message 
you received about 'domain'. Perhaps fixing that problem will
fix the current symptom/problem -> connectivity. Did you add
any hardware/software with unsigned drivers just before this?

---

### Post by thomas228 on 2008-12-06
Hi Tex

Post #19 and post#20 were quite clear and should give the original OP some hope.

If all the OP is able to do is hope for some data recovery is there not a way he can use the liveCD to at least look at the windows' xp data or does he have to be in windows to install the requiired ntsf/ext interface?

My remarks regarding inflammatory were only in regards to the last paragraph of the last referenced post.  I think you have too much to contribute to this forum to foolishly risk sanction by someone getting insulted.

Thanks
Tom

---

### Post by TeXtonyx on 2008-12-06
> **thomas228 said:**
> Hi Tex

Post #19 and post#20 were quite clear and should give the original OP some hope.

If all the OP is able to do is hope for some data recovery is there not a way he can use the liveCD to at least look at the windows' xp data or does he have to be in windows to install the requiired ntsf/ext interface?

My remarks regarding inflammatory were only in regards to the last paragraph of the last referenced post.  I think you have too much to contribute to this forum to foolishly risk sanction by someone getting insulted.

Thanks
Tom

Well, OP stated he was a Linux sysadmin so he surely knows that
one can mount partitions. The problem is that you cannot mount
a Windows partition from Ubuntu unless the Windows system has
been shut down cleanly, you get an error message. I think he
can still boot to Ubuntu and he could do it from there. One can
try to force the mount of the partition.. it seems so unlikely
that a sysadmin wouldn't think of that. That is why I didn't
suggest it, though I have in other threads with new users.

My spiritual guidelines emphasize honesty, which means airing
criticism and not stifling dissent. If the shoe fits, wear it.
What Subject: line is the number one problem? I think there are more
grub errors reported than any other error reported on this forum.

I want to reduce the number of grub error reports which come from
Windows/Ubuntu dual booters which has roots in the install policy.
The decision made about how to present install choices to the new
user. I think the current policy is weighted by prioritizing 
claims of how many Windows dabblers try Ubuntu first for its ease 
of installation. The result is that I see a few hundred
hours a month wasted on fixing grub errors that never needed to be.
The last thread I was thanked in by a new user (so was #1caljohnsmith)
was one where the user already had the Windows install cd and
just had to run Recovery Console. To get to that stage went
into the fifth page, over 40 posts. There is at least a dozen
of these threads per month that go about 30 posts. 

My point is that fixing these unnecessarily created grub problems
due to installation choices shaped by Policy takes a lot of time
and is frustrating for the new user. It doesn't do anything to
support a good first impression of Ubuntu, the pent-ultimate goal.
So the Policy is not aligned with the Spirit of Ubuntu. It has
more to do with old guard *nix icons and their personality quirks,
who are in control and shape decisions. When I list the 
objective advantages of installing grub into the /boot partition 
for dual booters of Windows/Linux, there is hardly anything to 
balance it on the other side of the scale, really minor stuff.
 
The Policy is being set by a different agenda. The policy varies
between different Linux OS's. If it were an objectively good
practice to install grub in the MBR in dual booting Windows/Linux
systems, the grub install choice would be much more uniform, to
obscure an alternative grub install location, and use just the MBR.

I think what is best for the user should determine policy for Ubuntu,
that's what its name means. (new) People come first, not *.centrism
Anyway, that is why I used the word philosophical in the other post.

---

### Post by rokyersoxoff on 2008-12-06
Wow...thanks for all the replies...I truly do appreciate them all!

Let me clarify a couple things, since some questions have been raised:
- I am currently a UNIX Sysadmin ( not Linux...I'm fairly new to Linux ), though there is a lot that translates.  As such, I am familiar with mounting filesystems, partitions, etc...
- The last time I was successfully running XP, I did run a system restore ( from the GUI in XP ); Every effort to log on since has yielded the "domain is not available" error
- My laptop has always been a personal home PC ( ie. never part of a domain )
- I purchased this laptop from Dell about 2.5 years ago.  I did not receive any "install" or "recovery" CD with my purchase ( bought it brand new ).  This is one of the most frustrating things about this situation.
- I realize that there are some people out there that "acquire" PC's and then attempt to "break in", but this is not the case here.
- Since I purchased this machine a couple years ago, the support agreement has expired.
- My end goal is to convert to Linux entirely, but for now windows is a necessary evil ( as it were )
- I truly don't believe that there is any issue "booting" XP at this point, as it boots up fine.  The issue is getting past the login error.


I will be going through all of these suggestions over the next few days and trying them out....but there's a lot of info to sift through here...with the limited and sporadic time I have to work on this.  Again, I truly do value all of the input and once I have tried your suggestions I'll provide more feedback.

---

### Post by rich1939 on 2008-12-06
> **rokyersoxoff said:**
> Well, I finally tried this....the system just hangs when trying to boot sda1

I think part of my problem is that I might not have the correct "repair cd".  Does anyone have any suggestions on where I can find a downloadable & bootable XP repair cd?  I received no XP cds with my Dell laptop purchase ( install, recovery, or otherwise ), which I'm assuming is par for the course nowadays.

Again, any suggestions are welcome.

If it's a Dell computer, there is probably a Recovery partition. You could try to boot and press CTRL-F11 during the 3-second pause when the Dell logo appears on the top of the screen, before Windows boots.

**BEWARE**: This *might* erase the entire contents of your hard drive, as the Recovery Partition is intended to put your computer back into the same state as when it was initially sent to you. This would, in effect, get rid of all of your currently installed applications, as well as your data, so **BEWARE!**

---

### Post by TeXtonyx on 2008-12-06
Something caused the login symptom, that's not the problem.
That is why I ask you about why you needed to run System Restore.
I think that that the symptom/problem that caused you to System
Restore has a good chance at being involved in the present problem.

It is like those missing hal.dll errors. Hal.dll is almost never
missing, that a broad error report that covers many things. Some
thing doesn't run and it sends an error message, there could be
two dozen reasons for a missing hal.dll (for instance). If you
remember the problem that led you to run System Restore and its
error message, it might correlate to the current error message
after a search. Maybe a connectivity issue, like a nic wireless
card driver or a new router and its driver, as a for instance. 
If you never joined like a corporate domain, or VPN? then it
doesn't mean that kind of domain. I'm reading about Domain Name
Servers at the moment. (maybe changed ISPs) It's just very likely
connected to a reason why one needs System Restore, but not certain.

Have you tried to force the mount of the XP partition from Ubuntu 
so that you could rescue some data files. I was just thinking could 
System Restore have removed some driver that you installed recently?

---

