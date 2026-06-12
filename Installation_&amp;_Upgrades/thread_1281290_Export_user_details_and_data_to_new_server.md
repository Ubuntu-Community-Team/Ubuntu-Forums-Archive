---
title: "Export user details and data to new server"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by pvee on 2009-10-03
hi

I m a developer in windows for long and last wk I started my journey in ubuntu world, but not an absolute beginner though. I wish someone here could help or point me to the right direction.

we have a ubuntu server (dedicated for our nightly build, unit test) crashed and the server is no longer usable but the hard disk is safe. I have instatlled ubuntu server on a new pc.
how do I copy existing user data to new pc..... at least a user "autobuild" group "autobuild" settings and data so that it will use all previous settings, data for the user to continue in the new build. Im sure it not trivial just like copying the prev home folder to the new pc and create new user with the same name ? 
(thought asking gurus here because I just dont want to loose any data or setting just incase I do something wrong)

thanks in advance 

pvee

---

### Post by akakingess on 2009-10-03
Actually, it should be that easy, that is why during installation I create a seperate /home partiton, if anything crashes, then I just do a reinstall and all my personal data is safe. You may have to reinstall some software, but whatever personal settings there were should still be in your home folder, just be sure to get the hidden stuff, too. View hidden by hitting CTRL +H while browsing your home directory.

---

### Post by ermeyers on 2009-10-03
> **pvee said:**
> hi

I m a developer in windows for long and last wk I started my journey in ubuntu world, but not an absolute beginner though. I wish someone here could help or point me to the right direction.

we have a ubuntu server (dedicated for our nightly build, unit test) crashed and the server is no longer usable but the hard disk is safe. I have instatlled ubuntu server on a new pc.
how do I copy existing user data to new pc..... at least a user "autobuild" group "autobuild" settings and data so that it will use all previous settings, data for the user to continue in the new build. Im sure it not trivial just like copying the prev home folder to the new pc and create new user with the same name ? 
(thought asking gurus here because I just dont want to loose any data or setting just incase I do something wrong)

thanks in advance 

pvee
Copy the home directories over.  The usernames and groups have user ids (uid) and group ids (gid) that need to be matched up.  Try to adduser's in the same order that you had.  If you 'ls -l' you'll see the usernames and groups of the files and directories.  If you view /etc/passwd you'll see usernames with user1:x:1000:1000 for the first user uid=1000, gid=1000.  If you view /etc/group you'll see group user1:x:1000.  There's the command "chown" that you need here.  You "sudo chown user1:user1 filename' changes ownership for a file or directory.  "cd /home" and "ls -l" to see what the user directories look like.  The ownership names should match up with the home directory names.  "sudo chown -R user1:user1 user1", etc. The "-R" means recursive.

$cd /home
$ ls -l
total 4
drwxr-xr-x 48 user1 user1 4096 2009-10-03 06:51 user1

If new home "autobuild" doesn't look like this you need to "chown -R autobuild:autobuild autobuild":
$ ls -l
total 4
drwxr-xr-x 48 autobuild autobuild 4096 2009-10-03 06:51 autobuild

---

### Post by ermeyers on 2009-10-03
A good recursive copy is "cp -Rpd from to".  And if you need to be root for a long time, use "sudo -s -H".  If you need help with mounting the old disk, I can help you with that.

---

