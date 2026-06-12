---
title: "cdrom and sound Permissions for user problems..."
date: 2005-12-08
forum: Installation &amp; Upgrades
---

### Post by ispmarin on 2005-12-08
Hello everybody. Here i come to talk about a problem that, IMHO, is serious. When you do a fresh install of Ubuntu Breezy (and Hoary had the same ), sometimes even the user that you creates on the installation does no have permission on /media/cdrom (/dev/hd*) or /media/floppy. And when you have a nis enviroment, things get worse: you have to add manually all the users on the nis database to the /etc/group file to correct this problem. Same goes to the sound: you have to add manually your user to the audio group, and add the /dev/dsp and /dev/mixer to the same group. There should be some automatic way to do this: the new user that does not understand very well linux wants the sound and drivers working out of the box, and not modify any files ! And this reminds me of something else: Why the root password is not configured on boot time? You have to do sudo passwd root to change the password...
Just my two cents to the improvement of linux... and Ubuntu!

Thank you!

---

