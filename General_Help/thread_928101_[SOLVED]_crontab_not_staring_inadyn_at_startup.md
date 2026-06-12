---
title: "[SOLVED] crontab not staring inadyn at startup"
date: 2008-09-23
forum: General Help
---

### Post by tarun.winlin on 2008-09-23
I am not sure what am I doing wrong here.
I have my root user disabled on my box.

Here is my crontab configuration for the root user:
root@tarun-desktop:~# crontab -u root -l
# m h  dom mon dow   command
@reboot /usr/sbin/inadyn #Runs at boot

Now when I reload my PC I do this to check if inadyn is running
root@tarun-desktop:~# ps -A | grep inadyn
root@tarun-desktop:~#

I run inadyn by itself & it runs fine:
root@tarun-desktop:/etc# /usr/sbin/inadyn
INADYN: Started 'INADYN version 1.96' - dynamic DNS updater.
I:INADYN: IP address for alias 'tarunlohumi.homeip.net' needs update to '59.178.50.70'
I:INADYN: Alias 'tarunlohumi.homeip.net' to IP '59.178.50.70' updated successful.

What am I missing?

---

### Post by rmockler on 2008-09-23
Instead of crontab, I start inadyn in the shell script at /etc/rc.local. Screenshot is attached.

---

### Post by tarun.winlin on 2008-09-23
Thanks, but I think I got my answer.

Cron job was failing - reason - my root account was disabled - I enabled it - cron jobs working fine now

correct command to disable root account without causing it to expire: 'sudo usermod -p ! root'

This would replace the hash in the shadow file corresponding to the root user to '!' which makes the password an invalid hash & hence the root account becomes locked because it is not an empty password, but it has a password that cannot be matched.

The command to enabled the root account again would be 'sudo passwd root' which would prompt you to change the password & then replace that password as the hash for the root account in the /etc/passwd file. Now since your root a/c has a valid hash - it works !!

The problem is that if you use the 'sudo passwd -l root'   command to disable the root a/c it appends a '!' to the password hash for the root a/c in the /etc/passwd file but also sets the account expiry field to 1 which causes the account to expire when you enable it back using the command 'sudo passwd root'

So, conclusion is to lock the root account use the command 'sudo usermod -p ! root' instead of the 'sudo passwd -l root' command. And to enable the root account back use the 'sudo passwd root' command.

These are the original posts that helped me a lot to find this answer.

[http://ubuntuforums.org/showthread.php?t=859210](http://ubuntuforums.org/showthread.php?t=859210)

[http://ubuntuforums.org/showthread.php?t=846093&highlight=cron+root+user+expired](http://ubuntuforums.org/showthread.php?t=846093&highlight=cron+root+user+expired)

[http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/shadow-file-formats.html](http://tldp.org/LDP/lame/LAME/linux-admin-made-easy/shadow-file-formats.html)

---

