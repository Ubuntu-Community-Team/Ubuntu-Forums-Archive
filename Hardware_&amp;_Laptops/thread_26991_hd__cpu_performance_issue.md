---
title: "hd / cpu performance issue"
date: 2005-04-14
forum: Hardware &amp; Laptops
---

### Post by Tomppa on 2005-04-14
Hi!

  My problem is slow hard drive transfer rate with strange cpu time consumption. When I copy file, from hd to same hd, processor usage gets up to 100%. Looks like task named  gam_server uses most of cpu time.
Transfer rate is also lower than it should be, I think.  Udma is on, and I have added line amd74xx in /etc/modules like thread [http://www.ubuntuforums.org/showthread.php?t=11892](http://www.ubuntuforums.org/showthread.php?t=11892) suggest.
 I have Asus A7N8X-X motherboard.

---

### Post by az on 2005-04-14
If you copy it through a console, do you get the same results? I find that the GUI progress bar thingies take up a lot of cpu.  It is the same when downloading from firefox and using wget...

---

### Post by Tomppa on 2005-04-14
Using Gnome-terminal won't help. Problem remains. So that is not the answer  :(

---

### Post by dolson on 2005-04-16
This is happening to me as well... CPU is permanently at 100%. This is not cool.

---

### Post by Reb on 2005-04-18
gam_server watches directories for file modifications... so if you're downloading a lot of stuff, it'll use more cpu. I don't think it should ever be 100% though. Google for gam_server and you'll see a lot of people have problems with it.

---

