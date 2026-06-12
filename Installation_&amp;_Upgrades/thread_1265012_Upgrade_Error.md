---
title: "Upgrade Error"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by kocis on 2009-09-12
I am trying to upgrade 9.0.4 on a Thinkpad T42 and get the following error.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

How do I proceeed?  Thanks

---

### Post by wojox on 2009-09-12
Open the terminal and run:

```
sudo dpkg --configure -a
```

---

### Post by Partyboi2 on 2009-09-12
Hi, open a terminal (Applications>Accessories>Terminal) and run the command that it mentions with
```
sudo dpkg --configure -a
```

---

### Post by kocis on 2009-09-12
Thanks.  Just tried that but when I am asked for my password I am unable to type it into terminal.

---

### Post by hansdown on 2009-09-12
Hi kocis.

Just type your password and hit enter.

You won't see the password as you type. It's for security.

---

### Post by wojox on 2009-09-12
Did you get another error ?  What is it saying ?

---

### Post by kocis on 2009-09-12
Thanks.   It worked.  It says I have a broken package though.

---

### Post by kocis on 2009-09-12
All set now.  Thanks.

---

### Post by hansdown on 2009-09-12
> **kocis said:**
> Thanks.   It worked.  It says I have a broken package though.

Click system> administration> synaptic package manager.

Enter password. 

In the left side, click broken packages.

It should give you an option to fix broken packages.

---

