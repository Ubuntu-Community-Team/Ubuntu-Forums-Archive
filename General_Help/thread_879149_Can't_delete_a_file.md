---
title: "Can't delete a file"
date: 2008-08-03
forum: General Help
---

### Post by rmeng on 2008-08-03
Hello everyone.

After I've removed one of the users on my PC I went to delete his home file.

Everything got removed except one directory. 

The permissions of the file are d????????? with ? as owner and the group owner belongs to.

When I've tried to delete the file with root permissions, it also said "permission denied". When I've tried to change the permissions using chmod it also didn't let me. 

I guess I can live with this file however I am curious - is there any way to remove it? 

I would be glad to receive some advice.

---

### Post by tdcdodger on 2008-08-03
thats very odd that the chmod doesn't work..

any luck with the chown or chgrp?

---

### Post by rmeng on 2008-08-03
Nope, same thing....

---

### Post by mike2357 on 2008-08-03
This is the behavior you would get if your former user had an encrypted file system.  If this is the case, the following steps might work:

1.  Figure out your former user's User ID.  To do this, cd to /home, then do an ls -l.  The owner of his or her home directory should show a number, such as 1005, as the owner.

2.  Re-add the user, making sure the User ID is preserved.  The user name shouldn't matter, and you can set the password to anything.

3.  Execute the following command (assuming the user name is xyz) to "become" the former user:
sudo su xyz
Or just log in as that user

4.  If this theory is correct, you should be able to delete the former user's files.

5.  Now re-delete the user.

---

### Post by rmeng on 2008-08-03
Didn't work.

User ID just like the name/group is question mark... 

There's no reason why that user would have an encrypted file system - I've created it for couple of hours to test something.

BTW when I type the ls command I also receive the "permission denied" message.

---

### Post by mike2357 on 2008-08-03
OK - Maybe simpler is better.

Theory #2 -- You don't have execute permissions on the former user's home directory.  Try
sudo chmod 777 /home/<former_users_home_directory>

Then you should be able to delete what's in it.  You may have to cd to the home directory and do the same thing on directories in it.

Good luck.

---

### Post by geirha on 2008-08-03
Most likely there is an error on that filesystem. A reboot should run a quick fsck and fix it if that is the case.

---

### Post by rmeng on 2008-08-03
That was the first thing I've tried before I asked for help... :confused:

---

### Post by rmeng on 2008-08-03
geirha, thx....

Another reboot did solve the problem actually...

---

### Post by geirha on 2008-08-03
Hm, that's odd, I thought fsck would fix such errors. How about booting the ubuntu CD, and run «sudo fdisk -l» (to find the correct partition) and «sudo fsck.ext3 -f /dev/sda1» (assuming it is /dev/sda1). This should force a full filesystem check, not just a quick one.

EDIT: Ah it got fixed. Good to hear :)

---

