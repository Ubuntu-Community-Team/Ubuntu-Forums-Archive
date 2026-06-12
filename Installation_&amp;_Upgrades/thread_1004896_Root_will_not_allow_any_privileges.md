---
title: "Root will not allow any privileges"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by cynd007 on 2008-12-07
Hello,

I just switched from Vista to Ubuntu 8.10 on my HP dv9000, and the version installed with a root user. I'm not very familiar with this, and can not lock out the account to change privileges for myself. From what I understand Root was replaced by Sudo in Ubuntu, but when I run the command:  $sudo passwd -l root it says that permission is denied. I would appreciate any information on how to customize my privileges, and/or use root if I have too. Thank you for any information.

---

### Post by aysiu on 2008-12-07
Perhaps you accidentally removed yourself from the sudoers group?

This may help:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

There really isn't a reason to run ```
sudo password -l root
``` though. The root account login is enabled by default.

---

### Post by snova on 2008-12-07
I don't understand. That command ('passwd -l') locks an account, but the root account is already locked.

Basically, when you need to run a command with root privileges, you just prefix the command with sudo (don't quote), or gksudo for graphical progams.

To my knowledge, the first created account has permissions to run anything with sudo.

But I'm not entirely sure what your question is...

Edit: I guess aysiu knew what it was, that's probably what you needed.

---

### Post by GnomeMax on 2008-12-07
Ummm...

I don't think the root account was ever locked out - at least it's never been that way for me.  You just can't get a GUI for root but it's still there (and better have a secure password!)

The sudo command didn't replace the root account, it just lets your account run a command as SuperUser.

Are you sure you are actually operating in an account that has sudo rights?  As in, did you create a regular user account and are using that one instead of an administration-level account?

You don't need to 'lock out' the root account so you can change your own permissions.  You need to have an account that has the rights to change permissions to do that - an administrator account - of which root is the ultimate.

---

