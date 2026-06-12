---
title: "Wired Network Guide Question"
date: 2006-03-03
forum: Hardware &amp; Laptops
---

### Post by sony102600 on 2006-03-03
Hey guys, I'm trying to get my internet up and running, not having much luck, have been working through the guide though, and have the following questions.

When I try the 

:/$ lspci | grep

command, I get put to a menu that says switch and has all this stuff, not the output predicted.... however, main question is... it says to look for drivers in this directory..

You'll find the drivers listed in the folling directory:

Code:

ls /lib/modules/$(uname -r)/kernel/drivers/net/

How do I get there?

---

### Post by hw-tph on 2006-03-03
The first command should be **lspci | grep** - the characters before that are just part of the command prompt. You should probably be grepping for something too - **lspci | grep -i -e ethernet -e network** should show all your network controllers.

In the second command there is a bashism. bash is the default shell in Ubuntu and it supports advanced programming. $(expression) means "insert the output of this command here", and the command **uname -r** outputs the kernel release, like 2.6.15-archck4.1 in my case.

---

