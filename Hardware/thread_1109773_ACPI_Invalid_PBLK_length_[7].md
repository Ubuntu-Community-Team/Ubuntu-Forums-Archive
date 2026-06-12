---
title: "ACPI: Invalid PBLK length [7]"
date: 2009-03-29
forum: Hardware
---

### Post by messner on 2009-03-29
I have installed Ubuntu 9.04 beta on my computer **HP Compaq DC7900**, because I had problems with former kernel:  Linux version 2.6.27.19-170.2.35.fc10.i686 .

Right after the start of the computer (after Grub), there is this message written on screen:

**ACPI: Invalid PBLK length [7]**
**ACPI: Invalid PBLK length [7]**

The same problems (messages) are also present on this computer with the same kernel (2.6.27) in Ubuntu 8.10 and on Fedora 10 and Fedora 11 alpha (2.6.29 kernel). 

There are also some additional error messages in the system log - I am attaching the log:
[https://bugzilla.redhat.com/attachment.cgi?id=337154]("https://bugzilla.redhat.com/attachment.cgi?id=337154")

I have also described the problem on Fedora kernels in bugzilla: 
[https://bugzilla.redhat.com/show_bug.cgi?id=491158]("https://bugzilla.redhat.com/show_bug.cgi?id=491158")

Otherwise, the computer seems to work without problems.

My questions are:

Is it safe to use this computer (DC7900/Ubuntu 9.04 beta) with this errors ?

What can be done about it ?

---

### Post by jhovik on 2009-05-04
I'm having the same problem here.  I've search quite a bit without any success.  I'm running the official release of jaunty, though.

---

### Post by messner on 2009-05-04
I am using it for a month now and it works very nice, but this message still bothers me.

---

### Post by tikey on 2009-05-12
I also get this message. I'm not sure if it is related or not but my computer stops working from time to time.
Does anyone have an idea what this error message might be?

---

### Post by nnorman on 2009-08-05
I just installed Ubuntu 9.04 server on a system that has power management disabled in the BIOS.  I promptly saw this error on boot and Google brought me here.

Making the error message go away was pretty easy ... I edited the kopt line in /boot/grub/menu.lst and appended "acpi=off".  Rebooted and the message is gone.

---

### Post by messner on 2009-08-05
> **nnorman said:**
> Rebooted and the message is gone.

But you are left without APCI with this solution ;(

But if you are using the server version, you probably don't care ...

---

### Post by gimper48 on 2009-09-30
Any update on this issue.  I am still having these problems. I cannot turn off acpi as I run a quad core that runs very hot if it cannot throttle with acpi.

---

### Post by kunibert65 on 2012-05-04
the same happened me after kernel updating from 2.6.40 to 3.3.2 on a DC 7900 (ubuntu 10.04)

---

