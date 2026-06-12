---
title: "Symbolic LInks to Windows Vista Possible?"
date: 2008-11-06
forum: General Help
---

### Post by Orange Luna on 2008-11-06
Hello,

I just installed Linux and am really liking so far but I have a question about creating links to my Windows-files.  I have a good number of files on my Windows partition and I'd like to be able to access them in a quick way.  I linked my Windows Vista folders to my home folder and they work just fine but when I login and logout again the links are locked.  If I try to open them nautilus will tell me that the links are broken.  Is the a right way to do this?

---

### Post by tiberiup on 2008-11-06
I think you must mount your windows partition in your /etc/fstab file
Ex : 
/dev/sda1 /media/WinVista ntfs rw 0 0
(where sda1 is your windows partition, /media/WinVista is your mountpoint, rw = read write perimission )
this will mount your partition at boot, it worked for me...

---

### Post by Orange Luna on 2008-11-17
> **tiberiup said:**
> I think you must mount your windows partition in your /etc/fstab file
Ex : 
/dev/sda1 /media/WinVista ntfs rw 0 0
(where sda1 is your windows partition, /media/WinVista is your mountpoint, rw = read write perimission )
this will mount your partition at boot, it worked for me...

thanks for the tiberiup, thats just what I did and it did the job.  thanks.

---

