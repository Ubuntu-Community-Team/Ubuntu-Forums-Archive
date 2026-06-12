---
title: "Brother MFC-7362N- can't install downloaded file(s)"
date: 2014-06-04
forum: Hardware
---

### Post by psyclone on 2014-06-04
Hi,
I've purchased a MFC-7362N. I'm running 12.04 (64 Bit) (Ubuntu) & running VMware virtual machine for Windows. I've installed and are successfully running the printer on Windows. But I'm unable to run it on Ubuntu. I've installed a recommended driver suggested by Ubuntu Software Centre. Also, it registers that the printer's connected in when attempting to print. But it won't print? I've down loaded the " linux-brprinter-installer-2.0.0-1 " file but I can't run or install it. 

Please help.
Regards.

---

### Post by pdc on 2014-06-05
> I've down loaded the " linux-brprinter-installer-2.0.0-1 " file but I can't run or install it. 

if you open a terminal; if you paste in the commands in red below

> [COLOR="#FF0000"]cd Downloads[/COLOR]               .........if you downloaded and saved the file, it should be there; and if you type > [COLOR="#FF0000"]ls[/COLOR] it will list the contents of the [COLOR="#0000FF"]Downloads[/COLOR] directory 

> [COLOR="#FF0000"]gunzip linux-brprinter-installer-2.0.0-1.gz[/COLOR]        (that is what Brother recommend if you are starting from scratch whereas you may have this already unpacked in that directory??)

> [COLOR="#FF0000"]sudo bash linux-brprinter-installer-2.0.0-1 MFC-7362N[/COLOR]

..........that should get the install script running; they say it installs the scanning side of things too; let us know how it goes

---

### Post by psyclone on 2014-06-05
Thanks, that worked.
Cheers

---

### Post by pdc on 2014-06-05
great; enjoy

the scanner is working well, is it?

As owner of the thread, you can mark it SOLVED using thread tools near the top: anyone googling on your device may get a help from your experience

---

