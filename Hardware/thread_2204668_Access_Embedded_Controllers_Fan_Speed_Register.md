---
title: "Access Embedded Controllers Fan Speed Register"
date: 2014-02-09
forum: Hardware
---

### Post by knicklicht on 2014-02-09
Hello, I am using a Lenovo Yoga 13, which works great with Ubuntu. Everything worked out of the box except for the WiFi. Anyways, the fans seem to be spinning at 100% all the time, even in the (pre installed) Windows, and there is no way to control them through software. Now I found a program called NotebookFanControl (Windows only) that reads the Embedded Controllers fan registers directly and then sets the speed accordingly. This works great in Windows, but how would I write to that register under Linux? There is a program called ReadWriteEverything (Windows only) in which you can directly read the EC registers and manipulate them. Is there an equivalent for Linux?

Cheers

---

### Post by rayfenwindspear on 2014-10-09
After tinkering with this and searching on my own, I found a perl script that does exactly this. I modified it to make it more usable for my own purposes of manually editing my fan speed curve, but it is very easy to use for a single register. Even better, if you have a RW Everything script file, you can use it with one command. See my GitHub repository and be sure to read the readme. If you have any questions or problems, just ask.

[http://github.com/RayfenWindspear/perl-acpi-fanspeed](http://github.com/RayfenWindspear/perl-acpi-fanspeed)

---

