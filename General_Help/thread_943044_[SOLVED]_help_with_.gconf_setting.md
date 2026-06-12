---
title: "[SOLVED] help with .gconf setting"
date: 2008-10-09
forum: General Help
---

### Post by Pranav Shanker on 2008-10-09
Hi,

I just got a desktop with ubuntu(7.0.4) but i am not being able to log into it. When i try to log in i get the following error

[I]" The files that contain your preference settings are currently in use.
You might be logged in to a session from another computer, and the other login session is using your preference settings files.
You can continue to use the current session, but this might cause temporary problems with the preference settings in the other session.
Do you want to continue?"[/I]

Well no other session is running and i have already removed the ethernet cable just in case. When i click on continue it gives me another error message :-

" Please contact your system administrator to resolve the following problem:
Could not resolve the address "xml:readwrite:/home//.gconf" inthe configuration file "/etc/gconf/2/path":failed: Could not make directory '/home//.gconf' "

Thinking it might be related to some permission to write to directory .gconf i had changed the permissions to 777 but still no luck.

Can anyone please guide me. I am fairly very new to Linux

Thanks Much appreciated

Pranav

---

### Post by Yellow Pasque on 2008-10-09
Let's start with output from:
```
cd /home
ls -la
```

---

### Post by sn3rd on 2008-10-09
Instead of logging in to the desktop environment, try the following:

At the login window, press CTRL + ALT + F1
You should be presented with a terminal login. Now login using your username / password.
Type
> sudo adduser test
and enter your password.
Then enter all the details that you like for a new user named "test".
Try to log in with the user "test" (and "test"'s password).

If this works, then you may need to just reset the user account.

---

### Post by Pranav Shanker on 2008-10-09
SN3RD

Mate I tried what you had told me and it worked it has allowed me to log back into GNOME and now i need to know how to reset my other account or how do i delete that old account and make another account with the same name with full admin rights.

Thanks
Pranav

Temüjin

Thanks for your help mate. I guess SN3RD way helped me to get the issue sorted. I really appreciate your quick reply and response

---

### Post by Pranav Shanker on 2008-10-09
I was finally able to get it working.

SN3RD 

This is what i did in case if it helps someone in the future. I made a new user. Then logged into failsafe Terminal session and then sudo and then i assigned the new user all the admin rights using usermod.

Logged back into GNOME using the new user and resetted the old accounts. And just in case if i goof up in future also made a new extra account as a fall back option.

Thanks All

Pranav

---

### Post by sn3rd on 2008-10-10
> **Pranav Shanker said:**
> SN3RD

Mate I tried what you had told me and it worked it has allowed me to log back into GNOME and now i need to know how to reset my other account or how do i delete that old account and make another account with the same name with full admin rights.

Thanks
Pranav

Temüjin

Thanks for your help mate. I guess SN3RD way helped me to get the issue sorted. I really appreciate your quick reply and response

Pleasure! Sorry I didn't reply to your other posts, timezone :(

I'm glad the problem is sorted! Enjoy!

---

