---
title: "Things I wanna know before upgrading to 9.04"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by deBALZAC on 2009-08-11
Hello there

I've been using Ubuntu 8.04 for 2 months and it works fine, but I'm worried about my security so I'm considering upgrading my sys to the latest version, 9.04. 

So I need to know:

1) Am I gonna experience lower performance? (any ex-windows user like me may think the **a-newer-OS-version-will-require-a-lot-more-resources-from-my-PC-so-it-would-got-slower-after-the-upgrade** factor, but I don't know if it applies for Linux-Ubuntu OS)

2) How big is the total of files I'll have to download? (so I can have an Idea of how many time it will take :) )

One more thing: this is an awesome community and it's great to know there are people out there who are up to destinate part of their time to give free support, you guys do a great job.

---

### Post by keith.newell on 2009-08-11
When I upgraded from 8.04 I experienced better performance and a bit of a speed increase.  As for your second question, I can't remember how large the download was to upgrade.  Hope this helps.  :)

---

### Post by Piscium on 2009-08-11
> **deBALZAC said:**
>  I've been using Ubuntu 8.04 for 2 months and it works fine, but I'm worried about my security so I'm considering upgrading my sys to the latest version, 9.04. 

So I need to know:

1) Am I gonna experience lower performance? (any ex-windows user like me may think the **a-newer-OS-version-will-require-a-lot-more-resources-from-my-PC-so-it-would-got-slower-after-the-upgrade** factor, but I don't know if it applies for Linux-Ubuntu OS) 

I would say, check your graphics card. If you have for example Nvidia or Radeon you are OK. There are however big problems with some Intel graphics. I know because I am one of the unlucky ones. 

So if you have Intel I would suggest to wait for 9.10. I have had many xorg freezes, Youtube and other video sites are very jerky, etc.

António

---

### Post by deBALZAC on 2009-08-12
Thx for the info ppl.

---

### Post by Magical Tiger on 2009-08-12
When I upgraded from 8.04 then to to 8.10 and then to 9.04, I experienced some minor glitches in the final 9.04. Recently I reinstalled Ubuntu 9.04 and everything was good. You may want to consider re-installation as an option instead of upgrading.

---

### Post by raymondh on 2009-08-12
See the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904").

Performance has been better for me (having used Hardy and Ibex...and still using them).

Check/try out the liveCd but note that it is not a true representation of speed (as you are running from the CD).  Try it out vis-a-vis your wifi, graphics, etc.

Good luck.

---

### Post by slakkie on 2009-08-12
Well, the upgrade itself is pretty easy. Be aware that you need to upgrade twice:

8.04 -> 8.10
8.10 -> 9.04

You cannot upgrade normally to 8.10, but you will read in the docs how (/etc/update-manager/release-upgrades is a hint).

As for security, 8.04 is fully supported by Canonical till 2012 or later. So you will receive all security updates for your applications. 

See [http://www.ubuntu.com/products/ubuntu/release-cycle](http://www.ubuntu.com/products/ubuntu/release-cycle)

If you can wait till april next year you can upgrade from 8.04 directly to 10.04 (which is something I'm going to do with my server).

As for desktops, you can make the switch. I've had problems with X (Intel card) when I upgraded to 8.10, but with my current hardware (also Intel) the upgrade from 8.04 to .10 went fine and I am now running 9.10 devel.

One thing that I would advise, [www.clonezilla.org](www.clonezilla.org), so you can restore if needed.

---

