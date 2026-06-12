---
title: "wubi vrs partition"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by muffinman96 on 2009-09-29
Hi! i am new to the ubuntu, but i have been on it long enough to understand how it works. there is one thing i don't understand. and that is the risks of using a partition, and the benefits--as opposed to a wubi install. anyone want to explain?

thx in advance =P


<-- i can haz breens?

hl2 much?

nerd much?

---

### Post by tommcd on 2009-09-30
If you have been using Ubuntu for a while you should install Ubuntu to a dedicated partition. According to Wubi's developer, wubi is not intended for long term installations. It was only meant for users to try out Ubuntu:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.
There is also a performance penalty running Ubuntu from Windows from what I have read. Plus Ubuntu is vulnerable to fragmentation when installed inside Windows.
So go ahead and install Ubuntu the right way, to a partition. See these links:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
and create a separate home partition while you are at it:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
That site is an excellent resource for Ubuntu beginners.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And for a comprehensive dual boot (Windows + Ubuntu) site:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

And welcome to the Ubuntu forums!

---

### Post by raymondh on 2009-09-30
> **tommcd said:**
> If you have been using Ubuntu for a while you should install Ubuntu to a dedicated partition. According to Wubi's developer, wubi is not intended for long term installations. It was only meant for users to try out Ubuntu:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

There is also a performance penalty running Ubuntu from Windows from what I have read. Plus Ubuntu is vulnerable to fragmentation when installed inside Windows.
So go ahead and install Ubuntu the right way, to a partition. See these links:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
and create a separate home partition while you are at it:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
That site is an excellent resource for Ubuntu beginners.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And for a comprehensive dual boot (Windows + Ubuntu) site:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

And welcome to the Ubuntu forums!

+ 1 and welcome as well.

Main thing (in my mind) is that since WUBI is a file (or part) of windows, if windows isn't happy (defragged), clean (virus free), running strong (no malware, etc to slow it down) ..... then neither is your Ubuntu. Another scenario is that if windows' crashes, you also lose the ability to boot into Ubuntu.

Regarding partitioning .....

1.  Remember that you have the 4 primary (or 3 primary + 1 extended) limit.  Depending on how your HD is configured right now, it may be a limiting factor.
2. By partitioning, you take away space from windows ... which will then be allocated to Ubuntu.  Depending on your usage of windows, this may affect the "sizing".

All considered, I would prefer to either :

1.  Put Ubuntu in it's own partition
2.  Put Ubuntu in a persistent USB and then save files in a dedicated drive

Just my .02 preference ;)

---

### Post by presence1960 on 2009-09-30
> **tommcd said:**
> If you have been using Ubuntu for a while you should install Ubuntu to a dedicated partition. According to Wubi's developer, wubi is not intended for long term installations. It was only meant for users to try out Ubuntu:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

There is also a performance penalty running Ubuntu from Windows from what I have read. Plus Ubuntu is vulnerable to fragmentation when installed inside Windows.
So go ahead and install Ubuntu the right way, to a partition. See these links:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
and create a separate home partition while you are at it:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
That site is an excellent resource for Ubuntu beginners.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
And for a comprehensive dual boot (Windows + Ubuntu) site:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)

And welcome to the Ubuntu forums!

+1

I always say that about wubi. it is meant to be used as a test drive to see if you like Ubuntu. Then install Ubuntu to a dedicated partition if you like ubuntu.

---

### Post by muffinman96 on 2009-09-30
thanks for all your input, fast replies too! certainly just what i needed, thanks.

---

### Post by tkelito on 2009-10-01
Out of curiosity, as this just dawned on me.

I use Wubi on the current 9.04 install of Ubuntu on this machine.  I understand all the downfalls, etc.  Usually my installs are good for a month or so then it is a format and reload.

But, in this scenario.

My XP install is setup as such:

C:\ -> Windows (52GB)
D:\ -> Storage (Is 180GB but has no data on it)

My D:\ drive only has the Wubi container on it.  No other files.

If that is the case technically it minimizes the risk of the issues listed.  If I say remove a system file from the C:\ to make sure that Windows doesn't boot (as a test of course), can I still boot Ubuntu?  Anyone messed around with this type of scenario?

---

### Post by raymondh on 2009-10-01
> **tkelito said:**
> 

But, in this scenario.

My XP install is setup as such:

C:\ -> Windows (52GB)
D:\ -> Storage (Is 180GB but has no data on it)

My D:\ drive only has the Wubi container on it.  No other files.

If that is the case technically it minimizes the risk of the issues listed.  If I say remove a system file from the C:\ to make sure that Windows doesn't boot (as a test of course), can I still boot Ubuntu?  Anyone messed around with this type of scenario?



Thru WUBI, Ubuntu is now a "file" within windows OS ... that you know.  You have to keep the OS happy, clean and healthy (including ALL its' recognized drives'). 

With regard to boot, the windows bootloader will just point to D: drive whenever you want to access Ubuntu.  Now, if windows' OS crashes (which also includes your bootloader), you have no means to access any file (windows system nor Ubuntu).

Regards,

---

