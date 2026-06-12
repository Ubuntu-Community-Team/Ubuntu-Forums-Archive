---
title: "[SOLVED] Does command line email work in a SSH environment?"
date: 2008-07-28
forum: General Help
---

### Post by djxcon on 2008-07-28
I have recently set up ssh on Ubuntu Hardy and can access this computer remotely from a Windows PC using Putty.  

I would like to know if a program such as nail will work in this type of environment and whether or not it would need a tweak in order to work in ssh.

Please let me know your thoughts and if you recommend any other program for this type of scenario.

---

### Post by cariboo on 2008-07-28
The quick answer is yes. If you installed the server version or if you have mysql installed exim4 is installed by default, there are various other mta's available like postfix.

To configure exim4 in a terminal type

```
sudo dpkg-reconfigure exim4-config
```

There is a postix howto here:

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Jim

---

### Post by HermanAB on 2008-07-28
Unless you plan to support millions of mail users, then I would advise against using Postfix, since it is simply too hard to set up. A good Postfix system with MySQL back end, webmail and web calendars, Spam control and so on, will take an experienced admin about a week to set up.  An inexperienced admin would need several weeks of dedication.

On the other hand, Citadel will provide you with everything you need and more, it can handle tens of thousands of users and can be set up in about 20 minutes.  See [http://www.citadel.org](http://www.citadel.org) and run the Easy Install script.

Cheers,

Herman

---

### Post by djxcon on 2008-07-28
Thanks for the replies!  I really only need one user to have access to ssh and email (myself). This is so that I can check Pop3 mail (not Gmail) from remote locations.

---

### Post by dontodd on 2008-07-28
If you're going to be reading mail via ssh, I'd give mutt a go. You'll need to install something for smtp, perhaps smail would do it?

---

### Post by djxcon on 2008-07-29
I think I can use something like Links2 in order to check POP3 mail from ssh.  This seems to be a decent option.

---

