---
title: "Ran out of hdd space and now can't log in"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by threethirty on 2007-08-09
Ok here is what happened, I use icepodder to download podcasts.  I filled my hdd with said podcasts and had this pop up windows that told me i had fewer than 2mb of space left.  So i turned off the laptop (stupid move) and now I can't log in.  I get all the way to the login screen, I put in my username and password, and then I get this error 

```
GDM could not write to your authorization file.  
This could mean that you are out of disk space or that your home directory could not be opened for writing.  
In any case, it is not possible to log in.  Please contact your system admin  
```

So now I am trying to do one of two things both using a live disk (right now im using Knoppix 4.0) I will separate these into two sections:

Backup and reinstall:

I have an external hdd that i planned on coping the /home/ directory to by I don't have the right permissions, I have tried doing this by sudo-ing, and trying after sudo su-ing, to no avail.

Just get in a delete a couple of files so that i can log in and then do the above:

The problem here is still permissions, the only thing I seem to have been able to delete was an empty NFS shared folder, which didn't help.

thanks in advance,
three

---

### Post by zero-9376 on 2007-08-09
you can either use the livecd to boot up mount your /home and delete some files or login from the terminal and do it from there crtl-alt=F1 should give you a terminal login and you can rm filename to delete a file.Once you delete a couple you should be able to login again through GDM

---

### Post by threethirty on 2007-08-09
sweet thanks, it worked, i was able to delete files from the terminal, thank you again

---

