---
title: "Hard drive problem with p5ld2."
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by kilovh on 2006-08-25
Hm, my new computer is giving me trouble. Basically, I can run the install up 'till the partitioner (With a few ctrl+c's) and then it doesn't work. Through trial and error, I know exactly why: It can't detect any hard drives.

You see, the ASUS P5LD2 MOtherboard has this weird system where *one* IDE controller on the motherboard works from boot. The other two work once inside an operating system, because they have certain drivers that need to be installed for them to work properly. The only problem is, all three of my hard drives are connected to those two IDE ports that don't work from boot (And thus don't work inside the install program). My question is basically, has anyone else had this problem before, and either way, how can I fix it?

Hope I explained it well.

-Kilovh

---

### Post by Dr. Dweebis on 2006-08-31
I am having exactly the same problem.  My system specs are:

Asus P5LD2
Pentium D 840 (Core Duo 3.2)
2GB Kingston DDR2 667 RAM
160GB UATA Seagate
Geforce 7600 GT KO

I also tried switching the hard drive to the primary IDE.  The hard drive was then detected by the bios, but had the same freeze. I also tried and using a different (Maxtor UATA 250GB).  No luck on any of these.

---

### Post by Dr. Dweebis on 2006-08-31
Hey Kilovh - so I got past that point.  Here's what I did.  FIRST - and perhaps most important - I disconnected my machine from the internet (just unplugged the ehternet port).  Then I plugged my CD (actually a DVD ROM) and a Ultra ATA Drive (Seagate 160GB, 7200.7) into the same ribbon which plugged into the primary IDE port on the motherboard (blue).  You'll need a ribbon connection with a long spacer b/w the hard drive and DVD.  Also, make sure to set the jumped on the hard drive to master and CD to slave.  Then I just used the Ubuntu disk and it loaded right up.

Once it was done and I restarted (which it asked me to do) and plugged it back into the internet, and now I'm writing to you.  I may need to download some drivers to make those other IDE connections work - would you like to hear about progress if I do?

Good luck.

DD

---

