---
title: "Ubuntu does not pickup my scanner"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by cavillas on 2006-03-30
](*,) I have an HP scanjet 3970.  There are no Linux drivers for it by HP and Ubuntu doesn't pick it up.  The normal linux Twain drivers won't work either. Any suggestions please?

---

### Post by benvdh on 2006-03-30
Hey,

did a little search on the site of the sane project (OSS project that makes it possible to use your scanner on linux). On their site I found that the project itself doesn't have a driver available but they did have a link to the following project :

[http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/)

Which is the driver you are looking for. Since it has been based on the sane api you will need to install sane to be able to work with the driver. So this what you have to do to make it work :

1. Install sane and sane-utils using synaptic or some other package manager.
2. Download the debian driver package here:

[http://prdownloads.sourceforge.net/hp3900-series/hp3900-sane_bin_0.4-1_i386.deb?download]("http://prdownloads.sourceforge.net/hp3900-series/hp3900-sane_bin_0.4-1_i386.deb?download")

3. Install it using the following instructions:

3.1 Open a terminal
3.2 use cd to go to the folder where the package has been downloaded
3.3 install the package using this command:
> sudo dpkg -i package_name.deb

replace package_name with the name of the deb file you've downloaded

Good luck,

Regards,

Ben

---

### Post by cavillas on 2006-04-03
sorry to be late with a reply.  But thanks very much, will try it soon.

---

### Post by gman2004 on 2006-05-17
Itryed your method but Iget this error:> dpkg: error processing package_hp3900-sane_bin_0.4-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 package_hp3900-sane_bin_0.4-1_i386.deb


---

### Post by garretwp on 2006-06-03
I have installed the driver package for this scanner, but I am getting a "Access to this resource has been denied" message. I can run it as root but can not as any other user! Is there a way to get this to work as any other user?

Garrett

---

### Post by garretwp on 2006-06-03
I have a fix for my problem. I had to go into /dev/bus/usb/005 and do a chmod a+w on 002 and all worked out well! 

I hope this helps or anyone who might run into a similar issue.

Garrett

---

### Post by gb7055 on 2006-09-30
Thanks for the tip Ben.  This works great with my Scanjet 3970.

---

