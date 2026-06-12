---
title: "Error mounting file system"
date: 2022-01-23
forum: Hardware
---

### Post by trekker182 on 2022-01-23
Hello,

I&#8217;m using Ubuntu Desktop 20.04 with Plexx and have filled my internal HD so I&#8217;m trying to use an external.  Each time I tried mounting it with my trekker182 user via remote session, I&#8217;d get the above message.  I then decided to try accessing it via keyboard plugged in and it worked so I figured it was permissions and the remote session.  (Also this came from googling)  I just made root accessible by remote and can see the external, but of course now no Plexx or videos because it&#8217;s a new user.  

I&#8217;m not using chrome share and verified the service isn&#8217;t running.  

I logged into root and typed visudo , added trekker182 ALL=(ALL:ALL) ALL saved and rebooted and still get &#8220;not authorized to perform operation&#8221; in files logged in as trekker182 when I try to access the external HD from files.  When I try to mount it I get the above error & &#8220;Not authorized to perform operation (polkit authority not available and caller is not uid 0) (udisks-error-quark, 3) 

At this point, is there a way to permanently elevate an existing user to root so I can access that external HD ?  I guess I could copy over all 1 TB of files and install Plexx on the root user, but I&#8217;d rather not do all of that lol.

Thanks!

---

### Post by trekker182 on 2022-01-23
Ok, so I re-formatted & mounted it as /extmedia.  What&#8217;s strange is I can click on /extmedia and view a blank directory, but now I don&#8217;t have write permissions it says the owner is root even though I was logged in as trekker182 when I formatted and mounted it from terminal.  I&#8217;m using the fat32 file system.

I also tried sudo chown -R trekker182 /extmedia both as the root GUI user and trekker182 and got operation not permitted.

---

### Post by TheFu on 2022-01-23
fat32 is a terrible choice for a file system today.
If you plan to have this device connected to Linux, format it as ext4.
You'll need to mount it using the /etc/fstab - if you google "ubuntu fstab", there is a guide for mounting it at boot.  Then you can make the owner and permissions whatever are needed for the access desired.

fat32/ntfs/exfat don't support chown/chmod. Sorry.

> At this point, is there a way to permanently elevate an existing user to root so I can access that external HD ? I guess I could copy over all 1 TB of files and install Plexx on the root user, but I&#8217;d rather not do all of that lol.
No.  Any that would be a terrible, terrible, terrible, terrible, terrible, terrible, terrible, terrible, idea. All sorts of other things would break.

You should put the sudoers file back the way it was too.  Hopefully, you created/have a backup.  Also, ensure it has the correct owner, group and permissions. On Unix systems, like Linux and Ubuntu, the data is only 50% of what makes file security work. The owner, group, permissions, acls and xattrs are all important.  This ain't Windows.

The mount using a GUI is the root issue.  Don't mount storage that needs to be there at boot using a GUI. Use the /etc/fstab file.  There are thousands of examples on the internet and in these forums. Here's one: [Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843](Https://ubuntuforums.org/showthread.php?t=2459633&p=14027843#post14027843)

---

### Post by trekker182 on 2022-01-23
Thanks!  

sudo mount -o,rw,users,uid=1000,exec /dev/sdb2 /extmedia seems to be working. 

I&#8217;m just researching how to get it to auto-run at startup because of the prompt each time.  I&#8217;ll take a look at the fstab file.

thanks!

---

### Post by TheFu on 2022-01-23
> **trekker182 said:**
> Thanks!  

sudo mount -o,rw,users,uid=1000,exec /dev/sdb2 /extmedia seems to be working. 

I&#8217;m just researching how to get it to auto-run at startup because of the prompt each time.  I&#8217;ll take a look at the fstab file.

thanks!

The fstab file is how to mount storage automatically. If you don't reformat away from fat32 to a native Linux file system, there will always be issues.
Don't use the device file, /dev/sdb2. Device names can change from boot to boot. That's why using either the UUID= or a LABEL= is better. They don't change.  Also, if you use snap packages, probably want to mount below /media somewhere - perhaps [COLOR="#FF0000"]/media/data[/COLOR].  There are reasons.  I think using the LABEL= method is the best. Humans understand a label.  **Gparted** can be used to set the label on a formatted file system/partition.

BTW, there's an extra comma in the options above. I'm a little surprised it worked.  Also, no need for the exec option. That is generally a bad idea for security. Actually, *noexec* would be better for disks that only contain data.

Main thing is NOT to use exfat or fat32.  If you need to allow access from Windows with a physical connection (you will physically move the USB plug to a different system), use NTFS.  If you only need to provide network access to Windows systems, use ext4 and samba or sftp over the network.  **gparted** makes formatting a partition easy.

---

### Post by trekker182 on 2022-01-24
Wow great information that&#8217;s so much!

---

### Post by TheFu on 2022-01-24
With these options "-o,rw,users,uid=1000,exec"
The *rw* is already the default, so it isn't needed.
*exec* is already the default, for data-only storage, noexec would be a security improvement.
*users* let's any user mount, but really only uid 1000 will be able, since other users cannot change the owner as the next option required.
*uid=* isn't desired for native Linux storage. It is necessary only for NTFS, exFAT or FAT32 non-Native file systems. This is to be avoided when possible. Standard Unix permissions as provided by all native Linux file systems is what you'd want to use. Then chown and chmod commands work, always and you can setup the storage correctly once, not every time it is mounted.

So, the first question is, which file system type will be used?  I'd strongly recommend ext4 if you don't have a specific need for something else. If it is a USB flash -stick, then f2fs.  I've posted in these forums which file system is best based on the type of storage used.  That post was targeted at beginners, since experts often want to do something non-standard.  The simple, TL;DR answer is:
* SSD or HDD, use ext4.
* USB flash "thumb" drives, use f2fs.

Always have a partition table with at least 1 partition. This applies regardless of the storage or purpose. It should be a GPT (GUID Partition Table) almost always. Win7 and later along with every version of Linux since pre-2010 have supported GPT. There are too many great reasons to use that rather than the MS-DOS/MBR partition table from 1985. I can admit that I have some storage devices using MBR partition tables still though Ubuntu installation defaults that have been carried forward or even on some of my RAID disk arrays that were initially built around 2005 and have been migrated forward and had all the drives changed over the years, a few times.

There's always more to know, but those are the basics.

---

