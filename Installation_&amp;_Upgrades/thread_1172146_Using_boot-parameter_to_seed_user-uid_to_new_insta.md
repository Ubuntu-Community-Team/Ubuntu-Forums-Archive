---
title: "Using boot-parameter to seed user-uid to new installation?"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by i-o on 2009-05-28
I need to change the default (1000) user-uid for new ubuntu installtion. I'm trying to seed user-uid as boot parameter in following order;
1. I boot from Alternate-CD
2. I choose Install Ubuntu
3. I press F6 - Other options and Esc to get into command line where boot parameters are set.
4. I set a new boot parameter; "passwd/user-uid=12345678"
5. I finish the installation.
In finished installation the user-uid should be what was just seed as a boot parameter, but it's not. In /etc/passwd -file the last line shows the user created in installation and its user-uid. It is the default 1000 and not the one which I just seeded to it.

Now, is my syntax wrong or is my method wrong?

---

### Post by i-o on 2009-06-25
Anyone?
Coffee served from correct answers!

---

