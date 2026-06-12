---
title: "MacBook Pro &amp; Ubuntu through parallels"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by teumima on 2007-01-31
I saw a few howtos for installing Ubuntu on the MacBook Pro. I haven't tried any of them.

I did however install parallels desktop last night. This is a commercial product so nothing open sources here. If you have a Mac in the first place your probably not pure opensource anyway (unless you won it from cocal cola ;)

I have a MacBook Pro 17" Intel Core Duo 2 2.33 Ghz, 2GB DDR RAM.

I installed Breezy straight from the CD, as if I were installing it on my PC, just in parallels virtual HD.

It looks so cool. So fast. i saw in the howtos that you had to do this to enable that and do this to enable that other thing, and so on. With parallels you dont have to enable anything. My keyboard backlight works by itself for example.

Tonight I'm going to install dapper.

The nice thing about it, is that I can have one desktop be Ubuntu, and my other three Mac OS X or whatever other OS I choose to install.

You can try it for free. I recommend it, even if you don't do commercial software, just to experience it, it's very impressive.

---

### Post by macpilot145 on 2007-02-14
Hello.  I am trying to do the same thing on my Mac.

I have Parallels installed and have been running XP on it.  I downloaded the Ubuntu 6.10 image and burned it to CD.

I get to the point in the install where you see a dialog box that is titled "Installing System" and the status is "Loading module aec62xx for IDE chipset support" and it just hangs at that point.

Is there something I am doing wrong?

Any help is greatly appreciated!

Thanks!

---

### Post by locklin on 2007-03-03
How can I get 1440x900 resolution in Ubuntu using parallels in my MacBook Pro?

---

### Post by teumima on 2007-03-03
sudo dpkg-reconfigure xserver-xorg

---

### Post by locklin on 2007-03-04
> **teumima said:**
> sudo dpkg-reconfigure xserver-xorg

Thanks! It Worked...

Now I have another issue, my ubuntu clock is going like 2x faster than the real clock.

---

### Post by tubasoldier on 2007-03-05
> **locklin said:**
> 
Now I have another issue, my ubuntu clock is going like 2x faster than the real clock.

That sounds like a kernel timing issue. the only fix that I know of is to recompile the kernel. Maybe someone else knows another way?

---

