---
title: "keyboard goes crazy"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by ljubomir on 2006-08-27
Hi!

I own an old T22 ThinkPad laptop. It worked nicely under breezy, but after a fresh dapper install I've noticed very strange keyboard behaviour. In some situations I'm unable to type some characters! For example, when I run apt in one terminal, I'm totally unable to type "l", "m" and some other characters in other applications, and "*" show when I type "p" . This is totally reproducable, and messes up keyboard both in X, and in plain console, occurs for all users, every time. When apt finishes, and I close the terminal, keyboard goes back to normal. Situations which affect my keyboard are: apt, adept, synaptic,copying files with kio_file or cp, and others. Only way to restore normal behaviour is to close those applications (or to wait for them to finish). I have no idea where to start debugging this very irritaning problem since I've never encoutered this behaviour on any machine before :|.

---

### Post by unclepedro on 2007-11-30
Sounds like your numlock is on. I've had this happen because I used a keyboard and then disconnected it, although that doesn't seem to be happening here. Not sure what the problem is but it's almost certainly numlock related (since p is the * key for the thinkpad 10-key emulation).

---

