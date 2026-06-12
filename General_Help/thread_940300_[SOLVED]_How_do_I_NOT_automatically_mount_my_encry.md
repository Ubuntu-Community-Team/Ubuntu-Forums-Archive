---
title: "[SOLVED] How do I NOT automatically mount my encrypted Private folder at startup?"
date: 2008-10-06
forum: General Help
---

### Post by willz06jw on 2008-10-06
Howdy,

I am using the new 8.10 Intrepid Beta and I have installed the EncryptedPrivateDirectory.  (By the way cheers on the great work I give you :KS:KS:KS:KS:KS)

Every time I start my computer the Private folder is mounted automatically.  I want to use this folder to store sensitive information and I also like having Ubuntu auto-login.  

Is there a way to have it mount only when I want and have it request a password?

Thanks,
Will

---

### Post by willz06jw on 2008-10-14
Howdy,

I posted in the Development area of the forum and this is what I have been told to do by taavikko:

> Open [home folder], show hidden folders (contrl-H), move to the .ecryptfs folder, and then remove the automount & autoumount [text files]

Regards,
Will

---

### Post by doncristobal on 2009-05-10
I removed both auto-mount and auto-umount from ~/.ecryptfs, and then graphical logins were no longer possible! I typed my user name and password, had to wait for 10-20 seconds, and then the login screen appeared again. 
I'm on Xubuntu 9.04, maybe this makes a difference?
I'm going to try only removing auto-mount, maybe it works like that.

---

### Post by doncristobal on 2009-05-10
> **doncristobal said:**
> 
I'm going to try only removing auto-mount, maybe it works like that.

It did _not_ work. Graphical login was impossible. So I cannot recommend removing any of these two files. 

Is there any (other) way to stop ecryptfs-xyz from auto-mounting the private directory?

---

