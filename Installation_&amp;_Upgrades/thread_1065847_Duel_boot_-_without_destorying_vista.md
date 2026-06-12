---
title: "Duel boot - without destorying vista"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by GodsDead on 2009-02-10
Hey all, iv been shitting duel booting my Vista machine (my main machine) due to various problems that can go wrong (read online), mostly because vista puts all this extra crap at the end of its partition, so it wont let me shrink the volume from within vista like it should.

Now there are some pretty risky steps to try and shrink properly from within vista, but what i want to know is, how safe is it to partition my hdd from ubuntu live? and make sure that my vista still works.. 

Thanks.

---

### Post by Mark Phelps on 2009-02-10
Basically, it's NOT safe to mess with the Vista partition using Linux utilities.  Yeah, there have been LOTS of posts where it worked without problems.  And, if you have a Vista DVD, you will be able to boot using it, and run  Startup Repair when Gparted messes with your Vista partition and renders it unbootable.

But if you don't have a Vista DVD, you run the risk of Vista being unusable after resizing.

Note: For those doubters, grab the very latest GParted CD image, boot from it, and read the Windows notes -- and notice where it says that it does NOT work with Vista yet.  It recommends using NTFSRESIZE instead.

As to the shrinkage problem, this is well noted, and if you go to the following link, it has some workarounds on that:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Also, after you shrink the Vista volume, when you install Ubuntu, be careful to NOT use the "full disk" option.  Have seen lots of posts in this forum where folks have used that option and then been surprised when the Vista partition was erased in the process.

---

### Post by ranch hand on 2009-02-10
I used the full disk option and think it improved Vista a lot.

---

### Post by GodsDead on 2009-02-18
haha, thats the exact link i was trying to use, alas, vista has been playing up and i need to keep my system restore points.

I do own the vista DVD, so maybe that will be the lest time consuming? =]

---

### Post by lvleph on 2009-02-18
There are programs that allow one to defrag the HD and then write zeros to the end of the drive. This will allow you to shrink you windows partition in vista. Sorry, I cannot remember what the program is called.

---

### Post by chakoshi on 2009-02-18
I've the same condition, one big drive and vista installed, then instead of risking the vista(and tens of hours for installing all my progs) I just used wubi and installed ubuntu in vista, and everything is working perfect!

---

### Post by GodsDead on 2009-02-18
Ah right, although wubi dousnt install - boot properly does it? apparently you can get better performance if you duel boot like normal? 
or am i thinking of 8.04?

---

