---
title: "Printer driver for Ricoh Aficio 1018"
date: 2017-12-10
forum: Hardware
---

### Post by aggresivo on 2017-12-10
Hey Friends,

I've gotten two old [Ricoh Aficio 1018]("http://goldencupexim.com.ph/wp-content/uploads/2014/12/Ricoh-Aficio-1018-or-2018.png") laser printers in more or less perfect working conditions. These are A3 B/W office copiers from a long gone era, but since the are still looking good I don't want to throw them away. 

The official Ricoh site has drivers for Windows, Mac and Windows Server, but for Linux they only have a "[Unix Connection Utility]("http://support.ricoh.com/bb/html/dr_ut_e/re1/model/x1015_18/x1015_18.htm?lang=en")"  which requires a TCP/IP connection to the printer, which mine doesn't  offer. Mine only has a parallel port on the back which I've connected an  parallel->USB adapter to.

The real problem I'm having is that there are no official Linux drivers out there. I've checked the [openprinting.org database]("http://www.openprinting.org/printers/manufacturer/Ricoh") and they only have the [Aficio 1022]("http://www.openprinting.org/printer/Ricoh/Ricoh-Aficio_1022") listed, but not the Aficio 1018. I've installed it as a 1022 in CUPS and it printed the test page just fine, both in A4 (letter) and in A3. Unfortunately any other page I'm trying to print, no matter if it is pdf, txt, or a website the printer is only producing garbage. It prints A3 pages with only a single line on the top with random characters, sometimes just one character alone..

It would be awesome if anyone could help me here or point me in the right direction.

All the best,
aggresivo

---

### Post by pdc on 2017-12-11
I have posted a suggestion on the AskUbuntu forum where this question also appears

---

### Post by aggresivo on 2017-12-15
This unfortunately didn't work out, do you have any other tips?

---

### Post by pdc on 2017-12-15
only that you perhaps need a version of Windows on a virtual machine inside your Ubuntu install; that could perhaps use the Ricoh windows drivers ...........

---

### Post by sccman on 2017-12-15
If you don't mind upgrading Ubuntu, you could upgrade to 17.10. 17.04 introduced support for driver-less printing, but its support lifespan is ending in January 2018. 17.10 allows support until June 2018.

Here is more information about 17.04's driver-less printing support:

[https://wiki.ubuntu.com/ZestyZapus/ReleaseNotes#Driverless_Printing](https://wiki.ubuntu.com/ZestyZapus/ReleaseNotes#Driverless_Printing)


Other than that, I know Google Chrome provides Google Cloud Print support for PDF or image files. That could be something you could look into.

---

### Post by kostkon on 2017-12-15
> **aggresivo said:**
> Mine only has a parallel port on the back which I've connected an  parallel->USB adapter to.
[This Ubuntu wiki page]("https://wiki.ubuntu.com/DebuggingPrintingProblems#USB_-.3E_Parallel_adapter") offers some suggestions about those adapters.

---

