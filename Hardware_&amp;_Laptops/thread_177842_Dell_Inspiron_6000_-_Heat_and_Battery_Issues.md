---
title: "Dell Inspiron 6000 - Heat and Battery Issues"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by Kishore Sundara-Rajan on 2006-05-17
I have Drapper Flight 7 with KDE on my Dell 6000. Everything works fine except my laptop gets really really hot when running off the mains; and when on batteries it can barely squeeze out 1 hr on a full charge. This problem does not occur when I boot into XP. Any pointers on how to solve it? Thanks!

---

### Post by Mr Fat Bat on 2006-05-17
Wow, I'm running a 6400 and it doesn't do that.  I have found though that it can really heat up if you do not have the latop on a flat surface such as desk.  When I have it on my mattress the thing gets really hot as the airflow sucks, but I doubt that's your issue ;)

I take it you're also not running anything too "hardcore" on there all the time, such as XGL or something like that?

---

### Post by slightly72 on 2006-05-17
There are a bunch of threads on heating issues on Inspiron laptops, search for "inspiron heat" and you'll see some. Granted, most of those are for the 51xx line of Inspirons, but they might help. Some things that helped: cleaning up the insides, loading p4-clockmod and powernowd (I assume 6000 has P4), disabling apmd.

---

### Post by Kishore Sundara-Rajan on 2006-05-18
Thanks for the inputs. I have installed gkrellm to monitor the temperatures accurately. I have also installed powernowd. However I could not find p4-clockmod on synaptic.

Another thing I noticed was that when I run the laptop under "powersave" mode in Klaptop, the processor speed is locked down to 800 MHz irrespective of the load, and the temperature is around 43C. In any other mode it goes up to 2 Ghz even when nothing is running, and heats up to 65C in a matter of seconds. What am I doing wrong?

---

### Post by groggyboy on 2006-05-19
I notice that my laptop also heats up - altho not nearly as fast or as extreme as yours.  As far as extending battery life, have you looked at laptop-mode and laptop-mode-tools?  I use them on top of powernowd.  There's a conf file somewhere to adjust the settings.  Or you might try powermgr.  Its not in the repositories and I haven't tried it, but the [website]("http://powermgr.sourceforge.net/") sounds promising.

Also, are you using dapper or breezy?  Laptops like the dell inspiron 6000 have slightly better performance all-around in dapper.

Other than that, the extreme heat is probably just something you'll just have to live with.

---

### Post by slightly72 on 2006-05-21
p4-clockmod is a kernel module, and installs with the kernel image -- so there's nothing that you need to install separately. You can do a "locate p4-clockmod" to see where it's located, but you can simply add  a line that says "p4-clockmod" to /etc/modules to have it loaded at boot time.

I've never used Klaptop, but I assume that it's an interface to powernowd. I've noticed that powernowd cannot read all the processor states correctly when p4-clockmod is not loaded (for example, when p4 was not loaded, the processor was in just two states -- 1.8GHz and 2.8GHz, with p4 loaded there were 8 possible states for powernowd -- each about 12.5%x2.8GHz apart) -- so that might be the root of your problem.

Also, how old is your laptop? You might need to open and clean it. The cooling system on my laptop easily catches dust, and clogs the ventilation entrance to the fan. For me it helped reduce the CPU temperature by about 8C.

There are a few more things that you could do (disable apmd -- use sysv-rc-config, downloadable from synaptic, search the forums for its use). I've also put my computer in the lowest performance state, 1.8Ghz, it works just fine for what I'm running on it (some CAD development, playing music, samba server for the rest of the home network).

---

### Post by Kishore Sundara-Rajan on 2006-05-22
Thanks for the replies. My laptop is about 5 months old, so I doubt if I need to open it up and clean it. Anyways, after spending a few days playing around with it, I just reinstalled Ubuntu from scratch, installed powernowd and enabled p4-clockmod. Everything seems to work fine now. Maybe it was a problem with KDE?

---

### Post by ephman on 2006-05-23
hi,

just to give some reference to temps.  i'm running ubuntu breezy on an inspiron 6000.  my temps when under a light load stays pretty steady around 34c, when i'm maxing out the cpu i've seen it go as high as 50c, but very quickly starts to drop as the fan picks up rpm's, and will stay between 42c - 46c.  i believe these are pretty normal temps for this machine under these loads.  

have you taken a look to see what programs are causing such a heavy load on your machine?  because your batts should last way more then an hour if your machine isn't maxing out the cpu or spinning those discs like crazy.  just a thought to try to narrow down what it could be.

thanks for the bandwidth,
ephman

---

