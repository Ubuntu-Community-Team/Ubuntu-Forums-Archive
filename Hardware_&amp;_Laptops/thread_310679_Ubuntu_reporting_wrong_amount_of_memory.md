---
title: "Ubuntu reporting wrong amount of memory"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by icksa on 2006-12-01
Hi:
I just upgraded to 4 gb of ram. When I went to the system monitor in gnome it only said I had 3 gb. Then I checked /proc/meminfo which also said I had 3 gb. 

I started the ubuntu memory test program from the boot menu and that reported 4 gb. Finally, I checked my computers BIOS which reported 4 GB as well.

Any suggestions?

Thanks

---

### Post by jml on 2006-12-01
Does your computer have a separate video card and VRAM?  Or does it have integrated graphics that shares system ram.  Since you see 4 gigs at the bios level, its unlikely that there is a problem with faulty RAM.  Since Gnome is very resource intensive, if you are running with integrated graphics, its possible that one gig is being dedicated to graphics duty.  If you have a dedicated graphics card, then I'm affraid that I am stumped.

Joe

---

### Post by meng on 2006-12-01
Holy cow I wish I had 4 GB of RAM.

---

### Post by icksa on 2006-12-01
Hi:
I do have a dedicated card with 64 mb of memory.

---

### Post by cyberbat on 2006-12-01
My understanding is that not only Ubuntu but even Windows Vista does not support RAM more than 3.2GB

Further, only 64-bit OS can recognize RAM beyond the 3.2GB limit... you may want to try [http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-desktop-amd64.iso](http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-desktop-amd64.iso)

---

