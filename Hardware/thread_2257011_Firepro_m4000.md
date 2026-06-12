---
title: "Firepro m4000"
date: 2014-12-16
forum: Hardware
---

### Post by diho on 2014-12-16
Hello all,

recently I have installed ubuntu on my laptop ( a HP Elitebook 8570w) and I've stumbled upon the problem that I can't find any drivers for my graphics card. (Which is a Firepro m4000)
I have browsed the forum and can' t find any good solution to this.

So my question is if any of you know where I can find the correct drivers, or know an other solution for this problem.

Kind regards,

~Diho

---

### Post by diho on 2014-12-19
Anyone? Please it is giving much problemen. Sensors says the temp is getting to 60 degrees celcius

---

### Post by Mark Phelps on 2014-12-19
> I can't find any drivers for my graphics card.

Go to the page in the link:  [http://support.amd.com/en-us/download]("http://support.amd.com/en-us/download")

Once there, enter the following values:
Step 1 - Workstation graphics
Step 2 - Mobility Firepro series
Step 3 - HP Elitebook 8570w
Step 4 - Linux x86 (if you're running 32-bit Ubuntu) Linux x86-64 (if you're running 64-bit Ubuntu)
Step 5 - Click Display Results, then click the Download button -- this will download a .ZIP file (compressed archive) to your PC

You have to uncompress the .ZIP file and when you do, you'll see a folder named fglrx-13.352.1006.  Inside that folder is a .run file.  You use that to install the drivers.

---

### Post by diho on 2014-12-22
Thanks for your reply, Mark.

Sadly it doesn't work. Here's the output it gives me:

> root@diho-HP:/home/diho/Downloads/fglrx-13.352.1006# ./amd-driver-installer-13.352.1006-x86.x86_64.run Created directory fglrx-install.LkGdZj
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-13.352.1006.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

error: Detected X Server version 'XServer 1.16.0_64a' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:x86_64:lib32:XServer 1.16.0_64a:none:3.16.0-28-generic:)
Installation will not proceed.

Removing temporary directory: fglrx-install.LkGdZj

Do you perhaps know what do to about this?

---

### Post by QIII on 2014-12-22
Hello!

This appears to indicate that much like the HD4000 and earlier adapters, your FirePro adapter no longer enjoys AMD support for Linux with the more current version of X-Server.

I'm afraid you will need to stay with the default open source driver that was initially installed with Ubuntu.

There is nothing anyone in the Linux world can do about this, as AMD is in control of their proprietary drivers.

---

