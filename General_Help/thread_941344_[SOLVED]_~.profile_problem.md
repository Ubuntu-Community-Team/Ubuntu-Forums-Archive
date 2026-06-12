---
title: "[SOLVED] ~/.profile problem"
date: 2008-10-08
forum: General Help
---

### Post by prem1er on 2008-10-08
I just made a new user for my server and the remote shell doesn't have the same functionality as my original user.  I'm assuming it has something to do with the .profile or .bashrc file, but I can't figure it out from there.  Any links or suggestions?

---

### Post by kpkeerthi on 2008-10-08
Can you be specific as to what you mean by 'same functionality'? What are you missing when you login as the new user?

---

### Post by justleen on 2008-10-08
if unsure what functionality, just copy .bashrc and .profile from your orginal user...

---

### Post by prem1er on 2008-10-08
@kpkeerthi
The functionality I am talking about is for instance when I log onto the new user instead of

```
user@hostname
```

for my prompt I get 

```
$
```

Also, tab complete doesn't work and the up arrow used to give me my history.  


@justleen
Which file controls what?  Why are there two of them?  A link would be sufficient if you have a good one.

Edit: I have also just copied the .bashrc and .profile files from my original user and it produced the same result.

---

### Post by kpkeerthi on 2008-10-08
> **prem1er said:**
> 
Edit: I have also just copied the .bashrc and .profile files from my original user and it produced the same result.

Copy ~/.bash_profile from the original user, if the file exists.
**Note:** You need to log out and log back in.

---

### Post by geirha on 2008-10-08
If you run ```
exec bash --login
``` after logging in, is the prompt set then?

EDIT: Also, it sounds like your new user might have gotten /bin/sh as the default shell, instead of /bin/bash. Check the entry in /etc/passwd

---

### Post by prem1er on 2008-10-08
> **geirha said:**
> If you run ```
exec bash --login
``` after logging in, is the prompt set then?

Yes! Works then. Is there a way to set that up so it works without the exec command?

Edit: Yes the default is /bin/sh, should I switch it?
Edit 2: Changed them.  Works correctly now.  Was it something I did wrong when creating the user?

---

### Post by geirha on 2008-10-08
> **prem1er said:**
> Yes! Works then. Is there a way to set that up so it works without the exec command?

Edit: Yes the default is /bin/sh, should I switch it?
Edit 2: Changed them.  Works correctly now.  Was it something I did wrong when creating the user?

When you create a user with the users-admin (Users and groups), you can set the shell under the Advanced tab. You've probably just changed it accidentally.

---

### Post by prem1er on 2008-10-08
> **geirha said:**
> When you create a user with the users-admin (Users and groups), you can set the shell under the Advanced tab. You've probably just changed it accidentally.

I used the command line on my server to do it.  So I'm guessing there is a parameter to pass in order to do the same thing over a terminal?

---

### Post by geirha on 2008-10-08
> **prem1er said:**
> I used the command line on my server to do it.  So I'm guessing there is a parameter to pass in order to do the same thing over a terminal?

```
sudo adduser *username*
``` will set the shell based on the DSHELL variable in /etc/adduser.conf

---

