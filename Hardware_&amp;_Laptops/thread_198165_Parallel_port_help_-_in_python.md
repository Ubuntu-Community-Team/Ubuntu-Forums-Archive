---
title: "Parallel port help - in python"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by uniphil on 2006-06-16
I am just learning python, and would like to control the parallel port. I used to control the parallel port all the time in MS QBasic, which was super-easy.

Anyway I found something called pyparallel, installed it, and tried it out, it suggested testing with:

>>>import parallel
>>>p = parallel.Parallel()     #opens lpt1
>>>p.setData(0x55)

so I tried that, import parallel worked, but p = parallel.Parallel() shouted this at me:

  File "usr/lib/python2.4/sitepackages/parallel/parallelppdev.py", line 174 in __init__
      self._fd = os.open(self.device, os.0_RDWR)
OSError: [errno 2] No such file or directory: '/dev/parport0'

so I am wondering how I should go about getting the file or directory /dev/parport0

Any help would be greatly appreciated!

ps. so far all my computer-controlled projects have been controlled by the parallel port. Any suggestions for replacements for this aging piece of equipment? Anything easy and cheap.

pps. Has anyone noticed that google seems to be slower than usual lately? where my searches used to take around .08 s., they are now taking around .4 s !?

---

### Post by uniphil on 2006-06-20
Can anyone help, please?

I really need this thing to work. Is it just a matter of installing something which will allow me to access /dev/parport0? or what?



If there is no possible way to get this to work, is there any other simple, cheap way of interfacing with the computer? preferably usable with python?

---

### Post by antario91 on 2008-07-11
So I see, noone replied for a long time.
I had this problem too, but a few days ago I found the solution (proud :D).
Before you use python, you have to:
```
sudo rmmod lp
sudo modprobe ppdev
```
And finally you have to execute your python program as root (you can try with the interpreter as well, but also as root).
 Cheers, Antario

---

