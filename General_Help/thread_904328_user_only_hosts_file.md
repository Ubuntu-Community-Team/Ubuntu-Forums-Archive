---
title: "user only hosts file"
date: 2008-08-29
forum: General Help
---

### Post by monkeyking on 2008-08-29
hi, I'm a non admin on a system,
can I make a user only hosts file instead of a systemwide

---

### Post by kidders on 2008-08-30
Hi there,

That's not something you should try. If you think about it, it doesn't make sense for different parts of the same application to have different DNS resolution rules, just because they're running as different users. There's scope for all kinds of weird behaviour.

What are you trying to achieve?

---

### Post by monkeyking on 2008-08-30
I have a small network, for which I am admin.
I can only connect to computers on this network (NET1),
through a ssh-server on a computer(NET2) on which I don't have admin rights.

The thing is,
there are no name resolution from NET1 on NET2.

I can only access machines if I know the ip adr.

As a solution, I have one of the machines on NET1 scp it's ip adress to a file on the computer on NET2.
I would be nice I could go directly to all the machines instead of going through the first one on NET1

---

### Post by kidders on 2008-08-30
Unfortunately, there's no way to manipulate NET2's name resolution without root privileges ... it'd be a *huge* security problem.

How many IP addresses would you need to remember? Perhaps you could configure shell aliases for them. For example ...```
alias test="ssh -t net2.ip.addr ssh net1.ip.addr"
```

---

