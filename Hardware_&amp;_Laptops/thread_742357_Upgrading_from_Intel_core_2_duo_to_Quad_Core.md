---
title: "Upgrading from Intel core 2 duo to Quad Core"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by jrharvey on 2008-04-01
Ok so I know nothing about hardware other than how to install a PCI or PCI-E video card and Upgrading RAM so i have a question here. My current processor is an intel core2 duo 2 Ghz and I want to upgrade to an intel core 2 QUAD processor. I dont even know if this is possible with the motherboard that i have so i wanted to ask the experts here. Im sure there is a little more involved than simply replacing them but idk. Does anyone know if ubuntu supports this chip?

---

### Post by TheLions on 2008-04-01
You'll probably had to buy a new motherboard, but i cant tell you for sure because i don't know which model you have.

about Linux and multicore CPU:

"the linux kernel has excellent support for intel multi-core processors. linux has supported multi-core, multi-thread and multi-cpu systems for most of its existence. without this capability, linux would never have become the default operating system for multi-core, multi-thread and multi-cpu systems.

having said that, i've read some of the bug reports for the intel quad-core and core duo processors. simply put, they have terrible mistakes built into the hardware allowing things like privilege escalation. i would recommend everybody to steer clear of them until the most important of these problems have been fixed." (from [http://www.ideastorm.com/article/show/73275/Ubuntu_PCs_with_Quad_Core_processors](http://www.ideastorm.com/article/show/73275/Ubuntu_PCs_with_Quad_Core_processors))

---

### Post by jrharvey on 2008-04-01
ok so i booted into windows and downloaded cpu-z to see what my motherboard was. This is what i got.

---

### Post by jrharvey on 2008-04-01
I went to the intel website but they only list intel motherboards for compatability. Im not sure where to go and find this out.

---

### Post by jrharvey on 2008-04-01
is there nobody out there that knows where i can go to find this out?

---

### Post by jrharvey on 2008-04-01
bumb

---

### Post by TheLions on 2008-04-02
is this your mainboard???
[http://www.asus.com/products.aspx?l1=3&l2=11&l3=348&l4=0&model=1374&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=11&l3=348&l4=0&model=1374&modelmenu=1)

if it is, then you'll need a new MBO cause quad CPU operates on 1333MHZ, but your MBO supports only up to 800MHZ.

Please let someone confirm this....

---

### Post by BooNality on 2008-04-02
In short your going to need one of the following chipsets to support a quad core processor.

P35
X38
X48
680i
750i
780i
790i

It gets a little more complicated for memory compatibility and what not but those chipsets all support intel quad cores, the P35 has support for the newest quad after BIOS update only.  The X38 and X48 support the newest one out of the box.  The P35 is alot cheaper and does support the Q6xxx series out of the box though.

---

### Post by jrharvey on 2008-04-02
Ok, thanks guys. Looks like i may just get a whole new computer. Quad core computers arent too expensive now.

---

### Post by cosh1 on 2008-04-10
I recently replaced my motherboard and cpu.  I am now running an Asus Rampage Formula based on Intel's new x48 chipset, and a Q6600.  I haven't been able to get 8.04 beta to load from cd or install in 32 or 64 bit versions.  Is the x48 chipset not yet supported?  Would I have better luck with drivers in 7.10?

---

### Post by cosh1 on 2008-05-14
bump

---

