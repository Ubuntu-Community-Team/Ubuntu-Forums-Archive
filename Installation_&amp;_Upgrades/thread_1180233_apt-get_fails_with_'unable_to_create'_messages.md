---
title: "apt-get fails with 'unable to create' messages"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by tim_t on 2009-06-06
I have somewhat recently installed ubuntu 9.4, and have installed some updates as they appeared in the package manager or update program.  I'll apologize in advance as I did not write down exactly what steps were taken, but [edit:  "Days after running an apt-get update and apt-get upgrade"] I noticed an update to openssh, and attempted to install it -- failed -- checked on some dependencies, and started trying to upgrade those.  long story short, I have a list of packages that keep getting marked for removal, and they fail to remove.  If I set it to upgrade or reinstall, it also fails.  Here is the message I get right now:

```
E: /var/cache/apt/archives/cron_3.0pl1-105ubuntu1.1_i386.deb: unable to create `./usr/sbin/cron'
E: /var/cache/apt/archives/update-motd_1.11.1_all.deb: unable to create `./usr/sbin/update-motd'
E: /var/cache/apt/archives/openssh-server_1%3a5.1p1-5ubuntu1_i386.deb: unable to create `./usr/sbin/sshd'
E: /var/cache/apt/archives/foomatic-db-engine_4.0.0-0ubuntu6.1_i386.deb: unable to create `./usr/sbin/foomatic-kitload'
E: /var/cache/apt/archives/cups_1.3.9-17ubuntu3.1_i386.deb: unable to create `./usr/sbin/cupsd'
E: /var/cache/apt/archives/cups-bsd_1.3.9-17ubuntu3.1_i386.deb: unable to create `./usr/sbin/lpc'
E: /var/cache/apt/archives/cups-client_1.3.9-17ubuntu3.1_i386.deb: unable to create `./usr/sbin/cupsaddsmb'
```I get the same message when I run apt-get from the command line even as root.

Here is something I find quite strange:  all of the files except update-motd are currently present on my system, but even root cant seem to create the file (even an empty one)

```
root:/usr/sbin# ls -al lpc
ls: unrecognized prefix: do
ls: unparsable value for LS_COLORS environment variable
-rwxr-xr-x   1 root     root         9612 Apr 28 05:59 lpc
root:/usr/sbin# ls -al cupsd
ls: unrecognized prefix: do
ls: unparsable value for LS_COLORS environment variable
-rwxr-xr-x   1 root     root       400584 Apr 28 05:59 cupsd
root:/usr/sbin# ls -al foomatic-kitload 
ls: unrecognized prefix: do
ls: unparsable value for LS_COLORS environment variable
-rwxr-xr-x   1 root     root         3246 Mar 27 06:12 foomatic-kitload
root:/usr/sbin# ls -al sshd
ls: unrecognized prefix: do
ls: unparsable value for LS_COLORS environment variable
-rwxr-xr-x   1 root     root       268804 Jan 28 16:01 sshd
root:/usr/sbin# update-motd
root:/usr/sbin# touch update-motd
touch: cannot touch `update-motd': Permission denied
root:/usr/sbin# touch ./update-motd
touch: cannot touch `./update-motd': Permission denied
```Permissions seem to be ok on the sbin folder? right?

```
drwxr-xr-x   2 root     root        12288 May 31 19:15 sbin
```any help is greatly appreciated.

---

### Post by tim_t on 2009-06-28
bumping this question again -- the problem is still there -- anyone have any ideas?

---

### Post by avidan on 2009-11-13
we are having the same issue. anyone know whats going on with this?

---

### Post by tim_t on 2009-11-13
Update:  After considerable snooping, I found some fishy looking files (directories named '.' and the like)  I ran a rootkit checker program and my system had been comprimised.  I'd suggest backing up your files and check for rootkits (I think the program is 'chrootkit' or so...
 
Good luck!

---

