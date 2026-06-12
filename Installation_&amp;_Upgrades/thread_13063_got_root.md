---
title: "got root?"
date: 2005-01-28
forum: Installation &amp; Upgrades
---

### Post by gogodidi on 2005-01-28
I can't do anything!!!

what's the root password?

I can't apt-get install
I can't change the fstab file
I can't do anything...
what's wrong

is there a default set password for root
how do you change it?
where do you change it?


-thanks for any help, i'm new to debian...

---gogodidi

---

### Post by DJ_Max on 2005-01-28
By default you use the password of the first account created. Also, their is no account named 'root'. So you can't su. If you want to, you'll have to configure it that way.

sudo apt-get install [BLAH]

---

### Post by gogodidi on 2005-01-28
thanks
atleast i can use apt-get now..

---

### Post by tim1 on 2005-01-28
[QUOTE=DJ_Max]So you can't su.[/QUOTE]

Yes you can.

try

$ sudo su

greets, tim

---

### Post by celloandy on 2005-01-28
Also, you can use sudo passwd to add a root password, if you feel the need.  I was so used to using su with previous distros that it was more comfortable for me to work that way, but the Ubuntu methodology would, I'm sure, be just as good once you got used to it.

Andrew

---

### Post by oracledarren on 2005-01-28
Although it is not recommended as the previous post says you can open a terminal and type sudo passwd root to change or create the root password.

If you want to also login through the gdm as root then you need to goto

computer->system configuration->login screen setup

then if you pick the tab that says security there is an option to allow root logins.

But is must be stressed, doing this sort of thing leads to bad habits forming and potentially leaving your system vunerable  :D 

Hope this helps

Darren

---

