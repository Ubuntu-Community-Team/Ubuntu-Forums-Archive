---
title: "Scanjet 6300C"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by Drate on 2008-04-09
Apparently NOBODY has ever had this exact message (according to google search).

Error during CMS conversion:
Could not open scanner ICM profile:

That's all it says.  The problem here being I can't seem to get color scans.  Sane-Project.org says the driver is complete, xsane recognized it fine, I can't find ANY decent information on ICM profiles or how to get one or create one or whatever needs to be done.  Any ideas?

---

### Post by ioulianos on 2008-05-05
> **Drate said:**
> Apparently NOBODY has ever had this exact message (according to google search).

Error during CMS conversion:
Could not open scanner ICM profile:

That's all it says.  The problem here being I can't seem to get color scans.  Sane-Project.org says the driver is complete, xsane recognized it fine, I can't find ANY decent information on ICM profiles or how to get one or create one or whatever needs to be done.  Any ideas?


I don't know if it makes you feel better but I have the same error message. I have a FB630Ui scanner.

---

### Post by rezerected on 2008-05-12
I'm also having the same problem with Xsane at the moment.  I'm still fairly new to Ubuntu, and the first time I used this program with GIMP, I did not have any problems at all with the scanning.

But right now, I am getting the same, repeated error messages as the OP and it will not let me set my scan size to scan the full 11.5 x 8.  It's preset to the previous scan area I had set before.  It bypasses the first Xsane preview screen and jumps to the scan screen. 

FWIW, I am using an HP 2400 series AIO printer and Ubuntu 8.04

---

### Post by Drate on 2008-05-14
Oh, well, actually it does make me feel better to know yall are experiencing this same error... I mean... I'm sorry for you two... but it is reassuring.

---

### Post by rezerected on 2008-05-14
I can't believe it's been more than 1 month since you posted this problem and not a single response from the Ubuntu community.  Maybe we should start a different thread in regards to the problem with Xsane?

---

### Post by LUPAREYES on 2008-05-21
simpemente desconecta en la ocion 
preferencia/habilitar gestion de color   debes estar off


	
simpemente disconnected in the ociones
preference / enable color management you must be off

---

### Post by Delawaredave on 2008-06-03
> **rezerected said:**
> I'm also having the same problem with Xsane at the moment.  I'm still fairly new to Ubuntu, and the first time I used this program with GIMP, I did not have any problems at all with the scanning.

But right now, I am getting the same, repeated error messages as the OP and it will not let me set my scan size to scan the full 11.5 x 8.  It's preset to the previous scan area I had set before.  It bypasses the first Xsane preview screen and jumps to the scan screen. 

FWIW, I am using an HP 2400 series AIO printer and Ubuntu 8.04

For me, if I uncheck "Preferences / Enable Color Management" this error goes away - and scanner works normally.

I think you only want this checked if you have specific ICC profiles loaded (under Preferences/ Setup / Color Management

---

### Post by rezerected on 2008-06-13
Thanks for the tips, guys.

Removing the "Enable Color Management" in Preferences seems to resolve the CMS error messages I was receiving.

But it still bypasses the first Xsane Preview screen.  I'm not sure how all this problem came about because the first few times I used Gimp and Xsane it worked perfectly.  And then the next time I went to use it I started encountering these problems, despite not having changed any settings whatsoever.

---

