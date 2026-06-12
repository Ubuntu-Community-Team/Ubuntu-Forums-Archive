---
title: "Loggin as root, got this message: &quot;Your account has expired; please contact your...&quot;"
date: 2008-10-18
forum: General Help
---

### Post by userkwokcmscv on 2008-10-18
I opened terminal and typed command "sudo su" and after that there's the message:
"Your account has expired; please contact your system administrator
su: User account has expired"

Why is this happening?

I can still login as the root, but I'll get always the same message.

---

### Post by sparky-steve on 2008-10-18
Hi,

It may be as simple as a locked-down root account. Try

```
sudo passwd -u root
```

---

### Post by TheNextBillGates on 2009-04-26
RRRGH!!!  I have not been able to find this answer anywhere!

Your post just solved my problem.  THANK YOU!!!

---

### Post by Dr_Willis on 2009-04-26
Just a added comment..  the 'proper way to do the sudo stuff' (taken from a web site whos url is:  [http://ubuntu-tutorials.com/2008/05/09/a-root-shell-on-ubuntu-the-right-way/](http://ubuntu-tutorials.com/2008/05/09/a-root-shell-on-ubuntu-the-right-way/)



Use the Following:

    **sudo -i**

The command sudo -i is the equivalent to the 'su -' command.  This will properly change to the root user, switch to the root user’s home directory, use his (her?) environment values, etc.

    **sudo -s**

The command sudo -s is the equivalent to the 'su' command.  This will change to the root user but will not properly use his (her?) environment values, etc.

Please DO NOT use the following methods to gain root access:

    sudo bash, sudo sh, sudo su -, sudo su, sudo -i -u root

---

### Post by nvarona on 2009-06-04
> **sparky-steve said:**
> Hi,

It may be as simple as a locked-down root account. Try

```
sudo passwd -u root
```


Thanks... it works...

---

