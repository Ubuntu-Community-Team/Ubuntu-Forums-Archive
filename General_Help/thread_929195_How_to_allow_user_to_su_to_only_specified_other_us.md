---
title: "How to allow user to su to only specified other user?"
date: 2008-09-24
forum: General Help
---

### Post by TheGoodDocta on 2008-09-24
I'm setting up a development environment where I would like multiple users to be able to act on behalf of one specific other user. I'd rather they not need to remember that other user's password though.

How can I lock down su such that a specific user, without gaining root access, can su to another specific user without using a password? Other users on the system, if they tried to su to this specific user, would be challenged for a password or simply denied.

Any help would be much appreciated...

---

### Post by bodhi.zazen on 2008-09-24
I would think the easiest way would actually be to use groups.

Make a group "Devel" and add the appropriate people in to that group.

Another easy way would be with ssh.

make a new user, "Devel". Make a ssh key for Devel with an empty password. Lock the Devel account.

Now anyone with the ssh key can :

ssh Devel@localhost -i ~/.ssh/Devel_key

---

### Post by ilrudie on 2008-09-25
The solution above may or may not work.  Its the easiest to use though.  The solution for exactly what you want would be to use sudo.  You will have to edit the sudoers file (using 'sudo visudo')  You will need to add a few lines to the file.  The first will be a user alias.

It should look like this:
User_Alias DEVEL = devel1, devel2, devel3

replace devel1, 2 and 3 with the usernames of the developers.

Next add a line that allows them to su to a specific user like:
DEVEL    ALL = (root) /bin/su - devel_target

This essentially says let any member of the DEVEL user group, on ALL hosts, su to devel_target (using only the standard su).  This only requires them to know their own password since they actually perform the su as root.  

If you are confused by how this setup works let me know and I will try to explain it better or you can always read up on sudo and the sudoers file in the man pages.

---

