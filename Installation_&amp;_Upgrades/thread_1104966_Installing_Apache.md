---
title: "Installing Apache"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by VorlonShadow on 2009-03-24
I need to install what I believe is called LAMP (Linux, Apache, MySQL & PHP) to work on a web site that someone handed me.  I have Kubuntu installed (I prefer to work in a GUI), and MySQL 5.  However, when I try to "apt-get install apache" I get the message "Package apache has no installation candidate".  Reading around, I find that my sources list needs to be updated to allow this installation, but I don't know what to put in there.  I'm very new to Linux, and not very familiar with what goes in the list.  Can anyone help me out there?

When I go to install PHP, am I going to end up with a similar problem?

Thanks,
Jesse

---

### Post by Cheesemill on 2009-03-24
To install the Ubuntu LAMP stack from the repositories just do the following:

```
sudo apt-get update && sudo apt-get -y install lamp-server^
```

This will take care of everything for you.

Cheesemill

---

### Post by VorlonShadow on 2009-03-24
Excellent.  I think that did the trick.

Thanks for your help.

Jesse

---

