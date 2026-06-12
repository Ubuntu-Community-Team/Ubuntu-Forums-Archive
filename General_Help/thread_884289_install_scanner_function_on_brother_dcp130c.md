---
title: "install scanner function on brother dcp130c"
date: 2008-08-08
forum: General Help
---

### Post by pdhb on 2008-08-08
I have now, thanks to plucky successfully got the dcp130c brother printer working, but now i want to get the scanner to work.

can anyone help with this, xsane cant find it??

thanks

pdhb

---

### Post by phidia on 2008-08-08
Entered in a terminal what does > scanimage -L output?
The [sane search engine]("http://www.sane-project.org/cgi-bin/driver.pl?manu=Brother&model=&bus=any&v=&p=") does not list your device.

---

### Post by plucky on 2008-08-09
> **pdhb said:**
> I have now, thanks to plucky successfully got the dcp130c brother printer working, but now i want to get the scanner to work.

can anyone help with this, xsane cant find it??

thanks

pdhb

You need to install the [Brother Scanner](http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html) driver brscan2,which can be downloaded from the Brother website(see link).Remember to get the **Debian** version for either 32 bit or 64 bit depending on which version you have installed.

The instructions to install are also on the website.


Good Luck

---

