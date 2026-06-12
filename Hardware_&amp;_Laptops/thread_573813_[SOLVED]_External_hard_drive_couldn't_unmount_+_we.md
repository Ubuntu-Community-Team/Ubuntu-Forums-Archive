---
title: "[SOLVED] External hard drive: couldn't unmount + weird problems, now can't mount"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by alexmoon on 2007-10-12
I have a Maxtor 120gb external hard drive. When I got it, I followed instructions from the forum and, using GParted, formatted it into ext3 format (at least, I'm fairly sure it was into ext3 - I can't check now, I'm afraid).

It had some problems copying certain files from my desktop, for example any files with a "?" in the filename. It started to get stuck on these files, and rather than letting me 'skip' when copying and go onto the next file, it would just stay on that one. I decided to try to format it again.

However, when I open Gparted and try to unmount the drive, it just says: "scanning removable media" - and then nothing happens. Even when I leave it for hours. 

I tried turning off the "mount removable media when inserted" option in system -> preferences -> removable drives and media. I also tried this line:

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi.backup

from the post here: [http://ubuntuforums.org/showthread.php?t=459258](http://ubuntuforums.org/showthread.php?t=459258)

The result, even when I allow "mount removable media when inserted", is that it won't mount. It suggests that I try: "dmesg | tail", which gives this output:
[  570.416000] sdb: Mode Sense: 17 00 00 00
[  570.416000] sdb: assuming drive cache: write through
[  570.416000] SCSI device sdb: 234441648 512-byte hdwr sectors (120034 MB)
[  570.420000] sdb: Write Protect is off
[  570.420000] sdb: Mode Sense: 17 00 00 00
[  570.420000] sdb: assuming drive cache: write through
[  570.420000]  sdb: sdb1
[  570.440000] sd 4:0:0:0: Attached scsi disk sdb
[  570.440000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  570.848000] VFS: Can't find ext3 filesystem on dev sdb1.

Any suggestions on how to fix this? I've looked around the forum, I hope I haven't missed the answer.

Thank you for any help you can give me.

---

### Post by alexmoon on 2007-10-14
Ok, in the end I managed to solve this by the time-honoured method of "fiddling around with some stuff". I plugged in the harddrive, opened GParted, and as usual it started 'scanning external media' and got stuck there. Then I unplugged the harddrive, which meant that GParted stopped scanning. The drive, however, still showed up on GParted. I marked it for formatting to ext3, plugged the drive back in, and then "edit -> apply". 

It seems to have worked out, and after some fiddling around with permissions it's running fine.

---

