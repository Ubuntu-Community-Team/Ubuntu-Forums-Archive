---
title: "System freezes with ati-driver"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by Ashtray on 2005-06-16
Hi peepz,

With the help of another thread in the how-to section, i was able to install the latest ati driver wich works. Now as i try running americas army, or tux racer my system freezes completely after a minute or so. I also had this problem with my previous distro (Fedora Core 3).

It got me puzzled for a while now, i hope anybody could point me into a direction where to look or even better, got the solution ...

---

### Post by Ashtray on 2005-06-18
Kicks up toppic..

Nobody ? :neutral:

---

### Post by Brikkah on 2005-06-18
I hope someone can help you, I had a similar problem to.. then nobody answered :(

[dutch] Hoi! :) [/dutch]

---

### Post by Ashtray on 2005-06-20
I kept on searching, restoring bios settings..
Using internal/external AGP from driver...

Overclocking / without overclocking, thats not it.. I'm pretty sure the problem is within the software or the combination with the soundblaster live! , but i'm not sure yet.

No results so far or what so ever..

 :neutral:

---

### Post by Ashtray on 2005-06-23
No results problem still not solved out

---

### Post by ywwg on 2005-06-23
I upgraded to kernel 2.6.12 (manually) and disabled DRI in my xorg.conf, and I haven't had any crashes since.  I'm not sure which of the two solved the problem.

---

### Post by Ashtray on 2005-06-24
Ok, ill try disabling dri then, ill let you know the outcome..

//edit
setting no_dri to " yes"  results in a VERY low frame rate.. this isnt an option

---

### Post by Gezzer on 2005-06-24
open a konsole and insert

sudo dpkg-reconfigure xserver-xorg

try the settings here to configure the system with the new ATI drivers ...

---

### Post by Ashtray on 2005-06-24
I tried the reconfigure thing,but i didn't get lucky and had to overwrite the xorg.conf with a backup to get X started again..

I dont think that restoring default X settings will clear up the problem really..

---

### Post by foxy123 on 2005-06-25
I guess if you disable DRI you will lose 3D accelaration. Disable FastWrite, try to set you AGP to x4 and try to increase AGP voltage.

---

### Post by python_guy on 2005-06-25
I have the same problem in a ATi 9100 and I found no fix yet. [-X

---

### Post by Ashtray on 2005-06-25
Thx for your reply (all of you ) but hey, why should i mess around with the bios settings ?
[moral talk]
The M$ XP operating system can work fine with my hardware and it's configuration. This really should be something i could fix within the ubuntu linux OS itself...

We, at least I, want to bring linux to the people, we don't want to tell people they need to change BIOS settings to make it all work, do we ?
[/moral talk]

It's kinda crappy the GUI installer wich came with the ati driver release doesn't install the driver as it should, as i still needed to copy those .ko files.

I really think the problem lies in the driver itself, looking at the installation, comparing to the Nvidia installation wich just WORKS, ati is far behind...

But hey, even after taking the (too much)  installation steps the system hangs after 2 minutes when running 3d applications...

I'm sorry i got a little offtopic here, but let us be honest, if we want to make linux a serious OS we should at least take care of "complex" video driver installations.

this wasn't flaming to ubuntu, but to ATI who are lacking in support for their customers.

---

### Post by foxy123 on 2005-06-25
It is not a problem of ATI driver installation but the way it works with X. Basically due to some unkown reasons it causes this freeze on some systems regardless of Linux distribution installed.  It usually affects R350 chip. As I said by other people's experience there are several things you can do trying to fix it. Although there s no guarantee you will succeed.

---

### Post by Ashtray on 2005-06-25
[QUOTE=foxy123]It is not a problem of ATI driver installation but the way it works with X. Basically due to some unkown reasons it causes this freeze on some systems regardless of Linux distribution installed.  It usually affects R350 chip. As I said by other people's experience there are several things you can do trying to fix it. Although there s no guarantee you will succeed.[/QUOTE]

That could isolate the problem to a kernel problem right ?
This said, it doesn't close the option that it IS the driver causing it...

//still we need to take to many steps to get it working anyway, if it would work...

---

