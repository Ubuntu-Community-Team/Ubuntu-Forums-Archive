---
title: "Sticky bit"
date: 2008-07-25
forum: General Help
---

### Post by Jungingen on 2008-07-25
Hi everyone, 

This question is not actually about UBUNTU, but this is the biggest linux/unix forum online i know.

See, i must give all users ssh access, with rbash as default shell. It's not allowed for them to look at the other user home directory, so their homedirs has 700 permission. The problem is i need to have some root owned files in their homedirs (.profile (for restricting their path), .procmailrc for local mail delivery), but they still have rights to delete those files, because they are owners of their homedirs.

I checked out example on internet about sticky bit, in which is told to change permission of directory to 1755, and files not to be deleted to 400. That works, but in this case, user is given ability to look at other user home directory, which is not allowed.  

Then, following that example, i changed all home directories to 1700, but all users are still able to delete those files.

filesystem: ufs

So, the question remains, how it is possible to isolate those users in their homedirs and not allow them to delete .profile and .procmail root owned files?

Any help would be appreciated.
Thanks

---

### Post by Yannick Le Saint kyncani on 2008-07-25
Example for a user named jungi which belongs to a group named jungi and is the only one belonging to that group :

- chown root:jungi /home/jungi
- chmod 1770 /home/jungi
- chown root:jungi /home/.profile
- chmod 0640 /home/.profile

And apply the same permissions to all users.

---

### Post by Jungingen on 2008-07-25
> **Yannick Le Saint kyncani said:**
> Example for a user named jungi which belongs to a group named jungi and is the only one belonging to that group :

- chown root:jungi /home/jungi
- chmod 1770 /home/jungi
- chown root:jungi /home/.profile
- chmod 0640 /home/.profile

And apply the same permissions to all users.


Thanks for your answer, but this can't solve my problem, cause all my users belong to group "mail" for some reasons :/

---

### Post by Yannick Le Saint kyncani on 2008-07-25
Users can belong to multiple groups, so you could make a group for any of them and give the additionnal group mail to them all.

---

