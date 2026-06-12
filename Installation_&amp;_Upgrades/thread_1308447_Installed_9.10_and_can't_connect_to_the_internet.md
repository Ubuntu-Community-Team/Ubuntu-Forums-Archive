---
title: "Installed 9.10 and can't connect to the internet"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by terry@softreq.com on 2009-10-31
I just installed 9.10 (update manager suggested it) and now I can't connect to the internet. 

I added a connection for DSL, used the normal username and password and no connection.

I sorta wish I hadn't downloaded it - is this version whacked? :(

---

### Post by skyiscrying on 2009-10-31
Try pppoeconf in terminal as root

---

### Post by terry@softreq.com on 2009-10-31
Yes, I did that. 

However, when I restart my computer, it seems I have to run pppoeconf again to connect.

So instead I went for a wireless connection and am working with that.

It seems 9.10 has some sort of a wired connection bug.  That will be really disappointing for those who upgraded from a stable system.

---

### Post by MerlinsLair on 2009-10-31
I agree with you Terry. Am going to stick with 9.04 until these bugs get worked out. Then I'll think about upgrading.

---

### Post by joplass on 2009-10-31
apt-get update or apt-get dist-upgrade will help.  I just updated about 23 packages that fixed a lot of my problems.

---

### Post by terry@softreq.com on 2009-10-31
I tried update manager but apparently my system is up to date.

I'm noticing that the system is crashing for every 30 minutes or so of use. 

Not sure why they offered this upgrade under the general update - its buggy and not ready for general distribution in my opinion.

---

### Post by 8472 on 2009-11-01
Hello,
I would like to know few things, because maybe I may have similar problem.

Anyway, I'm not using DSL as you do, but I have an fiber connection from my ISP ended to one router/firewall device, and in there I connect any client computer I want.
After my upgrade up to KK, after each start/restart of my KarmicKoala I have some network difficultys, that I simply can't ping e.g. [www.google.com](www.google.com) or else. What I've found is that it's some problem with DNS name resolving, because when I ping some external IP address of mine ISP, I can ping it, but I can't make it through the DNS names. That DNS resolving simply doesn't work. What else I've found is, that I must restart the network using '/etc/init.d/networking restart' to make it work. Anyway, after another restart I must make it again and again. What I've found in that networking script is, that the restart function executes only the 'ifdown -a' and after it the 'ifup -a' commands. After these steps my connection works fine again, even with using the DNS.

And I want to ask you, if you haven't noticed something similar?
thx

---

### Post by MerlinsLair on 2009-11-01
> **terry@softreq.com said:**
> 

Not sure why they offered this upgrade under the general update - its buggy and not ready for general distribution in my opinion.

I agree %100 with that statement. This version/release has way too many bugs to have been released to the public as a stable production product. I realize that not every computer out there will be issue free but for the most part the vast majority should be.

My HP dv1000 laptop ran 9.04 effortlessly with no issues what so ever pretty much since it was installed sometime during the first of the year. I wiped my drive after making a backup and installed 9.10. After the first boot into the new release, no internet connectivity at all at first. Then only slow connectivity no matter what. Made no difference if it were wired or wireless. All my other machines whether they were running Windows or Linux were running just fine.

That experience in itself would be a deal-killer for most who have decided to try Ubuntu for the first time.

Now, before anyone starts with the usual banter about how a user should have done this or done that, think before doing so. The majority of new users are used to Windows and as such expect the product to work right out of the box. They want it to work when they power up their machines without having to start figuring out what the heck is going on. Until the Ubuntu devs can get it to that point, Linux in general doesn't stand a chance in hell of getting wide-spread public acceptance like Windows enjoys at this point.

Personally, I like Ubuntu and Linux in general. But, I am a hobbiest when it comes to it. I don't depend on Linux yet to 'be there' for me when I'll need it most as it's still too buggy for general use. This latest release justifies my saying this. In all fairness, I don't trust Windows that much either but it at least has been there the majority of the time for me.

Now if you feel the need to flame me for my personal opinion, fine. So be it. But until Ubuntu or Linux in general can get the end product in a fashion that a new user can either install it and run it without issues or use it without constantly going searching for help, then it will remain out of the reach for the general public consumption.

BTW, I removed 9.10 and reinstalled 9.04 to this very same laptop. Works as it did before I installed 9.10. No slow connectivity, no wired or wireless issues. I posted this from it.

---

### Post by Batzi on 2009-11-01
> **joplass said:**
> apt-get update or apt-get dist-upgrade will help.  I just updated about 23 packages that fixed a lot of my problems.

how is that going to work when there is no connection at all? I have upgraded to 9.10 and I still can't connect to the internet whether it was wired or wireless. The router is found but there is no connection at all.

---

