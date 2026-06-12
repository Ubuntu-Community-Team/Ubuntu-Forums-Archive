---
title: "Oh man, I really broke something."
date: 2005-11-03
forum: General Help
---

### Post by extarbags on 2005-11-03
So I was trying to get Samba working right, and messing around, and I couldn't get it to acknowledge the normal login that I have on this machine. So I changed the password file in smb.conf from /etc/samba/smbpasswd to... /etc/passwd. Didn't work. Well, whatever.

However, this has really, really broken something. I don't have a username, I guess. Running smbpasswd returns "You don't exist - go away." I googled that and it apparently only happens when a user has a UID but no username. Not cool. I can't run the graphical Users and Groups thing, and usermod tells me that user extarbags does not exist.

So uh... how do I give myself a username?

---

### Post by bob k on 2005-11-04
Try using the Knoppix or Ubuntu live CD to correct your mistake.

---

### Post by extarbags on 2005-11-04
How precisely?

---

### Post by kvidell on 2005-11-04
I've not done it before but there's a restore option on the live and install CDs...

When it first comes up and says "boot: ", I think you type in "restore" and hit [enter].

I may be mistaken though, it should be easy enough to find on the forum.
Just do a quick search for "restore" or "live restore" mayhaps.
- Kev

---

### Post by extarbags on 2005-11-04
Man, that sounds likely to be disastrous... there isn't some file I can edit or command I can run to do this? At the very least, I should be able to just remake the user, right? Not that that's all that appealing either.

---

### Post by kvidell on 2005-11-04
That, technically, is do-able, yes...
Is the problem that the user cannot login to the system period (GDM, SSH) or just Samba?
- Kev

---

### Post by extarbags on 2005-11-04
No, I can log in. I'm logged in now on that account, as it is the only user account on this machine. I even tried logging in on a different terminal, and it worked, but instead of showing "extarbags@thatman" as the prompt, it shows "I have no name!@thatman."

The Gnome gui "Users and Groups" manager chokes on it, and the machine slows to a crawl whenever I'm trying to open up my home folder in Gnome. So I mean, the machine is still useable, even under this account, but it's not exactly ideal.

---

### Post by kvidell on 2005-11-04
[QUOTE=extarbags]No, I can log in. I'm logged in now on that account, as it is the only user account on this machine. I even tried logging in on a different terminal, and it worked, but instead of showing "extarbags@thatman" as the prompt, it shows "I have no name!@thatman."

The Gnome gui "Users and Groups" manager chokes on it, and the machine slows to a crawl whenever I'm trying to open up my home folder in Gnome. So I mean, the machine is still useable, even under this account, but it's not exactly ideal.[/QUOTE]
Have you tried making just a random extra user to login as and see if the problem persists?

---

### Post by extarbags on 2005-11-04
[QUOTE=kvidell]Have you tried making just a random extra user to login as and see if the problem persists?[/QUOTE]

I just made one, and it doesn't seem to be having this problem (the problem of not having a username, that is; I didn't bother testing Samba out). The Gnome User control panel still chokes, though. Is there some way I can just... set the username for my real account from the other one, now that I can run a command without being logged in as my real account?

---

### Post by kvidell on 2005-11-04
You need to add your new account to the admin group to be able to use SUDO and do adminy things.

Open an xterm (Alt+F2 -> xterm [enter]), switch it to your "original" user, (su happybrokenuser), then edit the group file (/etc/group) and add your new user to the "ADMIN" entry by adding a : to the end of the line and it's name. (just look at the other ones for an example), save the file, then logout of Gnome and back in (all with the new user) and it should be Sudo happy.

My two ideas from here are that you can either try to repair that account (but I wouldn't know how), or, move the contents of it's home directory to your new one and chown them to the new user. (chown -R username:groupname /home/username) (where groupname is the same as the username unless you set a custom GID).

This'll retain your previous setting sas they're all stored in the dotted files...

If anyone sees falws or possible clarifications in this method, say so :-P
- Kev

PS: I'm sure it'd be preferred to just fix the old account, but I'm not sure how to do this.

---

### Post by extarbags on 2005-11-04
Well let me ask you this: if I delete the user that's broken, will the home directory get deleted with it? If not, it's not really *that* big a deal to just delete the account and make a new one with that username, I guess, but it could be a pain otherwise.

---

### Post by kvidell on 2005-11-04
```
DESCRIPTION
       The userdel command modifies the system account files, deleting all entries that refer to login.  The named user must exist.  The options which apply to the userdel command are:

       -r     Files in the user’s home directory will be removed along with the home directory itself and the user’s mail spool.  Files located in other file systems will have to be searched for and deleted manually.
```My thinking is that if you just do```
sudo userdel happyuser
```without the -r flag, it won't trash your user account...
You might back it up just to be sure. Just tar it and let the file chill in /home/ until you see if it's okay or not.
- Kev

---

### Post by extarbags on 2005-11-04
This is so unbelievably effed up. My username appears to have come back magically, *but now I can't sudo, with either account*, because I accidentally added my new username to the admin entry in /etc/group with a colon instead of a comma. So I can't do anything... at all. Awesome.

Any last minute thoughts on how I can edit that file? It looks like I'm going to have to reinstall ;_;.

---

### Post by Xian on 2005-11-04
[QUOTE=extarbags]Any last minute thoughts on how I can edit that file? It looks like I'm going to have to reinstall ;_;.[/QUOTE]
Have you tried booting into recovery mode?

---

### Post by extarbags on 2005-11-05
[QUOTE=Xian]Have you tried booting into recovery mode?[/QUOTE]

[img]http://images.ibsys.com/2005/0515/4490722_200X150.jpg[/img]

You saved me so much time. Everything is working silky smooth now. Thanks for you help, everybody!

---

### Post by kvidell on 2005-11-05
Oh my... That image is awesome. *saves*

Glad you finally got it fixed... though I'm curious as to what you did that fixed it...
Did you finally resort to using the recovery options/mode?
- Kev

---

