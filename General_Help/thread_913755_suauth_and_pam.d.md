---
title: "suauth and pam.d"
date: 2008-09-08
forum: General Help
---

### Post by leeko on 2008-09-08
Hi,

Can anyone tell me how to run a command as a different user within a script, without requiring password input? I tried editing /etc/suauth so that my "leeko" user can run the following script, which runs irexec as user "mythtv". 

```

#!/bin/bash
# Launcher for IREXEC because it's STUPID and won't launch properly in startup scripts!
sleep 30
killall irexec
su mythtv -c "irexec /home/leeko/.lircrc" &
exit 0

```

My /etc/suauth looks like this:

```

leeko@leeko-media:~$ cat /etc/suauth
#leeko and mythtv can su to each other without a password
leeko:mythtv:NOPASS
mythtv:leeko:NOPASS
#
```

It didn't work, so I googled and found this page:

[http://ubuntuforums.org/showthread.php?t=251059&highlight=suauth](http://ubuntuforums.org/showthread.php?t=251059&highlight=suauth)

It suggests that ubuntu has deprecated /etc/suauth, and instead uses pam.d/su. But, I can't figure out how to edit this file so that user "leeko" can su to user "mythtv" without a password. Can anyone point me in the right direction? 

Thanks,

Lee

---

### Post by HalPomeranz on 2008-09-08
You can do this pretty easily with sudo instead of su.  First add this line to your /etc/sudoers file:

```

leeko   ALL = (mythtv) NOPASSWD: ALL

```

Then, instead of using su in your script, use a line like:

```

sudo -u mythtv irexec /home/leeko/.lircrc &

```

---

### Post by leeko on 2008-09-08
Hi Hal,

Thanks for the reply. I did as you suggested, but I ran into a small snag: It still asks me for a password when I run the script. 

Here's the contents of my sudoers file:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL
mythtv ALL=NOPASSWD: /etc/acpi/*
leeko ALL=NOPASSWD: /etc/acpi/*
mythuser ALL=NOPASSWD: /etc/acpi/*
mythtv ALL=NOPASSWD:/sbin/halt,/sbin/shutdown,/sbin/reboot,/bin/mount,/bin/umount,/usr/sbin/pmi
leeko ALL=NOPASSWD: /usr/sbin/pmi
leeko ALL = (mythtv) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

And my startup script (which is owned by leeko):

```

leeko@leeko-media:~$ cat /usr/local/bin/irexeclauncher
#!/bin/bash
# Launcher for IREXEC because it's STUPID and won't launch properly in startup scripts!
sleep 20
killall irexec
sudo -u mythtv irexec /home/leeko/.lircrc &
exit 0

```

When I reboot, the script kills the existing process, then does nothing else. If I run the script manually, it asks me for a password. If I've previously run a sudo command and entered my password, then the script runs flawlessly without requiring a password. 

I'm guessing that the entry in sudoers isn't doing what it's supposed to, but I've no idea how to fix it. 

Any ideas?

Thanks,

Lee

---

### Post by leeko on 2008-09-08
Been playing around a bit more - 

If I try:

sudo -u mythtv <command> 

from the CLI, it does the same thing (asks me for a sudoers password). If I've already used sudo in that session, it doesn't ask. 

Any help much appreciated :)

Lee

---

### Post by HalPomeranz on 2008-09-08
Weird, your sudoers file looks correct to me and the syntax I gave you should work.  What UID is the mythtv user ("grep mythtv: /etc/passwd" and look at the number in the third field)?  Does the mythtv user have the same UID as some other user on the system?

---

### Post by leeko on 2008-09-08
Hi Hal,

grep gives:

```

leeko@leeko-media:~$ grep mythtv: /etc/passwd
mythtv:x:105:110::/home/mythtv:/bin/sh
leeko@leeko-media:~$    

```

grepping for 105 gives only the mythtv entry. grepping for 110 gives:

```

leeko@leeko-media:~$ grep 110: /etc/passwd
mythtv:x:105:110::/home/mythtv:/bin/sh
sshd:x:110:65534::/var/run/sshd:/usr/sbin/nologin

```

Not sure what to make of it. I don't think they have the same UID?

Thanks,

Lee

---

### Post by leeko on 2008-09-08
Actually, I've noticed some slightly different (equally weird) behaviour after a reset:

- The existing irexec -d process is killed, but then nothing else happens
- If I manually run /usr/local/bin/irexeclauncher while logged in as user leeko, it sleeps for 20 seconds, then I get:

```

leeko@leeko-media:~$ /usr/local/bin/irexeclauncher
irexec: no process killed
[sudo] password for leeko: leeko@leeko-media:~$

```

That's not a typo above - as soon as it asks me for the sudo password, it puts "leeko@leeko-media:~$" right after the prompt. As soon, as I press any key, I get :

```

sudo: pam_authenticate: Conversation error

```

Then, it returns my prompt (leeko@leeko-media). But, keypresses are not shown on screen. They do register, and I can logout, but they are not shown. 

I don't really understand this. Please help!

Thanks,

Lee

---

### Post by HalPomeranz on 2008-09-08
The weird terminal behavior you're seeing is because your script is launching the sudo command in the background (that's what the "&" at the end of the sudo line means).  You could do this instead:

```

sudo -u mythtv irexec --daemon /home/leeko/.lircrc

```

This way you'll get the sudo password prompt as normal and it won't mess up your terminal.

But the point is, obviously, that you shouldn't be getting the password prompt in the first place.  It's very strange-- everything looks correct to me.  There should be some log messages in /var/log/auth.log from your sudo attempts-- could you just try doing a command like "sudo -u mythtv id" and post the relevant log entries from /var/log/auth.log?  Maybe there's something I'm missing that will be obvious once I look at the logs.

---

### Post by leeko on 2008-09-08
Hi Hal, 

Again, thanks for your persistence with this! 

sudo -u mythtv id asks me for my password as usual, then afte rpassword entry it gives:

```

leeko@leeko-media:~$ sudo -u mythtv id                                                                                             
[sudo] password for leeko:                                                                                                         
uid=105(mythtv) gid=110(mythtv) groups=20(dialout),24(cdrom),29(audio),44(video),110(mythtv)

```

cat /var/log/auth.log gives:

```

Sep  8 18:23:24 leeko-media sudo:    leeko : TTY=pts/0 ; PWD=/home/leeko ; USER=mythtv ; COMMAND=/usr/bin/id
Sep  8 18:23:24 leeko-media sudo: pam_unix(sudo:session): session opened for user mythtv by leeko(uid=0)
Sep  8 18:23:24 leeko-media sudo: pam_unix(sudo:session): session closed for user mythtv

```

Hope this helps,

Cheers,

Lee

---

### Post by HalPomeranz on 2008-09-08
Hmmm, well the log messages look normal.  Nothing out of the ordinary there.

Perhaps your "leeko" account is sharing a UID with another account?  Try "grep leeko: /etc/passwd", note the UID, and then check to see if there are other accounts in the password file with your UID.

I notice that there are a couple of other sudoers entries for your leeko account:

```

leeko ALL=NOPASSWD: /etc/acpi/*
...
leeko ALL=NOPASSWD: /usr/sbin/pmi

```

If you run "sudo /usr/sbin/pmi" from your leeko account, do you get prompted for a password the first time, or does it let you run the command without typing the password ever?

---

### Post by leeko on 2008-09-09
Hi,

no, my leeko account is uid 1000, but it doesn't seem to share a uid with anything else:

```

leeko@leeko-media:~$ grep leeko: /etc/passwd
leeko:x:1000:1000:lee alkureishi,,,:/home/leeko:/bin/bash
leeko@leeko-media:~$ grep 1000: /etc/passwd
leeko:x:1000:1000:lee alkureishi,,,:/home/leeko:/bin/bash
leeko@leeko-media:~$

```

And yes, it does ask me for a password the first time I sudo /usr/sbin/pmi. I never noticed it before, because I hadn't tested it yet (because it's related to this issue, which isn't yet resolved; i'm trying to set up suspend from my remote control). 

What's going on with my setup? 

Regards,

Lee

---

### Post by HalPomeranz on 2008-09-09
Hmmmm, I am truly perplexed.

I guess the next thing to verify is that there isn't some non-printing character that's messing up your sudoers file somehow.  The first thing to try is just doing "sudo visudo".  Make a small change to the file like adding a comment or some such thing, save the file, and quit out of the editor.  That should cause visudo to run a syntax checking pass over the contents of your new sudoers file and tell you if there are any problems.

If visudo doesn't report any problems, the next step would be to try and simplify the problem a little.  First make a backup copy of your original sudoers file ("sudo cp /etc/sudoers /etc/sudoers.SAVED").  Then do "sudo visudo" again, and change the file so that it contains only these lines:

```

Defaults        env_reset
%admin ALL=(ALL) ALL
leeko ALL = (mythtv) NOPASSWD: ALL

```

Once you've saved the new file, open another window and see if you can do "sudo -u mythv id" and not be prompted for your password.  If it works as expected with this minimal sudoers file, then you can start adding entries back into the file one at a time until it stops working.  Remember that each time you run a test you'll have to do it in a new window (don't close the old windows!) in order to force sudo into a situation where it would normally prompt you for your password.

---

### Post by leeko on 2008-09-09
Hi Hal,

It didn't make any difference, once I removed the other entries. It still asks me for a sudo password for mythtv. I even rebooted to double-check - still asks for a sudo password (I know, rebooting could have left me in a pickle, but hey..). I've uploaded a copy of my sudoers file, so you can see the exact layout of the file. I had to change the permissions on the file (777) so that I could upload it. Previously it was read-only for owner and group (owner root). There were no write or exec permissions on the file (I think that's how it's supposed to be?).

It's located here:

[http://alkureishi.com/sudoers](http://alkureishi.com/sudoers)

Thanks again,

Perplexed!

---

### Post by HalPomeranz on 2008-09-09
The file you uploaded looks good to me.  And, yes, read-only and owned by root, group root is the correct permissions for /etc/sudoers.  You should reset the permissions to their original values.

When you were first trying to get things working with the /etc/suauth file, did you happen to change any of the configuration files under /etc/pam.d (if you do an "ls -lrt /etc/pam.d" you'll see the most recently modified files at the end of the listing)?  If you get rid of the /etc/suath file, does that change the behavior of the sudo program?  I'm grasping at straws here, but I'm running out of other ideas.

---

### Post by leeko on 2008-09-10
Hi,

No, the last modified file was back in July. I didn't start my monkeying till last week. 

I moved suauth to suauth.SAVED, rebooted and tried again. It still asks me for a sudo password when I run

sudo -u mythtv id

This is killing me! I'm sure it is for you too!

Don't know if this is important, but I'm administering the machine via ssh, as it's attached to my tv. Would that account for any of the weirdness? 

Lee

---

### Post by HalPomeranz on 2008-09-10
The fact that you're logged in via SSH shouldn't make a difference.

One more thing I'd like to try.  Change your /etc/sudoers file so that it reads:

```

Defaults        env_reset
%admin ALL=(ALL) ALL
leeko ALL = ALL
leeko ALL = (mythtv) NOPASSWD: ALL

```

Then remove your leeko account from the admin group in /etc/group-- that way the "%admin ..." entry in /etc/sudoers won't apply to you anymore (you should still be able to do things as root however, because of the "leeko ALL = ALL" line added above).  Then try "sudo -u mythv id" and see if you get prompted for the password.

My thought is that perhaps the "%admin ..." line is overriding all of the other configuration lines.  Since there's no "NOPASSWD" clause in the "%admin ..." line, you'll always get prompted for the password, regardless of the other settings in the file.  It comes down to how sudo handles precedence for overlapping rules in its configuration file.

---

### Post by leeko on 2008-09-10
Ah, that would make sense. 

I've made the changes you suggested, and it worked! 

irexec now starts up as user mythtv, based on my startup script :) 

I can't thank you enough for sticking with me on this! 

Now, the problem is that irexec doesn't seem to be working properly, even when run as mythtv user. I think I should probably start another thread for that though!

Thanks so much!

Lee

---

### Post by HalPomeranz on 2008-09-10
Well, that's an interesting resolution for this problem.  I learned something about the way sudo handles it's rules, that's for sure.

Anyway, glad I could help.  Hope you get the irexec issue worked out...

---

