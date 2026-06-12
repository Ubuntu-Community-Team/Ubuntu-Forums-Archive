---
title: "What about the root password?"
date: 2008-08-10
forum: General Help
---

### Post by KOTAPAKA on 2008-08-10
OK I am a Debian user. I started with ubuntu and I just install it. One thing that caught my attention immediately was the absence of the root account. I looked in the internet but couldn´t find an answer to the question: ¨Why?¨ Is it a security reason? Can somebody explain.

---

### Post by lisati on 2008-08-10
you're correct - it's a security thing. Whenever root privileges are required from the command line, Ubuntu uses "sudo" before the command instead.

---

### Post by gjoellee on 2008-08-10
when you are root hacker only need to guess your password and not both your username and password. This is *one *of the reasons

---

### Post by niyonk on 2008-08-10
It is a security reason because when people try to gain access to your machine they will look for the root account.

In this case there is no root account :), so they'll just be gaining nothing EDIT: the root account is disabled by default

see [here]("https://help.ubuntu.com/community/RootSudo")

---

### Post by pparks1 on 2008-08-10
It's not that Ubuntu doesn't have a root account, but rather you don't set it up nor do you know the password.   You can log in and set the root password and use the account if you choose to do so...but with sudo there really is no good reason to do so.

---

### Post by Dr Small on 2008-08-10
> **gjoellee said:**
> when you are root hacker only need to guess your password and not both your username and password. This is *one *of the reasons
Actually, that is scriptkiddies. Unless you are running a service such as SSH or FTP, there is no way to connect to login as a root user, period.

---

### Post by koenn on 2008-08-11
> **KOTAPAKA said:**
> ... I looked in the internet but couldn´t find an answer to the question: 


look here: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

