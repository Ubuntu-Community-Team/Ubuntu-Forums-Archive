---
title: "Lost Complete Ownership"
date: 2008-11-18
forum: General Help
---

### Post by G-Dub on 2008-11-18
I was messing around with some settings and all my folder's permissions were set to "root." I can no longer boot into ubuntu. How do i change this back?

---

### Post by bodhi.zazen on 2008-11-18
Boot to recovery mode 

[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

---

### Post by G-Dub on 2008-11-18
that was very helpful, thankyou! Unfortunately i cannot boot into recovery mode either. Both ways send me to a (initramfs) command prompt. It's not like the regular terminal. Instead of my username@workstation at the beginning, it is replaced with (initramfs). It also says something about busybox. Is there a way of doing this through livecd?

---

### Post by bodhi.zazen on 2008-11-18
That sounds like a much bigger problem then I thought.

What did you do exactly ?

Can you try booting an older kernel ?

---

### Post by G-Dub on 2008-11-18
i tried booting from an older kernel and it failed as well. I was having a lot of trouble with permissions (i just reinstalled and recovered a lot of files on a different hard drive from a previous install). So i selected all the files, right clicked and went to permissions. I was unable to change the username, but i assumed it would automatically use mine, and i selected read and write. Then everything when white on the screen. I tried rebooting and it gave me the iniramfs.

---

### Post by taurus on 2008-11-18
You can always boot from the LiveCD (if you are able to), mount the harddrive where / is (or /home if /home is on a separate drive), and change the ownership of your $HOME on the harddrive from root back to your login name.

Can you boot your machine with a LiveCD?

---

### Post by G-Dub on 2008-11-18
i'm looking at that right now. home is actually still under my username.

---

### Post by G-Dub on 2008-11-18
to answer you question, yes. livecd works. but i can only view the contents of my harddrive through gksudo nautilus.

---

### Post by taurus on 2008-11-18
Do you have a separate partition for /home or do you only have one partition, /, besides the other one for swap.  Let's _assuming_ that you have only one partition and it is /dev/sda1.  From the LiveCD, open a terminal and mount it.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
```
Now, you can check your $HOME to make sure you are the owner of every file in there and have the right permissions.

```
ls -la /media/ubuntu/home/**john**
```
_Assuming_ **john** is your username.
Otherwise, you can change the ownership back to **john** again with

```
sudo chown **john**:**john** /media/ubuntu/home/**john**/*<filename>*
```
Replace *<filename>* with the actual name of a file.

And when you are done making changes, you can unmount your harddrive and reboot.

```
sudo umount /media/ubuntu
```

---

### Post by G-Dub on 2008-11-18
what about the other folders besides home? what should their permission be? does it matter?

---

### Post by G-Dub on 2008-11-18
also i have ubuntu installed on my second physical harddrive, should i use sda2? or sdb1?

---

### Post by G-Dub on 2008-11-18
ok, everything under Home is in my permission. I reboot and i get this:

```
Target filesystem doesn't have /sbin/init.
run-init: /bin/sh: Permission denied
[      7.1171497] Kernal Panic - not syncing: Attempted to kill init!
```

---

### Post by bodhi.zazen on 2008-11-18
> **G-Dub said:**
> what about the other folders besides home? what should their permission be? does it matter?
> **G-Dub said:**
> also i have ubuntu installed on my second physical harddrive, should i use sda2? or sdb1?

First of all we (you) need to know what is where. If you do not know, that is OK, you will need to mount the partitions and see what is in them.

```
sudo mkdir /media/sd{a,b}
sudo mount /dev/sda1 /media/sda
sudo mount /dev/sdb1 /media/sdb
```

See also : [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

With that said, if you changed ownership of all your directories, easiest fix is to re-install :(

---

### Post by G-Dub on 2008-11-20
thank you so much for your help, i ended up just reinstalling :/

---

