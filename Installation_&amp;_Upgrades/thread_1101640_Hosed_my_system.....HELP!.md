---
title: "Hosed my system.....HELP!"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by BobbyS on 2009-03-20
Hello,

I am running Ubuntu 8.10

I was changing permissions so I could install a program and hosed my system somehow. After rebooting I cannot log in. I get this message:  [-o<

GDM could not write to your authorization file. This could be because your drive is full or your home directory could not be opened for writing. In any case it is not possible to log in.

I know for a fact that my drive is not full as this is a fresh install and I allowed plenty of room on my partitions. How can I get in, or am I going to have to reinstall (I hope not)?

Sooooo..........can someone please help me? Thanks in advance for any help!

Thank You
BobbyS

---

### Post by utnubuuser on 2009-03-20
Have you tried getting in through the rescue console and changing permission to 755 for your root user?

> sudo chmod -R 755 /
There was a thread a while back about restoring proper permissions to system folders.

755 owner-read/write/execute - group-read/execute, and others-read/execute
 -might be a good starting point.

and I think 754 would probably be ok too.

---

### Post by taurus on 2009-03-20
What permissions did you change and what directory (directories)?  To help you save your machine, you should include the commands that you ran.

And by the way, I would definitely hold on running that command from the post above.

---

### Post by cariboo on 2009-03-20
I would suggest you start in recovery mode and once at the menu, select drop to root prompt. At the prompt type:

```
chmod -R 755 /home/<username>
```

Where <username> is your user name. You will get a couple of errors, but you should be able to at least login. You may have to change the permissions on ~/.dmrc to 640 once you are back to your desktop.

Jim

---

### Post by BobbyS on 2009-03-20
I was trying to change permissions on /

---

### Post by BobbyS on 2009-03-20
I used the:
 
chmod -R 755 /home/<username>

But it will not let me in.I get the same error.

---

### Post by taurus on 2009-03-20
What is your login name?

Changing permissions starting from / (recursively) could cause trouble down the line even if you can log into your account.

---

### Post by BobbyS on 2009-03-20
My login name is bobby

---

### Post by taurus on 2009-03-20
Boot into recovery mode from GRUB menu and get into root shell.  Then, run

```
chmod -R 755 /home/bobby
chown -R bobby:bobby /home/bobby
chmod 600 /home/bobby/.dmrc
chmod 600 /home/bobby/.ICEauthority
```
Reboot and see if you can log in to your account, bobby, again.

---

### Post by BobbyS on 2009-03-20
I ran that code but it still gives me the same error and will not let me in.

---

### Post by ajgreeny on 2009-03-20
> **BobbyS said:**
> I was trying to change permissions on /
Oh boy!  I think you may have caused yourself a major problem if you have changed permissions of files in the root filesystem without really knowing what you were doing, and I suspect that you may have to start again.  However, wait for more answers before doing that as someone else may have a brilliant idea that has not occurred to me.  I also suspect that changing your /home folder back to your ownership, if it had been taken away by whatever you did, will not really help much as it sounds as if it's the system root files that are now wrongly set, not /home files.

---

### Post by BobbyS on 2009-03-20
I think that is the case. I l look at it like this, I am new to this and usually, after hosing it big time I will learn alot.

---

