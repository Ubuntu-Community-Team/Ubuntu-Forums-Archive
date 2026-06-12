---
title: "hot swappable ubuntu hard drive system"
date: 2015-11-25
forum: Hardware
---

### Post by Harley_Frank on 2015-11-25
Background:
I have an old NITTIX server that no longer runs properly and I can't get it to boot into any other OS because it has a stupid ROM chip embedded into the motherboard to boot when there is no hard drive present. I have a semi-old machine maybe about 2 1/2 years old that still uses DDR2 RAM. I know, it was my old machine before I upgraded to a new one. It still runs perfectly fine so I installed server edition on it. Works great and I though about moving the setup to the nittix server box and using the hot swappable drive bays in the front for well data storage and backup.

What I want to do and also to know if it is possible. I am going to mount a 128 SSD inside the case and use it to run UBUNTU core systems and maybe a few other things like a GUI so my family can gain access to it when I am not around to make changes to the server, possibly LEMP and AJENTI control panel. It has 4 GB of RAM which is more than enough and a quad core AMD Phenom II x4 processor. Not a bad machine and can handle stuff someone easy. So what I need to know if there is some software or coding or something that I have to do to the server in order for it to mount say drive one all the time when there is a drive in the bay (i know how to mount them and keep them mounted but the settings go away when the device is removed and then put back in. never stays) and the second drive bay will mount and perform a backup image and the I remove the second drive to a secure location.

Why I am doing this is because I work in an IT environment where some of my clients have been infected with cryptowall and I don't want to chance it at my home network because I bring my work laptop home with me and work on work stuff while I am at home. Since I travel to client's facilities to disinfect and try to contain the data loss, there is a high risk of contaminating my machine.

But since it is a desktop board and not a server board I am not sure if that is possible with the motherboard ports.

Then my next question would be what card component would provide the hot swappable feature?

I appreciate your time. Thank you and Happy Thanksgiving.

---

### Post by Harley_Frank on 2015-11-25
To clarify even more, the reason about drive 1 to be mounted all the time and drive 2 as backup so that its a clone basically. If drive 1 fails or gets corrupted I can just remove drive 1 and place drive 2 in its place without any issues. I of course would probably have to reinstall the OS unless there is a way I could backup an entire image like you can with windows server backup.

---

### Post by weatherman2 on 2015-11-25
You can code up something so that whenever you plug a drive in, a script will run (e.g. to run a backup to that drive) and even email you when it is done so you know to remove it.  There are a few ways to do it, but one way would be via udev rules.  Do a web search for "udev launch script." (Sift through for a good tutorial - I forget the exact steps to make this work, it will take a little time but shouldn't be that dificult.)  You can automatically mount the backup partition, do the backup, and then unmount it so it is then safe to remove when you get the email (or however else you wish to notify yourself).

You can do this with USB of course - either with an external USB drive or with a USB hard drive dock into which you plug internal drives.

You can also hot swap SATA devices in some cases.  I have one motherboard that simply has that feature built in (not all of mine do).  I was playing with it today.  I had to enable (per SATA port) the hot swappable functionality in BIOS, but once I did that, I didn't have to do anything in Ubuntu.  I could plug in a drive, mount the partition(s) on the drive (I wasn't doing it automatically like you wish to), unmount them, then physically remove the drive.  I was using my USB dock that also has an eSATA port (I was turning off the power to the drive on the dock before removing it, though).  Adding an eSATA port to my box with that motherboard was just a matter of adding a connector to the back of the case and plugging the SATA cable into one of the motherboard's SATA ports.

I'm not sure what your options are for the server.  If it doesn't have USB 3 ports does it have an PCI-E slots?  Even PCI-E x1?  Then you could add a USB 3 card with USB 3 ports.  USB is most likely the easiest way to go.  eSATA would work too if you have the hot swap option I described above.

---

### Post by weatherman2 on 2015-11-25
As for Cryptowall, which I have had to deal with too, I have found that the most practical way to protect your data (for your clients, in the future at least) is to use cloud storage like Dropbox or Google Drive.  When I had to deal with it, the client had everything they cared about in Dropbox.  Cryptowall did infect (encrypt) all data in Dropbox but all we had to do was get Dropbox to roll everything in the share to one second before first infection (which was obvious).  They were lucky.  Removing the infection itself was not that hard though there were little "info" files all over the C: (I removed them all with a script).  Most people would simply nuke and pave the OS drive and re-install Windows from scratch, though.

The best way to avoid inadvertent infection (for you) is to have all your updates, all software like Java and Flash updated, etc.  Unless the infection gets in via a zero day security hole, it's getting in through some unpatched but known security hole.  Simpy accessing an infected/encrypted file did not in itself seem to put a fully updated Windows PC at risk.  On the one I worked on, the infection did not spread over the network to any other PCs - only got to one that wasn't updated.  If you really worry about your Windows OS, use something like True Image to backup your C: every now and then so you could always restore that if you get infected instead of re-installing Windows.

Otherwise, if you have too much data to do cloud backup (or just don't want to), you are wise to use a backup system that doesn't keep ALL copies of you data online at all times and vulnerable to an infection like Cryptowall.  This is one of those things that makes you realize how utterly useless a RAID mirror can be in protecting your data.   I keep a copy of my data offline on a separate device not even physically plugged in (to protect against power surges as well).

---

### Post by Harley_Frank on 2015-11-26
I know that my motherboard doesn't support hot swappable drives. Is there a PCI-E card I could use that would provide that technology? And that is precisely what I am going to do. Drop the second drive in run a backup and then take it out and leave it alone for a week and then run another backup. Or I may do every three days. I appreciate the advice though, I do recommend cloud storage through intronis, which have the same functionality like dropbox does.

---

### Post by mastablasta on 2015-11-27
I am not sure why you are taking drive 2 out. but what I understand from your post you would want a home server where drive one is server drive, while drive 2 acts as backup drive. and I am assuming you remove drive 2 to "make it safe". you could just unmounts, it to do that.

in any case - if drive 2 is bigger than drive 1 you should do versioned backups to drive 2. where you would perform automatic backup/sync and keep snapshots for example from a day, a week a months ago. you can do this in command line with rsync or using rdiff-backup providing. there are also a few other command line programs. I think zentyal interface has a backup button. 
another option would be to use either ZFS4linux or BTRFS file system which support snapshots. and just in case disk goes bad maybe connect them into a RAID array. raid is not a backup but a redundant disk array and protects against disk failure but does not protect the data. if you go ZFS way you should explore freenas.

---

### Post by Harley_Frank on 2015-11-29
That also works. Thank you for the input!

---

### Post by Harley_Frank on 2015-12-08
Ok so I got it working which I appreciate all the help now I am having issues with my NAS. I have tried most of the backup programs and they all don't offer backing up from network storages. So I tried to mount the network drives to my machine and well. I am able to see it but not read it. I have tried taking ownership and change the permissions and it just doesn't seem to want to work.

I followed this:
[http://knowledgelayer.softlayer.com/procedure/mount-nas-storage-linux](http://knowledgelayer.softlayer.com/procedure/mount-nas-storage-linux)

I'm not sure that I understand fully.

Or is there a backup program that can read network shares?

Any help would be awesomely appreciated.

---

### Post by mastablasta on 2015-12-09
what do you want to do? pull data from your NAS to another computer to perform backup? you can push it from NAS.

yes there are programs that read network shares. backuppc, [https://www.urbackup.org/](https://www.urbackup.org/)...

you have also programs where you push data to a networked drive on server via various protocols: Areca, rsync (grsync), duplicate, rdiff-backup...

or you can synchronise: bittorrent sync, syncronicity...

for example we went with Areca. we use sFTP with keys to connect to server driver and upload the backup data.

---

### Post by Harley_Frank on 2015-12-16
Well I did it a little bit differently. Instead of backing up I did file sync. dirsyncpro and well it seems to work.

One would think that WDmycloud would have that option. I can't even backup to usb....

I do appreciate the help. Very knowledgeable. Thank you.

---

