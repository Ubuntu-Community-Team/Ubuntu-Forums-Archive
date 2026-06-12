---
title: "Xorg needs a lot of my CPU"
date: 2008-11-02
forum: General Help
---

### Post by Nirva on 2008-11-02
Hay,

I recently bought a new laptop.  These are my specs :

Intel CORE 2 DUO P8400
3 Gig ram
Nvidia Geforce 9600GT 512mb

I'm running Ubuntu 8.10 with gnome.
This is quite a powerful laptop in my opinion, but there is one problem that is bothering me a lot.

The process Xorg uses way to much of my CPU time.
When I dont do anything ( don't even move the mouse ), it uses around 10%, but while using my computer, it sometimes peeks to 90% or more.

To give you an idea : While typing this post Xorg uses 30-80 % of my cpu.
This is quite annoying.  I use the most recent driver of nvidia : 177.80.
Also compiz is running.

Could someone please help me ?

I considered changing to KDE, but i heard that there were some problems between Kwin and Nvidia drivers, so this isn't a solution neither.

Thanks in advance

---

### Post by Azrael-ru on 2008-11-02
Same problem with KDE.
Nirva, please check your ~/.xsession_errors
On my machine xorg writing same string time by time:
> QObject: Do not delete object, 'unnamed', during its event handler!


do you have same? or it KDE only specific?

---

### Post by Nirva on 2008-11-02
Nope, I don't have the same error

---

