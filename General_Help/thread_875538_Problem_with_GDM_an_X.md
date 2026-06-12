---
title: "Problem with GDM an X"
date: 2008-07-30
forum: General Help
---

### Post by msmarc on 2008-07-30
I recently installed ubuntu server edition on a g4 mac and got everything to work. At some point I uninstalled gdm, couldn't boot into linux, reinstalled it remotely but now I can't get it to work.

My terminal works fine, I've tried to purge gdm and ubuntu-desktop and reinstall but no luck.

When I start gdm I get to the login screen, try and login and then the 1st error I get says the dmrc file in the home directory has the wrong permissions. Even if I change those permissions i get the same error when I try again.

If I continue past that error I get and error saying:
Can't create dir /var/Desktop
Can't create dir /var/Documents
and so on through all the main folders

It seems like I have problems with permissions in the home and var folder but I don't know how to fix them. What are the permissions supposed to be?

hers' the ls -li info for var:
drwxrwr-x root root
and for home
drwxr-xr-x root root

Somebody please help, I really don't want to have to reinstall the whole thing.

---

### Post by PmDematagoda on 2008-07-30
For the permissions of home, was it just the home or was it your own home directory?

And by the looks of it, it seems that GDM is trying to create folders in /var, which is quite wrong.

---

### Post by msmarc on 2008-07-31
for the /home directory the permissions are:
drwxr-xr-x root root

for the /home/<username> they are:
drwx------ msmarc msmarc 

I switched the permissions for var to:
drwxr-xr-x root root

This was just to match what the rest of the directory's in / said, I wasn't sure if it was correct or not.

Thanks for looking into it.

---

### Post by PmDematagoda on 2008-07-31
You didn't perform the permissions change in var recursively did you?

And what happens if you try running GDM again?

---

### Post by msmarc on 2008-07-31
Unfortunately last night I started to get antsy and I followed somebody elses advice and chmod -R 755 * in my var folder and now I can't even login to root anymore.  I'm not sure its even fixable anymore, I'll probably have to reinstall tonight.

It's all a learning experience, but I'm kind of bummed I didn't get a chance to try and fix it without having to reinstall. I guess I should be more careful about using "recursive" option and maybe shouldn't always trusts everyones' advice

Thanks for the help though, I'll try to be more patient next time

---

