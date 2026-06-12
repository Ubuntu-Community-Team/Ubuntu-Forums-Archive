---
title: "Older Laptop"
date: 2010-05-09
forum: Hardware
---

### Post by RasterBurn on 2010-05-09
hello, i am considering to buy an older laptop from a friend of mine, its about 11 years old so i am thinking only to offer him around $10 for it, the specs of the laptop are:

**Processor**

**[Pentium III processor 800MHz featuring Intel SpeedStep Technology 		]("http://www.intel.com/intelinside/weblinks/english/pmp.htm")**

 		
 	 	 	 	 	**Pre-Installed Software**

 	[Genuine]("http://www.toshibaeasyguard.com/notebooks/viewConfig.jsp?configID=104&status=classic#")  Windows® ME
 	 	**Standard Memory | Maximum Memory**

 	128MB PC100 Synchronous DRAM (SDRAM) | 384MB (maximum expandability)
 	 	**Hard Disk Drive**

 	20GB
 	 	**CD-ROM Drive**

 	8X DVD-ROM drive
 	 	**Display Size**

 	14.1
 	 	**Video Memory**

 	8MB
 	 	**Battery Life**

 	Up to 2.5H

i am unsure if he has done any upgrades to it or not, but would these specs be enough to run ubuntu 10.04? i was thinking of doing a minimal install on it and attaching it directly to my desktop computer via a network connection, either way, what would my options be for this laptop if i were to pursue purchasing it? aside from being a paper weight or straight to the bin

---

### Post by Mike BFD on 2010-05-10
According to Release notes ([http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)), 10.04 requires at least 256Mb of RAM - 256 after "stealing" some by videocard. So that laptop would work only with its maximal 384Mb.

Also, 10.04 offers just insufficient support for "legacy video chips", I experienced it with a much newer laptop (Intel 8xx video)...

---

### Post by RasterBurn on 2010-05-10
so in other words the said laptop would not cut it for Ubuntu 10.04? would the netbook edition of Ubuntu be suitable for this laptop? if not, would i be able to configure ubuntu to connect to my desktop during boot up and use the desktops resources as its own to free up the screen, if not, i suppose i could send an email or 2 out to the debian comunity to see if their net install disk has any such options for me :P

---

### Post by Mike BFD on 2010-05-10
I suspect all versions of 10.04 (including Netbook remix) have more or less similar requirements; however, I guess you better search the forums and/or wait for somebody from "the Cool Guys" to reply.

I also suspect it's just impossible to use another computer's resources like RAM on boot up...

---

### Post by krazyd on 2010-05-10
The 256MB requirement is more for the live CD than for the final ubuntu system. I've run Ubuntu (the gnome desktop) on a 128MB machine before.

There is a page with some more info on the community wiki:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I'd advise getting some more RAM anyway if the machine can be upgraded. (should be able to find some on ebay or similar for pretty cheap)

If you don't want to manually build the graphics stack as in the link above, you could try something like this?
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by RasterBurn on 2010-05-10
well i am familiar with fluxbox, used to run it on a laptop i had about 5 years ago on a laptop that came pre-installed with win98 and it ran exceptionally well with debian and firefox so naturally i should do the same seeing as this laptop would be a little bit more powerfull but of course that was a debian version of that time (i think at the time it was debian 3.0 codenamed: woody) though i havent worked with the cli installer of Ubuntu though as for resources go, i guess the goal would be to setup a minimal installation to get the laptop running enough to load up a remote login on the desktop, I think a stick of 256mb pc100 ram will cost about $30

---

