---
title: "Best CD Burning Program?"
date: 2008-09-24
forum: General Help
---

### Post by matey3 on 2008-09-24
This is to both inform everyone about a good program I found to burn CDs with, And also To ASK everyone what software they use and recommend to use for copying CDs!

The one I am impressed with is called K3B and can be downloaded here:
[http://soft.softoogle.com/ap/k3b-get-2420.shtml](http://soft.softoogle.com/ap/k3b-get-2420.shtml)

But you know I am new to linux and whatever I did to install it did Not work!?(./configure ./install/ make make install etc etc..)??!!(The readme file said to do all of that)??!!

So I said what the hekk and tried 
 apt-get install k3b

(as root) and bingo the thing came up as GUI inside my terminal box and finished installing in my gnome session!?

I like k3b because it is simple and get-to-the point kind of program. After failing to copy on my XP machine I gave Ubuntu 8.04 a try and it too did not copy but (k3b) said the probable cause was " The Burner does not like your kind of CDs" (or something like that) heh..
I thought that was cool cuz I bought these blank CDs overseas and I think it may have something to do with the problems I had?!


Any way I have not tried the built-in program (Brasero) except only once. It looks OK but it too did not give me any detail error messages ...just spit out the CD..

Anyone know of another CD/DVD burning program that I should try?

Thank You For sharing the knowledge!

---

### Post by DrMega on 2008-09-24
I use GnomeBaker, which is in the repositories so no messing about with installation. It does everything I need. It is similar to Nero, but free and doesn't crash.

---

### Post by AndyCooll on 2008-09-24
K3B is in the repos no need to download it from a website, and it is frequently mentioned on these forums as an excellent choice for CD burning. Of course there's also Brasero (which is pre-loaded in Ubuntu) and Gnomebaker too. And quite a few others.

I'm quite happy burning straight from Nautilus these days, since I only occasionally burn CD's.

:cool:

---

### Post by Sef on 2008-09-24
> So I said what the hekk and tried 
 apt-get install k3b

(as root)Next time just be safer and paste or type this code in the Terminal (Applications > Accessories > Terminal)

```
sudo apt-get update && sudo apt-get install k3b
```Running as root is inherently unsafe.   It will make Ubuntu Linux like Windows: easily hacked.   Read [RootSudo]("https://help.ubuntu.com/community/RootSudo") for more information.

---

### Post by NoGroidWare on 2010-07-11
You can su root?  Login as root?   How?

---

### Post by Seeked on 2010-07-11
Ubuntu has root disabled by default.  

The first account that was created when you were setting up Ubuntu has "sudo" rights.

If you are using the software center whether you are that original user or not it will ask you for the sudo user's password to do the install.

If you are working on the command line you will need to su to that original user, if you are not already logged in as them. 

Once logged in you can put "sudo" in front of ANY command you want to have elevated root privileges.

This is supposed to be more secure than having root enabled.

---

### Post by Sim-I-Am :} on 2010-07-11
I really like brasero, but I needed something that could do dual-layer DVD's, so I looked around and found GnomeBaker. Great program. ;)

---

### Post by philinux on 2010-07-11
Necro thread, closed.

---

