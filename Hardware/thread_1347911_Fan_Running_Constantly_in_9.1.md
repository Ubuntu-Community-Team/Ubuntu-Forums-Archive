---
title: "Fan Running Constantly in 9.1"
date: 2009-12-06
forum: Hardware
---

### Post by The_Pirate_King on 2009-12-06
I've tried a fix for it but it doesn't seem to do the trick. 

It's not so much that the fan doesn't know when to start up; it's that it doesn't know when to shut off.  The CPU will heat up, it will activate and cool it... and then it just never turns off, even when the CPU reaches the frigid temperature of 35 C. 
It's loud, it consumes battery power, and eventually it will wear down the fan. 
How do I fix this?

---

### Post by gnhorowitz on 2009-12-08
I'm having the same issue.  The fan turns on usually a few minutes after startup, and will then stay on permanently.

I've VERY new to Ubuntu (only installed last week), so I really have no idea where to start looking for a fix for this.  If someone has an idea, I'd love to hear it.

Thanks,
Gary

---

### Post by imaqt55 on 2009-12-14
Anyone found a solution yet?  I was using 9.04 and I never even heard the fan before. Just upgraded to 9.10 yesterday and the fan won't turn off!

---

### Post by luongo321 on 2010-08-07
I have a similar issue.

I just installed ubuntu 10.04 a few days ago on my laptop (first time dl'ing a Linux OS and it's amazing!)
I installed 10.04 with the wubi installer and have Windows Vista on my computer as well.

When I use Vista, the fan is pretty quiet, but when I use Ubuntu the fan is on quite often and runs louder. I have the 3d cube and skydome enabled. Could this be why my fan is running more frequently on Ubuntu? I have a toshiba a300-034 laptop. Not a super flashy graphics card on it, but it doesn't lag at all with the 3d cube. Could my cpu be working too hard because I have the 3d cube enabled?

---

### Post by tadaskr on 2010-08-08
i had same problems with fan. it runs same speed all time after bios set during boot. but if you have toshiba laptop i found solution. go to synaptic package manager and install packages: toshset, toshutils, fnfxd, acpi-support, acpitool, acpitool-dbg. I hear now fan goes faster when laptop heat and slow down when it's cold. It also fix briggtness. with these you can change it with fn+ f6 f7 keys, but it works after I install these packages and restart computer. The next time you restart computer it could don't work again and you should re-install all packages again. Well.. like this works on my toshiba satellite a300 and ubuntu 10.04 :)
Hope it helps

---

