---
title: "Password failure"
date: 2024-11-21
forum: Hardware
---

### Post by CowDoctor on 2024-11-21
I don't know if this is hardware or software, but my laptop has suddenly stopped recognizing my password. I have no idea what to do. Help, please, if there is any.

---

### Post by Bashing-om on 2024-11-21
CowDoctor -

If you do not care to troubleshoot for the cause - \A quick means to get back in business is to set a new password.
Easy Tutorial:
[www.psychocats.net/ubuntu/resetpassword](www.psychocats.net/ubuntu/resetpassword)

-hope this helps-

---

### Post by yancek on 2024-11-22
Which version and release of Ubuntu are you using?  Do you get an error such as authentication failed or some other error?  Does this happen immediately on boot when you try to login or at some other point?

---

### Post by CowDoctor on 2024-11-22
Thank you! Bashing-om.  Of course, it's not quite so easy. When I enter the passwd username command I get a list of options. The two that seem they might be relevant are: -r reset password in REPOSITORY repository or -u unlock the password in the named account. I am being extra cautious about making a mistake in root. 
Yours gratefully, 
Joe the cow doctor. 
PS I am running 24.04 and the error shows up immediately when I turn on the machine and am prompted to enter the password.

---

### Post by ajgreeny on 2024-11-22
Can we check that you have no encrypted partition in your system as you should not have that problem.
Can you also confirm that once you had booted to Recovery Mode you ran the command ```
mount -o rw,remount /
``` to remount the filesystem as read/write. If you omitted tha command nothing you do will make the changes needed.

---

### Post by CowDoctor on 2024-11-22
Yes, I did run that command. It did not give me any error message, just returned me to the command line.

---

### Post by CowDoctor on 2024-11-22
There should not be any encrypted partition. I have never run anything but the Ubuntu that came on the machine when I purchased it from System 76, just regular upgrades

---

### Post by yancek on 2024-11-22
[QUOTE] Yes, I did run that command. It did not give me any error message/QUOTE]

That means the command you ran was successful as it would output an error if it were not.  Have you tried resetting the password per the instructions in post 2?

Had you been using this computer and Ubuntu regularly before this problem occurred and had any changes been made just prior to the problem?

---

### Post by CowDoctor on 2024-11-22
I can't copy and paste the commands and responses, but I'll try to replicate. 
PressEnter for maintenance 
(or press Control-D to continue):
root@Bucky:~# mount -o rw,remount /
root@Bucky:~# passwd Joseph Snyder 
Usage: passwd [options] [LOGIN]

Options:
-a, --all       report password status on all accounts 
-d --delete  delete the password for the named account 
-e  -- expire. force expire the password for the named account 
-h --help  display this help message and exit 
-k -- keep tokens.   change password only if required 
-i -- inactive INACTIVE.  set password to inactive after expiration to INACTIVE 
-l lock --   lock the password of the named account 
-n -- mindays MIN_DAYS set minimum number of days before password change to MIN_DAYS
-q -- quiet.   quiet mode 
-r -- repository REPOSITORY.   change password in REPOSITORY repository 
-R -- root CHROOT_DIR.       directory to chroot into 
-S -- status.      report password status in the named account 
-u -- unlock.      unlock the password of the named account 
-w --warndays WARN_DAYS.      set expiration warning days to WARN_DAYS
-x maxdays MAX_DAYS.     set maximum number of days before password change to MAX_DAYS
root@Bucky~#

---

### Post by CowDoctor on 2024-11-22
I don't think there are any typos, but it at least should be close. Bucky is the name of the computer.

---

### Post by CowDoctor on 2024-11-22
I have been using the computer regularly for years.  It came from System 76 with Ubuntu which has been upgraded regularly.  O had some problems with the 20.04 upgrade, but it was running fine for a couple of weeks before this happened.

---

### Post by CowDoctor on 2024-11-22
You can see that I was following the instructions in that good tutorial and what returned

---

### Post by Bashing-om on 2024-11-22
CowDoctor - Hummm ...

An observation --
> 
root@Bucky:~# passwd Joseph Snyder


I do expect the kernel to see "Joseph Snyder" as two entries - thus invalid as the assumed username.

Run in terminal:
```

ls -al /home

```
To know what the username assignment is.
If in fact you have set the use name as the 2 words, Joseph Snyder, then in the passwd command enclose your username in quote marks:
"Joseph Snyder"

follow through with the tutorial.


-who wudda thunk it ?-

---

### Post by CowDoctor on 2024-11-22
Dear Bashing-om,
    Wellll, all fixed.  Thank you!  Curiously, the first time I just ran ls /home as the tutorial suggested and I could swear it came back Joseph Snyder, which is what show as the name at login.  I tried that with quotations and got a doesn't exist message, so ran ls -al /home and it came back joseph-snyder.  Ran that through the password and all was well.  So, again, thank you, resolved, and maybe some info for the next time?
Yours gratefully,
CowDoctor Joe

---

### Post by Bashing-om on 2024-11-23
CowDoctor - :D

Pleased I could render the aid.

As this issue is now at an end:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]happy trails to you
[/INDENT]

---

