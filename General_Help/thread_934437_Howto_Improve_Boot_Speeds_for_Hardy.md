---
title: "Howto Improve Boot Speeds for Hardy"
date: 2008-09-30
forum: General Help
---

### Post by brnetonboy on 2008-09-30
I want to improve my boot up time for Hardy Heron 8.04, and I'm wondering what the best way to go about doing this is. 

I installed _[bootchart]("http://www.bootchart.org/") _which automatically shows me my boot time info through pictures magically appearing in /var/log/bootchart . I'm at about 35 seconds.

I assume that improving boot speeds involves disabling things you don't need and getting your OS customized to your processor and other hardware. (For example, I saw somewhere something about making sure both processors in a dual core system are being used during boot.) But I don't know where to begin!

Is there a wiki somewhere where people share knowledge on this? How about a tutorial or a guide? If not, maybe this thread can be a good place to post tips on how to improve Hardy boot times.

Thanks!

--edit:--
Also, I am wondering how to read the bootchart chart! How can I identify problem spots and how can I improve those things?

---

### Post by Aero-Z on 2008-09-30
You can enable/disable additional services with [BUM]("http://ubuntuforums.org/showthread.php?t=82783")

---

### Post by cariboo on 2008-09-30
I just read a blog post about what Mandriva is doing to speed up the boot process. Have a look at it here:

[http://blog.crozat.net/2008/09/improving-boot-time-on-general-linux.html](http://blog.crozat.net/2008/09/improving-boot-time-on-general-linux.html)

You may find a few hints here, but it is pretty esoteric stuff.

If you are going to start disabling services, make sure you know what you're disabling, before you start as you will probably end up with a system that won't boot.

I would suggest that while looking at the bootchart png you do a google search on each and every service that you are unsure about. I noticed that quite a few services start up simultaneously so there won't be any help there.

Good luck.

Jim

---

### Post by Aero-Z on 2008-09-30
[Here's]("http://ubuntuforums.org/showthread.php?t=89491") an old guide where you might get some info about different services.

---

### Post by oldos2er on 2008-09-30
You can use sysv-rc-conf to disable uneeded services. It's CLI, but very easy to use.

 You can google loads of web sites with tips for speeding up boot times and performance in general. Just be careful; there is much bad info as well as much good info out there. It's probably best to ask about a specific tweak first before actually implementing it.

 I use the CONCURRENCY=SHELL and vm.swappiness tweaks myself.

---

