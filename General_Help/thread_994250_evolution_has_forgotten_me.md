---
title: "evolution has forgotten me"
date: 2008-11-26
forum: General Help
---

### Post by twistedtwig on 2008-11-26
Hi all,

Evolution seems to have forgotten me.  My system did not unmount correctly and when I booted up the next time it did the usual check.  It told me I had to type fsck which I did and it seemed to fix things.  Well i typed exit afterwards the system rebooted and I was able to log in.

All my settings are there, my programs remember me except evolution which asks me to setup a new profile.

I have tried rebooting to fix it (good old windows days) but no difference.

I don't really know where to start with this.

any and all help would be great.

Thanks

---

### Post by cmnorton on 2008-11-26
Go to an x-term to see if there are any evolution directories. They're probably preceeded with a dot (.) character. You might be able to import these directories.

---

### Post by twistedtwig on 2008-11-26
Hi cmnorton,

Thx for the reply.  OK so in  /home/jonh/ I have a .evolution folder with:

drwxr-xr-x 4 jonh jonh  4096 2008-11-15 09:55 addressbook
drwx------ 5 jonh jonh  4096 2008-10-07 22:03 cache
drwxr-xr-x 5 jonh jonh  4096 2007-07-20 23:05 calendar
-rw------- 1 jonh jonh     3 2008-11-26 19:52 camel-cert.db
-rw-r--r-- 1 jonh jonh  3152 2007-06-22 08:01 categories.xml
-rw------- 1 jonh jonh 65536 2008-11-25 20:11 cert8.db
-rw------- 1 jonh jonh 16384 2008-11-25 20:11 key3.db
drwxr-xr-x 8 jonh jonh  4096 2008-11-25 20:11 mail
drwxr-xr-x 5 jonh jonh  4096 2007-07-20 23:05 memos
-rw------- 1 jonh jonh 16384 2007-06-22 08:01 secmod.db
drwxr-xr-x 5 jonh jonh  4096 2007-07-20 23:05 tasks

Not sure how I would import them.  I will make a copy and try and figure it out.. don't want to loose anything either, (if avoidable).

---

### Post by 73ckn797 on 2008-11-26
Off topic but reading literally.

Your thread gives me the mental image that you still have a tail or gills!!

---

### Post by twistedtwig on 2008-11-26
ROFL!!! lol... I am rather tired and that took me 2 reads to figure out what you meant!!! very good.

sleep is in order and see if I can evolve a little :p

The GF might agree its needed.

---

### Post by 73ckn797 on 2008-11-26
> **twistedtwig said:**
> ROFL!!! lol... I am rather tired and that took me 2 reads to figure out what you meant!!! very good.

sleep is in order and see if I can evolve a little :p

The GF might agree its needed.


Understood, my friend. I could not resist the comment. Like Ubuntu there will be no charges for that one!!:guitar:

---

### Post by cmnorton on 2008-11-28
> **twistedtwig said:**
> Hi cmnorton,

Thx for the reply.  OK so in  /home/jonh/ I have a .evolution folder with:

drwxr-xr-x 4 jonh jonh  4096 2008-11-15 09:55 addressbook
drwx------ 5 jonh jonh  4096 2008-10-07 22:03 cache
drwxr-xr-x 5 jonh jonh  4096 2007-07-20 23:05 calendar
-rw------- 1 jonh jonh     3 2008-11-26 19:52 camel-cert.db
-rw-r--r-- 1 jonh jonh  3152 2007-06-22 08:01 categories.xml
-rw------- 1 jonh jonh 65536 2008-11-25 20:11 cert8.db
-rw------- 1 jonh jonh 16384 2008-11-25 20:11 key3.db
drwxr-xr-x 8 jonh jonh  4096 2008-11-25 20:11 mail
drwxr-xr-x 5 jonh jonh  4096 2007-07-20 23:05 memos
-rw------- 1 jonh jonh 16384 2007-06-22 08:01 secmod.db
drwxr-xr-x 5 jonh jonh  4096 2007-07-20 23:05 tasks

Not sure how I would import them.  I will make a copy and try and figure it out.. don't want to loose anything either, (if avoidable).

I could be that you have preserve these directories by moving them somewhere else. Then, you might have to create the new account, and then copy those directories back over what was created by default. I am not en Evolution expert. My recommendations are purely experimental. 

First, I'd see if there is a way to trigger a recovery on the command line.

---

