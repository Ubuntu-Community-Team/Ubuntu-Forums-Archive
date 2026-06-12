---
title: "Home folders moved to another partition"
date: 2008-07-27
forum: General Help
---

### Post by lonjim2 on 2008-07-27
Hi All,

I'm a bit of a n00b in the terminal dept.  So I followed this guide [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) and moved my home directory over to another partition.  The move went well...got my fstab file updated, everything copied over beautifuly...but when I attempt to login, I have some ownership errors.  Upon login, the message i receive is:

> 
User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other user's.

If my users are user a and user b, how might I reassign 644 permissions?

I feel this is a basic one, but ANY help is highly appreciated.

Thanks!

---

### Post by tamoneya on 2008-07-27
open up terminal and type:```
ls -l /home
ls -l ~
```then post the output here.

---

### Post by lonjim2 on 2008-07-27
> **tamoneya said:**
> open up terminal and type:```
ls -l /home
ls -l ~
```then post the output here.

ls -l /home
total 24
drwxr-xr-x 2 root root 4096 DATE TIME backdoor
drwxr-xr-x 26 root root 4096 DATE TIME jim
drwx------ 2 root root 16384 DATE TIME lost+found

ps. backdoor is a my backdoor user account for when things go wrong (not that i've ever messed my config up ;))

PS I didn't bother punching in the date/times

---

### Post by lonjim2 on 2008-07-27
> **tamoneya said:**
> open up terminal and type:```
ls -l /home
ls -l ~
```then post the output here.

drwxr-xr-x 2 root root 4096 DATE TIME backdoor
drwxr-xr-x 26 root root 4096 DATE TIME jim
drwx------ 2 root root 16384 DATE TIME lost+found

ls -l ~
total 2192
drwxr-xr-x 2 jim jim 4096  DATE TIME Desktop
drwxr-xr-x 2 root root 4096 DATE TIME Documents
lrwxrwxrwx 1 jim jim 26 DATE TIME Examples -> /usr/share/example-content
drwxr-xr-x 2 jim jim 496 DATE TIME Music
drwxr-xr-x 2 jim jim 496 DATE TIME Pictures
drwxr-xr-x 2 jim jim 496 DATE TIME Public
-rw-r--r-- 1 jim jim 2208832 DATE TIME SOMETHINGaboutIT_2560x1600.png
drwxr-xr-x 2 jim jim 4096 DATE TIME Templates
drwxr-xr-x 2 jim jim 4096 DATE TIME Videos

ps. backdoor is a my backdoor user account for when things go wrong (not that i've ever messed my config up ;))  I also haven't logged in (successfuly) with it really.

---

### Post by tamoneya on 2008-07-27
here are the commands to fix:```
sudo chown -R jim:jim /home/jim
sudo chmod 644 /home/jim/.dmrc
```
The first one make sure that all your files are owned by jim and the second sets the permissions correctly.

---

### Post by lonjim2 on 2008-07-28
Worked like a charm!  I can't thank you enough!

---

### Post by ityro on 2008-08-02
> **tamoneya said:**
> here are the commands to fix:```
sudo chown -R jim:jim /home/jim
sudo chmod 644 /home/jim/.dmrc
```
The first one make sure that all your files are owned by jim and the second sets the permissions correctly.

I have the same problem but I can't use your solution because I cannot find the correct place and method to enter the two commands. Tried from liveCD and when I try to login on my system I just go into a loop with no way to enter the commands.

I am using liveCD now and will check back periodically. Thanks for any help. If you received a garbled THANK YOU, that was probabley me.

---

### Post by ityro on 2008-08-03
tamoneya: I found the "Options" button on the Log-in screen when it is asking for the User-Id. Selecting the Failsafe Session/Failsafe Terminal did the trick. My Desktop was scrambled so I restored a Grsync home backuo with no delete on destination and desktop was back to normal.

I tried to use the chown and chmod instructions to make sure but failed due to "Permissions". Will have to take it one step at a time. Thanks again for your original solution.

---

### Post by dexter.deepak on 2008-08-03
> **ityro said:**
> I have the same problem but I can't use your solution because I cannot find the correct place and method to enter the two commands. Tried from liveCD and when I try to login on my system I just go into a loop with no way to enter the commands.


you have to try these commands in a terminal :
applications -> accessories -> terminal

---

### Post by dexter.deepak on 2008-08-03
> **ityro said:**
> 
I tried to use the chown and chmod instructions to make sure but failed due to "Permissions". Will have to take it one step at a time. Thanks again for your original solution.

this method works when you have already logged into your system.
if you use a live-cd, first mount all you drives. then use 'cd' to go to your home partition, and then try the chmod/chown commands with a "sudo" prefixed , like:
sudo chown -R jim:jim /media/sda6/home/jim

i asssume you know how to navigate in a terminal.

---

### Post by cariboo on 2008-08-03
The easiest way to fix your problem is to boot recovery mode, then run the commands tamoneya posted, just don't use the sudo command as you are root already.

Jim

---

### Post by ityro on 2008-08-03
The Thank You button is missing so first let me say THANKS to all who responded to my request for help. I appear late but I am in the Philippines and it is 3:30am here.

I received an email from the forum with a solution by cariboo97 which worked for me but I don't see his post on the forum. Anyway thanks for the advice. I used Recovery Mode/Root Terminal without the "sudo" and it worked like a charm. Thanks again.

---

