---
title: "Boot sequence"
date: 2009-12-11
forum: Hardware
---

### Post by Manyette on 2009-12-11
Hi all, Having written more than one O/S for various projects, I have a question about the Ubuntu boot sequence.  I am a complete newbie to Linux, and would like someone to explain to me the boot sequence of Ubuntu.  Something similar to the disk boot sequence of DOS, as an example:  First the MBR, which points to a particular disk partition, which reads the first sector of that partition, which loads the OS system loader file(s).

My reason for asking this question is because my backups always fail to restore, with the helpful comment "missing file", and no clue as to just WHAT file is missing. I always get to GRUB2 in Karmic, before this happens. (IMHO, a flaw in the process).  No, I've never lost any data, but always wind up having to reinstall Ubuntu, and update,and recover at least the prior kernel files before reloading my /home directory.  Can anyone elaborate on the process between the start up of GRUB, and to the point of system load?  Any help would be greatly appreciated.  At this point, it pains me how little I know on this subject, and feel like a complete dunce, so I don't ave a clue as to where to start looking.  Thanks for any help, It would be greatly appreciated.

---

### Post by IcarusR on 2009-12-12
Found this which explains boot sequence for Debian, as Ubuntu is based on Deb it ought to be the same.

[http://www.debianhelp.co.uk/boot.htm]("http://www.debianhelp.co.uk/boot.htm")

---

### Post by Manyette on 2009-12-12
Hello IcarusR, many thanks indeed!  Just what I was looking for, but couldn't find.  I've just got to get in the habit of searching Debian as well.  Again, thank you!

---

### Post by IcarusR on 2009-12-13
You're welcome

---

