---
title: "Can I use rpm?"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by dnewaza on 2005-10-18
Hi everyone

I've got a _82845G/GL[brookdale-G]/ge_ chipset integrated graphics device, and the only drivers that i've found are these:

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=865&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")

Can I use the rpm to install those drivers?
And how? this way:? ?

*apt -rpm-repository dri-I915-v1.1-20041217.i386.rpm*

Than you

---

### Post by fatbat on 2005-10-18
Try using a package called alien.  This will convert your rpm package to what ubuntu expects.

The command is 

alien -d *package.rpm*

the -d is an instruction to convert to deb.

Hope that helps.;)

---

### Post by frodon on 2005-10-18
It's generally not recomended to use rpm packages, use them only if you can't find a better way.

---

### Post by Polya on 2006-07-10
.rpm files are packaged in red hat's package standard, rpm, and can be converted to .deb files (debian/ubuntu packages) by using the "alien" command. to convert them, first install alien by typing "sudo apt-get install alien" if it isn't installed on your system, then type "sudo alien [filename]" to produce a .deb package in the same folder. you can then install the .deb by typing "sudo dpkg -i [filename]".

---

