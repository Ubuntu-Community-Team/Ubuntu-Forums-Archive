---
title: "Boot Time slow"
date: 2010-07-20
forum: Hardware
---

### Post by U b u n t u - L i n u x on 2010-07-20
Hi,

I have an asus eeepc 1000he and i am using the desktop version of ubuntu because i prefer the interface. my boot times are slow because it takes over a minute. i heard that if you recompile your kernel to your specs then that would improve the boot time, however i cannot get the kernel to work. can someone please analyse my attached bootchart image from today and give me some tips on how i can improve it.

---

### Post by iponeverything on 2010-07-20
your boot is good for an atom processor. 

Turn off some of the services that are started at boot and it will help.

---

### Post by IcarusR on 2010-07-20
You can use 'BUM' to graphically stop unneeded services, its in the repositories.

---

### Post by U b u n t u - L i n u x on 2010-07-21
I have disabled some services but the boot time is stlll over 1 minute excluding login time, is there anything else i can disable

---

### Post by IcarusR on 2010-07-21
Compiling your own kernel specifically for your hardware will help.

See these articles for further ideas...

[http://www.improvedsource.com/view.php/Linux_Fastest_Boot_Time_Challenge/3/]("http://www.improvedsource.com/view.php/Linux_Fastest_Boot_Time_Challenge/3/")

[http://blogs.techrepublic.com.com/10things/?p=387]("http://blogs.techrepublic.com.com/10things/?p=387")

---

### Post by PresenceofMind on 2010-07-21
Hello,

You can disable things like bluetooth (if you don't use one), Alarm Notifier, Ubuntu One, Visual assistance, Remote Desktop, Print queue applet, Check for new hardware, Deja Dup Monitor, Personal File Sharing etc. I disabled all that and I'm getting good results. My spec is shown below if you want to know.

 Mine boots in under 40 seconds, but i've enabled automatic login so it takes about 55 seconds. I've read that some guys can boot it in about 25 seconds by recompiling the kernel, but I'm not too confident in doing that.

---

