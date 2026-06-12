---
title: "Ubuntu Edgy Hosed My USB Hard Drive"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by Unoone on 2007-03-27
I have a USB hard drive that I have shared between Windows and Ubuntu for months. Today I plugged the USB drive into Ubuntu and at first I noticed that some of the folders were locked. I tried to "chmod -R 0777" /folder. But no change. Ubuntu let me unmount the drive so that I could hook it up to a machine running Windows. The entire drives folders are now unreadable in Windows. I then unmounted it from Windows and hooked it back up to Ubuntu. It wouldn't auto mount. So I did a fdisk -l to check the USB drive out. It shows, "Disk /dev/sda doesn't contain a valid partition table". 

What the freak just happened here!? :( 

The USB drive is in perfect condition. I did a software check in Windows and the hard drive is ok. What's up with this? BTW, I'm using Edgy. Thanks for your help.

Man, I was just about to toss the buggy Edgy and install Feisty. I had to go and check a file on my USB hard drive. I'm am so hosed.:mad:

---

### Post by kidders on 2007-03-27
Hi there,

The best way to find out what happened is to examine your system logs. It would be interesting to find out what turns up.

It's probably most likely that whatever went wrong happened *before* you noticed the problems you mentioned with Ubuntu. Did you do anything odd the previous time you used the disk? (Perhaps an unclean dismount, etc.) Other possibilities include exposure to strong magnetic fields, and hard falls. Depending on what OS you were using the last time you successfully used the disk, it's also possible that a serious software malfunction (eg a kernel panic) could have caused your problem.

> **Unoone said:**
> Today I plugged the USB drive into Ubuntu and at first I noticed that some of the folders were locked.This sort of thing is typical of Linux. If it notices problems with a filesystem, it often refuses to allow write access to it, so it doesn't wind up making things any worse.

> **Unoone said:**
> I tried to "chmod -R 0777" /folder.What filesystem were you using on the USB disk?

> **Unoone said:**
> Man, I was just about to toss the buggy Edgy and install Feisty. I had to go and check a file on my USB hard drive. I'm am so hosed.:mad:Feisty is in beta... if you want to stay away from bugs, installing it is the *last* thing you should do.

**Edit:** I forgot to mention the most important thing...

Don't make any further attempts to write to your USB disk, until you have a clearer idea of what's gone wrong. If you try to mount it, mount in read only mode. Also, it would be worth taking an image of its contents now, in case a future repair attempt goes pear-shaped.

---

### Post by s0cket on 2007-03-27
Have you tried going into Disk Management in Windows and try doing a file system scan?  I do the exact same thing you do and can't say I've experanced anything like that.

Also check your dmesg for seek errors and such.  Might be hardware related.

---

### Post by Unoone on 2007-03-27
Thanks for your responses.

> **kidders said:**
> Hi there,

The best way to find out what happened is to examine your system logs. It would be interesting to find out what turns up.

It's probably most likely that whatever went wrong happened *before* you noticed the problems you mentioned with Ubuntu. Did you do anything odd the previous time you used the disk? (Perhaps an unclean dismount, etc.)

I am always careful how I log out of Ubuntu, I unmount my USB drives every time. I have never this issue before while using Ubuntu. My logs look ok and don't appear to 
relate to this issue.

> **kidders said:**
> 
This sort of thing is typical of Linux. If it notices problems with a filesystem, it often refuses to allow write access to it, so it doesn't wind up making things any worse.

What filesystem were you using on the USB disk?

I always use Fat32 partitions on the drive that I share between Linux and Windows. Recently I was having problems with Edgy where root permissions were randomly assigned to my fat32 dives on various different Unbuntu PC installs. I didn't say much about it here. In fact one of my drives was making a clicking noise one day. I logged into that PC and realized that the data download from my FTP site had stopped. Once again root had taken over my fat32 partition permissions randomly. I took the drive out of Ubuntu Edgy and tested in a Windows PC. It was fine. Its been fine ever since, no more clicking and data drop-offs.

In researching this recent problem of erratic root permission hijacks I learned something new. I seems that "root" can't give any "real" "user" write permissions to fat32 drives in Linux. So to fix this issue with my permanently mounted fat32 drive I stopped manually mounting permanently installed fat32 drives in Ubuntu. Instead of setting up a fat32 drive and using "sudo mount -a" I just restart the PC and let the fstab settings handle the mounting. 

I never experienced this root permissions issue on my other Dreamlinux installs. My user permissions stay put from the time that I install the Linux OS. This crazy root stuff effects my cdr/dvd+r backups. Some of the data that I have written on optical disk is only readable now on my current Edgy install. Also in Edgy and Feisty test Firefox has to have manual permissions setup to download files to my fat32 drives. Otherwise I get a -0- data file. Dapper doesn't appear to do any of this stuff on my Ubuntu installs in my two other PC's. This root permission hijack stuff appears to be an Edgy issue though not a Feisty one.

> **kidders said:**
> 
Feisty is in beta... if you want to stay away from bugs, installing it is the *last* thing you should do.

I have used Linux Distros from Knoppix, Mandrake to Gentoo based. I have never had any trouble like this on any Ubuntu install until Edgy. That Feisty Firefox issue of needing to assign manual fat32 drive write permissions to Firefox for data file downloads worries me a bit. I'll still test it out.

> **kidders said:**
> 
**Edit:** I forgot to mention the most important thing...


Don't make any further attempts to write to your USB disk, until you have a clearer idea of what's gone wrong. If you try to mount it, mount in read only mode. Also, it would be worth taking an image of its contents now, in case a future repair attempt goes pear-shaped.

I think I have to put this drive on ice until I have time to worry about it. Like I said this "root" permission craziness was occurring on other PC's like my new Core 2 Duo PC builds with Ubuntu Edgy setups. As a Linux user I don't treat Ubuntu as my stable choice of a Linux OS right now since Edgy. And Edgy is supposed to be stable. For me Breezy was my most stable Ubuntu/Linux experience. I left Dapper and Upgraded to Edgy because it fixed my SMP issues. Nothing major just minor issues. It's seems in my case Edgy was just a disaster waiting to happen.  My Edgy issues had not been as bad as others experienced. And up until this USB issue I could live with the permission wackiness. I don't know what's up here. 

I use Dreamlinux on my other PC's but it's layout is not as good as Ubuntu. I mean seriously if one just installs Ubuntu and only uses Ubuntu with ext3 partitions, none of the fat32 drive stuff I think that things will be pretty much perfect. I can't work that way right now. I need to hook up with Windows for my work.

---

### Post by Unoone on 2007-03-27
> **s0cket said:**
> Have you tried going into Disk Management in Windows and try doing a file system scan?  I do the exact same thing you do and can't say I've experanced anything like that.

Also check your dmesg for seek errors and such.  Might be hardware related.

The USB drive is in perfect condition hardware wise. I'm just thinking at Edgy is not serving my needs anymore  as a production ready Linux OS. I have 7 PC's available to me and have run Edgy on all of them. From a Gateway athlon 64 4200, newer Core 2 Duo's, down to a P3 800. All of these PC's when running Edgy were effected by the crazy root permission hijacking of my internal fat32 drives. The fat32 drives are fine in Windows and other Linux OS's like the current Dreamlinux. I don't know what it is. Maybe it's the way that I personally use Ubuntu up until Edgy that fouls things up. But it's the way that I have used Ubuntu since Hoary so........... Up until now my Ubuntu experience has been ok. The main hardware issues I had were with my Nvidia cards. Those Nvidia issues were easily resolved.

I don't know....

---

### Post by kidders on 2007-03-27
Hmm...

It's important to remember that FAT filesystems are archaic, and don't support permissions of any kind. Ownerships & permissions are decided and imposed on a filesystem-wide basis, based on parameters provided at mount time.

Issues involving apparently random permissions assignment are due to misconfiguration, rather than any kind of problem or fault. Where non-root users are denied full access to data stored on FAT filesystems, this is typically a result of Linux defaulting to a safe configuration, for lack of an explicit instruction to do otherwise. Essentially, unless your dmesg specifically says Ubuntu is mounting a filesystem in read only mode, permissions problems with FAT are not indicative of a problem that could cause any kind of harm.

You do however seem to be suggesting that your permissions occasionally change *after* you've mounted and started using a filesystem. That should _never_ happen, and can really only be caused by a problem with Ubuntu itself, or your USB device. Either would be described in your system logs though.

> **Unoone said:**
> I mean seriously if on just installs Ubuntu and only uses Ubuntu with ext3 partitions, none of the fat32 drive stuff I think that things will be pretty much perfect.You have plenty of choices, really. Ext3 is just one.

---

### Post by Unoone on 2007-03-27
> **kidders said:**
> Hmm...

You do however seem to be suggesting that your permissions occasionally change *after* you've mounted and started using a filesystem. That should _never_ happen, and can really only be caused by a problem with Ubuntu itself, or your USB device. Either would be described in your system logs though.

You have plenty of choices, really. Ext3 is just one.

As far as Ext3 partitions, some of the data that I back up with my DVD burner from my Ext3 partitions in which I am the full owner is locked. Most of the data is fine. But some of the folders on my data DVD's are not accessible for read access outside of my Ubuntu Edgy system. Since installing Edgy I switched back to using fat32 partitions for backing up data. In this way I seem to have more control over my saved data in all cases. 

Maybe there is a change is the way Ubuntu Edgy and beyond handle permissions that is a bit out of the norm from other Linux Distros? I remember back when I used Mandriva I could choose system wide user global permissions from a configuration interface at install time. The permission levels were something like Paranoid, Medium and Standard. The these permission setting would stay put. Is there a way to do this in Ubuntu Edgy+ at install time other than messing around with flaky permissions later on after the system install of internal hardware? Maybe the standard installed user permission settings are not enough anymore for basic PC use like they were in previous Ubuntu versions.

---

### Post by Unoone on 2007-03-27
Ok I pluged in USB drive into Ubuntu and Ubuntu seemed to recognize it again. I didn't touch anything on it yet here is the fdisk -l info -

```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24792   199141708+   c  W95 FAT32 (LBA)
```

And my dmesg output -

```
[17239579.092000] usb 5-7: new high speed USB device using ehci_hcd and address 4
[17239579.224000] usb 5-7: configuration #1 chosen from 1 choice
[17239579.908000] usbcore: registered new driver libusual
[17239580.048000] Initializing USB Mass Storage driver...
[17239580.048000] scsi2 : SCSI emulation for USB Mass Storage devices
[17239580.048000] usb-storage: device found at 4
[17239580.048000] usbcore: registered new driver usb-storage
[17239580.048000] usb-storage: waiting for device to settle before scanning
[17239580.048000] USB Mass Storage support registered.
[17239585.048000] usb-storage: device scan complete
[17239585.100000]   Vendor: Maxtor    Model: OneTouch II       Rev: 023g
[17239585.100000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17239585.188000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17239585.244000] sda: Write Protect is off
[17239585.244000] sda: Mode Sense: 24 00 00 00
[17239585.244000] sda: assuming drive cache: write through
[17239585.300000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17239585.352000] sda: Write Protect is off
[17239585.352000] sda: Mode Sense: 24 00 00 00
[17239585.352000] sda: assuming drive cache: write through
[17239585.352000]  sda: sda1
[17239585.376000] sd 2:0:0:0: Attached scsi disk sda
[17239585.392000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17239586.124000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17239734.172000] FAT: Filesystem panic (dev sda1)
[17239734.172000]     invalid access to FAT (entry 0x317e6400)
[17239734.172000]     File system has been set read-only
[17240185.144000] UDF-fs: No VRS found
[17241078.816000] UDF-fs: No VRS found
[17241078.848000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17241078.852000] ISO 9660 Extensions: RRIP_1991A
[17243854.876000] usb 5-7: USB disconnect, address 4
[17263180.356000] cdrom: This disc doesn't have any tracks I recognize!
[17269207.648000] usb 5-7: new high speed USB device using ehci_hcd and address 5
[17269207.780000] usb 5-7: configuration #1 chosen from 1 choice
[17269207.780000] scsi3 : SCSI emulation for USB Mass Storage devices
[17269207.780000] usb-storage: device found at 5
[17269207.780000] usb-storage: waiting for device to settle before scanning
[17269212.780000] usb-storage: device scan complete
[17269216.528000]   Vendor: Maxtor    Model: OneTouch II       Rev: 023g
[17269216.528000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17269216.608000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17269216.664000] sda: Write Protect is off
[17269216.664000] sda: Mode Sense: 24 00 00 00
[17269216.664000] sda: assuming drive cache: write through
[17269216.716000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17269216.772000] sda: Write Protect is off
[17269216.772000] sda: Mode Sense: 24 00 00 00
[17269216.772000] sda: assuming drive cache: write through
[17269216.772000]  sda: unknown partition table
[17269216.796000] sd 3:0:0:0: Attached scsi disk sda
[17269216.796000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17271201.788000] usb 5-7: USB disconnect, address 5
[17271207.572000] usb 5-7: new high speed USB device using ehci_hcd and address 6
[17271207.708000] usb 5-7: configuration #1 chosen from 1 choice
[17271207.708000] scsi4 : SCSI emulation for USB Mass Storage devices
[17271207.708000] usb-storage: device found at 6
[17271207.708000] usb-storage: waiting for device to settle before scanning
[17271212.708000] usb-storage: device scan complete
[17271212.764000]   Vendor: Maxtor    Model: OneTouch II       Rev: 023g
[17271212.764000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17271212.820000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17271212.872000] sda: Write Protect is off
[17271212.872000] sda: Mode Sense: 24 00 00 00
[17271212.872000] sda: assuming drive cache: write through
[17271212.928000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17271212.984000] sda: Write Protect is off
[17271212.984000] sda: Mode Sense: 24 00 00 00
[17271212.984000] sda: assuming drive cache: write through
[17271212.984000]  sda: unknown partition table
[17271213.004000] sd 4:0:0:0: Attached scsi disk sda
[17271213.004000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[17272919.708000] usb 5-7: USB disconnect, address 6
[17272987.764000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17272987.764000] ISOFS: changing to secondary root
[17326638.504000] usb 5-7: new high speed USB device using ehci_hcd and address 7
[17326638.636000] usb 5-7: configuration #1 chosen from 1 choice
[17326638.636000] scsi5 : SCSI emulation for USB Mass Storage devices
[17326638.636000] usb-storage: device found at 7
[17326638.636000] usb-storage: waiting for device to settle before scanning
[17326643.636000] usb-storage: device scan complete
[17326643.692000]   Vendor: Maxtor    Model: OneTouch II       Rev: 023g
[17326643.692000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17326643.748000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17326643.800000] sda: Write Protect is off
[17326643.800000] sda: Mode Sense: 24 00 00 00
[17326643.800000] sda: assuming drive cache: write through
[17326643.856000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17326643.912000] sda: Write Protect is off
[17326643.912000] sda: Mode Sense: 24 00 00 00
[17326643.912000] sda: assuming drive cache: write through
[17326643.912000]  sda: sda1
[17326643.932000] sd 5:0:0:0: Attached scsi disk sda
[17326643.932000] sd 5:0:0:0: Attached scsi generic sg0 type 0
[17326645.000000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

I wonder why it went haywire on me?

---

### Post by kidders on 2007-03-27
> **Unoone said:**
> As far as Ext3 partitions, some of the data that I back up with my DVD burner from my Ext3 partitions in which I am the full owner is locked.Again, you're referring to a filesystem with no support for permissions. Ubuntu, just like any other Linux, will fake whatever ownership/permissions you ask it to, for the purpose of controlling access.

> **Unoone said:**
> Maybe there is a change in the way Ubuntu Edgy and beyond handle permissions that is a bit out of the norm from other Linux Distros?Not really. The fundamentals of file access privileges in Linux are pretty much set in stone.

> **Unoone said:**
> I remember back when I used Mandriva I could choose system wide user global permissions from a configuration interface at install time.I haven't used Mandriva since it was called Mandrake, I'm afraid. I imagine Ubuntu's permissions management should approximate the "paranoid" setting.

In general terms though, "paranoid" access control is by no means draconian, and shouldn't normally pose an obstacle to making full use of your computer. It does however require a basic working understanding of ownership & permissions, and where they come from ... especially when dealing with things that don't support access control properly.

Taking FAT filesystems as an example, Ubuntu (and all Linuxes) will always deny non-root users permission to write anything on them, unless explicitly instructed to do otherwise. (Any other policy would be completely unsafe.) Naturally, any attempt to alter permissions with chmod will fail since, in reality, there are no permissions to alter.

> **Unoone said:**
> I pluged in USB drive into and Ubuntu seemed to recongnise it again.Curious... but good news! :-)

If anything weird like that happens again, be sure to take a look at your system logs. From time to time, oddities crop up in USB device management. Many of them have good-quality solutions though.

---

### Post by Unoone on 2007-03-28
I am aware of Linux permission settings. It just seems that as far as the recent versions of Ubuntu my ability to to grant myself controlling access has changed. Or my settings for my user access permissions are less effective. I never had any issues with write permissions for DVD burning, or data back up for my Ext3 or fat32 drives in Ubuntu. As far as setting permissions after installing an extra hard drive or for a web folder I never had any major problems. Ubuntu would install Firefox and I as the user would have full permissions to download to my fat32 drives out of the box. If I used sudo to setup a Ext3 drive or fat32 drive when I installed Ubuntu the permissions would stay put. 

Ever since I started using Edgy my "file access privileges in this version of Linux were not pretty much set in stone." I could understand if this was a single PC incident. But it happens each time I install Ubuntu Edgy on different types of PC's. The Firefox issue of -0- data downloads to my fat32 drives also occurs on different Ubuntu Edgy and Feisty test install runs. Dapper doesn't have these problems. 

My other Linux Installs operate fine and don't have these annoyances which effect my basic Linux operations. 

I would like to get back a stable current version Ubuntu install without any these issues. The issue of Ubuntu Edgy's "root" scanning my actions and locking my user permissions randomly on my data is insane. There has to be a way around this.

Yeah I got my USB drive back online after I ran -

```
fsck.vfat -t -r /dev/sda1
```

At least that's cool.:)

---

### Post by kidders on 2007-03-28
Hey again,

> **Unoone said:**
> I am aware of Linux permission settings. It just seems that as far as the recent versions of Ubuntu my ability to to grant myself controlling access has changed.The way to do that for filesystems with no permissions support is the same on every Linux. :confused: All you should need to do is choose a set of mount options that sets an appropriate owner for all files & directories, and gives as many users as you need read/write/traverse access. Those permissions will never "stick" though, since they don't really exist.

> **Unoone said:**
> Or my settings for my user access permissions are less effective.That shouldn't happen. Is that to say that if you set the uid, gid, dmask & fmask mount options for a FAT filesystem to suit your needs, they don't result in the permissions you expect?

> **Unoone said:**
> Ever since I started using Edgy my "file access privileges in this version of Linux were not pretty much set in stone."
> **Unoone said:**
> My other Linux Installs operate fine and don't have these annoyances
> **Unoone said:**
> The issue of Ubuntu Edgy's "root" scanning my actions and locking my user permissions randomly on my data is insane.
> **Unoone said:**
> my settings for my user access permissions are less effective

It's very difficult to address your problem without specific examples of the circumstances and symptoms. If you could post one, it might give some indication of what's going on. I'd be glad to try to help, but I need something to work with!

Incidentally, Mozilla seems to be aware of the Firefox issue you mention, which also (apparently) affects NTFS filesystems, and is an issue on Solaris as well. The problem seems to occur with Firefox 2, but I don't know much more than that about it.

---

### Post by Unoone on 2007-03-28
> **kidders said:**
> Hey again,

........

It's very difficult to address your problem without specific examples of the circumstances and symptoms. If you could post one, it might give some indication of what's going on. I'd be glad to try to help, but I need something to work with!

Incidentally, Mozilla seems to be aware of the Firefox issue you mention, which also (apparently) affects NTFS filesystems, and is an issue on Solaris as well. The problem seems to occur with Firefox 2, but I don't know much more than that about it.

Thanks kidders for your help and tips. As far as examples of permission problems. Say I save lots of  html doc to a folders under a directory  in my /user/home/Desktop. I gather html data from our servers web sites and from my own local web files. Later on I attempt to copy this main html directory folder over to a fat32 device that I have set "fake" permissions for. As far as fake permissions I mean uid, gid, dmask & fmask mount options, etc. The directory folder begins to copy over to the faked permission fat32 drive. Errors start popping up -"Error "Invalid parameters" while copying" -you do not have permission to copy...". I investigate my folders and find that one or more folders is owned by "root" in my /user/home/Desktop. 

In other cases I had unknowingly burned a CDR or DVD+r data disk of folders that display these errors. Those individual folders on the CDR ot DVD+r would would only be readable on my machine running Ubuntu not in Windows. This is a new problem that that been occurring since I Started using Edgy. I recently found out that some of my old Dapper DVD+r's had this issue also. But as far as I know using Dapper most of the time this did not happen with the majority of my burns. And I did not need to alter my user permissions much beyond the basic Ubuntu Dapper install settings. Dapper was ok with the basic installed permission settings. This issue is a major problem for me in Edgy. Which is why I wanted to dump Edgy and move onto Feisty even if it is beta.

This "root" locking or Firefox problem does not happen on my Dreamlinux or Kanotix installs. If I track back to my DVD+r disk that I burned with Ubuntu Breezy and before I can't find this issue of any "root" locked data files. Maybe the problem only showed up in Dapper in a slight way due to later system updates etc. Dapper is free from any of the Firefox bugs.

Now obviously I'm doing something wrong "now" as this "root" locked data stuff is an issue for me and not other Ubuntu Edgy users. Yet I haven't found a solution so far in Edgy.

It's kind of scary because I never know where this issue will pop up in my important data files. And as I said before this "root" locked data problem and Firefox problem occurred on different types of PC's running Edgy.

---

### Post by kidders on 2007-03-29
> **Unoone said:**
> "Error "Invalid parameters" while copying"Hmm... That almost sounds like it might be a character set problem.

> **Unoone said:**
> In other cases I had unknowingly burned a CDR or DVD+r data disk of folders that display these errors. Those individual folders on the CDR ot DVD+r would would only be readable on my machine running Ubuntu not in Windows.Afaik Windows will refuse to read optical discs that don't adhere to certain rules. I'm not completely sure what they are though (I'm not a Windows user). Could that be the issue there, I wonder? I imagine that problems would only crop up some of the time, where you use invalid filenames or filesystem extensions that MS objects to.

> **Unoone said:**
> This "root" locking or Firefox problem does not happen on my Dreamlinux or Kanotix installs.That doesn't surprise me... It'll probably turn out that the source of the problem is a kernel issue. I hope figuring out exactly what it is doesn't take too long!

In the meantime, I wonder what would happen if you deliberately downgraded your Edgy kernel?

---

