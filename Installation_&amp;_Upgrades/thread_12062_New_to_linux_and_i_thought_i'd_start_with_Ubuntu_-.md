---
title: "New to linux and i thought i'd start with Ubuntu --&gt; need some help"
date: 2005-01-21
forum: Installation &amp; Upgrades
---

### Post by hubris on 2005-01-21
Ok so i'm new to this whole linux thingy but i'm gonna give it a go.
Ubuntu is nice it detected i think all of my hardware with no problem what so ever.
But i'm running into some questions these days.

1.
I'm trying to make a new partition on the HD so i can use it as a fileserver for all the other WindowXP pc's in the house.
I can't seem to figure out how to do it with fdisk.

2.
And this is prolly even nicer to get this started.
the PC has a ATI Radeon 9200SE that i don't seem to get working.
(my screenresolution is killing me right now. i'm used to 1600x1200 :) )

3.
I got on my WinXP box a network drive (in NTFS) how do i add it in Ubuntu?


That's all for now i think.
Ow and just so you guys now.
I've searched the forums and i've searched google, but i didn't find the things i need to solve my problems.
Hence the reason for my post.



Greetz
Hubris

---

### Post by celloandy on 2005-01-21
Samba is the service that allows filesharing with windows boxes.  The biggest reference is probably at [http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/) , but there may be others that are more gui-oriented and/or Ubuntu-specific.  The other thing is that if you're remote-mounting a windows filesystem (which would be with "mount -t smbfs name-of-share"), it doesn't matter what the actual native filesystem is of that share.  Likewise, if all you want to do is serve files from your box so that they'll be visible on other boxes, the samba server will handle all of that for you, once you configure your shares, and again, the actual local filesystem you use (ext3, or whatever) doesn't matter.  You don't need a native windows partition (ntfs, etc.) to share files with windows boxes.  I don't know as much about pretty gui samba configuration, so if anyone else knows of a tutorial or something that's more newbie-friendly that the one, it could be helpful.

Andrew

---

### Post by Moobert on 2005-01-21
[http://ubuntuguide.org/](http://ubuntuguide.org/)

will answer afew of  your questions as for the the screen res problem...
your need to edit your X config to include then higher screen modes, then use the program with gnome to change between them.

---

### Post by hubris on 2005-01-21
OK

i messed around a bit with SAMBA not success.

I want to mount a network drive (that is NTFS), can't find something for that.

GFX drivers there are no tutorials for ATI cards


Good thing is

i did get my ssh to work :d

nice tutorial already btw

Greetz
Hubris

---

### Post by Marquis_de_Carabas on 2005-01-21
I have an Nvidia card, so I know nothing about it, but [Tweaking Ubuntu After Your First Installation](http://www.ubuntuforums.org/showthread.php?t=3713)  has some info on setting up ATI drivers.

With regards to the partition, you'll need to ensure you have some free (unpartitioned) space first. Use something like Partition Expert (Windoze, but allows you to create a bootable CD that you can use with any OS) or QTParted to resize your existing partitions to leave some space, then you can go with fdisk to create the new partition.

---

### Post by celloandy on 2005-01-21
Assuming you have samba installed, and the sharing is turned on on the machine with the drive you want to mount, you can mount it as follows, regardless of whether or not the remote machine's filesystem is ntfs or fat32 (as I said, it doesn't matter):
```
mount -t smbfs //name-of-computer/name-of-share /path/to/local/mount/point
```
So, for example, I mount my remote drive as follows:
```
mount -t smbfs //Main-box/c-drive /mnt/windows-box
```
You'll have to be root to do this, and it'll probably prompt for a password.

Andrew

---

### Post by hubris on 2005-01-26
Ok i tried

No luck for the ATI ... yet

and for the share i got this

7151: protocol negotiation failed
SMB connection failed


for my samba i'm getting this...

---

### Post by hubris on 2005-01-29
i tried for my ATI drivers and now i'm getting this error:

The X server does not support the XRanderR extension. Runtime resolution changes to the display size are not available.


So i'm guessing i succesfully installed the drivers.
But then why am i getting this message??

If someone could help me out here i would be thankfull.

---

### Post by hubris on 2005-02-05
no one that can help me?

---

