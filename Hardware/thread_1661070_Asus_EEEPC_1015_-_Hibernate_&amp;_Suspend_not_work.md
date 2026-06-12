---
title: "Asus EEEPC 1015 - Hibernate &amp; Suspend not working"
date: 2011-01-06
forum: Hardware
---

### Post by Lupercalia on 2011-01-06
Hi,

I just installed Ubuntu 10.10 on my netbook, running 2.6.35-24-generic currently.

However, when I try to hibernate or suspend, the netbook does one of the following:

1) freezes completely and will not respond to button presses
2) goes to a black screen and will not respond to button presses
3) goes to a black screen with a single white underscore at the top left of the screen and will not respond to button presses.

With all of these, the processor activity light stops blinking after a while and the hard drive spins down, but the netbook stays on.

Additionally, the "shut down" sometimes doesn't work properly either, freezing at the "ubuntu" page. After using "sudo shutdown -h now", "shut down" seems to be working a bit better.

Any help would be much appreciated!

---

### Post by realloc on 2011-02-01
I have the exact same problem.  I filed a bug report on this issue:

[https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/711501](https://bugs.launchpad.net/ubuntu/+source/kernel-package/+bug/711501)

Please add your comments to the bug report, and click the "This bug affects me" button to let the developers know this is important.

---

### Post by Carson5696 on 2011-02-01
first type your user name second type your password press enter
I do not know if this works but at least try it

---

### Post by mrs. respect on 2011-02-19
I am experiencing the same problem with my asus eee pc 1015PEM. Typing my username and password as suggested above does nothing.

---

### Post by shad974 on 2011-03-17
I've experienced the same problem with my eeepc 1015 PE. It seems the problem was due (for me) to the wifi module rt2800pci I added the line "blacklist rt2800pci" in my file /etc/modprobe.d/blacklist.conf and the module rt2860sta was load instead of the rt2800, with this module I have no more problems.


(Excuse me for my english)

---

### Post by iris-n on 2011-06-14
I have an eeepc 1015pem running 10.10, and the post by shad974 solved the shutdown problem for me.

---

### Post by untwisted on 2011-07-06
I have an eeepc 1015pem running 11.04, and the post by shad974 solved the shutdown and sleep/hibernate problem for me.

---

### Post by eakinc on 2011-07-06
shad974's suggestion solved this shutdown issue on Eeepc 1015pe running 11.04. Added "blacklist rt2800pci" to /etc/modprobe.d/blacklist.conf
 In root terminal;
#echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
SOLVED: Shutdown works, suspend works.

---

