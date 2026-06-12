---
title: "permissions?"
date: 2008-09-18
forum: General Help
---

### Post by youdidntseenothing on 2008-09-18
hey everyone,
I have ubuntu 8.04 and would like to know how to disable all those things that ask me for my password i.e. when i goto change some settings its asks me and so on. I know its for the safety but I'm the only one who uses the computer. Thanks for the help

---

### Post by Pro-reason on 2008-09-18
No, that's a fundamental aspect of computer security.

If we made it easy to disable that sort of thing, all newbies would disable it, and Linux would turn into Windows.  No thanks.

---

### Post by vamped on 2008-09-18
This should help: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It points out the pros and _cons_ of what you're wanting to do, yet does explain how to enable the root account for the terminal.

The root account will still be disabled in X by a setting in gdm.conf: AllowRoot=false. Changing this is highly discouraged.

---

### Post by Pro-reason on 2008-09-18
> **vamped said:**
> This should help...

You've pretty much told him how to log on as root.

It's not just insecure.  I know several programs that will actually refuse to run as root, so it's a really, really bad idea not to have a standard user account.

---

### Post by lswb on 2008-09-18
Even if you're the only user the password can prevent damage to the system, for instance if you were logged in as root it would be just too easy to delete or overwrite system files by accident with for instance a simple typing error. On the other hand, if you just want to relax access to a few specific commands that you use frequently, take a look at 
man sudoers

---

### Post by youdidntseenothing on 2008-09-18
yeah you all are right. Linux for life aye

---

