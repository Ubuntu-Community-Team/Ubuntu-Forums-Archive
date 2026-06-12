---
title: "Ubuntu no longer booting -- is there something wrong with my hard drive?"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by Niomi on 2007-07-03
My installation of Ubuntu on my laptop is turning up errors very similar to the ones described [on this launchpad page](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104878).

Here are some photos:

First, it starts with a forced file system check.
[[IMG]http://img172.imageshack.us/img172/2657/checkforcedhx9.jpg[/IMG]](http://imageshack.us)

From around 30-40% into the check, it starts throwing out a lot of these errors.
[[IMG]http://img96.imageshack.us/img96/2292/exceptionemaskrn2.jpg[/IMG]](http://imageshack.us)

Lastly, it throws me to a prompt which fails to recognize commands like "sudo".
[[IMG]http://img293.imageshack.us/img293/7407/promptxj3.jpg[/IMG]](http://imageshack.us)

I ran a self-diagnostic scan of my hard drive which seems to suggest that it's the problem of my hard drive, not Ubuntu..
[[IMG]http://img241.imageshack.us/img241/2804/biosme1.jpg[/IMG]](http://imageshack.us)

My laptop dual-boots Windows and Ubuntu. Windows came with my laptop, the original partition with windows on it was re-sized to make room for Ubuntu. Ubuntu has been working fine for the two weeks I've had my laptop. Yesterday, I booted my PC into GDM, and then had to shut it down from there. Since then, Ubuntu has failed to boot. Windows shows no problems.

---

### Post by PaulFr on 2007-07-03
At the **#** prompt, please try the command **fsck** Once that is complete (this may ask you for confirmation repeatedly - typically I would enter yes), then press Ctrl-D to continue booting. If the system comes up, then immediately back up all your files.

---

### Post by ugm6hr on 2007-07-04
Or boot off the LiveCD (if possible), and backup everything to an external / another HD.  

If a diagnostic HD test says there's a problem with the HD, there probably is.  Question is whether it is recoverable - does the HD diagnostic not give an indication?  Might be worth looking at the HD manufacturers website to see if there is a more recent diagnostic tool avalable (I know Hitachi have one).

Sometimes the HD can be told to ignore certain damaged sectors, or you can partition around those sectors.

---

### Post by Niomi on 2007-10-08
I tried fsck. The computer will boot normally for a few weeks, but then the errors will come up again. I have been fscking for awhile and have otherwise been operating normally, but I'm worried that my hard drive is on it's last leg.

---

