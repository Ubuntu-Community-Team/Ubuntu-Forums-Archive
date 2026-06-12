---
title: "solution for SiS 672 resolution issue!"
date: 2010-01-18
forum: Hardware
---

### Post by tomlinson on 2010-01-18
Hello!

I've been trawling the interwebs for AGES looking for a solution to this problem with Ubuntu 9.10 - basically, Ubuntu 9.10 does not support the SiS 672 Mirage 3 Graphics out of the box, but doesn't have an xorg.conf file to configure manually.

Without wanting to create an xorg.conf file, here is a solution that worked for me:

the original forum thread is [http://forum.novatech.co.uk/showthread.php?p=208493](http://forum.novatech.co.uk/showthread.php?p=208493)

There is a link at the bottom of that page to a driver which should download, the more direct link is: [http://nacho.larrateguy.com.ar/wp-co...0.9-1_i386.deb]("http://nacho.larrateguy.com.ar/wp-content/uploads/2009/07/xorg-driver-sisimedia_0.9-1_i386.deb")

I downloaded the driver, installed the package and rebooted and voila - my resolution is now fine.

Hope that helps someone who's been stuck for ages like I was :)

Tom.

PS I'm running Ubuntu 9.10 on an Advent 5302 (32bit). Also I don't know much about linux, or computers, so I can't vouch for the above link, all I know is it's worked for me and hasn't yet resulted in my computer breaking. It might break other computers so please check it out before downloading/installing it.

---

### Post by throneless on 2010-08-10
I have a Packard Bell easynote MH35..First, Ubunutu 9.10 fixed the OEM problem that my laptop has..then, I had the same problem as tomlinson and the solution in this post totally fixed it !! thx

---

