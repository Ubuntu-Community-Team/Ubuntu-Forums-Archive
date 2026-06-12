---
title: "Ursename and Password"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by u.kirchgraber on 2009-04-19
I have installed unbutu via wubi-installer. When I choose unbutu at the start of the computer, it asks me for a username and password, which I did not enter, when installing. But without correct entries, it does not start. What can i do?

---

### Post by oldos2er on 2009-04-19
Did you install from a LiveCD? The first thing one should always do after creating a bootable CD is to run its integrity check (Check CD for defects), and/or md5sum ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)).

 Any Ubuntu installation should always ask you to create a user and password.

---

### Post by cariboo on 2009-04-19
Start in recovery mode, then at the menu select drop to root prompt. At the prompt type:

```
useradd -d <uername>
```

where <username> is your username without the brackets. The above command will create a user and a home directory. Next you need to create a password for the user. At the prompt type:

```
passwd <username>
```

The above command will ask you to create a password. It will not echo the password back to you as you type. If you don't get an error message you should be good to go. Type exit at the prompt and select resume from the menu. This should take you to the login prompt.

Jim

---

### Post by sisco311 on 2009-04-19
> **u.kirchgraber said:**
> I have installed unbutu via wubi-installer. When I choose unbutu at the start of the computer, it asks me for a username and password, which I did not enter, when installing. But without correct entries, it does not start. What can i do?

You did enter your username and password in Windows:
[IMG]http://psychocats.net/ubuntu/images/wubithumb02.png[/IMG]

If you don't remember the username and/or password, then try this:

[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

