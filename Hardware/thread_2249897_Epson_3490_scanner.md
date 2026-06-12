---
title: "Epson 3490 scanner"
date: 2014-10-25
forum: Hardware
---

### Post by joverstreet1 on 2014-10-25
Trying to install Epson perfection 3490 scanner.

Can anyone give me the short version of what the following error messaging means and how to fix it ?

Thanks.

[B]checking for GTK... no
checking for GTK... configure: error: Package requirements (gtk+) were not met:

No package 'gtk+' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

---

### Post by Enigma12 on 2014-10-27
I can't help you with understanding the error messages. I'm too new to Linux to know. But, FWIW, my Epson Perfection 1200 scanner is working perfectly with my Lubuntu 14.04 desktop computer. I did download, as well as I can recall, from the Epson website, the recommended .deb file and installed it to make it work. My scans have been excellent. 

If I had gotten this error message, I would have followed the advice in the last line you show.

---

### Post by joverstreet1 on 2014-10-27
> **Wayne_Terrebonne said:**
> I can't help you with understanding the error messages. I'm too new to Linux to know. But, FWIW, my Epson Perfection 1200 scanner is working perfectly with my Lubuntu 14.04 desktop computer. I did download, as well as I can recall, from the Epson website, the recommended .deb file and installed it to make it work. My scans have been excellent. 

If I had gotten this error message, I would have followed the advice in the last line you show.

Thanks for your reply, however, may I ask where you found .deb files on Epson site ?  I do not see any .deb files there.

As far as following the instructions on the error message, unless I am missing it, I can find NO folders or files (**pkg-config man page**) in the drivers that I downloaded from Epson site that are named as referred to in the last line of the error message.

Thanks.

---

### Post by Mike_Walsh on 2014-10-27
Hi there.Yes, you're quite right; there's no .deb files at all, are there? Only .rpm packages, and midi5 (whatever they are). 

I'm running an Epson all-in-one; an SX218. You still have to download printer drivers, and scanner data & driver packages separately, however. Have you tried extracting the tar.gz compressed file, to see what that contains?

Regards,

Mike.

---

### Post by joverstreet1 on 2014-10-27
> **Mike_Walsh said:**
> Hi there.Yes, you're quite right; there's no .deb files at all, are there? Only .rpm packages, and midi5 (whatever they are). 

I'm running an Epson all-in-one; an SX218. You still have to download printer drivers, and scanner data & driver packages separately, however. Have you tried extracting the tar.gz compressed file, to see what that contains?

Regards,

Mike.

Mike:

Yes, downloaded the tar file and ran ./configure and always get error messages.  The error message refers to a file or folder that does not exist in the extracted tar file, as far as I can see and I have looked thru every folder and file that was extracted.

Thanks.

---

### Post by joverstreet1 on 2014-10-27
> **Mike_Walsh said:**
> Hi there.Yes, you're quite right; there's no .deb files at all, are there? Only .rpm packages, and midi5 (whatever they are). 

I'm running an Epson all-in-one; an SX218. You still have to download printer drivers, and scanner data & driver packages separately, however. Have you tried extracting the tar.gz compressed file, to see what that contains?

Regards,

Mike.

Mike:

Yes, downloaded the tar file and ran ./configure and always get error messages.  The error message (**pkg-config man page)** refers to a file or folder that does not exist in the extracted tar file, as far as I can see and I have looked thru every folder and file that was extracted.

Thanks.

---

### Post by Mike_Walsh on 2014-10-27
Having said that, it's interesting to note that even the driver filter packages for my own Epson APPEAR to have been converted from .rpm files (is this a Red Hat conspiracy?) ;)

Regards,

Mike.

---

### Post by joverstreet1 on 2014-10-27
> **Mike_Walsh said:**
> Having said that, it's interesting to note that even the driver filter packages for my own Epson APPEAR to have been converted from .rpm files (is this a Red Hat conspiracy?) ;)

Regards,

Mike.

Mike:

I even converted the RPM driver files on Epson website using Alien and then went thru the installation process, everything seemed to go just fine, however, still no cigar, both Simple Scan and Xsane come back saying that scanner is not connected.  IT IS connected on both ends and has AC power to it !!!!

I reckon I am going to have to go to the **embarrsement** of taking it to a MS$ computer to see if it works !!!

Thanks.

---

### Post by joverstreet1 on 2014-10-29
I just hooked the scanner to a Windows 2000 machine and in less than 3 mintues I had the scanner working.

Going on 4 days now and still can not get it to work on Linux machine.

---

### Post by Enigma12 on 2014-10-29
> **joverstreet1 said:**
> Thanks for your reply, however, may I ask where you found .deb files on Epson site ?  I do not see any .deb files there.

As far as following the instructions on the error message, unless I am missing it, I can find NO folders or files (**pkg-config man page**) in the drivers that I downloaded from Epson site that are named as referred to in the last line of the error message.

Thanks.

Sorry about the very late response, but I missed this thread for a few days. I just tried to find drivers on the Epson website for your scanner and came up emply. Hopefully someone else can suggest a what-now? plan of action. I'm too new to Linux to have any suggestions.

---

