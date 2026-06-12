---
title: "jaunty upgrade fetchmail pam failure"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by sjv on 2009-06-19
I'm trying to upgrade to Jaunty, and during the upgrade process I was asked for the password for fetchmail. I entered mine and it didn't work, so install failed. I don't ever remember setting one. I went to the command line and ran "dpkg --configure -a", and I tried my password, as well as root, and just about any others I thought I would have used, nothing worked. I also tried deleting the password through passwd, as well as changing it. Anyone know what I need to do here?

Here is the output:
```

~$ sudo dpkg --configure -a
Setting up fetchmail (6.3.9~rc2-4ubuntu1) ...
Password: 
chsh: PAM authentication failed
dpkg: error processing fetchmail (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 fetchmail

```

Thanks,
Steve

---

### Post by sjv on 2009-06-19
Just a quick update. Not sure if it helps at all, but after consulting /var/log/auth.log I get the following entries:

```

Jun 19 14:19:41 dev1 sudo:    steve : TTY=pts/4 ; PWD=/home/steve ; USER=root ; COMMAND=/usr/bin/dpkg --configure -a
Jun 19 14:19:48 dev1 chsh[7386]: pam_unix(chsh:auth): authentication failure; logname=steve uid=0 euid=0 tty= ruser= rhost=  user=root

```

So it's trying to authenticate my user account, and not fetchmail. I don't understand why this is happening when I run dpkg with sudo, since I'm already authenticated as root. The log looks to show like it's asking me for my password to become root, but it's obviously not working.

---

### Post by sjv on 2009-06-22
Can anyone help with this? I have been all over google, and have no idea how to correct this problem.

---

