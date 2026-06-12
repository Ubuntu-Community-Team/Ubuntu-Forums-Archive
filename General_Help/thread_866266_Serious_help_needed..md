---
title: "Serious help needed."
date: 2008-07-21
forum: General Help
---

### Post by HpZ on 2008-07-21
So I needed to update pretty much all my packages so I went into the Update manager and started updating. Everything went fine but then before it finished my computer completely froze up (bad luck eh?) and I was forced to restarted the computer manually.

Now, when I'm back in and trying to do the updates again I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

So I try to run "dpkg --configure -a" in the terminal and I get another error: dpkg: requested operation requires superuser privilege.

Please help. I can't run firefox. I tried to run it from the terminal and this is the output:

"andy@andy-desktop:~$ firefox
Could not find compatible GRE between version 1.9 and 1.9."

---

### Post by WRDN on 2008-07-21
Type:

```
sudo dpkg --configure -a
```

You will then be prompted for your password.

sudo means 'super user do' and will give you the superuser privileges.

---

### Post by Potatoj316 on 2008-07-21
It seems everyone has this problem

---

### Post by HpZ on 2008-07-21
Okay I did that but seeing my system is rubbish the terminal crashed but I'm doing it again. Is there any safe mode style thing like on windows to prevent things from crashing while I'm doing something important?

By the way, I just got this: "Segmentation fault"


What do I do?

---

### Post by HpZ on 2008-07-21
Bah, I still get Segmentation Fault even after trying again. And I still get the r:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

problem when trying to use the update manager.

:(:(:(.

---

### Post by Potatoj316 on 2008-07-21
Segmentation faults are caused when a program tries to write to read only memory, theres really nothing you can do about it.  There is a recovery mode you can use but I dont really know what it is (it should be in the grub menu)

Perhaps if you try this.  Press crtl+alt+F1, you will be presented with your terminal.  Log in with your name and password.  Now try that sudo dpkg --configure -a again.

---

### Post by HpZ on 2008-07-21
Okay, Seg Fault is gone and is now stuck on  * Starting the Winbind daemon winbind                                          

Should I wait it out?

---

