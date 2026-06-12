---
title: "Lenovo 3000 v100 &amp; thinkfinger"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by david2b on 2007-03-12
Just bought a Lenovo 3000 v100 with fingerprint reader. I've installed feisty and most of hardware works (didn't test built-in webcam).
I wanted to log in with fingerprint reader, and installed thinkfinger :  [http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/)

and the result is 
"Initializing.....USB device not found"

...sounds like thinkfinger (made for thinkpad and SGS Thomson Microelectronics fingerprint reader) does not recognize my levovo hardware ... :( 

any ideas ?

---

### Post by IcemanV9 on 2007-03-12
Did you use "sudo" in your command??

---

### Post by david2b on 2007-03-12
of course, yes !
before I type "sudo tf-tool --add-user david", lsusb didn't show me fingerprint reader.

But, after running it, and having "USB device not found", lsusb shows : 
```

Bus 003 Device 005: ID 08ff:1600 AuthenTec, Inc. 

```
Is it the fingerprint reader ?

---

### Post by compmodder26 on 2007-03-12
That appears to be it.  Unfortunately, that means that thinkfinger won't work with it.

---

### Post by david2b on 2007-03-12
grrrrr!!!! why Lenovo didn't employ the same device in 3000 series and thinkpad ?

Don't you know if there is a driver for that ?
Anyway, thanks for all

---

### Post by compmodder26 on 2007-03-12
As far as I can tell there is pretty non-functional SANE backend for it.  That is all I've been able to find.

edit: actually, after a bit more research, it appears your model isn't even covered by that project. ([http://www.csz-online.de/projects/aesxxxx-linux/](http://www.csz-online.de/projects/aesxxxx-linux/))

---

### Post by IcemanV9 on 2007-03-12
Ok. It happened to me when I did not issue "sudo". :)

Too bad, thinkfinger doesn't work with yours. :(

However, for comparsion's sake ...

```
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
```

---

### Post by cmavr8 on 2007-07-14
Any news? I also have the Lenovo 3000 V100 and can't wait to use the fingerprint reader in ubuntu! (my windows partition is broken for a few months now, and I don't care about it anymore...)

---

### Post by david2b on 2007-08-20
i've tested today : nothing changes with thinkfinger 0.3 :-(

Ubuntu Feisty only - Shuttle SK83G + Lenovo 3000v100
Don't do windows since 2002....
-----------------------------------------------
[http://counter.li.org](http://counter.li.org)  - Registered Linux User #45312

---

### Post by moskrin on 2008-02-13
Sounds like you might need to modprobe uinput

---

### Post by Payteer on 2008-02-20
I am having the same problems with my Lenovo 3000 V100 also.  I haven't a clue what was said in the previous posts as I only have signed up to Ubuntu only about 2 months ago.  Most things work apart from the fingerprint reader and the built in webcam.  i am on Gutsy also.

---

### Post by intel on 2008-02-20
as far as ur webcam is concerned
see the output of command
#lsusb
if you see any text like "0c45"

then you need to join this group

https://groups.google.com/group/microdia

---

### Post by cmavr8 on 2008-02-20
No, our camera is a BisonCam Ali based one I think.

#lsusb:
Bus 001 Device 002: ID 0402:5602 ALi Corp.

---

### Post by cmavr8 on 2008-05-07
Anyone got fingerprint or webcam working?
Sound and suspend problems fixed!

---

### Post by Payteer on 2008-06-10
Any developments on these two problems from anyone?

---

### Post by cmavr8 on 2008-06-10
> **Payteer said:**
> Any developments on these two problems from anyone?

I managed to get the fingerprint reader to work, but it's no perfect..

After some time (being logged in) it doesn't ask for fingerprint, just password.

In terminal, here's the output:
```
USER@PC:~$ sudo top
aes1610:error [dev_init] could not claim interface 0
fp:error [fp_dev_open] device initialisation failed, driver=aes1610
[sudo] password for USER:
```

I'll upload the howto I wrote FOR MYSELF and a possible-non-working fix. I have no responsibility. It may work for you, too.

Thanks for understanding.
I'll be here for help/support and offcourse for seek of the optimum solution.

---

### Post by cmavr8 on 2008-06-10
(couldn't upload files while editing previous post..)
(Why is the file size limit 19.5K for ODT and 195K for DOC? I was forced to save in this lousy format)

---

