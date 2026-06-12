---
title: "Encrypted ZIP from a script"
date: 2008-10-23
forum: General Help
---

### Post by daemonk on 2008-10-23
Hi,

I am trying to create an encrypted zip file using the zip -e 

The problem is that I want to run this from Cron so will need a solution where I can pass the password through the command line or some other way besides being prompted for a password.

Is there anyone that can guide me in the right direction, I have googled loads of pages today and can't find a solution.

Thanks in advance

---

### Post by bodhi.zazen on 2008-10-23
take a look at "expect"

[http://www.linuxjournal.com/article/3065](http://www.linuxjournal.com/article/3065)

    [http://www.linux.com/articles/56066](http://www.linux.com/articles/56066)

---

### Post by Dr Small on 2008-10-23
I'm not exactly sure how this would work, since I don't have zip installed, but you could try something like this:
```
echo "password" | zip -e
```

Alternately, you can skip encrypting it with a password, and setup a GPG keypair and encrypt the entire file.

Edit:
Bohhi beat me to it. Yes, I forgot about expect.

---

### Post by daemonk on 2008-10-23
Thanks!

I came right using the GPG route, I will be playing with the echo ""... method as well as I reckon that would be very handy.

Thanks!

---

