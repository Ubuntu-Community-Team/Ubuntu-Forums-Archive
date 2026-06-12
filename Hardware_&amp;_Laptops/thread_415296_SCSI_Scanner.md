---
title: "SCSI Scanner"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by chasboz on 2007-04-20
This is what I did to get my scsi scanner, a Epsom gt-7000 working with 6.10 edgy.

[LIST=1]
[*]1 First I set my user to be a member of the Scanner group. This was done with the USERS control.
[*]2 Second I went to the terminal and through sudo nautilus command brought up a root user file manager which I used to go to /etc/sane.d to set the permissions of the the epsom.conf file to read and write for all users.
[*]3 Thirdly I went into /dev to set permissions on the sg0 file to read and write for all users.
This resulted in my user account being able to access Xsane and my scanner without having to go to root.

---

