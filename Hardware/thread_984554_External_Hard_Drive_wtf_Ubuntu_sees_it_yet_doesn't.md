---
title: "External Hard Drive wtf: Ubuntu sees it yet doesn't... Please help"
date: 2008-11-16
forum: Hardware
---

### Post by KeithA45 on 2008-11-16
I've got an external that's been weird and un-detectable by windows or apple for a while, but I plug it into Ubuntu and sure enough, it shows up (with most of the files missing, but I don't care I just want to wipe it and start over so my other computers can use it)

However, it shows up as an un-editable "500.0 GB Media" that won't show up in GParted. Is there anything I can do to wipe out the file system and start over?

At this point I'm ready to take a giant magnet to this thing if that's your best suggestion. Please help

Thanks,
 - Keith

---

### Post by detroit/zero on 2008-11-16
Sounds like that drive is all messed up. GParted also has a livecd version that you can boot into. Maybe you'll have better results with that. There are also forensic-recovery type livecds that you can download and run in that should give you more tools to play with..


[LIST]
[*] There's [Helix3]("http://www.e-fense.com/helix/") (I've never used this one but I'm downloading it now to mess with - says it's Ubuntu Based...);
[*][FCCU Linux]("http://news.softpedia.com/news/FCCU-GNU-Linux-32327.shtml") - Knoppix based;
[*][BackTrack]("http://www.remote-exploit.org/index.php/BackTrack") is good for **a lot** of things but don't expect any help in their forums unless you consider "[RTFM]("http://www.roflmaobbq.com/")!" help;
[*][Here's a list]("http://http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/") of the 10 best security distros, most (if not all) of which run from livecd;
[*] There's always [SecurityDistro.com]("http://www.securitydistro.com/") for a small selection/news about new distros;
[*] And, of course, [Google is your friend]("http://www.darknet.org.uk/2006/03/10-best-security-live-cd-distros-pen-test-forensics-recovery/").
[/LIST]
Good luck.

---

### Post by Carl Hamlin on 2008-11-16
> **KeithA45 said:**
> I've got an external that's been weird and un-detectable by windows or apple for a while, but I plug it into Ubuntu and sure enough, it shows up (with most of the files missing, but I don't care I just want to wipe it and start over so my other computers can use it)

However, it shows up as an un-editable "500.0 GB Media" that won't show up in GParted. Is there anything I can do to wipe out the file system and start over?

At this point I'm ready to take a giant magnet to this thing if that's your best suggestion. Please help

Thanks,
 - Keith

With a drive acting that twonky, I'd hesitate to put anything on it I cared about.

If the drive is IDE, what position are you using it in?

---

### Post by KeithA45 on 2008-11-16
> **Carl Hamlin said:**
> With a drive acting that twonky, I'd hesitate to put anything on it I cared about.

If the drive is IDE, what position are you using it in?

To be honest with you, I have no idea which kind of drive it is and I'm not sure what you mean by position (I'm new to Linux). For now, all I know is that I just showed up on the desktop, it says the Location is on the desktop, the Mount Point is "/media/disk", the File System is "hfsplus", and the mount options are are:

```
ro nosuid nodev relatime umask=22 uid=0 gid=0 nls-utf8
```

---

