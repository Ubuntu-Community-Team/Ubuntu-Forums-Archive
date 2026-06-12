---
title: "HP pavillion X2 10&quot; tablet battery not charging (USB C)"
date: 2018-07-15
forum: Hardware
---

### Post by holmlars on 2018-07-15
Hi everyone!

First of all; some technical specs of the system:

- computer: HP 10 n000nd (pavilion X2 10")
- OS: Ubuntu MATE 18.04 (LTS)
- Kernel: 4.17.5

So the problem is as follows: when the computer is booted, it does not charge via the USB-C port. This computer has only USB-C charging. This has always been done with the original charger. When the PC is shut down, it charges normally.

I've done a lot of reading online and nothing helped or pointed in the right direction (AFAIK). I've checked in the power monitor thingy in the MATE settings that it detects the AC charger, and it does. But when I look at the battery consumption when plugged in and when not, it only drops one watt when the charger is plugged in, while it's a 15-watt charger. So something's off... Also, when I pull up the USB log in the terminal, it does not detect a change when plugging in and out. This, while Ubuntu does detect the AC charger in its settings.

All in all, I'm out of options, as I need this pc to be able to charge when I'm working on it... 

I really do hope one of you knows the answer to this strange problem!

Thanks in advance,

Lars

P.S. It has the same problem in all other Linux distro's I've tried (I.E. Elementary OS)

---

### Post by Mark Phelps on 2018-07-16
You can try the Ubuntu-Mate forums, but I don't hold out much hope:  [https://ubuntu-mate.community/](https://ubuntu-mate.community/)

What I gather from HP is that they only support Linux on the commercial side, and then, only for RedHat.

So, Ubuntu versions get no real support from them.

My guess is that the USB-C plug has a chip in it, and that chip only allows charging when some special driver is running -- and that special driver is preloaded on the HP OEM version of Windows.

That said... someone may come along to contradict that and provide you a link to the driver you need.

---

### Post by holmlars on 2018-07-16
Thank you for your reply!

I have been searching for a generic USB C driver for a while already, with no luck.

Indeed, hopefully someone experienced a similar issue before and knows a fix!

---

### Post by netomx on 2019-06-05
Did you found the fix?

---

