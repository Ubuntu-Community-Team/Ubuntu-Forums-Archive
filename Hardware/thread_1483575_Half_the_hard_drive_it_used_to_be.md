---
title: "Half the hard drive it used to be"
date: 2010-05-14
forum: Hardware
---

### Post by zerobytes2003 on 2010-05-14
I have a 120gb 2nd HDD that appears to be working fine and installed correctly.  My dualboot of XP shows everything fine but when I mount it in Lucid more than half the files (mostly media files) just aren't there.  Disk usage analyzer shows the space is being used but for some reason I just can't access the files through nautilus or the command line.  Please help.

---

### Post by cj.surrusco on 2010-05-14
what format is the drive?

---

### Post by zerobytes2003 on 2010-05-14
oi - sorry, it is ntfs (htfs).  thanks for the speedy response!

---

### Post by Brainy142 on 2010-05-14
try ctrl-h (show hidden files hotkey). (make sure the file's aren't hidden)

---

### Post by Brainy142 on 2010-05-14
hmm.... try running a disk check maybe, I've had files disappear before, but got them back after the desk was checked for errors.

---

### Post by kio_http on 2010-05-15
Run a disk check in Windows.

Open a commanprompt
```
 chkdsk 
```

---

### Post by zerobytes2003 on 2010-05-15
Thanks for the comments guys!  Sadly, ctrl+h did not work but that is a very handy shortcut to know.  I checked the S.M.A.R.T. data on the drive and it threw all kinds of errors, mostly relating to the age of the drive.  I booted into my windows install and ran chkdsk which also threw a bunch of errors.  While there I made sure to back up some of my more important files.  Looks like it may be time to get a new drive.  Thank you for all the help and time!

---

