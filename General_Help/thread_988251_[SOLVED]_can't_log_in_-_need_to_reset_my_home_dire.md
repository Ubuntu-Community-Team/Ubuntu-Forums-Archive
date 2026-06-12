---
title: "[SOLVED] can't log in - need to reset my home directory"
date: 2008-11-20
forum: General Help
---

### Post by englishlion on 2008-11-20
Hi - this is my first post, sorry it's a call for help...

I set my home directory while in ubuntu to an alternative location.  This didn't work and now I can't login.

I get a variety of errors during login starting with cannot find... and then the new home location etc.  Sorry I can't show screenshots or text dumps as this is all before/during login.

I've tried all boot modes but without any success.  I don't have any other 'logins' to try.  I have the 'live CD' to boot from if this helps, maybe the location of the home directory is stored in a config file somewhere?

---

### Post by john183 on 2008-11-20
Have you tried booting from a livecd and copying your home folder to the standard location (/home/"username" where username is your login) and then booting from the harddrive and trying to login?

---

### Post by igor1102828 on 2008-11-20
I'd try to boot from Live CD, then mount HD and tried to use Places --> Search for files

---

### Post by englishlion on 2008-11-20
> **john183 said:**
> Have you tried booting from a livecd and copying your home folder to the standard location (/home/"username" where username is your login) and then booting from the harddrive and trying to login?

my files are still in the original location, it's just looking elsewhere.

---

### Post by john183 on 2008-11-20
What exactly is the error message that you are receiving? With that info i amy be able to figure out what needs changed.

---

### Post by englishlion on 2008-11-20
> **john183 said:**
> What exactly is the error message that you are receiving? With that info i amy be able to figure out what needs changed.

1st error

"Your home directory is listed as:'/media/disk/' but it does not appear to exist. Do you want to login with the / (root) directory? It is unlikely anything will work unless you use a failsafe session."

options are yes or no
-no takes me to blue "gnome" login screen and if I try to login I get the same error.
-yes gives a second error as below...

"User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $Home directory must be owned by user and not writable by other users."

options - OK - this leads to error 3 as below...

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

if I choose to view details there's a long list of entries starting with

Can't create dir /media/disk//

eg Can't create dir /media/disk//Desktop
Can't create dir /media/disk//Music
Can't create dir /media/disk//Templates
Can't create dir /media/disk//Pictures
etc

I then get an entry about libgnomevfs-WARNING that refers to "cannot create~/.gnome2 directory: No such file or directory.

I then click OK (only option) and after a few screen flickers I'm back to login and loop round again!

---

### Post by englishlion on 2008-11-20
Well I very proud of myself - I've managed to sort it.

I booted to the recovery shell and then used the adduser command to add an additional user.  I could then login as the new user and then from there I could change the home directory of my existing user back to what it was.

Thanks for your help anyway

---

