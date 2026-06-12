---
title: "Default username and password"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Kateos on 2009-10-30
When trying to log onto Ubuntu 9.04 I am asked for a username and password, which I was never asked for during installation.

I have followed the advice below, but when I have run the adduser command, I get the message 'only one or two names allowed.'

How can I change my username/password and log on?

[I]boot to the grub screen, watch closely, you will have to press escape
[/I]>[I] key to get there.  choose recovery kernel.  in the menu, choose drop to
[/I]>[I] root shell.  use the command adduser followed by the username you want
[/I]>[I] to add.  then the command passwd followed by the username you just
[/I]>* created to create the password.  reboot, and login.*

---

