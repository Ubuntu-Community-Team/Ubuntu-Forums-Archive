---
title: "Permissions on automounted NTFS drives - half arsed solution"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Plus+ on 2009-11-04
The problem  - when Karmic mounts an external drive with NTFS file system it gives read/write permissions only to the owner and they can't be changed in permission tab in properties, one implication being that network users won't be able to even browse it if you decide to share this drive.

Half arsed solution - in terminal open gconf-editor and navigate to system/storage/default_options/ntfs/mount_options

Change umask from 222 to 000. Next time the drive will be mounted with full access for everyone.

The solution is half arsed because I don't really know what I'm doing. Any values other than 0 in umask are supposed to put some restrictions and by changing them all to 0 I might open some holes elsewhere. I also don't know how to set permissions to read-only.

And the main problem remains - this default policy is applied to all affected drives, all their files and folders, and it cannot be overwritten. I guess it means that it's impossible to have one secure external drive for storing important backups and another for sharing public data.

Perhaps there's a way to give authorized users higher priority than this default policy so they can choose permission settings themselves.

---

### Post by allabouttowler on 2009-11-04
Hey Plus+ I'm glad you've mentioned this! It's become the bain of my existence over the last few days.

I'm no Ubuntu expert, and I've tried a whole array of ways to try and get access permissions for the other user on my box (purely to allow ssh'ing from a secondary machine on the internal network) but I can't find any way to rectify this issue.

I tried your gconfig workaround but couldn't find the entry you specified under system - I'm quite happy to accept that may be entirely due to the previously referenced lack of expertise on my behalf.

I've read somewhere that fstab can be edited to auto mount external NTFS volumes with specific permissions - which sounded ideal, but I've been unable to discover my UUID to give this a shot.

Anyone who might be prepared to hold my hand a bit and try and walk me through a way round this would be the recipient of my eternal gratitude!

---

### Post by allabouttowler on 2009-11-04
Sorry - to clarify I'm running Karmic off a clean install and there definitely isn't a 'storage' option under the 'system' tree in my gconf-editor...

Fstab wise when I open the file to try and edit the permissions assigned to the drive there's no signs of an ntfs volume in there for me to change the permission for (as I've seen other forums advise)

Don't know if this info's useful, but figured it was worth being as thorough as possible...

Cheers

---

### Post by Plus+ on 2009-11-07
Never mind, it stopped working for me, too.

All I did was to login into KDE session and it worked just fune for two days, but then I logged back into Gnome and the drive mounted with permissions set to "None" despite keeping the same umask mounting options. Switching back to KDE or restarting doesn't help.

There were a couple of Nautilus and some long name "helpers" crashes, both in KDE and Gnome, but those happen all the time on Karmic (updated from Jaunty). I suspect at some point they overrode whatever is stored in gconf.

Again, I have no idea what I'm talking about, just poking in the dark, trying to make sense out of it.

The fact that you don't have default storage values means there's some other place where your system get these rules.

I've also seen a post somewhere that said the system (something related to HAL in that case but in Karmic it could be something different) reads those rules in numerical order and the sequence was important to what takes precedence. 

It sounds reasonable but I have no idea where exactly that sequence is stored and how to edit it and what would be the implications of tweaking it.

In your case you could probably create a new storage/default/NTFS entry in your gconf and it might work for a while, until something overwrites it. Worth trying, imo. Find where the original gconf is, open it with sudo gedit, learn how to create new entries and so on. 

Personally I don't know what else to do now, I will wait until some knowledgeable person notices this thread and gives some fresh ideas. Short of figuring out all the details of how the mounting works in Karmic comparing to Jaunty I don't see any other way. New restrictions came in the name of security and that means it's way above my level of understanding.

Perhaps editing fstab can be a workaround, it mounts my permanently plugged usb thumb drive to serve as a swap, perhaps I could copy mounting info for external drive into fstab and set everything from there. The potential problem is that I often take the drive elsewhere and the next time I plug it in it might not comply with fstab entry and so will be messed up again.

---

### Post by Plus+ on 2009-11-07
And now the permissions are miraculously back.

I rebooted the system into Mandriva Live CD which didn't work, replugged external drive power supply, booted into Ubuntu KDE, and there it was - mounted with read/write permissions as if nothing had happened.

The big difference I noticed is that the drive is mounted under a different name (label?). Usually it's a FreeAgent Drive, sometiimes it's FreeAgent Drive-1, and now it's FreeAgent Drive again. When it mounts under a different name it screws up the shared folders and I have to reset them again (and that's a minor problem in real life situation, just screwing uuup paths to about a dozen torrents shared from that drive - phew!).

For Linux "-1" means a copy, means that when defaults in gconf are set to "allow" the system applies them to NEW drive names (labels) but the old drive names (labels) are mounted under old rules stored somewhere else.

I see a couple of ways to deal with this. First is to change the drive name, or label, via some other system - Live CD, Gparted or whatever. The name the drive announces itself must be editable somehow. With a new name I can start with a clean slate and set all the shares and permissions that are always to be followed by Ubuntu. There will be a problem if the system finds a way to mount the drive differently, though. 

I can't recollect what the second way was, being in the state of solid inebriation on this late Saturday night.

Allaboottowler, ultimately, gconf-editor reads values from some file. In my case of upgrading from Jaunty that file got something under "storage/default". With your clean isntall it might have no entry like that but Karmic clearly is able to handle it. Find the way to add those entries to gconf file and see how it goes from there.


>>>>

With Karmic giving me troubles with visual effects and file sharing I wanted to check out other distros. Mandriva install hang. OpenSuse will have new version next month, PCLinux is still on KDE3 {suckers!) and setting file sharing is a pain the *** that never went away (main reason I settled on Ubuntu Jaunty in the first place). 

Compiz flies on my old ati-9250 under PClinux though - exceptional.

I  don't know what else to try. Fedora? Hmm, maybe, but what I want is not exactly what they are aiming for. Debian? Can they have better support for ati drivers than ubuntu, especially in KDE with all those fancy plazma effects. Doubt so. PCLinux worked here but Mandriva didn't even run LiveCD. 

I guess I'm stuck with Ubuntu, Karmic reactions or not.

I'll check out Intel Core i5 here in Thailand, and support from Linux community. So far the most stable and fastest system has been pirated XP with SP3, with pirated Win7 edging it out on candy factor.

Give me flying KDE with easy access to some Control Center instead, it ROCKS! In KDE on Ubuntu I can't even change the input language - the relevant GUI menu entry is good only for Gnome.

---

### Post by fackamato on 2010-02-26
(Karmic, GNOME)

Problems:

* The ntfs partition is not automounted on boot, or even login.
* If the ntfs partition is added to fstab you get duplicate entries in Nautilus.
* If you mount the partition in Nautilus, permissions are too restrictive, only user has any rights.

I tried gconf, but I don't have the "storage" key there so I can't change any settings. Can someone shed some light on this please?

---

### Post by DawieS on 2010-02-26
To correct NTFS mounting problems in Karmic, see [this]("http://ubuntuforums.org/showthread.php?t=1409347") thread.

---

