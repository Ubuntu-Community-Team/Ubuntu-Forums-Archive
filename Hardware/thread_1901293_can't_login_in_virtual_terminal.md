---
title: "can't login in virtual terminal"
date: 2011-12-28
forum: Hardware
---

### Post by QuintenB on 2011-12-28
Hi,
i've been struggling with the virtual terminal today.

I need to install nvidia manually for some reason that ubuntu can't find any drivers for my laptop. I found the right driver and as you probably know you should stop the "x server" from running, before you can install the nvidia driver. 

the problem is... :o surprise!! i can't login... 
I keep getting "login incorrect".

I am the administrator and i tried about everything i knew about ubuntu, even tried to change my password. 
what surpised me is that i CAN login by an standard account but no adminitrators at all.

The standard account is useless to me btw, what i thought..

please help me out, 

thanks in front!!

Quinten

---

### Post by nfarley88 on 2011-12-28
Things to check (may sound silly, but I've made these mistakes!):
[LIST=1]
[*]Check captial letters
[*]Check you have the right password (sometimes I type in the right password for the wrong computer)
[/LIST]

Are you trying to log in as 'root' or as another user?

If you can log in somewhere, try typing ```
sudo passwd
``` to set the root password and then you can log in as root. If it's a standard user, it's unlikely to work, but it's worth a try!

---

