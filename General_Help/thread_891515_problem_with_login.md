---
title: "problem with login"
date: 2008-08-16
forum: General Help
---

### Post by BrandonBmx on 2008-08-16
just insalled XUBUNTU on my old laptop and t is now sking for a username and password, but theres a problm..
i type my username brandon and hit enter
when i try to type my password the little _ dosent move and letters appear... just blank spaces and it blinks quicker
can someone please help cus ive been waiting for ages to install this and now i have i cant even login!

---

### Post by lisati on 2008-08-16
It is normal for the password to be hidden or disguised when you type it in. What happens you type in the password you used when you setup your system and press "enter"?

---

### Post by BrandonBmx on 2008-08-16
thia is whats on the screen:
ubuntu 6.06.1 LTS ubuntu tty1

ubuntu login: (i can type brandon here)
password:(flashing_) (cant type password
login incorrect

its definatly recognising the username but not the password even if i just type my password without it coming up on the screen and i dont know why its doing it

---

### Post by BrandonBmx on 2008-08-16
also the command in grub or whatever it is when you edit kernal line to rw init=/bin/bash/ then boot itand type cat /etc/passwd/ no users show up

---

### Post by BrandonBmx on 2008-08-16
please hhelppp!!!!!!

---

### Post by lisati on 2008-08-16
I'm not sure what to suggest. Anyone else?

---

### Post by BrandonBmx on 2008-08-16
i have had trouble with the install before and i tried reinstalling to an unclean partition because it siad it would just overwrite the files anyway.. do you think that is the problem?

---

### Post by Tom--d on 2008-08-16
> **BrandonBmx said:**
> thia is whats on the screen:
ubuntu 6.06.1 LTS ubuntu tty1

ubuntu login: (i can type brandon here)
password:(flashing_) (cant type password
login incorrect

its definatly recognising the username but not the password even if i just type my password without it coming up on the screen and i dont know why its doing it

why didnt you install Xubuntu 8.04.1?

---

### Post by BrandonBmx on 2008-08-16
> **Tom--d said:**
> why didnt you install Xubuntu 8.04.1?

i dont know wich one to download there was a few but i had to download alternate cd but it should still login if it got to 6.0 or whatever also its Xubuntu

---

### Post by Tom--d on 2008-08-16
> **BrandonBmx said:**
> i dont know wich one to download there was a few but i had to download alternate cd but it should still login if it got to 6.0 or whatever also its Xubuntu

6.06 is old.

Download the xubuntu 8.04 here [http://www.xubuntu.org/get#hardy](http://www.xubuntu.org/get#hardy)

Pick a mirror and burn and reinstall.

Xubuntu 6.06 came out in 2006 June
Xubuntu 8.04 came out in 2008, April

New, updated things have changed between them.
They are BOTH Long Term Support (LTS)

---

### Post by Tom--d on 2008-08-16
a direct link to Xubuntu 8.04 alternate

[http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/8.04/release/xubuntu-8.04.1-alternate-i386.iso](http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/8.04/release/xubuntu-8.04.1-alternate-i386.iso)

---

### Post by BrandonBmx on 2008-08-16
> **Tom--d said:**
> 6.06 is old.

Download the xubuntu 8.04 here [http://www.xubuntu.org/get#hardy](http://www.xubuntu.org/get#hardy)

Pick a mirror and burn and reinstall.

Xubuntu 6.06 came out in 2006 June
Xubuntu 8.04 came out in 2008, April

New, updated things have changed between them.
They are BOTH Long Term Support (LTS)

if this 1 is better why is it a smaller filesize? lol
and also when i install 8 can i still delete old ubuntu from partition or do i have to use some kind of installer tool

---

### Post by ProDigit on 2008-08-16
I have the same issue.

In my case the OS removed the first 2 digits of my loginname.

I would suggest typing your username minus the first 2 digits.

If this doesn't work, then start Xubuntu in recovery mode (from grub)
when the menu pops up, choose to start in root shell mode.

If that didn't work you might try to start a live CD, and view the files on your / (root) partition.

There are several other ways to view the data on your disk.

Anyways, you should now be in ROOT mode.
if not, type 
> sudo bash

then do the following:

> 
nano /etc/passwd


scroll down to the last line where the username should be visible.

write down the username displayed (in my case the 2 first digits disappeared). Note that there's a bunch of data behind the username. Just write down whatever is left you remember to be your username.

then do:

> adduser ******
and replace the stars with a username containing lowercase, underscore, periods, sings dashes and/or numbers (NO CAPITAL LETTERS).
Fill in the questions as preferred.
*Note: must be done in Superuser or root account*


restart the system,and log in using that name and your original password.

then in the desktop open applications>>System>>Users and groups, and unlock.
Set userprivileges
Remove the fake user,
click 'Manage Groups' and remove the bad username under groups, and close.

log out,and login with your desired username.

Cheerzz

---

