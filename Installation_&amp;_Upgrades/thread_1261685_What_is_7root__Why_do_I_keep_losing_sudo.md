---
title: "What is 7root?  Why do I keep losing sudo?"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by ultralame on 2009-09-09
I have a system that has been installed and upgraded a few times.

Currently, it appears that gid 0 belongs to 7root.  I am not sure what that is, and searching for "7root" doesn't turn up a lot of good info.

I upgraded to 9.04 today, and when the installation was done, I can no longer use sudo. I get this error message:

"/etc/sudoers is owned by gid 1010, should be 0"

I have dealt with this before, possibly when I upgraded to 8.10.

Since my system is headless, I have to bring a monitor/KB into the garage and change the permission on the file back to gid 0.

Can someone tell me:
-WTF is 7root, and why would someone replace root with it?
-Why does this keep happening?
-What can I do to prevent it?

Thank you

---

### Post by tommcd on 2009-09-09
To get sudo working for you again see this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)
I have no idea what 7root is. A quick google search did not turn up anything.

---

