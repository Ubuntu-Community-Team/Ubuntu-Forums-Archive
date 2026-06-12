---
title: "webmin user = who?"
date: 2004-10-16
forum: General Help
---

### Post by wayover13 on 2004-10-16
Ok.  I wanted LVM support since I'll be adding at least one other disk to this system where I installed Ubuntu.  Not too familair with LVM, but finally figured out the partitioning part of things.  It seems Ubuntu comes with all the relevant command line tools for admin'ing LVM, but being the sissy-newbie I am, I want a GUI.  Where's my GUI!?  Anyway, not finding one, and being a somewhat experienced Debian user, I knew where to find one.  Searched using Synaptic and up turns a webmin module for admin'ing LVM.  I downloads and installs the mutha.  But now, when I go to log in, it won't accept my user and his passwd.  Whenn I try "root" and the sudo passwd, that won't work either.  So how the heck am I supposed to use this new webmin mdule and find out what it'll do in terms of LVM admin?  Do I need to create a root user?  Is there already - the horror! - some default root passwd for Ubuntu?  How 'bout a little input on this issue?

Thanks

---

### Post by bdoetsch on 2004-10-16
I think the default password for root is empty. Anyway, you can change the root password to your liking with something like

sudo passwd root

Then it should be no problem to login to webmin...

---

### Post by wayover13 on 2004-10-16
From somewhere out on the web:
> Using Webmin
Access Webmin through your favorite Web browser. Two of the tools, a file explorer and a telnet/ssh client, are applet-based and will require a Java Runtime Environment to be installed on your browser. These tools are handy, but not critical. All of the other modules have no special requirements.

To begin using Webmin, point your browser to port 10000 on the system. With a browser on the local system, you would use [http://localhost.localdomain:10000/](http://localhost.localdomain:10000/). Webmin will first bring you to a login screen.

Webmin users are separate from operating system users. This allows you to set up users for administration through Webmin that are not in the normal Unix authentication scheme. However, if you have users that you want to be able to use Webmin, you can enter them into the Webmin user list and have Webmin authenticate them through Unix facilities rather than through its internal mechanisms. Access to Webmin modules can be controlled for each user. Helpdesk staff could have access to just password functions, while other staff could have access to all modules, for example.

A root user is automatically created with the system's root password upon installation. Webmin logs activity by login, so in a multi-admin environment, it would probably be better to create an admin group with the rights of the root user, and create users for each individual who works on the system. Your first login must be as root. 

So when I installed webmin using Synaptic, it created a root user with the system's password.  So, what is the system's password?  What is the name of this user?

---

### Post by wayover13 on 2004-10-16
I finally resolved this by uninstalling webmin, changing root's passwd (per d's directions), then reinstalling webmin.  Yes, that's a kludge.  One of the ways the sudo method of administration leaves something to be desired.  Is there a way to fix this for those who may need to install webmin or other things that expect a root passwd?

Anyway, when all's said and done I find out Ubuntu (and maybe Debian) seems to be doing something non-standard with LVM.  The webmin module expects a /proc/lvm directory but finds none and thus concludes LVM is not installed or working on this system.  I know otherwise from other things the system tells me, and from having gone through alengthy setup/install with LVM.  Fodder for another thread . . .

---

### Post by zerohalo on 2004-11-14
I have the same problem, and I've tried unistalling webmin, changing root password, reinstall webmin, and I still can't get in. I try "root" as user and my new root password, and I get access denied. Stuck!

---

### Post by Razvan on 2004-11-14
have you deleted the wbmin config folder in /etc/webmin?

maybe webmin saves the password informations in an passwd-style file nd doesnt delete them when uninstalling..."just in case, you'd like to see your messed up config again, abfter reinstalling ;-)"

---

### Post by TravisNewman on 2004-11-14
[QUOTE=Razvan]have you deleted the wbmin config folder in /etc/webmin?

maybe webmin saves the password informations in an passwd-style file nd doesnt delete them when uninstalling..."just in case, you'd like to see your messed up config again, abfter reinstalling ;-)"[/QUOTE]
 delete webmin with the --purge or "complete removal" option and then enable root, give root a password, and then install webmin.

---

### Post by hndrcks on 2004-11-15
In /usr/share/webmin/ there is a Perl script called changepass.pl to change root password in webmin use this:

# /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>

And that will fix it! No install/removal necessary.

---

### Post by TravisNewman on 2004-11-15
[QUOTE=hndrcks]In /usr/share/webmin/ there is a Perl script called changepass.pl to change root password in webmin use this:

# /usr/share/webmin/changepass.pl /etc/webmin root <your passwordhere>

And that will fix it! No install/removal necessary.[/QUOTE]
 Thanks! I wish I'd known about that a couple weeks ago!

---

### Post by vyoufinder on 2008-02-08
What if my Webmin user has been deleted?  Is there a way to restore this?  I have backups of my Webmin configuration, but no way to get back in now!

I tried the password change script but that's how I found out my username had been deleted.

---

