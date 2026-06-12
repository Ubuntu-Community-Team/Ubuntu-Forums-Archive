---
title: "System hang on Hoary (Final Release)"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by rigues on 2005-04-10
Hi everyone!

About a week ago I did and upgrade from Warty to the Hoary release candidate without major issues. Now I did another upgrade to Hoary final, and i've been experiencing system hangups ever since. 

I still can't trace what's causing them, and they are not time-based. Sometimes the system hangs after a few minutes, sometimes after hours. Funny thing is, after it "hangs" I can still move the mouse, but not much else (like switching to another console. The keyboard seems "dead", even the LEDs (like CAPS) won't turn on).

The system is an AMD Duron 1.3 GHZ with 256 MB of RAM and an nVidia GeForce 2 MX 440 card. I'm running kernel 2.6.10-5-386 and the nVidia binary drivers from multiverse. (nvidia-glx 1.0.7174-0 and nvidia-kernel 1.0.7174+1). X.org is version 6.8.2-10.

I suspected the powernow daemon could be the source of the problem (since it's automatically being started, even if my machine does not support powernow), so I stopped it, but the problem persisted. I went back to kernel 2.6.8 about one hour ago to get rid of the problem. It's too soon to tell, but I have not had a system hang ever since.

Does anyone have any ideas on what is happening?

-- 
-Rafael Rigues
 [email]rigues@gmail.com[/email]

---

### Post by wolovids on 2005-04-10
Sounds like [Bugzilla Bug 7183 - nvidia-glx crashes/lockups](https://bugzilla.ubuntu.com/show_bug.cgi?id=7183).

It's the newest nvidia driver.  I turned off RenderAccel in my xorg.conf file and no more lock ups occurred.  However, that slows down the resizing of the windows.  So, I reinstalled all the nvidia packages and re-enabled RenderAccel again and so it hasn't locked up once all day today.

---

