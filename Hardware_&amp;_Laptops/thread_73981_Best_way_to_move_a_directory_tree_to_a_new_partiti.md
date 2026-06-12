---
title: "Best way to move a directory tree to a new partition?"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by Kensey on 2005-10-10
I have a hand-me-down laptop running Windows XP and Hoary (a Compaq Presario 12XL401... all you Presario 1200 owners, stop cringing, help is on the way). It has a 10 GB hard drive which I partitioned 8 GB to XP and 2 GB to Linux. I have a basic but still pretty functional install of Hoary on there, but it's never had more than 250 MB free (the initial default install failed for lack of disk space, I had to reinstall in server mode and add the X environment after that). As I add applications I find that has gone down to more like 160 MB. So I decided to cut a chunk of my NTFS partition off and reformat it as ext3 to become my new /usr partition.

ntfsresize seemed to go OK.  After it completed, I edited the partition table.  The initial table looked like this:

hda1: Primary, Windows, 7.7 GB
hda2: Extended, 2.1 GB
hda5: Linux, 2.1 GB

I edited this to the following:

hda1: Primary, Windows, 5.7 GB
hda2: Primary, empty, 2.0 GB
hda4: Primary, Linux, 2.1 GB

That didn't work.  Grub would give an error 22 on boot.  I booted the Live CD and fdisk'ed it to this:

hda1: Primary, Windows, 7.7 GB
hda3: Primary, empty, 2.0 GB
hda2: Extended, 2.1 GB
hda5: Linux, 2.1 GB

This boots Linux fine (and I assume Windows too -- and if it doesn't I'm not *that* broken up about reinstalling XP from scratch.  In any case the XP partition still mounts fine under Ubuntu so I could grab data off it if needed).

However, notice the out-of-order partition numbers.  Right now hda3 exists but I'm not trying to do anything with it -- it doesn't even have a filesystem yet.  Will grub or anything else care that partition 3 is physically ahead of partition 2 on the disk?  (I'll still be booting off hda5, but I want to move /usr to the new partition.)  I also notice that even though fdisk identifies my root partition as hda5, once Ubuntu is booted it calls it /dev/hda4 (the Windows partition is still /dev/hda1) -- is there a mapping table somewhere?  What's it for and what do I need to do to it to make Ubuntu recognize the new partition and mount it sensibly?  Is it just pulling this from fstab?  I seem to recall that my old fstab actually did refer to the Linux partition as /dev/hda5, but before my first ill-fated partition edit I changed it to use /dev/hda4 as the / partition (which would have been the / partition's real device name had that worked).  I never changed it back but it booted anyway.  Is this Grub doing something to make it "just work"?  If I change it back to /dev/hda5 in fstab, will it become /dev/hda5 to Ubuntu again?

What I'm aiming for is the following: I want that empty partition to become an ext3 filesystem with some useful set of directories on it.  My first thought is to move /usr to it, which would leave about 500 MB of it free, which would probably be enough for the foreseeable future (around Christmas I'm planning to get a Dell Latitude laptop which will have 60 GB, at which point space considerations will be largely academic).  Do I need to reorder/renumber the partitions, and if so, how do I do that in such a way that I can still boot afterward?  Once the partitions are ready to go, what's the best way to create an ext3 filesystem and move the selected directory to it?

Should I move something other than /usr?  Everything else is under 10 MB of usage except /var with 100 MB, /lib with 72 MB and /home with 24 MB.  Under /usr I have /usr/lib with 526 MB, /usr/share with 524 MB, /usr/src with 295 MB, /usr/bin with 76 MB, /usr/X11R6 with 50 MB, and /usr/include with 13 MB.  Maybe I should move /usr/lib, /usr/share and /usr/bin to the new partition and symlink them from the old?  Some other combination of files?  What's the accepted best-practice on this?

Yeah, I know this gets a little into partition-size holy wars.  This laptop isn't a server so I'm not concerned about /var/log getting too big or anything like that, and it's not going to be in use long enough to be seriously squeezing the total capacity of that 4.1 GB.  Heck, my old PII from 1999 didn't really start squeezing the capacity of its 8 GB drive for 5 years, although with a nice shiny Maxtor 80 GB drive I'm thinking about moving the whole kit-n-caboodle over to the new drive there, using it for a media server, and using the old drive as /tmp + swap or something.  So any answers to this will help there as well.

Lots of questions.  I imagine a lot of this is out there in FAQs in various places, but I can't find a unified "how to recarve your hard drive with a whole new partitioning scheme" FAQ or HOWTO anywhere :)

---

