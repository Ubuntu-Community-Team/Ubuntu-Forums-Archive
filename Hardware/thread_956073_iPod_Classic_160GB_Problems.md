---
title: "iPod Classic 160GB Problems"
date: 2008-10-22
forum: Hardware
---

### Post by nobugsforme on 2008-10-22
Hello everyone. I purchased a refurbished Black iPod Classic 160GB from Apple this week. I have an Asus Eee-PC 901 20GB with Ubuntu-Eee (Netbook Remix) installed on it. ([http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/))

Anyways, I have been having many problems with the iPod, and few successes.

First, after inserting the iPod, the iPod is recognized, but an error message appears:

Cannot mount volume.
Unable to mount the volume 'IPOD'
Details- mount: must be superuser to use mount

I fiddled around with it, and was eventually able to mount it with the following command:

sudo mount /dev/sdc1 /media/IPOD

Programs such as gtkpod, rhythmbox, banshee, etc were able to see my iPod at this point (although intermittently... see below). However, since I mounted it as superuser, none of these programs were able to write to it unless I ran them in root.

The only way I was able to get them to mount "properly" was to insert the following line into my fstab:

/dev/sdc1 /media/IPOD vfat rw,users,umask=000,auto 0 0

and then run:

sudo mount -a

This gave me read/write access on my standard user account.

I opened up banshee (this is where I keep my music organized), and attempted to copy my entire collection from this PC (10GB) to the iPod. It took a long time, but it finally finished, so I unmounted and ejected the drive to check it out... Unfortunately, it said that there was no music on the device! I plugged it back in, and was able to see (and play) my music in /media/IPOD/iPod_Control/Music/f* directories on my PC. The files also show up in banshee, and gtkpod.

Frustrated, I installed and ran iTunes on a Windows PC, to see if the music showed up there. No luck, so I used iTunes to restore the iPod to factory default settings.

I plugged it back into my Ubuntu machine, and tried just copying a few files from banshee. They worked. The music files were on my iPod and playable, complete with cover art. I tried adding more and more, little by little, but on my third or forth copy, it stopped working again. The iPod said it had no music. I thought it might be because banshee was converting a few of my files that were stored in wma and ogg formats. I removed those files from banshee and tried again. Another fail.

That's basically where I am right now. On top of that, sometimes when I plug my iPod in, it does not appear in banshee or gtkpod. But the files are accessible from Nautilus.

I have searched through many forums, and it seems like normally the iPod is recognized, automatically mounts and can be copied too without problems in Ubuntu. Does this look like a problem with my iPod or my computer (or me)? Any suggestions?

Thanks!!! I still love Ubuntu, but if I can't get this working I may have to break down and install XP on here (no room for dual-booting) :(

---

### Post by nobugsforme on 2008-10-26
Just an update in case anybody with a similar problem reads this thread.

The line that I added to the fstab was unnecessary. The version of Ubuntu that I am using assumes that sdc1 is a cdrom and has a line in the fstab mounting it accordingly. Simply commenting out that line will solve that problem. I'm not sure what would happen if you plug in an external cdrom after that, though.

Also, banshee seemed to be the source of my music not showing up on my iPod. I copied all of my music files to a windows machine, and loaded them onto my ipod using itunes. Since then I have been managing them with gtkpod with no problems.

---

