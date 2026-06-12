---
title: "I removed my privileges!!"
date: 2008-08-16
forum: General Help
---

### Post by Julius1988 on 2008-08-16
I logged in as the sudo user, and removed my prelileges now i am not able to do any administrative task.Is there any way i could resolve this i am stranded out, unfortunately i have only one account.:confused:

---

### Post by Elfy on 2008-08-16
I think that if you boot to recovery mode you should be able to add your user back to the admin group with

```
adduser *username* admin
```

---

### Post by Julius1988 on 2008-08-16
> **forestpixie said:**
> I think that if you boot to recovery mode you should be able to add your user back to the admin group with

```
adduser *username* admin
```

Thanks man its resolved.

---

### Post by Julius1988 on 2008-08-16
This is what i was trying to do and i messed up.
When i try to start VMWare from System Tools->VMWare it does not start.
However if i type sudo vmware it prompts for the password and starts.
I want to change this,How to do?

---

### Post by Elfy on 2008-08-16
Glad I could help with the first... but no idea with second - I use vbox and have never really got into vmware - wasn't even aware it requires root rights to run !

Back later...


Edit - been given this as the place to go to look for you

[http://ge.ubuntuforums.com/showthread.php?t=779934](http://ge.ubuntuforums.com/showthread.php?t=779934)

If you still have some problems come back again...

Note - 
take note of the "post install" section
you have to "ln -s" a few library files first


That said if you do get problems it might be worth making a new thread in the [virtualisation]("http://ubuntuforums.org/forumdisplay.php?f=308") forum making sure to say about the add to admin user group problem you had.


Edit edit - I'm not sure about vmware but vbox has a user group - do you need to be part of it, check users and groups - but check it out first as I'm not sure about it at all.

---

### Post by Julius1988 on 2008-08-17
> **forestpixie said:**
> Glad I could help with the first... but no idea with second - I use vbox and have never really got into vmware - wasn't even aware it requires root rights to run !

Back later...


Edit - been given this as the place to go to look for you

[http://ge.ubuntuforums.com/showthread.php?t=779934](http://ge.ubuntuforums.com/showthread.php?t=779934)

If you still have some problems come back again...

Note - 
take note of the "post install" section
you have to "ln -s" a few library files first


That said if you do get problems it might be worth making a new thread in the [virtualisation]("http://ubuntuforums.org/forumdisplay.php?f=308") forum making sure to say about the add to admin user group problem you had.


Edit edit - I'm not sure about vmware but vbox has a user group - do you need to be part of it, check users and groups - but check it out first as I'm not sure about it at all.

no fix.

---

### Post by Elfy on 2008-08-17
Well I'm afraid I don't know - make a thread for it as I suggessted in the virtulisation forum.

---

