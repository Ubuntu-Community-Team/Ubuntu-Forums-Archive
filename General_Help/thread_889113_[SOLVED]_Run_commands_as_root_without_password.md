---
title: "[SOLVED] Run commands as root without password"
date: 2008-08-13
forum: General Help
---

### Post by derrick81787 on 2008-08-13
Hello, everyone.

I'm trying to make it to where I can run /sbin/shutdown and a script /home/derrick/bin/wireless-connect.sh as root without a password.  I've modified my /etc/sudoers file, but it seems like no matter what, it prompts me for a password.

My /etc/sudoers file looks like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL
derrick ALL = NOPASSWD: /sbin/shutdown,/home/derrick/bin/wireless-connect.sh

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

My username is derrick, and everything looks correct to me.  Is there some reason sudo still prompts me for a password when I run these commands?

It may be worth noting that my computer is running an Ubuntu install that started with a minimal installation and then I installed Openbox, etc on top of it, so not everything is the Ubuntu default.  Any help with this problem would really be appreciated.

Thanks,
Derrick

---

### Post by Dr Small on 2008-08-13
What happens if you try?
```
derrick ALL=(ALL) NOPASSWD: /sbin/shutdown,/home/derrick/bin/wireless-connect.sh
```

---

### Post by bodhi.zazen on 2008-08-13
Your syntax is fine. The "problem" is you are calling a script. Each command in the script must be added to the list.

---

### Post by caljohnsmith on 2008-08-13
> **bodhi.zazen said:**
> Your syntax is fine. The "problem" is you are calling a script. Each command in the script must be added to the list.
Am I missing something? That has not been my experience, and I just now tried it out; I can add a script to my sudoers to run without a password, and I don't have to add a separate entry in sudoers for every single command in the script. The script runs fine without a password, and all commands in it are run as root.

Derrick81787, I think your problem might be that you have to add your "NOPASSWD" entry after the group entry:
```
%admin ALL=(ALL) ALL
derrick ALL = (ALL) NOPASSWD: /sbin/shutdown,/home/derrick/bin/wireless-connect.sh
```
Give that a try and let me know if it works.

---

### Post by bodhi.zazen on 2008-08-13
> **caljohnsmith said:**
> Am I missing something? That has not been my experience, and I just now tried it out; I can add a script to my sudoers to run without a password, and I don't have to add a separate entry in sudoers for every single command in the script. The script runs fine without a password, and all commands in it are run as root.

Derrick81787, I think your problem might be that you have to add your "NOPASSWD" entry after the group entry:
```
%admin ALL=(ALL) ALL
derrick ALL = (ALL) NOPASSWD: /sbin/shutdown,/home/derrick/bin/wireless-connect.sh
```Give that a try and let me know if it works.

In my experience it depends on the commands you are trying to run. For example, if you are mounting a samba share, you can not simply add "/bin/mount".

The syntax derrick81787 posted works with simple commands such as "/bin/cat", so I am guessing it is not a syntax error (although I use syntax posted by Dr Small and yourself).

---

### Post by derrick81787 on 2008-08-13
> **Dr Small said:**
> What happens if you try?
```
derrick ALL=(ALL) NOPASSWD: /sbin/shutdown,/home/derrick/bin/wireless-connect.sh
```

I changed it, and it still asks me for my password.  As for the whole script thing, I don't think that's the problem because it prompts me for a password when I run shutdown as well.  I can't figure out what the problem is.  Is it possible that sudo might not even be checking the file at all?

- Derrick

---

### Post by caljohnsmith on 2008-08-13
> **bodhi.zazen said:**
> In my experience it depends on the commands you are trying to run. For example, if you are mounting a samba share, you can not simply add "/bin/mount".

The syntax derrick81787 posted works with simple commands such as "/bin/cat", so I am guessing it is not a syntax error (although I use syntax posted by Dr Small and yourself).
Are you thinking maybe if mount asks you for the password for accessing the samba share, which is different then your user password? I'm just wondering still, because I just now added a script in sudoers as NOPASSWD, and in that script I used "mount" to mount a partition. Running the script didn't ask for a password, and I successfully mounted the partition. So am I still misunderstanding something here?

---

### Post by bodhi.zazen on 2008-08-13
> **derrick81787 said:**
> I changed it, and it still asks me for my password.  As for the whole script thing, I don't think that's the problem because it prompts me for a password when I run shutdown as well.  I can't figure out what the problem is.  Is it possible that sudo might not even be checking the file at all?

- Derrick

You need a space to separate commands :

```
derrick ALL=(ALL) NOPASSWD: /sbin/shutdown, /home/derrick/bin/wireless-connect.sh
```

---

### Post by derrick81787 on 2008-08-14
> **bodhi.zazen said:**
> You need a space to separate commands :

```
derrick ALL=(ALL) NOPASSWD: /sbin/shutdown, /home/derrick/bin/wireless-connect.sh
```

Oh, okay.  Hopefully, that's the problem, then.  I'm not at home right now, but I'll give it a try as soon as I get home.  I'll be sure and post back with the results.

Thanks,
Derrick

---

### Post by Mgiacchetti on 2008-08-14
lol and how many people verified syntax, only to miss a missing space?

lol its just humorous to me.

---

### Post by derrick81787 on 2008-08-14
> **derrick81787 said:**
> Oh, okay.  Hopefully, that's the problem, then.  I'm not at home right now, but I'll give it a try as soon as I get home.  I'll be sure and post back with the results.

Thanks,
Derrick

That didn't fix it.  After that didn't work, I commented out that line and replaced it with this line, just to see what would happen:

```
derrick ALL=(ALL) NOPASSWD: ALL
```

Even with that line in there, it still prompts me for my password.  Does anyone have any ideas?

---

### Post by finer recliner on 2008-08-14
did you restart your computer after saving the changes in your sudoers file?

---

### Post by Vivaldi Gloria on 2008-08-14
Move your line to the end:

```
%admin ALL=(ALL) ALL
derrick ALL=(ALL) NOPASSWD: /sbin/shutdown, /home/derrick/bin/wireless-connect.sh
```

Restart.

---

### Post by derrick81787 on 2008-08-15
> **Vivaldi Gloria said:**
> Move your line to the end:

```
%admin ALL=(ALL) ALL
derrick ALL=(ALL) NOPASSWD: /sbin/shutdown, /home/derrick/bin/wireless-connect.sh
```

Restart.

I'll give that a try as soon as I get home.  Is there a reason why that line should need to be at the end?  I am part a member of the admin group, so do you think that setting is over-riding mine?

- Derrick

---

### Post by bingoUV on 2008-08-15
For some reason, a Cmnd_Alias has been necessary whenever I tried this. Add such code to the end of your sudoers file
```

Cmnd_Alias DERRICKCMD=/sbin/shutdown, /home/derrick/bin/wireless-connect.sh
derrick ALL=NOPASSWD: DERRICKCMD

```

I don't know the reason, but it has never worked for me without a Cmnd_Alias however hard I try.

---

### Post by derrick81787 on 2008-08-15
> **bingoUV said:**
> For some reason, a Cmnd_Alias has been necessary whenever I tried this. Add such code to the end of your sudoers file
```

Cmnd_Alias DERRICKCMD=/sbin/shutdown, /home/derrick/bin/wireless-connect.sh
derrick ALL=NOPASSWD: DERRICKCMD

```

I don't know the reason, but it has never worked for me without a Cmnd_Alias however hard I try.

Thanks a lot.  That worked like a charm.

- Derrick

---

### Post by andrewabc on 2008-08-27
> **bingoUV said:**
> For some reason, a Cmnd_Alias has been necessary whenever I tried this. Add such code to the end of your sudoers file
```

Cmnd_Alias DERRICKCMD=/sbin/shutdown, /home/derrick/bin/wireless-connect.sh
derrick ALL=NOPASSWD: DERRICKCMD

```

I don't know the reason, but it has never worked for me without a Cmnd_Alias however hard I try.

Thank you for this advice. I have searched the internet and all this forum and this was the only way to get it to use shutdown commands without needing password. The manuals and tutorials everywhere did not work.

Spent 2 hours trying to figure it out, and finally came across this thread and this post allowed me to figure it out in a couple minutes.

---

