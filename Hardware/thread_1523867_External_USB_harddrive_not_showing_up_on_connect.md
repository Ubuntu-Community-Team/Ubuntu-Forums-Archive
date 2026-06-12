---
title: "External USB harddrive not showing up on connect"
date: 2010-07-04
forum: Hardware
---

### Post by couzin2000 on 2010-07-04
I have this LaCie USB2 box containing a Seagate 160GB hd. I can access this pc from a friend's Ubuntu Lucid box, and I could access it before when I had Jaunty on my box - but I lent him the drive, and upgraded my box to Lucid. He never used the drive at all.
I got it back today, and now I don't get the desktop icon showing me this drive. I do have another one which works (a 1TB drive in a similar USB2 ext box), but that one I can access - it works fine.

Here's what I get in [FONT="Courier New"]lsusb[/FONT]:
```
melanie@melanie-desktop:~$ lsusb
Bus 002 Device 002: ID 045e:009d Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 006: ID 059f:0651 LaCie, Ltd **
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
melanie@melanie-desktop:~$ 

```

Here's my [FONT="Courier New"]fdsik -l[/FONT]:
```
melanie@melanie-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x253c253b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdc: 8119 MB, 8119738368 bytes
16 heads, 63 sectors/track, 15733 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15732     7928896+   c  W95 FAT32 (LBA)

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdf1   *           1       19457   156288321    c  W95 FAT32 (LBA)** *(I think this is the LaCie drive)*
melanie@melanie-desktop:~$ 
```
I have no idea if this is permissions related. I need some input, I have run out of ideas. Help me out!

---

### Post by CharlesA on 2010-07-04
Have you tried it on a different machine?

Usually if a USB hard drive doesn't show up, it is more than likely toast.

---

### Post by couzin2000 on 2010-07-04
> **CharlesA said:**
> Have you tried it on a different machine?

Usually if a USB hard drive doesn't show up, it is more than likely toast.

Yes I did. As I said in my previous post, the drive worked on my friend's machine yesterday. Plus, it does show up - the computer sees it, I'm just not getting the desktop icon. It's like the pc is not mounting the drive at all, so I cannot access the files inside.

Here's more info: I tried turning on Virtualbox (latest), and the Windows XP virtual machine sees the drive -- it even installs the drivers for it. The problem is, when I go to the My Computer icon, I see another drive, it IS most definitely the USB drive, but XP calls it "Local Drive (E:)" - and I don't see the normal label which is supposed to say "USBDISK". Double-clicking it gets me a warning that the drive is not accessible or not ready.

But like I said, Windows DOES see the drive, Virtualbox too, so I'm not sure where the problem lies.

---

### Post by efflandt on 2010-07-05
You said it was a 250 GB drive, but the one you pointed to in fdisk that you thought it was is 160 GB.  Whichever it is (did your friend switch it on you?), sometimes a failing drive will show up in fdisk even if there is something wrong with it, like bad sectors.  Was it dropped or bumped around when on?

Try connecting it to Windows and assuming that it is drive e:, try doing **chkdsk /f e:** from a command window.

My boss' grandson had a laptop drive that WinXP refused to boot, and from an Ubuntu live CD I could not hardly copy any files from it before it hung trying to read.  When I put it in a USB enclosure, Linux fidisk on another laptop could see it, but it would not mount in Linux or Windows.  A few weeks later I connected it to Ubuntu on my desktop and it mounted and I was able to copy most of the user's WinXP home dir.  So if chkdsk from Windows can fix it, or you let it sit for awhile, maybe you will get lucky.

---

### Post by couzin2000 on 2010-07-05
> **efflandt said:**
> You said it was a 250 GB drive, but the one you pointed to in fdisk that you thought it was is 160 GB.  Whichever it is (did your friend switch it on you?), sometimes a failing drive will show up in fdisk even if there is something wrong with it, like bad sectors.  Was it dropped or bumped around when on?

Try connecting it to Windows and assuming that it is drive e:, try doing **chkdsk /f e:** from a command window.

My boss' grandson had a laptop drive that WinXP refused to boot, and from an Ubuntu live CD I could not hardly copy any files from it before it hung trying to read.  When I put it in a USB enclosure, Linux fidisk on another laptop could see it, but it would not mount in Linux or Windows.  A few weeks later I connected it to Ubuntu on my desktop and it mounted and I was able to copy most of the user's WinXP home dir.  So if chkdsk from Windows can fix it, or you let it sit for awhile, maybe you will get lucky.

160GB - sorry, my mistake. It's the same drive.

This is weird because it has always worked, then I didn't use it for 2 months (no power up), then I use it one day and it works flawlessly, then nothing.

I will try and access chkdsk from a direct boot into windows, and not from a virtual partition. Good idea. I'll check back and let you know.

In the meantime, any other suggestions? what's the linux equiv of chkdsk?

---

