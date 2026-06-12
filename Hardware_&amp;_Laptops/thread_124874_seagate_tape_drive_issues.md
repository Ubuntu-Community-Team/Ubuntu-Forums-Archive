---
title: "seagate tape drive issues"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by bcochran on 2006-02-02
I've been given the task to retrieve some data off of a tape for a friend. I was given the tape and the drive. The person who owns the tape only knows that the tape was backed up on a redhat box. not sure what version or format. All I know is, its a travan ide tape drive. dmesg | grep tape shows it as hdd: Seagate STT20000A.
Im having trouble getting the tape drive itself functioning properly in ubuntu. to get ht0 to show up in /dev I have to perform the following.
sudo modeprobe ide-scsi
cd /dev
sudo ./MAKEDEV ht0

From there I can half-*** get the drive to work. mt won't really function properly. mt -f /dev/ht0 rewind wont rewind the tape. and mt -f /dev/ht0 status only gives output if I have the read only lock on the tape turned on.

what do I need to do to get this tape drive to function properly so I can get the info off of it?
a few times I was able to get dd if=/dev/ht0 bs=1k count=1 to display some info... but for some reason if I try it more than once it tells me "premature end of tape" or something like that.
Also is there a way to tell what program I should use to remove the data from the tape? I tried running tar -tf /dev/ht0 on it, but it said it wasn't a tar archive.

---

### Post by bcochran on 2006-02-06
Anyone?

---

