---
title: "new user needs help"
date: 2010-09-17
forum: Hardware
---

### Post by richard.blastland on 2010-09-17
**i need help**             
                                                                have just bought a  laptop with unbunto installed on it.it has a user name and it asks for  his password.i dont know these.i have asked the person but he ays cant  remember.i cannot download anything and some tasks ask for a  administrators password.can anybody help
kind regards

rich):P

---

### Post by endotherm on 2010-09-17
one thing to remember, is that once you are logged in, if the system asks for a password, it's probably asking for the one you used to log in. are you able to login?

changing a password in ubuntu is easy if you have an active administrative user account, but even if you don't you can change it by rebooting into recovery mode. 
here is some info about how to get into recovery mode:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

then once you are in, enter this command:
```

passwd <username>

```
and enter/confirm your new password as prompted. then reboot with:
```

reboot

```

after that, your system should recognize your password.

Here is some info about the sudo system. sudo (and the graphical 'gksu') allow a user to run a task as an administrator. when you use sudo to launch a command, it will ask you for YOUR password (not a root or admin passwd). 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dirghrabadia on 2010-09-17
> 
changing a password in ubuntu is easy if you have an active  administrative user account, but even if you don't you can change it by  rebooting into recovery mode. 
here is some info about how to get into recovery mode:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

then once you are in, enter this command:
 	Code:
 	passwd <username> 
and enter/confirm your new password as prompted. then reboot with:
 	Code:
 	reboot 
after that, your system should recognize your password.


So can anyone change my password by rebooting into recovery mode?

---

### Post by endotherm on 2010-09-17
> **dirghrabadia said:**
> So can anyone change my password by rebooting into recovery mode?
yup. one of the most important rules of security is this:
"Physical access == Root access".

If I can get to your box physically, there is basically nothing you can do to keep me out. 

now for this issue specifically, you can set a grub password that you will have to enter to access the grub menu. that wou;dn't prevent someone from booting off a live disk though, and running scripts to alter your passwd. for that you lock down the bios to prevent booting from cd, with a setup/admin password, but that wouldn't stop someone from clearing your CMOS,  to reconfigure your bios, etc. it just keeps going on like that. this is a problem on all operating systems, so it's not just an ubuntu/linux issue. 

the best answer, is to lock the door.

---

### Post by dirghrabadia on 2010-09-17
> **endotherm said:**
> 
the best answer, is to lock the door.

:lolflag: Thanks.

---

