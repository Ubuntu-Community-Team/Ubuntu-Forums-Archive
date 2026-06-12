---
title: "Need some help installing a printer."
date: 2008-09-28
forum: General Help
---

### Post by fidde88pven on 2008-09-28
Hi!

I recently bought a new printer, a Brother dcp 135
but Ive never installed a printer on Ubuntu before.

I would really appreciate if someone could help me!

I found drivers but dont know what to do with them...

Thanks in advance!

Best regards Fredrik Eliasson SWEDEN

---

### Post by jigsaws on 2008-09-28
You should configure CUPS system. Try to run System/Config/Printers (i'm not sure). If you can find your printer, use drivers (ppd file?)

But first of all, check if you can print after connecting the printer :-)

---

### Post by plucky on 2008-09-29
> **fidde88pven said:**
> Hi!

I recently bought a new printer, a Brother dcp 135
but Ive never installed a printer on Ubuntu before.

I would really appreciate if someone could help me!

I found drivers but dont know what to do with them...

Thanks in advance!

Best regards Fredrik Eliasson SWEDEN

Are you running Hardy 8.04.1? If so,the driver packages are in synaptic.

See this [link](https://wiki.ubuntu.com/BrotherDriverPackaging?highlight=(brother)) for which packages you need to install.

After the drivers are installed,go to **System > Administration > Printing** and add a new printer.If the printer is powered on and connected,it should find it and install the correct driver.

After it is installed,you can then configure the options you require.

If you are not running Hardy the see this [thread](http://ubuntuforums.org/showthread.php?t=590793) for installing Brother printers.

Good Luck

---

### Post by reality1011 on 2008-09-29
Just so you know if you dont find the exact model, try one that is close.  For example, I have my computer setup on the 2551 setting but it is a 2571N

Still works

---

### Post by fidde88pven on 2008-09-30
Thanx for all your answers!

I will try once more and then get back to you.

One question still, according to the text in the link provided by plucky, there is no drivers for the scanner? 

Wont it work?

Thanx again, best regards Fredrik

---

### Post by Sef on 2008-09-30
>  One question still, according to the text in the link provided by plucky, there is no drivers for the scanner? 

Most likely the drivers for dc130 will work on your printer.

---

### Post by fidde88pven on 2008-09-30
Hello!


Thanx again, ive got the printer working!

Now its only the scanner that is not working, when starting Xsane I get an I/O error.

Help plz!

---

### Post by plucky on 2008-09-30
> **fidde88pven said:**
> Hello!


Thanx again, ive got the printer working!

Now its only the scanner that is not working, when starting Xsane I get an I/O error.

Help plz!

The drivers for the scanner have to be downloaded from the [Brother Website](http://solutions.brother.com/linux/en_us/download_scn.html#brscan2).

You need to download the deb package called **brscan2**,either the 32-bit or 64-bit, depending on which version of operating system you are running.Installation instructions are on the Website where you download the drivers from,or use the instructions shown in the second link I gave you for non Hardy installation.

Also install the **scan-key-tool** as well.

Good Luck

---

### Post by fidde88pven on 2008-10-01
Thanx for all you help, but I cant get it to work...

I have 8.04 but xsane gets an I/O error even after doing like all the links says... 

And I guess the links isnt made for Hardy??

Well I would appreciate it very much if someone could help me some more...


Best regards Fredrik

---

### Post by plucky on 2008-10-01
> **fidde88pven said:**
> Thanx for all you help, but I cant get it to work...

I have 8.04 but xsane gets an I/O error even after doing like all the links says... 

And I guess the links isnt made for Hardy??

Well I would appreciate it very much if someone could help me some more...


Best regards Fredrik

Open a terminal and ```
xsane
``` and post any output.
Also post output of ```
lsusb
```

Did you install sane-utils?

What driver did you install?

Try to run xsane in "sudo" mode to see if that works.Warning: It is not recommended in normal use to use "sudo" mode.

Have you edited the "/etc/udev/rules.d/40-basic-permissions.rules" file?

---

### Post by fidde88pven on 2008-10-07
Hello!

When I type sudo xsane it works...

lsusb output:
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 002: ID 04f9:01ce Brother Industries, Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

How should I edit basic-permissions?

//Fredrik

---

### Post by fidde88pven on 2008-10-07
Finally!!

Ive got the scanner working now!

I editet the file u mentioned, and changed the mode from 0664 to 0666.

There is howevera few things I wonder.

Can I scan from the scanner using its interface without loggin on to the computer and save the file on the PC. The power of the PC is allways on.

Thanx for all your help!

---

### Post by plucky on 2008-10-07
> Can I scan from the scanner using its interface without loggin on to the computer and save the file on the PC.


That doesn't work for me.


Good Luck

---

