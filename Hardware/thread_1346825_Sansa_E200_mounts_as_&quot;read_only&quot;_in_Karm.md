---
title: "Sansa E200 mounts as &quot;read only&quot; in Karmic"
date: 2009-12-05
forum: Hardware
---

### Post by Mrsongs on 2009-12-05
My Sansa E200 mounts as a read only filesystem on Karmic, whether I mount its rockbox firmware or the original Sansa firmware. Attempts to change permissions via gksudo nautilus have been fruitless. Help! Running the 64 bit version of Karma on an Acer Aspire 5532.

---

### Post by VirusCollector on 2009-12-06
Finally someone else with this problem. Running the same OS on a Gateway m-6846.

I followed a link for fixing the mounting problems that involved editing some kind of gphoto file, and this worked but only allows mounting read-only. Also, the OS says that my Clip is a "gphoto" filesystem... which makes no sense to me at all. It doesn't seem to be mounted through normal means, I can't access it using mount or umount commands.

---

### Post by mikewhatever on 2009-12-06
Check out this howto -> [https://help.ubuntu.com/community/SansaClip](https://help.ubuntu.com/community/SansaClip).

---

### Post by Mrsongs on 2009-12-14
Well, it turns out that the "read only" tag was kicked in because the Sansa was full. I went to Windows(blush), removed the offending file, and went back to Linux. At that point, no problem.

---

