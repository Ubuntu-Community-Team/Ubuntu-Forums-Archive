---
title: "Sentia 223 VERY slow boot..."
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by shaun.walkerIT on 2007-07-05
Hello all.  This is my first go round, (of many I'm sure) with this site.  I started using Ubuntu back a couple of months ago because I wanted to learn more about Linux (general statement I know).  Up until then, I had never used Linux at all.  It's been an interesting learning process that has involved a number of my buddies that are in on break from college.  I am still having one problem that I'm not sure what to do with.  I am currently running Fiesty on an Alienware Sentia 223.  It looks great once it gets booted.  However, it takes nearly 5 minutes to boot.  Someone had suggested that it might be the display drivers, but all drivers are correct and up to date.  As I understand it the i855GME chip set that this thing sports is a very common chip set.  I don't think the problem is there.  Is there anything else, any one knows about this system and why it seems to be incredibly slow in booting.  Once we get in, the system monitor doesn't show anything being over demanding.  It's a 2 GHz Pentium M with 1 GB of RAM.  

Any helpful thoughts would be greatly appreciated.
](*,)

---

### Post by reckless2k2 on 2007-07-05
the only reason i've ever seen for the EXTREMELY long boot up is with the networking feature. if you have it trying to connect wired and wireless that is when i see the extreme long startup. if you use it wireless all the time, disable the wired interface in /etc/network/interfaces.

if you connect to the same WAP all the time, map that in that same file under your wireless interface. you'll see your bootup quicken then. if you are using an open connect, then don't specify it. either way, it should speed you up.

---

### Post by shaun.walkerIT on 2007-07-05
Thanks for the quick reply....unfortunately that didn't do it for me.  When I power on the system it sits at "Starting Up...  Loading, please wait..." for nearly 1 minute.  The it goes to the Ubuntu splash where the orange indicator sits still for a number of minutes..."Reading files needed to boot..." I think that's where it's stalling.  once it gets past that, were about 30 seconds away from joy.  It's just that lovely delay thats driving me nuts.  I might should mention that the HDD shows very little activity during this time.  Could it be a problem with my HDD?

---

### Post by reckless2k2 on 2007-07-05
hhmmm...there is a post about disabling unnecessary startup functions like raid and such in this forum to speed up boot process. i'd query that real quick. it's odd that it's not the networking function because that's the only thing that usually "hangs" it that long on startup.

 also, make sure you are running the right kernel. it could be that as well. you might have to add kernel-i686 or k-7 or smp....depending on what you have going on.

---

### Post by MtnRoadBiker on 2007-11-03
I had a similar problem with my Sentia. I believe it had to do with the amount of memory (1GB). I added mem=900 to grub and it seems happier now.

---

### Post by bronson2005 on 2008-01-15
I am having the same problem.  I have a Sentia 223 with the 2.0 GHz processor and 2 GB of RAM.  It STILL takes 5 to 10 minutes.  The strange thing is, it runs much better from the Live CD.  Any ideas?  I would LOVE to get Ubuntu working on this laptop!  How did you change grub?

---

