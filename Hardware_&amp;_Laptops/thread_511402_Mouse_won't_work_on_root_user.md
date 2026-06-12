---
title: "Mouse won't work on root user"
date: 2007-07-27
forum: Hardware &amp; Laptops
---

### Post by colinireland on 2007-07-27
Hello,

I am running Feisty Fawn on a Dell Inspiron 6000. When I log in as the root user my mouse cursor wont move. It just stays in the centre of the screen. I do not have this problem when I log into my other account. If anybody could lend me a hand with this I would be very grateful.

Thanks,
Colin

---

### Post by kidders on 2007-07-29
Hi there,

The short answer is "Don't log in as root!". It is dangerous, and there should be no reason to *ever* do it. Having said that, your system logs or .xsession-errors files might contain some clues about the source of your problem ... but if I were you, I wouldn't be in any hurry to fix it.

---

### Post by FleetAdmiral74 on 2007-07-31
I second that. Log into a root user, and you could end up with problems a lot worse then your mouse not working :lolflag:

---

### Post by colinireland on 2007-08-08
Why is it dangerous to log in as root user, and what problems can arise?  The reason I wanted to log into that account is to use a programme called QTParted which will only run in the root account.

---

### Post by kidders on 2007-08-08
There's a wide variety of reasons not to do it. Most of them are security-related, but some involve odd behaviour of the type you describe, where things "mysteriously" misbehave when run later as an unprivileged user.

The most important thing to bear in mind is that almost no restrictions of any kind are imposed on the root account, so you (or something you run) can do untold damage to your system. You'd be fully exposed to any security holes or other bugs in any of the software on your box, so web browsing for instance, is particularly unsafe as root.

Unless you know what you're doing, you should really...[LIST]
[*]Leave the root account disabled, so logging into it (even from a text-based console) is impossible.
[*]Use sudo, gksudo, etc. to run applications as root ... but only if you really need to.
[*]Avoid running nautilus/konqueror/etc. as root.
[*]Consider console-based equivalents of graphical applications that need root privileges ... eg cfdisk & mkfs instead of qtparted.[/LIST]It may *seem* daft, but one of the reasons Linux & MacOS have such a good security reputation is that they are essentially designed to lock you out of 90% of your own box. To keep your Linux running safely & smoothly, you should only circumvent that layer of protection for short periods, and for individual applications.

---

### Post by colinireland on 2007-08-09
well u learn something new everyday.

thanks for the help lads

---

### Post by kidders on 2007-08-09
No worries. :-)

---

### Post by r0sa on 2007-10-08
can somebody give a direction how to set up mouse on root account to be working not freezing ? thanks

---

