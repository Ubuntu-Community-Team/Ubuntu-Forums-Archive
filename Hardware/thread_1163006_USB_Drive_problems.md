---
title: "USB Drive problems"
date: 2009-05-18
forum: Hardware
---

### Post by Bentrider on 2009-05-18
I've just installed Ubuntu and I'm slowly getting to grips with it.  I have a problem with my USB memory stick and an external hard drive (USB connection).  If I plug in either of them the whole system just freezes and I have to shut down and re-boot to unfreeze it.  If I plug either drive when the computer is off and then boot up then the drive is recognized and works fine but if it's unmounted and unplugged then it's back to square one.  Any advice

---

### Post by spacesamurai on 2009-05-18
Could you please give us some more information about your system so that we can help diagnosis? 

For one, since this is a hardware problem, what is your output with dmesg? 

```
$ dmesg
```

If you check your logs and see anything else, please show that as well.

---

### Post by Bentrider on 2009-05-18
Well, typing in 'dmesg' produces several pages of info, anything in particular you need?

I am a complete newbie to linux/ubuntu so I wouldn't know about any logs.  The computer is 7-8 years old and has a typical system from that time but I'm afraid I can't remember much about processor, memory and so on.

---

### Post by spacesamurai on 2009-05-18
As for the dmesg info, you can just copy it all and place it in a quote wrap like so. 

> INFO
MORE INFO
MORE MORE INFO

As for the log files, check the files within /var/log/ and see if you find anything odd.

Also, if you give some hardware specs about your machine and Ubuntu version, that would help as well.

---

