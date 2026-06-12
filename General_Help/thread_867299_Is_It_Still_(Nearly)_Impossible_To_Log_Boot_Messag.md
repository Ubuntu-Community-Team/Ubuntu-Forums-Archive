---
title: "Is It Still (Nearly) Impossible To Log Boot Messages?"
date: 2008-07-22
forum: General Help
---

### Post by Brando569 on 2008-07-22
I've been reading up on this for awhile and the threads that show how to enable bootlogd dont work since they were for SysvInit and ubuntu now uses upstart which is supposed to use logd to log boot messages but it is disabled since it is broken. 

I read in the bug report on launchpad that a guy named sergei edited a version of bootlogd that works and I installed it but it only gives me 3 seconds of boot messages and theyre towards the end, hence theyre no use to me.

I see all of these messages during my bootup but cant what they say and have no idea on how to get rid of them or even see what they say.

Any help would be appreciated.

---

### Post by Brando569 on 2008-08-02
*bump*

---

### Post by ModelM on 2008-08-02
I don't know exactly what you're looking for but just about everything which went on during the last boot can be seen by typing into a terminal:

dmesg | less

---

### Post by Brando569 on 2008-08-02
i just like to have my boot messages logged because sometimes stuff will flash by and i have no idea what it says, its too much hassle to sift through dmesg

---

### Post by ModelM on 2008-08-02
My point is that dmesg *is* the log. If you'd prefer to work from a file, you can find it at:

/var/log/dmesg

The command

dmesg

simply prints this log file to the screen for you.

In fact the man page for the dmesg command tells you about using the command:

```
 The program helps users to print out their bootup messages.

Instead of copying the messages by hand, the user need only:
              dmesg > boot.messages
and mail the boot.messages file to whoever can debug their problem.


```

---

### Post by Brando569 on 2008-08-02
hmm ok then why do dmesg and the boot log look drastically different? (bootlog is way more ledgible)

---

### Post by ModelM on 2008-08-02
I've only ever used dmesg, so I don't know about these others but maybe you should check out bootchart. It's in the repositories & it might be closer to what you're looking for.

---

### Post by Brando569 on 2008-08-02
i just installed it at the recommendation of another user in a thread i made about whether a large kernel vs a smaller kernel really affects performance, ill see how it fares for my needs

---

