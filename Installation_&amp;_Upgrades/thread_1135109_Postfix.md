---
title: "Postfix"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by PJDouglas on 2009-04-24
Hi,

I've just installed postfix and need to know how to rewrite the sender domain / address for all outbound mail.

Basically, I'am using postfix to rewrite the sender address before all mail is sent to a smarthost.

I'm new to ubuntu and would appreciate any help.

I've edited the main.cf file and configured the smarthost but not sure what the correct command is to use to rewrite the domain sender / return address.

Ive entered the command -  Rewrite "user" to "user@$myorigin in the main.cf and restart postfix and get an error saying that the '=' is missing.

Myorigin in main.cf reads - myorigin = pjdouglas.co.uk
This is the domain name I want all outbound mail to show as the sender address.

Is this the correct command for rewriting the domain name and is the syntax correct?

Would appreciate it if anyone could tell me ehat the correct syntax / command is for rewiting the sender address to pjdouglas.co.uk for all outbound mail.

Many Thanks


Paul.

---

