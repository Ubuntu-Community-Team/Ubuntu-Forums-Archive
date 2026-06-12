---
title: "root password problem for updates"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by jimsmith80220 on 2006-02-02
I seem to have installed Ubuntu from the shipped disks ok ( though it comes up Edubuntu ) but I am unable to get updates anymore with a failure of wrong root password ( I did get updates successfully at the start). I probably screwed things up when I changed the root password from a console using

su -
passwd

I can log in as root on a console with the new password but somehow the gui does not like it.

I also had a problem using automatix, when it asked for a password I ended up using my user ( not root ) password which worked, but after downloading firefox 1.5 my browser still says 1.07. I am probably not doing something correctly here also.

thanks for any help with these issues.

JS

---

### Post by mscman on 2006-02-02
Root login at the login screen is disabled by default. Go to system>Administration>Login Window and click on the security tab.  Enable "Allow local system administrator login."  Also note that logging in and running as root all the time can be insecure and isn't advised.  You should try to avoid logging in as root as much as possible and simply using the "sudo" command in terminals.

My only advice for the firefox issue is to try running automatix again with only the firefox package enabled.

---

### Post by jimsmith80220 on 2006-02-02
Unfortunately when I try any administrative functions that require a root login, I am unable to log in as root because it will not take the password. After a few attempts it fails completely and I must log out.

---

