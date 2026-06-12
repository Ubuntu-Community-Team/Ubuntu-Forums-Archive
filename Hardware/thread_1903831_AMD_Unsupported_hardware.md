---
title: "AMD Unsupported hardware"
date: 2012-01-03
forum: Hardware
---

### Post by maniat1k on 2012-01-03
Hi, I was trying to get spore on wine, but when I get it working...
[IMG]http://oi44.tinypic.com/15do35z.jpg

 a tranparent pop-up saying "AMD Unsupported hardware".
on the other hand when I try to hibernate. I won't come back. the pop up appear at the first. but nothing else.

Any idea?

**I try to take a snapshot of the pop up, but I doesnt appear**

my video info:
AMD Radeon HD 6320.

---

### Post by Mark Phelps on 2012-01-03
If you're not using the restricted drivers, then you should try installing them.

Also, that game has a Bronze rating at the WineHQ site -- the lowest rating a game can have that works at all!  See the link below for details:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=8185]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=8185")

---

### Post by 2F4U on 2012-01-03
What graphics drivers are you using, open source or proprietary?

---

### Post by maniat1k on 2012-01-03
I'm using this two:

fglrx
fglrx-amdcccle

They where on the repos. I think those are privatives.

---

### Post by maniat1k on 2012-01-03
Anyone can tell where can I find the solution?...
Or maybe I have to go back and install what to get all working like it used to be... Spore is a fun game to play, but maybe it's best to have it running on Virtualbox.

---

### Post by MoreOrLess on 2012-01-03
What version are you using?
```
fglrxinfo
```

---

### Post by collisionystm on 2012-01-03
I have a radeon hd 6380

The only thing I installed was fglrx-updates

sudo apt-get install fglrx-updates

everything was included.

I then tweaked the openGL plugin in compiz and enabled tear free. works great.

---

### Post by maniat1k on 2012-01-04
> **collisionystm said:**
> I have a radeon hd 6380

The only thing I installed was fglrx-updates

sudo apt-get install fglrx-updates

everything was included.

I then tweaked the openGL plugin in compiz and enabled tear free. works great.

that fixed my "unsupported hardware" issue... :D

> **MoreOrLess said:**
> What version are you using?
```
fglrxinfo
```

After @collisionystm solution it says:

```
~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6320 Graphics
OpenGL version string: 4.1.11251 Compatibility Profile Conte
```

but still when I try to get out of hibertation the notebook don't do anything... I didn't found a warning or something on /var/log/syslog ....

---

### Post by collisionystm on 2012-01-04
> **maniat1k said:**
> that fixed my "unsupported hardware" issue... :D



After @collisionystm solution it says:

```
~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6320 Graphics
OpenGL version string: 4.1.11251 Compatibility Profile Conte
```

but still when I try to get out of hibertation the notebook don't do anything... I didn't found a warning or something on /var/log/syslog ....

hibernation or sleep?

Just closing the lid, by default, puts the computer to sleep and I have had no issues.

I never use hibernation. I dont trust it.

---

### Post by maniat1k on 2012-01-04
I mean hibernation... I use hibernation to shut down the computer and use it later on, or the next day. with sleep If I round out of battery power my info on RAM it will be lost.

---

### Post by collisionystm on 2012-01-04
> **maniat1k said:**
> I mean hibernation... 
but a (this is maybe a dumb question)

I use hybernation to shut down the computer and use it later on or the next day.
With sleep I could do the same thing?


Yeah. you just close the lid and it goes to sleep.

Hibernation takes whatever is in the memory, writes it to the hard drive as a file and then powers off the computer completely.
problem is, I have seen the hibernation memory dump become corrupt easily.
Sleep just suspends everything as is and puts the computer into a lower power mode. Thats all I ever use...works for me

---

### Post by Mark Phelps on 2012-01-05
+1 for using "sleep".  Experimented with hibernation -- got unreliable results.  Now use sleep -- works fine every time.

---

### Post by maniat1k on 2012-01-05
ok set this threat as solved then.. thanks

---

