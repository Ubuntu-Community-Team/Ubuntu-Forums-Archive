---
title: "Reducing the size of a stubborn windows partition"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by jaebe2 on 2009-07-07
Hi,

I'm a relatively new ubuntu user.
I am currently dual booting vista and hardy heron (8.04). 

I would like to do a fresh install of Jaunty Jackalope (not upgrade via Intrepid Ibex). I have 80GB out of 115GB free on my windows partition. So I defragmented windows and tried to reduce the size of my windows partition using the 'shrink' volume' feature in vista's disk management.  But vista only allows me to shrink the partition by 15GB!, even though I have 80GB free. 

I searched through the forums and found a suggestion to turn off paging in windows and to delete 'ghost pages' (whatever they are)...I did so but still no luck. I then proceeded to defragment windows using a gnu tool (JFDefrag) twice and still the same. 

I tried to use gparted on the live CD. When I try to resize my windows partition it doesn't allow me to drag (and says there is no space before or after). 

Could someone please help me/suggest how I can reduce the size of my windows partition. :p

Regards,

Josh

---

### Post by mobilediesel on 2009-07-07
> **jaebe2 said:**
> Hi,

I'm a relatively new ubuntu user.
I am currently dual booting vista and hardy heron (8.04). 

I would like to do a fresh install of Jaunty Jackalope (not upgrade via Intrepid Ibex). I have 80GB out of 115GB free on my windows partition. So I defragmented windows and tried to reduce the size of my windows partition using the 'shrink' volume' feature in vista's disk management.  But vista only allows me to shrink the partition by 15GB!, even though I have 80GB free. 

I searched through the forums and found a suggestion to turn off paging in windows and to delete 'ghost pages' (whatever they are)...I did so but still no luck. I then proceeded to defragment windows using a gnu tool (JFDefrag) twice and still the same. 

I tried to use gparted on the live CD. When I try to resize my windows partition it doesn't allow me to drag (and says there is no space before or after). 

Could someone please help me/suggest how I can reduce the size of my windows partition. :p

Regards,

Josh

Try [JkDefrag]("http://www.kessels.com/Jkdefrag/"), it's faster than the Windows built-in tool. It has to run from Windows, though.

---

### Post by jaebe2 on 2009-07-07
Yes I did...Twice!
It still didn't help.

---

### Post by jaebe2 on 2009-07-07
Hey I think I've found a howto on this topic, 

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)


seems like it might work, I'll give it a try...

---

### Post by Mark Phelps on 2009-07-07
After you disable hibernation, remove the hiberfil.sys file -- this is the hibernation file that MS Windows automatically creates.  That's the size of your system memory and more.  Then, to the defrags.

Also, unless you have a Vista DVD handy, don't fall for the temptation to use Linux utilities to shrink the Vista OS volume.  You run the risk of corrupting the volume in the process, and only booting from the Vista DVD and running Startup Repair several times will restore the ability to boot into Vista.

---

