---
title: "Help accessing user accounts"
date: 2008-08-20
forum: General Help
---

### Post by Paradox41 on 2008-08-20
Hi,

I've been using kubuntu for quite some time now. Maybe half a year, and I've had no problems whatsoever in all these months. However, today I've been having trouble accessing my user accounts. Neither me nor my brother can access our accounts. When we try to log in, the screen refreshens how it always does when it's about to log in, but it doesn't. It takes us back to the login menu. I don't know what the problem is. It's the first time it's done this. And I don't think I have done anything with any files to trigger this problem.

Anyone has any idea what could be happening?

My version of kubuntu is Feisty. I can't remember what it is in numbers. 7.06 I think.

---

### Post by Paradox41 on 2008-08-20
Anyone that might know what's going on? :confused:

---

### Post by cdtech on 2008-08-20
Have you tried to use the recovery mode to login?

---

### Post by Paradox41 on 2008-08-20
> **cdtech said:**
> Have you tried to use the recovery mode to login?

No, I haven't. How do I login in recovery mode? And what would I fix once I do?

---

### Post by Vivaldi Gloria on 2008-08-20
> **Paradox41 said:**
> No, I haven't. How do I login in recovery mode? 

When boot starts press ESC to enter grub boot menu. Choose the recovery mode.

> And what would I fix once I do?

Try:

```
sudo dpkg-reconfigure kdm
```

and restart using the command

```
sudo reboot
```

---

### Post by Paradox41 on 2008-08-21
> **Vivaldi Gloria said:**
> When boot starts press ESC to enter grub boot menu. Choose the recovery mode.



Try:

```
sudo dpkg-reconfigure kdm
```

and restart using the command

```
sudo reboot
```

I just did all that, and it's still the same. :(

I don't know what's going on. When I try to log in, the screen just goes black like it's trying to load the desktop, but it just doesn't. It goes back to the login menu, as if I hadn't logged in at all. It's frustrating.

---

### Post by Vivaldi Gloria on 2008-08-21
> **Paradox41 said:**
> I just did all that, and it's still the same. :(

Sorry, I'm out of ideas. Anyone?

---

### Post by Paradox41 on 2008-08-22
Anyone else might have some ideas? I still can't access it. and I cant afford to start anew, as I had many files under my account I need. :S

---

### Post by aloshbennett on 2008-08-22
Can you try logging in from one of the other ttys?
Hit Ctrl + Alt + F1 and see if you are able to login.

---

### Post by Paradox41 on 2008-08-22
> **aloshbennett said:**
> Can you try logging in from one of the other ttys?
Hit Ctrl + Alt + F1 and see if you are able to login.


Just tried that, and it does seem to log me in like that. at least on the terminal thing. Cause my name appears, along with the @computer:$~ or something like that.
I don't know what command to input though. LOL

---

### Post by LateNiteTV on 2008-08-22
from there, try entering "startx" or "startkde"

---

### Post by aloshbennett on 2008-08-22
A shot in the dark.
Type in 'ls -l .ICEauthority'
Does it show root as the owner or are you the owner?

---

### Post by Paradox41 on 2008-08-22
Ok I tried startx and startkde, and this is what showed up:

startx:
Error: Cant connect kdeinit!
Creating link /home/[myname]/.kde/socket-Computer
Can't create mcop directory
startkde: runnung shutdown scripts
xprop: unable to open display
usage: xprop [-options...][[format [deformat]] atom...


startkde:
Fatal Server error:
server is already active for display 0
If this server is no longer running, remove /tmp/.x0-lock and start again.

xlib: connection to :0.0" refused by server
xlib: Invalid MIT-MAGIC-cookie-1 key
guving up
xinit: unable t oconnect to x server
xinit: No such process [errno 3]:server error.

---

### Post by LateNiteTV on 2008-08-22
type in:
```
killall xorg
```
or
```
killall Xorg
```
and try startx or startkde again.

---

### Post by bodhi.zazen on 2008-08-22
From the terminal, the command line ;

```
sudo /etc/init.d/kdm stop

startx
```

Post any errors with that startx command.

the other options are to look at your logs (/var/log/) for error messages or create a new user. If the new user works your config files are corrupt.

---

### Post by Paradox41 on 2008-08-22
I've tried all of these methods, but none of them seem to work. :( I've given up hope.

Can someone tell me how I could mount my HDD, so I can at least save some of my files into a CD and don't have to download them all over again after the re-install?

---

### Post by Paradox41 on 2008-08-23
> **Paradox41 said:**
> I've tried all of these methods, but none of them seem to work. :( I've given up hope.

Can someone tell me how I could mount my HDD, so I can at least save some of my files into a CD and don't have to download them all over again after the re-install?

A little bump. Just wanna know how to do this.. I remembered I mounted the HDD on the LiveCD with a command line someone told me about, but I forgot it. I just wanna burn some of my old files and reinstall kubuntu.

---

### Post by bodhi.zazen on 2008-08-23
list your partitions with :

sudo fdisk -l

mount a partition with :

```
sudo mount /dev/sdxy /mnt
```

unmount with 

```
sudo umount /mnt
```

If you need to mount more then 1 partition, use /media/sdxy

sudo mount /dev/sdxy /meida/sdxy

where /dev/sdxy == the partition to mount (sda1 , sda2, etc)

---

