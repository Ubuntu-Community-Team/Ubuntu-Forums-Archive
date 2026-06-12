---
title: "Fan running al the time Lenovo t420s (i7 SSD)"
date: 2011-12-04
forum: Hardware
---

### Post by lolnux on 2011-12-04
Just  installed the Ubuntu 11.10 64 bit on a t420s i7 SSD. I have use NVS  4200M graphics (set on discrete in BIOS - ubuntu works best with it on).  Also tried to just use integrated -> problem still exists. So it  must be with the CPU.

I have tried to install thinkfan with the configuration from this tread, but the problem is still there. [Then I found this: specific configuration for Intel Sandy Bridge CPU.]("http://www.jakubkotowski.com/2011/06/thinkpad-t420-thinkfan-settings.html")  I haven't tried it yet &#8211; anybody have experience with it? Or have a  thinkfan.conf file to share for a t420s i7 with SSD? (I have read that  you also have to set up temp parameters for the SSD?).

On a second note, I found out that [apparently there is a fan issue with a lot of Lenovos, no matter the OS]("http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T420s-Fan-noise-Issue/td-p/443569/page/2"). I am running BIOS v. 1.29 but there is a [update v. 1.30 out]("http://support.lenovo.com/en_US/research/hints-or-tips/detail.page?LegacyDocID=MIGR-77167"). Anybody have any experience with v. 1.30?

Do anybody know if other distros, like debian, are having the same issues?

---

### Post by fraktalek on 2011-12-16
Hi, coincidentally, the blog post is by me, so I do have experience with this kind of setting ;) do you have some specific question?

I upgraded the BIOS a few weeks/months ago and the problem went away for a while - resp. the fan was spinning at around 3500 RPM all the time which produces bearable noise.

However, after I installed newest updates yesterday, the fan started spinning at the highest speed again :-/ Seems like this time this behaviour is introduced by Ubuntu... So for now, I'm back to using ThinkFan with settings from my blog post. Although, after spending some weeks without ThinkFan and with the new BIOS, I think it would be better to let the fan run at higher speeds than my config does - e.g. at around 3500 RPM all the time so that it is closer to what Lenovo probably intends. 

I should add that I'm using two external LCDs which may cause the fan to run at higher speeds (check the lenovo forums).

---

### Post by Ph1b on 2011-12-16
I am having the same problem on Ubuntu but with Ideapad S205. Does The Ideafan also work for the Thinkpads?

---

### Post by fraktalek on 2011-12-16
@Ph1b I don't think ThinkFan works on IdeaPads, why not try it though - just be careful.

I'm using these settings now:

```
(0,	0,	35)
(1,	33,	38)
(2,	36,	45)
(3,	39,	49)
(4,	46,	58)
(5,	50,	62)
(7,	56,	32767)
```

So the fan spins around 3500 RPM most of the time.

---

### Post by lolnux on 2011-12-17
[LEFT]Tried installing mainline kernel (3.2 rc5) and there seemed to be a slight improvement. 
  
Your thinkfan settings seems to help with the fan issues though. It allows the much higher temp than the default, this could be work. Still haven't tried with the latest BIOS v. 1.30 for t420s. Will try to install the BIOS first and then do some testing. 

@fraktalek: Can see you updated your temp settings. Was it getting to hot? :-)
  
For others; also found this guide: [http://blog.ylatuya.es/?p=85](http://blog.ylatuya.es/?p=85)
[/LEFT]

---

### Post by fraktalek on 2011-12-18
I don't think it was getting too hot. I adapted the settings so that they more closely resemble what Lenovo probably intends - based on observation from the time when I didn't need thinkfan and ubuntu and BIOS took care of the fan on their own.

Btw, I filed a bug about this: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/905406](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/905406)

---

### Post by fraktalek on 2011-12-18
Also notice, that I have a T420 while this thread is about T420s which might get hotter sooner and thus might need higher fan speeds. On the other hand, I have an external monitor attached to the notebook most of the time - this may lead to a higher CPU load and fan speeds.

---

### Post by alexcriss on 2012-02-07
Hi there,

I am experiencing the "fan always on" behaviour that is reported in this thread. This is extremely frustrating, specially since the fan fires up even at very low temperatures. If you care, could you comment on the lenovo forum, adding a "me too" at:
[http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T420s-Fan-noise-Issue/m-p/673067/highlight/false#M56390](http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/T420s-Fan-noise-Issue/m-p/673067/highlight/false#M56390)

If you feel proud enough you could also help by signing an online petition to urge Lenovo's tech support to fix it at the BIOS level, that is where it belongs to! See it here:
[https://www.change.org/petitions/lenovos-tech-support-fix-the-fan-noise-issue-that-affects-t420s-thinkpads#](https://www.change.org/petitions/lenovos-tech-support-fix-the-fan-noise-issue-that-affects-t420s-thinkpads#)

Cheers!

---

