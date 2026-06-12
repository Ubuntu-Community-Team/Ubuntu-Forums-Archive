---
title: "Problem Logging In ($HOME/.dmrc Issue)"
date: 2008-09-02
forum: General Help
---

### Post by nbmatt on 2008-09-02
So, I work for a *relatively* small company and we're installing a web server in one of the offices. Installing Ubuntu went swimmingly, as did the installation of Apache2/PHP/MySQL/Perl, etc, but I encountered a HUGE problem after I tried to install wu-FTPd. 

See, during the installation through Synaptic the configuration hung up for several minutes (like 10). Now apparently this was the wrong thing to do, but I forced the computer into shutdown. Upon reboot I was surprised to see an unfamiliar message upon login - something to do with my home folder not having the correct permissions and whatnot.

The exact message read:
> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

I immediately looked up solutions on the internet and tried many of the ones suggested here. Here's what I've tried so far to no avail:

I've tried the following in "failsafe xterm" and the actual recovery root login terminal.

```
chmod 644 /home/nmatt/.dmrc
```

```
chmod 644 /home/nmatt/.dmrc
chown nmatt /home/nmatt/.dmrc
chmod -R 700 /home/nmatt
chown -R nmatt /home/nmatt
```

and I've also tried editing the '/etc/gdm/gdm.conf' file, making RelaxPermissions=2 and CheckDirOwner=false.

None of these things work and it continues to present this error and refuses to log me in completely (it logs me out immediately if I try to continue past the error message). 

I would appreciate any help as reinstalling Ubuntu is a last resort I'd rather not have to go through again (especially after all of the other work I've done so far).

Thanks a lot for any help given!

---

### Post by ibuclaw on 2008-09-02
Did you run chmod and chown in that order?

using the -R option on your home directory is usually a bad idea, but you could try the following without anything else.

```

sudo chown nmatt:nmatt $HOME -R

find $HOME -type d -exec chmod 755 "{}" \;

find $HOME -type f -exec chmod 644 "{}" \;

```
Basically, change your home folder/files to it's default permissions.

Regards
Iain

---

### Post by nbmatt on 2008-09-02
Oh geez!

I tried what you suggested and after I entered the last command and let it run (while spitting out a seemingly endless amount of Permission denied messages) the terminal refused to let me reboot (once again, permission denied). I pressed the reset button on my PC and tried to boot up again only to be presented with a new, different error message than ever before:

```
run-init: /sbin/init: Permission denied
[   58.0754051] Kernel panic - not syncing: Attempted to kill init!
```

Uh oh! :(

---

### Post by stoneage on 2008-09-02
I can't fix your present problem, but I just wanted to chip in my 2c worth as I had the same .dmrc issue recently. After successfully chown and chmod I still had the same message at login. I resolved it by doing the same for the other user account. 

Hope you get it sorted.

This is the fix I found:-

```
chown -R user:group /home/user
chmod -R 755 /home/user
chmod 600 /home/user/.dmrc   /home/user/.ICEauthority
shutdown -r now
```

---

### Post by mssever on 2008-09-02
> **nbmatt said:**
> Oh geez!

I tried what you suggested and after I entered the last command and let it run (while spitting out a seemingly endless amount of Permission denied messages) the terminal refused to let me reboot (once again, permission denied). I pressed the reset button on my PC and tried to boot up again only to be presented with a new, different error message than ever before:

```
run-init: /sbin/init: Permission denied
[   58.0754051] Kernel panic - not syncing: Attempted to kill init!
```Uh oh! :(
Looks like your permissions are totally screwed. You can try booting from a live CD and fixing them manually, but it might be easier to reinstall.

---

### Post by nbmatt on 2008-09-03
Does Ubuntu have an option to simply repair install? As in it reinstalls all of the required system files and settings but leaves everything else intact?

---

### Post by mssever on 2008-09-03
> **nbmatt said:**
> Does Ubuntu have an option to simply repair install? As in it reinstalls all of the required system files and settings but leaves everything else intact?
LaRoza has written a system restore program: [http://ubuntuforums.org/showthread.php?t=678665](http://ubuntuforums.org/showthread.php?t=678665) , but it might be too late for that.

You should also examine the permissions of /sbin/init from a live CD (since that's what your error referenced). They should be:
```
~:$ ls -l /sbin/init
-rwxr-xr-x 1 root root 88K 2008-04-11 08:50 /sbin/init
```

---

