---
title: "How to identify my motherboard's model?"
date: 2009-09-01
forum: Hardware
---

### Post by tbird6820 on 2009-09-01
my os is 9.04 and is up 2 date. I was reading a post by Sef Dec.8th 2007 and tried to identify my motherboard's model by openning the terminal typing: sudo dmidecode | more
than it asks for my password but I can't type it in nothing happens? I can hit enter but it just asks again for password?


dave@dave-desktop:~$  sudo dmidecode | more
[sudo] password for dave: 
Sorry, try again.
[sudo] password for dave:

---

### Post by wojox on 2009-09-01
Have a look at this site for fixing sudo:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Hope that helps.

---

### Post by philcamlin on 2009-09-01
ok aparently your sudo is messed up 
so follow ythe link above and it should most likely fix your issue

---

### Post by tbird6820 on 2009-09-04
At boot when I get to recovery mode I drop to root shell prompt,
root@dave-desktop:~#

I tried adding admin user and it said:
the user dave is already a member of admim. so I went to case 2 and tried the backup and it said:
cp: target /etc/sudoers is not in the directory.

---

### Post by tbird6820 on 2009-09-04
I retried it again and got it working so thanks.

---

### Post by tbird6820 on 2010-09-02
solved

---

