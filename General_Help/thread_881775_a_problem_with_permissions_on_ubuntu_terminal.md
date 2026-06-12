---
title: "a problem with permissions on ubuntu terminal"
date: 2008-08-06
forum: General Help
---

### Post by eagleye on 2008-08-06
when I try to install a software called: "aircrack-ng" it gives me errors, here is the code I entered in the terminal:

```

skypredator@skypredator-desktop:~$ cd aircrack-ng-1.0-rc1
skypredator@skypredator-desktop:~/aircrack-ng-1.0-rc1$ make
make -C src all
make[1]: Entering directory `/home/skypredator/aircrack-ng-1.0-rc1/src'
make -C osdep
make[2]: Entering directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
make[2]: Leaving directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
make[1]: Leaving directory `/home/skypredator/aircrack-ng-1.0-rc1/src'
skypredator@skypredator-desktop:~/aircrack-ng-1.0-rc1$ make install
make -C src install
make[1]: Entering directory `/home/skypredator/aircrack-ng-1.0-rc1/src'
make -C osdep
make[2]: Entering directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
make[2]: Leaving directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
make -C osdep install
make[2]: Entering directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
Building for Linux
make[3]: Entering directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
make[2]: Leaving directory `/home/skypredator/aircrack-ng-1.0-rc1/src/osdep'
install -d /usr/local/bin
install -m 755 aircrack-ng airdecap-ng packetforge-ng ivstools kstats buddy-ng m
akeivs-ng /usr/local/bin
install: cannot remove `/usr/local/bin/aircrack-ng': Permission denied
install: cannot remove `/usr/local/bin/airdecap-ng': Permission denied
install: cannot remove `/usr/local/bin/packetforge-ng': Permission denied
install: cannot remove `/usr/local/bin/ivstools': Permission denied
install: cannot remove `/usr/local/bin/kstats': Permission denied
install: cannot remove `/usr/local/bin/buddy-ng': Permission denied
install: cannot remove `/usr/local/bin/makeivs-ng': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/skypredator/aircrack-ng-1.0-rc1/src'
make: *** [install] Error 2
skypredator@skypredator-desktop:~/aircrack-ng-1.0-rc1


```

what seems to be the problem??

---

### Post by tuxxy on 2008-08-06
TRy adding a sudo to the start of the command to give you admin privs before making the file

```
sudo make install
```

---

### Post by eagleye on 2008-08-07
yea!! thanks lol I forgot to type sudo!
but you know what? I tried to type su and then he asked for my password so I typed it but it said that the password is wrong while when I use sudo and type my password it is being accepted without any problem...

what seems to be the problem recieving my password using su?

---

### Post by damoxc on 2008-08-07
Running su is to change to the root user, which means you'd need to enter the root password, but the root account is disabled by default in Ubuntu.

---

### Post by Uchiha_madara on 2008-08-09
Listen :

if you want to Access as root

Type :

> sudo su root

and give it your Password 


or Re-Configure the Password of the root Like :

> passwd root

Then you can create new Password to root and Type it again to Confirm it

then you can Type 
> su root 
then Type the password
and Typing the Commands without "sudo" Command

Good Luck

---

### Post by mikjp on 2008-08-09
> **damoxc said:**
> Running su is to change to the root user, which means you'd need to enter the root password, but the root account is disabled by default in Ubuntu.

su can be used to change to any user account, not only to the root.  It defaults to root.

greetings,

m

---

