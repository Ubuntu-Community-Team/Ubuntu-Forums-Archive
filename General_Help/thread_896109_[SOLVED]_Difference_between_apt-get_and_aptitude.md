---
title: "[SOLVED] Difference between apt-get and aptitude?"
date: 2008-08-20
forum: General Help
---

### Post by Pidgin on 2008-08-20
It is known that both apt-get and aptitude can download and install packages. What's the difference between them?
Thanks!

---

### Post by cdtech on 2008-08-20
No difference now, read more:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by spiderbatdad on 2008-08-20
There seems to be a slight difference on my system. Aptitude prompts to auto-remove with y/n to proceed. Apt-get merely suggests to run apt-get auto-remove if I want to remove the unused packages.

---

### Post by mb_webguy on 2008-08-20
However, they *are* separate programs, and switching from one to another *may* give you problems, such as one not recognizing packages installed or removed by the other.  Since Synaptic is a front-end for apt-get, I recommend using apt-get rather than aptitude if you also use Synaptic.

---

### Post by pparks1 on 2008-08-20
> **Pidgin said:**
> It is known that both apt-get and aptitude can download and install packages. What's the difference between them?
Thanks!

For the most part, they are the same thing.   However, some prefer aptitude because of the way that it handles dependencies during uninstallation.   

So, for example, lets say that you want to install package xyz and you use aptitude.   Well, if xyz also added package 123 and package 456...with aptitude when you delete xyz...it will also remove 123 and 456...as long as they aren't needed by something else.

If you were to delete package xyz with apt-get, it would simply delete xyz and would leave 123 and 456 behind.

---

### Post by Unanimated on 2008-08-20
They are almost the same thing, just that Aptitude looks slightly different and asks different questions when it's installing programs.

---

### Post by mb_webguy on 2008-08-20
> **pparks1 said:**
> If you were to delete package xyz with apt-get, it would simply delete xyz and would leave 123 and 456 behind.

But you can remove 123 and 456 with the command "sudo apt-get autoremove"...

---

### Post by pparks1 on 2008-08-20
> **mb_webguy said:**
> But you can remove 123 and 456 with the command "sudo apt-get autoremove"...

Yes, you can.   That was functionality added into apt-get over time.   I've read quite a number of complaints of people having too many things uninstalled with sudo apt-get autoremove...so I'm a little leary.

Personally, I don't really care about the orphaned packages...so I just leave them there.  When I have to get rid of something, I just simply run sudo apt-get remove package

---

### Post by Square on 2008-08-21
One thing I coudn't figure out how to do with apt-get is the equivalent of ```
aptitude download packageName
``` which essentially downloads the .deb file for the relevant package.

---

