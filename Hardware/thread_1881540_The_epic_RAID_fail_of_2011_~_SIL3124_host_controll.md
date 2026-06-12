---
title: "The epic RAID fail of 2011 ~ SIL3124 host controller"
date: 2011-11-15
forum: Hardware
---

### Post by DudeBud on 2011-11-15
So, i have 3TB worth of problems... help plz

Firstly, I’m new to Linux so if I don’t use proper terminology I apologize now.

I built a home server with my previous desktop rig and installed Ubuntu.  I was to be storing family docs on this server, along with family pictures, and other irreplaceable files.  I was using a PCI SATA 2 RAID host controller which I thought was supposed to be a hardware RAID solution. 

The problem;
I have Ubuntu installed on a single drive and I built a RAID1 array using the silicon image (SIL3124) chipset on the PCI card using two spare 3TB drives.  Fired up Ubuntu, no problems so far.  In disk utilities it showed both 3TB drives, but only one was able to be partitioned and written to, the other said RAID component. So I assumed the RAID1 array was working.

I installed Samba on Ubuntu to share files across my windows network, and began transferring the archive core that was stored across about 4 family PC’s back onto this one main 3TB server drive.  I successfully transferred all of the backed up data to this array. (approx 2.2 TB) I updated my Samba config file and restarted Samba… and then this is where problems start.

The drive I was writing to suddenly disappears. I do a hard restart and my host controller card says my RAID1 array failed.  Ok, whatever… I’ll just rebuild it. In the rebuild options I select the second drive that showed up previously in disk utilities as RAID component, as I suspected the first drive to be the failed component, not the drive that I partitioned and was writing data to.  I figured since it was a RAID1 array that it wouldn’t matter… The process takes about 16 hours…. And on restart all of my data is gone. 

In disk utilities the array shows up as an unpartitioned drive. 

This is where I start freaking out…

When I did partition the drives in Ubuntu I partitioned them using the windows friendly NTFS table just in case I ran into problems.  After the rebuild I ripped one of the drives out and hooked it up to a windows PC and the same thing happened… it showed up as unpartitioned space.

What I think happened;
I think that my SIL3124 RAID chipset card may not have been actually writing data to the second drive. So when I did a rebuild, I think I actually copied an unpartioned blank drive over my partitioned data drive. Wiping all my data… (basically a low level format)

I hope this is not what happened… 

Is there any way to recover my data?

Any help here would be greatly appreciated.  These are family files that cannot be replaced over the last 10 years.  I might be a dead man walking….

I did not know about madam during build otherwise I would have used it, as it sounds way more reliable then this junk card.  
Specs;

4 channel PCI SATA RAID host controller card, (link to it here): [http://www.amazon.com/Profile-Channels-Serial-Controller-SY-PCI40026/sim/B003IT6Z9U/2](http://www.amazon.com/Profile-Channels-Serial-Controller-SY-PCI40026/sim/B003IT6Z9U/2)
Mobo: intel D975XBX 
Ubuntu distro: 11.10

---

### Post by DudeBud on 2011-11-19
IS there any way to recover the data?
Or am i just a sad windows user gone linux, only to run back to windows server.

:(

---

### Post by Seq on 2011-11-19
Hey. Welcome to the club.

You could always try testdisk. It has saved me in the past with recovering deleted files, or rescuing files from corrupted filesystems.

Generally recovery is pretty simple as long as the data has not been actually overwritten. It appears that you may have instructed the RAID controller to overwrite everything, so you might be out of luck. I'd point out that RAID is not a backup strategy, but you probably thought about that already.

FWIW, I have a cheap SIL card as well, but I use it in plain non-raid mode, and used mdadm to create two RAID1 arrays. My reasoning was if the raid controller died, the drives might be useless until I found another SIL controller. Whereas mdadm will work on any Linux computer.

Also, there are utilities for mdadm to email you if any drive issues occur (failure, etc). That doesn't help now, but good to keep in mind for the future.

---

### Post by DudeBud on 2011-11-25
Hey, 
Thx for the help.

I've been trying to use testdisk for a few days now ever since you suggested it.  I'm not the greatest with this piece of software but i think i have something.  After a "deeper search" it shows me my old partition but i can't mount or extract anything from it bc it says my geometry is wrong.

I guess its still looking for 2 raided drives?
Its telling me that there is a mismatch "drive >6000GB" when I'm only looking at one of the drives.

Any idea how to proceed?

---

### Post by Seq on 2011-11-27
> **DudeBud said:**
> Hey, 
I guess its still looking for 2 raided drives?
Its telling me that there is a mismatch "drive >6000GB" when I'm only looking at one of the drives.

Are you sure you had the drives configured as RAID1 and not as RAID0?

---

### Post by DudeBud on 2011-11-28
> **Seq said:**
> Are you sure you had the drives configured as RAID1 and not as RAID0?

I am positive.
It was a RAID1 setup.

I even rebuilt the array in the sil controller to test the effects, but still got the same result.
I'll post my testdisk output in hopes you or someone can help me figure this out. :)

------------------------------------------------------------------------------

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgcsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 3000 GB / 2794 GiB - CHS 364801 255 63

The harddisk (3000 GB / 2794 GiB) seems too small! (< 6001 GB / 5589 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition  -                Start                     -  End  -  Size in sectors
NTFS                - 364801  80  30 -      729602  160  25 -    5860533101




[ Continue ]
NTFS, 3000 GB / 2794 GiBcarter@glad0s:~$
--------------------------------------------------------------------------------

I started testdisk up using sudo and selected the drive that i wrote to.
Yes, i did format and partition the array in NTFS using disk utility..... i thought that this might help in the samba windows environment. (whatever... a n00b move.)

So i think that is the partion with my data on it. I just don't know how to get it.

any wisdom?

---

### Post by DudeBud on 2011-12-29
........Data lost......

i had a good cry, and now i'm moving on.

---

