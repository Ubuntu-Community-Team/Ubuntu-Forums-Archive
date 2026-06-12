---
title: "Suspend --&gt; USB Mouse out"
date: 2005-12-17
forum: Hardware &amp; Laptops
---

### Post by xyz on 2005-12-17
Hello-
I suspend my Toshiba Satellite A40 and then press any key to get back to my desktop.No problem.
Then my Dell no longer works and I have to use touchpad which is sluggish.It used to work and, for some odd reason, stopped today.
Anybody has a clue as to what can be done to get my mouse back?
Thank you for your help.

---

### Post by xyz on 2005-12-18
Hi-
I might just add (and that doesn't help me understand what's going on!)  that when I reboot normally,my mouse is just fine and wiggling away!
Anybody has a clue?Thank you.

---

### Post by xyz on 2005-12-19
**amohanty** on another thread "USB Mouse not working" suggests to try this to configure it:
```
sudo dpkg-reconfigure xserver-xorg

```
Would that help my Dell mouse to work again upon resuming from suspend?It works fine but I have to reboot!
I'm a newbie and I would appreciate any advice on this command line.As I learn,I do so many things that get me into trouble.I'd like to avoid that just this once.
Thanks.

**guyforget**said on yet another related thread :"This frustrated me too. I just moved the mountall script back in the order when booting. "
```
cd /etc/rcS.d/
sudo mv S35mountall.sh S60mountall.sh
```

Any feedback?

---

### Post by xyz on 2005-12-26
Hi-
Here is the reply from [email]ben.collins@ubuntu.com[/email] :
[http://bugzilla.ubuntu.com/show_bug.cgi?id=21438](http://bugzilla.ubuntu.com/show_bug.cgi?id=21438) 

One of you guys/gals might help a newbie to understand what he means AND what to do exactly to help figure out what's wrong  and how to implement it on my Toshiba Satellite A40.:confused: 
Thanks a lot.

---

