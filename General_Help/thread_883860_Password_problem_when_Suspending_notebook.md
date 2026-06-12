---
title: "Password problem when Suspending notebook"
date: 2008-08-08
forum: General Help
---

### Post by ragflan on 2008-08-08
Hi. I'm under Hardy Heron. I just noticed that when I suspend my notebook and resume it at a later time, I cannot enter my password normally. My password is a mixture of lower case and upper case characters, and the login screen doesn't allow me to type the upper case characters. 

When I try inputing an uppercase character, a fat cursor (like the one that appears if you press the 'INSERT' key) appears and it doesn't allow me to type the uppercase characters.

I have to switch user and then I can type my password normally.

---

### Post by sdennie on 2008-08-08
I'm not sure what is causing the problem, but, two potential fixes would be:

1) Try hitting Ctrl-Alt-F1 and then Ctrl-Alt-F7

2) Use gconf-editor and navigate to /apps/gnome-power-manager/lock and uncheck suspend.  This will prevent the screen from locking on suspend which may not be desirable behavior but, it's a potential fix for the problem.

---

### Post by ragflan on 2008-08-09
Oh thank you! Even though it's a notebook, I hardly carry it around, so I don't need the password prompt on resume (although I do need it to keep my pesky roommates from looking around in my laptop). But this is a good fix for now. If anything else occurs to you, please let me know. Thanks again!

---

### Post by ragflan on 2008-08-11
[SIZE="3"]Part 1: If fixable.[/SIZE]: 

Hi, the problem is this:

I suspend notebook. 
Once it sleeps, I resume the session.
Password Prompt: 

The **first character** in my password **is uppercase**.

All the lower case characters are working fine and enter normally.
But when I press **Shift + M** (which is the first character of my password), the **cursor changes** to the type which is shown when you **press the insert key**. Then I cannot type Shift M. 

It's so strange! Everything else types out just fine. Why, just this one thing? Any ideas? **Every other uppercase character is fine as well.**



[SIZE="3"]Part 2: If it cannot be fixed.[/SIZE]

I've considered changing my password to avoid this behaviour. 

I'm the sole user on this account and right now my user password and the root password are the same (I don't remember having typed a separate password for the 'root' user). **So, if I change MY password, is the root password changed as well?**

---

### Post by sdennie on 2008-08-11
As for #2, the password you use for sudo is always the password for the user you are logged in as.

---

