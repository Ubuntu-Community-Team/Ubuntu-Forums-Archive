---
title: "Brother MFC-240C Printer install"
date: 2010-05-15
forum: Hardware
---

### Post by netnode on 2010-05-15
G'day,

I think I could really get to like Ubuntu.

I have just downloaded 10.04 and I have  64bit system.

I have searched this forum and the web trying to find out how I can install my printer a Brother MFC-240C.

It's not listed on the printers hidden within Ubuntu.

I have wasted so much time attempting to replicate what others say they have done, however, I got nowhere fast.

I have downloaded what Brother say are the drivers I need:

mfc440cnlpr-1.0.1-1.i386.deb

mfc440cncupswrapper-1.0.1-1.i386.deb

Can anyone PLEASE tell me what I need to do with these to install them?

Using the deb installer tells me it's the wrong architecture, yet, Brother say they are the files for a x64 system??

If I could only get my printer working I would be happy to keep using Ubuntu, however, not having a printer will be a big problem.

Any experts out there that can help an old digger?  :confused:

EDIT:  Did I mention that I am new at Linux and know nothing!

---

### Post by plucky on 2010-05-15
> **netnode said:**
> G'day,

I think I could really get to like Ubuntu.

I have just downloaded 10.04 and I have  64bit system.

I have searched this forum and the web trying to find out how I can install my printer a Brother MFC-240C.

It's not listed on the printers hidden within Ubuntu.

I have wasted so much time attempting to replicate what others say they have done, however, I got nowhere fast.

I have downloaded what Brother say are the drivers I need:

mfc440cnlpr-1.0.1-1.i386.deb

mfc440cncupswrapper-1.0.1-1.i386.deb

Can anyone PLEASE tell me what I need to do with these to install them?

Using the deb installer tells me it's the wrong architecture, yet, Brother say they are the files for a x64 system??

If I could only get my printer working I would be happy to keep using Ubuntu, however, not having a printer will be a big problem.

Any experts out there that can help an old digger?  :confused:

EDIT:  Did I mention that I am new at Linux and know nothing!

You are in luck as your printer is one that has already been packaged in Ubuntu.

Use Synaptic Package Manager to install your drivers.

Go To **System > Administration > Synaptic Package Manager** and search for **mfc-240c** and it will find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
```
Select and install both.

Then connect and power on your printer and open **System > Administration > Printing** and install your printer.


Good Luck

---

### Post by netnode on 2010-05-15
Thanks, it solved my problem and now I can relax and enjoy my experience with Ubuntu.

---

