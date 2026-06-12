---
title: "su Authentication failed...help"
date: 2012-11-17
forum: Hardware
---

### Post by FepzHz on 2012-11-17
I am new to linux/ubuntu...

I am trying to use a command to obtain information on internal devices on the PCI bus.
/sbin/lspci

before I enter that command in the terminal, I enter the { su } command. I get a return asking to enter a password, yet I can't actually see it in the terminal but I type it anyways. I am assuming its the same password i use to login, since i can't remember setting any other passwords. But i get a return saying{ su: Authentication failure}, so i am assuming thats not the password. From what i understand su is a command to switch to the root (admin) user, there aren't any other users on this pc though. This is all very confusing and im not sure how to handle this situation. I would greatly appreciate any help i can get, as i am trying to give my self a crash course on using Linux.

---

### Post by sisco311 on 2012-11-17
In Ubuntu you have to use sudo:
```
sudo lspci
```

See: [uhelp]community/RootSudo[/uhelp]

---

### Post by FepzHz on 2012-11-17
Thanks, i didn't realized the article i was reading was on centOS 5 not ubuntu.  :frown:

---

