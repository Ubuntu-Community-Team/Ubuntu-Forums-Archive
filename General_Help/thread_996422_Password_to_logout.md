---
title: "Password to logout?"
date: 2008-11-28
forum: General Help
---

### Post by manolomanolo on 2008-11-28
Hi.

It's been some days since I'm asked for password in order to halt the system. Quite strange thing, never happened before...

[http://img212.imageshack.us/my.php?image=screenshotauthenticatewv8.png](http://img212.imageshack.us/my.php?image=screenshotauthenticatewv8.png)

Cliking on the blue link (Action) a window opens showing some menu to enable/disable actions requiring password.

1) What caused that?
2) How to remove that request for password?

Reading some stuff on that menu it seems that a password could be requested in order to halt the system even if there are other user connected: anyone entered my system?!?

Thanks for your help!
Regards.

---

### Post by cariboo on 2008-11-28
To find out if you have other people logged on to your system in a Applications--Accessories-->Terminal type:

```
who
```

The result would be something like this:

```
 who
jim     tty2         2008-11-25 18:57
jim     tty1         2008-11-25 18:54
jim     pts/0        2008-11-28 17:41 (jack.local)
```

As you can see from the above I am logged in three times (this is on my server) I have two consoles open on the server and the third one is from me looging into the server from my desktop computer.

Another thing to check while you have the terminal open is to type:

```
last
```

This will show you a listing of all the people that have logged into your computer.

Jim

---

