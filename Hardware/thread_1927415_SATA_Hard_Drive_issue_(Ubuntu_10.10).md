---
title: "SATA Hard Drive issue (Ubuntu 10.10)"
date: 2012-02-18
forum: Hardware
---

### Post by BlueprintIT on 2012-02-18
**External Sata Drive issues (Ubuntu 10.10)** 			
 			 			 		   		 		 		I currently am  using Ubuntu 10.10 in a multiboot setup with windows 7 on a Toshiba  Satellite L305-S5933.

 A few days ago I connected a hard drive, via a USB-to-SATA adaptor, to my laptop to  back up some files from my Laptop (I've done this countless times  before with no issue).  I moved the files over to the drive and  everything looked fine.  I played one of the MP3 files (a lecture I  recorded from college) from the drive and after I closed VLC, the screen  flashed.  Odd but nothing seemed out of order.

I opened the Hard Drive via Ubuntu to open a paper I was working on and found that none of the files or  folders I had moved over were now showing!  I immediately went to my  trash can thinking that since I hadn't deleted the files from the laptop  yet, I could re-copy them to the hard drive.

When I restored the files to my laptop from the trash and tried copying  them over, Linux asked me if I wanted to overwrite the files and  folders....as if they were still there but just invisible.  I agreed.   I agreed to overwrite and the files/folders showed up but when I opened a folder then returned to the root of the hard drive, the files/folders were again missing.

I safely removed the drive, shut off power to the drive, powered it back  up and hooked it back up to the laptop.  Still no new files or folders.

Rebooted the laptop into Windows 7 and the hard drive now showed the files  and folders were there, accessible, and usable (media files played fine,  document files opened fine, pictures were ok).

Back to Ubuntu. New folders that were just moved were still not showing up.

Anyone able to suggest what I might be able to do so ubuntu can see the files again?

---

### Post by ahallubuntu on 2012-02-18
Try running chkdsk on the drive in Windows.  Sounds to me like some journaling inconsistency - is this an NTFS drive?

---

### Post by BlueprintIT on 2012-02-18
Yes, it is an NTSF drive and I ran Gparted to see if there was any information it could give me on the drive.  Turns out a few clusters are being referenced multiple times.  

I could boot into windows and do a chkdsk /f however I would like to get away from windows if I could.  Is there something in linux that can do the same function as chkdsk /f?

---

### Post by ahallubuntu on 2012-02-18
I'm not sure how this problem occurred, but it's not typical for NTFS use in Ubuntu.  I've used NTFS for regular file storage in Ubuntu for a couple of years and very rarely had issues like you describe.  NTFS is reliable in Ubuntu.  The one time I remember having something like this was when I hibernated in Ubuntu with the NTFS disk mounted and then accessed the files by booting in Windows - and then somehow the journaling seemed out of sync or something.  A chkdsk fixed it.

I think there is a Linux tool in ntfstools to do file checking of NTFS volumes, but personally I wouldn't use it when I could just do it with Windows.  I'm not a purist; I use the best tool for the job, and for checking/correcting Windows filesystem issues, Windows is the best for the job, the least likely to cause problems with it.  And I've rarely needed to use it for this.

---

