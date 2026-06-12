---
title: "install smartlink modem with kernel 2.6.12"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by protocol_2006 on 2005-09-12
Hi 
I get the last version of ubuntu.but the kernel version is 2.6.12.8.386 so i can't find any suitable driver for Smartlink modem.for example for kernel -->2.6.10 we have this  driver [http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb](http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb)    but for this new kernel how can i do? if i can't setup and use modem , ubuntu is't good for me. please tell where can i get the driver for new kernel. thanks

---

### Post by Bruce3000 on 2005-09-12
[QUOTE=protocol_2006]Hi 
I get the last version of ubuntu.but the kernel version is 2.6.12.8.386 so i can't find any suitable driver for Smartlink modem.for example for kernel -->2.6.10 we have this  driver [http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb](http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb)    but for this new kernel how can i do? if i can't setup and use modem , ubuntu is't good for me. please tell where can i get the driver for new kernel. thanks[/QUOTE]
 Do you have an internal modem?

If so, you may want to have a chat with the people at [www.linmodems.org;](www.linmodems.org;) it's an ogoing project - they helped me to get a driver for my old lucent chipset modem.

Right now I'm using a crappy old 1990s external modem. Works a dream - pity about the bandwidth though. Such is the life of a uni student ;)

Hope the above link helps!

Bruce

---

### Post by protocol_2006 on 2005-09-12
First thanks for your answer
but I have an externel modem with smartlink chipset. I have installed My modem in suse 9.2 and fedora core 2 . I used  rpm package that i downloaded from smartlink site , but in ubuntu i can't install rpm package .I have found in  ubuntuguide site  a deb package that  i mentioned in my first post for smartlink modem but that  package dosen't work with  new kernel 2.6.12 .

ubuntu company  released ubuntu with new kernel .where can i find driver for my modem for new kernel . I hope ubuntu  company  help me???

---

### Post by Bruce3000 on 2005-09-12
[QUOTE=protocol_2006]First thanks for your answer
but I have an externel modem with smartlink chipset. I have installed My modem in suse 9.2 and fedora core 2 . I used  rpm package that i downloaded from smartlink site , but in ubuntu i can't install rpm package .I have found in  ubuntuguide site  a deb package that  i mentioned in my first post for smartlink modem but that  package dosen't work with  new kernel 2.6.12 .

ubuntu company  released ubuntu with new kernel .where can i find driver for my modem for new kernel . I hope ubuntu  company  help me???[/QUOTE]
 actually, you can extract binaries and souce from RPMS and re-package them as .deb files ... it's rather invloved though :(

Can you find an RPM package that works with 2.6.12 kernel?

You can extract the rpm contents you can:

"To extract files from a RPM file to a directory without installing it.
    "rpm2cpio" archives the files to standard out in CPIO format.

    Example:  
	cd wip/foo
	rpm2cpio foo-2.0.i386.rpm | cpio -ivmud"
 
.deb files are constructed thusly: [http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.en.html)
there is a good article on packages here: [http://www.pcxperience.org/james/presentations/20040617-presentation.html](http://www.pcxperience.org/james/presentations/20040617-presentation.html)

Hope this helps...

As for the Ubuntu company helping... it's the Ubuntu community that helps ;)

---

