---
title: "DVD Drive won't see stuff"
date: 2010-03-18
forum: Hardware
---

### Post by Joebonanno on 2010-03-18
First, let me just preface this by saying I'm a brand new ubuntu user and only started a few hours ago. I'm a total newb so please go easy on me. For reference sake, I'm using Ubuntu 9.10- the Karmic Koala.

I'm having issues with my cd/DVD Drive. Ubuntu seems to be able to see it. When I go system>admin>disk utility it is clearly shown. When I look into "computer" it is also shown as being there. (when a DVD disk is NOT in the drive)

However, I went to put a DVD in and that's when I started having issues. It would still show in the disk utility, but I couldn't open the DVD itself. It says the following in the disk utility:

CD/DVD DRIVE
5.8GB/5.4 GiB/ 5,801, 691, 136 bytes
Unpartitoned Media
SMART is not available
/dev/sr0

The disk:

BFBC2
5.8GB/5.4 GiB/ 5,801, 691, 136 bytes
ISO 9660 File System
Not Partitioned
/dev/sr0 mounted at /media/cdrom0 *
Mountable Filesystem
The volume contains a mountable filesystem
 label: BFBC2

*-note I tried fixing this myself by using some commands through the terminal. I don't remember what the commands were :( but could /media/cdrom0 have something to do with my problems?

 The problem is when I go to computer to open it my cd/DVD drive magically dissapears! Also, I can't manually eject the DVD from the drive with the button. The only way to eject the disk without rebooting and ejecting in dos seems to be to go back into disk utility and press unmount the filesystem when I have the DVD highlighted and then press eject when I have the CD/DVD Drive selected. Pressing eject when the disk has its filesystem mounted (whatever that means) gets me this message:

Error ejecting device
The device is busy.
Details: /dev/sr0 is mounted

Please help!

---

### Post by soltanis on 2010-03-19
Whoa whoa whoa slow down.

First of all, when a disk is "mounted" that means it's been incorporated into the filesystem tree, or in other words if there are files that are accessible on it, you can now access it.

Now, a note about any kind of removable drive is that if it's mounted, the file system is using it actively (changes are pending writing to the file, they are in use by some processes, or a combination of the above). You need to *unmount* it first before you can eject it (safely). On some computers, including mine, just hitting the button on the drive won't eject the CD while it's mounted for this reason. However, if the disc is in the drive, it should show up under the file browser with a CD icon that you can right click and hit "Eject".

About reading the disc: if you put in a DVD video, Ubuntu can't play it by default if it's encrypted. Also, it won't be able to play proprietary formats (s/as MP3), because they'd have to pay royalties to distribute that software with the installation.

Software exists that will decrypt your proprietary formats (DVDs, MP3s, etc).

```

sudo apt-get install ubuntu-restricted-extras libdvdcss

```

Please be aware that the legality of libdvdcss is in question in the United States -- there's a huge back and forth over whether it constitutes violations of the DMCA, because it "could" be used to create unauthorized copies of a DVD. Many people use it anyway because it's the only way to play DVDs they legitimately purchased.

Finally, the standard built-in media player will probably not play DVDs (I don't know why that is beyond the explanation of "it sucks"). As an alternative, I use VLC, which plays just about anything you ask it to.

```

sudo apt-get install vlc

```

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

