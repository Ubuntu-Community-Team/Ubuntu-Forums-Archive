---
title: "unison (ssh) works manually, but not with cron"
date: 2008-07-30
forum: General Help
---

### Post by evencoil on 2008-07-30
Strange problem, which I believe is due to cron changing paths or something, but I don't know enough to know how to fix it.

If I run
  unison myunisonprofile
everything works fine

But when I try the same command running under a crontab and then check my unison logs, it fails with 
  Fatal error: Lost connection with the server

I'm guessing that cron is changing paths and not finding my ssh auth keys, or something. But I don't know how to diagnose it further or fix it!

---

### Post by Potatoj316 on 2008-07-30
what is the crontab entry you used?

---

### Post by evencoil on 2008-07-30
I did crontab -e and put this in:

0,5,10,15,20,25,30,35,40,45,50,55 * * * * unison myunisonprofile

I have checked the crontab logs and it is running the correct command at the correct times.

---

### Post by Potatoj316 on 2008-07-30
I would do it like this.  The first part (*/5) is not necessary it just makes it neater.  

*/5 * * * * whatToRun

---

### Post by evencoil on 2008-07-30
i'm not really concerned about my crontab style; i just want it to work. The crontab is running the program successfully (verified by the crontab logs) so I don't think that is the issue...

---

### Post by Potatoj316 on 2008-07-30
yeah i understand that you want to make it work and dont care how it looks.  It seems that everyone has cron problems.  Your computer is on at the time right?  what is this program suposed to do?

---

### Post by drs305 on 2008-07-30
> **evencoil said:**
> I did crontab -e and put this in:

0,5,10,15,20,25,30,35,40,45,50,55 * * * * unison myunisonprofile

I have checked the crontab logs and it is running the correct command at the correct times.

You need to include the complete path to *myunisonprofile* (and perhaps unison, depending where it is installed).

---

### Post by jimv on 2008-07-30
I did an odd work around to get SSH key authentication to work in a script. (It was running as me, but it wasn't picking up my key.)  I ran a script that dumped my SSH_AUTH_SOCK environment variable to a file at boot with this command:

```
env | grep SSH > ssh_env.txt
```

Then I put a step in my script that needed SSH to export the environmental variable from that file...so it looked like this:

```
SSH_VARIABLE=$(cat /home/jim/ssh_env.txt)
export $SSHVARIABLE
```

Then the SSH connection worked fine from the script.

---

### Post by evencoil on 2008-07-30
> **jimv said:**
> I did an odd work around to get SSH key authentication to work in a script. (It was running as me, but it wasn't picking up my key.)  I ran a script that dumped my SSH_AUTH_SOCK environment variable to a file at boot with this command:

```
env | grep SSH > ssh_env.txt
```

Then I put a step in my script that needed SSH to export the environmental variable from that file...so it looked like this:

```
SSH_VARIABLE=$(cat /home/jim/ssh_env.txt)
export $SSHVARIABLE
```

Then the SSH connection worked fine from the script.

Excellent, thanks jim. That is a great workaround and works perfectly for me. I would still like to know why cron changes the environment variables and what the logic is behind this...anyone know? And could I change them without doing a workaround like this?

---

### Post by Matt McCutchen on 2008-08-01
The same issue came up [on the rsnapshot list](http://sourceforge.net/mailarchive/forum.php?thread_name=d18977190808010812y2bfb9e87g719599976cb2d362%40mail.gmail.com&forum_name=rsnapshot-discuss).

> **evencoil said:**
> I would still like to know why cron changes the environment variables and what the logic is behind this...anyone know?

To say that cron changes the environment is a misconception.  The ssh agent is placed in the environment ([font=monospace]SSH_AUTH_SOCK[/font]) when you log in and is inherited by any programs started in that login session, even across an [font=monospace]su[/font].  However, since cron is a background daemon that isn't part of any particular session, cron jobs never get an ssh agent unless you insert it into their environment manually.  I would recommend directing any ssh processes started from cron to the proper key using an [font=monospace]-i[/font] option or an [font=monospace]IdentityFile[/font] line in [font=monospace]~/.ssh/config[/font].

---

### Post by evencoil on 2008-08-05
Well this didn't work as well as I had thought it did...it seems to have just stopped working even though I am making sure that the ssh_env.txt file workaround is updated as per jim's suggestion.

I tried both of Matt's suggestions too and neither of these work. I continue to have everything working PERFECTLY when I manually run unison, and have "Fatal Error: Lost connection with the server" when it runs in my cron. I am completely stumped now. Anyone else have ideas?

---

### Post by Matt McCutchen on 2008-08-06
evencoil, I need some information about your setup.  Are you starting unison on the local machine or after you have already ssh-ed to another machine?  What user is unison running as when you start it manually, and when you start it through cron?  What file contains the private key that is authorized on the remote host?

To narrow down the problem, try changing the cron job to a plain ssh command like:
```
ssh -vv user@remotehost echo foo >/tmp/log 2>&1
```  Compare the output of that command to a simple [font=monospace]ssh -vv user@remotehost echo foo[/font] at the terminal.  The [font=monospace]-vv[/font] output should show what private keys ssh is trying in each case.

---

### Post by evencoil on 2008-08-07
Hi Matt,

I'm running unison on the local machine. Both manually and in cron I am running unison as the same user. The private key is ~/.ssh/id_rsa.

I'm having difficulty with the code you gave me. If I run it manually of course I get a nice log file, but when I run it with cron the file just has "foo" in it. I'm still pretty novice with bash, so sorry for the stupid question.

---

### Post by Matt McCutchen on 2008-08-09
> **evencoil said:**
> If I run it manually of course I get a nice log file, but when I run it with cron the file just has "foo" in it.

That's bizarre.  Try putting the ssh command line in a shell script, like this:
```
#!/bin/bash
ssh -vv user@remotehost echo foo >/tmp/log 2>&1
```
and calling that script manually and from cron.  Does the same thing happen?

---

### Post by evencoil on 2008-08-10
Ok, when I put it in a script, cron runs it and creates the proper log file. Comparing the log files, however, I see no important differences. Both are using the same ssh config file, the same key and are successfully connecting. Seems like its a unison issue, then?

---

### Post by Matt McCutchen on 2008-08-10
Yes, the problem would appear to be with unison.

---

### Post by richardhuxton on 2008-09-29
The problem (as someone mentioned elsewhere) is probably ssh-agent not running from your cron-job's point of view.

You can solve this by creating another key-pair which you will only use for this and then specifying that ssh use that.

ssh-keygen -t dsa -f ~/.ssh/crontabkey_dsa

Then, so unison makes ssh use the right identity files:

unison -terse -batch ... -sshargs '-i /home/USER/.ssh/crontabkey_dsa' ssh://server//home/USER ...

Now, you *must* keep those key files safe since they don't have a protecting pass-phrase so anyone with access to them can connect to the server. At the very least add a "from=" to the relevant line in the server's authorized_hosts file (man 8 sshd), so that the key can't be used from a different machine.

Normally you'd have a "command=" clause, but I don't think that will work for unison. You also can't have the cron-job run as a different user since it needs access to your files on the local machine.

HTH

---

