---
title: "In Limbo"
date: 2008-10-15
forum: General Help
---

### Post by GrandBob on 2008-10-15
I was thrilled to have successfully installed (Hardy) Apache2/SSL/PHP5/Subversion/Firebird.  It's awesome.

Then it happened.  I thought it would be more convenient to include www-data in my group list.  Silly me.  In my impatient haste, my username is now in the www-data group ONLY.  Worse, I can't change my group list.  I seems I am no longer in the sudoers file.

I can't sudo anything.  How can I restore order to my universe?

---

### Post by woodenbrick on 2008-10-15
can't you use:
su 
<root password> 
and add yourself back into the sudoers list?

---

### Post by GrandBob on 2008-10-15
Ok... would that be the same password that I have been using for sudo commands?

---

### Post by woodenbrick on 2008-10-15
It's weird, I just checked, Ubuntu doesn't seem to have a default root password, so I guess its either blank, or your user pass.

Try and let me know.

I just set mine now with sudo passwd, though obviously you cant do that right now ;)

---

### Post by yaztromo on 2008-10-15
You could try booting to the recovery console.

---

### Post by GrandBob on 2008-10-15
You are correct on all accounts.

sudo passwd will not work... but

su
<password>       DOES WORK!

Now on to visudo.

Thank you VERY much.

---

### Post by woodenbrick on 2008-10-15
Good that it worked, a bit strange you got removed from the sudoers list.

---

### Post by geirha on 2008-10-15
> **yaztromo said:**
> You could try booting to the recovery console.

+1. Once in recovery mode you will have a root shell (no password required). Add your user to the admin group with
```
adduser yourusername admin
``` and your user should be able to use sudo again. 

Boot back normally, then open the users and groups gui and create a new temporary administrator user. Then add yourself to the groups that new user got added to, and you should be back to normal.

EDIT: Didn't see the latest posts until now. You don't need to change the sudoers file. Just add yourself to the admin group. The sudoers file has an entry for the admin group.

---

### Post by geirha on 2008-10-15
> **woodenbrick said:**
> It's weird, I just checked, Ubuntu doesn't seem to have a default root password, so I guess its either blank, or your user pass.

Try and let me know.

I just set mine now with sudo passwd, though obviously you cant do that right now ;)

Indeed, read about it at [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by GrandBob on 2008-10-15
Now I have TWO ways to get there.

Thank you all again.  I hope that someday I will be able to help some poor soul in Linux trouble.

---

