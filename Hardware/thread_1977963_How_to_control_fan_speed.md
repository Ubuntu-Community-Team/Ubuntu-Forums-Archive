---
title: "How to control fan speed"
date: 2012-05-11
forum: Hardware
---

### Post by vibrunazo on 2012-05-11
My Dell Inspiron 14R 910 laptop started overheating after upgrading from 11.10 to 12.04. I noticed fan speed is usually slow, so I'm guessing that's the culprit, so I'm trying to control fan speed via software.

I tried to use fancontrol, but I get this error:

~$ fancontrol
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file

I googled for help and found that I should use pwmconfig, but that gives me this error:

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

Googling for help I found that meant I had no sensors working. But running "watch sensors" from lm-sensors works fine and can accurately tell my cpu temperature. And running "sensors-detect" will find sensors fine.

Now I'm stuck, what can I do to control my cpu fan speeds?

---

### Post by sdrubish on 2012-05-18
I have EXACTLY the same problem.
My fans run at lower RPMs on 12.04 and my laptop overheats

Does somebody have any ideas?

---

### Post by Redblade20XX on 2012-05-19
Try looking into the bios for fan control options. Usually the os has a limited ability to control fan systems for operational reasons. But there maybe some limited control abilities, need to do some research on it. :)

- Red

---

