---
title: "Root confusion"
date: 2006-09-10
forum: Hardware &amp; Laptops
---

### Post by sp0nge on 2006-09-10
[FONT="Comic Sans MS"]I'm finally getting comfirtable enough within my system to take on a little shell scripting. I seem to have confused my understanding somewhere along the line. When I setup my system, I was prompted to create the root user. This was given a user name, then I created the various user accounts after. 

I come across a lesson to add an alias to .bash_profile, but I must be superuser to open this file. When I attempt to gain superuser permission, I enter the password to the account I presumed had been setup as the root and get this error message: [/FONT]

su: Authentication failure
Sorry.

Is there a way to reset this password or am I looking at a format/re-install situation?

---

### Post by tkjacobsen on 2006-09-10
The superuser is deactivated by default, the first created user have administrating rights using sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tribaal on 2006-09-10
Hum... Ubuntu doesn't use the classic root account. Try entering *your* password when prompted (if you login from an "administrator" account).

You should read [this wiki page]("https://help.ubuntu.com/community/RootSudo"), it will all make sense then.

Hope this helps

- trib'

---

### Post by sp0nge on 2006-09-10
I am slowly finding the value of the wiki... I toyed with sudo a bit and it worked. In aaddition to understanding the by disabling the root account by default, you have to create the root password. Thanks for the help!

---

