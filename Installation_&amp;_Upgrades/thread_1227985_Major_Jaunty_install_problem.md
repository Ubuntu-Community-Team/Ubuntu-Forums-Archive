---
title: "Major Jaunty install problem???"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by acimna on 2009-07-31
After several forum requests, one failed Hardy installation and two failed Jaunty installations and _repeatedly _reading all the documents recommended to me, I tried to partition the Hard Drive from the CD booted System/Admin/Partition Editor as follows:

1 Primary Partition: NTFS (about 10Gig)

1 Extended Partition (about 200Gig) - swap (4Gig), / (5Gig), /home (100Gig), /boot (250Meg)

That left about 250Gig free space

Hit the apply button to get an error reading of a failed partition that wrote something I don't understand to the root and prompting me to read the details.

The recommendation was that I go to http:/gparted.sourceforge.net/larry/tips/save_details.htm

As the new machine shares a monitor, keyboard and mouse with this old Pentium II I'm working on, I shut down the new machine in order to go to the recommended website - only read that I should not have exited at all - and a lot of technical jargon I don't understand anyway.

This really is getting a bit much to bear right now, so don't even dare recommend that I opt for a different OS, okay? :D

I do not deny that I am uninformed, perhaps not that intelligent, over-eager and most likely have made some serious mistakes, but is there really no-one out there with the patience, courage and empathy to help this fool onto the right track ... ANYONE?

Ps. I downloaded Jaunty for the second time last night (it takes about 7 hours in Namibia) and burnt the 3rd CD at 4X only to get the same message I got with the Canonical CD - a faulty file on the CD.  So I've been working from a CD with a faulty file because it will take about 3-4 weeks for the Canonical replacement CD to ge here (they dispatched it today).

---

### Post by 73ckn797 on 2009-07-31
> **acimna said:**
> 1 Primary Partition: NTFS (about 10Gig)

1 Extended Partition (about 200Gig) - swap (4Gig), / (5Gig), /home (100Gig), /boot (250Meg)

That left about 250Gig free space


It appears, I assume, that you are going to dual boot with the NTFS partition. Can you provide a screen shot of the gparted partitioner and how it is all arranged?

And/or post the results of:
```
 sudo fdisk -l
```

---

### Post by acimna on 2009-07-31
No, I'm leaving the NTFS partition empty.  It's only there because the Ubuntuguide recommends it and I've got enough disk space to waste on the remote chance that I might need it someday.

Necessity may dictate that Suse be loaded, because downscaling to 80% and setting the icon size to small does not reduce tollbar size and hence does not provide more workspace in OpenOffice.

The Terminal does not accept sudo fdisk -1 ... or anything else, it seems.  Should the command be typed in somewhere else?

---

### Post by ajgreeny on 2009-07-31
> **acimna said:**
> No, I'm leaving the NTFS partition empty.  It's only there because the Ubuntuguide recommends it and I've got enough disk space to waste on the remote chance that I might need it someday.

Necessity may dictate that Suse be loaded, because downscaling to 80% and setting the icon size to small does not reduce tollbar size and hence does not provide more workspace in OpenOffice.

The Terminal does not accept sudo fdisk -1 ... or anything else, it seems.  Should the command be typed in somewhere else?
If you are not using, nor going to be using windows on this computer, you certainly don't need an empty 10GB NTFS partition at the start of the drive, or anywhere else, for that matter, so get rid of that straight away.  I can find no reference to your comment aboiut the ubuntuguide suggesting that, so am uncertain where it came from.

You can still make use of an extended partition for all your ubuntu partitions if you wish, but it's not really needed, nor is a separate /boot partition unless you are going to use the ext4 file system for your main ubuntu partitions, when it could be useful.  It is worth going for a separate / and /home partition as that makes things easier when, or if, you mess things up and need to reinstall; that way you can keep your /home and just install the system files again.  However a 5GB / partition is a bit stingy and I suggest 10GB for that.  You will also need a swap, but if you have a newish machine, don't go for the old recommendation of twice the size of your ram; if you have 2GB ram or more you will be unlikely to need more than about 1.5 - 2GB swap, particularly at the moment while learning about linux.  4GB swap is overkill, I think.

Finally it is not ```
sudo fdisk -1
``` but ```
sudo fdisk -l
```a lower case L at the end not figure 1.  Try that and it may help that command work for you.  However, I note you say that your CD has a faulty file, unusual on a canonical produced CD, I think, so check your drive if possible, but whichever way you do it you may still have problems because of that faulty file, so be prepared.

---

### Post by merlinus on 2009-07-31
```
sudo fdisk -l
```

l is a lowercase L.

Are you running from the live cd?

---

### Post by snowpine on 2009-07-31
If Ubuntu will be the only operating system on the computer (no dual boot with Windows), you can simply choose "Guided Install: Entire Disk" and let the installer make the decisions for you.

ps It's always good to copy and paste terminal commands, to prevent a typo like "1" instead of "l". :)

---

