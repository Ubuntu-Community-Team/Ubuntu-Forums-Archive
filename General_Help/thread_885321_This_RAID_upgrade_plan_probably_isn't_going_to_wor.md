---
title: "This RAID upgrade plan probably isn't going to work huh?..."
date: 2008-08-10
forum: General Help
---

### Post by Erik765 on 2008-08-10
After reading around some, the idea I had about 'upgrading' my current single drive system to a RAID 0, sounds like it isn't going to work.
First, I'll tell you what I was thinking and then I'll vent a little about why I think it's lame that it wouldn't work.

I currently have a 500gb drive with a 160gb Kubuntu partition and a 160gb, XP partition (don't worry I only boot into XP maybe a few times a year). I also have an extra 320gb drive that I'm not using. My plan was to obtain another 320 gb drive set the two 320s up as a RAID0 with my integrated RAID controler (don't worry, it's a hardware-based controler), take the two 160gb partitions and image them over to the newly created RAID0 on the 320s and use 160 out of my other 500gb for extra space and the rest for a periodic image back up.

Will this work?

Sounds good in theory, until reading around and finding out that the operating systems aparrently need to be aware of the RAID during their installation. Why? In my opinion, it seems like the RAID controler should completely take over the drives and make the RAID invisible to the operating systems, instead making them appear as a single drive.

Am I way off here? Will this work or won't it. Why would the operating systems even need to be aware of a RAID and not just leave the data flow up to the RAID controler?

let me know your thoughts as I'm really interested in doing this... if it'll work.

Thanks.:confused:

---

### Post by fjgaude on 2008-08-10
As an OS starts to load it has to find the media upon which it it to run. To do that it has to know the drive, or have a driver to assemble the device that it is to go upon. There is no other way, even with Windows and Mac OS.

So you plan likely is doomed to fail. Sorry about that.

Now if your raid controller comes with a driver, a .deb one, you are in luck.

---

### Post by psusi on 2008-08-15
Moving Linux over is as simple as booting from a livecd and copying over all of the files from the old partition to the new one, then reinstalling grub.  Moving Windows is more challenging.

---

