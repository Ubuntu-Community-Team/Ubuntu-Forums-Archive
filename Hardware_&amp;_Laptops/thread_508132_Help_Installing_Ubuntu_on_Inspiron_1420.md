---
title: "Help Installing Ubuntu on Inspiron 1420"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by Zweih on 2007-07-23
I need help installing ubuntu 7.04 on the dell inspiron 1420

It keeps saying
can't access tty; job control is turned off

help plox

---

### Post by nichipet on 2007-07-23
Can you give some details of the setup? Is the Inspiron 1420 customized in any way, a different hard drive especially? Which CD or DVD are you using for installation, which version of Ubuntu, did you burn it or buy/order it?

---

### Post by Zweih on 2007-07-23
> **nichipet said:**
> Can you give some details of the setup? Is the Inspiron 1420 customized in any way, a different hard drive especially? Which CD or DVD are you using for installation, which version of Ubuntu, did you burn it or buy/order it?

Well, its Ubuntu 7.04

and the only difference between the normal inspiron 1420 and this is the 8400M GS card, otherwise free 2gb and 160gb hard drive and such
[http://www.dell.com/content/products/productdetails.aspx/inspnnb_1420?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/products/productdetails.aspx/inspnnb_1420?c=us&cs=19&l=en&s=dhs)

also, the ubuntu cd was one I ordered

---

### Post by nichipet on 2007-07-23
Take a look at this blog, maybe it can be of some help, even though you are working with only one hard drive:
[http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html](http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html)

---

### Post by Zweih on 2007-07-23
> **nichipet said:**
> Take a look at this blog, maybe it can be of some help, even though you are working with only one hard drive:
[http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html](http://blog.shevin.info/2007/04/how-did-i-fix-cant-acess-tty-in-feisty.html)

didnt work for me :(

---

### Post by nichipet on 2007-07-23
I'm running out of ideas. I searched Google and these forums for your error message and most people seem to have this problem after the install, during a reboot. That blog is one of the few places where it happened during a 7.04 install. I'm sorry I can't be of more help, maybe someone else has an idea of what to try.

---

### Post by bakketti on 2007-07-24
Zweih-

I had the same problem with my 1420. Here is what I did and everything worked out.

At the startup screen, press F6 to start with options. Add "break=top" to the commands. I also started in graphics safe mode because of my Nvidia card.

Next, when the startup stops again, type: "modprobe piix" then followed by "exit". Your installation should proceed without any more issues. *cross fingers* :)

---

### Post by Zweih on 2007-07-24
> **bakketti said:**
> Zweih-

I had the same problem with my 1420. Here is what I did and everything worked out.

At the startup screen, press F6 to start with options. Add "break=top" to the commands. I also started in graphics safe mode because of my Nvidia card.

Next, when the startup stops again, type: "modprobe piix" then followed by "exit". Your installation should proceed without any more issues. *cross fingers* :)
well, I installed ubuntu all good now.

Except I have to type modprobe piix then exit to get to the gui screen though

now, heres the troubling part; internet

---

### Post by nichipet on 2007-07-24
Wireless card problems?

I'm guessing since it's a Dell Inspiron, you have a Broadcom wireless card. If so, try this guide:
[http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

I've used it a few times on a Dell Inspiron 1501 and it works just fine (at least for 1501).

---

### Post by bakketti on 2007-07-24
> **Zweih said:**
> 
Except I have to type modprobe piix then exit to get to the gui screen though


You can edit a file in /etc to do it automatically. I found a post on the forums a week ago that describes what to do... unfortunately I can't find it and I already forgot how I did it. :)

---

### Post by nichipet on 2007-08-08
I think it's /etc/rc.local

Probably add modprobe piix to it and then make the file executable.

---

### Post by razeshkale on 2007-08-31
Anyone Got FIX???

Help Out Guys!!

---

