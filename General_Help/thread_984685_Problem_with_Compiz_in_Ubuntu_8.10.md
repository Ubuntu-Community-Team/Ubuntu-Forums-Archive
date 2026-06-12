---
title: "Problem with Compiz in Ubuntu 8.10"
date: 2008-11-16
forum: General Help
---

### Post by joecool362 on 2008-11-16
Ok, So in ubuntu 8.04 compiz worked great. When I upgraded, compiz worked, but horribly, like the cube effect worked great on the old edition, but on this one it was like I could almost see the frames. Now my friend said that my problem was simply my driver for my graphics card is wrong. He said use sudo dpkg-reconfigure xserver-xorg to fix. Well I ran though this process and got: sudo dpkg-reconfigure xserver-xorg xserver-xorg postin warning: overwriting possibly-customized configuration filr; backup in /ect/X11/xorg.conf.20081116202321 and then I got back where I started before typing cmd (root@nedry-ubuntu8:~#)my q is what now, how do I choose the correct driver for compiz?

---

### Post by Skripka on 2008-11-16
What graphics card do you have, and what driver?


From what I've read, it seems like Gnome/Compiz/Ibex and Nvidia/ATi have communications issues-and somewhere between those, there are big issues..  I say that as I've read several posts here about "Ubuntu" "Nvidia" problems---and the common thread these all usually have is that they are running Ibex with Gnome and wanting or using Compiz--and things at best aren't running well, and at worst are borderline unusable.


I say the above, with NO illusions of being thorough or scientific, or having researched the code etc....all I know is that my KDE setup runs slick with Nvidia driver 177.80 (and from what I hav and have not seen here-I'm "normal" in this regard)--and conversely lots of Gnome users are griping about the 177.80 Nvidia driver as being terrible.

---

### Post by loomsen on 2008-11-16
> **Skripka said:**
>  have communications issues

Yes indeed, even writing README in capitals won't do the trick.

Tho it's only one simple command in a terminal, at least for nvidia.
But since folks read about hotpluggable input support, it seems like README is a file to avoid. 
(plus, graphics devices are actually output devices....)

So, basically you're right, what most users seem to have in common is fear of death of a terminal, as well as reading useful files.

However, those who do know there are many nice and configurable options to be added to xorg.conf. 
OOps, did I say xorg.conf? I apologize, no need to configure it since the new X-server ships with hotpluggable INPUT support?...


@topic

You probably suffer from restrictive permissions of your nvidia driver.
Add a section, which will allow you to use your 3D accelerated driver with direct rendering. Install Protobuf. Be nice while protobuf builds the cache, you'll like it. Log out, back in, and ship it.

---

### Post by tuxxy on 2008-11-16
> **joecool362 said:**
> Ok, So in ubuntu 8.04 compiz worked great. When I upgraded, compiz worked, but horribly, like the cube effect worked great on the old edition, but on this one it was like I could almost see the frames. Now my friend said that my problem was simply my driver for my graphics card is wrong. He said use sudo dpkg-reconfigure xserver-xorg to fix. Well I ran though this process and got: sudo dpkg-reconfigure xserver-xorg xserver-xorg postin warning: overwriting possibly-customized configuration filr; backup in /ect/X11/xorg.conf.20081116202321 and then I got back where I started before typing cmd (root@nedry-ubuntu8:~#)my q is what now, how do I choose the correct driver for compiz?

If you are using nvidia what driver version 173 or 177? they should both be available for activation under system > admin > hardware drivers

> **Skripka said:**
> What graphics card do you have, and what driver?


From what I've read, it seems like Gnome/Compiz/Ibex and Nvidia/ATi have communications issues-and somewhere between those, there are big issues..  I say that as I've read several posts here about "Ubuntu" "Nvidia" problems---and the common thread these all usually have is that they are running Ibex with Gnome and wanting or using Compiz--and things at best aren't running well, and at worst are borderline unusable.


I say the above, with NO illusions of being thorough or scientific, or having researched the code etc....all I know is that my KDE setup runs slick with Nvidia driver 177.80 (and from what I hav and have not seen here-I'm "normal" in this regard)--and conversely lots of Gnome users are griping about the 177.80 Nvidia driver as being terrible.

Well my GNOME setup has run slick since Ibex beta with 173 or 177 drivers, funny I seem to remember a lot of ATI threads more than nvidia which isnt unusual heh

---

### Post by loomsen on 2008-11-16
PS:

[Section to add in this post...](http://sudan.ubuntuforums.com/showpost.php?p=6101579&postcount=19)

---

### Post by mike010 on 2008-11-17
I run Gnome/Compiz/Ibex and Nvidia on 8.04 and have no problem

---

### Post by loomsen on 2008-11-17
> Compiz/Ibex
> 8.04

Thank you for this useful post.

---

