---
title: "ATI/AMD properitairy FGLRX graphics driver"
date: 2011-10-20
forum: Hardware
---

### Post by minipot on 2011-10-20
Hi I recently reinstalled ubuntu after a rather turbulent wubi experience and the drivers I need to make My dual screen setup wont install properly. the drivers are ATI/AMD properitairy FGLRX graphics driver the original installs fine but the ATI/AMD properitairy FGLRX graphics driver post release update breaks with this message: Sorry, the installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

However when I look at /var/log/jockey.log I dont understand (still being a geek in training).


CAN ANYONE SUGGEST A WAY TO INSTALLL THE SECOND DRIVER?

---

### Post by 2F4U on 2011-10-20
It may be helpful if you could post the content of the log file so that we know what the error is.

---

### Post by minipot on 2011-10-20
Its very long I'll show you it next time i access my pc

---

### Post by minipot on 2011-10-21
[SIZE=4][/SIZE][B]sorry it was too big for the site to cope with.
but heres a query could it be because of a 32bit OS (ubuntu) running on a 64bit system
[/B]

---

### Post by minipot on 2011-10-21
Dont worryi found a way to fix it (aka. Ifound the the thing i wanted just wasnt in the same place as before

---

### Post by emanamini on 2011-10-21
I have same problem can you show me how to fix it?
thank you

---

### Post by sarloth on 2011-10-21
I am also experiencing this issue and would appreciate if you could share how you resolved it. Thanks!

---

### Post by skumara on 2011-10-21
I also have the same problem. How to fix ya?

---

### Post by ubupirate on 2011-10-21
Not sure why the post release updates one is even in the list when it's clearly broken.

---

### Post by Frostbytn on 2011-10-21
I am having the same issue. Been looking for weeks for a reason as to why it won't install. It wouldn't install them on 11.04 either. I have the ATI Raden HD 4200 series. If some one would like to view the jockey file. I would be willing to email it to them since it is too large to fit on here. I am using the 64 bit O/S with am AMD Phenom 2 64 bit processor.

---

### Post by jmate24 on 2011-10-22
go to amd's website [http://http://support.amd.com/us/Pages/AMDSupportHub.aspx]("http://http://support.amd.com/us/Pages/AMDSupportHub.aspx")

then enter your details on the right side of the screen i.e.

Component Category:
1. Desktop Graphics
Product Line:
2. Raedon HD Series
Product Model:
3. Raedon 5xxx HD Series PCIe
Operating System:
4. Linux x86_x64    note if you are running 32bit then choose Linux x86

then click green button: View Results >

the driver page for Linux x86_x64 for Raedon 6xxx, 5xxx, 4xxx, 3xxx HD Series is:
[http://http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

then go to the Applications Menu > Accessories > Terminal

or in Unity:

Dash > Type in the Search Pane: Terminal

then enter this into the command line and hit enter:
```
cd ~/Downloads && sudo sh ati-driver-installer-11-9-x86.x86_64.run 
```

Type your login password.

Recommended install works fine.

---

