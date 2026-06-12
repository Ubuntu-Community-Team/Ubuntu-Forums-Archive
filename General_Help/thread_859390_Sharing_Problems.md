---
title: "Sharing Problems"
date: 2008-07-14
forum: General Help
---

### Post by fedex1993 on 2008-07-14
Okay i am trying to share my /home/sean/movies file folder i right click and choose sharing options. I installed the samba daemons and i get a error message" 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share." How can i share this folder.

---

### Post by JoeEndUser on 2008-07-14
Evidently, you are supposed to reboot after the install, 

But I've been traveling down the same path and haven't got it working yet.

I'm here looking into file sharing via virtualbox as for me Samba seems to be a mess.

Please update with whether you got it working!

---

### Post by fedex1993 on 2008-07-14
oh i got it working using "sudo chmod 777 /var/lib/samba/usershares/

---

### Post by JoeEndUser on 2008-07-14
Thanks.  I saw an article from VMware describing that I think.  Maybe I'll go back through it.

Cheers

---

