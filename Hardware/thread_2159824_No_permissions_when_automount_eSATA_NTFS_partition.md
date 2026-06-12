---
title: "No permissions when automount eSATA NTFS partition in minimal install"
date: 2013-07-04
forum: Hardware
---

### Post by Bucky Ball on 2013-07-04
Hi all,

Bit infuriating. I did a minimal install a couple of weeks ago and all is working great. I installed a list of my main apps and packages when I did the install and have installed things I've needed as I go, and that hasn't been a lot. 

Situation now is I've bought a 2Tb drive for backups. Have two NTFS primary partitions on it, when I plug it in it is recognised and visible in the file manager, but not mounted and won't mount. The old story. I'm fairly certain that this would be due to something missing in my minimal install. I have ntfs-config, ntfsprog (I think) and ntfs-3g installed (the latter I didn't need as my internal NTFS partition I had mounting fine through fstab tweaks and ntfs-3g overwrites them, great!). 

One suggstion for a fix is to make sure I am a user in the correct group. I have no idea as I have no GUI for Users & Groups as is in the regular Xubuntu (I have xfce4 installed only, not xubuntu-desktop). I know I can drag in gnome-system-tools and that will give me the Users/Groups GUI in System, but it also drags in heaps of stuff I don't want or need (same with xfce4-goodies). 

So, any suggestions or do I need to work through this by learning how to do it with the command line? What is the Users & Groups app used in a regular Xubuntu install? Is it possible to just install that?

Bottom line is I am wanting to get this drive automounting with read/write permission anyways possible, using groups or otherwise. Any suggestions?

* Update: Currently NTFS partitions on external drive are auto-mounted in PCmanFM (and/or Thunar) but with no permissions. Partitions mount with partitions if mounted manually to mountpoints in /media or written into the /fstab and the drive is on at boot.

---

### Post by Bucky Ball on 2013-07-04
Following up on that, I just ran this:

```
sudo usermod -a -G admin username
```

... replacing 'username' with my username, and,
```

usermod: group 'admin' does not exist

```
Could this be connected with why I am not getting permission on the external partitions? Everything else is fine re. permissions (and all else).

PS: I can manually mount these partitions and get permission just fine and they work fine if I change fstab and have the drive on when I boot. It's only when the OS is running and I plug it in and switch it on (or just plug it on while its on) that I don't have permission. What am I missing? he ponders ... :-k

---

### Post by steeldriver on 2013-07-04
AFAIK 'admin' is just the old name for the group that is now called 'sudo' (i.e. sudoers used to belong to admin)

On my Mythbuntu box (which uses xfce4), auto mounting of hotplugged removable drives is handled by thunar-volman-settings - provided by the thunar-volman package - if there's not an 'Applications --> Settings --> Removable drives and media' menu item, then you could try just invoking thunar-volman-settings from a terminal

I'll let someone else advise about the specifics of getting the mounted permissions you want as I'm not too hot on that stuff

---

### Post by Bucky Ball on 2013-07-04
> **steeldriver said:**
> ... you could try just invoking thunar-volman-settings from a terminal



I can open that from Settings Manager>Removable Drives and Media. It is all set to go, which is probably why the partitions are appearing, but not mounting, so don't think it's related.

Thanks though. Got me thinking. :-k

---

### Post by Bashing-om on 2013-07-04
Bucky Ball;
I recently did the same install route.. and I discovered upon attempting administrative actions that -> I did not have :
a) the variable XAUTHORITY set
```
echo $XAUTHORITY
```
b) no ~/.Xauthority 
c) no ~/.ICEauthority

I continue to contend with small details in respect to permissions and authorizations. - Hey, was done for the learning ,and like you -  no bloat ,, and believe me I am learning !

I had not had an occasion to observe an external device at the time of install ... presently I am able to mount a fat32 usb (auto mount ->thunar)drive successfully. 

For that NTFS big drive... I am sure you have considered mounting it through /etc/fstab. Best I do recall one can mount it as upon insertion within the mounting instructions in /etc/fstab.

[INDENT][INDENT]2 heads are better than 1, even if I am a goat head
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-07-05
I can mount through fstab no problem but the drive would need to be on when I boot the machine. I can also mount manually by using a couple of mount points I have set up in /media. Clumsy and not what I'm after every time I want to use the drive. Neither do I want. I want to be able to have a running system, simply switch the drive on and there it appears, mounted and with permissions.

Where I'm at now: When I switch the drive on the two partitions I have on it appear in the left pane of the file manager (PCmanFM, incidentally, not Thunar). Unmounted. I click one, says 'You need permission to mount, etc.' and gives a box for password. I fill in password and the partitions mount and all is well with the world. Except I have them mounted as root. I definitely don't want that.

All suggestions appreciated and thanks so far. ;)

---

### Post by Bucky Ball on 2013-07-05
Quick update: Trying this on my desktop now. Switch external drive on connected eSATA, two partitions show up but, you guessed, no permissions. I even tried formatting the hard drive to two NTFS partitions in XP and no different. I honestly can't believe it is this hard to get permissions for an NTFS drive. I remember having this problem with *buntu back when I first started in '07. This machine is running Xubuntu also, incidentally. Might try it on the laptop with 12.04. 

He bought the drive to do the overdue backup and three days later ... :-k ;)

PS: Laptop still same; partitions show but no permissions. In a nutshell, no progress whatever in the last 24H.

---

### Post by Bashing-om on 2013-07-05
Bucky Ball; Nope ... 

I have the same situation of requiring authorization to mount that usb thumb drive - fat32...also in my 13.04/xfce. This mounting issue has not been present on any other install....standard desktop -12.04 and earlier versions of ubie and Lubuntu. As of now I can not point any fingers as I have other permission issues (very small ones not directly affecting operations).

But just confirmation the situation also affects me ! If I wanted to auto mount an external drive ... yeah would present a problem !

Just as a thought, maybe take a big learning dive into gvfs-mounting.

[INDENT][INDENT]we never will know it all[/INDENT][/INDENT]

---

### Post by Ranko Kohime on 2013-07-05
No solution from me either, but I will chime in with the same situation: minimal install, and no disk mount permissions for user.  I even added user to group 'disk', but no dice.

---

### Post by slickymaster on 2013-07-05
> **Bashing-om said:**
> ...
Just as a thought, maybe take a big learning dive into gvfs-mounting.[INDENT][INDENT]we never will know it all[/INDENT]
[/INDENT]


Sorry for stepping in guys. I'm not trying to be rude, but I think Bashing-om could be right, non auto mounting behavior is neither xfce nor thunar-specific, it affects all file-managers that employ gvfs.
Thing is, I don't have the slightest idea if PCmanFM employs it.

---

### Post by Bucky Ball on 2013-07-05
I'm using 12.04 for he minimal and have 10.04 on the desktop. I'm wanting to upgrade that which is the main reason I bought the backup drive. The 10.04 on the desktop is hybrid Ubuntu Studio originally 8.04, tweaked, upgraded to 10.04 and now has gnome, xfce, openbox, fluxbox and artwork and apps from all over the place! If that doesn't mount it with permissions, nothing will. 

Oddly, I just tried my old 500Gb external eSATA drive and that is now suffering from the same issue. Both drives tell me the volume is locked when I plug in to the desktop. I've tried the dock with a USB cable and that has exactly the same error. 

Maybe I should think about learning how to write my first script which mounts the two external partitions in the mount points I've created in /media when I plug the drive in. They mount fine when I do it manually. That script must be possible but haven't really got time to spend right now. Like an 'instant fstab'. :-k

PS: As mentioned previously, also works fine when I add the external partitions to /fstab mounting in mountpoints in /media and the drive is on and plugged in at boot.

---

### Post by Bucky Ball on 2013-07-05
Oh, thanks for the replies people. They arrived while I was pondering my last post so didn't see before posting. 

Step right in, Slickymaster. Yea, I checked on the desktop and I have gvfs and a whole lot of other related packages, etc. I'll look further into gvfs as suggested. ;)

Thanks again for the clues.

* Update: I think I've got it but don't know how to do it because I'm not really a coder. I just right clicked on the desktop>Create Launcher and in there put the command to mount the external drive at the mountpoint I've set up for it. Not much happened when I double clicked the icon, of course. So I edited the launcher and ticked the box to run in a terminal. This time when I double clicked the launcher icon it said 'File does not exist'. 

So, if a file (bash?) with the instructions 'sudo mount /dev/*** /media/***' did exist, then clicking on the icon would activate a command to run that script. The command would be '/path/to/file/something.sh'? Hmm. Obviously I need to look into this.

I get the concept at least. Please steer me in the right direction if that's not how it could work ...

---

### Post by Bucky Ball on 2013-07-05
Further update; I just quickly learnt how to put together and execute a bash script and it worked to mount the partition with permission (but not permission to unmount it) but only worked from a terminal if I'm in the correct directory. Oddly I can now not open the file to edit in anything, and when I do it's blank! I created it with 'touch' command. 

Any ideas how I might issue that command successfully anywhere other than in the /Desktop directory? I tried './' then the whole path to the directory but it didn't work. (I'll save this for another thread in ***Programming Talk*** perhaps).

So, when I'm at /Desktop in a terminal, if I issue:

./eSATA1.sh

... yep, the disk whirrs and it's ready to go! It appears the only way to unmount is through a terminal still but I'm getting there (I tried to create a script to unmount also but hasn't worked ... yet). :-k

PS: for those who might want to know, the script I used was simply a 'shebang' followed by the command:
```

#!/bin/bash
sudo mount /dev/sd** /media/***
```

... or however you like. I saved as eSATA1.sh, but use what you like. After that, while in the same directory as the file, for me:

```
./eSATA1.sh
```

That simple.

---

### Post by Bashing-om on 2013-07-05
Bucky Ball;

I can not shed much more light on this ... however, in docs IRT automounting a usb device. I did run across that if and when a external device is mounted via the CLI ... it MUST also be (un-)mounted in the cli... I recon there are 2 separate process - one for GUI (gvfs system) and in the cli,  dev proc (??); they do not talk one to the other ??

Trying to write the (un-)mount script ... now that may indeed be a challenge,

[INDENT][INDENT]no help, but I can sure feel for you[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-07-05
Thanks for that Bashing-om and good point. Yes, you're probably right. At one point, I did get the message that the disk must have been mounted manually and must be unmounted the same way. That could be as easy as ticking the 'Run in terminal' box when I create the lancher. Food for thought but I'm going to wake up first. Just arose. ;)

PS: If you have a custom fstab, DON'T use ntfs-3g. All my NTFS partitions are now unusable on the laptop whereas I had it purring before with the correct internal partitions mounting with permissions at boot. Should have backed up the original fstab like I'm always telling others to do (do as I say, not as I do?). :-k

---

### Post by Bucky Ball on 2013-07-07
Another up date to let you know where I'm going with this ... around in circles. I managed to create two scripts, one to mount with permissions and one to umount, but how tedious? I tried to make launchers for them but just couldn't get them to work (despite the fact the same commands used worked perfectly in a terminal).

So I thought there must be a better way. Perhaps I need to change permissions for the mount points. Perhaps I need to make sure I am in the group 'plugdev'. I am. So I went back to the regular 12.04 LTS Xubuntu install to check a few things out and low and behold, plug in the eSATA drive, up pop the two partitions, even opening file manager windows in the process, and with RW permissions! Bamboozled.

If nothing else, now I am certain there is something, software or tweak, in the regular Xubuntu install by default that is not in the minimal by default, so I need to find and tweak. Doesn't explain why I'm having the same problem on the desktop install, which isn't a minimal, but that is such a dog's breakfast of a setup things change from boot to boot. Not really a good example.

Any clues as to what's missing? :-k

---

### Post by Bucky Ball on 2013-07-07
Another up date to let you know where I'm going with this ... around in circles. I managed to create two scripts, one to mount with permissions and one to umount, but how tedious? I tried to make launchers for them but just couldn't get them to work (despite the fact the same commands used worked perfectly in a terminal).

So I thought there must be a better way. Perhaps I need to change permissions for the mount points. Perhaps I need to make sure I am in the group 'plugdev'. I am. So I went back to the regular 12.04 LTS Xubuntu install to check a few things out and low and behold, plug in the eSATA drive, up pop the two partitions, even opening file manager windows in the process, and with RW permissions! Bamboozled.

If nothing else, now I am certain there is something, software or tweak, in the regular Xubuntu install by default that is not in the minimal by default, so I need to find and tweak. Doesn't explain why I'm having the same problem on the desktop install, which isn't a minimal, but that is such a dog's breakfast of a setup things change from boot to boot. Not really a good example.

Any clues as to what's missing? :-k

---

### Post by Bashing-om on 2013-07-09
Bucky Ball; My continued interest;
Because I too want to comprehend our operating system. 

Maybe I am in error in respect to gvfs:
from community docs:
> flash drives and USB hard drives since these are generally automounted by hal (Hardware Abstraction Layer).
And to see some of the relationships:
```

ls -l /dev/disk/by-id/
# Details may be found in the autofs(5) manpage
ls -la /sys/block/
file /sys/block/sdb

```
[INDENT][INDENT]still on the hunt
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-07-09
sda=internal
sdb=external eSATA

ls -l /dev/disk/by-id/

```
lrwxrwxrwx 1 root root  9 Jul  9 04:47 wwn-0x500003925688264a -> ../../sda
lrwxrwxrwx 1 root root 10 Jul  9 04:47 wwn-0x500003925688264a-part1 -> ../../sda1
lrwxrwxrwx 1 root root 11 Jul  9 04:47 wwn-0x500003925688264a-part10 -> ../../sda10
lrwxrwxrwx 1 root root 11 Jul  9 04:47 wwn-0x500003925688264a-part11 -> ../../sda11
lrwxrwxrwx 1 root root 11 Jul  9 04:47 wwn-0x500003925688264a-part12 -> ../../sda12
lrwxrwxrwx 1 root root 10 Jul  9 04:47 wwn-0x500003925688264a-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul  9 04:47 wwn-0x500003925688264a-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jul  9 04:47 wwn-0x500003925688264a-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jul  9 04:47 wwn-0x500003925688264a-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jul  9 04:47 wwn-0x500003925688264a-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Jul  9 04:47 wwn-0x500003925688264a-part7 -> ../../sda7
lrwxrwxrwx 1 root root 10 Jul  9 04:47 wwn-0x500003925688264a-part8 -> ../../sda8
lrwxrwxrwx 1 root root 10 Jul  9 04:47 wwn-0x500003925688264a-part9 -> ../../sda9
lrwxrwxrwx 1 root root  9 Jul 10 04:50 wwn-0x50014ee25dcff2aa -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul 10 04:50 wwn-0x50014ee25dcff2aa-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jul 10 04:50 wwn-0x50014ee25dcff2aa-part2 -> ../../sdb2
```

ls -la /sys/block/

```
lrwxrwxrwx  1 root root 0 Jul  9 14:17 sda -> ../devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda
lrwxrwxrwx  1 root root 0 Jul 10 04:50 sdb -> ../devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sdb
```

file /sys/block/sdb

```
/sys/block/sda: symbolic link to `../devices/pci0000:00/0000:00:1f.2/host1/target1:0:0/1:0:0:0/block/sda'
/sys/block/sdb: symbolic link to `../devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sdb'
```

Thanks for the input. I can't see a lot wrong there. Not all the output is there, just what seems relevant. Ask if you want more.

I'm starting to wonder if it is the ancient bug/issue of Ubuntu considering eSATA an internal drive and refusing to mount after boot. This was a known issue. It has possibly been fixed but I just don't have that fix installed ,perhaps. Which may be why the regular Xubuntu install has no problem.

* As I was starting to drift off to trying adduser and groups and getting away from the topic of this thread, it warranted posting another here:

[http://ubuntuforums.org/showthread.php?t=2160784](http://ubuntuforums.org/showthread.php?t=2160784)

Might get some fresh clues from what else I've done.

---

### Post by Bucky Ball on 2013-07-09
And just for the heck of it, here is the result of dmesg after opening the laptop lid with the drive plugged in:

```
[49741.498144] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[49741.499029] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) succeeded
[49741.499099] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 (SET FEATURES) succeeded
[49741.499104] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 (SET FEATURES) filtered out
[49741.499198] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 (SET FEATURES) succeeded
[49741.501130] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) succeeded
[49741.501141] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 (SET FEATURES) filtered out
[49741.501255] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 (SET FEATURES) succeeded
[49741.502114] ata2.00: configured for UDMA/100
[49741.518122] PM: resume of drv:radeon dev:0000:01:00.0 complete after 1976.147 msecs
[49741.544091] PM: resume of drv:sd dev:1:0:0:0 complete after 2001.833 msecs
[49741.544141] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 2001.882 msecs
[49741.544156] PM: resume of drv:scsi_disk dev:1:0:0:0 complete after 1952.911 msecs
[49744.912662] ata5: link is slow to respond, please be patient (ready=0)
[49748.886966] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[49748.931629] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[49749.068625] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[49749.068631] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[49749.068837] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[49749.071383] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[49749.071389] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[49749.071582] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[49749.071722] ata5.00: configured for UDMA/133
[49749.092421] PM: resume of drv:sd dev:4:0:0:0 complete after 9552.132 msecs
[49749.092596] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 9552.287 msecs
[49749.092600] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 7551.521 msecs
[49749.092611] PM: resume of devices complete after 9554.049 msecs
[49749.093076] PM: resume devices took 9.556 seconds
[49749.093125] PM: Finishing wakeup.
```

---

### Post by Bucky Ball on 2013-07-09
And just for the heck of it, here is the result of dmesg after opening the laptop lid with the drive plugged in. It is just the bit that concerns the drive with matching messages to some in the output above:

```
[49741.498144] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[49741.499029] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) succeeded
[49741.499099] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 (SET FEATURES) succeeded
[49741.499104] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 (SET FEATURES) filtered out
[49741.499198] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 (SET FEATURES) succeeded
[49741.501130] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 (NOP) succeeded
[49741.501141] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 (SET FEATURES) filtered out
[49741.501255] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 (SET FEATURES) succeeded
[49741.502114] ata2.00: configured for UDMA/100
[49741.518122] PM: resume of drv:radeon dev:0000:01:00.0 complete after 1976.147 msecs
[49741.544091] PM: resume of drv:sd dev:1:0:0:0 complete after 2001.833 msecs
[49741.544141] PM: resume of drv:scsi_device dev:1:0:0:0 complete after 2001.882 msecs
[49741.544156] PM: resume of drv:scsi_disk dev:1:0:0:0 complete after 1952.911 msecs
[49744.912662] ata5: link is slow to respond, please be patient (ready=0)
[49748.886966] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[49748.931629] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[49749.068625] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[49749.068631] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[49749.068837] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[49749.071383] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[49749.071389] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[49749.071582] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[49749.071722] ata5.00: configured for UDMA/133
[49749.092421] PM: resume of drv:sd dev:4:0:0:0 complete after 9552.132 msecs
[49749.092596] PM: resume of drv:scsi_device dev:4:0:0:0 complete after 9552.287 msecs
[49749.092600] PM: resume of drv:scsi_disk dev:4:0:0:0 complete after 7551.521 msecs
[49749.092611] PM: resume of devices complete after 9554.049 msecs
[49749.093076] PM: resume devices took 9.556 seconds
[49749.093125] PM: Finishing wakeup.
```

Just a reminder that if I click the partition in PCmanFM's left panel and enter my password in the authentication window that pops up, all is good with the world, mounted and with permissions.

---

### Post by Bashing-om on 2013-07-09
Bucky Ball; Hey..
I am trying to comprehend the mapping of the device->buss->kernel->UUID->access permissions,
All thus far looks good, and no problems kernel wise as we know, just do not know where that integration with permissions/user-access takes place.

Last night I did have a thought process, but I seem to have lost that train of thought in my sleep !

I am putting it to rest and maybe it will come back to me.
When it does .. I will be back here or your other related thread ( I had read it too last eve )..

[INDENT][INDENT]user-access, on my mind[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-09
Bucky Ball;

As noted else where.. I bet the difference in "mounting" is to be found in " /lib/udev/rules.d" .
Your attention is invited to:
 ```
cat /etc/udev/rules.d/README
 cat /lib/udev/rules.d/README

```
where:
> 

 1) Write your own rules in /etc/udev/rules.d that assign the name,
    symlinks, permissions, etc. that you want.  Pick a number higher
    than the rules you want to override, and yours will be used.


[INDENT][INDENT]whatcha think
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-07-10
Me thinks that is definitely worth a sniff. I had drifted past the udev rules thing in my travel but thanks for bringing me back to it. Few things to do but will investigate shortly. ;)

---

### Post by Bucky Ball on 2013-07-11
!

This:

[https://wiki.archlinux.org/index.php/Udev#Detect_new_eSATA_drives](https://wiki.archlinux.org/index.php/Udev#Detect_new_eSATA_drives)

I used this to get the block node as the methods on the above link didn't work for me:

```
udevadm info -a -p $(udevadm info -q path -n /dev/sdd1)
```

Working perfectly. If anyone needs a hand with it just post.

Bashing-om, I can't thank you enough for keeping my brain ticking over on this when at times I felt stumped. Creating a udev rule was right on the mark, excellent spot, and when I eventually sat down to start digging it took about half an hour and I was there.

Conclusion: Yes, eSATA specific.

* For future travellers, take note: The partitions should show when the eSATA drive is plugged in, but ... ***they will not automount*** (or at least mine didn't). Just click on the partition and it will mount.

---

### Post by Bucky Ball on 2013-07-11
!

This:

[https://wiki.archlinux.org/index.php/Udev#Detect_new_eSATA_drives](https://wiki.archlinux.org/index.php/Udev#Detect_new_eSATA_drives)

I used this to get the block node as the methods on the above link didn't work for me:

```
udevadm info -a -p $(udevadm info -q path -n /dev/sdd1)
```

Working perfectly. If anyone needs a hand with it just post.

Bashing-om, I can't thank you enough for keeping my brain ticking over on this when at times I felt stumped. Creating a udev rule was right on the mark, excellent shot, and when I eventually sat down to start digging it took about half an hour and I was there.

Conclusion: Yes, eSATA specific. Without the rule, system thinks eSATA is an internal, not external, drive. The rule sets it straight.
Suggestion: Check the udev rules of an install that automounts eSATA drives for a rule that applies to eSATA, which is what I'm going to do after sleep.

* For future travellers, take note: The partitions should show when the eSATA drive is plugged in, but ... ***they will not automount*** (or at least mine didn't). Just click on the partition and it will mount.

---

### Post by Bashing-om on 2013-07-11
Bucky Ball; Wow.

Pleased you got it fingered out !... Your itineration of the basic "udevadm" command -> informative .

That page also pointed me to a direction on why umount2 is hollering on my install.

[INDENT][INDENT]Good docs, indispensable [/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-07-12
I have posted a step-by-step here:

[http://ubuntuforums.org/showthread.php?t=2161837&p=12728219#post12728219](http://ubuntuforums.org/showthread.php?t=2161837&p=12728219#post12728219)

Thanks again. ;)

---

