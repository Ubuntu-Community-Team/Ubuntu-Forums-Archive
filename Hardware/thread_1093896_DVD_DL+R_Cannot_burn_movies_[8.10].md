---
title: "DVD DL+R Cannot burn movies [8.10]"
date: 2009-03-12
forum: Hardware
---

### Post by mashiox on 2009-03-12
Hi all.

I have a Compaq C500 and I've gotten everything working the right way so I'm very pleased. I'm a regular Slackware user but wanted to put something simple and easy on my notebook.
That's my story, and I'm sticking to it.

But I'm having trouble burning DVD movies on it.
I just found out that it's a DVD+RDL burner, and that makes me t3h happy.
However, when I try to burn just a regular DVD+R k3b and any other burning software gives me [somewhat of] the same lame error.

"This project does not contain all the necessary VideoDVD Files
The resulting DVD will most likely not be playable on a HiFi DVD Player
Could not determine the size of the resulting image file"

Here's the debugging output:

```

mkisofs
-----------------------
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-mashiox/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
/usr/bin/genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents
/usr/bin/genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
/usr/bin/genisoimage: Can't open VMG info for '/tmp/kde-mashiox/k3bVideoDvd0/'.
/usr/bin/genisoimage: Unable to parse DVD-Video structures.
/usr/bin/genisoimage: Could not find correct 'VIDEO_TS' directory.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid line-pi_1 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-mashiox/k3bas9SBa.tmp -no-cache-inodes -udf -iso-level 1 -path-list /tmp/kde-mashiox/k3bTvvtvc.tmp -dvd-video -f /tmp/kde-mashiox/k3bVideoDvd0 


```

An .avi file exists in the VIDEO_TS directory of the project, and I get the same error when I try and put the file in the root directory of the DVD.
What's the diagnosis mates?

---

### Post by taurus on 2009-03-12
Are you trying to burn an .avi or a DVD?  I don't think you can put .avi in VIDEO_ST and expect it to burn as a DVD movie, hoping to play it on a standalone DVD player.  If you have an .avi movie, you need to use devede (or others) to convert it to .iso and then burn the .iso to a DVD as an image file.  Then, it should be able to play on your DVD player.

Devede is in the repos.

---

