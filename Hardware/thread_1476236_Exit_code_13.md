---
title: "Exit code 13"
date: 2010-05-07
forum: Hardware
---

### Post by kurtisnathan on 2010-05-07
I bought an external drive a while back. Today, while a file transfer was in progress, I accidentally cut power to the dive. I plugged it back in, but my computer wouldn't even see it. So I rebooted the computer, and when I plugged in the drive, it wouldn't mount, giving the following message:

Unable to mount Expansion Drive

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Now I'm a major noob, and don't know what to do to fix it. And I know it's not the drive, because I was able to mount it in Windows. I safely removed, and tried again in Ubuntu, and it still gave the same message. Help!

---

### Post by kurtisnathan on 2010-05-07
I solved my own problem! To anybody who has the same problem, all I did was mount the drive in windows, then deleted the last file that was being transfered. I suspected it must have been the corruption that was hindering the mount, and it was.

---

### Post by LouisBlank on 2011-12-20
Well, you might be a noobie, but you helped one person.  My error was almost identical - saved my life. 

I have a 2TB that I use to back up 4 computers and since I never start the Windows partition on my laptop, I would not have thought about that.

Linux usually does things better than Windows, so it surprises me that a simple corrupt file would cause the drive not to mount.

Incidentally, the file I was writing when it happened was a .tar backup - when I mounted in Windows, that file didn't show up on the list at all.  I just ran a quick scandisk, then mounted the drive back on my Linux box. 

Thanks! Every contribution helps

What Windows did...

[IMG]http://dl.dropbox.com/u/9159375/122011DriveError.jpg[/IMG]

---

