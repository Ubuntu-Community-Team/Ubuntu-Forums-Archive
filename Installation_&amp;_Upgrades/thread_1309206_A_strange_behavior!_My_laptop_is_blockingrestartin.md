---
title: "A strange behavior! My laptop is blocking/restarting after upgrade!"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by vasiauvi on 2009-11-01
Hello all,

This is a long writing but please be patient and read all. I really need your help.

I have a problem/issue that I can't manage to get it trough.
I have a laptop Asus X51R and a Intel DualCore that I've bought in 2008. Since the first day when I've installed Windows
I've seen that even from installation process my laptop was restarting. Because I had to send the laptop quickly in other country to my wife I didn't send the laptop to the warranty. The laptop with WindowsXP was restarting 2-3-4 times/day.

When my wife came from France I've installed OpenSuse 11 but in this case the laptop was blocking and the CAPS LOCK LED was blicking. The only thing to do was to hard restart (from the button) de laptop.
After that I've deleted the OpenSuse and installed Ubuntu 8.10. The same behavior.
Upgradet to 9.04 and the blocking was stopped but and different issue appeared: the system is logging OUT randomly like this: the screen is getting black and after that the image with the wallpaper or what I had open is appearing again but distortioned. After this the logging in window is appearing: where to choose the user, password, window manager -- you know what I mean :).
This was happening also 2-3 times/day.

Now I've upgrade to 9.10 and I have the same problem like on 8.10: blocking, CAPS LOCK LED blicking and after that restarting.

What I want to ask is : how can I find what is wrong with my laptop?
I've send it to warranty and they said that didn't found nothing wrong, they used a benchmark/stress program and it didn't restarted. This was that they said!

I think that a single module ot part is damaged but why the behavior from 8.10 to 9.04 and 9.10 is different. What is so different in the configuration? The kernel is not the problem, I think, because in 9.04 I've installed and used different kernel verion.

Before send again to warranty I want to make an idea of what can be damaged and for this I ask your help. Maybe there are some commands that I can use to find out! I will make a video with my photo camera and post on Internet and put here the link.

Thank you all for the patient and sorry for my mistakes in writing!

---

### Post by vasiauvi on 2009-11-02
Ok, it's seems that I've written a lot and unfortunately no one can help me with my issue.
But I want just to add something strange:
I have 2 kernels: 2.6.28 from previous 9.04 and 
kernel 2.6.31 from new 9.10.
The strange thing is that on 2.6.31 my laptop is blocking/restarting but on 2.6.28 it's working OK except that I don't have sound!:(

I don't know what could influence from 2.6.31 kernel that the system to hook up.

Now I regret that I've upgraded to 9.10 :(.

---

### Post by javorulz on 2009-11-02
I have the same problem, so, I decided to do a downgrade, I upgraded to Karmic but everything crashed, now im returning to jaunty

---

### Post by vasiauvi on 2009-11-02
And did you had problems downgrading? I only upgradet until now, but for everything there is a start :)

---

### Post by vasiauvi on 2009-11-08
It seems that nobody knows how could I see what is the reason for this issues. Then please look at this video: [http://www.youtube.com/watch?v=vc_ZTivLTZI](http://www.youtube.com/watch?v=vc_ZTivLTZI)
I've recorded a blocking phase but what is strange here is that the image is distortioned and this I didn't see it before.

What I want is to understand what is causing the problems to tell the warranty guys what could be the problem. I've send 5 month ago this laptop to them but they said that didn't saw anything!

Thanks!

---

### Post by vasiauvi on 2009-11-10
OK, thanks for the help! :(
I will try a different Linux distribution!

---

### Post by vasiauvi on 2010-03-20
OK, this problem is fanally over for me! There wasn't nothing wrong with Linux or WindowsXP, my laptop was the problem...My CPU was having some errors or something.

After sending the laptop 3 times to waranty now is OK.
But how I've managed to understand what piece of hardware was the problem? With Ubuntu ofcorse!
In Windows i've installed a lot of testing programs:RAM,hard disk, CPU etc but nothing was showing me that something is wrong.

In Ubuntu I have CPU Frequency Monitor and usually I let at Ondemand. But one day I've set the CPU to Performance, that means that the CPU is on the highest CPU power.I've observed that when I let the scalling on the Performance my laptop is not restarting ot blocking. After I set it to Ondemand and the CPU was going from 1.8GHz to 800 MHz the system blocks.

With this I've managed to see that the problem wasn't from RAM (has been changed from the second warranty), not from hard drive (checked with smarctl) and not from video card or something else.

I've said to the warranty guys that may be the CPU damaged and after replacing it (at the third time) now, after 2 months, everything is OK.

---

