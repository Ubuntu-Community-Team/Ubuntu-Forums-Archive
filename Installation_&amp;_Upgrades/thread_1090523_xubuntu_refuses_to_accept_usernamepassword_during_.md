---
title: "xubuntu refuses to accept username/password during install"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by makhaucrazy on 2009-03-08
my lenovo laptop has a configuration of 246MB RAM 1.6GHz intel Celeron processor and 20GB of hard disk space left after my first xp partition.

I tried to install xubuntu but after setting up the partition manually with 750 MB swap and 19GB under "\". However it gives an invalid username/password error in the login screen. Says it to be wrong. Then it logins with xubuntu as user and after displaying the main screen layout the system stops responding. It then only responds to Ctrl+Alt+Backspace where it returns to the login screen again refusing to accept my password. What to do?

---

### Post by taurus on 2009-03-08
What username did you create?  

You can boot into recovery mode from GRUB menu and get into the root shell.  Then, you can change the password for that user with

```
passwd *username*
exit
```

---

### Post by makhaucrazy on 2009-03-08
xubuntu does not install. It is during the installation that after entering my username and password the login screen appears. It is in this login screen that xubuntu refuses to accept my username/password. thus it logins as xubuntu and then stops responding. As a result I have to shut down the computer and neither the partitions are done and neither xubuntu is installed.

---

### Post by taurus on 2009-03-08
What username did you use or try to create?

---

### Post by makhaucrazy on 2009-03-08
username : ayush and password : ayush

---

### Post by taurus on 2009-03-08
What filesystem did you tell the installer to format / to?

---

### Post by makhaucrazy on 2009-03-08
:(

---

### Post by makhaucrazy on 2009-03-08
ext3 for "\"

---

### Post by makhaucrazy on 2009-03-08
can anyone help me out???

---

### Post by makhaucrazy on 2009-03-08
> **taurus said:**
> What filesystem did you tell the installer to format / to?
can you help me out of this????
filesystem was ext3

---

### Post by makhaucrazy on 2009-03-08
hello!!!!!!!!!!!!
Is anyone out there????????:(

---

### Post by taurus on 2009-03-08
When you first boot Xubuntu LiveCD, did you run the check cd for defects to make sure the CD is good?  Also while in Live, open a terminal and post the output of this command.

```
sudo fdisk -l
```

---

### Post by makhaucrazy on 2009-03-08
I checked the cd for defects. How to access the terminal when my system hangs after logging into xubuntu and only responds to Ctrl+Alt+Backspace.

---

### Post by makhaucrazy on 2009-03-08
cd has no defects

---

### Post by makhaucrazy on 2009-03-09
the cd has no defects and plus the system hangs when it logs on to xubuntu with ubuntu as a user. Thus I cannot open the terminal on LIVE CD. I also tried yo change the session to run as terminal safe mode and on logging on to it once it showed some sort of crash. Then it hung up and I was unable to open the terminal. What to do ?

---

### Post by makhaucrazy on 2009-03-09
????
What to do????

---

### Post by Neo_The_User on 2009-03-09
What to do? Stop bumping this thread. As to your problem... :X I'm out. I never heard of anything like this.

---

