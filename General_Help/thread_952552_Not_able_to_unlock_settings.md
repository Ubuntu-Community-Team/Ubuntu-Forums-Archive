---
title: "Not able to unlock settings"
date: 2008-10-19
forum: General Help
---

### Post by daanbrg on 2008-10-19
Hi everybody,

Today I installed VirtualBox OSE from Java, I know the program because I used this program before on my previous computer.

A beautiful program, but before you can start using it, you'll first have to install an addition through sudo apt-get install, and after that, you'll have to add yourself to the group "/dev/vboxdrv".

So after installing the addition, I went to System > Administration > Users and Groups, and I clicked the "Unlock" button. But nothing happened, and after a while (to be exact: 25 seconds), it told me the following:

> **Could not authenticate**

An unexpected error has occurred.

I have no idea of what's going on, and I tried the "Unlock" button at several different settings, but it just gives me excactly the same message. How great.

What do I have to do :confused:

Tell me!

Thanks in advance!

Daan Berg.

---

### Post by risu_vk on 2008-10-19
did you try 

```
sudo addgroup vboxusers
sudo adduser your_username vboxusers
sudo /etc/init.d/vboxdrv setup
```

---

### Post by daanbrg on 2008-10-19
> **risu_vk said:**
> did you try 

```
sudo addgroup vboxusers
sudo adduser your_username vboxusers
sudo /etc/init.d/vboxdrv setup
```

Output of sudo addgroup vboxusers:
```
daan@daan-desktop:~$ sudo addgroup vboxusers
[sudo] password for daan: 
daan is not in the sudoers file.  This incident will be reported.
daan@daan-desktop:~$ 
```

Output of sudo adduser daan vboxusers:
```
daan@daan-desktop:~$ sudo adduser daan vboxusers
[sudo] password for daan: 
daan is not in the sudoers file.  This incident will be reported.
daan@daan-desktop:~$ 
```

Output of sudo /etc/init.d/vboxdrv setup:
```
daan@daan-desktop:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for daan: 
daan is not in the sudoers file.  This incident will be reported.
daan@daan-desktop:~$ 
```

Why do I get this strange output? I NEVER had this before! :confused::confused::confused:

---

### Post by drs305 on 2008-10-19
It appears you are no longer in the 'admin' group. Since you don't seem to be able to use sudo to unlock System, Administration, Users, you will need to boot into recovery mode.

Choose the 'root prompt' option, and then:
```

adduser daan daan
adduser daan admin

```

Reboot.

---

