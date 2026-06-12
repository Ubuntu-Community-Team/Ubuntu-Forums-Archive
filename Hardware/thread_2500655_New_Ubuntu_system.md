---
title: "New Ubuntu system"
date: 2024-09-08
forum: Hardware
---

### Post by skysorcha on 2024-09-08
Hello All, I have 2 systems.

My main system is my gaming system, a AM4 5800x. As you can guess is a Windows 10 machine, for now I'm not changing this machine to linux, At least not now.

My old FX gaming system, I'm now using it as a test machine for Linux.

Since installing Ubuntu on my FX system I have noticed that 2 things.

1.  My usb 2.0 ports don't work but my usb 3 ports to work. I just find this strange.

2. my Transcend 512gm stick, it wont mount I think is becauce I put NTSF partaion, but I not sure.

Thanks

Ash

---

### Post by Autodave on 2024-09-08
As far as he USB stick is concerned.....did you have it connected to a Win machine and then not properly unmount it?  That will cause it not to work.  The NTFS is fine....all of mine are formatted to that.  Try plugging the stick into your Win machine and then unmount it properly and it should work in your Linux machine.

---

### Post by TheFu on 2024-09-08
Ok, and what have you done to figure out the issues?

If NTFS won't mount, it could be that MS-Windows left the file system open.  You'll need to use MS-Windows and close it before Linux can access it.  That's the normal, most likely, answer for HDDs or SSDs with NTFS that cannot be accessed from Linux.  It isn't the only possible issue.  

[LIST]
[*]I'm not sure what "NTSF" is.  Do you mean NTFS?  If so, did you load the correct drivers for it and run a mount command?  What was the mount command?  Details matter. Providing incorrect details can lead to wrong answers.  There are some file system drivers that end in "SF", so perhaps you aren't talking about NTFS.  I can't tell for certain. Misspellings are a problem for us all.
>  I think is becauce I put NTSF partaion, but I not sure.
You need to be sure.
[*]Did you look at the system log files for any warnings and errors?  This should be the 2nd step for anything that doesn't work in any Unix-like OS.  help.ubuntu.com has information at reviewing logs files.
[*]Have you googled for the exact hardware that isn't working to look for Linux incompatibilities or driver issues?  Exact details are necessary.  I have a blue car, what's the largest box I can fit into the back?  See how that isn't useful information to answer the question?  Facts are needed.
[/LIST]

Some more thoughts.
USB controllers aren't compatible with all USB flash storage.  Try different USB flash storage in the USB2 ports.  It could just be the flash drive.
Whenever posting for help, please don't make us assume things.  You should provide some basic, exact, details about the hardware that is a problem. The vendor, model number, and which driver is loaded for it at a minimum.  You should provide the OS release and DE (if any) so that DE-specific issues can be addressed - or DE-specific answers can be provided.  The way that Gnome can mount file systems is different from the way that KDE mounts file systems, for example. They have different GUI tools.  If you don't, then we'll have to answer with non-GUI methods, which is fine and easier for us, but most people from MS-Windows aren't as comfortable doing that.

It is always helpful if you say what level of Linux experience you are.  That way, the suggestions will be tailored for your skill level.  If you are a noob, I wouldn't respond at all, since it will just make you and me frustrated with each other. That doesn't help anyone.

If you don't understand something said, it is fine to ask, but realize that sometimes a very short question has a very long answer and nobody here is paid.  Best to try to find the answer or at least the background for the answer on your own.

Ok, some commands that can help gather information.
```
lshw
inxi
lsusb

```
These all have options to getting specific information. Usually they don't need sudo/root privilege to run, sometimes they do to gather more detailed information. I don't think they need it this time.  You can find lots of examples with options in these forums.

Don't assume people know your CPUs or other hardware  Between Athlon (owned 3 Athlon systems) and Ryzen ( 2 Ryzen systems now), I only used Intel CPUs (Core2Duo and better), so the entire FX series is just a label to me.  That's about 8 yrs of CPUs I know nothing about.  I know even less about GPUs. Beyond showing something on the screen, I don't really care about GPU performance. Nobody can know everything, right?

Anyway, come back with the facts, best to post the details from **inxi -bz** as a start. Please use forum code-tags, like I've done above so the information is readable.  The Adv Reply {#} is how.

NTFS is fine for HDDs and SSDs, but it will cause pre-mature wear on normal flash media.  For that type of media (SDHC and cheap USB flash storage), you'll want a non-journaled file system.  f2fs for Linux-only use or exFAT for cross platform, shared, use.

---

### Post by Yellow Pasque on 2024-09-09
See if you have any settings for legacy USB in the BIOS. Also, I remember some boards from the Socket AM3+ era had USB/IOMMU issues: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/859137)

---

