---
title: "Too many users...!"
date: 2005-12-06
forum: General Help
---

### Post by tomwell on 2005-12-06
Hi all,

Does anyone know why i would have all these users...?? am sure its something really stupid like some programs are added as users?? but why?? and is it normal???

Peace

Tom

---

### Post by soulestream on 2005-12-06
might wanna uncheck show users and groups button. 

most of those are groups like audio and noboby group


soule

---

### Post by daller on 2005-12-06
Right!

...but I havent seen "/home/syslog" and "/home/klog" before... (I assume "/home/tom" is your directory!)

Anyways, how many of those are displayed when unchecking "Show all users and groups"??

---

### Post by Bandit on 2005-12-06
[QUOTE=daller]Right!

...but I havent seen "/home/syslog" and "/home/klog" before... (I assume "/home/tom" is your directory!)

Anyways, how many of those are displayed when unchecking "Show all users and groups"??[/QUOTE]
I agree, I havent seen that before either.. its kinda strange..

---

### Post by soulestream on 2005-12-06
they have to be related to the daemons. 
they are also /bin/false so no one could actually log in. 

i have them on my ubuntu system also.

soule

---

### Post by tomwell on 2005-12-06
[QUOTE=soulestream]they have to be related to the daemons. 
they are also /bin/false so no one could actually log in. 

i have them on my ubuntu system also.

soule[/QUOTE]

Are you guys saying that perhaps someone could log in to my machine??? When i uncheck show all users, only my group shows ie tom....

Do you guys all have some extra users??

Peace

Tom

---

### Post by henriquemaia on 2005-12-06
[QUOTE=tomwell]Are you guys saying that perhaps someone could log in to my machine??? When i uncheck show all users, only my group shows ie tom....

Do you guys all have some extra users??

Peace

Tom[/QUOTE]

Everyone has all those users. Most of them are for programs, so that they can run with special (or not) previleges. If you're running a webserver and using Apache, for instance, you have user www-data, which gives apache access to /var/www, where it stores its public pages. Mysql has his own user, and so on.

Uncheck the Show all users and groups and you'll see only the ones that matter for the normal user - the users who can login on the machine.

---

### Post by soulestream on 2005-12-06
I guess technically someone can use another user account to log in, but my understanding is /bin/false cant get access to anything, it is probably something that they use to monitor logs. 

Also is you check, /home/syslog doesnt exist.

They are most likely harmless, however I am curious as to why they are there.

soule

---

### Post by tomwell on 2005-12-06
Well that is great news!!!

Am reassured...

henriquemaia thank you for your reply it has definately clarified the situation as to why i have lots of users...

Thank you to all who took there time to anwser...

Peace

Tom

---

