---
title: "166MHz MMX (ha) &amp; 40MB Latitude LM Distro"
date: 2011-09-17
forum: Hardware
---

### Post by silekonn on 2011-09-17
Hello,

This is to inquire if Xubuntu or some other Linux system would be usable for an /old/ system.  Basic internet (no flash) and email are the only requirements.  Xubuntu is "low end" but this is "ancient, end."  Low-experience installs are appreciated.

It is a Latitude LM with a non-bootable CD-ROM.  It has a partially functional hard disk drive (partitioned before bad sectors) and an installation of Windows 98.  There is no floppy disk drive but one could be ordered if it were necessary.  "Command Prompt Only" D.O.S. ([http://puppylinux.org/wikka/Pup4dos](http://puppylinux.org/wikka/Pup4dos)) boots with a CD-ROM driver.  A type II/III P.C.M.C.I.A. card with an ethernet port will be used.

Are there any suggestions?  I am able to reinstall Windows but could be converted.  All helpful comments are appreciated.

Thank you,

Ryan

---

### Post by papibe on 2011-09-17
Is that a pentium MMX right?
How much RAM do you have?
What is the maximum RAM you could put on it?

Regards.

---

### Post by silekonn on 2011-09-17
> **papibe said:**
> Is that a pentium MMX right?

How much RAM do you have?
What is the maximum RAM you could put on it?

Regards.


See thread title.  P166MMX w/ 40MB of ram.  Upgrades to the R.A.M. are too expensive.

Thanks,

Ryan

---

### Post by papibe on 2011-09-17
Welcome to the forums!

I'm afraid that's too low on RAM, even for the lightest version of Ubuntu called Lubuntu. Check the system requirements [here]("https://help.ubuntu.com/community/Installation/SystemRequirements").

Regards.

---

### Post by silekonn on 2011-09-17
> **papibe said:**
> Welcome to the forums!

I'm afraid that's too low on RAM, even for the lightest version of Ubuntu called Lubuntu. Check the system requirements [here]("https://help.ubuntu.com/community/Installation/SystemRequirements").

Regards.

I am not expecting to use release.  I am requesting a recommendation on a build version (Lubuntu 5, 6, 8?)

Is Xubuntu lighter than Lubuntu?

Thank you,

Ryan

---

### Post by papibe on 2011-09-17
> **silekonn said:**
> I am not expecting to use release.  I am requesting a recommendation on a build version (Lubuntu 5, 6, 8?)

Is Xubuntu lighter than Lubuntu?

Thank you,

Ryan
Lubuntu is lighter than Xubuntu.

Lubuntu is the lighter distribution of the official Ubuntu family. 

None of the official Ubuntu distros will work on that hardware, sorry.

Regards.

---

### Post by oldos2er on 2011-09-17
> **silekonn said:**
> This is to inquire if Xubuntu or some other Linux system would be usable for an /old/ system. 

No.

---

### Post by silekonn on 2011-09-17
papibe, oldos2er et. al,

Is there some reason that an earlier version will not work?  Can you offer some explanation?

I fully expect that Ubuntu version 1.0, v. two, five, eight or a derivative supported hardware of this age.

Thank you,

Ryan

---

### Post by JC Cheloven on 2011-09-17
Hi, I love to put back to live old computers :)

With your amount of memory, you should better look at really small distros. [SliTaz]("http://www.slitaz.org/"), or [TinyCore]("http://distro.ibiblio.org/tinycorelinux/welcome.html") come to mind. I tried both in the past. They're both nice, although quite spartan (which is what you need, really).

The [Ubuntu Contributed Documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems") is a great source of info. I quote something that could be of special interest for you if you want to try ubuntu (well, an abstract of the summary of the index of Ubuntu lol) on that machine: 
> Installing Ubuntu on any system requires at least 32 MB of memory: The text-based installer included with the alternate (install) CDs needs that much space to run reliably. Smaller memory configurations run into problems, and while not impossible, it can be very difficult to complete an installation with less than the minimum RAM requirement.

Depending on the hardware requirements, you can expect a sparse Ubuntu system to boot to a graphical desktop on anywhere from 19 MB to 54 MB. That requirement will fluctuate with the system demands, and increase while the system is active. Swap space is crucial to low-memory machines, so don't be stingy when setting up your system. 

So: Alternate Disk (not live cd) to install a comand-line ubuntu system. Set a swap space in the disk durng install (256Mb or more). Then, try to add a window manager only (not a full desktop environment). It could be Openbox. Then midori as a web browser. If you need an email clien, sylpheed. Don't expect marvels but it could work.

BTW, I don't think even the oldest version of ubuntu (with gnome, etc) could run on your pc. Plus using an unsupported operating system is not as nice...

And of course, there is [freeDOS]("http://www.freedos.org/"). I doubt it can get your interest (you have win98 ), but just in case.

Cheers
JC

EDIT: If you really want to try an old ubuntu system, download the alternate cd of the first release (warty, back from 2004) [from here]("http://old-releases.ubuntu.com/releases/4.10/").

---

