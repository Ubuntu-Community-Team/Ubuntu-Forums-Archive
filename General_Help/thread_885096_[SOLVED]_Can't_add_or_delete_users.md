---
title: "[SOLVED] Can't add or delete users"
date: 2008-08-09
forum: General Help
---

### Post by FizzBuntu on 2008-08-09
Hi
I'm trying to modify my users list (Have to add 2 and delete 1)
but when I go to user management, everything is greyd. As it doesn't ask for my admin password, i've tried starting it with gksudo but it didn't change anything.

Any clues ?


thx

---

### Post by ad_267 on 2008-08-09
They've changed how this works in Hardy.

You need to click on Unlock and then enter your password.

---

### Post by FizzBuntu on 2008-08-09
yup, I've figured that out but the unlock button is also greyd...

---

### Post by mike2357 on 2008-08-09
Do you have another user account?  One that has permissions to administer the system?  If you do, then Unlock hopefully won't be grayed out.

---

### Post by ad_267 on 2008-08-09
Hmm ok well that's weird. Can you use sudo for other things fine so you're definitely in the admin group?

---

### Post by ad_267 on 2008-08-09
I'm not sure how to fix this but I can tell you how to do this from the command line.

To add a user you do:
"sudo adduser username"
Then use the "groups" command to see what groups you are in. Then:
"sudo adduser username groupname" to add the new user to each group you want them to be in.
You can use "groups username" to see what groups a user is in.

To delete a user you use:
"sudo deluser username"

---

### Post by FizzBuntu on 2008-08-09
I do have administration rights on the system and sudo is working fine elsewhere. 
In facts i was using gksudo so I tried launching users-admin from command line with sudo and there I got some kind of an error message

** (users-admin:25526): CRITICAL **: Unable to lookup session information for process '25526'

does that help ?
Usually when there's CRITICAL in the message, it's not a good sign...

---

### Post by mike2357 on 2008-08-09
I don't have any problems with Unlock being grayed out, yet when I ran the same command you did (sudo users-admin) I got the same CRITICAL error message.

---

### Post by ad_267 on 2008-08-09
I guess it's something to do with the new way the users and groups works so it has to be run by a normal user. I don't know why the Unlock button is greyed out though. It might be a bug, you could report it on launchpad.

Found a couple of bugs that could be related:
[https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/221363](https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/221363)
[https://bugs.launchpad.net/ubuntu/+source/policykit-gnome/+bug/231246](https://bugs.launchpad.net/ubuntu/+source/policykit-gnome/+bug/231246)

I get the same error message running sudo users-admin and the unlock button is greyed out.
Running gksu users-admin I don't get the error message but the button is greyed out.

---

### Post by FizzBuntu on 2008-08-12
yes bug #221363 workaround works !!!

thx for the help

---

