---
title: "Broken Package Manager"
date: 2008-11-30
forum: General Help
---

### Post by Tobster on 2008-11-30
Hi Everyone,

I have broken My Packages (again! LOL) in Synaptic but this time I can't seem able to fix it...

I keep geting the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have looked at the archives but been unable to find a solution...  This error happen when I tried to down load Second Life from the 'getdebs' website..  Which is not supported by Conical I know 

Thanks

Toby:confused:

---

### Post by Tobster on 2008-11-30
People don't worry I am going to install Ubuntu 8.10 to make life easy.

Thanks

Toby

---

### Post by CatKiller on 2008-11-30
The first thing to do is to run the command (Applications -> Accessories -> Terminal) that it suggests; ```
sudo dpkg --configure -a
``` to finish configuring the packages that were interrupted.

It's generally not necessary to re-install the operating system because of small configuration problems.

---

### Post by Tobster on 2008-11-30
This is what i get:

toby@toby-desktop:~$ sudo dpkg-configure -a
[sudo] password for toby: 
sudo: dpkg-configure: command not found
toby@toby-desktop:~$

---

### Post by drs305 on 2008-11-30
> **Tobster said:**
> This is what i get:

toby@toby-desktop:~$ sudo dpkg-configure -a
[sudo] password for toby: 
sudo: dpkg-configure: command not found
toby@toby-desktop:~$

Check your spaces. The command is actually:
```
sudo dpkg --configure -a
```

---

### Post by CatKiller on 2008-11-30
> **Tobster said:**
> dpkg-configure: command not found

Sorry. My mistake - not firing on all cylinders today. It was a typo in the command I gave. I'll correct it.

---

### Post by Tobster on 2008-11-30
Thanks I get this now:

toby@toby-desktop:~$ sudo dpkg --configure -a
[sudo] password for toby: 
toby@toby-desktop:~$

---

### Post by drs305 on 2008-11-30
> **Tobster said:**
> Thanks I get this now:

toby@toby-desktop:~$ sudo dpkg --configure -a
[sudo] password for toby: 
toby@toby-desktop:~$

For security, you won't see your password or any other symbol as you type it. Just type it out completely and hit ENTER.

Or if you did that, it means there wasn't anything more for you to do.

---

### Post by CatKiller on 2008-11-30
> **Tobster said:**
> Thanks I get this now:

toby@toby-desktop:~$ sudo dpkg --configure -a
[sudo] password for toby: 
toby@toby-desktop:~$

Then the outstanding packages should have been configured. Does everything else work OK now?

---

### Post by Tobster on 2008-11-30
Please go to page two

---

### Post by Tobster on 2008-11-30
Sorry.. I know I did not need to reboot.  I did not read the error message but we are making progress!!!

This all started when I tried to install Second Life and so now I am getting this error message:

E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

So we are getting close...

Thanks

Toby

---

### Post by CatKiller on 2008-11-30
I've never used getdeb. Have you downloaded a .deb file? You should be able to just double-click on it to install it, if you have.

Which version of Ubuntu are you using? I just had a quick look at the getdeb website, and they don't appear to have a version for 8.10, just 8.04LTS.

---

